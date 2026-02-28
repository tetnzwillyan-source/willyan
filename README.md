#include <stdio.h>
#include <string.h>

// Estrutura representando uma carta de cidade
struct Carta {
    char estado[32];              // Estado
    char codigo[16];              // Código da carta (ex.: A01, B03)
    char cidade[64];              // Nome da cidade
    unsigned long int populacao;  // População (números grandes)
    float area;                   // Área em km²
    float pib;                    // PIB em reais
    int pontosTuristicos;         // Número de pontos turísticos
    float densidade;              // Densidade populacional (hab/km²)
    float pibPerCapita;           // PIB per capita
    float superPoder;             // Super Poder calculado
};

// Função para calcular atributos derivados
void calcularAtributos(struct Carta *c) {
    // Evita divisão por zero
    if (c->area <= 0 || c->populacao == 0) {
        c->densidade = 0.0f;
        c->pibPerCapita = 0.0f;
    } else {
        c->densidade = c->populacao / c->area;
        c->pibPerCapita = c->pib / c->populacao;
    }

    // Calcula o Super Poder com conversões adequadas
    if (c->densidade > 0)
        c->superPoder = (float)c->populacao + c->area + c->pib +
                        (float)c->pontosTuristicos + c->pibPerCapita +
                        (1.0f / c->densidade);
    else
        c->superPoder = (float)c->populacao + c->area + c->pib +
                        (float)c->pontosTuristicos + c->pibPerCapita;
}

int main() {
    struct Carta carta1, carta2;

    // --- Cadastro da Carta 1 ---
    printf("\n=== Cadastro da Carta 1 ===\n");
    printf("Estado: ");
    scanf(" %31[^\n]", carta1.estado);

    printf("Codigo da carta: ");
    scanf(" %15s", carta1.codigo);

    printf("Nome da Cidade: ");
    scanf(" %63[^\n]", carta1.cidade);

    printf("Populacao: ");
    scanf("%lu", &carta1.populacao);

    printf("Area (em km2): ");
    scanf("%f", &carta1.area);

    printf("PIB (em reais): ");
    scanf("%f", &carta1.pib);

    printf("Numero de Pontos Turisticos: ");
    scanf("%d", &carta1.pontosTuristicos);

    calcularAtributos(&carta1);


    // --- Cadastro da Carta 2 ---
    printf("\n=== Cadastro da Carta 2 ===\n");
    printf("Estado: ");
    scanf(" %31[^\n]", carta2.estado);

    printf("Codigo da carta: ");
    scanf(" %15s", carta2.codigo);

    printf("Nome da Cidade: ");
    scanf(" %63[^\n]", carta2.cidade);

    printf("Populacao: ");
    scanf("%lu", &carta2.populacao);

    printf("Area (em km2): ");
    scanf("%f", &carta2.area);

    printf("PIB (em reais): ");
    scanf("%f", &carta2.pib);

    printf("Numero de Pontos Turisticos: ");
    scanf("%d", &carta2.pontosTuristicos);

    calcularAtributos(&carta2);


    // --- Exibição das Cartas ---
    printf("\n=== Dados das Cartas ===\n");

    printf("\nCarta 1:\n");
    printf("Estado: %s\n", carta1.estado);
    printf("Codigo: %s\n", carta1.codigo);
    printf("Cidade: %s\n", carta1.cidade);
    printf("Populacao: %lu\n", carta1.populacao);
    printf("Area: %.2f km2\n", carta1.area);
    printf("PIB: %.2f reais\n", carta1.pib);
    printf("Pontos Turisticos: %d\n", carta1.pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km2\n", carta1.densidade);
    printf("PIB per Capita: %.2f reais\n", carta1.pibPerCapita);
    printf("Super Poder: %.2f\n", carta1.superPoder);

    printf("\nCarta 2:\n");
    printf("Estado: %s\n", carta2.estado);
    printf("Codigo: %s\n", carta2.codigo);
    printf("Cidade: %s\n", carta2.cidade);
    printf("Populacao: %lu\n", carta2.populacao);
    printf("Area: %.2f km2\n", carta2.area);
    printf("PIB: %.2f reais\n", carta2.pib);
    printf("Pontos Turisticos: %d\n", carta2.pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km2\n", carta2.densidade);
    printf("PIB per Capita: %.2f reais\n", carta2.pibPerCapita);
    printf("Super Poder: %.2f\n", carta2.superPoder);


    // --- Comparação das Cartas ---
    printf("\n=== Comparacao de Cartas ===\n");

printf("Populacao: ");
if (carta1.populacao > carta2.populacao)
    printf("Carta 1 venceu\n");
else if (carta1.populacao < carta2.populacao)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

printf("Area: ");
if (carta1.area > carta2.area)
    printf("Carta 1 venceu\n");
else if (carta1.area < carta2.area)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

printf("PIB: ");
if (carta1.pib > carta2.pib)
    printf("Carta 1 venceu\n");
else if (carta1.pib < carta2.pib)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

printf("Pontos Turisticos: ");
if (carta1.pontosTuristicos > carta2.pontosTuristicos)
    printf("Carta 1 venceu\n");
else if (carta1.pontosTuristicos < carta2.pontosTuristicos)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

// Menor densidade vence
printf("Densidade Populacional: ");
if (carta1.densidade < carta2.densidade)
    printf("Carta 1 venceu\n");
else if (carta1.densidade > carta2.densidade)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

printf("PIB per Capita: ");
if (carta1.pibPerCapita > carta2.pibPerCapita)
    printf("Carta 1 venceu\n");
else if (carta1.pibPerCapita < carta2.pibPerCapita)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");

printf("Super Poder: ");
if (carta1.superPoder > carta2.superPoder)
    printf("Carta 1 venceu\n");
else if (carta1.superPoder < carta2.superPoder)
    printf("Carta 2 venceu\n");
else
    printf("Empate\n");
    int pontosCarta1 = 0;
int pontosCarta2 = 0;

// População
if (carta1.populacao > carta2.populacao)
    pontosCarta1++;
else if (carta1.populacao < carta2.populacao)
    pontosCarta2++;

// Área
if (carta1.area > carta2.area)
    pontosCarta1++;
else if (carta1.area < carta2.area)
    pontosCarta2++;

// PIB
if (carta1.pib > carta2.pib)
    pontosCarta1++;
else if (carta1.pib < carta2.pib)
    pontosCarta2++;

// Pontos turísticos
if (carta1.pontosTuristicos > carta2.pontosTuristicos)
    pontosCarta1++;
else if (carta1.pontosTuristicos < carta2.pontosTuristicos)
    pontosCarta2++;

// Densidade (menor vence)
if (carta1.densidade < carta2.densidade)
    pontosCarta1++;
else if (carta1.densidade > carta2.densidade)
    pontosCarta2++;

// PIB per capita
if (carta1.pibPerCapita > carta2.pibPerCapita)
    pontosCarta1++;
else if (carta1.pibPerCapita < carta2.pibPerCapita)
    pontosCarta2++;

// Super Poder
if (carta1.superPoder > carta2.superPoder)
    pontosCarta1++;
else if (carta1.superPoder < carta2.superPoder)
    pontosCarta2++;

printf("\n=== Placar Final ===\n");
printf("Carta 1: %d pontos\n", pontosCarta1);
printf("Carta 2: %d pontos\n", pontosCarta2);

// Campeão
printf("Resultado: ");
if (pontosCarta1 > pontosCarta2)
    printf("Carta 1 e a campea!\n");
else if (pontosCarta1 < pontosCarta2)
    printf("Carta 2 e a campea!\n");
else
    printf("Empate geral!\n");

    return 0;
}

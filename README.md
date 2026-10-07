# Portfolio-CAPM

Risco, retorno e precificação de uma carteira de ações brasileiras com Python: **CAPM**, **fronteira
eficiente de Markowitz** e **Black-Scholes**, com dados reais (Yahoo Finance e Banco Central) e
verificações automáticas dentro do próprio notebook.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/o-allanribeiro/Portfolio-CAPM/blob/main/Treinando_carteira.ipynb)

## O que o notebook faz

[`Treinando_carteira.ipynb`](Treinando_carteira.ipynb) percorre, com texto explicativo e fórmulas:

1. **Dados:** preços ajustados de PETR4, VALE3, BBDC4 e do Ibovespa (jan/2019 a dez/2025) e a Selic como
   taxa livre de risco (SGS 1178 do Banco Central).
2. **Retornos e risco:** retorno e volatilidade anualizados, índice de Sharpe e matriz de correlação.
3. **Carteira 30/40/30:** retorno, variância, volatilidade e ganho de diversificação.
4. **Cenários:** retorno esperado e variância por cenários com probabilidades (exercício didático).
5. **CAPM:** beta por regressão dos retornos em excesso contra o Ibovespa, linha do mercado de
   títulos (SML) e alfa de Jensen, com p-valores.
6. **Fronteira eficiente:** 20.000 carteiras aleatórias x otimização (SLSQP), carteira de variância mínima
   e de máximo Sharpe.
7. **Black-Scholes:** preço de call e put europeias, delta, paridade put-call e verificação por
   Monte Carlo.

## Resultados da amostra (jan/2019 a dez/2025)

| Ativo | Beta | Alfa anual | p-valor do alfa | R² |
|---|---|---|---|---|
| PETR4 | 1,24 | +18,8% | 0,07 | 0,53 |
| VALE3 | 0,93 | +9,5% | 0,38 | 0,37 |
| BBDC4 | 1,12 | -3,8% | 0,66 | 0,57 |
| Carteira 30/40/30 | 1,08 | +8,3% | 0,12 | 0,76 |

Os betas são estimados com precisão (p-valores desprezíveis), mas **nenhum alfa é estatisticamente
significativo a 5%**: o retorno diário é ruidoso demais para distinguir sorte de habilidade numa janela
de sete anos. É o tipo de leitura que o notebook procura deixar explícita.

## Como executar

```bash
pip install -r requirements.txt
jupyter notebook Treinando_carteira.ipynb
```

Ou clique no botão do Colab acima. O notebook baixa os dados na hora (é preciso conexão com a internet),
e a janela é fixa para que os resultados sejam reproduzíveis. As células com `assert` falham se algo
estiver inconsistente (por exemplo, paridade put-call, pesos que não somam 1 ou Monte Carlo divergente).

## Limitações

- Resultados **dentro da amostra**; não há validação fora da amostra.
- O Ibovespa é apenas uma proxy da carteira de mercado, e o CAPM é um modelo de um fator.
- O Black-Scholes usado ignora dividendos e supõe volatilidade constante.
- Material educacional: nada aqui é recomendação de investimento.

## Autor

Allan Ribeiro da Silva, [LinkedIn](https://www.linkedin.com/in/allanribeirosilva/).

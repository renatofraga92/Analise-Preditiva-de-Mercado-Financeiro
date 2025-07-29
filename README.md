# Projeto: Análise Preditiva de Mercado Financeiro

Este projeto focou na análise exploratória e no pré-processamento de dados de séries temporais financeiras. O principal objetivo foi preparar os dados para a modelagem preditiva de retornos de ativos, demonstrando habilidades essenciais como coleta, manipulação, visualização de dados, análise de estacionaridade e estruturação de conjuntos de treino/teste. Todas essas etapas são cruciais para qualquer iniciativa de previsão no mercado financeiro.

## Ativo Analisado

O ativo central para esta análise foi **GOOGL** (Alphabet Inc. - Classe A). É importante destacar que você pode facilmente alterar o `TICKER_SYMBOL` no código para analisar outros ativos, como "AAPL", "MSFT", "PETR4.SA" ou "BTC-USD".

## Tecnologias e Bibliotecas Utilizadas

- **Python**: A linguagem de programação principal do projeto.
- **yfinance**: Usado para baixar de forma eficiente dados históricos de mercado financeiro diretamente do Yahoo Finance.
- **pandas**: Essencial para a manipulação e análise de dados tabulares, especialmente com DataFrames.
- **numpy**: Para operações numéricas de alto desempenho, notavelmente no cálculo de retornos logarítmicos.
- **matplotlib**: Utilizado para criar visualizações estáticas e informativas dos dados.
- **statsmodels**: Aplicado para realizar testes estatísticos de séries temporais, como o Teste de Dickey-Fuller Aumentado (ADF).

## Etapas Realizadas e Análises Chave

### Coleta de Dados Históricos

Foram baixados dados diários do **Preço de Fechamento Ajustado (Adj Close)** para o ativo selecionado, cobrindo um período de 5 anos. O *Adj Close* é a métrica preferida para calcular retornos, pois já considera eventos corporativos como dividendos e desdobramentos de ações.

### Análise Exploratória de Dados (EDA)

- **Visualização da Tendência de Preços**: Um gráfico de linha do *Adj Close* ao longo do tempo foi gerado para identificar a tendência geral do ativo (alta, baixa, lateral).
- **Cálculo e Visualização de Retornos Logarítmicos**: Os retornos logarítmicos diários foram calculados. Essa transformação é fundamental, pois os retornos tendem a ser mais estacionários do que os preços brutos, o que é uma premissa para muitos modelos preditivos. O gráfico de retornos mostra a flutuação em torno de zero e os períodos de maior volatilidade.
- **Análise de Sazonalidade**: Foram calculados e visualizados os retornos logarítmicos médios por mês e por dia da semana. Essa análise permite identificar quaisquer padrões sazonais recorrentes no comportamento do ativo.

### Pré-processamento de Dados e Teste de Estacionaridade

- **Teste de Dickey-Fuller Aumentado (ADF Test)**: Aplicado à série de retornos logarítmicos para verificar estatisticamente sua estacionaridade. Um *p-value* baixo (geralmente ≤0.05) indica que a série é estacionária, um requisito para modelos como ARIMA.
- **Divisão Cronológica em Conjuntos de Treino e Teste**: Os dados de retornos foram divididos em conjuntos de treino (80% dos dados mais antigos) e teste (20% dos dados mais recentes). Essa abordagem cronológica é essencial em séries temporais para simular um cenário real de previsão e evitar o "vazamento de futuro".

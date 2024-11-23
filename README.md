# Global-Solution---ML

# Previsão de Consumo de Energia Elétrica com LSTM

Este projeto implementa uma solução de Redes Neurais Recorrentes (RNN) com a arquitetura LSTM (*Long Short-Term Memory*) para prever o consumo de energia elétrica no Brasil. O modelo foi desenvolvido com um pipeline completo de *Machine Learning*, utilizando dados fictícios para cinco estados brasileiros, comparando padrões de consumo e realizando previsões para os próximos 12 meses.

---

## Sumário

- [Objetivos do Projeto](#objetivos-do-projeto)
- [Pipeline do Projeto](#pipeline-do-projeto)
- [Resultados Obtidos](#resultados-obtidos)
- [Requisitos](#requisitos)
- [Uso do Projeto](#uso-do-projeto)
- [Contribuição](#contribuição)
- [Licença](#licença)
- [Agradecimentos](#agradecimentos)
- [Contato](#contato)

---

## Objetivos do Projeto

1. **Criar um dataset** representando o consumo mensal de energia elétrica por estado.
2. **Comparar o consumo** de energia elétrica entre estados brasileiros com uma análise exploratória.
3. **Tratar os dados** para entrada no modelo, incluindo normalização e divisão em treino e teste.
4. **Desenvolver e treinar** um modelo LSTM para previsão de consumo energético.
5. **Realizar previsões** para os próximos 12 meses e avaliar o desempenho do modelo.
6. **Visualizar os resultados** com gráficos detalhados.

---

## Pipeline do Projeto

### 1. Geração do Dataset

- **Descrição:** Geração de dados fictícios de consumo de energia elétrica para cinco estados brasileiros entre janeiro de 2020 e dezembro de 2023.
- **Estados Incluídos:**
  - **SP (São Paulo):** 2.000 a 5.000 kWh
  - **RJ (Rio de Janeiro):** 1.500 a 4.000 kWh
  - **MG (Minas Gerais):** 1.800 a 4.500 kWh
  - **RS (Rio Grande do Sul):** 1.200 a 3.000 kWh
  - **BA (Bahia):** 1.000 a 3.500 kWh

### 2. Tratamento de Dados

- **Conversão de Data:** Formatação da coluna `Data` para o formato datetime.
- **Normalização:** Aplicação de **Min-Max Scaling** para cada estado, transformando os valores para o intervalo [0, 1].
- **Divisão dos Dados:** Separação dos dados em 70% para treino e 30% para teste.

### 3. Análise Exploratória dos Dados (EDA)

- **Descrição:** Criação de gráficos comparativos para visualizar os padrões de consumo normalizado entre os estados ao longo do tempo.
- **Gráfico:** [`consumo_por_estado.png`](images/consumo_por_estado.png)

### 4. Criação de Sequências Temporais

- **Descrição:** Criação de janelas deslizantes de 12 meses para capturar padrões temporais e prever o consumo do próximo mês.
- **Estrutura das Sequências:**
  - **X:** Consumo dos últimos 12 meses (entrada).
  - **Y:** Consumo do mês seguinte (saída).

### 5. Desenvolvimento do Modelo LSTM

- **Descrição:** Construção e treinamento de um modelo LSTM com duas camadas LSTM e uma camada densa.
- **Configurações do Modelo:**
  - **Camadas LSTM:** 50 neurônios cada.
  - **Camada Densa:** 25 neurônios com ativação ReLU.
  - **Camada de Saída:** 1 neurônio para previsão.
  - **Função de Perda:** MSE (*Mean Squared Error*).
  - **Otimizador:** Adam.
- **Treinamento:** 50 épocas com tamanho de lote de 32.

### 6. Previsões e Avaliação

- **Descrição:** Realização de previsões no conjunto de teste e avaliação do desempenho do modelo.
- **Métricas de Avaliação:**
  - **MAE (Erro Médio Absoluto)**
  - **MSE (Erro Médio Quadrático)**
  - **RMSE (Raiz do Erro Quadrático Médio)**

### 7. Previsões para os Próximos 12 Meses

- **Descrição:** Utilização do modelo treinado para prever o consumo de energia elétrica nos próximos 12 meses.
- **Gráfico:** [`previsao_proxima_12_meses_SP.png`](images/previsao_proxima_12_meses_SP.png)

---

## Resultados Obtidos

### Gráficos Gerados

1. **Consumo por Estado:**
   ![Consumo por Estado](images/consumo_por_estado.png)

2. **Previsão SP:**
   ![Previsão SP](images/previsao_consumo_SP.png)

3. **Previsão Futura SP:**
   ![Previsão Futura SP](images/previsao_proxima_12_meses_SP.png)

### Métricas de Avaliação

As métricas de avaliação foram calculadas para os estados SP, RJ, MG, RS, e BA:

| Estado | MAE (kWh) | MSE (kWh²) | RMSE (kWh) |
|--------|-----------|------------|------------|
| SP     | 167.05    | 37,712.41  | 194.20     |
| RJ     | 127.62    | 28,264.94  | 168.12     |
| MG     | 202.83    | 53,014.64  | 230.25     |
| RS     | 124.04    | 20,076.10  | 141.69     |
| BA     | 138.33    | 26,598.75  | 163.09     |

---

## Requisitos

Para executar este projeto, instale as seguintes bibliotecas utilizando o arquivo `requirements.txt`.

### **Instalação das Dependências**

```bash
pip install -r requirements.txt

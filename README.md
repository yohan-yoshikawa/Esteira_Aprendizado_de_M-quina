# Previsão de Intenção de Compra em Lojas Virtuais

## Sobre o projeto

Uma apresentação sobre o projeto pode ser encontrada no seguinte link do Youtube:
https://youtu.be/Z4CYx-y4GSg?si=28z5QYWq9iFXIFbK

Este projeto consiste no desenvolvimento de uma esteira de aprendizado de máquina (*Machine Learning Pipeline*) para prever a intenção de compra de visitantes de lojas virtuais, utilizando informações sobre o comportamento dos usuários durante suas sessões de navegação.

O objetivo é identificar padrões que permitam classificar uma sessão como uma possível compra ou uma visita sem realização de compra.

O projeto foi desenvolvido em Python, utilizando técnicas de pré-processamento, análise exploratória, treinamento e avaliação de modelos de classificação.

## Objetivo

Construir uma esteira de aprendizado de máquina contemplando as principais etapas de um projeto de classificação:

- Análise exploratória e estatística descritiva dos dados;
- Limpeza e transformação das informações;
- Divisão dos dados em treinamento, validação e teste;
- Construção de um pipeline de pré-processamento e classificação;
- Treinamento de um modelo de aprendizado supervisionado;
- Avaliação do desempenho por meio de métricas de classificação;
- Realização de previsões individuais.

**Tipo de aprendizado:** Supervisionado  
**Tipo de problema:** Classificação binária  
**Algoritmo utilizado:** Random Forest

## Base de dados

Foi utilizado o conjunto de dados [Online Shoppers Purchasing Intention Dataset](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset), disponibilizado pelo repositório UCI Machine Learning Repository.

A base contém 12.330 registros e 18 variáveis, com informações sobre o comportamento dos visitantes durante suas sessões de navegação.

Entre as informações disponíveis estão:

- Quantidade e duração das páginas visitadas;
- Taxas de rejeição e saída;
- Valor das páginas;
- Mês da visita;
- Sistema operacional e navegador;
- Tipo de visitante;
- Ocorrência de compra.

A variável `Revenue` representa o resultado que o modelo deve prever:
- `True`: o visitante realizou uma compra.
- `False`: o visitante não realizou uma compra.

## Desenvolvimento da esteira

O desenvolvimento foi organizado nas seguintes etapas:

### 1. Análise exploratória dos dados (EDA)

Inicialmente, foram analisadas as dimensões, os tipos de variáveis, as estatísticas descritivas, os valores ausentes e a distribuição das classes.

Foi identificada uma distribuição desbalanceada, com aproximadamente 84,53% das sessões sem compra e 15,47% com compra.

### 2. Limpeza e transformação dos dados

Foram realizadas as seguintes operações:

- Remoção de 125 registros duplicados;
- Padronização das variáveis numéricas utilizando `StandardScaler`;
- Codificação das variáveis categóricas utilizando `OneHotEncoder`;
- Conversão da variável booleana `Weekend` para valores inteiros (0 e 1).

### 3. Divisão dos conjuntos

Os dados foram divididos em três subconjuntos, utilizando estratificação (`stratify`) para preservar a proporção das classes.

| Conjunto | Proporção | Registros |
|---|---:|---:|
| Treinamento | 70% | 8.543 |
| Validação | 15% | 1.831 |
| Teste | 15% | 1.831 |

### 4. Treinamento do modelo

Foi utilizado o algoritmo **Random Forest Classifier**, configurado com:

- 200 árvores de decisão (`n_estimators=200`);
- Pesos balanceados entre as classes (`class_weight='balanced'`);
- Semente aleatória definida em 42 (`random_state=42`).

O pré-processamento e o classificador foram integrados em um `Pipeline` do Scikit-learn.

### 5. Ajuste do limite de decisão

Durante a validação, foram testados diferentes limites de decisão (*thresholds*) para a classificação da probabilidade de compra.

O limite de 0,35 apresentou o maior F1-score entre os valores avaliados, sendo escolhido para a avaliação final.

### 6. Avaliação do modelo

O modelo foi avaliado utilizando o conjunto de teste, que não participou do treinamento nem da escolha do limite de decisão.

Foram utilizadas as seguintes métricas:

- Acurácia (*Accuracy*);
- Precisão (*Precision*);
- Revocação (*Recall*);
- F1-score;
- Matriz de confusão.

## Resultados

A avaliação final do modelo apresentou os seguintes resultados:

| Métrica | Resultado |
|---|---:|
| Acurácia geral | 89,95% |
| Precisão (classe compra) | 66% |
| Recall (classe compra) | 73% |
| F1-score (classe compra) | 69% |

A matriz de confusão foi utilizada para visualizar a quantidade de classificações corretas e incorretas para cada classe.

Os resultados demonstram que o modelo conseguiu identificar aproximadamente 73% das sessões que efetivamente resultaram em compras, considerando o conjunto de teste.

## Tecnologias utilizadas

- **Python:** linguagem utilizada no desenvolvimento;
- **Pandas:** manipulação e análise dos dados;
- **NumPy:** operações numéricas;
- **Matplotlib:** visualização de dados;
- **Seaborn:** construção de gráficos estatísticos;
- **Scikit-learn:** pré-processamento, treinamento e avaliação do modelo;
- **UCI Machine Learning Repository:** fonte do conjunto de dados;
- **Google Colab:** ambiente utilizado para desenvolvimento e execução do notebook.

## Como executar o projeto

### 1. Clone o repositório

```bash
git clone URL_DO_SEU_REPOSITORIO
```

### 2. Acesse a pasta do projeto

```bash
cd NOME_DO_REPOSITORIO
```

### 3. Instale as dependências

```bash
pip install -r requirements.txt
```

### 4. Execute o notebook

Abra o arquivo Previsao_Intencao_Compra.ipynb no Google Colab ou em um ambiente Jupyter Notebook.

O conjunto de dados é carregado diretamente do UCI Machine Learning Repository por meio da biblioteca `ucimlrepo`, sendo necessário acesso à internet para essa etapa.

## Estrutura do repositório

```text
Previsao-Intencao-Compra/
│
├── Previsao_Intencao_Compra.ipynb
├── README.md
└── requirements.txt
```

## Autor

Projeto desenvolvido individualmente como atividade acadêmica sobre construção de esteiras de aprendizado de máquina.

Desenvolvido em Python, com foco em classificação supervisionada e previsão de intenção de compra em lojas virtuais.

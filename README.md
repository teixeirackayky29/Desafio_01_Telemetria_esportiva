# 🏎️ Desafio 01 — Telemetria Esportiva

Projeto de geração e estruturação de dados fictícios de telemetria de um simulador de corrida online, desenvolvido com Python e Google Sheets.

O objetivo é construir uma base de dados que permita analisar o desempenho de pilotos ao longo de diferentes corridas, considerando métricas como tempo de volta, velocidade média, consumo de combustível e posição na corrida.

## 🎯 Objetivo do projeto

Desenvolver uma base de dados estruturada e com volume significativo de registros, simulando um ambiente de automobilismo virtual.

O projeto busca criar condições para futuras análises de desempenho, identificação de padrões, comparação entre pilotos e avaliação de consistência nas corridas.

## 🗂️ Modelo de dados

O projeto utiliza duas tabelas principais:

### 1. `pilotos` — Dimensão / Cadastro

Armazena as informações cadastrais dos pilotos.

| Coluna | Descrição |
|---|---|
| `piloto_id` | Identificador único do piloto (PK) |
| `nome_ficticio` | Nome fictício do piloto |
| `equipe` | Equipe à qual o piloto pertence |
| `categoria` | Categoria de competição |
| `pais` | País de origem |

### 2. `voltas` — Fato / Evento

Armazena os dados de desempenho dos pilotos em cada volta.

| Coluna | Descrição |
|---|---|
| `volta_id` | Identificador único do registro (PK) |
| `piloto_id` | Identificador do piloto (FK) |
| `corrida_id` | Identificador da corrida |
| `numero_volta` | Número sequencial da volta |
| `tempo_volta_seg` | Tempo da volta em segundos |
| `velocidade_media_kmh` | Velocidade média em km/h |
| `combustivel_restante_pct` | Percentual de combustível restante |
| `posicao_na_volta` | Posição do piloto naquela volta |

### 🔗 Relacionamento entre tabelas

Um piloto pode participar de diversas voltas, enquanto cada registro de volta pertence a um único piloto.

```text
pilotos (1) ───────── (N) voltas
```

O relacionamento é realizado por meio da chave estrangeira `piloto_id`.

## ⚙️ Tecnologias utilizadas

- **Python:** geração e manipulação dos dados.
- **Pandas:** estruturação dos dados em DataFrames e exportação para CSV.
- **Faker:** criação de dados fictícios.
- **Random:** geração de valores e distribuições aleatórias.
- **Google Colab:** ambiente de desenvolvimento e execução.
- **Google Sheets:** armazenamento e organização das tabelas.
- **Gspread:** integração entre Python e Google Sheets.

## 🧪 Estratégia de geração dos dados

Os registros são produzidos por meio de dados mockados, utilizando distribuições e regras definidas no script.

### Distribuição das categorias

| Categoria | Distribuição |
|---|---:|
| Kart | 30% |
| Formula Sim | 30% |
| Stock Sim | 25% |
| Rally Sim | 15% |

### Distribuição dos países

Os países possuem probabilidades diferentes de ocorrência, com maior participação de pilotos brasileiros.

- Brasil: 35%
- Estados Unidos: 10%
- Alemanha: 9%
- Argentina e Itália: 8% cada
- Japão e França: 7% cada
- Portugal: 6%
- México e Espanha: 5% cada

### Regras de telemetria

- O tempo de volta considera a categoria, as características da pista, a habilidade do piloto e variações aleatórias.
- A velocidade média é calculada considerando a velocidade de referência da categoria e o tempo de volta.
- O combustível diminui progressivamente a cada volta.
- A posição é determinada pelo tempo acumulado dos pilotos na corrida, sem posições repetidas na mesma volta.

Os dados são fictícios e foram desenvolvidos exclusivamente para fins educacionais e analíticos.

## 📁 Estrutura dos arquivos

```text
desafio-01-telemetria-esportiva/
│
├── README.md
├── pilotos.csv
├── voltas.csv
└── desafio_01_telemetria_esportiva.ipynb
```

*Os arquivos CSV e o notebook devem ser adicionados ao repositório conforme a organização final do projeto.*

## 🚀 Possibilidades de expansão

Como evolução do projeto, estão previstas algumas melhorias na modelagem:

- **Tabela `corridas`:** normalização das informações de corrida, incluindo pista, data e categoria.
- **Tabela `equipes`:** criação de uma dimensão específica para equipes, incluindo país-sede e ano de fundação fictício.

Essas expansões permitirão enriquecer o modelo de dados e ampliar as possibilidades de análises relacionais.

## 📈 Aplicações analíticas futuras

A base permite desenvolver análises como:

- Comparação de desempenho entre pilotos.
- Identificação dos pilotos mais consistentes.
- Análise de evolução dos tempos de volta.
- Relação entre velocidade média e tempo de volta.
- Comportamento do consumo de combustível.
- Comparação de desempenho entre categorias.
- Ranking de pilotos e equipes.

---

**Projeto desenvolvido como parte do Desafio 01 — Telemetria Esportiva.**

Foco em estruturação de dados, geração de dados fictícios e preparação de bases para análises de dados.

# Checkpoint 3 — Clustering aplicado à energia

## Integrantes
- **Gabriel Savoy** — RM 568991
- **Victor Vidigal** — RM 571318
- **Raphael Tien** — RM 570261
- **Turma:** 1CCA

> Identificação dos integrantes e da turma preenchida no README e no notebook.

## Objetivo
Aplicar K-Means a uma base simulada de unidades consumidoras para identificar perfis de consumo de energia, comparar valores de **k** pelos métodos **Elbow** e **Silhouette Score** e sugerir ações de gestão fundamentadas.

## Base de dados
São **120 unidades fictícias** de um mesmo mês, geradas previamente com NumPy (semente 303). A base CSV está **incorporada ao notebook**; nenhum arquivo externo é necessário. Não são dados de medidores reais.

| Coluna | Descrição |
| --- | --- |
| `id_unidade` | Identificador, excluído do treinamento |
| `consumo_mensal_kwh` | Energia consumida no mês (kWh) |
| `demanda_maxima_kw` | Maior demanda média de 15 minutos (kW) |
| `consumo_noturno_pct` | Percentual do consumo entre 18h e 6h (%) |

## Como executar
1. Instale **Python 3.10+** e Jupyter Notebook/JupyterLab, ou abra o arquivo no Google Colab.
2. Instale as dependências com `pip install -r requirements.txt` (no Colab, normalmente já estão disponíveis).
3. Abra `Checkpoint_3_Clustering_Energia_Completo.ipynb`.
4. Execute **todas as células na ordem** (`Run All`). O notebook já foi salvo com saídas, tabelas e gráficos.
5. Confira a identificação dos integrantes antes de compartilhar o repositório.

## Método
As três variáveis numéricas foram padronizadas com `StandardScaler`, sem incluir o identificador ou a coluna de clusters. O K-Means foi comparado de **k=1 a 8** pelo Elbow e de **k=2 a 8** pelo Silhouette, com `random_state=42` e `n_init=10`. O modelo final foi ajustado sobre os mesmos dados padronizados.

## Resultados principais
**k=3** apresentou cotovelo claro e o maior Silhouette Score (**0,6031**). Inércias: k=1 **360,00**; k=2 **184,70**; k=3 **74,25**; k=4 **61,10**. O agrupamento final possui **40 unidades por grupo**.

| Cluster | Unidades | Consumo médio (kWh) | Demanda média (kW) | Noturno médio (%) | Perfil e ação sugerida |
| --- | ---: | ---: | ---: | ---: | --- |
| 0 | 40 | 876,50 | 6,87 | 25,49 | Consumo intermediário, maior demanda: investigar picos e escalonamento de cargas. |
| 1 | 40 | 245,09 | 2,58 | 60,82 | Baixo consumo: acompanhar e compreender uso noturno. |
| 2 | 40 | 1.433,93 | 6,15 | 67,37 | Alto consumo e uso noturno: priorizar auditoria e medições horárias. |

O notebook inclui gráficos de Elbow, Silhouette e dois gráficos de dispersão, além de interpretação, recomendações e limitações.

## Limitações
Dados simulados e de um único mês não representam necessariamente consumidores reais. K-Means é sensível a valores extremos e à geometria dos grupos. As médias não demonstram desperdício e não permitem concluir sobre tarifas ou viabilidade solar. Uma análise operacional exigiria medições temporais, equipamentos, ocupação, contrato e histórico de consumo.

## Entrega
Envie ao professor **somente o link do repositório GitHub**, com acesso habilitado para avaliação. Este pacote contém notebook executado, README e dependências.

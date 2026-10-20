# Varejo360 — Marketing Mix Modeling

Case de MMM desenvolvido com Google Meridian para estimar a contribuição dos canais de mídia, ROI e cenários de realocação de orçamento.

O notebook principal é [`case_mmm_tuanny_leite_clean.ipynb`](case_mmm_tuanny_leite_clean.ipynb). A base está em [`data/varejo360_weekly.csv`](data/varejo360_weekly.csv).

## Requisitos

- **Python 3.12.x** — o ambiente original foi executado em Python 3.12.15.
- Git.
- Alguns GB livres em disco para TensorFlow e suas dependências.

Evite Python 3.13 ou versões mais recentes caso o objetivo seja reproduzir o ambiente exatamente: a compatibilidade do TensorFlow e do Meridian pode variar.

## Criar o ambiente

Clone o repositório e entre na pasta:

```bash
git clone https://github.com/tuleite/Varejo360_case_Uncover.git
cd Varejo360_case_Uncover
```

### macOS ou Linux

```bash
python3.12 -m venv .venv-meridian
source .venv-meridian/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user \
  --name varejo360-meridian \
  --display-name "Python (varejo360-meridian)"
jupyter lab
```

### Windows (PowerShell)

```powershell
py -3.12 -m venv .venv-meridian
.\.venv-meridian\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user `
  --name varejo360-meridian `
  --display-name "Python (varejo360-meridian)"
jupyter lab
```

Se o PowerShell bloquear a ativação do ambiente, use o Prompt de Comando:

```bat
.venv-meridian\Scripts\activate.bat
```

## Executar o notebook

1. Abra `case_mmm_tuanny_leite_clean.ipynb` no JupyterLab ou VS Code.
2. Selecione o kernel **Python (varejo360-meridian)**.
3. Execute as células na ordem do notebook.

Os outputs das execuções principais já estão salvos no notebook. Rodar todas as células novamente pode levar alguns minutos, pois o ajuste posterior do Meridian usa amostragem Bayesiana e TensorFlow.

## Pontos de atenção

- O projeto foi executado em CPU; GPU não é necessária para reproduzir o case.
- Execute o Jupyter a partir da raiz do repositório, para que os caminhos relativos para `data/` funcionem.
- Caso o Matplotlib apresente erro de permissão para criar cache em Linux/macOS, antes de abrir o Jupyter rode:

  ```bash
  export MPLCONFIGDIR=/tmp/matplotlib
  ```

- No Windows, o equivalente é:

  ```powershell
  $env:MPLCONFIGDIR = "$env:TEMP\matplotlib"
  ```

- A pasta `case_legacy/` reúne versões intermediárias e não é necessária para executar o notebook final.

## Estrutura

```text
.
├── case_mmm_tuanny_leite_clean.ipynb  # notebook principal
├── data/
│   └── varejo360_weekly.csv           # base fornecida para o case
├── outputs/model_reports/             # relatórios HTML dos modelos finais
├── requirements.txt
└── README.md
```

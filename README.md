# Radar UnB

Plataforma colaborativa de geolocalização para mapeamento, divulgação e acompanhamento de problemas estruturais, segurança e eventos no campus da UnB.

---

# O que é necessário

Antes de começar, instale:

- Python3
- pip
- git

Depois instale o MkDocs:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install mkdocs mkdocs-material
```

---

# Estrutura do projeto

```text
docs/
├── index.md
├── doc1.md
├── doc2.md
└── ...

mkdocs.yml
```

- Todos os arquivos `.md` devem ficar dentro da pasta `docs/`
- O arquivo `mkdocs.yml` controla o site

---

# Executando localmente

Para testar localmente:

```bash
mkdocs serve
```

Depois abra:

```text
http://127.0.0.1:8000
```


## 5. Ative o GitHub Pages

No GitHub:

```text
Settings -> Pages
```

Em:

```text
Build and deployment
```

Selecione:

```text
Source: GitHub Actions
```

---

## 6. Acesse o site

O GitHub irá gerar um link parecido com:

```text
https://usuario.github.io/repositorio/
```

---

# Opção 2 — Adicionando MkDocs em um repositório já existente

Caso você já tenha um projeto e queira adicionar documentação:

---

## 1. Instale o MkDocs

```bash
pip install mkdocs mkdocs-material
```

---

## 2. Crie a estrutura

Dentro do repositório:

```bash
mkdir docs
touch docs/index.md
touch mkdocs.yml
```

---

## 3. Configure o `mkdocs.yml`

Exemplo:

```yaml
site_name: documentation

theme:
  name: material
```

---

## 4. Adicione um workflow do GitHub Actions

Crie:

```text
.github/workflows/deploy.yml
```

Conteúdo:

```yaml
name: Deploy MkDocs

on:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: '3.x'

      - run: pip install mkdocs mkdocs-material

      - run: mkdocs gh-deploy --force
```

---

## 5. Faça commit e push

```bash
git add .
git commit -m "add mkdocs"
git push
```

---

## 6. Ative o GitHub Pages

No GitHub:

```text
Settings -> Pages
```

Selecione:

```text
Source: Deploy from branch
Branch: gh-pages
Folder: /root
```

---


# Comandos úteis

Executar localmente:

```bash
mkdocs serve
```

Gerar site estático:

```bash
mkdocs build
```

Publicar manualmente:

```bash
mkdocs gh-deploy
```

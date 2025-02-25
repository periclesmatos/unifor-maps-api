# API de Marcadores

Esta API permite gerenciar marcadores, fornecendo endpoints para criar, atualizar, listar e deletar marcadores.

## Clonando o Repositório

Para começar, clone este repositório para sua máquina local:

```sh
git clone https://github.com/periclesmatos/unifor-maps-api.git
cd unifor-maps-api
```

## Criando um Ambiente Virtual

Crie um ambiente virtual para isolar as dependências do projeto:

```sh
python -m venv venv
```

Ative o ambiente virtual:

- **Windows:**
  ```sh
  venv\Scripts\activate
  ```
- **Linux/macOS:**
  ```sh
  source venv/bin/activate
  ```

## Instalando Dependências

Instale as dependências necessárias para rodar a API:

```sh
pip install -r requirements.txt
```

## Executando a Aplicação

Após configurar o ambiente, execute a API com o seguinte comando:

```sh
uvicorn app:app --host 0.0.0.0 --port 8000 --reload
```

A API estará rodando em `http://127.0.0.1:8000/` (por padrão).

## Configurando o CORS

Se o front-end estiver rodando em um domínio diferente, será necessário configurar o CORS. Para isso, edite o código da API e adicione a biblioteca `fastapi.middleware.cors`:

1. Instale o pacote:

   ```sh
   pip install fastapi[all]
   ```

2. No seu arquivo principal (ex: `main.py`), importe e configure o CORS:

   ```python
   from fastapi import FastAPI
   from fastapi.middleware.cors import CORSMiddleware

   app = FastAPI()

   app.add_middleware(
       CORSMiddleware,
       allow_origins=["*"],  # Altere para um domínio específico, se necessário
       allow_credentials=True,
       allow_methods=["*"],
       allow_headers=["*"],
   )
   ```

Se precisar restringir o acesso a um domínio específico, altere a configuração:

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],  # Substitua pela URL do seu front-end
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

Agora, a API estará pronta para receber requisições do seu front-end sem problemas de CORS.

## Contribuição

Sinta-se à vontade para abrir issues ou pull requests para melhorias no projeto.

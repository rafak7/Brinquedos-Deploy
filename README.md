<img width=100% src="https://capsule-render.vercel.app/api?type=waving&color=805a46&height=150&section=header&text=Brinquedos%20API%20CP3&fontSize=40&fontColor=f0ebe6&animation=blinking&fontAlign=50&fontAlignY=35&width=1000" />



Este projeto implementa uma API completa para manipulação de brinquedos, permitindo operações de criação, leitura, atualização, exclusão e outras operações no banco de dados. Utiliza o framework Spring Boot para construção da API e o banco de dados Oracle para persistência de dados.

## Alterações do CP2 para o CP3

Nesta versão do projeto, foram adicionados novos métodos HTTP para tornar a API mais robusta e completa, melhorando a flexibilidade e a capacidade de resposta da aplicação:

## Link Deploy

🚀: *https://deploy-brinquedos.onrender.com*

### HEAD

Este método foi adicionado para permitir a verificação da existência de um brinquedo específico sem a necessidade de retornar o corpo da resposta. É útil para validar se um recurso está disponível ou não, reduzindo o overhead de transferência de dados.

### PATCH

Com a inclusão do método PATCH, a API agora suporta a atualização parcial das informações de um brinquedo. Isso significa que, ao invés de enviar todos os dados do brinquedo para uma atualização, é possível enviar apenas os campos que precisam ser modificados, tornando o processo de atualização mais eficiente e rápido.

### OPTIONS

A adição do método OPTIONS permite que a API retorne as opções HTTP permitidas para um brinquedo específico. Isso é particularmente útil para clientes que precisam saber quais operações podem ser realizadas em um recurso antes de fazer uma chamada real, melhorando a comunicação e a integração entre sistemas.

Estas adições aumentam significativamente a flexibilidade e a funcionalidade da API, proporcionando uma melhor experiência tanto para desenvolvedores quanto para usuários finais.




## Configuração ⚙️

A configuração do projeto é realizada através do arquivo `application.properties` na pasta `resources`, que define os parâmetros de conexão com o banco de dados Oracle.

### CRUD Completo

- **Create (POST)**: Adiciona novos brinquedos ao banco de dados. ➕
- **Read (GET)**: Consulta brinquedos existentes no banco de dados. 🔍
- **Update (PUT)**: Atualiza informações de brinquedos existentes. ✏️
- **Delete (DELETE)**: Remove brinquedos do banco de dados. ❌
- **Patch (PATCH)**: Atualiza parcialmente um brinquedo existente. 🛠️
- **Options (OPTIONS)**: Consulta os métodos HTTP permitidos para o endpoint. ℹ️
- **Head (HEAD)**: Verifica se um brinquedo existe sem retornar o corpo da resposta. 📏

## Endpoints

### Listar Todos os Brinquedos
  - `GET /brinquedos`
  - **Descrição:** Retorna uma lista de todos os brinquedos.
  - **URL de Requisição:** `localhost:8080/brinquedos`

**Resposta:**
```json
[
    "idBrinquedo": 1,
    "nome": "Boneca Barbie",
    "descricao": "Boneca Barbie com vestido azul e acessórios.",
    "preco": 90.00,
    "fabricante": "Mattel",
    "tipo": "Bonecas"
  {
    "idBrinquedo": 2,
    "nome": "Boneca Barbie",
    "descricao": "Boneca Barbie com vestido rosa e acessórios.",
    "preco": 80.00,
    "fabricante": "Mattel",
    "tipo": "Bonecas",
    
  }
]
```
### Criar Brinquedo
   - `POST /brinquedos`
   - **Descrição:** Adiciona um novo brinquedo.
   - **URL de Requisição:** `localhost:8080/brinquedos`
   - **Corpo da Requisição:**
```json
{
    "nome": "Boneca Barbie",
    "descricao": "Boneca Barbie com vestido azul e acessórios.",
    "preco": 90.00,
    "fabricante": "Mattel",
    "tipo": "Bonecas"
}
```

  ### Deletar Brinquedo
  
  - `DELETE /brinquedo/{id}`
  - **Descrição:** Remove um brinquedo com base no ID fornecido.
  - **Parâmetros de URL:** `id` - ID do brinquedo a ser removido.
  - **URL de Requisição:** `localhost:8080/brinquedos/1`

- **Consultar Brinquedo por ID**
  - `GET /brinquedos/{id}`
  - **Descrição:** Retorna os detalhes de um brinquedo específico.
  - **Parâmetros de URL:** `id` - ID do brinquedo.
  - **URL de Requisição:** `localhost:8080/brinquedos/1`

  ### Atualizar Brinquedo

- **Método:** `PUT`
- **URL de Requisição:** `localhost:8080/brinquedos/{id}`
- **Descrição:** Atualiza as informações de um brinquedo existente.
- **Parâmetros de URL:** `id` - ID do brinquedo a ser atualizado.
- **Corpo da Requisição:**
```json
{
    "nome": "Boneca Barbie",
    "descricao": "Boneca Barbie com vestido azul e acessórios.",
    "preco": 90.00,
    "fabricante": "Mattel",
    "tipo": "Bonecas"
}
```

- **Resposta:**
```json
{
    "_links": {
        "self": {
            "href": "localhost:8080/brinquedos/1",
            "title": "PUT method"
        },
        "consultar": {
            "href": "localhost:8080/brinquedos/1",
            "title": "GET method"
        },
        "brinquedos": {
            "href": "localhost:8080/brinquedos",
            "title": "GET method"
        }
    }
}
```

### Consultar Opções de um Brinquedo

- **Método:** `OPTIONS`
- **URL de Requisição:** `localhost:8080/brinquedos/{id}`
- **Descrição:** Retorna as opções HTTP permitidas para um brinquedo específico.
- **Parâmetros de URL:** `id` - ID do brinquedo.

- **Resposta:**
  - Se o brinquedo existir:
    - **Status:** 200 OK
  - Se o brinquedo não existir:
    - **Status:** 200 OK
    - **Allow:** GET, POST, PATCH, PUT, DELETE, HEAD

### Atualizar Parcialmente Brinquedo

- **Método:** `PATCH`
- **URL de Requisição:** `localhost:8080/brinquedos/{id}`
- **Descrição:** Atualiza parcialmente as informações de um brinquedo.
- **Parâmetros de URL:** `id` - ID do brinquedo a ser atualizado.
- **Corpo da Requisição:**
```json
{
    "descricao": "Boneca Barbie com vestido rosa e acessórios."
}
```
- **Resposta:**
```json
{
    "_links": {
        "self": {
            "href": "localhost:8080/brinquedos/1",
            "rel": "self"
        },
        "consultar": {
            "href": "localhost:8080/brinquedos/1",
            "rel": "consultar"
        },
        "brinquedos": {
            "href": "localhost:8080/brinquedos",
            "rel": "brinquedos"
        }
    }
}
```
### Verificar Existência de Brinquedo

- **Método:** `HEAD`
- **URL de Requisição:** `localhost:8080/brinquedos/{id}`
- **Descrição:** Verifica se um brinquedo existe sem retornar o corpo da resposta.
- **Parâmetros de URL:** `id` - ID do brinquedo.

- **Resposta:**
  - Se o brinquedo existir:
    - **Status:** 200 OK
  - Se o brinquedo não existir:
    - **Status:** 404 Not Found

💄 Dezlumbrante - App de Maquiagem

React Native Expo Node.js SQLite

📱 Sobre o Projeto

Dezlumbrante é um aplicativo mobile completo de e-commerce de maquiagem, desenvolvido com React Native e Expo. O app possui dois perfis de usuário (Admin e Cliente), com funcionalidades específicas para cada um, além de sincronização de dados com um backend RESTful.

🎯 Funcionalidades

👑 Admin

✅ CRUD completo de produtos (Criar, Ler, Atualizar, Deletar)  
✅ Gerenciamento de categorias  
✅ Visualização de todos os produtos cadastrados  
✅ Interface exclusiva para administrador  

👤 Cliente

✅ Visualização de catálogo de produtos  
✅ Adicionar/remover produtos do carrinho  
✅ Favoritar produtos ❤️  
✅ Finalizar pedido  

🔧 Gerais

✅ Autenticação com JWT  
✅ Sincronização com backend RESTful  
✅ Integração com Makeup API (produtos externos)  
✅ Banco de dados local SQLite (offline-first)  
✅ Cache de dados para modo offline  

🏗️ Arquitetura do Projeto

dezlumbrante/  
├── backend/ # Backend Node.js + SQLite  
│ ├── controllers/ # Controladores da API  
│ ├── routes/ # Rotas da API  
│ ├── middleware/ # Middlewares (auth)  
│ ├── database.js # Configuração do banco  
│ └── server.js # Servidor Express  
│  
├── src/ # Frontend React Native  
│ ├── components/ # Componentes reutilizáveis  
│ ├── context/ # Contextos (Auth, Carrinho, Favoritos)  
│ ├── screens/ # Telas do aplicativo  
│ └── services/ # Serviços (API, Database, Sync)  
│  
└── package.json # Dependências do projeto  

🚀 Tecnologias Utilizadas

Frontend

React Native (Expo) - Framework mobile  
React Navigation - Navegação entre telas  
Expo SQLite - Banco de dados local  
Axios - Requisições HTTP  
AsyncStorage - Armazenamento local  

Backend

Node.js - Runtime JavaScript  
Express - Framework web  
SQLite3 - Banco de dados relacional  
Crypto - Hash de senhas  

APIs Integradas

Makeup API - Produtos de maquiagem externos  

📦 Instalação e Execução

Pré-requisitos

Node.js (v18 ou superior)  
npm ou yarn  
Expo Go (no celular) ou emulador Android/iOS  
Git  

1. Clone o repositório

git clone https://github.com/rangelisa/projeto_mobile.git  
cd projeto_mobile  

2. Instale as dependências do frontend  
npm install  

3. Instale as dependências do backend  
cd backend  
npm install  
cd ..  

4. Configure o IP do backend  
Edite o arquivo src/services/apiService.js:  

const SEU_BACKEND_URL = 'http://SEU_IP:3000/api'; // Substitua pelo seu IP  

5. Execute o backend  

cd backend  
npm run dev  

6. Execute o app  

# Em outro terminal, na pasta raiz  
npx expo start -c  

7. Acesse o app  

Escaneie o QR code com o app Expo Go  

Ou pressione a para emulador Android  
Ou pressione i para emulador iOS  

🔐 Credenciais de Acesso

Perfil | Email | Senha  
Admin | admin@dezlumbrante.com | admin123  
Cliente | Cadastre-se no app | A sua escolha  

📱 Telas do Aplicativo

Admin  
Tela | Descrição  
Login | Autenticação de usuários  
Admin Home | Lista de produtos com botões de editar/deletar  
Produto Form | Formulário para criar/editar produtos  

Cliente  
Tela | Descrição  
Login | Autenticação de usuários  
Cadastro | Criação de nova conta  
Cliente Home | Catálogo de produtos disponíveis  
Produto Detail | Detalhes do produto selecionado  
Carrinho | Itens adicionados ao carrinho  
Favoritos | Produtos favoritados pelo cliente  

🗄️ Endpoints da API

Método | Endpoint | Descrição  
POST | /api/auth/cadastrar | Cadastro de usuário  
POST | /api/auth/login | Login de usuário  
GET | /api/auth/validar | Validar token JWT  
POST | /api/auth/logout | Logout  
GET | /api/produtos | Listar produtos  
POST | /api/produtos | Criar produto (admin)  
PUT | /api/produtos/:id | Atualizar produto (admin)  
DELETE | /api/produtos/:id | Deletar produto (admin)  
GET | /api/categorias | Listar categorias  
POST | /api/sync/full | Sincronização de dados  
GET | /api/sync/all-data | Buscar todos dados  

🔄 Sincronização de Dados

O app implementa sincronização bidirecional:

App → Backend: Envia produtos criados/atualizados localmente  
Backend → App: Recebe produtos do servidor  
Makeup API → App: Importa produtos de API externa  

## 📊 Geração de Dados em JSON (Para Análise de Dados)

Com o objetivo de atender aos requisitos da disciplina de Análise de Dados e Estatística, o sistema disponibiliza os dados em formato JSON com base direta nos retornos reais da API.

---

### 📦 Produtos (GET /api/produtos)

{
  "success": true,
  "data": [
    {
      "id": 1,
      "nome": "Base Líquida Matte",
      "categoria": "Pele",
      "preco": 59.9,
      "descricao": "Alta cobertura e longa duração",
      "imagem": null,
      "quantidade": 20,
      "created_at": "2026-04-30 10:00:00",
      "updated_at": "2026-04-30 10:00:00"
    }
  ],
  "total": 1
}
---

### 🗂️ Categorias (GET /api/categorias)

[
  {
    "id": 1,
    "nome": "Boca",
    "descricao": "Produtos para os lábios",
    "cor": "#E91E8C",
    "icone": "💄",
    "created_at": "2026-04-30 10:00:00"
  }
]

### 🧾 Vendas / Pedidos (dados para análise)

[
  {
    "id": 1,
    "usuario_id": 2,
    "total": 89.8,
    "data": "2026-04-30",
    "itens": [
      {
        "produto_id": 1,
        "nome": "Base Líquida Matte",
        "quantidade": 1,
        "preco_unitario": 59.9
      },
      {
        "produto_id": 2,
        "nome": "Batom Vermelho",
        "quantidade": 1,
        "preco_unitario": 29.9
      }
    ]
  }
]

---

### 👤 Autenticação (POST /api/auth/login)

{
  "usuario": {
    "id": 1,
    "nome": "Administrador",
    "email": "admin@dezlumbrante.com",
    "tipo": "admin"
  },
  "token": "token_gerado",
  "expira_em": "2026-05-07T10:00:00.000Z"
}

---

### 🔄 Validação de Token (GET /api/auth/validar)

{
  "usuario": {
    "id": 1,
    "nome": "Administrador",
    "email": "admin@dezlumbrante.com",
    "tipo": "admin"
  }
}

---

### 🔄 Sincronização (GET /api/sync/all-data)

{
  "produtos": [
    {
      "id": 1,
      "nome": "Base Líquida Matte",
      "categoria": "Pele",
      "preco": 59.9,
      "descricao": "Alta cobertura",
      "imagem": null,
      "quantidade": 20,
      "created_at": "2026-04-30 10:00:00",
      "updated_at": "2026-04-30 10:00:00"
    }
  ],
  "categorias": [
    {
      "id": 1,
      "nome": "Boca",
      "descricao": "Produtos para os lábios",
      "cor": "#E91E8C",
      "icone": "💄",
      "created_at": "2026-04-30 10:00:00"
    }
  ]
}


---

## 📈 Uso para Dashboard

Os dados acima refletem exatamente o retorno da API e podem ser utilizados diretamente para:

- Análise de produtos por categoria  
- Controle de estoque (quantidade)  
- Volume de produtos cadastrados  
- Integração com dashboards (Power BI, Excel ou gráficos no app)  

📊 Estrutura do Banco de Dados

Local (SQLite)  
produtos - Produtos cadastrados localmente  
produtos_api - Cache de produtos da API externa  
config - Configurações do app  

Backend (SQLite)  
usuarios - Dados de usuários (admin/cliente)  
sessoes - Tokens de autenticação  
produtos - Produtos no servidor  
categorias - Categorias de produtos  
sync_logs - Logs de sincronização  

🛠️ Scripts Disponíveis

# Frontend  
npm start              # Inicia o Expo  
npm run android        # Roda no Android  
npm run ios            # Roda no iOS  
npm run web            # Roda na web  

# Backend  
cd backend  
npm run dev            # Roda com nodemon (hot reload)  
npm start              # Roda normalmente

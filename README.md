# Aula 0: Setup do Projeto

Instalação e Configuração Inicial

- Instalar a extensão Simple React Snippets: Certifique-se de que a extensão Simple React Snippets está instalada no seu editor de código.

- Criar um Novo Projeto Next.js: Execute o seguinte comando para criar um novo projeto Next.js com suporte a TypeScript, ESLint, Tailwind e o App Router:
  npx create-next-app@latest fsw-barber --typescript --eslint --tailwind --app

- Instalar PostgreSQL: Siga as instruções para instalar o PostgreSQL no seu sistema.

- Configurar Prisma:
  1. Instale o Prisma como uma dependência de desenvolvimento:
     npm install prisma --save-dev
  2. Inicialize o Prisma com o PostgreSQL como provedor de dados:
     npx prisma init --datasource-provider postgresql
  3. Crie um novo banco de dados no NeonDB e copie a URL do PostgreSQL para o arquivo .env do projeto.

- Definir Tabelas no Prisma: Configure as tabelas necessárias no arquivo schema.prisma.

- Formatar o Código Prisma: Execute o comando abaixo para formatar o código Prisma:
  npx prisma format

- Criar e Aplicar Migrações: Crie uma migração inicial em modo de desenvolvimento:
  npx prisma migrate dev --name init_db

- Inserir Dados de Seed:
  1. Crie um arquivo seed.ts para inserção de dados.
  2. Adicione o seguinte script ao package.json para rodar o script de seed:
     "prisma": {
       "seed": "ts-node prisma/seed.ts"
     }
  3. Instale o ts-node como uma dependência de desenvolvimento:
     npm install -D ts-node
  4. Execute o script de seed para inserir os dados no banco:
     npx prisma db seed

Configuração de Estilo

- Instalar Prettier e Configurar Tailwind:
  1. Instale o Prettier e o plugin para Tailwind CSS:
     npm install -D prettier prettier-plugin-tailwindcss
  2. Crie o arquivo .prettierrc.json e adicione a configuração abaixo:
     {
       "plugins": ["prettier-plugin-tailwindcss"],
       "tabWidth": 2,
       "semi": false
     }

- Instalar e Configurar Shadcn:
  1. Execute o comando para instalar o Shadcn UI:
     npx shadcn-ui@latest init
  2. Selecione as opções:
     - Style: Default
     - Base Color: Slate
     - CSS Variables: YES
  3. Mova as pastas lib e components para dentro da pasta app e renomeie para _lib e _components para organização.
  4. Atualize os aliases no arquivo components.json para:
     "@/app/_lib/utils"
     "@/app/_components"
  5. Para instalar o botão, use:
     npx shadcn-ui@latest add button

- Configurar o Estilo Global: Adicione a estilização do Tailwind CSS ao arquivo globals.css disponível em: https://github.com/felipemotarocha/fullstackweek-barber-v2/blob/main/app/globals.css

- Configurar Modo Escuro: Abra o arquivo app/layout.tsx e adicione a classe dark à tag <html> para ativar o modo escuro:
  <html className="dark">


Instalação e Configuração do Husky e Lint-Staged

1. **Instalar Husky e Lint-Staged**:
   - Execute o seguinte comando para instalar o Husky e o Lint-Staged como dependências de desenvolvimento:
     npm install -D husky lint-staged

2. **Inicializar Husky**:
   - Inicialize o Husky com o comando:
     npx husky init

3. **Configurar Lint-Staged**:
   - Execute o comando para configurar o Lint-Staged:
     npx lint-staged

4. **Criar Configuração do Lint-Staged**:
   - Crie o arquivo `.lintstagedrc.json` com o seguinte conteúdo:
     ```json
     {
       "*.ts?(x)": ["eslint --fix", "prettier --write"]
     }
     ```

5. **Atualizar Configuração do ESLint**:
   - No arquivo `.eslintrc.json`, adicione a seguinte regra:
     ```json
     "rules": {
       "no-unused-vars": "error"
     }
     ```

6. **Configuração de Commit Convencional**:
   - Instale o `git-commit-msg-linter` como uma dependência de desenvolvimento:
     npm install -D git-commit-msg-linter

7. **Criar Script de Commit**:
   - Crie o arquivo `commit-msg` dentro da pasta `.husky` e adicione o seguinte código:
     ```sh
     #!/bin/sh
     .git/hooks/commit-msg $1
     ```
   - Certifique-se de que o arquivo `commit-msg` tem permissões de execução.

Agora o Husky e o Lint-Staged estão configurados para garantir a qualidade do código e a conformidade com as mensagens de commit convencionais.

- Tecnologias utilizadas

- **Next.js**
- **React.js**
- **PostgreSQL**
- **Tailwind CSS**
- **Prisma**
- **Node.js**
- **ShadCN**
- **TypeScript**
- **JavaScript**

Links / Documentação:
Neon DB: https://neon.tech/
Conventional Commits: https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/
Prisma ORM: https://www.prisma.io/
ShadCn: https://ui.shadcn.com/docs

Figma do Projeto: https://www.figma.com/design/ByDjVh7THsTnsSVRKNN8yy/FSW-5.0-%5BLive%5D?node-id=0-1&t=hrkbES9BIPs5YtLE-0

Desafios

- Avaliações
- Responsividade
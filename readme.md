# Baileys com MYSQL

### Esta é um adaptação do projeto **Baileys PostgreSQL** desenvolvido por [Ericky Thierry](https://github.com/erickythierry/baileys-postgresql), que oferece uma implementação do protocolo Baileys para conexão com um banco de dados PostgreSQL.

### Este é um exemplo inicial de como usar o projeto Baileys e armazenar as chaves de autenticação no banco de dados MYSQL.

## Como usar:

1. Crie uma instância do MYSQL com o banco de dados `sessions`.
2. Clone este repositório e instale as dependências com `npm install pm2@latest -g && npm install`.
3. Edite o arquivo `config.js` e preencha os dados do seu banco MYSQL.
4. Na linha 20 do arquivo `index.js`, você pode escolher o nome da sessão que será salvo no banco de dados na coluna `session_id`.
5. Por fim, dentro da pasta do projeto, execute o projeto com `pm2 start index.js --name Baileys-MySQL` . O QR code da sessão aparecerá no console. Escaneie-o com seu WhatsApp.
6. Pronto! O bot foi criado e as chaves de autenticação estão sendo salvas no banco de dados (muito melhor do que armazená-las em arquivos JSON localmente).
- As auth keys estarão na tabela `auth_keys` com as colunas: `id, session_id, key_id, key_json, created_at` e `updated_at`

## Dicas:

- O `index.js` é apenas o exemplo inicial do projeto Baileys. Sinta-se à vontade para modificá-lo.
- O `useMySQLAuthStore.js` já está preparado para usar múltiplas sessões no mesmo script, bastando passar um nome diferente para cada um.
- O `useMySQLAuthStore.js` utiliza a mesma estrutura da função `useMultiFileAuthState` do Baileys, trocando apenas o salvamento em arquivos JSON para salvar em registros numa tabela.
- O `db.js` já cria a tabela caso ela não exista no Banco.
- O `db.js` já está preparado para reaproveitar a mesma conexão com o banco de dados e assim evitar múltiplas conexões e sobrecarregar o banco.
- O `logs.js` é uma instância do Pino para exibir os logs do Baileys de maneira mais legível no console.

## Finalizando:

- Sinta-se à vontade para modificar e melhorar este projeto. É bem simples mudar para outros bancos de dados relacionais.
- Pull requests são bem-vindos!

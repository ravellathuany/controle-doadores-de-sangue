1) Cadastro de doadores

Como um doador,
Eu quero ser capaz de me cadastrar no sistema,
Para que eu possa fazer parte do banco de doadores e visualizar minhas informações cadastradas.

Regras de negócio:

- Não pode haver duplicidade de cadastro (mesmo e-mail não pode ser usado por mais de um doador).
- Todos os campos obrigatórios (nome, e-mail, senha, tipo sanguíneo, cidade, estado) devem ser preenchidos.
- A senha deve ser armazenada de forma criptografada.
- O tipo sanguíneo deve estar dentro dos valores permitidos (A+, A-, B+, B-, AB+, AB-, O+, O-).

2) Login de doadores

Como um doador,
Eu quero realizar login no sistema,
Para que eu possa acessar meus dados pessoais e atualizar minhas informações.

Regras de negócio:
- O login deve ser feito com e-mail e senha válidos.
- Caso o e-mail não exista ou a senha esteja incorreta, o sistema deve retornar erro de autenticação.
- O sistema deve gerar um token JWT válido para autenticação das próximas requisições.
- O token expira após determinado período (por exemplo, 24h).

3) Retornar os dados do doador (perfil)

Como um doador autenticado,
Eu quero visualizar meus próprios dados cadastrados,
Para que eu possa confirmar minhas informações.

Regras de negócio:
- Apenas o próprio doador pode acessar suas informações (autorização baseada no token JWT).
- O sistema deve retornar todos os dados do doador, exceto a senha.
- Caso o token seja inválido ou expirado, o acesso deve ser negado.


4) Usuário administrador pré-cadastrado

Como administrador do sistema,
Eu quero que o sistema já venha configurado com um usuário administrador,
Para que eu possa acessar e gerenciar os dados sem precisar criar um cadastro manualmente.

Regras de negócio:
- O sistema deve criar automaticamente um administrador padrão na inicialização (ex: admin@banco.com e senha: admin123).
- O e-mail do administrador deve ser único e imutável.
- A senha deve ser criptografada.
- O administrador não pode ser excluído ou modificado por doadores comuns.

5) Login de administrador

Como administrador,
Eu quero realizar login no sistema,
Para que eu possa acessar as funcionalidades administrativas e gerenciar os doadores.

Regras de negócio:
- O login deve exigir e-mail e senha válidos.
- O sistema deve verificar se o usuário tem permissão de administrador.
- Em caso de falha na autenticação, o sistema deve retornar mensagem de erro apropriada.
- Um token JWT com papel de administrador deve ser gerado após login bem-sucedido.

6) Listar todos os doadores cadastrados

Como administrador,
Eu quero visualizar uma lista de todos os doadores cadastrados,
Para que eu possa acompanhar o banco de doadores ativo no sistema.

Regras de negócio:
- Apenas administradores autenticados podem acessar essa listagem.
- O sistema deve retornar dados básicos de cada doador (ex: nome, tipo sanguíneo, cidade).
- A senha dos doadores nunca deve ser retornada.
- Caso não haja doadores cadastrados, deve retornar uma lista vazia.

7) Listar doadores por tipo sanguíneo

Como administrador,
Eu quero filtrar os doadores por tipo sanguíneo,
Para que eu possa identificar rapidamente quais doadores estão disponíveis para um tipo específico de sangue.

Regras de negócio:
- Apenas administradores autenticados podem realizar a consulta.
- O tipo sanguíneo informado deve estar entre os valores válidos (A+, A-, B+, B-, AB+, AB-, O+, O-).
- Caso não existam doadores do tipo informado, deve retornar uma lista vazia.
- A pesquisa deve ser feita de forma exata (ex: "O+" ≠ "O-").

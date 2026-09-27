# simplitalk-preferencias

Página pública de descadastro do **Simplitalk Campanhas**, servida pelo GitHub Pages
(https://soluply.github.io/simplitalk-preferencias/). Repositório **público**: nada de dado, chave ou token aqui.

- Por que existe: o Supabase não serve HTML no domínio padrão das Edge Functions (vira `text/plain`).
- Como funciona: o link do rodapé do e-mail aponta para a função `campanhas-publico/u/<token>`, que
  redireciona para esta página com `?t=<token>`. A página consulta `/u/<token>/info` e, no clique do botão,
  faz `POST /u/<token>`. Abrir o link não descadastra ninguém: só o botão (a salvo de antivírus que abrem links).
- O botão "cancelar inscrição" do Gmail/Yahoo não passa por aqui: é um POST direto na função (RFC 8058).
- Código do app e da função: repositório privado `soluply/simplitalk-campanhas`.

Mudar o endereço da página (ex.: `preferencias.simplitalk.com.br`): ajustar o secret `CAMPANHAS_PREFS_URL`
das Edge Functions. E-mails já enviados continuam funcionando, porque apontam para a função.

# Fluxo pra rodar

- Fazer clone do projeto
- Executar ele com dotnet run ou dotnet watch


# Requisição pra listar os usuarios (vai dar erro porque não tem token mas roda ela)
curl --location --request GET 'localhost:4000/users' \
--data-raw ''

Resposta vai ser 
{
    "message": "Unauthorized"
}

# Requisição pra rodar no terminal para gerar o teu token
curl --location --request POST 'localhost:4000/users/authenticate' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "thales",
    "password": "thalesthales"
}'

Exemplo da resposta:
```
{
  "id":1,
  "firstName":"Thales",
  "lastName":"Liscano",
  "username":"thales",
  "token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjEiLCJuYmYiOjE2OTQ4MjEyODcsImV4cCI6MTY5NTQyNjA4NywiaWF0IjoxNjk0ODIxMjg3fQ.oaFnlLy0g8HCRoIxRA7hTv-wA7_xvRjLyuPPwdX-DnE"
}
```

# Requisição pra listar os usuarios (nessa precisamos gerar o token, dai copiarmos o valor do do token ali de cima e usamos pra listar)
curl --location --request GET 'localhost:4000/users' \
--header 'Authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjEiLCJuYmYiOjE2OTQ4MjEyODcsImV4cCI6MTY5NTQyNjA4NywiaWF0IjoxNjk0ODIxMjg3fQ.oaFnlLy0g8HCRoIxRA7hTv-wA7_xvRjLyuPPwdX-DnE'
* Lembrar de trocar o valor depois do Authorization: pelo valor do token
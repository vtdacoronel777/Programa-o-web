# Programa-o-web
Atividades 

Tarefa 1: JavaScript e Efeitos Visuais em Páginas Web
1. JavaScript e Manipulação de Estilos (CSS Dinâmico)
O JavaScript é uma linguagem de programação que roda no navegador e permite que as páginas web se tornem interativas e dinâmicas. Ele interage com o DOM (Document Object Model) — uma representação da estrutura HTML da página — permitindo alterar elementos em tempo real.

Por meio do DOM, o JavaScript pode acessar e modificar propriedades CSS de qualquer elemento HTML. Por exemplo:

javascript
Copiar código
document.getElementById("caixa").style.backgroundColor = "blue";
Nesse caso, o fundo da <div id="caixa"> será alterado dinamicamente para azul.

2. Implementação de Animações Simples
JavaScript permite criar animações manipulando propriedades CSS em intervalos regulares, utilizando funções como setInterval() ou requestAnimationFrame(). Exemplo:

javascript
Copiar código
let pos = 0;
const box = document.getElementById("caixa");
function moverCaixa() {
  if (pos < 300) {
    pos++;
    box.style.left = pos + "px";
    requestAnimationFrame(moverCaixa);
  }
}
moverCaixa();
Esse código move uma caixa da esquerda para a direita, alterando dinamicamente a propriedade left.

3. Integração com CSS Transitions e Classes
Outra abordagem é alterar classes CSS com JavaScript para acionar efeitos visuais predefinidos:

javascript
Copiar código
document.getElementById("botao").addEventListener("click", () => {
  document.getElementById("caixa").classList.toggle("animado");
});
Com um CSS como:

css
Copiar código
.animado {
  transition: transform 0.5s;
  transform: scale(1.2);
}
4. Bibliotecas de JavaScript para Efeitos Visuais
Para efeitos mais complexos, como sliders, modais animados, ou parallax scrolling, utilizam-se bibliotecas como:

jQuery: Simplifica a manipulação do DOM e animações.

javascript
Copiar código
$("#caixa").fadeOut();
GSAP (GreenSock Animation Platform): Oferece controle avançado sobre animações com alta performance.

javascript
Copiar código
gsap.to("#caixa", { duration: 1, x: 100, opacity: 0.5 });
Anime.js: Anima propriedades CSS, SVGs e muito mais com facilidade.

Essas bibliotecas oferecem funções prontas que reduzem a complexidade do código e permitem criar interfaces ricas e envolventes.

Atividade 2: Validação de Formulários com JavaScript
1. O Que é Validação de Formulários?
É o processo de verificar se os dados inseridos pelo usuário em um formulário estão corretos antes do envio ao servidor. Isso melhora a experiência do usuário e reduz erros de entrada.

2. Validação no Lado do Cliente com JavaScript
JavaScript pode ser usado para capturar eventos como submit ou input e validar campos. Exemplo básico:

javascript
Copiar código
document.getElementById("form").addEventListener("submit", function(event) {
  const nome = document.getElementById("nome").value;
  if (nome.trim() === "") {
    alert("O campo nome é obrigatório!");
    event.preventDefault(); // Impede envio do formulário
  }
});
3. Uso de Expressões Regulares (Regex)
Expressões Regulares são padrões usados para identificar sequências de caracteres. São úteis para validar formatos específicos, como e-mails, telefones, CPFs, etc.

Exemplo de Regex para validar e-mail:

javascript
Copiar código
const email = document.getElementById("email").value;
const regexEmail = /^[\w.-]+@[a-zA-Z\d.-]+\.[a-zA-Z]{2,}$/;
if (!regexEmail.test(email)) {
  alert("E-mail inválido");
}
Explicação da expressão:

^[\w.-]+ – Início da string com letras, números, underline, ponto ou hífen.

@ – Caractere obrigatório “@”.

[a-zA-Z\d.-]+ – Nome do domínio (letras, números, ponto ou hífen).

\.[a-zA-Z]{2,}$ – TLD como .com, .br, .org, com pelo menos duas letras.

4. Vantagens da Validação com JavaScript
Evita envios desnecessários ao servidor.

Fornece feedback instantâneo ao usuário.

Reduz a carga do servidor.

Importante: A validação no cliente melhora a usabilidade, mas não substitui a validação no servidor por motivos de segurança.

Se quiser, posso criar um exemplo prático completo com formulário, validação e animações. Deseja isso?

Atividade 3: Detalhando a Arquitetura Cliente-Servidor na Web
1. O que é a Arquitetura Cliente-Servidor?
A arquitetura cliente-servidor é um modelo de comunicação em que dois participantes têm papéis distintos:

Cliente: é geralmente um navegador web (como Chrome ou Firefox). Ele faz requisições solicitando recursos, como páginas HTML, imagens, ou dados.

Servidor: é o computador (ou conjunto de computadores) que hospeda o site e responde às requisições enviando os recursos solicitados.

2. Fluxo de Comunicação: Do Navegador ao Servidor
Vamos detalhar passo a passo o que acontece quando você digita um endereço no navegador, como www.exemplo.com.

Passo 1: Resolução de Nome (DNS)
O navegador precisa descobrir o endereço IP do servidor correspondente ao nome www.exemplo.com.

Ele consulta um servidor DNS (Domain Name System), que funciona como uma “agenda telefônica da internet”, convertendo nomes de domínio em endereços IP.

Exemplo: www.exemplo.com → 192.0.2.1

Passo 2: Estabelecendo a Conexão
Com o IP, o navegador se conecta ao servidor usando o protocolo TCP/IP, geralmente pela porta 80 (HTTP) ou 443 (HTTPS).

Se for HTTPS, ocorre um processo de criptografia chamado SSL/TLS handshake.

Passo 3: Envio da Requisição HTTP (Cliente para Servidor)
O navegador envia uma requisição HTTP. Exemplo:

http
Copiar código
GET /index.html HTTP/1.1
Host: www.exemplo.com
User-Agent: Mozilla/5.0
GET: método HTTP indicando que o cliente quer obter dados.

/index.html: o recurso solicitado.

Cabeçalhos HTTP: informações adicionais como navegador usado, idioma aceito etc.

Passo 4: Processamento no Servidor
O servidor recebe a requisição, processa-a e localiza o recurso solicitado.

Se necessário, ele executa scripts (como PHP ou Node.js) para gerar conteúdo dinâmico.

Em seguida, prepara uma resposta HTTP.

Passo 5: Envio da Resposta HTTP (Servidor para Cliente)
O servidor envia algo como:

http
Copiar código
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1024

<html>
  <head><title>Exemplo</title></head>
  <body>Bem-vindo ao site!</body>
</html>
200 OK: código de status indicando sucesso.

Content-Type: indica o tipo de conteúdo (HTML, JSON, imagem, etc).

O corpo da resposta contém o HTML da página.

Passo 6: Renderização da Página (Cliente)
O navegador interpreta o HTML recebido.

Em seguida, faz novas requisições para os recursos referenciados (CSS, JavaScript, imagens).

Cada recurso segue o mesmo ciclo: DNS → Requisição → Resposta.

Resumo dos Conceitos Importantes
Cliente (navegador): envia requisições e exibe o conteúdo recebido.

Servidor: processa requisições e envia as respostas com os recursos da web.

HTTP: protocolo que define como cliente e servidor trocam mensagens.

Requisição HTTP: pedido feito pelo navegador.

Resposta HTTP: resposta enviada pelo servidor com os dados.

DNS: serviço que traduz nomes de domínio em IPs.

Se desejar, posso montar um esquema visual com esse fluxo ou fornecer um exemplo em código para simular uma requisição/resposta. Deseja isso?




























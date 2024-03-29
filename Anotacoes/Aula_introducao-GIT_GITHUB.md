### Sistema de versionamento de código distribuído  → SISTEMA DISTRIBUÍDO SEGURO.

O <strong> Git Bash </strong>é um terminal extendido para otimizar o uso do Git.

GUI x CLI

GUI: Graphical User Interface

CLI: Command Line Interface —> GIT

Windows:

cd, dir, mkdir, del (deleta apenas arquivos) / rmdir (remove todo o diretório), cls

cd \ —> raiz

cd .. —> volta 1 nível

TAB —> função de autocompletar

echo —> printa o que vc digitar

">" —> redirecionador de fluxo, transforma em arquivo (ex. echo hello > hello.txt)

/S = removes all directories and files in the specified directory in addition to the directory itself.

/Q = quiet mode

SHA1:  algoritmo de encriptação. Significa *Secure Hash Algorithm,* e é um conjunto de funções hash criptográficas projetadas pela NSA. Gera um conjunto de caracteres identificadores de 40 dígitos.

Git bash: trocar o tema na barra superior, botão D, options.

**Objetos internos do GIT**

- Blobs
- Trees
- Commits

**Blob** ('bolha'): é um objeto usado para guardar arquivos (guarda o sha1 do arquivo), que contém metadados: tipo do objeto, tamanho do arquivo, "\0", conteúdo de fato do arquivo.

echo 'conteudo' | git hash-object —stdin

echo -e 'blob 9\0conteudo' | openssl sha1

**Trees:** armazenam blobs —> guarda o sha1 e o nome dos arquivos. É um comportamento de diretório com arquivos dentro.

**Commit:** é o objeto que junta tudo. Aponta para árvore, para o parente (o último realizado antes dele), para o autor e para uma mensagem. Explica e dá significado para as pastas, seus arquivos e alterações. Tem timestamp. Também tem sha1 em seus metadados.

**Chaves SSH e Tokens**

- Chave SSH: forma de se estabelecer conexão segura e encriptada entre máquinas.

Para gerar as chaves, tem que ir no GITHUB (settings, SSH e GBG) + Git Bash (comandos a seguir):

ssh-keygen -t ed25519 -c wholopes@gmail.com

Na pasta em que a chave for gerada: cat id_ed25519.pub

copia a chave e cola no github, com uma descrição da máquina

Depois volta no bash e digita:     

eval $(ssh-agent -s)

ssh-add id_ed25519

Para testar: acha um diretório para clonar por SSH e copia o endereço. No Bash:

git clone *cola o endereço*

- Token de acesso pessoal: no github, nos settings → Developer settings → Personal access tokens → generate new token.
    
    Pode ter prazo de expiração. Marcar *repo.* Precisa copiar o token e colar em um arquivo, que deve ser guardado com segurança. Não tem como consultar novamente. 
    
    Neste caso, clona-se copiando o endereço pela opção HTTPS
    
    **Comandos iniciais:**
    
    - git init
    - git add
    - git commit
    
    - **ls -a: lista arquivos ocultos**
        1. dir/a deve **mostrar pastas ocultas**.
        2. dir /a:d mostra todos os diretórios.
        3. dir /a:h mostra todos os **arquivos ocultos**.
    - git config —global [user.email](http://user.email) "wholopes@gmail.com"
    - git config —global [user.name](http://user.name) “Rute”
    
    - git config —list (lista configurações do git)
    
    Para fazer alterações:
    
    - git config —global —unset [user.email](http://user.email) (exemplo de alteração de email)
    
    - git add *
    - git commit -m “commit inicial”
    
- git status
- mv *nomedoarquivo.ext* ./*nomedaPastaDestino/*
- git add *nomedoartquivo.ext pasta/*
- **echo > README.md**

### PARA APONTAR A PASTA LOCAL PARA O GITHUB:

- **git remote add origin https://github.com..... (endereço da pasta no github) (ex** [https://github.com/wholopes/studies.git](https://github.com/wholopes/studies.git))
- git remote -v (lista onde está a origem no github)
- git status

### DEPOIS, PARA ENVIAR OS ARQUIVOS

- git push origin master

### QUANDO MODIFICAR ALGUM ARQUIVO:

- git status
- git add *
- git commit -m “Descreva a modificacao que foi realizada neste commit”
- git push origin master

### SE HOUVER CONFLITO DE VERSÕES, PORQUE NO GITHUB JÁ ESTÁ UMA VERSÃO MAIS ATUAL QUE NA SUA MÁQUINA:

- git pull origin master (vai trazer os arquivos que estão no Github, para que sejam comparados manualmente e consertados em sua última versão, antes de enviar as modificações que eu fiz)
    - <<<<<<< HEAD (indica as modificações que eu fiz)
    - ======= (indica as modificações que já tinham sido feitas por outra pessoa, no arquivo do GITHUB)

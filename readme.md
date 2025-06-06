 1. Instalar o 7-Zip via Scoop
Se ainda não tem o Scoop:

powershell
Copiar
Editar
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
irm get.scoop.sh | iex
Depois instale o 7zip:

powershell
Copiar
Editar
scoop install 7zip
Verifique se o comando 7z está disponível:

powershell
Copiar
Editar
7z
📦 2. Usar o 7-Zip para splitar arquivos maiores que 100MB
Para dividir, por exemplo, o GitKrakenSetup_x64.exe em partes de 90MB:

powershell
Copiar
Editar
7z a -v90m GitKrakenSetup_x64_split.zip GitKrakenSetup_x64.exe
Explicação:
a → adiciona ao arquivo

-v90m → divide em partes de 90 megabytes

GitKrakenSetup_x64_split.zip → nome base do novo arquivo

GitKrakenSetup_x64.exe → o arquivo original a ser dividido

🎯 Resultado:
Você verá algo como:

python
Copiar
Editar
GitKrakenSetup_x64_split.zip.001
GitKrakenSetup_x64_split.zip.002
...
Cada parte com até 90MB, agora possível de versionar no GitHub ou enviar por outras formas.

🔁 Para recompor:
powershell
Copiar
Editar
7z x GitKrakenSetup_x64_split.zip.001
Se quiser gerar como .7z ao invés de .zip (geralmente mais compacto):

powershell
Copiar
Editar
7z a -v90m GitKrakenSetup_x64_split.7z GitKrakenSetup_x64.exe

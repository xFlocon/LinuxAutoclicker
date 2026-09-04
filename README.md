# Linux AutoClicker

![Linux](https://img.shields.io/badge/Linux-Debian%20%7C%20Arch-1793D1?logo=linux&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-x64-0078D4?logo=windows11&logoColor=white)
![Versão](https://img.shields.io/badge/versão-1.0.0-22C55E)

Autoclicker para Linux e Windows com perfis independentes para os botões esquerdo e direito, atalhos globais e velocidade configurável.

## Downloads

| Plataforma | Versão | Requisito | Download |
| --- | --- | --- | --- |
| Linux x86_64 | 1.0.0 | Debian, distribuições derivadas ou Arch Linux | [AppImage](https://github.com/xFlocon/LinuxAutoclicker/releases/download/v1.0.0/LinuxAutoClicker-x86_64.AppImage) |
| Windows x64 | 1.0.0 (sem assinatura digital) | Windows de 64 bits | [EXE](https://github.com/xFlocon/LinuxAutoclicker/releases/download/v1.0.0/LinuxAutoClicker.exe) |

> **Aviso para Windows:** o arquivo `.exe` não possui assinatura digital. Por isso, o Windows e o Microsoft Defender SmartScreen podem exibir um alerta antes da execução, mesmo que o arquivo tenha sido baixado pela release oficial.

## Recursos

- Perfis separados para os botões esquerdo e direito.
- Atalho global configurável para ativar ou desativar cada perfil.
- Autoclick somente enquanto o botão correspondente estiver pressionado.
- Velocidade configurável em cliques por segundo (CPS).
- Indicadores visuais dos estados desligado, armado e clicando.
- Captura de teclas e botões do mouse para configurar os atalhos.
- Configurações salvas dentro do próprio executável.
- Suporte a dispositivos de entrada globais no Linux e no Windows.

## Como usar

1. Abra o programa.
2. Escolha o perfil **Esquerdo** ou **Direito**.
3. Capture a tecla ou o botão que ativará o perfil.
4. Defina a velocidade em cliques por segundo.
5. Ative o autoclick.
6. Mantenha o botão correspondente pressionado para clicar automaticamente.

## Instalação no Linux

O AppImage é compatível com Debian, distribuições derivadas e Arch Linux em computadores x86_64.

### Debian e derivados

O AppImage precisa do utilitário FUSE e da biblioteca de compatibilidade FUSE 2. No Debian estável atual:

```bash
sudo apt update
sudo apt install fuse libfuse2t64
```

Em versões anteriores ou distribuições que ainda forneçam `libfuse2`:

```bash
sudo apt update
sudo apt install fuse libfuse2
```

Instale apenas a biblioteca disponível na sua versão do sistema.

### Arch Linux

Instale o FUSE 2:

```bash
sudo pacman -S fuse2
```

### Executando

```bash
chmod +x LinuxAutoClicker-x86_64.AppImage
./LinuxAutoClicker-x86_64.AppImage
```

Na primeira execução, o programa solicita autorização administrativa para configurar `uinput`, `evdev`, o grupo `input` e as regras de acesso aos dispositivos. Essa configuração permite capturar os botões físicos e emitir os cliques virtuais.

O programa utiliza `pkexec`. Se a configuração automática não iniciar, instale o PolicyKit e as ferramentas necessárias:

```bash
# Debian e derivados
sudo apt install policykit-1 kmod acl udev

# Arch Linux
sudo pacman -S polkit kmod acl
```

Se os dispositivos ainda não aparecerem após a configuração, encerre a sessão e entre novamente para atualizar a associação ao grupo `input`.

## Instalação no Windows

1. Baixe `LinuxAutoClicker.exe` pela release oficial.
2. Confira o SHA-256 antes de abrir o arquivo.
3. Execute o programa e aceite a solicitação de administrador.

> **Aviso:** o executável para Windows ainda não possui certificado digital. O Microsoft Defender SmartScreen pode exibir um alerta de editor desconhecido. Se você baixou o arquivo pela release oficial e confirmou o hash, use **Mais informações** e **Executar assim mesmo**, caso essa opção esteja disponível.

## Configurações

As configurações são anexadas ao próprio AppImage ou EXE. O arquivo precisa continuar com permissão de escrita para que as alterações sejam salvas. Ao mover o executável para outro computador, as configurações salvas acompanham o arquivo.

## Integridade dos arquivos

Os hashes oficiais estão em [`SHA256SUMS`](SHA256SUMS). No Linux, verifique os arquivos com:

```bash
sha256sum -c SHA256SUMS
```

## Privacidade

O autoclicker funciona localmente e não depende de conta ou servidor on-line. No Linux, o acesso a `uinput` e aos dispositivos em `/dev/input` é necessário para capturar os comandos e gerar os cliques.

> Os executáveis são distribuições binárias. O código-fonte não está incluído neste repositório.

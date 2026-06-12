---
title: "No success trying to install AMSN can anyone help me !"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by vitoruk on 2009-05-13
when i tried to install amsn it came up with the following error 
can anyone help me to sort this out 

usuario@usuario-desktop:~$ sudo apt-get install amsn
[sudo] password for usuario: 
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Lendo estado da informação... Pronto
Pacotes sugeridos:
  docker
Os pacotes a seguir serão REMOVIDOS:
  linux-restricted-modules-2.6.27-7-generic
Os NOVOS pacotes a seguir serão instalados:
  amsn
0 pacotes atualizados, 1 pacotes novos instalados, 1 a serem removidos e 1 não atualizados.
1 pacotes não totalmente instalados ou removidos.
É preciso fazer o download de 0B/271kB de arquivos.
Após esta operação, 1335kB de espaço em disco serão liberados.
Quer continuar [S/n]? S
(Lendo banco de dados ... 179580 arquivos e diretórios atualmente instalados.)
Removendo linux-restricted-modules-2.6.27-7-generic ...
rmdir: falha ao remover `/lib/modules/2.6.27-7-generic/volatile/': Arquivo ou diretório inexistente
FATAL: Could not open '/boot/System.map-2.6.27-7-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Cannot find /lib/modules/2.6.27-7-generic
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: erro processando linux-restricted-modules-2.6.27-7-generic (--remove):
 subprocesso post-removal script retornou código de saída de error 1
Erros foram encontrados durante processamento de:
 linux-restricted-modules-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Also i did not manage to install wine came up with the following error 

usuario@usuario-desktop:~$ sudo apt-get install wine
[sudo] password for usuario: 
Lendo lista de pacotes... Pronto
Construindo árvore de dependências       
Lendo estado da informação... Pronto
Alguns pacotes não puderam ser instalados. Isso pode significar que
você solicitou uma situação impossível ou se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram tirados do Incoming.

Já que você solicitou uma única operação é bem provável que o pacote
esteja simplesmente não instalável e um relato de erro sobre esse
pacotes deve ser enviado.
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  wine: Depende: libasound2 (> 1.0.18) mas 1.0.17a-0ubuntu2~hardy1 está para ser instalado

Any help , would be very appreciated this is getting me crazy . 

thank you

---

### Post by skompier on 2009-05-14
Try installing it from Add/Remove. Just do a search for aMSN and see if that works for you.

---


---
title: "Huwaei e220 wireless modem problem"
date: 2008-05-08
forum: Hardware
---

### Post by yeehi on 2008-05-08
I cannot get an internet connection with my e220 on Hardy Heron.

Vodafone software won't work - Python twisted is required.

I tried to install python twisted and its dependencies, in order to get the vodafone software to detect my modem. 

Unfortunately, the package installer crashes every time i try and install the files i downloaded from another computer and saved to a flash drive.

I have just ground to a halt with this problem. What can i do?

---

### Post by fdimmling on 2008-05-08
I just tried the vodafone software in version 2.0beta2. At installation time you need a running internet connection because the installer uses apt-get to fetch the missing packages. There is no need to compile anything from sources. However you have to run the installer with sudo

sudo sh vodafone-mobile-connect-card-driver-for-linux-2.0.beta2-ubuntu-installer.run

and you have to close all instances of synaptic before. The installer places a file with udev rules in /etc/udev/rules.d and you have to restart the computer after installation.

I have installed it on an eeePC running eeeXubuntu which is a Gutsy brand but there is no reason why it should not work with Hardy too, in fact from Vodafone it is explicitely specified for Hardy too.

Try it, it is a nice piece of software. Of course UMTSmon works too, needs no additional packeages but additional udev rules too which you can find in the net.

Good luck

Friedrich

---

### Post by sparttacus on 2008-05-09
Ubuntu 8.04 Gnome
A minha placa é da Kanguru Huawei E220 e foi ligada da seguinte forma:

1.Acede a definições de rede (Sistema->Administração->Rede ou ícone de rede) 
2.Configuração manual
3.Destranca
4.Conecção ponto-a-ponto
5.Propriedades
6.Em Geral
7.Activar esta ligação
8.Tipo de ligação: Modem série
9.Número de telefone : *99#
10.Nome de utilizador: qualquer
11.Senha: qualquer
12.Em Modem
13.Alterar para /dev/ttyUSB0
14.Em definições, podes seleccionar tudo.
15.Ok
Aguardar uns segundos

Espero que tenha ajudado

---


---
title: "AMD/Intel Hybrid Graphics: anything new in Ubuntu 13.10?"
date: 2013-10-18
forum: Hardware
---

### Post by talestomaz on 2013-10-18
Hi friends,

Since long time I try to use proprietary drivers for my AMD/Intel Hybrid Graphics (ATI HD Radeon 6370m) in my notebook (HP dv7 Pavilion) and I've been always unsucessful, no matter the version of my Ubuntu (12.04, 12.10 or 13.04). I've tried already many methods and nothing worked to me.

Do you know if there's something new in Ubuntu 13.10? Any change that could make such graphics finally work?

---

### Post by terebet on 2013-10-25
Yes, there is official support for hybrid graphics. Check [http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

---

### Post by talestomaz on 2013-10-27
> **terebet said:**
> Yes, there is official support for hybrid graphics. Check [http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

Thank you for the tip. That really excited me! But it didn't work for me. I've just installed a fresh version of Ubuntu 13.10, entered the commands "update" and "dist-upgrade" and then the command "sudo apt-get install fglrx fglrx-pxpress", as can be seen below (though it is in portuguese, most things can be understood). Then, after the reboot, it came again to the black screen that says I'm running in low-graphics. I've bolded below where is probably the error. But I don't know how to solve it. If anyone has any idea, I'd be very glad. Thanks in advance!

--


tales@talestomaz:~$ sudo apt-get install fglrx fglrx-pxpress
[sudo] password for tales: 
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Os pacotes extra a seguir serão instalados:
  fglrx-amdcccle lib32gcc1 libc6-i386
Os NOVOS pacotes a seguir serão instalados:
  fglrx fglrx-amdcccle fglrx-pxpress lib32gcc1 libc6-i386
0 pacotes atualizados, 5 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso baixar 92,4 MB de arquivos.
Depois desta operação, 271 MB adicionais de espaço em disco serão usados.
Você quer continuar [S/n]? s
Obter:1 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) saucy/main libc6-i386 amd64 2.17-93ubuntu4 [4.140 kB]
Obter:2 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) saucy/main lib32gcc1 amd64 1:4.8.1-10ubuntu8 [53,5 kB]
Obter:3 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) saucy/restricted fglrx amd64 2:13.101-0ubuntu3 [82,3 MB]
Obter:4 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) saucy/restricted fglrx-amdcccle amd64 2:13.101-0ubuntu3 [5.964 kB]
Obter:5 [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) saucy/main fglrx-pxpress all 0.4 [3.462 B]
Baixados 92,4 MB em 6min 53s (223 kB/s)                                        
A seleccionar pacote anteriormente não seleccionado libc6-i386.
(Lendo banco de dados ... 167269 ficheiros e directórios actualmente instalados.)
Desempacotando libc6-i386 (de .../libc6-i386_2.17-93ubuntu4_amd64.deb) ...
A seleccionar pacote anteriormente não seleccionado lib32gcc1.
Desempacotando lib32gcc1 (de .../lib32gcc1_1%3a4.8.1-10ubuntu8_amd64.deb) ...
A seleccionar pacote anteriormente não seleccionado fglrx.
Desempacotando fglrx (de .../fglrx_2%3a13.101-0ubuntu3_amd64.deb) ...
A seleccionar pacote anteriormente não seleccionado fglrx-amdcccle.
Desempacotando fglrx-amdcccle (de .../fglrx-amdcccle_2%3a13.101-0ubuntu3_amd64.deb) ...
A seleccionar pacote anteriormente não seleccionado fglrx-pxpress.
Desempacotando fglrx-pxpress (de .../fglrx-pxpress_0.4_all.deb) ...
Processando gatilhos para ureadahead ...
Configurando libc6-i386 (2.17-93ubuntu4) ...
Configurando lib32gcc1 (1:4.8.1-10ubuntu8) ...
Configurando fglrx (2:13.101-0ubuntu3) ...
update-alternatives: a usar /usr/lib/fglrx/ld.so.conf para disponibilizar /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) em modo automático
update-alternatives: a usar /usr/lib/fglrx/alt_ld.so.conf para disponibilizar /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) em modo automático
update-initramfs: deferring update (trigger activated)
Loading new fglrx-13.101 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-12-generic
Building for architecture x86_64
Building initial module for 3.11.0-12-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-12-generic/updates/dkms/

depmod......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Configurando fglrx-pxpress (0.4) ...
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:[B]
dpkg: erro: base de dados de estado do dpkg está bloqueado por outro processo (dpkg status database is locked by another process)
dpkg: erro: base de dados de estado do dpkg está bloqueado por outro processo [/B]**(dpkg status database is locked by another process)**

PowerXpress: Discrete GPU is selected (High-Performance mode), please restart Xserver(s) for changes to take effect!
Processando gatilhos para ureadahead ...
Processando gatilhos para bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Configurando fglrx-amdcccle (2:13.101-0ubuntu3) ...
Processando gatilhos para libc-bin ...
Processando gatilhos para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic
tales@talestomaz:~

--

---

### Post by Bashing-om on 2013-10-27
talestomaz; Hi !

This caught my attention, and you may find it of use:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
> 
we have worked to officially support Hybrid graphics in Ubuntu 13.10 and in 12.04.3 LTS.


Which I took to be very promising for those looking for switchable graphics solutions.


[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

### Post by maxikd on 2013-10-27
hey guys,

I was able to install fglrx and fgrlx-pxpress and AMD CCC. this is great, but I can't launch the "administrative" mode, so I can't change from AMD card to Intel card.
does anybody know what can I do?

[IMG]http://img10.imageshack.us/img10/7203/0wrg.png[/IMG]


**Tales**, try to install fglrx first and then you install fglrx-pxpress. and check if both card are on. after that, reboot. it worked here.

thanks, Max

---

### Post by ujjavalkanwar on 2013-10-28
You need to run The AMD Catalyst Control Center as Administrator from the terminal, follow steps [http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/) and you will be able to switch between GPUs better than ever from the AMD control Center itself!

---


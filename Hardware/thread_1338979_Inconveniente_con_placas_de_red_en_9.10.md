---
title: "Inconveniente con placas de red en 9.10"
date: 2009-11-27
forum: Hardware
---

### Post by cartos on 2009-11-27
hola despues de un tiempo pude recuperar la clave del foro como un"b... ya saben que palabra sigue aca" le ponia para recuperar convencido que era con otro mail

bueno vamos al grano


gente me ayudan??? tengo un maquina desktop la maquina de mi primo que venia rengiando a la FDF, se acuerdan?

lo que tiene un pequeño inconventiene no se conecta con el modem de via cable motorola 5101 a internet, lo que le pasa es lo siguiente

con la placa de red on-board no aparese el eth0, cuando le inserto una pci aparece la eth0 y eth1, raro no?, y con la eth0 no enciende pc activiti del modem, pero con la eth1 si, pero o tema siempre aparese la eth0 y la eth1 "desconectado", despues cuando paso al winchous, con las dos placas enlasan con internet lo mas bien,

y tambien intete conectar el modem via usb y tampoco nada siempre aparese desconectado, 

tambien hice las preguntas de rigor mientras me pasaba todo esto

el modem esta prendido? si
el cable coaxil esta bien? si
el cable de red esta bien? si anda con winchous lo mas bien
el calbe usb esta bien? si es el de la impresora de mi casa
le mande un ifconfig no tiene ip
le mande un ping a mi maquina de casa y no hubo respuesta


hable con z37a del tema y el tampoco no sabe por que?

a mi se me agoto mis pocos conocimientos   


gente que hago? 

les paso el lspci y el lsusb?


pd: ya pronto lo voy a meter a mi primo aca... el entiende poco y nada es nuevo y como lo convensi para que cambie el SO no quiero que se vuelva esas feas ventanas viejas.


GRACIAS GENTE!!!! LES MANDO UN SALUDO GRANDE A TODOS.

---

### Post by guillermolisi on 2009-11-27
Anda pasando la salida de esos comandos.

La conexion entre cable modem y PC es via USB o Ethernet ?

---

### Post by cartos on 2009-11-27
> **guillermolisi said:**
> Anda pasando la salida de esos comandos.

La conexion entre cable modem y PC es via USB o Ethernet ?

guille via ethernet



aca esta el lspci

nicolas@nicolas:~$ sudo lspci 
[sudo] password for nicolas:  
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1) 
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01) 


y aca el lsusb

nicolas@nicolas:~$ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0402:5661 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


saludos

---

### Post by guillermolisi on 2009-11-27
No deberias tener problema con esa interface de red, una Intel Pro/100 VE deberia salir funcionando al toque.

Podrias mostrar la salida del comando "lsmod" (sin las comillas) ?
y ya que estamos, el contenido del archivo /etc/network/interfaces tambien ?

---

### Post by cartos on 2009-11-27
nicolas@nicolas:~$ lsmod  
 Module                  Size  Used by  
 binfmt_misc             8356  1  
 joydev                 10272  0  
 psmouse                56180  0  
 hid_drff                3068  0  
 ppdev                   6688  0  
 lp                      8964  0  
 parport_pc             31940  1  
 parport                35340  3 ppdev,lp,parport_pc  
 serio_raw               5280  0  
 ff_memless              5188  1 hid_drff  
 snd_hda_codec_realtek   203328  1  
 snd_hda_intel          26920  2  
 snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               7200  1 snd_hda_codec  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 snd_rawmidi            22208  1 snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 iptable_filter          3100  0  
 snd_timer              22276  2 snd_pcm,snd_seq  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 ip_tables              11692  1 iptable_filter  
 x_tables               16544  1 ip_tables  
 soundcore               7264  1 snd  
 snd_page_alloc          9156  2 snd_hda_intel,snd_pcm  
 usbhid                 38208  1 hid_drff  
 e100                   32452  0  
 mii                     5212  1 e100  
 intel_agp              27484  0  
 agpgart                34988  1 intel_agp  
 nicolas@nicolas:~$  
 

 /etc/network/interfaces



 auto lo
 iface lo inet loopback

---

### Post by guillermolisi on 2009-11-27
El driver esta cargado en memoria (e100                   32452  0) y veo que la administracion de la placa la tiene Network Manager, por lo cual te pido que hagas lo siguiente para ver si sacamos funcionanado la red:

En una consola/terminal escribi ```
sudo nano /etc/network/interfaces
``` (podes usar otro editor de texto, por ej gedit)

y agregale estas lineas
```
auto eth0
 iface eth0 inet dhcp
```Con lo cual el archivo deberia quedarte con este contenido:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Guardas los cambios y ejecutas a continuacion (en consola/terminal)
```
sudo /etc/init.d/networking restart
```Para verificar como anduvo todo, ejecuta "ifconfig" (sin las comillas) y mostra su contenido.

Todo esto con el cable de red que va al cablemodem conectado.

---

### Post by cartos on 2009-11-30
nicolas@nicolas:~$ ifconfig 
eth0      Link encap:Ethernet  direcciÃ³nHW 00:19:d1:4b:72:bb   
          ACTIVO DIFUSIÃ&#8220;N MULTICAST  MTU:1500  MÃ©trica:1 
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:1000  
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
eth0:avahi Link encap:Ethernet  direcciÃ³nHW 00:19:d1:4b:72:bb   
          Direc. inet:169.254.9.12  Difus.:169.254.255.255  MÃ¡sc:255.255.0.0 
          ACTIVO DIFUSIÃ&#8220;N MULTICAST  MTU:1500  MÃ©trica:1 
 
lo        Link encap:Bucle local   
          Direc. inet:127.0.0.1  MÃ¡sc:255.0.0.0 
          DirecciÃ³n inet6: ::1/128 Alcance:AnfitriÃ³n 
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  MÃ©trica:1 
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:0  
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)



guille sigue sin funcionar lo que voy a probar conectarlo con otro modem haber que hace

---

### Post by z37a on 2009-12-01
> **cartos said:**
> 
guille sigue sin funcionar lo que voy a probar conectarlo con otro modem haber que hace

Usando cablemodem no podes cambiar al modem, cada modem tiene su MAC y Fibertel(o cualquiera de Clarin) identifica por la misma, asi que si lo cambias no vas a poder conectarte.

---

### Post by guillermolisi on 2009-12-01
> **z37a said:**
> Usando cablemodem no podes cambiar al modem, cada modem tiene su MAC y Fibertel(o cualquiera de Clarin) identifica por la misma, asi que si lo cambias no vas a poder conectarte.
Salvo que desconecte el cablemodem por un par de minutos y vuelva a conectar todo con la maquina que no esta habitualmente en uso en ese modem. A veces me ha sucedido que esta maniobra funciona, otras directamente usaba la funcion de clonacion de MAC del router que habia en la red (mas rapido).

---

### Post by z37a on 2009-12-01
> **guillermolisi said:**
> Salvo que desconecte el cablemodem por un par de minutos y vuelva a conectar todo con la maquina que no esta habitualmente en uso en ese modem. A veces me ha sucedido que esta maniobra funciona, otras directamente usaba la funcion de clonacion de MAC del router que habia en la red (mas rapido).

El modem tiene una MAC address, aparte de que Fibertel te autentifica con tu placa de red, verifica quien sos con la MAC del modem. Por lo cual no se puede cambiar el modem.

Yo probaria poniendo un router de por medio, viendo a ver si el dhcp del router te entrega ip y podes conectarte.

---

### Post by cartos on 2009-12-01
le dije a mi primo que pruebe llevando la cpu a la casa de un amigo que tiene fiber y que se fije que pasa y tambien si consigue alguien que le preste un router haber si larga alguna ip

asiq eu cuando lo haga les digo el resultado

saludos

---


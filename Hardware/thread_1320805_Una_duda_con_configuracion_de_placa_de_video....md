---
title: "Una duda con configuracion de placa de video..."
date: 2009-11-09
forum: Hardware
---

### Post by -=The_Chacal=- on 2009-11-09
Yo poseo una s3 Graphic ProSavageDDR y necesito configurarla ya que cuando muevo una ventana por el escritorio se ve muy "cortada" y el puntero titila constantemente... Busque y busque en google y lo que encuentro es que es inconfigurable, hasta que encontre esto.

[https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-savage/1:2.3.0-1ubuntu1](https://launchpad.net/ubuntu/karmic/+source/xserver-xorg-video-savage/1:2.3.0-1ubuntu1)

Segun entiendo son drivers, pero no se cual deberia descargarme. 
Ademas me gustaria que me explicaran que es el xserver-xorg o el xorg.conf ya que de esto lei pero no termino de darme cuenta que es (segun entendi, es donde se guarda la configuracion de la placa de video, no?)

PD: Es una pregunta sobre placa de video por lo tanto deberia ir en hard... Pero a la vez necesito saver sobre los drivers, que es soft... Si esta mal posteado, pido disculpas y muevanlo.

---

### Post by guillermolisi on 2009-11-09
Bienvenido.

Si se puede patear, va en Hardware. Si solo lo podes insultar va en Software. SI el tema va mejor con una cafe o cerveza de por medio y esta relacionado con la comunida de SL y/o Ubuntu, va en Comunidad.

Los drivers los consideramos parte del hardware porque por si solos no hacen nada y es software especifico para un dispositivo en particular.

El Xserver es el motor que permite que se pueda trabajar mediante un entorno grafico en los sistemas Unix/Linux. NO es el escritorio grafico, si es su base sin el cual Gnome, KDE o cualquier otro no funcionarian.
Su configuracion, de hacer falta ya que no siempre es necesaria, se guarda en /etc/X11/xorg.conf. Lo que pongas ahi solapara lo que el Xserver entienda deba definir por defecto para tus perifericos (monitor, teclado, mouse, tableta digitalizadora, placa de video, etc.).

Sobre la placa de video y para tener el dato preciso de como es reconocida por Ubuntu, podrias mostrar la salida del comando "lspci" (sin comillas) ejecutado en una consola/terminal ?

A priori te digo que no veo muy auspicioso el tema ya que S3 se basa en chipset VIA y drivers Openchrome que no se llevan para nada bien con Linux.

---

### Post by -=The_Chacal=- on 2009-11-11
> **guillermolisi said:**
> Bienvenido.

**Si se puede patear, va en Hardware. Si solo lo podes insultar va en Software.** SI el tema va mejor con una cafe o cerveza de por medio y esta relacionado con la comunida de SL y/o Ubuntu, va en Comunidad.

Los drivers los consideramos parte del hardware porque por si solos no hacen nada y es software especifico para un dispositivo en particular.

El Xserver es el motor que permite que se pueda trabajar mediante un entorno grafico en los sistemas Unix/Linux. NO es el escritorio grafico, si es su base sin el cual Gnome, KDE o cualquier otro no funcionarian.
Su configuracion, de hacer falta ya que no siempre es necesaria, se guarda en /etc/X11/xorg.conf. Lo que pongas ahi solapara lo que el Xserver entienda deba definir por defecto para tus perifericos (monitor, teclado, mouse, tableta digitalizadora, placa de video, etc.).

Sobre la placa de video y para tener el dato preciso de como es reconocida por Ubuntu, podrias mostrar la salida del comando "lspci" (sin comillas) ejecutado en una consola/terminal ?

A priori te digo que no veo muy auspicioso el tema ya que S3 se basa en chipset VIA y drivers Openchrome que no se llevan para nada bien con Linux.

jaja esa es la mejor definicion sobre hard y soft que escuche en mi vida xD

on: Ok, cuando pueda edito y pongo screen del lspci. Y gracias por sacarme la duda del xserver. Yo por lo que habia leido ya sabia que no iba a poder mover los efectos con esta placa de mier**, pero por lo menos algo que haga que el mouse deje de titilar.

---

### Post by guillermolisi on 2009-11-11
> **-=The_Chacal=- said:**
> jaja esa es la mejor definicion sobre hard y soft que escuche en mi vida xD

on: Ok, cuando pueda edito y pongo screen del lspci. Y gracias por sacarme la duda del xserver. Yo por lo que habia leido ya sabia que no iba a poder mover los efectos con esta placa de mier**, pero por lo menos algo que haga que el mouse deje de titilar.
La autoria de esa definicion tan pragmatica sobre soft y hard la tome de Hei Ku (supongo que tendra su respectiva licencia CC :) )

De paso, fijate las frecuencias de barrido vertical y horizontal que soporta tu monitor ya que posiblemente las necesites para que te quede con buena resolucion y sin efectos raros de video (como el del puntero del mouse).

---

### Post by -=The_Chacal=- on 2009-11-14
Después de haberme tardado mi tiempito me reporto con los datos del lspci

> 00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


Cuando encuentre esos datos del monitor los pongo.

---


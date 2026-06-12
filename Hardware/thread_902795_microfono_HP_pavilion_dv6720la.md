---
title: "microfono HP pavilion dv6720la"
date: 2008-08-27
forum: Hardware
---

### Post by ArgentinoGuy on 2008-08-27
Hola gente,

Antes que nada me presento, mi nombre es Cesar y vivo en Cordoba (no se si habran notado es mi primer post).

Bueno, como el titulo lo indica poseo una notebook HP pavilion dv6720la (es la que se vende con el plan para jubilados de la ANSES), yo asumo que por culpa del "la" es que no doy con la solucion por mas que googlee y googlee :( asi que acudo a la comunidad de mi pais (alquien mas tiene que tener la misma ******* notebook).
Bue, resulta que mis amigos me rompen las que ya saben con el tema del skype, asi que me instale uno, cree una cuenta y me percato del pequeño detalle que no me anda el mic integrado. No es que no me ande solo en el skype, no me anda en ubuntu (en el vista anda, todavia no se porque no formatie esa particion...). La placa de sonido es realtek creo (aunque el ALSA mixer me dice intel HDA).

Bueno si alguien tuvo el mismo problema con alguna notebook similar, por favor me indique como solucionarlo.

desde ya muchas gracias!!!

saludos.

---

### Post by sergiom99 on 2008-08-28
el mio anda bastante mal tambien, gtalk es imposible.
postea la salida del comando lspci a ver que tenes y seguimos buscando.

---

### Post by niko_3100 on 2008-08-28
yo tambien tengo mic en mi compaq v3614 pero no se si anda, con el amsn no probaron? o algun programa propio para probar el microfono habria que probar.

---

### Post by cespinal on 2008-08-28
Lo mismo por aca... tengo un par de meses tratando de encontrarle solucion a esto junto con algunas otras personas del foro (en ingles).. y la verdad es que nada hemos podido hacer al respecto..

---

### Post by ArgentinoGuy on 2008-08-29
Hola gente,

aca les pego la salida pci y la usb

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

eso fue el lspci, ahora les copio el lsusb (la verdad que de toooodooo ese monton de cosas no vi uno que diga tarjeta de sonido)

lsusb

Bus 007 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


bue los que tienen notebooks compaq la solucion va a ser muy similar.

desde ya gracias por los aportes, saludos!

---

### Post by faktorqm on 2008-08-30
che pero ustedes quieren el microfono de la camara web integrada o el del jack? me vuelven loco! son dos distintos. probaron jack control? salu2!

si aparece la placa de sonido...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by sergiom99 on 2008-08-30
sip, esa es tu placa y eso es lo que tenes que buscar "Intel Corporation 82801H"
la mia es conexant.
para buscar por la camara, usa "08ff:2580 AuthenTec"
Suerte

---

### Post by ArgentinoGuy on 2008-09-01
la webcam anduvo de entrada "in the box" nunca tuve que tocar nada, solo me generó conflictos la placa wireless que está andando con ndiswrapper y me falta hacer andar el mic, y microfono me refiero al que viene empotrado en la notebook, al lado de la webcam.
Bueno gracias por sus respuesta, esta noche me fijo que encuentro para esa placa de sonido.

Saludos.

---

### Post by niko_3100 on 2008-09-03
Muchachos probe el microfono de mi v3614 y me lo tomo FUi a grabador de sonido y en Grabar de la entrada puse intMic, prueben.

---

### Post by faktorqm on 2008-09-04
Alguien leyo esto de casualidad? [http://trauko.wordpress.com/2007/12/07/instalacion-webcam-ubuntu-710-en-hp-dv6000-serie/](http://trauko.wordpress.com/2007/12/07/instalacion-webcam-ubuntu-710-en-hp-dv6000-serie/) es viejo y no es para el modelo, pero capaz...

cuando van a control de volumen, editar -> preferencias no les aparece ningun control para manejar el volumen de otro microfono que no sea en realidad el microfono de la placa de sonido? salu2!

---

### Post by ArgentinoGuy on 2008-09-09
hola gente,

Todavia no he podido hacer andar el mic, busqué por todos lados y siempre es que tienen el volumen bajo o algo asi. Yo por otro lado, estoy con todo al maximo y activado eh entrado a alsamixer desde consola, a sonido dentro de preferencias y al control de volumen, en todos lados esta todo "al mango" asi bien criollo, es mas por los parlantes sale un ruido rosa, pero mi voz no sale :(

Ahora... tengo para elegir dos entradas de microfono, una es mic y la otra es front mic. Cual es la que corresponde al microfono embebido? igual es para sacarme la duda, ya probe las dos y ninguna de las dos me funcionó.

Bueno si a alguien se le ocurre algo mas por favor no dude en compartirlo ya que no pienso loguear en windows solo por un microfono jaja.

Bueno como siempre muchas gracias por la molestia que se toman.

Saludos.

PD: si necesitan screenshots de como tengo todo avisen.

---

### Post by ArgentinoGuy on 2008-09-09
Bueno, nuevo status, usando el sound recorder me escucho... pero bastante feo... mucho ruido, mucho chrrchggrs seguro algo esta saturando... cual sera? mic boost o mic front boost? o los dos?

---

### Post by niko_3100 on 2008-09-16
No se cual es, el que ande mejor?? jeje!! una consulta super offtopic, el control remoto de las pavillion anda en ubuntu? con el rythmbox?? estoy a putno de pillarmelo jeje.

---

### Post by sergiom99 on 2008-09-16
con el amarok algunas cosas hace.

---

### Post by niko_3100 on 2008-09-16
amarok?? hem... kde? jaja! y con el rhytmbox? espero escuchar que si, que para poner play, pause, adelantar, atrasar, subir y bajar el volumen lo cumple y estoy chocho...

---

### Post by niko_3100 on 2008-09-16
JAjaja aca lo estoy probando anda mejor en ubuntu que en vista el control remoto, con rhytmbox funciona de 10, los unicos botones que no andan son el de lanzar el reproductor (con el logo de windows) y el de dvd tampoco,pero bueno lo importante para mi es adelantar, pausar, volumenes... una ves que abris el rhytmbox andan todos los botones.... increible... por dios hasta el infrarrojo anda mejor en GNU Linux que en mocosoft...

---

### Post by ArgentinoGuy on 2008-09-20
con el "elisa media player" el control remoto me anda de 10" igual como dicen mas arriba el mismo sistema operativo detecta bien el remoto, puedo poner a dormir la notebook a distancia, no lo uso, pero se que anda bien :D

Ahh!!! y el mic ya esta funcionando, ya puedo hablar con mis amigos en skype desde la notebook :D

saludos!

---

### Post by dhcancelo on 2008-09-22
> **ArgentinoGuy said:**
> con el "elisa media player" el control remoto me anda de 10" igual como dicen mas arriba el mismo sistema operativo detecta bien el remoto, puedo poner a dormir la notebook a distancia, no lo uso, pero se que anda bien :D

Ahh!!! y el mic ya esta funcionando, ya puedo hablar con mis amigos en skype desde la notebook :D

saludos!

Buenas....
¿Como pudiste solucionar lo del mic incorporado? Tengo el mismo problema y aun no di en la tecla... todo lo demas anda joya !!!
Saludos.
Wex.

---

### Post by vk-cdg on 2008-09-22
> **niko_3100 said:**
> JAjaja aca lo estoy probando anda mejor en ubuntu que en vista el control remoto, con rhytmbox funciona de 10, los unicos botones que no andan son el de lanzar el reproductor (con el logo de windows) y el de dvd tampoco,pero bueno lo importante para mi es adelantar, pausar, volumenes... una ves que abris el rhytmbox andan todos los botones.... increible... por dios hasta el infrarrojo anda mejor en GNU Linux que en mocosoft...

> **ArgentinoGuy said:**
> con el "elisa media player" el control remoto me anda de 10" igual como dicen mas arriba el mismo sistema operativo detecta bien el remoto, puedo poner a dormir la notebook a distancia, no lo uso, pero se que anda bien :D

Ahh!!! y el mic ya esta funcionando, ya puedo hablar con mis amigos en skype desde la notebook :D

saludos!


Que notebook tienen?
Marca y modelo! Viene con el control remoto o usan el de otro modelo?

---

### Post by niko_3100 on 2008-09-22
Yo tengo una compaq v3614la, no viene con el control remoto, lo compre en mercadolibre, el original nuevo en bolsita sellada, en realidad es un control remoto infrarrojo porque tambien funcionan los de dell, este que yo tengo es el que viene con cualquier hp pavilion y andubo de una.

---

### Post by vk-cdg on 2008-09-22
Tendré que probarlo con la mia, pero no se si tiene el hard para captar señales infrarojas.
Veremos, creo que tengo alguien a quien pedirle uno prestado.

---

### Post by niko_3100 on 2008-09-22
Pera yo te digo que notebook tenes? si tenes modelos compaq f7xx o c7xx o f5xx ya te digo que no tienen infrarrojos.

---

### Post by ArgentinoGuy on 2008-09-22
dhcancelo,

lo arregle agregando esta linea de codigo
#

    *
          o Add following line to /etc/modprobe.d/alsa-base and reboot.
                 "options snd-hda-intel model=laptop" 
en donde dice laptop pone "hp", lo que si, con el sound recorder siempre me escucho con mucho ruido, pero mis amigos me dicen por skype que se escucha barbaro.
espero lo soluciones loco!

saludos.

---

### Post by dhcancelo on 2008-09-23
> **ArgentinoGuy said:**
> dhcancelo,

lo arregle agregando esta linea de codigo
#

    *
          o Add following line to /etc/modprobe.d/alsa-base and reboot.
                 "options snd-hda-intel model=laptop" 
en donde dice laptop pone "hp", lo que si, con el sound recorder siempre me escucho con mucho ruido, pero mis amigos me dicen por skype que se escucha barbaro.
espero lo soluciones loco!

saludos.

OK. Muchas gracias.
Hoy mismo al llegar a casa lo pruebo.
Gracias por la respuesta!!!!

---

### Post by dhcancelo on 2008-09-27
> **ArgentinoGuy said:**
> dhcancelo,

lo arregle agregando esta linea de codigo
#

    *
          o Add following line to /etc/modprobe.d/alsa-base and reboot.
                 "options snd-hda-intel model=laptop" 
en donde dice laptop pone "hp", lo que si, con el sound recorder siempre me escucho con mucho ruido, pero mis amigos me dicen por skype que se escucha barbaro.
espero lo soluciones loco!

saludos.

Al final no pude solucionar el problema del mic incorporado, pero creo que el problema esta en la linea de codigo que agregue ya que mi lspci me tira esto: 00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
Un mic conectado en el frente si anda, probe con el grabador de sonido y por mas que ponga mic externo o mic interno, el mic anda, pero si lo desconecto y pruebo con el mic incorporado (de al lado de la webcam) no pasa nada.....
Googleando no pude dar con la solucion... tenes alguna idea?
Muchas gracias.
Wex

---

### Post by ArgentinoGuy on 2008-10-02
La verdad que ni probe con un microfono externo, pero me resulta totalmente extraño una placa de sonido nvidia... que yo sepa solo se dedican al video

---

### Post by faktorqm on 2008-10-03
hacen chipsets tambien...

---

### Post by sozza on 2009-07-21
Perdon, fuera del tema del microfono de la pavilion! Lei en este post que el control remoto de las paviliion funciona en la compaq V3614LA, pues tengo una hace mas de un anio, y aca al lado mio un contro de pavilion, pero no funciona, no se como hacer para que el debian lo reconozca...

Alguna pista?

salu2
Leandro

---

### Post by guillermolisi on 2009-07-21
Este thread versa sobre el microfono de esa maquina.

Si tu consulta es sobre otro componente, sea del mismo equipo o de otro , por favor abri otro thread (despues de buscar si alguien ya trato el tema con anterioridad) y plantea tu consulta.

Te recuerdo que este foro es sobre temas relacionados con Ubuntu. Debian tiene el suyo al igual que una buena parte de las demas distribuciones.

---


---
title: "Internet SUPER lento en Ubuntu"
date: 2010-06-28
forum: Hardware
---

### Post by Karmaloco on 2010-06-28
Saludos!
Les cuento que en mi PC tengo instalado XP y Ubuntu 10.04LTS (el xp lo necesito para trabajar, sino lo borraría! ;) y sucede que internet es MUY lento en Ubuntu, cosa que no pasa cuando arranco en XP.
Supuse desde el principio que podía ser problema del router o del módem, pero lo descarté desde el momento en que en XP funciona bien y que en la PC de mi mujer también funciona bien.

El módem es un Linksys WRT54g2, el ISP es Arnet y el módem es HUAWEII smartax 880a.
La PC la tengo conectada al router via wireless, con un USB de la marca TP-LINK, modelo TL-WN321G.

Busqué en el foro, busqué en la pagina de TP LINK y lo único que encontré es que aparentemente hay drivers para LINUX, los cuales descargue, pero no tienen ningún instalador (o quizás, como soy un usuario básico de Ubuntu, no lo encuentro).

Probé haciendo ping en google.com y tarda un montón, pero no pierdo ningún paquete.

Les paso lo que me aparece haciendo LSPCI en el terminal por si les sirve de algo.

[COLOR="Blue"]leo@leo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600GT] (rev a1)
02:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
[/COLOR]

Agrego info:
leo@leo-desktop:~$ lsusb
Bus 008 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Despues de investigar un poco, busqué a través del chip del usb, y encontré que había gente que con el ndisgtk cargaba el driver de xp que siempre le anduvo, así que bajé el driver, bajé el ndisgtk, instalé, reinicié, y nada... reconoce las redes inalambricas, puedo acceder al router via wireless muy rapidamente, pero cuando abro cualquier pagina web, tarda un montón...

Esta es la configuración de la tarjeta de red

leo@leo-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


Gracias por leer el post, y espero que me den una mano.

Saludos!

Karma

---

### Post by Karmaloco on 2010-06-30
> **Karmaloco said:**
> Saludos!
Les cuento que en mi PC tengo instalado XP y Ubuntu 10.04LTS (el xp lo necesito para trabajar, sino lo borraría! ;) y sucede que internet es MUY lento en Ubuntu, cosa que no pasa cuando arranco en XP.
Supuse desde el principio que podía ser problema del router o del módem, pero lo descarté desde el momento en que en XP funciona bien y que en la PC de mi mujer también funciona bien.

El módem es un Linksys WRT54g2, el ISP es Arnet y el módem es HUAWEII smartax 880a.
La PC la tengo conectada al router via wireless, con un USB de la marca TP-LINK, modelo TL-WN321G.

Busqué en el foro, busqué en la pagina de TP LINK y lo único que encontré es que aparentemente hay drivers para LINUX, los cuales descargue, pero no tienen ningún instalador (o quizás, como soy un usuario básico de Ubuntu, no lo encuentro).

Probé haciendo ping en google.com y tarda un montón, pero no pierdo ningún paquete.

Les paso lo que me aparece haciendo LSPCI en el terminal por si les sirve de algo.

[COLOR="Blue"]leo@leo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600GT] (rev a1)
02:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
[/COLOR]

Agrego info:
leo@leo-desktop:~$ lsusb
Bus 008 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Despues de investigar un poco, busqué a través del chip del usb, y encontré que había gente que con el ndisgtk cargaba el driver de xp que siempre le anduvo, así que bajé el driver, bajé el ndisgtk, instalé, reinicié, y nada... reconoce las redes inalambricas, puedo acceder al router via wireless muy rapidamente, pero cuando abro cualquier pagina web, tarda un montón...

Esta es la configuración de la tarjeta de red

leo@leo-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


Gracias por leer el post, y espero que me den una mano.

Saludos!

Karma

Les quería comentar a todos que, después de buscar en foros, y de culpar al ISP, al router, al modem, al usb wireless, intenté con otro navegador, así que probé usar Chrome en lugar de Firefox.

El problema de la lentitud al navegar en internet simplemente DESAPARECIO, así que asumo que será algún problema de firefox con mi placa o con mi pc.

Supongo que este problema ya está solucionado, así que pido a los moderadores si lo pueden dar por terminado.

Gracias

---

### Post by Tuexnovia on 2011-03-22
Bueno después de haberme tirado 3 días desde que instale Ubuntu y sin poder arreglar el problema de super lentitud con Internet, voy a desistir... Y mis poquita razones son...

-No se ni editar un archivo.

-Me dicen pon esto en la consola pero me vuelvo loko, (Lo que hago es copiar y pegar)

-Tengo v-sinc en las peliculas jajajjaa esto es lo ultimo xD (Supongo que con otro reproductor se arreglaría pero es para reír)

-Instalo un programa y no tengo forma de encontrarlo bien hay miles de paquetes, super perdido por que soy un NOOB.

-Me pongo a ver un video en youtube y va a tirones... Aun ASÍ CARGADO (Flash? no lo se la verdad)


- Soy un puro NOOB, que quizás si lee mas me guste con el tiempo.


Gracias...


PD: Logre desactivar IPV6 no se como pero sigue igual de lente. Intente editar un archivo y no pude, otro archivo llamado elises estaba vació etc...

---


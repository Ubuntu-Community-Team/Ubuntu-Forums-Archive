---
title: "Kubuntu 9.04 me va lento"
date: 2009-06-01
forum: Hardware
---

### Post by ezesapo on 2009-06-01
Decidi hace un mes pasarme a Kubuntu y resulta que me va demasiado lento.

Tengo una notebook DELL Inspiron 1520, Intel Centrino Duo 1.2 GHz, 2 GB de RAM.

No es LA maquina, pero creo que deberia irme un poco mas rapido.

El tema es que no son fluidos los movimiento. O son lentos, o cuando apreto algun boton, tarda en reaccionar.

Para que se den una idea de lo grave que es, Windows Vista me funciona mas rapido!! (y me pase a Ubuntu porque no me bancaba mas Windows Vista).

Bueno, eso, antes con Ubuntu no tenia ningun problema, iba rapidisimo.
Supongo que es algun problema de configuracion de ALGO.
No se si el Xorg o que cosa, pero espero que sea eso porque KDE la verdad que me esta gustando mucho.

Si a alguien le paso o tiene idea que puede ser o me puede tirar algo para probar, les estare agradecido!!

---

### Post by josecuervo86 on 2009-06-01
Podrias poner el resultado de lspci en la terminal?

---

### Post by ezesapo on 2009-06-01
> **josecuervo86 said:**
> Podrias poner el resultado de lspci en la terminal?

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                                  
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)                                                 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)                                                        
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by guillermolisi on 2009-06-01
> **ezesapo said:**
> Decidi hace un mes pasarme a Kubuntu y resulta que me va demasiado lento.

Tengo una notebook DELL Inspiron 1520, Intel Centrino Duo 1.2 GHz, 2 GB de RAM.

No es LA maquina, pero creo que deberia irme un poco mas rapido.

El tema es que no son fluidos los movimiento. O son lentos, o cuando apreto algun boton, tarda en reaccionar.

Para que se den una idea de lo grave que es, Windows Vista me funciona mas rapido!! (y me pase a Ubuntu porque no me bancaba mas Windows Vista).

Bueno, eso, antes con Ubuntu no tenia ningun problema, iba rapidisimo.
Supongo que es algun problema de configuracion de ALGO.
No se si el Xorg o que cosa, pero espero que sea eso porque KDE la verdad que me esta gustando mucho.

Si a alguien le paso o tiene idea que puede ser o me puede tirar algo para probar, les estare agradecido!!
Que version de Kubuntu instalaste ?

---

### Post by ezesapo on 2009-06-01
Tengo instalado Kubuntu Jaunty Jackalope.

---

### Post by guillermolisi on 2009-06-01
[Dale una leida a este thread]("http://ubuntuforums.org/showthread.php?t=1130135") que parece ser un caso de exito con la misma placa de video que la de tu maquina.

---

### Post by ezesapo on 2009-06-01
> **guillermolisi said:**
> [Dale una leida a este thread]("http://ubuntuforums.org/showthread.php?t=1130135") que parece ser un caso de exito con la misma placa de video que la de tu maquina.

Esto me habia funcionado cuando instale Ubuntu 9.04.

Pero ahora que me pase a Kubuntu 9.04, no uso compiz, uso los efectos de KDE, que funcionan bien, solo que son lentos. (igual probe, pero no me funciono :()

Cuando me muevo entre ventanas tardan en aparecer y dibujarse.
Cosas asi, como una maquina con poca RAM, algo asi.

Todo es como poco fluido..

---

### Post by guillermolisi on 2009-06-01
> **ezesapo said:**
> Esto me habia funcionado cuando instale Ubuntu 9.04.

Pero ahora que me pase a Kubuntu 9.04, no uso compiz, uso los efectos de KDE, que funcionan bien, solo que son lentos. (igual probe, pero no me funciono :()

Cuando me muevo entre ventanas tardan en aparecer y dibujarse.
Cosas asi, como una maquina con poca RAM, algo asi.

Todo es como poco fluido..
Y por casualidad [leiste este otro]("http://phyx.wordpress.com/2009/05/30/como-regresar-al-driver-2-4-de-intel-jauntyxorg/") ? Es para usar el driver anterior, el que venia con Intrepid.

---

### Post by Hei Ku on 2009-06-01
Que pasa si desactivas los efectos? anda bien?

---

### Post by ezesapo on 2009-06-01
Si voy a Preferencias del sistema - Escritorio y saco el check a 'Habilitar los efectos de escritorio', la verdad es que mejora mucho. No me parece wooo que rapido, pero mucho mejor, a costa de q se vea un poco mas feo (los efectitos estan weeeenos =P ).

Ahora tambien estoy probando que pasa si uso XRender en lugar de OpenGL (no tengo idea de cual es la diferencia).

---

### Post by Hei Ku on 2009-06-01
Es el motor de rendering, y creo haber escuchado que en algunos casos mejora la performance. Por alguna razon, las Intel tienen bastantes problemas ultimamente, pero seguramente se iran arreglando.

---

### Post by leonardomdq on 2009-06-02
Yo tengo la misma placa en mo HP Pavilion (la peor compra que me mande) y solucione quitando de la black list el driver intel, tengo activados los efectos de escritorio y la aceleradora 3D ahora va bien. Esa fue la mejor solucion que me funciono hasta el momento.

---


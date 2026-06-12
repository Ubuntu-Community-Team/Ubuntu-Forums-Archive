---
title: "Problemas con red y ubuntu 9.04"
date: 2009-08-17
forum: Hardware
---

### Post by CristianCarle on 2009-08-17
Hola soy nuevo en esto y ayer instale por primera vez el ubuntu 9.04,me aparece el icono de red sobre el menu superior pero si el hago un click derecho me aparece editar conexiones pero con el izquierdo me aparece atenuado "no hoy conexiones de red disponibles" o algo asi es una netbook u1005 no se como saber si detecto las placas yo fui a sistema donde me hace un informe y cuando busca las placas me detecta las dos placas pero cuando edito en la wifi
le pongo el SSID despues cargo el mac 
no tengo seguridad
y en IPv4 le pongo servidor dhcp  no se que tengo que poner en id del servidor DHCP pero no conecta 
yo particione el disco y ahora estoy con windows porque no conecta ni con cable ni wifi
si alguien me puede ayudad.
gracias a todos.

---

### Post by guillermolisi on 2009-08-17
Mostranos las salidas de los comandos "lspci" y "lsusb" corridos en una consola/terminal (sin las comillas).
De paso, tambien el contenido del archivo /etc/network/interfaces.

---

### Post by CristianCarle on 2009-08-17
esto esta en interface
 
auto lo
iface lo inet loopback
 
 
 
esto cuando pongo lspci
 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
 
 
espero que me puedas ayudar
gracias

---


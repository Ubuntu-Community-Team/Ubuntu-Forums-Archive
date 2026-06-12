---
title: "Problemas con acer 5315 2608 con wifi"
date: 2009-03-14
forum: Hardware
---

### Post by dmela2012 on 2009-03-14
Hola, me costo llegar hasta acá, es la primera vez que usu ubuntu, recién ahora me doy cuenta que lo que dan para poner era en el terminal, era para mi totalmente desconocido. hice esto y tuve wifi:

En una terminal (Aplicaciones > Accesorios > Terminal) ejecutá
Code:

sudo aptitude install linux-backports-modules-intrepid

Te va a pedir tu contraseña y va a instalar una serie de drivers. Luego vas a Sistema > Administración > Controladores de Hardware, y deshabilitás los drivers de wifi que estén habilitados y habilitás el que tiene el nombre "Support for 5xxx series of Atheros 802.1 wireless LAN cards". Reiniciás y el wifi va a funcionar.

despues actualice todo el equipo, y ahora no tengo mas, tengo instalado el "Support for 5xxx series of Atheros 802.1 wireless LAN card cuando voy a controladores de hardware, pero me dice que esta instalado pero que no esta en uso, y no me funca, ahora con cable si me funciona, cuando lo instale tampoco pero un problema del cable. muchas gracias, y a pesar de estos problemas me gusta mucho, de paso les pido que me recomienden de donde puedo bajar algunos themes buenos, y que cosas recomiendan para ubuntu. muchas gracias.

---

### Post by luks911 on 2009-03-14
Ejecutá en una terminal

```
sudo lshw -C Network
```

y pegá el resultado acá. Eso va a mostrar, entre otras cosas, cuál es el driver que está tratando de usar.

---

### Post by dmela2012 on 2009-03-14
muchas gracias, pego el resultado

daniel@danielnote:~$ sudo lshw -C Network
[sudo] password for daniel: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:e2:a4:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.1.102 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:97:e6:b6:3c:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
daniel@danielnote:~$ 

estuve tratando de seguir el post que daba instrucciones para instalar el madwifi, pero cuando llegue a la parte de descargar, no funciona el link. el post esta aca en esta pagina, pero ahora no funciona. y lo del led dice actualizar un archivo pero no tengo idea como se hace eso.

---

### Post by luks911 on 2009-03-14
Probá con hacer esto en una terminal
```
sudo modprobe ath5k
```
es para cargar el módulo/driver del wifi. Si funciona, vas a hacer que ese módulo se cargue en cada inicio, con:
```
sudo gedit /etc/modules
```
eso te abre un archivo de texto al que al final le agregás una línea que diga
```
ath5k
``` y lo guardás. Avisá si saltá algún error.

Ahora, si te le animás al madwifi (los tutoriales que hay por acá están muy bien), el enlace para bajarlo es
```
http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3942-20090205.tar.gz
```
pasó que hace unos meses los movieron y los tutoriales quedaron desactualizados.

---

### Post by dmela2012 on 2009-03-14
cuando hice el paso de agregar algo a lo ultimo me salio esto, te lo paso porque no se si esta bien porque aparece el ndiswrapper, ahora sigo haciendo lo demas y te digo. muchas gracias, la verdad que mil gracias.


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
ndiswrapper

---

### Post by luks911 on 2009-03-14
Sí, la verdad es que esas líneas que dicen ndiswrapper no deberían estar. Si querés borralas, sólo ésas, agregá la que te decía. Y si funcionó el wifi cuando cargaste el módulo, listo.

---


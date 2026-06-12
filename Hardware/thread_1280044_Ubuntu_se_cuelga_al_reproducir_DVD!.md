---
title: "Ubuntu se cuelga al reproducir DVD!"
date: 2009-10-01
forum: Hardware
---

### Post by el_eternauta on 2009-10-01
Hola gente, cómo están? Yo con el siguiente problema: Mi Ubuntu Jaunty se cuelga al intentar reproducir DVD, ya sea desde HD o disco. Abro el programa (VLC, MPlayer, etc) y cuando le doy abrir DVD se cuelga el sistema no dejándome más opción que resetear. Copié la película al HD por si era problema de lectora pero sigue igual. Es una instalación nueva por eso no entiendo que pasa, instalé todos los códecs siguiendo esta guía "[http://tecnicos.escenf.unam.edu.ar/ubuntu/579.html]("http://tecnicos.escenf.unam.edu.ar/ubuntu/579.html")" y me sigue pasando. He llegado a pensar que es problema de Hardware. 

La máquina es de un amigo y tiene estas especificaciones: 

Processor: Intel(R) Celeron(R) CPU 2.26GHz
Memory: 2061MB 
Placa video:	GeForce 6200/AGP/SSE2
Audio Adapter: VIA8237 - VIA 8237
Motherboard: ASRock P4VM800

Espero les alcanze esto y puedan darme una mano. Saludos y muchas gracias por su tiempo desde ya!

---

### Post by pablo.s on 2009-10-01
Ahí veo un problema de video:
Los drivers de NVidia son los
propietarios?

---

### Post by luks911 on 2009-10-01
Probá de ejecutar el programa en una terminal, por ejemplo
```
mplayer
```
y tratar de reproducir el DVD para ver si enla terminal te devuelve algún error.

---

### Post by filtro_tuc on 2009-10-13
Hola, yo tengo el mismo problema desde hace un mes aproximadamente.
Esto ocurrio despues de alguna de las actualizaciones (no se cual).
Tengo Ubuntu 9.04 corriendo en una HP pavilion a1700n.
Cuando quiero montar el cd o dvd se congela la pc y tengo que resetear.

mi fstab es el siguiente

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=3ccb612c-9d30-467a-9de4-5aea151c8075 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=9be8cad7-f39f-4063-b8fb-ce2f6f96fcad /home           ext3    relatime        0       2
# /dev/sda1
# UUID=9f23c71b-3844-45ca-a6c0-a77170dfef3f /home/goliver/Documents ext3    relatime        0       2
# /dev/sdc1
UUID=f1e3d2f5-c50a-4247-8514-53b5f7ac58d8 /home/goliver/Media ext3    relatime        0       2
# /dev/sdb5
UUID=3eb27954-345e-4314-ac71-631214d156b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Virtualbox
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0


sudo ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2008-05-07 20:42 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-05-07 20:42 cdrom0

sudo lshw

*-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi5
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
        *-cdrom
             description: DVD-RAM writer
             product: CD/DVDW TS-H652L
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0603
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

Ya hice la prueba de cambiar la grabadora por otra de otra marca y tengo el mismo problema.

Espero me puedan ayudar
Gracias

---

### Post by mama21mama on 2009-10-14
primero a [instalar los últimos driver propietarios estables de nvidia]("http://mamalibre.eshost.com.ar/?q=node/30"), [ luego los codec]("http://mamalibre.eshost.com.ar/?q=content/codec-para-ubuntu").

El que tengo yo en mi jaunty es v 185.18.36

---

### Post by filtro_tuc on 2009-10-14
Pero la placa de video que tengo funciona bien, me parece que el tema viene por la controladora IDE.
Ademas en el repositorio no esta esa version. Tengo que bajarla de nvidia?

---

### Post by mama21mama on 2009-10-14
Si. Para tener los driver ultimos debes bajarlos de nvidia... siempre estan adelantados y con las mejoras en los bugs.

Yo de mi parte siempre, siempre uso los ultimos estables de la web de nvidia.

---

### Post by filtro_tuc on 2009-10-19
Los drivers de la nvidia no tienen nada que ver con el tema.
Encontre googleando que hay que cambiar el orden de los parametros del archiv fstab como figura a continuacion

/dev/scd0       /media/cdrom0	**iso9660,udf** user,noauto,exec,utf8 0       0
/dev/sr0       /media/cdrom0	**iso9660,udf** user,noauto,exec,utf8 0       0

lo que esta resaltado es lo que cambia de posicion.
Asi empezo a funcionar con los DVD y algunos CD
No comprendo todavia por que no funciona con todos los CD de musica.

Sigo investigando

aqui esta el link de donde saque la info

[http://ubuntuforums.org/archive/index.php/t-1135452.html]("http://ubuntuforums.org/archive/index.php/t-1135452.html")

---


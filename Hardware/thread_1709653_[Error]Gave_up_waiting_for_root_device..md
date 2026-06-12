---
title: "[Error]Gave up waiting for root device."
date: 2011-03-18
forum: Hardware
---

### Post by Celswolf on 2011-03-18
El problema se aplica a muchos diestro y versiones de cada uno. Pero me voy a centrar en la instalacion de Ubuntu 9.10.

En la parte de la instalacion el problema radica en que no reconoce ningun disco duro. Llega al 4 paso y no muestra ninguna particion/disco duro la pantalla de elección no muestra nada, NADA . En el Gparted el resultado es el mismo salvo que si conecto un USB si me lo reconoce.

Ese problema lo solucione haciendo **F6** en el menu de instalcion del CD y agregar la linea **pci=nomsi.**
Y me deja instalar el SO aparentemente.

Ahora reinicio el sistema, me aparece el logo color blanco de ubuntu, se pone la pantalla en negro, y espero pero nada sucede. Hasta que toco un tecla y me aparece el siguiente error:

> Gave up waiting for root device. Common problems: 
-Boot args (cat/proc/cmdline) 
-Check rootdelay = (did the system wait long enough?) 
-Check root = (did the system wait for the right device?) 
-Missing modules (cat/proc/modules; ls/dev) 
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXX does not exist. Dropping to a shell! 

BussyBox v1,13,3 (Ubuntu 1:1.13.3-1 ubunut 11) built-in shell (ash) 

Intente entrar de forma normal, también de la modo de recuperación y el resultado es el mismo.

Este es mi equipo:
> 
_Tipo de CPU_ AMD Athlon 64, 2200 MHz (11 x 200) 3500+
_Nombre del motherboard_ Asus A8V-X (3 PCI, 2 PCI-E x1, 1 AGP, 4 DDR DIMM, Audio, LAN)
_Chipset del motherboard_ VIA K8T800Pro, AMD Hammer
_Memoria del sistema_ 1024 MB (PC2100 DDR SDRAM)
_Placa de video_ NVIDIA GeForce2 MX/MX 400 (Microsoft Corporation) (64 MB)
_Disco rígido_ HDT722516DLA380 (160 GB, 7200 RPM, SATA-II)

Info extra:
1] El bios no reconoce el disco rigido si no esta configurado como SATA
2] Estoy instalando desde un disco completamente formateado.
3] Entro con el LiveCD para ver el grub y resulta QUE EL GRUB ESTA VACIO, no tiene nada escrito.

---


---
title: "Grub a dejado de iniciar windows"
date: 2009-08-23
forum: Instalación y Actualización
---

### Post by ense on 2009-08-23
Hola amigos, soy nuevo en este foro, y con ubuntu también llevo poco tiempo, para ser más exacto hace un año que instale ubuntu con windows xp, tuve que modificar el menu.lst, pero me funcionaban ambos perfectamente, bueno voy a por el problema.

Hace una semana más o menos, ubuntu 8.10 me pidió reiniciar después de una actualización (llevaba un tiempo sin utilizarlo) y desde entonces no me arranca windows. Concretamente me aparece esto:
```

Startig up ...

Error de disco
Prersione una tecla

```He probado montones de configuraciones distintas de grub, he actualizado el ubuntu a la vs 9.04 - Jaunty Jackalope (es la que utilizo actualmente), desistalé el grub desde el supergrub disk y windows me arranca perfectamente, incluso he intentado utilizar el boot.ini de windows para tener los dos sistemas, pero no me ha funcionado nada, al volver a instalar grub sucede lo mismo.

El fdisk -l me dice lo siguiente:
```

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x503e503d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disco /dev/sdb: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf829f829

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        7296    58605088+   7  HPFS/NTFS
/dev/sdb2            7297       14409    57135172+  83  Linux
/dev/sdb3           14410       14593     1477980    5  Extendida
/dev/sdb5           14410       14593     1477948+  82  Linux swap / Solaris

Disco /dev/sdc: 8074 MB, 8074035200 bytes
39 cabezas, 31 sectores/pista, 13043 cilindros
Unidades = cilindros de 1209 * 512 = 619008 bytes
Identificador de disco: 0x04030201

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           2       13044     7883772    b  W95 FAT32

```Y el menu.lst de grub lo tengo actualmente así:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=dbb67e0b-4c66-41ef-b032-5c8a4adefe00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dbb67e0b-4c66-41ef-b032-5c8a4adefe00

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        dbb67e0b-4c66-41ef-b032-5c8a4adefe00
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=dbb67e0b-4c66-41ef-b032-5c8a4adefe00 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        dbb67e0b-4c66-41ef-b032-5c8a4adefe00
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=dbb67e0b-4c66-41ef-b032-5c8a4adefe00 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
uuid        dbb67e0b-4c66-41ef-b032-5c8a4adefe00
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=dbb67e0b-4c66-41ef-b032-5c8a4adefe00 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid        dbb67e0b-4c66-41ef-b032-5c8a4adefe00
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=dbb67e0b-4c66-41ef-b032-5c8a4adefe00 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, memtest86+
uuid        dbb67e0b-4c66-41ef-b032-5c8a4adefe00
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
root        (hd1,0)
map (hd1,0) (hd0,0)
map (hd0,0) (hd1,0)
makeactive
chainloader    +1

```También cabe mencionar que sdb1 (C: en windows) es donde está instalado windows y sda1 (D: ) es donde guardo mis archivos.

Bueno creo que esto es todo, gracias por vuestro tiempo.

Enrique

---

### Post by Carlos C on 2009-08-23
Hola. Bueno, antes de cualquier cambio lo mejor es respaldar:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```Ahora, tengo mis dudas respecto a dónde tienes el sector boot. Por favor escribe en el terminal:
```
df /boot
```y copia acá lo que te aparezca.
En vista de que tienes más de un disco sería bueno saber cómo identifica GRUB tus discos. Por favor escribe en el terminal:
```
cat /boot/grub/device.map
```y dinos lo que te sale.
Me parece extraño esto:
> title        Microsoft Windows XP Professional
root        (hd1,0)
map (hd1,0) (hd0,0)
map (hd0,0) (hd1,0)
makeactive
chainloader    +1Creo que bastaría con tener:
```
title        Microsoft Windows XP Home Edition
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1
```Pero no soy un experto, así que la copia de seguridad aquí es importante ;).

---

### Post by ense on 2009-08-24
Gracias Carlos por responder tan rápido, he configurado el menu.lst como me has aconsejado, pero continua el mismo problema, hay te pongo lo que me has pedido:

df /boot:
```

S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sdb2             56238496   5242860  48138880  10% /

```
cat /boot/grub/device.map:
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```

---

### Post by Carlos C on 2009-08-24
Al parecer Grub está instalado en el disco correcto y la identificación de la partición de windows corresponde. Te sugiero revises la integridad de la partición NTFS. En este post:

[http://ubuntuforums.org/showthread.php?t=1246680](http://ubuntuforums.org/showthread.php?t=1246680)

gmunioz recomienda instalar el paquete ntfsprogs:

> tools for doing neat things in NTFS partitions from Linux

The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
support for the NTFS filesystem to the Linux operating system.

This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.Tal y como dice gmunioz lo que debiera servirte es ntfsfix.
Si tienes dudas sobre cómo usarlo te recomiendo que, una vez instalado el paquete, leas el manual escribiendo en el terminal "man ntfsfix".
Saludos.

---

### Post by ense on 2009-08-31
Gracias Carlos, perdona que no halla respondido antes, he estado muy liado ](*,), ya había probado que el disco no tuviera errores, con scandisk desde windows y con las ntfsprogs (o como se llamen :confused:) desde linux, ninguna encontró nada, pero como no me fiaba opte por formatear la partición y reinstalar windows, no quería llegar hasta ahí pero parece ser que esa es la única solución para algunos problemas de windows.

Bueno finalmente creo que si había algún error, ya que después de reintalar windows y despues restarar grub con el supergrubdisk me funciona todo correctamente.

Enrique.

---


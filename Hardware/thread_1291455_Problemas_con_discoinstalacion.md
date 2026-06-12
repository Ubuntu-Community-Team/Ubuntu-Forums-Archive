---
title: "Problemas con disco/instalacion"
date: 2009-10-14
forum: Hardware
---

### Post by Mustaine666 on 2009-10-14
Bueno.. les cuento.. despues de armar el conky descubri q el swap no anda..  buscando por internet encontre un post.. en donde usaba el Gparted para activarlo y me di cuenta de algo

[[img]http://i.imagehost.org/t/0626/Pantallazo.jpg[/img]](http://i.imagehost.org/view/0626/Pantallazo)

no tengo particiones ni home ni "/" ni swap en ubuntu?? .. como puede ser? .. que tengo q hacer.. tengo que formatear todo??.. 

el disco de windows anda de diez.. no tiene drama.. con el gparted se puede ver y se visualiza tal cual lo dividi! 

:mad::mad::mad::mad::mad:

windows era mas facil! .. pero no me voy a resignar!

---

### Post by Mauro22 on 2009-10-14
La swap si no hace falta no se va a usar nunca, no obstante ello, se recomienda el doble de la RAM...

GNU/Linux administra muy bien los recursos, si necesita swap la va a usar...


El disco ese de 40gb? es el unico que tenes?

---

### Post by Mustaine666 on 2009-10-14
[[img]http://i.imagehost.org/t/0041/particiones.jpg[/img]](http://i.imagehost.org/view/0041/particiones)

aca esta la captura desde windows.. tengo 2 de 40gb .. pero uno es de datos.. y el otro windows + ubuntu! ..

---

### Post by gmunioz on 2009-10-14
Hola mus....:

Ejecuta en Consola, aplicaciones - Accesorios - Terminal:

```
sudo fdisk -l *(es ele no i ni uno)*
```

```
sudo cat /boot/grub/menu.lst
```

```
sudo cat /etc/fstab
```

```
sudo cat /boot/grub/device.map
```

Copia las salidas y pegalas en el post.

---

### Post by Mustaine666 on 2009-10-14
```
sudo fdisk -l *(es ele no i ni uno)*
```

```
Disco /dev/sda: 40.0 GB, 40000000000 bytes
255 cabezas, 63 sectores/pista, 4863 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0ff40ff4

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1085     8709088+   7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2            1086        4622    28410952+  83  Linux
/dev/sda3            4623        4865     1951897+   5  Extendida
/dev/sda5            4623        4865     1951866   82  Linux swap / Solaris

Disco /dev/sdb: 40.0 GB, 40020664320 bytes
240 cabezas, 63 sectores/pista, 5169 cilindros
Unidades = cilindros de 15120 * 512 = 7741440 bytes
Identificador de disco: 0x578d578d

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               2        5169    39070080    f  W95 Ext'd (LBA)
/dev/sdb5               2        5169    39070048+   7  HPFS/NTFS

```



```
sudo cat /boot/grub/menu.lst
```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3415ec85-9101-435e-bfe4-3bf7f72ba599

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

title		Ubuntu 9.04, kernel 2.6.30-02063006-generic
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.30-02063006-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-02063006-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-02063006-generic (recovery mode)
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.30-02063006-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro  single
initrd		/boot/initrd.img-2.6.30-02063006-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3415ec85-9101-435e-bfe4-3bf7f72ba599
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

```
sudo cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=47e53ee5-ab20-4b03-8ca9-561a2438c5d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```


```
sudo cat /boot/grub/device.map
```
```

mustaine@mustaine-desktop:~$ sudo cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb


```

---

### Post by gmunioz on 2009-10-14
Hola mus...:

No existe ningun problema, esta todo correcto:

```
Tienes /

En el disco 0

(hd0)	/dev/sda

Es la partición primaria

/dev/sda2  1086  4622    28410952+  83  Linux
```

```
Tienes swap

En el disco 0

(hd0)	/dev/sda

Es la partición lógica

/dev/sda5      4623    4865   1951866   82  Linux swap / Solaris

Que se encuentra dentro de la extendida y la ocupa totalmente

/dev/sda3        4623     4865     1951897+   5  Extendida

```

```
Y estan correctamente montadas:

# / was on /dev/sda2 during installation
UUID=3415ec85-9101-435e-bfe4-3bf7f72ba599 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=47e53ee5-ab20-4b03-8ca9-561a2438c5d8 none            swap    sw              0       0

```

Obviamente no has creado partición para /home, asi que se encuentra

dentro de /

---

### Post by Mustaine666 on 2009-10-14
y existe alguna solucion? .. o seria formatear.. segui el orden de las particiones.. de un tutorial de internet!

---

### Post by guillermolisi on 2009-10-14
> **Mustaine666 said:**
> y existe alguna solucion? .. o seria formatear.. segui el orden de las particiones.. de un tutorial de internet!
Solucion a que cosa ?

Abriste el thread diciendo que Gparted no te mostraba particiones para /, /home y /swap pero esta visto que tenes todas con la salvedad de que /home esta ubicada dentro de /.

Si lo que queres es tener /home en una particion aparte de /, abri otro thread siempre que no encuentres otros que te den alguna guia, solucion o pista para resolver tu objetivo sin tener que volver a instalar, para que sea especifico de lo que queres realizar/conseguir.

---

### Post by Mustaine666 on 2009-10-14
a bueno.. gracias!..

---


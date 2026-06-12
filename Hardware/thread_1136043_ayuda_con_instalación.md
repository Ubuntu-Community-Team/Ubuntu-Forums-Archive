---
title: "ayuda con instalación"
date: 2009-04-24
forum: Hardware
---

### Post by joseluis on 2009-04-24
Bueno, necesito ayuda sobre un tema que paso a detallar. Intentaré ser claro, porque es medio lio (al menos eso me parece a mi)
Tengo dos discos:
c: con winxp (ntfs)
d: con ubuntu 8.04 (ext3; swap) y en este disco otra partición con FAT32

Quiero instalar ubuntu 9.04, y podria hacerlo DESDE CERO, pisando y formateando la particiòn en donde ahora tengo 8.04.
Sin embargo, quizas una buena opción sea crear una nueva particion en el llamado D.
Esto por un par de motivos:
1- quiero formatear en ext4
2. quiero poner el ubuntu de 64 ya que mi maquina lo soporta y antes no lo había hecho.

Por lo tanto, me quedaría la opcion de : o formatear e instalar sobre la anterior o crear una nueva particion manteniendo el anterior ubuntu, del cual sacaria luego todos mis archivos (home y archivos de sistema etán en la misma particion) y los pasaria a la nueva instalación.

ahora LA/S PREGUNTAS/S

Una vez que instale el nuevo sistema en una nueva particiòn, 
¿deberé corregir algo de FSTAB?
¿deberé corregir ademas algo del grub?

aclaro que nunca se pudo instalar el grub en el mbr proque el disco esclavo (d) es un ide y el otro es un SATA, y la conexión que me hicieron sacaron el cable desde la lectora de CD ya que mi maquina no bancaba SATA e IDE (eso me dijeron). Asi que desde siempre estoy buteando con SGD (y no me quejo..ta bien asi).

este es el fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=3525b77c-1060-4737-97e6-8fdba6cc546b	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=4840-5BE0	/media/sda4	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sdb1 :
UUID=54FCF8B7FCF89488	/media/sdb1	ntfs-3g	defaults,locale=es_AR.UTF-8	0	0
UUID=f278ffd8-98f6-45e6-acf8-d6c9ce93139f	none	swap	sw	0	0
/dev/hdc	/media/cdrom0	udf,iso9660	user,noauto,exec	0	0

y este es menu.lst del grub (q lo tengo en la carpeta /boot/grub

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
# kopt=root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash locale=es_ES

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-20-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-20-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-virtual
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-19-virtual
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-virtual (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-virtual root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-19-virtual

title		Ubuntu 8.04.2, kernel 2.6.24-19-server
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-server (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-19-server

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3525b77c-1060-4737-97e6-8fdba6cc546b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,2)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


GRACIAS

---

### Post by gmunioz on 2009-04-24
Hola jos....:

Te sugiero lo siguiente:

1- Desde una sesión live de Jaunty, crea una nueva partición en sistema

de archivos ext4, monta luego si no se hubiere montado la partición con

la instalación de Hardy y la nueva partición y copia todo el contenido

de /home a la nueva partición.

2- Desmonta las particiones, e inicia la instalación, al llegar a parti-

cionamiento elige manual e instala:

En tu primitivo /, con sistema de archivos ext4, punto de montaje /

En tu primitiva swap, con sistema de archivos intercambio

En la nueva partición, sistema de archivos ext4, manteniendo los datos, 

sin formatear, punto de montaje /home

Deberás mantener el mismo nombre de usuario y la misma contraseña.

3- Si previamente desde synaptic creas un archivo de texto plano con las 

aplicaciones instaladas, mediante la opción Archivo - Guardar selecciones

marcando el recuadro estado completo, una vez completada la instalación

y activados los repositorios de Jaunty, desde synaptic con la opción

Archivo - leer selecciones - aplicar, podr{as tener todas las aplicaciones

instaladas tal como lo estan en Hardy, siempre y cuando esten disponibles

para Jaunty.

Saludos.

Gabriel.

---


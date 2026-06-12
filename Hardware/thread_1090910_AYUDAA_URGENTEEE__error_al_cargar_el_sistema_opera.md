---
title: "AYUDAA URGENTEEE  error al cargar el sistema operativo"
date: 2009-03-08
forum: Hardware
---

### Post by liccid on 2009-03-08
Hola como les va les comento

tenia instalado windows en un disco rigido y ubuntu en otro ambos discos sata

le di formato con el gparted al dico con windows apague el pc le saque el disco  ya que lo vendi y me fui a entregarlo

la sorpresa es que volvi a casa mi pc me tiraba un error ingrese disco de sistema un amigo me dijo que probara con el supergrub 

y ahora me dice error al cargar el sistema operativo estoy desesperado mis conocimientos no son muchos y no quiero tener que formatear y reinstalar todo si es posible

---

### Post by staar on 2009-03-08
pasanos que error exacto te da, asi te podemos ayudar mejor...

lo mas seguro es que el disco que vendiste haya sido donde el sistema buscaba primero para cargar, y donde estaba instalado el grub (cargador de arranque, el menu que te perimitia elegir entre windows o ubuntu), con el supergrub podes instalar el grub en el disco de ubuntu, pero si lo recuperaste seguramente te esta tomando el orden de las particiones incorrecto, ya que falta un disco...

hace una cosa, bootea con un livecd, busca y postea aca el archivo /boot/grub/menu.lst, seguramente cambiando el numero de disco donde esta instalado ubuntu se arregla, es cambiar donde dice (hd1,1) por (hd0,1) o similar (el primer numero es el disco y el segundo la particion, si tenias dos discos y el de windows era el primero, entonces ese era el "0" y el de ubuntu el "1")

saludos

---

### Post by liccid on 2009-03-08
Primero que todo Gracias por darme una mano con este tema

bueno el error es : "error al cargar el sistema operativo" no dice mas que eso la pantalla

como te decia use el supergrub y tambien un tutorial para reinstalar el grub ninguno funciono es mas creo que empeore la situacion.

en el bios de mi pc

el sata 1 lo ocupa la lectora de dvd
el sata 2 lo ocupa mi dico rigido donde esta linux ubuntu(en la actualidad)

y este es el archivo que me pediste:

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
# kopt=root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ef5e59fb-96f3-4f96-a73b-25a4985233f4

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		ef5e59fb-96f3-4f96-a73b-25a4985233f4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		ef5e59fb-96f3-4f96-a73b-25a4985233f4
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ef5e59fb-96f3-4f96-a73b-25a4985233f4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ef5e59fb-96f3-4f96-a73b-25a4985233f4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ef5e59fb-96f3-4f96-a73b-25a4985233f4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
root		(hd1,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by staar on 2009-03-08
bueno ahora veo el problema, ubuntu es una distro que usa el UUID, identificador unico de los discos, para reconocerlos, (otras distros usan hdx,x, como te explique antes) y vos tenes dos diferentes, osea que esta buscando ubuntu en dos discos diferentes...

> esta linea busca cargar ubuntu desde un disco...

title Ubuntu 8.10, kernel 2.6.27-11-generic
uuid [COLOR="Red"]ef5e59fb-96f3-4f96-a73b-25a4985233f4[/COLOR]
kernel /boot/vmlinuz-2.6.27-11-generic [COLOR="Red"]root=UUID=ef5e59fb-96f3-4f96-a73b-25a4985233f4[/COLOR] ro quiet splash 
initrd /boot/initrd.img-2.6.27-11-generic
quiet


Other operating systems:

y esta desde otro...

title Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.27-11-generic [COLOR="Red"]root=UUID=17fbfbca-e02c-4ad3-89cf-51bdbf344f99[/COLOR] ro quiet splash 
initrd /boot/initrd.img-2.6.27-11-generic
savedefault
boot


proba seleccionando la segunda linea (es la primera despues de que dice Other operating systems) y booteando desde esa...

saludos

---

### Post by liccid on 2009-03-08
Bueno te cuento lo que hice paso a paso

puse el live cd y modifique en la linea que me digiste con el gedit donde decia (hd0,0)
por (hd1,1) guarde 
y al reiniciar vuelve a pasar lo mismo pantalla negra "error al cargar el sistema operativo"

=_(

---

### Post by liccid on 2009-03-08
a todo esto si yo inicio la maquina sin el live cd no aprece ninguna instancia de eleccion. solamenete el error "error al cargar el sistema operativo"

por eso me tire por modificar con el gedit

---

### Post by Hei Ku on 2009-03-09
Probablemente sea (hd1,0), no 1,1.

---

### Post by staar on 2009-03-09
> **liccid said:**
> a todo esto si yo inicio la maquina sin el live cd no aprece ninguna instancia de eleccion. solamenete el error "error al cargar el sistema operativo"

por eso me tire por modificar con el gedit

y apretando ESC, justo despues de que termine la BIOS? te tendria que aparecer el menu del GRUB, y ahi seleccionar...

saludos

---

### Post by liccid on 2009-03-09
> **staar said:**
> y apretando ESC, justo despues de que termine la BIOS? te tendria que aparecer el menu del GRUB, y ahi seleccionar...

saludos

Bueno mil gracias voy a provar y les cuento como me fue.:popcorn:

---

### Post by ADICTOALMAXIMO on 2009-03-10
Ojala que nunca me pase

---


---
title: "Seleccion de SO (Jumpers/ Master/ Slave)"
date: 2009-09-12
forum: Hardware
---

### Post by PabloGNU/LINUX on 2009-09-12
Tengo Windws en un HDD y Ubuntu en otro HDD. 
Como debo poner la configuracion de los HDD, cual va en esclavo y cual en master.
 
Intente, puse la primera vez Windows en master pero no resulto. incia en windows y no dejaba seleccionar SO.
Tambien intente poniendo Ubuntu de master pero tampoco, iniciaba Ubuntu directamente. 
Tambien puse los 2 de master pero iniciaba directamente Ubuntu.
 
Luego quise Iniciar solamente el HDD de Windows (sin tener conectado ningun otro disco) y hay un mensaje que dice: "Error al cargar el SO"
y cuando entro para ver los formatos de los discos la particion de windows es desconocida. 
Pero esto creo que ya es otro Thread no?.
 
Gracias por su tiempo.

---

### Post by staar on 2009-09-12
poné el disco de ubuntu para que arranque primero, una vez cargado el SO, apretá Alt + F2 y poné ```
gksudo gedit /boot/grub/menu.lst
``` poné tu contraseña, y al final del archivo que se te abre agregá esto ```

title           Windows
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader +1

``` guardá y cerra el editor de textos, después andá a Aplicaciones > Accesorios > Terminal y en ella corré ```
sudo update-grub
``` poné tu contraseña (no sale nada cuando la escribís, es normal) y esperá que termine, la próxima vez que reinicies, te va a salir en el menú de GRUB (el cargador de arranque de ubuntu, el primer menu que te salía, donde había tres líneas que decían Ubuntu 9.04, kernel *tanto*) al final, una opción para arrancar Ventanas seleccionala y te tendría que arrancar ese SO...

saludos

---

### Post by PabloGNU/LINUX on 2009-09-12
Gracias, pero hay un problema cuando seleciono windows me aparece este error:

[IMG]http://s4.subirimagenes.com/fotos/previo/thump_319712112092009001.jpg[/IMG]

Puede ser en el nombre del dispositivo?. 

Antes de la carga del SO ubuntu empieza una cuenta regresiva, en la cual aprento escape para acceder a las opciones de SO, se puede suprimir esa cuenta regresiva e ir directamente a la seleccion del SO?. 

Muchas gracias.

---

### Post by gmunioz on 2009-09-12
Hola pab....:

A tu menu le falta una orden:

boot


El item completo es:


```
title           Windows
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader +1
boot
```

Respecto de ver el menu al inicio sin escape:


busca la opción hiddenmenu

Y comentala con una almohadilla #

para que quede asi

# hiddenmenu

---

### Post by PabloGNU/LINUX on 2009-09-12
Verifico y comunico. gracias muchachos

---

### Post by PabloGNU/LINUX on 2009-09-12
Esta bien, saco el tiempo para apretar "ESC" y directamente a las opciones, pero sigue sin funcionarme la parte de windows. 

Muestro como me quedo:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1

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
uuid        f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f12d2615-4cc4-4f8b-ad08-cc65ad1c4de1
kernel        /boot/memtest86+.bin
quiet

title           Windows
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader +1
boot

### END DEBIAN AUTOMAGIC KERNELS LIST 

---

### Post by staar on 2009-09-12
mmm, por ahí Ventanas no está en la primera partición del segundo disco, para asegurarnos, posteá la salida de correr ```
sudo fdisk -l
``` en una Terminal...

saludos

---


---
title: "Instalar win despues de ubuntu"
date: 2009-04-07
forum: Hardware
---

### Post by javier. on 2009-04-07
Hola a todos, a ver si me ayudan con esta. Digamos que por cuestiones x necesito tener una partición win xp, ya bootie el cd de instalación, copio todos los archivos y no bootea mas. Recupero ubuntu y acá estoy, el grub no me deja bootear el windows, que esta a medio instalar. como sigo?

(Ubuntu esta en hd0 y win hd1)

Gracias!

---

### Post by Hei Ku on 2009-04-07
Usas uno de los 500 Live CDs que hay por ahi para recuperar el boot de Windows, o, lo mas facil, Volves a bootear el CD de instalacion de windows y empezas de vuelta la instalacion.

---

### Post by pablo.s on 2009-04-07
Si podés copiar y pegar el archivo menu.lst que está
dentro de /boot/grub podria ser de ayuda. Y también
en que partición de que disco está Windows.
Saludos

---

### Post by javier. on 2009-04-07
Pablo: aca dejo el menu, windows esta en hd1,1   que desde ubuntu lo puedo ver como sdb2

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
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=7c0287fe-3023-40be-99cf-8db220caaa44 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7c0287fe-3023-40be-99cf-8db220caaa44

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
uuid		7c0287fe-3023-40be-99cf-8db220caaa44
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7c0287fe-3023-40be-99cf-8db220caaa44 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7c0287fe-3023-40be-99cf-8db220caaa44
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7c0287fe-3023-40be-99cf-8db220caaa44 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7c0287fe-3023-40be-99cf-8db220caaa44
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c0287fe-3023-40be-99cf-8db220caaa44 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7c0287fe-3023-40be-99cf-8db220caaa44
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c0287fe-3023-40be-99cf-8db220caaa44 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7c0287fe-3023-40be-99cf-8db220caaa44
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Professional
root		(hd1,1)
savedefault
makeactive
chainloader	+1
```


Hei Ku: ya probe con eso, es como la tercera vez que la instalación de windows copia los archivos a la partición y después de reiniciar no bootea.

Gracias

---

### Post by Hei Ku on 2009-04-07
De acuerdo al grub, la particion de windows seria la segunda del segundo disco. Esto es correcto?

---

### Post by pablo.s on 2009-04-07
No veo nada irregular en menu.lst.
¿El problema es que Windows no arranca?

Seguís teniendo grub intacto después de la
instalación? Me suena a que no está terminando
de instalar bien ¿o me equivoco?
Una instalación correcta tiene que sobreescribir
grub y arrancar enseguida.

---

### Post by guillermolisi on 2009-04-07
> **pablo.s said:**
> No veo nada irregular en menu.lst.
¿El problema es que Windows no arranca?

Seguís teniendo grub intacto después de la
instalación? Me suena a que no está terminando
de instalar bien ¿o me equivoco?
Una instalación correcta tiene que sobreescribir
grub y arrancar enseguida.
Coincido.

Normalmente esta secuencia de instalacion termina por anular el inicio con Ubuntu porque Windows pisa la informacion que el MBR posee sobre la particion donde esta el Linux. Por eso se aconseja primero instalar Win y despues Ubuntu.

Ahora que lo pienso mejor, no sera una nueva proteccion que preserva a la gente de "SOs contaminantes" ? ;)

---

### Post by pablo.s on 2009-04-07
> **guillermolisi said:**
> Ahora que lo pienso mejor, no sera una nueva proteccion que preserva a la gente de "SOs contaminantes" ? ;)

En mi barrio a eso mismo le dicen
"tomarse la pastilla azul".

---

### Post by javier. on 2009-04-08
Si, xp me arruino el grub, lo arregle con el cd de ubuntu.

windows esta en el segundo hd, segunda partición . (segun entiendo hd1,1)

---

### Post by Elrengo on 2009-04-09
Hola como va, no se mucho, pero espero poder ayudarte.

Segun entiendo tenes 2 HD conectados a tu pc, uno hd0 con ubuntu, y el hd1 con una instalacion parcial de windows (segun grub).

y segun lo que contas, despues de que la instalacion de windows pide reiniciar el sistema (luego de copiar los archivos) te vuelve a arrancar el grub y bootea ubuntu de nuevo.

Si es asi, podes probar seteando desde el BIOS que bootee primero el disco que esta instalado windows, o si no, directamente desconectar el HD que tiene Ubuntu hasta que termine la instalacion, y de ahi en mas, corregir el grub con el Live Cd de Ubuntu

Saludos

Matias

---

### Post by infernus92 on 2009-04-10
no... si saca el hdd con ubuntu... despues no va a funcionar el grub segun entiendo...
estas seguro que funciona bien el cd de win$ que tenes??
eso de intentar bootear de la bios... yo le iba a decir lo mismo... pero supongo que a estas alturas ya lo habra intentado...
igual no esta de mas decirlo...
sino podrias usar una computadora virtual dentro de tu ubuntu... con QtEmu es muy facil hacerlo...

---

### Post by Elrengo on 2009-04-10
Desconecta tranquilo el HD de windows, la idea es que windows y la pc ni se entre que tenes instalado Ubuntu.


Cuando termina la instalacion de windows apagas la pc, y pones como booteable el hdd de ubuntu, cuando levanta, corregimos el menu.lst, para agregar como corresponde las lineas que haran bootear tu particion de linux.  (Si cuando volves a conectar el HD de ubuntu no bootea, no te preocupes, que lo arreglamos con el live cd)

Saludos

Matias

---

### Post by sp33d3rs on 2009-05-01
Yo no entiendo mucho, pero tube un problema similar. Yo para que funcione, ingrese con el live cd y destrui todas las particiones (click derecho borrar) y empece de nuevo, lo unico "anormal" es que al instalar windows me decia que el tipo de disco duro tenia un formato irreconosible y se lo queria reparar (claro, no salio del trasero de bill asi hay que "repararlo"), en fin, das ok y listo, problema solucionado, queda el mbr a full para windows.

Otro de las posibles salvaciones es el supergrubdisk, Lo insertas y das enter en (" MBR BOOT WIN! :((((  ") y listo, configura el boot de windows en el disco donde esta instalado para que arranque windows.

---

### Post by infernus92 on 2009-05-01
no habria que poner Linux-> Arreglar arranque GRUB con el supergrub disk?
segun lo que tengo entendido eso seria para arreglar el grup "pisado" por la nueva instalacion de win$

---


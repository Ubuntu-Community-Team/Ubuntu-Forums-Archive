---
title: "Ubuntu 9.04 se congela al bootear"
date: 2009-07-07
forum: Hardware
---

### Post by zeusolimpo on 2009-07-07
Estimados foristas
Después de "toquetear" las particiones del único rígido de mi laptop con Ubuntu 9.04 funcionando de 10, para ordenar y hacer lugar, me encuentro que al bootear se congela la pantalla con las siguientes líneas:

* Checking root file system ...
134
fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 44671/4792320 files, 6770593/19167545 blocks
                                           [OK]
* Checking file systems ...
134
fsck 1.41.4 (27-Jan-2009)
                                           [OK]
* Mounting local filesystems ...           [OK]
* Activating swapfile swap ...             [OK]
* Configurating network interfaces ...     [OK]
* Starging system log daemon ...           [OK]
* Starting kernel log daemon ...           [OK}
=

y ahí se queda parpadeando el cursor. Lo dejé hasta media hora y no sale.
Puedo rebootear con Ctrl-Alt-Del, y también puedo iniciar en modo seguro. Desde allí intenté hacer un apt-get update pero me sale un error y sugier hacer un dpkg manual. Esto tampoco prospera. Estuve buscando en los foros y encontré cosas parecidas pero las soluciones aplicadas no me han dado resultado.
Recurro a Uds. para saber si hay alguna manera de recuperar el sistema sin perder la configuración actual (que parece que está en los archivos que puedo ver desde la consola).
Gracias de antemano por la ayuda y saludos.

---

### Post by zeusolimpo on 2009-07-07
Con todo respeto desde mi poco conocimiento: no me parece un problema de Hardware sino mas bien de Software.
La laptop (lenovo 3000 C200) funciona perfectamente así como todos sus componentes, puedo montar Ubuntu 9.04 desde un live CD. Se conecta a internet y puedo navegar con el browser.
El problema está en el booteo normal, como que se queda enganchada buscando algún archivo o dirección que no encuentra.
Mis disculpas si estoy equivocado. Saludos

---

### Post by guillermolisi on 2009-07-07
> **zeusolimpo said:**
> Con todo respeto desde mi poco conocimiento: no me parece un problema de Hardware sino mas bien de Software.
La laptop (lenovo 3000 C200) funciona perfectamente así como todos sus componentes, puedo montar Ubuntu 9.04 desde un live CD. Se conecta a internet y puedo navegar con el browser.
El problema está en el booteo normal, como que se queda enganchada buscando algún archivo o dirección que no encuentra.
Mis disculpas si estoy equivocado. Saludos
Puede ser, pero suponiendo que asi sea, por que no abriste el hilo en el subforo correspondiente en lugar de hacer en el de threads normales ?

Luego, si es un problema de drivers, controladores (que es lo mismo) ACPI o cosas equivalentes, se considera hardware (por lo menos hasta que la solucion demuestre lo contrario).

---

### Post by guillermolisi on 2009-07-07
> **zeusolimpo said:**
> Estimados foristas
Después de "toquetear" las particiones del único rígido de mi laptop con Ubuntu 9.04 funcionando de 10, para ordenar y hacer lugar, me encuentro que al bootear se congela la pantalla con las siguientes líneas:

* Checking root file system ...
134
fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 44671/4792320 files, 6770593/19167545 blocks
                                           [OK]
* Checking file systems ...
134
fsck 1.41.4 (27-Jan-2009)
                                           [OK]
* Mounting local filesystems ...           [OK]
* Activating swapfile swap ...             [OK]
* Configurating network interfaces ...     [OK]
* Starging system log daemon ...           [OK]
* Starting kernel log daemon ...           [OK}
=

y ahí se queda parpadeando el cursor. Lo dejé hasta media hora y no sale.
Puedo rebootear con Ctrl-Alt-Del, y también puedo iniciar en modo seguro. Desde allí intenté hacer un apt-get update pero me sale un error y sugier hacer un dpkg manual. Esto tampoco prospera. Estuve buscando en los foros y encontré cosas parecidas pero las soluciones aplicadas no me han dado resultado.
Recurro a Uds. para saber si hay alguna manera de recuperar el sistema sin perder la configuración actual (que parece que está en los archivos que puedo ver desde la consola).
Gracias de antemano por la ayuda y saludos.
Como esta particionado el disco, que sistema de archivos usas en cada particion y cuanto espacio libre y total posee cada una ?

---

### Post by zeusolimpo on 2009-07-07
Que haya puesto el thread en Normales solo demuestra mi incapacidad, lo siento.
En cuanto a lo que preguntás, transcribo la salida:

[FONT="Courier New"]root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777[/FONT]
[FONT="Courier New"]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris
[/FONT]
Gracias por responder

---

### Post by zeusolimpo on 2009-07-07
Al correr un script para obtener información de booteo tengo los siguientes resultados:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 16810047 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77777777

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,340,424   153,340,362  83 Linux
/dev/sda2         153,340,425   156,296,384     2,955,960   5 Extended
/dev/sda5         153,340,488   156,296,384     2,955,897  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xecbe50ce

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,015,231     2,015,200   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2b4cdc51-44b2-4159-976a-c7ebfbf5a77d" TYPE="ext3" 
/dev/sda5: UUID="ed314371-7134-4b80-8bc7-a8ed644cb0c2" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: LABEL="KINGSTON1GB" UUID="C4BF-B840" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1 on /media/KINGSTON1GB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		2b4cdc51-44b2-4159-976a-c7ebfbf5a77d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		2b4cdc51-44b2-4159-976a-c7ebfbf5a77d
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2b4cdc51-44b2-4159-976a-c7ebfbf5a77d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2b4cdc51-44b2-4159-976a-c7ebfbf5a77d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2b4cdc51-44b2-4159-976a-c7ebfbf5a77d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f4356525-072b-4b65-bc81-32ca93344339 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f4356525-072b-4b65-bc81-32ca93344339 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 9.04, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2b4cdc51-44b2-4159-976a-c7ebfbf5a77d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ed314371-7134-4b80-8bc7-a8ed644cb0c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.2GB: boot/grub/menu.lst
   8.6GB: boot/grub/stage2
   8.7GB: boot/initrd.img-2.6.28-11-generic
  11.3GB: boot/initrd.img-2.6.28-13-generic
   8.6GB: boot/vmlinuz-2.6.28-11-generic
   9.8GB: boot/vmlinuz-2.6.28-13-generic
=============================== StdErr Messages: ===============================


Parece como que lo que quise eliminar (la otra instalación de Ubuntu 9.04 en sda6) no se borró del Grub. Esto tendrá algo que ver?
Por las dudas estoy backupeando todo en previsión de una nueva instalación "limpia"!

---

### Post by guillermolisi on 2009-07-07
Como la quisiste eliminar a esa otra instalacion de JJ en /dev/sda6 (particion que no figura en ninguno de los discos que tenias al momento de pasar la info sobre el inicio de la PC) ?

Comenta en detalle porque por mas que la instalacion en /dev/sda6 figure en el Grub, mientras no la selecciones no deberia afectar el inicio normal con otra instalacion que se encuentre operativa (dev/sda1).

Ademas, recordas haber modificado algun permiso de archivos ?

---

### Post by zeusolimpo on 2009-07-07
Yo tenía el disco particionado como sda1(Primaria Linux A), sda2 (extendida), sda5 (swap de Linux A), sda6 (no me acuerdo si primaria o ext con linux B) y sda7 (swap de linux B). Esto fué producto de algunos errores de configuración y una instalación nueva de Ubuntu, Cuando conseguí que la instalación A funcionara correctamente, hice BU de todos los archivos, entré en el gparted, eliminé sda6 y sda7 y aumenté al máximo el tamaño de sda2, para poder utilizar todo el disco.
Hasta ahí todo andaba bien, salvo que desde el usuario no tenía acceso a sda2, solamente podía acceder como root.
Supongo que debería haber parado en este punto y averiguar como podía acceder a sda2, pero no, me entusiasmé con el live gparted y:
1 redimensioné sda2 al mínimo posible
2 aumenté sda1 al máximo posible
3 monté / en sda1 y confirmé que estuviera marcado como boot.
4 apliqué los cambios

y ya no arrancó mas en modo normal!

Utilicé el CD de restauración de Ubuntu y parece ir todo bien hasta que llega a las opciones de reinstalar Grub y entonces lanza un "Fatal Error" en rojo que da miedo. El rebooteo se cuelga igual.
No recuerdo haber cambiado permisos en files.

---

### Post by guillermolisi on 2009-07-07
> **zeusolimpo said:**
> Yo tenía el disco particionado como sda1(Primaria Linux A), sda2 (extendida), sda5 (swap de Linux A), sda6 (no me acuerdo si primaria o ext con linux B) y sda7 (swap de linux B). Esto fué producto de algunos errores de configuración y una instalación nueva de Ubuntu, Cuando conseguí que la instalación A funcionara correctamente, hice BU de todos los archivos, entré en el gparted, eliminé sda6 y sda7 y aumenté al máximo el tamaño de sda2, para poder utilizar todo el disco.
Hasta ahí todo andaba bien, salvo que desde el usuario no tenía acceso a sda2, solamente podía acceder como root.
Supongo que debería haber parado en este punto y averiguar como podía acceder a sda2, pero no, me entusiasmé con el live gparted y:
1 redimensioné sda2 al mínimo posible
2 aumenté sda1 al máximo posible
3 monté / en sda1 y confirmé que estuviera marcado como boot.
4 apliqué los cambios

y ya no arrancó mas en modo normal!

Utilicé el CD de restauración de Ubuntu y parece ir todo bien hasta que llega a las opciones de reinstalar Grub y entonces lanza un "Fatal Error" en rojo que da miedo. El rebooteo se cuelga igual.
No recuerdo haber cambiado permisos en files.
Como hiciste el backup de todos los archivos ?

Cuando te referis a "todos los archivos" te estas refiriendo a los ocultos, a los del SO, del usuario, etc. o solamente a un grupo especifico ?

---

### Post by zeusolimpo on 2009-07-07
Siguiendo esta entrada:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by guillermolisi on 2009-07-07
> **zeusolimpo said:**
> Siguiendo esta entrada:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Antes de hacer la restauracion del backup, repetiste el "sudo su" ?

---

### Post by zeusolimpo on 2009-07-07
No hice restauración de BU. Me resisto a creer que no hay forma de recuperar el sistema sin instalar de cero. Me voy a dar un tiempo mas preguntando por ahí a ver si hay una solución mas elegante.
De última, el fin de semana lo instalo de nuevo.

---

### Post by guillermolisi on 2009-07-07
Me maree.

Hiciste el backup de las particiones que borraste, si ?
Luego modificaste los tamaños de las primeras particiones en el mismo disco, ok?

De ahi en mas no pudiste iniciar mas pero en todo esto lo del backup es anecdotico y el tutorial tambien ....

Hay que ver que paso con el redimensionamiento de las particiones y el Grub. Ahi esta la cosa.

Confirmame si es asi o sigo perdido.

---

### Post by guillermolisi on 2009-07-07
> **zeusolimpo said:**
> Yo tenía el disco particionado como sda1(Primaria Linux A), sda2 (extendida), sda5 (swap de Linux A), sda6 (no me acuerdo si primaria o ext con linux B) y sda7 (swap de linux B). Esto fué producto de algunos errores de configuración y una instalación nueva de Ubuntu, Cuando conseguí que la instalación A funcionara correctamente, hice BU de todos los archivos, entré en el gparted, eliminé sda6 y sda7 y aumenté al máximo el tamaño de sda2, para poder utilizar todo el disco.
Hasta ahí todo andaba bien, salvo que desde el usuario no tenía acceso a sda2, solamente podía acceder como root.
Supongo que debería haber parado en este punto y averiguar como podía acceder a sda2, pero no, me entusiasmé con el live gparted y:
1 redimensioné sda2 al mínimo posible
2 aumenté sda1 al máximo posible
3 monté / en sda1 y confirmé que estuviera marcado como boot.
4 apliqué los cambios

y ya no arrancó mas en modo normal!

Utilicé el CD de restauración de Ubuntu y parece ir todo bien hasta que llega a las opciones de reinstalar Grub y entonces lanza un "Fatal Error" en rojo que da miedo. El rebooteo se cuelga igual.
No recuerdo haber cambiado permisos en files.
Por lo que acusa el FDISK el swap esta dentro de la particion logica o la solapa, fijate que ambas coinciden en el punto de inicio y en el final:
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            **9546        9729 **    1477980    5  Extended
/dev/sda5            **9546        9729     **1477948+  82  Linux swap / Solaris
```

---

### Post by guillermolisi on 2009-07-07
Esta es la tabla de particiones de una de mis maquinas en cuyo disco principal la primera particion es la de swap:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866    5  Extended
/dev/sda2   *         244        3890    29294527+  83  Linux
/dev/sda3            3891       19457   125041927+  83  Linux
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
```

/dev/sda2 es / y /dev/sda3 es /home.

Con esto confirmo que la extendida y la swap de tu disco aparentemente estan normales pero no tenes mas que dos particiones en realidad. Era asi originalmente en tu caso ?

---

### Post by zeusolimpo on 2009-07-08
Efectivamente

---

### Post by guillermolisi on 2009-07-08
Ok. Entonces o hay algun problema en /var/log (permisos fundamentalmente o la remota posibilidad de, por ejemplo, que /var directamente no exista) o algun otro problema que podria estar en el Grub.

Vos habias dicho que cuando quisiste reconstruir Grub te salia un error "horrible". Podrias mostrar que dice ese error y de que forma intentaste reconstruirlo ?

---

### Post by zeusolimpo on 2009-07-11
Bueno, finalmente instalé de cero y restauré algunos archivos del backup, solamente los necesarios para poder arrancar confortablemente.
Gracias Guillermo por la paciencia!

---


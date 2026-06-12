---
title: "el nuevo kernel me fundio la nvidia"
date: 2008-05-29
forum: Hardware
---

### Post by crosssover on 2008-05-29
Hola gente, les paso a contar mi problema.
ayer hice el update al kernel 2.6.24-17, sabia que con el update los drivers privativos de nvidia iban a dejar de funcionar ya que necesitan recompilar el kernel y demas ... pero bueno los iba a volver a instalar.

para mi sorpresa una vez que bajo los nuevos drivers y los instalo sigo sin poder iniciar con los controladores de nvidia.

Ya probe desinstalar el controlador anterior, volver a reinstalar el nuevo driver y editar el xorg.

No se me ocurre que mas hacer, si alguien me puede dar una mano sino tendre que volver a usar el kernel anterior.

---

### Post by jpmorelli on 2008-05-29
Probaste instalando desde el paquete "EnvyNG" ? con la versión 7.10 me pasó lo mismo y bajando Envy y configurando Nvidia con ese programa todo funcionó sin dramas.

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Suerte !

---

### Post by pol666 on 2008-05-30
Actualizar Kernels es la perdicion U_U

---

### Post by pablo0469 on 2008-05-30
No tenes la necesidad de actualizar el kernel por tu cuenta, a mi se me actualizo solito y no tuve ningun drama con mi NVIDIA despues de desisntalar los modulos del 2.6.24-16.

Saludos.

---

### Post by crosssover on 2008-05-30
los del envy no me sirven pasa que estaba usando los drivers 173 no los 169, ya que tengo una geforce serie 8 y los anteriores funcionaban un tanto mal.
Alguien sabe como eliminar por completo los drivers privativos ?

---

### Post by rojojuan on 2008-05-30
> **crosssover said:**
> los del envy no me sirven pasa que estaba usando los drivers 173 no los 169, ya que tengo una geforce serie 8 y los anteriores funcionaban un tanto mal.
Alguien sabe como eliminar por completo los drivers privativos ?


Con el mismo EnvyNG podés eliminar los drivers, es una de las opciones que tiene

---

### Post by crosssover on 2008-05-30
ya los elimine con sh NVIDIA-(version).run --uninstall, reinstale, genere otro xorg con nvida-xconfig, aparece todo en la seccion device como debe aparecer pero no hay caso. sigue iniciando sin driver :S

probe instalar el 169 con EnvyNG y ahora me tira error de que un archivo en /usr/shar/Envy# no se puede instalar.

el kernel nuevo me meo el sistema

---

### Post by rojojuan on 2008-05-30
> **crosssover said:**
> ya los elimine con sh NVIDIA-(version).run --uninstall, reinstale, genere otro xorg con nvida-xconfig, aparece todo en la seccion device como debe aparecer pero no hay caso. sigue iniciando sin driver :S

probe instalar el 169 con EnvyNG y ahora me tira error de que un archivo en /usr/shar/Envy# no se puede instalar.

el kernel nuevo me meo el sistema

En una máquina me funcionó lo sguiente:
Desistale los drivers propietarios con EnvyNG, luego reinicié e instalé los drivers que vienen con Ubuntu (Sistema - Controladores de Hardware); reinicié e instalé los propietarios con EnvyNG.

---

### Post by crosssover on 2008-05-31
gracias por seguir ayudandome, pero no tuve suerte, veo si si la arreglo de otro modo. Alguien esta usando el driver 173.14.05 con el nuevo kernel ?

---

### Post by Applelnx on 2008-05-31
Poseo aca aunque no mi problema no es puntulamente el de crossover.  Disculpen si no va aca.

Cuando actualice el kernel a la version 2.6.24-17 creo que me dejaron de funcionar los drivers v4l (video4linux)los cuales uso para mi tarjeta de tv (cuando inicio con ese kernel no me capta la tarjeta). Ahora estoy iniciando linux en el kernel viejo, pero queria saber si habia alguna manera de eliminar el nuevo kernel, asi no me aparece en el grub.

Saludos

---

### Post by Hei Ku on 2008-05-31
tenes que editar el menu.lst y borrar el kernel nuevo de las opciones.
despues corre el sudo update-grub

O tambien hay una opcion grafica, Sajnox posteo esa opcion en un thread anterior.

---

### Post by sergiom99 on 2008-05-31
yo iba a hacerlo, pero el menu.lst dice q esta dentro del AUTOMAGIC y que no hay que editarlo.
Lo borro igual?

---

### Post by Hei Ku on 2008-05-31
En vez de borrarlo podes cambiarlo de orden y poner como default el kernel viejo. Es menos bardo, y nunca se sabe si alguna vez vas a necesitar el nuevo.

---

### Post by sergiom99 on 2008-05-31
ok, en realidad queria sacar el anterior, pero tenes razon, hasta q tenga otro dejo 2 versiones. gracias.

---

### Post by Applelnx on 2008-05-31
> **Hei Ku said:**
> En vez de borrarlo podes cambiarlo de orden y poner como default el kernel viejo. Es menos bardo, y nunca se sabe si alguna vez vas a necesitar el nuevo.

Esa me gusto. Pero como se hace :confused::confused:

---

### Post by Hei Ku on 2008-05-31
Tendrias que cambiar el orden en el menu.lst.

En todo caso, postealo y te damos una mano. Y como siempre al hacer estas cosas locas, hace backup.
Igual, siempre la mas facil es cambiarle el default, para que arranque la opcion que vos queres. Lo cambias de 0 a por ejemplo 2 o 3, que debe ser la opcion del kernel viejo.

---

### Post by luks911 on 2008-05-31
> **crosssover said:**
> gracias por seguir ayudandome, pero no tuve suerte, veo si si la arreglo de otro modo. Alguien esta usando el driver 173.14.05 con el nuevo kernel ?

Yo acabo de instalarlo de forma manual y no tuve problemas. ¿Es posible que al finalizar la instalación del driver no hayas desabilitado los módulos nv y nvidia_new? Para hacerlo, una vez que instalaste el driver, pero antes de volver al entorno gráfico hacés:

$ sudo nano /etc/default/linux-restricted-modules-common

Y donde dice “DISABLED_MODULES” agregás entre comillas nv y nvidia_new. Tienee que quedar así.

DISABLED_MODULES="nv nvidia_new"

Guardás y salís.

---

### Post by Applelnx on 2008-06-01
> **Hei Ku said:**
> Tendrias que cambiar el orden en el menu.lst.

En todo caso, postealo y te damos una mano. Y como siempre al hacer estas cosas locas, hace backup.
Igual, siempre la mas facil es cambiarle el default, para que arranque la opcion que vos queres. Lo cambias de 0 a por ejemplo 2 o 3, que debe ser la opcion del kernel viejo.

Disculpa Hei Ku, pero no encuentro el archivo menu.lst

Donde esta? Tengo que hacerlo desde la consola?

---

### Post by Hei Ku on 2008-06-01
Esta en /boot/grub/menu.lst
Tenes que editarlo con sudo. Y tener mucho cuidado al hacerlo.

---

### Post by Applelnx on 2008-06-02
Esto es lo que contiene el archivo:

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
# kopt=root=UUID=7fc80efd-a3dc-46dc-91ce-a7beb3344358 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7fc80efd-a3dc-46dc-91ce-a7beb3344358 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7fc80efd-a3dc-46dc-91ce-a7beb3344358 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7fc80efd-a3dc-46dc-91ce-a7beb3344358 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7fc80efd-a3dc-46dc-91ce-a7beb3344358 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

No entiendo muy bien donde tocar para que me ponga el kernel viejo como default.

Es en el default que tengo que poner 3 para el kernel viejo?

---

### Post by faktorqm on 2008-06-02
No, en default 2. Busquen y lean mis posts sobre GRUB que hay varios. O la documentacion en todo caso. Salu2!

---

### Post by sajnox on 2008-06-02
Hay un programa para manejar el grub graficamente y es muy facil de usar
```

sudo apt-get install startupmanager
```

Lo buscan en sistema/administracion/administrador de arranque

---

### Post by Applelnx on 2008-06-02
Perfecto, gracias ;)

---


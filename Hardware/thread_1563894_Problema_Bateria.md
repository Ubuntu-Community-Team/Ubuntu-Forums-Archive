---
title: "Problema Bateria"
date: 2010-08-29
forum: Hardware
---

### Post by Applelnx on 2010-08-29
Hola, hace mas o menos 1 mes y medio tengo el problema de que mi batería no dura practicamente nada en Ubuntu (40 - 60 min a lo sumo). La carga dura hora y media. En Windows la bateria tiene una duracion normal (1,5 - 2 horas). 

Como dato a tener en cuenta, cuando me logueo en Ubuntu, me salta un cartel de que Power Manager no responde ([https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)). 

No se si sera relacionado a esto, pero la computadora larga mucho calor desde abajo. Tengo una HP Pavilion dv4-1225dx con Ubuntu 10.04 64 bits. Alguien me podría dar una mano para chequear que es lo que anda mal?

Saludos

---

### Post by guillermolisi on 2010-08-29
Podes verificar si esta iniciando con la opcion acpi=off en el grub ?

---

### Post by Applelnx on 2010-08-30
Hola Guillermo, me fije en **/etc/default/grub** (ver codigo) y en **/boot/grub/grub.cfg** y no dice nada de acpi=off.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash quiet vga=773"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

EDIT: dejo imagenes de las estadisticas de energia por si sirven

[ATTACH]167990[/ATTACH][ATTACH]167991[/ATTACH][ATTACH]167992[/ATTACH]

---

### Post by guillermolisi on 2010-08-31
Una forma de saber con que parametros esta iniciando el bootting es configurar Grub para que muestre el menu (/etc/default/grub). Cuando tenes el menu de inicio de Grub a la vista, edita la linea de arranque que estas utilizando habitualmente (por si tenes mas de un kernel/SO) y ahi podras ver que opciones, ademas de "quiet", se estan utilizando.

Te paso un ejemplo para que te ubiques:
```
kernel          /boot/vmlinuz-2.6.32-24-generic root=UUID=72c5d05e-b996-4634-9cd3-130716ed6404 ro **pci=nomsi,noaer** quiet splash
```esas opciones las utilizo en una de mis maquinas para no tener logs llenos de errores espureos producidos por las caracteristicas de la motherboard Asus que utiliza.

---

### Post by alfplayer on 2010-08-31
También

```
cat /proc/cmdline
```

---

### Post by guillermolisi on 2010-08-31
> **alfplayer said:**
> También

```
cat /proc/cmdline
```
Buena esa !! Gracias !

---

### Post by Applelnx on 2010-08-31
Gracias por responder. No entendi bien que es lo que me tengo que fijar ni donde. Por un lado tengo el archivo /etc/default/grub, del cual pegue lo que decia en el post #3. 

Por otro lado tengo el /boot/grub/grub.cfg, en donde encuentro el codgio similar al que posteas:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6a59a51e-7813-49c5-a41f-3239f2189451
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=6a59a51e-7813-49c5-a41f-3239f2189451 ro splash quiet vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
```

En cuanto al cat /proc/cmdline, esto es lo que sale (que es igual a una de las lines del grub.cfg)

```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=6a59a51e-7813-49c5-a41f-3239f2189451 ro splash quiet vga=773 quiet splash
```

---

### Post by guillermolisi on 2010-08-31
Ok. Inicia con acpi activo.

Ahora habria que confirmar que reconozca correctamente la tabla acpi del BIOS y/o revisar la configuracon del administrador de energia.

Lo primero requiere leer el log de inicio de la maquina, que esta en /var/log/dmesg.
Lo segundo requiere revisar, a traves de Gnome si usas este escritorio, como tenes configurada la administracion de energia, particularmente cuando funciona con bateria y sin el cargador.

Los recursos con impacto mas negativo en la autonomia de la bateria son intensidad del display, antenas de radio (wifi/Bluetooth), conexiones USB activas y motores de unidades de disco/ventiladores.

---

### Post by Applelnx on 2010-09-01
Guillermo, adjunto el dmesg:

[ATTACH]168187[/ATTACH]

Por otra parte, dejo la captura de pantalla de mi configuracion del gestor de energia:

[ATTACH]168188[/ATTACH]

---

### Post by guillermolisi on 2010-09-01
En el log que pasaste encontre estos mensajes relacionados con el tema administracion de energia que podrian influir:
> 
[    0.358607] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.358607] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
...
...
[   10.405478] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function


Es decir, asi es como reconoce el hardware Linux. Habria que ver que sucede con el kernel de Windows como para comparar.

La configuracion del administrador de energia para mi esta bien, ahora, estara funcionando bien el backend del administrador de energia ? (lo que se ve es la interface grafica, no el administrador en si mismo).

---

### Post by Applelnx on 2010-09-07
Guillermo, como podria fijarme eso que me estas diciendo del funcionamiento del backend del administrador de energia?

La verdad que estuve buscando por google problemas similares pero por el  momento no encontre ninguna solucion :(

---

### Post by guillermolisi on 2010-09-07
Ahora veo que la bateria te dura menos porque el administrador de energia no puede controlar el brillo del display, una de las cosas que hace que la autonomia sea mayor o menor. Los errores que marque indicarian esa imposibilidad.

Que kernel estas usando ?

---

### Post by Applelnx on 2010-09-07
> **guillermolisi said:**
> Ahora veo que la bateria te dura menos porque el administrador de energia no puede controlar el brillo del display, una de las cosas que hace que la autonomia sea mayor o menor. Los errores que marque indicarian esa imposibilidad.

Que kernel estas usando ?

Linux version 2.6.32-24-generic

---

### Post by Applelnx on 2010-10-11
Bueno aparentemente pasaron la solucion para el kernel linux-2.6.36-rc6-git2. Esperemos que funcione.

[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31491.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg31491.html)

---


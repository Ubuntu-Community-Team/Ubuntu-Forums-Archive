---
title: "Lubuntu no carga GUI"
date: 2011-06-15
forum: Instalación y Actualización
---

### Post by TitoHL on 2011-06-15
Amigos:
Saludos a todos. Estoy recién aproximándome a Linux y hasta el momento he quemado 3 LiveCD. Puppy Linux, Xubuntu y Lubuntu. Lamentablemente, cuando trato de probar Lubuntu sólo me aparece esto en un Terminal en la esquina superior izquierda de la pantalla:

```
Loading the saved-state of the serial devices...                 [OK]
* Starting NTP server ntpd                                       [OK]
* Starting bluetooth
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic i686)

* Documentation:  http://help.ubuntu.com/


To run a command as administrator (user “root”), use “sudo <commnd>”.
See “man sudo_root” for details.

ubuntu@ubuntu:~$
```


¿Porqué no aparece la GUI? ¿Será un problema al cargar bluetooth?, que por cierto, mi equipo no tiene. ¿Habré descargado una versión de Lubuntu inadecuada para un Athlon 1800+ con 1Gb de RAM?
Con las otras distros no he tenido ningún problema. Realmente me gustaría probar Lubuntu.

---

### Post by asterix77 on 2011-06-16
Escribe startx en la terminal y ve si inicia el entorno gráfico, de lo contrario (si es que no se inicia), pega la salida aquí para tener alguna pista del problema.

También pega la salida del siguiente comando para ver el tipo de tarjeta gráfica.

$lspci | grep VGA

Saludos

---

### Post by TitoHL on 2011-06-17
Gracias por responder Asterix.
En la terminal coloqué startx y la salida fue:
```
xauth:    file /home/ubuntu/.Xauthority does not exist

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux ubuntu 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=es keyboard-configuration/layoutcode?=es
Build Date: 19 April 2011 03:33:17PM
xorg-server 2:1.10.1-ubuntu1 (for technical support please see http://www.inuntu.com/support)
Current version of pixman: 0.20.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the lastest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 17 17:23:32 2011
(==) Using system config directory "usr/share/X11/xorg.conf.d"
(EE) Failed to load module "fglrx" (module does exist, 0)
(II) [KMS] kernel modesetting enabled.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

waiting for X server to shut down  ddxSigGiveUp: Closing log
```

Después el comando $lspci | grep VGA no tubo ningún efecto. Pero la tarjeta de vídeo que uso es una Asus V7100Pro/SI416 (AGP) con un GPU NVIDIA GeForce2 MX/MX 400.
Lo probé en otro PC y pasa lo mismo. Pensé que el disco podría tener algún problema. Así que descargué un iso (versión 11.04), verifiqué el MD5 y lo quemé. Pero aún se repite el problema.
¿A qué se refiere con el módulo fglrx?

---

### Post by asterix77 on 2011-06-18
Al parecer tu problema es el driver de tu tarjeta de video que no está siendo reconocida por ubuntu, lo curioso es que te solicite el módulo fglrx que hasta donde sé, son para tarjetas ATI, siendo que tu tienes una nvidia, pero bueno, por eso era importante la salida de lspci para saber en forma exacta el ID del dispositivo.

Si no aparece nada con lspci | grep VGA, pega la salida del comando lspci a solas

El módulo fglrx de todos modos lo puedes descargar desde el sig. enlace, debes escoger el de tu distribución y arquitectura (32 ó 64 bit).

[https://launchpad.net/ubuntu/+source/fglrx-installer](https://launchpad.net/ubuntu/+source/fglrx-installer)

Para instalarlo desde la terminal primero nos situamos en donde esté la carpeta con el .deb,  si fuese necesario usamos el comando “cd” para desplazarnos a dicha  carpeta.

Luego escribimos esto:

$sudo dpkg -i nombredelpaquete.deb
[LEFT][COLOR=#000000]
Saludos
[/COLOR][/LEFT]

---

### Post by TitoHL on 2011-06-20
Tienes toda la razón Asterix. Coloqué la salida de la terminar de otro PC en que también hice pruebas y que tiene tarjeta ATI. La salida del mi PC dice en sus últimas líneas:

```
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 19 13:39:03 2011
(==) Using system config directory "usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does exist, 0)
(EE) Failed to load module "nv" (module does exist, 0)
resize called 1280  1024
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
xinit: connection to X server lost

waiting for X server to shut down  ddxSigGiveUp: Closing log
```

Y la salida de lspci | grep VGA es:

```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce 2 MX/MX 400] (rev b2)
```

Lo extraño es que la falla se produce en aproximadamente el 50% de las veces que intento arrancar con el LiveCD.
De a poco estoy aprendiendo a usar algunos comandos de la terminal, como cd, ls, pstree y pwd. Con esta información corregida, ¿cómo me aconsejas proceder?
¿Qué indica la línea xinit: connection to X server lost?

---

### Post by asterix77 on 2011-06-22
Hola Tito

No pude contestar antes debido a viajes e imposibilidad de conectarte....

Ahora al tema, ya me parecía que había algo raro, bueno puedes intentar hacer lo siguiente:

a) Descargar el driver  nvidia_geforce2_driver.run del siuiente link [http://www.sendspace.com/file/n79rwg](http://www.sendspace.com/file/n79rwg) y guardarlo en una carpeta conocida

b) Instalar el paquete nvidia-glx-185 desde Synaptic (se instalará también los paquetes dkms; nvdia-current; y nvidia-settings

c) Por terminal lo puedes instalar con el siguiente comando (automáticamente instalará los otros 3)

$sudo apt-get install nvidia-glx-185

d)  Una vez instalado todos los paquetes reinicia tu pc, lo más seguro es que te inicie en modo no gráfico (solo texto)

e) Logeate y acudes a la carpeta donde tengas el driver descargado, una vez en la carpeta escribes en la terminal sudo mas el nombre del paquete.run

$sudo nvidia_geforce2_driver.run

f) Después de esto, y si es que no hay problemas, debes reiniciar y deberías poder entrar ya a un entorno gráfico.

Espero que te sirva.

Saludos

---

### Post by TitoHL on 2011-06-27
Asterix77, muchas gracias por responder y disculpa la demora.
En estos día he tratado de seguir varios consejos, los cuales me han permitido iniciar el diagnóstico y tener una solución transitoria del problema.
Primero, las controladores de la tarjeta de video están instaladas y trabajando bien.
La interfaz gráfica de Lubuntu carga bien sólo en la mitad de los intentos, usando el LiveCD. Por lo tanto, se descartan como origen del problema.
Cuando la GUI no carga normalmente, una solución "parche" es instalar lxde-common, usando:
```
sudo apt-get install lxde-common
```
y para cargar LXDE uso
```
startx
```
No obstante, los menús, iconos, tema, etc. difieren de la GUI que carga Lubuntu por defecto.
Hasta ahora, he logrado determinar que el archivo startlubuntu incluye la línea:
```
exec /usr/bin/lxsession -s Lubuntu -e LXDE
```
con la cual se debería cargar la GUI de Lubuntu.
Tengo la teoría de que hay algo que no se instala, así que estoy tratando de averiguar si existen algunas discrepancias en algunos componentes de Lubuntu cuando se carga normalmente la GUI y cuando instalo lxde-common.
Ya que soy nuevo en Linux, supongo que debe existir un equivalente del Visor de sucesos de Windows que pueda facilitarme encontrar el problema con mayor precisión.

---

### Post by asterix77 on 2011-06-28
Bueno, al menos es un gran avance de que ya puedas tener una interfaz gráfica, con respecto al visor de sucesos, si existe:

Si quieres ver los sucesos del arranque del sistema, puedes usar en la terminal dmesg  con la opción de more o less para que te muestre el contenido por bloques.

$dmesg | more

Existe una forma gráfica más detallada que está dentro del paquete gnome-utils

$sudo apt-get install gnome-utils

Y después invocas por terminal

$gksudo gnome-system-log


Saludos

---

### Post by TitoHL on 2011-07-05
Gracias Asterix, muy buen dato. Gracias a él, me di la lata de comparar algunos logs ubicados en /var/log, cuando falla la carga de la GUI y cuando se carga normalmente. Estos son el resultado de las comparaciones:

**syslog**
Cuando no carga la GUI, contiene las líneas:
[INDENT]Jul 3 20:17:41 ubuntu kernel: [ 0.321044] tty tty28: hash matches
Jul 3 20:17:59 ubuntu init: lxdm main process (1439) terminated with status 1[/INDENT]
Cuando carga bien, contiene las líneas:
[INDENT]Jul 4 22:01:10 ubuntu kernel: [ 167.494371] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Jul 4 22:01:10 ubuntu kernel: [ 167.519923] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Jul 4 22:01:10 ubuntu kernel: [ 167.519935] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A[/INDENT]

**dmesg**
Cuando no carga la GUI se agregan las líneas:
[INDENT][ 0.321044] tty tty28: hash matches
[ 97.905692] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[ 97.905703] PCI: setting IRQ 4 as level-triggered
[ 97.905715] EMU10K1_Audigy 0000:00:0a.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4[/INDENT]

**kern.log**
Cuando no carga la GUI se agregan las líneas:
[INDENT]Jul 3 20:17:41 ubuntu kernel: [ 0.321044] tty tty28: hash matches[/INDENT]
Cuando carga bien, agrega las líneas:
[INDENT]Jul 4 22:01:10 ubuntu kernel: [ 167.494371] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Jul 4 22:01:10 ubuntu kernel: [ 167.519923] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Jul 4 22:01:10 ubuntu kernel: [ 167.519935] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
[/INDENT]
**auth.log**
Cuando no carga la GUI, se agregan:
[INDENT]Jul 4 00:18:21 ubuntu sudo: ubuntu : TTY=tty1 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/bin/su
Jul 4 00:18:21 ubuntu su[2680]: Successful su for root by root
Jul 4 00:18:21 ubuntu su[2680]: + /dev/tty1 root:root
Jul 4 00:18:21 ubuntu su[2680]: pam_unix(su:session): session opened for user root by ubuntu(uid=0)[/INDENT]
Cuando la GUI se carga normalmente, se agregan:
[INDENT]Jul 4 18:00:20 ubuntu lxdm-binary: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No such file or directory
Jul 4 18:00:20 ubuntu lxdm-binary: PAM adding faulty module: pam_gnome_keyring.so
Jul 4 18:00:20 ubuntu lxdm-binary: pam_unix(lxdm:session): session opened for user ubuntu by (uid=0)
Jul 4 18:00:36 ubuntu gnome-keyring-daemon[2764]: couldn't communicate with already running daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul 4 18:00:36 ubuntu gnome-keyring-daemon[2768]: couldn't communicate with already running daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2771]: GLib-GIO: Using the 'memory' GSettings backend. Your settings will not be saved or shared with other applications.
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2778]: GLib-GIO: Using the 'memory' GSettings backend. Your settings will not be saved or shared with other applications.
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2775]: GLib-GIO: Using the 'memory' GSettings backend. Your settings will not be saved or shared with other applications.
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2778]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2775]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2775]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Jul 4 18:00:37 ubuntu gnome-keyring-daemon[2771]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files
Jul 4 18:00:39 ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.16 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale es_ES.UTF-8)
Jul 4 22:05:13 ubuntu sudo: ubuntu : TTY=unknown ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/sbin/synaptic[/INDENT]

**lxdm.log**
Aunque parezca extraño, debido a las líneas que informan de errores, este es el archivo lxdm.log cuando Lubuntu arranca sin problemas:
```
** (process:1413): DEBUG: user ubuntu auth ok

** (process:1413): DEBUG: login user ubuntu session /usr/bin/startlubuntu lang (null)

xauth:  file /var/run/lxdm/lxdm-:0.auth does not exist
** Message: add xserver watch


X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=es keyboard-configuration/layoutcode?=es
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.20.2
   Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
   to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  4 18:00:11 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
resize called 1280 1024
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
resize called 1152 864
```


**Xorg.0.log**
Finalmente, cuando no se carga la GUI al final de Xorg.0.log aparecen las líneas:
[INDENT][ 1262.858] (II) Power Button: Close
[ 1262.858] (II) UnloadModule: "evdev"
[ 1262.858] (II) Unloading evdev
[ 1262.858] (II) Power Button: Close
[ 1262.858] (II) UnloadModule: "evdev"
[ 1262.858] (II) Unloading evdev
[ 1262.858] (II) AT Translated Set 2 keyboard: Close
[ 1262.858] (II) UnloadModule: "evdev"
[ 1262.858] (II) Unloading evdev
[ 1262.858] (II) ImPS/2 Generic Wheel Mouse: Close
[ 1262.858] (II) UnloadModule: "evdev"
[ 1262.859] (II) Unloading evdev
[ 1262.859] (II) NOUVEAU(0): NVLeaveVT is called.
[ 1262.859] (II) NOUVEAU(0): Closed GPU channel 1
[ 1262.873] ddxSigGiveUp: Closing log[/INDENT]
Mientras que cuando Lubuntu se carga con su GUI estas son reemplazadas por casi una centena de líneas del tipo:
[INDENT][ 131.787] (II) NOUVEAU(0): EDID vendor "MEI", prod id 3194
[ 131.787] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[ 131.787] (II) NOUVEAU(0): Modeline "1280x1024"x0.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 131.787] (II) NOUVEAU(0): Modeline "1024x768"x0.0 80.00 1024 1056 1152 1328 768 771 774 804 -hsync -vsync (60.2 kHz)
etc, etc...[/INDENT]
Disculpen la extensión del post, pero es hasta donde he llegado con los múltiples consejos que he recibido. Por último, tengo la esperanza que con una próxima versión de Lubuntu estos problemas desaparezcan.

---

### Post by TitoHL on 2011-08-19
Asterix, retomé el tema.
Para probar Lubuntu usaba Try Lubuntu without installing y a veces no se cargaba la GUI.
La solución es ingresar por la opción Install Lubuntu y en la primera ventana presionar el botón salir. Esto dejará corriendo Lubuntu desde el LiveCD sin problemas.
Además, instalé Lubuntu en el HDD y me siento muy cómodo con él.
Gracias por todos tus comentarios, he aprendido mucho.
Saludos.

---


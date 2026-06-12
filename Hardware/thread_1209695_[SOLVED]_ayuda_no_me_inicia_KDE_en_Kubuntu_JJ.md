---
title: "[SOLVED] ayuda no me inicia KDE en Kubuntu JJ"
date: 2009-07-10
forum: Hardware
---

### Post by r@fitiiixxx on 2009-07-10
Hola foro,

otra ves, tengo un problema, con Kubuntu 9.04 y su escritorio KDE

hoy mas temprano he intentado arreglar el problema que tengo desde que lo instalé al S.O. 
eran 6 actualizaciones que estaban "bloqueadas" y aparecian en el gestor de paquetes para actualizar pero no me dejaba... 

hoy me decidí a ver que era, y me fijé que varios eran cosas como "Kubuntu-restricted-extras update i386"
y algunos mas que tenían que ver con el Kernel... pero la verdad no me acuerdo que o cuales eran...

cuestión, me decidí a reinstalar los paquetes en cuestión, el Ubuntu restricted extras, echo esto me fui a jugar al Sauerbraten para hacer tiempo mientras se descargaba todo, mate un par de bichitos... salgo al escritorio, me pide de reiniciar, "bueno dale" digo... reinicio la pc... entro a la primer opción del grub...

y me aparece el modo consola como si hubiera apretado Ctrl + Alt + F2 COMO!!?? y además como que la pantalla flashea un poco como que anda mal o algo, y cuando me pide el login salta algo de que el demonio DNS/nosequemas a cesado la actividad, todo en ingles me lo dice.
Lo mas raro es que eran paquetes soportados por el gestor de paquetes, osea están ahí no los bajé de una pagina loca, mas creible si fueran los codecs de medibuntu pero todavia... como fallaron? porque fallaron? nadie lo sabe (no mentira solo yo no se capás uds. si saben) ahora estube puteando un buen rato, para cuando me cansé, intenté ver de iniciar en modo seguro.

 osea la opción de abajo que es el mismo kernel y todo pero "recovery mode", ahí le puse reparar entorno grafico, recuperar paquetes rotos y recuperar archivos, inicia todo bien, el entorno KDE que lindo... pero no tenía mis efectos de escritorio, y no los podía activar, y digo, 

"aaa claro esto es modo seguro, seguramente ahora reinicio y ya se arregló porque al comienzo puse recuperar entonrno grafico y todas las otras cosas"

reinicio... y nada, sigue igual, si entro al Kubuntu "principal" del GRUB no me carga el entorno grafico, es mas, me salió el tema del monitor de OUT OF RANGE en una vuelta, pero después no salió mas...

también probé de leer el sticky de *staar en la secc. HARDWARE pero no tiene que ver con mi problema ya que no fue después de actualizar drivers, si no despues de bajar unos paquetes del gestor de paquetes, el cual no me gusta mucho, me gustaba mas el Añadir y/o quitar programas de GNOME.

en este no sabes si agregaste el programa completo o solo una parte porque va por pedasos en paquetes, no es para novatos como yo :(
mi placa de video es una NVIDIA GeForce 8600 GT 512mb

Ojalá me ayuden y gracias de antemano

Salu2,

r@fitiiixxx

---

### Post by Hei Ku on 2009-07-10
Esto es problema de drivers, no de KDE.

Pone que te sale con lspci.

---

### Post by staar on 2009-07-10
si las actualizaciones estaban bloqueadas era por algo, algún conflicto tiene que haber habido, y si tenian que ver con el kernel, más todavía...

con un kernel anterior anda todo?

probaste reinstalar el driver de nvidia?

saludos

---

### Post by r@fitiiixxx on 2009-07-10
> **staar said:**
> si las actualizaciones estaban bloqueadas era por algo, algún conflicto tiene que haber habido, y si tenian que ver con el kernel, más todavía...

con un kernel anterior anda todo?

probaste reinstalar el driver de nvidia?

saludos

em, probé de reinstalar el driver ver. 180 recomendada devuelta en modo de recovery con el ultimo kernel y no pude, o porque era de recuperación o porque anda mal

y ahora para el resto del quote y para hei ku les digo que ahora mismo no puedo probarlo porque estoy con una descarga muy importante, cuando la termino me paso a kubuntu y testeo las cosas esas,

pd: yo no sabía si postearlo en soft o hard, pero como no había drivers de por medio, solo el entorno grafico, me pareció que iva en soft, sorry :S

gracias por responder =)

---

### Post by r@fitiiixxx on 2009-07-10
bueno hice las pruebas, primero paso a comentar que como sugirió staar, pruebe en un kernel anterior y si, anda perfecto, hasta los efectos de escritorio y todo, las opciones del grub me aparecen así:

```
Ubuntu 9.04, kernel 2.6.28-13-Generic  #este no anda
Ubuntu 9.04, kernel 2.6.28-13-Generic (recovery mode) #este anda pero sin drivers privativos
Ubuntu 9.04, kernel 2.6.28-11-Generic #este anda perfecto
Ubuntu 9.04, kernel 2.6.28-11-Generic #este no lo probé pero deve ser como el de arriba
Ubuntu 9.04, kernel 2.6.28-13-rt #no se que es
Ubuntu 9.04, kernel 2.6.28-13-rt (recovery mode) # no se que es menos todavia
#acá hay otra opción mas pero no se que es...
Other Operating Systems:
Windows XP Professional: Service Pack 2
```

para que se den una idea, igual seguramente es igual en todos lados el grub. yo como no se por las dudas... nunca está de más.

el kernel 2.6.28-11-Generic que me anda me fijé los controladores y si, está corriendo hasta con efectos de escritorio, con controlador de targetas NVIDIA ver. 180 [recomendada]

el kernel que me andubo solo tiene 3 actualizaciones que están bloqueadas:
-3 actualizaciones blokeadas:

>linux-headers-generic - 2.6.28.11.15 (i386)
*Generic Linux Kernel headers*

>amarok -2:2.0.2.mysql5.1.30-Oubuntu3 (i386)
*ease to use media player based n the KDE 4 technology platform*

>amarok-common - 2:2.0.2mysql5.1.30-Oubuntu3 (all)
*architecture independent files for Amarok*

ahora, probé el comando que pasó Hei Ku, el "lspci" y me salió esto:

```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)       
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600GT (rev a1)

```

ahí está toda la info que me pidieron, si me faltó algo diganme.

Salu2, ):P

r@fitiiixxx

---

### Post by staar on 2009-07-10
arrancá con el kernel nuevo, y cuando te tire a la consola, logueate y reinstalá los drivers ```
sudo apt-get --reinstall install nvidia-glx-180
```

saludos

---

### Post by guillermolisi on 2009-07-10
> Ubuntu 9.04, kernel 2.6.28-13-rt #no se que esLa sigla "rt" al final de la version del kernel indica que es un kernel Real Time.
Esos kernels son los de mas baja latencia y se usan para aplicaciones que procesan
datos en tiempo real, como controladores MIDI, editores de ondas de sonido, etc.

---

### Post by r@fitiiixxx on 2009-07-11
> **staar said:**
> arrancá con el kernel nuevo, y cuando te tire a la consola, logueate y reinstalá los drivers ```
sudo apt-get --reinstall install nvidia-glx-180
```saludos

weno estos días me ausenté, pero ahora ya estoy acá,

probé lo de reinstalar los drivers con el "$sudo apt-get --reinstall install nvidia-glx-180"

pero no tuve suerte, al reiniciar la pantalla me tiraba "monitor out of range 1280 x 720" y así con el boton del CPU tuve que reiniciar...

yo puse ese comando, enter y como vi que no cambiaba solo, reinicié, habré echo mal?

alguna otra idea? capas se me j***ó alguna configuración...

@guillermolisi: 
 gracias por la explicación :D igual no se que es baja latencia en este caso, ahora la busco en google :).  Se lo que es en los videojuegos pero no se como se aplicará a un kernel :O

---

### Post by staar on 2009-07-12
para cambiar entre consolas virtuales y el entorno gráfico, usá Ctrl + Alt + F1 a F6 para las consolas y F7 para el entorno gráfico, las 6 consolas siempre están ahí, aunque vos accedas directamente al entorno gráfico, usalas, te permiten manejar completamente el sistema...

si te tiraba out of range, pasate por [acá]("http://ubuntuforums.org/showthread.php?t=1183319"), ahí expliqué como arreglar eso...

saludos

---

### Post by r@fitiiixxx on 2009-07-12
> **staar said:**
> para cambiar entre consolas virtuales y el entorno gráfico, usá Ctrl + Alt + F1 a F6 para las consolas y F7 para el entorno gráfico, las 6 consolas siempre están ahí, aunque vos accedas directamente al entorno gráfico, usalas, te permiten manejar completamente el sistema...

si te tiraba out of range, pasate por [acá]("http://ubuntuforums.org/showthread.php?t=1183319"), ahí expliqué como arreglar eso...

saludos

gracias staar :D aunque no entendí que tengo que hacer con esas consolas virtuales, yo solo sabía de la que está en Ctrl + Alt + F2 . siempre es bueno saber que hay otras jeje.

te cuento que después de ver "Out of Range" hice reinicio y se volvió al modo consola otra ves, mañana mismo hago lo del tuto que preparaste, hoy no porque ya me voy a ir a dormir en un rato

mañana cuento como me fue...

---

### Post by r@fitiiixxx on 2009-07-13
hola gente, malas noticias...

no funcionó el tuto de staar, además la resolución del kernel viejo ahora se estropeó y se ve todo a 640x480, quedó horrible, ahora paso a explicar las cosas:

primero tuve que editar con el nano en modo consola el archivo citado en el tuto, y hacer esto
> [i]...Vamos hasta la sección Monitor, que debe ser similar a esta (puede variar):
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CRT-0" 
EndSection
```

y le agregamos dos valores, el VertRefresh y el HorizSync, dejándola así:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CRT-0" 
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection
```
...[/i]

yo estos valores ya los tenía, no hizo falta agregarlos, ahí supe que algo estaba mal.

> [i]...y le agregamos tres opciones, una para que no lea los datos desde el EDID, otra para indicarle la resolución deseada, y una última para indicarle algunas de las resoluciones que sabemos que el monitor es capaz de mostrar:
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "False"
    Option         "MetaModes" "1400x1050 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600"
    EndSubSection
```
EndSection
...[/i]
mi monitor es de resolución 1280x720 LCD widescreen a 16:9 creo... le puse esa y un par mas, como 640x480 y 840x480 (wide) en "Modes". yo creo que eso fue lo que desconfiguró el kernel viejo, ahora el kernel viejo me anda a 640x480 y se ve pesimo, me tuve que ir a win2 por ahora...
Guardé el archivo que se yo... y->
> [i]...Si estamos en una consola virtual, iniciar las X con
Code:
sudo /etc/init.d/gdm start
...[/i]

una sola frase a eso: > bash: command "/etc/init.d/gdm" not found
entonces mas abajo decía;
> *...Si estamos en Gnome, reiniciar sesión...*
bueno no estoy en Gnome, estoy en KDE pero deve aplicarse si el cmd de arriba no anda no?, bueno, reinicié y seguía igual además claro de que ahora el kernel viejo me anda con la resolución toda gorda, creo que es 640x480

una cosa, a mi este problema no me surgió reinstalando los drivers, yo creo que por eso hay muchas variables sueltas, y eso no hay que dejarlo pasar, porque lo mio no tuvo que ver con drivers de entrada, tuvo que ver con actualizaciones bloqueadas y que las busqué por el manejador de paquetes, el cual es algo dificil de manejar.

saben que es lo mas triste de todo esto?
que reinstalando todo Kubuntu creo que hubiera tardado menos :(
pero no puedo seguir haciendo eso, porque no tiene sentido.

---

### Post by staar on 2009-07-13
en kubuntu no se usa gdm sino kdm ```
sudo /etc/init.d/kdm start
``` sinceramente, cada vez me desconcierta más el driver de nvidia, aunque fue cosa mía, perdón, si en el kernel viejo te andaba bien la resolución, no tendrías que haber tocado los archivos de configuración ya que los dos kernels usan los mismos, y si funciona para uno, también para el otro, pero siempre podés volver a poner el xorg.conf como estaba antes, y usar el nvidia-settings para cambiar la resolución...

pero bueh, vamos a hacer las cosas como las tendríamos que haber hecho desde un principio, vamos a ver los logs, postea el contenido del archivo /var/log/Xorg.0.log que ahí seguro te dice porqué no arrancan las X... 

saludos

---

### Post by r@fitiiixxx on 2009-07-13
> **staar said:**
> en kubuntu no se usa gdm sino kdm ```
sudo /etc/init.d/kdm start
``` sinceramente, cada vez me desconcierta más el driver de nvidia, aunque fue cosa mía, perdón, si en el kernel viejo te andaba bien la resolución, no tendrías que haber tocado los archivos de configuración ya que los dos kernels usan los mismos, y si funciona para uno, también para el otro, pero siempre podés volver a poner el xorg.conf como estaba antes, y usar el nvidia-settings para cambiar la resolución...

pero bueh, vamos a hacer las cosas como las tendríamos que haber hecho desde un principio, vamos a ver los logs, postea el contenido del archivo /var/log/Xorg.0.log que ahí seguro te dice porqué no arrancan las X... 

saludos

aa sisi kdm!! me re suena! siempre que ponía sudo reboot en consola me saltaba algo de WARNING shuting down kdm. pero ni idea que era, además aparecía un segundo y se iva. ahora voy a buscar esa config, pero para que me ande por lo menos el kernel viejo, es necesario que ponga el archivo anterior como estaba antes? o alguna especificación especial que necesite saber antes de volver a retocar ese archivo.

ahora busco el log aquel y edito el mismo post asi no es doble. 

gracias por ayudar ^^

EDIT: estoy en Kubuntu, kernel viejo, o dios que está gordo jeje. la letra O es mas grande que mi dedo meñique jajaja.
e aquí el log "sudo kate /var/log/Xorg.0.log" (no lo modifiqué, solo para verlo le puse kate):
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux pieza 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 13 15:29:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation GeForce 8600GT rev 161, Mem @ 0xdf000000/16777216, 0xa0000000/536870912, 0xdc000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "MetaModes" "1280x720+0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.43.00.81
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GT at PCI:2:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x720+0+0"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event6"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device HID Keyboard Device
(**) HID Keyboard Device: always reports core events
(**) HID Keyboard Device: Device: "/dev/input/event4"
(II) HID Keyboard Device: Found 1 mouse buttons
(II) HID Keyboard Device: Found keys
(II) HID Keyboard Device: Configuring as keyboard
(**) HID Keyboard Device: YAxisMapping: buttons 4 and 5
(**) HID Keyboard Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID Keyboard Device: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID Keyboard Device: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) HID Keyboard Device: xkb_layout: "es"
(II) config/hal: Adding input device HID Keyboard Device
(**) HID Keyboard Device: always reports core events
(**) HID Keyboard Device: Device: "/dev/input/event3"
(II) HID Keyboard Device: Found keys
(II) HID Keyboard Device: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID Keyboard Device" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID Keyboard Device: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID Keyboard Device: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) HID Keyboard Device: xkb_layout: "es"

```

---

### Post by staar on 2009-07-13
el problema es que con el kernel viejo las X si andan, entonces no sale ningún error en el log, arrancá con el nuevo y hace una copia del log a tu home ```
cp /var/log/Xorg.0.log ~/
``` y después subilo...

la resolución no la podes modificar con el nvidia-settings?

saludos

---

### Post by r@fitiiixxx on 2009-07-13
> **staar said:**
> el problema es que con el kernel viejo las X si andan, entonces no sale ningún error en el log, arrancá con el nuevo y hace una copia del log a tu home ```
cp /var/log/Xorg.0.log ~/
``` y después subilo...

la resolución no la podes modificar con el nvidia-settings?

saludos

:O a bueno, no sabía che, perdón jeje, con respecto a la resolución del kernel viejo, mas simple, reestablecí el archivo a su origen usando un backup que se auto "fabricó" y reinicie y MAGIA tenía el escritorio 1280x720 por lo menos en el kernel viejo :D.
ahora si, acá está el log, lo copié desde el kernel nuevo y verifiqué que se halla pasado bien :) , ahora si este es el log (igual puede que halla fallado, yo desde la consola puse el cmd que me pasaste igualito y dsps me fije con el nano):
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux pieza 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 13 15:56:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation GeForce 8600GT rev 161, Mem @ 0xdf000000/16777216, 0xa0000000/536870912, 0xdc000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

para concluir, este post aunque el thread no ha terminado e aprendido algo, yo ni enterado de que existía el "nano", está muy bueno si solo estas en consola! es muy util, al menos aprendí algo por ahora :D

---

### Post by staar on 2009-07-13
bueno, ahora estamos seguros de que, por alguna razón, el nuevo kernel no puede cargar el módulo del driver nvidia...

primero que nada, como instalas los drivers? con el .run desde la página de Nvidia o desde la herramienta de ubuntu?

puede que te falten algunos paquetes, fijate si tenés instalados estos (lo podés hacer desde el kernel viejo si querés):
-linux-headers-2.6.28-13
-linux-headers-2.6.28-13-generic
-linux-restricted-modules-2.6.28-13-generic

saludos

---

### Post by r@fitiiixxx on 2009-07-14
> **staar said:**
> bueno, ahora estamos seguros de que, por alguna razón, el nuevo kernel no puede cargar el módulo del driver nvidia...

primero que nada, como instalas los drivers? con el .run desde la página de Nvidia o desde la herramienta de ubuntu?

puede que te falten algunos paquetes, fijate si tenés instalados estos (lo podés hacer desde el kernel viejo si querés):
-linux-headers-2.6.28-13
-linux-headers-2.6.28-13-generic
-linux-restricted-modules-2.6.28-13-generic

saludos

los drivers los instalé con la herramienta que viene en Kubuntu JJ en "Aplicaciones > Sistema >Hardware Drivers" desde ahí los instalo.
 igual reinstalé los paquetes que me pediste
y ME ANDA :D no se como agradecerte lo suficiente che, jejeee me arreglaste el kernel nuevo, necesitaba instalar esos paquetes al parecer. muchísimas gracias :)

todavía me queda el problema de dos actualizaciones bloqueadas

X 2 actualizaciones bloqueadas:

>amarok - 2:2.0.2mysql5.1.30-Oubuntu3 (i386)
easy to use media player based on the KDE 4 technologoy platform

>amarok-common - 2:2.0.2mysql5.1.30-Oubuntu3 (all)
arhitecture independent files for Amarok

la verdad es que tengo miedo de reinstalar esos paquetes porque a ver si me pasa lo de recién, creo que mejor los dejo como están o creo un nuevo thread en software acerca de estos paquetes, porque ahí dice que son de Amarok así que va en soft jeje.

para todo lo demás Kubuntu me anda re bien ahora, mil gracias otra ves y un Salu2 ):P

r@fitiiixxx

---


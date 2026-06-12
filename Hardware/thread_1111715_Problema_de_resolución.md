---
title: "Problema de resolución"
date: 2009-03-30
forum: Hardware
---

### Post by exegeses on 2009-03-30
acabo de actualizar a 8.04 y al reiniciar, me cambia la resolución.

quiero cambiarla yendo a > preferencias > Rasolución de pantalla  
y me sale el siguiente mensaje: 

```
El servidor X no soporta la extensión XRandR. Los cambios de resolución de la pantalla durante la sesión no están disponibles.
```

la verdad, parece una boludés, pero me molesta mucho no poder usar mi resolución de pantalla (1680 x 1050 - 60hz)

desde ya, muchas gracias.

---

### Post by staar on 2009-03-30
dos preguntas: que placa de video tenes? para saberlo podes postear la salida de correr, en una consola, el comando ```
lspci
```

otra, tenés instalados los drivers de tu placa?

saludos

---

### Post by exegeses on 2009-03-30
la placa es una ATI Technologies Inc RV380 [Radeon X600]


el resultado del comando es:

```
:~$ lspci

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
06:03.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)
```

creo que todos los drivers están como corresponden. los privativos estásn habilitados.

dónde podrá ser el problema???

desde ya, muchas gracias

---

### Post by staar on 2009-03-31
oka, ya contamos con mas datos ;-), lo que pasa es que ubuntu muchisimas veces no reconoce bien el monitor, suerte que estas en hardy y esa versión todavia tiene una interfaz grafica para seleccionar el monitor (en las nuevas versiones no está, lo que hace todo un poco mas dificil ¬¬), bueno, apretá Alt-F2 y corre ```
displayconfig-gtk
``` ahi seleccioná tu monitor (o uno similar), después, no me acuerdo si lo pide, pero reinicia el servidor gráfico (Ctrl-Alt-Backspace), y probá...

si esto no te funciona va ha haber que modificar el xorg.conf, pero primero fijate si eso te sirve...

saludos

---

### Post by exegeses on 2009-03-31
ya probé con didpasyconfig-gtk y me cambia la configuración. el tema es que va MUY lento, INSOPORTABLEMENTE lento, a nivel que no puedo escuchar música y scrolear en este foro...

my xorg.conf quedó así:

```
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection
```


ah, tengo un Samsung T220 (dvi 22" wide)
se podrá solucionar???
desde ya, muchas gracias.

---

### Post by exegeses on 2009-03-31
por favor, alguien me puede ayudar?
es terrible lo lento quye funciona todo
con este configuración.
logro ver a 1680x1050, pero lentísimo, no me sirve.
no puedo trabajar.

gracias

---

### Post by hictio on 2009-03-31
Consulta:
De dónde sacaste esos valores de Horizontal sync y Vertical refresh?
Con la herramienta que te recomendaron, seleccionaste exactamente tu modelo de monitor, o uno genérico de características similares?

---

### Post by exegeses on 2009-04-01
> **hictio said:**
> Consulta:
De dónde sacaste esos valores de Horizontal sync y Vertical refresh?
Con la herramienta que te recomendaron, seleccionaste exactamente tu modelo de monitor, o uno genérico de características similares?


primero, gracias hictio por tu respuesta.

acerca del problema:


este es el mensaje que me sale al tratar de cambiar la resolución de pantalla en  > **Preferencias** > **Resolución de pantalla** 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108238&stc=1&d=1238562705[/IMG]

después, me fijé que estuvieran los controladores privativos.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108239&stc=1&d=1238562705[/IMG]

y finalmente, al tirar el comando ```
displayconfig-gtk
```
veo los siguientes monitores

si me fijo en Samsung veo estos:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108240&stc=1&d=1238562705[/IMG]

si me fijo en genéricos, veo estos:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108241&stc=1&d=1238562705[/IMG]

elegí uno del listado y de ahí salieron esos valores de Horizontal sync y Vertical refresh (que no sé cuales son) :cry:

como no creo haber encontrado mi tu modelo de monitor, ¿cual sería uno genérico de características similares que debería elegir?
[-o<  por favor, ¿me dan una mano?

la verdad, es un dolor de (*)(*) usar la gráfica de esta manera. estuve toda la tarde trabajando en window$, ya que no podía programar en mi Hardy... :cry:

y encima estuve hasta esta hora, ya que se me hizo todo más lento.
por favor si alguien me ayuda

[-o< 

desde ya, muchas gracias.

---

### Post by staar on 2009-04-01
una solución podria ser poner a mano en el xorg.conf los rangos de vertical refresh y de horizontal sync, buscalos en el manual del monitor, que seguro están...

saludos

---

### Post by hictio on 2009-04-01
> **staar said:**
> una solución podria ser poner a mano en el xorg.conf los rangos de vertical refresh y de horizontal sync, buscalos en el manual del monitor, que seguro están...

saludos

Te diría de una, probá esa opción, y además, sacá (comentá) los modelines. La verdad, nunca había escuchado ni visto que X Window ande "lento" por un problema de resolución.
Es realmente bizarro el problema.
Pero, por otro lado, nunca usé ATI, siempre o tarjetas NVIDIA, o totalmente pedorras e ignotas, sin efectos de ningún tipo :)

De hecho, la máquina que uso para hacer tests de Linux, es una [catramina sideral](http://oesediez.blogspot.com/search/label/Orbis%20Tertius), pero X Window/ Gnome nunca me dio problemas (excepto lo lógico por lo viejo del hardware)

Un par de consejos más para que puedas trabajar sin esperar al GUI -que deber ser una pesadilla...-.
Si podés, logeate via SSH a tu máquina, si tenés instalado el openssh-server; sino, loggeate normal, y pasate a una consola vitual, y editá desde el CLI, si te sentís cómodo, total es simple lo que hay que hacer.

Para pasarte a la consola virtual, Ctrl + Alt + F2 (al F5); lo mismo pero con F7 para volver al GUI.
Una vez editado, forzás un re-init del GUI con Ctrl + Alt + Backspace, podés hacerlo en la pantalla de login, sin necesidad de iniciar tu sesión.
Como siempre, hacé backups de los archivos antes de editarlos, por si necesitás algo de una versión vieja, o necesitás hacer roll back.

---

### Post by exegeses on 2009-04-01
> **staar said:**
> una solución podria ser poner a mano en el xorg.conf los rangos de vertical refresh y de horizontal sync, buscalos en el manual del monitor, que seguro están...

saludos

acabo de ver el manual del monitor. ahi encuentro lo siguiente:

Sincronización Horizontal    30 ~ 81 kHz

Sincronización Vertical      56 ~ 75 Hz


y mi pregunta es la siguiente
debería cambiar esto:
```
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
[COLOR="DarkRed"]	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0[/COLOR]
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection
```

por esto:
```
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
[COLOR="DarkRed"]	Horizsync	30-81
	Vertrefresh	56.0 - 75.0[/COLOR]
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection
```

hay algún otro parámetro que deba cambiar?
gracias.

---

### Post by staar on 2009-04-01
exactamente, pero en Horizsync pone los decimales, te quedaría 30.0-81.0, probá y contanos...

ah, y comenta los modelines, como bien te sugirió hictio, pone un # antes de cada línea que empieze con "modeline"...

saludos

---

### Post by exegeses on 2009-04-01
> **staar said:**
> exactamente, pero en Horizsync pone los decimales, te quedaría 30.0-81.0, probá y contanos...

ah, y comenta los modelines, como bien te sugirió hictio, pone un # antes de cada línea que empieze con "modeline"...

saludos


buno, modifiqué los valores, reinicié la gráfica. y lo que pasa es peor incluso. 
veo esto:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108314&stc=1&d=1238613239[/IMG]

veo el foro rojo. sigue lento, muevo una ventana y demora un año en moverse, escalo una ventana y demora otro año.
ni hablar de los efectos al cerrar!!!
ya me las quiero cortar!

digo, bueno, veamos si reiniciamos...
reinicié el sistema y ahora el foro se vé amarillo!!!  si, si, lo que en la captura ven rojo, yo lo veo amarillo. 
ni me dá para hacer una captura. ya me puso de los pelos.

ya no sé que hacer. no puede ser que esto sea como windoor$, que sólo haya que reinstalar. encima tengo backup de archivos y servicios. todo.
me hubiese llevado menos tiempo, pero no creo sea la solución. de cabaza dura ahora lo quiero solucionar!

igual entre cierre de una ventana y movida de mouse, me voy a poner a ver si existe un quanta+ para windoor$ o algo parecido para las ventanas del lado oscuro.

bueno, ya me desahogué.
ahora veamos, mi xorg.conf quedó así:


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" #     
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #     
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56-75
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" #     
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #     
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

me parece que el problema es otro.
no es un tema de vesa-vga???
no sé, ni idea. 
no hay algún comando como xconfig-configaramelolareconch@detum@dre

me parece que debe haber. además de tanta fruta que mandé, en cualquier momento me dice que el monitor es un:

[COLOR="DarkRed"]**EPSON Longvie Orbis Calorama**[/COLOR]

bueno, la ayuda viene muy bien. es sólo que necesitaba "blow up some steem"
saludos

---

### Post by hictio on 2009-04-01
Ja Ja JA JA JA
Tenés la máquina poseída!!!!!
Fuera de broma, el foro está actuando raro hoy, en Safari, desde Os X, se amarillo patito y/o naranjita! :p :D
Será una hoja de estilo o algo así?
No es tu máquina.

[URL=http://img145.imageshack.us/img145/4476/010409171151quicksilver.jpg]
[IMG]http://img145.imageshack.us/img145/4476/010409171151quicksilver.th.jpg[/IMG]
[/URL]

---

### Post by hictio on 2009-04-01
Estaba viendo el xorg.conf que posteaste arriba.
Hay algo que no entiendo, tenés 2 monitores en uso actualmente?

---

### Post by exegeses on 2009-04-01
> **hictio said:**
> Ja Ja JA JA JA
Tenés la máquina poseída!!!!!
Fuera de broma, el foro está actuando raro hoy, en Safari, desde Os X, se amarillo patito y/o naranjita! :p :D
Será una hoja de estilo o algo así?
No es tu máquina.

[URL=http://img145.imageshack.us/img145/4476/010409171151quicksilver.jpg]
[IMG]http://img145.imageshack.us/img145/4476/010409171151quicksilver.th.jpg[/IMG]
[/URL]

ufff, menos mal. ya estaba buscando a los elefantes que habían orinado mi teclado ;)
al menos comparto alguna pena :D 
puede ser que haya trulado la css. me fijo a ver si encuentro el problema así avisamos.
aunque la verdad:      "Merry April's Fool"   :tongue:

> **hictio said:**
> Estaba viendo el xorg.conf que posteaste arriba.
Hay algo que no entiendo, tenés 2 monitores en uso actualmente?

ahora no tengo dos monitores, los he tenido en algún momento, pero no ahora. y no creo tenerlos hasta no solucionar esto.

gracias hictio por el aguante.

---

### Post by hictio on 2009-04-01
Okas, sin 2 monitores, etc, agarré el xorg.conf que posteaste, y lo limpié un poco, probalo a ver si te camina.
Ante la duda, o si ves algo raro, siempre lo podés matar con Ctrl + Alt + Backspace, o mejor, pasate a una consola virtual, para revertir los cambios.
Acordate de hacer backup, siempre, por si tenés que volver para atrás (aunque ahora parezca una pesadilla, puede ser que se ponga peor :)  Naaaaaa! Pero por si acaso )

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

###################
## Keyboard
###################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection


###################
## Mouse
###################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

###################
## Effects
###################
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection


###################
## Display
###################
Section "monitor"    
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56-75
EndSection


###################
## Video card
###################
Section "device"     
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection


##############################
## Everything, all together
##############################
Section "screen"
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050" "1600x1024"
	EndSubSection
EndSection

# EoF #

```

---

### Post by exegeses on 2009-04-01
hictio:

probé esa configuración y la verdad, funca un toque más lento.
nunca pensé que hubiese algo más lento que la respuesta de este monitor.
tiene menos reacción que una babosa!!!

muevo una ventana y se arrastra una hora hasta llegar a destino, mueo la rueda del mouse y le duele subir a bajar en el browser!
(hasta mi abuelito se aburrió y se fue a mirar por el balcón :tongue: )

bueno, no se, si muevo una ventana dibuja unas líneas verticales muy finas. incluso haciendo click en el desktop dibuja cada tanto esas líneas.

me parece que es otra cosa.
no habrá algún conflicto con compiz-gtk-ymca-tdk-usb-afa-kgb-eaeapp?

sorry por las pavadas, pero la verdad, ya es hora que le ponga algo de onda y me ría de mi pena.
gracias por el tiempo.

seguro que con mi sugerencia de conflicto se soluciona ;)
saludos

---

### Post by hictio on 2009-04-01
Será algo del driver de ATI?
Por los screenshots que posteaste, tenés los Desktop Effects funcionando, verdad?

Encontré estos reportes de bugs:

[Ati Radeon 9200 extremely slow in Gutsy](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/145715)
[X locks with lots of "tossed event which came in late. mieqEnequeue: out-of-order valuator event; dropping."](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/184430)
[xserver freezes regularly](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173653)

Algún otro usuario con Hardy y ATI que pueda postear algo?

---

### Post by Hei Ku on 2009-04-01
Hay algo que no entiendo. Supuestamente estas usando drivers privativos, pero tu xorg.conf dice otra cosa.
Con esa placa deberias tener una buena performance de 3d.

Podes postear el resultado de este comando?

```

glxinfo |grep vendor

```

---

### Post by Hei Ku on 2009-04-01
Leyendo un poco mas, si el driver propietario te aparece como habilitado, pero el xorg.conf esta configurado para usar el driver libre "ati", entonces no te habilita el 3D y por eso te anda lentisimo.
Si te figura como habilitado, entonces pone esto:

```

sudo apt-get remove --purge xorg-driver-fglrx

```

---

### Post by exegeses on 2009-04-01
> **Hei Ku said:**
> Hay algo que no entiendo. Supuestamente estas usando drivers privativos, pero tu xorg.conf dice otra cosa.
Con esa placa deberias tener una buena performance de 3d.

Podes postear el resultado de este comando?

```

glxinfo |grep vendor

```

acá está el resultado del comando:
```
:~$ glxinfo |grep vendor

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org

```
domo arigatô Hei Ku-san

---

### Post by Hei Ku on 2009-04-01
Ok. Entonces no deberías tener el driver privativo.

Corre lo que te dije en el segundo post:

```

sudo apt-get remove --purge xorg-driver-fglrx

```

Gasshô

---

### Post by exegeses on 2009-04-01
> **Hei Ku said:**
> Ok. Entonces no deberías tener el driver privativo.

Corre lo que te dije en el segundo post:

```

sudo apt-get remove --purge xorg-driver-fglrx

```

Gasshô

bueno, corrí el comando, desinstaló driver...
pidió reinicio. reincié...
pidió configuración del monitor. configuré...

truló de nuevo...(a 800 x 600)

intenté configurar el monitor para que tenga mayor resolución.

entonces hago:
```
:~$ sudo displayconfig-gtk
awk: cannot open /var/log/Xorg.1.log (No such file or directory)
warning: failed to get module paths from '/var/log/Xorg.1.log' - falling back to default
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

```


veamos que tenemos ahora:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108238&stc=1&d=1238562705[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108352&stc=1&d=1238638112[/IMG]

me fijo cómo está el xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

```
:~$ glxinfo |grep vendor

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
```


creo que estoy en el mismo punto que antes.
seguro algo hice mal...


por lo que veo debería desinstalar de nuevo driver privativo.

```
sudo apt-get remove --purge xorg-driver-fglrx
```

calculo que otra vez voy a tener 800x600. el team es ahí, cómo sigo????
please, estamos cerca de dejarlo listo y funcionando.
desde ya, muchas, pero muchas gracias por su tiempo
ganbatte kudasai

(y perdón si contesto mal, ya me tiene ####)

> como cadorcha debería quedar el xorg.conf!!!!!

---

### Post by hictio on 2009-04-01
Cuando te "queda" en 800x600, los Desktop Effects funcionan?
Podés llegar a probar, nuevamente, cuando está en 800x600, de editar el xorg.conf, y agregarle la resolución deseada en la línea:

```

Modes		"1680x1050" "1600x1024"

```

De paso, fijate si los valores de Horizontal Sync y Vertical Refresh están correctos.

---

### Post by Hei Ku on 2009-04-02
Este es el tutorial que deberias seguir.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

De acuerdo a eso, pone:

```

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

```

Despues de esto, reinicia el X y postea el resultado de esto:
```

glxinfo | grep "direct rendering"

```

Y si seguis teniendo quilombos, postea de vuelta tu xorg.conf y lo vamos arreglando.


Por alguna razon, tu placa deberia tomar bien el driver libre pero te instalo los privativos, y ahi se armo el lio. :S

---

### Post by exegeses on 2009-04-02
ok, entonces:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```

```
CTRL+ALT+BACKSPACE
```

(todo sigue igual...
así que...)

```
glxinfo | grep "direct rendering"

No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

```
glxinfo -LIBGL_DEBUG=verbose | grep "direct rendering"

-i: Force an indirect rendering context.
```

como creo que mandé fruta...

```
 glxinfo | grep -v "direct rendering"

name of display: :1.0
display: :1  screen: 0
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 16  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

como no entiendo nada, 
creo que lo que sigue es:  sudo gedit /etc/X11/xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

muchas gracias por el esfuerzo. creo que se va a solucionar. me vienen bárbaro la ayuda y espero aprender.

ah, una cosa: en mi 7.10 GG todo funcionaba perfecto. se truló todo al actualizar al HH. lo había dicho en el primer post, pero por las dudas, recuerdo.

muchas gracias nuevamente y gambarô (vamos que podemos!)
saludos

---

### Post by Hei Ku on 2009-04-02
Acá te paso tu xorg.conf "tocado" y ordenado un poco. Figuraban 2 placas de video, puede ser?


```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"monitor1"
	SubSection "Display"
		Modes		"800x600" "1680x1050" "1600x1024"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection


Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


```


La verdad es que tu xorg.conf es un descontrol. Traté de arreglarlo un poco, pero si con esto no funciona vamos a tener que seguir ordenandolo.

---

### Post by exegeses on 2009-04-02
bueno, veamos:

cambio el xorg.conf por el que me pasaste


CTRL+ALT+BACKSPACE


CHAN.wav! ;)
la ventana dice:

"¿otra vez vos?, bueno, te paso el mensaje que tengo que pasarte:
el coso este está en baja resolución, ¿lo desea configurar o no?"
  [LIST]
     [*]sí, lo deseo, amo.
     [*]no, ya tiré, gracias.
     [*]none of the above.
   [/LIST]

luego de aceptar, me aparece la configuración del monitor, elijo uno, pero lo digo DETECTAR y selecciono el que me detecta automáticamente (sorry si mandé fruta, me pareció logico para empezar de nuevo).
le doy aceptar.


la ventana dice:

"¿todavía seguis acá?  bueno, te paso el mensaje que tengo que pasarte:
no te olvides de reiniciar para que los cambios blablabla..."

...
...

CHAN.wav! ;)
800x600 en un monitor de 22!!! imaginense que los íconos me aplastaron contra la pared de la habitación.

reinicio
...
...
SUPERCHAN.wav
sigue lento, pero a 1680x1050.
sigue el XRandR.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

creo que se genera así porque le puse DETECTAR cuando elijo el monitor.
me parece que ahí se desbarajusta todo.

(ya no sé como darme ánimos...)

---

### Post by Hei Ku on 2009-04-02
Te arma un desastre, y termina todo repetido en el archivo.

Vamos de cero.

Tenés una sola placa de video?
Tenés un solo monitor? Supongo que los valores de refresco son los que dice ahi, no?

Y si aparece el XRandr otra vez, ponele que no haga nada, porque no esta colaborando. :D

---

### Post by exegeses on 2009-04-02
esta momia vé dos placas de video!!!
tengo una sola, eso con absoluta seguridad.

por ahi tengo los backups de los xorg.conf que tenía antes, acá hay uno que me pasó hictio.
calculo que limpiando un poco se podrá utilizar alguno.

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" #     
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #     
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56-75
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" #     
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #     
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

no se dan una idea lo que me cuesta postear. hacer scroll es doloroso.
abrir y cerrar una ventana duele, pero ya me acostumbré.
mover una ventana simplemente es un sufrimiento.
no quiero volver a windoor$

antes en GG funcionaba todo y de toque.
ya no sé que hacer.
gracias por todo el tiempo que le estan dedicando.
bueno, ya me desahogue.
ahora, veamos cómo seguimos.

---

### Post by exegeses on 2009-04-02
> **Hei Ku said:**
> Te arma un desastre, y termina todo repetido en el archivo.

Vamos de cero.

Tenés una sola placa de video?
Tenés un solo monitor? Supongo que los valores de refresco son los que dice ahi, no?

Y si aparece el XRandr otra vez, ponele que no haga nada, porque no esta colaborando. :D

domo arigatô Hei Ku san.
respondí tarde, porque me cuesta postear. en cualquier momento me paso al eliks2 ;)

veamos:  
tengo una sólo placa de video.
tengo un sólo monitor conectado.
me fijé en las especificaciones técnicas del Samsung T220 y dice que son
Sincronización Horizontal 30 ~ 81 kHz
Sincronización Vertical 56 ~ 75 Hz

el XRandrR se puede ir a hacer una colostomía, no le pone nada de onda a esto.

ganbatte kudasai.

---

### Post by hictio on 2009-04-02
> **exegeses said:**
> domo arigatô Hei Ku san.
respondí tarde, porque me cuesta postear. en cualquier momento me paso al eliks2 ;)

veamos:  
tengo una sólo placa de video.
tengo un sólo monitor conectado.
me fijé en las especificaciones técnicas del Samsung T220 y dice que son
Sincronización Horizontal 30 ~ 81 kHz
Sincronización Vertical 56 ~ 75 Hz

el XRandrR se puede ir a hacer una colostomía, no le pone nada de onda a esto.

ganbatte kudasai.

Yo te había pasado un xorg.conf ordenado (digamos), no se porqué la herramienta de auto detección que usás te detecta 2 monitores y 2 tarjetas, eso lo había dejado afuera del que postee.
Si mal no recuerdo, lo probaste, y decías que seguía lento.
Agarrá el xorg.conf que te pasé y editalo para que use el driver que dice Hei Ku que es el que hay que usar, eso lo probaste?

Otra cosa, si te es tan complejo por lo lento, pasate a una consola virtual, o si tenes otra máquina en red, instalale openssh-server a la linux con HH, y haces todas las ediciones (y copias de archivo, etc) sin tener que soportar la lentitud del GUI, por lo menos, hasta que se arregle el problema.

---

### Post by Hei Ku on 2009-04-02
Aca te paso uno modificado.

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-75.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600" "1600x1024" "1600x1050"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Default Screen" 0 0
EndSection


```

---

### Post by exegeses on 2009-04-02
a ver:

en el xorg.conf hay cosas que están bien. 
por ejemplo:

```
#######################
##  Teclado 
#######################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

#######################
##  Mouse 
#######################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection
```

eso no se toca. listo.

pero el video cómo debería ser?
yo tengo esto:
```
#######################
##  Video 
#######################
Section "Device"
	Identifier	"Configured Video Device"
[COLOR="DarkRed"]**	Driver		"vesa"**[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
[COLOR="DarkGreen"]**		Modes		"800x600"**[/COLOR]
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
[COLOR="Indigo"][B]Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection[/B][/COLOR]

```

resalté algunas partes para preguntar:

en Device donde dice
[COLOR="DarkRed"]**	Driver		"vesa"**[/COLOR]
no debería decir
[COLOR="DarkRed"]**	Driver		"ati"**[/COLOR]

####################################

en Screen
donde dice
[COLOR="DarkGreen"]**		Modes		"800x600"**[/COLOR]
puedo poner:
[COLOR="DarkGreen"]**		Modes		"800x600" "1680x1050"**[/COLOR]

####################################

y en [COLOR="Indigo"]**Section "Module" y en Section "device" # **[/COLOR] calculo que está bien, pero no sé. si eso está bien. podemos seguir.

(no se dan una idea lo que me cuesta postear. espero poder solucionarlo y navegar y usar la gráfica con placer.)

bueno, mi xorg.conf sigue así:
```
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

```

después hay referecnia a otra placa de video que no tengo y calculo hay que borrar y hay referencia a otro monitor que no tengo y calculo hay que borrar también.

si me dan una mano hasta acá, creo que se habrá avanzado un buen trecho.
saludos

---

### Post by Hei Ku on 2009-04-02
Ahi te pase uno modificado, donde le saque las partes repetidas.

---

### Post by exegeses on 2009-04-02
> **Hei Ku said:**
> Ahi te pase uno modificado, donde le saque las partes repetidas.

me lo pasaste por email? por MP?

bueno, aun no llegó, ya llegará.
domo arigatô gozaimasu

por lo pronto, sigo mirando y veo que no están especificados los valores
	Horizsync	30-81
	Vertrefresh	56-75

no debería tener algo como esto:
```
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75

```

por lo pronto mi email es mi nick [@] gmail.com

ganbarimasu &#38929;&#24373;&#12426;&#12414;&#12377;

---

### Post by Hei Ku on 2009-04-02
Fijate en el post #34

---

### Post by hictio on 2009-04-02
En el xorg.conf del post #34, la línea de Modes, no debería ser así:

```

	SubSection "Display"
		Modes		"1600x1050" "1600x1024" "800x600"
	EndSubSection

```

Asi usa por defecto la resolución máxima.

---

### Post by Hei Ku on 2009-04-02
Tenés razón. La resolución deberia empezar con la mas grande. Mi error, porque mi configuracion no tiene esa parte ya.

---

### Post by exegeses on 2009-04-02
> **Hei Ku said:**
> Fijate en el post #34

> **hictio said:**
> En el xorg.conf del post #34, la línea de Modes, no debería ser así:

```

	SubSection "Display"
		Modes		"1600x1050" "1600x1024" "800x600"
	EndSubSection

```

Asi usa por defecto la resolución máxima.

bueno, ahora hagamos backup...
edité el xorg.conf y lo dejé así:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#######################
##  Teclado 
#######################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

#######################
##  Mouse 
#######################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

#######################
##  Video 
#######################
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
        BusID           "PCI:1:0:0"
EndSection

#######################
##  Monitor 
#######################
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-75.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

#######################
##  Pantalla 
#######################
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection

```

reinciamos gráfica y veamos qué pasa.
a ver si nos responde un TADA.wav ;)
BRB

---

### Post by Hei Ku on 2009-04-02
La parte de Screen y ScreenLayout estan mal.
Deberian ser asi:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1600x1050" "1600x1024" "800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Default Screen" 0 0
EndSection

```

---

### Post by exegeses on 2009-04-02
CHAN.wav
SUPERCHAN.wav
CHAN.wav
SUPERCHAN.wav

pantalla que dice...
"el coso este está en baja resolución, ¿lo desea configurar o no?"

[LIST]
[*]si, lo deseo, amo.
[*]no, ya tiré, gracias.
[*]none of the above.
[/LIST]

selecciono la configuración del monitor, elijo el samsung con los valores de sincronía que me corresponden.
le doy aceptar...


truló de nuevo...(a 800 x 600)
digo, bueno, no pasa naranja, voy a preferencias a cambiar el monitor...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108449&stc=1&d=1238712174[/IMG]

no lo reconoce...
no cambié nada, lo dejé así.

funcionar, funciona a la velocidad debida, pero los íconos me están aplastando contra la pared. a 800x600 es inhumano

digo... a ver los efectos...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108450&stc=1&d=1238712174[/IMG]

no están habilitados. no los voy a habilitar.
paso cómo está el xorg.conf ahora.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

no cambié nada, a ver si se puede solucionar algo.
(casi no me puedo mover en la habitación con las ventanas e íconos a este tamaño.)

---

### Post by exegeses on 2009-04-02
> **Hei Ku said:**
> La parte de Screen y ScreenLayout estan mal.
Deberian ser asi:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1600x1050" "1600x1024" "800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Default Screen" 0 0
EndSection

```


cambio xorg.conf y lo dejo así:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#######################
##  Teclado 
#######################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

#######################
##  Mouse 
#######################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

#######################
##  Video 
#######################
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
        BusID           "PCI:1:0:0"
EndSection

#######################
##  Monitor 
#######################
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-75.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

#######################
##  Pantalla 
#######################
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1680x1050" "1600x1024" "800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Default Screen" 0 0
EndSection


```

reinicio gráfica y les aviso...

---

### Post by exegeses on 2009-04-02
> **exegeses said:**
> cambio xorg.conf y lo dejo así:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#######################
##  Teclado 
#######################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

#######################
##  Mouse 
#######################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

#######################
##  Video 
#######################
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
        BusID           "PCI:1:0:0"
EndSection

#######################
##  Monitor 
#######################
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-75.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

#######################
##  Pantalla 
#######################
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes		"1680x1050" "1600x1024" "800x600"
	EndSubSection
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen 0 "Default Screen" 0 0
EndSection


```

reinicio gráfica y les aviso...

nada, siguió a 800x600...
dije, bueno, como en el lado oscuro, reinicio sistema...

1680x1050... como carreta...
no lo puedo entender.

---

### Post by Hei Ku on 2009-04-02
Probemos algo intermedio. 1680x1050 es el maximo de esa placa. Vamos a 1280x800.


Modes		"1280x800" "1600x1024" "800x600"


A ver qué pasa. Tené en cuenta que esa placa es viejita.

---

### Post by exegeses on 2009-04-02
antes que nada, me estuve fijando cómo estaba.

los efectos están cargados. no los habilité. simplemente estaban, o sea, los recargó.

sigo mirando y veo esto:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108459&stc=1&d=1238715028[/IMG]

es correcto verdad?

ah, XRandrX volvió de su colostomía. sigue exactamente igual, no coopera y envía saludos. ;)

finalmente, no puedo, simplemente no puedo entender cómo esto funcionaba en 7.10 y en 8.04 no funciona. en 7.10 tenía mi monitor a 1280x1050 y compiz con los efectos y el cubo del @rt@ funcionando. 
no creo que sea la placa, la placa funcionaba bien en 7.10
no creo que en 8.04 le hayan sacado funcionalidad.

por otro lado, 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108459&stc=1&d=1238715028[/IMG]
esto no indica que no estamos usando la aceleración?
no entiendo porqué cambiar la configuración, ya que 1680x1050 es la óptima para este monitor.

perdón por la insistencia.
gomen nasai.

tiene que funcionar. no puedo creer que windows la reconozca y mi HH no...

---

### Post by Hei Ku on 2009-04-02
El cartel ese solo indica que no usas los drivers privativos.

Hacé el cambio de modes como te indiqué, para probar. Así nos sacamos la duda. Entiendo que quieras aprovechar al maximo el monitor, pero vamos por partes.

Si en 1280x1050 anda bien, vamos subiendo hasta encontrar el modo optimo, te parece?

---

### Post by pablo.s on 2009-04-02
Aparte una cuestión es la resolución y otra
muy distinta es la aceleración 3D, que la
maneja el módulo DRI. Tiene razón el sensei,
primero solucionar la resolución que es un tema
mas importante.

---

### Post by hictio on 2009-04-02
Otra cosa que podés probar, sólo por descartar, es bajar al profundidad. Está setteada en 24, testeá con 16 y 8.

En cuanto a lo que decís de quitar funcionalidad, no se con tu tarjeta en particular, pero la NVIDIA que tengo, una GeForce2 MX (muy vieja) en Intrepid ya no tiene soporte oficial de Ubuntu para los drivers 3D.

---

### Post by exegeses on 2009-04-02
para probar algo, descativé los efectos.

tiene un flicker al mover las ventanas, ya es más humano esto...
el scroll del navegador va bien. 

bueno, luego cambié el xorg.conf

```
	SubSection "Display"
		Modes		"1280x800" "800x600"
	EndSubSection
```

reseteo la gráfica.
es exactamente igual que con los efectos quitados.
flicker al mover ventanas

intento habilitar efectos.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108475&stc=1&d=1238720722[/IMG]

:(

---

### Post by Hei Ku on 2009-04-02
Corre esto para asegurarnos que tenes todo lo que hace falta

```

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

```

Agrega esto al final de tu xorg.conf

```

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Reinicia, y despues a ver que dice cuando en la terminal pones:
```

glxinfo | grep "direct rendering"

```

---

### Post by exegeses on 2009-04-03
bueno, ahí vamos...

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 2 reinstalados, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/13,3MB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
....
  
124197 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libgl1-mesa-glx 7.0.3~rc2-1ubuntu3 (usando .../libgl1-mesa-glx_7.0.3~rc2-1ubuntu3_i386.deb) ...
Desempaquetando el reemplazo de libgl1-mesa-glx ...
Preparando para reemplazar libgl1-mesa-dri 7.0.3~rc2-1ubuntu3 (usando .../libgl1-mesa-dri_7.0.3~rc2-1ubuntu3_i386.deb) ...
Desempaquetando el reemplazo de libgl1-mesa-dri ...
Configurando libgl1-mesa-glx (7.0.3~rc2-1ubuntu3) ...

Configurando libgl1-mesa-dri (7.0.3~rc2-1ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

agrego 
```

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```
al final de mi xorg.conf

reinicio sistema, no sólo la gráfica...

demora un toque más que de costumbre

hago
```
glxinfo | grep "direct rendering"

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

y ahora hace más flicker que antes, no es mucho, pero es.
 y además...

[No se han podio activar los efectos de escritorio.]("http://ubuntuforums.org/attachment.php?attachmentid=108475&stc=1&d=1238720722")

:(

---

### Post by exegeses on 2009-04-03
> **Hei Ku said:**
> 
...
...

Reinicia, y despues a ver que dice cuando en la terminal pones:
```

glxinfo | grep "direct rendering"

```

no sirvió lo que postee?
me gustaría usar los efectos que me funcionaban en mi GG (7.10). la placa es la misma, debería funcionar.

no hay que hacer algúna historieta loca con el emerald o algo así?
si, ya sé, mandé fruta... pero me gustaría usar los efectos como antes de la actualización a HH (8.04 )
sino, al menos sería re-triste, pero me resigno a conformarme con una gráfica que no haga flicker al mover una ventana.

alguien tiene idea cómo podemos seguir?
saludos

---

### Post by pablo.s on 2009-04-03
Yo te recomendaria algo que le recomiendo 
a todos en el foro:
ACTUALICEN A JAUNTY
No solo porque trae lo mas reciente, sino
porque hay muchos avances en seis meses,
ni hablar de un año ( o mas) en materia de
detección de hardware, modulos de kernel
que detectan placas de sonido, webcams,
te hace funcionar el winmodem asi te 
conectas a America Online, te baja los
episodios de Lost a 384 kbps, etc.
Para las benditas placas ATI trae algunas
mejoras en XOrg 1.6 (la verdad que ni
idea porque uso NVidia) pero ponele que si.
Saludos.

---

### Post by hictio on 2009-04-03
exegeses, cómo va?
Disculpame, pero me perdí con el status.

Ahora:

* El GUI te está funcionando correctamente (no está lento)
* No tenés Desktop Effects
* Qué resolución estás usando? La óptima de tu LCD, o tuviste que bajar un punto?

Gracias.

---

### Post by Hei Ku on 2009-04-04
El problema es con los drivers. Por alguna razon no quiere habilitar el 3D, aunque tu placa esta soportada.

Pone esto en la consola y pasa el resultado:
```

LIBGL_DEBUG=verbose glxinfo

```

---

### Post by Hei Ku on 2009-04-04
Para mas info: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Es un buen tutorial sobre como activar el driver libre.

Si no, habra que ir con el privativo, pero me parece que esa placa ya no esta soportada.

---

### Post by exegeses on 2009-04-04
```
lspci -nn | grep VGA

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
```



[COLOR="DarkRed"]**X600 / rv380 based cards**[/COLOR]

wiiiiii. I think we had contact!!!
que bueeeee

domo arigatô gozaimasu. Hei Ku-san

que bueeeee
parece que se puede.
ahora voy saliendo, pero ni bien venga me pongo con esto.
la verdad, me levantó más el ánimo este post.
que bueno es formar parte de esta comunidad donde pueden ayudar a "little melons" como yo.

gracias a todos por no dajerme en banda. y apoyar ;)
bueh, me voy porque sinó me matan.
ni bien vuelva trato de configurar la placa y cuanto cómo va.

ja mata (nos vemos)

---

### Post by exegeses on 2009-04-05
bueno, malas noticias...

seguí el tutorial paso a paso.

ahora no pudo usar bien el mouse...
no funciona

el click secundario (derecho) no deja ver las opciones, selecciona la primara siempre. la única manera es dejarlo pulsado y ahí moverse y seleccionar.
el click primario simplemente NO funciona excepto sobre la barra superior del menu gnome. no deja ver las opciones, la única manera es dejarlo pulsado y ahí moverse y seleccionar.

no tengo manera de ver si al mover las ventanas hacen flicker, aunque calculo que si.

en la terminal me aparece este mensaje 

```
(gedit:24709): Gtk-CRITICAL **: gtk_widget_event: assertion `GTK_IS_WIDGET (widget)' failed

```

mi xorg.conf quedó así:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#######################
##  Teclado 
#######################
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

#######################
##  Mouse 
#######################
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

#######################
##  Video 
#######################
Section "Device"
	Identifier	"RV380 Radeon X600"
	Driver		"ati"
        BusID           "PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

#######################
##  Monitor 
#######################
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-75.0
  #modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  #modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  #modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  #modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  #modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  #modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  #modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  #modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  #modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  #modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  #modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  #modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  #modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  #modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

#######################
##  Pantalla 
#######################
Section "Screen"
	Identifier	"Default Screen"
	Device		"RV380 Radeon X600"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050" "1600x1024" "1280x800" "800x600"
		Depth		24
	EndSubSection	
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

no se.
ya no sé...
ayuda por favor

---

### Post by Hei Ku on 2009-04-05
La unica opcion distinta con lo que tenias antes es esta:

Option          "XAANoOffscreenPixmaps"

Sacala por el momento.

Y postea el resultado de correr este comando:

```

LIBGL_DEBUG=verbose glxinfo

```

---

### Post by exegeses on 2009-04-05
> **Hei Ku said:**
> La unica opcion distinta con lo que tenias antes es esta:

Option          "XAANoOffscreenPixmaps"

Sacala por el momento.

Y postea el resultado de correr este comando:

```

LIBGL_DEBUG=verbose glxinfo

```


opción comentada.
CTRL-ALT-BACKSPACE

lo mismo...

reinicio. creo que una de las pocas cosas que tengo seguridad es que reiniciar la gráfica no siempre sirve. a veces (la mayoría) hay que reinicial el SO. 
[NOTA]eso no lo voy a entender. antes las cosas no eran así. con reiniciar la gráfica se reiniciaba todo lo de la gráfica...
en fin[/NOTA]

tiro al comando:
```
LIBGL_DEBUG=verbose glxinfo

name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

se podrá solucionar?
hay esperanza?
saludos y gracias.

---

### Post by Hei Ku on 2009-04-05
grrr.... Estuve buscando informacion y no veo nada que pueda ayudar. Tu placa deberia estar soportada, pero por alguna razon no la levanta el driver libre.

Cambio de metodo, vamos por el driver privativo. :(

La versión de este mes es la última que va a soportar tu modelo de placa, asi que estamos justo a tiempo.

Esta es la página con el tutorial:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

El driver lo podes bajar de aca:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

---

### Post by exegeses on 2009-04-05
estoy entendiendo el funcionamiento del mouse...

cada vez que se hace click, el mouse entiende un doble click.

no es el mouse. ya lo cambié por otro. además dejó de funcionar cuando seguí el tutorial al pie de la letra.

se podrá solucionar lo del mouse?

antes, en mi redhat, o en debian, en la época del moño, había un comando XF86Config que te guiaba en la configuración de la gráfica.(obviamente ya lo probé y no está)

no hay ahora un comando tipo sudo XConfigur@melolareconch@detum@dre para hacer eso. tenemos que morir en...
bueno, esperemos se pueda solucionar.


[NOTA]Ubuntu 7.10 GG me funcionaba casi perfecto. Ubuntu 8.04 HH está comportándose como un mal sueño[/NOTA]

---

### Post by Hei Ku on 2009-04-05
Fijate en los settings del mouse, si no hay algo que se haya activado por ese lado.

---

### Post by exegeses on 2009-04-05
> **Hei Ku said:**
> grrr.... Estuve buscando informacion y no veo nada que pueda ayudar. Tu placa deberia estar soportada, pero por alguna razon no la levanta el driver libre.

Cambio de metodo, vamos por el driver privativo. :(

La versión de este mes es la última que va a soportar tu modelo de placa, asi que estamos justo a tiempo.

Esta es la página con el tutorial:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

El driver lo podes bajar de aca:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

estuve leyendo el tuto de la instalación.
no estoy tratando de cuestionar o poner peros...

```
After installation, in GNOME or Kubuntu, turn off visual effects or you will notice a flicker in OpenGL.
```
si yo ya perdí los efectos visuales, y no los voy a tener, no veo porqué hacer todo esto...
si ahora ni siquiera puedo usar el mouse... (para programar no lo necesito, podré vivir sin ello)

no quiero poner peros...
estoy analizando el origen del problema.
perdón, a veces tengo una mente analítica, es mi problema. no siempre me conformo con un NO SE PUEDE, me gustaría saber el porqué.
ya llegué a un punto donde cambio settings y no estoy aprendiendo nada.

perdí todo lo bueno que tenía el GG, no gané estabilidad, performance, velocidad de proceso.
tengo los mismos daemons que necesito, ellos se comportan igual (apache2 +modules, mysql-server +addons, vsftp, postfix, etc).
poqué debería actualizar?
no es este ultimo caso, pero me han recomendado actualizar a II (8.10), no veo qué ganaría y dado la evolución histórica de actualizaciones, es probable que pierda algo.

perdon, pero detesto window$, no voy a volver al lado oscuro, pero ¿será remotamente posible que me convenga quedarme en en 7.10 que tan simplemente funcionaba?

reconozco que no necesito el mouse para trabajar (aunque el GIMP me lo agradecerá), trabajo con una diseñadora que me hará le gráfica (demoraré más, tendré que esperar que ella me saque los iconitos y demás widgts visuales de mi trabajo), pero...
¿no hay nada mejor que esto?
¿tengo que volver al 7.10?
¿tengo que comprar una placa de video nueva? (si esta es la solución entro a mercado libre ahora mismo)

finalmente:
¿como hago para avanzar y no retroceder en mi esperiencia como usuario de ubuntu?

a eso se reduce todo...

si volver al 7.10 es la solución, entonces gano tiempo y reinstalo al mejor estilo window$...

pordón, no deseo dar una comunicación desagradecida.
estoy más que satisfecha con la ayuda desinteresada.
pero el trabajo y el nivel de vida-usuario de Ubuntu me ha llevado a esta inquietud que deseo responder.

perdón por los peros, pero mil gracias y quedo a la espera de su respuesta que seguiré sin cuestionamientos y seguramente aprenderé mucho de ello.

gomen nasai

gambarimashô

---

### Post by Hei Ku on 2009-04-05
Por lo que entiendo, el flicker se da si usas el driver que esta en los repositorios de Ubuntu. 

Por otro lado, en tu caso, yo reinstalaria la 7.10 y me quedaria con esa por el momento, ya que estas acostumbrada, y anda muy bien con tu hardware.
Salvo que haya alguna funcion en particular que tengas que usar de las nuevas versiones, no actualizaria.

---

### Post by pablo.s on 2009-04-05
Che, y si de ultima ultima ultima
bajas la beta de Jaunty y le probás
como live y si te funciona la instalás?

Rompo la paciencia con el tema porque
me parece que te puede servir...

En un rato baja (depende de la conexión,
ojo) y podés ganar tiempo.

Mi humilde re-re-re sugerencia.


[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

---

### Post by Hei Ku on 2009-04-05
La 9.04 esta complicada con los drivers de esa placa, porque el driver de ati no esta preparado para la version de x.org que trae jaunty, asi que no va a ser una solucion.

La unica forma de hacerlo andar es con unos drivers beta, pero que ya no incluyen el soporte de esa placa de video. Asi que podria ser la solucion, pero despues de comprar una placa nueva en mercadolibre.

---

### Post by pablo.s on 2009-04-05
> **Hei Ku said:**
> La 9.04 esta complicada con los drivers de esa placa, porque el driver de ati no esta preparado para la version de x.org que trae jaunty, asi que no va a ser una solucion.

Extractado de las notas de la [Beta de Jaunty]("http://www.ubuntu.com/testing/jaunty/beta")

X.Org server 1.6

The latest X.Org server, version 1.6, is available in Jaunty. A number of video cards have been transitioned to free drivers as part of this update. 

**The -ati driver has received numerous fixes and performance improvements. It now uses the EXA acceleration method by default. 2D acceleration support for the newest R6xx/R7xx family of cards is also available. 3D support is available up to R5xx cards for -ati. An updated -fglrx proprietary driver is available for R6xx/R7xx users who need 3D support.**

---

### Post by Hei Ku on 2009-04-05
La X600 es la R380, que no esta incluida en ese anuncio.

---

### Post by pablo.s on 2009-04-05
Ufa.

---

### Post by exegeses on 2009-04-06
> **Hei Ku said:**
> Fijate en los settings del mouse, si no hay algo que se haya activado por ese lado.

> **Hei Ku said:**
> Por lo que entiendo, el flicker se da si usas el driver que esta en los repositorios de Ubuntu. 

Por otro lado, en tu caso, yo reinstalaria la 7.10 y me quedaria con esa por el momento, ya que estas acostumbrada, y anda muy bien con tu hardware.
Salvo que haya alguna funcion en particular que tengas que usar de las nuevas versiones, no actualizaria.

por lo pronto he hecho un rollback al xorg.conf (version 321) y he recuperado el uso del mouse.

calculo que esperaré una semanita a que me baje el nivel de escherichia_colli que me causó esta "configuración" y luego volveré a las andadas. 
por ahí instalando toooda la gráfica de 0. empezando por los privativos y sus efectos.

así que no voy a dejar esto así...

quisiera agradecer a 
[LIST]
[*]Hei Ku
[*]pablo.s
[*]hictio
[*]staar
[/LIST]

por haber ayudado. al menos he aprendido algunas cosas y eso es lo más importante.

bueno, nos leemos
muchas gracias nuevamente
(I'll be back with this ;) )

---


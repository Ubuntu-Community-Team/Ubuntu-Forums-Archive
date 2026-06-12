---
title: "Bajo rendimiento con la placa de video"
date: 2008-12-27
forum: Hardware
---

### Post by cab3z0n on 2008-12-27
Instalé el Ubuntu 8.10 hace pocos días y me encontré con el problema de que cualquier juego que use la aceleración 3D se ve mucho más lento de lo que debería. Por ejemplo, instalé el Half-Life y el Unreal Tournament y tienen pocos FPS en comparación con el Windows. Estuve revisando el tema de los drivers pero los que están instalados supuestamente soportan 100% mi placa de video.

Tengo un AMD Athlon 900MHz, 512 MB de RAM y placa ATI Radeon 7200 32 MB DDR. Espero que alguien pueda ayudarme porque aunque tenga los drivers correctos parece que la aceleración 3D no funciona del todo bien.

Saludos y gracias.

---

### Post by Hei Ku on 2008-12-28
Qué drivers tenés instalados? Para esa tenés los libres y los privativos.

---

### Post by cab3z0n on 2008-12-28
> **Hei Ku said:**
> Qué drivers tenés instalados? Para esa tenés los libres y los privativos.

Tengo instalado los libres, y los privativos no sirven porque soportan a partir de la 8500.

---

### Post by Hei Ku on 2008-12-28
Que te aparece si ponés esto? 

```

glxinfo | grep direct

```

---

### Post by cab3z0n on 2008-12-28
Aparece

```
direct rendering: Yes
```

Creo la aceleración sí está activada y funciona pero se ve todo más lento de lo que debería.

---

### Post by Hei Ku on 2008-12-28
Tené en cuenta que la aceleración del driver libre es más lenta que la del propietario.

Cuantos fps te da con el glxgears?

---

### Post by cab3z0n on 2008-12-28
El glxgears tira 870 FPS. Entiendo que puede ser más lenta la aceleración del driver libre, pero en este caso la diferencia es muy grande, por ejemplo el Half-Life en el Windows XP, con los últimos drivers funciona a 60 FPS y en el Ubuntu anda a alrededor de 15 FPS.

---

### Post by Hei Ku on 2008-12-28
Mi 9200 andaba a unos 900 FPS, así que no me parece tan mal. En cuanto al Half-life, no sé si habrá algo en particular que se pueda hacer. Te fijaste en los foros del juego a ver si alguien tiene el mismo problema?

---

### Post by cab3z0n on 2008-12-29
Ojalá fuera problema del Half-Life únicamente, pero los demás juegos también funcionan muy lentos, por ejemplo el Unreal Tournament. El único que anda bien es la Tomb Raider II pero por momentos se ralentiza un poco, lo que es absolutamente anormal considerando que es un juego de 1997. El emulador Gens funciona con buenos FPS en tanto lo deje en OpenGL, con VSync y sin ningún filtro (por lo que se ve horrible), porque en cuanto le pongo 2xSaI se vuelve lento y molesto.

Te digo más, todo lo que sea flash por algún motivo también anda lento. Supongo que debe ser un problema de los drivers, y como si fuera poco ATI no se dignó a hacer los suyos para placas viejas (al contrario de lo que hizo nVidia). Probé cambiarle de todo al xorg.conf y no sirvió para nada. No sé qué más hacer, si sabés alguna configuración que le pueda hacer o algo para que no parezca una 486 decime.

---

### Post by Hei Ku on 2008-12-29
Cómo tenés la seccion del xorg.conf de la placa de video?

---

### Post by cab3z0n on 2008-12-29
Ahora lo tengo así:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "xtrap"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  280   210	# mm
	Identifier   "Monitor0"
	VendorName   "GSM"
	ModelName    "60A"
	HorizSync    30.0 - 61.0
	VertRefresh  50.0 - 120.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R100 QD [Radeon 7200]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
Pero no noto ninguna diferencia en velocidad a como lo tenía cuando instalé el Ubuntu:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Saludos.

---

### Post by Hei Ku on 2008-12-29
Proba de agregar estas opciones a la sección de "Device"

```

Option "AccelMethod" "EXA"
Option "MigrationHeuristic" "greedy"

```

O avisame si ya lo habías probado.

---

### Post by cab3z0n on 2008-12-29
Te agradezco pero no se solucionó el problema. Para que me lea el xorg.conf modificado basta con apretar CTRL+ALT+BACKSPACE no?

---

### Post by Hei Ku on 2008-12-30
Debería bastar con eso.
Los FPS siguen igual en el glxgears?

---

### Post by cab3z0n on 2008-12-31
Pasó de 870 a 850 FPS. Encima en un momento pensé que se había arreglado todo porque no sé qué mier** hice que no me tomaba el xorg.conf, así que lo reemplacé por uno más viejo, le puse lo que me sugeriste, y reinicié el Linux. Después me fijé que me detectaba bien las frecuencias de actualización del monitor, o sea, 1024x768 a 75 Hz. Hasta ese momento sólo me dejaba ponerlo en 60 Hz. Entonces probé el glxgears a ver si había mejorado y se cagó todo y tuve que resetear. Y después volvió todo a como estaba antes, o sea, lento y con la tasa de refresco incorrecta. Durante esos 2 minutos de alegría pude ver que no se notaba el molesto redibujado del escritorio. Tenés idea de qué pasó??

Lo bueno es que ahora el escritorio con los efectos Compiz funciona perfecto. Antes se trababa insoportablemente, pero con este cambio, por lo menos eso se arregló. Pero lo 3D ni a palos.

Saludos.

PD: Feliz año nuevo :)

---

### Post by Hei Ku on 2009-01-01
El tema del refresco del monitor, podemos verlo por separado. Esos son seteos en la seccion Monitor.

---

### Post by cab3z0n on 2009-01-01
> **Hei Ku said:**
> El tema del refresco del monitor, podemos verlo por separado. Esos son seteos en la seccion Monitor.

Lo raro es que se había arreglado solo, pero dicen que "fácil viene, fácil se va", y así me pasó en 2 minutos...

Y siguiendo con lo de los fps, probé el Ubuntu en otra computadora con una GeForce 8600GT, le puse los drivers propietarios de nVidia y todo funcionó perfecto. Con los drivers libres el glxgears tiraba 150 FPS, y con los propietarios pasó a 2500. Lástima que con la ATI no haya tenido tanta suerte.

---

### Post by Hei Ku on 2009-01-01
Hmmm, creo que comparar la 8600GT de 128MB con la Radeon 7200 de 32MB de RAM es un poquito injusto, no te parece? Son placas de eras diferentes. En todo caso, te podría decir que la Radeon 9200 que tenía yo me tiraba 900FPS con los drivers libres.

Volviendo a la resolución, yo se la puse a mano, porque el monitor era viejo y la placa también. Así me aseguraba que los tome bien.

Posteá tu xorg.conf completo, así veo también el tema de la resolución. Y cuál es tu monitor, y qué frecuencia horizontal y vertical se banca.

---

### Post by cab3z0n on 2009-01-01
Ya sé que no hay mucha comparación, pero la idea es que una es totalmente compatible y tiene drivers oficiales y la otra no va ni para atrás en lo referente a 3D.

El monitor es un LG Studioworks 560A de 15 pulgadas y creo que soporta como máximo 1024x768 a 75 Hz (así lo uso bajo Windows). No sé qué frecuencia horizontal soporta, pero creo que en el xorg.conf que puse antes aparece detectada.

Después de cambiarlo mil veces, esto es lo que tengo ahora:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "EXA"
	Option "MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by Hei Ku on 2009-01-01
Acá va el xorg.conf modificado

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "EXA"
	Option "MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        Option          "DPMS"
        HorizSync       30-61
        VertRefresh     50-120

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

---

### Post by cab3z0n on 2009-01-02
No sirvió, sigue empecinado en ponerme 1024x768 a 60 Hz. 800x600 siempre me dejó ponerlo a 85 Hz, lo que está bien, pero 1024x768 está limitado a lo que ya dije.

---

### Post by Hei Ku on 2009-01-02
En el mode, ponele tambien los Hz. Por ej: "1024x768@75"

Fijate si así anda.

Si no levanta, desde la consola: sudo nano xorg.conf y revertis el cambio. ;)

---


---
title: "antes de iniciar me dice &quot;SINC Fuera de limite&quot;"
date: 2007-12-01
forum: Hardware
---

### Post by atatiducken on 2007-12-01
buenas gente disculpen las molestias, mis problemas son dos, uno antes de que inicie el SO me dice "sync fuera de limite" o "Syc Fuera de limite", no recuerdo bien, son unos segundos y despues inicia ubuntu tranquilamente, pero es bastante molesto, alguien podria ayudarme imagino q la soluion es bastante facil pero soy noob.

El segundo es referido a mi conexion a internet, ya la tengo configurado gracias a su ayuda, mi conexion es de arnet con el modem Hauwei segui esta guia q me dieron [http://ubuntuforums.org/showthread.php?t=591651&highlight=duda+con+modem](http://ubuntuforums.org/showthread.php?t=591651&highlight=duda+con+modem)
, la conexion anda perfecto, el problema es en la parte q automatizamos todo para que cada vez q iniciemos ubunto se inicie sola la conexion, en mi caso no pasa debo hacer siempre lo siguiente
$ sudo modprobe br2684
$ sudo br2684ctl -c 0 -b -a 0.33
$ sudo ifconfig nas0 up
$ sudo pppoe-start

Edito el sudo gedit /etc/rc.local y le agrego las lineas q me indican pero nada, siempre q entro debo escribir esos comandos
Como veran mis problemas no son graves, solo de comodidad, espero q alguien pueda ayudarme gracias; ah soy usuario de Gutsy

---

### Post by Mauro22 on 2007-12-01
Hola!

Lo de 'Sync fuera de limite' es porque el sincronizado de la frequencia del monitor esta afuera de los limites permitidos por el monitor.

Que monitor tenes? a que resolucion lo usas ahora?

-----------------

Para lo otro podes hacer un script al inicio, sólo que te va a pedir el pass, cada vez que inicias.

Aca explico como hacer un script:
[http://ubuntuforums.org/showthread.php?t=601194&highlight=Sony](http://ubuntuforums.org/showthread.php?t=601194&highlight=Sony)

El paso 3, en tu caso seria:

[FONT=monospace]#!/bin/sh[/FONT]
sudo modprobe br2684
sudo br2684ctl -c 0 -b -a 0.33
sudo ifconfig nas0 up
sudo pppoe-start

y agregarlo al inicio de sesion:
Sistema -> preferencias -> Sesiones

Elegis añadir y pones el nombre del script que hiciste

---

### Post by atatiducken on 2007-12-01
wow q velocidad de respuesta ^^ mi monitor es un Samsung SyncMaster 551v y la resolucion q uso es 1024x768 a 51hz, tiene solucion?

Lo del script para conectarse simplemente INCREIBLE me solucionaste el problema en 2 minutos, la verdad sos crack! ahora me conecta rapidisimo. 
Mil gracias

---

### Post by Mauro22 on 2007-12-01
Tenes bajos los Hz, te aparece 51Hz, cuando en 1024x768 tiene que ser 75.

Primero hace una copia de seguridad de tu xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp

Por si algo falla y no te inicia modo gráfico, haces:

sudo rm /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf

-----------

Una vez hecho el backup, abrilo para editar (si usas gnome, es gedit)

sudo gedit /etc/X11/xorg.conf

y en Esta seccion (lo tuyo es diferente al mio)

Section "Screen"
    Identifier    "Default Screen"
    Device        "Tarjeta de vídeo genérica"
    Monitor        "L1752S"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1792    1344
        Modes        "1280x1024@60"    "1280x960@75"    "1280x960@60"    "1400x1050@60"    "1280x1024@75"    "1400x1050@75"    "1152x864@75"    "1600x1200@65"    "1024x768@60"    "1600x1200@60"    "1024x768@70"    "1792x1344@60"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

En modes, modifica el 1024x768 para que te aparezca @75. Reinicia y fijate. Si no levante el modo grafico acordate el codigo de arriba.


-----
Larga vida al script! :)
-----

---

### Post by atatiducken on 2007-12-01
gracias man, hice lo q me dijiste pero el mio es un poco diferente al tuyo, las resoluciones no tiene las frecuencias al lado, mira esto me aparece 

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

lo q yo hice fue agregarle un @75 a mi resolucion pero me sigue diciendo "Sinc. Fuera de limite" antes de iniciar, me quedo asi

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1152x864"	"1024x768@75"	"800x600"	"640x480"
	EndSubSection
EndSection

q puedo hacer? gracias

---

### Post by Hei Ku on 2007-12-01
Fijate si no tenes la seccion Monitor.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
EndSection


Ahi le podes configurar el refresco horizontal y vertical.

---

### Post by atatiducken on 2007-12-01
smi seccion monitor dice esto

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection


yo le agregue esas lineas q faltaban al mio y quedo asi

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
        HorizSync 30-83
        VertRefresh 56-75
EndSection

pero solo me da 55hz o 56 hz, no se q hacer

---

### Post by vk-cdg on 2007-12-02
> **atatiducken said:**
> smi seccion monitor dice esto

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection


yo le agregue esas lineas q faltaban al mio y quedo asi

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
        HorizSync 30-83
        VertRefresh 56-75
EndSection

pero solo me da 55hz o 56 hz, no se q hacer

Yo tuve el mismo problema. 
Fijate en el manual de tu monitor (o en su defecto en el sitio web) cual es el rango de frecuencias horizontal y vertical soportado por ese modelo de monitor y en la parte donde dice  HorizSync y VertRefresh ponele los valores que te indique el manual (o sitio web).

Con eso tendría que solucionarse.

---


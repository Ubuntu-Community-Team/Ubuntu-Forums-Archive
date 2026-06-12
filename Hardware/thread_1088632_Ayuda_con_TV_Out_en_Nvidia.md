---
title: "Ayuda con TV Out en Nvidia"
date: 2009-03-06
forum: Hardware
---

### Post by leandroamato on 2009-03-06
Hola! A ver si alguien me puede dar una mano con esto... Uso Ubuntu Intrepid, instalé hace poco una NVIDIA GeForce 8600, con los drivers privativos (probé la versión 173 y la 177 por las dudas), y no hay forma de que funcione el TV OUT.

Probé montones de cosas, busqué en este foro y probé todas las opciones que se comentaron, pero ninguna me funcionó. Probé nvtv pero no reconoce mi hardware o algo así. Puedo tener algo raro yo que haga que cosas que comentaron por acá no me funcionen? Me falta algo?

El xorg.conf lo edité y se editó por el nvidia-settings un montón de veces. Con el nvidia-settings probé todo, de todas las formas, guardando en xorg.conf, sin guardar... nada, ninguna funcionó, y en varios casos tuve que reconfigurar x o volver a un backup.

Lo único que si logré, después de muchísimos intentos. por si ayuda y para comprobar que la placa funciona y el cable también, es iniciar X viendo SOLO la TV, pero con la resolución de la PC.

Les copio la versión de xorg que quedó puesta ahora en mi PC... la verdad es que no tengo mucha experiencia y no sé si falta algo fundamental o si sobra algo... es lo que quedó después de muchas pruebas, reconfiguraciones y tutoriales... Básicamente es la versión reconfigurada automáticamente por el sistema con el agregado de una de las soluciones que encontré en un foro:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "True"
Option "MetaModes" "1680x1050,1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "CRT"
EndSection
```

Con este xorg.conf, si cambio el "UseDisplayDevice" por "TV" y reinicio X, veo sólo la tele, aunque a 1680x1050, o sea que veo solo el medio y no se llega a ver lo que hay a los costados.

Alguien tiene alguna idea de que puedo hacer para ver la tele en la resolución correcta (1024x768 en mi caso)? Alguna forma de habilitar la TV y el monitor a la vez? Aunque sea me conformo con poder alternar entre una cosa y otra, preferentemente sin tener que reiniciar X...

Muchas gracias!

---

### Post by rojojuan on 2009-03-06
En nvidia-settings te detecta el otro display?

---

### Post by leandroamato on 2009-03-06
Si, aparece como "TV-O - Disabled". Toque lo que toque, ponga Twinview o Separate X Screen, como usuario normal o abriendo la aplicación con sudo desde la consola, al reiniciar (si es que no me da un error y tengo que volver a un backup del xorg o restaurarlo) vuelve a estar como "Disabled"...

:(

---

### Post by luks911 on 2009-03-06
Tendría que funcionar con el nvidia-settings. 
¿Probaste con Xinerama? Acá[0] hay un tutorial. Debe haber algún otro en español. Nunca lo hice pero sé que se usa para eso.

[0] [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

---

### Post by leandroamato on 2009-03-06
> **luks911 said:**
> Tendría que funcionar con el nvidia-settings. 
¿Probaste con Xinerama? Acá[0] hay un tutorial. Debe haber algún otro en español. Nunca lo hice pero sé que se usa para eso.

[0] [http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

Seguí el tutorial y no funcionó... fui probando las cosas que iban agregando en el thread pero no logré nada... Ya estoy totalmente perdido, no sé bien por dónde más buscar...

---

### Post by c4d0rn4 on 2009-03-08
> **leandroamato said:**
> Seguí el tutorial y no funcionó... fui probando las cosas que iban agregando en el thread pero no logré nada... Ya estoy totalmente perdido, no sé bien por dónde más buscar...

desinstalá los drivers y ponelo en 640*400 (o lo más bajo). Cuando lo pongas en la tv debe andar.

A mi me pasó algo similar (si no es lo mismo). Cuando conectaba la placa con la tv con un cable supervideo-rca no funcionaba. Cuando la puse con supervideo-supervideo (mi tv milagrosamente tiene) SÍ lo toma.

Aún así hay algo que no pude solucionar que es un overscan (lease la pantalla es más grande que la tv)

---

### Post by rojojuan on 2009-03-08
A ver si entendí. Te detecta el display y podés habilitarlo?
La cuestión de que quede seteado en forma permanente es fácil.
Veamos primero si lo podés habilitar y ver correctamente.

---

### Post by leandroamato on 2009-03-08
**c4d0rn4**: Mi TV también tiene super video, estoy usando el cable que viene con la placa (svideo/svideo)... Llegué a pensar si probando con otro cable puede funcionar, pero no tengo ningún otro a mano y no se si tiene algún sentido como para comprarme otro.

Decís que desinstale los drivers de Nvidia y ponga la resolución del monitor en lo más bajo y pruebe detectar la TV?

**rojojuan**: Si uso el nvidia-settings, veo que hay una TV, pero no puedo activarla de ninguna forma... pruebo todo pero en la TV no se ve nada. A veces da errores de que no se pudo activar algún modo, otras no dice nada, pero al reiniciar falla todo y tengo que restaurar el xorg.conf...

La única que me funcionó fue editar el xorg.conf a mano y en Device poner ```
Option "UseDisplayDevice" "TV"
```. Con esto, al reiniciar se ve todo en la TV, aunque a la resolución del monitor (me queda media pantalla afuera), pero no se ve nada en el monitor... Para volver al monitor, tengo que editar el xorg.conf de alguna forma (por suerte la terminal recuerda lo que puse en la última sesión y logro abrirlo) y poner ahí "CRT"...

---

### Post by granjero on 2009-03-08
hola, yo tengo la misma placa que vos... uso ubuntu hardy

lo que hice yo fue instalar envy

creo que lo instalé con 

```
sudo aptitude install envy
```

despues lo corrés y te autodetecta/instala los drivers que necesites.

despues configuré asi el xserver... (imagen adjunta) para abrirlo tenes que hacer 

```
sudo nvidia-settings 
```


lo que logré fue que en un pedazo a la derecha del escritorio este la tele que la veo en la habitación.

es una tele del año de la humedad así que uso la salida svideo con el adaptador que viene con la placa para salir por RCA.

ahi te dejo unos adjuntos ilustrativos de como funciona y mi xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: 640x480 +1440+210"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```



salud!

---

### Post by leandroamato on 2009-03-09
Nada, les agradezco mucho a todos por las respuestas, pero no hubo forma. Probé todo lo que sugirieron, busqué un poco más, toqué algunas cosas por mi cuenta... Incluso me conseguí un cable svideo/RCA para ver si con ese cambiaba algo, pero nada...

Supongo que me queda resignarme o probar una instalación de Windows sólo para esto, aunque me da bastante paja... 

De nuevo, gracias por la ayuda!

---

### Post by ideafix on 2009-03-11
Hey no te des por vencido! jaja o por lo menos, intenta en...4 meses...como suelo hacer yo cuando me caliento con las cosas q no salen jaja. No se si servira de mucha ayuda, ya q desde q tengo Intrepid el tele lo detecta bien mi nvidia integrada. Lo que tuve que tocar fue para verlo en color, algo que segun lei es por los driver para linux que saca nvidia. Fijate, se que no es tu problema, pero quien sabe que puede pasar ja. Saludos

[http://dejavucista.blogspot.com/2008/12/tv-out-en-color-en-nvidia-con-ubuntu.html](http://dejavucista.blogspot.com/2008/12/tv-out-en-color-en-nvidia-con-ubuntu.html)

---

### Post by c4d0rn4 on 2009-03-12
probá como se ve con un live cd y decinos como te fue. Yo creo que se va a ver bien, obvio que sin aceleración.

---


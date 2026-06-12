---
title: "Nvidia Settings no guarda en el xorg.conf"
date: 2009-05-11
forum: Hardware
---

### Post by guidito73 on 2009-05-11
Bueno, estuve viendo y mucha gente tiene este problema...

Tras inconvenientes con la resolución, etc con mi GeForce 5200 FX, lo solucioné instalando los drivers anteriores los 173.XXXXX

El inconveniente es que Ubuntu arranca con la configuración de Nvidia Settings con una tasa de 87 Hz que hace que se vea todo con un interlineado bastante feo. Puedo entrar y cambiarlo a 60 Hz, pero cuando hago click para guardar los cambios en el xorg.conf, me da este error:

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Nota: lo estoy abriendo con sudo, asi que no es un problema de permisos...

Intenté metiendo una línea que saqué del ubuntu guide de Intrepid para poner la tasa de refresco manualmente a 60 hz en el xorg pero me dio un problema terrible que ni me abría el escritorio.

En fin, todo se solucionaría:

a) Pudiendo hacer que Nvidia Settings guarde el Xorg.conf.

o

b) Si alguien me da una mano con alguna línea que especifique manualmente al xorg.conf de meter esa tasa.

Gracias!

---

### Post by staar on 2009-05-11
posteá tu xorg.conf, así te podemos ayudar mejor...

saludos

---

### Post by guidito73 on 2009-05-11
No es de mucha ayuda, está bastante pelado... Algo que ver con lo que Jaunty hace con el xorg no? En Hardy estaba lleno XD

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

---

### Post by staar on 2009-05-11
tendrías que agregarle los valores, para tu monitor (buscalos en el manual), de HorizSync y VertRefresh, en la sección Monitor, te quedaría así: ```

Section "Monitor"
    Identifier	    "Configured Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

``` esos valores son de MI monitor, vos poné los del tuyo...

si sigue jodiendo, forzalo a que no use los valores de edid que envía el monitor, porque la mayoría de las veces los lee mal (es por eso que muchos se quejan de que no pueden aumentar su resolución), tendrías que editar la sección Screen, dejándola así: ```

Section "Screen"
    Identifier	      "Default Screen"
    Monitor	      "Configured Monitor"
    Device	      "Configured Video Device"
    DefaultDepth      24
    Option	      "AddARGBGLXVisuals"     "True"
    Option            "UseEdid"               "False"
    SubSection        "Display"
       Depth          24
       Modes          "1400x1050" "1280x1024" "1024x768" "800x600"
EndSection
``` de nuevo, esas resoluciones son las de MI monitor, vos poné las que sepas que el TUYO soporta...

saludos

---

### Post by guidito73 on 2009-05-12
Bueno, probé los dos procedimientos y ninguno funcionó... los valores son iguales para mi monitor (LG T710SH).

El problema me parece que reside en Nvidia-Settings... O sea, es el que está manejando todo (porque sino no pasaría por encima al xorg.conf como lo está haciendo).

La verdad que no sé qué puede ser =S

---

### Post by staar on 2009-05-12
tengo una placa muy similar a la tuya, GeForce FX 5500 (en realidad es la misma, levemente overclockeada de fábrica) y ya que los valores del monitor son iguales, podrías probar con mi xorg.conf ```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection                      

Section "Module"
    Load           "glx"
EndSection              

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "DontZap"  "False"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "MetaModes" "1400x1050 +0+0"
    Option         "UseEdid" "False"
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection 
``` este me anda bien en ubuntu y en arch linux, fijate que tengo unos modelines configurados en mi sección monitor, son bastante específicos, no estoy seguro, te recomendaría que los comentes (agregar un # al inicio de cada línea), para evitar problemas...

tenés el live cd de hardy? hacé una cosa iniciá con ese, apretá Alt + F2, ejecutá 'displayconfig-gtk', seleccioná tu monitor manualmente y gurdá, así generas el xorg.conf correcto para tu monitor, después copiá la sección monitor de ese xorg (el del live) en el xorg de jaunty (tené cuidado con el 'Identifier' del monitor, tiene que ser el mismo en la sección 'Screen' en la línea 'Monitor')

saludos

---

### Post by dirty fingers on 2009-05-13
dos posibles soluciones.

1- iniciar la aplicación de nvida desde la(o el jaja genero indefinido) terminal con
```
gksudo nvidia-settings
```2- abirir el archivo con
```
sudo gedit /etc/X11/xorg.conf 
```y en el metamode agregar la frecuencia ( anchoxalto_frecuencia) ej: 1280x1024_85

---

### Post by stimpyjcat on 2009-05-13
el que corrige instalación de nvidia es el **nvidia-xconfig** aunque se me hace que **nvidia-detector** también agrega algo a xorg.conf (creo que a algunos no se nos instalan bien los drivers y esas utilidades lo reconfiguran)
 
**nvidia-settings** además tiene una opción para guardar modificaciones en xorg.conf (no se dónde guardará si no es allí)

saludos ^^

---

### Post by guidito73 on 2009-05-13
Bueno, finalmente pude hacer que nvidia-settings guarde al xorg.conf (era cuestión de comentar la línea 39 que me daba problemas)

Pero aún así sigue rehusando a cambiar la frecuencia :S

Volví a la versión 173.XX.XX de los drivers, pero nada...

Ya agregué en el xorg.conf la frecuencia correcta pero cuando inicia Ubuntu a Nvidia esto parece no importarle y le mete 87 hz con un interlineado asqueroso...

Ya no sé qué hacer =(

---

### Post by dirty fingers on 2009-05-13
empeza de vuelta. le estas errando en alguna boludes.
con todo lo que ya sabes tiene que salir andando.

---

### Post by staar on 2009-05-13
> Volví a la versión 173.XX.XX de los drivers, pero nada... esa placa TIENE que usar esos drivers, ya que son los que la soportan, los drivers más nuevos soportan a partir de la serie 6 de GeForce...

si tirás un ```
xrandr
``` en la terminal, que modos te devuelve como disponibles?

saludos

---

### Post by guidito73 on 2009-05-14
> **staar said:**
> esa placa TIENE que usar esos drivers, ya que son los que la soportan, los drivers más nuevos soportan a partir de la serie 6 de GeForce...

si tirás un ```
xrandr
``` en la terminal, que modos te devuelve como disponibles?

saludos

Sí sí pero había instalado los anteriores (96.XX.XX creo que son) y esos me habían permitido poner la resolución bien aunque sea... En estos momentos estoy bajo el yugo de Bill Gates debido a mis padres, cuando vague por Ubuntu te digo qué me tira...

(Igual vale la aclaración: puedo usar una frecuencia de 60 Hz, pero tengo que cambiarlo manualmente CADA VEZ que entro a Ubuntu, a través de Nvidia-settings)

EDIT: Hete aquí el resultado de xrandr.

```
Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0     53.0     54.0  
   960x540        55.0  
   840x525        56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0  
   800x512        64.0  
   720x450        65.0  
   720x400        66.0  
   680x384        67.0     68.0  
   640x512        69.0  
   640x480        70.0     71.0     72.0     73.0     74.0  
   640x400        75.0  
   640x350        76.0  
   576x432        77.0     78.0     79.0     80.0  
   512x384        81.0     82.0     83.0     84.0     85.0  
   416x312        86.0  
   400x300        87.0     88.0     89.0     90.0     91.0  
   360x200        92.0  
   320x240        93.0     94.0     95.0     96.0  
   320x200        97.0  
   320x175        98.0  

```

---

### Post by staar on 2009-05-14
hacé una cosa:

- abrí una terminal y poné ```
gtf 1024 768 60
``` eso te va a generar una Modeline (la última línea de la salida del comando) válida para el xorg.conf...

- abrí el xorg.conf y agregá la Modeline en la sección Monitor, junto con una opción PreferredMode, te quedaría algo así: ```

Section "Monitor"
    Identifier	    "Configured Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Modeline        "1024x768_60.00"  *muchos números*
    Option          "PreferredMode" "1024x768_60.00"
EndSection
```

- reinicía las X

- si no te funciona, otra cosa que podrías hacer es agregar un Metamode en la sección Screen especificando la tasa (como creo que ya te recomendaron), te quedaría algo así: ```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	        "AddARGBGLXVisuals"	"True"
        Option          "Metamode"              "1024x768_60 +0+0"         
        Option          "UseEdid"               "False"
        SubSection      "Display"
           Depth        24
           Modes        "1024x768" "800x600"
EndSection
```

saludos

---

### Post by guidito73 on 2009-05-14
Gracias Staar, gracias a todos por la ayuda!

El último comando que me diste me dio resultados (casi) perfectos!

Ahora la tasa con la que entra es de 70 Hz, sin interlineado ni nada así que se puede decir que 1 semana más tarde ya disfruto a plento de Jaunty jajaja. La única diferencia que veo con respecto a 60 Hz es un leve blur (o efecto borroso) pero muy muy leve, y la verdad que no me disgusta.

Cual será la razón por la que entra en 70 y no en 60? Te dejo el Xorg como quedó:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"

	#Disable	"dri2"
    Load           "glx"
	#Disable	"dri2"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
    Option          "PreferredMode" "1024x768_60.00"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5500"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by staar on 2009-05-14
buenísimo, me alegro...

creo ver por donde viene eso de que le pones 60 Hz y te usa 70 hz, me pasa algo parecido, yo uso 1400x1050, me dice que lo tengo a 50 Hz, sin embargo, en menú del monitor lo toma como 60 Hz, no se porque esa diferencia de 10 Hz, será un bug...

pero tu monitor es de 17', no? si estás acostumbrado a 1024x768, por lo menos subile el refresco a 85 Hz (agregando otro metamode, al lado del que tenés, igual, pero cambiando el 60 por un 75), si no te va a matar los ojos...

saludos

---

### Post by guidito73 on 2009-05-14
No no, el problema viene con los 85 Hz, hace un interlineado horrible en la pantalla... y siempre lo tuve a 60-70 Hz, y todavía no uso anteojos =P

Así que por ahora me gusta así... ya me acostumbré =)

---

### Post by staar on 2009-05-14
guarda, una cosa es 85 Hz y otra 87 Hz (interlaced, es dos veces 43 Hz, o algo así), no es lo mismo...

saludos

---

### Post by pablo0469 on 2009-05-26
Mirá, lamentablemente desde Hardy a los que tenemos esta placa (la mas problematica de todas, aunque vale para toda la serie 5X y 6X), Ubuntu no ha hecho mas que traernos dolores de cabeza. Entre NVIDIA y Canonical se tiran la pelota entre sí, aunque para ser honesto les creo mas a los de NVIDIA, porque con otras distros (Mandriva, Fedora, Suse) no he tenido ni el menor problema.

Y despues de buscar miles de soluciones, algunas muy complejas, de esas donde se trabaja "al limite", y donde de hecho el resultado fue el quiebre completo del servidor gráfico, la unica que mas o menos me ha permitido ir tirando para no cambiarme de distro es copiar el xorg.conf de Feisty o Gutsy, y despues hacerle los retoques necesarios.

Lo podes hacer imprimiendo el xorg.conf desde una sesión live o copiandolo tras la instalacion en una maquina virtual.

El problema aparentemente es que hay algunos pequeños modulos del kernel que son incompatibles con los drivers de esta placa, y la solucion mas aconsejable es la modificacion del xorg.conf.

Espero no haberte mareado, y ojala te sirva.

Saludos.

---

### Post by guillermon on 2009-05-28
Hola, la me sumo a este post que recién descubro. Yo tengo el mismo problema, pero más complicado. He aplicado la solución propuesta más arriba y me ha mejorado el hecho de que no me hace el 87 (interlace); es decir, no se ve con rayas, y desencuadrado. Del mismo modo que ha pasado, se pone con bajos Hz, que es del todo terrible. Lo peor en mi caso es que lo hace en mi sesión solamente. Cierro la mía, abro la de mi mujer, y está con unos 85 Hz radiantes (pero no tiene sonido... se corta luego de hacer el sonido de inicio); y lo mismo ocurrió cuando cerré esa sesión y abrí una nueva de prueba, en la que andaba bien la resolución y tenía sonido, ahora ya no lo tiene!
  ¿no es el mismo xorg.config para todas los usuarios?
Gracias si alguien tiene una solución, saludos

---


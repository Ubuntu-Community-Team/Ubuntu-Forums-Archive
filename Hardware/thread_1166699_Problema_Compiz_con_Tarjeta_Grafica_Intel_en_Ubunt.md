---
title: "Problema Compiz con Tarjeta Grafica Intel en Ubuntu 9.04 Jaunty"
date: 2009-05-22
forum: Hardware
---

### Post by dnovai on 2009-05-22
Hola amigos!,
Les cuento que desde que actualice el sistema de 8.10 a 9.04 no he podido activar los efectos de escritorio de compiz. Mi laptop es un compaq 751la y tengo la siguiente tarjeta gráfica:

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Estuvo revisando algunos foros e investigando, pero no he podido solucionar el problema. El archivo /etc/X11/xorg.conf me entrega lo siguiente:



```
david@david-laptop:~$ gedit /etc/X11/xorg.conf
```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Al parecer no me esta detectando la tarjeta gráfica o los controladores no corresponden.

Alguna solución, sugerencia o ayuda se los agradeceré.


Saludos!!

---

### Post by Carlos C on 2009-05-22
Mira acá:

[http://ubuntuforums.org/showpost.php?p=7316719&postcount=2](http://ubuntuforums.org/showpost.php?p=7316719&postcount=2)

---

### Post by 3nG3ndR0 on 2009-05-22
> **dnovai said:**
> Hola amigos!,
Les cuento que desde que actualice el sistema de 8.10 a 9.04 no he podido activar los efectos de escritorio de compiz. Mi laptop es un compaq 751la y tengo la siguiente tarjeta gráfica:

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Estuvo revisando algunos foros e investigando, pero no he podido solucionar el problema. El archivo /etc/X11/xorg.conf me entrega lo siguiente:



```
david@david-laptop:~$ gedit /etc/X11/xorg.conf
```Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Al parecer no me esta detectando la tarjeta gráfica o los controladores no corresponden.

Alguna solución, sugerencia o ayuda se los agradeceré.

Saludos!!

Navegando por ahí encontré esta [solución]("http://www.chilecomparte.cl/index.php?showtopic=797300"), espero te ayude a solucionar tu problema.

---

### Post by Patriciologico on 2009-05-22
Lo primero que debes tener en cuenta es que si estan descativados es por algo, y ese algo es importante: **No existe un driver estable de intel** por lo cual compiz tiene tu tarjeta en blacklist (sacarla asi de cajon como proponen algunos foros, me parece un poco bruto)

Luego habemus porfiudus, que queremos a toda costa toquetear el sistema.

Te propongo dos cosas: la primera me parece sensata y la segunda es la que aplique en mi PC :D y se me cuelga de vez en cuando :p Pero funcionan bien el 95 % del tiempo (ya que la solucion 2 implica actualizacion casi diaria de drivers)

1.- activa las actualizaciones sugeridas y no soportadas e instala las de compiz y xorg-intel y esperes que den con la solucion en algun paquete futuro (las cosas en el Software Libre andan rapido)

2.- Sigue las instrucciones de esta [Pagina]("http://kaeltas.blogspot.com/2009/05/como-solucionar-problemas-de.html")

Por ultimo te pido que edites el titulo de tu post y lo hagas mas descriptivo: Por ejemplo "Problema Compiz con Tarjeta Grafica Intel en Ubuntu 9.04 Jaunty"

Saludos!!

---

### Post by Carlos C on 2009-05-22
> **Patriciologico said:**
> 
Por ultimo te pido que edites el titulo de tu post y lo hagas mas descriptivo: Por ejemplo "Problema Compiz con Tarjeta Grafica Intel en Ubuntu 9.04 Jaunty"

Saludos!!

Hecho.

---

### Post by dnovai on 2009-06-09
Hola, he intentado de todo y he googleado, pero nada me ha dado resultado.

Como puedo estar al tanto de las actualizaciones o un sitio oficial donde me muestren las GPU (o aceleradores gráficos) que están en la blacklist para estar al tanto de las modificaciones y actualizacones.

Saludos!
Igual seguiré intentando o de último caso me tocará volver a 8.10

---

### Post by moreback on 2009-06-09
Estimado, Ud. no ha leído el foro, hay post especial para activar UXA en las Intel que incluso está pegado en el subforo de Hardware!

[http://ubuntuforums.org/showthread.php?t=1166388](http://ubuntuforums.org/showthread.php?t=1166388)


SLd.s

---

### Post by dnovai on 2009-06-09
Gracias, intentare con lo que me dicen.


Saludos!):P

---

### Post by dnovai on 2009-06-09
Hola moreback!
Hice lo que me dejaste en el link, pero no obtuve ninguna mejora.

Alguna otra idea?
:-k


Saludos!

---

### Post by CdK1 on 2009-06-09
Supongo que tienes:

xserver-xorg-video-intel

Además cuando hablas que tienes problemas después de actualizar, doy por hecho que tenías corriendo compiz no? si es así, borra también los archivos de configuración en tú $HOME/ de compiz y vuelve a correrlo...

y que tu xorg.conf es algo similar a esto:

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "latam"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver        "intel"
    Option        "DRI" "true"
    BusID        "PCI:0:2:0"
    Option        "AllowGLXWithComposite" "true"
    Option        "RenderAccel" "true"
    Option        "XAANoOffscreenPixmaps" "True"
    Option        "UseFBDev" "true"
    Option        "AccelMethod" "XAA"
EndSection

Section "Monitor"
    Identifier    "Monitor genérico"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Monitor        "Monitor genérico"
    DefaultDepth    24
#    Option        "AddARGBGLXVisuals" "True"
    SubSection "Display"
        Modes        "1280x800" 
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

Section "DRI"
    Group 0
    Mode 0666
EndSection

---

### Post by dnovai on 2009-06-09
Eso es lo que me arroja:
```
david@david-laptop:~$ sudo gedit /etc/X11/xorg.conf
```> Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Option        "AccelMethod" "uxa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionAdemás, tengo instalado el xserver-xorg-video-intel 2.4
y tambien he quitado editado
```

david@david-laptop:~$ gedit /etc/xdg/compiz/compiz-manager 
```> SKIP_CHECKS=yes
Alguna otra sugerencia?

Saludos!

---

### Post by CdK1 on 2009-06-10
1° Supongo que antes de actualizar los efectos te funcionaban verdad?
2° Probaste cambiando tu xorg.conf por el que te postee verdad?
3° Probaste borrando los archivos de configuracin de compiz verdad?

Espero tu respuesta ;)

---

### Post by moreback on 2009-06-10
Revisa que tu archivo **/var/log/Xorg.0.log** contenga las siguientes líneas:

```
(**) intel(0): Using UXA for acceleration
```o lo siguiente:

```
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
```

Esto es indicativo de la activación de UXA, después sólo tienes que activar los efectos desde **Sistema -> Preferencias -> Apariencia**, pestaña **Efectos visuales**.

Saludos.

:KS

---

### Post by dnovai on 2009-06-10
> 1° Supongo que antes de actualizar los efectos te funcionaban verdad?Efectivamente, antes de pasar de 8.10 a 9.04 todos los efectos del compiz funcionaban a la perfección.

> 2° Probaste cambiando tu xorg.conf por el que te postee verdad?Si te refieres a modificar la línea...

> Option        "AccelMethod" "uxa"Si lo hice.

3° Probaste borrando los archivos de configuración de compiz verdad?
Esto no supe como hacerlo, pero asumí que reinstalando los paquetes de compiz quedaría la configuración que trae por defecto. Podrías decir a que te refieres con este punto con un poco mas de detalles.

Finalmente revisando el archivo [B]/var/log/Xorg.0.log
[/B]```

(--) intel(0): Using UXA for acceleration
```y...
```
.
.
..
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
...
.
.
```Supongo que existe una diferencia entre los "(--)" y los "(**)" o me equivoco?

Gracias por tu paciencia.
Saludos!

---

### Post by moreback on 2009-06-10
En verdad el último log es el que más importa ya que te indica que a través de UXA tiene soporte de *composite*.

Creo que tu problema es con el compiz, revisa nuevamente el archivo **/etc/xdg/compiz/compiz-manager** y verifica que tenga la línea **SKIP_CHECKS=yes**.

Saludos

---

### Post by dnovai on 2009-06-12
```
david@david-laptop:~$ gedit /etc/xdg/compiz/compiz-manager 
```
```
SKIP_CHECKS=yes
```Esta como lo dices tú.
Alguna otra sospecha =S


Saludos y gracias por la ayuda.

---

### Post by moreback on 2009-06-12
¿Qué error te da al intentar activar los efectos? ¿Qué método usas? Pega pantallazo del error.

Gracias.

---

### Post by dnovai on 2009-06-17
Me voy a Sistema>Preferencias>Apariencia y selecciono efectos visuales.


[ATTACH]118018[/ATTACH]

[ATTACH]118019[/ATTACH]

[ATTACH]118020[/ATTACH]

Eso es lo que me sucede.

Gracias por la ayuda.

---

### Post by CdK1 on 2009-06-17
Cuando hagas eso en una terminal escribe tail -f .xsession-error apra ver cuale s el error exacto además de hacerlo con el archivo: tail -f /var/log/Xorg.0.log

Me refiero a que dentro de tu $HOME se crearon ciertos directorios tipo .compiz, etc, borralos y prueba...

---

### Post by moreback on 2009-06-18
Me huele a tarjeta de video en lista negra, para confirmar ejecuta en un terminal

compiz --replace

y fijate los errores que imprime... ah! y no olvides postearlos.

---

### Post by dnovai on 2009-06-18
Esto es lo que obtengo al ejecutar el comando en una terminal...

```
root@david-laptop:/home/david# compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz: 455: /usr/local/bin/compiz: not found
xterm:  bad command line option "--replace"

usage:  xterm [-/+132] [-C] [-Sccn] [-T string] [-/+ah] [-/+ai] [-/+aw]
    [-b number] [-/+bc] [-bcf milliseconds] [-bcn milliseconds] [-bd color]
    [-/+bdc] [-bg color] [-bw number] [-/+cb] [-cc classrange] [-/+cjk_width]
    [-class string] [-/+cm] [-/+cn] [-cr color] [-/+cu] [-/+dc]
    [-display displayname] [-e command args ...] [-fa pattern] [-fb fontname]
    [-/+fbb] [-/+fbx] [-fd pattern] [-fg color] [-fi fontname] [-fn fontname]
    [-fs size] [-fw fontname] [-fwb fontname] [-fx fontname] [%geom] [#geom]
    [-geometry geom] [-help] [-/+hm] [-/+hold] [-iconic] [-/+ie] [-/+im]
    [-into windowId] [-/+j] [-/+k8] [-kt keyboardtype] [-/+l] [-/+lc]
    [-lcc path] [-leftbar] [-lf filename] [-/+ls] [-/+maximized] [-/+mb]
    [-mc milliseconds] [-/+mesg] [-/+mk_width] [-ms color] [-n string]
    [-name string] [-nb number] [-/+nul] [-/+pc] [-/+pob] [-rightbar] [-/+rv]
    [-/+rvc] [-/+rw] [-/+s] [-/+samename] [-/+sb] [-selbg color] [-selfg color]
    [-/+sf] [-/+si] [-/+sk] [-sl number] [-/+sm] [-/+sp] [-/+t] [-ti termid]
    [-title string] [-tm string] [-tn name] [-/+u8] [-/+uc] [-/+ulc] [-/+ulit]
    [-/+ut] [-/+vb] [-version] [-/+wc] [-/+wf] [-xrm resourcestring]
    [-ziconbeep percent]

Type xterm -help for a full description.

```Alguna idea, yo soy newbie en esto de linux.
Gracias por tu ayuda, saludos!

---

### Post by moreback on 2009-06-18
Creo que el problema está en tu xorg.conf, prueba borrando la línea que dice

```
Option        "UseFBDev"        "true"
```

Me parece que eso activa video vía framebuffer (eso pasa por el kernel directamente) y no tiene soporte para aceleración.

Saludos.

---

### Post by giov on 2009-06-18
Tuve   al parecer el mismo problema que tu,   después de mucho probar, probar, probar e..   intentar asimile que mi sistema ya no estaba como debía   debido a muchos cambios hechos, me meti al irc ubuntu-es ahí alguien me dijo que probara los repositorios que indican como aun no soportadas y los que salen como aun no publicadas en esa había un driver de prueba que había funcionado bastante bien, a si que entre a pikar, reinstale ubuntu completo, y la primera actualización la hice con esa casilla activada, y me funciono bastante bien, no he tenido problemas de ningún tipo.

tal ves t puede ayudar ojala que si.
y con todo funcionando a mil
:p

salu2

---

### Post by dnovai on 2009-06-18
Gracias moreback por tu paciencia, pero no dio resultado lo ultimo que me sugeriste. Por lo visto nada dara resultado y leyendo lo que dice el amigo del ultimo post, creo que ya he probado tantas cosas que mi sistema lo he modificado y ya no recuerdo nada de lo que hice.

He tomado la desicion de reinstalar ubuntu desde cero. El dilema que tengo es si instalo la version 8.10 que me funcionaba a full y luego actualizo el sistema (que fue el metodo que realice la ultima vez) o instalar desde un disco la version 9.04 directamente.

Que me recomiendan?

Saludos!

y gracias por su paciencia.

---

### Post by dnovai on 2009-06-19
Bueno, se tardaron mucho xD

ya estoy por ubuntu 8.10

Ahora me queda probar si puedo activar los efectos de escritorio.

Saludos!

---

### Post by dnovai on 2009-06-19
Hola, ya estoy con los efectos del escritorio de compiz ubuntu 8.10. interpid ibex. Ahora la pregunta sera conveniente actualizar el sistema a 9.04???

que opinas moreback?

Saludos!

---

### Post by giov on 2009-06-19
No se si probaste lo qeu t dije pero creo que es una buena alternativa ya que en mi caso me funciono

---

### Post by dnovai on 2009-06-19
giov:
Pero tu tarjeta grafica estaba en la black list?
A que repositorios te refieres? cuando dices:

> los repositorios que indican como aun no soportadas y los que salen como aun no publicadas en esa había un driver de prueba que había funcionado bastante bien, a si que entre a pikar, reinstale ubuntu completo, y la primera actualización la hice con esa casilla activada, y me funciono bastante bien, no he tenido problemas de ningún tipo.


Saludos!

---

### Post by giov on 2009-06-20
Segun me dijeron que si, emmm   pero no lo tengo muy claro si alguien sabe...
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by moreback on 2009-06-20
La GM965 está en lista negra de Compiz, así que si actualizas a 9.04 no te van a funcionar los efectos a menos que ponga el texto **SKIP_CHECKS = yes** en el archivo **/etc/xdg/compiz/compiz-manager**.

---

### Post by giov on 2009-06-20
no kiero ser repetitivo pero no modifique ningun archivo, y tengo los efectos funcionando a full

y active las casillas en Sistema-->administración--> Orígenes de software

Ahy tan las 2 casillas a las que me refiero

---

### Post by dnovai on 2009-06-21
Una duda giov. Tu instalalntes ubuntu 9.04desde un disco de instalacion o pasaste desde 8.10 actualizando el sistema a 9.04?

Yo hice lo segundo la ultima vez y me sucedio el problemilla que me hizo volver ha instalar 8.10.

Lo otro, si fue la segunda opcion. Antes de actualizar el sistema 8.10 a 9.04 configurastes dichas opciones (las que muestras en el pantallazo) y luego permitiste al sistema actualizarse?

Gracias por la paciencia.
Saludos!

---

### Post by giov on 2009-06-22
No   lo instale nuevamente y los pasos que t indique los hice apenas instalado luego desactive las casillas para continuar normalmente, espero haya sido de ayuda

---

### Post by dnovai on 2009-06-22
Quisiste decir:
No lo instale nuevamente y los pasos que te indique los hice apenas instalado. Luego desactive las casillas para continuar normalmente. Espero haya sido de ayuda.

ó

No, lo instale nuevamente y los pasos que te indique los hice apenas instalado. Luego desactive las casillas para continuar normalmente. Espero haya sido de ayuda.

Saludos!

---

### Post by giov on 2009-06-24
> **dnovai said:**
> Quisiste decir:
No lo instale nuevamente y los pasos que te indique los hice apenas instalado. Luego desactive las casillas para continuar normalmente. Espero haya sido de ayuda.

ó

No, lo instale nuevamente y los pasos que te indique los hice apenas instalado. Luego desactive las casillas para continuar normalmente. Espero haya sido de ayuda.

Saludos!

Sorry 
Emmm   opcion 2 
"No,lo instale ........  "

---

### Post by RafaelG on 2009-06-25
Hola Yo tuve el mismo Problema y lo Solucione de este modo revisa el siguiente Link:

[http://ubuntusur.org/?p=512](http://ubuntusur.org/?p=512)

y despues habilitie Aceleracion UXA y no he tenido mas Problema 

Espero te sirva a ti tambien 
Saludos.

---

### Post by Patriciologico on 2009-06-25
Rafael, estas recomendando una solución incompleta, como lo dije en la primera página de este thread. No es llegar y sacar Intel del Blacklist como dice el post que enlazaste, por algo esta en blacklist y eso por si solo, aunque active efectos, no resuelve el problema. Es más, aun no hay solución definitiva, sólo posibles soluciones, por favor documentense m&#347;s al respecto.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) 

Ahi hay una muy buena guía (que ya Carlos C posteo en un tema similar)

y aqui he puesto mas información:

[http://ubuntuforums.org/showthread.php?t=1190336](http://ubuntuforums.org/showthread.php?t=1190336)

**Recuerden todas las soluciones son riesgosas para el sistema.**

Saludos!

---

### Post by giov on 2009-06-25
Que sabes de la forma que solucione este tema???

---

### Post by Patriciologico on 2009-06-25
No se cual es tu Intel, no he leido a nadie mas (por su puesto que hay muuucho que no he leido) que solucione solo con actualizar. Si he sabido de actualizaciones que solucionan el problema, pero cambiando repositorios y agregando actualizaciones propuestas o no soportadas.

Saludos

---

### Post by dnovai on 2009-06-25
Esta complicada la cosa.
Por el momento prefiero quedarme en Ubuntu 8.10 intrepid ibex.

No quiero dejar la embarrada nuevamente.


Saludos!

---


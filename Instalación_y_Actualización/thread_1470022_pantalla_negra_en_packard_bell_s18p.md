---
title: "pantalla negra en packard bell s18p"
date: 2010-05-02
forum: Instalación y Actualización
---

### Post by viejash on 2010-05-02
hola amigos linuxeros, mi problema consiste en que no puedo instalar o iniciar ubuntu netbook edition 10.04 en mi netbook packard bell s18p [este ]("http://www.packardbell.cl/sitio/notebook/easynote_s18p.php")debido a que la pantalla se queda en negro, ya he intentado con las opciones de arranque como noacpi, etc. nada funciona. incluso probe con karmic koala pero me da el mismo problema.

lo que quiero saber es si existe alguna distro que funcione para mi netbook porque creo que con ubuntu ya no va a andar.

porfavor no me hagan pebre que soy pollo..  si me falta alguna informacion me la indican para agregarla.

salu2:P

---

### Post by Carlos C on 2010-05-02
Tienes idea del modelo de tarjeta de video que tiene tu equipo?

---

### Post by viejash on 2010-05-03
si, me parece que es una AMD custom graphics, del procesador "embedded" AMD LX800, por lo visto encontre a gente que le funciona el Jaunty asi que lo estoy descargando.. luego les cuento si me funciona o no =)

---

### Post by viejash on 2010-05-03
no me funciono ubuntu 9.04 !! inicia y se escucha el sonido, pero no se ve nada en la pantalla.. algun consejo para hacer funcionar el video?

salu2

---

### Post by XERO_ZX on 2010-10-11
Hola tengo el mismo modelo de netbook y me ocurre algo similar salvo que solo una vez logre que iniciara desde el pendrive cambiando la secuencia de boot del equipo. aun si luego de aparecer la pantalla de presentacion de Ubuntu para cargar pasa a una pantalla negra y no avanza mas.

---

### Post by themasterdark on 2010-10-11
A modo de post rápido (estoy algo apurado), podrías probar con la última versión (Ubuntu 10.10 Maverick Meerkat) del sistema que vio la luz ayer 10/10/10

te dejo el link de descarga:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

Saludos y espero se arreglen las cosas con la última versión del sistema.

---

### Post by Maciett on 2010-11-17
Hola,

Yo tengo ese modelo y, a ensayo y error, el SO que funciona más rápido es el crunchbang, pero no es perfecto, aún no aprendo a configurar la wireless, pero he hecho más de 30 informes para la universidad, con necesidad de editar contenido multimedia para ellos, sin mayores problemas, y lo básico, entiéndase gestor de correo, navegar en inet, es expedito con los programas que deje.

Recuerdo que en otro post otra persona que también tenía este equipo contaba que le había funcionado bien Xubuntu, es otra alternativa.

Saludos

---

### Post by viejash on 2010-12-17
holas y gracias por todas sus respuestas, bueno despues de ensayo y error tal como dijo Maciett, el único SO de ubuntu en donde funciono la pantalla fue el 7.04, todos los demas tienen el mismo problema de la pantalla negra.. el crunchbag tampoco me funciono (la ultima version). 

bueno lo curioso de todo esto es que se me ocurrió probar el ubuntu 10.10 pero como saben no me levantaba la pantalla de instalacion, entonces leí por ahí la genial idea de conectarle al netbook una pantalla externa (la de mi pc de escritorio)... como se imaginaran, logre instalar el SO y los drivers de la tarjeta eran correctos, actualicé el sistema pero igual seguía sin funcionar la pantalla del netbook. por esto concluyo que el problema no esta en la tarjeta de video sino en el _monitor_ y me gustaria saber si alguien sabe como solucionarlo.

probé lo de configurar manualmente el archivo xorg.conf pero no me resulto =(. yo creo que la clave esta en saber como esta configurado el tema de la pantalla en el ubuntu 7.04 y eso aplicarlo a las otras distros... ahora que recuerdo en el 7.04 me aparecían las resoluciones soportadas por la pantallita durante la instalación, en cambio en el 7.10 ya no aparecian marcadas con una x. a que se deberá esto????

agradezco de antemano todos sus aportes al tema

---

### Post by moreback on 2010-12-17
Yo antes hacía ajustes finos con **xvidtune**. La idea era jugar con los Modelines y ponerlos en el xf86config de ese tiempo, ahora el archivo es /etc/X11/xorg.conf, pero ya ni viene pq todo se autodetecta.

Creo que la solución iría por generar un xorg.conf genérico y agregarle las frecuencias que soporta tu monitor (escarba en la documentación de tu pc para ver si las encuentras) y los Modelines si es que son necesarios. Usa xvidtune para sacarlos.

Saludos.

---

### Post by viejash on 2010-12-18
bueno, intente cambiar las frecuencias con xvidtune como me dijiste pero me dio fallo :(. Lo que creo yo (supongo), es que no me detecta la pantalla y el video funciona (o si no no podria estar escribiendo esto en la otra pantalla).

si alguien sabe como forzar la deteccion de la pantalla, o bien que deberia modificar en el xorg conf aqui adjunto lo que me sale, lo ideal seria que la pantalla funcionara en 1024x768 60Hz.

muchas gracias por toda la ayuda =)

>   GNU nano 2.2.4         Archivo: /etc/X11/xorg.conf                            

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
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "dri2"
        Load  "glx"
        Load  "extmod"
        Load  "dbe"
        Load  "dri"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection
Section "Module"
        Load  "dri2"
        Load  "glx"
        Load  "extmod"
        Load  "dbe"
        Load  "dri"
        Load  "record"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        Identifier  "Card0"
        Driver      "geode"
        BusID       "PCI:0:1:1"
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



---


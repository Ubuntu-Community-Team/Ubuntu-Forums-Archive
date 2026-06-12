---
title: "Problema con nVidia GeForce 2 MX y Samsung SyncMaster 551v"
date: 2010-02-10
forum: Hardware
---

### Post by renzo.martinez.friz on 2010-02-10
Estimados:

Desde hace meses vago por uno y otro sitio buscando solución a mi problema con un PC que tiene lo siguiente:

-  Tarjeta gráfica:  nVidia GeForce 2 MX Integrated Graphics.
-  Un monitor Samsung SyncMaster 551v.
-  Ubuntu 9.10

Al terminar la instalación, la pantalla se enciende en una resolución de 800x600 y quiero que quede en 1024x768.

Instalo en controlador nVidia recomendado (96) y realizo los cambios de configuración, pero sólo con resultados peores.  Puesto que si bien es cierto la imagen se ajusta a lo requerido, al abrir y cerrar un ventana esta queda "manchando" la pantalla a pesar de ya haberse cerrado.  En otras oportunidades, los textos se quedan pegados.  Todo lo anterior sólo si estoy trabajando "a prueba de fallos", porque al tratar de ingresar de manera normal, la pantalla de inicio se pega.

He tratado con varias configuraciones, forzando la carga del monitor, pero no doy en el clavo.  ¿Podrían ayudarme por favor?

---

### Post by Carlos C on 2010-02-11
Hola. Voy a mover el thread al subforo "Hardware". Por favor recuerda siempre publicar en el subforo adecuado.

Respecto a tu problema, dinos qué te aparece si en tu panel superior accedes a Sistema-->Administración-->Controladores  de hardware.

Saludos.

---

### Post by xtremox on 2010-02-11
hola yo tenia el mismo problema con esa tarjeta lo arregle instalando el envy y poniendo el controlador mas viejo de nvidia el mismo envy te dice cual version es la recomendada

```
Abrimos el terminal y escribimos

sudo apt-get install envyng-gtk

aceptamos todo y cuando termine el proceso cargamos

sudo apt-get install envyng-qt

después escribimos

sudo apt-get install envyng-core

Ahora instalamos el driver de la placa de video

sudo envyng -t 
```

fuente [http://www.taringa.net/posts/linux/1576090/EnvyNG---Drivers-ATI-o-Nvidia-para-Ubuntu.html](http://www.taringa.net/posts/linux/1576090/EnvyNG---Drivers-ATI-o-Nvidia-para-Ubuntu.html)

---

### Post by renzo.martinez.friz on 2010-02-11
> **Carlos C said:**
> Hola. Voy a mover el thread al subforo "Hardware". Por favor recuerda siempre publicar en el subforo adecuado.
 
Respecto a tu problema, dinos qué te aparece si en tu panel superior accedes a Sistema-->Administración-->Controladores de hardware.
 
Saludos.
 
Aparece que me recomienda el controlador 96 (que está en este momento activado gracias a la configuración que me entregó xtremox). Sin embargo, después de sólo ingresar "GNOME a prueba de fallos", pero al cambiar la configuración a 1024x768 lo hace a medias porque si leo un menú, queda como una "huella" de donde estuvo el menú y sólo se puede limpiar si se pasa el mouse encima de nuevo, pero vuelve a quedar con lo que mostró el mouse la última vez que pasó sobre un lugar.  De ingresar "GNOME" quedará pegado durante la carga.
 
Al final opera tan mal que termino quitando el controlador para, por lo menos, ver sin huellas ni sombras a 800x600.
 
El archivo xorg.conf no dice nada y no sé cómo generar uno nuevo para poder mostralo aquí y de ahí ver si es posible corregir este problemita.

---

### Post by robertor on 2010-02-11
Una consultilla de rebote... para descartar problemas con el driver de video... pero por lo menos en ATI (que es la gráfica que tengo) el driver empezó a dejar modelos sin soporte... ¿con nvidia pasa lo mismo
¿Has probado con el driver libre (nv)? En el xorg.conf podrias agregar (o modificar) estas lineas:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver "nv"
EndSection

```

Luego reinicias la X (ctrl+alt+backspace) y ve que pasa.
Saludos,
Roberto

---

### Post by renzo.martinez.friz on 2010-02-12
> **robertor said:**
> Una consultilla de rebote... para descartar problemas con el driver de video... pero por lo menos en ATI (que es la gráfica que tengo) el driver empezó a dejar modelos sin soporte... ¿con nvidia pasa lo mismo
¿Has probado con el driver libre (nv)? En el xorg.conf podrias agregar (o modificar) estas lineas:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver "nv"
EndSection

```
 
Luego reinicias la X (ctrl+alt+backspace) y ve que pasa.
Saludos,
Roberto
 
 
El problema es que Xorg.conf está más pelado que z... de muñeca. No tiene ningún dato ahí. No sé cómo generar uno nuevo para agregar modificaciones.  Me parece que hay una instrucción Conf Nvidia, pero no la tengo en ninguna parte puesto que la vi antes de reinstalar 9.10 y se borró del PC, como no me acuerdo cuando la tiro a San Google, no me arroja lo que busco.
[-(

---

### Post by Carlos C on 2010-02-13
> **renzo.martinez.friz said:**
> El problema es que Xorg.conf está más pelado que z... de muñeca. No tiene ningún dato ahí. No sé cómo generar uno nuevo para agregar modificaciones.
[-(
Para crear un xorg.conf nuevo puedes usar este comando:
```
sudo X :1 -configure
```
Con eso se crea un archivo xorg.conf.new en tu home y debes copiarlo en la carpeta correspondiente:
```
sudo cp xorg.con.new /etc/X11/xorg.conf
```

Saludos.

---

### Post by renzo.martinez.friz on 2010-02-16
Gracias,  por fin se generó.  

Este es el actual contenido:

> 
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
    Load  "record"
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    VendorName  "nVidia Corporation"
    BoardName   "NVCrush11 [GeForce2 MX Integrated Graphics]"
    BusID       "PCI:2:0:0"
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


Qué puedo cambiar?  Como les conté tengo la tarjeta Nvidia (que se entorpece con el driver 96x) y un monitor Samsung SyncMaster 551v.

Por su atención,  gracias.

---

### Post by renzo.martinez.friz on 2010-02-18
> **renzo.martinez.friz said:**
> Gracias, por fin se generó. 
 
Este es el actual contenido:
 
 
 
Qué puedo cambiar? Como les conté tengo la tarjeta Nvidia (que se entorpece con el driver 96x) y un monitor Samsung SyncMaster 551v.
 
Por su atención, gracias.
 
Siguiendo estos pasos: [http://ubuntuforums.org/showthread.php?t=1215309](http://ubuntuforums.org/showthread.php?t=1215309)
 
El sistema en la partida me indica que encontró un error y que Ubuntu se iniciará en baja resolución, al ingresar sigue todo igual como antes de haber intervenido. El xorg.conf se mantiene con los últimos datos modificados.

---

### Post by Carlos C on 2010-02-18
Copia acá cómo estás dejando tu *Section "Monitor"*

---

### Post by renzo.martinez.friz on 2010-02-18
> **Carlos C said:**
> Copia acá cómo estás dejando tu *Section "Monitor"*
 
Quedó tal cual la recomendación de la dirección superior:
 
>  
Section "Monitor"
          Identifier "Configured Monitor"
          HorizSync 30-55
          VertRefresh 50-120
          Option "DPMS"
EndSection
 

 
Tal como dice el link anterior, primero grabé esta parte y reinicié sin problemas; pero el monitor no estaba reconocido aún como Samsung SyncMaster 551v ni las resoluciones sobrepasaban del actual 800x600.

---

### Post by Carlos C on 2010-02-18
Su *Section "Screen"* también es diferente, ¿la cambiaste?

---

### Post by renzo.martinez.friz on 2010-02-19
> **Carlos C said:**
> Su *Section "Screen"* también es diferente, ¿la cambiaste?

Sí, copié lo mismo de la instrucción y ahí se me producía el problema debido a que al inicio del archivo Xorg.conf dice:
> Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Donde identifica '*Screen 0 "Screen0" 0 0'* y el texto que copie decìa:
> Section "Screen"
	Identifier	"Default Screen"...
	

Como arriba decía "*Screen0"* y más abajo "Screen" se perdía.

Se arregló, ahora sólo me queda ajustar a 75Mzh la tasa de refresco y arreglar el teclado numérico, pues en el modo consola funciona bien mas no de modo gráfico en Ubuntu.

Se agradece enormemente la ayuda, pues fueron meses sin corregir este problema.

---

### Post by Carlos C on 2010-02-19
Para modificar el refresco puedes mirar como lo hicieron en este thread:

[http://ubuntuforums.org/showthread.php?t=1364175&page=2](http://ubuntuforums.org/showthread.php?t=1364175&page=2)

Saludos.

---

### Post by renzo.martinez.friz on 2010-02-19
> **Carlos C said:**
> Para modificar el refresco puedes mirar como lo hicieron en este thread:

[http://ubuntuforums.org/showthread.php?t=1364175&page=2](http://ubuntuforums.org/showthread.php?t=1364175&page=2)

Saludos.

El problema del teclado lo solucioné así, súper fácil.  Gracias por tu ayuda.

[http://www.soygik.com/solucion-no-funciona-el-teclado-numerico/](http://www.soygik.com/solucion-no-funciona-el-teclado-numerico/)

---

### Post by renzo.martinez.friz on 2010-02-21
El problema con la tasa de refresco no lo puedo cambiar, este es mi nuevo Xorg.conf

> Section "ServerLayout"
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
    Load  "record"
    Load  "glx"
    Load  "extmod"
    Load  "dbe"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
    HorizSync 30-55
    VertRefresh 50-120
    Option "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    VendorName  "nVidia Corporation"
    BoardName   "NVCrush11 [GeForce2 MX Integrated Graphics]"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    DefaultDepth 24
    SubSection "Display"
    Depth 1
    Modes "1024x768_75 +0+0"
    EndSubSection
    SubSection "Display"
    Depth 4
    Modes "1024x768_75 +0+0"
    EndSubSection
    SubSection "Display"
    Depth 8
    Modes "1024x768_75 +0+0"
    EndSubSection
    SubSection "Display"
    Depth 15
    Modes "1024x768_75 +0+0"
    EndSubSection
    SubSection "Display"
    Depth 16
    Modes "1024x768_75 +0+0"
    EndSubSection
    SubSection "Display"
    Depth 24
    Modes "1024x768_75 +0+0"
    EndSubSection
EndSection


¿Están bien anotadas las configuraciones "1024x768_75 +0 +0"?  En las opciones *Sistemas > Preferencias > Pantallas *indica sólo la tasa de 60 mhz.

---

### Post by Carlos C on 2010-02-22
El problema es que añadiste la configuración a tu *Section "Screen"*, pero no lo hiciste en tu *Section "Monitor"*. El listado de *Modes* de la primera lo único que hace es activar los modos definidos en tu *Section "Monitor"*. Por lo tanto, si llamas un modo que no ha sido definido no va a funcionar. Definelo también en tu *Section "Monitor"*. Si te fijas, es lo que hicieron en el enlace que usamos como referencia.


Cuando tengas dudas siempre puedes mirar acá:

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)


Saludos.

---

### Post by robertor on 2010-02-22
> **renzo.martinez.friz said:**
> El problema con la tasa de refresco no lo puedo cambiar, este es mi nuevo Xorg.conf
¿Están bien anotadas las configuraciones "1024x768_75 +0 +0"?  En las opciones *Sistemas > Preferencias > Pantallas *indica sólo la tasa de 60 mhz.

Ojo, que el refresco no está dado solo por lo que le pongas al xorg.conf. Existe una limitación física del hardware. Tu monitor, debiera tener cual es el rango que soporta y esos valores los debieras poner en el Xorg, con lo que automáticamente se determina cual es el refresco que se usará.
En el manual de tu monitor (o en las especificaciones de este) debieran aparecer los valores para el refresco horizontal y vertical y cual es el refresco soportado según las resoluciones que uses.
Saludos,
Roberto

---


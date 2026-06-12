---
title: "[SOLVED] Tableta Wacom"
date: 2008-05-22
forum: Hardware
---

### Post by Gpafundi on 2008-05-22
Hola a todos. Soy novato en esto. Hice el paso de Windows a Ubuntu hace mas o menos 2 semanas y me costo bastante entender como funciona esto. Todavía hay cosas que son bastante complicadas y que no entiendo. De a poco fui instalando todos los drivers en mi Ubuntu 8.04 pero mi problema es el siguiente:

Tengo una tableta Wacom Graphire 4 y no puedo instalarla correctamente. Hice varios intentos y todos fueron fallidos. De hecho, la mayoría me arruinaron Ubuntu y lo tuve que reinstalar. La verdad que me encanta el sistema operativo y me siento muy entusiasmado. Es lo único que me falta instalar. Si alguien puede ayudarme, desde ya le agradezco. 

Por favor, si alguien sabe y tiene ganas de explicarme, les pido que sean bastante claros en la especificación ya que todavía no comprendo demasiado como funciona todo esto.

---

### Post by faktorqm on 2008-05-22
Hola, primero que nada bienvenido al foro. :D

En segundo lugar, vamos a intentar ayudarte lo más que podamos, debés tener en cuenta que la gente que hace esto (entre ellos me incluyo) lo hace en su tiempo libre y lo hace "de onda", así que quizá nadie te responda, o quizá te respondan muchos, pero la idea es que no te desesperes, y sepas por que ocurre esto. 

Por último, te pediría que postees algunos comandos que necesitamos saber para reunir más información sobre tu computadora, y así poder ayudarte mejor en el proceso de instalación de tu Wacom. 

Para cumplir con el último punto, contanos si ese Wacom es USB (tengo entendido que si), que compu tenes, y estos comandos:

Ir a Aplicaciones -> Accesorios -> Terminal

```
cat /etc/X11/xorg.conf
```
```
lspci
```
```
lsusb
```

El primer comando muestra el contenido del archivo xorg.conf ubicado en /etc/X11. El segundo muestra una lista de los dispositivos pci de tu computadora. El tercero muestra una lista de los dispositivos usb de tu computadora. (Debes correrlo con la wacom conectada claro está)

Espero tu respuesta, Salu2!!

---

### Post by Gpafundi on 2008-05-23
Hola. Desde ya muchas gracias por intentar ayudarme.

Mira, te cuento. Mi tableta es USB. Me acuerdo que al tratar de instalarla (siguiendo unos pasos que posteaba la gente) me hacían modificar el "xorg.conf". No se bien que es, pero me hacían ingresar unos datos en el archivo.

Bueno, escribí lo que me dijiste en el terminal y me devolvió esto:



Al poner "cat /etc/X11/xorg.conf"

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection






Al poner "lspci"

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE6145 SATA II PCI-E controller (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)






Y al poner "lsusb"

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:002b Microsoft Corp. Internet Keyboard Pro
Bus 001 Device 004: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 056a:0016 Wacom Co., Ltd 
Bus 002 Device 001: ID 0000:0000  






Desde ya te agradezco tu interés.

---

### Post by MeduZa on 2008-05-23
tenes que editar el xorg.conf (esta en /etc/X11 ) y sacarle el # a la wacom que corresponda con la tuya (ahi 3) 
mas que eso no te puedo decir :( pero se qeu estan desactivados por defecto proque en edgy venian activados y molestaban mucho sobre todo al photoshop en wine!

> Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

y estas:
> 
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

si no las tenes proba agregarlas, y despues echate una busqueda en don google que capas haya mas info.


saludos.

---

### Post by faktorqm on 2008-05-24
Hola, ya estoy de vuelta. Mas o menos este tutorial lo vi en todos lados, asi que paso en limpio:

Primero instalamos los paquetes necesarios:

```
sudo apt-get install wacom-tools xserver-xorg-input-wacom
```

Si ya los tenes instalados no te preocupes que te los saltea. Ahora bien, hacemos un back de nuestro xorg.conf por las dudas de que algo ande mal...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back_wacom
```

Ahora editamos el archivo xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

Y localizamos la seccion "server layout" (si no existe agregala al final del archivo tal como se muestra aca):

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen 0 "Screen0"   0 0
        InputDevice    "Mouse0"    "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

```

y te tiene que quedar algo asi:

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen 0 "Screen0"   0 0
        InputDevice    "Mouse0"    "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # Sólo para tablas NO-LCD
        InputDevice    "pad"
EndSection

```

Lo que esta despues de un numeral es un comentario. Si tu tabla es LCD, vas a tener que eliminar esa linea.

Ahora también debemos agregar esto pero NO al final, sino exactamente abajo de donde se encuentre la seccion "InputDevice" que contenga al mouse. (Te vas a dar cuenta por que dice /dev/mouse o algo por el estilo)
NOTA: Al igual que antes, si tu tabla es LCD, no debes agregar la parte que diga "option" Type cursor.

```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event0"   
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event0"   
  Option        "Type"          "eraser"
  Option        "USB"           "on"                 
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event0" 
  Option        "Type"          "cursor"
  Option        "USB"           "on"                
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/event0"   
  Option        "Type"          "pad"
  Option        "USB"           "on"                  
EndSection
```

Despues lo guardas. Ahora cerras todos los programas y apretas "CTRL + ALT + BKSPACE" y se te va a reiniciar la interfaz grafica, ahi te logueas de vuelta y probas a ver si te funciona. Si tenes problemas nos consultas.
Salu2!

Bibliografia consultada:

[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main) (the linux wacom project howto)
[http://ubuntufs.wordpress.com/2007/02/28/wacom-tablet-tutorial/](http://ubuntufs.wordpress.com/2007/02/28/wacom-tablet-tutorial/) (blog de un usuario)
[http://blog.ubrio.us/ubuntu/review-wacom-graphire4-on-ubuntu-feisty-fawn/](http://blog.ubrio.us/ubuntu/review-wacom-graphire4-on-ubuntu-feisty-fawn/) (otro blog)

---

### Post by Gpafundi on 2008-05-27
Probé lo que me pusiste faktorqm y no me funciono. De hecho, por algún motivo me desconfiguró, no se si la placa de vídeo, o el monitor o algo por el estilo. Ya me había pasado al seguir otros tutoriales. Además no andaba la tableta. Pero por suerte hice el back up que me dijiste y esta vez no tuve que reinstalar ubuntu.

Voy a probar lo que puso el otro post a ver si anda.

Gracias igual. Después les cuento.

---

### Post by Gpafundi on 2008-05-27
Gracias a los dos. Funciono mi tableta Wacom. Probe con lo que puso MeDuZa y andubo barbaro. Muchas gracias.

---

### Post by undolaure on 2009-08-30
Hola,

querría hacer una pequeña corrección de lo faktorqm posteó, para futuras consultas de este hilo. Si no me equivoco, a Gpafundi no le funcionó lo que incluyó en su xorg.conf porque en el post de faktorqm, las líneas donde pone
```

  Option        "Device"        "/dev/input/event0" 
```

tendría que poner, tal y como se indica en el post de Meduza,

```
Option "Device" "/dev/input/wacom"
```

, y es por eso que cuando copió el código de Meduza sí le funcionó. No soy ningún megaexperto, y puede que faktorqm tuviera razones o configuraciones en su ordenador en las que el "event0" era lo que correspondía. En cualquier caso en mi experiencia personal siempre he visto lo del "/dev/input/wacom".

A propósito de esto merece la pena mencionar este hilo también en ubuntuforums, en inglés,
[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)
donde se aborda una forma mucho más compleja de instalar la tableta. Parece ser que fue la utilizada por el autor para instalar una Bamboo, y puede que para este modelo sea realmente necesario hacerlo de este modo. De nuevo desde mi experiencia personal, para el modelo Graphire de Wacom es suficiente seguir los pasos que se indican en el presente hilo, en castellano.

Eso sí, cuidando mucho lo que ponemos en el xorg.conf:
[LIST]
[*]haciendo que concorden los "identifiers" con sus llamadas posteriores que, como era mi caso, no coincidían necesariamente con el ejemplo aportado por el autor. Estoy hablando de los ServerLayout, Screen, InputDevices para el teclado y el ratón, etc. Si hay alguna inconcordancia, puede pasar que este dispositivo (y quizá otros) no funcionen o directamente que no nos arranque el servidor de X, o lo haga en modo "emergencia".
[*]vigilando que todas las secciones tengan encabezado de apertura y pie de cierre, y toda esa mandanga sintáctica
[/LIST]

Gracias en cualquier caso por compartir la información.
Saludos,
Raimon

---

### Post by carlosic on 2012-05-31
Hola:
En la distribución Precise no funcionaron ninguno de los métodos indicados arriba, algunos incluso provocaron que el servidor X no arrancara. Mis problemas se solucionaron así:
1.- Reinstale el paquete para mi distribución desde la dirección:
[https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages](https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages)
2.- Lo probé en un portátil y en un sobremesa. En el 2º el otro problema era que conectaba la Table a un hub usb. Cuando lo conecte directamente al puerto usb del Pc funcionó sin problemas.
Muchas gracias por la ayuda y las indicaciones. Espero que mi aportación os sea útil.

---


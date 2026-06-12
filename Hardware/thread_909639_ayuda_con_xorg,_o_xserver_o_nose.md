---
title: "ayuda con xorg, o xserver o nose"
date: 2008-09-03
forum: Hardware
---

### Post by phxnd on 2008-09-03
actualize los paquetes que cada tanto te avisa automaticamente que hay una version disponible, y siempre tengo problemas, pero esta vez no lo puedo solucionar xD

me tira el siguiente error cuando trato de iniciar

etc/gdm/failsafeXServer
line 47 demasiados argumentos


y se queda trabada ahi y no inicia, lo que hice para poder prenderla es borrar el xorg.conf xD np, igual tengo varios backup, probe reemplazandolo por alguno de los backup pero pasa lo mismo =S

Como hago para arreglar esto



PD no tengo ni los signos de interrogacion jaja

---

### Post by phxnd on 2008-09-05
nadie me puede ayudar??

---

### Post by juanman on 2008-09-06
Hola, debe ser un problema del modulo del driver... Habria q reinstalarlo...
Por favor postea mas datos: placa de video, el xorg.conf.

Una solucion temporaria es cambiar en el xorg.conf, en section device, el driver por el vesa...

Y trata de no usar los repositorios proposed, q suelen traer estos problemas...

---

### Post by phxnd on 2008-09-06
> **juanman said:**
> Hola, debe ser un problema del modulo del driver... Habria q reinstalarlo...
Por favor postea mas datos: placa de video, el xorg.conf.

Una solucion temporaria es cambiar en el xorg.conf, en section device, el driver por el vesa...

Y trata de no usar los repositorios proposed, q suelen traer estos problemas...


tengo una placa de video geforce mx 4000

lo de cambiar el driver po el vesa no entendi, y en cuanto a usar los repositorios proposed te referias a los uqe no son oficiales?


mi xorg es
> Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
    Option         "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Monitor        "SyncMaster"
Option "AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


saludos

---

### Post by phxnd on 2008-09-09
estube viedo un poquito y cuando pongo los siguientes comandos me tira algunos errores:

> usuario@usuario-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

> usuario@usuario-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

y si hago compiz --remplace me tira:
> usuario@usuario-desktop:~$ compiz --remplace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


y buscando, encontre que haciendo:
> sudo dpkg-reconfigure -phigh xserver-xorg
reconfiguraba el xorg, y eso hace ^^ pero sigue pasando lo mismo
ahh y si hago
> sudo nvidia-xconfig
me tira el mismo error de siempre

> etc/gdm/failsafeXServer
line 47 demasiados argumentos

sugerencias?
por lo menos diganme algo asi no piesno que estoy solo contra la maquina ^^

---

### Post by phxnd on 2008-09-10
no me dieron ni bola y gracias a dios lo pude solucionar solo ¬¬
amen
/closed

---

### Post by esplinter on 2009-02-14
muy amable por compartir la solución.......

---


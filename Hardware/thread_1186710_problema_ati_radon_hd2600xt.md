---
title: "problema ati radon hd2600xt"
date: 2009-06-13
forum: Hardware
---

### Post by zaret on 2009-06-13
hola amigos espero que alguno de ustedes pueda ayudarme.
el gran problema es que con ubuntu no puedo activar la aceleración 3d por hardware 
he buscado distintas formas de instalar el driver privativo he usado envy un par de veces y he seguido varias guias que encontré por la red pero no me funciona o me funciona por cortos lapsos de tiempo (cortos lapsos de tiempo es ke derrepente reinicio y se va y me da "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)" )

la descripcion completa de mie hardware es esta [clic aqui]("http://www.alumnos.usm.cl/%7Ecamilo.fonseca/hardwaredelmal.htm") 
cuando instalo los driver privativos con la aplicacion que trae ubuntu para esto el gnome se me cae apenas me pongo a provar si esta la aceleracion 3d con el glxinfo o el glxgears
he usado estas tutoriales espero ke no aya problemas por los link de otras pag
[tutorial 1]("http://www.esdebian.org/wiki/graficas-ati#3.2.2")
[tutorial 2]("http://www.islabit.com/7262/instalando-driver-de-ati-en-ubuntu-904.html")
para las tutoriales use la ultima vercion del driver privativo
 mas las veces que instale los driver privativos de modo grafico
realmente no se que mas hacer

---

### Post by Carlos C on 2009-06-14
hola, te faltó decir qué versión de ubuntu usas. Lo que te digamos dependerá de ese dato.

---

### Post by zaret on 2009-06-14
se me olvidaba uso ubuntu 9.04 pero por lo que he leido por la red al parecer el catalis 9.5 no es compatible con el xorg 1.6 que trae jaunty por lo que he intentado usar el radeon hd pero me da direct redenderin yes pero no me funcionan las transparencias alguna idea??

---

### Post by moreback on 2009-06-15
A lo mejor tu tarjeta está en un a lista negra del compiz, agrega la línea

**SKIP_CHECKS=yes**

a tu archivo **/etc/xdg/compiz/compiz-manager** e intenta activar los efectos nuevamente.

---

### Post by Patriciologico on 2009-06-15
> **moreback said:**
> A lo mejor tu tarjeta está en un a lista negra del compiz, agrega la línea

**SKIP_CHECKS=yes**

a tu archivo **/etc/xdg/compiz/compiz-manager** e intenta activar los efectos nuevamente.

Pero el no tiene aceleración 3D. Entiendo que la lista negra de compiz te impide activar los efectos de escritorio, pero no impide que glxgears funcione, que haya aceleración activada.

---

### Post by kamus on 2009-06-15
> **zaret said:**
> hola amigos espero que alguno de ustedes pueda ayudarme.
el gran problema es que con ubuntu no puedo activar la aceleración 3d por hardware 
he buscado distintas formas de instalar el driver privativo he usado envy un par de veces y he seguido varias guias que encontré por la red pero no me funciona o me funciona por cortos lapsos de tiempo (cortos lapsos de tiempo es ke derrepente reinicio y se va y me da "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)" )

la descripcion completa de mie hardware es esta [clic aqui]("http://www.alumnos.usm.cl/%7Ecamilo.fonseca/hardwaredelmal.htm") 
cuando instalo los driver privativos con la aplicacion que trae ubuntu para esto el gnome se me cae apenas me pongo a provar si esta la aceleracion 3d con el glxinfo o el glxgears
he usado estas tutoriales espero ke no aya problemas por los link de otras pag
[tutorial 1]("http://www.esdebian.org/wiki/graficas-ati#3.2.2")
[tutorial 2]("http://www.islabit.com/7262/instalando-driver-de-ati-en-ubuntu-904.html")
para las tutoriales use la ultima vercion del driver privativo
 mas las veces que instale los driver privativos de modo grafico
realmente no se que mas hacer

Podrias adjuntar tu /etc/X11/xorg.conf ?

salu2

---

### Post by zaret on 2009-06-15
bueno como les contaba tengo "direct rendering yes" pero el rendimiento con el driver libre radeonhd es bastante malo con el glxgears el cual da alrededor de 200 fps comparado que cuando usaba las pruebas del fglrx_gears (o algo asi se escrivia no recuerdo bien) me dava arededor de 1500 fps por lo cual esoty tratando de afinar el driver pero no encuentro una buena wiki que lo explique en español no espero demaciado pero me gustaria llegar a las 500 fps para que se vean bien los efectos  (no soy demaciado bueno con el ingles) bueno de todas maneras les adjunto mi:
[xorg.conf]("http://www.alumnos.usm.cl/%7Ecamilo.fonseca/xorg.conf") 

cualquier cosa que queran saber mas diganmela

---

### Post by moreback on 2009-06-16
Probaste lo que te dije del compiz?

---

### Post by kamus on 2009-06-16
> **zaret said:**
> bueno como les contaba tengo "direct rendering yes" pero el rendimiento con el driver libre radeonhd es bastante malo con el glxgears el cual da alrededor de 200 fps comparado que cuando usaba las pruebas del fglrx_gears (o algo asi se escrivia no recuerdo bien) me dava arededor de 1500 fps por lo cual esoty tratando de afinar el driver pero no encuentro una buena wiki que lo explique en español no espero demaciado pero me gustaria llegar a las 500 fps para que se vean bien los efectos  (no soy demaciado bueno con el ingles) bueno de todas maneras les adjunto mi:
[xorg.conf]("http://www.alumnos.usm.cl/%7Ecamilo.fonseca/xorg.conf") 

cualquier cosa que queran saber mas diganmela

Te adjunto el xorg con una ati 2400 XT HD , ocupando el controlador de ati (descargado de su sitio web).

```

# xorg.conf.failsafe (X.Org X Window System server configuration file)
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
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" 1440 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "vesa"
	Option	    "UseFBDev" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

---

### Post by zaret on 2009-06-18
muchas gracias por el xorg.conf lo provare hacerle un par de modificaciones al mio...
la verdad prove usar el driver privativo que baje de la pagina de ati  y todo bien teni aceleracion 3d y toodo como 1500 glxgears pero de un momento a otro derrepente se me colgo la X mostrrando las ventanas donde no devia y cosa extrañas... rebotie por consola y al volver prove si tenia el directrenderin yes y me decia:
$ glxinfo |grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
asi de la nada proveche de hacer una copia del archivo de log y cosas varias, se me ocurrio probar nuevamente el glxgears y me dava algo asi como esto
~$ glxgears
19958 frames in 5.0 seconds = 3983.210 FPS
22820 frames in 5.0 seconds = 4562.471 FPS
23145 frames in 5.0 seconds = 4628.368 FPS
23112 frames in 5.0 seconds = 4618.584 FPS
22980 frames in 5.0 seconds = 4595.436 FPS
lo cual no comprendo como pudo subir la cantidad de fps posteo mi xorg .conf

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


PD: desde ke instale el driver privativo los efectos del compiz estan funcionando todos...
relamente no se que pasa
saludos

---

### Post by moreback on 2009-06-18
¿Problema solucionado entonces?

---

### Post by zaret on 2009-06-18
como dije se me pego la X y perdi el direct rendering... lo cual me causa algunos problemas varios... asi que aun no esta resuelto
alguna idea

---

### Post by zaret on 2009-06-19
la solucion fue mas simple de lo que esperaba como leir por la red las ATI no tieien aun un driver privativo que funcione bien en jaunty jacalope devido a siertos problemas de inestabilidad  y compativilidad que vi expuesto en mi pc la mejor opcion fue donwgradear a intrepid donde el xserver no es tan nuevo y por lo cual es compatible con los driver privativos de ATI... actualmente esta corriendo muy bien en intrepid hasta que no tenga noticias sobre la compativilidad del driver privativo no upgradeare a jaunty bueno eso es todo:lolflag:

---


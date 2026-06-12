---
title: "Problema de resolución de pantalla"
date: 2008-12-05
forum: Hardware
---

### Post by Malmsteen20 on 2008-12-05
Tengo una PC de arquitectura x86. Tiene un procesador Athlom XP de 1.7 GHz, con 768 MB de RAM, no tengo aceleradora gráfica y Tengo un monitor de 17'' NEC MultiSync V700. Aún así cuando instalo Ubuntu 8.10 tengo problemas con la resolución de pantalla, no puedo ponerla en 1024x768 pixeles porque no me da la opción.

Por alguna razón no encuentro el modelo exacto en la página de NEC de mi monitor pero... estas parecerían ser las especificaciones técnicas del modelo más próximo: [http://www.nec-computers.com/support/pib.asp?platform=spec_V720-721_Multisync&mode=default&source=1409](http://www.nec-computers.com/support/pib.asp?platform=spec_V720-721_Multisync&mode=default&source=1409)
;las dejo por si sirven de algo. :???:

He buscado mucho y en todos lados hablan de editar el archivo xorg.conf pero... como recien estoy queriendo comenzar con Linux, soy novato y, no sé muy bien cómo editarlo o qué poner. :(


¿Qué debo hacer?

---

### Post by guillermolisi on 2008-12-06
> **Malmsteen20 said:**
> Tengo una PC de arquitectura x86. Tiene un procesador Athlom XP de 1.7 GHz, con 768 MB de RAM, no tengo aceleradora gráfica y Tengo un monitor de 17'' NEC MultiSync V700. Aún así cuando instalo Ubuntu 8.10 tengo problemas con la resolución de pantalla, no puedo ponerla en 1024x768 pixeles porque no me da la opción.

Por alguna razón no encuentro el modelo exacto en la página de NEC de mi monitor pero... estas parecerían ser las especificaciones técnicas del modelo más próximo: [http://www.nec-computers.com/support/pib.asp?platform=spec_V720-721_Multisync&mode=default&source=1409](http://www.nec-computers.com/support/pib.asp?platform=spec_V720-721_Multisync&mode=default&source=1409)
;las dejo por si sirven de algo. :???:

He buscado mucho y en todos lados hablan de editar el archivo xorg.conf pero... como recien estoy queriendo comenzar con Linux, soy novato y, no sé muy bien cómo editarlo o qué poner. :(

¿Qué debo hacer?
Una forma de conocer que hardware reconoce Ubuntu es a traves del comando lspci.

Para correrlo y obtener su resultado tenes que abrir una consola e ingresar lspci en la linea de comando. La salida la copias y pegas en otro mensaje, en este mismo hilo de conversacion, asi todos podemos ver la misma informacion y hacerte la mejor sugerencia segun sea el caso.

---

### Post by Malmsteen20 on 2008-12-06
> **guillermolisi said:**
> Una forma de conocer que hardware reconoce Ubuntu es a traves del comando lspci.

Esto es lo que me apareció al ingresar el comando:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

```

Por cierto, muchas gracias por querer ayudarme Guillermo. :)

---

### Post by guillermolisi on 2008-12-06
> **Malmsteen20 said:**
> Esto es lo que me apareció al ingresar el comando:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

```Por cierto, muchas gracias por querer ayudarme Guillermo. :)
Mira, a pesar de los cambios que se han introducido a nivel del Xserver, te paso el contenido del archivo /etc/X11/xorg.conf para que pruebes en tu maquina y ver si logras algun avance:
```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "VESA driver (generic)"
    Busid        "PCI:1:0:0"
    Driver        "vesa"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Samsung"
    Modelname    "Samsung SyncMaster 750(M)s(T)"
    Horizsync    30-70
    Vertrefresh    50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        en la entrada que remarque en negrita hay una resolucion de 1280x1024
        Modes        "1280x1024@60"    "1400x1050@60"    "1280x960@60"    "1152x864@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "ServerFlags"
EndSection

```Si bien la entrada que marque en negrita dice 1280x1024 solo logre que funcione estable en 1024x768 que es lo que queres lograr en tu maquina.

Tengo el mismo chipset de video que tu maquina pero lo uso con driver vesa porque el UniChrome NO funciona at all.

Hacete una copia del archivo que tenes ahora, copialo tipo /etc/X11/xorg.conf.backup por ejemplo y reemplaza entradas, a ver que resultado obtenes (si protesta la copia usa sudo antes del comando cp....)

Cada vez que hagas cambios tenes que reiniciar el servidor X (<ctrl><backspace>) para que los tome.

Conta como te fue.

---

### Post by Malmsteen20 on 2008-12-07
> **guillermolisi said:**
> Mira, a pesar de los cambios que se han introducido a nivel del Xserver, te paso el contenido del archivo /etc/X11/xorg.conf para que pruebes en tu maquina y ver si logras algun avance:
```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "VESA driver (generic)"
    Busid        "PCI:1:0:0"
    Driver        "vesa"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Samsung"
    Modelname    "Samsung SyncMaster 750(M)s(T)"
    Horizsync    30-70
    Vertrefresh    50-160
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        en la entrada que remarque en negrita hay una resolucion de 1280x1024
        Modes        "1280x1024@60"    "1400x1050@60"    "1280x960@60"    "1152x864@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "832x624@75"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@85"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection
Section "ServerFlags"
EndSection

```Si bien la entrada que marque en negrita dice 1280x1024 solo logre que funcione estable en 1024x768 que es lo que queres lograr en tu maquina.

Tengo el mismo chipset de video que tu maquina pero lo uso con driver vesa porque el UniChrome NO funciona at all.

Hacete una copia del archivo que tenes ahora, copialo tipo /etc/X11/xorg.conf.backup por ejemplo y reemplaza entradas, a ver que resultado obtenes (si protesta la copia usa sudo antes del comando cp....)

Cada vez que hagas cambios tenes que reiniciar el servidor X (<ctrl><backspace>) para que los tome.

Conta como te fue.

Probé de diferentes maneras hasta que, en uno de los tantos intentos, al reiniciar la PC, me apareció un error y ya ni siquiera me mostraba el prompt para ingresar algún comando. :???:

Lamento decirte que decidí dejar de lado a Ubuntu (Espero no te enfades por haberte hecho perder tiempo en responderme o algo así). En vez de eso probé otras distribuciones de Linux, empezando por Mandriva pero... tube algunos problemas también y ahora tengo instalado OpenSUSE. Esta última, hasta el momento, no me está dando ningún problema más allá de los que yo espero de una distribución de Linux. Es decir, no tengo problemas más allá del hecho de no poder reproducir mp3 o visualizar videos con formatos cuyos códigos fuente no son "open source".

Lo único de esta distribución que me molesta un poco es la cantidad de espacio en disco que requiere, en comparación con Ubuntu, Mandriva e inclusive respecto al propio Windows XP, pero bue... :p

Te agradezco igualmente el esfuerzo por intentar ayudarme. Y... si conoces buenos manuales/tutoriales y/o páginas web donde expliquen lo necesario para desenvolverse bien en un entorno de Linux te agradecería también si pudieras pasarme las direcciones donde puedo encontrarlos.

Saludos... desde Corrientes, Argentina. ):P

---

### Post by Hei Ku on 2008-12-07
MP3 y otros formatos de video deberías poder reproducirlos sin problemas. Sólo tenés que instalar el paquete correcto. 
Esto es así en Ubuntu, Opensuse o cualquier otra distribucion, e incluso con XP tenes que instalar los codecs aparte. 
Solo busca en Google y te va a aparecer la respuesta. No te puedo orientar mas porque no uso OpenSUSE.

---

### Post by faktorqm on 2008-12-07
Aca hice una guia donde te responde lo que pedis: [http://ubuntuforums.org/showthread.php?t=977483](http://ubuntuforums.org/showthread.php?t=977483) salu2!

---


---
title: "Configurar TV-HD"
date: 2009-05-02
forum: Hardware
---

### Post by dirty fingers on 2009-05-02
Hola comunidad ubuntu. La semana pasada entre al mundo de linux con la versión 9.04. Ya controle bastante problemas comunes de usuario nuevo, y voy encaminado con algún hardware rebelde pero voy a necesitar ayuda con mi "placa de video y TV" porque por mas que busque y busque no encontré ni una pista de por donde empezar. 

Tengo una ASUS 7600GS que trae salida (DVI - VGA - TV) y un TV PHILLIPS 29PT9467

La salida de TV puede funcionar como:
--"video compuesto" un cable lleva toda la informacion (la tipica calidad de imagen que hoy en dia se considera mala).
--"video separado" un cable con 4 pines, tambien conocido como s-video... y que algunos animalitos por ahí piensan que es super-video en vez de separate-video (señal de croma y lumi por separado) bastante mejor , se ve lindo, mas calidad de color y contraste.
--"componentes de video" 3 cables que llevan los colores por separado (mas otros datos) y acá tocamos el cielo ,a la calidad de color y contraste tenemos que sumarle imagen de alta definición de 720x480 para arriba.

La cuestión es que desde windows xp la gente de nvidia me da este hermoso panel para ajustar la placa de video al mode de salida que uso para el TV y desde el "nvidia x server" no tengo nada.

[[IMG]http://img7.imageshack.us/img7/871/xpnvidiatvoutput.jpg[/IMG]]("http://img7.imageshack.us/my.php?image=xpnvidiatvoutput.jpg")

Desde ya muchas gracias por las respuestas. El solo intento de ayudar vale mucho.

-------------------------------------------------------------------------------------------------------------------------
**SOLUCIONADO**

:popcorn: Ya se puede disfrutar el TV con calidad

*Ver solución mas abajo

---

### Post by pablo.s on 2009-05-02
No entiendo el problema...
¿Vos querés tener un panel
igual al de Windows o no tenés
salida de señal?

---

### Post by dirty fingers on 2009-05-03
Quiero saber si tengo que editar algun archivo de texto o bajar un driver, aplicación, etc o que para indicarle a la placa que esta conectado por CVI el TV.
Obvio que si conecto un cable normal se ve porque por defecto la salida compuesta de video funciona pero no tiene ninguna gracia tener un TV-HD y no usarlo.

---

### Post by pablo.s on 2009-05-03
Podés probar con nvtv, está en
los repositorios.

---

### Post by staar on 2009-05-03
primero que nada una pregunta, que no me quedo claro, conectaste la placa al tele, y decís que tenés señal? el problema sería que, dicha señal, no es de la calidad que quisieras?

si es ese tu problema, si, tenés que modificar un 'archivo de texto', más precisamente el /etc/X11/xorg.conf...

para empezar a resolver tu cuestión, por favor postea el contenido de ese archivo, para hacerlo fácilmente, poné este comando en una Terminal ```
cat /etc/X11/xorg.conf
``` y pega acá la salida...

saludos

EDIT: wiki con info sobre tu tema [http://www.mythtv.org/wiki/NVIDIA_Component_Out]("http://www.mythtv.org/wiki/NVIDIA_Component_Out"), ta medio áspera para un novato, pero es lo que hay :-P ;-)

EDIT2: acabo de leer el post de pablo, tiene razón, primero probá con nvtv, es lo más fácil para alguien nuevo, aunque desconozco si tiene la funcionalidad específica que buscás...

---

### Post by dirty fingers on 2009-05-03
Con NVTV tengo el mismo problema que parece tener todo el mundo por lo que leí. No identifica el hard.

```

adrian@Topower:~$ nvtv
Fatal: No supported video card found.

```

Ya estuve mirando el xorg.conf pero solo veo información sobre coordenadas, profundidad de color, resolución, barrido.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG T910B"
    HorizSync       30.0 - 98.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: 1280x1024_85 +0+0; CRT: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024_85 +0+0, TV: 720x480 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Y si me anda en resolución estandar conectado por video compuesto el tv.

Excelente eso que encontraste en wiki. creo que con un poco de paciencia y algunas pruebas puedo hacer que funcione. apenas tenga novedad les cuento y es mas si sale todo perfecto dejo una explicación de como se hace.

---

### Post by dirty fingers on 2009-05-03
**SOLUCIONADO** :popcorn: Ya se puede disfrutar el TV con calidad


Bueno el secreto esta en conocer los comandos de configuración de nvidia y agregarlos en el xorg.conf.

```

The "TVStandard" option should be added to your screen section; valid values are:
      TVStandard     Description
      "PAL-B"     used in Belgium, Denmark, Finland, Germany, Guinea, Hong Kong, India, Indonesia, Italy, Malaysia, The Netherlands, Norway, Portugal, Singapore, Spain, Sweden, and Switzerland
      "PAL-D"     used in China and North Korea
      "PAL-G"     used in Denmark, Finland, Germany, Italy, Malaysia, The Netherlands, Norway, Portugal, Spain, Sweden, and Switzerland
      "PAL-H"     used in Belgium
      "PAL-I"     used in Hong Kong and The United Kingdom
      "PAL-K1"     used in Guinea
      "PAL-M"     used in Brazil
      "PAL-N"     used in France, Paraguay, and Uruguay
      "PAL-NC"     used in Argentina
      "NTSC-J"     used in Japan
      "NTSC-M"     used in Canada, Chile, Colombia, Costa Rica, Ecuador, Haiti, Honduras, Mexico, Panama, Puerto Rico, South Korea, Taiwan, United States of America, and Venezuela
      "HD480i"     480 line interlaced
      "HD480p"     480 line progressive
      "HD720p"     720 line progressive
      "HD1080i"     1080 line interlaced
      "HD1080p"     1080 line progressive
      "HD576i"     576 line interlace
      "HD576p"     576 line progressive

``````

The "TVOutFormat" option can be used to force the output format. Without this option, the driver autodetects the output format. Unfortunately, it does not always do this correctly. The output format can be forced with the "TVOutFormat" option; valid values are:
      TVOutFormat     Description     Supported TV standards
      "AUTOSELECT"     The driver autodetects the output format (default value).     PAL, NTSC, HD
      "COMPOSITE"     Force Composite output format     PAL, NTSC
      "SVIDEO"     Force S-Video output format     PAL, NTSC
      "COMPONENT"     Force Component output format, also called YPbPr     HD
      "SCART"     Force Scart output format, also called Peritel     PAL, NTSC

``````

The "TVOverScan" option can be used to enable Overscan, when the TV encoder supports it. Valid values are decimal values in the range 1.0 (which means overscan as much as possible: make the image as large as possible) and 0.0 (which means disable overscanning: make the image as small as possible). Overscanning is disabled (0.0) by default.

``````

The "UseDisplayDevice" option can be used if there are multiple display devices connected, and you want the connected TV to be used instead of the connected CRTs and/or DFPs. E.g.,

```

---

### Post by luks911 on 2009-05-03
Como no la tengo del todo clara con el xorg, ¿cómo te quedó el archivo después de las modificaciones?

Gracias

---

### Post by dirty fingers on 2009-05-03
Solo agregue dos lineas:
```

Option         "TVStandard" "*"
Option         "TVOutFormat" "*"

```* = la opcion que corresponda a el cable que usas y la resolucion del tv

Apenas hago un ajuste mas te muestro el archivo; ahora que se ve, estoy probando entre "twinview" y "separate x screen" para ver cual es mas adecuada para ver video a pantalla completa en el tv y poder seguir usando el monitor para otra cosa.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Hay que usar "separate x screen" al parecer para que tome los ajustes del tv. con "twinview" no lo logro. Mete esas dos lineas que te dije en screen(ojo, el screen del tv no del monitor)
Con VLC podes configurar que el video a pantalla completa vaya siempre a parar al tv.

---

### Post by staar on 2009-05-03
me alegro que te haya funcionado ;-)

saludos

---

### Post by luks911 on 2009-05-03
> **dirty fingers said:**
> Solo agregue dos lineas:
```

Option         "TVStandard" "*"
Option         "TVOutFormat" "*"

```* = la opcion que corresponda a el cable que usas y la resolucion del tv

Apenas hago un ajuste mas te muestro el archivo; ahora que se ve, estoy probando entre "twinview" y "separate x screen" para ver cual es mas adecuada para ver video a pantalla completa en el tv y poder seguir usando el monitor para otra cosa.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Hay que usar "separate x screen" al parecer para que tome los ajustes del tv. con "twinview" no lo logro. Mete esas dos lineas que te dije en screen(ojo, el screen del tv no del monitor)
Con VLC podes configurar que el video a pantalla completa vaya siempre a parar al tv.

¡Muchas gracias!

---


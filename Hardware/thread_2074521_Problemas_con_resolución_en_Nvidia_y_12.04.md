---
title: "Problemas con resolución en Nvidia y 12.04"
date: 2012-10-21
forum: Hardware
---

### Post by RubeDF on 2012-10-21
Buenas. Les comento que soy nuevo en el foro pero no tanto en ubuntu. Paso a mi problema tengo ubuntu 12.04 instalado con los controladores privativos de nvidia. Y con esto me vino el clasico problema de la resolucion de pantalla.
Mi monitor es un samsung syncmaster 933 de 18.5 pulgadas 1360x768, bastante comun en Argentina, el problema en si no es la resolucion ya que modificando el xorg.conf queda configurado, lo raro esta en la definicon de la pantalla, las letras se ven como borrosas y algunas no tienen el tamaño adecuado. 
Lo raro es que con el driver libre se ve bien definida la imagen. aunque no siempre reconoce el monitor y se queda en 1024x768. 

Mi placa es una nvidia gt430,  no quiero usar el driver libre por miedo a la gestion de energía. Mi presentimiento me dice que es un problema de edid porque nouveau lo reconoce perfectamente y configuroa sin necesidad de tocar el xorg. dejo una imagen y una copia de mi xorg.conf espero que puedan darme una mano.

[http://sta.sh/0188k3v8q52o](http://sta.sh/0188k3v8q52o)

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster 933SN"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    option         "UseEdid" "False"
    Option         "MetaModes" "1360x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1360x768"
    EndSubSection
EndSection


---


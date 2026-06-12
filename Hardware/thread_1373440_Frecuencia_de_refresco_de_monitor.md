---
title: "Frecuencia de refresco de monitor"
date: 2010-01-05
forum: Hardware
---

### Post by mauri19877 on 2010-01-05
Buenas tardes.

Como muchas otras personas, tuve problemas con el driver de video (nvidia) y la taza de refresco del monitor. Actualmente el único problema que tengo es que cuando inicia la sesión, inicia con la tasa de refresco del monitor en 60 Hz (en realidad seguramente sea menos, ya que se ven lineas en el monitor) Generé modelines como se habla en [este post]("http://ubuntuforums.org/showthread.php?t=1156560&page=2") pero igual inicia en 60 hz según nvidia-settings.

Monitor: ViewSonic e70 17 pulgadas
Video: Geforce 5070

Una aclaración: poniendo en 70 hz es cuando se logra el mejor resultado, aunque igual apenas se ven lineas. en una resolución mayor, sin ser interlace las lineas son más notorias. Este monitor lo probé en otra pc y no tengo inconvenientes.

Muchas gracias.

Mi xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E70-8"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    ModeLine       "1024x768_70.00" 76.16 1024 1080 1192 1360 768 769 772 800 -hsync +vsync
    Option         "PreferredMode" "1024x768_70.00"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 / nForce 610i"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "UseEdid" "False"
    Option         "Metamode" "1024x768_70 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---


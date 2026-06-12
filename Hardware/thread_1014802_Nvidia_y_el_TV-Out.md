---
title: "Nvidia y el TV-Out"
date: 2008-12-18
forum: Hardware
---

### Post by Thalskarth on 2008-12-18
Hola gente, quería hacerles 2 consultas:

[LIST=1]
[*]Existe alguna forma de usar la salida TV-Out de mi placa Nvidia (FX 5200) usando los drivers libres "nv"?? o eso solo puede lograrse con los privativos?

[*]Sea con los privativos o con los libres, como hago para que el TV y el monitor muestren exactamente lo mismo (twinview) pero acorde a sus resoluciones, o sea..el monitor lo tengo seteado en 1280*1024 pero el TV no admite eso y el máximo es 1024*768. El drama es que si los seteo así, el TV solo muestre un pedazo de la pantalla quedando cosas fuera por lo que me veo obligado a bajar la resolución del monitor para que al estar los 2 en 1024*768 muestren lo mismo.
En windows, podía hacerlo y lo debaja configurado así, pero en gnu/linux todavía no encontré forma de hacerlo, es posible??
[/LIST]

Desde ya muchas gracias

---

### Post by ! ! ! winner on 2008-12-18
> **Thalskarth said:**
> Hola gente, quería hacerles 2 consultas:

[LIST=1]
[*]Existe alguna forma de usar la salida TV-Out de mi placa Nvidia (FX 5200) usando los drivers libres "nv"?? o eso solo puede lograrse con los privativos?

[*]Sea con los privativos o con los libres, como hago para que el TV y el monitor muestren exactamente lo mismo (twinview) pero acorde a sus resoluciones, o sea..el monitor lo tengo seteado en 1280*1024 pero el TV no admite eso y el máximo es 1024*768. El drama es que si los seteo así, el TV solo muestre un pedazo de la pantalla quedando cosas fuera por lo que me veo obligado a bajar la resolución del monitor para que al estar los 2 en 1024*768 muestren lo mismo.
En windows, podía hacerlo y lo debaja configurado así, pero en gnu/linux todavía no encontré forma de hacerlo, es posible??
[/LIST]

Desde ya muchas gracias



[http://www.prizerebel.com/index.php?r=806574](http://www.prizerebel.com/index.php?r=806574)

---

### Post by rojojuan on 2008-12-18
> **Thalskarth said:**
> Hola gente, quería hacerles 2 consultas:

[LIST=1]
[*]Existe alguna forma de usar la salida TV-Out de mi placa Nvidia (FX 5200) usando los drivers libres "nv"?? o eso solo puede lograrse con los privativos?

[*]Sea con los privativos o con los libres, como hago para que el TV y el monitor muestren exactamente lo mismo (twinview) pero acorde a sus resoluciones, o sea..el monitor lo tengo seteado en 1280*1024 pero el TV no admite eso y el máximo es 1024*768. El drama es que si los seteo así, el TV solo muestre un pedazo de la pantalla quedando cosas fuera por lo que me veo obligado a bajar la resolución del monitor para que al estar los 2 en 1024*768 muestren lo mismo.

En windows, podía hacerlo y lo debaja configurado así, pero en gnu/linux todavía no encontré forma de hacerlo, es posible??
[/LIST]

Desde ya muchas gracias

Yo uso los privativos.
Dejalo en 1024 por 768  y elegí la opción clone en nvidia-settings, que se instala en sistema cuando bajas los drivers privativos.

Ante todo es importante averiguar qué versión de Ubuntu usás porque me parece que esa placa anda en Hardy Heron pero no en Intrepid.
Si usas Hardy podés correr para instalar los drivers la utilidad envyNG. Ojo en Intrepid no.
Si tenés más dudas, la podemos seguir hasta donde se acaben mis conocimientos.

---

### Post by Thalskarth on 2008-12-19
> **rojojuan said:**
> Yo uso los privativos.
Dejalo en 1024 por 768  y elegí la opción clone en nvidia-settings, que se instala en sistema cuando bajas los drivers privativos.

Ante todo es importante averiguar qué versión de Ubuntu usás porque me parece que esa placa anda en Hardy Heron pero no en Intrepid.
Si usas Hardy podés correr para instalar los drivers la utilidad envyNG. Ojo en Intrepid no.
Si tenés más dudas, la podemos seguir hasta donde se acaben mis conocimientos.

Hola, uso Intrepid y con el nvidia-settings he podido hacerlo... mi duda es si no puedo dejar el monitor a más resolución ya que a 1024 todo se ve "muy grande".

Sino de ultima, voy configuro y desconfiguro cada vez que quiero el TV-Out, con el nvidia-settings no es tán dificil por suerte... pero si hubiese forma de que funcionase así, como hacía en windows, sería más práctico.

gracias

---

### Post by rojojuan on 2008-12-19
> **Thalskarth said:**
> Hola, uso Intrepid y con el nvidia-settings he podido hacerlo... mi duda es si no puedo dejar el monitor a más resolución ya que a 1024 todo se ve "muy grande".

Sino de ultima, voy configuro y desconfiguro cada vez que quiero el TV-Out, con el nvidia-settings no es tán dificil por suerte... pero si hubiese forma de que funcionase así, como hacía en windows, sería más práctico.

gracias


Probaste usando la opción clone?

---

### Post by granjero on 2008-12-19
yo uso ubuntu hardy, y mi placa es una 8600gt pero me imagino que el xserver no debe cambiar mucho.

en mi configuración TWIN VIEW, a pesar de que la traducción sería "vistas gemelas·, es añadir otra pantalla que es parte del escritorio.

te dejo un screen de mi xserver y una copia del xorg.conf me parece que es un poco desprolijo, pero funciona...



> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
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
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: 640x480 +1440+210"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


yo no logré tener el duplicado pero me gusto esta configurración para ver pelis en el cuarto...

salud!

---

### Post by Thalskarth on 2008-12-20
hoy no estoy en casa, pero en cuanto pueda pruebo con esa idea,

gracias :)

---


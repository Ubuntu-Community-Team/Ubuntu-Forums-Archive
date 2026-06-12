---
title: "[How-To] Problemas con resolución en Nvidia"
date: 2009-06-09
forum: Hardware
---

### Post by staar on 2009-06-09
Bueno, visto que es un problema bastante común y que se abren muchos threads al respecto, me decidí a hacer este how-to de como solucionarlo.

El problema en cuestión es la falla del driver propietario de Nvidia al colocar la resolución correcta para nuestro monitor (en la mayoría de los casos, porque no es capaz de leer correctamente la [EDID]("http://en.wikipedia.org/wiki/EDID") del mismo), con otras placas de video este problema no surge, debido a que los demás drivers usan XRandR, una extensión del X Server que permite manejar los temas de resolución, y que tiene mejor autodetección de hard gracias al uso de HAL.

_Traducción de los síntomas para novatos_ :-D: después de instalar el driver privativo de Nvidia, al iniciar, o bien no se ve nada y el monitor tira 'Out of Range' (o similar), o bien la resolución seteada es incorrecta y no se puede colocar la deseada desde Resolución de pantalla en Sistema > Preferencias (esto último es lógico, ya que dicha aplicación es solo un front-end para XRandR, que no funciona con los drivers privativos de Nvidia), ni desde NVIDIA X Server Settings en Sistema > Administración (esta herramienta es útil, pero no hace magia, lo que no hace el driver, no lo hace ella, y además no es muy práctica agregando resoluciones)

_Paso 1_: instalar los drivers privativos, si no estaban instalados ya (en Sistema > Administración > Controladores de hardware) y correr en una Terminal (Aplicaciones > Accesorios > Terminal) ```
sudo nvidia-xconfig
``` para que el driver de Nvidia escriba en el archivo de configuración del X Server (el servidor gráfico) los datos que es capaz de detectar...

_Paso 2_: reiniciar la sesión, si la resolución es la correcta, el tutorial termina acá, feliz uso de ubuntu :-), si la resolución es incorrecta el tutorial sigue...

_Paso 3_: si la resolución no es la correcta pueden ocurrir dos cosas:

- el monitor se queda en negro con un cartel que indica 'Out of Range', con Ctrl + Alt + - se puede disminuir la resolución, si esto no funciona, con Ctrl + Alt + F1 se puede acceder a una consola virtual y trabajar desde alli...
- el monitor si es capaz de mostrar la resolución, por lo que el inicio es normal, pero se ve todo 'grande'...

En ambos casos, hay que editar el archivo de configuración del servidor X, y agregarle los datos de nuestro monitor. Ese archivo está en /etc/X11/xorg.conf (en sistemas Unix como GNU/Linux, las mayúsculas son importantes, la carpeta es X11, con mayúscula), y para modificarlo se necesitan permisos de administrador (root), por lo que se usa el comando 'sudo'. En el primer caso, al no tener activo el servidor gráfico, se debe usar un editor de texto de consola, como 'nano', que es el más simple, en 'nano' se usan las Flechas para mover el cursor, Ctrl + O para guardar, Ctrl + W para buscar una palabra, y Ctrl + X para salir. En el segundo caso se puede usar el editor de textos de Gnome, 'gedit' que es gráfico y muy fácil de usar.

Bueno, en el primer caso, una vez logueados en la consola virtual, tipeamos ```
sudo nano /etc/X11/xorg.conf
``` para editar el archivo.
En el segundo caso, en una Terminal, tipeamos ```
sudo gedit /etc/X11/xorg.conf
```
En ambos casos hacemos las siguientes modificaciones:

-Vamos hasta la sección Monitor, que debe ser similar a esta (puede variar): ```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CRT-0" 
EndSection
``` y le agregamos dos valores, el VertRefresh y el HorizSync, dejándola así: ```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "CRT-0" 
    [B]HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0[/B]
EndSection
``` estos valores cambian entre los modelos y tipos de monitor, tienen que colocar los que correspondan a SU monitor, los cuales pueden encontrar en el manual, en las especificaciones o en internet (son valores en Hz, muchas veces traducidos como refresco horizontal y vertical).

-Luego nos dirigimos a la sección Screen: ```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
``` y le agregamos tres opciones, una para que no lea los datos desde el EDID, otra para indicarle la resolución deseada, y una última para indicarle algunas de las resoluciones que sabemos que el monitor es capaz de mostrar: ```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    [B]Option         "UseEdid" "False"
    Option         "MetaModes" "1400x1050 +0+0"[/B]
    SubSection     "Display"
        Depth       24
        **Modes      "1400x1050" "1280x1024" "1024x768" "800x600"**
    EndSubSection
EndSection
``` obviamente sustituyendo esos valores de resolución por los que correspondan a SU monitor (el +0+0 es el panning, no cambiar, a menos que sepan lo que hacen).

-Guardar (en nano Ctrl + O, Enter) y salir del editor (Ctrl + X en nano).

-Si estamos en una consola virtual, iniciar las X con ```
sudo /etc/init.d/gdm start
```

-Si estamos en Gnome, reiniciar sesión.

Eso es todo, al iniciar sesión nuevamente, la resolución debería ser la correcta.

saludos

---

### Post by pablo.s on 2009-06-09
Muy buen trabajo!

---

### Post by josecuervo86 on 2009-06-09
Muy bueno Staar!!

---

### Post by staar on 2009-06-10
'chas gracia' compañeros!

---

### Post by rubioo on 2009-06-10
Excelente trabajo staar!!!
 Aunque yo desde que me compré mi placa Nvidia no tuve ningún problema, a
 más de uno le va a servir mucho


             Saludos!

---

### Post by danielasrin on 2009-07-16
lamentablemente sigo con el mismo problema. Sigo todos los pasos, pero al volver a iniciar sesión vuelvo con la resolución 800x600, cuando en el xorg.conf dice:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

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
    Identifier    
*"Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7050 PV / NVIDIA nForce 630a"
EndSection

Section "Screen"

# Removed Option "metamodes" "1360x768_60 +0+0; 1360x768 +0+0; nvidia-auto-select +0+0"
# Removed Option "metamodes" "1440x900 +0+0; 1360x768_60 +0+0; 1360x768 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "False"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1360x768 +0+0; 1360x768_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
   
*EndSubSection
EndSection

alguna otra sugerencia?

---

### Post by staar on 2009-07-16
y con el xorg.conf así? ```

Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Module"
Load "dbe"
Load "extmod"
Load "type1"
Load "freetype"
Load "glx"
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "CRT-0"
HorizSync 30.0 - 61.0
VertRefresh 56.0 - 75.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 7050 PV / NVIDIA nForce 630a"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "UseEdid" "False"
Option "TwinView" "0"
Option "TwinViewXineramaInfoOrder" "CRT-0"
Option "metamodes" "1360x768 +0+0"
SubSection "Display"
Depth 24
Modes "1360x768"
EndSubSection
EndSection
```

saludos

---

### Post by gaboxeon on 2009-08-25
ola uqe tal llevo tiempo usando linux y me acabo de conseguir una tv de lcd de 32" y me es muy frustante no poderle dar la resolucion que deberia (1360x768), ya intente modificando el xorg.conf y cuando reinicio el x, la pantalla vuelve a la resolucion de 1024x768,  y cuando la cambio con el nvidia settings la pantalla se alarga demasiado o me pone recortados los 1360x768 en un cuadro de 1024x768.... antes de leer tu how to(ayer) no se como pero si pude ponerle la resolcion pero al reiniciarla regreso a lo mismo, 


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "Monitor"
#    Identifier     "Configured Monitor"
#EndSection
#Section "Device"
#    Identifier     "Configured Video Device"
#    Driver         "nvidia"
#    Option         "NoLogo" "True"
#EndSection
#Section "Screen"
#    Identifier     "Default Screen"
#    Device         "Configured Video Device"
#    Monitor        "Configured Monitor"
#    DefaultDepth    24
#EndSection
#Section "Screen"
#    Identifier     "Screen0"
#    Device         "Device0"
#    Monitor        "Monitor0"
#    DefaultDepth    24
#    Option         "UseEdid" "False"
#    Option         "MetaModes" "1360x768 +0+0"
#    SubSection     "Display"
#        Depth       24
#    Modes      "1360x768" "1280x768" 
#    EndSubSection
#EndSection

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
    Option         "DontZap" "False"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
# Removed Option "metamodes" "1360x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "False"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1360x768 +0+0; 1360x768 @1360x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by staar on 2009-08-25
primero, asegurate que los valores de horizsync y vertrefresh sean los correctos, buscalos en el manual del monitor...

después, intentá con el xorg.conf así ```

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Screen0" 0 0
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "Mouse0" "CorePointer"
EndSection

Section "Module"
  Load "glx"
EndSection

Section "ServerFlags"
  Option "DontZap" "False"
  Option "Xinerama" "0"
EndSection

Section "InputDevice"
  Identifier "Keyboard0"
  Driver "kbd"
EndSection

Section "InputDevice"
  Identifier "Mouse0"
  Driver "mouse"
  Option "Protocol" "auto"
  Option "Device" "/dev/psaux"
  Option "Emulate3Buttons" "no"
  Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
  Identifier "Monitor0"
  VendorName "Unknown"
  ModelName "CRT-0"
  HorizSync 28.0 - 55.0
  VertRefresh 43.0 - 72.0
EndSection

Section "Device"
  Identifier "Device0"
  Driver "nvidia"
  VendorName "NVIDIA Corporation"
  BoardName "GeForce 6200"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  Option "UseEdid" "False"
  Option "TwinView" "0"
  Option "TwinViewXineramaInfoOrder" "CRT-0"
  **Option "MetaModes" "1360x768 +0+0"**
 SubSection "Display"
   **Modes "1360x768"**
   Depth 24
 EndSubSection
EndSection
```

saludos

---

### Post by nemodot on 2009-09-12
Che, no hay modo, no puedo corregir el problema.

Gracias a esta guía pude resolverlo hace un mes pero ahora me compre un nuevo monitor y no se queda en la resolucion deseada.

Arranca con una resolución de 1024x768 cuando mi monitor es de 23'' (Aún cuando en el xorg.conf dice claramente "1920x1080" y estan hechas todas las modificaciones sugeridas en este post.

El Nvidia settings es el que se reinicia a 1024x768 cada vez.

Entre otras cosas también he notado que las especificaciones del compiz manager también vuelven a como estaban en un principio por default así que aunque desactive las horrendas "woobly windows", al reiniciar las tengo de nuevo.

---

### Post by staar on 2009-09-12
> **nemodot said:**
> Che, no hay modo, no puedo corregir el problema.

Gracias a esta guía pude resolverlo hace un mes pero ahora me compre un nuevo monitor y no se queda en la resolucion deseada.

Arranca con una resolución de 1024x768 cuando mi monitor es de 23'' (Aún cuando en el xorg.conf dice claramente "1920x1080" y estan hechas todas las modificaciones sugeridas en este post.

El Nvidia settings es el que se reinicia a 1024x768 cada vez.

Entre otras cosas también he notado que las especificaciones del compiz manager también vuelven a como estaban en un principio por default así que aunque desactive las horrendas "woobly windows", al reiniciar las tengo de nuevo.

mmm, creando un usuario nuevo, e iniciando con ese, también te pasa? que placa es?

saludos

---

### Post by PabloGNU/LINUX on 2009-09-12
> [SIZE=3][COLOR=Red]danielasrin, gaboxeon, nemodot esta puede ser su solucion[/COLOR][/SIZE] Bueno despues de hacer todo eso hay que guardar el archivo en Xorg.conf al intentar guardarlo no se puede, por que estamos restringidos entonces hacemos lo siguiente:

1_Antes de guardar se puede ver un preview del back up. Copiamos toda esa seccion
2_Abrimos Terminal y colocamos: Sudo gedit /etc/x11/xorg.conf
3_Reemplazamos el contenido por el que tenemos en el portapapeles ( osea lo que copiamos)
4_Guardamos y cerramos

y listo cuando inicien el Sitema de nuevo van a tener la resolusion que guardaron.

---

### Post by PabloGNU/LINUX on 2009-09-12
> *[SIZE=3][COLOR=Red]danielasrin, gaboxeon, nemodot esta puede ser su solucion[/COLOR][/SIZE]* 

Bueno despues de hacer todo eso hay que guardar el archivo en Xorg.conf al intentar guardarlo no se puede, por que estamos restringidos entonces hacemos lo siguiente:

1_Antes de guardar se puede ver un preview del back up. Copiamos toda esa seccion
2_Abrimos Terminal y colocamos: Sudo gedit /etc/x11/xorg.conf
3_Reemplazamos el contenido por el que tenemos en el portapapeles ( osea lo que copiamos)
4_Guardamos y cerramos

y listo cuando inicien el Sitema de nuevo van a tener la resolusion que guardaron.

---

### Post by staar on 2009-09-12
> **PabloGNU/LINUX said:**
> Bueno despues de hacer todo eso hay que guardar el archivo en Xorg.conf al intentar guardarlo no se puede, por que estamos restringidos entonces hacemos lo siguiente:

1_Antes de guardar se puede ver un preview del back up. Copiamos toda esa seccion
2_Abrimos Terminal y colocamos: Sudo gedit /etc/x11/xorg.conf
3_Reemplazamos el contenido por el que tenemos en el portapapeles ( osea lo que copiamos)
4_Guardamos y cerramos

y listo cuando inicien el Sitema de nuevo van a tener la resolusion que guardaron.
si lees bien el tutorial te vas a dar cuenta que especifica que se abra el editor de textos (nano o gedit) usando sudo, además, el nvidia-settings solo modifica la opción Metamodes cuando se quiere cambiar la resolución, y el tutorial explica como hacerlo a mano, asi que el uso de la utilidad de nvidia no es necesario (es más, mejor no usarlo)

saludos

---

### Post by nemodot on 2009-09-12
> **PabloGNU/LINUX said:**
> Bueno despues de hacer todo eso hay que guardar el archivo en Xorg.conf al intentar guardarlo no se puede, por que estamos restringidos entonces hacemos lo siguiente:

1_Antes de guardar se puede ver un preview del back up. Copiamos toda esa seccion
2_Abrimos Terminal y colocamos: Sudo gedit /etc/x11/xorg.conf
3_Reemplazamos el contenido por el que tenemos en el portapapeles ( osea lo que copiamos)
4_Guardamos y cerramos

y listo cuando inicien el Sitema de nuevo van a tener la resolusion que guardaron.

Eso ya lo hice antes como primer solución pero ya no funciona, de todas formas seria incoherente por que en mi caso el xorg ya está configurado como debería ser, me parece que el problema es del programa de nvidia-settings.

Tengo una Geforce 6600gt

---

### Post by PabloGNU/LINUX on 2009-09-12
Claro, despues comprendi. tu caso. 
Saludos, sepan disculpar.

---

### Post by nemodot on 2009-09-15
No quiero ser <pesado> pero todavía no puedo arreglar el problema.

Hice todo lo que dicen en la guía con distintas combinaciones pero nada sirve, sigo comenzando con una resolucion de 1024x867 en un monitor de 23''.

Este es mi xorg:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

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
    ModelName      "CRT-0"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"

# Removed Option "MetaModes" "1280x1024 +0+0"
# Removed Option "metamodes" "1280x1024_60 +0+0"
# Removed Option "metamodes" "1920x1080 +0+0"
# Removed Option "metamodes" "1920x1080_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "False"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by guillermolisi on 2009-09-15
Nemodot, por favor, cuida tu lenguage.

---

### Post by staar on 2009-09-15
> **nemodot said:**
> No quiero ser <pesado> pero todavía no puedo arreglar el problema.

Hice todo lo que dicen en la guía con distintas combinaciones pero nada sirve, sigo comenzando con una resolucion de 1024x867 en un monitor de 23''.

Este es mi xorg:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

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
    ModelName      "CRT-0"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"

# Removed Option "MetaModes" "1280x1024 +0+0"
# Removed Option "metamodes" "1280x1024_60 +0+0"
# Removed Option "metamodes" "1920x1080 +0+0"
# Removed Option "metamodes" "1920x1080_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdid" "False"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
en la sección "Screen", subsección "Display", no definiste los modos que soporta el monitor...

que resolución tenés seleccionada en el nvidia-settings? y en el programita que trae ubuntu? podrías postear el contenido del archivo /var/log/Xorg.0.log?

que versión de los drivers usas? la 180.xx, no? porque este tuto lo hice con la versión 173.xx (tengo una FX 5500), aunque, que yo sepa, no cambió nada en este tema, voy a buscar un poco...

saludos

---

### Post by nemodot on 2009-09-15
Mmmm que raro, ahora parece funcionar luego de agregarle los modes, pero juraría haberlos establecido antes entre todas las combinaciones que hice.
Seguí la guia al pie de la letra y como aquello no funciono de principio volví a tener el xorg como estaba y probar distintas soluciones.

Gracias a todos y perdón por mi *gravísimo* lenguaje.

---

### Post by Sargento_Loco on 2010-01-03
Gracias, ya resolvi el problema...

---

### Post by rojojuan on 2010-06-03
Quiero agradecerte esta ayuda. Hoy pude solucionar la cuestión con:
sudo nvidia-xconfig
Espectacular!!!!
Saludos



[QUOTE=staar;7431006]Bueno, visto que es un problema bastante común y que se abren muchos threads al respecto, me decidí a hacer este how-to de como solucionarlo.

---

### Post by tbsisl on 2010-06-24
muy, pero que muy bueno. muchas gracias de verda

  	 	 	 	 	 	  Mantenimiento Informático Madrid
 

 [http://www.tecnobyteinformatica.com/](http://www.tecnobyteinformatica.com/)

---

### Post by heberrojo on 2010-06-27
Gracias Staar! con tu ayuda pude solucionar el problema de la resolución en mi vieja Geforce II MX 400. Toqué los modes en el xorg.conf y la tasa de refresco en la aplicación de Nvidia. Ahora estoy usando 1024x768 a 60hz mi monitor es un Biswal 15' muy viejito. Resumiendo: con hardware "obsoleto" el Lucid Linx con los efectos visuales a pleno funciona de maravillas.
Muchas gracias

---

### Post by marcelo_bur on 2010-07-20
Hola. Estaba por abrir un tema, pero viendo que aqui se trata más o menos de lo mismo que quiero preguntar creo que es mejor usar este tema.
Vamos al grano... yo tengo una pc de escritorio cuya mother tiene una tarjeta de vidie Nvidia. Hasta hace poco estuve usando Ubuntu 8.04 y un monitor viejo de 15 pulgadas sin ningún problema. Luego migré a Ubuntu 10.04, tambien sin problemas salvo que el monitor parpadeaba bastante en una esquina (ya lo hacia, aunque menos, con el 8.04). Como ya tenía decidido cambiar el monitor compré un Samsung de 22 pulgadas. El SO operativo lo reconoció sin problemas y abrió la sesión con la resolución adecuada 1920x1080 a 60 Hz. Sin embargo la pantalla se me puso muy lenta, algo no está bien. Leí que podía ser un problemas de drivers e instalé el propietario de Nvidia, lo cual no mejoró para nada la situación, por el contrario, sin este driver consigo que la pc funcione mejor bajando la resolución, con el de Nvidia la bajaba y al encender de nuevo la maquina volvia a 1920x1080 automáticamente. Lo quité y estoy usando una resolucion menor, 1440x900 a 60 Hz (si bien no es la adecuada ya que este monitor es para una relacion 16:9 y esta es 16:10) con lo cual anda bastante bien, pero no del todo bien. Me han sugerido que agregue  una tarjeta de video y le he encargado a un técnico al que considero bueno que me averigue sobre la mejor opción para esta máquina y este sistema operativo. Pero se me ocurrio que aquí hay gente que sabe mucho de todo esto y quizás me pueda decir si, primero, una nueva tarjeta puede solucionar el problema y, segundo, cual es a su criterio la más adecuada. 
No se que modelo de mother tengo, el procesador es un AMD Athlon (tm) 64x2 Dual Core Processor 5200+, al menos eso sale en el monitor de sistema, tengo una memoria de un giga que, descontado lo que consume la tarjeta de video integrada, me deja 875.5 MB de RAM.
Desde ya muchas gracias por cualquier consejo o idea que me puedan aportar.

---

### Post by guillermolisi on 2010-07-20
> **marcelo_bur said:**
> Hola. Estaba por abrir un tema, pero viendo que aqui se trata más o menos de lo mismo que quiero preguntar creo que es mejor usar este tema.

Movido a un [nuevo thread]("http://ubuntuforums.org/showthread.php?t=1535325") por tratarse de una consulta. Este thread, como dice su tag, es un Como para resolver problemas, a pesar de que se dejaron pasar algunas muy especificas, como los que mencionas o similares.

---

### Post by lopulus on 2010-09-14
Hola: Tengo unos problemas que supongo pueden estar relacionados. Uno es que cuando quise actualizar a lucid, luego de seleccionar en el menú, no aparecía la imagen habitual de Ubuntu, sino que iba cargando líneas hasta que en un momento se detenía en “verificando bateria2 (obvio en ingles). Y ahí quedaba. Decía algo como lo que figura aquí. 
Luego hice la prueba de entrar en una versión anterior y ahí si pude entrar, actualice el sistema después de mucho tiempo y cuando reinicie pude entrar a la ultima versión, salvo que nunca aparecia el logo de Ubuntu. Intente con algunos tutoriales de cómo arreglar Plymouth y logre que apareceiera el logo de Ubuntu pero luego me aparecia la pantalla en negro con algunas instrucciones seguido de una que decía “enabling laptop mode” y a continuación al me pedia nombre de usuario y contraseña.
por ahora no puedo brindar mas datos ya que no estoy en mi compu.
Si alguien puede ayudarme…
Gracias
__________________

---

### Post by narchy81 on 2011-01-28
¡Uf! No sabes el tiempo que llevo "intentando" hacer que mi archivo xorg.conf le asigne más resolución a la pantalla, ¡he probado lo habido y por haber! y nada. Sólo tu solución dió en el clavo. ¡Estupendo! ¡Mil y mil gracias!

Creo que en mi caso el principal problema venía de las velocidades de refresco Vertical y Horizontal (que las que tenía estaban completamente erradas) Me costó lo suyo encontrarlas porque es un CRT super viejo que compré de segunda hace un par de años. ¡De no poder pasar de 1152x864 ahora el NVIDIA X Server SEttings me da un listado larguísimo (de resoluciones rarísimas:grin:) que llega hasta 2048x1536! =D> Gracias hermano, esto va para información relevante e hiperútil del año :)

---

### Post by o2bith on 2011-10-14
Gracias staar, muchas gracias de verdad! no sabes todo lo que hice y leí por la web para poder solucionar este tema. Nada funcionaba, solo podía tener la resolución que queria en mandriva.
Tu how-to me funciono sin problemas.

S.O. ubuntu 11.10
Monitor: Mitsubishi Diamond Pro 920
Tarjeta Nvidia: 8400 gs
Resolución: 1280 x 1024 a 85hz

Gracias de nuevo!!

---

### Post by pato497 on 2011-12-21
Muchas Gracias!!!...Problema solucionado. ;)

---

### Post by wildmanne39 on 2012-10-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

### Post by guillermolisi on 2012-10-21
> **Wild Man said:**
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thank you Wild Man for your kindly attention.

The post [was moved to a new thread]("http://ubuntuforums.org/showthread.php?t=2074521")

By the way, como es el subforo del Argentina LoCo Team, acostumbramos a usar Español para facilitar la comunicacion con quienes interactuan ;)

Si el interesado inicia la conversacion en Español, continua todo en Español. Si lo hace en Ingles (porque no sabe Español) alguien podra responderle en Ingles.

Best Regards

---


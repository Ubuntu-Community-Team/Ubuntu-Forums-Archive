---
title: "Problem with my laptop..."
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by fdamay on 2005-12-27
Hello,
First sorry for the errors but I don't speak English very well, I'm French

I have a Compaq Armada M300 and i have a resolution problem with my screen. In fact there is a shift upward of my desktop. I don't know why and I don't know solve this problem alone... Somebody can help me ?

I have a other question : What can I do to connect a bigger screen on my laptop ( with alt F4 I have no results... )

---

### Post by tcrom2 on 2005-12-27
You might try resetting the res to something arond 6x8 first. Sounds like the LCD doesn't handle the res that you have set.

---

### Post by fdamay on 2005-12-27
In 640*480 it's OK... But it's a bigger resolution to work on my laptop...

In a french Forum a man have sais that..


> Je me suis décidé à installer Ubuntu sur mon ancestrale portable Armada M300 de chez compaq, toute la procédure c'est déroulée sans aucun accros. Premier démarrage tout est ok le serveu x démarre puis utilisateur mot de pass gnome arrive et la horreur l'écran est décalé de 5 mm vers le haut, sachant que la résolution de l'écran est de 800x600 la barre du menu démarrer il en manque un sérieux bout.

Après avoir gratté mes cheveux la seule solution que j'ai trouvé pour palier au probleme c'est en modifiant le fichier du serveur X et de remplacer le driver ati par vesa et tout est rentré dans l'ordre plus de probleme d'affichage.

Si quelqu'un a une idée elle est la bienvenue.

He has the identical problem of me and he have resolve that.. But I don't understand what the solution...

Have you an idee ?

---

### Post by Quirky on 2005-12-28
The suggestion there is to replace the ati driver for vesa (I think, I can't speak French and just guessed). You need to change the driver in the X config files: type *sudo gedit /etc/X11/xorg.conf* Find the section that says  **Driver "ati"** and change it to **Driver "vesa"**. Then restart X. For example by typing *sudo /etc/init.d/gdm restart*

---

### Post by fdamay on 2005-12-28
Tank you very much...
The problem is killed...


Just a question .. My screen is optimized for 800*600.. Is it possible to go to 1024*768 ?

---

### Post by Sef on 2006-01-06
You might be able to go to 1024x768.  If in Ubuntu, do this:  System -----> Preferences ----->Screen Resolution (Ecran Resolution.)   If you can do that, it will show up.  Some older laptops, you can't get that setting.

---

### Post by paulhurleyuk on 2007-06-30
I also have a Armada M300 running Feisty 7.04.  I use the ati driver and the LCD panel runs upto 1024x768

here's my xorg.conf

```


Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        load    "synaptics"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection
#new mouse section for trackpad - from guide at http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/3
Section "InputDevice"
Driver "synaptics"
Identifier "touchpad"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
#Option "LeftEdge" "1700"
#Option "RightEdge" "5300"
#Option "TopEdge" "1700"
#Option "BottomEdge" "4200"
#Option "FingerLow" "25"
#Option "FingerHigh" "30"
Option "MaxTapTime" "180"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.09"
Option "MaxSpeed" "0.18"
Option "AccelFactor" "0.015"
Option "SHMConfig" "on"
#always usefull
Option "Emulate3Buttons" "on"
EndSection

#old mouse section - maybe this should be left for the ps/2 port ??
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "stylus"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "stylus"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "eraser"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "eraser"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#EndSection

#Section "InputDevice"
##      Driver          "wacom"
#       Identifier      "cursor"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "cursor"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#E#ndSection

Section "Device"
        Identifier      "ATI Technologies Inc 3D Rage LT Pro"
        Driver          "ati"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage LT Pro"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "touchpad"      "AlwaysCore"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Maybe this might help...

Paul.

---


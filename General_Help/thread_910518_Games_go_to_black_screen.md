---
title: "Games go to black screen"
date: 2008-09-04
forum: General Help
---

### Post by Flyingjester on 2008-09-04
Hello all,i have a problem, I Have a nvidia geforce 7100 video card with the driver from nvidia installed, whenever i go to play a game the screen goes to black, i can still back out of the game using esc to get to my desktop but i can't see anything, i have tried putting modes into my display subsection but to no avail, if  i use the nv driver i can play the games, but then compiz doesn't work for me, here are the contents of my xorg file 
> 
Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
    Load           "fbdevhw"
    Load           "record"
    Load           "freetype"
    Load           "type1"
## for nVidia driver
    Load           "glx"
    Load           "dbe"
    Load           "extmod"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

# keyboard added by rhpxl
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Daewoo L510B1"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 76.0
    Option         "dpms"
EndSection
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0; 1024x768 +0+0"
# Removed Option "metamodes" "800x600 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
   Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



thank you all for your help :)

---

### Post by Flyingjester on 2008-09-05
bumpity

---

### Post by Flyingjester on 2008-09-06
bumpity

---

### Post by Infinite Indefinite on 2008-09-06
Well, you might want to have two different login sessions - one with compiz and one for gaming.

Depending on what version of Ubuntu you're using, you might the following link useful:

[http://ubuntuforums.org/archive/index.php/t-581568.html](http://ubuntuforums.org/archive/index.php/t-581568.html)

It explains how to create a separate login without XGL and Compiz. I've found it very helpful.

---


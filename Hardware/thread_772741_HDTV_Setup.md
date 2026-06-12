---
title: "HDTV Setup"
date: 2008-04-28
forum: Hardware
---

### Post by s2welee on 2008-04-28
Not meaning to double post, but after posting this in ABT I thought that it would fit better here...

I am trying to get my hardy setup with my HdTV using vga. I cannot seem to get past 1024x768 even after edidting my xorg.conf to look like this.


Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "vesa"
Screen 0
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Hisense"
Modelname "LCD Panel 1360x768"
Horizsync 31.5-48.0
Vertrefresh 56.0 - 65.0
ModeLine "1366x768_60" 88.0 1366 1424 1704 1816 768 770 782 808
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1366x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "v4l"
EndSection
Section "ServerFlags"
EndSection 

Not sure what else to do. As far as I can tell, I have done this right, but I must be missing a step. Thanks,

---

### Post by s2welee on 2008-04-30
Anyone have any ideas?

---


---
title: "Acer AL1916W problem"
date: 2009-02-18
forum: Hardware
---

### Post by RAS7331 on 2009-02-18
I recently installed Ubuntu 8.10 and everything is great besides one thing. I get this annoying "Input not supported" message before i log in. After i log in my screen flickers black then it goes away. From what i have read searching google i need to change my xorg.conf file to accept the 1440:900 resulation but thats were my problem is.

Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:2:0:0"
Option "UseEDIDFreqs" "FALSE"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

The xorg.conf file doesnt seem to recognize the monitor at all and doesnt list any resolutions. My video card is ATI Sapphire X1650 and i installed the drivers from ATIs website.

---

### Post by RAS7331 on 2009-02-18
bump

---


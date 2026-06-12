---
title: "Problem with resolution in Xubuntu laptop"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by katon on 2007-11-11
i have several problems with my old laptop with XUBUNTU i can't change the resolution more than 800x600 and before this it had WInXP and the resolution was 1024x768

what can i do? i have ATI Technologies Inc Rage Mobility P/M AGP 2x at my laptop old one Ibm Celeron 500 thinkpad this is my xorg sections for displays Pp


Section "Device"
Identifier "ATI Technologies Inc Rage Mobility P/M AGP 2x"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Rage Mobility P/M AGP 2x"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

---


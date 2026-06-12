---
title: "Dual monitor"
date: 2009-03-11
forum: Hardware
---

### Post by natacho on 2009-03-11
I just got a LCD for my laptop, I'm using the property drivers from ATI. It is working ok with my ubuntu but i have a couple of problems. I'm using the property drivers from ATI
1) When i maximize a window it maximizes over the two monitors. If i want to take only one i have to do it manually.
2)When i open i video on vlc and i choose full screen it use the 2 screens, i would like to use the big lcd for the video and have the laptop screen free to keep working.

Thanks a lot for the help!.

---

### Post by Beefeater on 2009-03-18
For a Nvidia card I know that you can use absolute positioning to make that work. Dunno if something similar exists for ATI.

Your option would be to run two different X sessions on the monitors. Be aware that you can't move windows between the monitors.

You would do something like this in your xorg.conf :

```
Section "Monitor"
Identifier "Laptop Monitor"
Option "DPMS" "true"
EndSection

Section "Monitor"
Identifier "LCD Monitor"
Option "DPMS" "true"
EndSection

Section "Screen"
Identifier "LAP"
Device "Laptop"
Monitor "Laptop Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1680x1050"
EndSubSection
EndSection

Section "Screen"
Identifier "LCD"
Device "VGA"
Monitor "LCD Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1200"
EndSubSection
EndSection

Section "Module"
Load "glx"
EndSection


Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "LAP" 0 0
Screen 1 "LCD" LeftOf "LAP"
EndSection

Section "Device"
Identifier "Laptop"
BusID "PCI:1:0:0"
Screen 0
Driver "fglrx"
EndSection

Section "Device"
Identifier "VGA"
BusID "PCI:1:0:0"
Screen 1
Driver "fglrx"
EndSection
```

---


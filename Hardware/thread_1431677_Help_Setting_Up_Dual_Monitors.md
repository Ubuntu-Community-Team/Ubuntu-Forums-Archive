---
title: "Help Setting Up Dual Monitors"
date: 2010-03-16
forum: Hardware
---

### Post by Famicube64 on 2010-03-16
So I've got this old Dell E196FP and I wanted a bit more space for coding. My video card only has a VGA and DVI, so I picked up a VGA to DVI adapter for an old Viewsonic LCD (Native VGA is used by the E196FP). How do I set it up for dual monitors? My xorg.conf is below. I'm not using FGLRX or Compiz, if it matters.

```
Section "Device"
        Identifier      "Radeon 9600 PRO"
        Driver          "ati"
        Option          "BusID"             "PCI:1:0:0"
        Option          "BusType"           "PCI"
        Option          "AGPMode"           "8"
        Option          "RenderAccel"       "1"
        Option          "AccelMethod"       "EXA"
        Option          "AGPFastWrite"      "1"
        Option          "ColorTiling"       "1"
        Option          "EnablePageFlip"    "1"
        Option          "DRI"               "1"
EndSection

Section "Monitor"
        Identifier      "Dell E196FP"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Radeon 9600 PRO"
        Monitor         "Dell E196FP"
        DefaultDepth    24
        SubSection "Display"
                   Depth                    24
                   Modes                    "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection     

Section "DRI"
        Mode            0666
EndSection

Section "Extensions"
        Option          "Composite"         "1"
EndSection
```

---

### Post by lyall on 2010-03-16
see Twin View [https://help.ubuntu.com/community/XineramaHowTo]("https://help.ubuntu.com/community/XineramaHowTo")

scroll down to ATI and read the info there

help this helps

good luck and have fun learning

---

### Post by Famicube64 on 2010-03-16
The site you posted says I should have the ATi binary drivers. I'm using the open source driver, not FGLRX. Will it still work?

---

### Post by Famicube64 on 2010-03-17
Bump.

---


---
title: "ATI HD 4850 Not accelerated when KDE window effects enabled"
date: 2009-04-28
forum: Hardware
---

### Post by elapouya on 2009-04-28
Hello,

I have a brand new Dell Studio Intel i7 + Radeon HD 4850
which runs on Kubuntu 9.04 + ATI CATALYST drivers 9.4

I have the following problem:

If I use the following xorg.conf:

```
 Section "ServerLayout"
         Identifier "aticonfig Layout"
         Screen 0 "aticonfig-Screen [0] -0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
         Option "DontZap" "True"
EndSection

Section "Monitor"
         Identifier "aticonfig-Monitor [0] -0"
         Option "VendorName" "ATI Proprietary Driver"
         Option "ModelName" "Generic Monitor Autodetecting"
         Option "DPMS" "true"
EndSection

Section "Device"
         Identifier "aticonfig-Device [0] -0"
         Driver "fglrx"
         Option "VideoOverlay" "on"
         Option "OpenGLOverlay" "off"
         BusID "PCI: 5:0:0"
EndSection

Section "Screen"
         Identifier "aticonfig-Screen [0] -0"
         Device "aticonfig-Device [0] -0"
         Monitor "aticonfig-Monitor [0] -0"
         DefaultDepth 24
         SubSection "Display"
                 ViewPort 0 0
                 Depth 24
         EndSubSection
EndSection
Section "Extensions"
         Option "Composite" "1"
EndSection 
```

The KDE window effects are enabled, but I have no hardware acceleration:
glxgears gives me 400 FPS and resizing a window is deadly slow.

But, if I turn off the composite mode (Option "Composite" "0" in xorg.conf)
I have no problem of slowness (glxgears running at 11000FPS ie 25 times faster!)
Unfortunately, KDE window effects are then disabled.

Question: How do I get both ATI accelerated and KDE window effects enabled at the same time?

---


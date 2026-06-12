---
title: "Xpress 1150 i ~160 fps with glxgears"
date: 2009-05-03
forum: Hardware
---

### Post by mrover on 2009-05-03
Hi,

I've just installed Catalyst 9.3 X300 (Xpress 1150) but i doesn't seem work properly.
Results of fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series      
OpenGL version string: 2.1.8543 Release
```glxgears:
```

811 frames in 5.0 seconds = 161.719 FPS
809 frames in 5.0 seconds = 161.160 FPS
838 frames in 5.0 seconds = 167.588 FPS
779 frames in 5.0 seconds = 155.562 FPS
811 frames in 5.0 seconds = 161.509 FPS
792 frames in 5.0 seconds = 157.463 FPS 
```fgl_glxgears:
```
173 frames in 5.0 seconds = 34.600 FPS
183 frames in 5.0 seconds = 36.600 FPS
198 frames in 5.0 seconds = 39.600 FPS
197 frames in 5.0 seconds = 39.400 FPS
191 frames in 5.0 seconds = 38.200 FPS
```xorg.conf:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

I have no idea what is wrong. On another (identical) laptop without fglrx glxgears gives results about 700 fps.

---


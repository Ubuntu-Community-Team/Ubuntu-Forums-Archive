---
title: "Help with HDMI and xrandr - a bit overwhelmed"
date: 2009-04-15
forum: Hardware
---

### Post by Vexed Arcanist on 2009-04-15
I simply want my LCD to display in 1920x1080 and mirrored (displays the same as the laptop monitor), however currently I have nothing showing on it.   I feel a bit overwhelmed trying to resolve this, Ubuntu 9.04 simply worked pretty well after adding the proprietary ATI driver and messing with Ubuntu's display preferences a tad.  Here is the relevant info, if there is anything I forgot to include let me know.

**Output of xrandr:**

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1366 x 1366
LCD connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.1*+
   1280x768       60.1  
   1280x720       60.1  
   1024x768       60.1  
   800x600        60.1  
   720x480        60.1  
   640x480        60.1  
   640x400        60.1  
   512x384        60.1  
   400x300        60.1  
   320x240        60.1  
   320x200        60.1  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
```

**Output of fglrxinfo:**

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 2.1.8575
```

**xorg.conf:**


```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection
```

---


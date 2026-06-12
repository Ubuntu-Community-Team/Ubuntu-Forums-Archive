---
title: "800x600 maximum resolution on nVidia GeForce 4200"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by conz on 2007-06-18
Howdy all, 

I tried a form of this on another post, but perhaps used too cryptic a title, thus this reposte:

I've a Acer 77c monitor on an nVidia GeForce4 Ti 4200 card. The default legacy nvidia driver suggested by Ubuntu 7.04 was installed. However, all I get for resolution options are 800x600. Prior to installing the proprietary nvidia driver, xorg happily supported 1024x768.

I suspect that there's a problem that may need Modeline config to resolve, but this is outside my area of expertise. I've had a go at forcing a higher resolution, but editing xorg.conf, specifically the section below. I've also forced the hSync and vRefresh rates to the max, still no luck.

Any assistance or pointers appreciated. This is one of the kids' PCs, and they've gotten hooked on SuperTuxKart, thus don't want to go back to non-accelerated modes. 

/etc/xorg.conf follows:


Section "Device"
Identifier "nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Driver "nvidia"
Busid "PCI:1:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
EndSection

Section "Monitor"
Identifier "Acer 77c"
Option "DPMS"
HorizSync 72
VertRefresh 120
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Monitor "Acer 77c"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

---


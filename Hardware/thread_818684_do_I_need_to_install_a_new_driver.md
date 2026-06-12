---
title: "do I need to install a new driver?"
date: 2008-06-04
forum: Hardware
---

### Post by SteveNorman on 2008-06-04
I just upgraded from an nvidea 6600 to an 8800 series vid card. I seems to be working fine,,but I dont know if I need to upgrade my driver,,or if that happens automatically? From my xorg.conf:

```
from Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
EndSection

Section "Screen"
        #ending fa mod
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
  #begining fa mod May 27 2008
        Viewport    0 0
        Depth       24
        Modes      "1600x1200" "1600x1024" "1440x900" "1400x1050" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x720" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Nvidea settings sees the card,,shown in th thumbnails.
Do I just manually edit xorg.conf? or do I need to download and install a new driver?

Thank you

---

### Post by cudaman73 on 2008-06-04
You should be fine. I don't see any reason to upgrade unless it's causing you problems.

---

### Post by SteveNorman on 2008-06-04
thanks,,I just want to give myself a seizure with amazing graphics!

---


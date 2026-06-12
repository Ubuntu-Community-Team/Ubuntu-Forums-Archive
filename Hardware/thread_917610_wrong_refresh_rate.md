---
title: "wrong refresh rate"
date: 2008-09-12
forum: Hardware
---

### Post by fallen seraph on 2008-09-12
Whenever I start gnome the refresh rate on my monitor seems to be set back to 50 hz, despite the fact that this isn't even provided for in my xorg.conf (as far as I can tell)

This is quite frustrating, is there any solution?


Also, this is the display section of my xorg.conf, as I presume it's relevant.

> Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
EndSection


---

### Post by frklin on 2008-09-12
```
sudo apt-get install nvidia-settings
```
```
sudo nvidia-settings
```

---

### Post by fallen seraph on 2008-09-12
aye, I've tried that, and sometimes it'll change it for the session, and other times it certainly feels like it's changed the refresh rate but gnome still says 50 hz. either way it's definately back to 50hz after I've restarted if I try it that way.

---

### Post by regeya on 2008-11-09
> **fallen seraph said:**
> aye, I've tried that, and sometimes it'll change it for the session, and other times it certainly feels like it's changed the refresh rate but gnome still says 50 hz. either way it's definately back to 50hz after I've restarted if I try it that way.

Same here, and it's annoying.  iirc I had the resolution pop up way too low, and made the mistake of changing 'em in the GNOME Monitor Resolution Settings box.  Now, even though I've edited xorg.conf and GDM is running at 1152x864@75Hz, as soon as I log in it's dropped back down to 50Hz(!) 

Where is that setting stored?   I cannot find it in gconf, and wasn't able to find it in .gnome2.

For my little desktop-war jab of the evening, KDE keeps everything in human-readable files in .kde. :p

---


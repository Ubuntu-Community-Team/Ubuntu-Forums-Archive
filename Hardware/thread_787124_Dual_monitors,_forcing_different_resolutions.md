---
title: "Dual monitors, forcing different resolutions"
date: 2008-05-08
forum: Hardware
---

### Post by Datana on 2008-05-08
I have a dual-head setup on an nVidia 8800GTS, with driver install on Hardy AMD64 using EnvyNG followed by configuration via nvidia-settings.  The primary monitor is a Dell 2005FPW (20" widescreen, 1680x1050), and to the left of it is a Sceptre X9N Naga-IV (19" 4:3, 1280x1024).  For the life of me, I can't get the Sceptre recognized at the proper resolution at all.  The Dell is detected properly, but the Sceptre is invariably reported as a 640x480@60 monitor when connected via a VGA dongle, and isn't detected at all via DVI.  It doesn't appear to be a monitor issue, as it works normally under Windows XP (where a DVI connection is used).

I attempted to force the correct resolution via adjusting the metamode in xorg.conf, but this only resulted in the Sceptre displaying nothing at all (and forcing a trip to the console after shutting down X completely).  For now, I've disabled that monitor entirely, but I would like to be able to get both monitors going.  Does anyone know what might be going on here?

---

### Post by chewearn on 2008-05-09
Find out the horizontal frequencies and vertical refresh rates of the monitor.  Open xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```Under Section "Monitor", add the correct values to the HorizSync and VertRefresh.

E.g. here is a typical Section "Monitor" from my HDTV:
```

Section "Monitor"
    VendorName    "Unknown"
    ModelName     "LPL"
    HorizSync      30.0 - 75.0
    VertRefresh    60.0
EndSection

```.

---

### Post by Datana on 2008-05-17
I've managed to solve this myself.  I had to manually add modelines to xorg.conf, as follows:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       24.0 - 80.0
    VertRefresh     50.0 - 75.0
    Modeline "640x480@60" 24.11 640 672 760 792 480 490 495 505
    Modeline "800x600@60" 38.21 800 832 976 1008 600 612 618 631
    Modeline "1280x960@60" 105.68 1280 1312 1712 1744 960 979 989 1009
    Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
EndSection
```

Strangely, HorizSync and VertRefresh were already correctly detected, even though something was preventing my monitor from reporting EDID data properly.  At this point, it was just tweaking metamodes around and it started working properly.

I still can't get the monitor detected at all in DVI, but this is quite usable in CRT mode.

---


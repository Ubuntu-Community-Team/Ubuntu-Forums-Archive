---
title: "The old story: Mach64 and ATI Rage Mobility"
date: 2011-02-20
forum: Hardware
---

### Post by Mr. Pinky on 2011-02-20
Hej there! I'm a German XUbuntu User, using version 10.10 on an old laptop. Everything runs just fine but not the "/($"/(QQ@3249 mach64. As you see this problem is just maddening my to hell. I spend days of work but no success, so hoppefully there is someone here who can show my the way to the world in 3d ;).

glxgears shows me 67fps. This is, what *grep -i MACH64 /var/log/Xorg.0.log* returns me:
```
(...)
[    29.818] (II) MACH64(0): [drm] SAREA 2200+1208: 3408
[    29.869] [drm] failed to load kernel module "mach64"
[    29.869] (EE) MACH64(0): [dri] DRIScreenInit Failed
[    29.869] (II) MACH64(0): Largest offscreen areas (with overlaps):
[    29.869] (II) MACH64(0): 	1024 x 1279 rectangle at 0,768
[    29.869] (II) MACH64(0): 	768 x 1280 rectangle at 0,768
[    29.870] (II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
(...)
[    29.873] (II) MACH64(0): Direct rendering disabled

```

As you can see, mach64 fails to load. In the internet there are millions of threads to this topic but I couldn't find any suitable solution (I already tried in 16 Bit mode, no chance..). I'm also really disappointed that this problem concerning this driver isn't solved until now :(.

My Xorg config file looks like this:
```
Section "Device"
        Identifier      "Device[0]"
        Card    "ATI Rage Mobility P/M AGP 2x (rev 64)"
        Driver  "ati"
        Option  "DmaType"       "AGP"
        Option  "BusType"       "AGP"
        Option  "ForcePCIMode"  "false"
        Option  "AgpMode"       "2"
        Option  "AgpSize"       "16"
        Option  "BufferSize"    "2"
        Option  "LocalTextures" "true"
        Option  "AccelMethod"   "XAA"
        Option  "EnablePageFlip" "true"
        Option  "HWCursor"      "true"
        Option  "UseInternalAGPGART" "yes"
        Option  "AGPFastWrite"  "true"
        Option  "backingstore" "true"
EndSection

Section "Module"
        Load    "glx"
        Load    "dri"
EndSection

Section "Screen"
        Identifier      "Screen[0]"
        Device          "Device[0]"
        Monitor         "Monitor[0]"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection

Section "DRI"
       Mode 0666 #allows anybody to use DRI
EndSection

```


I'm so hoping now, that someone can help me :popcorn:

---

### Post by TinkererNE on 2011-03-04
Try this link and it's redirects, most all solutions involve recompiling the driver.  It seems that it (direct rendering) isn't included because of some old problem with security when DRI is enabled.  Hope this leads you in the right direction.

[http://ubuntuforums.org/showthread.php?t=1516414&highlight=mach64](http://ubuntuforums.org/showthread.php?t=1516414&highlight=mach64)

---


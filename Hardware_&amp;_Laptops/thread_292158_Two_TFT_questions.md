---
title: "Two TFT questions"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by ehird on 2006-11-03
OK, got my new TFT today and I love it! Just a few questions for you folks:

1. Ubuntu wiki says to put the refresh rate at the lowest. Surely it should be the highest?
2. Using subpixel antialiasing, I can sometimes make out the blue and red tints. Shouldn't this be gone on a TFT, is it a wrong configuration setting?
3. The orange headers on this forum is light gray. :confused: Any ideas?

---

### Post by ehird on 2006-11-03
[Bump]

---

### Post by ehird on 2006-11-04
[Badump]

---

### Post by ehird on 2006-11-04
[kabadadabump]

---

### Post by dbott67 on 2006-11-04
Cna you post the make & model of your screen, as well as the output of your /etc/X11/xorg.conf file:
```
cat /etc/X11/xorg.conf
```

BTW, my Dell 2007 FP has a refresh rate of 60 Hz.

```
Section "Monitor"
    Identifier     "DELL 2007FP"
    **[COLOR="Red"]VertRefresh     60.0 - 60.0[/COLOR]**
    Option         "DPMS"
#       HorizSync       60
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
        Option          "RenderAccel"           "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "DELL 2007FP"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by ehird on 2006-11-04
Mine can do multiple refresh rates though. And my monitor is really irrelivent to this but, Samsung SyncMaster 640BF.

---

### Post by FrankVdb on 2006-11-04
TFT screens need lower refresh rates than CRT's because they operate differently. TFT screens can get damaged when the refresh rate is higher than what is recommended by the manufacturer. TFT's don't flicker like CRT's because they work with crystals and not with electron beams, which cause a screen to flicker when they are not projected fast enough.

---


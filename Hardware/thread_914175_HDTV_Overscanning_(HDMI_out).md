---
title: "HDTV Overscanning (HDMI out)"
date: 2008-09-08
forum: Hardware
---

### Post by Lord C on 2008-09-08
I've browsed so many posts and blogs, but I can't find any working solutions.

First of, my setup:
I have a nVidia GeForce 9800GX2.
A 22inch widescreen in DVI slot 1, and regular 19inch in DVI slot 2, and a 37inch TV in the HDMI out.

Now, the problem;
The monitors display their native resolutions perfectly. I had to re-order the screens, but that's the only thing I've touched in xorg.conf - everything else I did with nvidia-settings-manager.

My HDTV shows the correct image, but it is off-centre by quite a bit. There's a black bar on the left, and the screen disapears off to the right.

I tried using xvidtune, which would have been nice - but anytime I try to 'Test' a confiuration, I am greeted with the error:
[IMG]http://i34.tinypic.com/s1kr5s.png[/IMG]

I tried adding
```
       Mode    "1366x768"      # vfreq 59.815Hz, hfreq 47.553kHz
               DotClock        85.500000
               HTimings        1366 1494 1624 1798
               VTimings        768 770 776 795
               Flags           "-HSync" "+VSync"
       EndMode
```
To the screen, and 
```
       Option          "AddARGBVisuals"                "True"
       Option          "AddARGBGLXVisuals"             "True"
       Option          "NoLogo"                "True"
       Option "ModeValidation" "NoWidthAlignmentCheck"  # Important!!! need this option to use nvidia card at 1366 x 768

```
To monitor.
Both from [http://www.mythtv.org/wiki/index.php/Vizio_VX37L](http://www.mythtv.org/wiki/index.php/Vizio_VX37L)
Problem is, this isn't my TV, and I can't find anythhing specific for my TV.

I've also tried adding Option "TVOverScan" with everything from 1.0 to 0.0, with no success.

If anyone could shed any light on this for me, I would really appreciate it.

Here's my xorg.conf;
```

#----------------Monitors----------------#
################# Video7 ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "CMO CMC 22 W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

#################  HDTV  ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSP YT08H"
    HorizSync       28.1 - 64.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

#################  Dell  ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1908FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

#----------------Devices-----------------#
################# Video7 ################# 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

#################  HDTV  ################# 
Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

#################  Dell  ################# 
Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:5:0:0"
EndSection

#----------------Screens-----------------#
################# Video7 ################# 
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

#################  HDTV  ################# 
Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

#################  Dell  ################# 
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard2"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Lord C on 2008-09-10
Shameless Bump

---

### Post by Lord C on 2008-09-16
Someome must be familiar with overscanning, or at least xvidtune?

---

### Post by Lord C on 2008-09-19
Really need help with this one.

---


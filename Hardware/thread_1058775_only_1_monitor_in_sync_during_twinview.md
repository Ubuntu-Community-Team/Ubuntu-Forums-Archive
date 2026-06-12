---
title: "only 1 monitor in sync during twinview"
date: 2009-02-03
forum: Hardware
---

### Post by Tiftof on 2009-02-03
Hi,

I recently started using a second screen and set up a twinview setup using ubuntu intrepid (currently using driver version 180.27). Everything works great except that my primary monitor is not in sync: when I move windows around or a movie is playing, a horizontal stripe is slowly moving downwards across my screen. This happens on my lcd (dell 2007wfp) that is connected via dvi to my nvidia 7600gs (DFP-0).

My second monitor (CRT-1) is also an lcd but has a vga connection and is connected to that same nvidia 7600gs using a dvi-to-vga connector. On that monitor, everything seems smooth without any issues.

I've been reading a lot and also tried a lot. I read that I can only sync to 1 monitor when using twinview, but is there a way to choose which one to have in sync? I'd like to have my lcd connected via dvi to be in sync.

my xorg.conf:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    ModeLine	   "1680x1050_60" 119.0 1680 1728 1760 1840 1050 1053 1059 1080 -HSync +VSync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
    Option         "RenderAccel"    "true"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0,CRT-1"
    Option         "metamodes" "DFP-0: 1680x1050_60 +0+0, CRT-1: nvidia-auto-select +1680+150; DFP-0: nvidia-auto-select +0+0"
    Option "HorizSync"   "DFP-0: 30-81; CRT-1: 31-83"
    Option "VertRefresh" "DFP-0: 56-76; CRT-1: 60"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
    Option         "AddARGBGLXVisuals" "True"
EndSection
```

---

### Post by alexfpms on 2011-02-21
I'd like to know if someone found any solution for this ?

---

### Post by PizzAp on 2011-04-04
As far as I know you can sync to one of your monitors in twinview.

Take a look at nvidia-settings, you should be able to set your primary monitor under "X Server XVideo Settings"->"Sync to this display device".

---


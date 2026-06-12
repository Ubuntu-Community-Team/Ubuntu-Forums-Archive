---
title: "NVDIA - Twinview Second Monitor Issues"
date: 2008-05-03
forum: Hardware
---

### Post by cprofitt on 2008-05-03
I was having issues with Twinview and my nvidia drivers due to the second screen being restricted to 640x480. From reading it was apparent that the issue is when the second monitor's refresh rate is not detected properly.

To solve the problem I ended up replacing the following sections of my xorg.conf:

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
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
    BoardName      "GeForce 8800 GTS"
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
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: **1280x1024_60** +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
The key appeared to be removing the second monitor that was auto-configured and forcing the size and refresh of the CRT.

The method I used to do this was to completely deleted my xorg.conf file (after making a backup) and then I used the nvidia-xconfig --twinview to generate a completely new xorg.conf. After that I made a copy of the Nvidia generated file, restored my original and replaced the sections you see above.

YMMV

---


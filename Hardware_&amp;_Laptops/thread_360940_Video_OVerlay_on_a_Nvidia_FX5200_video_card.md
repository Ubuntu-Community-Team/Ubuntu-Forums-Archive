---
title: "Video OVerlay on a Nvidia FX5200 video card"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by Riem2k on 2007-02-13
Hello i was wondering if anyone can help me with my nvidia FX5200 video card, i was able to set TV out and have the TV as a clone right now. In windows i was able to use video overlay, an option in which when i opened a video file the output could be shown full screen in my TV so i can continue working on my computer normally,, i would really appreciate if anyone knows how to set this feature on..  thanks  :guitar:

---

### Post by Riem2k on 2007-02-13
heres a copy of my current setting on my xorg.conf file *********************

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option         "NoLogo"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "true"
    Option         "TwinViewOrientation" "Clone"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVOverScan"	"0.6"
    Option         "TVStandard" "NTSC-M"
    Option         "SecondMonitorHorizSync" "30-50"
    Option         "SecondMonitorVertRefresh" "60"
    Option         "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---


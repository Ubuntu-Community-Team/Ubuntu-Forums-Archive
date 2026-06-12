---
title: "nvidia-settings: external projector stuck at 640x480"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by peterkirn on 2007-09-03
I'm trying to configure an external projector mirrored via the VGA connection on my Toshiba Satellite M35-S320 laptop, which has an NVIDIA GeForce FX GO5200 video card. All is working fine, except I can't get the external projector resolution beyond 640x480. nvidia-settings offers 320x240, 640x480, and "auto" as options. I've tried editing the xorg.conf file, as well, but that seems to have no impact on nvidia-settings. 

TwinView cloning (mirroring) is working just fine, as well, but stuck at the same resolution.

Is there a way to disable nvidia-settings and just use xorg.conf? Or to get nvidia-settings to recognize the xorg.conf settings? Or am I missing something?

Thanks,
Peter Kirn
[http://createdigitalmotion.com](http://createdigitalmotion.com)

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
Option "TwinViewOrientation" "Clone"
    Option         "MetaModes" "1280x800, 1280x800; 1024x768, 1024x768; 800x600, 800x600; 640x480, 640x480"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "640x480"
    EndSubSection
EndSection
```

---

### Post by pikmaster on 2008-01-02
It is because X server does not detect the second display at the start or the display does not provide correct EDID information at the start / detection moment. So it falls back to a safe resolution of 640x480. If you restart X server, the display will be detected but it may affect the order the screens are displayed (usually external displays are initialized first, which may not be what you want). Also, restarting X is not always convenient, especially, when you have some applications opened.

To work around the fact the  X server does not detect the second display at the start is to force him to think the second display IS there. This section in /etc/X11/xorg.conf works for me:

[FONT="Fixedsys"]Section "Device"
Identifier "Videocard0"
Driver "nvidia"
[B]Option "ConnectedMonitor" "DFP-0,CRT-0"
Option "UseDisplayDevice" "DFP-0,CRT-0"[/B]
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
Option "MonitorLayout" "LFP,LFP+CRT"
Option "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
EndSection[/FONT]

See also this post for a complete xorg.conf file
[http://ubuntuforums.org/showthread.php?p=4024050#post4024050](http://ubuntuforums.org/showthread.php?p=4024050#post4024050)

---


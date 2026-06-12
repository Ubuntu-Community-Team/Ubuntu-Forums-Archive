---
title: "Laptop,nvidia,dell-monitor,xorg.conf funnyness"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by AndersRiggelsen on 2007-11-11
Hello there.
I have a T61 Lenovo Thinkpad with a nvidia graphics card and everything goes smoothly.
That is... until I want to plug in my external dell monitor.

For that to work I am told I have to use 'nvidia-settings' to set it up. And it works - kinda.
After I apply i have it fully working, but then after the next restart chances are that Xorg will refuse to respond and use 100% CPU. Only thing that works when that happens is REISUB because Ctrl+Alt+Backspace doesn't in that case.

I have found out what nvidia-settings adds to my xorg.conf file and here it is:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 140M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0; CRT: nvidia-auto-select +0+0, DFP: 1440x900@60 +0+0"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

```
//Only the option inside ServerFlags is new, ServerFlags was just empty before.

Some of theese changes just messes up my system. Can you spot it because I am unable to :'-(

Specs:
Core 2 Duo (64bit)
1GB RAM
nVidia Quadro NVS 140M

If you want me to post the full xorg.conf just ask.

---


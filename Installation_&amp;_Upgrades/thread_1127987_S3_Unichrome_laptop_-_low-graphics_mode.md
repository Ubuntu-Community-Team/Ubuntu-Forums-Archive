---
title: "S3 Unichrome laptop - low-graphics mode"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by jaygo on 2009-04-17
Hi all,
I've got an older Gateway laptop with an S3 unichrome pro integrated video card. Running Ubuntu 8.10.

With default settings, it boots fine but uses 1600x1200 resolution. The monitor only does 1280x768 and so a lot of the screen is cut off. I've been trying to use my old xorg.conf which worked perfectly under 8.04 xubuntu however anytime I use it, ubuntu chokes on the video after a number of tries and outputs the error "Ubuntu is running in low-graphics mode".

I've tried trimming my custom xorg.conf down to the barebones but I haven't found a middle ground that let's me use the correct video res - 1280x768 - and actually boot. What *I am able* to do is kill x, switch to a tty, login, and startx from there (using my custom xorg) and everything works peachy.

Any help is appreciated.

current, barebones xorg.conf:
```

Section "device"
    Identifier    "onboard vesa"
    Boardname    "S3 Unichrome Pro"
    Busid        "PCI:1:0:0"
    Driver        "vesa"
#    Screen    1
EndSection

Section "monitor" 
    Identifier    "laptop"
    Vendorname    "Gateway"
    Modelname    "WXGA LCD Panel 1280x768"
    Horizsync    31.5-50.0
    Vertrefresh    56.0-61.0
#    modeline grabbed from cvt command:
#    Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
#    default modeline copied from failsafe (working) monitor:
      modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "screen" 
    Identifier    "native vesa"
    Device        "onboard vesa"
    Defaultdepth    24
    Monitor        "laptop"
    SubSection "Display"
        Depth    24
        Modes    "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by epetersons on 2009-12-29
Thank you for this new script.  I have been battling this screen resolution issue for a long time - going back and forth with many people on another thread.  I had given up and returned to Windows (dread).  But just recently, someone emailed me with your post.  It has worked perfectly.

Many sincere thanks.
Erik

---


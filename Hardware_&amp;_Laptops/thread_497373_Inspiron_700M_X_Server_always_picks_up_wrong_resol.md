---
title: "Inspiron 700M: X Server always picks up wrong resolution on startup"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by shayborg on 2007-07-10
Hey,

I just installed Ubuntu for the first time tonight and noticed that the resolution defaulted to 1024x768 instead of the native 1280x800.  Luckily I found lots of very helpful instructions here and on the Web as to how to set up the 915resolution tool and other stuff to get it working properly.  (That said, it wouldn't have been easy for, say, my grandmother...)

Unfortunately, the settings don't seem to take effect immediately.  Every time I restart, the resolution returns to 1024x768, but restarting X a single time (using Ctrl-Alt-Backspace) fixes the problem.  

The relevant sections of my xorg.conf look like this (I mucked with them a bit following various sets of directions I found on the Web, but nothing helped):

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline        "1280x800" 83.46 1280 1344 1480 1680 800 801 804 848 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600"
                ViewPort        0 0
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600"
                ViewPort        0 0
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600"
                ViewPort        0 0
        EndSubSection
EndSection
```

I'd appreciate any tips.

Thanks,

Shayon

---


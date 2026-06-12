---
title: "Increasing Gnome desktop size"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by hakgun on 2007-12-20
I have Ubuntu 7.10 installed on my Lenovo T42 laptop that has an ATI Radeon video card. The LCD resolution is 1024x768, on which I spend about half my time happily; the other half, I have the system docked and, through the DVI port, connected to an LCD monitor with 1600x1200 resolution.

Now, when I operate in that configuration, the display works all right; however, Gnome desktop covers only the upper left 1024x768 pixels of the entire screen; i.e., both the upper and lower bars stretch only 1024 pixels, and the lower bar is practically in the middle of the screen and on top of other windows...

How do I configure Gnome to use 1600x1200 for the desktop size? I don't see anything higher than 1024x768 in settings.

Thank you,

---

### Post by ttran on 2008-02-11
Hi,

I have the same problem: T42 with Ubuntu 7.10.

However, my Gnome desktop is stuck at 640x480 instead of 1024x768. 
So on a 1024x768 display,
the Gnome bars stopped 2/3 of the way from the left, and 2/3 of the way down.

I changed the xorg.conf to the lines below with no effect. Did I miss something?

How/where does Gnome get the configuration for its display?
I'm a newbie in X/Gnome so any help is appreciated?

Thanks
ttran

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

---


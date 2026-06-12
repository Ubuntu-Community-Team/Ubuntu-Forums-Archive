---
title: "jaunty display not recognized"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Bulli2010 on 2009-05-09
Hi,
installing Jaunty i cannot get a higher resolution then 800x600.

Display is: Medion MD 9760AI Type M150P1
Expected resuolution: 1024x768 at 60 Hz

As display is not recognized i manually changed xconf.org by using modeline as follows:
[COLOR=Blue]Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768_60.00"
        EndSubSection
EndSection[/COLOR][COLOR=Blue]

[/COLOR]

but nothing happend nor the resolution changed or is possible now to change.
Anybody any help idea what to do?
Help would be greatly appreciated :popcorn:

---


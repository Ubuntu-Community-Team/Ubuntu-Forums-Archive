---
title: "How can I permanently change default screen resolution"
date: 2008-10-22
forum: Hardware
---

### Post by mibadt on 2008-10-22
Hi,
I installed Kubuntu Intrepid (8.1)/KDE 4.1 on an old laptop supporting a 1024 X 768 @ 60Hz screen resolution. Unfortunately, my default resolution, as reported by xrandr is 1600X1200.
Trying to edit my xorg.conf I found that it's useless as:
1. It contains predefined entries-see example below
b. On every boot it' rewritten, presumably by dexconf.

Searching further down the line, I found hat dexconf is a front end to debconf.
Looking at /etc/debconf.conf didn't refer to screen resolution.

My questions:
1. How is screen resolution and refresh rate set during the boot/X/kdm session?
2. How can I fix my screen parameters and make these permanent? (I'd rather use the terminal/command line as currently my screen is almost useless-being oo large and partly unaccessible).

Thanks!
Michael Badt




--------copy of partial xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection
-----------------end of copy----------

---

### Post by ad_267 on 2008-10-22
Try running "nvidia-settings" as root, I think you use "kdsu nvidia-settings" in kubuntu. It might not be installed by default.

---


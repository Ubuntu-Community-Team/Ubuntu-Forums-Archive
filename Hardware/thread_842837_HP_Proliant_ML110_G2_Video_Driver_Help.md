---
title: "HP Proliant ML110 G2 Video Driver Help"
date: 2008-06-27
forum: Hardware
---

### Post by imolafem on 2008-06-27
Hi everyone, I just installed the latest version of Ubuntu Desktop on an HP Proliant ML110 and so far I am very impressed.  Everything I need to work is 'right there'.  However, I am stuck in 800x600 resolution and this is driving me crazy!  I need a much higher resolution and I can't seem to find a video driver to do this when I search Google.  Can someone please help me?

---

### Post by imolafem on 2008-06-28
Thought I would post the solution for all who run into this problem with the ATI Rage XL integrated video card.  I tried the ATI proprietary drivers, but this caused X not to load because it couldn't find a display to use.  I guess this means the ATI Rage XL integrated card doesn't work with the ATI proprietary drivers.  So I modified the /etc/X11/xorg.conf file to look like this and I can get 1024x768 resolution now:

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 24-82
        VertRefresh 50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Modes   "1024x768"
        EndSubSection
EndSection

Please note you should look up your monitor's specs to make sure the HorizSync and VertResfresh rate values are correct for your specific monitor.

---


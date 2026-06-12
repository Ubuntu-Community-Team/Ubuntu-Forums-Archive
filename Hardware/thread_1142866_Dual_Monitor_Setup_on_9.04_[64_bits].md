---
title: "Dual Monitor Setup on 9.04 [64 bits]"
date: 2009-04-29
forum: Hardware
---

### Post by pmatos on 2009-04-29
Hi all, 

I have gotten a dell xps 1330 with a 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

and installation of ubuntu went well. I have a monitor DELL 22'' (dell s2209w).

I want to be able to plug the laptop into the monitor, close the laptop monitor and keep working but it seems that configuring it through the display in gnome doesn't work very well. It detects the monitor but it doesn't detect appropriate resolutions since when I click mirror it only allows me to use the laptop monitor resolution and that's not what I want. I want to use a higher resolution for my big monitor.

I thought about tweaking /etc/X11/xorg.conf but it doesn't seem to have much:
[INDENT]Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1280 1792
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
[/INDENT]
What's the best way to configure something like this in Ubuntu?

Cheers,

Paulo Matos

---


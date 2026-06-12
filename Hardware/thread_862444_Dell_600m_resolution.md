---
title: "Dell 600m resolution"
date: 2008-07-17
forum: Hardware
---

### Post by Oziyak on 2008-07-17
I'm fairly new to ubuntu and linux in general.... and I've installed 8.04 on my older dell 600m.... and with some searching I've finally got some hardware accelerated graphics going... but my resolution won't go higher than 1024.768

here is my xorg.conf file.... well the part describing the graphics
Section "Device"
        Identifier      "Radeon 9000"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "GARTSize" "64"
        Option          "MergedFB" "off"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9000"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth           24
                #Virtual                1920 1440
                Modes           "1280x800@60" "1024x768@60" "800x600@60"
        EndSubSection
EndSection



I've heard of people doing resolutions higher than 1280x800
but whenever I go to system->preferences->screen resolution ... it only shows a maximum of 1024x768

please ... any help you can provide would be wonderful

thanks

really getting to like this ubuntu :)

---

### Post by Oziyak on 2008-07-19
still can't figure this out

I also run the intel pro wireless 2100 and seem to have my connection dropped all the time

these are the only two problems I have left with my ubuntu installation and would love to have them fixed...

any suggestions are greatly appreciated

thanks

---

### Post by and.hunt on 2008-07-20
I've always been able to fix reoslution problems by running:
```
sudo xfailsafedialog
```
There, you have to select configure, select Display 1, and open model. Then select a monitor which most closely resembles your monitor: I had to select a generic LCD with 1024x768 for my laptop to get full resolution.

I also have the same wireless card, but don't use it, so I can't really (try to) help you... It detects surrounding networks fine, but I haven't tried connecting to any.

---


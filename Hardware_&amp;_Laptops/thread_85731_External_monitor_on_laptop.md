---
title: "External monitor on laptop"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by Plagued on 2005-11-03
Hello all,
  I will be migrating from a desktop to a laptop at work and am trying to work out some issues before the migration officially happens. I have the laptop already and here are the specs:

Compaq Evo N800c
Pentium 4
640MB RAM
30 G HDD
ATI Mobility Video card

I have done some searching around for this, but it appears that most people are actually looking for something different than I. There are lots of posts regarding mirrored displays (laptop & external) and dual monitor (xinerama), but what I would like to be able to do would be to run the laptop closed while I am at the office.

The laptop itself can support 1024x768, which is great, but the external monitor that I have can do 1280x1024. So what I would like to be able to do would be to use the laptop screen at 1024x768 when I am on the road / out of the office, but use the external monitor at 1280x1024 when at the office. I would prefer it to have it do the work for me, but I don't mind changing resolutions manually when I plug in the external monitor. The problem that I have hit is that it won't seem to let me go higher than 1024x768, which I find to be an annoying resolution on a 17" monitor.

Any advice would be appreciated.

---

### Post by x3nos on 2006-12-15
I believe the basic setup at the following link will help you out.

[http://ozlabs.org/~jk/docs/mergefb/]("http://ozlabs.org/~jk/docs/mergefb/")

Basically your xorg.conf should look something like this:

```

Section "Device"
        Identifier      "ATI Radeon 9600 (Primary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9600 (Secondary)"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Laptop LCD"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Device          "ATI Radeon 9600 (Primary)"
        Monitor         "Laptop LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x854"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "ATI Radeon 9600 (Secondary)"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x854" "1280x1024"
        EndSubSection
EndSection


```

Basically you just need to setup two devices with the monitors being the key difference and then put them together in two separate Screen sections.  Yours may look much different depending on hardware and how you setup the xorg.conf file.

---


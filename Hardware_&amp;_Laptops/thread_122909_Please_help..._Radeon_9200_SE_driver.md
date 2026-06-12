---
title: "Please help... Radeon 9200 SE driver"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by chugru on 2006-01-28
Hi, all...

I'm totally new at this (1 day) and trying to set up Kubuntu. My graphics card is an ATI Radeon 9200 SE.

Could someone please tell me what driver Kubuntu requires for this?

Thanks...

---

### Post by halfvolle melk on 2006-01-28
Hi,

This thread:
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)
seems to have been of much help to several users.
Somewhere it says "<your-kernel-version>". You can determine this by typing:
uname -r
in a console. It will probably state "2.6.12-10-386". Dunno if you need to put "linux-" in front of it. Hope this helps, but maybe some non-newby users have better suggestions :).

---

### Post by chugru on 2006-01-29
**halfvolle melk wrote:**

> This thread:
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)
seems to have been of much help to several users.

I followed the advice, but, now things are worse...

When I reboot, now, I end up hanging near the end of the boot process with the following error from Xorg.0.log: ```
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(II) fglrx(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 8/8
(EE) fglrx(0): Given depth (8) is not supported by fglrx driver
(EE) fglrx(0): PreInitVisual failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

If I **sudo -i** to root, I can **startx** KDE in root mode, still with a fixed low display resolution (640x480), which is why I opted to install the driver in the first place.

I know I'm dealing with either an ATI "fglrx" driver problem or a config issue. My **xorg.conf** which is giving mt this problem is as follows:```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver          "fglrx" # this is the important bit
#       Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL P991"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Monitor         "DELL P991"
#       DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Is this maybe an "old Dell cathode ray monitor" issue?

Could someone please give me some insight?? :confused: 

Thanks...

---

### Post by h3xx3r on 2006-01-29
a restart should sort it if you can sudo and startx 
GDM will do the rest on boot, ( well it has here a couple of times recently with the dapper xorg)

---

### Post by chugru on 2006-01-29
But restart doesn't seem to sort anything...

And, what is GDM??

Thanks!

---


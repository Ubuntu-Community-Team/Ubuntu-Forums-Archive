---
title: "FGLRX and XGL with an Ati X600"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Anouar on 2006-09-22
Hi guys

I have problems with installing XGL 
First i want to install fglrx 

so instead of "ati"  i use fglrx  in xorg.conf
but when i restart 

i stucks at "runiing local boot scripts (/etc/rc.local)"

And if I boot in recovery mode and then check /etc/X11/xorg.conf

It says:

Section "Device"
        Identifier      "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Driver          "fglrx"
        Option          "MonitorLayout" "LVDS,Auto"
        BusID           "PCI:1:0:0"
And when i fglgrxinfo:

Section "Device"
        Identifier      "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Driver          "fglrx"
        Option "MonitorLayout" "LVDS,Auto"
        BusID           "PCI:1:0:0"



So, why it does not work if i boot the normal way



Can anyone help me with installing fglrx so i can run XGL

I tried a how to installing fglrx but now if return it to Ati i get very slow graphics

---


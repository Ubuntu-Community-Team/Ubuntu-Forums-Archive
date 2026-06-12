---
title: "TV out with different resolution"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by DidRocks on 2004-12-28
Hi!

I read a lot to get Tv-out with nvidia drivers (i have a geforce 4 ti). But, impossible to find a way to have 2 differents resolutions (one for my tv and one for my monitor), because the latter is on 1280x1024 and my tv can't support it ...
Is somebody know how to get it?

Thanks in advance!

Did

---

### Post by diebels on 2004-12-28
[QUOTE=/usr/share/doc/nvidia-glx/examples/XF86Config.sample.gz]Section "Device"
    Identifier "NV AGP TwinView"
    VendorName "nvidia"
    Driver "nvidia"
    # update this with the PCI id of your card.  Consult the output
    # of the 'lspci' command. The  BusID is usually optional when
    # only using one graphics card.
    BusID       "PCI:1:0:0"

    # sample twinview setup
    Option "TwinView"
    # be sure to replace the HorizSync and VertRefresh with correct values
    # for your monitor!
    Option "SecondMonitorHorizSync"   "31-82"
    Option "SecondMonitorVertRefresh" "55-120"
    Option "TwinViewOrientation"      "RightOf"
    Option "MetaModes"                "1280x1024,1280x1024; 1024x768,1024x768"
    Option "ConnectedMonitor"         "crt,crt"
EndSection
[/QUOTE]
I think it's the
Option "MetaModes" "1280x1024,640x480"
you need

---

### Post by DidRocks on 2004-12-29
thx a lot, that works perfectly!

---


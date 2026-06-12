---
title: "Intel graphics (G45) won't work on 9.04"
date: 2009-05-30
forum: Hardware
---

### Post by ebike on 2009-05-30
Hi All,

I have been having issues with the Intel driver for my on-board graphics of by G45 based motherboard (ASUS P5Q-EM). With Mythbuntu 8.10, I could not get an X11 session running, all I got was a green screen. I could only use the opengl driver. So hoping that the driver was fixed, I upgraded to 9.04 only to discover that the intel graphics driver would not load at all, and I had to boot in VESA safe mode .... which is not good for watching TV in ..

The error in the log is:
> (II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/local/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.5.99
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(EE) module ABI major version (4) doesn't match the server's version (5)
(II) UnloadModule: "intel"
(II) Unloading /usr/local/lib/xorg/modules/drivers//intel_drv.so
(EE) Failed to load module "intel" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log 

As you can see, I am having a version issue between X and the Intel driver ... X looks to be 1.6.0 and the Intel driver 1.5.2.

Can anyone tell me how to upgrade the intel driver to 1.6.0??
Also, if anyone has an xorg.conf for this motherboard or G45 chipset, I would love to see it.

Many Thanks,
Bernie

---

### Post by zuerston on 2009-05-30
Did you check this?

"Please consult the The X.Org Foundation support
         at [http://wiki.x.org]("http://wiki.x.org/")
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information."

---

### Post by ebike on 2009-05-31
Yep, had seen that. I found the issue. I remembered that I had compiled aversion of the intel drive some time ago .. I forgot it put it under /usr/local/lib and it was been picked up before the one in /usr/lib.

I removed the one in local and all was fine again. Solved.

---


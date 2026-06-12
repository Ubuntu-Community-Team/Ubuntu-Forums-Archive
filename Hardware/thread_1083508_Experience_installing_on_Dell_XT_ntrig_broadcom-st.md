---
title: "Experience installing on Dell XT ntrig broadcom-sta"
date: 2009-03-01
forum: Hardware
---

### Post by onlyoneskwalla on 2009-03-01
Figured I'd post my findings on the installing with ubuntu. First things first Intrepid Ibex(8.10) at least for me will crash (Xserver) when installing in gnome. However in Kubuntu 8.10 kde4 disc it will install perfectly, but with Ubuntu Ultimate disc in the kDE session it will crash unless I explicitly tell grub the boot drive is /dev/sda not (hd0).:confused:

:KS[For broadcom wireless dell 1510 using sta had to add these commands to block the modules from loading before wl. ]("http://www.backports.ubuntuforums.org/showthread.php?t=949198")

:P[Support for Ntrig tablet function is coming in the kernel.  Patches are currently available but you will lose ubuntu "support" patching your own kernel i think but you should be allowed to make that choice.]("http://ofb.net/~rafi/latitude_xt.html") That link is a rundown of hardware advice on a Debian unstable system.  I tested the patches on a sabayon installation 2.6.28 kernel and they do work, both touch and pen worked but was having wacom config issues and the input was not smooth and not acceptable. Will test on ubuntu when ready and post here.:guitar:

---


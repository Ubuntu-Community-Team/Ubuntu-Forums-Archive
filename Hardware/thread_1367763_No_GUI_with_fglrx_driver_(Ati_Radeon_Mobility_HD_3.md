---
title: "No GUI with fglrx driver (Ati Radeon Mobility HD 3400 series graphics card)"
date: 2009-12-29
forum: Hardware
---

### Post by RodGer GR on 2009-12-29
It is a Toshiba Satellite A300 friend's laptop where I installed Ubuntu for the first time. When I activate the certain driver and reboot, the graphic desktop never shows up and I only get a black screen instead. I have to boot from an older kernel (where the driver is not active) or from a live cd so that I can disable the proprietary driver. I delete or edit the /etc/X11/xorg.conf or uninstall the driver packages using synaptic, reboot and there comes the graphic desktop back.

Without this driver I can't enable the desktop effects. There is a bug filed for this driver [here ( link )]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all") although nobody refers such a serious problem like losing GUI.

Is there any work-around so that I can enable desktop effects. I would use Ubuntu and try to make it better even without the effects cause I believe in open source software benefits. My friend though (whose the laptop is) is a new user and for new users, it's always the effects that do the trick until they really learn what Ubuntu is all about.

So, please help me find a solution. I'll provide any information asked and I'll be grateful for any idea you are willing to suggest.

---

### Post by Yellow Pasque on 2009-12-30
If you get a 2.6.32 kernel running, you can get 3D with the open-source drivers: [http://ubuntuforums.org/showthread.php?t=1355358](http://ubuntuforums.org/showthread.php?t=1355358)

---

### Post by RodGer GR on 2009-12-30
Thanks thanks thanks and again thanks. You're really great. Your suggestion worked like a charm. 

P.S. Thanks again.:guitar:

---


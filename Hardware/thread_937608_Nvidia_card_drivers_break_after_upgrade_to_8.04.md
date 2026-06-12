---
title: "Nvidia card drivers break after upgrade to 8.04"
date: 2008-10-04
forum: Hardware
---

### Post by Lance423 on 2008-10-04
For starters, here's the specs of the machine I'm currently having the issue with:

Intel Pentium 4 2.66Ghz
1GB RAM
Nvidia GeForce FX 5500 PCI, 256MB

The issue is that after my distribution upgrade from 7.10 to 8.04 and updating from nvidia-glx to nvidia-glx-new and restarting GDM, I'm always starting in safe video mode, and it's asking me to configure which drivers to use. There is an Onboard Intel i810 chipset, but I can't even find the VGA port for it, which normally I would have noticed by now. My question is how can I get my 5500 working again WITH 3D acceleration. All I really want is to be able to do my homework, play WoW every so often, and have normal desktop effects enabled. The machine has an AGP slot, but the AGP cards I have are OLD and I don't have money to spend on a new(er) card at the moment. Any help is GREATLY GREATLY appriciated. Thanks in advanced!

---

### Post by shredder12 on 2008-10-04
hey why don't you just switch it back to the older version may be that will work..or you may even try the Ubuntu restricted drivers..

---

### Post by Lance423 on 2008-10-04
nvidia-glx-new is the restricted drivers, I know enough about that. The problem is GDM isn't wanting to use them properly, and the old drivers aren't giving me the acceleration for direct rendering anymore. I need to be able to boot without safe graphics mode and I have no clue how to go about that. I've been Googling for HOURS now, and I've not gotten many results, and the one's I've gotten aren't helpful

---

### Post by Lance423 on 2008-10-04
Sorry to bump, but needs an update. I've been working off this HOWTO:
[http://ubuntuforums.org/archive/index.php/t-33142.html](http://ubuntuforums.org/archive/index.php/t-33142.html)

But I've still had no luck. Again, and help is greatly appriciated. I've been using Ubuntu and other flavors of linux for a while now, but I'm still kinda new to a lot of things. If any file outputs are needed let me know.

---


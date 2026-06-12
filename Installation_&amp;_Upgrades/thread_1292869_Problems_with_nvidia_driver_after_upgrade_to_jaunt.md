---
title: "Problems with nvidia driver after upgrade to jaunty"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by treuss on 2009-10-16
I just upgraded to jaunty and upgrade went ok, however after installing the proprietary nvidia driver (forgive me, I don't have the version number at hand - 818 or so), the system boots into safe-graphic mode with
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
in the Xorg.log.

Checking with lsmod, it looks like the nvidia kernel is indeed not loaded.

I've attached lspci and lsmod output along with xorg log and conf files. I'd appreciate any hint on why this isn't working.

Intrepid was working ok.

---


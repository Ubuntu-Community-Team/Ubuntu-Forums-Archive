---
title: "Boot from USB Pendrive to boot into Ubuntu"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by DylanNIRVANA on 2009-04-04
Hey guys.

So basically, my setup consists of, Ubuntu which was installed with WUBI, and obviously my Windows XP installation. Basically, i want to be able to boot Ubuntu ONLY when the USB pendrive is inside, well, boot to the pendrive which then boots the Ubuntu WUBI installation. So that the user who normally uses Windows XP can just turn on the PC, without having to select anything, which will just boot straight into XP. But when i put the pendrive and boot from that, the pendrive boots from the WUBI installation.
I was thinking of making a boot.ini on the USB pendrive, specifying the WUBI installation item, so that it would boot that way, do you guys have any ideas?

Thanks

---

### Post by DylanNIRVANA on 2009-04-05
~Bump~

Nobody?

---

### Post by SR_ELPIRATA on 2009-04-06
Never done this. I have, however, installed Ubuntu on a pendrive and works great. I would recommend installing to pendrive and have the Ubuntu user plug it in when he wants.

You'll have to set the bios accordingly, so that the usb storage boot devices are higher than the hard disk. If the USB is not in, then should load windows no problem.

This pendrive I've tested with some dell laptops and systems and whenever I want to use it just plug it in and make sure the bios is set to check the usb first :)

Your idea of using the pendrive as a key for the system to load wubi/ubuntu... I dont think it will work, but I can't say that categorically. Its a good idea, but why go with all the trouble when you can install Ubuntu in the pendrive as well?

ELP

---


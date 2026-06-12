---
title: "pcmcia cdrom and boot disks"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by tommcb on 2005-09-20
I have been playing with an older Toshiba Portege 7020ct laptop.  It has a pcmcia cdrom drive.

Because this machine does not boot to the cdrom drive,  I'll need to use floppy boot disks.  

The SBM boot image included with 5.04 doesn't work because I need to turn on pcmcia before it would see the cdrom drive.

Has anyone seen any regular boot disks for ubuntu 5.04?  The old fashioned way works great, ex. boot.img, root.img, and cd-drivers.img gets debian going great on this machine.  (or bootdisk.img and pcmciadd.img for fedora core)



P.S. No network install cause the network card would be pcmcia also.  (And the guy who owns the toshiba left his network card at home)

---

### Post by stepic on 2007-01-09
I've exactly the same problem.
My laptop has a PCMCIA CD-ROM  and I didn't find any way to install.

Can anybody give me some idea how to install it.

Thank you

---

### Post by tommcb on 2007-01-09
Solved the problem by installing Fedora Core instead.  It finds the cdrom drive with some minor tweaks (Don't remember which tweaks in particular at this point).   It's still going strong at this point and the 8 year old who uses it couldn't be happier.

---

### Post by stepic on 2007-01-10
Really? That's fantastic.
Don't you remember anything how you made it?

I've downloaded the Fedora Core 6 too, but .... as I have a PCMCIA CD-ROM that can't boot I have no success.
Somebody told me to try the install loading the kernel directly from hard disk (with autoboot and loadlin) but even that didn't work. 

I am still looking for some helps.

Thank you.

---


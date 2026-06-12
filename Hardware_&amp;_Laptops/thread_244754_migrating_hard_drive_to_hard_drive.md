---
title: "migrating hard drive to hard drive"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by spartan777 on 2006-08-26
so i have ubuntu on a 20gig hard drive, and just want to copy everything exactly to an 80 gig hard drive. i can't seem to do it with gparted. i copied the 20 to the 80, made an "extended" partition of 800megs, and made the swap space inside that. i made the partition i copied from the 20 bootable. all this i did with the bootable live cd of gparted .2.5. whenever i try booting from the 80, after everything is copied over, i only get a flashing cursor. also, i installed gag, and can't seem to get rid of it, though i don't thinks it could be hurting anything. anyone know of a tool for copying a hard drive identically over to another? thanks in advance.

---

### Post by catlett on 2006-08-26
I never used ity but Aysiu made a how to for it, it may be the thing your looking for. Partimage [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by spartan777 on 2006-08-30
partimage is handy, but gparted does the same thing, only easier, and safer (since it has a gui).

what I want is is to boot off the hard drive once I copy over the information. i've tried adding the bootable flag to the partition, and then using gag for a bootloader, but that doesn't work. those directions are only good for replicating data, not for making a new, bootable hard drive with everything on it that is already on my older hard drive.

thanks for the help though.

---


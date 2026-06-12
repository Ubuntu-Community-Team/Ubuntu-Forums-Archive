---
title: "Need help uninstaling ubuntu"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by mister_pal on 2009-08-04
So, I tried Ubuntu for a few months, and I don't like it. I'm trying to reinstall Windows XP, but when I put the disk in at startup and go through the installation process, it always tells me that it cannot detect any hard disk on my computer. Clearly, I have a hard disk, why can't it detect it? Does anyone know an easier way to replace Ubuntu with Windows XP?

Thank you.

---

### Post by razorboy5 on 2009-08-04
did it have XP installed on it when u got it or was it pre installed with Vista?

XP does not recognize SATA drives by default meaning if u have a SATA drive then it will not be able to find it and consequently not be able to install

i would recommend u installing Vista if that came preinstalled (then u know it works) or u can add the floppy SATA drivers so it works or if u dont have a floppy drive u can install the SATA drivers onto the XP disk so it recognizes it

---

### Post by mister_pal on 2009-08-04
it came with windows xp, it's a 2007 Thinkpad.

---

### Post by razorboy5 on 2009-08-04
perhaps the person installing had a copy or XP with SATA drivers installed :S

check what kind of hard drive u have then u can go from there :P

---

### Post by merlinus on 2009-08-04
You may need to use gparted on the live cd to delete all your partitions, and create one formatted as ntfs.  Windows hates anything but itself.

Also, IIRC xp sp2 and 3 have support for sata hdds.

---

### Post by ugm6hr on 2009-08-04
> **merlinus said:**
> You may need to use gparted on the live cd to delete all your partitions, and create one formatted as ntfs.  Windows hates anything but itself.

I have encountered this before too.

XP does not recognise a HD with all non-Windows partitions.

I used a low level disk formatting program to wipe the HD and start afresh.  It's called Active KillDisk (or something similar).

---

### Post by mister_pal on 2009-08-08
How do I burn an ISO image to a blank disc? I tried right clicking and selecting "burn to disc" but it always gives me this error and tells me to try a slower burning speed, but that isn't working either. Any thoughts?

---

### Post by ugm6hr on 2009-08-08
> **mister_pal said:**
> How do I burn an ISO image to a blank disc? I tried right clicking and selecting "burn to disc" but it always gives me this error and tells me to try a slower burning speed, but that isn't working either. Any thoughts?

On Ubuntu ? Or Windows?

If former, try installing gnome-baker or k3b.

---


---
title: "Problem: grub error 15 when installing root and home on different drives."
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by skaldyr on 2009-06-24
I have two very small harddrives(1.9gb) so i have made the root partition on ones drive and the swap and home partitions on the other. It installs fine but when i boot it, i get 



plese wait grub loading
error 15

:confused:


How can i fix the bootloader or is it not possible to install like i have done?

---

### Post by presence1960 on 2009-06-24
1.9 GB? that definitely isn't enough space for an installation.

---

### Post by skaldyr on 2009-06-25
It's two physical(not partitions) drives with 1,9gb on each.
I have a 500mb swap and a 1300mb home on one and a 1900mb root on the other.

I think i need to edit the bootloader but i don't know what to do.

---

### Post by presence1960 on 2009-06-25
> **skaldyr said:**
> It's two physical(not partitions) drives with 1,9gb on each.
I have a 500mb swap and a 1300mb home on one and a 1900mb root on the other.

I think i need to edit the bootloader but i don't know what to do.

[https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html)

[https://help.ubuntu.com/9.04/installation-guide/i386/disk-space-needed.html](https://help.ubuntu.com/9.04/installation-guide/i386/disk-space-needed.html)

---

### Post by SteveDee on 2009-06-25
> **skaldyr said:**
> It's two physical(not partitions) drives with 1,9gb on each.
I have a 500mb swap and a 1300mb home on one and a 1900mb root on the other.

I think i need to edit the bootloader but i don't know what to do.

Grub error 15 means it cannot locate a file specified in the /boot/grub/menu.lst file, but it is happy with the drive & partition info.

The easiest way to sort out problems with grub is to download SuperGrub, create a CD, boot from this disk, and then try fixing it from the SuperGrub menu.

SuperGrub link: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by presence1960 on 2009-06-25
Grub error 15 from [http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

# 15 : "Error while parsing number"

This error is returned if GRUB was expecting to read a number and encountered bad data.

seems that different sites give different explanations. 
I still think he may not have enough space to install to. see this from the second link I posted earlier:

Disk Space Needed

A minimal server installation of jaunty requires 400MB of disk space. The standard Ubuntu desktop installation requires 2GB. Hopefully that is not the problem, but I think it may be.

---

### Post by SteveDee on 2009-06-25
> **presence1960 said:**
> Grub error 15 from [http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

# 15 : "Error while parsing number"

This error is returned if GRUB was expecting to read a number and encountered bad data.

seems that different sites give different explanations. 
I still think he may not have enough space to install to. see this from the second link I posted earlier:

Disk Space Needed

A minimal server installation of jaunty requires 400MB of disk space. The standard Ubuntu desktop installation requires 2GB. Hopefully that is not the problem, but I think it may be.

...Yeah but this is the official site: [http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

---

### Post by skaldyr on 2009-06-26
Thank you for the replies.

I have tried super grub disk. but i get an error while loading it no matter what i try.


I might go back to moblin, at least that can boot on this device.

---


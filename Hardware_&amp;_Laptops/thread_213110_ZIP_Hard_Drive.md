---
title: "ZIP Hard Drive"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by ssmithy on 2006-07-10
I have been trying to get my dad's Iomega ZIP 100MB external parallel drive to mount in Ubuntu.  So far...

1. I've added PPA to the /etc/modules/
2. Made the directory /mnt/zip100.0
3. Added this to my /etc/fstab/
   /dev/sda4 /mnt/zip100.0 vfat noauto,user 0 0

I try to mount the drive, which shows up in the gnome-volume-manager, and it gives me the following:

mount: special device /dev/sda4 does not exist

The really wierd thing is when I run dmesg on my computer I get absolutley nothing related to the zip drive.  Do I need to recomplie the kernel to recongnize this device?  I've posted this elsewhere and followed other howtos but have hit a brick wall. ](*,) 

I hope someone can help.  Thanks!

---


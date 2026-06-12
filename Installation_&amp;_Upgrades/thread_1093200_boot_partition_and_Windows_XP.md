---
title: "/boot partition and Windows XP"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by notesetter on 2009-03-11
I have a 250 GB drive, but my BIOS will only let me access +/- 137 GB of it. I've read with interest about using a separate /boot partition to allow Ubuntu to use the whole drive by locating the kernel at the beginning of the beginning. My question is:

Is it possible to set up a dual-boot scenario where I use a /boot partition with GRUB in conjunction with a partition for Windows XP within the first 115 GB or so, and then a partition for the rest of the drive which is for Ubuntu? What does this scenario look like and how can I install the OS's?

Links to online forums would be great. If any of you have already succeeded with this, I'd love to know how you did it.

Thanks,

Dave

---

### Post by maybeway36 on 2009-03-11
The boot partition would go in the readable part of the drive. If you are reinstalling windows anyway, might as well put Ubuntu's /boot before Windows. You won't need more than 128MB for /boot.
If you have a seperate /boot, it's OK to put / on a logical partition (inside an extended partition.)

---


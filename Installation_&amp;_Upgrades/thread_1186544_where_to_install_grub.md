---
title: "where to install grub?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-06-13
Jaunty installation problem.  At startup, the GRUB loader screen appears, I select Ubuntu (first option) and then the system hangs.  If I choose XP from the GRUB loader screen, windows boots correctly.

I have installed Jaunty (32 bit) from the live CD.

Windows XP is installed on 2 NTFS hard drives, /dev/sda and /dev/sdb, each with several partitions.

Jaunty is installed on a separate physical hard drive, /dev/sdc, with 1 primary partition (/dev/sdc1) and 10 logical partitions (/dev/sdc5 throught /dev/sdc14).  One of the logical partitions (/dev/sdc7) is swap.

I think the problem exists because GRUB doesn't know where to find menu.lst, /sbin/init, etc.

When I installed Jaunty from the live CD I chose manual installation.  The / (root) is on logical partition /dev/sdc5, and /boot is on logical partition /dev/sdc6.

Towards the end of the install there is an "advanced" box to select where to install GRUB.  I Selected the / partition (dev/sdc5).  But now I'm wondering if that was the wrong thing to do, since /boot is located on a separate logical partition.

Does anyone have any suggestions?

---

### Post by Bucky Ball on 2009-06-13
Yes, it should be in /boot. Not sure what you need to change to get it there though, sorry. You might even be able to change it so it finds it in / !

---

### Post by raymondvillain on 2009-06-13
I tried another trick.  Booted to Jaunty (with the help of rescuecd), opened a terminal, and typed:

sudo grub

then at the grub prompt, I typed:

find /boot/grub/stage1

and it returned the message "Error 15: File not found"

But in fact, /boot/grub/stage1 exists and I can see it from within Nautilus.

Does all this mean grub is somehow royally messed up?

---


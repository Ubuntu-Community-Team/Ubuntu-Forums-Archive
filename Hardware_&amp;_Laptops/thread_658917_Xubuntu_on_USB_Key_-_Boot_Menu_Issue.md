---
title: "Xubuntu on USB Key - Boot Menu Issue"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Ironfighter on 2008-01-05
Hi,

This is my first post on this board.  
I have just Installed Xubuntu on a 4Gig USB key from the live CD via an XP laptop.  I have been learning about linux for the past 3 years and no longer use Windows at home (Mandrake 10.1 Community).  The laptop in question is for business use when I need to work from home or when travelling.  Therein lies the problem.  Since I installed Xubuntu on the USB key the only way I can access XP on the laptop is if I have the Xubuntu USB key inserted during the start up routine.  At first glance this seems to be quite an attractive security feature however, I am worried that I may loose the USB key or it becomes corrupt or damaged.  I would like to get the laptop to boot up straight into XP without the USB key inserted.  I have tried a system restore under XP but it didn't work.  From what I can discover from other threads it seems I may be able to edit the boot menu.  I would appreciate some advice as to how to resolve this issue.  Here is the output from <sudo leafpad /boot/grub/menu.1st>

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e43bdc26-584e-471a-96f3-c735ef8d4de8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e43bdc26-584e-471a-96f3-c735ef8d4de8 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

By the way - I have tried many live Linux CD's over the past 3 years to find the Linux flavour that I like.  From what I have seen so far Xubuntu is the most user friendly in getting must have applications and utilities (like wireless internet) up and running quickly.

Thank you in anticipation.

---


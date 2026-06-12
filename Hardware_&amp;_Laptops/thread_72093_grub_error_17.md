---
title: "grub error 17"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by gnicezw on 2005-10-05
I've been trying to tidy up my hard-drive by deleting empty and non- essential partitions. I've had a few problems which i have been able to resolve( with some help from this forum). 
Current problem is that i deleted a partition my root partition has changed from /hda9 to /hda8 . i updated fstab and menu.Ist but immediately got grub err 17 on reboot. 
my understanding is that this error arises from a filesystem mismatch. I've updated menu.Ist for my ubuntu install as follows:
title          Ubuntu, kernel 2.6.10....
root          (hd0,7)
kernel        /boot/vmlinuz-2.6.10..... root=/dev/hda8 ro quiet splash
intrd          /boot/initrd.img-2.6.1...........
savedefault
boot.
all i changed was (hd0,8 ) --->(hd0,7) 
and root=/dev/hda9 ------->root=/dev/hda8
i know the partition is definately /dev/hda8 because i can mount it from the live cd. Is it possible that it might not be (hd0,7) and would that be important?

---

### Post by mlomker on 2005-10-05
Might want to boot the liveCD and use the find command to verify the partition number, etc.

A [how-to]("http://geodsoft.com/howto/dualboot/grub.htm#install") on that.

---


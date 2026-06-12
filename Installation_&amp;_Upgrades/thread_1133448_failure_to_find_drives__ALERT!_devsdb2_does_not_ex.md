---
title: "failure to find drives : ALERT! /dev/sdb2 does not exist"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by king vash on 2009-04-22
I did a upgrade to Jaunty beta and it ran completely everything went well and I hit restart. was happy with the pretty new start logo when bam I get dropped to the busybox shell

with the error 
ALERT! /dev/sdb2 does not exist dropping to a shell!

The problem is not UUID's or anything like that. I have been debugging that for a long time.

"ls /dev | grep sd" returns nothing
"ls /dev | grep hd" returns nothing
/dev/disk does not exist

I can load up a old (8.10) live cd and then my drives show up and the /dev/disk, /etc/fstab and /boot/grub/menu.lst work look correct.

I have tried changing my boot loader to 
     root=UUID=thing from old menu.lst
     root=/dev/sdb2

I have tried changing root (hd 0,1)

any other suggestings?

---

### Post by king vash on 2009-04-23
solved!

live disk

sudo su
mkdir /mnt/test
mount -t ext3 /dev/sdb2 /mnt/test
chroot /mnt/test
mount -t proc proc /proc
apt-get autoremove
apt-get dist-upgrade

fixed!

---


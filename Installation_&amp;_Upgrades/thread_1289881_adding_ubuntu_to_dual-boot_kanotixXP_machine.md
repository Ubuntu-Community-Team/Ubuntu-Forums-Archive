---
title: "adding ubuntu to dual-boot kanotix/XP machine"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by ryancw on 2009-10-12
I have been running kanotix for quite a while, on a dual-boot (grub) PC, alongside WinXP. After a good experience with eeebuntu on my new eeepc, I would like to try installing ubuntu on the desktop. I have an Ubuntu 8.10 DVD. 

I have two 500-MB hard drives: sda and sdb

sda is set up as follows:

/dev/sda2              65G  3.6G   58G   6% /
tmpfs                 1.5G   12K  1.5G   1% /lib/init/rw
udev                   10M   84K   10M   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
/dev/sda3             187G   15G  164G   9% /home
/dev/sda1             120G  9.0G  111G   8% /windows

When the Ubuntu installer partition manager first popped up, I noticed that none of my existing partitions had a mountpoint listed. I created an ext3 partition, called sda4. I set the mountpoint as /   My intention was to put Ubuntu in there. I also went and edited some of the existing partitions, to give them mountpoints as listed above. I don't know whey the mountpoints weren't shown at first, and perhaps specifying the mountpoints for them at that time was not the right thing to do. I just didn't want to lose the working Kanotix installation I had--didn't want to make it unbootable. 

   At any rate, the Ubuntu installer objected to having two partitions with the same mountpoint. So I abandoned the installation for now.

How  should I go about installing Ubuntu so that I can choose either Kanotix or Ubuntu at the grub bootloader screen?

Thanks.

--Chris

---


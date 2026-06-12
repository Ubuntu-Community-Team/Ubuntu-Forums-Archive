---
title: "[SOLVED] Change GRUB loader from one partition to another"
date: 2008-08-17
forum: General Help
---

### Post by march2503 on 2008-08-17
Hi all! This is my first post on this forum ):P

I am a real newbie to Linux & Ubuntu and have been experimenting with various distros, with a view to eventually dropping windows.

What I have at  present is XP on my first hard drive (sda) and two partitions on sdb, the first containing HH and the second having Mepis 7 on. Grub is on the Mepis partition but I want to get rid of this, increase the space available for Hardy and change the Grub over to the Ubuntu partition.

Can anyone advise me if this is possible without re-installing Hardy? I am loathe to do this as I have made a number of changes already and don't really want to start over. Please keep instructions as simple as possible as I am still getting used to using Terminal etc.

Thanking you in anticipation.

Frank

---

### Post by Elfy on 2008-08-17
Boot with the buntu livecd and reinstall grub, making sure not to use the mepis partition

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by march2503 on 2008-08-17
Thanks for the quick reply, forestpixie. I'll have a go at that tomorrow when I'm more wide awake! Should I tackle the re-partitioning at the same time or after the reboot?

Frank

---

### Post by Elfy on 2008-08-17
I would do the partitioning first probably, you can use the same livecd to do that, might need to turn off swap befoire you can work on the partitions though

```
sudo swapoff -a
``` for that.

Good luck

---

### Post by ajgreeny on 2008-08-17
It shouldn't matter when you do the resizing.  Just remember to do it from the live CD and don't try to use gparted on your Ubuntu install as it will not be able to resize itself as it can only work on unmounted partitions.  The live CD has gparted on it by default and can make your Ubuntu partition larger and delete your Mepis partition.  Just make sure you install grub to the right disk.  You can actually do it already in Ubuntu by simply using the command ```
sudo grub-install /dev/sdb
```You may, however, need to change your partition UUIDs in bith the /boot/grub/menu.lst and also in /etc/fstab in your Ubuntu install, as the gparted action will have changed that, I think.

Get the new UUIDs with ```
sudo blkid
``` in the live CD and then mount and edit the files if needed.

---


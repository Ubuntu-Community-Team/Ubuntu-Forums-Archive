---
title: "Changing the partitions in my system"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by tristure on 2006-01-10
Hi, my Breezy installation is located on device /dev/hda7.

I've got my / and /home in that partition.

Now what I would like to do is to have my / on device /dev/hda3 and /home in /dev/hda7.

THe first solution is to make a new installation on this partition. But I don't want to reinstall all the packages and make all my settings again.

Is it possible to "move" my installation. I tried to copy folder with cp, but there seems to be some problems, for instance with files in /proc...

Any help greatly appreciated! Thanks!

---

### Post by Jenda on 2006-01-10
Easy...
You boot up from live CD, mount the partitions in question... and then cp.
Last you need to change fstab to boot the proper partitions and you're done.
1) Live CD
2) mount all partitions in question
3) cp all you might want from the old partition (prolly cp all and then delete whatever you have in /home on the new partition, since you will use the old for that)
4) edit fstab

---

### Post by az on 2006-01-10
Use a partitioner from a live cd.  

The installer cd is a live cd without a graphical interface.  You can use it to move your data.

Boot the installer and go to the console after it detects your hardware (CTRL-ALT-F2)

run parted

parted

show your partitions

print

cop your dta from 7 to 5
cp
(enter info as prompted, ex: 7 then 5)

quit

mount the partition 5

mkdir /mnt
mount /dev/hda5 /mnt

Edit the neccessary files to boot into that partition

vi /mnt/etc/fstab
vi /mnt/boot.grub.menu.list

reinstall grub

chroot /mnt
grub-install /dev/hda


reboot

If all your data is there, edit fstab and make /dev/hda7 your home partition and remove everything else from there.

---

### Post by lha on 2006-01-10
I used this [Hard Disk Upgrade Mini How-To]("http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/index.html") to find advice when I changed my partitioning scheme. There are a few gotcha's you'll have take care of when doing these kind of things. Especially now when you want to move your root and split it into two, at the same time. I know that how-to talks about lilo but it shouldn't be too hard to figure out what you need to do with grub.

Remember to backup and have some sort of emergency plan if you trash your system.

---

### Post by 504harry on 2006-01-10
[QUOTE=lha]I used this [Hard Disk Upgrade Mini How-To]("http://www.tldp.org/HOWTO/Hard-Disk-Upgrade/index.html") to find advice when I changed my partitioning scheme. There are a few gotcha's you'll have take care of when doing these kind of things. Especially now when you want to move your root and split it into two, at the same time. I know that how-to talks about lilo but it shouldn't be too hard to figure out what you need to do with grub.

Remember to backup and have some sort of emergency plan if you trash your system.[/QUOTE]

Hi,
I did try reading this Guide, but became more confused.......I've heard of Slackware but don't think I've got any.....lilo? ....and what does "mounted" mean for a HDD?
/
/
I want to re-install Ububtu 510 and would like to keep the existing 3-partitions (=swap/61G/61G) - all the data can be trashed if necessary. However I understand one of the 61G partitions is reserved for my files (eg photos) and it would be nice to know for next time, how to keep them. 
Normally I would make copies using a CD/DVD burner which appears to be working OK under Ububtu.
Can someone define the partitions *- so I can refer to them by conventional names?  Does Ubuntu have a viewer facility for the partitions - I watched the install process but Partitioning was a blur....
If I use a genuine Ubuntu 5.10 install disc, will I have to start Partitioning all over again?
Sorry if these are easy questions..........


*( I suspect I have a small swap-file and maybe Root plus another for my photos - but don't know their names, etc)

---

### Post by lha on 2006-01-10
[QUOTE=504harry]Hi,
I did try reading this Guide, but became more confused.......I've heard of Slackware but don't think I've got any.....lilo? ....and what does "mounted" mean for a HDD?
/
/
I want to re-install Ububtu 510 and would like to keep the existing 3-partitions (=swap/61G/61G) - all the data can be trashed if necessary. However I understand one of the 61G partitions is reserved for my files (eg photos) and it would be nice to know for next time, how to keep them. 
Normally I would make copies using a CD/DVD burner which appears to be working OK under Ububtu.
Can someone define the partitions *- so I can refer to them by conventional names?  Does Ubuntu have a viewer facility for the partitions - I watched the install process but Partitioning was a blur....
If I use a genuine Ubuntu 5.10 install disc, will I have to start Partitioning all over again?
Sorry if these are easy questions..........


*( I suspect I have a small swap-file and maybe Root plus another for my photos - but don't know their names, etc)[/QUOTE]

Lilo is a boot loader, an alternative to grub. Ubuntu uses grub as default, so you probably have it and not lilo. If a partition is mounted, it basically means that it is "in use". Windows mounts all partitions it access automatically, but in Linux you can choose what partitions are in use. There's a short description of [mount]("http://en.wikipedia.org/wiki/Mount") in wikipedia. It's the last one on that page.

You see some information on your partitions in Applications->System Tools->System Monitor under Devices-tab. If please post ouput of
```
cat /etc/fstab[\CODE] and [CODE]sudo fdisk -l

``` so we can help you out and tell what partition you want to keep. You can choose to manually edit partition tables during install. That option will let you to choose which partitions you want to delete or format and what to keep as they are.

---

### Post by Jenda on 2006-01-12
A nice GUI tool for viewing and manipulating partitions is gParted. I use it all the time.

---


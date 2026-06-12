---
title: "Help on installing 9.04 needed"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by vasya10 on 2009-08-10
Totally new Ubuntu , first time installer ...

I have Windows Server on a sata drive and am trying to install ubuntu on a new IDE drive (set to master).

Sata is recognized as /dev/sda and IDE as /dev/sdb.

Partitioned the IDE drive as 90 gb primary (ext3) + rest as swap.

Installed boot loader on /dev/sdb1

After installating and rebooting getting error 25.

My device.map looks like

(hd0) /dev/sdb # should be my linux drive, acc. to bios boot order
(hd1) /dev/sda # should be my windows drive acc. to boot order

menu.lst initally did not have a root entry under the 3 linux sections. I added them to have 

title ...
root (hd0,0)
makeactive # also was absent, added this

Under Windows section modified to

root (hd1,0)
makeactive # was absent, added

My BIOS boot order is CDROM, Hard Disk
My BIOS boot priority is Linux drive (IDE), Windows drive (SATA)

BIOS and mobo are pretty new (Gigabyte UD3LR) and can handle large drives.

What am I doing wrong? Any help is very much appreciated.

---

### Post by raymondh on 2009-08-10
Hope this helps:

[http://members.iinet.net.au/%7Eherman546/p15.html#25](http://members.iinet.net.au/%7Eherman546/p15.html#25)

Good luck.

---

### Post by running_rabbit07 on 2009-08-10
Grub boot loader has to be on same disk as the MBR.

Edit: +1 with the site Raymond is recommending.

---

### Post by vasya10 on 2009-08-11
Thanks for the replies. I checked my cables, the Linux pata (/dev/sdb) is set to Master, dvd rom is set to slave. All these show up in BIOS correctly. The hdd settings is also Auto (not LBA or large). My BIOS boot order is CDROM, HDD; I changed my BIOS Hard Drive Priority to SATA, then HDD. Sata is where my MBR is.

Tried a few suggestions given else where in this forum --

- boot via livecd, mount /dev/sdb, re-install grub, but it doesnt work.

Here is what i get trying to reinstall grub:

root@ubuntu:/boot/grub# grub-install /dev/sda
/dev/sda: Not found or not a block device.

root@ubuntu:/boot/grub# more device.map 
(hd0)    /dev/sdb
(hd1)    /dev/sda

fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97ab97ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26108   209712478+   7  HPFS/NTFS
/dev/sda2           26109       77824   415408770    f  W95 Ext'd (LBA)
/dev/sda5           26109       77824   415408738+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84401914

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12158    97659103+  83  Linux
/dev/sdb2           12159       14593    19559137+   5  Extended
/dev/sdb5           12159       14593    19559106   82  Linux swap / Solaris

Appreciate any help!

---

### Post by vasya10 on 2009-08-12
Just wanted to add something.. Read somewhere that PATAs must be /dev/hdX and SATAs must be /dev/sdX. But Ubuntu is reading sata as /dev/sda and pata as /dev/sdb. 

Is there something else wrong?

---

### Post by vasya10 on 2009-08-12
Whoohoo. Got it working. I was about to remove ubuntu, did a fixmbr using Windows CD, that didnt work. Was still getting Error 25. I finally decided to  remove the Ubuntu hard disk itself. Noticed that it was using a regular 40pin master/slave (for hdd and cdrom). Changed it to cable-select for one last try. Booted up, before I could blink, Ubuntu was running.

Thanks a lot for help, learnt a lot in just a couple of days.

---

### Post by raymondh on 2009-08-12
well done ... happy ubuntu-ing.

---


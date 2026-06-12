---
title: "Best Filesystem"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by groovywombat on 2005-11-28
I'm going to reformat all of my harddrives, and I was wondering if anyone had some input as to the best filesystems to choose.  I have a 60gb internal IDE HDD, a 160GB internal IDE RAID0 array, and a 250GB external Firewire drive.
I want to be able to read and write to all of them from within ubuntu (like being able to save to another drive, instead of my home directory) but i would also like    one of the internal hdd to be readable in windows (so i can play a few games every now and then and For using Bryce 5 until I can solder a couple new usb ports onto my laptop and use that for bryce)  As well i'd like to be able to drag the external hdd to other friends' computers and copy stuff to and fro.  I'm assuming I'd need to have a FAT32 filesystem on the external and one of the internals.  but even if that is the case, what would be a good choice for the other linux filesystem, and woudl i be able to write to the other fat32 hdds without being in su mode?
thanks

---

### Post by sean.smithson on 2005-11-28
snip

---

### Post by kosmic on 2005-11-28
Hum the external drive has to be FAT, and yes you can write to anydrive without becoming superuser (root) or using su, in FSTAB just add the line 'users' and 'umask=000'
 
About the filesystem any that use journaling is good ext3, ReiserFs, XFS, etc, ext3 is a very good filesystem and very well tested.
 
 
What I think you should do is when come to the partition menu in Ubuntu install choose to use LVM (in case later you want to add another drive or to aument, decrease the space ocupied by linux, is very easy using LVM).
 
 
Attention - for you to boot using LVM you need to have the /boot partition outside of the LVM discs, otherwise Grub can't Initialize
Make a parititon with +/- 100MB for /boot using ext3 or ext2.

---

### Post by groovywombat on 2005-11-28
Thanks i really appreciate all this help.  I'm not reinstalling ubuntu as it is already installed on a 45gb hdd.  But i guess that helps answer m question of whether or not I have to use the FAT FS on the external.  But it's good to know i don' have to use it for the RAID array.

---

### Post by Adrian on 2005-11-28
I'm using this for sharing an ext3 drive between Ubuntu and Windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Works fine.

---

### Post by sean.smithson on 2005-11-28
snip

---

### Post by RiTarDid on 2008-01-22
> **kosmic said:**
> Hum the external drive has to be FAT

I'm using ntfs on all my external storage, as my ubunut is mainly just a samba share for the family's XP boxes...works great and is better performing than FAT....just go "sudo mount /dev/*devpath* /media/*drivename* -t ntfs".

---


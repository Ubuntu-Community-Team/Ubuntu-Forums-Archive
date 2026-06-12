---
title: "Remove Windows Partition"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by AutootuA on 2009-10-08
I have a dual boot system and I no longer need Windows. How do I remove the dual boot option and how can I remove the NTFS partition and then include the extra drive space in sda5?

[IMG]http://i47.photobucket.com/albums/f198/AutootuA/Screenshot-1.jpg[/IMG]

---

### Post by pmlxuser on 2009-10-08
you can do that use the live disk, so that your hard disk is not mounted..

1. back up your data
2. boot with live cd
3. open gparted
4.delete windows partion
5. move parttion to wards the end 
6. add parttion to partition you want

Note: you might need to reinstall grub () because high posibility its installed in the windows partition MBR....

---

### Post by jeremyswalker on 2009-10-08
I have to say, pmlxuser is right. However, be prepared. In my experience, such a task as you are about to attempt takes a *looong* time.

---

### Post by oldfred on 2009-10-08
If you delete the first partition all the others will likely get renumbered. If so, be prepared to edit menu.lst & fstab to get it working again. If partitions are renumbers you will have to reinstall Grub.
It would be easiest just to use the partition for more data.

---

### Post by mick55 on 2009-10-08
Hi

You can grow a partition to the right but not to the left.
You cannot move the start of an ext3 filesystem.

Looking at your partition info,here are the steps 
you will need to take.

1.boot to live cd
2.Run gparted from live cd
3.Shrink Linux partition /dev/sda5/ to about 70GB
4.delete partition /dev/sda1/,leave as unallocated space
5.copy Linux partition /dev/sda5/ to the unallocated space
6.delete partition /dev/sda5/
7.delete /dev/sda6/
8.grow new Linux partition to the right to use all but 1GB of the unallocated space
9.create a swapfile in the 1GB unallocated space 

you will need to edit your menu.lst or reinstall grub when this is complete.

good luck
mick

---


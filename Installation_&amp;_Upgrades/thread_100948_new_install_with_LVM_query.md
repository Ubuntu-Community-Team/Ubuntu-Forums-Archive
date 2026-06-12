---
title: "new install with LVM query"
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by fsman on 2005-12-08
I've got two hard disks and LVM configured so that /home can span my two disks with ease.

First HD was configured with LVM at install time
/Ubuntu/root LVM
/Ubuntu/swap_1 LVM
/Ubuntu/home LVM

Then I did pvcreate /dev/hdb
lvextend -l 64855 /dev/Ubuntu/home - extended home to scan both disks

then used the livecd using "resize2fs" to reallocate /home

Problem is I'm worried that I have done something wrong as I get the following error "Disk /dev/hdb doesn't contain a valid partition table" when I do

paul@Paul:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 31 248976 83 Linux
/dev/hda2 32 14593 116969265 5 Extended
/dev/hda5 32 14593 116969233+ 8e Linux LVM

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table
paul@Paul:~$


Is everything OK?
Do I need to mount hdc somehome

I'm new to LVM and nervious (this is my second clean install with LVM)

---

### Post by tonym on 2005-12-09
What you appear to have done is use the whole of /dev/hdb as your physical partition,  without partitioning the disk first.  Thus there is no partition table.

Whilst this may work it usually isn't a good idea.  Rather, partition the disk and create one big partition spanning the whole disk then use this as your physical volume.

However,  as you have already done it you can probably live with it and ignore the messages.

Regards

Tony

---

### Post by fsman on 2005-12-19
what do I need to do to correct this?

---

### Post by fsman on 2005-12-20
got there in the end.
had to use a live cd

resize2fs # reduced the filesystem
lvreduce

well I muddled through. hope the following helps. Its my notes - but I was doing it trial by error so it will hopefully serve as a starting point for others.

Remove data from old disk see . [http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html](http://www.tldp.org/HOWTO/LVM-HOWTO/removeadisk.html)

$ vgreduce Ubuntu /dev/hdb # removes disk from the volume group

 

Then add back the disk see [http://www.tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html)

$ fdisk /dev/hdb

Device contains neither a valid DOS partition table, nor Sun or SGI

disklabel Building a new DOS disklabel. Changes will remain in memory

only, until you decide to write them. After that, of course, the

previous content won't be recoverable.

 

Command (m for help): n

Command action

   e   extended

   p   primary partition (1-4)

p

Partition number (1-4): 1

First cylinder (1-1000, default 1):

Using default value 1

Last cylinder or +size or +sizeM or +sizeK (1-1000, default 1000): 

Using default value 1000

 

Command (m for help): t

Partition number (1-4): 1

Hex code (type L to list codes): 8e

Changed system type of partition 1 to 8e (Unknown)

 

Command (m for help): w

The partition table has been altered!

 

$ pvcreate /dev/hdb1

pvcreate -- physical volume "/dev/hdb1" successfully created

 

$ vgextend Ubuntu /dev/hdb1

 

Then extend and resize the logical volume see [http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://www.tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

 

$ lvdisplay # note size of space to increase LV (note use –help use –l or –L)

# lvextend -L+1G /dev/Ubuntu/home

   # resize2fs /dev/Ubuntu/home

---


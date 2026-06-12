---
title: "Is this partion of my harddrive well prepared for installation of Ubuntu?"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by Physicist on 2006-01-29
[IMG]http://static.flickr.com/11/92816662_212e6cd715_o.png[/IMG]

Is this partition good and prepared for an installation of Ubuntu?

This is a screenshot from a PartitionMagic 8.0, Chinese version.

In the last column: 
``&#20027;/&#36923;&#36753;'' means  means ``primary/logic partition''.

I wander wheather the `` primary/logic partition'' assignments now are OK.

---

### Post by DoorGunner on 2006-01-29
I am curious about where you intend to put it. Currently you have a lot of NTFS and some Fat and CPM/DOS........

What i generally recommend to people is to make some freespace rather than manually partitioning for Ubuntu.....that way when you come to the partition protion of the installation you just tell it to use freespace. Ubuntu will sort itself out appropriatelly.

Hopefully this helps you.

---

### Post by towsonu2003 on 2006-01-29
I can't understand much (I don't use partition magic) but you don't have any linux native partitions (reiserfs, ext3, ext2 are some). you also don't have a linux swap partition. I also don't think you have free space (i.e. hard disk space that is not partitioned) to create new partitions without resizing others. 

backup everything before you install ubuntu or partition the drive.

try the live cd first to make sure ubuntu behave nicely to your hard drive.

this reading should be helpful: [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

---

### Post by Physicist on 2006-01-29
Could I install Ubuntu in H: and make I:: my swap? Do I have to have a free/unpartitioned space before installing Ubuntu? This partitioning is made when I install WIndows a few weeks ago when I don't have Ubuntu CD. How could I avoid unnecessary hassles?

---

### Post by az on 2006-01-29
They would be hdb4 and hdb5.  The best way to avoid a hassle is to boot the installer, go into manual partitioning, delete hdb4 and hdb5, then scroll down to "guided partitioning" and let it recreate those partitions for you.  It may resize them depending on how much memory you have and so forth.

That would be the most straightforward way I know.  

Otherwise, you would have to go to manual partitoining and select the hdb4 and make it your root "/" partition and then make hdb5 your swap.  It would just seem to me to be fewer keys pressed to delete them and let guided partitioning do the magic.

---

### Post by towsonu2003 on 2006-01-29
[QUOTE=Physicist]Could I install Ubuntu in H: and make I:: my swap? Do I have to have a free/unpartitioned space before installing Ubuntu? This partitioning is made when I install WIndows a few weeks ago when I don't have Ubuntu CD. How could I avoid unnecessary hassles?[/QUOTE]
nope... you will need a partition with native linux filesystem + a linux native swap (both). your partitions are too personalized for me to give any suggestions... did you scan a little bit the link in my previous post? check this one as well [https://wiki.ubuntu.com/HowtoPartition](https://wiki.ubuntu.com/HowtoPartition) you will need to do some reading as you'll be dual booting. 

what I can see is you will have to resize (or delete) one or more ntfs partitions to get space.

PS. just a reminder: **back up your data!** :) ;)
PS2. another reminder: you might want to defragment the partitions you wanna resize with windows in safe mode once or twice.
PS3. to my understanding, you were asking whether you could install linux to an ntfs partition, which is no. if I misunderstand you and you wanna delete H and I, what are their sizes?

---

### Post by Physicist on 2006-01-29
By hdb4 and hdb5, what do you mean? H: (NTFS) and I: (NTFS) or K: (FAT) and H: (NTFS), if later, what shall I do to I: ?

---

### Post by mips on 2006-01-30
Delete H & I partitions to give you a single large freespace area. When you do the ubuntu install select the freespace and let ubuntu automatically partition that space for you.

---

### Post by az on 2006-01-30
[QUOTE=Physicist]By hdb4 and hdb5, what do you mean? H: (NTFS) and I: (NTFS) or K: (FAT) and H: (NTFS), if later, what shall I do to I: ?[/QUOTE]
On the image, you seem to have two hard drives.

Linux uses a more accurate way to name hard drive partitions.

The master on the primary ide is hda, the slave is hdb.  The master on the secondary ide is hdc, and the slave is hdd, and so on...

Each partition has a number - extended partitions count for one, so you han have more partition numbers than you actually have partitions.

The second partition on your primary ide's slave drive would be /dev/hdb2, for example....

Anyway, you are going to get rid of the filesystem when you install ubuntu - it will format it for you, so it is irrelevant that it is currently NTFS.

---


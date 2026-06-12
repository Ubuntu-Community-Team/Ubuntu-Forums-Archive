---
title: "Do I need a seperate partition?"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by trav1085 on 2005-12-30
I'm going to install Ubuntu, but need to know if I need a seperate partition for it, becuase I have Windows XP and want to keep both OSs on it, I know there is an advanced mode that can keep the files but wan't to know if I need a seperate partition, I have PartitionMagic.

Do I need a Linux partition, like Ext2 or an unformatted partition.

---

### Post by TransitMan on 2005-12-30
I made a new partiton with the Partition Manager in Ubuntu.
It was quick and painless. 
My WinXP is still there, and works in dual-boot.

You should have no problems with this partitioner.

However, before you do, you will want to do a defrag on the XP, so that all the files are in proper order and not leaving any empty sectors.

You may also want to disable or decrease your swap file in XP to a bare minimum too.

Good luck.

---

### Post by KEMitchell on 2005-12-30
[QUOTE=trav1085]need to know if I need a seperate partition for it[/QUOTE]
Yes, you will need a new partition

> Do I need a Linux partition, like Ext2 or an unformatted partition.

I dual boot XP and Kubuntu, with the following setup (in order):

Primary Partitions:
   40 gigs NTFS - Windows
   100 megs - /boot
   1 gig - linux swap

   Logical Partitions:
      20 gigs ext3 (ext2 works too!) - linux root /
      remainder: vfat shared partition

You may or may not have a 100 gig drive as i do, but those sizes have proved more than sufficient
The shared partition is completely a matter of preference. I use one to dump some music on and share settings for common apps like the mozilla suite, but in the end it really isnt necessary. Drivers exist in Windows to read ext2 partitions, and linux has read (NOT write) support for NTFS.

Special Note: Some prefer to run windows on VFAT so that they can do the read/write operations on their windows partitions from within Linux. Again, if you prefer (or already have) NTFS there is no need to change...

Check your Windows Drive first to make sure that it is (1) defragged and (2) not filled with more stuff than you intend to give it space to hold.


Good luck!
Post more questions/details!

---

### Post by az on 2005-12-30
[QUOTE=trav1085]

Do I need a Linux partition, like Ext2 or an unformatted partition.[/QUOTE]

Yes, you need a seperate partition and it would be best to leave it as free space, if you insist on using third-party tools.  Partition magic does not handle linux filesystems very well.


Considering that a big percentage of linux users originally dual-boot with windows, the installer (which can safely partition a drive with an NTFS filesystem on it) is probably responsable for a lot more partitioning than any other partitioning tool out there.  Most people use it and it is very safe.

Always backup your data.

Just boot the installer and follow the instructions.  It will offer to shrink your current partition down.  All you have to do it tell it how big.  

The installer runs in text mode (text menus, actually) but is very very safe and straightforward.

---

### Post by trav1085 on 2005-12-30
I created a partitions for Ubuntu, instead of explaining it all and writing a paragraph I just took a screenshot of my partitions

[http://ca.geocities.com/trav1085/pictures/partitions.jpg](http://ca.geocities.com/trav1085/pictures/partitions.jpg)

---

### Post by az on 2005-12-30
W00t!

Actually, I would tell the installer to delete it and let it repartition the free space using "guided partitioning"  That way, it will create a swap partition for you withou you having to do all the work.

You need another partition for virtual memory - It is called a swap partition.  Let the installer make it as big as it thinks is best.  Please do not ask anybody how big your swap should be.  Touchy subject. (Because nobody is wrong) :)

---


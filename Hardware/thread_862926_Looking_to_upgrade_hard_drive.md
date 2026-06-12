---
title: "Looking to upgrade hard drive"
date: 2008-07-18
forum: Hardware
---

### Post by kroon78 on 2008-07-18
I want to swap my current 60GB IDE out and put in a 320GB I have.  I'm putting the 60 in an old computer so having two drives is out of the question.  What is the easiest way to upgrade hard drives and keep all your data and settings?

Thanks

---

### Post by logos34 on 2008-07-18
[Partimage]("http://www.partimage.org/Partimage-manual_Usage") is probably the fastest (because it copies only the used space).  But if the drive is nearly full, you might as well use **dd** (which copies used and unused)--it has the virtue of being simple, just one command.  Either way you're copying an exact image.  So everything ends up exactly the same, even the partition UUID.

But with Partimage you have to backup the image first to some location (either on the same hard disk, space permitting, or on a second partition on the 320 gb disk), then restore it to the destination/target partition.  Use Gparted to create the destination partition (as close in size the original as possible--one iota smaller and the restore will fail).  If necessary, also make a second partition to temporarily hold the compressed image if it won't fit in your home dir on the source drive.  Then you would boot to the live cd and run it there (root cannot be mounted).  Create a gzip image of root.  Then restore the image to the destination partition.

With [**dd** you just do this]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html") (again from live cd):

ex:

Copy root partition to another hard disk:

> sudo dd if=/dev/sda2 of=/dev/sdb1 bs=4096 conv=notrunc,noerrorOR
 
Cloning an entire hard disk:

> sudo dd if=/dev/sda of=/dev/sdb conv=notrunc,noerrorSame for /home if on a separate partition.

Oh, and [install Grub to the MBR of the new HDD]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck!

---

### Post by kroon78 on 2008-07-19
thanks, i'll give this a try tomorrow, sounds like just what i was looking for

Cheers

Ryan

---


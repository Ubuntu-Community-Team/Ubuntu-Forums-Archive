---
title: "Changing hard disk drive for my laptop"
date: 2011-08-31
forum: Hardware
---

### Post by luchtzak on 2011-08-31
I would like to change the hard drive of my laptop, is it okay that I:

burned a ubuntu startup CD
backed up my files in folder HOME

or should I take other things into consideration?

---

### Post by ajgreeny on 2011-08-31
Why not clone the current disk with clonezilla, and then restore the clone to your new disk?  That way you will end up with a system that is just that; a clone of your current system, with all the added applications and setup exactly as it was on your old, current disk.

[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)

and full instructions on how to do it
[http://clonezilla.org/clonezilla-live-doc.php](http://clonezilla.org/clonezilla-live-doc.php)

---

### Post by luchtzak on 2011-08-31
And does it work for about 400 gigs on my harddrive ?

---

### Post by walt.smith1960 on 2011-08-31
It might be worth checking the disk manufacturer's site.  They might offer some sort of migration software.  I've just done images but I've never had to move 400 gigs.  What I might do with that much data would be to store it in a partition separate from the O.S.  That way you can clone the O.S. and apps, create a separate  /home or data storage partition and just copy files from one drive to another.  A separate partition might simplify backups, too.

---

### Post by gecko55 on 2012-10-27
I would like to do the same thing, that is clone my system to a new hard drive. But I intend to go to a SSD. Does that matter, create new or different considerations for imaging/cloning?

Also, is it necessary to go through an image create, then image restore process, requiring a third hard drive? Or can I can I just clone my current internal hard drive (with dd or Clonzilla) to an external hard drive, then do a physical swap?

---

### Post by ahallubuntu on 2012-10-27
Spend $10 USD on a USB hard drive adapter for 2.5" SATA (laptop) drives; then you can attach both drives to the laptop at the same time (one internal, one USB).

I've been using Gparted lately to clone drives (partitions) - it works pretty well.` Clonezilla may be easier, not sure these days. When I tried it a few years ago when cloning a variety of drives, sometimes it would work perfectly, sometimes it would fail without a good explanation.  If it works, it should be more hands-off.  If it doesn't, you'll have to go and muck with things like re-installing Grub anyway.

To clone with Gparted:

1. attach both drives to computer
2. boot a Ubuntu live CD
3. start up Gparted (if not installed, install it in the live session, so you must be on the internet).
4. create the new partition scheme you want on your new drive (you can make the new partitions larger but not smaller than original size).  Create a new swap partition too.
5. Copy the partitions (except swap) with Gparted - right-click on a partition to copy, right-click on the destination to paste it.
6. Edit your /etc/fstab file to point to the new partitions (use "sudo blkid" to get the new UUIDs of the new partitions, then copy-paste them into /etc/fstab).
7. Re-install grub on target drive - I like the "chroot" method.  Google for it.

You probably don't need to go through that process if Clonezilla works...

---

### Post by gecko55 on 2012-10-27
AHALLUBUNTU

Thanks. I have a USB hardive dock I think I can use for the new SSD, the existing internal drive is already attached, and will be until the new SSD is ready to go.

Your Gparted approach sounds complicated, easy to mess up. I have done this sort of thing before, move to a new or bigger hardrive, but in Windows. I used Acronis TrueImage and it was easy.

I was hoping there was a similar approach in Ubuntu. Gparted does not sound similar, sounds like using Fdisk.

---


---
title: "Putting an IDE HD from an iMac into a PC box question"
date: 2009-10-20
forum: Hardware
---

### Post by mjp29 on 2009-10-20
My mother is very impressed with Ubuntu, as are many of my friends, and considering her old iMac (very old) is so slow [I put a older version of os x on it] and it just runs slow, I promised her I'd find an old PC box or give her one of my 2 old ones and put Ubuntu on it for her.  I have found another old PC which has a Pentium 4 I believe and it also has a crashed HD in it.

I did put a new Seagate HD in her old iMac a year or two ago, which I believe is around 120 gigs in size.  She has digital photos on her iMac, which is the only files she wants to retain.

I think this can be done.  Can I take the IDE HD out of her iMac and put it in the PC desktop box and also put Ubuntu on her 120 gig HD and install Ubuntu as a Partition and retain her digital photo files?

If this can be done, is there a way to get to those files on that partition from the Ubuntu operating system.  Unlike ms windows, I don't think I can force the Mac OS to boot from it's partition on a PC box without doing some hackintosh hacking that I don't have the skills or time to do.

If so, then once I transfer the digital photo files (mostly .jpg) to Ubuntu, can't I then tell Ubuntu to wipe out the old mac os x partition and claim all the space on the HD for just Ubuntu operating system and storage.

---

### Post by mjp29 on 2009-10-24
bump

---

### Post by lensman3 on 2009-10-24
How old is old:  If it OS X then


mount -f ufstype=openstep /dev/sdx# /media/mac


might work.  /dev/sdx# is the drive number that will be used when you mount the Apple disk.  the x will be a letter and the # will be a number.  The man page for OS X, says this is currently read-only.  So you should be able to copy the pictures to the new machine.

If it is the old Mac OS then

mount -f hfs /dev/sdx# /media/mac

hfs is the old mac file system type.

To figure out what the new drive becomes look at the file use the command from a text window: "fdisk -l /dev/sda".  Increment  the sda to sdb to sdc until you see the right partition table.  The number will follow from the partitions that are seen 1 for the first one listed, 2 for the second and so on.

See the man page "man mount" and search for mac and OS X.  Hopefully, Ubuntu compile the hfs or openstep kernel module.  The mount program should be smart enough to load the appropriate kernel module.

---

### Post by mjp29 on 2009-10-24
It is running OS X [very slowly though].

So, would you suggest that I could take the hd out of the iMac, put it in a Pentium 4 box, and install Ubuntu (as a partition I presume) leaving os X and files on the hd, and then I could boot the PC box and access the digital photo files on the partition that is still Mac os x.

---

### Post by viper250 on 2009-10-24
you should have no problem using the drive as the imac and powerpc both use an ide/eide drive.  copy the photos to a thumb drive or transfer files via lan cable to another pc .
you will need a crossover cable to connect the computers directly unless you are using a hub. after saving the pictures you can use the partition editor to erase and rewrite the partition table. 
If you are using this as a primary drive ubuntu install will do this for you, after installation you can copy them back to the  ubuntu machine

---


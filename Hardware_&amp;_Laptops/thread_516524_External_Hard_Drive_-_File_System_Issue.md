---
title: "External Hard Drive - File System Issue"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by StonePiano on 2007-08-03
I have a new Seagate 320 Gb External Hard Drive.

It mounted automatically on my Ubuntu 7.04 machine.  Nice.  I could read and write fine.

The only problem was that it was formatted with FAT32.  So I could only write files smaller than 4Gb.  The main reason I got the file was that I needed to back up and transport larger files.

So I ran fdisk, and got a confusing partition table with overlapping partition boundaries, etc.
```

Command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Total allocated sectors 1701990412 greater than the maximum 625137282

```

I re-wrote a new partition table with one new primary linux partition.  But then it failed to write the new partition table.  (Sorry, I didn't get the error.)

After that, I could not even see the drive with df.  :mad:

So I plugged the drive into an XP machine, and re-formatted it.  XP defaulted to create an NTFS partition.

Then my Linux box could mount and read it, but not write.
When I run fdisk and print the partitions I get this:
```

Command (m for help): p

Disk /dev/sdd1: 320.0 GB, 320070288384 bytes
255 heads, 63 sectors/track, 38912 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdd1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdd1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdd1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdd1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I had wanted to switch the main partition to a linux partition, but there was no way I could work with the partition table.  This is a similar confusing array of partitions as the original FAT32 format setup.
I am now in the process of re-formatting back to FAT32 on an XP box.

Does anyone understand why the partition table looks such a mess (both originally, and after a successful format in Windows)?

Has anyone successfully put a linux partition on a drive like this?

Many thanks,
StonePiano

---

### Post by dannyboy79 on 2007-08-03
Well if the drive said that it had automated backup tools on it and what not than it'll look like that. 

all you have to do is plug in the drive. make sure it's NOT mounted. open Gparted from System, Admin pull down (install from synaptic if you don't have it), then simply delete all partitions on it, hit apply, create a new ext3 partition, hit apply, that's it.

Otherwise, I would write zero's (use dd if=/dev/null of=/dev/blahblah ) [I am pretty sure that it's, gogle it to make sure] to it to properly "shred" the drive so that nothing is on it. MAKE SURE YOU SHRED the correct drive and not your Ubuntu drive. Then use fidsk again. by the way, fdisk is horrible with partition tables. Testdisk can rescue and rewrite proper partition tables.

---

### Post by vmikalinis on 2007-08-03
I think clonezilla might be better than G4U.

---

### Post by StonePiano on 2007-08-03
DannyBoy, you are a genius!

Thanks for the solution.  Gparted is excellent!

Kind regards,
StonePiano

---

### Post by dannyboy79 on 2007-08-03
im not a genious but I do know a few things. Glad you got it. If you're going with ext3, you'll have access to a properly ejected ext3 disc within Windows IF you install the fs-driver program. When I say properly ejected, that means you have to unmount it with umount so that the journal can be written to the drive. If your computer crashes or is shutoff improperly or you pull the usb cord out without ejecting it properly windows using the fs-driver will not be able to open the contents of the drive.

Same goes for NTFS write support in linux. If you don't eject your drive from windows using the safe remove hardware from the lower right corner, Linux won't even be able to see it. This is actually a good thing otherwise you could overwrite something that you didn't mean to. 

Boils down to always eject the disk properly and hwne you don't. Just mount it in it's native OS (ext3 linux and ntfs winxp), then unmount it and you'll be able to use it again.

---


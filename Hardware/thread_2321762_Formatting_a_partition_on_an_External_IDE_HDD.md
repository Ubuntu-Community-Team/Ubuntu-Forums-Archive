---
title: "Formatting a partition on an External IDE HDD?"
date: 2016-04-24
forum: Hardware
---

### Post by cybrsaylr on 2016-04-24
I have and old external IDE 160GB HDD from around 2001, in an enclosure with 4 partitions. It still works fine. Use it for music backup. All partitions are ~40GB. The first partition has XP on it and can be used to boot into XP. Well XP is not needed anymore. Was wondering if this first partition can be wiped clean and formatted, so it can be used for additional storage without losing anything on the other 3 partitons which have music saved as MP3 files. This ext HDD  has thousands of MP3s and I don't want to lose any of them. What is the easiest and safest way to do this?

---

### Post by weatherman2 on 2016-04-24
Use Gparted in Ubuntu to format just the XP partition.   Obviously, be very careful to know which partition was the C: that XP booted from, and check the old \Documents and Settings folder to make sure there isn't any remaining data in Desktop or My Documents that you really wanted to keep.

But of course, any hard drive could fail tomorrow, without warning, especially an older drive, and you could lose everything.  So if you care much about the MP3 files on this drive, you should have a backup of them on some other device.

---

### Post by cybrsaylr on 2016-04-24
Yes this is an old HDD only used for backup. Also have these MP3 files saved on 2 other drives for peace of mind in case one of them fails.

Opened Gparted and found the XP partition I want to format and eliminate. Checked and there is nothing on it needed anymore. However Gparted will not do anything when clicking on 'Partition' other than show; Unmount, Manage Flags and Information. All other options such as; New, Delete, Format to, etc are grayed out and can not be used. Gparted will not let me format the XP partition, or any of the other 3 partitions for that matter on this HDD.

On Gparted, clicked on Device > Create Partition Table, but get a drop down message saying no new partition table can be created because there are 4 active partitions on drive and to unmount them. When they are unmounted, this Ext HDD vanished from Gparted! 

Don't know how to delete/format that XP boot partition?

---

### Post by weatherman2 on 2016-04-24
You will need to unmount the XP partition first before you format it.

DO NOT create a new partition table unless you want to wipe the entire drive!!!

---

### Post by cybrsaylr on 2016-04-24
OK weatherman that worked!

Now Just Format it to whatever I desire?

---

### Post by weatherman2 on 2016-04-24
If you want to use it again with another Windows machine, use NTFS or FAT32.  If you will use it only with Linux, use ext4 (my preference).

NTFS is well supported in Ubuntu now, except that it can be a bit slower when writing files especially - the fuse driver will use some CPU.  But if you will use it on that i7 Dell desktop you shouldn't have any issue.

You could also use FAT32 - probably faster in Linux than NTFS, but you are limited to file sizes of 4.1GB.

---

### Post by cybrsaylr on 2016-04-24
The whole drive was NTFS since I got it just before moving to Linux and due to having a Dell i7 it has never been slow.
Will probably keep it NTFS so it works with Windows machines also.

Once it formats to a new empty partition, is it easy or possible  to merge, expand, resize, or whatever you call this new partition to the next partition which is almost full, without losing anything that is on that second partiton? This would leave this HDD with 3 partitions rather than 4.  Never did this sort of thing before.

---

### Post by weatherman2 on 2016-04-24
You can't really "merge" partitions directly, but you can grow an existing partition from free space (say after deleting another partition). Sometimes it is easy sometimes difficult depending on the partition scheme of your hard drive.

Growing a partition is first complicated - perhaps - if you have an extended partition on your drive (not required if you have only four partitions, but sometimes they get created anyway).  The old MSDOS-style partition table supported a maximum of four primary partitions.  "Extended" partitions were added as a hack at some point to allow more than four.  The "Extended" partition (you'd have only one per drive) is a container inside which you can create as many logical partitions as you wish (within reason).  But you can't grow/merge free space from inside of an extended partition to one of the primary partitions outside of it.   You'd have to do it in a multi-step process of shrinking each one.

If you have only four primary partitions and no extended, then this is all moot.

Still, the best case for growing a partition is when the free space is directly AFTER it on the drive (so you'd delete a partition after the one you are trying to grow).  Then growing it should be quick an easy - probably a 30 second task.  But I'll bet, in your case, the old XP partition was FIRST and the others follow it.  That means if you try to grow one of the other partitions, everything inside the partition must be moved FORWARD, which basically means (even though Gparted would do this automatically) copying everything again, possibly a long, slow process, probably taking hours and hours on an old PATA drive connected by USB.  And if something goes wrong in the middle (drive accidentally unplugged; power outage, just some random error, etc.), you could screw it all up and wind up with a drive that is completely inaccessible.

Although Gparted will grow a partition both ways as I described above, you can't tell how long it will take unless you understand how the growing process works - that's why I tried to explain it.

The safest way to do this is to use a second drive as a staging drive - copy everything off, then format the whole 160GB drive and start over, then copy everything back.  That won't necessarily take a lot less time, but it's much safer.  Any glitch in the middle and you can just start over.  (Use rsync to copy, then if you have to start over it won't re-copy what has already been copied.)

Still, unless you are dead broke, realize that a 160GB PATA (IDE) drive is worth almost nothing today.  My local thrift store was selling them (internal 3.5" drives) for about $5 I think, recently.  And you can buy a USB flash drive almost that big (128GB) for about $30.  Portable 1TB USB drives can be had for under $50.  I am all for keeping and using old equipment, but sometimes it's not worth hours and hours of hassle to skip buying something that will make your life a whole lot easier.

---

### Post by cybrsaylr on 2016-04-24
Yes, the old XP partition was FIRST and the other 3 were in an extended partition. 
So since all it was used for is music storage and given the age of the HDD, will just use it as another partition for storage. 

Right now am using a 128GB Flash drive for backup also. They are amazing and cheap.

Just formatted that XP partition to NTFS. Took about 5 seconds with Gparted.

Thanks for all your help  weatherman.

---


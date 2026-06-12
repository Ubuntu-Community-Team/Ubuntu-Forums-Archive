---
title: "External Hard Drive Trouble"
date: 2012-01-04
forum: Hardware
---

### Post by LiamOS on 2012-01-04
Using Ubuntu 10.04 amd64.
I have an external hard drive that has the same files and folders as would be found on a Live CD(How it came to be that way is an open question, but it has a hilariously stupid answer, I'm sure).
I've tried deleting files through a file browser, but nothing comes of that. Also, I've tried to reformat it through System > Administration > Disk Utility, but it always gives the message that the drive is busy.

Does anybody know of a way to reformat hard drives in a more forceful way or something else which might help?

Thanks.

---

### Post by lindsay7 on 2012-01-04
Download an ISO image of Gparted from their website and burn it to a cd.  It will start up when you have it in a cd drive and open the program.  You can then format or partition all of the drives on your computer.  The good thing about using the Gparted cd is that all of the drives are unmounted so you can work on any of them.

---

### Post by madvinegar on 2012-01-05
Is this external hard disk your main OS hard disk? If not, when you go to disk utility you must unmount it first and then perform a format.

Otherwise you can boot from a live CD, and again use either disk utility or gparted to format the drive.

---

### Post by LiamOS on 2012-01-11
I've managed to format the disk, but I am consistently getting an error when I attempt to create a FAT partition(I get the error when attempting NTFS, etc. too).
The error details are as follows:
> Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdd, start=0, size=750156374016, type=0x0c
Entering MS-DOS parser (offset=0, size=750156374016)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
Warning: Device /dev/sdd has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed


Any ideas?

---

### Post by lindsay7 on 2012-01-15
Use Gparted and under device, pick create partition table. This will clean up the hard drive, then you can format it and partition it like a new drive.

---

### Post by LiamOS on 2012-02-02
GParted worked delightfully. Took me some time to procure a CD, but thanks for the help!

---


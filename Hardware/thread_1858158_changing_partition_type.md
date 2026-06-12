---
title: "changing partition type"
date: 2011-10-11
forum: Hardware
---

### Post by skvaditya on 2011-10-11
Hi
I am using ubuntu 10.10. I am having two hard disks 160Gb and 250Gb. My ubuntu is installed in 160Gb hard drive and 250 Gb I use only to store data. I was changing partition type using disk utility and by mistake I selected "linux extended" and now when I am trying to change it back to ext4 or NTFS I am not getting the option in disk utility to change it back. 
Please help me to change my partition back to ext4 or NTFS.

Thanks in advance
Adi

---

### Post by ajgreeny on 2011-10-11
You can not change the partition from extended to ext4 without deleting it or reformatting it.  An extended partition is not a partition with its own filesystem, but a wrapper for other partitions, each of which will have their own filesystem.

So select the extended partition and choose to make a new logical partition within it.  This new one can take the whole of the extended partition if you wish, or you can make several logical partitions if you prefer with a different filesystem on each, eg ext4, ntfs, fat32.

Should you ever need to install windows on that disk, bear in mind that you will have to do so in a primary partition as you can not boot windows from a logical partition.  Linux can boot from either type.

---

### Post by skvaditya on 2011-10-12
Thank you for the help, but now I have a new issue. When I restarted my PC this morning, I am not able to view my 250Gb partition in places. In disk utility I can see it. It is showing whole 250GB as unallocated space and if I am trying to create new partition assuming my data is gone, I am not able to do so. Its giving the following error.

> Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=33280, size=250059316736, type=0x83
Entering MS-DOS parser (offset=0, size=250059350016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 250056705024, type 0x85)
Entering MS-DOS extended parser (offset=32256, size=250056705024)
readfrom = 32256
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
Error: Invalid partition table on /dev/sdb -- wrong signature 0.
ped_disk_new() failed
 I am attaching the screenshots of the result of disk utility. Please help.

Thanks in Advance
Adi

---

### Post by ajgreeny on 2011-10-12
Are you saying there was data on that disk that is now gone, as you did not mention that in your original post?

If that is correct I suggest you try installing and running **testdisk** from a live CD to avoid any possibility of using that problem disk for the moment.  I have never used it personally bit there are plenty of references to its use in these forums which might be of use to you, so do a search and see if it helps you any further.

---


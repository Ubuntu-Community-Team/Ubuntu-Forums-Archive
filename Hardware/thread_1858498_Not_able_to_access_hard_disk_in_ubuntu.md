---
title: "Not able to access hard disk in ubuntu"
date: 2011-10-12
forum: Hardware
---

### Post by skvaditya on 2011-10-12
Hi
I am using ubuntu 10.10. I am having two hard disks 160Gb and 250Gb. My ubuntu is installed in 160Gb hard drive and 250 Gb I use only to store data.Yesterday I was changing partition type using disk utility and by mistake I selected "linux extended".
When I restarted my PC this morning, I am not able to view my 250Gb partition in places. In disk utility I can see it. It is showing whole 250GB as unallocated space and if I am trying to create new partition assuming my data is gone, I am not able to do so. Its giving the following error.
 
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
 
I posted this error in reply of my own previous post. I had attached screenshots of the disk utility over there. 
[URL="http://ubuntuforums.org/showthread.php?t=1858158"][HTML] 
http://ubuntuforums.org/showthread.php?t=1858158
[/HTML][/URL]
 
Please help me how to retrieve my data back again.
 
Thanks in Advance
Adi

---

### Post by WasMeHere on 2011-10-12
Hi Adi,

I read your post
> **skvaditya said:**
> Hi
I am using ubuntu 10.10. I am having two hard disks 160Gb and 250Gb. My ubuntu is installed in 160Gb hard drive and 250 Gb I use only to store data.Yesterday I was changing partition type using disk utility and by mistake I selected "linux extended"....
I will try to help you, but I am afraid it will be very difficult to restore your disk back to before you made an extended partition. As stated by *ajgreeny* repartitioning is not reversible.
> **ajgreeny said:**
> You can not change the partition from extended to ext4 without deleting it or reformatting it.  An extended partition is not a partition with its own filesystem, but a wrapper for other partitions, each of which will have their own filesystem.

So select the extended partition and choose to make a new logical partition within it.  This new one can take the whole of the extended partition if you wish, or you can make several logical partitions if you prefer with a different filesystem on each, eg ext4, ntfs, fat32.

Should you ever need to install windows on that disk, bear in mind that you will have to do so in a primary partition as you can not boot windows from a logical partition.  Linux can boot from either type.
1. In general, you should *always backup your data before* changing or formating partitions, because it is risky business!

2. There are tools to try to restore the previous partition table, but I have no experience of such tools myself. You may get help from someone else or find out via the internet.

3. There are tools to recover files without having a proper heading of the partition (partition table and pointers to the files). One of these tools is ***Photorec***. It was originally intended for recovery of photos on flash drives with destroyed file allocations tables, but now it has developed into a general tool to get back files, as long as the file data is not overwritten, so

4. Avoid writing anything to your disk!

I suggest that you browse the internet to find information and tutorials about Photorec and prepare carefully to get files back!

Good luck :-)
Olle

---

### Post by skvaditya on 2011-10-13
Thank you Olle for you idea of searching tool on google. I searched and found a tool gpart and with that I was able to resolve my issue. 
 
Thanks & Regards
Adi

---

### Post by WasMeHere on 2011-10-13
> **skvaditya said:**
> Thank you Olle for you idea of searching tool on google. I searched and found a tool **gpart** and with that I was able to resolve my issue. 
 
Thanks & Regards
Adi
Congratulations :-({|=

Please mark the thread SOLVED

Olle

---


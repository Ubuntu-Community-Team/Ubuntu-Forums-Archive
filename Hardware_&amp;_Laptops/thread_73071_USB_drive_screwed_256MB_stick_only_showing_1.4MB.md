---
title: "USB drive screwed: 256MB stick only showing 1.4MB"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by swerner on 2005-10-08
I have a what used to be 256MB USB stick and now it only shows 1.4MB. I can successfully mount and read/write files from/to it. I can use fdisk create and delete partitions, however none can be larger than 1.4MB. Here is the fdisk -l /dev/sda output when there are no partitions allocated:

    Disk /dev/sda: 1 MB, 1474560 bytes
    1 heads, 3 sectors/track, 960 cylinders
    Units = cylinders of 3 * 512 = 1536 bytes

    Device Boot Start End Blocks Id System

I should be able to change the number of heads and cylinders using fdisk, has anyone done this before? Any other suggestions?

---

### Post by jasmuz on 2005-10-08
The example below assumes your USB device is on /dev/sda1 or /dev/sda.

   Usually USB devices come preformatted with a FAT16 partition.

   It's not strictly necessary to create a partition on the USB device,
   you can just put a FAT16 or FAT32 filesystem on it "mkdosfs -I -F 16
   /dev/sda" or "mkdosfs -I -F 32 /dev/sda".

   If you use FAT16, the USB device can't be more than 1 GB.

   Create a FAT16 (type 6) or FAT32 (type b) partition on the USB drive,
   if not already.

# fdisk /dev/sda
Command (m for help): p

Disk /dev/sda: 128 MB, 128974848 bytes
4 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System

Command: n  "Create new partition!"
p           "Create primary partition!"
Partition number (1-4): 1
First cylinder: (enter for default) "Use the whole drive, otherwise it may not boot
Last cylinder:  (enter for default)  
Command: t
Hex code (type L to list codes): b
Command: a  "Make partition #1 active!"
Partition number (1-4): 1
Command: p

Disk /dev/sda: 128 MB, 128974848 bytes
4 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 248 * 512 = 126976 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1015      125829    b  FAT32

Command: w  "Write table to disk and exit!"

   Format the USB drive with a FAT filesystem.

   # mkdosfs -F 32 /dev/sda1  "It only works with FAT12/16 or FAT32!"

---

### Post by swerner on 2005-10-08
Thank you for your detailed reply, but I think you miss-understood my question.  I am quite familar with creating such a partition table.  However, my USB stick is unable to be partitioned any larger than 1.4MB at the moment. It used to be 256MB.  That means that even if I try to create the largest single partition when the USB stick's partition table is empty I cannot create a partition larger than 1.4MB.

I think playing with the heads/sectors/cylinders will do something.  Looking at your example above I see that your setup is 4/62/1015 for 128MB, so I tried 8/62/1015 to try to create a 256MB partition, but this did not work.

Any ideas? I will try another couple of combinations.

Cheers,

---

### Post by jasmuz on 2005-10-08
No ideas, if worse comes to worse...then you will have to Windoze and repartition & reformat the drive.

---

### Post by swerner on 2005-10-09
I think it's like this because of Windows.

---

### Post by swerner on 2005-10-15
Actually I found out it was my fault.  I had turned on write protection!!! For some reason this will show a 1.44MB drive.  Now it shows /dev/sda and /dev/sdb like it used to.  Does anybody know why the write protect switch will do this?

---


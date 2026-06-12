---
title: "Can't Write to Vertex 2 in Ubuntu"
date: 2010-08-21
forum: Hardware
---

### Post by Confucius! on 2010-08-21
My 120 GB Vertex 2 just arrived yesterday. First i aligned the partition  (sudo fdisk -H 32 -S 32 /dev/sdx) and started the first cylinder at 2.  Then I made it a ext4 filesystem (sudo mkfs.ext4 /dev/sdx1). Next I  mounted the the drive and tried to create a folder on it. The create  folder is grayed out and I cant seem to write to the drive. I checked  that it is mounted as RW. I have tried both Ubuntu 10.04 and 10.10 Alpha  3. I have also tried making it a ext2 filesystem with no luck. I am  getting Failed "command: Flush Cache" and "status:{DRDY} when i try to  shutdown Ubuntu 10.04. The shutdown also takes way longer then what it  should.  I have read that SSD have issues with EVGA 780i MB which is  what i have. Could it just be that my MB does not support SSD drives?  Thanks for you help in advance.[IMG]http://www.ocztechnologyforum.com/forum/images/smilies/chit.gif[/IMG]

---

### Post by Confucius! on 2010-08-21
I just tried it in Windows 7 and it seems to be working. Any Ideas why it is not working in Ubuntu. I would really like to keep it as a ext4 FS and not a NTFS.

---

### Post by Confucius! on 2010-08-21
Seems like there is an issue with the heads and sectors being 32. I am  not really sure what the issue is because it seems to work with other  people. I did see a suggestion to use 224 Heads and 56 sectors. Is this a  good option to use? if so do I still need to start the first cylinder  at 2? Or should I just use how windows 7 alignment and change it to a  ext4 FS. Windows 7 alignment is 240 Heads and 63 sectors. 

120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3480c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       15506   117218304    7  HPFS/NTFS


120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3480c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048   234438655   117218304    7  HPFS/NTFS

---

### Post by Ruhani04 on 2010-10-29
I know this is a very old thread but I thought I give a little input from my side as I have been using vertex drives for a while.
To get the drives aligned I use gparted on a boot CD.
All you have to do is leave the first MB free and make sure that the box for "align to cylinders" is unchecked when creating a new partition. You can also google this to find these instructions in greater detail. 
After that you can use gparted to create your desired filesystem.
I found this the easiest way to get a properly aligned partition for a ssd drive.
\\:D/

---


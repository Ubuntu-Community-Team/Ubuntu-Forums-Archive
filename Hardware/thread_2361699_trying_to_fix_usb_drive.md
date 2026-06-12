---
title: "trying to fix usb drive"
date: 2017-05-19
forum: Hardware
---

### Post by jgw on 2017-05-19
I have a problem with a thumb drive (got errors).  There is nothing on the drive I want.  I thought I would goto gparted and remove the partition and start over.  When I try and look at it with gparted it blows up gparted.  I have tried a lot of stuff to no avail.  Sometimes it tells me I have a read only file system and sometimes not. I did a little searching and tried:

Identify it:
sudo fdisk -l
Disk /dev/sdc: 125 GiB, 134217728000 bytes, 262144000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x67d70445

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1        2048 262143999 262141952  125G  c W95 FAT32 (LBA)

format it:
sudo mkdosfs -F 32 -I /dev/sdc1
mkfs.fat 3.0.28 (2015-05-16)

look at it with nautilus and get:
Sorry, could not display all the contents of &#8220;usb-Generic_Flash_Disk_52B2B4C7-0:0-part1&#8221;: Error when getting information for file '/mnt/usb-Generic_Flash_Disk_52B2B4C7-0:0-part1/System Volume Information': Input/output error

Thoughts?

---

### Post by TheFu on 2017-05-20
Thumb drives fail.  Could it be dead?
Not all thumb drives are compatible with all USB controllers.  Try a different controller, see if that helps.

---

### Post by jgw on 2017-05-20
Thanks for the reply.  tried it on three different machines to no avail.  Its probably dead.  My problem is that i'm cheap and this is a 128gb flash drive (i only bought it to see if it actually worked)  Guess I have my answer.  I am going to mark this as solved.  I remember the good old days when you could submit stuff to a transformer field and just wipe away everything and start over.

---


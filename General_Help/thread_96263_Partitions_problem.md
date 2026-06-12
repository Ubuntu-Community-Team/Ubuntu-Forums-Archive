---
title: "Partitions problem"
date: 2005-11-28
forum: General Help
---

### Post by Daminator on 2005-11-28
I am having trouble creating the FAT32 partition I have planned at the end of my drive.

Currently, I have:
hda1 - NTFS - 10,498MB - Main XP partition
hda2 - NTFS -  3,499MB - XP Swap file partition
hda3 - ext3 - 10,017 - Ubuntu main partition
hda4 - extended partition - 1,906
-hda5 - linux-swap - 1,906
unallocated - 50,391

I want all of that unallocated space to be FAT32 so that it's accessible by both Ubuntu and XP, but I don't seem to be able to put anything in there now. I thought that I could just slot another partition into that extended partition, but nothing seems to be letting me do it. Not Ubunto, not XP, not Knoppix.
Is there a way to do this? Please don't tell me that I have to format everything AGAIN????

How can I extend the extended partition so that I can slot the FAT32 drive at the end?

If that's not possible, is there a way to delete the extended and the swap, then put them back (along with the new FAT32 drive) without breaking everything?

Please help.

---

### Post by Bachstelze on 2005-11-28
Run system > administration > disks

You could be allowed to format your unallocated space as a new fat32 partition from here.

---

### Post by ecobuntu on 2005-11-28
you can always use fdisk...i know this is a little scary but...
sudo fdisk /dev/hda
--then try to create a new partition

---

### Post by Daminator on 2005-11-29
Neither of these two options are working

Is there anything I can do?

Is there a way to delete the extended partition (along with the swap partition), then try to build them again (this time with the FAT32 too), without breaking linux?

---

### Post by Daminator on 2005-11-29
Tried the latest version of Partition Magic in XP - it didn't like it

Tried booting with a Win98 bootdisk and using FDISK - it didn't like it.

I think I need to:

1) delete both the Linux swap partition and the extended partition
2) make an extended partition the size of the whole of the rest of the disk
3) make a new linux-swap partition in that space
4) make the new FAT32 partition in that space.

The problem is that I do not know how I can do all of the above without breaking everything!!

---

### Post by Daminator on 2005-11-29
If I delete the extended partition from DOS (using Win98 boot disk and FDISK), then rebuild the extended partition to take up all of the space available.
Then boot into Linux with a 'LiveCD' and make a 'Linux-Swap' partition and a FAT32 partition within the new extended partition .... should that work???

Will Ubuntu just use the new swap drive like nothing's changed?

What happens to Ubuntu if I mess up the Swap drive?

---


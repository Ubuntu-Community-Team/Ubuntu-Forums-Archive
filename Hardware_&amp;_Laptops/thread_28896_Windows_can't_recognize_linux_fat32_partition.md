---
title: "Windows can't recognize linux fat32 partition"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by moose6589 on 2005-04-22
Hi, 

Recently, I have been trying to create a new fat32 partition for sharing files between Windows and Ubuntu. I used Ubuntu, installed gparted, and used that to create a 2 GB fat32 partition that was previously space from my NTFS volume. So, now I have a large ext3 partition, a large NTFS partition, and a 2GB fat32 partition, which is what I want, and Linux can see all 3 and write safely to the ext3 and the fat32. 

Now, the problem is that when I log back into Windows, it doesn't recognize the 2GB fat32 partition! The fat32 partition is not listed as a drive in My Computer, and when I go to disk management, it lists the 2GB fat32 partition as unknown. It shows the correct amount of free space, so I know Windows can see it, but why is it listed as unknown? I also can't take any actions with the fat32 drive except delete, so I can't set drive letters or anything like that either. 

I have attached a screen of the disk management to clarify things.

---

### Post by andvaranaut on 2005-04-22
hi,

I think that the problem is that the partition type is not set correctly. Partitions have an identification telling the system the kind of filesystem that is (should be) in them. So, if you format a partition as FAT32 but don't mark it as such, Windows won't like it.

The solution is using fdisk to change the partition type. WARNING, fdisk can be dangerous to your data, so use it with care!

First type 'mount' in a terminal to know what partition your fat32 filesystem is in (in case you don't know). It will (most likely) be /dev/hdaX, with X=a number. (If it's hdbX or something else, substitute it in the following discussion).

Then use: ** sudo fdisk /dev/hda ** (only hda, without the X). If it complains about not being able to find fdisk, try ** sudo /bin/fdisk /dev/hda **.

The fdisk prompt should appear. Type 'p' and Enter to print the partition table. You will see a series of lines. The important fields for you are the first and the last. Locate your fat32 filesystem (that's when you need the number X) in the first field and check to see which 'System' (last field) is listed. If it does not have FAT32 in it's name (ie. it reads Unknown, Linux, or something like that), you have found your problem.

Type t and enter to change the offending partition type. Fdisk will ask you for the partition number. Type the "X number" and Enter. Then, fdisk will ask you for the partition code. You can type L and Enter to see a list. I have found that *c* (a single c and Enter), 'W95 FAT32 (LBA)" works well for me, so if you don't know which type to choose, try with c.

Then type w and Enter to write the changed partition table to disk. Reboot in Windows and see how it goes.

If you make a mistake with fdisk, type q and Enter in the prompt to exit without saving your changes. The changes are not written to disk until you type w and Enter, so there's no need to panic if you accidentally use the wrong key.

Hope this helps. Cheers

---

### Post by BAshworth on 2005-04-22
Or you can do it through Windows by going to Administrative Tools -> Computer Management -> Drives (something like that) select the partition, and then format it.

Sometimes Windows wants more than just a designation flag for drive format, it wants the record that it did the formatting.

---

### Post by hypermorphism on 2005-05-09
I had this problem as well, with a FAT32 partition and my linux partition on an SATA drive. Another method is to use gparted to remove the FAT32 formatting and leave it as free space, then go to WinXP's control panel > Administrative Tools > Storage. Then use the proper storage tool to format the unformatted free space as FAT32.  For some reason, leaving it as the linux Fat32 and booting into windows didn't allow me the option of formatting it.

---


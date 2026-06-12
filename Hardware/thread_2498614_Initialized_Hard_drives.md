---
title: "Initialized Hard drives"
date: 2024-06-21
forum: Hardware
---

### Post by mwatkins-wfvp on 2024-06-21
I have a PC that is dual-boot Ubuntu 22.04 and Win11. Two (ext4) /dev/sdb and /dev/sdc HDs in the PC were initialized by Win11. Now they both have 17MB partitions sdb1 and sdc1 labeled "microsoft reserved" with a second volume 4TB unallocated space. I have not written anything to them. I have tried testdisk and it shows several superblock entries. But when I run the fsck.ext4 cmd with the superblock info, I receive a "the drive is in use".


So I booted a live disk, and ran testdisk but I get the same msg. I have tried umount, blkid and other cmds...no joy. I tried fuser yesterdya on both sdb and sdc but it returned clear. So no processes are using the devs? Now I wondering is it the ms-reserved partition that is the issue. If so can I just delete the 17MB partiton without losing the data that is still on the drive? Since they have not been mounted or written to, in theory my data should still be on the drives?

I've searched the web for similar issues, I can't believe I'm the only person to have ran into this...initializing an ext4 hd? I've attached photos for context.

Any ideas..

---

### Post by tea for one on 2024-06-21
> **mwatkins-wfvp said:**
> Two (ext4) /dev/sdb and /dev/sdc HDs in the PC were initialized by Win11.
> **mwatkins-wfvp said:**
> I can't believe I'm the only person to have ran into this...initializing an ext4 hd?
Windows 11 disk management tools will not understand ext4 partitions.
Boot into a live session and use Gparted to re-create your ext4 partitions.

---

### Post by mwatkins-wfvp on 2024-06-21
> **tea for one said:**
> Windows 11 disk management tools will not understand ext4 partitions.
Boot into a live session and use Gparted to re-create your ext4 partitions.

I understand that Win11 does not recognize ext4 partitions. I accidentally initialized the HDs while working a windows disk issue. Theres data still on the "unallocated" space. It isn't visible but still there. I am trying to "recover" the data. Thats why I'm using tools like testdisk, fsck.ext4...etc. Can you explain how gparted will recover my data? I can recreate formats/partitions all day but will I recover my data?

---

### Post by tea for one on 2024-06-21
> **mwatkins-wfvp said:**
> Theres data still on the "unallocated" space. It isn't visible but still there. I am trying to "recover" the data.
The info below from post 1
> I have not written anything to them.
Conflicting information.
Now, it seems that you have data on these ext4 disks after "initializing" them with Windows tools?
Gparted can copy partitions to other devices if you have suitable available space.

Your original post confused me somewhat.
> I accidentally initialized the HDs while working a windows disk issue
Which explains your comment about being the only person having run into the issue of using Windows tools to initialize an ext4 partition.
It's an accident, an unforeseen event.

I do not know what Windows has done to the data on these disks and I cannot offer more advice.

---

### Post by yancek on 2024-06-22
If you had data on the drive, just restore it from backup which you will have if the data was important.   As shown in the images you posted, other than the tiny 17MB windows partition, the rest of the drive is free/unallocated space which doesn't contain anything. Trying to run fsck is pointless as you do not have any partition nor do you have any ext4 filesystem.  That has all been destroyed by your accidentally initializing the disk which cause the loss of all files as explained in the link to the microsoft site below.  Testdisk and photorec are the most probably options if you didn't have backups.

 [https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks)

---


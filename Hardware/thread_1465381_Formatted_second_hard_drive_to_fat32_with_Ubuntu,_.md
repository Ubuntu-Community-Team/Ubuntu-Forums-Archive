---
title: "Formatted second hard drive to fat32 with Ubuntu, but doesn't show in XP?"
date: 2010-04-29
forum: Hardware
---

### Post by djvic87 on 2010-04-29
I installed a second hard drive (brand new seagate barracuda 1TB) in my computer to store my multimedia. Then, I used Ubuntu to format the drive to fat32 so that it can be cross-platform compatible. So, next day I went and started up XP, and for some reason the hard drive didn't show up under my computer. Also, if I go to device manager and look under disk management, it shows that the drive is there as "unallocated" Is there something I did wrong? Or could it mean that the hard drive malfunctioning? Why would it only mount in Ubuntu, and not in XP?

---

### Post by Paddy Landau on 2010-04-29
Did you create a partition on the drive?

If your drive contains no data yet, then I suggest that you delete the partition on the drive (it will delete ALL data on the drive, so **take care to select the correct drive!**), recreate the partition, then format as NTFS.

NTFS works well on both Ubuntu and Windows, and is more efficient than FAT32.

---

### Post by limey_rick on 2010-04-29
Did you try to look and see if the disk was shown through Disk Manager in Computer Management in Xp? 

[http://support.microsoft.com/kb/308423](http://support.microsoft.com/kb/308423)

Use the Disk Management tool.

This will show you if XP sees the disk; windows will not display disks in the explorer if they are unallocated, but you can allocated them in the Disk Manager of the Computer Management screen.

---

### Post by djvic87 on 2010-04-29
Wait, are you saying that formatting and creating a partition are two different things when it comes to having a new drive?:confused: I mean, As what I can recall, I simply installed the drive, opened disk utility from ubuntu, formatted the drive to FAT. And then it gave me a 1000GB partition. I assume I did make a new FAT partition. But for some reason, it wouldn't shou in explorer nor in disk management in XP.

---

### Post by Paddy Landau on 2010-04-29
> **djvic87 said:**
> Wait, are you saying that formatting and creating a partition are two different things when it comes to having a new drive?
Yes, they are. These days, the manufacturers usually create the partition and format it beforehand, so you should not have to. But not all manufacturers do it.

Personally, I find that doing it anyway prevents any problems; and using NTFS instead of FAT32 makes better use of the hardware.

---

### Post by limey_rick on 2010-04-29
Actually, I forgot something; I think the problem is that Windows XP cannot format a FAT32 drive larger than 32GB so maybe that's why it cannot see it. 

If you do as Paddy suggested and format as NTFS, Ubuntu will see it fine, as will XP.

---

### Post by djvic87 on 2010-04-29
Actually the hard drive didn't came pre-formatted out of the box. When I connected the drive in ubuntu, it showed as unrecognized, etc. So from there I just went and formatted the drive to FAT. It is weird because I've seen external hard drives that are readable under XP with FAT even if the size was over 32GB.

A friend of mine has the same drive, went through Ubuntu and formatted his 1TB secondary drive to FAT. I don't know why it's not working for me. I don't have any problem with formatting my drive to NTFS, I was just concerned if the drive is defective.

EDIT: This is what happens, fist I went to disk utility, and see the hard drive labeled as 1000gb Hard Disk, on the bottom it says Not Partitioned. Then, right on the bottom of that, it shows 1000 GB Unrecognized "Unknown or Unused. When I highlight the 1000 GB "Unrecgonized part, it gives me two options either create a file system and create partition table. What I did next is create a FAT filesystem. Then, after it created the new FAT filesystem, and when I click on the new filesystem, it shows that it's not partitioned. I have no idea why it doesn't give me an option to partition the new filesystem?

---

### Post by Paddy Landau on 2010-04-29
All right, djvic87, we have the answer now.

Your drive doesn't have a partition.

In Ubuntu:

[LIST=1]
[*]Go to System > Administration > Partition Editor (or it may be called GParted).
[*]Choose the device that is your second drive. **It's important to choose this correctly**, otherwise you could delete your system drive or your data!
[*][B]Double-check that you have selected the right drive, because the next steps will delete *all* data on the drive.
[/B]
[*]It will list any partitions. If you see any, then for each partition:
[LIST]
[*]Right-click and select Unmount, if available.
[*]Right-click and select Delete. **This will delete all data on the drive!**
[/LIST]
 
[*]You should have no partitions left.
[*]Right-click in the white area and select New.
[*]Choose a Primary partition; choose the entire drive; type a label for your drive (something unique to you and your drives, and use only letters and digits for cross-platform compatibility); select NTFS as the format type.
[*]Apply.
[/LIST]
When Gparted has finished, right-click the partition and select Mount. Close GParted.

Check that you can write a file, read a file, and delete a file.

Boot into Windows and check again that you can write, read and delete files.

Let us know whether it works.

---

### Post by djvic87 on 2010-04-29
Thanks for the step by step instructions. However, I got tired of the problem so I just went with your suggestion of formatting the drive as NTFS through windows. Thanks.

---

### Post by Paddy Landau on 2010-04-30
I'm glad you got it fixed.

Please mark the thread as Solved.

---

### Post by Symbioosi on 2011-05-30
NTFS is not compatible with Macs  [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by coffeecat on 2011-05-30
> **Symbioosi said:**
> NTFS is not compatible with Macs  [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

As far as I can see, this has nothing to do with the thread subject, but it does need a response. Mac OSX (Leopard and Snow Leopard at least) can read NTFS filesystems out of the box, but not write to them. So the "no" in the Mac column in that Wikipedia link for NTFS support is an over-simplification at best and misleading at worst. And it is a trivial matter to install the ntfs-3g driver in MacOS to get read-write support.

**EDIT**: I've just noticed that the thread was over a year old before being resurrected. I did not mean to add to a thread necromancy. I'll ask a mod if they want to close it.

---

### Post by s.fox on 2011-05-30
This thread is solved:

> **djvic87 said:**
> Thanks for the step by step instructions. However, I got tired of the problem so I just went with your suggestion of formatting the drive as NTFS through windows. Thanks.

This thread is also over a year old.

Thread Necromancy - Thread Closed.

---


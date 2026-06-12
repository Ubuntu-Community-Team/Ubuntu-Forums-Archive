---
title: "Partition Questions..."
date: 2011-09-13
forum: Hardware
---

### Post by Aurauxis on 2011-09-13
Hello... I have a 500 GB external hard drive with 3 partitions. One is a FAT 32 used for storage another contains an installation of Ubuntu 10.10 (Ext4) and the third one I use for swap space (Swap). Despite all this I still have plenty of space in there. Anyway I had created a system earlier before in which I would use the FAT partition to run an Virtualbox installer with some plugins and after doing so I would mount the hard drive in a specific way so I could run Ubuntu off of Virtualbox. The problem is it didn't work. Ubuntu is fine I can boot off from BIOS that but I want to be able to run it while using Windows. When I mount it wants me to format the drive :shock: before I can use it. But what about the FAT partition. Must the partition be NTFS or must it me formatted by Windows before it can be used? Yeah I tried Ext2 but it didn't really work. The data appeared as "RAW" and I couldn't get the folders to open. I think thats all. 

I have been told before that my posts are a bit confusing. Sorry but I am in a rush. Also the comma key is broke. In its simplest form my problem:

[LIST]
[*]I have 3 partitions on an external hard drive. (FAT32 Ext4 Swap)
[*]I want to mount the FAT partition on Windows.
[*]It doesn't work. It wants me to format the disk (!)
[*]I've tried Ext2
[*]I don't want to lose my data.
[*]Does anyone have any ideas?
[*]Support would be greatly appreciated. ):P
[/LIST]

---

### Post by Aurauxis on 2011-09-14
Infamous (bump!)

---

### Post by coffeecat on 2011-09-14
> **Aurauxis said:**
> Infamous (bump!)

I'll have a go. :wink:

A few possibilities.

Windows won't recognise multiple partitions on a flash drive, but I don't know whether that's so with a conventional USB drive. Might be worth investigating.

Windows tends to get confused when there are logical partitions with a Linux filesystem. But that's with logical Linux partitions on an internal drive. I've never investigated this with an external drive. It could be that this is the problem. The question is: do you have logical partitions on the drive? Plug the drive into an Ubuntu system, or boot up the Ubuntu that is on that 500GB drive. Now open a terminal and post the output of:

```
sudo fdisk -lu
```

Last thought. I don't think this is likely, but I wonder if the drive has a GUID partition table (GPT), and not a mbr one. That shouldn't matter to Windows 7 but I don't think Windows XP would cope. What version of Windows are you running? The output of fdisk will tell us if your have a GPT.

---

### Post by Aurauxis on 2011-09-25
Sorry! I thought I had already posted a reply. Maybe it didn't go through. Anyway here is the output:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb41b90c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   156252047    78125000    6  FAT16
/dev/sda2   *   248807424   625139710   188166143+   7  HPFS/NTFS
/dev/sda3       156252160   248807423    46277632   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000deb5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   117194174    58597056    7  HPFS/NTFS
/dev/sdb2   *   117194175   800792054   341798940   83  Linux
/dev/sdb3       800792574   840792063    19999745    5  Extended
/dev/sdb5       800792576   840792063    19999744   82  Linux swap / Solaris

Disk /dev/dm-0: 60.0 GB, 60002332672 bytes
255 heads, 63 sectors/track, 7294 cylinders, total 117192056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System

``` My drive is the sdb. Yes we have logical partitions I believe. And also I have MBR not GUID.

---

### Post by coffeecat on 2011-09-25
Out of interest, I simulated your partition layout on a spare 60GB drive sitting in a USB docking station. Smaller than your 500GB drive, but it was the multiple partitions, Linux filesystems and a logical partition I wanted to test. Relevant part of my "sudo fdisk -lu":

```
Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ce65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    51202047    25600000    7  HPFS/NTFS/exFAT
/dev/sdc2        51202048   112642047    30720000   83  Linux
/dev/sdc3       112642048   117209087     2283520    5  Extended
/dev/sdc5       112644096   117209087     2282496   82  Linux swap / Solaris

```

I tried plugging that into Windows 7. Windows 7 mounts the NTFS partition 1 quite happily and can read and write to it. It shows sdc2 and sdc5 as "healthy unknown primary partitions" in Disk Manager. Yes, sdc5 is a logical but Windows is known to get confused with Linux logical partitions and call them primary.

But to go back to your OP, you referred to a FAT partition, whereas the partition table thinks it is NTFS. I wonder if the filesystem itself is FAT32, but the partition table has the wrong code and that is what is confusing Windows. Just a theory - I really don't know.

Perhaps the best thing would be to copy your data off sdb1, reformat it with Gparted, copy the data back on again and see what Windows has to say about it this time.

---

### Post by Aurauxis on 2011-10-06
I just did that. I plugged it into a Vista machine and it still wants a format (!) But my target is XP. I will get a chance soon and try it on that.

---

### Post by Aurauxis on 2011-10-07
Nope.
I hate Windowz.

---

### Post by coffeecat on 2011-10-07
So long as you have backed up your data, try creating a new partition table in Gparted and then whichever partitions you want and see if Windows is happy with that. There may be a problem in the partition table.

---

### Post by Aurauxis on 2011-10-10
Never mind it all!
Did I ever mention the partition was encrypted? I had another USB stick that I intended to use in the meantime while I try to fix up my harddrive. I recently encrypted that too and it stopped working. I formated the disk and the harddrive partition and left them without encryption and they work!

---


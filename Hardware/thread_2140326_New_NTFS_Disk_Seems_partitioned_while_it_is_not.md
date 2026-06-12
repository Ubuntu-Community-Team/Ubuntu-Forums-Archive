---
title: "New NTFS Disk Seems partitioned while it is not"
date: 2013-04-29
forum: Hardware
---

### Post by HandleWithCare on 2013-04-29
I just bought a Seagate Barracuda 3TB disk To replace an older 2TB disk. So I copied all data from the 2TB one to the new one. I formatted the disk as NTFS first since I want to be able to use it from windows as well. The old was was 99% full and with a 13,8 Mb/sec transfer rate it took over 40 hours to copy all data. After that the new disk worked perfectly under Ubuntu, all data was fine. But when I restarted I got an error complaining about a missing MBR. Weird, I thought. I switched the SATA cables from my SSD, containing a dual-boot Ubuntu-windows with that from the new disk. Now, Both Ubuntu and windows start fine, but the new disk is not mounted in any of them. When I load disk management both OS show the disk split in six parts:
[LIST]
[*]3,14 GB unallocated
[*]914,50 GB primary
[*]13,74 GB unallocated
[*]867,17 GB primary
[*]249,45 GB unallocated
[*]746,52 GB unallocated
[/LIST]

Edit: Just noticed the disk looks different in Ubuntu (the previous list is in Windows). Ubuntu says this:
[LIST]
[*]112 GB Free Space
[*]871 GB NTFS Partition 1
[*]372 GB NTFS Partition 2
[*]1,6 TB Free Space
[/LIST]

Edit 2: when I run fdisk -l this is what it shows for my new disk:
```

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/sdc2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not start on physical sector boundary.
/dev/sdc3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not start on physical sector boundary.
/dev/sdc4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order
```

Edit 3: found [this post]("http://askubuntu.com/questions/266024/ntfs-corrupted-hdd") that pretty much exaclty describes my problem. However, a solution is not provided. Before I give in and just start over I would like to know how to prevent these kind of problems in the future
 
Edit 4: From [this answer]("http://askubuntu.com/a/229991") to a similar problem I learned about testdisk. When I install this I can browse the new disk without problems. Now all I need is to find a way to really fix the disk (with testdisk?)

Is there a way to get the disk working properly again? Because I really don't want to waste another 40+ hours.

---

### Post by oldfred on 2013-04-29
If it is a 3TB drive you cannot use fdisk nor MBR(msdos) partitioning. 
You need gpt(GUID). 
You can use gparted, parted or gdisk which is the fdisk for gpt drives.

It looks like you just have data in the partition table area of the drive and the partition tools are trying to read that as a partition table.

Did you partition drive before copying data or just format it and copy data? Some have done that and it does copy as if a very large floppy drive that does not have partitions. But just about every tool requires partition table to correctly read drive.

What does gdisk say?
sudo apt-get install gdisk
       sudo gdisk -l /dev/sdb

      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by HandleWithCare on 2013-04-29
Thank you for your quick reply oldfred. I formatted the drive as NTFS and then copied data, so that is probably what caused the issue since I did not create a partition first. I have ran gdisk and it tells me this:
```
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Exact type match not found for type code 7000; assigning type code for
'Linux filesystem'
Exact type match not found for type code 4300; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Disk /dev/sdc: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7B426AC5-61AF-4C8E-AC6F-B66598CAB1AF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 8-sector boundaries
Total free space is 2124109109 sectors (1012.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1         6579571      1924427647   914.5 GiB   8300  Linux filesystem
   2      1953251627      3771827541   867.2 GiB   8300  Linux filesystem
   3       225735265       225735274   5.0 KiB     8300  Linux filesystem

```

---

### Post by oldfred on 2013-04-29
So did that work or more importantly can you read your data?

If there was no partition table and the invalid MBR was arbitrarily converted by gpt, I am not sure it would be ok?

---

### Post by HandleWithCare on 2013-04-29
The command did nothing, it only lists partition type. I have to check out gdisk to see whether it gives me some options to resolve the problem. Any tips?

---

### Post by oldfred on 2013-04-29
I think with gdisk you have to do a w to write the new partition data, but I would hesitate to do that if it is not working with valid MBR table to convert from.

Do you have the data well backed up from old drive? Or does it have changes. 

Does entire drive have to be NTFS for compatiblity with Windows? That is slower from Ubuntu than the native ext4 copy would be.

I also do not like one huge partition as then file checks or repairs can take long times, and if one issue then entire drive has to run chkdsk or fsck. But if multiple partitions an issue in one should not be an issue in another partition unless entire drive fails. But it does take more management of where data is with multiple partitions.

---

### Post by HandleWithCare on 2013-04-29
The data is directly copied from an old drive that still has the data on it. So I have a perfect backup. I do want a single partition since the disk is for a single purpose and single type of data. If I do 'w', will it create a new partition table so that I can set the whole drove as a single partition or will this maintain the (wrong) 'partitions' ubuntu sees now?

---

### Post by oldfred on 2013-04-29
I think it sets the wrong partitions.You could just try it as an experiment, but I do not think you will have any salvageable data and would have to repartition and reformat. 

You probably just have to start over. Create one large NTFS partition with gdisk or gparted and format at NTFS, You will loose all your data.

 I have created my gpt partitions with gparted, but only on smaller drives. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by HandleWithCare on 2013-04-29
Yep, there is no other way. I have created a new partition table and a new (single) partition. Now I have to wait another 40+ hours for all the data to be transfered.
Any, many thanks for your help oldfred!

---

### Post by oldfred on 2013-04-29
We have seen several users with the same issue.

Formatting tools should recognize that there is no partition table and at least warn you.

It seems like we need a tool to understand how the data is written, move the data around to make room for partition tables and preserve the data. But some of the MFT - master file table is backed up throughout drive so it is not exactly easy to do.

---


---
title: "Trying to mount HD that doesn't show up in blkid"
date: 2014-08-20
forum: Hardware
---

### Post by dorian.schramm on 2014-08-20
I just installed Ubuntu 14.04 this weekend. Here is my setup:
128GB SSD = Win7
128GB SSD = Ubuntu 14.04
500GB Seagate Barracuda = Files, music, photos, etc

  For some reason the SSD with Win7 is already mounting automatically.
I need to mount my "data" drive. From what I read I need to find out the UUID of the drive. But when inserted ```
sudo blkid -c /dev/null
``` I got: 

  ```
/dev/sda1: UUID="6C761AC0761A8B4A" TYPE="ntfs" 
/dev/sdb1: UUID="25b325e9-3f4a-4406-9a0d-ca51c364f287" TYPE="swap" 
/dev/sdb5: UUID="e685ce58-9a19-431b-bf26-39f5b68a1515" TYPE="ext4" 
/dev/sdc: TYPE="nvidia_raid_member"

```  The drive I want to mount is /dev/sdc. A looong time ago I used it  with his "twin brother" in raid, he died. So I just reformatted it.  Apparently it still is configured for raid. 
I did some research and found (on a old post) that if I use ```
sudo dmraid -E -r /dev/sdc
``` the raid mark will be removed. 
I used that command and now when I do ```
sudo blkid -c /dev/null
``` 
I get 
```
/dev/sda1: UUID="6C761AC0761A8B4A" TYPE="ntfs" 
/dev/sdb1: UUID="25b325e9-3f4a-4406-9a0d-ca51c364f287" TYPE="swap" 
/dev/sdb5: UUID="e685ce58-9a19-431b-bf26-39f5b68a1515" TYPE="ext4" 
```


  I did the ```
sudo fdisk /dev/sdc
``` then ```
p
``` and it gave me this:

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa15239e4

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?        2048   976769023   488383488    7  HPFS/NTFS/exFAT
```

 
  
Since I have data on it I wish to know if there is a way to make it work without reformatting.

Thanks!

---

### Post by yancek on 2014-08-20
First create a mount point for sdc1, you can name it whatever you want for simplicities sake I'll call it sdc1:

```
sudo mkdir /mnt/sdc1
```

Then mount it so it is accessible:

```
sudo mount -t ntfs-3g /dev/sdc1 /mnt/sdc1
```

The above is the standard method but since it was previously part of RAID, I don't know if that will make a difference.

---

### Post by dorian.schramm on 2014-08-21
Thanks for thaking your time to answer this. :D

Unfortunately it doesn't work. :cry: It says ```
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
```
I think it's because there is no /dev/sdc1, only /dev/sdc. But when I try with that I get this ```
NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

What I don't understand is why it works fine on Windows...

The drive shows up on Disks application but the Contents are Unkown and it doesn't say anything about the partition type.

---

### Post by yancek on 2014-08-21
Your output from fdisk on sdc above clearly shows sdc1 as an ntfs partition.  Using the device name "sdc" won't work.  Might be because it was part of a RAID setup, I don't know.
Did you create the directory /mnt/sdc1 prior to mounting?

> The drive shows up on Disks application but the Contents are Unkown and it doesn't say anything about the partition type.

Is that from windows?  Expected behavior as windows is incapable of reading a Linux filesystem unless you install third party software.

---

### Post by oldfred on 2014-08-21
The NTFS signature is the first sector of the partition or PBR which is constructed just like the MBR is on a MBR(msdos) partitioned drive. And Windows normally has boot code in the PBR and size info that must match partition table. Usually Windows then sees it as RAW not NTFS. But a partition table may still see it as NTFS.

It may just need chkdsk from Windows. I have had Windows use a NTFS partition that even prevented Linux from mounting entire drive. But a chkdsk resolved the issue.

If that does not work:
I might try testdisk just to see what it says about boot sector. NTFS partitions also have a backup, but do not know if having been in RAID makes a difference or not. Testdisk should say if good or not. But for now do not make any changes with testdisk.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by dorian.schramm on 2014-08-21
Yes I did create the directory. I even tried creating and mounting on /media but it didn't work either.

No, that is from Ubuntu. Everything is fine on Windows. I have been using it for more than a year without any problems.

Edit: I saw oldfred reply now. Thanks for answering. I'll try that and update this reply ASAP

UPDATE: chkdisk gives this: > The type of the file system is NTFS.
Volume label is Disco Local.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
  221696 file records processed.
File verification completed.
  18 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  222172 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  221696 file SDs/SIDs processed.
Security descriptor verification completed.
  239 data files processed.
CHKDSK is verifying Usn Journal...
  35079328 USN bytes processed.
Usn Journal verification completed.
Windows has checked the file system and found no problems.

 488383487 KB total disk space.
 334569428 KB in 1956 files.
      1568 KB in 240 indexes.
         0 KB in bad sectors.
    337267 KB in use by the system.
     65536 KB occupied by the log file.
 153475224 KB available on disk.

      4096 bytes in each allocation unit.
 122095871 total allocation units on disk.
  38368806 allocation units available on disk.

---

### Post by oldfred on 2014-08-21
You just ran chkdsk in read only mode, so it did not make any repairs. It did say it found no errors
Better to run it, so it does make repairs if needed.

If newest version:
Best to use /b as that includes /r and /r includes /f or it does everything. Often required to run multiple times.

       [http://technet.microsoft.com/en-us/library/cc730714.aspx](http://technet.microsoft.com/en-us/library/cc730714.aspx)

---

### Post by dorian.schramm on 2014-08-21
That will take some time. I'll do it overnight then.

UPDATE:I did again and got this:
> C:\Users\Dorian>chkdsk e: /f /r
The type of the file system is NTFS.
Volume label is Disco Local.

CHKDSK is verifying files (stage 1 of 5)...
  221696 file records processed.
File verification completed.
  18 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 5)...
  222170 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 5)...
  221696 file SDs/SIDs processed.
Security descriptor verification completed.
  238 data files processed.
CHKDSK is verifying Usn Journal...
  35080720 USN bytes processed.
Usn Journal verification completed.
CHKDSK is verifying file data (stage 4 of 5)...
  221680 files processed.
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
  40151450 free clusters processed.
Free space verification is complete.
Windows has checked the file system and found no problems.

 488383487 KB total disk space.
 327438856 KB in 1950 files.
      1564 KB in 239 indexes.
         0 KB in bad sectors.
    337267 KB in use by the system.
     65536 KB occupied by the log file.
 160605800 KB available on disk.

      4096 bytes in each allocation unit.
 122095871 total allocation units on disk.
  40151450 allocation units available on disk.

---

### Post by dorian.schramm on 2014-08-22
Here is the log for testdisk

```

Fri Aug 22 11:48:24 2014
Command line: TestDisk

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 3.13.0-34-generic (#60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014) x86_64
Compiler: GCC 4.8
Compilation date: 2013-10-29T01:29:29
ext2fs lib: 1.42.9, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       250069680 sectors
/dev/sda: user_max   250069680 sectors
/dev/sda: native_max 250069680 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       250069680 sectors
/dev/sdb: user_max   250069680 sectors
/dev/sdb: native_max 250069680 sectors
/dev/sdc: LBA, HPA, LBA48, DCO support
/dev/sdc: size       976773168 sectors
/dev/sdc: user_max   976773168 sectors
/dev/sdc: native_max 976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 1 sectors, sector size=512
Hard disk list
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63, sector size=512 - M4-CT128M4SSD2, S/N:000000001143031D7B02, FW:000F
Disk /dev/sdb - 128 GB / 119 GiB - CHS 15566 255 63, sector size=512 - M4-CT128M4SSD2, S/N:000000001119030727C2, FW:000F
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ST3500418AS, S/N:5VM928ZN, FW:CC38

Partition table type (auto): Intel
Disk /dev/sdc - 500 GB / 465 GiB - ST3500418AS
Partition table type: Intel

Analyse Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/32/33
Current partition structure:
 1 * HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]

search_part()
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63
NTFS at 0/32/33
filesystem size           976766976
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]
     NTFS, blocksize=4096, 500 GB / 465 GiB

Results
   * HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]
     NTFS, blocksize=4096, 500 GB / 465 GiB

interface_write()
 1 * HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]

search_part()
Disk /dev/sdc - 500 GB / 465 GiB - CHS 60801 255 63
NTFS at 0/32/33
filesystem size           976766976
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]
     NTFS, blocksize=4096, 500 GB / 465 GiB
NTFS at 60801/15/14
filesystem size           976766976
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]
     NTFS found using backup sector, blocksize=4096, 500 GB / 465 GiB
NTFS at 60801/47/46
filesystem size           976564224
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             12 223 20 60801  47 46  976564224
     NTFS found using backup sector, blocksize=4096, 500 GB / 465 GiB

Results
     HPFS - NTFS              0  32 33 60801  15 14  976766976 [Disco Local]
     NTFS, blocksize=4096, 500 GB / 465 GiB
     HPFS - NTFS             12 223 20 60801  47 46  976564224
     NTFS found using backup sector, blocksize=4096, 500 GB / 465 GiB

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

---

### Post by oldfred on 2014-08-22
It does look like chkdsk ran without error.

Testdisk shows this:
Warning: can't get size for Disk /dev/mapper/control
and:
NTFS found using backup sector

So there still seems to be some issue with sdc?

Is BIOS set for AHCI, not RAID nor IDE for sdc?

---

### Post by dorian.schramm on 2014-08-22
Yes there is some issue with it, because it still doesn't show with blkid and therefore I cannot mount it.

The BIOS is set for AHCI.

It most be something that only affects Ubuntu since it works flawlessly on Windows 7.

---

### Post by oldfred on 2014-08-22
That testdisk is saying something about /mapper that is typical of RAID (or LVM).
But you ran the dmraid command that should have removed the RAID meta-data, so I do not know what else to check.

Windows does seem to ignore a variety of issues, that Linux in trying to be careful sees. Usually the issue in Windows does come up later.

---

### Post by dorian.schramm on 2014-08-22
Hmm so is there a way out of this?

Is it possible to make it raid again and then try to mount it?

---

### Post by oldfred on 2014-08-22
I am out of ideas.

When you ran this did it give any messages. Everyone that has used it before just responded that it worked. So do not know what it says.

sudo dmraid -E -r /dev/sdc

You can create UUIDs and add them to a partition for ext4, not sure if a way for NTFS and whether that creates more issues.

---

### Post by sudodus on 2014-08-22
Have you got another disk to backup the content of this drive? Then back it up, and then you can wipe it (at least the first megabyte), and after that start with a fresh partition table and file system.

If you have no way to back it up (now), wait until you can get another disk or a cloud service, because in the long run it is too risky to 'live without a backup', because the disk may crash mechanically or electronically any day, tomorrow or five years from now.

---

### Post by dorian.schramm on 2014-08-22
If you are out of ideas imagine me, the noobie.

When I ran it, it asked for a confirmantion. (y to yes)
Am pretty sure it worked because I cannot do it again, it says that there are no RAIDs.

The hard drive isn't full but I have nothing else to backup it to.
Maybe I could create a proper partition with what is left and transfer the files to the new one. Then delete the old one and merge the two.
I don't have any knowledge on this, so I don't even know if it is possible.

About what you said about creating UUIDs: did you mean creating a ext4 partition?
Because my ideia was to use this drive has a common drive for both OSs.


Edit: sudodus, I don't have anything that important on this drive.. most of it are movies, music and some drivers that I keep just in case.
I was just avoiding reformatting because I have no way to do a backup and downloading everything again on my 1mb connectiong will take ages :P

---

### Post by sudodus on 2014-08-22
It is risky to mess with partitions, so I really have to tell you to avoid that. If you have a current backup, you can 'do anything' with the drive, but not now.

Maybe you can borrow an external drive (for example a USB disk) from a friend for a week or whatever time you need (to backup your data, fix the problem with your data drive, and restore the data from the backup).

---

### Post by dorian.schramm on 2014-08-22
Ok I guess I'll just watch all the movies first.

When the data on it is not the problem anymore what will be the steps? (So you can close the thread)

---

### Post by sudodus on 2014-08-23
We need not close the thread. Instead, let us wait until you have solved your problem. Then you can click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Is it correct that you need no help with backup?

Boot from another drive (no problem in this case, because it is a drive with only a data partition)

I suggest that you start by wiping the first megabyte of the drive. This operation means that you overwrite with zeros, and it is very fast. But it is risky, because you might overwrite another drive by mistake. So I suggest that you use the tool ***mkusb***, that helps you identify the correct drive. This tool was originally made to create boot usb drives, and uses the same menu system for wiping the first megabyte. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Then use ***gparted***. Install if not there already

```
sudo apt-get install gparted
```

Use the pulldown menu 'Device' -- 'Create partition table'

Then create your data partition(s) and file system(s). Use NTFS or FAT32, if you want to read from Windows, otherwise ext4 (linux).

Check that it works properly, can be mounted, is seen by blkid etc.

You can also check that the file system is good, for Windows files systems with chkdsk /f, for linux ext4 with

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number, for example /dev/sdb1

If still problems, wipe more of the drive. I suggest that you use DBAN or hdparm, because they are more efficient than mkusb (dd under the hood) for wiping a whole device. This takes hours anyway.

---

### Post by dorian.schramm on 2014-08-23
Ok lets wait then.

Yeah, I don't think need help with backup, unless there is a way to make the backup of 300 GB in files become 90 GB.
Otherwise I'll just copy the files to another drive when I have enough space.

There is one thing that isn't clear to me yet.
Wiping the first megabyte will work like the windows "quick format"?
Or it will keep the files and just change the partition?

Your other suggestions (DBAN and hdparm) will work has windows "regular format"?

Thanks for the assistance

---

### Post by sudodus on 2014-08-23
Pictures and multimedia files are usually well compressed already, so you cannot compress them. The exception are some video formats created by cameras, where it is possible to compress the files a lot without losing quality.

It is a good idea to wait until you can copy the files to another drive (when you have enough space). Such backups can be made systematically (keeping track of what is already backed up) with ***rsync*** or some graphical user interface. I use Unison to synchronize my data partition with an external (eSATA) drive.

Wiping the first megabyte is different from  the windows "quick format". Often data concerning the partitions are stored in the beginning of the drive, before the partitions. Also special data concerning the bootloader can be stored there.

Quick format does not overwrite with zeros, it only changes the file allocation table, any file data in the partitions are still there, and data before (outside) the partitions are not touched.

DBAN is run from a boot drive CD or USB, and hdparm is a linux program. They can wipe the drive completely, but I think it will be enough to wipe the first megabyte with mkusb, which is *much* faster.

In all these cases, you can use gparted to create a new partition table and new file systems.

---

### Post by dorian.schramm on 2014-12-28
I finally was able to backup my stuff.

I used mkusb to wipe the first megabyte of the drive as you said.

I installed gparted, selected the drive and went to create partition table.
But I can't find NTFS in the partition table types.
There is only: aix, amiga, bsd, dvh, gpt, mac, msdos, pc98, sun, loop.
Should I select msdos if I want to see the drive in Windows 7 AND in Ubuntu?

Thanks again

---

### Post by sudodus on 2014-12-28
This is going to be a backup drive and/or a data drive, not intended to boot(?)

The versions of ***gparted*** that come with the  Ubuntu desktop iso files, and that can be installed from the Ubuntu  repositories into an installed system, have the option to create an NTFS  file system.

I think you are looking at the kind of ***partition table***. If the drive size is more than 2 GB, I recommend GPT (GUID partition table), otherwise you can use the old MSDOS partition table.

When you have made a partition table, you can make ***partitions***, and fill the partitions will ***file systems*** (that will be able to contain and keep track of your files).

Use ***NTFS*** if you want to read it from Windows. Otherwise the ***ext4*** file system is better (faster, keeps file permissions etc) if you will use it only with linux.

---

### Post by dorian.schramm on 2014-12-28
Yes, I intend to use the drive for data only. The main purpose is to use it to store files (music, movies, ebooks, etc) that can be seen by both OSs (Win7, Ubuntu) and to install some Win7 games on it.

It says **select new partition table type**.
The drive is a 500GB Seagate Barracuda, so I guess I'm going to use GPT.
If I use GPT will Windows still be able to read/write on the drive?

Edit: I did some searching and I'm going with GPT

---

### Post by oldfred on 2014-12-28
I do recommend gpt with the only exception beings if you only have BIOS and may want to ever install Windows. Windows only boots from gpt partitioned drives with UEFI.  If drive may ever be moved to a newer system then definitely gpt and perhaps include the required efi partition at beginning of drive. It is not large 100 to 500MB and would be difficult to add when drive has lots of data. It should be first partition or at least near beginning of drive.

If booting with BIOS, you must have a 1 or 2MB unformatted partition with the bios_grub flag if using gparted to create partition. If using gdisk to create partitions then the bios_grub flag is set with ef02. 

XP would not read gpt drives, but all newer Windows read gpt partition data drives if NTFS, but not Linux formatted partitions.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

I used gpt on one drive with XP on another drive starting with Ubuntu 10.10. And since I was planning a new system back then (just built last month), I started partitioning all new drives even flash drives with gpt.

---

### Post by dorian.schramm on 2014-12-28
Thanks for the links.
I wont ever install Windows on this drive. I started using SSDs for boot drives and don't plan to go back to HDs.
I created only one partition, using NTFS and leaving 1mb at the start. I labeled Data. It is flaged as mstfdata.
If I build a new system I'll probably use this drive on it.
Do I need to create the efi partition then? If so, how?

Thanks again

Edit: My motherboard supports UEFI, I'm just not sure if I'm using it

---

### Post by sudodus on 2014-12-28
It is a good idea. Make it the first partition (near the head of the drive).

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

> 
[LIST]
[*]*Mount point:* /boot/efi  (remark: no need  to set this mount point when using the manual partitioning, the Ubuntu  installer will detect it automatically) 


[*]*Size:* minimum 100Mib. 200MiB recommended. [COLOR=#0000cd]/My comment: make it 300 MiB, otherwise you must watch it very carefully to avoid lack of space./[/COLOR]


[*]*Type:* FAT32 

[*]*Other:* needs a "boot" flag. 

[/LIST]


If Windows cannot read the big data partition after it when connected via USB, you can always delete the efi partition (and let there be unallocated space). And that space can be 're-used' as an efi partition, when you need it.

---

### Post by dorian.schramm on 2014-12-28
Ok, so sdc1 is a fat32 300mb partition flagged with boot.
sdc2 is a 2mb unformatted partition
sdc3 ia a NTFS partition with 465.47GB (All that the drive had left) flagged with msftdata.

Did I got everything write?

---

### Post by sudodus on 2014-12-28
Yes, I think so. It is good to have prepared for possible future alternatives, even if you will never really use them. Remember also, that the drive must be moved to an internal connection for windows to boot from it, while linux can boot also from external drives.

---

### Post by dorian.schramm on 2014-12-28
I think it's already in an internal connection, since I use it in a HotSwap bay.

Thanks for you help. I'm marking the thread as solved.

Huge kudos!

---

### Post by sudodus on 2014-12-28
You are welcome and good luck :-)

---


---
title: "Help with Reeeeeeaaaallly Corrupted USB Drive"
date: 2023-04-04
forum: Hardware
---

### Post by wmichaelb2 on 2023-04-04
I was asked by a non technical friend to try and resurrect a corrupt USB drive. The story is that it's full of family photos; it was a backup for a laptop that died, and was used for a photo display at a wedding. Afterward, no one can access the data, and there is no backup for this backup. It was originally used on Windows; I'm running Ubuntu Studio 22.04, if that matters. I've done some fair research, and tried ddrescueview, fsck.vfat (on a guess, I really don't know what the filesystem was), and fsck.

I cannot get the drive to mount, although the system recognizes it:

```
ls /dev/disk/by-id 

usb-PNY_USB_2.0_FD_AA1A0E2D00000147-0:0
wwn-0x5001480000000000
wwn-0x50014ee2697684b6
wwn-0x50014ee2697684b6-part1
wwn-0x50014ee2b9e7c1e7
wwn-0x50014ee2b9e7c1e7-part1


```

I tried to copy the files off the drive:

```

sudo dd if=/dev/disk/by-id/usb-PNY_USB_2.0_FD_AA1A0E2D00000147-0:0 status=progress | gzip -
c > /home/myusername/backups/DaveR.img.gz          
dd: error reading '/dev/disk/by-id/usb-PNY_USB_2.0_FD_AA1A0E2D00000147-0:0': Input/output error 
0+0 records in 
0+0 records out 
0 bytes copied, 0.330554 s, 0.0 kB/s 
myusername@StudioRat:$ sudo fsck.vfat -V -a /dev/disk/by-id/wwn-0x50014ee2697684b6-part1 
fsck.fat 4.2 (2021-01-31) 
Logical sector size is zero. 
myusername@StudioRat:~$ sudo fsck.vfat -V -a /dev/disk/by-id/wwn-0x50014ee2b9e7c1e7-part1 [/COLOR]
fsck.fat 4.2 (2021-01-31) 
Logical sector size is zero.

```

I tried gparted, but it will not detect the drive. 

KDE Partition Manager detects the drive as USB 2.0 FD - 30.23 GiB (/dev/sdi). If I open /dev/sdi with dolphin,it tells me that it's an empty block device.

ddrescueview was not successful.

I'd be really happy if I could help my friend by simply getting the files off the drive, but so far, I've had no luck. His theory is that he pulled the drive out while it was still active. ??? Any suggestions would be appreciated, and thanks in advance.

---

### Post by yancek on 2023-04-05
If it was originally used on windows, it is in all likelihood a windows filesystem (probably ntfs or exfat) which won't be repaired by Linux, if that's the problem (filesystem corruption).  Do you have a windows system you can use to check the drive?  The link below gives some suggestions you may have tried if you have access to windows.

[https://www.easeus.com/resource/problem-ejecting-usb-mass-storage-device.html](https://www.easeus.com/resource/problem-ejecting-usb-mass-storage-device.html)

I would expect that to copy files you would need the mount point to copy from rather than the device name and since you can't mount it that would not be possible.

---

### Post by TheFu on 2023-04-05
Looks like a flash drive, probably 32GB in size.  It probably is FAT32, not exFAT, nor NTFS.
Sadly, when flash drives fail and don't allow any read to happen, that's usually it.

Rather than using **dd**, use **ddrescue** to clone the storage.  ddrescue tries harder AND doesn't stop on bad blocks.  dd stops on any error.  If that doesn't work, tell them it is too far gone. Sorry. You'll never restore anything.

If you can get an image with ddrescue, then you can try to open it using a loop mount.  Since it is 95% FAT32, the easiest answer is probably to get a 32G SDHC/microSD/Flash drive and shove the image you created back onto that new device, then use MS-Windows to attempt any recovery efforts.  It will be too much effort to use testdisk/photorec on Linux.  Sure, you could restore files, but all the filenames will be generic ... something like f234924343.jpg or f2385364563.jpg for each.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

a) never use flash media for backups. It is for moving files between locations, never long term storage.
b) Stuff that is really important needs to be on at least 3 different media, in 3 different locations, with 1 of those locations at least 500 miles away.

---

### Post by wmichaelb2 on 2023-04-22
I ran ddrescue to no avail, and referred my friend to a local data recovery service.

---

### Post by TheFu on 2023-04-22
> **wmichaelb2 said:**
> I ran ddrescue to no avail, and referred my friend to a local data recovery service.

Data recovery services hate flash storage, including SSDs.  Much of their business is forensics and there's no way to be certain that deleted files are truly unrecoverable off SSD flash storage, even with 100 write cycles.  Add in that SSD vendors keep their write-load methods a closely guarded secret, what we do know is that all SSD (and probably flash) storage is virtual.  HDDs and recovery of data from HDDs makes assumptions about where blocks are located.  With flash storage, every block is virtual and can be in any order regardless of the storage chip layout.

---


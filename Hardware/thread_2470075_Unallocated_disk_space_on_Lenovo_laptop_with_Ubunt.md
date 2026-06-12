---
title: "Unallocated disk space on Lenovo laptop with Ubuntu pre-installed"
date: 2021-12-19
forum: Hardware
---

### Post by lenveen on 2021-12-19
I recently bought a Lenovo laptop with Ubuntu 20.04.3 pre-installed. When installing my favourite software I ran out of disk space. It tuns out that only about a quarter of the available disk space is in use. In the output of "fdisk -l" I see:
```

GPT PMBR size mismatch (122879999 != 500118191) will be corrected by write.
Disk /dev/nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: SKHynix_HFS256GOE9X081N                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: ...

Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1      34   1050781   1050748 513.1M EFI System
/dev/nvme0n1p2 1050782   9768967   8718186   4.2G Microsoft basic data
/dev/nvme0n1p3 9771008 122877951 113106944    54G Linux filesystem

```

When I open the "Disks" utility from the menu, I see a block labelled "Free Space 193 GB" with "Device nvme0n1, Contents Unallocated space". There are no options to delete or modify that part of the disk.
I want to expand "nvme0n1p3", which includes my home directory, to use the whole disk. When I click "Resize Volume", a warning comes up saying "Resizing a file system can lead to data loss. (...) Keep additional free space for the file system to work fast and reliably."
My first question is: is that "unallocated space" actually useful/necessary as the warning message suggests? If so, is 193GB excessive? Secondly, if (a good part of) that space is available, how do I safely expand the partition "nvme0n1p3"? I shouldn't like to start from scratch installing software.

In addition (and in reply to Oldfred below):

```

> sudo gdisk -l /dev/nvme0n1p1
[sudo] password for username: 
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/nvme0n1p1: 1050748 sectors, 513.1 MiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 3132C908-9C71-4C3F-9C31-8049CE897B3B
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1050714
Partitions will be aligned on 2048-sector boundaries
Total free space is 1050681 sectors (513.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

And also:
```

> lsblk -e7 -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT
FSTYPE NAME        LABEL      PARTLABEL            SIZE FSUSED MOUNTPOINT
       nvme0n1                                   238.5G        
vfat   &#9500;&#9472;nvme0n1p1 EFI System EFI                513.1M   8.9M /boot/efi
vfat   &#9500;&#9472;nvme0n1p2 PQSERVICE  Recovery Partition   4.2G        
ext4   &#9492;&#9472;nvme0n1p3                                  54G    46G /

```

---

### Post by oldfred on 2021-12-19
Post these in question above.
sudo gdisk -l /dev/nvme0n1p1
lsblk -e7  -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT

---

### Post by rsteinmetz70112 on 2021-12-21
It looks like the partition table is MRB - If so it should probably be converted to GPT
You should be able to grow the partitions to use the unallocated space.

---

### Post by TheFu on 2021-12-21
Please edit the first post and wrap all the output in 'code tags', so the columns line up. Too hard to read otherwise.
Code tags: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

A quick look seems to say the GPT is corrupted. I'd fix that first. I think gdisk can do it, since there is a primary and backup copy of the partition table.  I suspect the person/company that installed it, used disk cloning software and didn't actually do an install that knows how to correctly place the backup GPT at the end of the disk, as it should. 

**After ** you get the partition table fixed and the backup is properly placed at the end, then you should be able to boot from alternate media (typically a flash drive with the Ubuntu installer on it), run gparted and simply drag the right side of the ext4 partition to the right - perhaps 50G more. Don't drag it all the way, since when you gain more experience, there are some better solutions and if all the storage is already used, then you won't be able to use those. Best to use no more than 40% of the total SSD size.

But be 100% certain you fix the partition table issue first.

---

### Post by oldfred on 2021-12-21
Normally UEFI is gpt partitioned, but gdisk says it found MBR.
Gdisk can convert drive to gpt which is what you should have if using UEFI. 
Ubuntu does let you install in UEFI mode to the old MBR partitioned drives, but really should not.

Make sure you have good backups.
Conversion with gdisk should keep data, but any major change has risks. 
And at minimum you will need to do a total reinstall of grub in UEFI mode as UUIDs & GUIDs will change.
Or you may have to do a full reinstall.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by lenveen on 2021-12-24
Did not go well. Made my backups and started gdisk. On nvme0n1p1 and nvme0n1p2 is detected MRB but no GPT. It said it had translated to GTP "in memory". I then pressed "w" to write the changes and exit. After that I could not reboot from the menu. Turned off the laptop by pressing the power button for a few seconds and then it would not boot up. Booted from Ubuntu usb drive and re-installed from scratch. Cost me an hour or two to re-tweak the OS and re-place the files, so no big deal. Quite annoying though to buy form Lenovo with Ubuntu pre-installed, only to find they did a shoddy job! Thanks for your help, though!

---


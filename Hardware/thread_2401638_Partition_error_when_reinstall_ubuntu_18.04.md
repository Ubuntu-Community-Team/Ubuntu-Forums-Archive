---
title: "Partition error when reinstall ubuntu 18.04"
date: 2018-09-20
forum: Hardware
---

### Post by levshkatov on 2018-09-20
I have two physical drives with Ubuntu 18.04 and Windows 8.1. Both have  EFI partitions. I'm trying to reinstall Ubuntu from a live USB. If I  have both drives connected I have an error that two file systems have  identical mount points and I can't do anything with that. If I  disconnect the drive with Windows, I have another error:  

```
The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as an "EFI boot partition" and should be at least 35 MB in size. Note that this is not the same as a partition mounted on /boot.

If you do not go back to the partitioning menu and correct this error, bootloader installation may fail later, although it may still be possible to install the bootloader to a partition.
```

My Gigabyte motherboard has UEFI dualbios. I selected no CSM support,  Other OS and UEFI OpROM. I have no options for the secure boot so I  don't know whether it's enabled or not. 
  How can I deal with this error?

---

### Post by toaki on 2018-09-20
[SIZE=4]I Have same problem last week. I can't find any solution so at last I install windows and ubuntu in the same drive. :D
[/SIZE]

---

### Post by levshkatov on 2018-09-20
Sounds really bad. Now I'm trying to reinstall ubuntu in data-safe mode. If it isn't possible I will wipe data and install it.

---

### Post by oldfred on 2018-09-20
For UEFI install you must have the ESP - efi system partition which is FAT32 with the boot flag and/or esp flag.
And Ubuntu's grub wants to only install to drive seen as first drive, normally sda, or first NVMe drive. So that drive needs the ESP, but best to have ESP on every drive, even if only for future use.
And for UEFI all drives should be gpt partitioned.

        Always have good backups, in case a mistake is made.

Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... change to sdb or if sda,  or you may erase Windows drive if you use that drive.
this will erase all of hard drive/SSD.
Best to check drive as often plugging in a flash drive installer in live mode becomes sda, then Windows drive may be sdb, and drive you want to change is sdc.
sudo parted -l
sudo parted /dev/sdX mklabel gpt 

      
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 
    Partitions are essentially the same, but newer versions of Ubuntu installed now.

---


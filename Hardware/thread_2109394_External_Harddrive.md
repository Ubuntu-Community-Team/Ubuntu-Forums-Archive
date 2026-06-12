---
title: "External Harddrive"
date: 2013-01-27
forum: Hardware
---

### Post by Stvnx7 on 2013-01-27
Hi everyone. 

I have a Western Digital USB hard drive, about 1TB in size. Unfortunately, my partition table has become corrupted, and my hard drive is now seen in RAW format. 

I haven't been able to restore the partition table, unfortunately. (I tried testdisk - didn't work). I have tried to recover files from the harddrive, but it takes much too long to scan a 1TB disk. 

Anyway, I feel like the only option I have left is to format the harddrive and lose the data that is on it. 

I was wondering if anyone had any suggestions as to which filesystem I should use in order to prevent the HDD from losing its partition table again. 

I am aware that the best way to prevent this from happening is to make sure I unmount the hard drive properly, but I was wondering if there was any filesystem that was less prone to this type of error. 

Thanks! 

-Steven

---

### Post by thermion on 2013-01-27
This is not about which filesystem to use rather than what kind of "partition table".

I would suggest using a GPT rather than the old MS-DOS partition table.
The great thing about GPT is that you have multiple copies of the partition table across your entire volume.

---

### Post by Stvnx7 on 2013-01-27
> **thermion said:**
> This is not about which filesystem to use rather than what kind of "partition table".

I would suggest using a GPT rather than the old MS-DOS partition table.
The great thing about GPT is that you have multiple copies of the partition table across your entire volume.

That sounds incredibly awesome and I wonder why anyone would use the old MS-DOS vs. GPT given what a horrible hassle it is to have a RAW HDD (you know your files are there but it is a huge pain to recover them). 

I will read up on GPT and how to use it. Thank you very much.

---

### Post by thermion on 2013-01-27
Well, there are some things to keep in mind:

Windows can only handle gpt drives since Vista x64. So any Windows OS older than that won't be able initialize the drive.

---

### Post by Stvnx7 on 2013-01-27
> **thermion said:**
> Well, there are some things to keep in mind:

Windows can only handle gpt drives since Vista x64. So any Windows OS older than that won't be able initialize the drive.

I figured I would run into legacy issues of that nature, but I'm willing to put up with that if it means avoiding this again.

---

### Post by thermion on 2013-01-27
It's not bullet proof or anything. It just adds some level of redundancy. To be 100% save, you would still have to backup you files to another volume.

---

### Post by Peltsi on 2013-01-28
Before formatting the drive, type (with your usb HDD connected) lsusb in terminal and see what your usb-sata adapter is. There has been a lot of problems lately with super top M6116 adapter, which due to driver error will corrupt your disk. It seems to be a very common chip used especially in affordable ebay usb-sata adapters.

---

### Post by oldfred on 2013-01-28
RAW means Windows lost the NTFS PBR or partition boot sector. But if data is ok, you should be able to restore the PBR. Or from testdisk build a generic (XP type) NTFS PBR that should work.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If backup is invalid also, use the rebuild BS option also on same testdisk screen.

I also suggest gpt for larger drives if not using XP, but file system damage will still occur if you do not shutdown normally. gpt can only be booted with Windows if UEFI boot. But Windows does not boot from an external anyway. Ubuntu will boot from gpt, I even have gpt on my 16GB flash drive with a full install of Ubuntu.

---


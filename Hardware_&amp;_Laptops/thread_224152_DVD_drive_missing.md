---
title: "DVD drive missing"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by Jason Spaceman on 2006-07-27
I installed Ubuntu 6.06 on my laptop.  The laptop comes with a Pioneer DVR-K16 DVD burner.  But for some reason it isn't showing up in either Windows or Ubuntu.  I know the drive works, as I used it to install Ubuntu.

Perhaps the issue is with the way I partitioned my hard drive?  Windows is formatted as NTFS, and I created a FAT32 partition, as well as a / and swap partition for Ubuntu.  I made all 4 partitions primary.  

In Windows my DVD drive was labelled D: and the FAT32 partition was labelled E:.  But now the D: drive has disappeared altogether, and similarly there is no /dev entry for it in Ubuntu.

---

### Post by Jason Spaceman on 2006-09-03
I wonder if the problem has something to do with the bootloader.  It doesn't seem to make a difference whether I use Lilo or Grub.  Either way my DVD drive doesn't show up in WinXP or Linux.  Once I do a 'fdisk /mbr', and restore my master boot record, the DVD drive shows up again in WinXP as D:.  However I am unable to boot back into Linux.

Is it possible to modify the grub or lilo .conf files so that both Windows and Linux see my DVD drive?

---


---
title: "Can I Move FAT32 Partition to First Sectors"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by joeinazyes on 2006-08-15
I installed DD 6.06 64-bit on my 80GB hard disk and it is formatted in Ext3 (68.3GB partition), with a 1.42 GB Swap Partition.  I then added a 4.7 GB FAT32 partition in between the MAIN 68.3 GB Ext3 partition and the 1.42 GB Swap Partition with the intention of loading Windows 98SE on the FAT32 partition.

However, on install Win98 doesn't recognize the FAT32 partition because the first sectors on the drive are formatted in Ext3.  I want to load Win 98SE and dual boot with DD 6.06.

However, I loaded DD 6.06 first and am trying to go backwards and install Win 98SE after the fact on the FAT32 partition that appears to be sandwiched between the other 2 partitions.  I used GParted Live CD and it won't let me move the Ext3 or Swap Partitions.

Please direct me on how I can load Win 98SE on the FAT32 partition AFTER having installed Dapper Drake.

---

### Post by bonjun on 2006-08-15
i believe, Win98 must be on the first sector your harddisk...
i don't know if you can run Win98 on VMware player

---

### Post by joeinazyes on 2006-08-15
I'm still searching for answers and can use help.  Please respond if you have a solution.
Thanks.

---

### Post by joeinazyes on 2006-08-17
Still looking for options other than to completely reformat my DD 6.06 64-bit partition, load Win98SE, and re-load DD 6.06.


> **joeinazyes said:**
> I'm still searching for answers and can use help.  Please respond if you have a solution.
Thanks.

---

### Post by waldschm on 2006-08-17
What I would do is use the System Rescue CD [www.sysresccd.org/](www.sysresccd.org/) and use the partition client (run_qtparted) that's included. It allows you to resize partitions (GParted may be able to do the same?). I'm assuming your partitions are as such:

|------DapperDrake------| |--Win98--| |--Linux Swap--|

What you need to do is erase the Win98, resize Dapper to take up the new space one the right edge but to take up less space (the size you want for Win98 ) on the left. This will leave a gap at the beginning which you can format as either fat32 or ntfs. Now, this will erase Win98 entirely so I'm not sure if you're ok with that. I also can't guarantee 100% this won't mess up dapper. I've done it before and it says 'moving data' and it works for me, but that doesn't guarantee success, so backup anything essential. Also I think you need to backup your MBR as Windows overwrites it and you will need to restore it (this is the case with WinXP at least).

---

### Post by joeinazyes on 2006-08-17
Thanks waldschm, you described my situation perfectly.  It appears that you are the only one that understands my system state and what I am trying to do.  I'll report back when I try the System Rescue CD approach. I know that you personally are not guarenteeing succes, and it is my risk, so I'll give it a whirl.
Thank you.

---

### Post by waldschm on 2006-08-18
No problem, good luck with the move and remember to backup your MBR and you might want to do the partition table just in case.

(mbr backup)
dd if=/dev/hda of=/$PATH_TO_BACKUP_MEDIA/boot_backup.mbr count=1 bs=512

(partition table backup)
sfdisk -d /dev/hda > /$PATH_TO_BACKUP_MEDIA/ptable_backup.pt

(change the $PATH_TO_BACKUP_MEDIA to the path for your handy usb stick or cd-rw)

---


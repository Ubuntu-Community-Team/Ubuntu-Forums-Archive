---
title: "External Hard disk empty, urgent help needed..."
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by flavio newbie on 2007-12-10
After saving 60 gb on a external harddisk of 80 i formatted the computer, when i plugged the exteral harddisk back in it told me it was unformatted.... and therefore apparently emtpy, what do i do know? It would be really a great thing to hear that i have some hope. Tank you very much

---

### Post by linuxonbute on 2007-12-10
> **flavio newbie said:**
> After saving 60 gb on a external harddisk of 80 i formatted the computer, when i plugged the exteral harddisk back in it told me it was unformatted.... and therefore apparently emtpy, what do i do know? It would be really a great thing to hear that i have some hope. Tank you very much


What format is the external disk drive?
Is it NTFS?

What version of Ubuntu are you using?

---

### Post by flavio newbie on 2007-12-10
ntfs and im using 7.10 but gparted tells me it has no format

---

### Post by taurus on 2007-12-10
Did you do the backup to your external harddrive from windows or Ubuntu? 

Post this command from a terminal after you have plugged in your external harddrive (and power on).

```
sudo fdisk -l
```

---

### Post by flavio newbie on 2007-12-10
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf695f695

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26        5276    42173236   af  Unknown
/dev/sda3   *        5276       12095    54774136    b  W95 FAT32
/dev/sda4           12095       16192    32903348    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00fd7cbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

---

### Post by taurus on 2007-12-10
What happens if you run

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by flavio newbie on 2007-12-10
i saved the files from ubuntu by moving them into the external hard disk (sdb1)

---

### Post by taurus on 2007-12-10
> **flavio newbie said:**
> i saved the files from ubuntu by moving them into the external hard disk (sdb1)

And did you remember to unmount or reject it before you unplugged it?

---

### Post by flavio newbie on 2007-12-10
root@flavio-laptop:/home/flavio# sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@flavio-laptop:/home/flavio# ls -la /media/sdb1
total 8
drwxr-xr-x 2 root root 4096 2007-12-11 01:38 .
drwxr-xr-x 8 root root 4096 2007-12-11 01:38 ..
root@flavio-laptop:/home/flavio# 

i was in a rush, and i thin i didnt eject

---

### Post by flavio newbie on 2007-12-10
i know im the one to blame...

---

### Post by flavio newbie on 2007-12-10
to be blamed..
i don't know

---

### Post by r00tzz on 2007-12-10
Depending on how important is your files, why dont you try some commercial software? Google'ing for them maybe you can try some before you buy.
[http://www.diskinternals.com/ntfs-recovery/](http://www.diskinternals.com/ntfs-recovery/)
[http://www.smartpctools.com/ntfs_recovery/index1.html](http://www.smartpctools.com/ntfs_recovery/index1.html)
Google for "ntfs recovery"

---

### Post by Pforrest on 2007-12-10
Could you give some additional detail: Under what OS and what program do you use to create the partition on the external drive.

---

### Post by flavio newbie on 2007-12-12
OK i found some restore programs, they are really slow in doing their work, but the files are emerging...

thank you to everybody

---


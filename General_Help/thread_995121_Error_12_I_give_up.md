---
title: "Error 12: I give up"
date: 2008-11-27
forum: General Help
---

### Post by jtwillobee on 2008-11-27
I've been through like 30 threads but still can't get this fixed. Windows will not boot, I get an "error 12". ](*,)

My partitions are a little wack:
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18e118e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   976751999   488375968+   f  W95 Ext'd (LBA)
/dev/sda5        20482938   348160679   163838871    7  HPFS/NTFS
/dev/sda6       356353893   358811774     1228941   82  Linux swap / Solaris
/dev/sda7       358811838   809900909   225544536   83  Linux
/dev/sda8       809900973   873968129    32033578+   7  HPFS/NTFS
/dev/sda9       873968193   976751999    51391903+   7  HPFS/NTFS
/dev/sda10      348160743   356353829     4096543+  83  Linux
/dev/sda11            189    20482874    10241343   83  Linux

Partition table entries are not in disk order


sda8 is my Windows partition
sda10 is /

And here is my menu.lst:
> 
title		Windows 95/98/NT/2000
root		(hd0,9)
makeactive
chainloader	+1


Help would be greatly appreciated. :D

---

### Post by linux_tech on 2008-11-27
Set bios to boot from cd, then boot using the win XP install, open the recovery console and type:  fixmbr
(it will wipe out Grub and replace it with Windows boot loader)

If you do not have the XP cd, you can also use super grub disk to fix the MBR-
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can also try this way to fix the mbr
[http://www.arsgeek.com/2008/01/15/ho...ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/ho...ubuntu-livecd/)

---

### Post by geirha on 2008-11-27
Your windows partition is a logical parition. As far as I know windows can't boot off a logical partition (linux has no problem with that though).

---

### Post by jtwillobee on 2008-11-27
Thanks. I'll give that a try.

---

### Post by caljohnsmith on 2008-11-27
I would not recommend running the "fixmbr" command that linux_tech gave, because then you won't be able to boot into any of your OSes the way you have things configured right now. Unfortunately Windows is on sda8, which is a logical partition; Windows will only let you install it to a logical partition if Windows can put its boot files on a primary partition. But since you don't have any primary partitions, that means that most likely Windows is missing its boot files. Is your Windows XP or Vista? Fortunately though, it is possible to boot Windows solely from a logical partition with a little work. How about posting the output of the following:
```
sudo mount /dev/sda8 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
And we can work from there if you want. :)

---


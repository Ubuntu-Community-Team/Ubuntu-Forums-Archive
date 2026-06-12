---
title: "Used fdisk and format but Grub is still there"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by wgregori on 2006-02-18
I put Ubuntu on a system that previously was running DOS FAT32.  I used fdisk to remove and then recreate the partitions.  I then used FORMAT /s to put the DOS system on the drive but when I try to boot I get a GRUB error...

how do I get rid of GRUB

Thanks!

Wayne

---

### Post by wgregori on 2006-02-18
Got it... apparently I needed to do a "low level" format... I downloaded a utility from the disk manufacturer... the software simply writes 0 in all disk sectors destroying all the data.

Thanks,
Wayne

---

### Post by lcg on 2006-02-18
[QUOTE=wgregori]Got it... apparently I needed to do a "low level" format... I downloaded a utility from the disk manufacturer... the software simply writes 0 in all disk sectors destroying all the data.[/QUOTE]
While that obviously worked, it was a tiny bit oversized. ;)

Grub is (usually) installed into your MBR, that's why it survived the re-partitioning, the formatting and everything else. However, its configuration in /boot/grub/menu.lst did not survive, which led to your Grub error.

You can write a new MBR with either the recovery console from a Windows 2000/XP CD (the command is 'fixmbr') or with Microsoft's fdisk, if you have a DOS floppy and this tool somewhere:
```
fdisk /mbr
```

HTH,
Lars

---


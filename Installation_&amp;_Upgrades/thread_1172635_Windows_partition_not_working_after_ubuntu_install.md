---
title: "Windows partition not working after ubuntu install"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by wee017 on 2009-05-28
I installed ubuntu in a dual-boot configuration alongside windows XP.  The installation went fine, and after messing around with ubuntu for a while, I tried going back to my windows partition and I get a BSOD after the black windows loading screen.

When I put in the windows recovery CD it says it can't find any hard drives, although gparted recognizes the hard drive and all partitions within it. Here is my fdisk -l output

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16779   134777286    7  HPFS/NTFS
/dev/sda2           16780       17883     8867880    7  HPFS/NTFS
/dev/sda3           17884       19457    12643155    5  Extended
/dev/sda5           17884       19342    11719386   83  Linux
/dev/sda6           19343       19457      923706   82  Linux swap / Solaris


---

### Post by snowboardb86 on 2009-05-28
I had the same issue when I installed Ubuntu 9.04 to dual boot with Vista. When I tried to boot it again it gave me the option to run a start-up repair, and this resolved the issue. That is normal when you change the partition table though.

---

### Post by wee017 on 2009-05-28
I wish I had that option, after the blue screen windows automatically reboots. I used VMWare to run a copy of windows so I could run chkdsk and it still doesn't work.

---

### Post by Mark Phelps on 2009-05-29
I'm surprised the windows recovery CD won't work.  Is this something you made or did it come with the PC?  One possibility is that you have a SATA drive and the recovery CD isn't loading the SATA drivers -- but if it came with the PC and you're still using the original hard drive, that shouldn't be the problem.

Have you tried booting into safe mode?

---

### Post by wee017 on 2009-05-29
I tried booting into safe mode and recovery console, both did not work.I do have an HP_RECOVERY partition in my hard drive, although I don't think it's useful in this situation.

---


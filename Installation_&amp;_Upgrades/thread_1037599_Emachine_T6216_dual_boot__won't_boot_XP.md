---
title: "Emachine T6216 dual boot  won't boot XP"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by n8fau on 2009-01-11
Hello all:

I installed Ubuntu 8.10 desktop from CD. The install went great, until my wife tried to boot to XP.

After selecting XP from the GRUB screen it goes straight to a system recovery program. I've tried everything I know to get around it...  No luck...

Let me know if you need more info:

Ubuntu 8.10
Emachine T6216

Thanks
Bob

---

### Post by Mark Phelps on 2009-01-11
Open a terminal and type the following "sudo fdisk -lu" (that's a lower-case L, not a one), and post the results here.

---

### Post by n8fau on 2009-01-12
Here are the results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb334b7c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1         9992430   159782489    74895030    7  HPFS/NTFS
/dev/sda2   *          63     9992429     4996183+   b  W95 FAT32
/dev/sda3       159782490   312576704    76397107+   5  Extended
/dev/sda5       159782553   310327604    75272526   83  Linux
/dev/sda6       310327668   312576704     1124518+  82  Linux swap / Solaris

Partition table entries are not in disk order
bob@missy-desktop:~$ 

Thanks for the help....

Bob

---

### Post by n8fau on 2009-01-16
If I'm reading it right it looks like it's trying to boot off /dev/sda2. The partition with XP on it is /dev/sda1. 

To me it looks like it's pointing to the wrong partition and trying to boot from that...  

Looking at my laptop (dual boot) It boots from /dev/sda1 which has my Windows on it....

---


---
title: "no bootloader after install 9.10 with XP already"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by fred_gavin on 2009-11-05
I have been reading posts in this forum for the whole day, but still cannot find the solutions for my problem. Offcoz there were ppl experiencing the same problem. But I am totally new to this. Hope some one can give me some direct solutions on my situation. 
Here was What I have done using a LiveCD terminal: 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f188f18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d635d63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749      121601   874361722+   f  W95 Ext'd (LBA)
/dev/sdb5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sdb6           25497      120182   760565263+   7  HPFS/NTFS
/dev/sdb7          120183      121535    10867941   83  Linux
/dev/sdb8          121536      121601      530113+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdadc6a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ sudo apt-get install grub-pc

where I made the configuration to "select/dev/sda". Then I dont know what to do now. 
As I am totally new to Linux, so even didn't know what exactly what I have done so far. Just following some random instructions found in the documentation and forum posts. 

Many Thanks in advance.

---

### Post by fred_gavin on 2009-11-05
I just realized that my XP is under /dev/sdb. But when I installed grub-pc, I configured it under /dev/sda. 

Does it make sense that I still do not have a bootloader in startup? 

And how can I make the change?

Thanks

---

### Post by fred_gavin on 2009-11-05
I do not really understand what other posts talking about. As I tried several methods, but nothing seemed be effective. 

Really need help, Please.

---

### Post by fred_gavin on 2009-11-05
Any one? I am waiting here.

---


---
title: "&quot;dirty&quot; filesystem, again and again"
date: 2008-11-13
forum: General Help
---

### Post by theduffman on 2008-11-13
Ubuntu 8.10
/dev/sda1   *           1        1104     8867848+   7  HPFS/NTFS
/dev/sda2            1105        1986     7084665    7  HPFS/NTFS
/dev/sda3            1987        2521     4297387+  83  Linux
/dev/sda4            2522        7296    38355187+   5  Extended
/dev/sda5            2522        2655     1076323+  82  Linux swap / Solaris
/dev/sda6            2656        7296    37278801   83  Linux
sda1 and 2 is my windows ntfs (C: and D:).  SDA3(ext3) is / SDA5 is swap and SDA6(jfs) is /home . I randomly do a quick read-only check of /home "fsck.jfs -n /dev/sda6" and its comin back as dirty, after only using it a few hours, general browsing, nothing intensive.  I reboot and do another check and it comes back 'clean'
/ has been fine when ive forced a boot check.  Whats goin on?  Should i backup my home and reformat ext3 ?

---

### Post by JNelson on 2008-11-14
try
> sudo fsck.jfs -f -v /dev/sda6


Becareful this could delete your data as the -f means force it to fix corruptions. The -v means verbose.

---


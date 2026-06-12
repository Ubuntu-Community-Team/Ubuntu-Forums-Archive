---
title: "3Tb sector misalignment; REAL guru needed here..."
date: 2011-11-21
forum: Hardware
---

### Post by Moozillaaa on 2011-11-21
I've tried re-partitioning a few times, and no success yet. Each time, GParted reports that there's still sector mis-alignment.

I tried NTFS and ext2 fs formats.

Will it make a difference if I try an MS-DOS partition table, instead of GPT?

I ain't scared of CLI, and the drive is clean. But it must be filled with data, which is a backup for another 3TB, WITH THE SAME PROBLEM  : ohnoes: : ohnoes: : ohnoes:

---

### Post by pctechplus on 2011-11-21
Try HDD Regenerator:

[http://www.dposoft.net/](http://www.dposoft.net/)

Use the bootable CD or USB version and regenerate your sectors.

Good luck!

---

### Post by Telengard C64 on 2011-11-21
> **Moozillaaa said:**
> 3TB,

Does your system support disks that large?

---

### Post by oldfred on 2011-11-22
What exactly is the error? Is this a 4K drive?

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

How to install a WD Advanced Format Drive on a non-Windows Operating System
the following distributions will default to good alignment for Advanced Format disk drives: Ubuntu 10.04, Fedora 13, Redhat 6 and derived products. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)

What do these show?
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

Install gdisk if you do not have it. Old version is in repositories, but better to have newest.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---


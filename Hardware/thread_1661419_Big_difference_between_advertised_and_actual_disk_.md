---
title: "Big difference between advertised and actual disk space"
date: 2011-01-06
forum: Hardware
---

### Post by 3602 on 2011-01-06
Now, on the casing of my portable computer, it says *750GB* HDD.
With Disk Usage Analyzer, however, I see a total system capacity of *676GB*.
So what's up? That can't be Ubuntu and it says I've only "used" 6.4GB. Hidden partition?

EDIT: Additional info.
Doing *sudo fdisk -l* gave me:
> Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007661b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89672   720285696   83  Linux
/dev/sda2           89672       91202    12285953    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5           89672       91202    12285952   82  Linux swap / Solaris


One thing you probably need to understand is that this computer has three bays with a 250GB disk in each bay. Somehow this is identified as one single disk.

---

### Post by Fafler on 2011-01-07
Output of df -h?

It's not just because of the fact that Ubuntu reserves 5% of the filesystem for root, so the system won't crash if it runs out of space?

---

### Post by 3602 on 2011-01-07
Code *df -h* gives:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             677G  6.5G  636G   2% /
none                  1.8G  256K  1.8G   1% /dev
none                  1.8G  184K  1.8G   1% /dev/shm
none                  1.8G  220K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
EDIT: GParted says */dev/sda* is 698.64GB, while as you can see above, *fdisk -l* says [I]Disk /dev/sda: 750.2 GB
[/I]What!?

EDIT II: Or is it because of this here: [http://forums.macrumors.com/showthread.php?t=196571](http://forums.macrumors.com/showthread.php?t=196571)
EDIT III: Ok, after reading this here: [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion) all is clear. Come on, where is ANSI in all this.

---

### Post by cascade9 on 2011-01-08
> **3602 said:**
> EDIT III: Ok, after reading this here: [http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion) all is clear. Come on, where is ANSI in all this.

Yes, its the 'decimal' byte biting again. The whole MB/MiB thing is stupid, they should never have let the HDD manufacturers get away with it. 

ANSI? This is above them, binary measurement (mainly memory now) is from JEDEC standard, 'decimal' is from IEEE/IEC.

---


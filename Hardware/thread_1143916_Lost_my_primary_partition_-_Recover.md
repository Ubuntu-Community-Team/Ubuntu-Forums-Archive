---
title: "Lost my primary partition - Recover ?"
date: 2009-04-30
forum: Hardware
---

### Post by d_ced on 2009-04-30
Hi, 

I've lost yesterday my partition table on one of my USB HD drive. I've done nothing so i still don't know how this partition has been lost. 

Concerning the disk, the only that i'm sure off is the partioning. THere was only one primary partition using the full drive. When it was still functionning, the mount was done on /dev/sdb.

The disk is still recognised at boot but no partition is found. 

When i use gpart, i can't find anything.

When i use parted and issue 'rescue' command, parted returns '/dev/sdb unrecognised disk label'

Is there any chances to restore this disk ? 

Thanks

---

### Post by blackgr on 2009-04-30
```
sudo apt-get install testdisk
```
It will search for lost partitions

---

### Post by caljohnsmith on 2009-04-30
+1 for blackgr's advice to try testdisk for recovering your partition. Is your lost partition NTFS? If so, I would recommend using the latest testdisk to try and recover it, because testdisk versions prior to 6.10 sometimes segfault (crash) when they try to list the directories of NTFS partitions. So to use the latest testdisk, first download the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seems to be the partition you lost. We can work from there if you want.

Cheers,
John

---


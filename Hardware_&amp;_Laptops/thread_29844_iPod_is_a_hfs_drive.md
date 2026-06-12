---
title: "iPod is a hfs drive"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by cusco on 2005-04-26
Hi... I have a brand new iPod mini and I'm using gtkpod for my songs... altho once I disconnected it without umouting it first...

now when I plug it back in it mounts read-only as it shows on dmesg:

**HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.**

ok so I should run fsck...

root@Portatil:/home/cusco # fsck /dev/sda3
fsck 1.35 (28-Feb-2004)
**fsck: fsck.hfs: not found**
fsck: Error 2 while executing fsck.hfs for /dev/sda3
root@Portatil:/home/cusco #

well.. I donloaded this hfsplus from apt...

but I have this error:

root@Portatil:/home/cusco # hpfsck /dev/sda3
*** Checking Volume Header:
Volume was not cleanly unmounted
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
0.01                                            Done ***
*** Checking Backup Volume Header:
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
JSFH                                            Done ***
*** Checking Extents Btree:
                                                Done ***
*** Checking Catalog Btree:
Node 3 with 10 records is damaged trying to fix ***
checkbtree_key_by_index: offset out of range 2200 >= 2000
                                *** Check stopped ***
hpfsck: hpfsck: Invalid key length in record_readkey (Invalid argument)
root@Portatil:/home/cusco # hpfsck /dev/sda3
*** Checking Volume Header:
Volume was not cleanly unmounted
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
0.01                                            Done ***
*** Checking Backup Volume Header:
Volume is inconsistent
Reserved attribute in use: 2000
Volume was last Mounted by unknnown implemenatation:
JSFH                                            Done ***
*** Checking Extents Btree:
                                                Done ***
*** Checking Catalog Btree:
Node 3 with 10 records is damaged trying to fix ***
checkbtree_key_by_index: offset out of range 2200 >= 2000
                                *** Check stopped ***
hpfsck: hpfsck: Invalid key length in record_readkey (Invalid argument)
root@Portatil:/home/cusco #

basically I cannot writte on my iPod because its on read-only mode! what should I do?

thanks

---

### Post by cusco on 2005-04-26
so as you see... I was using it fine with gtkpod. Suddenly it wouldn't mount read-write anymore, only read-only. I had left the original HFS+ filesystem on it, and was learning that there is no fsck.hfsplus for Linux that would clear the INCONSISTENT-bit of my HFS+ filesystem. I tryed mounting it with hpmount and tryed to use hpfsck but I always get an error: 
hpmount: /dev/sda3: Invalid key length in record_readkey (Invalid argument)
or
hpfsck: hpfsck: Invalid key length in record_readkey (Invalid argument)

---

### Post by johndoe on 2005-04-28
This may not be of much help to you, but I have an iPod mini too and it came formatted as hfs. After a bit of messing around I figured it wasn't worth the bother, switched it to vfat (vfat support is very, very mature), adjusted the location in gtkpod preferences and haven't had a problem since.

I have 2nd gen 4G version, the partition table looks like this:

```

Disk /dev/sda: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    0  Empty
/dev/sda2   *           6         497     3951990    b  W95 FAT32

```

sda1 contains the firmware, you can make a backup of it like this,

```

~$ sudo dd if=/dev/sda1 of=~/ipod-firmware.raw

```

You can probably pick up the firmware "somewhere on the net", fdisk your sdX to match this and be good to go (possibly messing up your iPod in the process..) I'm guessing that if you have the 6G version the start and end of sda1 will be the same as will the start of sda2 and the end just the end of the disk. Then mkfs -t vfat sda2 and dd if=firmware of=/dev/sda1 and cross your fingers.. (once again, you could screw up the iPod like this..YMMV).

.. or just cop out and attach it to a Windows machine and let the installer format it and install the firmware for you. Just abort the installation when it asks for the serial number!

---

### Post by cusco on 2005-05-05
thanks! I actually did changed it to a "win ipod". I was searching this forum for answers and someone pointed out this linuxquestions.org thread which had all the step by step commands explaining how to format the ipod in fat32

basically was just back up the firmware and use fdisk on it, two partitions, one with 33Megs for the firmware and another onw with the rest. than copy the firmware back!

thanks again

---


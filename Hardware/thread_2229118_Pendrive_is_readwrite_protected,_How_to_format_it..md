---
title: "Pendrive is read/write protected, How to format it..?"
date: 2014-06-11
forum: Hardware
---

### Post by Varun_C on 2014-06-11
Pendrive is read/write protected, How to format it..?



Please help,

 Thanks.

---

### Post by slickymaster on 2014-06-11
How do you know it's write-protected? Is it encrypted? Does the pen drive has a write protect switch on it, if none, the following command should help:
```
sudo hdparm -r0 /dev/sdb
```

---

### Post by Varun_C on 2014-06-11
Tried the command. resullt is:

/dev/sdd:
 setting readonly to 0 (off)
 readonly      =  0 (off)




Then tried to delete the existing partition in the pen drive using fdisk. The result is

fdisk: unable to write /dev/sdd: Bad file descriptor


Please help on this..

thank you..

---

### Post by slickymaster on 2014-06-11
Plug in your pen drive, and in a terminal run:```
sudo umount /dev/sdb1 ## make sure the pen drive in question is labeled as sdb1
sudo fdisk /dev/sdb
```and when prompted, click the following keys in order: '**d**' (to delete the existing partition) and after '**w**' (to write table to disk and exit).
Once that finished, run again```
sudo fdisk /dev/sdb
```and in order hit '**n**' (to create a new partition), "**Enter**" to other prompts (Enter=default settings) and finally '**w**' (to write table to disk and exit).

---

### Post by Varun_C on 2014-06-11
I Tried the same ...
the above error occurs when I save the changes(**w**).

Thanks..

---

### Post by siepo on 2014-06-15
I think your flash drive just failed. At least, I have had a couple of flash drives that became read-only on their own accord.
I use gparted for partitioning. When I try to format, it thinks it succeeds, but in reality it did nothing. Output of 
```

hdparm /dev/sdb

```
(without options):
```

/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  f0 00 05 00 00 00 00 0a 00 00 00 00 26 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 multcount     =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 15902/64/32, sectors = 32567296, start = 0

```

---


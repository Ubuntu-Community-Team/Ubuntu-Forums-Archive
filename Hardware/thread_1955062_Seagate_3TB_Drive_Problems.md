---
title: "Seagate 3TB Drive Problems"
date: 2012-04-09
forum: Hardware
---

### Post by imwithid on 2012-04-09
Generally I take precautions and test drives under both Windows and Ubuntu before doing something irresponsible, but I was on a tight deadline and now I think I'm stuck.

I just got a 3 TB drive (put into an eSATA enclosure) and created a 2.2 TB partition with the remainder unused (for future expansion or if I end up needing the remainder, I'll create a new partition in a worst case).

This 2.2 TB partition was created using fdisk under the maximum allowable size recommended. All went well and the drive is properly aligned and works well under Ubuntu 10.04.4 x64. I then  copied the contents from an old drive that had to be passed on.

I finally gave it a try through windows XP x64 edition and it detects the hard drive, however, as a raw 4 TB drive.

This is very strange. I was hoping to use this drive to amalgamate data from 5 separate hard drives.

Does anyone know if:

1. This is a maximum sector allocation problem (perhaps it's a few too many for Windows's bounds for NTFS partitions)?

2. This is similar to the first, the allocation unit size needs to be higher than 512 bytes?

3. I'm stuck and need to transfer data and redo everything?

I appreciate any advice.

---

### Post by shakabra on 2012-04-09
If( everything works fine under Linux && You have a live CD/USB)
{ boot into a live environment;
      copy needed files;
{ else you're  screwed.

---

### Post by ajgreeny on 2012-04-09
What filesystem is the 2.2TB partition you made on the disk?  If you did not specify ntfs it will be an ext# partition which windows will not be able to use.  From a ubuntu system, live or installed run command ```
sudo fdisk -l
``` to show what is actually on the disk.

---

### Post by imwithid on 2012-04-10
Perhaps I should expand.

Initially, this drive was setup using fdisk, aligned starting at sector 64. This, however, is not readable under Windows XP

```
sudo fdisk -l -u /dev/sdb

Disk /dev/sdb: 3000.6 GB, 3000592850944 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860532912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x86999998

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              64  4294967294  2147483615+   7  HPFS/NTFS
```

This works well under Ubuntu, however, when I need it, it does not read using Windows.

I then tried creating a GPT disk via Windows, hwoever, it does not read on Ubuntu. I then tried using Disk Utility, GParted and gdisk to create a GPT drive, but neither can be seen using Windows.

This is a case of either or so far. Either it works on Ubuntu or it works on Windows. It will not work on both.

Has anyone any ideas?

---

### Post by imwithid on 2012-04-10
This seems to be an odd problem. All of my external drives (except one) are connected via eSATA. I thought I'd give the USB connection a try and it works. I'm stunned!

Currently, Ubuntu detects the drive (formatted via gdisk and fixed via GParted), but Windows will only detect it if it is connected via USB. Otherwise, the drive is not detected and when I go into Administrative Tools, I am asked to "Initialize the Drive" in order to get it to work (by then, the drive is automatically shrunk to the 2.2TB limit with the remainder as a second partition).

Although I don't like this configuration (having to use a USB cable when using Windows), it'll have to do for now.

Does anyone know why this happens and perhaps a work around?

---


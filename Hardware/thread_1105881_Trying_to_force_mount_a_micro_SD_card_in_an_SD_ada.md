---
title: "Trying to force mount a micro SD card in an SD adaptor on the Dell Studio 15"
date: 2009-03-25
forum: Hardware
---

### Post by jtreach on 2009-03-25
I have been trying to mount my micro SD card using an SD card adaptor in my SD card slot on the Dell Studio 15.

I website suggested doing the following:

> sudo mkdir /media/cardreader
sudo mount /dev/mmcblk0p1 /media/cardreader

This didn't work but I figured out that my device is card mmcblk0 (without the p1) this command results in mount asking for the filesystem. After searching the internet I found that it would probably be fat16. I then tried the following line:

```
sudo mount -t msdos /dev/mmcblk0 /media/cardreader
```

Which resulted in mount moaning it was the wrong filesystem. I then input dsmeg | tail which resulted in this:

```
[  673.185147]   groups: 0 1
[  673.185155] CPU1 attaching sched-domain:
[  673.185158]  domain 0: span 0-1 level MC
[  673.185162]   groups: 1 0
[  764.912291] CE: hpet increasing min_delta_ns to 15000 nsec
[  947.912276] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1694.952916] FAT: bogus number of reserved sectors
[ 1694.952929] VFS: Can't find a valid FAT filesystem on dev mmcblk0.
[ 1734.334147] FAT: bogus number of reserved sectors
[ 1734.334159] VFS: Can't find a valid FAT filesystem on dev mmcblk0.
```

I then tried 'sudo fdisk /dev/mmcblk0' this resulted in the following output:

```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x9ac6b5eb.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1904.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```

At this point it asks for commands but I'm too scared to format it. Can some one guide me through it or help me in any way?

---


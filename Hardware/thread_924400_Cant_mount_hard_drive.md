---
title: "Cant mount hard drive"
date: 2008-09-19
forum: Hardware
---

### Post by Rival904 on 2008-09-19
Ok I am having a hard time trying to mount this hard drive. 

The drive itself came out of a NAS drive like you would buy at BestBuy of the sort, it HAD a bunch of data on it, not sure if it does, my goal is to recover it, if possible. 


The drive is a 400GB Seagate. 

I did the "sudo fdisk -l" and came back with


```

Disk /dev/sda: 80.0 GB, 80060424192 bytes

255 heads, 63 sectors/track, 9733 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xd7d3d7d3



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        9356    75152038+  83  Linux

/dev/sda2            9357        9733     3028252+   5  Extended

/dev/sda5            9357        9733     3028221   82  Linux swap / Solaris



Disk /dev/sdb: 400.0 GB, 400088457216 bytes

255 heads, 63 sectors/track, 48641 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00000000



Disk /dev/sdb doesn't contain a valid partition table

```

Any ideas? There is only 2 hard drives on this system, the 80Gb samsung that the OS is on, and this 400GB one. 

Any help would be GREATLY appreciated.

---

### Post by andrewc6l on 2008-09-19
If you're trying to recover the data on the drive, it's not looking too likely without a lot of work, I'm afraid. You might get lucky: the NAS might have just used the whole drive without a partition table.

sudo mount -o ro /dev/sdb /mnt

If that works and you see stuff under /mnt, you're in good shape. If it doesn't, the data is still there but reconstructing it is probably harder than you want to do.

If you're just trying to use the drive and not recover the data, you can fdisk it, create partitions the way you want, mkfs the partitions and mount them. A tutorial on that is here:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---


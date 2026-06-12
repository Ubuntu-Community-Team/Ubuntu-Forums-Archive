---
title: "FATAL ERROR: Bad primary partition 2: Partition ends in the final partial cylinder"
date: 2010-05-15
forum: Hardware
---

### Post by loklaan on 2010-05-15
Hi there!

I was moving my vista partition with GParted when about halfway through it got an error and stopped. I haven't been able to access it at all, its lost its recognition as the vista partition and is just 'unknown' to GParted.

This is the error I get when running cfdisk.
```
FATAL ERROR: Bad primary partition 2: Partition ends in the final partial cylinder
```

And this is what comes out with fdisk. /dev/sda2 is the Vista partition
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3bef74b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            1021       16220   122094000    7  HPFS/NTFS
/dev/sda3           16221       30402   113905665    f  W95 Ext'd (LBA)
/dev/sda5           16221       25180    71962624    7  HPFS/NTFS
/dev/sda6           25180       30182    40175616   83  Linux
/dev/sda7           30182       30402     1765376   82  Linux swap / Solaris

```

I would like to be able to recover the partition if possible. :(

---

### Post by srs5694 on 2010-05-15
First, it's generally recommended to use Windows' own tools to resize Windows partitions. Now you know why. I'm sorry you had to learn about this the hard way.

Second, could you please post the output of "sudo fdisk -lu" rather than just "sudo fdisk -l". Adding the "u" changes the reporting unit from cylinders to sectors, which may be important in diagnosing at least some of the problems.

Third, what does "sudo blkid /dev/sda2" produce?

Broadly speaking, if "sudo fdisk -lu" shows that you've got overlapping partitions, that problem will have to be corrected. (The extended and logical partitions are partial exceptions; all logical partitions must reside entirely inside your extended partition, /dev/sda3.) If blkid can't identify the filesystem in /dev/sda2, then the partition's start point is probably wrong and will have to be adjusted. It looks like you've got some free space at the start of the disk, so unless you have a backup of the original partition table, testdisk may be your best bet to do this, if it becomes necessary; however, since your resize operation aborted mid-way, it's likely that the filesystem will be damaged -- perhaps just moderately, but maybe beyond repair. If you've got vital personal files on the partition, it's conceivable that you'll be able to recover at least some of them with [PhotoRec.](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by loklaan on 2010-05-15
fdisk -lu
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3bef74b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2        16386300   260574299   122094000    7  HPFS/NTFS
/dev/sda3       260585470   488396799   113905665    f  W95 Ext'd (LBA)
/dev/sda5       260585472   404510719    71962624    7  HPFS/NTFS
/dev/sda6       404512768   484863999    40175616   83  Linux
/dev/sda7       484866048   488396799     1765376   82  Linux swap / Solaris
```


And "sudo blkid /dev/sda2" didn't receive any feedback.. So can PhotoRec still recovery data when the filesystem can't be detected? Most of this is new to me :) Thanks for being so helpful!

---

### Post by loklaan on 2010-05-15
Using testdisk from the Ubuntu Software Center. Copying things I need, its working so far :)

Thanks again, you were awesome!

---

### Post by srs5694 on 2010-05-15
FWIW, I don't see anything wrong with your partitions. (That's not to say that the filesystems they contain are all OK.) I suspect the cfdisk error message you report is a result of a relatively recent change in how most utilities align partitions. In the past, they were aligned on cylinder boundaries, a "cylinder" being (today) an entirely fictitious construct that's not very useful. Since Windows Vista, Microsoft has been aligning partitions on 1MB boundaries, since this optimizes performance on RAID, SSD, and the latest "Advanced Format" drives with 4096-byte sectors. Linux utilities now follow this example, although the change is new enough that it might not be present on your system. (You'd need util-linux 2.17 or later, preferably 2.17.2.) My suspicion is that cfdisk was applying cylinder-alignment assumptions to a disk that didn't meet those assumptions and it overreacted. This has nothing to do with the problems accessing the filesystem in /dev/sda2, which were caused by an interrupted partition resize operation.

Best of luck with your recovery efforts!

---


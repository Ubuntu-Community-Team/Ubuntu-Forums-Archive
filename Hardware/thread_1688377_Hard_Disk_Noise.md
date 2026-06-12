---
title: "Hard Disk Noise"
date: 2011-02-15
forum: Hardware
---

### Post by justjustin on 2011-02-15
Hi,
I've started getting strange disk noises in Maverick, as if the HDD is constantly being accessed or written to. By constantly, I mean once a second for 5-10 seconds, then a pause for a couple of seconds and repeat, endlessly. This is extremely annoying.

Could this have something to do with my partitioning? - I have tried swapoff and it persists.
Has anyone else encountered similar problems?

Any help greatly appreciated,
Thanks in advance,
Justin

---

### Post by arsenic23 on 2011-02-15
Close any CPU intensive applications and run top.  If something is using your hard drive that much it might should also be using the CPU a bit.

---

### Post by justjustin on 2011-02-15
Hi,
Thanks for the response,

top gives me:

> PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND   
20   0  376m  61m  21m S    3  1.5   2:32.57 compiz                                  
20   0  263m  63m  18m S    1  1.6   5:52.79 Xorg                                     
20   0  750m 108m  32m S    1  2.7   5:58.68 firefox-bin                              
20   0 19276 1324  944 R    1  0.0   0:00.07 top                                      
20   0     0    0    0 S    0  0.0   0:02.34 events/0                                 
20   0 19276 1324  944 S    0  0.0   0:01.19 top

---

### Post by justjustin on 2011-02-15
Just to give a bit more info, my drive is partitioned like this:

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04a17a65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       26122   209715200    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           26122       26187      524288   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           26187      121602   766417921    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           26187       28537    18874368   83  Linux
/dev/sda6           28537       35064    52428800   83  Linux
/dev/sda7           35064       36748    13526016   82  Linux swap / Solaris
/dev/sda8           36748      121602   681585664    7  HPFS/NTFS

/sda3  /boot   ext2
/sda4          extended
/sda5  /       ext4
/sda6  /home   ext4
/sda7          linux-swap

/sda8 this is my ntfs "storage" partition

Win7 installed a few months before, then shrunk using GParted on live cd and other partitions created manually on live cd. Win7 does not suffer this noise problem.

Do I have too many partitions?
Is my swap "Too Big" and causing some issue?

I also came across this post, it's old but sounds like a similar issue, [http://ubuntuforums.org/showthread.php?t=5617]("http://ubuntuforums.org/showthread.php?t=5617")

Thanks in advance

---

### Post by tgalati4 on 2011-02-15
Page through dmesg and post anything that looks suspicious:

dmesg | more    (spacebar to page forward, q to quit)

---

### Post by justjustin on 2011-02-15
Hi, Thanks for the response,

I'm not fully sure what I should be looking for, but I did notice these:

> [    1.690316] ata1.00: ATA-8: Hitachi HDS721010CLA332, JP4OA39C, max UDMA/133
[    1.690322] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.730336] ata1.00: configured for UDMA/133
[    1.730477] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72101 JP4O PQ: 0 ANSI: 5
[    1.730674] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.730701] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.730815] sd 0:0:0:0: [sda] Write Protect is off
[    1.730819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.730854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

> [   19.923442] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[   19.923451] EXT4-fs (sda5): write access will be enabled during recovery
[   20.176610] EXT4-fs (sda5): orphan cleanup on readonly fs
[   20.176624] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 349
[   20.176730] EXT4-fs (sda5): 1 orphan inode deleted
[   20.176737] EXT4-fs (sda5): recovery complete
[   20.360525] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)

> [   42.103592] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   42.383378] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0

> [   45.996534] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   49.141013] EXT4-fs (sda6): re-mounted. Opts: user_xattr,commit=0

---


---
title: "auto-mount fails on external HD in 8.04"
date: 2008-06-17
forum: Hardware
---

### Post by tripod on 2008-06-17
I have 2 partitions, one formatted as an EXT3-partition, and one formatted as a FAT32-partition.
At the beginning, my external harddisc were mounted okay (the mounted partitions were showed at the desktop), but, in my opinion, at a wrong place in my system. Therefore I right-clicked on the partitions icon, choosed Properties > Volume > Settings > Mount Point and wrote "/mnt/sdb1".

Because of that, I'm now unable to mount my sdb1-partition (the one with FAT32), with the argument ```
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)
```
How can I change things back to normal?

My /etc/fstab (with the external HD plugged in):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=7d1b0eed-d7d1-459b-a909-df56e710af9c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=0e2fa1a3-795b-40d2-a484-f6ab173b0c1c /home           ext3    relatime        0       2
# /dev/sda5
UUID=3d9938b5-ca8e-4128-9258-b1ac1e94e802 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
And the output from fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47fa12fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7181    57673350    7  HPFS/NTFS
/dev/sda2           18773       19457     5496120   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            7522       18772    90373657+   f  W95 Ext'd (LBA)
/dev/sda5            7523        7784     2104515   82  Linux swap / Solaris
/dev/sda6           16271       18772    20097283+   c  W95 FAT32 (LBA)
/dev/sda7            7785       10395    20972826   83  Linux
/dev/sda8           10396       16270    47190906   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000071c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       39894   320448523+   b  W95 FAT32
/dev/sdb2           39895       60801   167935477+  83  Linux

```
Post Scriptum: My EXT3-partition (sdb2) mounts okay.

---

### Post by tripod on 2008-06-17
Argh damn. Right after I clicked the "submit post"-button I found a link in another thread on this forum, answering my question. For the interested, the answer can be found [here](http://ubuntuforums.org/showthread.php?t=376404#10). Thanks for the help to "staticsage".

My problem now is, that only root is allowed to see the content on the FAT32-partition, how can I change that? I tried opening Nautilus as root, and change the owner on the folder were my harddisk is mounted, but Nautilus gives me this error: ```
Sorry, couldn't change the owner of "EKSTERN": Error setting owner: Operation not permitted
```

How do I solve this one? (I'm completely new to Gnome, I've used OpenSuse with KDE before)

---


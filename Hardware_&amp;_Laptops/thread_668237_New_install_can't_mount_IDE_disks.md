---
title: "New install can't mount IDE disks?"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by Kablooie!! on 2008-01-15
Hi all,

I tried posting this in the Installation forum and got no answers, so I thought I'd try here:


Hi all,

This is a strange one (to me, anyway).

I did a fresh install of the latest Ubuntu on my machine.  It's a dual 1.7GHz Xeon Compaq EVO  machine with 1G of RAM.  The boot/OS disk is an old 40G drive.  

I have a 320G IDE drive installed (had it in previous Linux install on this machine - no hardware has changed).  It worked fine.  

After successfully installing the latest Ubuntu, I made a mount point for the disk and mounted it via this entry in /etc/fstab:

```
/dev/sdb1      /video          xfs     rw,user,noauto,exec 0   1

```
Initially mounted it manually with:

```
mount /video
```

Worked fine.  I verified that it was there and that I could access the data. 

Then I rebooted the machine and found that I couldn't access the disk any more!

It wasn't mounted, and when I tried to mount it, I got:

```
root@mythbox:~# mount /video
mount: /dev/sdb1 already mounted or /video busy
root@mythbox:~# df -k /video
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   4000088  30971552  12% /
root@mythbox:~# fuser /video
root@mythbox:~# df -k|grep sdb
root@mythbox:~# umount /video
umount: /video: not mounted
```

I tried moving the mount point aside and using a different mount, no joy.  I tried manually mounting it with:

```
root@mythbox:~# mount -t xfs /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy
```


I was able to run xfs_check and xfs_repair on /dev/sdb fine.  I did a 

```
dd if=/dev/sdb1 of=/tmp/foo bs=8132
```

waited a bit, hit Control C, and then "file /tmp/foo" and it said it was an XFS filesystem, as expected.

... strange...

I had been meaning to install the second 320G IDE drive, so this seemed like a good time to do it.

I popped the drive in, partitioned it as one big primary partition, set the partition type to Linux, and created an ext3 filesystem on it.  Then I created a /video2 mount point and mounted the new disk just fine.  Verified that I could write to it, and added it to /etc/fstab as follows:

```
/dev/sdc1      /video2         ext3    rw,user,noauto,exec 0   1
```

The next time I rebooted, I couldn't access EITHER disk!  The bootup process failed partway through, indicating that /dev/sdb1 and /dev/sdc1 couldn't be checked by fsck because they were already mounted, or the mount point was busy.  It left me in administrative mode.  I commented out the fstab entries (after trying to mount them, fsck them, etc with the same failure), and booted up.

Does anyone have any idea what the heck is going on?  Is there perhaps some sort of hardware/BIOS thing that is preventing linux from mounting these things properly?

Here's some reference material that might be useful (sorry for making this post so long-winded but I wanted to try to pre-answer all the questions you might ask):

```
root@mythbox:~# fdisk -l /dev/sdb

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


root@mythbox:~# fdisk -l /dev/sdc

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998b6635

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux

root@mythbox:~# mount /dev/sdb1 /mnt
mount: /dev/sdb1 already mounted or /mnt busy

root@mythbox:~# df -k /mnt
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   4000088  30971552  12% /
root@mythbox:~# df |grep sdb
root@mythbox:~# mount /dev/sdc1 /mnt
mount: /dev/sdc1 already mounted or /mnt busy

root@mythbox:~# df |grep sdc

root@mythbox:~# dmesg |grep sdb
[   66.937580] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   66.937604] sd 1:0:1:0: [sdb] Write Protect is off
[   66.937609] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   66.937644] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.937753] sd 1:0:1:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   66.937774] sd 1:0:1:0: [sdb] Write Protect is off
[   66.937778] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   66.937812] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.937817]  sdb: sdb1
[   66.957336] sd 1:0:1:0: [sdb] Attached SCSI disk
root@mythbox:~# dmesg |grep sdc
[   66.957468] sd 2:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   66.957493] sd 2:0:1:0: [sdc] Write Protect is off
[   66.957498] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   66.957533] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.957633] sd 2:0:1:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   66.957658] sd 2:0:1:0: [sdc] Write Protect is off
[   66.957663] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[   66.957696] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   66.957703]  sdc: sdc1
[   66.975678] sd 2:0:1:0: [sdc] Attached SCSI disk
```


Any help or suggestions would be greatly appreciated!

Thanks,
Grant

---


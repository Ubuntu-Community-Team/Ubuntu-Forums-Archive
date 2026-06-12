---
title: "partition table lost in Gparted"
date: 2009-10-10
forum: Hardware
---

### Post by JakcV on 2009-10-10
I try to resize my hard disk partition to make room for Karmic Koala Beta using Live USB. While I am resizing, power down suddenly. The partition is corrupted and unable to boot. Then I search online, and found the testdisk program. It recover my partition and I am able to boot to my ubuntu. However, the partition is not showed up at Gparted. When i use fdisk -l, ubuntu can recognize all the partition. 
Now i am not able to install the new ubuntu, because i still have other thing in other partition. In the installation, the partition just show up like Gparted. One huge unformated partitiion.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57ad6c4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            5319       11655    50901952+   c  W95 FAT32 (LBA)
/dev/sda3           11656       18181    52420095    f  W95 Ext'd (LBA)
/dev/sda4           18182       19458    10257502+   7  HPFS/NTFS
/dev/sda5           11656       17932    50419971   83  Linux
/dev/sda6           17933       18181     2000061   82  Linux swap / Solaris
partition_table (END) 
```


[COLOR="DarkRed"]Solution:[/COLOR]
What I did is backup the partition then delete it by using fdisk. Then write back the partition table. Then the partition table is correct now.
Can create back the partition with Gparted now.

---

### Post by prshah on 2009-10-10
> **JakcV said:**
> In the installation, the partition just show up like Gparted. One huge unformated partitiion.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
<snip>
/dev/sda6           17933       18181     2000061   82  Linux swap / Solaris
partition_table (END) 
```

From the live CD, open a terminal (Applications-Accessories-Terminal) and give the command ```
gparted
``` Post back the output messages, for a clue as to what is wrong.

---

### Post by JakcV on 2009-10-10
```
ubuntu@ubuntu:~$ gksu gparted
======================
libparted : 1.8.9
======================
Can't have a partition outside the disk!
```

This is the output from the liveCD, when i type gparted at gnome-terminal.

---

### Post by theozzlives on 2009-10-10
> **JakcV said:**
> ```
ubuntu@ubuntu:~$ gksu gparted
======================
libparted : 1.8.9
======================
Can't have a partition outside the disk!
```

This is the output from the liveCD, when i type gparted at gnome-terminal.

try live CD and do:
```
sudo fsck /dev/sda5
```

---

### Post by JakcV on 2009-10-10
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 149635/3153920 files, 3006055/12604992 blocks
```

Thanks for replying.

---

### Post by prshah on 2009-10-10
> **JakcV said:**
> 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, [color=red]19457[/color] cylinders
   Device Boot      Start         End      Blocks   Id  System
<snip>
/dev/sda4           18182       [color=red]19458[/color]    10257502+   7  HPFS/NTFS
<snip>
```

> **JakcV said:**
> ```
ubuntu@ubuntu:~$ gksu gparted
Can't have a partition outside the disk!
```


Though your hard disk is listed as having 19457 cylinders, your /dev/sda4 partition seems to be ending on 19458, which is causing gparted to barf.

You can manually change this using linux's fdisk program, but it is risky and you'd better have a backup. Post back if you want / need more details.

---

### Post by JakcV on 2009-10-10
Can i just use the fdisk on /dev/sda4? It is my recovery partition for window. Will it cause other partition to be unusable?

---

### Post by JakcV on 2009-10-10
When i use the cfdisk to check the hard disk. The problem occur. The program did not execute. "partition end after disk"

---

### Post by JakcV on 2009-10-10
I change the cyclinder of /dev/sda4 and the output is 
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

I restart now. Hopefully, can have back the partition table.

---

### Post by JakcV on 2009-11-03
What I did is backup the partition then delete it by using fdisk. Then write back the partition table. Then the partition table is correct now.
Can create back the partition with Gparted now.

Thanks for helping.

---

### Post by tollboy on 2010-03-31
i am having the same problem.
but i cant delte my partition...
as there is lots of data.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fac8fac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5103    20506972+  83  Linux
/dev/sda3            5104        5350     1984027+  82  Linux swap / Solaris
/dev/sda4            5351       19458   113322510    f  W95 Ext'd (LBA)
/dev/sda5            5351       19457   113314446    c  W95 FAT32 (LBA)
```


somebody tell me how to edit the cylinder used by extended partition

---

### Post by tollboy on 2010-03-31
my problem is solved....


got answer from here 
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---


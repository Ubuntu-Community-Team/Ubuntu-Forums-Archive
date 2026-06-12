---
title: "partitions on invalid boundaries"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by fangorious on 2006-02-27
I seem to have a problem where my partitions aren't on valid cylinder boundaries. It seems to be manifesting itself by making my swap partition (hda6) unrecognizable at boot time. I can fomat and activate the partition without problem after the machine is booted, but it is gone at the next reboot. Can anyone give me pointers on how to fix this user parted or gparted? Note below that hda2 and hda4 are not in the extened partition, just hda5 and hda6.

```

[justin@justinxp ~]
$ sudo fdisk -l /dev/hda
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2714    20517808+   7  HPFS/NTFS
/dev/hda2            5078        5945     6555465   83  Linux
/dev/hda3            5946        7752    13655250    5  Extended
/dev/hda4            2715        5076    17854357+  83  Linux
/dev/hda5   *        5946        7674    13060813+  83  Linux
/dev/hda6            7674        7752      594373+  82  Linux swap / Solaris

Partition table entries are not in disk order
[justin@justinxp ~]
$ sudo parted /dev/hda print
Disk geometry for /dev/hda: 0kB - 60GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    21GB    21GB    primary   ntfs         boot
4       21GB    39GB    18GB    primary   ext3
2       39GB    46GB    6713MB  primary   ext3
3       46GB    60GB    14GB    extended
5       46GB    59GB    13GB    logical   ext3         boot
6       59GB    60GB    609MB   logical
Information: Don't forget to update /etc/fstab, if necessary.

[justin@justinxp ~]
$

```

---


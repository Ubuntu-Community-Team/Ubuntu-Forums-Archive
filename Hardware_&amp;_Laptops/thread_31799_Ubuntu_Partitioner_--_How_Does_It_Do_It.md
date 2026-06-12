---
title: "Ubuntu Partitioner -- How Does It Do It?"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Xian on 2005-05-04
I just can't figure out how the Ubuntu Install-CD partitioner handles the extended partition that it creates when I manually set up the hard drive. Listed below are a couple of quick illustrations to show you what I mean. 

This is the output of 'fdisk -l' under a hda 1-9 partition scheme. Notice that the end point of the extended partition on hda4 matches exactly the one shown for hda9. At this stage there is approximately 70GB of free space on the drive.

```
# fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3265    26223687    7  HPFS/NTFS
/dev/hda2            3266        4480     9759487+  83  Linux
/dev/hda3            4481        5939    11719417+  83  Linux
/dev/hda4            5940       10572    48933990    5  Extended
/dev/hda5            5940        6061      979933+  82  Linux swap / Solaris
/dev/hda6            6062        6669     4883728+  83  Linux
/dev/hda7            6670        8128    11719386   83  Linux
/dev/hda8            8129       10560    19535008+  83  Linux
/dev/hda9           10561       10572       96358+  83  Linux
```

Okay, now after this I went back and used the Install-CD partitioner to create another partition from the available free space. It did so perfectly, and when I rebooted into my system I again ran a 'fdisk -l' command to check on the current disk scheme. Listed below is that output and notice once again that the end points on both the extended partition and the last partition (in this case hda10) are the same.

```
# fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3265    26223687    7  HPFS/NTFS
/dev/hda2            3266        4480     9759487+  83  Linux
/dev/hda3            4481        5939    11719417+  83  Linux
/dev/hda4            5940       12031    48933990    5  Extended
/dev/hda5            5940        6061      979933+  82  Linux swap / Solaris
/dev/hda6            6062        6669     4883728+  83  Linux
/dev/hda7            6670        8128    11719386   83  Linux
/dev/hda8            8129       10560    19535008+  83  Linux
/dev/hda9           10561       10572       96358+  83  Linux
/dev/hda10          10573       12031    11719386   83  Linux
```

How and WHY does the partitioner keep adjusting the end disk point for the extended partition instead of just setting it up initially for the entire remaining space on the drive? Wouldn't this make it impossible for a program like gparted to add additional logical partitions since it always appears that there are no free sectors available? In fact, when I used fdisk and told it to create a new partition from the command line that is precisely the error message that I received.

I've just never seen it handled this way before and can't see why it is desirable.

---


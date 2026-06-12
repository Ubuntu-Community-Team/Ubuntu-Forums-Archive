---
title: "Buffer I/O error on USB hdd, visible on fdisk, not on gparted"
date: 2011-06-07
forum: Hardware
---

### Post by MattP220 on 2011-06-07
I've got an external USB hdd that has three partitions on it -- one for the filesystem, a separate /home partition, and then a /files partition which I used for file backups.

This disk is plugged into a USB cradle. Just a bit ago, I turned the drive on and all three partitions mounted. Then we had a brief power flicker and the drive briefly unmounted before automatically reconnecting. After that, nautilus started chewing up CPU cycles and I couldn't get the now-re-mounted hdd to respond to unmount commands. 

After a forced reboot, I can access my / and /home partitions, but the /files partition is gone, as in I can't see it under GParted and dmesg spits out this:

```
[ 1302.573772] Buffer I/O error on device sdc, logical block 53711319
[ 1305.586385] sd 8:0:0:0: [sdc] Unhandled sense code
[ 1305.586394] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1305.586402] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 1305.586412] sd 8:0:0:0: [sdc] Add. Sense: Unrecovered read error
[ 1305.586420] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 19 9c 8e b8 00 00 08 00
[ 1305.586438] end_request: I/O error, dev sdc, sector 429690552
[ 1305.586448] Buffer I/O error on device sdc, logical block 53711319
```

But fdisk still shows the partition:

```
matt@matt-home:~$ sudo fdisk -l

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000713c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2432    19535008+  83  Linux
/dev/sdc2            2433       26747   195310237+   5  Extended
/dev/sdc3           26748       75378   390628507+  83  Linux
/dev/sdc5            2433       26747   195310206   83  Linux
```

The missing drive is /dev/sdc3

I can access sdc1, 2, and 5 just fine -- they mount and they show up on GParted. It's just sdc3 that's being troublesome and spitting out the buffer I/O errors. 

I'm currently running testdisk, and it picked up /dev/sdc3. I'll update the thread if it turns up anything more.

In the mean time, any ideas here? Is this a recoverable error or is this more likely a hardware screwup?

---

### Post by MattP220 on 2011-06-07
testdisk gives me a read error where /dev/sdc3 begins on the disk:

```
Read error at 26747/0/7 (lba=429690561)
```

But it still recognizes the partition and displays its label and size correctly.

---

### Post by MattP220 on 2011-06-08
I've now tried to write new partition tables with testdisk twice, and after reboot there's no changes -- fdisk still shows /dev/sdc3 there, testdisk recognized the volume and label both times, and after this second try it still won't show up as a mountable volume. 

I'm stuck now, can anybody help?

---


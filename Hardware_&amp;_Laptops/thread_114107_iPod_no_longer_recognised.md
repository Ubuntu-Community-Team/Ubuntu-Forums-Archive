---
title: "iPod no longer recognised"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by GoUbuntu on 2006-01-07
My iPod (3G) used to work OK, now Ubuntu doesn't even seem to know that it's plugged in (and the screen on the iPod does not change to "Do not disconnect").

I've tried sudo /etc/init.d/hotplug restart, no joy.

Here's the output from sudo fdisk -l when the iPod is plugged in.  I am dual booting XP on another 40G drive.  I can't see the iPod anywhere:

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         262     2104483+  1b  Hidden W95 FAT32
/dev/hda2   *         263        4997    38033887+   7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4694    37704523+  83  Linux
/dev/hdd2            4695        4870     1413720    5  Extended
/dev/hdd5            4695        4870     1413688+  82  Linux swap / Solaris
```

In Users and Groups, I've added hal and my user to:
1. cdrom
2. disk
3. floppy
4. plugdev
5. hal

After I plug the iPod in:
dmesg | tail
```
[4304996.952000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4304997.210000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4305002.330000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[000a2700020e613 a]
[4305051.943000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4305051.943000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a2700020e6 13a]
[4305193.451000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4305193.451000] ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[000a2700020e613 a]
[4305193.451000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4305193.710000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4305193.711000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
```

I'd appreciate any ideas to get this working.

---

### Post by Amon_Re on 2006-01-08
Is the iPod still working? Properly charged? iPods are odd little bits of hardware, if the battery charge level is to low, they won't initiate their usb connection untill it's recharged, even if the usb port itself is powered.

If the battery is good, and it still doesn't sync, try plugging it in another computer to rule out a possible problem with the datacable.

---


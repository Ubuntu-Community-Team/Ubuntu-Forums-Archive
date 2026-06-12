---
title: "Errors while reading data from hard disk"
date: 2008-06-12
forum: Hardware
---

### Post by Raziel. on 2008-06-12
Hi,

I've got strange problem with Ubuntu. While I'm reading data from my hard disk, data errors occur. It appears by:
- when listening some mp3's in rhythmbox sometimes playing hangs, song stops. sometimes I also hear some "noises" during playing songs.
- when I unpack some archives (for example *.tgz) CRC errors occur.

There are NO bad sectors at my hard disk.

At Debian everything is all right - the same songs play OK, and archives unpack also without errors.

I have no idea how to debug this.

Here are some useful informations:
- my system: **Ubuntu 8.04 (at 7.10 were the same errors)**,
- my hard disk: **Seagate 120 GB Barracuda ATA**,
- **fdisk -l**:
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef88ef88

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1824    14651248+  83  Linux
/dev/hda2            1825        9788    63970830    5  Extended
/dev/hda3   *        9789       12161    19061122+   7  HPFS/NTFS
/dev/hda4           12162       14593    19535040    c  W95 FAT32 (LBA)
/dev/hda5            1825        1886      497983+  82  Linux swap / Solaris
/dev/hda6            1887        9788    63472783+  83  Linux
```

Help!

---


---
title: "NTFS HD Vanished"
date: 2008-11-10
forum: Hardware
---

### Post by ctopel on 2008-11-10
Hey Ubuntu Forums - this is my first post ever. I did use the search function to try to find an answer, but nothing seemed like it could help. I'm new(ish) to Ubuntu and having the following problem:

Recently I installed 8.10 and it detected both of my hard drives just fine (one is SATA, the other IDE) after I used ntfs-3g to force them to mount. Afterwards, they showed up in my Places -> System. Recently I tried to boot in to Windows again. I got the error "NTLDR is missing". I booted back to linux and the secondary windows drive had gone missing. I'll break this down a bit further.

Hard Drives(2):
/dev/sda1 (80.2GB Drive): Misc Files. Movies/Music/Etc : NTFS Format
/dev/sdb1 (72.7GB Drive): Primary Windows Partition. : NTFS Format
/dev/sdb5 (7.0GB Drive): Primary Linux Partition : EXT3 Format

Here's the read-out of fdisk-l:
```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc76a2e33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10007    80381196    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x672fb9b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8835    70967106    7  HPFS/NTFS
/dev/sdb2            8836        9729     7181055    f  W95 Ext'd (LBA)
/dev/sdb5            8836        9729     7181023+  83  Linux

```

So, somehow fdisk is able to see my secondary drive like it did before. Here's the kicker though - when I try to mount I get:

```

blah@blahblah:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

So, all of this seems crazy because just a few days ago everything worked fine and even though the drive didn't show up I could at least force it to mount. 

If anyone has ideas, I'd love to hear them. I'll be punctual in my responses and glad to print out whatever you need me to so I can get this working. I'd like to listen to my music again. :P

Thanks in advance, 
Chris

---

### Post by ctopel on 2008-11-10
Bump.

Anyone?

---


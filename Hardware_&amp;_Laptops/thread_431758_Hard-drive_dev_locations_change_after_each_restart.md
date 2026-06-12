---
title: "Hard-drive /dev/ locations change after each restart?"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by khughitt on 2007-05-03
Hi,

I have an odd problem i hoped someone might be able to shed some light on. Since i've upgraded my desktop to feisty, each time i reboot, my hard-drives have are located in different places under /dev/ ! At least, they change back and forth, seemingly at random, between two configurations. This is a big pain because my single FSTAB will only mount the drives now when they are located in the right place.. I have a total of 3 hard-drives, two of which each have a single large ntfs / fat32 partition, and a third that is partitioned into ntfs , ext3, swap, etc to dual boot win + linux.

Here is what i get from fdisk after two different restarts:

_Config One_

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9944    79875148+   7  HPFS/NTFS
/dev/sdb4            9945       16191    50179027+   5  Extended
/dev/sdb5           12495       13004     4096543+  82  Linux swap / Solaris
/dev/sdb6           13005       16191    25599546   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36483   293049666    c  W95 FAT32 (LBA)
```

_Config Two (One restart later...)_

```

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9944    79875148+   7  HPFS/NTFS
/dev/sda4            9945       16191    50179027+   5  Extended
/dev/sda5           12495       13004     4096543+  82  Linux swap / Solaris
/dev/sda6           13005       16191    25599546   83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    c  W95 FAT32 (LBA)

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

```

The only possible thing i could come up with is that it has to do with the jumpers being set to auto-detect whether they are primary / slave drives, but this has never been a problem in the past with XP or Edgy.

Anyone have any suggestions?

Thanks,

---

### Post by jack1254 on 2007-05-04
You could consider using UUIDs in your /etc/fstab file instead of "/dev" locations. Change, for example:

```
/dev/sda1    /    ext3   nouser,defaults,...
```

to:

```

UUID=v5i4m9mv-45gf-4f54f-f5f    /    ext3   nouser,defaults,...
```

Find the UUID of sda1 with:

```
sudo vol_id -u /dev/sda1
```

---

### Post by strikeback03 on 2007-05-04
now what if it says it can't find a UUID?

---

### Post by khughitt on 2007-05-06
Great! That worked like a charm. Thanks! :)

---

### Post by LukeGX on 2008-04-17
Thanks jack1254, your solution also worked for me!

---


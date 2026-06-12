---
title: "Imminent disk failure - unable to mount disk"
date: 2010-02-11
forum: Hardware
---

### Post by damnated on 2010-02-11
According to Ubuntu, one of my hard drives is failing, and advices that i backup my data. However i can't seem to mount the drive. It is not available from /media and i can't mount it with ```
mount -t ntfs-3g /dev/sda1 /media/disk -o force
```, it says there is no sda1, although ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c540c54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/sda2            3041       30400   219769200    f  W95 Ext'd (LBA)
/dev/sda5            3041       30400   219769168+   7  HPFS/NTFS

``` there is.If i try to mount only sda, it says 
```
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```Any ideas?

---


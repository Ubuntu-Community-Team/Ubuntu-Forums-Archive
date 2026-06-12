---
title: "[SOLVED] Disk Renumbering"
date: 2008-07-12
forum: General Help
---

### Post by fahadsadah on 2008-07-12
Hi all,
I have 2 partitions on sdb:
```
[0750]501:~ sudo fdisk -l /dev/sdb
[sudo] password for fahad: 

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ebf8a8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5442    43712833+   7  HPFS/NTFS
/dev/sdb3            5443       10011    36700492+   7  HPFS/NTFS
[0750]502:~ 

```(yes, that [0750]501:~ thing IS my prompt!)

How do I change the second drives number to sdb2? (there was an sdb2 previously, but I deleted it, thus leaving myself with this).

---

### Post by dcstar on 2008-07-12
> **fahadsadah said:**
> Hi all,
I have 2 partitions on sdb:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5442    43712833+   7  HPFS/NTFS
/dev/sdb3            5443       10011    36700492+   7  HPFS/NTFS

```

How do I change the second drives number to sdb2? (there was an sdb2 previously, but I deleted it, thus leaving myself with this).

You don't - that is the way things are meant to be.

If you want a new second partition, then create one and it will probably be sdb2.

---

### Post by fahadsadah on 2008-07-12
No simple renaming method?

OK, thanks. It's not causing much trouble right now, so I'll leave it as it is.

---


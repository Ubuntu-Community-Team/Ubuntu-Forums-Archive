---
title: "USB Flash memory stick won't mount on insertion?"
date: 2008-12-28
forum: Hardware
---

### Post by Julian David Pitt on 2008-12-28
I have a Corsair flash voyager memory stick that refuses to mount. Please see attached image for the error message I receive. The drive is fat32 but Intrepid seems to think it is NTFS in the error message. However if I do ```
fdisk -l
```
I get
```
Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   IdSystem
/dev/sdb1   *           1         984     7897056+   bW95 FAT32
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)
```
At some point I also get the DBUS error in the second image, sorry not sure what brought it up though. This problem  has been with me since I upgraded from Hardy.. Your help is much appreciated.

---

### Post by corsairgt on 2009-01-21
I've installed half a dozen USB flash drives with Ubuntu v8.10. Although Corsair guarantees that their drives are compatible with Linux v2.4 or later, the current Corsair Flash Voyager and FV/GT 4, 8 and 16 GB drives are NOT compatible with Ubuntu v8.10. 

At present, Corsair offers no explanation or solution. However, my older 4, 8 GB FV batches number beginning 080xxxxx are compatible. You may try to scavenge in your local market for the older fingers. The batch no. is listed on the packing.

Other brands which I have found to be compatible are:-

- A Data 8 GB Xupreme XPG  
- Toshiba 8 GB TransMemory

---

### Post by Julian David Pitt on 2009-01-22
Thanks for taking the trouble to reply, i had no idea there was a problem with the stick itself. Many thanks Corsairgt.

---

### Post by corsairgt on 2009-01-23
In addition to the above list of compatible fingers, the 8 GB Buffalo model: RUF2-K8GS-BK is also compatible.

When the finger is compatible, the installation is a breeze. Good luck with your search.


> **Julian David Pitt said:**
> Thanks for taking the trouble to reply, i had no idea there was a problem with the stick itself. Many thanks Corsairgt.

---

### Post by Julian David Pitt on 2009-01-23
I updated my laptop last night and now lo and behold the stick now mounts and unmounts correctly!!

---


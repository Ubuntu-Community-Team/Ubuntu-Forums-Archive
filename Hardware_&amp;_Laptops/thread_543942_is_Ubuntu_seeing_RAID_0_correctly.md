---
title: "is Ubuntu seeing RAID 0 correctly?"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by DiGiTY on 2007-09-05
I installed a Silicon Image 0680 based PATA RAID card (Rosewill RC-200) into my Ubuntu 7.04 box and setup two 40 GB drives for RAID 0/stripping, then formatted the set as FAT32. According to the Silicon Image support site, Linux supports the chipset/card by default, but when I do "sudo fdisk -l" I see that Ubuntu sees the drives seperately as two 40 GB drives and not as one 80 GB drive:

```
Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9725    78116031    c  W95 FAT32 (LBA)

Disk /dev/sdd: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdd doesn't contain a valid partition table
```

is this normal, is this how Ubuntu/Linux shows a hardware RAID set? If not how do I fix it to show correctly?

If this is normal, how do I mount and use the RAID 0 80 GB drive?

TIA

---

### Post by DiGiTY on 2007-09-07
so after doing a lil' research i learned this cheap [$13] RAID card actually may not be a "true" RAID card and is a FakeRAID card and I'll need to install dmraid.

I was warned about going cheap with a RAID card and I'm assuming this is why. If I went with a Promise, Adaptec or High Point RAID card running $65+, will it be a true RAID card and will Linux/Ubuntu actually see the BIOS configured RAID set as one drive?

TIA

---

### Post by Blue Lightning on 2007-09-26
> **DiGiTY said:**
> If I went with a Promise, Adaptec or High Point RAID card running $65+, will it be a true RAID card and will Linux/Ubuntu actually see the BIOS configured RAID set as one drive?

Unfortunately you need to spend a little more than that. True hardware RAID cards cost at least $200 USD - anything less and it's almost certainly not true hardware RAID.

A list of some fake/true SATA RAID adapters is here:  [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html) (page is horribly formatted I know, but at least it's informative)

---


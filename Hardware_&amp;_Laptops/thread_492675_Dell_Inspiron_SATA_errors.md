---
title: "Dell Inspiron SATA errors"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by f3nrir on 2007-07-05
Got this errors in my Dell Inspiron laptop, I think it's related to de SATA interface or the hard-disk... All the other OS's (have a multiboot with Ubuntu 7.04, Mac OS X, Vista & XP SP2) present hangs or crashes, but randomly... doesn't seem to be a pattern :( 

> Jul  4 22:36:07 gleipnir kernel: [ 2027.508000] ata1.00: ata_hpa_resize 1: sectors = 153356490, hpa_sectors = 156301488
Jul  4 22:36:07 gleipnir kernel: [ 2027.508000] ata1.00: Host Protected Area detected.
Jul  4 22:36:07 gleipnir kernel: [ 2027.508000]      current size : 153356490 sectors (78518 MB)
Jul  4 22:36:07 gleipnir kernel: [ 2027.508000]      native  size : 156301488 sectors (80026 MB)
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] ata1.00: ata_hpa_resize 1: sectors = 153356490, hpa_sectors = 156301488
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] ata1.00: Host Protected Area detected.
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000]      current size : 153356490 sectors (78518 MB)
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000]      native  size : 156301488 sectors (80026 MB)
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] ata1.00: configured for UDMA/100
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] ata1: EH complete
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] SCSI device sda: 153356490 512-byte hdwr sectors (78519 MB)
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] sda: Write Protect is off
Jul  4 22:36:07 gleipnir kernel: [ 2027.516000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  4 22:36:14 gleipnir kernel: [ 2034.660000]          res 51/84:01:40:86:ac/00:00:00:00:00/e7 Emask 0x20 (host bus error)

I'll try with a low level format of the hdd or get a spare sata disk for a few days to discard the hdd. Any ideas or suggestions are welcomed.

---


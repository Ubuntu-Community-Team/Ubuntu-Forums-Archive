---
title: "Startech PEXESATA2I Does Not Properly Function"
date: 2009-01-26
forum: Hardware
---

### Post by rudyg13 on 2009-01-26
I added a startech sata card (1 esata port, 1 sata port) to our dell 2950 system running Ubuntu Server 8.04.1 (kernel 2.6.24-19-server).  When I plug in our external raid box doing a raid 5 array in hardware, these messages appear in dmesg:

```
[   73.100707] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   73.102720] ata2.00: failed to read native max address (err_mask=0x1)
[   73.102723] ata2: failed to recover some devices, retrying in 5 secs
[   73.470498] floppy0: no floppy controllers found
[   78.797473] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   78.799470] ata2.00: failed to read native max address (err_mask=0x1)
[   78.799472] ata2.00: revalidation failed (errno=-13)
[   78.799517] ata2: failed to recover some devices, retrying in 5 secs
[   84.494240] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   84.496220] ata2.00: failed to read native max address (err_mask=0x1)
[   84.496222] ata2.00: revalidation failed (errno=-13)
[   84.496264] ata2.00: disabled
```

And the disk array is not detected as a device.  This card uses the JMicron JMB363 chipset, which apparently caused a lot of people problems in earlier kernel versions.  Any thoughts?

Thanks in advance for any help.

---


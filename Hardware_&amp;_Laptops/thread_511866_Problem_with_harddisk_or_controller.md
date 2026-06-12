---
title: "Problem with harddisk or controller?"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by bjorntj on 2007-07-28
I have just  installed Ubuntu 7.04 on my wifes's laptop (where she has been running Windows seemingly fine) but I have one problem. The laptop freezes every 30 sec or so and this gets in the log:

```

Jul 28 18:24:11 sirimw-laptop kernel: [  643.784000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 28 18:24:11 sirimw-laptop kernel: [  643.784000] ata1: soft resetting port
Jul 28 18:24:11 sirimw-laptop kernel: [  644.112000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jul 28 18:24:11 sirimw-laptop kernel: [  644.120000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Jul 28 18:24:11 sirimw-laptop kernel: [  644.120000] ata1.00: configured for UDMA/33
Jul 28 18:24:11 sirimw-laptop kernel: [  644.296000] ata1.01: configured for UDMA/33
Jul 28 18:24:11 sirimw-laptop kernel: [  644.296000] ata1: EH complete
Jul 28 18:24:11 sirimw-laptop kernel: [  644.320000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul 28 18:24:11 sirimw-laptop kernel: [  644.332000] sda: Write Protect is off
Jul 28 18:24:11 sirimw-laptop kernel: [  644.356000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 28 18:24:11 sirimw-laptop kernel: [  644.380000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Jul 28 18:24:11 sirimw-laptop kernel: [  644.384000] sda: Write Protect is off
Jul 28 18:24:11 sirimw-laptop kernel: [  644.384000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Is it the harddisk that is the problem or controller or something else?


Regards,

BTJ

---


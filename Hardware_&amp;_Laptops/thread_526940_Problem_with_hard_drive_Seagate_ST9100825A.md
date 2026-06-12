---
title: "Problem with hard drive Seagate ST9100825A"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by _mali_ on 2007-08-16
Hi,
I have notebook Asus with Seagate ST9100825A hard drive. This drive freezes for 30s every 3-5 minutes. In dmesg after this is:
```

[  247.968000] ata1.01: qc timeout (cmd 0xa0)
[  247.968000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  247.968000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[  247.968000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  255.040000] ata1: port is slow to respond, please be patient (Status 0xd1)
[  277.968000] ata1: port failed to respond (30 secs, Status 0xd1)
[  277.968000] ata1: soft resetting port
[  278.564000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  278.628000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  278.628000] ata1.00: configured for UDMA/100
[  278.924000] ata1.01: configured for UDMA/33
[  278.924000] ata1: EH complete
[  278.996000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  279.068000] sda: Write Protect is off
[  279.068000] sda: Mode Sense: 00 3a 00 00
[  279.212000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  279.356000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  279.428000] sda: Write Protect is off
[  279.428000] sda: Mode Sense: 00 3a 00 00
[  279.432000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Can you help me pls? I dont know if it is hw or sw problem. Thank you

_mali_

---

### Post by ddrichardson on 2007-08-17
Is your CD drive empty when this happens? If so there is a bug report on this issue [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603").     Have a look over it and let us know if it points the way.

---


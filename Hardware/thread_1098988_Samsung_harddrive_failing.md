---
title: "Samsung harddrive failing"
date: 2009-03-17
forum: Hardware
---

### Post by Catoman on 2009-03-17
I have a Samsung HD502IJ that is giving some errors in the syslog.

Mar 17 21:37:14 Home1 kernel: [343619.495992] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x400100 action 0x6 frozen
Mar 17 21:37:14 Home1 kernel: [343619.496000] ata1.00: irq_stat 0x08000000, interface fatal error
Mar 17 21:37:14 Home1 kernel: [343619.496003] ata1: SError: { UnrecovData Handshk }
Mar 17 21:37:14 Home1 kernel: [343619.496014] ata1.00: cmd 61/50:00:8d:c2:b1/00:00:0b:00:00/40 tag 0 ncq 40960 out
Mar 17 21:37:14 Home1 kernel: [343619.496016]          res 40/00:04:8d:c2:b1/00:00:0b:00:00/40 Emask 0x10 (ATA bus error)
Mar 17 21:37:14 Home1 kernel: [343619.496019] ata1.00: status: { DRDY }
Mar 17 21:37:14 Home1 kernel: [343619.496024] ata1: hard resetting link
Mar 17 21:37:15 Home1 kernel: [343620.023707] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 17 21:37:15 Home1 kernel: [343620.037474] ata1.00: configured for UDMA/133
Mar 17 21:37:15 Home1 kernel: [343620.037485] ata1: EH complete
Mar 17 21:37:15 Home1 kernel: [343620.037530] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Mar 17 21:37:15 Home1 kernel: [343620.037547] sd 0:0:0:0: [sda] Write Protect is off
Mar 17 21:37:15 Home1 kernel: [343620.037550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 17 21:37:15 Home1 kernel: [343620.037576] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

This drive is not more that 3 months old....

Should i consider it dying ?

---

### Post by Catoman on 2009-03-18
I have replaced the SATA-cable but it didn't help much (the errormessages are still there)

---

### Post by Catoman on 2009-03-18
Mar 18 07:49:51 Home1 kernel: [380376.106450] ata1.00: exception Emask 0x10 SAct 0x38000181 SErr 0x400100 action 0x6 frozen
Mar 18 07:49:51 Home1 kernel: [380376.106457] ata1.00: irq_stat 0x08000000, interface fatal error
Mar 18 07:49:51 Home1 kernel: [380376.106461] ata1: SError: { UnrecovData Handshk }
Mar 18 07:49:51 Home1 kernel: [380376.106473] ata1.00: cmd 61/00:00:6d:86:6d/04:00:0e:00:00/40 tag 0 ncq 524288 out
Mar 18 07:49:51 Home1 kernel: [380376.106474]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106477] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106482] ata1.00: cmd 61/00:38:6d:7e:6d/04:00:0e:00:00/40 tag 7 ncq 524288 out
Mar 18 07:49:51 Home1 kernel: [380376.106483]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106486] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106490] ata1.00: cmd 61/00:40:6d:8a:6d/04:00:0e:00:00/40 tag 8 ncq 524288 out
Mar 18 07:49:51 Home1 kernel: [380376.106491]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106501] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106506] ata1.00: cmd 61/00:d8:6d:82:6d/04:00:0e:00:00/40 tag 27 ncq 524288 out
Mar 18 07:49:51 Home1 kernel: [380376.106512]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106522] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106526] ata1.00: cmd 61/78:e0:6d:8e:6d/00:00:0e:00:00/40 tag 28 ncq 61440 out
Mar 18 07:49:51 Home1 kernel: [380376.106532]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106542] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106546] ata1.00: cmd 61/50:e8:ed:8e:6d/00:00:0e:00:00/40 tag 29 ncq 40960 out
Mar 18 07:49:51 Home1 kernel: [380376.106553]          res 40/00:ec:ed:8e:6d/00:00:0e:00:00/40 Emask 0x10 (ATA bus error)
Mar 18 07:49:51 Home1 kernel: [380376.106562] ata1.00: status: { DRDY }
Mar 18 07:49:51 Home1 kernel: [380376.106566] ata1: hard resetting link
Mar 18 07:49:51 Home1 kernel: [380376.630101] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 18 07:49:51 Home1 kernel: [380376.642825] ata1.00: configured for UDMA/133
Mar 18 07:49:51 Home1 kernel: [380376.642846] ata1: EH complete
Mar 18 07:49:51 Home1 kernel: [380376.642916] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Mar 18 07:49:51 Home1 kernel: [380376.642933] sd 0:0:0:0: [sda] Write Protect is off
Mar 18 07:49:51 Home1 kernel: [380376.642935] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 18 07:49:51 Home1 kernel: [380376.642965] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by frenkel on 2009-12-10
Is this drive still working? I have errors like yours with my Samsung disk also...

---


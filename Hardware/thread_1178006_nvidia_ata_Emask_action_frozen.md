---
title: "nvidia ata Emask action frozen"
date: 2009-06-04
forum: Hardware
---

### Post by agne on 2009-06-04
I have this really annoying problem with hdd freeze. Everytime I stress my two disks that is in raid5, fakeraid i get a 3-5 second freeze and the drive does a hard reset.

I have been using ubuntu for almost two years and have never had this problem before. I just upgraded to a new mobo and this problem comes along.

I'm using the 2.6.28-11-generic kernel.

from dmesg when a freeze has just accured occured:
> [28990.792050] ata1.00: exception Emask 0x0 SAct 0xff SErr 0x0 action 0x6 frozen
[28990.792065] ata1.00: cmd 60/80:00:00:4f:ae/00:00:07:00:00/40 tag 0 ncq 65536 in
[28990.792068]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792073] ata1.00: status: { DRDY }
[28990.792081] ata1.00: cmd 60/80:08:80:4e:ae/00:00:07:00:00/40 tag 1 ncq 65536 in
[28990.792086]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792090] ata1.00: status: { DRDY }
[28990.792097] ata1.00: cmd 60/07:10:80:e0:78/00:00:05:00:00/40 tag 2 ncq 3584 in
[28990.792099]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792105] ata1.00: status: { DRDY }
[28990.792111] ata1.00: cmd 60/08:18:9f:e0:78/00:00:05:00:00/40 tag 3 ncq 4096 in
[28990.792113]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792118] ata1.00: status: { DRDY }
[28990.792123] ata1.00: cmd 60/08:20:af:e0:78/00:00:05:00:00/40 tag 4 ncq 4096 in
[28990.792125]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792130] ata1.00: status: { DRDY }
[28990.792135] ata1.00: cmd 60/38:28:c7:e0:78/00:00:05:00:00/40 tag 5 ncq 28672 in
[28990.792137]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792143] ata1.00: status: { DRDY }
[28990.792148] ata1.00: cmd 60/08:30:8f:1e:ba/00:00:01:00:00/40 tag 6 ncq 4096 in
[28990.792150]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792155] ata1.00: status: { DRDY }
[28990.792160] ata1.00: cmd 60/08:38:47:21:9d/00:00:03:00:00/40 tag 7 ncq 4096 in
[28990.792162]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792167] ata1.00: status: { DRDY }
[28990.792174] ata1: hard resetting link
[28991.277065] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[28991.380687] ata1.00: configured for UDMA/133
[28991.380756] ata1: EH complete
[28991.380998] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[28991.381035] sd 0:0:0:0: [sda] Write Protect is off
[28991.381040] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[28991.381087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by agne on 2009-06-06
Nvm fixed it.

---

### Post by armon_d on 2009-07-28
Could you please explain how you fixed this? I have the same problem, also with a Nvidia controller.

---


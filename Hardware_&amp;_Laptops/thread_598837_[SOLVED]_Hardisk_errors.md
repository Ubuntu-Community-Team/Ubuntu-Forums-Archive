---
title: "[SOLVED] Hardisk errors"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by gwi on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157650](https://bugs.launchpad.net/ubuntu/+bug/157650) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Does anyone know what these errors mean, and how the problem can be solved?

My system has random freezes, sometimes during boot, sometimes after a few minutes, sometimes after a few hours. Everytime there are ata port errors like "ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x1c00000 action 0x2 frozen" (see logs). I had this with Feisty, but even after a fresh Gutsy install the problem doesn't disappear.
I tried three different motherboards, two different harddisks, on the current motherboard two different SATA-controllers.

I reported it as a bug, but absolutely no response from anyone at Ubuntu or Canonical or whatever they call themselves. Is that what they call support?:mad::mad::mad:

```
Oct 31 19:52:49 saturnus kernel: [  128.512000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x1c00000 action 0x2
Oct 31 19:52:49 saturnus kernel: [  128.512000] ata1.00: (BMDMA stat 0x25)
Oct 31 19:52:49 saturnus kernel: [  128.512000] ata1.00: cmd ca/00:b0:a1:56:8a/00:00:00:00:00/e7 tag 0 cdb 0x0 data 90112 out
Oct 31 19:52:49 saturnus kernel: [  128.512000]          res 51/84:21:30:57:8a/00:00:00:00:00/e7 Emask 0x10 (ATA bus error)
Oct 31 19:52:49 saturnus kernel: [  128.824000] ata1: soft resetting port
Oct 31 19:52:49 saturnus kernel: [  128.980000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 31 19:52:49 saturnus kernel: [  129.020000] ata1.00: configured for UDMA/133
Oct 31 19:52:49 saturnus kernel: [  129.020000] ata1: EH complete
Oct 31 19:52:49 saturnus kernel: [  129.020000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 19:52:49 saturnus kernel: [  129.024000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 19:52:49 saturnus kernel: [  129.024000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 19:52:49 saturnus kernel: [  129.024000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 19:54:35 saturnus kernel: [  235.188000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 19:54:35 saturnus kernel: [  235.188000] ata1.00: (BMDMA stat 0x24)
Oct 31 19:54:35 saturnus kernel: [  235.188000] ata1.00: cmd ca/00:30:e3:18:97/00:00:00:00:00/e0 tag 0 cdb 0x0 data 24576 out
Oct 31 19:54:35 saturnus kernel: [  235.188000]          res 51/84:01:12:19:97/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 19:54:36 saturnus kernel: [  235.500000] ata1: soft resetting port
Oct 31 19:54:36 saturnus kernel: [  235.656000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 31 19:54:36 saturnus kernel: [  235.688000] ata1.00: configured for UDMA/133
Oct 31 19:54:36 saturnus kernel: [  235.688000] ata1: EH complete
Oct 31 19:54:36 saturnus kernel: [  235.688000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 19:54:36 saturnus kernel: [  235.688000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 19:54:36 saturnus kernel: [  235.688000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 19:54:36 saturnus kernel: [  235.704000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 19:55:24 saturnus kernel: [  283.908000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 19:55:24 saturnus kernel: [  283.908000] ata1.00: (BMDMA stat 0x25)
Oct 31 19:55:24 saturnus kernel: [  283.908000] ata1.00: cmd ca/00:60:1b:e7:dd/00:00:00:00:00/e2 tag 0 cdb 0x0 data 49152 out
Oct 31 19:55:24 saturnus kernel: [  283.908000]          res 51/84:30:4b:e7:dd/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
Oct 31 19:55:24 saturnus kernel: [  284.220000] ata1: soft resetting port
Oct 31 19:55:25 saturnus kernel: [  284.376000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 31 19:55:25 saturnus kernel: [  284.412000] ata1.00: configured for UDMA/133
Oct 31 19:55:25 saturnus kernel: [  284.412000] ata1: EH complete
Oct 31 19:55:25 saturnus kernel: [  284.416000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 19:55:25 saturnus kernel: [  284.416000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 19:55:25 saturnus kernel: [  284.416000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 19:55:25 saturnus kernel: [  284.416000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 19:55:25 saturnus kernel: [  284.520000] ata1: limiting SATA link speed to 1.5 Gbps
Oct 31 19:55:25 saturnus kernel: [  284.520000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x6
Oct 31 19:55:25 saturnus kernel: [  284.520000] ata1.00: (BMDMA stat 0x25)
Oct 31 19:55:25 saturnus kernel: [  284.520000] ata1.00: cmd ca/00:38:41:5c:8a/00:00:00:00:00/e7 tag 0 cdb 0x0 data 28672 out
Oct 31 19:55:25 saturnus kernel: [  284.520000]          res 51/84:28:51:5c:8a/00:00:00:00:00/e7 Emask 0x10 (ATA bus error)
Oct 31 19:55:25 saturnus kernel: [  284.520000] ata1: hard resetting port
Oct 31 19:55:25 saturnus kernel: [  285.152000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 19:55:25 saturnus kernel: [  285.188000] ata1.00: configured for UDMA/133
Oct 31 19:55:25 saturnus kernel: [  285.188000] ata1: EH complete
Oct 31 19:55:25 saturnus kernel: [  285.188000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 19:55:25 saturnus kernel: [  285.196000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 19:55:25 saturnus kernel: [  285.196000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 19:55:25 saturnus kernel: [  285.204000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:21:33 saturnus kernel: [ 1852.332000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:21:33 saturnus kernel: [ 1852.332000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:21:33 saturnus kernel: [ 1852.332000] ata1.00: cmd 35/00:00:86:97:e4/00:04:24:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:21:33 saturnus kernel: [ 1852.332000]          res 51/84:c1:c5:97:e4/84:03:24:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:21:33 saturnus kernel: [ 1852.644000] ata1: soft resetting port
Oct 31 20:21:33 saturnus kernel: [ 1852.800000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:21:33 saturnus kernel: [ 1852.844000] ata1.00: configured for UDMA/133
Oct 31 20:21:33 saturnus kernel: [ 1852.844000] ata1: EH complete
Oct 31 20:21:33 saturnus kernel: [ 1852.852000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:21:33 saturnus kernel: [ 1852.856000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:21:33 saturnus kernel: [ 1852.856000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:21:33 saturnus kernel: [ 1852.880000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:22:10 saturnus kernel: [ 1890.148000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:22:10 saturnus kernel: [ 1890.148000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:22:10 saturnus kernel: [ 1890.148000] ata1.00: cmd 35/00:00:ae:c5:fb/00:04:24:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:22:10 saturnus kernel: [ 1890.148000]          res 51/84:a0:0e:c6:fb/84:03:24:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:22:11 saturnus kernel: [ 1890.460000] ata1: soft resetting port
Oct 31 20:22:11 saturnus kernel: [ 1890.616000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:22:11 saturnus kernel: [ 1890.660000] ata1.00: configured for UDMA/133
Oct 31 20:22:11 saturnus kernel: [ 1890.660000] ata1: EH complete
Oct 31 20:22:11 saturnus kernel: [ 1890.672000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:22:11 saturnus kernel: [ 1890.672000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:22:11 saturnus kernel: [ 1890.672000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:22:11 saturnus kernel: [ 1890.680000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:22:12 saturnus kernel: [ 1891.376000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:22:12 saturnus kernel: [ 1891.376000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:22:12 saturnus kernel: [ 1891.376000] ata1.00: cmd 35/00:00:2e:85:fc/00:04:24:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:22:12 saturnus kernel: [ 1891.376000]          res 51/84:d0:5e:85:fc/84:03:24:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:22:12 saturnus kernel: [ 1891.688000] ata1: soft resetting port
Oct 31 20:22:12 saturnus kernel: [ 1891.844000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:22:12 saturnus kernel: [ 1891.876000] ata1.00: configured for UDMA/133
Oct 31 20:22:12 saturnus kernel: [ 1891.876000] ata1: EH complete
Oct 31 20:22:12 saturnus kernel: [ 1891.880000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:22:12 saturnus kernel: [ 1891.884000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:22:12 saturnus kernel: [ 1891.884000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:22:12 saturnus kernel: [ 1891.892000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:23:09 saturnus kernel: [ 1948.544000] ata1.00: limiting speed to UDMA/100:PIO4
Oct 31 20:23:09 saturnus kernel: [ 1948.544000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:23:09 saturnus kernel: [ 1948.544000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:23:09 saturnus kernel: [ 1948.544000] ata1.00: cmd 35/00:00:53:8a:de/00:04:02:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:23:09 saturnus kernel: [ 1948.544000]          res 51/84:60:f3:8a:de/84:03:02:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:23:09 saturnus kernel: [ 1948.856000] ata1: soft resetting port
Oct 31 20:23:09 saturnus kernel: [ 1949.012000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:23:09 saturnus kernel: [ 1949.048000] ata1.00: configured for UDMA/100
Oct 31 20:23:09 saturnus kernel: [ 1949.048000] ata1: EH complete
Oct 31 20:23:09 saturnus kernel: [ 1949.052000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:23:09 saturnus kernel: [ 1949.052000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:23:09 saturnus kernel: [ 1949.052000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:23:09 saturnus kernel: [ 1949.056000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:30:35 saturnus kernel: [ 2395.216000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:30:35 saturnus kernel: [ 2395.216000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:30:35 saturnus kernel: [ 2395.216000] ata1.00: cmd 35/00:00:2b:88:d7/00:04:02:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:30:35 saturnus kernel: [ 2395.216000]          res 51/84:b0:7b:88:d7/84:03:02:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:30:36 saturnus kernel: [ 2395.528000] ata1: soft resetting port
Oct 31 20:30:36 saturnus kernel: [ 2395.684000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:30:36 saturnus kernel: [ 2395.712000] ata1.00: configured for UDMA/100
Oct 31 20:30:36 saturnus kernel: [ 2395.712000] ata1: EH complete
Oct 31 20:30:36 saturnus kernel: [ 2395.716000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:30:36 saturnus kernel: [ 2395.720000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:30:36 saturnus kernel: [ 2395.720000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:30:36 saturnus kernel: [ 2395.736000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 20:50:28 saturnus kernel: [ 3587.784000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 20:50:28 saturnus kernel: [ 3587.784000] ata1.00: (BMDMA stat 0x25)
Oct 31 20:50:28 saturnus kernel: [ 3587.784000] ata1.00: cmd 35/00:00:73:dc:dd/00:04:02:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 20:50:28 saturnus kernel: [ 3587.784000]          res 51/84:00:73:dd:dd/84:03:02:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 20:50:28 saturnus kernel: [ 3588.096000] ata1: soft resetting port
Oct 31 20:50:28 saturnus kernel: [ 3588.252000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 20:50:28 saturnus kernel: [ 3588.288000] ata1.00: configured for UDMA/100
Oct 31 20:50:28 saturnus kernel: [ 3588.288000] ata1: EH complete
Oct 31 20:50:28 saturnus kernel: [ 3588.292000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 20:50:28 saturnus kernel: [ 3588.296000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 20:50:28 saturnus kernel: [ 3588.296000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 20:50:29 saturnus kernel: [ 3588.316000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 21:13:15 saturnus kernel: [ 4954.388000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 21:13:15 saturnus kernel: [ 4954.388000] ata1.00: (BMDMA stat 0x25)
Oct 31 21:13:15 saturnus kernel: [ 4954.388000] ata1.00: cmd 35/00:00:f3:1e:d2/00:04:02:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 21:13:15 saturnus kernel: [ 4954.388000]          res 51/84:90:63:22:d2/84:00:02:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 21:13:15 saturnus kernel: [ 4954.696000] ata1: soft resetting port
Oct 31 21:13:15 saturnus kernel: [ 4954.852000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 21:13:15 saturnus kernel: [ 4954.880000] ata1.00: configured for UDMA/100
Oct 31 21:13:15 saturnus kernel: [ 4954.880000] ata1: EH complete
Oct 31 21:13:15 saturnus kernel: [ 4954.888000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 21:13:15 saturnus kernel: [ 4954.888000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 21:13:15 saturnus kernel: [ 4954.888000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 21:13:15 saturnus kernel: [ 4954.896000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 21:14:43 saturnus kernel: [ 5042.804000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2
Oct 31 21:14:43 saturnus kernel: [ 5042.804000] ata1.00: (BMDMA stat 0x25)
Oct 31 21:14:43 saturnus kernel: [ 5042.804000] ata1.00: cmd 35/00:00:13:fc:de/00:04:02:00:00/e0 tag 0 cdb 0x0 data 524288 out
Oct 31 21:14:43 saturnus kernel: [ 5042.804000]          res 51/84:31:e2:fe:de/84:01:02:00:00/e0 Emask 0x10 (ATA bus error)
Oct 31 21:14:43 saturnus kernel: [ 5043.116000] ata1: soft resetting port
Oct 31 21:14:43 saturnus kernel: [ 5043.272000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Oct 31 21:14:43 saturnus kernel: [ 5043.308000] ata1.00: configured for UDMA/100
Oct 31 21:14:43 saturnus kernel: [ 5043.308000] ata1: EH complete
Oct 31 21:14:44 saturnus kernel: [ 5043.316000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Oct 31 21:14:44 saturnus kernel: [ 5043.320000] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 21:14:44 saturnus kernel: [ 5043.320000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 21:14:44 saturnus kernel: [ 5043.324000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by SixedUp on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159521](https://bugs.launchpad.net/ubuntu/+bug/159521) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				What was your bug number?  I seem to be getting exactly the same behavior, and have also got a bug open (see above).  Would be interested if you can see any commonality / differences between what you are seeing, and what I've reported.
Thanks

---

### Post by gwi on 2007-11-07
My bug number is 157650 (a link is in the top line of my first posting).

I am having the problem on an nForce SATA controller (nForce4, nForce570 and nForce590), as well as on a Sil controller (SiI3124). In all cases there is only one harddisk attached, so no RAID. At times when there are no errors, performance is normal. So my guess is we are having two different problems here.

---

### Post by SixedUp on 2007-11-08
Oops. Not sure how I managed to miss you bug link ... must be going cross-eyed here :)  From your description, I agree ... its not at all clear that this is the same problem.  Thanks anyway

---

### Post by Bogo999 on 2007-11-30
To me it sounds like you have a SATA cable problem.  I'm not sure who designed the SATA cable connectors, but they should be drawn and quartered.  There is no way for it to be a truly long term reliable design.  In all the years I was using PATA type cables, from before ATA discs existed (remember MFM?), I've only had a few bad cables for both home and work.  With SATA cables I've now got well over 20 bad cables in only 4 years of use on my own home systems, don't ask about work...

---

### Post by gwi on 2007-12-03
I tried three different motherboards (two of them brand new), two different harddisks, several different cables, different SATA ports on the boards (and even two different SATA controllers on my present board).
How can this be a cable problem? All cables are rotten then?

---

### Post by SixedUp on 2007-12-03
> **Bogo999 said:**
> To me it sounds like you have a SATA cable problem.  I'm not sure who designed the SATA cable connectors, but they should be drawn and quartered.  There is no way for it to be a truly long term reliable design.  In all the years I was using PATA type cables, from before ATA discs existed (remember MFM?), I've only had a few bad cables for both home and work.  With SATA cables I've now got well over 20 bad cables in only 4 years of use on my own home systems, don't ask about work...

I'd certainly agree that there are a lot of pretty dreadful SATA cables out there. However, like gwi, I've swapped cables, drives, adaptors and OS', and the common theme in my problem always seems to be the combination of a Silicon Image-based PCI card, with sata-sil and libata from a (fairly) recent kernel :(

---

### Post by gwi on 2007-12-06
If I would buy a new SATA cable, how can I see if it is a high quality cable?

---

### Post by SixedUp on 2007-12-11
> **gwi said:**
> If I would buy a new SATA cable, how can I see if it is a high quality cable?

In general, the best you can do is not to buy either the cheapest or the most expensive. Personally I've had good experience with the ones I've had from LinITX, which were nice thick semi-translucent red ones, with black connectors.

---

### Post by gwi on 2007-12-12
Well, after trying several of the 6 or 8 cables that came with my motherboard, I more or less ruled out the cable as a cause for the problems. Especially since setting the harddisk to 150Mb/s with a jumper on it, did not solve the problem.

Monday I put in a new cable, which was sold as a "SATA II cable". Didn't look different compared to the cables I already tried, except that the connector on the motherboard side has a clip to lock it in position. So far I haven't had any problems since, so maybe a €5 investment solved the problem... [-o<

---

### Post by al108 on 2007-12-12
Yep, I've got a similar problem. Tried different cards (made by different companies, both SIl 3114 PCI though) but it didn't help. Didn't have that problem until a couple of days ago. I've seen this problem popping up in other distros and I haven't seen anybody solved it yet.

SATA cables suck for sure, even the locking ones. In my other computer I've got those locking cables with Abit ip35pro motherboard, still had problems  with HDDs not being recognized until I pushed and wiggled those cables; even though it looked like the cables were all the way in.

I doubt the problem will be fixed anytime soon. It is probably not something Ubuntu specific either. Hopefully in the spring will get a new kernel that won't do that. Or we will have to "upgrade" to a different SATA adapter/motherboard/HDD... My other 7 computers that don't have Sil cards work fine.

Please don't forget to report back if your problem is fixed somehow.

---

### Post by fergus on 2007-12-13
gwi,  any errors yet?  I am having a similar problem and found some emails that say it could be an NCQ issue.  You can try disabling NCQ by changing the queue depth for the device.  See below.  If they come back this may help.

$ echo 1 > /sys/block/sdX/device/queue_depth

set it back to 31 to turn them back on

fergus

---

### Post by gwi on 2007-12-17
Changed cable last monday. I did not have any more ata problems since. And I moved around dozens of gigabytes last weak.
So, all cables I has were rotten, and now I have found a good one? Still can't beleave it. But if it is still true in 14 days, I will have an extra champagne on it. :cool:

---

### Post by al108 on 2007-12-19
I messed with cables some more - the errors didn't come back yet.

---

### Post by gwi on 2008-01-07
Three weeks have passed, without any more ata problems. So, it seems that buying a "SATA II" cable has solved the problem...

---

### Post by PierGroup on 2008-01-17
Thanks to this thread I have identified the same problem with a new Esprimo system. I swapped the SATA cables and -bingo!- no more problem.

Thanks, people!

---


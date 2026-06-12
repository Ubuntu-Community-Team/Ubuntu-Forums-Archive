---
title: "I/O error with 250 MB disks on ASUS A7V133"
date: 2009-03-16
forum: Hardware
---

### Post by f03el on 2009-03-16
Hi,
I have problem with I/O error on two 250 GB IDE disks connected to an ASUS A7V133 motherboard jumpered not to use the onboard RAID controller. The BIOS is of version 1009. Only one of the disks are tagged as failed in the software array and I can see all files when it's mounted. One interesting thing to note is that the I/O error is on the same sector for both disks:```
...
[   22.660532] end_request: I/O error, dev sdb, sector 243798095
...
[   22.680420] end_request: I/O error, dev sdc, sector 243798095
...
```
I start to suspect that support for LBA48 is missing somewhere. Should I try to find a newer firmware for the MB?
Here's a longer excerpt from dmesg:
```

...
[   15.358617] md: md0 stopped.
[   15.361676] md: bind<sdc1>
[   15.361963] md: bind<sdb1>
[   15.611520] raid1: raid set md0 active with 2 out of 2 mirrors
[   15.617434] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[   18.838751] loop: module loaded
[   18.886234] lp0: using parport0 (interrupt-driven).
[   19.246722] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   19.629583] EXT3 FS on sda1, internal journal
[   20.610934] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   20.611002] ata3.00: BMDMA stat 0x4
[   20.611069] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   20.611072]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   20.611221] ata3.00: status: { DRDY ERR }
[   20.611278] ata3.00: error: { ICRC ABRT }
[   20.611355] ata3: soft resetting link
[   20.611496] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   20.611559] ata4.00: BMDMA stat 0x4
[   20.611619] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   20.611621]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   20.611769] ata4.00: status: { DRDY ERR }
[   20.611826] ata4.00: error: { ICRC ABRT }
[   20.611896] ata4: soft resetting link
[   20.830451] ata3.00: configured for UDMA/100
[   20.830488] ata3: EH complete
[   20.830587] ata4.00: configured for UDMA/100
[   20.830594] ata4: EH complete
[   20.980209] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   20.980279] ata3.00: BMDMA stat 0x4
[   20.980345] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   20.980348]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   20.980521] ata3.00: status: { DRDY ERR }
[   20.980584] ata3.00: error: { ICRC ABRT }
[   20.980659] ata3: soft resetting link
[   20.980892] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   20.980963] ata4.00: BMDMA stat 0x4
[   20.981031] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   20.981033]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   20.981213] ata4.00: status: { DRDY ERR }
[   20.981277] ata4.00: error: { ICRC ABRT }
[   20.981352] ata4: soft resetting link
[   21.200474] ata3.00: configured for UDMA/100
[   21.200483] ata3: EH complete
[   21.200571] ata4.00: configured for UDMA/100
[   21.200578] ata4: EH complete
[   21.350155] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   21.350226] ata3.00: BMDMA stat 0x4
[   21.350293] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   21.350296]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   21.350468] ata3.00: status: { DRDY ERR }
[   21.350530] ata3.00: error: { ICRC ABRT }
[   21.350606] ata3: soft resetting link
[   21.350797] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   21.350868] ata4.00: BMDMA stat 0x4
[   21.350934] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   21.350937]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   21.351114] ata4.00: status: { DRDY ERR }
[   21.351176] ata4.00: error: { ICRC ABRT }
[   21.351250] ata4: soft resetting link
[   21.550486] ata3.00: configured for UDMA/100
[   21.550495] ata3: EH complete
[   21.570329] ata4.00: configured for UDMA/100
[   21.570337] ata4: EH complete
[   21.700253] ata3.00: limiting speed to UDMA/66:PIO4
[   21.700260] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   21.700333] ata3.00: BMDMA stat 0x4
[   21.700403] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   21.700406]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   21.700584] ata3.00: status: { DRDY ERR }
[   21.700651] ata3.00: error: { ICRC ABRT }
[   21.700733] ata3: soft resetting link
[   21.720614] ata4.00: limiting speed to UDMA/66:PIO4
[   21.720620] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   21.720689] ata4.00: BMDMA stat 0x4
[   21.720754] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   21.720757]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   21.720931] ata4.00: status: { DRDY ERR }
[   21.720995] ata4.00: error: { ICRC ABRT }
[   21.721071] ata4: soft resetting link
[   21.920457] ata3.00: configured for UDMA/66
[   21.920475] ata3: EH complete
[   21.940331] ata4.00: configured for UDMA/66
[   21.940340] ata4: EH complete
[   22.070193] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   22.070264] ata3.00: BMDMA stat 0x4
[   22.070329] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   22.070332]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   22.070507] ata3.00: status: { DRDY ERR }
[   22.070569] ata3.00: error: { ICRC ABRT }
[   22.070643] ata3: soft resetting link
[   22.090624] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   22.090695] ata4.00: BMDMA stat 0x4
[   22.090761] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   22.090764]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   22.090940] ata4.00: status: { DRDY ERR }
[   22.091005] ata4.00: error: { ICRC ABRT }
[   22.091081] ata4: soft resetting link
[   22.290458] ata3.00: configured for UDMA/66
[   22.290467] ata3: EH complete
[   22.310343] ata4.00: configured for UDMA/66
[   22.310351] ata4: EH complete
[   22.440210] ata3.00: limiting speed to UDMA/33:PIO4
[   22.440215] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   22.440285] ata3.00: BMDMA stat 0x4
[   22.440351] ata3.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   22.440354]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   22.440530] ata3.00: status: { DRDY ERR }
[   22.440593] ata3.00: error: { ICRC ABRT }
[   22.440668] ata3: soft resetting link
[   22.460640] ata4.00: limiting speed to UDMA/33:PIO4
[   22.460645] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   22.460717] ata4.00: BMDMA stat 0x4
[   22.460784] ata4.00: cmd ca/00:08:4f:10:88/00:00:00:00:00/ee tag 0 dma 4096 out
[   22.460786]          res 51/84:00:4f:10:88/00:00:00:00:00/ee Emask 0x10 (ATA bus error)
[   22.460965] ata4.00: status: { DRDY ERR }
[   22.461029] ata4.00: error: { ICRC ABRT }
[   22.461104] ata4: soft resetting link
[   22.660458] ata3.00: configured for UDMA/33
[   22.660479] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   22.660486] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   22.660495] Descriptor sense data with sense descriptors (in hex):
[   22.660499]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   22.660512]         0e 88 10 4f 
[   22.660517] sd 2:0:0:0: [sdb] Add. Sense: Scsi parity error
[   22.660532] end_request: I/O error, dev sdb, sector 243798095
[   22.660609] raid1: Disk failure on sdb1, disabling device.
[   22.660612] raid1: Operation continuing on 1 devices.
[   22.660764] ata3: EH complete
[   22.661173] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   22.661209] sd 2:0:0:0: [sdb] Write Protect is off
[   22.661215] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.661263] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.680362] ata4.00: configured for UDMA/33
[   22.680377] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   22.680383] sd 3:0:0:0: [sdc] Sense Key : Aborted Command [current] [descriptor]
[   22.680390] Descriptor sense data with sense descriptors (in hex):
[   22.680394]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   22.680406]         0e 88 10 4f 
[   22.680411] sd 3:0:0:0: [sdc] Add. Sense: Scsi parity error
[   22.680420] end_request: I/O error, dev sdc, sector 243798095
[   22.680491] Buffer I/O error on device md0, logical block 30474754
[   22.680553] lost page write due to I/O error on md0
[   22.680577] ata4: EH complete
[   22.680814] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   22.681016] sd 3:0:0:0: [sdc] Write Protect is off
[   22.681021] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   22.710778] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.710831] RAID1 conf printout:
[   22.710835]  --- wd:1 rd:2
[   22.710841]  disk 0, wo:1, o:0, dev:sdb1
[   22.710845]  disk 1, wo:0, o:1, dev:sdc1
[   22.710888] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   22.710918] sd 2:0:0:0: [sdb] Write Protect is off
[   22.710924] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.710970] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.711002] RAID1 conf printout:
[   22.711005]  --- wd:1 rd:2
[   22.711009]  disk 1, wo:0, o:1, dev:sdc1
[   23.099685] kjournald starting.  Commit interval 5 seconds
[   23.274481] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   23.274578] ata4.00: BMDMA stat 0x4
[   23.274648] ata4.00: cmd ca/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 out
[   23.274652]          res 51/84:00:3f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.274830] ata4.00: status: { DRDY ERR }
[   23.274893] ata4.00: error: { ICRC ABRT }
[   23.274977] ata4: soft resetting link
[   23.490317] ata4.00: configured for UDMA/33
[   23.490331] ata4: EH complete
[   23.640637] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   23.640709] ata4.00: BMDMA stat 0x4
[   23.640776] ata4.00: cmd ca/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 out
[   23.640779]          res 51/84:00:3f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.640954] ata4.00: status: { DRDY ERR }
[   23.641017] ata4.00: error: { ICRC ABRT }
[   23.641093] ata4: soft resetting link
[   23.840320] ata4.00: configured for UDMA/33
[   23.840329] ata4: EH complete
[   23.990650] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   23.990720] ata4.00: BMDMA stat 0x4
[   23.990786] ata4.00: cmd ca/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 out
[   23.990789]          res 51/84:00:3f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   23.990964] ata4.00: status: { DRDY ERR }
[   23.991028] ata4.00: error: { ICRC ABRT }
[   23.991104] ata4: soft resetting link
[   24.190325] ata4.00: configured for UDMA/33
[   24.190334] ata4: EH complete
[   24.340662] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   24.340732] ata4.00: BMDMA stat 0x4
[   24.340797] ata4.00: cmd ca/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 out
[   24.340800]          res 51/84:00:3f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   24.340971] ata4.00: status: { DRDY ERR }
[   24.341033] ata4.00: error: { ICRC ABRT }
[   24.341108] ata4: soft resetting link
[   24.540315] ata4.00: configured for UDMA/33
[   24.540323] ata4: EH complete
[   24.690654] ata4.00: limiting speed to PIO4
[   24.690660] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   24.690725] ata4.00: BMDMA stat 0x4
[   24.690784] ata4.00: cmd ca/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 out
[   24.690787]          res 51/84:00:3f:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   24.690936] ata4.00: status: { DRDY ERR }
[   24.690992] ata4.00: error: { ICRC ABRT }
[   24.691062] ata4: soft resetting link
[   24.890326] ata4.00: configured for PIO4
[   24.890334] ata4: EH complete
[   24.891101] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   24.891134] sd 3:0:0:0: [sdc] Write Protect is off
[   24.891140] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   24.891189] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.891236] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[   24.891264] sd 3:0:0:0: [sdc] Write Protect is off
[   24.891269] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   24.891315] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...

```

---

### Post by f03el on 2009-03-22
I've upgraded to the latest BIOS firmware (version 1010.01B which should support LBA48), but the boot messages are the same. There seems to be problem with the driver for the onboard Promise PDC20265 ATA controller (pata_pdc202xx_old); see [_here_]("https://bugzilla.novell.com/show_bug.cgi?id=457037") and [_here_]("http://bugzilla.kernel.org/show_bug.cgi?id=9337"), and this bug has been known for some year now but not fixed. Now I consider to buy another ATA controller which uses another driver.

---


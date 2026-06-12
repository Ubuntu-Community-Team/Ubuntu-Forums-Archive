---
title: "/var/log/messages getting flood with esata drive errors?"
date: 2008-07-28
forum: General Help
---

### Post by dark_phantom on 2008-07-28
I have an esata enclosure with two 500GB drives in a raid0 mode, I also have it configure with an ext3 file system.  When I play a video on that drive I constantly get these messages.

```

[ 2300.286257]          res 51/84:00:a7:51:c1/0e:00:30:00:00/40 Emask 0x410 (ATA bus error) <F>
[ 2300.594279] ata6.00: soft resetting link
[ 2300.762116] ata6.00: SATA link up 3.0 Gbps (SStatus 123 SControl 310)
[ 2300.762496] ata6.00: configured for UDMA/33
[ 2300.762620] ata6: EH complete
[ 2300.762671] sd 5:0:0:0: [sde] 1953546336 512-byte hardware sectors (1000216 MB)
[ 2300.762683] sd 5:0:0:0: [sde] Write Protect is off
[ 2300.762699] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[ 2436.441874] ata6.00: failed to read SCR 0 (Emask=0x100)
[ 2436.441880] ata6.01: failed to read SCR 1 (Emask=0x40)
[ 2436.441892]          res 51/84:00:c7:e8:c1/0e:00:30:00:00/40 Emask 0x410 (ATA bus error) <F>
[ 2436.441904] ata6.15: hard resetting link
[ 2438.089474] ata6.15: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 2438.089994] ata6.00: hard resetting link
[ 2438.572212] ata6.00: SATA link up 3.0 Gbps (SStatus 123 SControl 310)
[ 2438.572396] ata6.01: hard resetting link
[ 2438.891997] ata6.01: SATA link down (SStatus 0 SControl 310)
[ 2438.892491] ata6.00: configured for UDMA/33
[ 2439.202990] ata6.00: soft resetting link
[ 2439.367167] ata6.00: SATA link up 3.0 Gbps (SStatus 123 SControl 310)
[ 2439.367496] ata6.00: configured for UDMA/33
[ 2439.367565] ata6: EH complete

```

Also, I was copying a few files when these messages got dumped and the file system crash or something.

```

[ 1087.778522] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1087.778969] ata6.15: Port Multiplier 1.1, 0x1095:0x5744 r33, 2 ports, feat 0x1/0x9
[ 1087.779064] ata6.00: hard resetting link
[ 1088.098187] ata6.00: SATA link down (SStatus 0 SControl 320)
[ 1088.098212] ata6.01: hard resetting link
[ 1088.581229] ata6.01: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[ 1088.581352] ata6.01: ATA-7: Config   Disk 0, 1.1516, max MWDMA2
[ 1088.581355] ata6.01: 16777215 sectors, multi 1: LBA 
[ 1088.581504] ata6.01: configured for PIO4
[ 1088.581551] ata6: EH complete
[ 1088.581650] scsi 5:1:0:0: Direct-Access     ATA      Config   Disk 0  1.15 PQ: 0 ANSI: 5
[ 1088.581718] sd 5:1:0:0: [sde] 16777215 512-byte hardware sectors (8590 MB)
[ 1088.581728] sd 5:1:0:0: [sde] Write Protect is off
[ 1088.581743] sd 5:1:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1088.581782] sd 5:1:0:0: [sde] 16777215 512-byte hardware sectors (8590 MB)
[ 1088.581789] sd 5:1:0:0: [sde] Write Protect is off
[ 1088.581804] sd 5:1:0:0: [sde] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1088.581808]  sde: unknown partition table
[ 1088.582686] sd 5:1:0:0: [sde] Attached SCSI disk
[ 1088.582720] sd 5:1:0:0: Attached scsi generic sg6 type 0
[ 1090.620663] ata6.00: soft resetting link
[ 1090.783848] ata6.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[ 1091.496664] ata6.01: soft resetting link
[ 1091.496825] ata6.01: SATA link down (SStatus 0 SControl 320)
[ 1091.496958] ata6.00: ATA-7: External Disk 0, 1.1516, max UDMA/133
[ 1091.496965] ata6.00: 1953546336 sectors, multi 1: LBA48 NCQ (depth 31/32)
[ 1091.497116] ata6.00: configured for UDMA/133
[ 1091.497138] ata6.01: disabled
[ 1092.003305] ata6.00: configured for UDMA/133
[ 1092.003356] ata6: EH complete
[ 1092.003364] ata6.01: detaching (SCSI 5:1:0:0)
[ 1092.003597] sd 5:1:0:0: [sde] Stopping disk
[ 1092.003674] sd 5:1:0:0: [sde] START_STOP FAILED
[ 1092.003676] sd 5:1:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 1092.003778] scsi 5:0:0:0: Direct-Access     ATA      External Disk 0  1.15 PQ: 0 ANSI: 5
[ 1092.003826] sd 5:0:0:0: [sde] 1953546336 512-byte hardware sectors (1000216 MB)
[ 1092.003835] sd 5:0:0:0: [sde] Write Protect is off
[ 1092.003848] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1092.003877] sd 5:0:0:0: [sde] 1953546336 512-byte hardware sectors (1000216 MB)
[ 1092.003885] sd 5:0:0:0: [sde] Write Protect is off
[ 1092.003900] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1092.003904]  sde: sde1
[ 1092.011315] sd 5:0:0:0: [sde] Attached SCSI disk
[ 1092.011354] sd 5:0:0:0: Attached scsi generic sg6 type 0
[ 1109.923696] kjournald starting.  Commit interval 5 seconds
[ 1109.927828] EXT3 FS on sde1, internal journal
[ 1109.927833] EXT3-fs: recovery complete.
[ 1109.928096] EXT3-fs: mounted filesystem with ordered data mode.
[ 1398.451084] ata6.00: failed to read SCR 1 (Emask=0x40)
[ 1398.451090] ata6.01: failed to read SCR 1 (Emask=0x40)
[ 1398.451117]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451128]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451139]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451149]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451159]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451169]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451179]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451189]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451209]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451216]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451223]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451231]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451239]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451246]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451253]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451260]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451268]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451275]          res 50/00:50:57:73:d7/00:00:30:00:00/40 Emask 0x100 (unknown error)
[ 1398.451287] ata6.15: hard resetting link
[ 1399.493245] ata6.15: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1399.493726] ata6.00: hard resetting link
[ 1399.977036] ata6.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[ 1399.977060] ata6.01: hard resetting link
[ 1400.296018] ata6.01: SATA link down (SStatus 0 SControl 320)
[ 1400.296383] ata6.00: configured for UDMA/133
[ 1400.296513] ata6: EH complete

```

Is my external drive having problems?  I see a few error lines but nothing convincing that my enclosure is going to die.  Any help is appreciated.

PS: Mods, if it's not on the right section please move it.

Thanks.

---

### Post by RealPSL on 2008-07-28
Judging from the difficulties being shown in the logs the drive could be going bad or maybe a bad connection. You should back up as soon as possible to avoid data loss.

---

### Post by dark_phantom on 2008-07-28
What I don't get is that both drives and the enclosures are brand new.  And this seems to happen when I do it via the terminal (find, cpio, and cp) and not through nautilus (copy & paste).  The reason, I'm doing it via commands is that through nautilus it seems to be pretty slow for an esata connection.  Even my USB copies are faster then the sataII link. :confused:

---

### Post by dark_phantom on 2008-07-29
ttt

---


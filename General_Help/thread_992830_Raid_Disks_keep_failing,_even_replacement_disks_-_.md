---
title: "Raid Disks keep failing, even replacement disks - Emask 0x9 (media error)"
date: 2008-11-25
forum: General Help
---

### Post by ubtutu on 2008-11-25
Very strange errors going on in my dmesg:

I have 4 disks in a raid 5 configuration (sdb sdc sdd sde) and it feels like all four disks are failing.... this is the second time this has happened; these four disks are four replacement disks after the previous raid5 had similar problems!

It surely can't be bad disks, as this set of four makes 8 disks in a row that have failed or exhibited errors. It must surely be something else?

Is it a motherboard problem? PSU? Kernel? No idea where to start but I am fed up of buying new drives. Any help would be much appreciated!

Running Linux ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux 

```

Nov 25 10:05:32 ubuntu -- MARK --
Nov 25 10:23:52 ubuntu kernel: [74364.444000] raid5:md0: read error corrected (8 sectors at 1408 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.444000] raid5:md0: read error corrected (8 sectors at 1424 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.444000] raid5:md0: read error corrected (8 sectors at 1440 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.444000] raid5:md0: read error corrected (8 sectors at 1416 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.444000] raid5:md0: read error corrected (8 sectors at 1448 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1512 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1504 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1488 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1480 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1472 on dm-6)
Nov 25 10:23:52 ubuntu kernel: [74364.448000] raid5:md0: read error corrected (8 sectors at 1456 on dm-6)
Nov 25 10:45:32 ubuntu -- MARK --
Nov 25 10:49:15 ubuntu kernel: [75887.484000]          res 40/00:04:80:02:d5/00:00:00:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:49:15 ubuntu kernel: [75887.796000] ata4: soft resetting port
Nov 25 10:49:15 ubuntu kernel: [75887.968000] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:49:15 ubuntu kernel: [75887.980000] ata4.00: configured for UDMA/133
Nov 25 10:49:15 ubuntu kernel: [75887.980000] ata4: EH complete
Nov 25 10:49:15 ubuntu kernel: [75887.980000] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:49:15 ubuntu kernel: [75887.980000] sd 3:0:0:0: [sdc] Write Protect is off
Nov 25 10:49:15 ubuntu kernel: [75887.980000] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:49:48 ubuntu kernel: [75920.788000]          res 40/00:14:e0:aa:b4/00:00:01:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:49:48 ubuntu kernel: [75921.100000] ata3: soft resetting port
Nov 25 10:49:49 ubuntu kernel: [75921.272000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:49:49 ubuntu kernel: [75921.276000] ata3.00: configured for UDMA/133
Nov 25 10:49:49 ubuntu kernel: [75921.276000] ata3: EH complete
Nov 25 10:49:49 ubuntu kernel: [75921.276000] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:49:49 ubuntu kernel: [75921.276000] sd 2:0:0:0: [sdb] Write Protect is off
Nov 25 10:49:49 ubuntu kernel: [75921.276000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:49:50 ubuntu kernel: [75922.416000]          res 40/00:14:e0:aa:bf/00:00:01:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:49:50 ubuntu kernel: [75922.728000] ata3: soft resetting port
Nov 25 10:49:50 ubuntu kernel: [75922.900000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:49:50 ubuntu kernel: [75922.900000] ata3.00: configured for UDMA/133
Nov 25 10:49:50 ubuntu kernel: [75922.900000] ata3: EH complete
Nov 25 10:49:50 ubuntu kernel: [75922.900000] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:49:50 ubuntu kernel: [75922.900000] sd 2:0:0:0: [sdb] Write Protect is off
Nov 25 10:49:50 ubuntu kernel: [75922.900000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:50:06 ubuntu kernel: [75938.244000]          res 40/00:14:88:55:fd/00:00:01:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:50:06 ubuntu kernel: [75938.556000] ata4: soft resetting port
Nov 25 10:50:06 ubuntu kernel: [75938.728000] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:50:06 ubuntu kernel: [75938.728000] ata4.00: configured for UDMA/133
Nov 25 10:50:06 ubuntu kernel: [75938.728000] ata4: EH complete
Nov 25 10:50:06 ubuntu kernel: [75938.728000] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:50:06 ubuntu kernel: [75938.728000] sd 3:0:0:0: [sdc] Write Protect is off
Nov 25 10:50:06 ubuntu kernel: [75938.728000] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:50:17 ubuntu kernel: [75949.772000]          res 40/00:14:88:55:26/00:00:02:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:50:17 ubuntu kernel: [75950.084000] ata4: soft resetting port
Nov 25 10:50:18 ubuntu kernel: [75950.256000] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:50:18 ubuntu kernel: [75950.256000] ata4.00: configured for UDMA/133
Nov 25 10:50:18 ubuntu kernel: [75950.256000] ata4: EH complete
Nov 25 10:50:18 ubuntu kernel: [75950.256000] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:50:18 ubuntu kernel: [75950.256000] sd 3:0:0:0: [sdc] Write Protect is off
Nov 25 10:50:18 ubuntu kernel: [75950.256000] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:58:37 ubuntu kernel: [76449.776000]          res 40/00:14:88:55:1e/00:00:04:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:58:37 ubuntu kernel: [76450.088000] ata5: soft resetting port
Nov 25 10:58:38 ubuntu kernel: [76450.260000] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:58:38 ubuntu kernel: [76450.272000] ata5.00: configured for UDMA/133
Nov 25 10:58:38 ubuntu kernel: [76450.272000] ata5: EH complete
Nov 25 10:58:38 ubuntu kernel: [76450.272000] sd 4:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:58:38 ubuntu kernel: [76450.272000] sd 4:0:0:0: [sdd] Write Protect is off
Nov 25 10:58:38 ubuntu kernel: [76450.272000] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUANov 25 10:58:57 ubuntu kernel: [76470.024000] ata4.00: NCQ disabled due to excessive errors
Nov 25 10:58:57 ubuntu kernel: [76470.024000]          res 40/00:14:88:55:9d/00:00:04:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:58:58 ubuntu kernel: [76470.336000] ata4: soft resetting port
Nov 25 10:58:58 ubuntu kernel: [76470.508000] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:58:58 ubuntu kernel: [76470.508000] ata4.00: configured for UDMA/133
Nov 25 10:58:58 ubuntu kernel: [76470.508000] ata4: EH complete
Nov 25 10:58:58 ubuntu kernel: [76470.520000] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:58:58 ubuntu kernel: [76470.520000] sd 3:0:0:0: [sdc] Write Protect is off
Nov 25 10:58:58 ubuntu kernel: [76470.524000] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 10:59:26 ubuntu kernel: [76498.480000]          res 40/00:14:e8:aa:27/00:00:05:00:00/40 Emask 0x2 (HSM violation)
Nov 25 10:59:26 ubuntu kernel: [76498.792000] ata3: soft resetting port
Nov 25 10:59:26 ubuntu kernel: [76498.964000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 10:59:26 ubuntu kernel: [76498.964000] ata3.00: configured for UDMA/133
Nov 25 10:59:26 ubuntu kernel: [76498.964000] ata3: EH complete
Nov 25 10:59:26 ubuntu kernel: [76498.964000] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 10:59:26 ubuntu kernel: [76498.964000] sd 2:0:0:0: [sdb] Write Protect is off
Nov 25 10:59:26 ubuntu kernel: [76498.964000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:02:45 ubuntu kernel: [76697.236000]          res 40/00:14:30:00:db/00:00:06:00:00/40 Emask 0x2 (HSM violation)
Nov 25 11:02:45 ubuntu kernel: [76697.548000] ata5: soft resetting port
Nov 25 11:02:45 ubuntu kernel: [76697.720000] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 11:02:45 ubuntu kernel: [76697.720000] ata5.00: configured for UDMA/133
Nov 25 11:02:45 ubuntu kernel: [76697.720000] ata5: EH complete
Nov 25 11:02:45 ubuntu kernel: [76697.720000] sd 4:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:02:45 ubuntu kernel: [76697.720000] sd 4:0:0:0: [sdd] Write Protect is off
Nov 25 11:02:45 ubuntu kernel: [76697.720000] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:03:17 ubuntu kernel: [76730.152000]          res 40/00:14:88:55:f9/00:00:06:00:00/40 Emask 0x2 (HSM violation)
Nov 25 11:03:18 ubuntu kernel: [76730.464000] ata5: soft resetting port
Nov 25 11:03:18 ubuntu kernel: [76730.636000] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 11:03:18 ubuntu kernel: [76730.636000] ata5.00: configured for UDMA/133
Nov 25 11:03:18 ubuntu kernel: [76730.636000] ata5: EH complete
Nov 25 11:03:18 ubuntu kernel: [76730.636000] sd 4:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:03:18 ubuntu kernel: [76730.636000] sd 4:0:0:0: [sdd] Write Protect is off
Nov 25 11:03:18 ubuntu kernel: [76730.636000] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:11:03 ubuntu kernel: [77195.872000]          res 40/00:1c:48:ad:21/00:00:08:00:00/40 Emask 0x2 (HSM violation)
Nov 25 11:11:04 ubuntu kernel: [77196.184000] ata3: soft resetting port
Nov 25 11:11:04 ubuntu kernel: [77196.356000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 11:11:04 ubuntu kernel: [77196.356000] ata3.00: configured for UDMA/133
Nov 25 11:11:04 ubuntu kernel: [77196.356000] ata3: EH complete
Nov 25 11:11:04 ubuntu kernel: [77196.356000] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:11:04 ubuntu kernel: [77196.356000] sd 2:0:0:0: [sdb] Write Protect is off
Nov 25 11:11:04 ubuntu kernel: [77196.356000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:11:35 ubuntu kernel: [77227.800000]          res 40/00:14:38:00:85/00:00:08:00:00/40 Emask 0x2 (HSM violation)
Nov 25 11:11:35 ubuntu kernel: [77228.112000] ata3: soft resetting port
Nov 25 11:11:36 ubuntu kernel: [77228.284000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 11:11:36 ubuntu kernel: [77228.284000] ata3.00: configured for UDMA/133
Nov 25 11:11:36 ubuntu kernel: [77228.284000] ata3: EH complete
Nov 25 11:11:36 ubuntu kernel: [77228.284000] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:11:36 ubuntu kernel: [77228.284000] sd 2:0:0:0: [sdb] Write Protect is off
Nov 25 11:11:36 ubuntu kernel: [77228.284000] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:13:45 ubuntu kernel: [77357.352000]          res 40/00:14:88:55:53/00:00:09:00:00/40 Emask 0x2 (HSM violation)
Nov 25 11:13:45 ubuntu kernel: [77357.664000] ata5: soft resetting port
Nov 25 11:13:45 ubuntu kernel: [77357.836000] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 25 11:13:45 ubuntu kernel: [77357.836000] ata5.00: configured for UDMA/133
Nov 25 11:13:45 ubuntu kernel: [77357.836000] ata5: EH complete
Nov 25 11:13:45 ubuntu kernel: [77357.836000] sd 4:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:13:45 ubuntu kernel: [77357.836000] sd 4:0:0:0: [sdd] Write Protect is off
Nov 25 11:13:45 ubuntu kernel: [77357.836000] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:22 ubuntu kernel: [77574.648000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:22 ubuntu kernel: [77574.680000] ata6.00: configured for UDMA/133
Nov 25 11:17:22 ubuntu kernel: [77574.680000] ata6: EH complete
Nov 25 11:17:22 ubuntu kernel: [77574.680000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:22 ubuntu kernel: [77574.680000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:22 ubuntu kernel: [77574.680000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:25 ubuntu kernel: [77577.704000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:25 ubuntu kernel: [77577.704000] ata6.00: configured for UDMA/133
Nov 25 11:17:25 ubuntu kernel: [77577.704000] ata6: EH complete
Nov 25 11:17:25 ubuntu kernel: [77577.704000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:25 ubuntu kernel: [77577.704000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:25 ubuntu kernel: [77577.704000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:28 ubuntu kernel: [77580.728000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:28 ubuntu kernel: [77580.728000] ata6.00: configured for UDMA/133
Nov 25 11:17:28 ubuntu kernel: [77580.728000] ata6: EH complete
Nov 25 11:17:28 ubuntu kernel: [77580.728000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:28 ubuntu kernel: [77580.728000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:28 ubuntu kernel: [77580.728000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:31 ubuntu kernel: [77583.748000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:31 ubuntu kernel: [77583.752000] ata6.00: configured for UDMA/133
Nov 25 11:17:31 ubuntu kernel: [77583.752000] ata6: EH complete
Nov 25 11:17:31 ubuntu kernel: [77583.752000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:31 ubuntu kernel: [77583.752000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:31 ubuntu kernel: [77583.752000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:34 ubuntu kernel: [77586.772000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:34 ubuntu kernel: [77586.772000] ata6.00: configured for UDMA/133
Nov 25 11:17:34 ubuntu kernel: [77586.772000] ata6: EH complete
Nov 25 11:17:34 ubuntu kernel: [77586.772000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:34 ubuntu kernel: [77586.772000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:34 ubuntu kernel: [77586.772000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 25 11:17:37 ubuntu kernel: [77589.936000]          res 41/40:00:aa:aa:c2/87:00:0b:00:00/40 Emask 0x9 (media error)
Nov 25 11:17:37 ubuntu kernel: [77589.940000] ata6.00: configured for UDMA/133
Nov 25 11:17:37 ubuntu kernel: [77589.940000] ata6: EH complete
Nov 25 11:17:37 ubuntu kernel: [77589.940000] sd 5:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Nov 25 11:17:37 ubuntu kernel: [77589.940000] sd 5:0:0:0: [sde] Write Protect is off
Nov 25 11:17:37 ubuntu kernel: [77589.940000] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by ubtutu on 2008-11-25
anyone? :)

---

### Post by ubtutu on 2008-11-25
Please anyone?

---

### Post by fjgaude on 2008-11-25
I'm no expert on hardware (or software) but I would think you have a motherboard problem...

---


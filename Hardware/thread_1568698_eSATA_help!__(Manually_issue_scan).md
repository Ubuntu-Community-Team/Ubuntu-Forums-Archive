---
title: "eSATA help!  (Manually issue scan?)"
date: 2010-09-05
forum: Hardware
---

### Post by mattlach on 2010-09-05
Hey all!

I have a purpose built AMD 780G based box running Ubuntu Server edition to serve as my NAS via eSATA.

My eSATA storage array (a Drobo S) is not useable after boot.

Here are what I think are the relevant portions of dmesg

```

dmesg| grep ata3


[    0.956381] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    1.880037] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.880430] ata3.15: Port Multiplier 1.1, 0x1a62:0x0003 r23, 14 ports, feat 0x0/0x0
[    1.880434] ata3.15: Asynchronous notification not supported, hotplug won't
[    1.881194] ata3.00: hard resetting link
[    2.410350] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    2.410399] ata3.01: hard resetting link
[    2.760497] ata3.01: SATA link down (SStatus 0 SControl 320)
[    2.760581] ata3.02: hard resetting link
[    3.110580] ata3.02: SATA link down (SStatus 0 SControl 320)
[    3.110677] ata3.03: hard resetting link
[    3.460581] ata3.03: SATA link down (SStatus 0 SControl 320)
[    3.460677] ata3.04: hard resetting link
[    3.810588] ata3.04: SATA link down (SStatus 0 SControl 320)
[    3.810685] ata3.05: hard resetting link
[    4.160584] ata3.05: SATA link down (SStatus 0 SControl 320)
[    4.160681] ata3.06: hard resetting link
[    4.510543] ata3.06: SATA link down (SStatus 0 SControl 320)
[    4.510631] ata3.07: hard resetting link
[    4.860586] ata3.07: SATA link down (SStatus 0 SControl 320)
[    4.860684] ata3.08: hard resetting link
[    5.210580] ata3.08: SATA link down (SStatus 0 SControl 320)
[    5.210676] ata3.09: hard resetting link
[    5.560584] ata3.09: SATA link down (SStatus 0 SControl 320)
[    5.560681] ata3.10: hard resetting link
[    5.910579] ata3.10: SATA link down (SStatus 0 SControl 320)
[    5.910675] ata3.11: hard resetting link
[    6.260585] ata3.11: SATA link down (SStatus 0 SControl 320)
[    6.260682] ata3.12: hard resetting link
[    6.610599] ata3.12: SATA link down (SStatus 0 SControl 320)
[    6.610689] ata3.13: hard resetting link
[    6.960590] ata3.13: SATA link down (SStatus 0 SControl 320)
[    6.960972] ata3.00: ATA-6: Drobo   3rd Gen DRDR3-A, v1.0.0, max UDMA/133
[    6.960976] ata3.00: 17179869184 sectors, multi 0: LBA48 
[    6.961352] ata3.00: configured for UDMA/133
[    6.961407] ata3: PMP SError.N set for some ports, repeating recovery
[    6.961465] ata3.00: hard resetting link
[    7.890351] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    7.891063] ata3.00: configured for UDMA/133
[    7.891114] ata3: PMP SError.N set for some ports, repeating recovery
[    7.891167] ata3.00: hard resetting link
[    8.820354] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    8.821063] ata3.00: configured for UDMA/133
[    8.821121] ata3.00: failed to recover link after 3 tries, disabling
[    8.821124] ata3.00: disabled
[    8.821128] ata3.00: PHY status changed but maxed out on retries, giving up
[    8.821131] ata3.00: Manully issue scan to resume this link
[    8.821137] ata3: EH complete

```

So it looks like it is trying to connect to the unit via eSATA 3 times and then gives up and disables the connection.  It says I can manually issue a scan to resume the link.

How do I do this?

Any other suggestions?

Thanks,
Matt

---

### Post by idallen on 2010-12-06
I get the same "Asynchronous notification not supported" using a Thermaltake BlacX Duet ST0014U 2-drive eSATA docking station under Ubuntu 10.10 x86_64.  Resetting the port doesn't help:

 echo '- - -' > /sys/class/scsi_host/host4/scan

My Vantec NexStar Dual Bay 2-drive eSATA docking station doesn't generate that error and works fine.

Themaltake (not working) says:

 Port Multiplier 1.1, 0x197b:0x2352 r0, 2 ports, feat 0x0/0x0

Vantec (works fine) says:

 Port Multiplier 1.1, 0x1095:0x5744 r33, 3 ports, feat 0x1/0x9

---


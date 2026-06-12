---
title: "strange behavior handling esata drives"
date: 2008-08-21
forum: Hardware
---

### Post by darkenergy on 2008-08-21
Hi

I noticed something strange.
I switched to Intrepid because of the newer kernel providing support for my cardbus esata card. after the dist-upgrade, the first time i inserted the card and pluged an esata device - it worked fine and i was happy.

--->
```
Aug 21 20:26:49 amphi klogd: [  157.400170] pccard: CardBus card inserted into slot 1
Aug 21 20:26:55 amphi klogd: [  163.876483] sata_inic162x 0000:03:00.0: enabling device (0000 -> 0003)
Aug 21 20:26:55 amphi klogd: [  163.876500] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 20 (level, low) -> IRQ 20
Aug 21 20:26:56 amphi klogd: [  163.917827] scsi2 : sata_inic162x
Aug 21 20:26:56 amphi klogd: [  163.919118] scsi3 : sata_inic162x
Aug 21 20:26:56 amphi klogd: [  163.919199] ata3: SATA max UDMA/133 mmio m4096@0x50000000 port 0x50000000 irq 20
Aug 21 20:26:56 amphi klogd: [  163.919207] ata4: SATA max UDMA/133 mmio m4096@0x50000000 port 0x50000040 irq 20
Aug 21 20:26:56 amphi klogd: [  164.268043] ata3: SATA link down (SStatus 0 SControl 300)
Aug 21 20:26:56 amphi klogd: [  164.624061] ata4: SATA link down (SStatus 0 SControl 300)
Aug 21 20:27:01 amphi klogd: [  169.061962] type=1503 audit(1219343221.165:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6465/net/" pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.066141] type=1503 audit(1219343221.169:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.067516] type=1503 audit(1219343221.169:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.068235] type=1503 audit(1219343221.173:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.071192] type=1503 audit(1219343221.173:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.077177] type=1503 audit(1219343221.181:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.077200] type=1503 audit(1219343221.181:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.077215] type=1503 audit(1219343221.181:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.077229] type=1503 audit(1219343221.181:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:01 amphi klogd: [  169.077323] type=1503 audit(1219343221.181:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6465/net/dev" pid=6465 profile="/usr/sbin/cupsd"
Aug 21 20:27:23 amphi klogd: [  191.490414] ata3: unhandled interrupt: cmd=0xff irq_stat=0x82 idma_stat=0x20
Aug 21 20:27:23 amphi klogd: [  191.504080] ata3: hard resetting link
Aug 21 20:27:24 amphi klogd: [  192.400063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 20:27:24 amphi klogd: [  192.400077] ata3: link online but device misclassified, retrying
Aug 21 20:27:24 amphi klogd: [  192.400083] ata3: reset failed (errno=-11), retrying in 10 secs
Aug 21 20:27:33 amphi klogd: [  201.504042] ata3: hard resetting link
Aug 21 20:27:34 amphi klogd: [  202.400074] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 20:27:34 amphi klogd: [  202.401348] ata3.00: native sectors (1) is smaller than sectors (312581808)
Aug 21 20:27:34 amphi klogd: [  202.401363] ata3.00: ATA-7: ST9160823AS, 3.AAB, max UDMA/133
Aug 21 20:27:34 amphi klogd: [  202.401369] ata3.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 0/32)
Aug 21 20:27:34 amphi klogd: [  202.403316] ata3.00: configured for UDMA/133
Aug 21 20:27:34 amphi klogd: [  202.403334] ata3: EH complete
Aug 21 20:27:34 amphi klogd: [  202.403523] scsi 2:0:0:0: Direct-Access     ATA      ST9160823AS      3.AA PQ: 0 ANSI: 5
Aug 21 20:27:34 amphi klogd: [  202.422091] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Aug 21 20:27:34 amphi klogd: [  202.422383] sd 2:0:0:0: [sdb] Write Protect is off
Aug 21 20:27:34 amphi klogd: [  202.423699] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 20:27:34 amphi klogd: [  202.428103] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Aug 21 20:27:34 amphi klogd: [  202.429071] sd 2:0:0:0: [sdb] Write Protect is off
Aug 21 20:27:34 amphi klogd: [  202.435824] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 20:27:34 amphi klogd: [  202.435835]  sdb: sdb1
Aug 21 20:27:34 amphi klogd: [  202.447581] sd 2:0:0:0: [sdb] Attached SCSI disk
Aug 21 20:27:34 amphi klogd: [  202.447669] sd 2:0:0:0: Attached scsi generic sg2 type 0
```

**but then** after a reboot it stopped working. whatever i try, dmesg shows me that:
```

[  408.172177] pccard: CardBus card inserted into slot 1
[  408.172482] sata_inic162x 0000:03:00.0: enabling device (0000 -> 0003)
[  408.172494] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[  408.212043] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  408.212584] scsi4 : sata_inic162x
[  408.217149] scsi5 : sata_inic162x
[  408.217234] ata5: SATA max UDMA/133 mmio m4096@0x50000000 port 0x50000000 irq 20
[  408.217242] ata6: SATA max UDMA/133 mmio m4096@0x50000000 port 0x50000040 irq 20
[  408.724218] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  438.724049] ata5.00: qc timeout (cmd 0xec)
[  438.740185] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  438.740191] ata5: failed to recover some devices, retrying in 5 secs
[  444.236202] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  474.236187] ata5.00: qc timeout (cmd 0xec)
[  474.252199] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  474.252211] ata5: failed to recover some devices, retrying in 5 secs
[  479.748191] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  509.748195] ata5.00: qc timeout (cmd 0xec)
[  509.764185] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  509.764196] ata5: failed to recover some devices, retrying in 5 secs
[  515.260192] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  515.784228] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  545.784204] ata6.00: qc timeout (cmd 0xec)
[  545.800161] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  545.800173] ata6: failed to recover some devices, retrying in 5 secs
[  551.296197] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  581.296200] ata6.00: qc timeout (cmd 0xec)
[  581.312174] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  581.312185] ata6: failed to recover some devices, retrying in 5 secs
[  586.808060] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  616.808050] ata6.00: qc timeout (cmd 0xec)
[  616.824170] ata6.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  616.824182] ata6: failed to recover some devices, retrying in 5 secs
[  622.320206] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

```

if you want i can also post an lspci output...
i have absolutely no idea why it stopped working. if it never worked it would be something different but now i know that it is possible and i'd like to work with esata.

I'll be grateful for every suggestion.

---

### Post by darkenergy on 2008-08-22
bump

---

### Post by gervin23 on 2008-08-26
i have this error too but with a sata based flash adapter

---

### Post by VinceLe on 2008-09-07
I had this error (link online but device misclassified) with a compactflash->sata adapter until I checked the CONFIG_SATA_PMP kernel option:

SATA Port Multiplier support                                                                                            
Location:                                                                                                                     
-> Device Drivers                                                                                                           
-> Serial ATA (prod) and Parallel ATA (experimental) drivers

---

### Post by norealname on 2009-06-19
> **VinceLe said:**
> I had this error (link online but device misclassified) with a compactflash->sata adapter until I checked the CONFIG_SATA_PMP kernel option:

SATA Port Multiplier support                                                                                            
Location:                                                                                                                     
-> Device Drivers                                                                                                           
-> Serial ATA (prod) and Parallel ATA (experimental) drivers

I have the same problem with a Cavalry esata drive.  this did not work for me. any other suggestions?

---


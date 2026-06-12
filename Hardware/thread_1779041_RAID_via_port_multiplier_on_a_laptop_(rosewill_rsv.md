---
title: "RAID via port multiplier on a laptop (rosewill rsv-s8, asus g51jx, intel 3400 series)"
date: 2011-06-09
forum: Hardware
---

### Post by zephyr707 on 2011-06-09
Hi all,

I have a fairly specific question (specific to my set of hardware, really), but I'm hoping someone has broad enough experience with RAID and port multipliers that they can help me out or at least point me in the right direction for more information, because I am at a loss as to how to figure this out and mr. google doesn't seem to be turning anything up.

I have an external enclosure ([Rosewill RSV-S8]("http://www.rosewill.com/products/1189/productDetail.htm"), that has a [Silicon Image Sil3726]("http://www.siliconimage.com/products/product.aspx?pid=26") port-multiplier in it) that comes with a [Silcon Image Sil3132R5]("http://www.siliconimage.com/products/product.aspx?pid=32") PCI-Express card.  The 3132 is in a windows XP machine and the enclosure plugs into the e-SATA port and everything is great, RAID 10 high fives all around.  

Now the hard part: I want to ditch this windows machine and just use my 64-bit ubuntu 10.10 laptop (an ASUS G51J-X3).  I think the intel 3400 series e-SATA port/controller on my laptop:

```

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1f47]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 51
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f4906000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

```

should be able to do this since it says it supports port multiplying.  But I can't get it to recognize more than a single drive when plugged in, and apparently I'm [not alone]("http://communities.intel.com/thread/16183").  Does anyone have any experience within this realm, is it even possible to do this on a laptop w/o some sort of additional hardware?

Here is some dmesg output when I connect the drive (I think I had just disconnected beforehand, hence the errors):

```

[ 1475.733816] ata6: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[ 1475.733823] ata6: irq_stat 0x00400040, connection status changed
[ 1475.733830] ata6: SError: { RecovComm PHYRdyChg CommWake DevExch }
[ 1475.733842] ata6: hard resetting link
[ 1476.479511] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1476.489907] ata6.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1476.490081] ata6.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1476.490084] ata6.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1476.490939] ata6.00: ATA-7: Hitachi HDS721010KLA330, GKAOAB0A, max UDMA/133
[ 1476.490942] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[ 1476.492308] ata6.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[ 1476.492474] ata6.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[ 1476.492480] ata6.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 1476.493429] ata6.00: configured for UDMA/133
[ 1476.493436] ata6: EH complete
[ 1476.493601] scsi 5:0:0:0: Direct-Access     ATA      Hitachi HDS72101 GKAO PQ: 0 ANSI: 5
[ 1476.493780] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1476.493988] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 1476.494037] sd 5:0:0:0: [sdb] Write Protect is off
[ 1476.494041] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1476.494061] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1476.494228]  sdb: sdb1 sdb2
[ 1476.513776] sd 5:0:0:0: [sdb] Attached SCSI disk

```

Any help would be greatly appreciated, this box of drives is the one thing holding me back from selling my windows desktop!

thanks!
zephyr

---

### Post by zephyr707 on 2011-07-20
bought a different RAID box with the RAID hardware built-in, works much better.  marked as solve.

---


---
title: "Samsung SSD 840 Not Recognized &gt;12.04"
date: 2016-04-27
forum: Hardware
---

### Post by clueo8 on 2016-04-27
I've been running 12.04 Precise for quite some time without any issues.  I've tried to go to 14.04 and also 16.04, but something within the newer kernels (I believe) is preventing it from recognizing and mounting my Samsung SSD 840 Hard drive.  I've compared dmesg from both and found that in 16.04, when grep'ing for ata, I see this in it:

```

[    0.000000] BIOS-e820: [mem 0x000000006ffa0000-0x000000006ffadfff] ACPI data
[    0.000000] NODE_DATA(0) allocated [mem 0x6ff9b000-0x6ff9ffff]
[    0.000000] Memory: 1756836K/1834228K available (8356K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 77392K reserved, 0K cma-reserved)
[    0.262137] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.269797] libata version 3.00 loaded.
[   15.606806] Write protecting the kernel read-only data: 14336k
[   15.956112] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   15.974373] ata1: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72100 irq 24
[   15.974460] ata2: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72180 irq 24
[   15.974542] ata3: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72200 irq 24
[   15.974627] ata4: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72280 irq 24
[   15.974708] ata5: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72300 irq 24
[   15.974791] ata6: SATA max UDMA/133 abar m8192@0xfae72000 port 0xfae72380 irq 24
[   16.292062] ata2: SATA link down (SStatus 0 SControl 300)
[   16.292167] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   16.292935] ata1.00: READ LOG DMA EXT failed, trying unqueued
[   16.296046] ata3: SATA link down (SStatus 0 SControl 300)
[   16.296136] ata6: SATA link down (SStatus 0 SControl 300)
[   16.296224] ata5: SATA link down (SStatus 0 SControl 300)
[   16.296330] ata4: SATA link down (SStatus 0 SControl 300)
[   21.292042] ata1.00: qc timeout (cmd 0x2f)
[   21.292120] ata1.00: failed to get NCQ Send/Recv Log Emask 0x5
[   21.292127] ata1.00: ATA-9: Samsung SSD 840 Series, DXT06B0Q, max UDMA/133
[   21.292192] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   21.292258] ata1.00: failed to get Identify Device Data, Emask 0x40
[   21.292274] ata1.00: failed to set xfermode (err_mask=0x40)
[   21.612032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   21.612688] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[   26.612034] ata1.00: qc timeout (cmd 0x2f)
[   26.612107] ata1.00: failed to get Identify Device Data, Emask 0x5
[   26.612131] ata1.00: failed to set xfermode (err_mask=0x40)
[   26.612198] ata1: limiting SATA link speed to 1.5 Gbps
[   26.612264] ata1.00: limiting speed to UDMA/133:PIO3
[   26.932035] ata1: SATA link up <unknown> (SStatus 103 SControl 310)
[   26.932317] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[   31.932030] ata1.00: qc timeout (cmd 0x2f)
[   31.932101] ata1.00: failed to get Identify Device Data, Emask 0x5
[   31.932121] ata1.00: failed to set xfermode (err_mask=0x40)
[   31.932185] ata1.00: disabled
[   31.932258] ata1: hard resetting link
[   32.252032] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   32.252109] ata1: EH complete
[   71.737766] systemd[1]: Listening on LVM2 metadata daemon socket.

```

In my working 12.04 dmesg, it gets to the point where it has direct access and then mounts the ext4, but this does not happen with anything >12.04:

```

[    1.736757] ata1.00: ATA-9: Samsung SSD 840 Series, DXT06B0Q, max UDMA/133
[    1.736766] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.736960] ata1.00: configured for UDMA/133
[    1.737284] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXT0 PQ: 0 ANSI: 5
[    1.865196] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```

I am going to try to update the firmware of the Samsung SSD tonight using their ISO from their webpage.  I found this bug report which appears to be the same issue and someone mentioned that a firmware update fixed it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1338706]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1338706")

---

### Post by clueo8 on 2016-04-28
I upgraded the firmware to the latest on the Samsung website ([http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_SSD_840_Series_DXT09B0Q_Win_Mac.iso]("http://www.samsung.com/global/business/semiconductor/minisite/SSD/downloads/software/Samsung_SSD_840_Series_DXT09B0Q_Win_Mac.iso")) and its now detecting my SSD!  I also found that adding libata.force=noncq to the kernel boot parameters would also resolve the issue but I find that later is a workaround where as the firmware update is the best fix.  Hope this helps anyone else that is running into issues with the newer kernels and their Samsung SSD...

---


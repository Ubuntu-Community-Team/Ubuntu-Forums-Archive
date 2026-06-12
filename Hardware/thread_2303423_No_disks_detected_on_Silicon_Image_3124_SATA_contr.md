---
title: "No disks detected on Silicon Image 3124 SATA controller (sata_sil24)"
date: 2015-11-18
forum: Hardware
---

### Post by Fredrik_Pettersson on 2015-11-18
I have decided to upgrade my (rather old) Gentoo installation on my server, and my choice was Ubuntu 14.04.04 server edition. Unfortunately I found an issue rather quickly, in that there seems to be some kind of problem detecting the drives connected to my SiI 3124. This card works fine in my Gentoo installation, but when the module is loaded in this Ubuntu version I get errors and no drives are detected. The kernel in my old installation is older, and another difference is that the sata_sil3124 driver is compiled into the kernel rather than as a module.

I'm hoping that someone here can provide some hints on where to start fixing this as I am at a loss on where to start. Would really like to get a fresh start with this new installation rather than keep going with the old stuff that is getting a bit messy. 

lspci -vv
```
02:02.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)    Subsystem: Silicon Image, Inc. Device 7124
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr+ Stepping+ SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e1a08000 (64-bit, non-prefetchable) [size=128]
    Region 2: Memory at e1a00000 (64-bit, non-prefetchable) [size=32K]
    Region 4: I/O ports at 2000 [size=16]
    Expansion ROM at e1a80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil24
```

Output when I do a modprobe sata_sil3124
```
[ 3813.383044] sata_sil24 0000:02:02.0: version 1.1[ 3813.383152] sata_sil24 0000:02:02.0: PCI IRQ 32 -> rerouted to legacy IRQ 16
[ 3813.383186] sata_sil24 0000:02:02.0: Applying completion IRQ loss on PCI-X errata fix
[ 3813.384211] scsi host20: sata_sil24
[ 3813.384354] scsi host21: sata_sil24
[ 3813.384492] scsi host22: sata_sil24
[ 3813.384622] scsi host23: sata_sil24
[ 3813.384704] ata21: SATA max UDMA/100 host m128@0xe1a08000 port 0xe1a00000 irq 16
[ 3813.384709] ata22: SATA max UDMA/100 host m128@0xe1a08000 port 0xe1a02000 irq 16
[ 3813.384712] ata23: SATA max UDMA/100 host m128@0xe1a08000 port 0xe1a04000 irq 16
[ 3813.384716] ata24: SATA max UDMA/100 host m128@0xe1a08000 port 0xe1a06000 irq 16
[ 3815.480033] ata21: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3820.480027] ata21.00: qc timeout (cmd 0xec)
[ 3820.480039] ata21.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3822.592027] ata21: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3832.592027] ata21.00: qc timeout (cmd 0xec)
[ 3832.592035] ata21.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3832.592040] ata21: limiting SATA link speed to 1.5 Gbps
[ 3834.704027] ata21: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3864.704025] ata21.00: qc timeout (cmd 0xec)
[ 3864.704037] ata21.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3866.816028] ata21: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3868.944040] ata22: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3873.944027] ata22.00: qc timeout (cmd 0xec)
[ 3873.960017] ata22.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3876.060045] ata22: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3886.060052] ata22.00: qc timeout (cmd 0xec)
[ 3886.076020] ata22.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3886.076030] ata22: limiting SATA link speed to 1.5 Gbps
[ 3888.172048] ata22: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3918.172026] ata22.00: qc timeout (cmd 0xec)
[ 3918.188021] ata22.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3920.304041] ata22: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3922.416053] ata23: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3927.416025] ata23.00: qc timeout (cmd 0xec)
[ 3927.432020] ata23.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3929.544044] ata23: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3939.544031] ata23.00: qc timeout (cmd 0xec)
[ 3939.560022] ata23.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3939.560031] ata23: limiting SATA link speed to 1.5 Gbps
[ 3941.672038] ata23: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3971.672029] ata23.00: qc timeout (cmd 0xec)
[ 3971.672041] ata23.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3973.784041] ata23: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 3975.932037] ata24: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3980.932029] ata24.00: qc timeout (cmd 0xec)
[ 3980.948052] ata24.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3983.060052] ata24: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[ 3993.060028] ata24.00: qc timeout (cmd 0xec)
[ 3993.076026] ata24.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 3993.076035] ata24: limiting SATA link speed to 1.5 Gbps
[ 3995.188049] ata24: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
[ 4025.188028] ata24.00: qc timeout (cmd 0xec)
[ 4025.188040] ata24.00: failed to IDENTIFY (I/O error, err_mask=0x5)
[ 4027.300039] ata24: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
```

---

### Post by Fredrik_Pettersson on 2015-11-18
Well isn't this typical. I struggle with this for a couple of days making no progress, and then 5 minutes after posting I find the solution myself. What solved it was to add the "irqpoll" option to grub, and suddenly my disks are found.

---

### Post by Yellow Pasque on 2015-11-18
> **Fredrik_Pettersson said:**
> I struggle with this for a couple of days making no progress, and then 5 minutes after posting I find the solution myself.

No worries. That's how it goes for me too. Thanks for posting the solution and marking the thread solved.

---


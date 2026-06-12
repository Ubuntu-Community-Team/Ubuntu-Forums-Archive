---
title: "eSata &amp; Port Multiplier (PMP) woes with SIL3132"
date: 2009-08-06
forum: Hardware
---

### Post by kayex on 2009-08-06
Hello,  

I'm running Ubuntu Jaunty (9.04) with 2.6.28-14-server kernel.  I've recently purchased an external eSata 4 disk enclosure (Sans Digital TR4M-B) with 4x Caviar Green 1TB drives. It came with the Silicon Image 3132 PCI-E 2x eSATA controller card.  

lspci -vnn shows it is detecting the controller card and driver:

> 
02:00.0 RAID bus controller [0104]: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller [1095:3132] (rev 01)
        Subsystem: Silicon Image, Inc. Device [1095:7132]
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e5004000 (64-bit, non-prefetchable) [size=128]
        Memory at e5000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=128]
        [virtual] Expansion ROM at a0000000 [disabled] [size=512K]
        Capabilities: [54] Power Management version 2
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Kernel driver in use: sata_sil24
However, I am unable to get Ubuntu to detect the 4 external drives.  When I boot up, it seems to hang for quite awhile and it appears as though it is scanning each drive (1-4 LEDs come off and on). 

My Syslog contains the following: 

> 

Aug  6 18:43:35 xbmc kernel: [    4.848691] sata_sil24 0000:03:00.0: version 1.1
Aug  6 18:43:35 xbmc kernel: [    4.848704] sata_sil24 0000:03:00.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
Aug  6 18:43:35 xbmc kernel: [    4.848768] sata_sil24 0000:03:00.0: setting latency timer to 64
Aug  6 18:43:35 xbmc kernel: [    4.848935] scsi6 : sata_sil24
Aug  6 18:43:35 xbmc kernel: [    4.848977] scsi7 : sata_sil24
Aug  6 18:43:35 xbmc kernel: [    4.849004] ata7: SATA max UDMA/100 host m128@0xe5004000 port 0xe5000000 irq 16
Aug  6 18:43:35 xbmc kernel: [    4.849007] ata8: SATA max UDMA/100 host m128@0xe5004000 port 0xe5002000 irq 16
Aug  6 18:43:35 xbmc kernel: [    7.060033] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [    7.060266] ata7.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
Aug  6 18:43:35 xbmc kernel: [    7.060531] ata7.00: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    7.410318] ata7.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Aug  6 18:43:35 xbmc kernel: [    7.410323] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    7.760304] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [    7.760308] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    8.110305] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [    8.110309] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    8.460306] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [    8.460310] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    8.810305] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [    8.810310] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [    9.160232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [    9.160234] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [    9.160237] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [    9.160239] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   11.380033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   12.410055] ata7.00: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   12.760318] ata7.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   12.760323] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   13.110308] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   13.110312] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   13.460305] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   13.460310] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   13.810308] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   14.160027] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   14.510230] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   14.510232] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   14.510234] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   14.510237] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   16.730033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   17.760038] ata7.00: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   18.110319] ata7.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   18.110323] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   18.460308] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   18.460312] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   18.810303] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   18.810308] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   19.160318] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   19.160322] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   19.510317] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   19.510321] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   19.860231] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   19.860233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   19.860236] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   19.860238] ata7.00: failed to recover link after 3 tries, disabling
Aug  6 18:43:35 xbmc kernel: [   19.860239] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   22.080032] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   23.460060] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   23.810303] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   23.810308] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   24.160307] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   24.160311] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   24.510317] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   24.860047] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   25.210232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   25.210234] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   25.210237] ata7.01: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   25.210239] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   27.430032] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   28.810044] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   29.160319] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   29.160323] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   29.510316] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   29.510320] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   29.860305] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   29.860310] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   30.210305] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   30.210309] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   30.560232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   30.560233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   30.560236] ata7.01: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   30.560238] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   32.780032] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   34.160028] ata7.01: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   34.510318] ata7.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   34.510322] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   34.860303] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   34.860308] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   35.210306] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   35.560017] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   35.910232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   35.910233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   35.910236] ata7.01: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   35.910238] ata7.01: failed to recover link after 3 tries, disabling
Aug  6 18:43:35 xbmc kernel: [   35.910240] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   38.130033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   39.860049] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   40.210305] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   40.210309] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   40.560303] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   40.560308] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   40.910304] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   40.910309] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   41.260231] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   41.260233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   41.260235] ata7.02: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   41.260237] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   43.480032] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   45.210033] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   45.560318] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   45.560322] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   45.910306] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   46.260038] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   46.610231] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   46.610233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   46.610236] ata7.02: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   46.610238] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   48.830033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   50.560017] ata7.02: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   50.910307] ata7.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   50.910312] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   51.260318] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   51.260323] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   51.610308] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   51.610312] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   51.960232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   51.960234] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   51.960237] ata7.02: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   51.960239] ata7.02: failed to recover link after 3 tries, disabling
Aug  6 18:43:35 xbmc kernel: [   51.960241] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   54.180032] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   56.260038] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   56.610308] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   56.960047] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   57.310231] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   57.310232] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   57.310235] ata7.03: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   57.310237] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   59.530033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   61.610023] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   61.960306] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   61.960310] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   62.310307] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   62.310311] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   62.660232] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   62.660234] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   62.660237] ata7.03: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   62.660239] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   64.880033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   66.960060] ata7.03: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   67.310306] ata7.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  6 18:43:35 xbmc kernel: [   67.660027] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   68.010230] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   68.010232] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   68.010235] ata7.03: failed to IDENTIFY (I/O error, err_mask=0x40)
Aug  6 18:43:35 xbmc kernel: [   68.010236] ata7.03: failed to recover link after 3 tries, disabling
Aug  6 18:43:35 xbmc kernel: [   68.010238] ata7.15: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   70.230033] ata7.15: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   71.630149] ata7.04: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   71.980304] ata7.04: SATA link down (SStatus 0 SControl 320)
Aug  6 18:43:35 xbmc kernel: [   73.010011] ata7.05: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   73.360231] ata7.05: failed to read SCR 1 (Emask=0x1)
Aug  6 18:43:35 xbmc kernel: [   73.360233] ata7.05: failed to read SCR 0 (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   73.360236] ata7.15: failed to write PMP_FEAT_EN (Emask=0x40)
Aug  6 18:43:35 xbmc kernel: [   73.360285] ata7: failed to recover PMP after 5 tries, giving up
Aug  6 18:43:35 xbmc kernel: [   73.360331] ata7.15: Port Multiplier detaching
Aug  6 18:43:35 xbmc kernel: [   73.360355] ata7.00: disabled
Aug  6 18:43:35 xbmc kernel: [   73.360362] ata7: exception Emask 0x3 SAct 0x0 SErr 0x0 action 0x6 frozen t4
Aug  6 18:43:35 xbmc kernel: [   73.360410] ata7: irq_stat 0x00060002, device error via D2H FIS
Aug  6 18:43:35 xbmc kernel: [   73.360457] ata7: hard resetting link
Aug  6 18:43:35 xbmc kernel: [   75.580032] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
Aug  6 18:43:35 xbmc kernel: [   75.580038] ata7: EH complete
Aug  6 18:43:35 xbmc kernel: [   77.670034] ata8: SATA link down (SStatus 0 SControl 0)
Does anyone have an idea what may be the problem?  I've tried upgrading the kernel to Karmic and still had no luck.

Any help is greatly appreciated!!

---

### Post by nxj18 on 2009-08-16
I just got the same product, the Sans Digital 4-bay bundled with an eSATA controller based on the Sil3132 chipset.  I ran into exactly the same issue, but it's got nothing to do with drivers, since if you look at the controller card's output during POST, it's only seeing one drive.

It could be that the port multiplier on the card which uses FIS-based switching isn't compatible with the backplane in the 4-bay external enclosure (it may use command-based switching instead).

Luckily, my motherboard has an eSATA port (AMD 780G chipset) and when I plugged the array into there it detected all the drives just fine. The only downside is that the controller already has four drives on it, so adding another four to the same controller will slow everything down as opposed to using a separate controller.

For now, I'm just using the motherboard controller, but I'm looking around for another eSATA controller that will properly work.  I also e-mailed Silicon Image with a description of the problem, but haven't heard anything back yet.

---

### Post by kayex on 2009-08-16
> **nxj18 said:**
> I just got the same product, the Sans Digital 4-bay bundled with an eSATA controller based on the Sil3132 chipset.  I ran into exactly the same issue, but it's got nothing to do with drivers, since if you look at the controller card's output during POST, it's only seeing one drive.

It could be that the port multiplier on the card which uses FIS-based switching isn't compatible with the backplane in the 4-bay external enclosure (it may use command-based switching instead).

Luckily, my motherboard has an eSATA port (AMD 780G chipset) and when I plugged the array into there it detected all the drives just fine. The only downside is that the controller already has four drives on it, so adding another four to the same controller will slow everything down as opposed to using a separate controller.

For now, I'm just using the motherboard controller, but I'm looking around for another eSATA controller that will properly work.  I also e-mailed Silicon Image with a description of the problem, but haven't heard anything back yet.

 From what I read on the Sans Digital forum, only 1 drive detected by the controller card's POST is normal, oddly. I tried out the card and the drive enclosure on a Windows Vista machine and it worked perfectly, unfortunately.  So I think it has something to do with the sata_sil24 driver in Ubuntu.

You're lucky your motherboard supports esata port multiplier! Mine doesn't so I'm stuck for now.  Let me know if you find a more compatible controller card or a fix. I tried the manufacturer already, but they weren't too helpful.

---


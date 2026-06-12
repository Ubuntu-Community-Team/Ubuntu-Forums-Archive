---
title: "VT6421 or bad drives"
date: 2010-09-08
forum: Hardware
---

### Post by silvatech on 2010-09-08
I recently bought a PCI VT6421 sata controller (MASSCOOL XWT-RC018) to setup two x 1 TB SAMSUNG HD103SJ drives.  Running Lucid 10.04 and 2.6.32-24-generic.

The issue that I'm seeing is that one of the drives keeps causing resets visible in the syslog. 

```
Sep  8 15:40:27 stargate kernel: [247737.552406] ata6: EH complete
Sep  8 15:40:27 stargate kernel: [247737.673210] ata6: hard resetting link
Sep  8 15:40:27 stargate kernel: [247737.992057] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  8 15:40:27 stargate kernel: [247738.008385] ata6.00: configured for UDMA/33
Sep  8 15:40:27 stargate kernel: [247738.008404] ata6: EH complete
Sep  8 15:40:27 stargate kernel: [247738.127780] ata6: hard resetting link
Sep  8 15:40:27 stargate kernel: [247738.444057] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep  8 15:40:27 stargate kernel: [247738.460384] ata6.00: configured for UDMA/33
Sep  8 15:40:27 stargate kernel: [247738.460406] ata6: EH complete
Sep  8 15:40:28 stargate kernel: [247738.578253] ata6: hard resetting link

```

So I did a smartctrl test on both new drives.  Both pass smartctl. I run a short test on /dev/sdd it passes fine.
When I run a short test on /dev/sde I get a "Interrupted (host reset)   ".  This fails on all tests for that drive.  So I assume that ATA6 is really /dev/sde  (reset happens when I run the test and


lspci:
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:07.0 Mass storage controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
02:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:09.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
02:0a.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

```

I have the VIA controller listed in memory. 

My question is, since SmartCTL passes both drives, but one drive is having issues, is it the drives fault OR the driver?  I've read that it could either, but I want to run more tests before I RMA the drive.  Could I get any assistance?

---


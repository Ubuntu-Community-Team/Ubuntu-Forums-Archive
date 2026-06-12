---
title: "The drive appears confused"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by Footer on 2007-09-01
I just started getting this message in my /var/log/syslog:

```
Sep  1 04:21:00 kubuntu64 kernel: [243008.808341] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
Sep  1 04:21:00 kubuntu64 kernel: [243008.808823] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Sep  1 04:21:00 kubuntu64 kernel: [243008.808826] ide: failed opcode was: unknown
Sep  1 04:21:00 kubuntu64 kernel: [243008.808829] hda: drive not ready for command
```

The hard drive light is constantly on yet both hard drives (SATA) seem to be working fine.  Here are a few other details about the machine:

```
dmesg|grep hda
[   34.610542]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   35.365425] hda: LITE-ON DVDRW LH-20A1P, ATAPI CD/DVD-ROM drive
[   39.922879] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache

```

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

```

```
uname -a
Linux kubuntu64 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

```

I can still play music CDs and DVDs work OK as well.  Haven't tried burning a CD/DVD yet but I'm assuming that will work fine as well.

Any ideas???

Thanks!

---

### Post by Footer on 2007-09-01
Well, I think I've resolved the hard drive light being constantly on ... There were several konqueror processes running so I killed them all and the drive light finally turned off.  Funny thing is these processes survived several reboots and logging off/on.

So that appears to have resolved at least part of the problem.  Haven't seen the confused drive message in syslog in the past few hours so perhaps it was caused by the errant konqueror processes ... ?

I'm so :confused: ... about as confused as my drives!  :lolflag:

---


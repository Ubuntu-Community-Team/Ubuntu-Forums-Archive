---
title: "High Kernel CPU Usage during file transfers"
date: 2010-04-15
forum: Hardware
---

### Post by firewrks on 2010-04-15
During local file transfers, whether USB, SATA, or eSATA, the kernel will have 100% CPU load for a specific processor core.   The the utilizing application (i.e. mv or cp) will have a nominal usage of 1-4%.  Additionally, partition type doesn't seem to factor (NTFS, FAT, EXT3, EXT4 ReiserFS all experience this). Is anyone else seeing anything similar to this?  I was considering if ResierFS BKL is potentially the issue, but the other partitions shouldn't be affected?

MotherBoard is an ASUS P5N-D (SATA/IDE(not in use)/USB) and PCIe eSATA (Sil3132)
Kubuntu 9.10 64bit 
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
07:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
08:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

Advice and guidance appreciated.

---


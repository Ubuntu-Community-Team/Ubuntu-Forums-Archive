---
title: "Out of SW-IOMMU space error"
date: 2013-06-08
forum: Hardware
---

### Post by kenhuman on 2013-06-08
Hello.  I am experiencing a problem that leads to an unresponsive system.  Relevant log excerpts follow:

syslog:
```

Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394347] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394431] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394510] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394588] DMA: Out of SW-IOMMU space for 74 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394666] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394745] DMA: Out of SW-IOMMU space for 74 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394823] DMA: Out of SW-IOMMU space for 1514 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394906] DMA: Out of SW-IOMMU space for 572 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.394993] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.395076] DMA: Out of SW-IOMMU space for 66 bytes at device 0000:08:00.0
Jun  8 12:02:48 ken-MS-7681 kernel: [14534.395160] DMA: Out of SW-IOMMU space for 1523 bytes at device 0000:08:00.0
Jun  8 12:02:58 ken-MS-7681 kernel: [14544.143933] DMA: Out of SW-IOMMU space for 1876 bytes at device 0000:06:00.0
Jun  8 12:02:58 ken-MS-7681 kernel: [14544.144013] DMA: Out of SW-IOMMU space for 1876 bytes at device 0000:06:00.0
Jun  8 12:02:58 ken-MS-7681 kernel: [14544.144091] DMA: Out of SW-IOMMU space for 1876 bytes at device 0000:06:00.0

```

kern.log:
```

Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443093] Buffer I/O error on device sda1, logical block 2610687
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443095] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error writing to inode 38011504 (offset 39321600 size 524288 starting block 2610944)
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443098] ata1: EH complete
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443216] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.2
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443268] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443270] ata1.00: failed command: WRITE DMA EXT
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443272] ata1.00: cmd 35/00:00:00:b8:3e/00:04:01:00:00/e0 tag 0 dma 524288 out
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443272]          res 50/00:00:af:6d:70/00:00:74:00:00/e0 Emask 0x40 (internal error)
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.443274] ata1.00: status: { DRDY }
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.458921] ata1.00: configured for UDMA/133
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.458934] ata1: EH complete
Jun  7 23:18:30 ken-MS-7681 kernel: [ 9014.459108] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.2

```

lspci -v
```

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. Device 7681
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 57
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at fe705000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
06:00.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at fe300000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device 7681
    Flags: bus master, fast devsel, latency 0, IRQ 58
    I/O ports at b000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-68-4c-e0-00
    Kernel driver in use: r8168

```

uname -a
```

Linux ken-MS-7681 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```





The wireless card is used sporadically, while the RTL8111/8168 is always on.  I've not noticed any strange noises or other issues from the hard drive.  I recently installed 4 8GB sticks of ram, which I've run for ~6 hours in memtest86 with no errors.  As a note, this issue was happening before the new ram was installed.  I've noticed that I have to restart networking periodically up until about the 4 hour mark after a reset, at this point the hard drive becomes read only and the machine nearly always becomes unresponsive after about 10 minutes.

Any help or advice would be greatly appreciated.

---

### Post by 2F4U on 2013-06-09
Seems to be a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132477](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132477)
[https://bugzilla.redhat.com/show_bug.cgi?id=787054](https://bugzilla.redhat.com/show_bug.cgi?id=787054)

---

### Post by kenhuman on 2013-06-09
Upgrading the kernel to 3.9.0 seems to have fixed it.  Thank you.

---


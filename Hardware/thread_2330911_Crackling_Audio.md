---
title: "Crackling Audio"
date: 2016-07-16
forum: Hardware
---

### Post by Mike_Stampone on 2016-07-16
I have crackling audio on my front panel headphone jack using Bose noise cancelling headphones.  I tried the three fixes, one per reboot, suggested at: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
Please let me know what information you need to help resolve this issue and I will be happy to provide it.  My OS version: 64-bit Ubuntu 16.04 LTS

---

### Post by T.J. on 2016-07-16
> **Mike_Stampone said:**
> I have crackling audio on my front panel headphone jack using Bose noise cancelling headphones.  I tried the three fixes, one per reboot, suggested at: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
Please let me know what information you need to help resolve this issue and I will be happy to provide it.  My OS version: 64-bit Ubuntu 16.04 LTS

Hello, Mike.  Welcome to the Forums. =)

Before I can really help you, I need to make sure that you "undo" all of the fixes that you have tried.  The "tsched=0" fix will actually cause issues in sound with certain applications, such as games from Steam.

The second thing I need is a diagnostic printout of the hardware that is actually on your system before I can comment with any reasonable degree of accuracy.  You can get this by running the command*** lspci -vnn*** in a terminal and then copy/paste the results into a message using the ```
 tag (in advanced posting mode).  The results will be long and more than one screen, but during the mouse copy you should be able to hold the mouse button while moving toward the top of the text window and it should scroll backward.  As an example:

[CODE]00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14]
    Flags: fast devsel
    Capabilities: <access denied>


00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Flags: fast devsel, IRQ 72
    Capabilities: <access denied>


00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fd000000-fe0fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fe500000-fe5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:0a.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A) [1002:5a1d] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe400000-fe4fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:0b.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (NB-SB link) [1002:5a1f] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe300000-fe3fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:b002]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at fe60b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe60a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe609000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe608000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe607000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385]
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus


00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:a132]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fe200000-fe2fffff


00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe606000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: fe100000-fe1fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe605000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe604000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: <access denied>


00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel


00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel


00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp


00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1401] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:2966]
    Flags: fast devsel, IRQ 24
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: <access denied>


01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2966]
    Flags: fast devsel, IRQ 7
    Memory at fe080000 (32-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>


02:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
    Flags: bus master, fast devsel, latency 0, IRQ 74
    Memory at fe500000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


03:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:b000]
    Flags: bus master, fast devsel, latency 0, IRQ 76
    I/O ports at d040 [size=8]
    I/O ports at d030 [size=4]
    I/O ports at d020 [size=8]
    I/O ports at d010 [size=4]
    I/O ports at d000 [size=16]
    Memory at fe410000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at fe400000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Barts XT [Radeon HD 6870] [1002:6738] (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Device [1682:3108]
    Flags: fast devsel, IRQ 10
    Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at fe320000 (64-bit, non-prefetchable) [disabled] [size=128K]
    I/O ports at c000 [disabled] [size=256]
    Expansion ROM at fe300000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci


04:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
    Subsystem: XFX Pine Group Inc. Device [1682:aa88]
    Flags: fast devsel, IRQ 7
    Memory at fe340000 (64-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci


05:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd GA-7VT600-1394 Motherboard [1458:1000]
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fe200000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at b000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Flags: bus master, fast devsel, latency 0, IRQ 73
    I/O ports at a000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169


07:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:5007]
    Flags: bus master, fast devsel, latency 0, IRQ 75
    Memory at fe100000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

```

This will tell me what hardware you have, and what drivers you are using. Once I have some idea, I may be able to help you.  I can't make any promises, but I will do my best.

---

### Post by Mike_Stampone on 2016-07-16
I was careful to always revert to the previous state whenever I  tried a fix.  Here is the information you requested.  Thank you for your  effort whether it be successful or not.

```
00:00.0 Host bridge [0600]: Intel Corporation Sky Lake Host Bridge/DRAM Registers [8086:191f] (rev 07)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Skylake Host Bridge/DRAM Registers [1462:7977]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>

00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 120
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: de000000-df0fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: [88] Subsystem: Micro-Star International Co., Ltd. [MSI] Skylake PCIe Controller (x16) [1462:7977]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral [0880]: Intel Corporation Sky Lake Gaussian Mixture Model [8086:1911]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Skylake Gaussian Mixture Model [1462:7977]
    Flags: fast devsel, IRQ 11
    Memory at df432000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [dc] Power Management version 2
    Capabilities: [f0] PCI Advanced Features

00:14.0  USB controller [0c03]: Intel Corporation Sunrise Point-H USB 3.0 xHCI  Controller [8086:a12f] (rev 31) (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H USB 3.0 xHCI Controller [1462:7977]
    Flags: bus master, medium devsel, latency 0, IRQ 121
    Memory at df410000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

00:14.2 Signal processing controller [1180]: Intel Corporation Sunrise Point-H Thermal subsystem [8086:a131] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H Thermal subsystem [1462:7977]
    Flags: fast devsel, IRQ 11
    Memory at df431000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-

00:15.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-H LPSS I2C Controller #0 [8086:a160] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H Serial IO I2C Controller [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df430000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:15.1 Signal processing controller [1180]: Intel Corporation Sunrise Point-H LPSS I2C Controller #1 [8086:a161] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H Serial IO I2C Controller [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at df42f000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller [0780]: Intel Corporation Sunrise Point-H CSME HECI #1 [8086:a13a] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H CSME HECI [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 331
    Memory at df42e000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0  SATA controller [0106]: Intel Corporation Sunrise Point-H SATA  controller [AHCI mode] [8086:a102] (rev 31) (prog-if 01 [AHCI 1.0])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H SATA controller [AHCI mode] [1462:7977]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 322
    Memory at df428000 (32-bit, non-prefetchable) [size=8K]
    Memory at df42d000 (32-bit, non-prefetchable) [size=256]
    I/O ports at f050 [size=8]
    I/O ports at f040 [size=4]
    I/O ports at f020 [size=32]
    Memory at df42c000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1c.0  PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root  Port #1 [8086:a110] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: df300000-df3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H PCI Express Root Port [1462:7977]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2  PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root  Port #3 [8086:a112] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: df200000-df2fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H PCI Express Root Port [1462:7977]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0  PCI bridge [0604]: Intel Corporation Sunrise Point-H PCI Express Root  Port #9 [8086:a118] (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: df100000-df1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H PCI Express Root Port [1462:7977]
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [220] #19
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1e.0 Signal processing controller [1180]: Intel Corporation Sunrise Point-H LPSS UART #0 [8086:a127] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H Serial IO UART [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 20
    Memory at df42b000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:1f.0 ISA bridge [0601]: Intel Corporation Sunrise Point-H LPC Controller [8086:a145] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H LPC Controller [1462:7977]
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller [0580]: Intel Corporation Sunrise Point-H PMC [8086:a121] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H PMC [1462:7977]
    Flags: fast devsel
    Memory at df424000 (32-bit, non-prefetchable) [disabled] [size=16K]

00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-H HD Audio [8086:a170] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H HD Audio [1462:d977]
    Flags: bus master, fast devsel, latency 32, IRQ 332
    Memory at df420000 (64-bit, non-prefetchable) [size=16K]
    Memory at df400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1f.4 SMBus [0c05]: Intel Corporation Sunrise Point-H SMBus [8086:a123] (rev 31)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Sunrise Point-H SMBus [1462:7977]
    Flags: medium devsel, IRQ 11
    Memory at df42a000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]
    Kernel modules: i2c_i801

01:00.0  VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX  960] [10de:1401] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] GM206 [GeForce GTX 960] [1462:3205]
    Flags: bus master, fast devsel, latency 0, IRQ 333
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at df000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_361

01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:3205]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at df080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242] (prog-if 30 [XHCI])
    Subsystem: Micro-Star International Co., Ltd. [MSI] ASM1142 USB 3.1 Host Controller [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df300000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [200] Advanced Error Reporting
    Capabilities: [280] #19
    Capabilities: [300] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller [1969:e0a1] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E2400 Gigabit Ethernet Controller [1462:7977]
    Flags: bus master, fast devsel, latency 0, IRQ 334
    Memory at df200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable+ Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-24-2f-df-4c-cc-6a-ff
    Kernel driver in use: alx
    Kernel modules: alx

04:00.0  Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe  SSD Controller [144d:a802] (rev 01) (prog-if 02 [NVM Express])
    Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller [144d:a801]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at df110000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at c000 [size=256]
    Expansion ROM at df100000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [b0] MSI-X: Enable+ Count=9 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [158] Power Budgeting <?>
    Capabilities: [168] #19
    Capabilities: [188] Latency Tolerance Reporting
    Capabilities: [190] L1 PM Substates
    Kernel driver in use: nvme
    Kernel modules: nvme

```

---

### Post by T.J. on 2016-07-16
You, sir, have some very nice hardware.  Do you have a Skylake CPU as well?  I noted your internal Intel HD sound card.  Yes, those do give us a problem now and then.  I'm going to ruminate for a bit to see what I can think of to help you since you have already tried most of the usual fixes.

---

### Post by Yellow Pasque on 2016-07-16
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by T.J. on 2016-07-17
Back to basics.  A test for Pulseaudio:

1. Open a terminal.  
2. install vlc: apt-get install vlc.
3. In VLC 's settings select alsa as output. Save it.  Close and restart VLC.
4. Force Pulseaudio to shutdown.[I] pulseaudio -- kill
5. [/I] Play something in VLC. Does it still crackle? Does it work at all?


After that just log out and back in and everything will be back to normal. It will restart Pulseaudio.

Set VLC for Pulseaudio. Close and restart VLC.
Test Playback.

If it crackles for PA but not when it has been killed then it is a Pulseaudio problem.  If it still crackles when PA is off, it relates to ALSA.  Be sure to test several different kinds of media video and music formats both times.  It may be a buggy codec.

---

### Post by Yellow Pasque on 2016-07-17
^Isn't Pulse going to autorespawn?
```
echo autospawn = no >> ~/.config/pulse/client.conf
```

Edit: Also curious if these specific headphones have been tested on another machine or a different pair of headphones has been tested on the machine in question.

---

### Post by sli908 on 2016-08-30
Hey, I'm not the OP but I have the exact same issue and at least for me I noticed the crackling is present even when pulseaudio is killed.

---


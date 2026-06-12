---
title: "HP Pavilion A1118x"
date: 2010-12-02
forum: Hardware
---

### Post by JuKen on 2010-12-02
Hi all,

My brother recently got an HP Pavilion A1118x for free and installed the latest version of Ubuntu on it. The machine has been running great but experiencing some video lag when scrolling. Does anyone have any recommendations on how we might be able to fix this?

Below is the output of lspci -v:

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 32
	Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-amd64
	Kernel modules: amd64-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ed000000-ed0fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
	Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 128
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 4000 [size=16]
	Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Hewlett-Packard Company Device 2a05
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at b000 [size=256]
	I/O ports at b400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at ed104000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at ed100000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at ed101000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at ed102000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at b800 [size=256]
	Memory at ed103000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 60000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sis900
	Kernel modules: sis900

00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a04
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	I/O ports at bc00 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at cc00 [size=16]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: sata_sis
	Kernel modules: sata_sis

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Netgear GA311
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	I/O ports at d400 [size=256]
	Memory at ed105000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 60020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Device 044c
	Flags: bus master, medium devsel, latency 32, IRQ 3
	Memory at ed106000 (32-bit, non-prefetchable) [size=256]
	I/O ports at d800 [size=8]
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Device 0003:000f
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at ed107000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at e000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 2a06
	Flags: 66MHz, medium devsel, IRQ 5
	BIST result: 00
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at a000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: sisfb

---


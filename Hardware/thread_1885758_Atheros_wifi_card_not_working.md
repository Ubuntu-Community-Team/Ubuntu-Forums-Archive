---
title: "Atheros wifi card not working"
date: 2011-11-23
forum: Hardware
---

### Post by jonnyhoffer on 2011-11-23
Hi guys, I'm kinda new to Ubuntu, but ever since I installed it on my Lenovo B575, I haven't been able to get my wifi card to work. It recognizes it, and says that it has a driver installed, but when I try to turn it on, it automatically turns it back off.... 

Here's what I get after entering "lspci -v" in Terminal

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 397b
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at e0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
	Subsystem: Lenovo Device 397b
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at e0244000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 2118 [size=8]
	I/O ports at 2124 [size=4]
	I/O ports at 2110 [size=8]
	I/O ports at 2120 [size=4]
	I/O ports at 2100 [size=16]
	Memory at e024b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at e024a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at e024b500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at e0249000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at e024b400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
	Subsystem: Lenovo Device 397b
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Lenovo Device 397b
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at e0240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Lenovo Device 397b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at e0248000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: e0100000-e01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
	Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
	Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
	Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
	Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
	Flags: fast devsel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Lenovo Device 3975
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at 1000 [size=256]
	Memory at e0004000 (64-bit, prefetchable) [size=4K]
	Memory at e0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lenovo Device 30a1
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at e0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k


If there's anything else you want me to add about it, just let me know. :) 

Thanks!!!

---


---
title: "Getting sound to work"
date: 2009-10-18
forum: Hardware
---

### Post by aeubz on 2009-10-18
Hi I'm having trouble getting my sound to work on my computer.  I'm kinda new to linux. -TIA

Distro: Ubuntu 9.10

typed in command : lspci -v

Output:

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fdefec00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000cdf00000-00000000cdffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe000000-fe9fffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fdeff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=32]
	Memory at fdeff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: medium devsel, IRQ 15
	Memory at fdeff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 6740
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at c800 [size=256]
	Memory at fdfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at cdff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1067
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

06:00.0 VGA compatible controller: ATI Technologies Inc Device 9488
	Subsystem: Micro-Star International Co., Ltd. Device 7220
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at e000 [size=256]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

06:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
	Subsystem: Micro-Star International Co., Ltd. Device aa38
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at febec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---


---
title: "Audio Issues."
date: 2010-09-22
forum: Hardware
---

### Post by Linuxperiment on 2010-09-22
Hi, can anyone help me with this issue? It had sound in Windows 7 of course....but no luck in Linux. This is a fairly new laptop. Here's the lspci -v output. I would like to add that sound initially works when using the live session.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 90200000-903fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Capabilities: <access denied>

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 90100000-901fffff
	Prefetchable memory behind bridge: 0000000070000000-00000000701fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 70200000-702fffff
	Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 4038 [size=8]
	I/O ports at 404c [size=4]
	I/O ports at 4030 [size=8]
	I/O ports at 4048 [size=4]
	I/O ports at 4010 [size=16]
	Memory at 90408000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 90407000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 90408600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 90406000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 90408500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: 66MHz, medium devsel

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 90400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 90405000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 90404000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 90408400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=256]
	Memory at 90300000 (32-bit, non-prefetchable) [size=64K]
	Memory at 90200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 90100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1444
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at 2000 [size=256]
	Memory at 90010000 (64-bit, prefetchable) [size=4K]
	Memory at 90000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 90020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169

```

---

### Post by Linuxperiment on 2010-09-22
Ugh, I really want this to work but I'll probably switch back to Windows if I can't get any help.

Note: I've made sure nothing is muted.

---


---
title: "printer problems - new motherboard"
date: 2009-07-23
forum: Hardware
---

### Post by hubiedo on 2009-07-23
i recently was forced to build a new box and used a asus m3a78-emh-hdmi motherboard. i plugged in to the lpt onboard port and installed cable etc.

the printer was recognized and did print from the previous ubuntu 8.04 install but would periodically reboot w/o warning when tried to print to samsung ml-2510 printer. i used the previous hard drive w/ 8.04 installed and working.

i think it might be a pin configuration deal, not sure. then i said easy deal get a parallel port card. wrong. i got a pci netmos 9865 card and installed. i still have nothing to print with. when i go to their website for drivers i try to sign up and am in a big circle w/ no resolution. 

can anyone help? suggestions for on board port fix? fix the pci controller card? do i need to reinstall ubuntu, run some kind of repair?

any other ideas would be helpful.

the system sees the parallel port card == see below;

$ lspci -v

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Unknown device 82f1
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: ASUSTeK Computer Inc. Unknown device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fbc00000-fbdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
	Capabilities: <access denied>

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 221
	I/O ports at b000 [size=8]
	I/O ports at a000 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 7000 [size=16]
	Memory at fbbff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbbfe000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fbbfd000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	Memory at fbbff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbbfc000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbbfb000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
	Memory at fbbfa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: ASUSTeK Computer Inc. Unknown device 8230
	Flags: bus master, slow devsel, latency 64, IRQ 18
	Memory at fbbf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fbbf9000 (32-bit, non-prefetchable) [size=4K]

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fbc00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82c6
	Flags: bus master, fast devsel, latency 0, IRQ 222
	I/O ports at d800 [size=256]
	Memory at fbeff000 (64-bit, non-prefetchable) [size=4K]
	Memory at faff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbec0000 [disabled] [size=128K]
	Capabilities: <access denied>

03:06.0 Parallel controller: NetMos Technology Unknown device 9865 (prog-if 03 [IEEE1284])
	Subsystem: Unknown device a000:2000
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=8]
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

03:06.2 Parallel controller: NetMos Technology Unknown device 9865 (prog-if 03 [IEEE1284])
	Subsystem: Unknown device a000:2000
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=8]
	Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
	Memory at fbffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

03:07.0 SCSI storage controller: Adaptec AIC-7861 (rev 03)
	Subsystem: Adaptec AHA-2940AU Single
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at e000 [disabled] [size=256]
	Memory at fbffb000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at fbf00000 [disabled] [size=64K]
	Capabilities: <access denied>

---


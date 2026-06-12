---
title: "No sound, please help!"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by fargus on 2007-12-12
Sound does not work at all. No system sounds, mp3, wav, microphone does not work. please help! here is some info.

lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
Subsystem: ATI Technologies Inc Unknown device 1234
Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
I/O behind bridge: 00009000-00009fff
Memory behind bridge: cfd00000-cfefffff
Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
Memory behind bridge: f0200000-f02fffff
Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
I/O behind bridge: 0000a000-0000afff
Memory behind bridge: f0300000-f03fffff
Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
I/O ports at 8440 [size=8]
I/O ports at 8434 [size=4]
I/O ports at 8438 [size=8]
I/O ports at 8430 [size=4]
I/O ports at 8400 [size=16]
Memory at f0409000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
Memory at f0404000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
Memory at f0405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
Memory at f0406000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
Memory at f0407000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
Memory at f0408000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
Memory at f0409400 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
Subsystem: Gateway 2000 Unknown device 0566
Flags: 66MHz, medium devsel
I/O ports at 8410 [size=16]
Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
Subsystem: Gateway 2000 Unknown device 0566
Flags: slow devsel, IRQ 16
Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
Flags: bus master, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=14, subordinate=19, sec-latency=64

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

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, fast devsel, latency 64, IRQ 18
Memory at b0000000 (64-bit, prefetchable) [size=256M]
Memory at cfdf0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at 9000 [size=256]
Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller
Flags: bus master, fast devsel, latency 64, IRQ 19
Memory at cfdec000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

08:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f0210000 (32-bit, non-prefetchable) [size=64K]
Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
Subsystem: Gateway 2000 Unknown device 0566
Flags: bus master, fast devsel, latency 0, IRQ 19
I/O ports at a000 [size=256]
Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
Capabilities: <access denied>


What does all this mean and what should I do?

---


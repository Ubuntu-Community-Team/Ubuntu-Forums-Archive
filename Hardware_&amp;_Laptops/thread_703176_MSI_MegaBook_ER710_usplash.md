---
title: "MSI MegaBook ER710 usplash"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by altoas on 2008-02-21
Hi, I have MSI MEGABOOK ER710 and Kubuntu/Ubuntu desktop's. When I boot from the Live CD's usplash is displayed correctly, but after the install durring boot there's no usplash and no monitor signal. just after GRUB boot's the kernel and befor GDM or KDM. I've pluged external monitor during boot one time and on the external monitor there was the usplash screen. it's bugging me because i can't see any diagnostics. how can I fix this, is there any way?
I'm using Ubuntu/Kubuntu 7.10 GENERIC Kernel 2.6.22-14
My lspci:
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 0

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 248
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=248
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fd500000-fd6fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: fd700000-fd7fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Capabilities: [b8] HyperTransport: MSI Mapping

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd800000-fe1fffff
        Prefetchable memory behind bridge: 00000000f8000000-00000000faffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Capabilities: [b8] HyperTransport: MSI Mapping

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe200000-fe2fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
        I/O ports at a000 [size=8]
        I/O ports at 9000 [size=4]
        I/O ports at 8000 [size=8]
        I/O ports at 7000 [size=4]
        I/O ports at 6000 [size=16]
        Memory at fd4ff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
        Memory at fd4fe000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at fd4fd000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at fd4fc000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at fd4fb000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at fd4fa000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
        Memory at fd4ff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, slow devsel, latency 240, IRQ 17
        Memory at fd4f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe300000-febfffff
        Prefetchable memory behind bridge: fb000000-fcffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, fast devsel, latency 248, IRQ 19
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd6f0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at b000 [size=256]
        Memory at fd500000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, fast devsel, latency 248, IRQ 21
        Memory at fd6e8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fd7f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, fast devsel, latency 0, IRQ 21
        I/O ports at c800 [size=256]
        Memory at fe2ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fe2c0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

06:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 16
        Memory at fe300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 80000000-83fff000 (prefetchable)
        Memory window 1: 84000000-87fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

06:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: slow devsel, IRQ 16
        Memory at fe3ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [a0] Power Management version 2

06:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: slow devsel, IRQ 3
        Memory at fe3fe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [a0] Power Management version 2

06:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 42d7
        Flags: bus master, medium devsel, latency 248, IRQ 16
        Memory at fe3fd000 (32-bit, non-prefetchable) [size=4K]
        Memory at fe3ff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [60] Power Management version 2

---


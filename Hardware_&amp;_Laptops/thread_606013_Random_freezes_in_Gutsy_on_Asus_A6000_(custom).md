---
title: "Random freezes in Gutsy on Asus A6000 (custom)"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Inputevilsoundingnamehere on 2007-11-07
I'm having problems with random freezes, sometimes the whole computer stops, and other times it's just a couple windows. Had this problem with the Feisty, but it happened more frequently then.

if more information is needed, or anything else, just ask:)

Thanks!

$ lspci -v

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000bdf00000-00000000ddefffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1123
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe000000-fe0fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe100000-fe1fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e880 [size=32]
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000bdf00000-00000000ddefffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1123
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe000000-fe0fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe100000-fe1fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHC00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000bdf00000-00000000ddefffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1123
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe000000-fe0fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe100000-fe1fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe200000-feafffff
	Prefetchable memory behind bridge: 00000000ddf00000-00000000dfefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600] (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 10b2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fdff0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at c800 [size=256]
	Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe0e0000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

04:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: medium devsel, IRQ 3
	Memory at feaff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
I])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe200000-feafffff
	Prefetchable memory behind bridge: 00000000ddf00000-00000000dfefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600] (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 10b2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fdff0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at c800 [size=256]
	Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe0e0000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

04:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: medium devsel, IRQ 3
	Memory at feaff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe200000-feafffff
	Prefetchable memory behind bridge: 00000000ddf00000-00000000dfefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600] (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 10b2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fdff0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fdfc0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at c800 [size=256]
	Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe0e0000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001

04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

04:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
	Subsystem: ASUSTeK Computer Inc. Unknown device 1237
	Flags: medium devsel, IRQ 3
	Memory at feaff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


/var/log/messages after freeze
> 
Nov  7 20:34:43 system666 -- MARK --
Nov  7 20:47:43 system666 kernel: [ 8002.904000] ata1.01: qc timeout (cmd 0xa0)
Nov  7 20:47:54 system666 kernel: [ 8002.904000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Nov  7 20:47:54 system666 kernel: [ 8007.952000] ata1: port is slow to respond, please be patient (Status 0xd1)
Nov  7 20:47:54 system666 kernel: [ 8012.936000] ata1: device not ready (errno=-16), forcing hardreset
Nov  7 20:47:54 system666 kernel: [ 8012.936000] ata1: soft resetting port
Nov  7 20:47:54 system666 kernel: [ 8013.312000] ata1.00: configured for UDMA/100
Nov  7 20:47:54 system666 kernel: [ 8013.508000] ata1.01: configured for UDMA/33
Nov  7 20:47:54 system666 kernel: [ 8013.508000] ata1: EH complete
Nov  7 20:47:54 system666 kernel: [ 8013.528000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov  7 20:47:54 system666 kernel: [ 8013.544000] sd 0:0:0:0: [sda] Write Protect is off
Nov  7 20:47:54 system666 kernel: [ 8013.568000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  7 20:47:54 system666 kernel: [ 8013.608000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov  7 20:47:54 system666 kernel: [ 8013.628000] sd 0:0:0:0: [sda] Write Protect is off
Nov  7 20:47:54 system666 kernel: [ 8013.664000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  7 20:48:40 system666 kernel: [ 8059.652000] ata1.01: qc timeout (cmd 0xa0)
Nov  7 20:48:51 system666 kernel: [ 8059.652000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Nov  7 20:48:51 system666 kernel: [ 8064.692000] ata1: port is slow to respond, please be patient (Status 0xd1)
Nov  7 20:48:51 system666 kernel: [ 8069.676000] ata1: device not ready (errno=-16), forcing hardreset
Nov  7 20:48:51 system666 kernel: [ 8069.676000] ata1: soft resetting port
Nov  7 20:48:51 system666 kernel: [ 8070.040000] ata1.00: configured for UDMA/100
Nov  7 20:48:51 system666 kernel: [ 8070.240000] ata1.01: configured for UDMA/33
Nov  7 20:48:51 system666 kernel: [ 8070.240000] ata1: EH complete
Nov  7 20:48:51 system666 kernel: [ 8070.256000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov  7 20:48:51 system666 kernel: [ 8070.272000] sd 0:0:0:0: [sda] Write Protect is off
Nov  7 20:48:51 system666 kernel: [ 8070.296000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  7 20:48:51 system666 kernel: [ 8070.336000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov  7 20:48:51 system666 kernel: [ 8070.352000] sd 0:0:0:0: [sda] Write Protect is off
Nov  7 20:48:51 system666 kernel: [ 8070.384000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  7 20:49:01 system666 kernel: [ 8080.380000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Nov  7 20:49:01 system666 kernel: [ 8080.576000] ata1.00: configured for UDMA/100
Nov  7 20:49:01 system666 kernel: [ 8080.764000] ata1.01: configured for UDMA/33
Nov  7 20:49:01 system666 kernel: [ 8080.764000] ata1: EH complete
Nov  7 20:49:01 system666 kernel: [ 8080.780000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov  7 20:49:01 system666 kernel: [ 8080.796000] sd 0:0:0:0: [sda] Write Protect is off
Nov  7 20:49:01 system666 kernel: [ 8080.820000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


---

### Post by mezhaka on 2007-12-09
it seems i hvae the same problem, at least my /var/log/messages says something similar
```

Dec  9 20:21:50 hatka kernel: [ 2219.180000] ata1.01: qc timeout (cmd 0xa0)
Dec  9 20:21:50 hatka kernel: [ 2219.180000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
Dec  9 20:21:55 hatka kernel: [ 2224.220000] ata1: port is slow to respond, please be patient (Status 0xd0)
Dec  9 20:22:00 hatka kernel: [ 2229.204000] ata1: device not ready (errno=-16), forcing hardreset
Dec  9 20:22:00 hatka kernel: [ 2229.204000] ata1: soft resetting port
Dec  9 20:22:01 hatka kernel: [ 2229.572000] ata1.00: configured for UDMA/100
Dec  9 20:22:01 hatka kernel: [ 2229.760000] ata1.01: configured for UDMA/25
Dec  9 20:22:01 hatka kernel: [ 2229.760000] ata1: EH complete
Dec  9 20:22:01 hatka kernel: [ 2229.768000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Dec  9 20:22:01 hatka kernel: [ 2229.776000] sd 0:0:0:0: [sda] Write Protect is off
Dec  9 20:22:01 hatka kernel: [ 2229.792000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  9 20:22:01 hatka kernel: [ 2229.808000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
Dec  9 20:22:01 hatka kernel: [ 2229.816000] sd 0:0:0:0: [sda] Write Protect is off
Dec  9 20:22:02 hatka kernel: [ 2230.192000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

i am on asus a6000 series. not sure if it's a model number -- there's also an asus z92v label on the bottom of this laptop.
it looks like a hdd problems. have you somehow solved this issue? i promise to post here if i find out anything new.

---

### Post by EnglishJoel on 2007-12-09
Looks like the same problem I started a thread about this morning, with different hardware.

My thread is called "Hard drive keeps resetting"

I have not had any complete system freezes, but I have had many short freezes. 

I'm at a loss.

---

### Post by mezhaka on 2007-12-10
there's a launchpad bug here, despite there's plenty of solutions there -- i did not tried any of them yet. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603")

---

### Post by mezhaka on 2007-12-13
> **mezhaka said:**
> there's a launchpad bug here, despite there's plenty of solutions there -- i did not tried any of them yet. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603")

i have successfully get rid of the problem using this guide

---


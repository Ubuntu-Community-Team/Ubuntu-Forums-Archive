---
title: "Acer Aspire 5672Wlmi Texas Instruments 5-in-1 Multimedia Card Reader"
date: 2010-02-18
forum: Hardware
---

### Post by m0r6h3us on 2010-02-18
Hello everyone,
I noticed my Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) doesn't work on Ubuntu 9.10 - Karmic Koala.
Laptop: Acer Aspire 5672 Wlmi.

I tried using older post, but nothing.

Here is my lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c8100000-c81fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d7ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 44000000-440fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 44100000-441fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at c8004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c8400000-c84fffff
	Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: medium devsel, IRQ 10
	I/O ports at 18c0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c8120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at 44000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at 44100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at c8404000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at c8405000 (32-bit, non-prefetchable) [size=2K]
	Memory at c8400000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Acer Incorporated [ALI] Device 0094
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at c8406000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

Thanks to all

---


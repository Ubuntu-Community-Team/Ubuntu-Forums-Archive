---
title: "PCMCIA card/slot not being detected?"
date: 2008-09-04
forum: Hardware
---

### Post by pejsaboy on 2008-09-04
I've got an older laptop [Compaq Presrio 2100] that I just installed ubuntu on, and I'm having trouble getting a netgear WPN511 pcmcia card working. According to the madwifi website, it uses the AR5212 chipset and is compatible with the driver. I think the problem is that ubuntu isn't seeing the pcmcia slot at all. Here's the output of lspci -v, can anyone confirm this yes or no?
```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Memory at d4005000 (32-bit, prefetchable) [size=4K]
	Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d4300000-d43fffff
	Prefetchable memory behind bridge: dc000000-dfffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [60] Power Management version 2

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1000 [size=256]
	Memory at d4001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: [a0] Power Management version 1

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: medium devsel, IRQ 10
	Memory at d4002000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1400 [size=256]
	Capabilities: [40] Power Management version 2

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
	Memory at d4003000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 44000000-47fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 2000 [size=16]
	Capabilities: [60] Power Management version 2

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 90, IRQ 10
	I/O ports at 2400 [size=256]
	Memory at d4004000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 48000000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	I/O ports at 9000 [size=256]
	Memory at d4300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d4320000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2

```

---


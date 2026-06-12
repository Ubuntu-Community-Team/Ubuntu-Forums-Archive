---
title: "PCI Modem not working"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by mercuryone on 2005-04-27
I use a D-Link ESS PCI modem and want to use it in Woary but it doesn't automatically detect it. I am unsure as to how to proceed in resolving this issue. I am posting the output of lspci -v below some urgent assistance would be appreciated.

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.4
	RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Asustek Computer, Inc.: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at c000 [size=32]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ea004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at ea005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at ea000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard onboard nForce2 Ethernet
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ea001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c400 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: Asustek Computer, Inc.: Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at b000 [size=256]
        I/O ports at b400 [size=128]
        Memory at ea002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Asustek Computer, Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: d8000000-e7ffffff

0000:01:0a.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
        Subsystem: ESS Technology ES2838/2839 SuperLink Modem
        Flags: fast devsel, IRQ 5
        I/O ports at 9000 [size=16]
        Capabilities: <available only to root>

0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA])
        Subsystem: Info-Tek Corp.: Unknown device 0170
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at a000 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
        Subsystem: Info-Tek Corp.: Unknown device 0171
        Flags: 66MHz, medium devsel
        Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root>

---


---
title: "Default interrupts, irq's"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by sornen on 2005-10-22
A couple of questions on the interrupts.  

1) My interrupts for the sound card originally shared the same interrupts as the video card.  This caused problems with latency for a realtime application.  I stuck the sound card in a different pci slot and the got a different interrupt assigned.  But now it shares it with another device.  How can assign a different interrupt to my sound card.  I have fiddled with the bios assignment but this makes no difference.  I notice that Fedora assigns a lower level interrupt and there is no conflict.

2) Also with the lspci command somethings come up with unknown device.  Is this bad?

>lspci -v

```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at c400 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 2000 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (p rog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fc002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1) (p rog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fc003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2) (p rog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fc004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fc000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=8]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2) (pr og-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: f8000000-f9ffffff
        Prefetchable memory behind bridge: e0000000-efffffff

0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00009000-0000afff
        Memory behind bridge: fa000000-fbffffff

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation NV 36 [GeForce 5700] (rev a1) (prog-if 00 [VGA])
        Subsystem: LeadTek Research Inc.: Unknown device 2982
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:02:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 9000 [size=64]
        Capabilities: <available only to root>

0000:02:07.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (re v 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9400 [size=8]
        Capabilities: <available only to root>

0000:02:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04 ) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at fb008000 (32-bit, non-prefetchable) [size=2K]
        Memory at fb004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Et hernet 10/100/1000Base-T Adapter (rev 13)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at fb000000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at 9800 [size=256]
        Capabilities: <available only to root>

0000:02:0d.0 Unknown mass storage controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
        Subsystem: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3512 [S ATALink/SATARaid] Serial ATA Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        I/O ports at 9c00 [size=8]
        I/O ports at a000 [size=4]
        I/O ports at a400 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at ac00 [size=16]
        Memory at fb009000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <available only to root>

```

---


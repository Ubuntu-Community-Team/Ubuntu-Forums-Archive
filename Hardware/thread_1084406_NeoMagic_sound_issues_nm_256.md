---
title: "NeoMagic sound issues nm_256"
date: 2009-03-02
forum: Hardware
---

### Post by smallgodinacan on 2009-03-02
I am beating my head against the wall on this one. I am try to get Xubuntu 8.04.1 going on a decommissioned Amrel RT686 notebook but I can't get the sound going at all. I have searched around and can't seem to find a working guide on getting the sound drivers which come with the modules to actually work.

Info on the system from lspci -v:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e6000000-e67fffff
        Prefetchable memory behind bridge: e4000000-e5ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at e000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9

00:0c.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
	Subsystem: Unknown device 3412:7856
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at e6800000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

00:0c.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
	Subsystem: Unknown device 3412:7856
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at e6804000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 18000000-1bfff000 (prefetchable)
	Memory window 1: 1c000000-1ffff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20) (prog-if 00 [VGA controller])
	Subsystem: Neomagic Corporation NM2200 [MagicGraph 256AV]
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at e4000000 (32-bit, prefetchable) [size=16M]
	Memory at e6000000 (32-bit, non-prefetchable) [size=4M]
	Memory at e6400000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
	Flags: medium devsel, IRQ 11
	Memory at e5000000 (32-bit, prefetchable) [size=4M]
	Memory at e6500000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Belkin Unknown device 7c1a
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at 1c000000 (32-bit, non-prefetchable) [size=8K]

```

Any advice and hints would be greatly appreciated.

---

### Post by smallgodinacan on 2009-03-02
I am going to give sudo dpkg-reconfigure alsa-source a try to see if I can get pointed to the file. It seems a lot of other people have used alsaconf in other distro to get this chip working but *ubuntu doesn't include the package.

---

### Post by mister_playboy on 2009-03-27
I'm having the same problem.  There is an ALSA driver for this chipset, but I still can't get the sound to work.

---


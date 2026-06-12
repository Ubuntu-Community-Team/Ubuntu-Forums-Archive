---
title: "No Sound and XFCE Won't Load"
date: 2008-11-02
forum: Hardware
---

### Post by rrriles on 2008-11-02
I just ran the command:

lspci -v

and this is the output I received:

riley@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
	Flags: bus master, medium devsel, latency 32
	Memory at d0000000 (32-bit, prefetchable) [size=256M]

00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Dell MagicGraph 128XD
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=16M]
	Memory at fde00000 (32-bit, non-prefetchable) [size=2M]
	Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]

00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Subsystem: Dell Unknown device 0074
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at ece0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Flags: medium devsel, IRQ 9

05:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)
	Subsystem: Xircom Cardbus Ethernet 10/100
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1800 [size=128]
	Memory at 2c000000 (32-bit, non-prefetchable) [size=2K]
	Memory at 2c000800 (32-bit, non-prefetchable) [size=2K]
	[virtual] Expansion ROM at 28000000 [disabled] [size=16K]
	Capabilities: <access denied>

05:00.1 Serial controller: Xircom Cardbus Ethernet + 56k Modem (rev 03) (prog-if 02 [16550])
	Subsystem: Xircom CBEM56G-100 Ethernet + 56k Modem
	Flags: medium devsel, IRQ 11
	I/O ports at 1880 [size=8]
	Memory at 2c001000 (32-bit, non-prefetchable) [size=2K]
	Memory at 2c001800 (32-bit, non-prefetchable) [size=2K]
	[virtual] Expansion ROM at 28004000 [disabled] [size=16K]
	Capabilities: <access denied>

My question are:

1. Is my sound card installed according to the output and just not detected or is it not even recognizing it at all? I have a Dell CPi D266XT laptop and the onboard sound is turned on in the bios.

2. My XFCE doesn't always load. I've run it once, but have not seen it under my applications menu since. Any suggestions?

---


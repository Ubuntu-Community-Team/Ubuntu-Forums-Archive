---
title: "aplay -l"
date: 2008-07-24
forum: General Help
---

### Post by Uchiha_madara on 2008-07-24
When I Type This Command

> aplay -l

this is The Message :

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



When I tried the Alsamixer :

this is The Result :

> alsamixer: function snd_mixer_load failed: No such file or directory


When I used lspci This is The Result :

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0100000-d01fffff
	Prefetchable memory behind bridge: d4000000-d7ffffff
	Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at d0004000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 10000000 [disabled] [size=512K]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: 66MHz, medium devsel
	I/O ports at 8040 [size=16]
	Memory at d0004400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 88 [Master SecP])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0200000-d02fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 21
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at 9000 [size=256]
	Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0120000 [disabled] [size=128K]
	Capabilities: <access denied>

09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
	Memory window 0: 14000000-17fff000 (prefetchable)
	Memory window 1: 18000000-1bfff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff31
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at a000 [size=256]
	Memory at d0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7094
	Flags: bus master, medium devsel, latency 168, IRQ 19
	Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


and The Sound Card is Realtek High Definition  Audio

This Problem is Cracking My head I don't Know what shall I do ...:mad:

---

### Post by Uchiha_madara on 2008-07-24
Pleaaaase help>>>>>>>>>>>>>>>>>..

---

### Post by caljohnsmith on 2008-07-24
I think it would help if you would tell us what you would like to accomplish. Are you just trying to get alsamixer working, but otherwise sound works fine? Or is sound not working either? If not, please give more details.

---


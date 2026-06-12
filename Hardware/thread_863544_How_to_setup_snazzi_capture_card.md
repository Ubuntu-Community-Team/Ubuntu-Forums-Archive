---
title: "How to setup snazzi capture card?"
date: 2008-07-18
forum: Hardware
---

### Post by Rain_Wolf on 2008-07-18
Hi!
I have a snazzi capture card. I have installed tvtime, but i don't have any source from it. lspci in my pc:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
[COLOR="Red"]05:02.0 Multimedia video controller: Winbond Electronics Corp W99200F MPEG-1 Video Encoder (rev 03)[/COLOR]
```

thanks for any help.

---

### Post by phidia on 2008-07-18
Just curious but did you do any research to see if that card is supported in linux?
I don't see your card listed at the [multimedia hardware section]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia") for ubuntu, nor at the somewhat larger database [here]("http://www.linuxquestions.org/hcl/index.php/cat/120") at linuxquestions.

---

### Post by Rain_Wolf on 2008-07-18
> **phidia said:**
> Just curious but did you do any research to see if that card is supported in linux?
I don't see your card listed at the [multimedia hardware section]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia") for ubuntu, nor at the somewhat larger database [here]("http://www.linuxquestions.org/hcl/index.php/cat/120") at linuxquestions.

yes i do. but i didn't have any result for install it.Is that mean i can't install it in ubuntu?!

---

### Post by phidia on 2008-07-18
I wouldn't say that you can't but you need more information on the card.
Does "lspci -v" provide more details? If the card is just a rebranded card of a type that's supported then you should be able to get it working.

---

### Post by Rain_Wolf on 2008-07-21
> **phidia said:**
> I wouldn't say that you can't but you need more information on the card.
Does "lspci -v" provide more details? If the card is just a rebranded card of a type that's supported then you should be able to get it working.
I think it can't be useful. anyway the export of lspci -v is:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d000 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at c000 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Unknown device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fa205000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: fa000000-fa0fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at c800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology Unknown device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at cc00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology Unknown device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fa204000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fa100000-fa1fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device 5001
	Flags: medium devsel, IRQ 5
	Memory at fa206000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at d800 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e800 [size=16]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8241
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 7000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology Unknown device b000
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fa000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Unknown device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 8000 [size=8]
	I/O ports at 8400 [size=4]
	I/O ports at 8800 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 9000 [size=16]
	Capabilities: <access denied>

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
	Subsystem: Giga-byte Technology Unknown device e000
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at f9000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>

05:02.0 Multimedia video controller: Winbond Electronics Corp W99200F MPEG-1 Video Encoder (rev 03)
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at b000 [size=16]
	Memory at fa100000 (32-bit, non-prefetchable) [size=4K]
	Memory at fa101000 (32-bit, non-prefetchable) [size=4K]

```

---


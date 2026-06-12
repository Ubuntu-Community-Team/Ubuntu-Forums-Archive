---
title: "[SOLVED] no sound after compiling kernel 2.6.26.3-custom"
date: 2008-09-05
forum: General Help
---

### Post by _sluimers_ on 2008-09-05
I followed the instructions on [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) to get kernel 2.6.26.3 and now my sound
isn't working. 

alsamixer gives me:
```

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

lspci -v gives me:
```

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fb000000-fcffffff
	Prefetchable memory behind bridge: f4000000-f7ffffff
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at fc00 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f400 [size=8]
	I/O ports at f000 [size=4]
	I/O ports at ec00 [size=16]
	I/O ports at e800 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e400 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d400 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: medium devsel, IRQ 22
	I/O ports at d000 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 23
	I/O ports at c800 [size=256]
	Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA controller])
	Subsystem: VIA Technologies, Inc. UniChrome Pro IGP
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fc000000 [disabled] [size=64K]
	Capabilities: <access denied>

rogier@dhcppc3:/etc/Wireless/RT2870STA$ sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [80] AGP version 3.5
	Capabilities: [50] Power Management version 2

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fb000000-fcffffff
	Prefetchable memory behind bridge: f4000000-f7ffffff
	Capabilities: [70] Power Management version 2

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at fc00 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f400 [size=8]
	I/O ports at f000 [size=4]
	I/O ports at ec00 [size=16]
	I/O ports at e800 [size=256]
	Capabilities: [c0] Power Management version 2

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e400 [size=16]
	Capabilities: [c0] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at e000 [size=32]
	Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=32]
	Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d400 [size=32]
	Capabilities: [80] Power Management version 2

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: medium devsel, IRQ 22
	I/O ports at d000 [size=256]
	Capabilities: [c0] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 23
	I/O ports at c800 [size=256]
	Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA controller])
	Subsystem: VIA Technologies, Inc. UniChrome Pro IGP
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fc000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] AGP version 3.0

```

audio part of lspci -v:
```

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: VIA Technologies, Inc. Unknown device aa08
	Flags: medium devsel, IRQ 22
	I/O ports at d000 [size=256]
	Capabilities: [c0] Power Management version 2

```

asoundconf list gives me nothing.

---

### Post by Washer on 2008-09-06
Make sure your sound card as well as alsa are being built in in the kernel config.

---

### Post by cooke77 on 2008-09-06
That AC'97 'detail'(the moment I read it)....says it all.
Realtek. (On-board, too, I bet.)
Change it....to Creative, and, you won't need to 'compile' anything.

---

### Post by _sluimers_ on 2008-09-08
> **Washer said:**
> Make sure your sound card as well as alsa are being built in in the kernel config.

how?

[QUOTE=cooke77]
That AC'97 'detail'(the moment I read it)....says it all.
Realtek. (On-board, too, I bet.)
Change it....to Creative, and, you won't need to 'compile' anything.
[/QUOTE]

how?

---


---
title: "Surround Sound not working - ASUS M2NPV-"
date: 2008-05-17
forum: Hardware
---

### Post by resilius on 2008-05-17
I've recently tried Linux, and love it. I'm hoping to make the full switch from Windows but due to one niggly thing I can't just yet. I currently have a 4 speaker set up (subwoofer, left, right, centre). No sound will come out my centre speaker. I'm unable to find any sound settings within Ubuntu to play with, and I can't find Linux drivers for my Asus M2NPV-VM board with on board sound.

Any ideas?

Thanks,
resilius

---

### Post by teaker1s on 2008-05-17
double click sound icon
file>change device
this will let you select available alsa or oss mixer
edit>preferences
will allow you to set switches for preferences

---

### Post by resilius on 2008-05-18
Thanks - I've activated the centre speaker with Alsa, but there's still no sound coming from it. It still works fine in Windows.

---

### Post by resilius on 2008-05-19
Just a cheeky bump - any help would be appreciated, thanks.

---

### Post by teaker1s on 2008-05-19
okay I think you will find the solution is hidden in one of the alsa config files. but before I can suggest anything, we need to know your onboard sound manufacturer.
If you open terminal
Application>Accessories>Terminal
paste this code into it and post output

```
lspci -v
```

---

### Post by resilius on 2008-05-21
I've typed that code in, and the output is as follows...

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:81c0
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81c0
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81cb
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 816a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

01:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>



Thanks for your help

---


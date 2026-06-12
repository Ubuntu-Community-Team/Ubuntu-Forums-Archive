---
title: "Openchrome and VIA Drivers do not work"
date: 2009-03-18
forum: Hardware
---

### Post by verxs on 2009-03-18
After almost a month of reading and trying I still could not solve this problem.

Ubuntu 8.10 alternate was installed.  I have downloaded the driver from viaarena and followed the steps and got it installed.  I managed to boot into ubuntu but my screen shows just a brown screen then it slowly disappears.

So I tried installing the openchrome.  Same thing happens.  But the funny thing is the screen on this laptop shows this brown self disintegrating display but when I plug it into an LCD TV, the display on the tv is great!  In fact it went all the way to 1024x800!

So the most logical thing to do I thought was to drop the resolution and I went all the way to 640x480 with a refresh rate of 60hz.  Still the same problem display is ok on tv but not on my lcd.


I can't remember how I did it but I managed to figure out that my graphics card was Unichrome VT3353.  Openchrome supports only up to VT3108.  SO no way Openchrome is going to work for me.  VIA drivers?  I have tried but nothing works.  Please help.



Here's my lspci -v

user@user-laptop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. Unknown device 0353 (rev 12)
	Subsystem: VIA Technologies, Inc. Unknown device 0353
	Flags: bus master, medium devsel, latency 8

00:00.1 Host bridge: VIA Technologies, Inc. Unknown device 1353
	Subsystem: VIA Technologies, Inc. Unknown device 1353
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. Unknown device 2353
	Subsystem: VIA Technologies, Inc. Unknown device 2353
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. Unknown device 3353
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. Unknown device 4353
	Subsystem: VIA Technologies, Inc. Unknown device 4353
	Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. Unknown device 5353 (prog-if 20 [IO(X)-APIC])
	Subsystem: VIA Technologies, Inc. Unknown device 5353
	Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6353
	Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. Unknown device 7353
	Subsystem: VIA Technologies, Inc. Unknown device 7353
	Flags: bus master, medium devsel, latency 0

00:01.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 1122 (rev 11) (prog-if 00 [VGA controller])
	Subsystem: VIA Technologies, Inc. Unknown device 3349
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at c0000000 (32-bit, prefetchable) [size=128M]
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, non-prefetchable) [size=256M]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. Unknown device c353 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. Unknown device e353 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
	Capabilities: <access denied>

00:03.1 PCI bridge: VIA Technologies, Inc. Unknown device f353 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0c.0 SD Host controller: VIA Technologies, Inc. Unknown device 95d0 (rev 10) (prog-if 01)
	Subsystem: VIA Technologies, Inc. Unknown device 95d0
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at feaefc00 (32-bit, non-prefetchable) [size=256]
	Memory at feaef800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 FLASH memory: VIA Technologies, Inc. Unknown device 9530
	Subsystem: VIA Technologies, Inc. Unknown device 9530
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at feaef000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at dc00 [size=8]
	Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. CX700M2 IDE (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. CX700M2 IDE
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at d880 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at d480 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at feaeec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 8353
	Subsystem: VIA Technologies, Inc. Unknown device 8353
	Flags: medium devsel
	Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. Unknown device a353
	Subsystem: VIA Technologies, Inc. Unknown device 7323
	Flags: bus master, medium devsel, latency 128

00:13.0 PCI bridge: VIA Technologies, Inc. Unknown device b353 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:14.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 20)
	Subsystem: VIA Technologies, Inc. VIA High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at feae8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at cfff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>

---

### Post by davidryderuk on 2009-03-18
Hi,
If you want the latest via drivers for Ubuntu you are probably more likely to find them at the VIA Linux portal than viaarena. Note that the drivers for hardy seem to work better and are a more stable release than the drivers for intrepid. Therefore it may be worth downgrading to hardy until they release a stable video driver for intrepid.

```
http://linux.via.com.tw/support/downloadFiles.action
```

I'm not sure about openchrome, but you might want to try and compile the latest driver from source like described in the instructions below.

```
https://help.ubuntu.com/community/OpenChrome
```

---

### Post by verxs on 2009-03-19
Hi David,

Thank you for replying.  I will try hardy with the driver from via linux website.  I will report back soon.

---


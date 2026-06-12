---
title: "Dual monitor extended desktop with different resolution"
date: 2013-01-28
forum: Hardware
---

### Post by aromo on 2013-01-28
Hi all, I've searched my issue but haven't been able to find this problem reported before.  Perhaps someone here can point me in the right direction.

My setup:
Thinkpad T43 (LDVS 1024x768) with Lubuntu 12.10 + docking station
External LG monitor (DVI-1 1280x1024)

My problem:
I want to keep the laptop screen (LDVS) as the primary display (i.e. the one that holds the task bar), and **extend** the desktop to the external monitor (DVI-1) **using its maximum resolution (1280x1024)**.

The external monitor is configured to the right of LDVS using arandr.

Mirroring display and extended desktop work fine at 1024x768 on both monitors.

If I bump up the resolution on the external monitor, I lose the task bar on the laptop screen and only see the second half of the task bar on the external monitor.

I know I can set the task bar to a fixed length of 1024, but it causes I cannot see it on either display when the external monitor is at 1280x1024.

Hope I haven't been too confusing.  Any thoughts?

---

### Post by prabhanjan on 2013-01-28
get ur pciids

---

### Post by aromo on 2013-01-28
Here you go:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: IBM ThinkPad Z60t
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: c0000000-c7ffffff
	Capabilities: [88] Subsystem: IBM Device 0578
	Capabilities: [80] Power Management version 2
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: b0200000-b02fffff
	Prefetchable memory behind bridge: 0000000060000000-00000000601fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b2000000-b3ffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000c80fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: IBM Device 0565
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: IBM Device 0566
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0e, sec-latency=64
	I/O behind bridge: 00005000-00008fff
	Memory behind bridge: b4000000-bfffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d7ffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: IBM Device 0567
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 1c00 [size=256]
	I/O ports at 1880 [size=64]
	Memory at b0000800 (32-bit, non-prefetchable) [size=512]
	Memory at b0000400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: snd_intel8x0
	Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: IBM Device 0576
	Flags: medium devsel, IRQ 23
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: IBM Device 0568
	Flags: bus master, medium devsel, latency 0
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: IBM Device 056a
	Flags: bus master, 66MHz, medium devsel, latency 0
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18c0 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: IBM Device 056b
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV370 [Mobility Radeon X300] (prog-if 00 [VGA controller])
	Subsystem: IBM Device 056e
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at c0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
	Subsystem: IBM ThinkPad Z60t
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0200000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Kernel driver in use: tg3
	Kernel modules: tg3

0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
	Subsystem: IBM ThinkPad Z60t
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at b4000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0b, secondary=0c, subordinate=0d, sec-latency=176
	Memory window 0: d0000000-d3ffffff (prefetchable)
	Memory window 1: b8000000-bbffffff
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

0b:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2711
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at b4001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200

```

Thank you.

---

### Post by kwoodham on 2013-02-15
I have not found a solution either but have the following work-around.  I don't like it, but it's the best I can do.

First set the width of your panel to 1024 pixels, and move it to the top of the screen on your laptop.  Also under the Advanced tab for panel preferences, deselect "Reserve space".

Connect your external monitor and enable it using arandr or however you like and set it to extent you laptop display to the right.

Now you should have your panel on your laptop, and the full display available on the dual monitor.  You might have to restart openbox. But you should be able to get there.

I went from linux mint to lubuntu, and under mint I was able to keep my panel at the bottom of my netbook while still extending the display to a monitor with the top edges lined up.  

Note also that you might need to use xrandr to set LDVS as primary if the toolbar is on the wrong display.

Sorry I don't have better news for you.

- Kurt

---

### Post by aromo on 2013-03-05
Thanks!  Sorry I was away for a while.  I will give this a try and post the result.

---


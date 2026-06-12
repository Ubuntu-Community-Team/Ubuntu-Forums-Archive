---
title: "Please help"
date: 2008-08-29
forum: General Help
---

### Post by enzodad on 2008-08-29
VOLUME controll not working i did and do everything people tell me i am useing 8.04 ubuntu i have volume coontroll but it does nothing

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lspci -v

---

### Post by enzodad on 2008-08-29
chris@Enzo:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Dell Unknown device 0179
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfd00000-dfefffff
	Prefetchable memory behind bridge: d8000000-dbffffff
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: dfc00000-dfcfffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: dfb00000-dfbfffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Optiplex GX280
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ec00 [size=256]
	I/O ports at e8c0 [size=64]
	Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
	Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0179
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Optiplex GX280
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Dell Optiplex GX280
	Flags: medium devsel, IRQ 10
	I/O ports at e8a0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device 0f02
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	I/O ports at dc00 [size=256]
	Memory at dfde0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at dfe00000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
	Subsystem: ATI Technologies Inc Unknown device 0f03
	Flags: bus master, fast devsel, latency 0
	Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Dell Optiplex GX280
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfcf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

---


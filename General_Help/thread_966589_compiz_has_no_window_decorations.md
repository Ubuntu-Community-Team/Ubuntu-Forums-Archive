---
title: "compiz has no window decorations"
date: 2008-11-01
forum: General Help
---

### Post by cic.11 on 2008-11-01
so i recently decided to make my xubuntu look better(not that there is anything wrong with the default). so yesterday i installed compiz along with emerald. so this is the problem. when i run compiz there are no window decorations.
when i run compiz --replace on terminal this is what i get.

> bobo@bobo:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0


sorry if i didnt include any more information. i dont know what else to say.

---

### Post by yogo on 2008-11-01
Wait til others weigh in but I do not think Compiz works on Xbuntu....?


Checked it does work but there seems to be some issues.

---

### Post by Cl0ud9 on 2008-11-01
while you are running compiz try:
```

emerald --replace

```

---

### Post by cic.11 on 2008-11-01
> **Cl0ud9 said:**
> while you are running compiz try:
```

emerald --replace

```

I tried this and nothing changes when i do this in the terminal i get

> bobo@bobo:~$ emerald --replace
/home/bobo/.gtkrc-2.0:3: error: unexpected character `\342', expected string constant
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:63: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:64: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Alphacube GTK 0.5/gtk-2.0/gtkrc:65: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

(emerald:5730): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


---

### Post by Cl0ud9 on 2008-11-01
Make sure Window Decorations are enabled in compiz. It's under the effects category.

---

### Post by cic.11 on 2008-11-02
window decorations are enabled. should i just re install compiz?

---

### Post by cic.11 on 2008-11-02
when i run lspci -v i get

> bobo@bobo:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 98000000 (32-bit, prefetchable) [size=128M]
	Memory at 90100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, fast devsel, latency 0
	Memory at 88000000 (32-bit, prefetchable) [size=128M]
	Memory at 80100000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at aca0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at ace0 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: a0100000-a01fffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at b060 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: medium devsel, IRQ 10
	I/O ports at 7000 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at a000 [size=256]
	I/O ports at a400 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: medium devsel, IRQ 10
	I/O ports at a800 [size=256]
	I/O ports at ac00 [size=128]

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at 9000 [size=256]
	Memory at a0100000 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>

01:09.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
	Subsystem: Acer Incorporated [ALI] Unknown device 1024
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at a0101000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 24000000-27fff000 (prefetchable)
	Memory window 1: 28000000-2bfff000
	I/O window 0: 00009400-000094ff
	I/O window 1: 00009800-000098ff
	16-bit legacy interface ports at 0001

02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
	Subsystem: Unknown device 1630:0003
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at 28000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>


---


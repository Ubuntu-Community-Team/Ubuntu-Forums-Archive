---
title: "Sound Card (Intel  82801EB/ER (ICH5/ICH5R)) doesn't work."
date: 2008-11-01
forum: Hardware
---

### Post by bSLiON on 2008-11-01
My sound works properly when my Ubuntu is installed, while problem occurs when I did some updates on Ubuntu 8.04 the other day. There's a red cross on the volume applet and when clicking, it says:

> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


out of aplay -l:
> 
aplay: device_list:215: no soundcards found...

out of lspci -v:
> 
lang@Langyuze-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: ASRock Incorporation Device 2570
	Flags: bus master, fast devsel, latency 0
	Memory at fe800000 (32-bit, prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
	Subsystem: ASRock Incorporation Device 2572
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at fe780000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe77bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe500000-fe5fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASRock Incorporation Device 24d0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fc00 [size=16]
	Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: ASRock Incorporation Device 24d0
	Flags: medium devsel, IRQ 5
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASRock Incorporation Device 9739
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at d800 [size=256]
	I/O ports at d400 [size=64]
	Memory at fe77b800 (32-bit, non-prefetchable) [size=512]
	Memory at fe77b400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: ASRock Incorporation Device 8139
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at b800 [size=256]
	Memory at fe5ffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too



When updated to Ubuntu 8.10, the sound card works again ,but because 8.10 runs too slowly on my computer, I started an old kernel and the problem comes back. 

I'm new to Ubuntu and this forum, I hope I clearly stated my problem and thanks for your helping..

---


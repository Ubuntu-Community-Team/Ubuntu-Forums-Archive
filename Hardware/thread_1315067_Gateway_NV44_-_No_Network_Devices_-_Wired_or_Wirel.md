---
title: "Gateway NV44 - No Network Devices - Wired or Wireless"
date: 2009-11-04
forum: Hardware
---

### Post by sonni_kuba on 2009-11-04
I've been using Linux since 2005 and have pretty much tried out every Ubuntu animal since Warty Warhog.

Depending on the iteration, it would be expected that some hardware is not detected (most usually wireless card). Anyways, I'll cut to the chase.

I was recently using 9.04 with automatic hardware detection without any tweaking. Recently, I've just loaded 9.10 on my laptop and it doesn't recognize either the Wired or Wireless card. I am actually typing this from another computer.

Below is the printout from lspci-v. Thanks in advance for your help.

laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, fast devsel, latency 0
	Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f0904800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	Memory behind bridge: b6000000-b60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: b6100000-b61fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0904c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0904000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: medium devsel, IRQ 10
	Memory at b6200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Foxconn International, Inc. Device e006
	Flags: fast devsel, IRQ 16
	Memory at b6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath9k

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 021c
	Flags: fast devsel, IRQ 17
	Memory at b6100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: tg3

---

### Post by sonni_kuba on 2009-11-05
Any suggestions ...

In the past I have resorted to updating the repositories, installing ndiswrapper, and then installing the card. But, since I can't connect to the internet, how can I install ndiswrapper???

I even tried updating to 9.10 from 9.04 via synaptic, since my network cards worked flawlessly under 9.04, and once again, 9.10 cannot recognize any of them. How can ubuntu keep doing this ???

---

### Post by sergio jose dias on 2009-11-05
Go the link: 
[http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html](http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html)
And try the solution.

---

### Post by sonni_kuba on 2009-11-07
> Go the link:
[http://pelenegra.blogspot.com/2009/1...do-bug-da.html](http://pelenegra.blogspot.com/2009/1...do-bug-da.html)
And try the solution. 

Yup, tried that solution. No solution.

I also tried booting with acpi=off, but that didn't solve any problems, although, then the network connection were visible, but not usable.

I don't know why this is such a problem, why it was working under 9.04, and doesn't in 9.10????

Is the kernel incompatible or what ????

---

### Post by sonni_kuba on 2009-11-07
Was thinking about this some more ...

Since both wired and wireless network adapters were detected right away in 9.04, that means the drivers are written in the kernel. So, it doesn't seem likely that they had been removed. 

Is there a conflict that prevents their use? How would I check this ???

---

### Post by sonni_kuba on 2009-11-08
Solution, went back to 9.04

This is really bad though, and people wonder why linux on the desktop can't gain any traction ...

---


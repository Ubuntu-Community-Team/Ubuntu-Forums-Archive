---
title: "i need help i messed something up maybe you can help?"
date: 2011-08-27
forum: Hardware
---

### Post by TheDevilMr666 on 2011-08-27
so my computer was acting up so i decided to delete so stuff and i guess i deleted the microphone driver maybe i did maybe i didnt idk but now my mike dont work im using ubuntu 11.04 i will post my specs. but when i do the system test it picks my mic up but then if i try and use cheese or anything like that it dont work . any ideas?


dustin@dustin-Aspire-7745:~$ sudo lspci -v
[sudo] password for dustin: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0805800 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0806000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000a01fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0367
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0500000-f05fffff
	Prefetchable memory behind bridge: 00000000a0200000-00000000a03fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 0367
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0806400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 0367

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=10 <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0805000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: medium devsel, IRQ 10
	Memory at f0806800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: fast devsel, IRQ 18
	Memory at f0604000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0367
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [180] Device Serial Number ff-65-5d-7a-c8-0a-a9-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

09:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
	Subsystem: Foxconn International, Inc. Device e021
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-cb-ff-ff-7b-f0-7b
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, brcm80211

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

---

### Post by jerrrys on 2011-08-28
two things:

open a terminal and enter these commands one at a time

sudo dpkg --configure -a

sudo apt-get clean

sudo apt-get update

this will attempt to fix broken packages

second

when posting a long list if you put a < at the beginning and a > at the end, it will be in it own window

---


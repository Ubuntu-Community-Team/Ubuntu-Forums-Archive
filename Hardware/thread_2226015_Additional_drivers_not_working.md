---
title: "Additional drivers not working?"
date: 2014-05-24
forum: Hardware
---

### Post by Diskdoc on 2014-05-24
Why doesn't the Additional drivers tool offer to install fglrx? It works if I do it with apt-get..

Xorg identifies my graphics as:

[    43.840] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 5000 Series" (Chip
ID = 0x68c1)

---

### Post by grahammechanical on 2014-05-24
You ask why. Additional Drivers keeps things simple by not showing every proprietary driver that is available in the Ubuntu archives. Drivers that I used on my machine since before Ubuntu 12.04 are not shown in Additional Drivers of Ubuntu 14.04.

I have a Nvidia card but I only get offered Nvidia 304; 304-updates and 331; 331-updates. I know that there are other older drivers in the archive but I am glad that I am not presented with a long list of Nvidia drivers going back to 173 or earlier.

---

### Post by Yellow Pasque on 2014-05-25
What kind of laptop do you have? Perhaps it's got hybrid graphics (intel+ati).
```
lspci -k
```

---

### Post by Diskdoc on 2014-05-28
Checking with apt-cache, the version of the available (and working) fglrx package is 2:13.350.1-0ubuntu2. As I understand it, it is the current version in Trusty repositories, not an old one.

However, choosing the "Additional drivers" tab results in it searching for available drivers and then coming up empty.

I have an Acer Aspire TimelineX 3820T. It does indeed have hybrid graphics but I have set the graphics setting in the BIOS from "switchable" to "discreet" so as only to use the Radeon chip.

However, since you asked for it, here is the results of lspci -k:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Acer Incorporated [ALI] Device 0364
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
	Kernel driver in use: pcieport
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: intel ips
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
	Subsystem: Acer Incorporated [ALI] Mobility Radeon HD 5650
	Kernel driver in use: radeon
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: snd_hda_intel
03:00.0 Ethernet controller: Qualcomm Atheros AR8151 v1.0 Gigabit Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0364
	Kernel driver in use: atl1c
05:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
	Subsystem: Foxconn International, Inc. T77H103.00 Wireless Half-size Mini PCIe Card
	Kernel driver in use: bcma-pci-bridge
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086

---


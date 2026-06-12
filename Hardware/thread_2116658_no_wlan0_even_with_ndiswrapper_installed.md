---
title: "no wlan0 even with ndiswrapper installed"
date: 2013-02-16
forum: Hardware
---

### Post by mariceles on 2013-02-16
Hi all, I have a problem with my new laptop, and I can use some help.


getting straight to the point, here's what I get from lspci -nnk (the troubling wlan is at the bottom of the list)

```
$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 650M] [10de:0fd1] (rev a1)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0e1b] (rev a1)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: COMPAL Electronics Inc Device [14c0:0065]
	Kernel driver in use: r8169
	Kernel modules: r8169
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]

```


I have ndiswrapper 1.58rc1 installed (I downloaded it from sourceforge and built from source as the version in the repositories [won't install]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645")), and I have the Windows driver installed. Here's what I get out of ndiswrapper -l
```
$ ndiswrapper -l
netrtwlane : driver installed
	device (10EC:8723) present

```
ndisgtk shows the same thing.


but upon typing $ sudo lshw -C network
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: b8:88:e3:ce:6d:59
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=121.124.107.169 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:3000(size=256) memory:d2004000-d2004fff memory:d2000000-d2003fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d2100000-d2103fff
```


as you can see it still says UNCLAIMED.

How do I solve this problem? Thanks a lot!

---


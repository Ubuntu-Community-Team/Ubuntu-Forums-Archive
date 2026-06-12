---
title: "my laptop not good with ubuntu ?? can u help my ?"
date: 2009-10-20
forum: Hardware
---

### Post by kingropen on 2009-10-20
[SIZE=4]hi evry one 
i have a broplom (1) with cpu , in ubuntu well give me 1 cpu and in windows 2 cpu !!
(2) some time wen i play movie mp4 an maked in full screen the laptop well hang or stack !!
(3) wen i play gtk-RecordMeDesktop , the laptop well come aslow & th record not good !!
this is my info of the laptop 
lshw: 
```
[SIZE=3][SIZE=4][SIZE=1]description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 2400
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-ide:1
             description: IDE interface
             product: SATA Controller / IDE mode
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=64
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:15:af:af:36:e4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.64 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:1d:92:56:d8:82
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
        *-pcmcia
             description: CardBus bridge
             product: OZ711SP1 Memory CardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=67 module=yenta_socket
        *-system UNCLAIMED
             description: SD Host controller
             product: Integrated MMC/SD Controller
             vendor: O2 Micro, Inc.
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=64
        *-storage UNCLAIMED
             description: Mass storage controller
             product: Integrated MS/xD Controller
             vendor: O2 Micro, Inc.
             physical id: 9.3
             bus info: pci@0000:00:09.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage cap_list
             configuration: latency=0
        *-firewire UNCLAIMED
             description: FireWire (IEEE 1394)
             product: Firewire (IEEE 1394)
             vendor: O2 Micro, Inc.
             physical id: 9.4
             bus info: pci@0000:00:09.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64
        *-multimedia
             description: Audio device
             product: Azalia Audio Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52 module=snd_hda_intel
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:af:05:e0:62:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/SIZE]
```
[/SIZE][/SIZE]lscpi
[SIZE=1]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
00:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
00:09.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
00:09.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)[/SIZE]
lspci -n
[SIZE=1]00:00.0 0600: 1039:0671
00:01.0 0604: 1039:0004
00:02.0 0601: 1039:0968 (rev 01)
00:02.5 0101: 1039:5513 (rev 01)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.3 0c03: 1039:7002
00:05.0 0101: 1039:1183 (rev 03)
00:06.0 0604: 1039:000a
00:07.0 0604: 1039:000a
00:09.0 0607: 1217:7136 (rev 01)
00:09.2 0805: 1217:7120 (rev 02)
00:09.3 0180: 1217:7130 (rev 01)
00:09.4 0c00: 1217:00f7 (rev 02)
00:0f.0 0403: 1039:7502
01:00.0 0300: 1002:94c9
02:00.0 0200: 168c:001c (rev 01)
03:00.0 0200: 10ec:8136 (rev 01)
[/SIZE]

[/SIZE]

---


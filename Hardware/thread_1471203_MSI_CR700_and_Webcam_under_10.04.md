---
title: "MSI CR700 and Webcam under 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by xtremesupremacy3 on 2010-05-03
So yes, I have been testing 10.04 from beta 2 and since the beginning, up until now, I have no webcam.
I have done updates whenever they are available and hit the webcam button lots of times without the hardware being picked up.
All I get are the responses that hardware is not found and ls /dev/video* delivers a no such file or directory result.

The thing is, this worked out of the box in 9.10 and this was simply the ideal laptop for 9.10 but there are lots of problems in 10.04 which don't work out of the box. I have finally got everything working again except this webcam. Anyone have any ideas?

EDIT: Here are some vitals:

lsusb:
Bus 002 Device 002: ID 04fc:0538 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw:

 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2767MiB
     *-cpu
          product: Celeron(R) Dual-Core CPU       T3000  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: MCP79 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: b1
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP79 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:4f00(size=256)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP79 SMBus
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:15 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: MCP79 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: b1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor
             description: Co-processor
             product: MCP79 Co-processor
             vendor: nVidia Corporation
             physical id: 3.5
             bus info: pci@0000:00:03.5
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=nvidia latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fae80000-faefffff
        *-usb:0
             description: USB Controller
             product: MCP79 OHCI USB 1.1 Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:fae7f000-fae7ffff
        *-usb:1
             description: USB Controller
             product: MCP79 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:fae7ec00-fae7ecff
        *-multimedia
             description: Audio device
             product: MCP79 High Definition Audio
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:23 memory:fae78000-fae7bfff
        *-pci:0
             description: PCI bridge
             product: MCP79 PCI Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
        *-network
             description: Ethernet interface
             product: MCP79 Ethernet
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: b1
             serial: 00:24:21:69:ec:25
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:23 memory:fae7d000-fae7dfff ioport:c080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
        *-storage
             description: SATA controller
             product: MCP79 AHCI Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: b1
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:26 ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=16) memory:fae72000-fae73fff
        *-pci:1
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d000(size=4096) memory:faf00000-fbffffff ioport:e0000000(size=402653184)
           *-display
                description: VGA compatible controller
                product: C79 [GeForce 9200M G]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:20 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff(prefetchable) ioport:dc00(size=128) memory:fafe0000-faffffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fe000000-feafffff ioport:f8000000(size=33554432)
        *-pci:3
             description: PCI bridge
             product: MCP79 PCI Express Bridge
             vendor: nVidia Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: b1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 01
                serial: 00:25:d3:49:12:9f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.55+,03/13/2009,7.7.0.259 ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11g
                resources: irq:19 memory:febf0000-febfffff

---

### Post by xtremesupremacy3 on 2010-05-05
Well, after a new clean install with the release version of 10.04 this problema has been cleared.

---


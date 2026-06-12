---
title: "Nvidia Proprietary Driver Problems - Xubuntu 15.04"
date: 2015-09-13
forum: Hardware
---

### Post by ChaoticFlounder on 2015-09-13
For the past 2 weeks i have been having trouble using anything but the "nouveau" driver.  If i try to install anything else from the "Additional Drivers" GUI it will black screen on reboot to xubuntu.  I went into recovery mode to see what i could do and discovered that the standard nouveau seems to be the only one that will let me boot normally.

Please let me know how I can get started solving this problem.

Thanks,

C

---

### Post by oldos2er on 2015-09-13
What Nvidia device do you have?

---

### Post by ChaoticFlounder on 2015-09-13
it's a evga gtx 680 4gb version, reference card

is there a terminal command i can post to give you the details on my hardware?

Thanks,

C

---

### Post by mörgæs on 2015-09-14
Yes: Run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by ChaoticFlounder on 2015-09-15
```
computer    description: Computer
    width: 64 bits
    capabilities: smbios-2.7 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 3698MHz
          capacity: 3800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt cpufreq
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:f5000000-f61fffff ioport:e0000000(size=167772160)
           *-pci
                description: PCI bridge
                product: PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ba
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:29 memory:f6100000-f613ffff ioport:e000(size=4096) memory:f5000000-f60fffff ioport:e0000000(size=167772160)
              *-pci:0
                   description: PCI bridge
                   product: PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 8
                   bus info: pci@0000:02:08.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:30 ioport:e000(size=4096) memory:f5000000-f60fffff ioport:e0000000(size=167772160)
                 *-display
                      description: VGA compatible controller
                      product: GK104 [GeForce GTX 680]
                      vendor: NVIDIA Corporation
                      physical id: 0
                      bus info: pci@0000:03:00.0
                      version: a1
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                      configuration: driver=nouveau latency=0
                      resources: irq:49 memory:f5000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f6000000-f607ffff
                 *-multimedia
                      description: Audio device
                      product: GK104 HDMI Audio Controller
                      vendor: NVIDIA Corporation
                      physical id: 0.1
                      bus info: pci@0000:03:00.1
                      version: a1
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress bus_master cap_list
                      configuration: driver=snd_hda_intel latency=0
                      resources: irq:17 memory:f6080000-f6083fff
              *-pci:1
                   description: PCI bridge
                   product: PEX 8747 48-Lane, 5-Port PCI Express Gen 3 (8.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 10
                   bus info: pci@0000:02:10.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:31
        *-display
             description: Display controller
             product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:47 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:f7100000-f710ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 3.19.0-28-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 3.19
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 3.19.0-28-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Mouse
                   product: SteelSeries Sensei
                   vendor: La-VIEW Technology
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.fc
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=200mA speed=12Mbit/s
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:46 memory:f711a000-f711a00f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7118000-f71183ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-28-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@7:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: Bluetooth wireless interface
                      vendor: IMC Networks
                      physical id: 1
                      bus info: usb@7:1.1
                      version: 0.02
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Audio device
                      product: ASTRO Gaming USB MixAmp
                      vendor: ETHER ELECTRONICS CO.,LTD.
                      physical id: 4
                      bus info: usb@7:1.4
                      version: 1.00
                      serial: [REMOVED]
                      capabilities: usb-1.10 audio-control
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f7110000-f7113fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:cfb00000-cfcfffff ioport:cfd00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:f7000000-f70fffff
           *-storage
                description: SATA controller
                product: ASM1062 Serial ATA Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:44 ioport:d050(size=8) ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4) ioport:d000(size=32) memory:f7000000-f70001ff
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f6f00000-f6ffffff
           *-network
                description: Wireless interface
                product: AR9462 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.19.0-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:18 memory:f6f00000-f6f7ffff memory:f6f80000-f6f8ffff
        *-pci:4
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:b000(size=8192) memory:f6800000-f6efffff ioport:ea100000(size=2097152)
           *-pci
                description: PCI bridge
                product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: ba
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:32 memory:f6e00000-f6e1ffff ioport:b000(size=8192) memory:f6800000-f6dfffff ioport:ea100000(size=2097152)
              *-pci:0
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 1
                   bus info: pci@0000:09:01.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:33 memory:f6d00000-f6dfffff ioport:ea200000(size=1048576)
                 *-network
                      description: Ethernet interface
                      product: NetLink BCM57781 Gigabit Ethernet PCIe
                      vendor: Broadcom Corporation
                      physical id: 0
                      bus info: pci@0000:0a:00.0
                      logical name: eth0
                      version: 10
                      serial: [REMOVED]
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=twisted pair
                      resources: irq:16 memory:ea210000-ea21ffff memory:ea200000-ea20ffff memory:f6d00000-f6d007ff
              *-pci:1
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 4
                   bus info: pci@0000:09:04.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:34 ioport:c000(size=4096) memory:f6c00000-f6cfffff
                 *-storage
                      description: SATA controller
                      product: ASM1062 Serial ATA Controller
                      vendor: ASMedia Technology Inc.
                      physical id: 0
                      bus info: pci@0000:0b:00.0
                      version: 01
                      width: 32 bits
                      clock: 33MHz
                      capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list
                      configuration: driver=ahci latency=0
                      resources: irq:45 ioport:c050(size=8) ioport:c040(size=4) ioport:c030(size=8) ioport:c020(size=4) ioport:c000(size=32) memory:f6c00000-f6c001ff
              *-pci:2
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 5
                   bus info: pci@0000:09:05.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:35 memory:f6b00000-f6bfffff ioport:ea100000(size=1048576)
                 *-network
                      description: Ethernet interface
                      product: NetLink BCM57781 Gigabit Ethernet PCIe
                      vendor: Broadcom Corporation
                      physical id: 0
                      bus info: pci@0000:0c:00.0
                      logical name: eth1
                      version: 10
                      serial: [REMOVED]
                      size: 1Gbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                      resources: irq:16 memory:ea110000-ea11ffff memory:ea100000-ea10ffff memory:f6b00000-f6b007ff
              *-pci:3
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 6
                   bus info: pci@0000:09:06.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:36 ioport:b000(size=4096) memory:f6a00000-f6afffff
                 *-firewire
                      description: FireWire (IEEE 1394)
                      product: VT6315 Series Firewire Controller
                      vendor: VIA Technologies, Inc.
                      physical id: 0
                      bus info: pci@0000:0d:00.0
                      version: 01
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress ohci bus_master cap_list
                      configuration: driver=firewire_ohci latency=0
                      resources: irq:17 memory:f6a00000-f6a007ff ioport:b000(size=256)
              *-pci:4
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 7
                   bus info: pci@0000:09:07.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:37 memory:f6900000-f69fffff
                 *-usb
                      description: USB controller
                      product: EJ188/EJ198 USB 3.0 Host Controller
                      vendor: Etron Technology, Inc.
                      physical id: 0
                      bus info: pci@0000:0e:00.0
                      version: 00
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci bus_master cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:41 memory:f6900000-f6907fff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 3.19.0-28-generic xhci-hcd
                         physical id: 0
                         bus info: usb@4
                         logical name: usb4
                         version: 3.19
                         capabilities: usb-3.00
                         configuration: driver=hub slots=4 speed=5000Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 3.19.0-28-generic xhci-hcd
                         physical id: 1
                         bus info: usb@3
                         logical name: usb3
                         version: 3.19
                         capabilities: usb-2.00
                         configuration: driver=hub slots=4 speed=480Mbit/s
                       *-usb
                            description: Keyboard
                            product: Corsair Vengeance K90 Keyboard
                            vendor: Corsair
                            physical id: 3
                            bus info: usb@3:3
                            version: 1.13
                            capabilities: usb-2.00
                            configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-pci:5
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 8
                   bus info: pci@0000:09:08.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:38 memory:f6800000-f68fffff
                 *-usb
                      description: USB controller
                      product: EJ188/EJ198 USB 3.0 Host Controller
                      vendor: Etron Technology, Inc.
                      physical id: 0
                      bus info: pci@0000:0f:00.0
                      version: 00
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci bus_master cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:42 memory:f6800000-f6807fff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 3.19.0-28-generic xhci-hcd
                         physical id: 0
                         bus info: usb@6
                         logical name: usb6
                         version: 3.19
                         capabilities: usb-3.00
                         configuration: driver=hub slots=4 speed=5000Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 3.19.0-28-generic xhci-hcd
                         physical id: 1
                         bus info: usb@5
                         logical name: usb5
                         version: 3.19
                         capabilities: usb-2.00
                         configuration: driver=hub slots=4 speed=480Mbit/s
              *-pci:6
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 9
                   bus info: pci@0000:09:09.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:39
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7117000-f71173ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 3.19.0-28-generic ehci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 3.19
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@8:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Z77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7116000-f71167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7115000-f71150ff ioport:f040(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: BB6Q
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=c2bd8e83
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-01-27 21:47:04 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 232GiB
                capacity: 232GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-01-27 21:47:04 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG SSD 830
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 3B1Q
             serial: [REMOVED]
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00040e92
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                size: 59GiB
                capacity: 59GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /
                   capacity: 57GiB
                   capabilities: bootable
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sdb6
                   capacity: 2GiB
                   capabilities: nofs
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: [REMOVED]
                size: 59GiB
                capacity: 59GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-10-11 09:40:41 filesystem=ntfs state=clean



```

---

### Post by mörgæs on 2015-09-16
What is the problem using Nouveau?

---

### Post by ChaoticFlounder on 2015-09-16
I've just been under the impression that the proprietary drivers give better FPS in game (CS:GO & Kerbal Space Program).  Also, I am experiencing what I believe to be tearing when watching youtube videos and scrolling up and down on web pages.  I was hoping the proprietary drivers would help that.

C

---

### Post by mörgæs on 2015-09-17
They probably do, yes. 
I don't know this card so can't help you here, sorry.

---

### Post by kryten35 on 2015-09-18
Nvidia install may be corrupted and unable to install.Completely remove it and try again.

```
sudo apt-get purge nvidia-*
```

Then try the additional drivers install

Another option is to try an nvidia repository: purge nvidia again,then
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

```
sudo apt-get update
```

```
sudo apt-get install nvidia-current
```

---


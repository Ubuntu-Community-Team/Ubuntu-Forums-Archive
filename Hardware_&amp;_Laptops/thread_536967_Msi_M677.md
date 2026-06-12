---
title: "Msi M677"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by gmenelau on 2007-08-28
Hi 


I have the MSI M677 and i just move from Windows to Ubuntu and i dont know much very well actully i dont know anything.
 I need help with the wireless  card and also i need to know how i can install new drivers , coz i cant work the 1.3 build in camera etc . 

Can anyone help me ?


Thanks

---

### Post by nosrednaekim on 2007-08-28
I need the output of "sudo lshw"

---

### Post by gmenelau on 2007-08-30
Can you help me or not ?

---

### Post by nosrednaekim on 2007-08-31
I need the output of "sudo lshw"

type that into a command line and paste the output here.

---

### Post by gmenelau on 2007-09-01
capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-cpu:1
          description: CPU
          product: (To Be Filled By O.E.M.)
          physical id: 8
          bus info: cpu@1
          version: 15.8.2
          serial: To Be Filled By O.E.M.
          slot: CPU 2
          size: 800MHz
          capacity: 2GHz
          capabilities: cpufreq
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 9
             slot: L1-Cache
             size: 128KB
             capabilities: internal
        *-cache:1 DISABLED
             description: L2 cache
             physical id: a
             slot: L2-Cache
             size: 512KB
             capabilities: internal
        *-cache:2 DISABLED
             description: L3 cache
             physical id: b
             slot: L3-Cache
             capabilities: internal
     *-memory:0
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM Synchronous 266 MHz (3.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Ethernet interface
             product: RTL8111/8168B PCI Express Gigabit Ethernet controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 0
             bus info: pci@01:00.0
             logical name: eth0
             version: 01
             serial: 00:16:17:52:2e:15
             size: 10MB/s
             capacity: 1GB/s
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
             resources: ioport:a800-a8ff iomemory:f8cff000-f8cfffff irq:19
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G70 [GeForce Go 7600]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@04:00.0
             version: a1
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia latency=0
             resources: iomemory:fc000000-fcffffff iomemory:c0000000-cfffffff iomemory:fb000000-fbffffff ioport:cc00-cc7f irq:21
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: ioport:5000-503f ioport:6000-603f irq:5
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fdfc0000-fdffffff irq:11
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fdfbe000-fdfbefff irq:18
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=8 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fdfbfc00-fdfbfcff irq:18
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-16-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
        *-ide
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                description: DVD-RAM writer
                product: PHILIPS DVD-RAM SDVD8821
                vendor: Philips
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: EX04
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: mode=udma2
              *-disc
                   physical id: 0
                   logical name: /dev/hdc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:e800-e807 ioport:e480-e483 ioport:e400-e407 ioport:e080-e083 ioport:e000-e00f iomemory:fdfbd000-fdfbdfff irq:17
        *-disk
             description: SCSI Disk
             product: FUJITSU MHV2100B
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0000
             serial: NWAET6525ENR
             size: 93GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                size: 15GB
                capacity: 15GB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 15GB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 674MB
                   capabilities: nofs
           *-volume:1
                description: HPFS/NTFS partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                capacity: 63GB
                capabilities: primary bootable
           *-volume:2
                description: Linux filesystem partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                capacity: 13GB
                capabilities: primary
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-pcmcia
             description: CardBus bridge
             product: OZ711MP1/MS1 MemoryCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 4
             bus info: pci@05:04.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=195
             resources: iomemory:fd600000-fd600fff irq:16
        *-system
             description: Generic system peripheral
             product: Integrated MMC/SD Controller
             vendor: O2 Micro, Inc.
             physical id: 4.2
             bus info: pci@05:04.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=sdhci latency=64
             resources: iomemory:fdefe400-fdefe4ff irq:16
        *-bridge UNCLAIMED
             description: Bridge
             product: Integrated MS/xD Controller
             vendor: O2 Micro, Inc.
             physical id: 4.3
             bus info: pci@05:04.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             configuration: latency=64
             resources: iomemory:fdefd000-fdefdfff irq:10
        *-firewire
             description: FireWire (IEEE 1394)
             product: Firewire (IEEE 1394)
             vendor: O2 Micro, Inc.
             physical id: 4.4
             bus info: pci@05:04.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64
             resources: iomemory:fdeff000-fdefffff iomemory:fdefe800-fdefefff irq:16
        *-network
             description: Wireless interface
             product: RT2500 802.11g Cardbus/mini-PCI
             vendor: RaLink
             physical id: 9
             bus info: pci@05:09.0
             logical name: ra0
             version: 01
             serial: 00:13:d3:80:81:94
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 ip=192.168.1.105 latency=64 link=yes multicast=yes wireless=RT2500 Wireless
             resources: iomemory:fdefa000-fdefbfff irq:20
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:fdfb8000-fdfbbfff irq:22
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by gmenelau on 2007-09-01
And something also , when in the setting of my wireless is security mode  the wireless cant connect  only when is open , can you tell me why,  ? i put the keys ,everything but there is no signal nothing.

---


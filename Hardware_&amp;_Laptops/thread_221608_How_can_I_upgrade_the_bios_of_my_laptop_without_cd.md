---
title: "How can I upgrade the bios of my laptop without cd-rom or floppy directly in Dapper?"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by stani on 2006-07-23
Hi,
My laptop doesn't recognize usb on boot. I need to have this feature enabled. I was able to install Dapper by inserting my harddrive in another laptop. Is there anyway of upgrading the bios directly in Dapper? Or is it impossible? Unfortunately my laptop doesn't have a floppy drive or cdrom as well.

My laptop is a IBM thinkpad X30. Full specifications according to lshw are included:
```
$ sudo lshw
ibmx30
    description: Notebook
    product: 26724AU
    vendor: IBM
    version: Not Available
    serial: 99MDF65
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=D83A2280-4506-11CB-9A3A-BBFFAAE99971
  *-core
       description: Motherboard
       product: 26724AU
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1NLC2C918M
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1KET41WW (1.02 ) (09/13/2002)
          size: 144KB
          capacity: 960KB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.11.4
          slot: None
          size: 798MHz
          capacity: 1200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 768MB
          capacity: 1GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 256MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:e0000000-e7ffffff iomemory:d0000000-d007ffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:e8000000-efffffff iomemory:d0080000-d00fffff
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   vendor: Belkin
                   physical id: 2
                   bus info: usb@2:2
                   version: 2.70
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB (Hub #3)
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@01:00.0
                version: a8
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:50000000-50000fff iomemory:b00502010-b0050200f irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@01:00.1
                version: a8
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:50100000-50100fff iomemory:b00906010-b0090600f irq:11
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@01:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:d0201000-d02017ff irq:11
           *-network:0
                description: Wireless interface
                product: Prism 2.5 Wavelan chipset
                vendor: Intersil Corporation
                physical id: 2
                bus info: pci@01:02.0
                logical name: eth2
                version: 01
                serial: 00:05:3c:06:c2:96
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.4.9 ip=10.0.0.4 link=no multicast=yes wireless=IEEE 802.11b
                resources: iomemory:f8000000-f8000fff irq:11
           *-network:1
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth1
                version: 42
                serial: 00:09:6b:a0:35:5d
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.123.129 link=yes multicast=yes port=MII speed=100MB/s
                resources: iomemory:d0200000-d0200fff ioport:7000-703f irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1860-186f iomemory:40000000-400003ff irq:11
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HTS548040M9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MG2OA53A
                   serial: MRL222L2JSMSTB
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 36GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff irq:11
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:2400-24ff ioport:2000-207f irq:11

```
Thanks for any help,
Stani

---

### Post by mips on 2006-07-24
Have a look here,   [http://www.thinkwiki.org/wiki/BIOS_Upgrade](http://www.thinkwiki.org/wiki/BIOS_Upgrade)

Look at 7, 8 & 9, especially 9.

And bookmard that site, it is one of the best thinkpad resources on the net.

---

### Post by mips on 2006-07-24
Apologies, double post.

---


---
title: "External Hard Drive"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by RizingDamp on 2008-02-03
Hi Guys,

Well I just installed Feisty 7.04 having made the switch from windows.  All installed fine no problems.  Im currently using it on a dual boot, dual drive system.  However I have encountered a problem, mt external hard drive doesent show up as an icon on the desktop when switched on.  If I plug a flash drive in that shows up no problem.  I have run a sudo lshw command in the termnal and this is the output if it helps.  I have highlited the relevent section which I presume is my external Hard drive as the capacity seems to fit for a 250gb drive.  Any help at this time would be much appreciated. :)

 slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: DIMM_B1
             width: 64 bits
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM_B2
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: DIMM_A1
             width: 64 bits
        *-bank:3
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_A2
             size: 1GB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP55 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@00:01.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: ioport:fc00-fc3f ioport:1c00-1c3f ioport:1c40-1c7f irq:10
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@00:01.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02f000-fe02ffff irq:16
        *-usbhost
             product: OHCI Host Controller
             vendor: Linux 2.6.20-16-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=10 speed=12.0MB/s
           *-usb:0
                description: Keyboard
                product: USB Keyboard
                vendor: CHESEN
                physical id: 3
                bus info: usb@1:3
                version: 1.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
           *-usb:1
                description: Mouse
                product: USB-PS/2 Optical Mouse
                vendor: Logitech
                physical id: 4
                bus info: usb@1:4
                version: 30.00
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
     *-usb:1
          description: USB Controller
          product: MCP55 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02e000-fe02e0ff irq:17
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-16-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=10 speed=480.0MB/s
           *-usb:0
                description: USB hub
                product: USB2.0 Hub
                physical id: 1
                bus info: usb@2:1
                version: 7.02
                capabilities: usb-2.00
                configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
          [B] *-usb:1
                description: Mass storage device
                product: Cypress AT2LP      RC7
                physical id: 2
                bus info: usb@2:2
                logical name: scsi4
                version: 2.40
                serial: DEF10B4886F0
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
              *-disk
                   description: SCSI Disk
                   product: 3A
                   vendor: ST325082
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sdb
                   version: 0000
                   size: 232GB
                   capabilities: partitioned partitioned:dos
                 *-volume
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: scsi@4:0.0.0,1
                      logical name: /dev/sdb1
                      capacity: 232GB
                      capabilities: primary bootable[/B]
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f000-f00f
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-disk
                description: ATA Disk
                product: WDC WD400JB-00ETA0
                vendor: Western Digital
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                version: 77.07W77
                serial: WD-WCAHL4749971
                size: 37GB
                capacity: 37GB
                capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                configuration: mode=udma2 smart=on
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: ide@0.0,1
                   logical name: /dev/hda1
                   capacity: 35GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: ide@0.0,2
                   logical name: /dev/hda2
                   size: 1608MB
                   capacity: 1608MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/hda5
                      capacity: 1608MB
                      capabilities: nofs
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          logical name: scsi2
          logical name: scsi3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list emulated scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:dc00-dc0f iomemory:fe02d000-fe02dfff irq:16
        *-disk
             description: SCSI Disk
             product: WDC WD5000AAKS-0
             vendor: ATA
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 12.0
             serial: WD-WCAS82630947
             size: 465GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume:0
                description: HPFS/NTFS partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                capacity: 195GB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 270GB
                capacity: 270GB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 195GB
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S203N
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5
           *-disc
                physical id: 0
                logical name: /dev/cdrom
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.1
          bus info: pci@00:05.1
          logical name: scsi7
          logical name: scsi8
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9e0-9e7 ioport:be0-be3 ioport:960-967 ioport:b60-b63 ioport:c800-c80f iomemory:fe02c000-fe02cfff irq:17
     *-ide:3
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: nVidia Corporation
          physical id: 5.2
          bus info: pci@00:05.2
          logical name: scsi10
          logical name: scsi9
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:c400-c407 ioport:c000-c003 ioport:bc00-bc07 ioport:b800-b803 ioport:b400-b40f iomemory:fe02b000-fe02bfff irq:18
     *-pci:0
          description: PCI bridge
          product: MCP55 PCI bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: b
             bus info: pci@01:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
             resources: iomemory:fdeff000-fdeff7ff iomemory:fdef8000-fdefbfff irq:20
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:fe020000-fe023fff irq:19
     *-bridge:0
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a3
          serial: 00:1d:60:ca:37:a3
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=172.16.1.102 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02a000-fe02afff ioport:b000-b007 iomemory:fe029000-fe0290ff iomemory:fe028000-fe02800f irq:18
     *-bridge:1
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          logical name: eth1
          version: a3
          serial: 00:1d:60:ca:48:01
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: iomemory:fe027000-fe027fff ioport:ac00-ac07 iomemory:fe026000-fe0260ff iomemory:fe025000-fe02500f irq:19
     *-pci:1
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: JMicron 20360/20363 AHCI Controller
             vendor: JMicron Technologies, Inc.
             physical id: 0
             bus info: pci@02:00.0
             logical name: scsi5
             logical name: scsi6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: storage ahci_1.0 bus_master cap_list scsi-host
             configuration: driver=ahci latency=0
             resources: iomemory:fddfe000-fddfffff irq:21
        *-ide
             description: IDE interface
             product: JMicron 20360/20363 AHCI Controller
             vendor: JMicron Technologies, Inc.
             physical id: 0.1
             bus info: pci@02:00.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=pata_jmicron latency=0
             resources: ioport:9c00-9c07 ioport:9800-9803 ioport:9400-9407 ioport:9000-9003 ioport:8c00-8c0f irq:21
     *-pci:2
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@00:0f.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: G70 [GeForce 7600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@03:00.0
             version: a1
             size: 256MB
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia latency=0
             resources: iomemory:fa000000-faffffff iomemory:e0000000-efffffff iomemory:fb000000-fbffffff ioport:7c00-7c7f irq:21
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MH

---

### Post by shutslar on 2008-02-03
You might want to try logging into windows, and then unmounting the drive from windows (I think it will say: safe to disconnect device).  Then reboot into linux and see if that helps.  Also, I have seen where it is necessary to unmount from windows, unplug the usb from the computer, boot into linux, then plug the usb back in.  

Might give these two options a try.

---

### Post by RizingDamp on 2008-02-03
Ok I tried those two options, but still nothing!!  Its still showing in the hslw report.  This is sooo frustrating.

---


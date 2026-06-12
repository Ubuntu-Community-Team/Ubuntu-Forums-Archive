---
title: "Is my graphics card supported"
date: 2010-11-21
forum: Hardware
---

### Post by Staz84 on 2010-11-21
Hello 

This is my first post.
I have tried to install lubuntu on my old toshiba portege laptop.
I am unable to run the minimum graphics option - or any graphics.

here is my lshw output
```

computer
    description: Notebook
    product: PORTEGE7200
    vendor: TOSHIBA
    version: PP720A-6D90N
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=expansion frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=5C187E80-2BAE-11D4-8067-C41650013015
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.90 (12/31/1999)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba acpi usb agp ls120boot biosbootspecification netboot
     *-cpu:0 DISABLED
          description: CPU [empty]
          product: Pentium III
          vendor: Intel Corporation
          physical id: 4
          slot: IC20
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 32KiB
             capacity: 32KiB
             clock: 500MHz (2.0ns)
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 256KiB
             capacity: 256KiB
             clock: 500MHz (2.0ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 128MiB
          capacity: 320MiB
        *-bank:0
             description: SDRAM Synchronous
             physical id: 0
             slot: System 0
             size: 64MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 0
             size: 64MiB
             width: 64 bits
     *-cpu:1
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64
          resources: irq:0 memory:f0000000-f7ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fec00000-ff7fffff memory:10100000-101fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Cyber 9540
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 52
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=8
                resources: memory:ff400000-ff7fffff memory:ff3e0000-ff3fffff memory:fec00000-feffffff memory:10100000-1010ffff
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 5.1
             bus info: pci@0000:00:05.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fff0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK1214GA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: N0.1
                serial: [REMOVED]
                size: 11GiB (12GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002a695
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-20 22:52:38 filesystem=ext4 lastmountpoint=/O]9
d modified=2010-11-21 01:12:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-21 13:46:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 374MiB
                   capacity: 374MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 374MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-C2102
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1329
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 5.2
             bus info: pci@0000:00:05.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: irq:11 ioport:ff80(size=32)
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 5.3
             bus info: pci@0000:00:05.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-network
             description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             logical name: eth0
             version: 05
             serial: [REMOVED]
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
             resources: irq:11 memory:effff000-efffffff ioport:ff60(size=32) memory:feb00000-febfffff memory:fea00000-feafffff
        *-communication UNCLAIMED
             description: Communication controller
             product: 56k WinModem
             vendor: Agere Systems
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
             resources: memory:ffefff00-ffefffff ioport:2f8(size=8) ioport:1c00(size=256)
        *-generic DISABLED
             description: IRDA interface
             product: FIR Port Type-DO
             vendor: Toshiba America Info Systems
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: irda0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list irda logical
             configuration: driver=donauboe latency=64
             resources: irq:11 ioport:ff40(size=32)
        *-pcmcia:0
             description: CardBus bridge
             product: ToPIC95
             vendor: Toshiba America Info Systems
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=0 maxlatency=5
             resources: irq:11 memory:10200000-10200fff ioport:1000(size=256) ioport:1400(size=256) memory:14000000-17ffffff memory:18000000-1bffffff
        *-pcmcia:1
             description: CardBus bridge
             product: ToPIC95
             vendor: Toshiba America Info Systems
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128
             resources: irq:11 memory:10201000-10201fff ioport:1800(size=256) ioport:2000(size=256) memory:1c000000-1fffffff memory:20000000-23ffffff
        *-multimedia
             description: Multimedia audio controller
             product: ES1978 Maestro 2E
             vendor: ESS Technology
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ES1968 (ESS Maestro) latency=64 maxlatency=24 mingnt=2
             resources: irq:11 ioport:fc00(size=256)
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 2
          bus info: pci@0000:02:00.0
          version: 41
          width: 32 bits
          clock: 33MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:11 memory:18000000-18000fff
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@0000:02:00.1
          version: 41
          width: 32 bits
          clock: 33MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:11 memory:18001000-18001fff
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@0000:02:00.2
          version: 02
          width: 32 bits
          clock: 33MHz
          capabilities: pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=68 maxlatency=34 mingnt=16
          resources: irq:11 memory:18002000-180020ff
     *-scsi
          physical id: 3
          bus info: usb@4:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: U3 Cruzer Micro
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 8.02
             serial: [REMOVED]
             size: 7663MiB (8036MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 7663MiB (8036MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   physical id: 1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: [REMOVED]
                   size: 7655MiB
                   capacity: 7655MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
  *-battery
       description: Lithium Ion Battery
       product: LI960U
       vendor: TOSHIBA
       physical id: 1
       version: 04/03/00
       serial: [REMOVED]
       slot: 1st Battery
       configuration: voltage=10.8V

```
I imported the file into wordpad so there may be some nonsense included!
Will I be able to run lubunto?

Many thanks in advance

---

### Post by Staz84 on 2010-11-21
P.S.  I used the minimum install method to install lubuntu

---

### Post by cavalier911 on 2010-11-21
See this: 
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+question/122266](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+question/122266)

---

### Post by Staz84 on 2010-11-21
Thanks cavalier911

I was kind of busy today and didn't check those earlier posts.

---


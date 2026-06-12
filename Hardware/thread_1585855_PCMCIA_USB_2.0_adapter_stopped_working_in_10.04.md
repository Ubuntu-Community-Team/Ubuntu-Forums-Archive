---
title: "PCMCIA USB 2.0 adapter stopped working in 10.04"
date: 2010-10-01
forum: Hardware
---

### Post by Oswald1 on 2010-10-01
Greetings all,

Here's my conundrum:

I have a (pretty old) laptop, which doesn't have usb 2.0 ports of it's own, so I use a PCMCIA card to get those. It used to work just fine, but yesterday I upgraded from 9.10 to 10.04 and the party was over.

It seems to 'almost' work in the sense that e.g. a usb network adapter get's recognized, but doesn't make a connection, and an external hdd gets mounted after trying for a long time if at all.

Concurrently stuff like this appears in kern.log

```

Sep 30 19:46:41 maikki kernel: [   59.940067] usb 6-1: reset high speed USB device using ehci_hcd and address 2
Sep 30 19:46:41 maikki kernel: [   75.092071] usb 6-1: device descriptor read/64, error -110
Sep 30 19:48:47 maikki kernel: [  214.080090] usb 6-1: new high speed USB device using ehci_hcd and address 7
Sep 30 19:48:57 maikki kernel: [  224.512091] usb 6-1: device not accepting address 7, error -110
Sep 30 19:48:57 maikki kernel: [  224.512146] hub 6-0:1.0: unable to enumerate USB device on port 1

```

Here's the output of lshw if it helps:

```
maikki
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 1015MiB
     *-cpu
          product: Intel(R) Pentium(R) III Mobile CPU      1200MHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.11.1
          size: 1197MHz
          capacity: 1197MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:98000000-9fffffff(prefetchable) memory:90100000-9017ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0 maxlatency=11
             resources: memory:88000000-8fffffff(prefetchable) memory:80200000-8027ffff
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:a4a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:a4e0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:a800(size=32)
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 41
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:7000(size=4096) memory:80100000-801fffff memory:30000000-3bffffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:10 memory:80100000-801007ff memory:80104000-80107fff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:80102000-80102fff ioport:7400(size=256) ioport:7800(size=256) memory:30000000-33ffffff(prefetchable) memory:40000000-43ffffff
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 41
                serial: 00:00:e2:5b:c5:68
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.0.13 latency=66 maxlatency=56 mingnt=8 multicast=yes
                resources: irq:11 memory:80101000-80101fff ioport:7000(size=64)
           *-pcmcia:1
                description: CardBus bridge
                product: OZ6933/711E1 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:10 memory:80103000-80103fff ioport:7c00(size=256) ioport:1000(size=256) memory:34000000-37ffffff(prefetchable) memory:44000000-47ffffff
           *-pcmcia:2
                description: CardBus bridge
                product: OZ6933/711E1 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 9.1
                bus info: pci@0000:01:09.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:10 memory:80108000-80108fff ioport:1400(size=256) ioport:1800(size=256) memory:38000000-3bffffff(prefetchable) memory:48000000-4bffffff
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a890(size=16) memory:3c000000-3c0003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:8000(size=32)
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:9800(size=256) ioport:9c00(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:a000(size=256) ioport:a400(size=128)
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0
          bus info: pci@0000:06:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:10 memory:44000000-44000fff
     *-usb:1
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@0000:06:00.1
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
          resources: irq:10 memory:44001000-44001fff
     *-usb:2
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@0000:06:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=ehci_hcd latency=68 maxlatency=34 mingnt=16
          resources: irq:10 memory:44002000-440020ff
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth2
       serial: 00:1a:9f:0b:08:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=asix driverversion=14-Jun-2006 firmware=ASIX AX88178 USB 2.0 Ethernet ip=213.243.180.230 multicast=yes

```

I tried booting up using an older kernel  (2.6.31-22) and the ports started working again.

Here's the result of lshw in that case:
```
maikki
    description: Notebook
    product: TravelMate 620
    vendor: acer
    version: -1
    serial: 9142S01C6V207040F7T000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=4EFC82C0-2583-11D6-A252-E2689375053A
  *-core
       description: Motherboard
       product: Intel Almador-M
       vendor: acer
       physical id: 0
       version: -1
       serial: 9142S01C6V207040F7T000
     *-firmware
          description: BIOS
          vendor: ACER
          physical id: 0
          version: V3.3 R01-A1B (12/11/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp smartbattery biosbootspecification
     *-cpu:0 DISABLED
          description: CPU [empty]
          product: Pentium III
          vendor: Intel
          physical id: 400
          version: Pentium(R) III
          slot: U11
        *-cache:0
             description: L1 cache
             physical id: 700
             slot: U11
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 701
             slot: U37
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 759MiB
        *-bank:0
             description: DIMM SDRAM Synchronous [empty]
             physical id: 0
             slot: DM2
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: CN22
             width: 64 bits
     *-cpu:1
          product: Intel(R) Pentium(R) III Mobile CPU      1200MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.1
          size: 1197MHz
          capacity: 1197MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:98000000-9fffffff(prefetchable) memory:90100000-9017ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=11
             resources: memory:88000000-8fffffff(prefetchable) memory:80200000-8027ffff
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:a4a0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:a4e0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:a800(size=32)
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 41
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:7000(size=4096) memory:80100000-801fffff memory:30000000-3bffffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:10 memory:80100000-801007ff memory:80104000-80107fff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:80102000-80102fff ioport:7400(size=256) ioport:7800(size=256) memory:30000000-33ffffff(prefetchable) memory:40000000-43ffffff
              *-network
                   description: WaveLAN/IEEE
                   product: Version 01.01
                   vendor: Lucent Technologies
                   physical id: 0
                   slot: Socket 0
           *-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 41
                serial: 00:00:e2:5b:c5:68
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.13 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:11 memory:80101000-80101fff ioport:7000(size=64)
           *-pcmcia:1
                description: CardBus bridge
                product: OZ6933/711E1 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:10 memory:80103000-80103fff ioport:7c00(size=256) ioport:1000(size=256) memory:34000000-37ffffff(prefetchable) memory:44000000-47ffffff
           *-pcmcia:2
                description: CardBus bridge
                product: OZ6933/711E1 CardBus/SmartCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 9.1
                bus info: pci@0000:01:09.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: irq:10 memory:80108000-80108fff ioport:1400(size=256) ioport:1800(size=256) memory:38000000-3bffffff(prefetchable) memory:48000000-4bffffff
              *-pccard UNCLAIMED
                   description: SmartCardBus Reader
                   vendor: O2Micro
                   physical id: 0
                   version: V1.0
                   slot: Socket 2
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a890(size=16) memory:3c000000-3c0003ff
           *-disk
                description: ATA Disk
                product: IC25N030ATDA04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DA4O
                serial: 64A64MP3216
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f7c8f7c8
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 668001d7-51ef-4b7f-b60a-eef3d448ba89
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-11-02 19:41:34 filesystem=ext3 modified=2010-09-30 20:30:52 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-10-01 00:45:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1011MiB
                   capacity: 1011MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1011MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-C2502
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1C11
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801CA/CAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:8000(size=32)
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:9800(size=256) ioport:9c00(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:a000(size=256) ioport:a400(size=128)
     *-usb:0
          description: USB Controller
          product: USB
          vendor: NEC Corporation
          physical id: 2
          bus info: pci@0000:06:00.0
          version: 43
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=255 maxlatency=42 mingnt=1
          resources: irq:10 memory:44000000-44000fff
     *-generic
          product: USB
          vendor: NEC Corporation
          physical id: 0.1
          bus info: pci@0000:06:00.1
          version: ff
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=255 maxlatency=42 mingnt=1
          resources: irq:10 memory:44001000-44001fff
     *-usb:1
          description: USB Controller
          product: USB 2.0
          vendor: NEC Corporation
          physical id: 0.2
          bus info: pci@0000:06:00.2
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ehci_hcd latency=255 maxlatency=34 mingnt=16
          resources: irq:10 memory:44002000-440020ff
     *-scsi
          physical id: 3
          bus info: usb@6:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0005181e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/bufbak
                version: 1.0
                serial: fe62878c-b164-4837-a528-9441514ad6ff
                size: 464GiB
                capacity: 464GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-09-13 16:19:14 filesystem=ext4 lastmountpoint=/media/bufbak%Â€Oï¿½ï¿½hï¿½ï¿½ïï¿½ï¿½ï¿½iï¿½>Uï¿½Ifï¿½ ï¿½ï¿½ï¿½ ï¿½ï¿½ï¿½Oï¿½ï¿½ï¿½>UÝ¸>UÝ¥h modified=2010-10-01 00:46:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-01 00:46:01 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/bufext
                version: 1.0
                serial: 2657c66e-19b8-440d-b11b-5d13fcfaf21a
                size: 466GiB
                capacity: 466GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-11-02 14:06:00 filesystem=ext4 label=BufEXT4 lastmountpoint=/media/bufextï¿½!Ò·ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½HÝ€ï¿½ï¿½ïï¿½ï¿½ï¿½kï¿½Ifï¿½ï¿½ulï¿½ï¿½ulÇ€ï¿½ï¿½ï¿½ïï¿½ï¿½kà¸¾kï¿½h modified=2010-10-01 00:46:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-01 00:46:01 state=mounted
  *-battery
       description: Lithium Ion Battery
       physical id: 1
       slot: On the Right-hand side
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth2
       serial: 00:1a:9f:0b:08:44
       size: 1GB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88178 USB 2.0 Ethernet ip=213.243.180.230 link=yes multicast=yes port=MII speed=1GB/s

```

One difference between the old-kernel-output and 'normal' output is that I have the hdd and network adapter plugged in the pcmcia card in the old-kernel case.

If I'm correct, the relevant parts are the usb-controllers with vendor NEC Corporation. The differences I spot there are: 
1. The usb:1 is named as generic in the configuration with the old kernel. 
2. The old kernel output lists pm in capabilities for the devices but not with the new one.
3. latency is 64 with the old kernel, but 255 with the old one.
4. The physical id of usb:0 is 0 with the new kernel and 2 with the old one.


Any ideas what might be wrong here? Could it be about the latency? The pcmcia latency is 176 in both cases. Is it a bad thing that the usb latency is lower than the pcmcia latency (just shooting air here)? 


Thanks a bunch for any advice!

---

### Post by Oswald1 on 2010-10-01
I booted again with the old kernel, but this time the latencies were shown the same way as with the new kernel, but the devices worked still as previously, so I suppose this is not about latencies.

Any ideas anyone?

---

### Post by brattham on 2010-10-07
I have exactly the same problem with Ubuntu 10.04 on my old laptop (Fujitsu-Siemens Lifebook C1020). USB 2.0 to PCMCIA/BusCard (NEC-controller, of course) doesn't work: Can't get any connection whit my Huawei E1820, HSPA+, mobile broadband. With my computers original USB 1.1-port, there is no problemo, except for the speed (about 30 - 50 percent slower connection).

There is no problem to get other things working with the USB 2.0-BusCard, for example like a USB-memory: The problem is related just to the broadband modem!

Maybe there is another USB 2.0-BusCard without a NEC USB 2.0-controller, who is working better with linux? Let me know if you find a solution! :)

/Mvh Per

---


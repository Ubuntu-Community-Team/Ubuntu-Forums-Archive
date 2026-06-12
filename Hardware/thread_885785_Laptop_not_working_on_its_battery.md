---
title: "Laptop not working on its battery"
date: 2008-08-10
forum: Hardware
---

### Post by fredmt on 2008-08-10
I recently acquired a new battery for my laptop: Compaq Presario 2100, after not having a working battery in my laptop for over two years. It has always been plugged into AC but the problem is, the computer will only work for a few seconds (less than a minute) before shutting down. Computer will not start on battery though icon says battery is at 100%. Icon is green as opposed to yellow, which has been dead these two years.

A little history on the dead battery: It was also a new replacement but since it was not used for a couple of months after I got it, I assumed the deadness was my fault; I am a line-haul trucker in the USA and the battery sat at home until I eventually got to it.

Anyhow: I have read the forums looking for clues and ideas for any possible solutions but have come up short.

Any ideas would be greatly appreciated...

Here is the posting of the laptop:

description: Notebook
    product: Presario 2100 (DM745A)
    vendor: Hewlett-Packard
    version: KE.M1.64
    serial: CNF3362G2W
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=40B1FD1E-6AD1-D711-A873-000BCDEB7D03
  *-core
       description: Motherboard
       product: 002A
       vendor: Hewlett-Packard
       physical id: 0
       version: NS570 Version PQ1A80
       serial: None
       slot: &#65533;USB2
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: KE.M1.64 (08/07/2003)
          size: 109KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom pcmciaboot edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: Mobile Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: WMT478/NWD
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts sync_rdtsc cid xtpr
          configuration: id=0
        *-cache
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 8KiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J400
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: J401
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: RS200/RS200M AGP Bridge [IGP 340M]
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon IGP 330M/340M/350M
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2 module=snd_ali5451
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ALi Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=64
        *-pcmcia
             description: CardBus bridge
             product: OZ601/6912/711E0 CardBus/SmartCardBus Controller
             vendor: O2 Micro, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
           *-network
                description: SMC
                physical id: 0
                version: 2632W-V2
                slot: Socket 0
                resources: irq:3
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=32 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23EA-40
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00K3A0A2
                   serial: LM3493
                   size: 37GiB (40GB)
                   capacity: 37GiB (40GB)
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 signature=ae32ae32 smart=on
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      logical name: /
                      logical name: /dev/.static/dev
                      version: 1.0

                      serial: d07eee6d-81e2-4bbc-9ee9-4d4d566b01f1
                      size: 36GiB
                      capacity: 36GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-05-10 17:58:54 filesystem=ext3 modified=2008-08-10 08:30:33 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-10 08:30:33 state=mounted
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 1286MiB
                      capacity: 1286MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 1286MiB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: QSI CD-RW/DVD-ROM SBW-241
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: VH04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2 status=nodisc
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm
             configuration: driver=ali1535_smbus latency=0 module=i2c_ali1535
        *-network
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:eb:7d:03
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=24.192.249.227 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:04:e2:46:d0:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

Thanks in advance for any help...

---

### Post by silkstone on 2008-08-10
It sounds like a faulty battery or a defective circuit within the computer which is causing rapid drain. It may show fully charged, but it rapidly discharges under load, and doesn't have enough power for boot-up.

I can't offer a quick fix, but it reminds me of a problem a few years back with a certain type of digital camera, where batteries were discharging very quickly. It turned out that the paint around the battery housing had some carbon in it and was slightly conductive, so there was a partial short circuit across the terminals. It would be a real coincidence if you had a similar problem, but it's strange that two batteries should behave the same way.

---


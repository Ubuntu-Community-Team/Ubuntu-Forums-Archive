---
title: "Determinar placa de video y configurar xorg.conf"
date: 2010-01-31
forum: Hardware
---

### Post by isaias2 on 2010-01-31
Que tal, buenas tardes, les queria consulta sobre un problema que tengo para configurar el archivo xorg.conf en ubuntu 9.10, para que en mi noteboock marca HP modelo ze5400 con monitor de 15 pulgadas (1024x786 @ 60hz) pueda colocar un monitor externo de mi trabajo marca samsung de 22 pulgadas (1680 x 1050 @ 60hz)a traves de la salida VGA.

El problema es que no se que placa grafica tenga la maquina o mejor dicho no se como configurar la seccion "device" en el archivo:

```
Section "Device"
        Identifier      "?????"
        Driver          "?????"
        BusID           "?????"
        Screen          0
EndSection
```Este es mi lspci, ahi dice 330/340/350 realmente no se cual seria:

> 00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
Aca les paso mi lshw completo por si las dudas quieran revisar algo:

```
                   
    description: Notebook
    product: Pavilion ze5400 (DL807A)
    vendor: Hewlett-Packard
    version: KH.F.08
    serial: CNF3260XLQ
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=20D58494-299E-D711-973B-000BCDAADA7F
  *-core
       description: Motherboard
       product: 0850
       vendor: Hewlett-Packard
       physical id: 0
       version: NS570 Version PQ1B56
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies Ltd.
          physical id: 0
          version: KF_KH.F.08 (06/06/2003)
          size: 107KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom pcmciaboot edd int13floppynec int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: WMT478/NWD
          size: 2400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
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
          physical id: e
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
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:d4000000-d7ffffff(prefetchable) memory:d0009000-d0009fff(prefetchable)
        *-pci
             description: PCI bridge
             product: PCI Bridge [IGP 340M]
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:d0300000-d03fffff memory:d8000000-dfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon IGP 330M/340M/350M
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:d8000000-dfffffff(prefetchable) ioport:9000(size=256) memory:d0300000-d030ffff memory:d0320000-d033ffff(prefetchable)
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
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2
             resources: irq:5 ioport:1000(size=256) memory:d0000000-d0000fff
        *-isa
             description: ISA bridge
             product: M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
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
             capabilities: pm cap_list
             configuration: latency=64
             resources: memory:d0001000-d0001fff ioport:1400(size=256)
        *-network:0
             description: Wireless interface
             product: Prism 2.5 Wavelan chipset
             vendor: Intersil Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth1
             version: 01
             serial: 00:02:8a:99:89:c1
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list ethernet physical wireless
             configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 latency=64 link=no multicast=yes wireless=IEEE 802.11b
             resources: irq:10 memory:d000a000-d000afff(prefetchable)
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
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
             resources: irq:11 memory:d0002000-d0002fff ioport:1800(size=256) ioport:1c00(size=256) memory:2c000000-2fffffff(prefetchable) memory:30000000-33ffffff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:2000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:2020(size=32)
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 51
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:d0003000-d00030ff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
             resources: irq:10 memory:d0003800-d0003fff memory:d0004000-d0007fff
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: scsi0
             logical name: scsi1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_ali latency=32 maxlatency=4 mingnt=2
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2040(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHS2040A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8006
                serial: NLBDT36152C7
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d4cad4ca
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 41bd7752-d5d3-4296-9bb9-61552d739fe7
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-12-27 16:06:27 filesystem=ext4 lastmountpoint=/n&#65533;&#65533;\&#65533;&#65533;UX&#1770;&#65533;&#65533;x&#65533;&#65533;&#65533;9Z&#65533;(&#65533;X&#65533;(&#65533;X&#1742;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1108;&#65533;&#65533;&#1109;\&#65533;&#65533;&#65533;p&#65533;%&#65533;&#65533;&#65533; modified=2010-01-28 20:53:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-31 17:55:04 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1027MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/bt4
                      capacity: 18GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback state=mounted
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4240N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0111
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=ali1535_smbus latency=0
             resources: irq:0
        *-network:1
             description: Ethernet interface
             product: DP83815 (MacPhyter) Ethernet Controller
             vendor: National Semiconductor Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 00
             serial: 00:0b:cd:aa:da:7f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.6 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
             resources: irq:10 ioport:2400(size=256) memory:d0008000-d0008fff memory:34000000-3400ffff(prefetchable)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
```Otra consulta que tengo es que si debo crear 2 secciones "device" (que tendrian de diferente?) y "monitor" ( en realidad monitor me imagino que si para el monitor en si de la maquina y el externo).

Aclaro que todo esto surge a que conectando el monitor externo la resolucion maxima que puedo usar es 1024x786...no me interesa mas nada que clonar la pantalla no extenderla como eh visto porque no me sirve.

Desde ya gracias y si hace falta algo mas me dicen.

---


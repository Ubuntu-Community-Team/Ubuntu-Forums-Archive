---
title: "Adding more storage to desktop/server"
date: 2011-05-09
forum: Hardware
---

### Post by electric-wildflower on 2011-05-09
Hello everyone i was wondering if anyone could help me on a question i need answering.

I have a desktop computer i also use as a server for storage and to stream stuff of it onto my gaming machine/laptop and for family to connect to and i was wondering if anyone could help me on figuring out what would be the best options on upgrading storage.

I am looking to get a few tb's in there to give it proper storage as the hard disks i currently have well there not really big.

my desktop specs are as followed i used the command sudo lshw so i could show you more details.

---------------------------------------------------------------------------------------

description: Desktop Computer
    product: MX46-533
    vendor: CENTERPRISE
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 1244
       vendor: AOpen
       physical id: 0
       version: 9189U10061
       serial: 24400536LM75
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/05/2002)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1536MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 651 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: memory:e4000000-e5ffffff memory:d0000000-dfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:e4000000-e4ffffff memory:d0000000-dfffffff(prefetchable) memory:e5000000-e501ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:10c0(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-disk:0
                description: ATA Disk
                product: Maxtor 2F030L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: VAM5
                serial: F18NX8HE
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002e4a4
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a336db30-3412-4a4d-a553-d3d3b0f6eadc
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-06 21:41:30 filesystem=ext4 lastmountpoint=/k&#65533;Y&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;p&#65533;r&#65533;~ &#65533;&#65533;/&#65533;d&#65533;r&#65533;>.!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;r&#65533;M&#65533; modified=2011-05-06 22:35:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-05-08 20:32:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1254MiB
                   capacity: 1254MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1254MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 6L200P0
                vendor: Maxtor
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: BAH4
                serial: L40XVQTG
                size: 189GiB (203GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000af9de
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/sdb1
                   version: 1.0
                   serial: 8f591e14-4615-4020-b232-8b09c74c6cc1
                   size: 189GiB
                   capacity: 189GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-17 22:29:25 filesystem=ext4 label=New Volume lastmountpoint=/media/sdb1&#65533;&#65533;<$&#1565;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Ev&#65533;^&#65533;&#65533;~ &#65533;&#65533;/&#65533;&#65533;^&#65533;&#65533;>.!&#65533; "&#65533; "&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-05-08 20:32:16 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-05-08 20:32:16 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H55N
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [HL-DT-STDVD-RAM GSA-H55N1.0007/03/21 7U02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:2
                description: ATA Disk
                product: Maxtor 4R120L0
                vendor: Maxtor
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: RAMB
                serial: R35H53EE
                size: 114GiB (122GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00013fbd
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   logical name: /media/sdc1
                   version: 1.0
                   serial: 51a152b1-69c0-4c67-bde9-b25102460ddf
                   size: 114GiB
                   capacity: 114GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-17 22:31:32 filesystem=ext4 label=New Volume lastmountpoint=/media/sdc1_&#65533;&#65533;&#65533;K&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;c`&#65533;&#65533;&#65533;~ &#65533;&#65533;/&#65533;&#65533;&#65533;&#65533;>.!&#65533;@t&#65533;&#65533;@t&#65533;&#65533;&#65533;&#65533;&#65533;K modified=2011-05-08 20:32:16 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-05-08 20:32:16 state=mounted
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:d800(size=256) ioport:dc00(size=128)
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:e6033000-e6033fff
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
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:e6034000-e6034fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:e6030000-e6030fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:e6031000-e6031fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:01:80:31:3a:d3
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:e000(size=256) memory:e6032000-e6032fff memory:60000000-6001ffff(prefetchable)
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k HSFi Modem
             vendor: Conexant Systems, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:e6020000-e602ffff ioport:e400(size=8)
     *-scsi:0
          physical id: 1
          bus info: usb@1:2
          logical name: scsi30
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@30:0.0.0
             logical name: /dev/sdd
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000e2ae8
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@30:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/usb external 1
                version: 1.0
                serial: f8e74295-6779-4c61-ae21-d4e7cde32132
                size: 465GiB
                capacity: 465GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-02-19 14:37:02 filesystem=ext4 label=usb external 1 lastmountpoint=/media/usb external 1&#65533;&#65533;kH&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;~ &#65533;&#65533;/&#65533;&#65533;~&#65533;>.!&#65533;([&#65533;&#65533; modified=2011-05-09 12:02:56 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2011-05-09 12:02:56 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:1
          logical name: scsi32
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@32:0.0.0
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



---------------------------------------------------------------------------------------

I have been looking around at options such as 

Bigger ide/ata hard disks.
Raid card with 4 port sata + sata to Molex IDE Power Adaptor Cables for converting to older power supply.
External hard disks.

With your guidance what would be the best option to take so i can have bigger hard disks for better storage.

thanks all for help in advanced :)

---


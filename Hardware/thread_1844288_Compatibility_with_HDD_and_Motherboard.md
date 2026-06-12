---
title: "Compatibility with HDD and Motherboard"
date: 2011-09-14
forum: Hardware
---

### Post by Juliolp on 2011-09-14
My PC Medion is 5 years old and it seems my HDD is near its end of life, and i would like to buy a new one. But i wonder wich kind of HDD i can install in the motherboard to copy the Ubuntu installation to the new HDD. I found one in Amazon that i like: 
**[SIZE=1]Western Digital WD2500BEVT Scorpio Blue - 250 GB (5400 rpm, 2,5'',  8 MB Cache, SATA)[/SIZE]**

and I wonder if it's compatible with my motherboard. I can read the word SATA in the lshw command but i would like to ask to the experts here. Now my HDD is ATA, as you can read in the description below. Thank you very much to the community, i really don't know enough to be secure of my buy, i only know... that i came from Windows and i love Ubuntu! :guitar::lolflag:

    ```
description: Desktop Computer
    version: 1.00
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=4895FC26-FB1D-B211-8000-64456E4E6973
  *-core
       description: Motherboard
       product: MS-7222
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.00
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 06/14/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Socket 775
          size: 3066MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Socket 775
          size: 3066MHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e8000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:fb000000-fcffffff memory:f4000000-f7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f4000000-f7ffffff memory:fb000000-fbffffff memory:fc000000-fc00ffff
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 7
             bus info: pci@0000:00:07.0
             logical name: eth0
             version: 10
             serial: 00:16:17:2e:85:8f
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
             resources: irq:20 ioport:fc00(size=256) memory:fdfff000-fdfff0ff memory:3c000000-3c00ffff
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64
             resources: irq:20 ioport:f800(size=8) ioport:f400(size=4) ioport:f000(size=8) ioport:ec00(size=4) ioport:e800(size=16) ioport:e400(size=256)
           *-disk
                description: ATA Disk
                product: ST3250824AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 4ND2EHNW
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00091b50
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: c8663ef3-f8a4-48bf-9fdb-78835f422586
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-15 21:36:13 filesystem=ext4 lastmountpoint=/ modified=2011-07-18 17:13:39 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2011-07-24 02:36:28 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 958MiB
                   capacity: 958MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 958MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW DW-G120A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: MYS2
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:dc00(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d400(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d000(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:fdffe000-fdffe0ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:cc00(size=256)
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
```

---

### Post by karrank% on 2011-09-15
No expert here, but I've had three--no, four different builds using different WD HDDs from caviars, to blues to greens and they all worked without issue (plug and play)  in every release I've used from dapper to lucid. Don't see why it wouldn't work for you.

---

### Post by coffeecat on 2011-09-15
According to some specs I found online, your motherboard has two headers for the older ide (PATA) drives (that's up to four devices - your optical drive is probably connected to one header) and it also has 2 SATA 150 headers. I *think* SATA150 is the first generation SATA standard and that most new 2nd and 3rd generation drives are backwards compatible, but you might want to check that or wait for someone a little more informed than myself to comment.

One thing about your selected WD drive. You don't give a link, but with the information you posted, this would appear to be a 2½" laptop-sized drive. 2½" drives are generally more expensive than equivalent capacity desktop-sized 3½" ones, and you would need a special carrier-adapter to fit it into a 3½" drive bay in a desktop machine. It would work - I've fitted a 2½" drive in a desktop; you are getting the benefit of it with this post! :wink: - but it's probably unnecessary for your needs.

---

### Post by Juliolp on 2011-09-15
Thanks very very much to both, Karrank% and Coffeecat, that info was very importante for me! And yes, coffeecat, i got the benefit of it, thank you very much for the info about sizes and i will find in searchers about backwards compatible,

a big hug to both! :D

---


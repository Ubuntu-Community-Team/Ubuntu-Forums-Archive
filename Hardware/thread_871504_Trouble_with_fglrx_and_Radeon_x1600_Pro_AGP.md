---
title: "Trouble with fglrx and Radeon x1600 Pro AGP"
date: 2008-07-27
forum: Hardware
---

### Post by dookehster on 2008-07-27
Hey Guys,

After working a few months at work with Ubuntu, I decided to switch from the dark side (I still love MS Office 2007 though).

Unfortunately, unlike every other installation I've done (4 different computers), this installation didn't seem to want to work. I'm on Ubuntu 8.04 btw.

My computer is a pre-lga775 (forget the old socket) P4 3GHz, 1.5 gigs of DDR, a TV Tuner card that I no longer use, Radeon x1600 Pro, and the rest you can see below (lshw).

I've tried the following approaches to get the proprietary ATI drivers:
1. Restricted hardware manager (Incorrectly detects my card as a FireGL)
2. Envy NG (Correctly detects my card, I get white screened when my computer tries to get GDM working)
3. [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) -I tried both from ATI and from the repositories and I get the same effect as Envy NG.

I suspect my TV tuner might be giving me some trouble or perhaps its because my card is AGP rather than the expected PCI-E. 

I'm tempted to just rebuild the damn kernel and turn this box into a pure server without Gnome or any other GUI.

Any help is greatly appreciated, thanks!

My lshw:

PCI (sysfs)  
dook1                     
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=B4447750-7633-DA11-9A7B-2436B8FA0C77
  *-core
       description: Motherboard
       product: P4P800-E
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: DIMM B2
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1009.003 (09/05/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPU 1
          size: 3GHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DDR Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM DDR Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 256MiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV530 [Radeon X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 msi vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=64 mingnt=8 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV530 [Radeon X1600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
           *-storage
                description: RAID bus controller
                product: PDC20378 (FastTrak 378/SATA 378)
                vendor: Promise Technology, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=sata_promise latency=96 maxlatency=18 mingnt=4 module=sata_promise
           *-network:0
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 13
                serial: 00:13:d4:da:06:a4
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: wifi0
                version: 01
                serial: 00:13:46:74:a1:92
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.2.10 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-multimedia
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: vpd pm bus_master cap_list
                configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD reader
                product: RW/DVD GCC-4521B
                vendor: HL-DT-ST
                physical id: 0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD writer
                product: DVDRW SOHW-1213S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: TS0C
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-disk:0
                description: ATA Disk
                product: ST3250824A
                vendor: Seagate
                physical id: 2
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 4ND1WQMG
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=994bf3ce
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 4aa38d94-0e49-4c45-b1fb-21ddb6207306
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-06-26 14:13:26 filesystem=ntfs label=Thaw state=clean
           *-disk:1
                description: ATA Disk
                product: Maxtor 6Y080P0
                vendor: Maxtor
                physical id: 3
                bus info: scsi@4:0.1.0
                logical name: /dev/sdb
                version: YAR4
                serial: Y245XV4C
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=24722471
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 765111a5-47a5-4135-bfb7-75c2c5ab09cb
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-26 12:03:03 filesystem=ext3 modified=2008-07-27 00:03:57 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-26 19:14:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.1.0,2
                   logical name: /dev/sdb2
                   size: 3223MiB
                   capacity: 3223MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 3223MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by dookehster on 2008-07-28
Bump^

---


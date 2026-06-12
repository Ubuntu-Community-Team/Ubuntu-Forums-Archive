---
title: "toughbook cf-29 live cd stops halfway / black screen"
date: 2010-06-25
forum: Hardware
---

### Post by SikDuk on 2010-06-25
Hello from AZ , I have a panasonic cf-29 1.3 P4 768mb RAM . It came with win7 on it and no cd drive just the floppy.. So I pulled the HD and put in a HD out of one of my cf-48's It choked at first then fired up Hardy and ran like a top fueler.. When the cd/rw dvd got here I tried to run ubuntu hardy and Lucid 10.04 they while booting it came to black screen and hung . It did this every time , now edgy booted ok and dapper a go. Also PCLinuxOS2010 fired up great.. I is running Linux Mint the best which if I'm not mistaken is built on ubuntu.. Has anyone figured out or had this problem before and found the fix??? I want to dual boot a 160gb with ubuntu10.04 & LinuxMint9 , to hell with windows... I would sure appreciate it.. I had a problem with no sound and figured out it was a hardware issue and flashed a upgraded BIOS and I have sound , but the latest ubuntu releases won't boot to the desk top.. Graphic's maybe??? my bios has the acpi=off on safeboot as well as regular boot.. So I'm stumped... Thank you...:confused: more info  
MY MACHINE
metal@metal-laptop ~ $ sudo lshw
[sudo] password for metal: 
metal-laptop              
    description: Notebook
    product: CF-29ENKNXKM
    vendor: Matsushita Electric Industrial Co.,Ltd.
    version: 001
    serial: 4KKSA76267
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=00000000-0000-1000-8000-000B972959F0
  *-core
       description: Motherboard
       product: CF29-2
       vendor: Matsushita Electric Industrial Co.,Ltd.
       physical id: 0
       version: 001
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies K.K.
          physical id: 0
          version: V2.00L17 (10/06/2005)
          size: 124KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1300MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: IC1
          size: 800MHz
          capacity: 1300MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: TSOP DDR Synchronous
             physical id: 0
             slot: Onboard
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             physical id: 1
             slot: DIMM
             size: 512MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 1f
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: TSOP FLASH Non-volatile
             physical id: 0
             slot: Flash ROM
             size: 512KiB
             width: 8 bits
     *-memory:2 UNCLAIMED
          physical id: 1
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e4000000-e7ffffff(prefetchable)
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82852/82855 GM/GME/PM/GMV Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:9 memory:e0100000-e01003ff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:30000000-37ffffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00303020-b0030301f irq:9 memory:e0202000-e0202fff ioport:3400(size=256) ioport:3800(size=256) memory:30000000-33ffffff(prefetchable) memory:3c000000-3fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 82
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704020-b0070401f irq:9 memory:e0203000-e0203fff ioport:3c00(size=256) ioport:1400(size=256) memory:34000000-37ffffff(prefetchable) memory:40000000-43ffffff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:94:d6:b6
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.3 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
                resources: irq:9 memory:e0200000-e0200fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:0b:97:29:59:f0
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:9 ioport:3000(size=256) memory:e0201000-e02010ff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:38000000-380003ff
           *-disk
                description: ATA Disk
                product: HTS424040M9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MA2O
                serial: MPA241Q2GNKM5A
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=05f7dbef
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8ed4af43-dcdb-2a4e-9061-bd287c2c938b
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-06-12 11:13:19 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 4ba0bc90-93cb-4e9e-a2e0-2a4eda6692d6
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-06-25 09:45:27 filesystem=ext3 modified=2010-06-25 10:21:10 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-06-25 10:22:37 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: fec1a30d-7315-4e84-80b2-f8fcb106c0ec
                   size: 2149MiB
                   capacity: 2149MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD reader
                product: UJDA750 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.50
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-battery:0
       description: Lithium Ion Battery
       product: CF-VZSU29
       vendor: Panasonic
       physical id: 1
       slot: in the front,left-hand side
       capacity: 58600mWh
       configuration: voltage=11.1V
  *-battery:1
       description: Lithium Ion Battery
       vendor: Panasonic
       physical id: 2
       slot: left-hand side
metal@metal-laptop ~ $ sudo  /make the/bad-things/go/away-NOW:guitar:

---

### Post by SikDuk on 2011-03-13
Right on.. Thanks for your info.. I was referring to running it live before the install.. bThe HD already has 8.04 and I want to install 10.04 at that time.. I'm thinking the CD DVD unit isn't reading it right to run..But LinuxMint 10 runs great..Bad *** hacking box.. Stay intouch.. Oh!!!! Like your outfit... LOL

---


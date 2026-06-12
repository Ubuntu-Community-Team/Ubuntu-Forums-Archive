---
title: "Compatible Video Cards with Mother Board SIS 741"
date: 2010-05-09
forum: Hardware
---

### Post by mr_random on 2010-05-09
Hi Everyone,
I am thinking of getting a video.  However, I am concerned if I buy a new video card it will not be compatible with my motherboard.
```
chris-desktop             
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: SiS-741
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (01/07/2004)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1250MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 1GiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 741/741GX/M741 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:e1000000-e10fffff memory:d8000000-dfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:d8000000-dfffffff(prefetchable) memory:e1000000-e101ffff ioport:d000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-disk:0
                description: ATA Disk
                product: Maxtor 6L300R0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAJ4
                serial: L6260KSG
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2ba52ba4
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 5e405642-546d-43d6-9686-bdf57e9cb66d
                   size: 273GiB
                   capacity: 273GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-03-01 22:05:34 filesystem=ext3 modified=2010-04-07 18:52:46 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-05-07 18:22:18 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5796MiB
                   capacity: 5796MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5796MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.76
                serial: 5JV4L6EV
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001a890
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: FAT32
                   serial: 153d-08fe
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   version: 1.0
                   serial: e83cae09-7824-4f57-a9e9-a0170aa7f527
                   size: 101MiB
                   capacity: 101MiB
                   capabilities: primary journaled extended_attributes ext3 ext2 initialized
                   configuration: created=2005-01-21 16:02:51 filesystem=ext3 label=/boot modified=2008-09-06 23:28:50 mounted=2008-09-06 22:58:27 state=clean
              *-volume:2
                   description: Linux LVM Physical Volume partition
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   serial: Lqhvss-7TNL-wogp-G4Z4-YEYa-MpDa-DsYw3s
                   size: 21GiB
                   capacity: 21GiB
                   capabilities: primary multi lvm2
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW DRU-830A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SS25
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: irq:18 ioport:e000(size=256) ioport:e400(size=128)
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
             resources: irq:20 memory:e1104000-e1104fff
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
             resources: irq:21 memory:e1100000-e1100fff
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
             resources: irq:22 memory:e1101000-e1101fff
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
             resources: irq:23 memory:e1102000-e1102fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:0d:87:b2:2f:f2
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.69 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:e800(size=256) memory:e1103000-e1103fff memory:80000000-8001ffff(prefetchable)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 10EADS External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 1.75
             serial: WD-WCAV55795690
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=00043682
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Elements_
                version: 3.1
                serial: 9405-2983
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-12-01 01:02:26 filesystem=ntfs label=Elements mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted

```

Are there any graphic cards that are compatible with SIS 471 mother boards?

Thanks!
Chris

---

### Post by cascade9 on 2010-05-16
As long as the motehrboard has the slot needed for the new video card, in most cases it will work. You've got to be caeful, however, that motherboard is old enough that it will only have PCI slots for sure, probably an AGP slot- but not the new PCIe slot that almost all the video cards currently on the market use.  

I've used various video cards on various different SiS chipsets, and never had an issue. 

BTW, I think your CPU is underclocked. Its using 100Mhz FSB, and says 'capcity- 1500Mhz'. There were no 1500Mhz Athlons with 100Mhz FSB. Its probably meant to use 133FSB- which would take it from 1500Mhz to 2000hz.

---


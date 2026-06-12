---
title: "How to install drivers for IBM / LSI SAS3444E PCI-E SATA Controller 25R8071"
date: 2013-10-11
forum: Hardware
---

### Post by Derek_Gentle on 2013-10-11
Hello All

I am in the process of setting up my server again after a couple (very) old HD's finally gave up the ghost.
No great loss, and in fact it gave me the opportunity to rebuild the server with newer and better hardware,
One of the pieces of hardware I installed is an IBM / LSI SAS3444E PCI-E SATA/SAS Controller (25R8071).

I'm having some trouble getting it setup, and was wondering if I am doing something wrong.

The hardware I am running is listed below:

```

ubuntu-server
    description: Computer
    product: X7DWE ()
    vendor: Supermicro
    version: 0123456789
    serial: 0123456789
    width: 64 bits
    capabilities: vsyscall32
    configuration: administrator_password=disabled boot=normal frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=53D19F64-D663-A017-8922-003048C7996C
  *-core
       description: Motherboard
       product: X7DWE
       vendor: Supermicro
       physical id: 0
       version: PCB Version
       serial: 0123456789
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.2c
          date: 11/19/2010
          size: 108KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppy2880 acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz
          slot: LGA771/CPU1
          size: 3020MHz
          width: 64 bits
          clock: 1600MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 12MiB
             capabilities: burst internal write-back
     *-cpu:1
          description: CPU
          product: Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@1
          version: Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz
          slot: LGA771/CPU2
          size: 3020MHz
          width: 64 bits
          clock: 1600MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 12MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns)
             product: M395T5750CZ4-CE61
             vendor: Samsung
             physical id: 0
             serial: 5119D008
             slot: DIMM1A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 1
             slot: DIMM1B
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 2
             slot: DIMM2A
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 3
             slot: DIMM2B
             clock: 667MHz (1.5ns)
        *-bank:4
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns)
             product: M395T5750CZ4-CE61
             vendor: Samsung
             physical id: 4
             serial: 0712A422
             slot: DIMM3A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:5
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 5
             slot: DIMM3B
             clock: 667MHz (1.5ns)
        *-bank:6
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 6
             slot: DIMM4A
             clock: 667MHz (1.5ns)
        *-bank:7
             description: DIMM DDR2 FB-DIMM Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 7
             slot: DIMM4B
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: 5400 Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5400 Chipset PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:48
        *-pci:1
             description: PCI bridge
             product: 5400 Chipset PCI Express Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:50
        *-pci:2
             description: PCI bridge
             product: 5400 Chipset PCI Express Port 5
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52
        *-pci:3
             description: PCI bridge
             product: 5400 Chipset PCI Express Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:54
        *-pci:4
             description: PCI bridge
             product: 5400 Chipset PCI Express Port 9
             vendor: Intel Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:56 ioport:2000(size=4096) memory:de100000-de2fffff ioport:d0000000(size=1048576)
           *-pci:0
                description: PCI bridge
                product: 6311ESB/6321ESB PCI Express Upstream Port
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:56 ioport:2000(size=4096) memory:de200000-de2fffff ioport:d0000000(size=1048576)
              *-pci:0
                   description: PCI bridge
                   product: 6311ESB/6321ESB PCI Express Downstream Port E1
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:06:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:56
              *-pci:1
                   description: PCI bridge
                   product: 6311ESB/6321ESB PCI Express Downstream Port E3
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:06:02.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:71 ioport:2000(size=4096) memory:de200000-de2fffff ioport:d0000000(size=1048576)
                 *-network:0
                      description: Ethernet interface
                      product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:08:00.0
                      logical name: eth0
                      version: 01
                      serial: 00:30:48:c7:99:6d
                      size: 1Gbit/s
                      capacity: 1Gbit/s
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=2.1-12 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1Gbit/s
                      resources: irq:89 memory:de220000-de23ffff memory:de200000-de21ffff ioport:2000(size=32) memory:d0000000-d000ffff
                 *-network:1
                      description: Ethernet interface
                      product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
                      vendor: Intel Corporation
                      physical id: 0.1
                      bus info: pci@0000:08:00.1
                      logical name: eth1
                      version: 01
                      serial: 00:30:48:c7:99:6d
                      size: 1Gbit/s
                      capacity: 1Gbit/s
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k duplex=full firmware=2.1-12 latency=0 link=yes multicast=yes port=twisted pair slave=yes speed=1Gbit/s
                      resources: irq:90 memory:de260000-de27ffff memory:de240000-de25ffff ioport:2020(size=32) memory:d0010000-d001ffff
           *-pci:1
                description: PCI bridge
                product: 6311ESB/6321ESB PCI Express to PCI-X Bridge
                vendor: Intel Corporation
                physical id: 0.3
                bus info: pci@0000:05:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm pcix normal_decode bus_master cap_list
        *-generic
             description: System peripheral
             product: 5400 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msix pciexpress bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:57 memory:fe700000-fe703fff
        *-pci:5
             description: PCI bridge
             product: 631xESB/632xESB/3100 Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:88 ioport:4000(size=4096) memory:d0100000-d02fffff ioport:d0300000(size=2097152)
        *-usb:0
             description: USB controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1800(size=32)
        *-usb:1
             description: USB controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1820(size=32)
        *-usb:2
             description: USB controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:1840(size=32)
        *-usb:3
             description: USB controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB controller
             product: 631xESB/632xESB/3100 Chipset EHCI USB2 Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:de504000-de5043ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d9
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:3000(size=4096) memory:de000000-de0fffff ioport:dc000000(size=33554432)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Z9s/Z9m (XG21 core)
                vendor: XGI Technology Inc. (eXtreme Graphics Innovation)
                physical id: 1
                bus info: pci@0000:0b:01.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller cap_list
                configuration: latency=0
                resources: memory:dc000000-ddffffff memory:de000000-de03ffff ioport:3000(size=128)
        *-isa
             description: ISA bridge
             product: 631xESB/632xESB/3100 Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 631xESB/632xESB IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1880(size=16)
        *-storage
             description: RAID bus controller
             product: 631xESB/632xESB SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 09
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:17 ioport:18d0(size=8) ioport:18c8(size=4) ioport:18c0(size=8) ioport:1894(size=4) ioport:18a0(size=32) memory:de504400-de5047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 631xESB/632xESB/3100 Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 09
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1100(size=32)
     *-pci:1
          description: Host bridge
          product: 5400 Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:00:10.0
          version: 20
          width: 32 bits
          clock: 33MHz
          configuration: driver=i5400_edac
          resources: irq:0
     *-pci:2
          description: Host bridge
          product: 5400 Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:00:10.1
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: 5400 Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:00:10.2
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: 5400 Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:00:10.3
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 5400 Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:00:10.4
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 5400 Chipset CE/SF Registers
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:00:11.0
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: 5400 Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:00:15.0
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: 5400 Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:00:15.1
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: 5400 Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:00:16.0
          version: 20
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: 5400 Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:00:16.1
          version: 20
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDR8164B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0L06
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-224BB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr1
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2502ABYS-5
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WCAT1E289787
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ed045
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 685ecd5f-38e7-4680-9429-576bfcc025dc
                size: 232GiB
                capacity: 232GiB
                capabilities: primary bootable multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-10-09 22:29:45 filesystem=ext4 lastmountpoint=/target modified=2013-10-09 22:49:39 mounted=2013-10-09 22:29:48 state=clean
     *-scsi:3
          physical id: 6
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2502ABYS-5
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             version: 02.0
             serial: WD-WCAT1E439387
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ed045
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 685ecd5f-38e7-4680-9429-576bfcc025dc
                size: 232GiB
                capacity: 232GiB
                capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2013-10-09 22:29:45 filesystem=ext4 lastmountpoint=/target modified=2013-10-09 22:49:39 mounted=2013-10-09 22:29:48 state=clean
     *-scsi:4
          physical id: 7
          logical name: scsi6
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000NM0033-9ZM
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 0001
             serial: Z1W04LZ9
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00071284
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                capacity: 931GiB
                capabilities: primary multi
     *-scsi:5
          physical id: 8
          logical name: scsi7
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000NM0033-9ZM
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdd
             version: 0001
             serial: Z1W043GM
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00083d94
           *-volume
                description: Linux raid autodetect partition
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdd1
                capacity: 931GiB
                capabilities: primary multi
     *-scsi:6
          physical id: 9
          bus info: usb@1:8
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sde
             size: 7385MiB (7743MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0006a976
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sde1
                logical name: /boot
                version: 1.0
                serial: 8b9a8978-17eb-49fa-965e-ac250b5d36e0
                size: 3814MiB
                capacity: 3814MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-09 23:09:47 filesystem=ext4 lastmountpoint=/boot modified=2013-10-11 11:40:44 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2013-10-11 11:40:44 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@8:0.0.0,2
                logical name: /dev/sde2
                version: 1
                serial: 5ec2e74c-8a6e-45de-9763-9916bedd4f53
                size: 3570MiB
                capacity: 3570MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: bond0
       serial: 00:30:48:c7:99:6d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bonding driverversion=3.7.1 firmware=2 ip=192.168.1.148 link=yes master=yes multicast=yes

```

```

00:00.0 Host bridge: Intel Corporation 5400 Chipset Memory Controller Hub (rev 20)
00:01.0 PCI bridge: Intel Corporation 5400 Chipset PCI Express Port 1 (rev 20)
00:03.0 PCI bridge: Intel Corporation 5400 Chipset PCI Express Port 3 (rev 20)
00:05.0 PCI bridge: Intel Corporation 5400 Chipset PCI Express Port 5 (rev 20)
00:07.0 PCI bridge: Intel Corporation 5400 Chipset PCI Express Port 7 (rev 20)
00:09.0 PCI bridge: Intel Corporation 5400 Chipset PCI Express Port 9 (rev 20)
00:0f.0 System peripheral: Intel Corporation 5400 Chipset QuickData Technology Device (rev 20)
00:10.0 Host bridge: Intel Corporation 5400 Chipset FSB Registers (rev 20)
00:10.1 Host bridge: Intel Corporation 5400 Chipset FSB Registers (rev 20)
00:10.2 Host bridge: Intel Corporation 5400 Chipset FSB Registers (rev 20)
00:10.3 Host bridge: Intel Corporation 5400 Chipset FSB Registers (rev 20)
00:10.4 Host bridge: Intel Corporation 5400 Chipset FSB Registers (rev 20)
00:11.0 Host bridge: Intel Corporation 5400 Chipset CE/SF Registers (rev 20)
00:15.0 Host bridge: Intel Corporation 5400 Chipset FBD Registers (rev 20)
00:15.1 Host bridge: Intel Corporation 5400 Chipset FBD Registers (rev 20)
00:16.0 Host bridge: Intel Corporation 5400 Chipset FBD Registers (rev 20)
00:16.1 Host bridge: Intel Corporation 5400 Chipset FBD Registers (rev 20)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 RAID bus controller: Intel Corporation 631xESB/632xESB SATA RAID Controller (rev 09)
00:1f.3 SMBus: Intel Corporation 631xESB/632xESB/3100 Chipset SMBus Controller (rev 09)
05:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
05:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
06:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
06:02.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E3 (rev 01)
08:00.0 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
08:00.1 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
0b:01.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z9s/Z9m (XG21 core)

```

Unless it's just me, it does not look like the card is even being recognized?  I've made sure that it is securley seated in the PCI-E slot on my motherboard, and it has a flashing light on the back of the card.

Anyone have any thoughts?

Many thanks in advance!

---


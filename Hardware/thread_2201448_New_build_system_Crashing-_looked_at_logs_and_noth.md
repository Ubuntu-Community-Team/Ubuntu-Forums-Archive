---
title: "New build system Crashing- looked at logs and nothing"
date: 2014-01-24
forum: Hardware
---

### Post by teaker1s-gmail on 2014-01-24
okay I had an account with the forums prior to their hack, and have been using various linux since 2005.

my problem is with a new build computer.
firstly gigabyte motherboard  IOMMU must be on to allow usb ports to function, without this boot is faster, but no usb ( I can see AMD vi page fault on start up and syslog from memory).
I have an 8 core 3.5ghz amd processor and 8gb ram.
I have passed ubuntu system testing
I have checked logs- the computer abruptly reboots without any warning- though generally more so when libre office and firefox are running.
I have disabled onboard realtek ethernet and fitted a pci card model that has worked without issue for years
I have substituted the power supply for reasonable quality make and output- incase the power supply issues
tried different graffics driver

```
description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 970A-DS3P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F1
          date: 04/08/2013
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: AMD FX(tm)-8320 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-8320 Eight-Core Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1400MHz
          capacity: 3500MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=8 enabledcores=8 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) Synchronous [empty]
             product: Dimm0_PartNum
             vendor: Dimm0_Manufacturer
             physical id: 0
             serial: Dimm0_SerNum
             slot: Node0_Dimm0
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) Synchronous [empty]
             product: Dimm1_PartNum
             vendor: Dimm1_Manufacturer
             physical id: 1
             serial: Dimm1_SerNum
             slot: Node0_Dimm1
        *-bank:2
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2013-10-12 13:19+0000X-Generator: Launchpad (build 16799) Synchronous [empty]
             product: Dimm2_PartNum
             vendor: Dimm2_Manufacturer
             physical id: 2
             serial: Dimm2_SerNum
             slot: Node0_Dimm2
        *-bank:3
             description: DIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: ST102464BA160
             vendor: Undefined
             physical id: 3
             serial: 61420000
             slot: Node0_Dimm3
             size: 8GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RD890 PCI to PCI bridge (external gfx0 port B)
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: RD990 I/O Memory Management Unit (IOMMU)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port B)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 ioport:e000(size=4096) memory:fea00000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Caicos [Radeon HD 6450/7450/8450]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:74 memory:d0000000-dfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff
           *-multimedia
                description: Audio device
                product: Caicos HDMI Audio [Radeon HD 6400 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:73 memory:fea40000-fea43fff
        *-pci:1
             description: PCI bridge
             product: RD890 PCI to PCI bridge (PCI express gpp port D)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:52 memory:fe900000-fe9fffff
           *-usb UNCLAIMED
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci cap_list
                configuration: latency=0
                resources: memory:fe900000-fe900fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:feb0b000-feb0b3ff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb0a000-feb0afff
        *-usb:1
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb09000-feb090ff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb08000-feb08fff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb07000-feb070ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=32
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:feb00000-feb03fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:d000(size=4096) memory:fe800000-fe8fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:03:07.0
                logical name: eth1
                version: 10
                serial: 00:30:bd:2e:c3:7b
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.108 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:21 ioport:d000(size=256) memory:fe810000-fe8100ff memory:fe800000-fe80ffff
        *-usb:4
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb06000-feb06fff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:feb05000-feb05fff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:feb04000-feb040ff
     *-pci:1
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500DM002-1BD14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: KC45
             serial: W2AVNZG6
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=00009fdc
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 05c7b151-ad87-4350-b416-d8bec37468fe
                size: 462GiB
                capacity: 462GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-11-21 21:38:03 filesystem=ext4 lastmountpoint=/ modified=2014-01-24 14:47:38 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-01-24 14:47:38 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223C
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3120026AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 3.56
             serial: 5LJ0CS08
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000b6407
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 1a1cf9d7-c45a-4483-a85f-a534da10ef5f
                size: 107GiB
                capacity: 107GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2011-05-26 02:46:21 filesystem=ext4 lastmountpoint=/media/office/1a1cf9d7-c45a-4483-a85f-a534da10ef5f modified=2013-11-23 23:34:12 mounted=2013-11-23 23:33:55 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdb2
                size: 4693MiB
                capacity: 4693MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 4693MiB
                   capabilities: nofs
     *-scsi:3
          physical id: 5
          bus info: usb@2:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB   HS-CF Card
             vendor: Sony
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             version: 3.95
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             product: USB   HS-SM Card
             vendor: Sony
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
             version: 3.95
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             product: USB   HS-MS Card
             vendor: Sony
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
             version: 3.95
             serial: 3
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             product: USB   HS-SD Card
             vendor: Sony
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
             version: 3.95
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdf
```
office@office-pc:~$ 

 lspci
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 USB controller: VIA Technologies, Inc. Device 3483 (rev 01)
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
[COLOR=#c20cb9][B]grep error /var/log/dmesg
[   18.311837] xhci_hcd: probe of 0000:02:00.0 failed with error -110
[   30.252216] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro


boot log
[/B][/COLOR]```

[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 6

[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 6

[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 6

[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 6

[./ply-boot-client.c]        ply_boot_client_detach_from_event_loop:detaching from event loop

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       #[80G 
#[74G[ OK ]
 * Starting bluetooth daemon#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Setting sensors limits       #[80G 
#[74G[ OK ]
 * Starting mDNS/DNS-SD daemon#[74G[ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated#[74G[ OK ]
 * Starting SystemD login management service#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated#[74G[#[31mfail#[39;49m]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Setting up X socket directories...       #[80G 
#[74G[ OK ]
 * Stopping System V initialisation compatibility#[74G[ OK ]
 * Starting System V runlevel compatibility#[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting Restore Sound Card State#[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting save kernel messages#[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting anac(h)ronistic cron#[74G[ OK ]
 * Starting ACPI daemon#[74G[ OK ]
 * Stopping #[74G[ OK ]
 * Stopping Restore Sound Card State#[74G[ OK ]
 * Starting #[74G[ OK ]
 * Starting configure network device security#[74G[ OK ]
 * Starting Initializes zram swaping#[74G[ OK ]
 * Starting CPU interrupts balancing daemon#[74G[ OK ]
 * Starting configure virtual network devices#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping Restore Sound Card State#[74G[ OK ]
 * Starting automatic crash report generation#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Starting network connection manager#[74G[ OK ]
 * Stopping save kernel messages#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Loading cpufreq kernel modules...       #[80G 
#[74G[ OK ]
 * Stopping anac(h)ronistic cron#[74G[ OK ]
 * Starting startpar bridge for notification of upstart job start/stop#[74G[ OK ]
 * Stopping startpar bridge for notification of upstart job start/stop#[74G[ OK ]
```

---

### Post by oldfred on 2014-01-25
Please use code tags with long text output. You can easily add them in Advanced editor with # in edit panel at top.

Is this just a somewhat random reboot. That can be difficult to debug.

Have you checked temperatures? 
Too much or too little silver paste on CPU can reduce heat transfer.

---

### Post by teaker1s-gmail on 2014-02-07
[http://unigine.com/products/valley/](http://unigine.com/products/valley/) runs perfectly

flash and particularly libre office at same time= reboot

I think it is flash issue, but no logs
yes I have checked temperatures.

this is annoying as hell on a machine with decent spec.

---


---
title: "ASUS Nvidia Geforce 210 Silent Freezing"
date: 2015-01-10
forum: Hardware
---

### Post by valeriancafe on 2015-01-10
Help system freezing with graphics card Asus Geforce 210 Silent

I reinstalled Ubuntu 14.04 after getting a new ssd. My graphics card is Asus Geforce 210 Silent url is [http://www.asus.com/Graphics_Cards/EN210_SILENTDI1GD3V2LP/](http://www.asus.com/Graphics_Cards/EN210_SILENTDI1GD3V2LP/)

and then after the install, I rebooted system, opened command-line did sudo apt-get update && sudo apt-get upgrade. Then rebooted and the system started to slow down. I tried all the Nvidia drivers listed and ALL freeze ????? I can only run the system if I don't install any updates at All

My system info is " without Nvida card installed " The card works in windows 7 no problems  


ubuntu-pc with out ASUS Geforce 210 Silent card installed

    ```
description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=A058C7C4-6BB8-DC11-808F-C86000BDEB2F
  *-core
       description: Motherboard
       product: E45M1-I DELUXE
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: MT7022050700501
       slot: To be filled by O.E.M.
     *-firmware:0
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0504
          date: 05/23/2014
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD E-450 APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: AMD E-450 APU with Radeon(tm) HD Graphics
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1320MHz
          capacity: 1650MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat hw_pstate npt lbrv svm_lock nrip_save pausefilter cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 0
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 1
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies data
        *-cache:2
             description: L1 cache
             physical id: 2
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back unified
        *-cache:3
             description: L2 cache
             physical id: 3
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies data
     *-memory:0
          description: System Memory
          physical id: 2
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 99U5471-021.A00LF
             vendor: Kingston
             physical id: 0
             serial: 65372569
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 99U5471-021.A00LF
             vendor: Kingston
             physical id: 1
             serial: 69372269
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 99U5471-021.A00LF
             vendor: Kingston
             physical id: 2
             serial: 65372569
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: 99U5471-021.A00LF
             vendor: Kingston
             physical id: 3
             serial: 69372269
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-firmware:1
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 3
          version: 0504
          date: 05/23/2014
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu:1
          description: CPU
          product: (To Be Filled By O.E.M.)
          vendor: AMD E-450 APU
          physical id: 4
          bus info: cpu@1
          version: AMD E-450 APU with Radeon(tm) HD Graphics
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1650MHz
          capacity: 1650MHz
          clock: 100MHz
          capabilities: x86-64 cpufreq
          configuration: cores=2 enabledcores=2
     *-memory:1
          description: System Memory
          physical id: 5
          slot: System board or motherboard
     *-memory:2 UNCLAIMED
          physical id: 6
     *-memory:3 UNCLAIMED
          physical id: 7
     *-pci:0
          description: Host bridge
          product: Family 14h Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Wrestler [Radeon HD 6320]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:48 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
        *-multimedia:0
             description: Audio device
             product: Wrestler HDMI Audio
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:47 memory:feb44000-feb47fff
        *-pci:0
             description: PCI bridge
             product: Family 14h Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:d0100000-d02fffff ioport:d0300000(size=2097152)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb4f000-feb4f3ff
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
             resources: irq:18 memory:feb4e000-feb4efff
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
             resources: irq:17 memory:feb4d000-feb4d0ff
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
             resources: irq:18 memory:feb4c000-feb4cfff
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
             resources: irq:17 memory:feb4b000-feb4b0ff
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
        *-multimedia:1
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
             resources: irq:16 memory:feb40000-feb43fff
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
        *-pci:1
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
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
             resources: irq:18 memory:feb4a000-feb4afff
        *-pci:2
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 74:2f:68:29:7c:f7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-43-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fea00000-fea0ffff
        *-pci:3
             description: PCI bridge
             product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: c8:60:00:bd:eb:2f
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:46 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:4
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fe900000-fe901fff
        *-pci:5
             description: PCI bridge
             product: SB900 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fe800000-fe8fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:fe800000-fe801fff
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
             resources: irq:18 memory:feb49000-feb49fff
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
             resources: irq:17 memory:feb48000-feb480ff
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
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
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 8
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SV300S3
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 580A
             serial: 50026B774B0A2B97
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00047d00
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: c6fad356-3e20-4f85-8aef-0a94d9a2aa64
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-01-07 08:52:26 filesystem=ext4 lastmountpoint=/ modified=2015-01-10 12:13:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-01-10 12:13:24 state=mounted
     *-scsi:1
          physical id: 9
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EZEX-08M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 01.0
             serial: WD-WCC3FFPZPJCN
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000b9acb
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/valeriancafe/e7b01b74-13a9-4d6f-a54d-d727928ba531
                version: 1.0
                serial: e7b01b74-13a9-4d6f-a54d-d727928ba531
                size: 923GiB
                capacity: 923GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-01-02 17:32:56 filesystem=ext4 lastmountpoint=/media/valeriancafe/e7b01b74-13a9-4d6f-a54d-d727928ba531 modified=2015-01-10 11:46:54 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2015-01-10 08:19:34 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                size: 7786MiB
                capacity: 7786MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 7786MiB
                   capabilities: nofs
     *-scsi:2
          physical id: a
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HDS72101
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: JP4O
             serial: JP9921HD3R0LSH
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=6d39f841-b516-db41-a4d3-f902b2e4e047 sectorsize=512
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/valeriancafe/more_backup
                version: 1.0
                serial: 97af5208-5ba5-4902-886a-aad9f3823f07
                size: 931GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-06 22:33:05 filesystem=ext4 label=more_backup lastmountpoint=/media/valeriancafe/more_backup modified=2015-01-10 12:13:44 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2015-01-10 12:13:44 state=mounted
     *-scsi:3
          physical id: b
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW AD-7200S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 102A
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by oldfred on 2015-01-10
Please use code tags for long text or terminal output.

Do not know if running the propritary AMD drive then interferes with nVidia driver.
>  configuration: driver=fglrx_pci latency=0



But I do know that installing more than the one correct nVidia drive causes major issues. You must totally uninstall/purge all nVidia drivers and install from repository the one for your card.
Repository does not have the very newest, but only if you have the very newest nVidia card should you need a driver that is not in repository.

       # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status
#Then for verson installed
sudo apt-cache policy nvidia-3XX-updates 

   sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

    
       nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

It looks like your 210 is one that now will be legacy and the newest you can install is 340.xx. Repositroy may not have that, but then just install newest available.

---


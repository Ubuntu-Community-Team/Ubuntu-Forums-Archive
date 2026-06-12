---
title: "Detecting Cardbus (ExpressCard) Bridge"
date: 2010-09-26
forum: Hardware
---

### Post by tangie on 2010-09-26
Hi

I'm about to purchase an ExpressCard adapter in order to add a steady FireWire functionality to my laptop, Toshiba A505 s6033 (HM55 chipset). It already has one FW port built-in, but this one doesn't work so good with my external audio interface, it's a known problem the only solution for which is to install another FW adapter with a proper chipset.

Now, prior to make an order I decided to make sure my CardBus is actually working. I tried to find it with lspci -nn, and with lshw, but none is shown :(. The laptop does have the slot and it should be working, but this was never tested. This laptop was purchased second-hand, so I don't really know what it's gone through before.

I was already intended to think CardBus doesn't function on this laptop, but then I looked for additional lspci reports from this laptop and found this thread:
[http://ubuntuforums.org/showthread.php?t=1520385](http://ubuntuforums.org/showthread.php?t=1520385)

It shows quite a similar results, so now I have no idea what to do next :confused:. Tried to check some pciids with a vague descprition like the HECI and also searched for "8086:3b42", but found nothing. Could it be that in HM55 chipset the CardBus bridge shows up as "PCI Express Root Port" or something similar? BTW I'm dualbooting with Win7, and the Device Manager didn't tell me anything about it neither... I don't have a card to plug in and check if it works...

Googling "cardbus lspci" prooves that CardBus Bridge does show up in lspci in some cases.

Thanks for any help!

lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
04:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
04:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
3f:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
3f:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
3f:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
3f:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
3f:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
3f:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
3f:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
3f:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
3f:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
3f:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
3f:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
```sudo lshw:
```
    description: Notebook
    product: Satellite A505
    vendor: TOSHIBA
    version: PSAT9U-006002
    serial: 1A241992Q
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=33A76080-0121-11DF-BBA9-00266C4130DE
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: 1.30 (04/14/2010)
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: HMT125S6BFR8C-G7
             physical id: 0
             serial: 2974CCDC
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: HMT125S6BFR8C-G7
             physical id: 1
             serial: 14C04814
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 24
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          slot: CPU
          size: 933MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 25
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 27
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 28
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 26
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:5000(size=4096) memory:d2000000-d30fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 310M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:d3080000-d30fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:d3000000-d3003fff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:db106100-db10610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:db105c00-db105fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:52 memory:db100000-db103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:4000(size=4096) memory:da100000-db0fffff ioport:d3100000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:26:6c:41:30:de
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:50 ioport:4000(size=256) memory:d3110000-d3110fff memory:d3100000-d310ffff memory:d3120000-d313ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:3000(size=4096) memory:d9100000-da0fffff ioport:d4100000(size=16777216)
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: 70:1a:04:d2:58:ad
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=10.0.0.5 latency=0 link=yes multicast=yes wireless=802.11bg
                resources: irq:17 ioport:3000(size=256) memory:d9100000-d9103fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:48 ioport:2000(size=4096) memory:d8100000-d90fffff ioport:d5100000(size=16777216)
           *-generic:0
                description: SD Host controller
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:d8100a00-d8100aff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d8100900-d81009ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d8100800-d81008ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:17 memory:d8100000-d81007ff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:49 ioport:1000(size=4096) memory:d7100000-d80fffff ioport:d6100000(size=16777216)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:db105800-db105bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:51 ioport:6048(size=8) ioport:6054(size=4) ioport:6040(size=8) ioport:6050(size=4) ioport:6020(size=32) memory:db105000-db1057ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: PB4O
                serial: 091207PBG400Q7CX3G8V
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=31ac024b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0e43-7ed1
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-03-03 18:55:00 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 9256a833-1a89-8b46-8904-800d837b9204
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-22 05:08:29 filesystem=ntfs state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 94680e73-ec84-a641-ad2d-f1af378200fe
                   size: 273GiB
                   capacity: 273GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-04-22 05:08:24 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 347MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 976MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 40GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633Y
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TF02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:db106000-db1060ff ioport:6000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:3f:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:3f:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:3f:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:3f:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:3f:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:3f:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:3f:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:3f:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:3f:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh

```

---

### Post by Fafler on 2010-09-26
Cardbus =! ExpressCard

Cardbus is based on PCI and needs a bridge in order to handle stuff like hotswapping and 16 bit cards.

ExpressCard is based on PCIe and has native hotswapping, and in turn, does not need a bridge to work.

---

### Post by tangie on 2010-09-26
Great, finally this whole thing makes sense! :P
That's probably a common misconception, because I've seen many sellers call their products "Cardbus", clearly meaning ExpressCard.

Another unrelated question: I'm thinking of making this machine a Hackintosh. It's said there are some models of Macs that have an ExpressCard slot. Should it be recognized by the system? If there is no bridge, any card inserted should be recognized as a PCIe device? (which are properly recognized in Hackintoshes, as far as I know) Sorry if this is a bit offtopic for the forum, asking just in case someone of the Pros here may have an idea.

---

### Post by Fafler on 2010-09-26
That is correct.

The Intel Macs are just like any other PC, except for the BIOS, and ExpressCards will work just fine.

---


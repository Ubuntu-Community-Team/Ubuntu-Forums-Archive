---
title: "Broken SD card reader"
date: 2014-03-27
forum: Hardware
---

### Post by Danimal411 on 2014-03-27
Ubuntu 13.10

You guys will get a kick out of this.  I really screwed it up.  If anyone can solve this one, kudos.  Here it is:

In the process of trying to fix a corrupted SD card, I deleted my SD card partition and thus, any ability to read future SD cards.  At the time, I thought I couldn't get my SD card to reformat, and got confused with the difference between sda(x) and sdb.  So in a fit of rage, I used a little "**s****udo rm -r /dev/sda5**".  I thought sda5 was the problem, for whatever reason, and it wouldn't go away.  So I deleted it.  Ha!  It gets worse.  As I'm rooting around in Gparted, I noticed an 8 GB (it was an 8 GB SD card) unknown partition in the SDA section.  "That's weird", I thought, foolishly, where did that come from?  Hm.  So I added it to the end of my Ubuntu partition.  More free space, right?  I don't know what the hell is going on.  Listen: it was late at night, and I was three beers deep.  Other people may have worse stories stemming from a similar situation, but those stories probably involve weapons and automobiles.  

Gparted can still see the SD card on sdb, but I'm unable to mount it.  Gparted is the only breath of life that I've seen from it.  

**sudo fdisk -l** = not there.  Everything else shows up.

I dual boot with Windows 7, so I went into Device Manager there, disabled and re-enabled all USB drivers, tried updating all drivers, all without result.  Yes, Windows 7 can't see it anymore either.

Thanks in advance.

---

### Post by Danimal411 on 2014-03-27
Scratch that.  I can't get gparted to see the card anymore, either.

---

### Post by Danimal411 on 2014-03-27
Here is the output of lspci -v -nn:

> 00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>


00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:0116]
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at dd000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at e000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915


00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at dfc0b000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei_me


00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at dfc08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci


00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1bc3]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at dfc00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: df200000-dfbfffff
	Prefetchable memory behind bridge: 00000000d2100000-00000000d2afffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport


00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: de800000-df1fffff
	Prefetchable memory behind bridge: 00000000d1600000-00000000d1ffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport


00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: dde00000-de7fffff
	Prefetchable memory behind bridge: 00000000d0b00000-00000000d14fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport


00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: dd400000-dddfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d09fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport


00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, medium devsel, latency 0, IRQ 4
	Memory at dfc07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci


00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: lpc_ich


00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at e0b0 [size=8]
	I/O ports at e0a0 [size=4]
	I/O ports at e090 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e060 [size=32]
	Memory at dfc06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci


00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1387]
	Flags: medium devsel, IRQ 11
	Memory at dfc05000 (64-bit, non-prefetchable) [size=256]
	I/O ports at e040 [size=32]


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at de800000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 40-25-c2-ff-ff-c1-d5-e8
	Kernel driver in use: iwlwifi


03:00.0 USB controller [0c03]: Fresco Logic FL1000G USB 3.0 Host Controller [1b73:1000] (rev 04) (prog-if 30 [XHCI])
	Subsystem: ASUSTeK Computer Inc. Device [1043:1039]
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at dde00000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [80] Express Endpoint, MSI 00
	Kernel driver in use: xhci_hcd


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at dd400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at a000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [180] Device Serial Number ff-52-66-6a-c8-60-00-ff
	Kernel driver in use: atl1c




---

### Post by Danimal411 on 2014-03-27
Here is the output of **lshw**:

>  description: Laptop    product: U46E (To be filled by O.E.M.)
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: C4N0AS065923140
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=laptop family=U sku=To be filled by O.E.M. uuid=00548E59-0D7E-E181-2B0B-C8600052666A
  *-core
       description: Motherboard
       product: U46E
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: NB-1234567890
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: U46E.206
          date: 10/07/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 3d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT351S6BFR8C-H9
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 00271C59
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT351S6BFR8C-H9
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 00971C58
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:42 memory:dfc0b000-dfc0b00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:11 memory:dfc08000-dfc083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:dfc00000-dfc03fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:11 ioport:d000(size=4096) memory:df200000-dfbfffff ioport:d2100000(size=10485760)
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:3 ioport:c000(size=4096) memory:de800000-df1fffff ioport:d1600000(size=10485760)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N + WiMAX 6150
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 67
                serial: 40:25:c2:c1:d5:e8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-18-generic firmware=41.28.5.1 build 33926 ip=192.168.72.80 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:43 memory:de800000-de801fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:10 ioport:b000(size=4096) memory:dde00000-de7fffff ioport:d0b00000(size=10485760)
           *-usb
                description: USB controller
                product: FL1000G USB 3.0 Host Controller
                vendor: Fresco Logic
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:10 memory:dde00000-dde0ffff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:3 ioport:a000(size=4096) memory:dd400000-dddfffff ioport:d0000000(size=10485760)
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: c0
                serial: c8:60:00:52:66:6a
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:dd400000-dd43ffff ioport:a000(size=128)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:4 memory:dfc07000-dfc073ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:e0b0(size=8) ioport:e0a0(size=4) ioport:e090(size=8) ioport:e080(size=4) ioport:e060(size=32) memory:dfc06000-dfc067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dfc05000-dfc050ff ioport:e040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK7559GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: GN00
             serial: 123KC0KCT
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=e3102a4b
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: 4c8b-2392
                size: 24GiB
                capacity: 25GiB
                capabilities: primary hidden fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 0651072a-3909-5541-8066-25895447e60e
                size: 394GiB
                capacity: 394GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-04-04 10:45:48 filesystem=ntfs label=OS state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 279GiB
                capacity: 279GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 279GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8A2ASW
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery:0
       description: Lithium Ion Battery
       product: MOLICEL
       vendor: E-One Moli Energy
       physical id: 1
       version: 10/31/2006
       serial: FSPK50074
       slot: Real 1
  *-battery:1
       description: Lithium Ion Battery
       product: MOLICEL
       vendor: E-One Moli Energy
       physical id: 2
       version: 10/31/2006
       serial: FSPK50074
       slot: Real 2
  *-battery:2
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 3
       version: 10/31/2006
       serial: Battery 0
       slot: Fake
  *-battery:3
       description: Nickel Cadmium Battery
       product: Battery Name
       vendor: Battery Manufacturer
       physical id: 4
       version: 01/01/2007
       serial: Serial Number
       slot: Location of the battery
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 5
       version: To Be Filled By O.E.M.
       serial: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Ethernet interface
       physical id: 6
       logical name: wmx0
       serial: 64:d4:da:6c:2c:a9
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no




---

### Post by Danimal411 on 2014-03-27
And finally, the output of **lsblk**:

> NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTsda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda1   8:1    0    25G  0 part 
&#9500;&#9472;sda2   8:2    0 394.1G  0 part 
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 279.5G  0 part /
sr0     11:0    1  1024M  0 rom  




---


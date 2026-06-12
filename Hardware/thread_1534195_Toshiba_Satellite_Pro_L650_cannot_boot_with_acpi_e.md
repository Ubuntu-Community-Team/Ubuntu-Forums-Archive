---
title: "Toshiba Satellite Pro L650: cannot boot with acpi enabled"
date: 2010-07-19
forum: Hardware
---

### Post by der_On on 2010-07-19
Hello,

I've just got my new laptop, a Toshiba Satellite Pro L650 and had several issues installing Ubuntu Studio 10.04 (AMD64).

The premier issue is that I had to turn acpi=off for the installation to work at all.
However If I enable it in the grub loader now, the laptop won't boot but freeze displaying mesages like "? acpi-init ...", wich I think say as much as acpi cannot be initialized on my machine.

Second issue was that my ethernet won't work. Only after manually installing a new kernel, and the manufacture driver i got it to work. But the wireless isn't working. I think it has something to do with acpi too.
Trying to manually install my wifi driver from the manufacturer showed me, that something with lib80211 crypting is wrong, as that stopped the installation.

I've read that the new lucid kernel 2.6.35-020635rc1-generic fixes acpi but with no luck.

Here my output of various commands:

```

# sudo lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
ondrej@anzui:~$ sudo lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d6000000-d60fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [88] Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at d6106100 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, medium devsel, latency 0, IRQ 7
    Memory at d6105c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at d6100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d5000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d4000000-d4ffffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=20, subordinate=22, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d3000000-d3ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d2ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at d6105800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [50] Subsystem: Toshiba America Info Systems Device [1179:ff1e]

00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 5048 [size=8]
    I/O ports at 5054 [size=4]
    I/O ports at 5040 [size=8]
    I/O ports at 5050 [size=4]
    I/O ports at 5020 [size=32]
    Memory at d6105000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA <?>
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: medium devsel, IRQ 9
    Memory at d6106000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d6104000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
    Subsystem: Toshiba America Info Systems Device [1179:fd12]
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d6000000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 4000 [size=256]
    Expansion ROM at d6040000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Kernel modules: radeon

01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
    Subsystem: Toshiba America Info Systems Device [1179:fd12]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at d6020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d5000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data <?>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
    Subsystem: Askey Computer Corp. Device [144f:7175]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00


``````

# sudo lshw
anzui                     
    description: Notebook
    product: Satellite Pro L650
    vendor: TOSHIBA
    version: PSK1KE-00K015GR
    serial: 5A693778Q
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=19D3F550-6883-11DF-80DB-00266C4EF190
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
          version: 1.40 (05/17/2010)
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: M471B5673FH0-CF8
             physical id: 0
             serial: 66807C1F
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: HMT351S6AFR8C-G7
             physical id: 1
             serial: 1AB3D461
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 24
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          slot: CPU
          size: 2262MHz
          capacity: 2266MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc up arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
        *-cache:0
             description: L3 cache
             physical id: 25
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
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
     *-pci
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:d6000000-d60fffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Redwood [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:d6000000-d601ffff ioport:4000(size=256) memory:d6040000-d605ffff
           *-multimedia
                description: Audio device
                product: Redwood HDMI Audio [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:24 memory:d6020000-d6023fff
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
             resources: memory:d6106100-d610610f
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
             resources: irq:7 memory:d6105c00-d6105fff
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
             resources: irq:23 memory:d6100000-d6103fff
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
             resources: irq:18 ioport:3000(size=4096) memory:d5000000-d5ffffff ioport:d0000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 00:26:6c:4e:f1:90
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.178.22 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:22 memory:d5000000-d503ffff ioport:3000(size=128)
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
             resources: irq:19 ioport:2000(size=4096) memory:d4000000-d4ffffff ioport:d1000000(size=16777216)
           *-network UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d4000000-d4003fff
        *-pci:3
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
             resources: irq:20 ioport:1000(size=4096) memory:d3000000-d3ffffff ioport:d2000000(size=16777216)
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
             resources: irq:11 memory:d6105800-d6105bff
        *-pci:4
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
             resources: irq:21 ioport:5048(size=8) ioport:5054(size=4) ioport:5040(size=8) ioport:5050(size=4) ioport:5020(size=32) memory:d6105000-d61057ff
           *-disk
                description: ATA Disk
                product: ST9500325AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 0002
                serial: 5VE7KA5M
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=20f50280
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 414352ba-b9ad-407b-ba63-b1bf8ce72ded
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-07-17 02:42:42 filesystem=ext4 label=System lastmountpoint=/&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'&#65533;&#65533;&#65533;&#65533; 0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-07-19 10:46:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-07-19 11:06:28 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 447GiB
                   capacity: 447GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 223GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /games
                      capacity: 139GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /vm
                      capacity: 65GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 18GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: BD-MLT UJ240ES
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.20
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
             resources: memory:d6106000-d61060ff ioport:5000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d6104000-d6104fff
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh

``````

# ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:26:6c:4e:f1:90  
          inet Adresse:192.168.178.22  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::226:6cff:fe4e:f190/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6134 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:4859416 (4.8 MB)  TX bytes:1125616 (1.1 MB)
          Interrupt:22 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:15088 (15.0 KB)  TX bytes:15088 (15.0 KB)

``````

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```I hope I've created this post in the correct subforum? Sorry but I'm absolutely new to the ubuntu community. I'm using ubuntu for about a year now.

---

### Post by dino99 on 2010-07-19
check into synaptic that: toshset, toshutils and fnfxd are installed

---

### Post by SebX86 on 2010-07-19
This will not solve your problem... Because you don't have ACPI,
you won't get the Fn keys. I'm not sure these tools work with the new Toshiba BIOSes. They were designed for the Toshiba BIOS not the
Phoenix.

I have a similar issue with a Satellite C650 laptop. Have you tried
a BIOS update to fix the ACPI issue ?

---

### Post by der_On on 2010-07-19
I've checked and seen that I missed some of the tools mentioned above.  Installed them now, but as mentioned nothing happens, as I cannot activate acpi without the machine freezing on boot.

> **SebX86 said:**
> This will not solve your problem... Because you don't have ACPI,
you won't get the Fn keys. I'm not sure these tools work with the new Toshiba BIOSes. They were designed for the Toshiba BIOS not the
Phoenix.

I have a similar issue with a Satellite C650 laptop. Have you tried
a BIOS update to fix the ACPI issue ?

I have looked on the toshiba website and only found windows-based BIOS update. I tried to start it with wine but it said that I have to run it as administrator. Any way of getting that update to work in linux?

---

### Post by der_On on 2010-07-19
Problem partly solved!

I now have at least solved part of the problem: The wireless network is working now and I got my ATI drivers to work.

The mistake was using the rc1 of the linux-kernel 2.6.35 and after that using the 2.6.32 generic kernel. Switching back to the 2.6.32 preempt made my NetworkManager re-appear (it was gone from the panel) and my wifi work. However my ethernet is now disabled for some reason, but at least it is not unclaimed. To be sure I've rebuild the broadcom hybrid wifi driver as written in there manual.

As the next step I've build the ATI packages for my kernel with success.

So every problem was related to the wrong kernel.

Slowly I'm getting to a working system again. *puh*

Hopefully the acpi support will come someday soon.

---

### Post by der_On on 2010-07-23
Well, almost there!

I've already got used to not working Fn keys and missing auto-shutdown of computer. However then I've run into another annoying problem. My audio was randomly becoming noise/creaky without a reason. 

So I've read here and there and ended up updating ALSA wich made the problem even worse. Now my audio becomes noisy by random and my headphone jack is not working anymore. I've tried to install the Realtek HD-Audio drivers, reinstalled all kinds of pulseaudio packages, but with no luck. As far as I did understand, the SDPIF-function is what makes my headphone-jack working and that this function is not working for me.
Even alsamixer does not allow me to set a volume to the SDPIF.

Any help is appreciated.

---

### Post by der_On on 2010-07-23
Hurray! Sound issue is solved now!

After a lot of reading and googling this thread helped me out: [http://ubuntuforums.org/showthread.php?t=1366524](http://ubuntuforums.org/showthread.php?t=1366524)

The thing to do is to install the drivers from linuxant: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)
Note that those drivers only apply to conexant sound cards as the one provided with the toshiba satellite pro L650.


So all I need now is to wait for a kernel that fixes the acpi issues and I'm set. :)

---

### Post by IcarusR on 2010-07-23
See this thread for ways to flash bios without windows, it's old but people are still using it & op updates it....

[http://ubuntuforums.org/showthread.php?t=318789]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by ralpyka on 2010-07-23
[http://ubuntuforums.org/showthread.php?p=9622930#post9622930](http://ubuntuforums.org/showthread.php?p=9622930#post9622930)
I had problems with the ACPI too, but Toshiba released a bios update, and now Ubuntu is working. So I think that you need to update the BIOS, if you want to use Ubuntu.

---


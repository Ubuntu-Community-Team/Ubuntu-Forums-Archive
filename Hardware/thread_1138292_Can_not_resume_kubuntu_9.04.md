---
title: "Can not resume kubuntu 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by bluevalley on 2009-04-26
Hi all,

My labtop can suspend/resume well on kubuntu 8.10.
Since begin upgraded to kubuntu 9.04: my laptop can't be resumed.
It takes me two days for seeking a solution, :(. 

- when being suspended it sleeps very well.
- when I turn it on, only a 'black monitor'. It seems no keyboard. 
The harddisk led is nearly off. Finally, I have to turn it off.

Could you help me to fix this error. How can I debug this error.
Thank you very much.

---

### Post by LinuxGuy1234 on 2009-04-26
> **bluevalley said:**
> Hi all,

My labtop can suspend/resume well on kubuntu 8.10.
Since begin upgraded to kubuntu 9.04: my laptop can't be resumed.
It takes me two days for seeking a solution, :(. 

- when being suspended it sleeps very well.
- when I turn it on, only a 'black monitor'. It seems no keyboard. 
The harddisk led is nearly off. Finally, I have to turn it off.

Could you help me to fix this error. How can I debug this error.
Thank you very much.

Something in the kernel must be wrong... Post your laptop specs here to route the error down...

---

### Post by bluevalley on 2009-04-26
I am using a Samsung R5100 notebook. The route of this error is at the point:  1. [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)  2. [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1345607.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1345607.html)  ...

---

### Post by bluevalley on 2009-04-28
:(, anyone else?

> lshw

  [html]*-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3019MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GeForce 9200M GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:21:63:44:9b:92
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci ip=10.22.15.12 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8055 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 13
                serial: 00:13:77:a9:53:38
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:84:65:08:8a:28
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/html]> dmesg 

[html][    0.000000] BIOS EBDA/lowmem at: 0009e400/0009e400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9bd000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9bd000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbfd65 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e400 (usable)
[    0.000000]  modified: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  modified: 00000000bf8a7000 - 00000000bf9bd000 (usable)
[    0.000000]  modified: 00000000bf9bd000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  modified: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfe00000 (ACPI data)
[    0.000000]  modified: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fef69d
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb369d
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fef69c to 00881000 - 00fb369c
[    0.000000] ACPI: RSDP 000F7250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BFDF8661, 006C (r1 SECCSD LH43STAR  6040000  LTP        0)
[    0.000000] ACPI: FACP BFDE8000, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BFDE9000, 6529 (r2 Intel  CANTIGA   6040000 INTL 20050624)
[    0.000000] ACPI: FACS BFD9EFC0, 0040
[    0.000000] ACPI: HPET BFDFED86, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFDFEDBE, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: APIC BFDFEDFA, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFDFEE62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC BFDFEE8A, 0176 (r1 SECCSD LH43STAR  6040000  LTP        0)
[    0.000000] ACPI: SSDT BFDE7000, 05F9 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFDE6000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFDE5000, 020F (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2185MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009e400 - 0000100000]    BIOS reserved ==> [000009e400 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb369d]      NEW RAMDISK ==> [0000881000 - 0000fb369d]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f72f0] 000f72f0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfd65
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9bd
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd65
[    0.000000] On node 0 totalpages: 785037
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4371 pages used for memmap
[    0.000000]   HighMem zone: 554478 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778898
[    0.000000] Kernel command line: root=UUID=7f148792-a4d2-493f-9a0d-083d2097ac3f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.118 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15714980 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3083316k/3143060k available (4126k kernel code, 55956k reserved, 2208k data, 532k init, 2235396k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.23 BogoMIPS (lpj=7980472)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018354] ACPI: Core revision 20080926
[    0.020660] ACPI: Checking initramfs for custom DSDT
[    0.319464] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.359160] CPU0: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.360001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.92 BogoMIPS (lpj=7979840)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.444360] CPU1: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.444376] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.448037] Brought up 2 CPUs
[    0.448040] Total of 2 processors activated (7980.15 BogoMIPS).
[    0.448093] CPU0 attaching sched-domain:
[    0.448095]  domain 0: span 0-1 level MC
[    0.448098]   groups: 0 1
[    0.448103] CPU1 attaching sched-domain:
[    0.448105]  domain 0: span 0-1 level MC
[    0.448108]   groups: 1 0
[    0.448175] net_namespace: 776 bytes
[    0.448175] Booting paravirtualized kernel on bare hardware
[    0.448323] Time:  9:22:20  Date: 06/04/92
[    0.448323] regulator: core version 0.5
[    0.448323] NET: Registered protocol family 16
[    0.448323] EISA bus registered
[    0.448323] ACPI: bus type pci registered
[    0.448323] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.448323] PCI: MCFG area at e0000000 reserved in E820
[    0.448323] PCI: Using MMCONFIG for extended config space
[    0.448323] PCI: Using configuration type 1 for base access
[    0.449137] ACPI: EC: Look up EC in DSDT
[    0.454679] ACPI: BIOS _OSI(Linux) query ignored
[    0.456259] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.457213] ACPI: Interpreter enabled
[    0.457213] ACPI: (supports S0 S3 S4 S5)
[    0.457213] ACPI: Using IOAPIC for interrupt routing
[    0.462425] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.462425] ACPI: EC: driver started in interrupt mode
[    0.462425] ACPI: No dock devices found.
[    0.462425] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.462425] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.462425] pci 0000:00:01.0: PME# disabled
[    0.462425] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.462425] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.462425] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.462425] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf6204800-0xf6204bff]
[    0.462425] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.462425] pci 0000:00:1a.7: PME# disabled
[    0.462425] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf6200000-0xf6203fff]
[    0.462425] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.462425] pci 0000:00:1b.0: PME# disabled
[    0.464018] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.464023] pci 0000:00:1c.0: PME# disabled
[    0.464089] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.464094] pci 0000:00:1c.2: PME# disabled
[    0.464159] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.464164] pci 0000:00:1c.3: PME# disabled
[    0.464238] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.464319] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.464400] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.464482] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf6204c00-0xf6204fff]
[    0.464526] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.464530] pci 0000:00:1d.7: PME# disabled
[    0.464743] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.464750] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.464757] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.464765] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.464772] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.464779] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf6204000-0xf62047ff]
[    0.464799] pci 0000:00:1f.2: PME# supported from D3hot
[    0.464804] pci 0000:00:1f.2: PME# disabled
[    0.464842] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.464861] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.464948] pci 0000:01:00.0: reg 10 32bit mmio: [0xce000000-0xceffffff]
[    0.464965] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.464982] pci 0000:01:00.0: reg 1c 64bit mmio: [0xcc000000-0xcdffffff]
[    0.464991] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.465001] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.465083] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.465086] pci 0000:00:01.0: bridge 32bit mmio: [0xcc000000-0xceffffff]
[    0.465092] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.465159] pci 0000:02:00.0: reg 10 64bit mmio: [0xf3000000-0xf300ffff]
[    0.465214] pci 0000:02:00.0: PME# supported from D3hot
[    0.465219] pci 0000:02:00.0: PME# disabled
[    0.465291] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.465296] pci 0000:00:1c.0: bridge 32bit mmio: [0xf3000000-0xf3ffffff]
[    0.465303] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf0ffffff]
[    0.465359] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.465364] pci 0000:00:1c.2: bridge 32bit mmio: [0xf4000000-0xf4ffffff]
[    0.465372] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf1000000-0xf1ffffff]
[    0.465812] pci 0000:06:00.0: reg 10 64bit mmio: [0xf5000000-0xf5003fff]
[    0.465866] pci 0000:06:00.0: reg 18 io port: [0x5000-0x50ff]
[    0.466071] pci 0000:06:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.466143] pci 0000:06:00.0: supports D1 D2
[    0.466145] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.466168] pci 0000:06:00.0: PME# disabled
[    0.466291] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.466296] pci 0000:00:1c.3: bridge 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.466304] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf2000000-0xf2ffffff]
[    0.466363] pci 0000:00:1e.0: transparent bridge
[    0.466403] bus 00 -> node 0
[    0.466412] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.466741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.466911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.467048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.467180] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.478090] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.478212] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.478332] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    0.478450] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[    0.478568] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[    0.478688] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    0.478806] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.478923] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[    0.479035] ACPI: Power Resource [FN00] (off)
[    0.479082] ACPI: Power Resource [FN01] (off)
[    0.479274] ACPI: WMI: Mapper loaded
[    0.479312] SCSI subsystem initialized
[    0.479312] libata version 3.00 loaded.
[    0.479312] usbcore: registered new interface driver usbfs
[    0.479312] usbcore: registered new interface driver hub
[    0.479312] usbcore: registered new device driver usb
[    0.480042] PCI: Using ACPI for IRQ routing
[    0.484011] Bluetooth: Core ver 2.13
[    0.484016] NET: Registered protocol family 31
[    0.484016] Bluetooth: HCI device and connection manager initialized
[    0.484016] Bluetooth: HCI socket layer initialized
[    0.484018] NET: Registered protocol family 8
[    0.484020] NET: Registered protocol family 20
[    0.484034] NetLabel: Initializing
[    0.484036] NetLabel:  domain hash size = 128
[    0.484037] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484050] NetLabel:  unlabeled traffic allowed by default
[    0.484065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.484070] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.488075] AppArmor: AppArmor Filesystem Enabled
[    0.492416] pnp: PnP ACPI init
[    0.492426] ACPI: bus type pnp registered
[    0.493697] pnp 00:05: io resource (0x5000-0x500f) overlaps 0000:00:1c.3 BAR 7 (0x5000-0x5fff), disabling
[    0.493721] pnp 00:05: io resource (0x5000-0x500f) overlaps 0000:06:00.0 BAR 2 (0x5000-0x50ff), disabling
[    0.494937] pnp: PnP ACPI: found 11 devices
[    0.494940] ACPI: ACPI bus type pnp unregistered
[    0.494944] PnPBIOS: Disabled by ACPI PNP
[    0.494956] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.494963] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.494966] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.494968] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.494971] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.494973] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.494976] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.494978] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.494981] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.494983] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.494989] system 00:06: ioport range 0x6a0-0x6af has been reserved
[    0.494991] system 00:06: ioport range 0x6b0-0x6ff has been reserved
[    0.494998] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.495000] system 00:0a: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.495003] system 00:0a: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.495006] system 00:0a: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.495008] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.495011] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.495013] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.495016] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.500416] Switched to high resolution mode on CPU 1
[    0.504003] Switched to high resolution mode on CPU 0
[    0.529729] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.529732] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.529735] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.529739] pci 0000:00:01.0:   MEM window: 0xcc000000-0xceffffff
[    0.529742] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.529748] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.529751] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.529758] pci 0000:00:1c.0:   MEM window: 0xf3000000-0xf3ffffff
[    0.529762] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f0ffffff
[    0.529770] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.529773] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.529779] pci 0000:00:1c.2:   MEM window: 0xf4000000-0xf4ffffff
[    0.529784] pci 0000:00:1c.2:   PREFETCH window: 0x000000f1000000-0x000000f1ffffff
[    0.529792] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.529796] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.529801] pci 0000:00:1c.3:   MEM window: 0xf5000000-0xf5ffffff
[    0.529806] pci 0000:00:1c.3:   PREFETCH window: 0x000000f2000000-0x000000f2ffffff
[    0.529814] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.529816] pci 0000:00:1e.0:   IO window: disabled
[    0.529821] pci 0000:00:1e.0:   MEM window: disabled
[    0.529826] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.529841] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.529845] pci 0000:00:01.0: setting latency timer to 64
[    0.529854] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.529859] pci 0000:00:1c.0: setting latency timer to 64
[    0.529868] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.529873] pci 0000:00:1c.2: setting latency timer to 64
[    0.529881] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.529886] pci 0000:00:1c.3: setting latency timer to 64
[    0.529894] pci 0000:00:1e.0: setting latency timer to 64
[    0.529898] bus: 00 index 0 io port: [0x00-0xffff]
[    0.529900] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.529902] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.529904] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]
[    0.529906] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.529908] bus: 01 index 3 mmio: [0x0-0x0]
[    0.529910] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.529912] bus: 02 index 1 mmio: [0xf3000000-0xf3ffffff]
[    0.529914] bus: 02 index 2 mmio: [0xf0000000-0xf0ffffff]
[    0.529916] bus: 02 index 3 mmio: [0x0-0x0]
[    0.529918] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.529919] bus: 04 index 1 mmio: [0xf4000000-0xf4ffffff]
[    0.529921] bus: 04 index 2 mmio: [0xf1000000-0xf1ffffff]
[    0.529923] bus: 04 index 3 mmio: [0x0-0x0]
[    0.529925] bus: 06 index 0 io port: [0x5000-0x5fff]
[    0.529927] bus: 06 index 1 mmio: [0xf5000000-0xf5ffffff]
[    0.529929] bus: 06 index 2 mmio: [0xf2000000-0xf2ffffff]
[    0.529931] bus: 06 index 3 mmio: [0x0-0x0]
[    0.529933] bus: 08 index 0 mmio: [0x0-0x0]
[    0.529934] bus: 08 index 1 mmio: [0x0-0x0]
[    0.529936] bus: 08 index 2 mmio: [0x0-0x0]
[    0.529938] bus: 08 index 3 io port: [0x00-0xffff]
[    0.529940] bus: 08 index 4 mmio: [0x000000-0xffffffff]
[    0.529949] NET: Registered protocol family 2
[    0.544051] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.544298] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.544703] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.545019] TCP: Hash tables configured (established 131072 bind 65536)
[    0.545021] TCP reno registered
[    0.552098] NET: Registered protocol family 1
[    0.552224] checking if image is initramfs... it is
[    1.154608] Freeing initrd memory: 7369k freed
[    1.154647] Simple Boot Flag at 0x37 set to 0x1
[    1.154813] cpufreq: No nForce2 chipset.
[    1.154942] audit: initializing netlink socket (disabled)
[    1.154958] type=2000 audit(3863409741.153:1): initialized
[    1.161996] highmem bounce pool size: 64 pages
[    1.162001] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.163275] VFS: Disk quotas dquot_6.5.1
[    1.163333] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.163912] fuse init (API version 7.10)
[    1.163994] msgmni has been set to 1672
[    1.164161] alg: No test for stdrng (krng)
[    1.164173] io scheduler noop registered
[    1.164175] io scheduler anticipatory registered
[    1.164177] io scheduler deadline registered
[    1.164192] io scheduler cfq registered (default)
[    1.164374] pci 0000:01:00.0: Boot video device
[    1.166753] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.166794] pcieport-driver 0000:00:01.0: found MSI capability
[    1.166820] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.166831] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.166846] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.166858] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.166912] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.166958] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.166989] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.167003] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.167016] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.167027] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.167096] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.167141] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.167172] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.167186] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.167198] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.167213] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.167285] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.167331] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.167361] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.167376] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.167388] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.167400] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.167477] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.167600] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.167924] ACPI: AC Adapter [ADP1] (on-line)
[    1.173132] ACPI: Battery Slot [BAT1] (battery present)
[    1.173206] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.173209] ACPI: Power Button (FF) [PWRF]
[    1.173261] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.173309] ACPI: Lid Switch [LID0]
[    1.173353] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.173361] ACPI: Power Button (CM) [PWRB]
[    1.173400] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.173403] ACPI: Sleep Button (CM) [SLPB]
[    1.173527] fan PNP0C0B:00: registered as cooling_device0
[    1.173532] ACPI: Fan [FAN0] (off)
[    1.173628] fan PNP0C0B:01: registered as cooling_device1
[    1.173633] ACPI: Fan [FAN1] (off)
[    1.174331] ACPI: SSDT BFD1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.174757] ACPI: SSDT BFD18720, 065B (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.177122] Monitor-Mwait will be used to enter C-1 state
[    1.177126] Monitor-Mwait will be used to enter C-2 state
[    1.177139] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.177158] processor ACPI_CPU:00: registered as cooling_device2
[    1.177162] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.177589] ACPI: SSDT BFD19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.178019] ACPI: SSDT BFD19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.179310] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.179329] processor ACPI_CPU:01: registered as cooling_device3
[    1.179367] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.183637] thermal LNXTHERM:01: registered as thermal_zone0
[    1.184195] ACPI: Thermal Zone [TZ00] (56 C)
[    1.184831] thermal LNXTHERM:02: registered as thermal_zone1
[    1.185418] ACPI: Thermal Zone [TZ01] (56 C)
[    1.185470] isapnp: Scanning for PnP cards...
[    1.540813] isapnp: No Plug & Play device found
[    1.553247] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.554242] brd: module loaded
[    1.554544] loop: module loaded
[    1.554608] Fixed MDIO Bus: probed
[    1.554613] PPP generic driver version 2.4.2
[    1.554667] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.554697] Driver 'sd' needs updating - please use bus_type methods
[    1.554706] Driver 'sr' needs updating - please use bus_type methods
[    1.554745] ahci 0000:00:1f.2: version 3.0
[    1.554759] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.554802] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.554885] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.554888] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    1.554893] ahci 0000:00:1f.2: setting latency timer to 64
[    1.555199] scsi0 : ahci
[    1.555305] scsi1 : ahci
[    1.555360] scsi2 : ahci
[    1.555417] scsi3 : ahci
[    1.555472] scsi4 : ahci
[    1.555524] scsi5 : ahci
[    1.555570] ata1: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204100 irq 2299
[    1.555574] ata2: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204180 irq 2299
[    1.555576] ata3: DUMMY
[    1.555577] ata4: DUMMY
[    1.555580] ata5: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204300 irq 2299
[    1.555583] ata6: SATA max UDMA/133 abar m2048@0xf6204000 port 0xf6204380 irq 2299
[    1.872018] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.877486] ata1.00: ATA-8: SAMSUNG HM320JI, 2SS00_01, max UDMA7
[    1.877489] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.884724] ata1.00: configured for UDMA/133
[    2.220018] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.220944] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, SC03, max UDMA/100, ATAPI AN
[    2.220958] ata2.00: applying bridge limits
[    2.222381] ata2.00: configured for UDMA/100
[    2.556017] ata5: SATA link down (SStatus 0 SControl 300)
[    2.892014] ata6: SATA link down (SStatus 0 SControl 300)
[    2.908110] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM320JI  2SS0 PQ: 0 ANSI: 5
[    2.908202] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.908218] sd 0:0:0:0: [sda] Write Protect is off
[    2.908220] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.908244] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.908320] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.908334] sd 0:0:0:0: [sda] Write Protect is off
[    2.908336] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.908359] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.908362]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.985140] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.985186] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.987389] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  SC03 PQ: 0 ANSI: 5
[    2.992734] sr0: scsi3-mmc drive: 16x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.992737] Uniform CD-ROM driver Revision: 3.20
[    2.992831] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.992869] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.993534] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.993556] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.993578] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.993581] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.993638] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.997563] ehci_hcd 0000:00:1a.7: debug port 1
[    2.997569] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.997588] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf6204800
[    3.012008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.012069] usb usb1: configuration #1 chosen from 1 choice
[    3.012095] hub 1-0:1.0: USB hub found
[    3.012103] hub 1-0:1.0: 6 ports detected
[    3.012212] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.012223] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.012226] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.012267] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.016180] ehci_hcd 0000:00:1d.7: debug port 1
[    3.016187] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.016200] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf6204c00
[    3.032008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.032063] usb usb2: configuration #1 chosen from 1 choice
[    3.032089] hub 2-0:1.0: USB hub found
[    3.032095] hub 2-0:1.0: 6 ports detected
[    3.032193] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.032210] uhci_hcd: USB Universal Host Controller Interface driver
[    3.032237] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.032244] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.032247] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.032286] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.032320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.032396] usb usb3: configuration #1 chosen from 1 choice
[    3.032420] hub 3-0:1.0: USB hub found
[    3.032426] hub 3-0:1.0: 2 ports detected
[    3.032509] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.032515] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.032518] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.032560] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.032592] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    3.032660] usb usb4: configuration #1 chosen from 1 choice
[    3.032683] hub 4-0:1.0: USB hub found
[    3.032689] hub 4-0:1.0: 2 ports detected
[    3.032774] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.032781] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.032784] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.032822] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.032847] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    3.032914] usb usb5: configuration #1 chosen from 1 choice
[    3.032937] hub 5-0:1.0: USB hub found
[    3.032943] hub 5-0:1.0: 2 ports detected
[    3.033022] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.033029] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.033032] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.033073] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.033098] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    3.033164] usb usb6: configuration #1 chosen from 1 choice
[    3.033187] hub 6-0:1.0: USB hub found
[    3.033193] hub 6-0:1.0: 2 ports detected
[    3.033276] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.033282] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.033285] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.033331] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.033356] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.033423] usb usb7: configuration #1 chosen from 1 choice
[    3.033446] hub 7-0:1.0: USB hub found
[    3.033452] hub 7-0:1.0: 2 ports detected
[    3.033532] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.033538] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.033541] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.033580] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.033615] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.033689] usb usb8: configuration #1 chosen from 1 choice
[    3.033712] hub 8-0:1.0: USB hub found
[    3.033718] hub 8-0:1.0: 2 ports detected
[    3.033843] usbcore: registered new interface driver libusual
[    3.033874] usbcore: registered new interface driver usbserial
[    3.033884] USB Serial support registered for generic
[    3.033900] usbcore: registered new interface driver usbserial_generic
[    3.033902] usbserial: USB Serial Driver core
[    3.033950] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.036498] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.037650] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.037655] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.037657] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.037660] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.037662] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.044036] mice: PS/2 mouse device common for all mice
[    3.064104] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.064132] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.064197] device-mapper: uevent: version 1.0.3
[    3.064298] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.064365] device-mapper: multipath: version 1.0.5 loaded
[    3.064367] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.064447] EISA: Probing bus 0 at eisa.0
[    3.064453] Cannot allocate resource for EISA slot 1
[    3.064456] Cannot allocate resource for EISA slot 2
[    3.064458] Cannot allocate resource for EISA slot 3
[    3.064460] Cannot allocate resource for EISA slot 4
[    3.064463] Cannot allocate resource for EISA slot 5
[    3.064475] EISA: Detected 0 cards.
[    3.064575] cpuidle: using governor ladder
[    3.064663] cpuidle: using governor menu
[    3.065159] TCP cubic registered
[    3.065255] NET: Registered protocol family 10
[    3.065659] lo: Disabled Privacy Extensions
[    3.065984] NET: Registered protocol family 17
[    3.066001] Bluetooth: L2CAP ver 2.11
[    3.066002] Bluetooth: L2CAP socket layer initialized
[    3.066005] Bluetooth: SCO (Voice Link) ver 0.6
[    3.066007] Bluetooth: SCO socket layer initialized
[    3.066040] Marking TSC unstable due to TSC halts in idle
[    3.066042] Bluetooth: RFCOMM socket layer initialized
[    3.066050] Bluetooth: RFCOMM TTY layer initialized
[    3.066051] Bluetooth: RFCOMM ver 1.10
[    3.066752] Using IPI No-Shortcut mode
[    3.066849] registered taskstats version 1
[    3.066957]   Magic number: 0:81:373
[    3.066959]   hash matches /build/buildd/linux-2.6.28/drivers/base/power/main.c:390
[    3.067036] rtc_cmos 00:07: setting system clock to 1992-06-04 09:22:23 UTC (707649743)
[    3.067038] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.067040] EDD information not available.
[    3.067330] Freeing unused kernel memory: 532k freed
[    3.067456] Write protecting the kernel text: 4128k
[    3.067501] Write protecting the kernel read-only data: 1532k
[    3.090667] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.320246] sky2 driver version 1.22
[    3.320333] sky2 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.320362] sky2 0000:06:00.0: setting latency timer to 64
[    3.320475] sky2 0000:06:00.0: Yukon-2 EC Ultra chip revision 3
[    3.353678] sky2 0000:06:00.0: Marvell Yukon 88E8055 Gigabit Ethernet Controller
[    3.353681]  Part Number: Yukon 88E8055
[    3.353683]  Engineering Level: Rev. 1.3
[    3.353685]  Manufacturer: Marvell
[    3.354098] sky2 0000:06:00.0: irq 2298 for MSI/MSI-X
[    3.358602] sky2 eth0: addr 00:13:77:a9:53:38
[    3.428125] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    3.704576] usb 1-3: configuration #1 chosen from 1 choice
[    3.941852] PM: Starting manual resume from disk
[    3.941855] PM: Resume from partition 8:6
[    3.941857] PM: Checking hibernation image.
[    3.942073] PM: Resume from disk failed.
[    3.945024] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.945363] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.945366] EXT3-fs: write access will be enabled during recovery.
[    4.204703] usb 3-1: configuration #1 chosen from 1 choice
[    4.212388] usbcore: registered new interface driver hiddev
[    4.225590] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input6
[    4.226088] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
[    4.226106] usbcore: registered new interface driver usbhid
[    4.226109] usbhid: v2.6:USB HID core driver
[    4.312971] kjournald starting.  Commit interval 5 seconds
[    4.312984] EXT3-fs: recovery complete.
[    4.334023] EXT3-fs: mounted filesystem with ordered data mode.
[   11.857614] udev: starting version 141
[   12.061092] cfg80211: Calling CRDA to update world regulatory domain
[   12.246104] iTCO_vendor_support: vendor-support=0
[   12.313502] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.313771] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   12.313936] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.442822] cfg80211: World regulatory domain updated:
[   12.442826]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.442829]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.442831]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.442833]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.442836]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.442838]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.460047] Linux agpgart interface v0.103
[   12.546275] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.805997] acpi device:04: registered as cooling_device4
[   12.806187] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input8
[   12.812086] ACPI: Video Device [NVID] (multi-head: yes  rom: no  post: no)
[   13.154105] Linux video capture interface: v2.00
[   13.169278] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.424854] uvcvideo: Found UVC 1.00 device Vega USB 2.0 Camera. (0ac8:c302)
[   13.426298] input: Vega USB 2.0 Camera. as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input9
[   13.429124] usbcore: registered new interface driver uvcvideo
[   13.429148] USB Video Class driver (v0.1.0)
[   13.507156] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.507170] ath5k_pci 0000:02:00.0: setting latency timer to 64
[   13.507264] ath5k_pci 0000:02:00.0: registered as 'phy0'
[   13.548221] phy0: Selected rate control algorithm 'pid'
[   13.686815] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   13.687515] ath_hal: module license 'Proprietary' taints kernel.
[   13.688731] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.699197] wlan: 0.9.4
[   13.704868] ath_pci: 0.9.4
[   13.709715] udev: renamed network interface wlan0 to wlan1
[   13.723966] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.724047] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.753883] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   13.979644] lp: driver loaded but no devices found
[   14.019390] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1c0b1, caps: 0xa04711/0xa00000
[   14.055447] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   14.060536] Adding 3180828k swap on /dev/sda6.  Priority:-1 extents:1 across:3180828k
[   14.598842] EXT3 FS on sda5, internal journal
[   15.536125] type=1505 audit(707642555.965:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2156
[   15.536246] type=1505 audit(707642555.965:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2156
[   15.536287] type=1505 audit(707642555.965:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2156
[   15.536328] type=1505 audit(707642555.965:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2156
[   15.680712] type=1505 audit(707642556.109:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2161
[   15.680889] type=1505 audit(707642556.109:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2161
[   15.739478] type=1505 audit(707642556.168:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2165
[   20.446928] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.446932] vboxdrv: Successfully done.
[   20.446934] vboxdrv: Found 2 processor cores.
[   20.448023] vboxdrv: fAsync=0 offMin=0x1b0 offMax=0x1b90
[   20.448076] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.448078] vboxdrv: Successfully loaded version 2.2.0 (interface 0x000a0009).
[   21.573867] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.573870] Bluetooth: BNEP filters: protocol multicast
[   21.592266] Bridge firewalling registered
[   22.615755] ppdev: user-space parallel port driver
[   26.570182] sky2 eth0: enabling interface
[   26.570410] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.600486] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   28.503777] wlan1: authenticate with AP 00:b0:0c:02:80:e3
[   28.505412] wlan1: authenticated
[   28.505416] wlan1: associate with AP 00:b0:0c:02:80:e3
[   28.507666] wlan1: RX AssocResp from 00:b0:0c:02:80:e3 (capab=0x401 status=0 aid=8)
[   28.507668] wlan1: associated
[   28.507928] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   28.508049] wlan1: disassociating by local choice (reason=3)
[   39.329021] wlan1: no IPv6 routers present
[   57.192150] wlan1: authenticate with AP 00:12:da:94:80:80
[   57.196000] wlan1: authenticated
[   57.196005] wlan1: associate with AP 00:12:da:94:80:80
[   57.200694] wlan1: RX AssocResp from 00:12:da:94:80:80 (capab=0x421 status=0 aid=22)
[   57.200697] wlan1: associated
[/html]> /etc/default/acpi-support

[html]SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=false

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
#RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
#DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
[/html]> /var/lib/pm-utils/stress.log

[html]
*** no primary user (via sudo) dbus tests skipped ...
v---
Waiting for suspend to complete 29 to go ...
Waiting for suspend to complete 28 to go ...
> [  122.293034] sky2 eth0: disabling interface
Waiting for suspend to complete 27 to go ...
> [  122.544058] wlan1: disassociating by local choice (reason=3)
> [  122.584982] wlan1: authenticate with AP 00:12:da:9e:1e:00
> [  122.586096] wlan1: authenticated
> [  122.586103] wlan1: associate with AP 00:12:da:9e:1e:00
> [  122.587927] wlan1: RX AssocResp from 00:12:da:9e:1e:00 (capab=0x421 status=0 aid=116)
> [  122.587932] wlan1: associated
> [  122.593283] wlan1: disassociating by local choice (reason=3)
> [  122.594376] wlan1: deauthenticated
Waiting for suspend to complete 26 to go ...
Waiting for suspend to complete 25 to go ...
Waiting for suspend to complete 24 to go ...
> [  125.737608] PM: Syncing filesystems ... done.
> [  125.742332] PM: Preparing system for mem sleep
> [  125.742337] Freezing user space processes ... (elapsed 0.00 seconds) done.
> [  125.742954] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
> [  125.742993] PM: Entering mem sleep
> [  125.743007] Suspending console(s) (use no_console_suspend to debug)
> [  126.320930] sd 0:0:0:0: [sda] Synchronizing SCSI cache
> [  126.321031] sd 0:0:0:0: [sda] Stopping disk
> [  126.810256] ACPI handle has no context!
> [  126.824339] ath5k_pci 0000:02:00.0: PCI INT A disabled
> [  126.920759] ehci_hcd 0000:00:1d.7: PCI INT A disabled
> [  126.936339] uhci_hcd 0000:00:1d.2: PCI INT C disabled
> [  126.936586] uhci_hcd 0000:00:1d.1: PCI INT B disabled
> [  126.936830] uhci_hcd 0000:00:1d.0: PCI INT A disabled
> [  126.968113] HDA Intel 0000:00:1b.0: PCI INT A disabled
> [  126.984413] ehci_hcd 0000:00:1a.7: PCI INT C disabled
> [  127.000322] uhci_hcd 0000:00:1a.2: PCI INT C disabled
> [  127.000567] uhci_hcd 0000:00:1a.1: PCI INT B disabled
> [  127.000812] uhci_hcd 0000:00:1a.0: PCI INT A disabled
> [  127.001209] PM: suspend devices took 1.260 seconds
> [  127.001335] ACPI: Preparing to enter system sleep state S3
> [  127.003935] Disabling non-boot CPUs ...
> [  127.006544] NOHZ: local_softirq_pending 100
> [  127.104079] CPU 1 is now offline
> [  127.104082] SMP alternatives: switching to UP code
> [  127.223054] CPU0 attaching NULL sched-domain.
> [  127.223057] CPU1 attaching NULL sched-domain.
> [  127.223340] CPU0 attaching NULL sched-domain.
> [  127.223495] CPU1 is down
> [  127.223642] Extended CMOS year: 2000
> [  127.223642] Back to C!
> [  127.223642] Extended CMOS year: 2000
> [  127.223642] Enabling non-boot CPUs ...
> [  127.223642] SMP alternatives: switching to SMP code
> [  127.343154] Booting processor 1 APIC 0x1 ip 0x6000
> [  127.222923] Initializing CPU#1
> [  127.222923] Calibrating delay using timer specific routine.. 3992.06 BogoMIPS (lpj=7984138)
> [  127.222923] CPU: L1 I cache: 32K, L1 D cache: 32K
> [  127.222923] CPU: L2 cache: 1024K
> [  127.222923] CPU: Physical Processor ID: 0
> [  127.222923] CPU: Processor Core ID: 1
> [  127.432363] CPU1: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
> [  127.432419] CPU0 attaching NULL sched-domain.
> [  127.432955] CPU0 attaching sched-domain:
> [  127.432958]  domain 0: span 0-1 level MC
> [  127.432960]   groups: 0 1
> [  127.432964] CPU1 attaching sched-domain:
> [  127.432965]  domain 0: span 0-1 level MC
> [  127.432967]   groups: 1 0
> [  127.436018] Switched to high resolution mode on CPU 1
> [  127.436030] CPU1 is up
> [  127.436032] ACPI: Waking up from system sleep state S3
> [  127.639276] ACPI: EC: non-query interrupt received, switching to interrupt mode
> [  127.645544] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0x20002020, writing 0x2020)
> [  127.645548] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x100, writing 0x10100)
> [  127.645554] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
> [  127.645558] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
> [  127.645582] pcieport-driver 0000:00:01.0: setting latency timer to 64
> [  127.645595] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
> [  127.645599] uhci_hcd 0000:00:1a.0: setting latency timer to 64
> [  127.645659] usb usb3: root hub lost power or was reset
> [  127.645689] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
> [  127.645694] uhci_hcd 0000:00:1a.1: setting latency timer to 64
> [  127.645752] usb usb4: root hub lost power or was reset
> [  127.645770] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
> [  127.645775] uhci_hcd 0000:00:1a.2: setting latency timer to 64
> [  127.645833] usb usb5: root hub lost power or was reset
> [  127.660019] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
> [  127.660024] ehci_hcd 0000:00:1a.7: setting latency timer to 64
> [  127.676032] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
> [  127.676053] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  127.676059] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
> [  127.676078] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
> [  127.676084] HDA Intel 0000:00:1b.0: setting latency timer to 64
> [  127.767627] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
> [  127.767649] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf0f1f001)
> [  127.767657] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf3f0f300)
> [  127.767662] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
> [  127.767677] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  127.767686] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  127.767749] pcieport-driver 0000:00:1c.0: setting latency timer to 64
> [  127.767773] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x40305)
> [  127.767790] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f101)
> [  127.767799] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
> [  127.767813] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  127.767823] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  127.767882] pcieport-driver 0000:00:1c.2: setting latency timer to 64
> [  127.767909] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x40405)
> [  127.767930] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf2f1f201)
> [  127.767941] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
> [  127.767954] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  127.767964] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  127.768042] pcieport-driver 0000:00:1c.3: setting latency timer to 64
> [  127.768052] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
> [  127.768059] uhci_hcd 0000:00:1d.0: setting latency timer to 64
> [  127.768142] usb usb6: root hub lost power or was reset
> [  127.768161] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
> [  127.768168] uhci_hcd 0000:00:1d.1: setting latency timer to 64
> [  127.768252] usb usb7: root hub lost power or was reset
> [  127.768271] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
> [  127.768277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
> [  127.768361] usb usb8: root hub lost power or was reset
> [  127.784023] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
> [  127.784028] ehci_hcd 0000:00:1d.7: setting latency timer to 64
> [  127.784092] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
> [  127.784104] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
> [  127.784109] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
> [  127.784113] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
> [  127.784125] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  127.784140] pci 0000:00:1e.0: setting latency timer to 64
> [  127.800035] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
> [  127.800057] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
> [  127.800095] ahci 0000:00:1f.2: setting latency timer to 64
> [  127.800224] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xc2000004)
> [  127.800333] pci 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
> [  127.800391] pci 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
> [  127.800417] pci 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xcc000004)
> [  127.800442] pci 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xd000000c)
> [  127.800460] pci 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xce000000)
> [  127.800477] pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  127.800503] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  127.800611] ath5k_pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
> [  127.800636] ath5k_pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf3000004)
> [  127.800642] ath5k_pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  127.800650] ath5k_pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  127.816032] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
> [  127.832196] sky2 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
> [  127.832323] sky2 0000:06:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x5001)
> [  127.832372] sky2 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf5000004)
> [  127.832400] sky2 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  127.832450] sky2 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  127.833147] sd 0:0:0:0: [sda] Starting disk
> [  128.000033] Clocksource tsc unstable (delta = -500021623 ns)
> [  128.120033] ata5: SATA link down (SStatus 0 SControl 300)
> [  128.120052] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
> [  128.120071] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
> [  128.120087] ata6: SATA link down (SStatus 0 SControl 300)
> [  128.132775] ata1.00: configured for UDMA/133
> [  128.148064] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
> [  128.148081] sd 0:0:0:0: [sda] Write Protect is off
> [  128.148083] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
> [  128.148107] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
> [  128.351080] ata2.00: configured for UDMA/100
> [  128.840021] usb 1-3: reset high speed USB device using ehci_hcd and address 3
> [  129.284049] usb 3-1: reset low speed USB device using uhci_hcd and address 2
> [  129.594884] PM: resume devices took 1.956 seconds
> [  129.595062] PM: Finishing wakeup.
> [  129.595064] Restarting tasks ... 
^---
v---
Waiting for suspend to complete 29 to go ...
Waiting for suspend to complete 28 to go ...
> [  357.427901] sky2 eth0: disabling interface
Waiting for suspend to complete 27 to go ...
> [  357.658144] wlan1: disassociating by local choice (reason=3)
Waiting for suspend to complete 26 to go ...
Waiting for suspend to complete 25 to go ...
Waiting for suspend to complete 24 to go ...
> [  360.808957] PM: Syncing filesystems ... done.
> [  360.818674] PM: Preparing system for mem sleep
> [  360.818678] Freezing user space processes ... (elapsed 0.00 seconds) done.
> [  360.819294] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
> [  360.819333] PM: Entering mem sleep
> [  360.819347] Suspending console(s) (use no_console_suspend to debug)
> [  361.393187] sd 0:0:0:0: [sda] Synchronizing SCSI cache
> [  361.393283] sd 0:0:0:0: [sda] Stopping disk
> [  361.876328] ACPI handle has no context!
> [  361.892339] ath5k_pci 0000:02:00.0: PCI INT A disabled
> [  361.988760] ehci_hcd 0000:00:1d.7: PCI INT A disabled
> [  362.004329] uhci_hcd 0000:00:1d.2: PCI INT C disabled
> [  362.004573] uhci_hcd 0000:00:1d.1: PCI INT B disabled
> [  362.004817] uhci_hcd 0000:00:1d.0: PCI INT A disabled
> [  362.036148] HDA Intel 0000:00:1b.0: PCI INT A disabled
> [  362.052370] ehci_hcd 0000:00:1a.7: PCI INT C disabled
> [  362.068358] uhci_hcd 0000:00:1a.2: PCI INT C disabled
> [  362.068602] uhci_hcd 0000:00:1a.1: PCI INT B disabled
> [  362.068845] uhci_hcd 0000:00:1a.0: PCI INT A disabled
> [  362.069264] PM: suspend devices took 1.252 seconds
> [  362.069390] ACPI: Preparing to enter system sleep state S3
> [  362.072006] Disabling non-boot CPUs ...
> [  362.074587] NOHZ: local_softirq_pending 100
> [  362.172081] CPU 1 is now offline
> [  362.172084] SMP alternatives: switching to UP code
> [  362.293992] CPU0 attaching NULL sched-domain.
> [  362.293995] CPU1 attaching NULL sched-domain.
> [  362.294283] CPU0 attaching NULL sched-domain.
> [  362.294436] CPU1 is down
> [  362.294547] Extended CMOS year: 2000
> [  362.294547] Back to C!
> [  362.294547] Extended CMOS year: 2000
> [  362.294547] Enabling non-boot CPUs ...
> [  362.294547] SMP alternatives: switching to SMP code
> [  362.419546] Booting processor 1 APIC 0x1 ip 0x6000
> [  362.293867] Initializing CPU#1
> [  362.293867] Calibrating delay using timer specific routine.. 3990.07 BogoMIPS (lpj=7980142)
> [  362.293867] CPU: L1 I cache: 32K, L1 D cache: 32K
> [  362.293867] CPU: L2 cache: 1024K
> [  362.293867] CPU: Physical Processor ID: 0
> [  362.293867] CPU: Processor Core ID: 1
> [  362.508404] CPU1: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
> [  362.508468] CPU0 attaching NULL sched-domain.
> [  362.509012] CPU0 attaching sched-domain:
> [  362.509016]  domain 0: span 0-1 level MC
> [  362.509018]   groups: 0 1
> [  362.509022] CPU1 attaching sched-domain:
> [  362.509023]  domain 0: span 0-1 level MC
> [  362.509025]   groups: 1 0
> [  362.512019] Switched to high resolution mode on CPU 1
> [  362.512031] CPU1 is up
> [  362.512033] ACPI: Waking up from system sleep state S3
> [  362.715462] ACPI: EC: non-query interrupt received, switching to interrupt mode
> [  362.721200] pcieport-driver 0000:00:01.0: restoring config space at offset 0x7 (was 0x20002020, writing 0x2020)
> [  362.721204] pcieport-driver 0000:00:01.0: restoring config space at offset 0x6 (was 0x100, writing 0x10100)
> [  362.721209] pcieport-driver 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
> [  362.721214] pcieport-driver 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
> [  362.721238] pcieport-driver 0000:00:01.0: setting latency timer to 64
> [  362.721249] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
> [  362.721254] uhci_hcd 0000:00:1a.0: setting latency timer to 64
> [  362.721314] usb usb3: root hub lost power or was reset
> [  362.721343] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
> [  362.721348] uhci_hcd 0000:00:1a.1: setting latency timer to 64
> [  362.721407] usb usb4: root hub lost power or was reset
> [  362.721425] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
> [  362.721429] uhci_hcd 0000:00:1a.2: setting latency timer to 64
> [  362.721488] usb usb5: root hub lost power or was reset
> [  362.736026] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
> [  362.736031] ehci_hcd 0000:00:1a.7: setting latency timer to 64
> [  362.752039] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
> [  362.752060] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  362.752066] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
> [  362.752085] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
> [  362.752091] HDA Intel 0000:00:1b.0: setting latency timer to 64
> [  362.843647] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
> [  362.843666] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf0f1f001)
> [  362.843672] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf3f0f300)
> [  362.843678] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
> [  362.843691] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  362.843702] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  362.843761] pcieport-driver 0000:00:1c.0: setting latency timer to 64
> [  362.843786] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x40300, writing 0x40305)
> [  362.843806] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x9 (was 0x10001, writing 0xf1f1f101)
> [  362.843814] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x7 (was 0x20000000, writing 0x4040)
> [  362.843831] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  362.843840] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  362.843901] pcieport-driver 0000:00:1c.2: setting latency timer to 64
> [  362.843929] pcieport-driver 0000:00:1c.3: restoring config space at offset 0xf (was 0x40400, writing 0x40405)
> [  362.843947] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf2f1f201)
> [  362.843956] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
> [  362.843970] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
> [  362.843981] pcieport-driver 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  362.844057] pcieport-driver 0000:00:1c.3: setting latency timer to 64
> [  362.844070] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
> [  362.844079] uhci_hcd 0000:00:1d.0: setting latency timer to 64
> [  362.844162] usb usb6: root hub lost power or was reset
> [  362.844180] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
> [  362.844187] uhci_hcd 0000:00:1d.1: setting latency timer to 64
> [  362.844270] usb usb7: root hub lost power or was reset
> [  362.844290] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
> [  362.844296] uhci_hcd 0000:00:1d.2: setting latency timer to 64
> [  362.844379] usb usb8: root hub lost power or was reset
> [  362.860030] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
> [  362.860035] ehci_hcd 0000:00:1d.7: setting latency timer to 64
> [  362.860100] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
> [  362.860111] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
> [  362.860116] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
> [  362.860121] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
> [  362.860133] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  362.860148] pci 0000:00:1e.0: setting latency timer to 64
> [  362.876042] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
> [  362.876065] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
> [  362.876103] ahci 0000:00:1f.2: setting latency timer to 64
> [  362.876235] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0xc2000004)
> [  362.876343] pci 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
> [  362.876401] pci 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0x2001)
> [  362.876427] pci 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xcc000004)
> [  362.876452] pci 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xd000000c)
> [  362.876470] pci 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xce000000)
> [  362.876487] pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  362.876513] pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  362.876621] ath5k_pci 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
> [  362.876646] ath5k_pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf3000004)
> [  362.876652] ath5k_pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  362.876660] ath5k_pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
> [  362.892029] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
> [  362.908204] sky2 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
> [  362.908332] sky2 0000:06:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x5001)
> [  362.908380] sky2 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf5000004)
> [  362.908409] sky2 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
> [  362.908458] sky2 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
> [  362.909156] sd 0:0:0:0: [sda] Starting disk
> [  363.000024] Clocksource tsc unstable (delta = -500010296 ns)
> [  363.196037] ata5: SATA link down (SStatus 0 SControl 300)
> [  363.196056] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
> [  363.196076] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
> [  363.196091] ata6: SATA link down (SStatus 0 SControl 300)
> [  363.208805] ata1.00: configured for UDMA/133
> [  363.224070] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
> [  363.224088] sd 0:0:0:0: [sda] Write Protect is off
> [  363.224090] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
> [  363.224114] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
> [  363.453645] ata2.00: configured for UDMA/100
> [  363.912029] usb 1-3: reset high speed USB device using ehci_hcd and address 3
> [  364.356055] usb 3-1: reset low speed USB device using uhci_hcd and address 2
> [  364.666263] PM: resume devices took 1.952 seconds
> [  364.666441] PM: Finishing wakeup.
> [  364.666442] Restarting tasks ... 
^---
[/html]

---

### Post by bluevalley on 2009-04-28
it can not be simpler: Just enabling Nvidia drivers solved my problem.

---

### Post by ken78724 on 2009-04-29
in conclusion did you say that proper programming of nVidia solved "can't resume kubuntu 9.04? i recall before my newly installed 9.04 became inaccessible with a grey screen on my 80giB [during a long update, a note came up saying nvidia could not install due to incompatibilities]. whereas I was tired I said, "I'll do that later so I can get back to work." Sure enough I had to let kbuntu/on 80 gig go and use 8.10 interplex on my 750 gib. I'd like benefit of using kubuntu 9.04. 

so if you don't mind telling me, what is involved in getting past a grey screen [can't resume kubuntu 9.04] and programming nvidia? :)

---

### Post by gfxcoder on 2009-04-29
i have an hp pavilion dv7t-2000 that is having problems resuming from suspend to ram.  it will blackout and blink the power button, but resuming will seem to "cycle" through the stored states for caps-lock, num-lock, etc... the hdd light turns on for a second, the back-light for the screen is on (but blacked out), and then nothing.  it just sits there.  any suggestions?  (i'm new to diagnosing acpi problems)

thanks!

lshw
```
hep
    description: Notebook
    product: HP Pavilion dv7 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF9152K36
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=434E4639-3135-324B-3336-00238BAEDE6A
  *-core
       description: Motherboard
       product: 3624
       vendor: Quanta
       physical id: 0
       version: 18.27
       serial: CNF9152K36
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.12 (03/23/2009)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: e
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          slot: CPU
          size: 1200MHz
          capacity: 2GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: f
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 10
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 737373737373737373737373737373737373
             vendor: Samsung
             physical id: 0
             serial: 94754573
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 252525252525252525252525252525252525
             vendor: Samsung
             physical id: 1
             serial: 61838225
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: M92 [Mobility Radeon HD 4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-multimedia
                description: Audio device
                product: R700 Audio Device [Radeon HD 4000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: 00:24:2b:dc:c9:b6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:ae:de:6a
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.101 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=ohci1394 latency=0 module=ohci1394
           *-system:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.2
                bus info: pci@0000:06:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.3
                bus info: pci@0000:06:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.4
                bus info: pci@0000:06:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHZ2320B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8909
                serial: K618T943LS9K
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a2bf227e
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 98eda4c4-0f7a-40e5-b4c8-69230b08e2c1
                   size: 186GiB
                   capacity: 186GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-04-25 10:08:53 filesystem=ext4 modified=2009-04-28 18:45:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-04-28 15:06:38 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 5158aa14-2b04-4cb8-8c86-232019c3b826
                   size: 8581MiB
                   capacity: 8581MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633M
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:10:86:c2:6b:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=98eda4c4-0f7a-40e5-b4c8-69230b08e2c1 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfca8000 (usable)
[    0.000000]  BIOS-e820: 00000000bfca8000 - 00000000bfcbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfcbf000 - 00000000bfd81000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd81000 - 00000000bfdbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfde1000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde1000 - 00000000bfdf7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdf7000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfca8000 (usable)
[    0.000000]  modified: 00000000bfca8000 - 00000000bfcbf000 (reserved)
[    0.000000]  modified: 00000000bfcbf000 - 00000000bfd81000 (usable)
[    0.000000]  modified: 00000000bfd81000 - 00000000bfdbf000 (ACPI NVS)
[    0.000000]  modified: 00000000bfdbf000 - 00000000bfde1000 (usable)
[    0.000000]  modified: 00000000bfde1000 - 00000000bfdf7000 (ACPI data)
[    0.000000]  modified: 00000000bfdf7000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfe00000
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000] kernel direct mapping tables up to bfe00000 @ 10000-14000
[    0.000000] last_map_addr: bfe00000 end: bfe00000
[    0.000000] RAMDISK: 3785c000 - 37fefc9a
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HPQOEM)
[    0.000000] ACPI: XSDT BFDF6120, 006C (r1 HPQOEM SLIC-MPC        1       1000013)
[    0.000000] ACPI: FACP BFDF4000, 00F4 (r4 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: DSDT BFDE4000, B6B3 (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: FACS BFD8D000, 0040
[    0.000000] ACPI: DMAR BFDF5000, 0040 (r1                       1             0)
[    0.000000] ACPI: HPET BFDF3000, 0038 (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: APIC BFDF2000, 006C (r2 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: MCFG BFDF1000, 003C (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: ASF! BFDF0000, 00A5 (r32 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: SLIC BFDE3000, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: BOOT BFDE2000, 0028 (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
[    0.000000] ACPI: SSDT BFDE1000, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bfe00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785c000 - 0037fefc9a]          RAMDISK ==> [003785c000 - 0037fefc9a]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]  [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x000bfca8
[    0.000000]     0: 0x000bfcbf -> 0x000bfd81
[    0.000000]     0: 0x000bfdbf -> 0x000bfde1
[    0.000000]     0: 0x000bfdf7 -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785689
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2540 pages reserved
[    0.000000]   DMA zone: 1376 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10689 pages used for memmap
[    0.000000]   DMA32 zone: 771028 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bfca8000 - 00000000bfcbf000
[    0.000000] PM: Registered nosave memory: 00000000bfd81000 - 00000000bfdbf000
[    0.000000] PM: Registered nosave memory: 00000000bfde1000 - 00000000bfdf7000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 772404
[    0.000000] Kernel command line: root=UUID=98eda4c4-0f7a-40e5-b4c8-69230b08e2c1 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.144 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 31457280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 3044176k/3143680k available (4760k kernel code, 924k absent, 97860k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.28 BogoMIPS (lpj=7980576)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.006533] ACPI: Checking initramfs for custom DSDT
[    0.348017] Setting APIC routing to flat
[    0.348380] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.388074] CPU0: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.392001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.95 BogoMIPS (lpj=7979916)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.476516] CPU1: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
[    0.476539] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.480039] Brought up 2 CPUs
[    0.480042] Total of 2 processors activated (7980.24 BogoMIPS).
[    0.480087] CPU0 attaching sched-domain:
[    0.480090]  domain 0: span 0-1 level MC
[    0.480092]   groups: 0 1
[    0.480096] CPU1 attaching sched-domain:
[    0.480098]  domain 0: span 0-1 level MC
[    0.480099]   groups: 1 0
[    0.480160] net_namespace: 1400 bytes
[    0.480160] Booting paravirtualized kernel on bare hardware
[    0.480258] Time: 10:20:53  Date: 04/29/09
[    0.480258] regulator: core version 0.5
[    0.480258] NET: Registered protocol family 16
[    0.480258] ACPI: bus type pci registered
[    0.480258] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.480258] PCI: MCFG area at f8000000 reserved in E820
[    0.484258] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.484260] PCI: Using configuration type 1 for base access
[    0.485250] ACPI: EC: Look up EC in DSDT
[    0.490356] ACPI: BIOS _OSI(Linux) query ignored
[    0.620017] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.624276] ACPI: Interpreter enabled
[    0.624279] ACPI: (supports S0 S3 S4 S5)
[    0.624304] ACPI: Using IOAPIC for interrupt routing
[    0.638306] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.638308] ACPI: EC: driver started in interrupt mode
[    0.638510] ACPI: No dock devices found.
[    0.638519] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.638607] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.638611] pci 0000:00:01.0: PME# disabled
[    0.638698] pci 0000:00:1a.0: reg 20 io port: [0x80e0-0x80ff]
[    0.638773] pci 0000:00:1a.1: reg 20 io port: [0x80c0-0x80df]
[    0.638854] pci 0000:00:1a.7: reg 10 32bit mmio: [0xda105c00-0xda105fff]
[    0.638898] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.638903] pci 0000:00:1a.7: PME# disabled
[    0.638955] pci 0000:00:1b.0: reg 10 64bit mmio: [0xda100000-0xda103fff]
[    0.638990] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.638994] pci 0000:00:1b.0: PME# disabled
[    0.639050] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.639054] pci 0000:00:1c.0: PME# disabled
[    0.639112] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.639116] pci 0000:00:1c.1: PME# disabled
[    0.639176] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.639180] pci 0000:00:1c.3: PME# disabled
[    0.639238] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.639242] pci 0000:00:1c.4: PME# disabled
[    0.639299] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.639303] pci 0000:00:1c.5: PME# disabled
[    0.639368] pci 0000:00:1d.0: reg 20 io port: [0x80a0-0x80bf]
[    0.639444] pci 0000:00:1d.1: reg 20 io port: [0x8080-0x809f]
[    0.639520] pci 0000:00:1d.2: reg 20 io port: [0x8060-0x807f]
[    0.639596] pci 0000:00:1d.3: reg 20 io port: [0x8040-0x805f]
[    0.639674] pci 0000:00:1d.7: reg 10 32bit mmio: [0xda105800-0xda105bff]
[    0.639720] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.639724] pci 0000:00:1d.7: PME# disabled
[    0.639920] pci 0000:00:1f.2: reg 10 io port: [0x8108-0x810f]
[    0.639927] pci 0000:00:1f.2: reg 14 io port: [0x8114-0x8117]
[    0.639933] pci 0000:00:1f.2: reg 18 io port: [0x8100-0x8107]
[    0.639939] pci 0000:00:1f.2: reg 1c io port: [0x8110-0x8113]
[    0.639945] pci 0000:00:1f.2: reg 20 io port: [0x8020-0x803f]
[    0.639952] pci 0000:00:1f.2: reg 24 32bit mmio: [0xda105000-0xda1057ff]
[    0.639969] pci 0000:00:1f.2: PME# supported from D3hot
[    0.639972] pci 0000:00:1f.2: PME# disabled
[    0.640012] pci 0000:00:1f.3: reg 10 64bit mmio: [0xda106000-0xda1060ff]
[    0.640029] pci 0000:00:1f.3: reg 20 io port: [0x8000-0x801f]
[    0.640088] pci 0000:00:1f.6: reg 10 64bit mmio: [0xda104000-0xda104fff]
[    0.640174] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.640181] pci 0000:01:00.0: reg 14 io port: [0x7000-0x70ff]
[    0.640189] pci 0000:01:00.0: reg 18 32bit mmio: [0xda000000-0xda00ffff]
[    0.640212] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.640222] pci 0000:01:00.0: supports D1 D2
[    0.640266] pci 0000:01:00.1: reg 10 32bit mmio: [0xda010000-0xda013fff]
[    0.640309] pci 0000:01:00.1: supports D1 D2
[    0.640370] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]
[    0.640373] pci 0000:00:01.0: bridge 32bit mmio: [0xda000000-0xda0fffff]
[    0.640377] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.640723] pci 0000:02:00.0: reg 10 64bit mmio: [0xd9000000-0xd9003fff]
[    0.640842] pci 0000:02:00.0: supports D1 D2
[    0.640947] pci 0000:00:1c.0: bridge io port: [0x6000-0x6fff]
[    0.640951] pci 0000:00:1c.0: bridge 32bit mmio: [0xd9000000-0xd9ffffff]
[    0.640958] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.641011] pci 0000:03:00.0: reg 10 io port: [0x5000-0x50ff]
[    0.641034] pci 0000:03:00.0: reg 18 64bit mmio: [0xd1010000-0xd1010fff]
[    0.641050] pci 0000:03:00.0: reg 20 64bit mmio: [0xd1000000-0xd100ffff]
[    0.641059] pci 0000:03:00.0: reg 30 32bit mmio: [0xffff0000-0xffffffff]
[    0.641072] pci 0000:03:00.0: supports D1 D2
[    0.641073] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.641079] pci 0000:03:00.0: PME# disabled
[    0.641145] pci 0000:00:1c.1: bridge io port: [0x5000-0x5fff]
[    0.641149] pci 0000:00:1c.1: bridge 32bit mmio: [0xd8000000-0xd8ffffff]
[    0.641156] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd1000000-0xd1ffffff]
[    0.641205] pci 0000:00:1c.3: bridge io port: [0x4000-0x4fff]
[    0.641209] pci 0000:00:1c.3: bridge 32bit mmio: [0xd7000000-0xd7ffffff]
[    0.641216] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd2000000-0xd2ffffff]
[    0.641274] pci 0000:06:00.0: reg 10 32bit mmio: [0xd6000000-0xd60007ff]
[    0.641285] pci 0000:06:00.0: reg 14 32bit mmio: [0xd6000d00-0xd6000d7f]
[    0.641316] pci 0000:06:00.0: reg 20 32bit mmio: [0xd6000c80-0xd6000cff]
[    0.641327] pci 0000:06:00.0: reg 24 32bit mmio: [0xd6000c00-0xd6000c7f]
[    0.641416] pci 0000:06:00.1: reg 10 32bit mmio: [0xd6000b00-0xd6000bff]
[    0.641539] pci 0000:06:00.2: reg 10 32bit mmio: [0xd6000a00-0xd6000aff]
[    0.641661] pci 0000:06:00.3: reg 10 32bit mmio: [0xd6000900-0xd60009ff]
[    0.641784] pci 0000:06:00.4: reg 10 32bit mmio: [0xd6000800-0xd60008ff]
[    0.641910] pci 0000:00:1c.4: bridge io port: [0x3000-0x3fff]
[    0.641914] pci 0000:00:1c.4: bridge 32bit mmio: [0xd6000000-0xd6ffffff]
[    0.641921] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd3000000-0xd3ffffff]
[    0.641970] pci 0000:00:1c.5: bridge io port: [0x2000-0x2fff]
[    0.641974] pci 0000:00:1c.5: bridge 32bit mmio: [0xd5000000-0xd5ffffff]
[    0.641981] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd4000000-0xd4ffffff]
[    0.642038] pci 0000:00:1e.0: transparent bridge
[    0.642082] bus 00 -> node 0
[    0.642097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.642604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.642791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.643043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.643243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.643449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.643649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.643872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.647535] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.647712] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.647886] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.648066] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.648243] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.648416] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.648590] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.648763] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.649031] ACPI: WMI: Mapper loaded
[    0.649071] SCSI subsystem initialized
[    0.649071] libata version 3.00 loaded.
[    0.649071] usbcore: registered new interface driver usbfs
[    0.649071] usbcore: registered new interface driver hub
[    0.649071] usbcore: registered new device driver usb
[    0.649071] PCI: Using ACPI for IRQ routing
[    0.660010] Bluetooth: Core ver 2.13
[    0.660021] NET: Registered protocol family 31
[    0.660021] Bluetooth: HCI device and connection manager initialized
[    0.660021] Bluetooth: HCI socket layer initialized
[    0.660021] NET: Registered protocol family 8
[    0.660021] NET: Registered protocol family 20
[    0.660030] NetLabel: Initializing
[    0.660031] NetLabel:  domain hash size = 128
[    0.660033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.660045] NetLabel:  unlabeled traffic allowed by default
[    0.660076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.660080] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.664058] AppArmor: AppArmor Filesystem Enabled
[    0.668008] Switched to high resolution mode on CPU 0
[    0.668571] Switched to high resolution mode on CPU 1
[    0.676007] pnp: PnP ACPI init
[    0.676015] ACPI: bus type pnp registered
[    0.680331] pnp: PnP ACPI: found 12 devices
[    0.680333] ACPI: ACPI bus type pnp unregistered
[    0.680343] system 00:00: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.680348] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.680351] system 00:02: ioport range 0x600-0x60f has been reserved
[    0.680353] system 00:02: ioport range 0x610-0x610 has been reserved
[    0.680355] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.680357] system 00:02: ioport range 0x810-0x817 has been reserved
[    0.680359] system 00:02: ioport range 0x820-0x823 has been reserved
[    0.680361] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.680363] system 00:02: ioport range 0x500-0x53f has been reserved
[    0.680365] system 00:02: ioport range 0x380-0x38e has been reserved
[    0.680367] system 00:02: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.680369] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.680371] system 00:02: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.680374] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.680376] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.680378] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.680380] system 00:02: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.680382] system 00:02: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.680384] system 00:02: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.680387] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.685078] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.685081] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    0.685084] pci 0000:00:01.0:   MEM window: 0xda000000-0xda0fffff
[    0.685087] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.685092] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.685095] pci 0000:00:1c.0:   IO window: 0x6000-0x6fff
[    0.685100] pci 0000:00:1c.0:   MEM window: 0xd9000000-0xd9ffffff
[    0.685104] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    0.685111] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.685114] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
[    0.685119] pci 0000:00:1c.1:   MEM window: 0xd8000000-0xd8ffffff
[    0.685123] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1000000-0x000000d1ffffff
[    0.685129] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.685132] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.685137] pci 0000:00:1c.3:   MEM window: 0xd7000000-0xd7ffffff
[    0.685141] pci 0000:00:1c.3:   PREFETCH window: 0x000000d2000000-0x000000d2ffffff
[    0.685148] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.685151] pci 0000:00:1c.4:   IO window: 0x3000-0x3fff
[    0.685156] pci 0000:00:1c.4:   MEM window: 0xd6000000-0xd6ffffff
[    0.685160] pci 0000:00:1c.4:   PREFETCH window: 0x000000d3000000-0x000000d3ffffff
[    0.685167] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
[    0.685169] pci 0000:00:1c.5:   IO window: 0x2000-0x2fff
[    0.685174] pci 0000:00:1c.5:   MEM window: 0xd5000000-0xd5ffffff
[    0.685178] pci 0000:00:1c.5:   PREFETCH window: 0x000000d4000000-0x000000d4ffffff
[    0.685185] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.685186] pci 0000:00:1e.0:   IO window: disabled
[    0.685191] pci 0000:00:1e.0:   MEM window: disabled
[    0.685195] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.685207] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.685211] pci 0000:00:01.0: setting latency timer to 64
[    0.685218] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.685222] pci 0000:00:1c.0: setting latency timer to 64
[    0.685230] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.685233] pci 0000:00:1c.1: setting latency timer to 64
[    0.685242] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.685246] pci 0000:00:1c.3: setting latency timer to 64
[    0.685253] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.685257] pci 0000:00:1c.4: setting latency timer to 64
[    0.685264] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.685268] pci 0000:00:1c.5: setting latency timer to 64
[    0.685275] pci 0000:00:1e.0: setting latency timer to 64
[    0.685278] bus: 00 index 0 io port: [0x00-0xffff]
[    0.685280] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.685282] bus: 01 index 0 io port: [0x7000-0x7fff]
[    0.685283] bus: 01 index 1 mmio: [0xda000000-0xda0fffff]
[    0.685285] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.685287] bus: 01 index 3 mmio: [0x0-0x0]
[    0.685288] bus: 02 index 0 io port: [0x6000-0x6fff]
[    0.685290] bus: 02 index 1 mmio: [0xd9000000-0xd9ffffff]
[    0.685291] bus: 02 index 2 mmio: [0xd0000000-0xd0ffffff]
[    0.685293] bus: 02 index 3 mmio: [0x0-0x0]
[    0.685294] bus: 03 index 0 io port: [0x5000-0x5fff]
[    0.685296] bus: 03 index 1 mmio: [0xd8000000-0xd8ffffff]
[    0.685297] bus: 03 index 2 mmio: [0xd1000000-0xd1ffffff]
[    0.685299] bus: 03 index 3 mmio: [0x0-0x0]
[    0.685300] bus: 05 index 0 io port: [0x4000-0x4fff]
[    0.685302] bus: 05 index 1 mmio: [0xd7000000-0xd7ffffff]
[    0.685303] bus: 05 index 2 mmio: [0xd2000000-0xd2ffffff]
[    0.685305] bus: 05 index 3 mmio: [0x0-0x0]
[    0.685306] bus: 06 index 0 io port: [0x3000-0x3fff]
[    0.685308] bus: 06 index 1 mmio: [0xd6000000-0xd6ffffff]
[    0.685309] bus: 06 index 2 mmio: [0xd3000000-0xd3ffffff]
[    0.685311] bus: 06 index 3 mmio: [0x0-0x0]
[    0.685312] bus: 07 index 0 io port: [0x2000-0x2fff]
[    0.685314] bus: 07 index 1 mmio: [0xd5000000-0xd5ffffff]
[    0.685315] bus: 07 index 2 mmio: [0xd4000000-0xd4ffffff]
[    0.685317] bus: 07 index 3 mmio: [0x0-0x0]
[    0.685318] bus: 0a index 0 mmio: [0x0-0x0]
[    0.685320] bus: 0a index 1 mmio: [0x0-0x0]
[    0.685321] bus: 0a index 2 mmio: [0x0-0x0]
[    0.685323] bus: 0a index 3 io port: [0x00-0xffff]
[    0.685324] bus: 0a index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.685332] NET: Registered protocol family 2
[    0.720551] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.721054] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.723395] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.723901] TCP: Hash tables configured (established 262144 bind 65536)
[    0.723904] TCP reno registered
[    0.732621] NET: Registered protocol family 1
[    0.732744] checking if image is initramfs... it is
[    1.407475] Freeing initrd memory: 7759k freed
[    1.411047] Simple Boot Flag at 0x44 set to 0x1
[    1.411337] audit: initializing netlink socket (disabled)
[    1.411351] type=2000 audit(1241000453.408:1): initialized
[    1.419576] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.420707] VFS: Disk quotas dquot_6.5.1
[    1.420756] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.421233] fuse init (API version 7.10)
[    1.421301] msgmni has been set to 5962
[    1.421444] alg: No test for stdrng (krng)
[    1.421452] io scheduler noop registered
[    1.421454] io scheduler anticipatory registered
[    1.421456] io scheduler deadline registered
[    1.421491] io scheduler cfq registered (default)
[    1.421847] pci 0000:01:00.0: Boot video device
[    1.428161] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.428194] pcieport-driver 0000:00:01.0: found MSI capability
[    1.428215] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.428224] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.428236] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.428246] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.428291] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.428332] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.428359] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.428373] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.428384] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.428394] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.428456] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.428496] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.428529] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.428542] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.428553] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.428563] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.428625] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.428665] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.428692] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.428706] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.428716] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.428728] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.428792] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.428832] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.428859] pcieport-driver 0000:00:1c.4: irq 2299 for MSI/MSI-X
[    1.428873] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.428883] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.428893] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.428955] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.428995] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.429022] pcieport-driver 0000:00:1c.5: irq 2298 for MSI/MSI-X
[    1.429035] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.429046] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.429057] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.429127] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.430172] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.431744] ACPI: AC Adapter [ACAD] (on-line)
[    1.522511] ACPI: Battery Slot [BAT0] (battery present)
[    1.522580] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.522583] ACPI: Power Button (FF) [PWRF]
[    1.522622] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.522624] ACPI: Power Button (CM) [PWRB]
[    1.522660] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.524756] ACPI: Lid Switch [LID0]
[    1.524797] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.524799] ACPI: Sleep Button (CM) [SLPB]
[    1.525640] ACPI: SSDT BFCB4C98, 0223 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.526230] ACPI: SSDT BFCB2618, 05B3 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.526781] Monitor-Mwait will be used to enter C-1 state
[    1.526783] Monitor-Mwait will be used to enter C-2 state
[    1.526785] Monitor-Mwait will be used to enter C-3 state
[    1.526797] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.526818] processor ACPI_CPU:00: registered as cooling_device0
[    1.526821] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.527353] ACPI: SSDT BFCB3E18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117)
[    1.527878] ACPI: SSDT BFCB4F18, 008D (r1  PmRef    ApCst     3000 INTL 20051117)
[    1.528591] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.528606] processor ACPI_CPU:01: registered as cooling_device1
[    1.528610] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.540639] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.576746] Linux agpgart interface v0.103
[    1.576753] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.577628] brd: module loaded
[    1.577909] loop: module loaded
[    1.577967] Fixed MDIO Bus: probed
[    1.577971] PPP generic driver version 2.4.2
[    1.578019] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.578041] Driver 'sd' needs updating - please use bus_type methods
[    1.578049] Driver 'sr' needs updating - please use bus_type methods
[    1.578090] ahci 0000:00:1f.2: version 3.0
[    1.578101] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.578135] ahci 0000:00:1f.2: irq 2297 for MSI/MSI-X
[    1.578210] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.578213] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[    1.578218] ahci 0000:00:1f.2: setting latency timer to 64
[    1.578481] scsi0 : ahci
[    1.578560] scsi1 : ahci
[    1.578608] scsi2 : ahci
[    1.578652] scsi3 : ahci
[    1.578701] scsi4 : ahci
[    1.578748] scsi5 : ahci
[    1.578847] ata1: SATA max UDMA/133 abar m2048@0xda105000 port 0xda105100 irq 2297
[    1.578851] ata2: SATA max UDMA/133 abar m2048@0xda105000 port 0xda105180 irq 2297
[    1.578852] ata3: DUMMY
[    1.578853] ata4: DUMMY
[    1.578855] ata5: SATA max UDMA/133 abar m2048@0xda105000 port 0xda105300 irq 2297
[    1.578858] ata6: SATA max UDMA/133 abar m2048@0xda105000 port 0xda105380 irq 2297
[    2.060012] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.060370] ata1.00: ATA-8: FUJITSU MHZ2320BH G2, 8909, max UDMA/100
[    2.060372] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.060812] ata1.00: configured for UDMA/100
[    2.964011] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.981656] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633M, 0200, max UDMA/100
[    2.999578] ata2.00: configured for UDMA/100
[    3.336014] ata5: SATA link down (SStatus 0 SControl 300)
[    3.672013] ata6: SATA link down (SStatus 0 SControl 300)
[    3.688090] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2320B 8909 PQ: 0 ANSI: 5
[    3.688175] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.688190] sd 0:0:0:0: [sda] Write Protect is off
[    3.688192] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.688215] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.688274] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.688287] sd 0:0:0:0: [sda] Write Protect is off
[    3.688289] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.688311] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.688314]  sda: sda1 sda2
[    3.738953] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.738995] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.739681] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633M  0200 PQ: 0 ANSI: 5
[    3.746895] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.746898] Uniform CD-ROM driver Revision: 3.20
[    3.746969] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.746999] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.747596] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.747615] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.747631] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.747634] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.747684] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.751576] ehci_hcd 0000:00:1a.7: debug port 1
[    3.751582] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.751596] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xda105c00
[    3.764007] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.764067] usb usb1: configuration #1 chosen from 1 choice
[    3.764088] hub 1-0:1.0: USB hub found
[    3.764095] hub 1-0:1.0: 4 ports detected
[    3.764183] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.764192] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.764195] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.764229] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.768146] ehci_hcd 0000:00:1d.7: debug port 1
[    3.768151] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.768164] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda105800
[    3.780007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.780051] usb usb2: configuration #1 chosen from 1 choice
[    3.780071] hub 2-0:1.0: USB hub found
[    3.780077] hub 2-0:1.0: 8 ports detected
[    3.780162] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.780175] uhci_hcd: USB Universal Host Controller Interface driver
[    3.780192] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.780198] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.780201] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.780246] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.780279] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
[    3.780344] usb usb3: configuration #1 chosen from 1 choice
[    3.780365] hub 3-0:1.0: USB hub found
[    3.780371] hub 3-0:1.0: 2 ports detected
[    3.780446] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.780452] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.780455] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.780488] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.780519] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000080c0
[    3.780584] usb usb4: configuration #1 chosen from 1 choice
[    3.780604] hub 4-0:1.0: USB hub found
[    3.780610] hub 4-0:1.0: 2 ports detected
[    3.780684] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.780690] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.780693] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.780726] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.780751] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000080a0
[    3.780814] usb usb5: configuration #1 chosen from 1 choice
[    3.780833] hub 5-0:1.0: USB hub found
[    3.780839] hub 5-0:1.0: 2 ports detected
[    3.780914] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.780920] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.780923] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.780959] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.780983] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008080
[    3.781045] usb usb6: configuration #1 chosen from 1 choice
[    3.781067] hub 6-0:1.0: USB hub found
[    3.781072] hub 6-0:1.0: 2 ports detected
[    3.781143] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.781149] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.781152] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.781190] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.781213] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00008060
[    3.781277] usb usb7: configuration #1 chosen from 1 choice
[    3.781297] hub 7-0:1.0: USB hub found
[    3.781303] hub 7-0:1.0: 2 ports detected
[    3.781375] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.781380] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.781383] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.781419] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    3.781449] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00008040
[    3.781513] usb usb8: configuration #1 chosen from 1 choice
[    3.781533] hub 8-0:1.0: USB hub found
[    3.781538] hub 8-0:1.0: 2 ports detected
[    3.781656] usbcore: registered new interface driver libusual
[    3.781687] usbcore: registered new interface driver usbserial
[    3.781696] USB Serial support registered for generic
[    3.781708] usbcore: registered new interface driver usbserial_generic
[    3.781710] usbserial: USB Serial Driver core
[    3.781751] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    3.808040] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.808045] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.816535] mice: PS/2 mouse device common for all mice
[    3.876553] rtc_cmos 00:04: RTC can wake from S4
[    3.876585] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.876611] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.876659] device-mapper: uevent: version 1.0.3
[    3.876738] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.876799] device-mapper: multipath: version 1.0.5 loaded
[    3.876801] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.876936] cpuidle: using governor ladder
[    3.877029] cpuidle: using governor menu
[    3.877392] TCP cubic registered
[    3.877449] NET: Registered protocol family 10
[    3.877800] lo: Disabled Privacy Extensions
[    3.878046] NET: Registered protocol family 17
[    3.878062] Bluetooth: L2CAP ver 2.11
[    3.878063] Bluetooth: L2CAP socket layer initialized
[    3.878065] Bluetooth: SCO (Voice Link) ver 0.6
[    3.878067] Bluetooth: SCO socket layer initialized
[    3.878094] Bluetooth: RFCOMM socket layer initialized
[    3.878101] Bluetooth: RFCOMM TTY layer initialized
[    3.878102] Bluetooth: RFCOMM ver 1.10
[    3.878506] Marking TSC unstable due to TSC halts in idle
[    3.878776] registered taskstats version 1
[    3.878914]   Magic number: 5:497:326
[    3.879018] rtc_cmos 00:04: setting system clock to 2009-04-29 10:20:56 UTC (1241000456)
[    3.879021] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.879022] EDD information not available.
[    3.879077] Freeing unused kernel memory: 536k freed
[    3.879278] Write protecting the kernel read-only data: 6708k
[    3.895576] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.081689] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.081712] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.082201] r8169 0000:03:00.0: setting latency timer to 64
[    4.084521] r8169 0000:03:00.0: irq 2296 for MSI/MSI-X
[    4.085777] eth0: RTL8168c/8111c at 0xffffc2000007c000, 00:23:8b:ae:de:6a, XID 3c4000c0 IRQ 2296
[    4.092524] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    4.186367] ohci1394 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.186376] ohci1394 0000:06:00.0: setting latency timer to 64
[    4.238111] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d6000000-d60007ff]  Max Packet=[512]  IR/IT contexts=[4/4]
[    4.258795] usb 2-4: configuration #1 chosen from 1 choice
[    4.420295] PM: Starting manual resume from disk
[    4.420298] PM: Resume from partition 8:2
[    4.420299] PM: Checking hibernation image.
[    4.420450] PM: Resume from disk failed.
[    4.444330] EXT4-fs: barriers enabled
[    4.458185] kjournald2 starting.  Commit interval 5 seconds
[    4.458214] EXT4-fs: delayed allocation enabled
[    4.458216] EXT4-fs: file extents enabled
[    4.472955] EXT4-fs: mballoc enabled
[    4.472958] EXT4-fs: mounted filesystem with ordered data mode.
[    5.000600] Clocksource tsc unstable (delta = -410742319 ns)
[    5.516556] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0082d16a01]
[    8.068302] udev: starting version 141
[    8.621390] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.639717] [fglrx] Maximum main memory to use for locked dma buffers: 2836 MBytes.
[    8.640020] [fglrx]   vendor: 1002 device: 9553 count: 1
[    8.640429] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[    8.640445] pci 0000:01:00.0: power state changed by ACPI to D0
[    8.640453] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.640458] pci 0000:01:00.0: setting latency timer to 64
[    8.641770] [fglrx] Driver built-in PAT support is enabled successfully
[    8.641798] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[    8.740845] lis3lv02d: laptop model unknown, using default axes configuration
[    8.927964] iTCO_vendor_support: vendor-support=0
[    8.929416] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.929576] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[    8.929653] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.938865] ieee80211_crypt: registered algorithm 'NULL'
[    8.944797] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.944810] wl 0000:02:00.0: setting latency timer to 64
[    8.984924] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[    8.987916] sdhci: Secure Digital Host Controller Interface driver
[    8.987919] sdhci: Copyright(c) Pierre Ossman
[    8.999555] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    9.008900] lis3lv02d driver loaded.
[    9.023973] Linux video capture interface: v2.00
[    9.036363] acpi device:0a: registered as cooling_device2
[    9.042032] acpi device:0c: registered as cooling_device3
[    9.042280] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input8
[    9.053408] ieee80211_crypt: registered algorithm 'TKIP'
[    9.053779] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.79.10
[    9.065942] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[    9.065964] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.066024] sdhci-pci 0000:06:00.1: setting latency timer to 64
[    9.066093] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[    9.066104] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[    9.066121] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.066127] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[    9.066133] sdhci-pci 0000:06:00.2: PCI INT A disabled
[    9.076103] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.087954] uvcvideo: Found UVC 1.00 device HP Webcam (064e:c107)
[    9.090919] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input9
[    9.108251] usbcore: registered new interface driver uvcvideo
[    9.108288] USB Video Class driver (v0.1.0)
[    9.130332] leds-hp-disk driver loaded.
[    9.212919] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.262354] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.262436] HDA Intel 0000:00:1b.0: irq 2295 for MSI/MSI-X
[    9.262471] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.340453] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[    9.376498] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input11
[    9.392253] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[    9.404249] input: HDA Intel Line Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[    9.416972] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.417059] HDA Intel 0000:01:00.1: irq 2294 for MSI/MSI-X
[    9.417100] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.268324] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   10.347682] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   14.342436] lp: driver loaded but no devices found
[   14.408971] Adding 8787544k swap on /dev/sda2.  Priority:-1 extents:1 across:8787544k
[   14.943582] EXT4 FS on sda1, internal journal on sda1:8
[   15.940545] type=1505 audit(1241000468.561:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2231
[   15.940653] type=1505 audit(1241000468.561:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2231
[   15.940687] type=1505 audit(1241000468.561:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2231
[   15.940719] type=1505 audit(1241000468.561:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2231
[   16.040232] type=1505 audit(1241000468.657:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2236
[   16.040377] type=1505 audit(1241000468.657:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2236
[   16.062603] type=1505 audit(1241000468.681:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2240
[   19.495733] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.495736] Bluetooth: BNEP filters: protocol multicast
[   19.534014] Bridge firewalling registered
[   20.985422] ppdev: user-space parallel port driver
[   23.771398] fglrx_pci 0000:01:00.0: irq 2293 for MSI/MSI-X
[   23.783122] [fglrx] Firegl kernel thread PID: 3256
[   23.834183] [fglrx] Gart USWC size:1426 M.
[   23.834186] [fglrx] Gart cacheable size:60 M.
[   23.834191] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   23.834193] [fglrx] Reserved FB block: Unshared offset:fd0d000, size:2f3000 
[   23.834195] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   24.383145] r8169: eth0: link up
[   24.383151] r8169: eth0: link up
[   29.852093] eth1: no IPv6 routers present
[   34.712113] eth0: no IPv6 routers present
[   79.645520] CPU0 attaching NULL sched-domain.
[   79.645524] CPU1 attaching NULL sched-domain.
[   79.660621] CPU0 attaching sched-domain:
[   79.660625]  domain 0: span 0-1 level MC
[   79.660628]   groups: 0 1
[   79.660635] CPU1 attaching sched-domain:
[   79.660637]  domain 0: span 0-1 level MC
[   79.660640]   groups: 1 0
[  213.891620] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[  213.891625] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[  213.913777] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[  213.913781] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[  216.433913] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[  216.433918] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[  216.441600] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[  216.441605] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[  485.676161] type=1505 audit(1241000937.592:9): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=4688
[  485.676269] type=1505 audit(1241000937.592:10): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=4688
[  485.676310] type=1505 audit(1241000937.592:11): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=4688
[  485.676347] type=1505 audit(1241000937.592:12): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=4688
[  485.797116] type=1505 audit(1241000937.712:13): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4693
[  485.797287] type=1505 audit(1241000937.712:14): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=4693
[  485.821406] type=1505 audit(1241000937.736:15): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=4697
[  493.880032] eth1: no IPv6 routers present

```

/etc/default/acpi-support
```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 

```

---

### Post by dulbirakan on 2009-04-29
@gfxcoder

I think your problem might be related to fglrx drivers. I am using a 4850 with proprietary drivers provided and I have the same suspend problem. Also the boot time is longer than usual.

---

### Post by gfxcoder on 2009-04-29
i'm not having the same long boot time; from hitting power button to being able to run apps takes about 30-35sec.  so, i'm not all too concerned about the suspend issue (short boot time anyways).  although, these drivers may very well be the cause of the suspend problem.

---

### Post by dulbirakan on 2009-04-29
That is exactly what I mean, without these drivers my boot time is around 20 seconds... With these drivers it is more like 35...

---

### Post by dhabud on 2009-09-25
I am seeing similar issues too.

I have system with 
ASUS Motherboard
PHENOMII X3 CPU
Motherboard has NVIDIA 8300 Graphics chip on it.
Graphics Driver: 185.18.36 Latest as of Sept 24, 2009
System: Debian Lenny 2.26.26 kernel


Suspend and resume used to work correctly on this system, Things that I have put in after that were install NFS and remove linksys wireless card and added rt2860 based wireless card.



No when system wakes up after suspend and tries to resume, I see that there is blinking cursor for a while on screen, mouse and keyboard for a while but everything goes away and cannot do anything,
Reboot the system and everything is back. I need to get this suspend and resume working correctly

 
I tried couple of things mentioned on web

/etc/init.d/alsa-utils

ifconfig ra0 down

ifconfig wlan0 down

 

/boot/grub/menu.lst

acpi_sleep=s3_mode, s3_bios

vga=791

and things from [http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)

Nothing has helped so far. Please Please help. I know this is ubuntu forum but there is very less info on Debian..

---


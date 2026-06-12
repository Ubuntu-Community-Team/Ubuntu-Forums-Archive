---
title: "[SOLVED] DVD-RW drive not detected?"
date: 2008-09-01
forum: General Help
---

### Post by porchrat on 2008-09-01
OK the problem Ubuntu seems unable to detect my DVD-RW drive.  The BIOS boots and sees the drive fine, but ubuntu seems to have a problem.

I am running 8.04, here are a few ouputs in case anyone needs any extra info:

here is the lshw entry to do with the controllers and disks

```
 *-storage UNCLAIMED
                description: RAID bus controller
                product: Promise Technology, Inc.
                vendor: Promise Technology, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: latency=0
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk:0
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD15
                serial: 5QM23983
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00068d43
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 92777b3b-3049-4f4d-8726-2a8c29b0ea4b
                   size: 972MiB
                   capacity: 972MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-11 12:18:31 filesystem=ext3 modified=2008-09-01 12:37:27 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-09-01 12:29:56 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 18GiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 6922929b-6e62-43c5-b2fb-0b4e1e3a787d
                   size: 445GiB
                   capacity: 445GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-11 12:18:34 filesystem=ext3 modified=2008-09-01 12:38:47 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-09-01 12:38:47 state=mounted
           *-disk:1
                description: EXT3 volume
                product: ST3500320AS
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 1.0
                serial: bd0feddb-39a5-4e0e-a760-fd3a05b01e1a
                size: 931GiB
                capabilities: journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: ansiversion=5 created=2008-07-11 18:43:02 filesystem=ext3 modified=2008-09-01 12:37:27 mounted=2008-09-01 12:29:56 state=clean
           *-disk:2
                description: ATA Disk
                product: ST3500320AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: SD15
                serial: 5QM21JPE
                size: 465GiB (500GB)
                configuration: ansiversion=5

```

and here is the dmesg ouput for those of you who like reading things:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] Command line: root=UUID=6922929b-6e62-43c5-b2fb-0b4e1e3a787d ro
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000093800 (usable)
[    0.000000]  BIOS-e820: 0000000000093800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffc0000 - 00000000cffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffce000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfffe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000230000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 147) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851872) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 2293760) 2 entries of 3200 used
[    0.000000] end_pfn_map = 2293760
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F9960 checksum 0
[    0.000000] ACPI: RSDP 000F9960, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFFC0000, 0038 (r1 061708 RSDT0906 20080617 MSFT       97)
[    0.000000] ACPI: FACP CFFC0200, 0084 (r2 061708 FACP0906 20080617 MSFT       97)
[    0.000000] ACPI: DSDT CFFC0440, 6E9B (r1  1ADNC 1ADNC001        1 INTL 20051117)
[    0.000000] ACPI: FACS CFFCE000, 0040
[    0.000000] ACPI: APIC CFFC0390, 006C (r1 061708 APIC0906 20080617 MSFT       97)
[    0.000000] ACPI: MCFG CFFC0400, 003C (r1 061708 OEMMCFG  20080617 MSFT       97)
[    0.000000] ACPI: OEMB CFFCE040, 0071 (r1 061708 OEMB0906 20080617 MSFT       97)
[    0.000000] ACPI: HPET CFFC72E0, 0038 (r1 061708 OEMHPET  20080617 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000230000000
[    0.000000] Entering add_active_range(0, 0, 147) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851872) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 2293760) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000230000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  2293760
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      147
[    0.000000]     0:      256 ->   851872
[    0.000000]     0:  1048576 ->  2293760
[    0.000000] On node 0 totalpages: 2096947
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1226 pages reserved
[    0.000000]   DMA zone: 2705 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833496 pages, LIFO batch:31
[    0.000000]   Normal zone: 17024 pages used for memmap
[    0.000000]   Normal zone: 1228160 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 0000000000093000 - 0000000000094000
[    0.000000] swsusp: Registered nosave memory region: 0000000000094000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cffa0000 - 00000000cffc0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cffc0000 - 00000000cffce000
[    0.000000] swsusp: Registered nosave memory region: 00000000cffce000 - 00000000cfff0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfff0000 - 00000000cfffe000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfffe000 - 00000000fff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cfffe000:2ff02000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2064361
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=6922929b-6e62-43c5-b2fb-0b4e1e3a787d ro
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   57.822247] Marking TSC unstable due to TSCs unsynchronized
[   57.822249] time.c: Detected 2400.154 MHz processor.
[   57.823202] Console: colour VGA+ 80x25
[   57.823204] console [tty0] enabled
[   57.826736] Checking aperture...
[   57.826778] CPU 0: aperture @ 4000000 size 32 MB
[   57.826819] Aperture too small (32 MB)
[   57.837726] No AGP bridge found
[   57.837767] Your BIOS doesn't leave a aperture memory hole
[   57.837809] Please enable the IOMMU option in the BIOS setup
[   57.837851] This costs you 64 MB of RAM
[   57.858569] Mapping aperture over 65536 KB of RAM @ 4000000
[   57.858615] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
[   57.910135] Memory: 8183676k/9175040k available (2489k kernel code, 204112k reserved, 1318k data, 320k init)
[   57.910208] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   57.988306] Calibrating delay using timer specific routine.. 4998.16 BogoMIPS (lpj=9996320)
[   57.988410] Security Framework initialized
[   57.988455] SELinux:  Disabled at boot.
[   57.988504] AppArmor: AppArmor initialized
[   57.988547] Failure registering capabilities with primary security module.
[   57.989118] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   57.992441] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   57.993810] Mount-cache hash table entries: 256
[   57.993949] Initializing cgroup subsys ns
[   57.993993] Initializing cgroup subsys cpuacct
[   57.994044] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   57.994087] CPU: L2 Cache: 512K (64 bytes/line)
[   57.994129] CPU 0/0 -> Node 0
[   57.994171] CPU: Physical Processor ID: 0
[   57.994212] CPU: Processor Core ID: 0
[   57.994270] SMP alternatives: switching to UP code
[   57.994792] Early unpacking initramfs... done
[   58.261548] ACPI: Core revision 20070126
[   58.261637] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   58.306361] Using local APIC timer interrupts.
[   58.348011] APIC timer calibration result 12500806
[   58.348012] Detected 12.500 MHz APIC timer.
[   58.348118] SMP alternatives: switching to SMP code
[   58.348574] Booting processor 1/4 APIC 0x1
[   58.359264] Initializing CPU#1
[   58.439923] Calibrating delay using timer specific routine.. 4800.57 BogoMIPS (lpj=9601157)
[   58.439928] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   58.439929] CPU: L2 Cache: 512K (64 bytes/line)
[   58.439931] CPU 1/1 -> Node 0
[   58.439933] CPU: Physical Processor ID: 0
[   58.439934] CPU: Processor Core ID: 1
[   58.440204] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
[   58.440318] SMP alternatives: switching to SMP code
[   58.440992] Booting processor 2/4 APIC 0x2
[   58.451682] Initializing CPU#2
[   58.531786] Calibrating delay using timer specific routine.. 4800.43 BogoMIPS (lpj=9600863)
[   58.531791] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   58.531792] CPU: L2 Cache: 512K (64 bytes/line)
[   58.531794] CPU 2/2 -> Node 0
[   58.531796] CPU: Physical Processor ID: 0
[   58.531797] CPU: Processor Core ID: 2
[   58.532068] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
[   58.532210] SMP alternatives: switching to SMP code
[   58.532889] Booting processor 3/4 APIC 0x3
[   58.543579] Initializing CPU#3
[   58.623649] Calibrating delay using timer specific routine.. 4800.39 BogoMIPS (lpj=9600782)
[   58.623654] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   58.623655] CPU: L2 Cache: 512K (64 bytes/line)
[   58.623657] CPU 3/3 -> Node 0
[   58.623659] CPU: Physical Processor ID: 0
[   58.623660] CPU: Processor Core ID: 3
[   58.623929] AMD Phenom(tm) 9750 Quad-Core Processor stepping 03
[   58.623967] Brought up 4 CPUs
[   58.624429] CPU0 attaching sched-domain:
[   58.624432]  domain 0: span 0f
[   58.624433]   groups: 01 02 04 08
[   58.624436]   domain 1: span 0f
[   58.624437]    groups: 0f
[   58.624439] CPU1 attaching sched-domain:
[   58.624440]  domain 0: span 0f
[   58.624441]   groups: 02 04 08 01
[   58.624443]   domain 1: span 0f
[   58.624444]    groups: 0f
[   58.624445] CPU2 attaching sched-domain:
[   58.624446]  domain 0: span 0f
[   58.624447]   groups: 04 08 01 02
[   58.624449]   domain 1: span 0f
[   58.624450]    groups: 0f
[   58.624452] CPU3 attaching sched-domain:
[   58.624453]  domain 0: span 0f
[   58.624454]   groups: 08 01 02 04
[   58.624456]   domain 1: span 0f
[   58.624457]    groups: 0f
[   58.624675] net_namespace: 120 bytes
[   58.625056] Time: 10:38:29  Date: 09/01/08
[   58.625117] NET: Registered protocol family 16
[   58.625282] ACPI: bus type pci registered
[   58.625374] PCI: Using configuration type 1
[   58.628675] ACPI: EC: Look up EC in DSDT
[   58.632128] ACPI: Interpreter enabled
[   58.632170] ACPI: (supports S0 S1 S3 S4 S5)
[   58.632407] ACPI: Using IOAPIC for interrupt routing
[   58.632667] Error attaching device data
[   58.632711] Error attaching device data
[   58.632754] Error attaching device data
[   58.632797] Error attaching device data
[   58.638836] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   58.640302] PCI: Transparent bridge - 0000:00:14.4
[   58.640368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   58.640579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   58.640661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[   58.640751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[   58.640847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   58.643588] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 *15)
[   58.644160] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[   58.644720] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   58.645274] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   58.645833] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   58.646464] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[   58.646793] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[   58.647352] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[   58.647939] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  EB, should be E2 [20070126]
[   58.648064] Linux Plug and Play Support v0.97 (c) Adam Belay
[   58.648123] pnp: PnP ACPI init
[   58.648168] ACPI: bus type pnp registered
[   58.651294] pnp: PnP ACPI: found 13 devices
[   58.651336] ACPI: ACPI bus type pnp unregistered
[   58.651524] PCI: Using ACPI for IRQ routing
[   58.652253] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   58.671592] NET: Registered protocol family 8
[   58.671634] NET: Registered protocol family 20
[   58.671724] PCI-DMA: Disabling AGP.
[   58.672753] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   58.672801] PCI-DMA: using GART IOMMU.
[   58.672847] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   58.673817] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   58.674045] hpet0: 4 32-bit timers, 14318180 Hz
[   58.675129] AppArmor: AppArmor Filesystem Enabled
[   58.675584] Time: hpet clocksource has been installed.
[   58.675639] Switched to high resolution mode on CPU 0
[   58.675899] Switched to high resolution mode on CPU 2
[   58.675904] Switched to high resolution mode on CPU 1
[   58.675908] Switched to high resolution mode on CPU 3
[   58.683616] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   58.683661] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   58.683710] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   58.683754] system 00:09: ioport range 0x40b-0x40b has been reserved
[   58.683796] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[   58.683839] system 00:09: ioport range 0xc00-0xc01 has been reserved
[   58.683882] system 00:09: ioport range 0xc14-0xc14 has been reserved
[   58.683925] system 00:09: ioport range 0xc50-0xc51 has been reserved
[   58.683968] system 00:09: ioport range 0xc52-0xc52 has been reserved
[   58.684011] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[   58.684058] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[   58.684101] system 00:09: ioport range 0xcd0-0xcd1 has been reserved
[   58.684144] system 00:09: ioport range 0xcd2-0xcd3 has been reserved
[   58.684186] system 00:09: ioport range 0xcd4-0xcd5 has been reserved
[   58.684229] system 00:09: ioport range 0xcd6-0xcd7 has been reserved
[   58.684272] system 00:09: ioport range 0xcd8-0xcdf has been reserved
[   58.684315] system 00:09: ioport range 0x800-0x89f has been reserved
[   58.684358] system 00:09: ioport range 0xb10-0xb1f has been reserved
[   58.684400] system 00:09: ioport range 0x900-0x90f has been reserved
[   58.684443] system 00:09: ioport range 0x910-0x91f has been reserved
[   58.684487] system 00:09: ioport range 0xfe00-0xfefe has been reserved
[   58.684530] system 00:09: iomem range 0xffb80000-0xffbfffff has been reserved
[   58.684576] system 00:0a: ioport range 0x600-0x6df has been reserved
[   58.684619] system 00:0a: ioport range 0xae0-0xaef has been reserved
[   58.684665] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   58.684712] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   58.684755] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[   58.684798] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   58.684841] system 00:0c: iomem range 0x100000-0xcfffffff could not be reserved
[   58.684887] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[   58.685234] PCI: Bridge: 0000:00:02.0
[   58.685276]   IO window: b000-bfff
[   58.685319]   MEM window: fe800000-fe8fffff
[   58.685361]   PREFETCH window: d0000000-dfffffff
[   58.685404] PCI: Bridge: 0000:00:05.0
[   58.685446]   IO window: c000-cfff
[   58.685488]   MEM window: fe900000-fe9fffff
[   58.685530]   PREFETCH window: disabled.
[   58.685573] PCI: Bridge: 0000:00:09.0
[   58.685614]   IO window: d000-dfff
[   58.685656]   MEM window: fea00000-feafffff
[   58.685699]   PREFETCH window: disabled.
[   58.685742] PCI: Bridge: 0000:00:14.4
[   58.685784]   IO window: e000-efff
[   58.685828]   MEM window: feb00000-febfffff
[   58.685872]   PREFETCH window: disabled.
[   58.685931] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   58.686016] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   58.686023] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   58.686106] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   58.686112] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   58.686196] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   58.686209] NET: Registered protocol family 2
[   58.719702] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   58.720989] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   58.723881] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   58.724279] TCP: Hash tables configured (established 524288 bind 65536)
[   58.724322] TCP reno registered
[   58.735581] checking if image is initramfs... it is
[   59.214167] Freeing initrd memory: 7804k freed
[   59.217995] audit: initializing netlink socket (disabled)
[   59.218049] audit(1220265509.360:1): initialized
[   59.219869] VFS: Disk quotas dquot_6.5.1
[   59.219965] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   59.220103] io scheduler noop registered
[   59.220145] io scheduler anticipatory registered
[   59.220187] io scheduler deadline registered
[   59.220312] io scheduler cfq registered (default)
[   59.344126] Boot video device is 0000:01:00.0
[   59.344266] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.344289] assign_interrupt_mode Found MSI capability
[   59.344357] Allocate Port Service[0000:00:02.0:pcie00]
[   59.344413] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   59.344434] assign_interrupt_mode Found MSI capability
[   59.344495] Allocate Port Service[0000:00:05.0:pcie00]
[   59.344544] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   59.344565] assign_interrupt_mode Found MSI capability
[   59.344626] Allocate Port Service[0000:00:09.0:pcie00]
[   59.364229] Real Time Clock Driver v1.12ac
[   59.364412] hpet_resources: 0xfed00000 is busy
[   59.364451] Linux agpgart interface v0.102
[   59.364493] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   59.364660] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.365114] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.365676] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   59.365763] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   59.365894] PNP: No PS/2 controller found. Probing ports directly.
[   59.367983] serio: i8042 KBD port at 0x60,0x64 irq 1
[   59.368039] serio: i8042 AUX port at 0x60,0x64 irq 12
[   59.388034] mice: PS/2 mouse device common for all mice
[   59.388110] cpuidle: using governor ladder
[   59.388155] cpuidle: using governor menu
[   59.388305] NET: Registered protocol family 1
[   59.388433] registered taskstats version 1
[   59.388581]   Magic number: 8:731:627
[   59.388623]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:76
[   59.388747] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   59.388794] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   59.388836] EDD information not available.
[   59.388886] Freeing unused kernel memory: 320k freed
[   59.524537] fuse init (API version 7.9)
[   59.540324] ACPI: duty_cycle spans bit 4
[   59.644689] SCSI subsystem initialized
[   59.651681] usbcore: registered new interface driver usbfs
[   59.651744] usbcore: registered new interface driver hub
[   59.651811] usbcore: registered new device driver usb
[   59.652434] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   59.652461] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   59.653145] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   59.653362] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   59.653434] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe7fe000
[   59.653510] libata version 3.00 loaded.
[   59.714248] usb usb1: configuration #1 chosen from 1 choice
[   59.714311] hub 1-0:1.0: USB hub found
[   59.714360] hub 1-0:1.0: 2 ports detected
[   59.760323] Floppy drive(s): fd0 is 1.44M
[   59.781660] FDC 0 is a post-1991 82077
[   59.813883] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   59.814562] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   59.814659] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   59.814722] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe7fd000
[   59.873970] usb usb2: configuration #1 chosen from 1 choice
[   59.874029] hub 2-0:1.0: USB hub found
[   59.874077] hub 2-0:1.0: 2 ports detected
[   59.973609] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   59.974298] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   59.974411] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   59.974474] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe7fc000
[   60.033733] usb usb3: configuration #1 chosen from 1 choice
[   60.033794] hub 3-0:1.0: USB hub found
[   60.033842] hub 3-0:1.0: 2 ports detected
[   60.137362] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   60.138074] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   60.138171] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   60.138232] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe7fb000
[   60.197476] usb usb4: configuration #1 chosen from 1 choice
[   60.197534] hub 4-0:1.0: USB hub found
[   60.197581] hub 4-0:1.0: 2 ports detected
[   60.301108] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   60.301726] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   60.301824] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   60.301886] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe7fa000
[   60.361224] usb usb5: configuration #1 chosen from 1 choice
[   60.361285] hub 5-0:1.0: USB hub found
[   60.361334] hub 5-0:1.0: 2 ports detected
[   60.465184] ahci 0000:00:12.0: version 3.0
[   60.465209] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   60.465859] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   60.465909] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   60.780320] usb 5-1: new low speed USB device using ohci_hcd and address 2
[   60.997127] usb 5-1: configuration #1 chosen from 1 choice
[   61.307508] usb 5-2: new low speed USB device using ohci_hcd and address 3
[   61.467295] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   61.467343] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   61.467631] scsi0 : ahci
[   61.467722] scsi1 : ahci
[   61.467803] scsi2 : ahci
[   61.467874] scsi3 : ahci
[   61.467966] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 22
[   61.468014] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 22
[   61.468061] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 22
[   61.468108] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 22
[   61.524317] usb 5-2: configuration #1 chosen from 1 choice
[   61.526336] usbcore: registered new interface driver hiddev
[   61.532395] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1:1.0/input/input1
[   61.544644] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:13.4-1
[   61.551350] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input2
[   61.568608] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.4-2
[   61.568809] usbcore: registered new interface driver usbhid
[   61.568852] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   61.942520] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   61.943997] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   61.944043] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   61.945800] ata1.00: configured for UDMA/133
[   62.417780] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   62.419195] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   62.419239] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   62.421024] ata2.00: configured for UDMA/133
[   62.893050] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   62.894499] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   62.894542] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   62.896357] ata3.00: configured for UDMA/133
[   63.205547] ata4: SATA link down (SStatus 0 SControl 300)
[   63.205668] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   63.205778] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   63.205878] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   63.206018] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   63.206133] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   63.206196] scsi4 : pata_atiixp
[   63.206281] scsi5 : pata_atiixp
[   63.207134] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   63.207178] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   63.213112] Driver 'sd' needs updating - please use bus_type methods
[   63.222061] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   63.222111] sd 0:0:0:0: [sda] Write Protect is off
[   63.222153] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   63.222163] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.222249] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   63.222296] sd 0:0:0:0: [sda] Write Protect is off
[   63.222338] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   63.222353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.222400]  sda: sda1 sda2 < sda5 > sda3
[   63.257555] sd 0:0:0:0: [sda] Attached SCSI disk
[   63.257635] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.257685] sd 1:0:0:0: [sdb] Write Protect is off
[   63.257728] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   63.257738] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.257814] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.257864] sd 1:0:0:0: [sdb] Write Protect is off
[   63.257908] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   63.257921] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.257975]  sdb: unknown partition table
[   63.262523] sd 1:0:0:0: [sdb] Attached SCSI disk
[   63.262589] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   63.262637] sd 2:0:0:0: [sdc] Write Protect is off
[   63.262679] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   63.262688] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.262753] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   63.262800] sd 2:0:0:0: [sdc] Write Protect is off
[   63.262847] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   63.262856] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   63.262909]  sdc: unknown partition table
[   63.270383] sd 2:0:0:0: [sdc] Attached SCSI disk
[   63.273308] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   63.273365] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   63.273417] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   63.516218] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   63.516910] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   63.517007] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   63.517090] ehci_hcd 0000:00:13.5: debug port 1
[   63.517142] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe7ff000
[   63.517243] usb 5-1: USB disconnect, address 2
[   63.532544] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   63.532676] usb usb6: configuration #1 chosen from 1 choice
[   63.532736] hub 6-0:1.0: USB hub found
[   63.532781] hub 6-0:1.0: 10 ports detected
[   63.631998] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 23 (level, low) -> IRQ 23
[   63.665342] usb 5-2: USB disconnect, address 3
[   63.685149] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   63.690291] r8169 Gigabit Ethernet driver 2.2LK loaded
[   63.690360] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   63.690458] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   63.690682] eth0: RTL8168b/8111b at 0xffffc20001752000, 00:1d:92:65:08:35, XID 38000000 IRQ 508
[   63.697106] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   63.697153] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   63.719570] device-mapper: uevent: version 1.0.3
[   63.719635] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   64.526499] usb 5-1: new low speed USB device using ohci_hcd and address 4
[   64.743523] usb 5-1: configuration #1 chosen from 1 choice
[   64.751580] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1:1.0/input/input3
[   64.767668] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:13.4-1
[   64.959440] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc10000153fc3e]
[   65.081645] usb 5-2: new low speed USB device using ohci_hcd and address 5
[   65.298690] usb 5-2: configuration #1 chosen from 1 choice
[   65.307732] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input4
[   65.338777] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.4-2
[   68.887878] kjournald starting.  Commit interval 5 seconds
[   68.887883] EXT3-fs: mounted filesystem with ordered data mode.
[   73.707598] ip_tables: (C) 2000-2006 Netfilter Core Team
[   73.741965] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   74.085300] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   74.094206] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.225081] input: Power Button (FF) as /devices/virtual/input/input5
[   74.244418] ACPI: Power Button (FF) [PWRF]
[   74.244540] input: Power Button (CM) as /devices/virtual/input/input6
[   74.276377] ACPI: Power Button (CM) [PWRB]
[   74.334818] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   74.375328] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   74.397538] ACPI: WMI-Acer: Mapper loaded
[   74.572469] r8169: eth0: link up
[   74.572519] r8169: eth0: link up
[   74.578645] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   74.605203] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   74.641246] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 19 (level, low) -> IRQ 19
[   74.641907] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   74.717939] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   74.739301] [fglrx]   vendor: 1002 device: 9442 count: 1
[   74.739446] [fglrx] Maximum main memory to use for locked dma buffers: 7766 MBytes.
[   74.740643] [fglrx] PAT is enabled successfully!
[   74.740746] [fglrx] module loaded - fglrx 8.50.3 [Jun  2 2008] with 1 minors
[   76.526264] NET: Registered protocol family 17
[   76.602812] lp: driver loaded but no devices found
[   76.704604] Adding 19800072k swap on /dev/sda5.  Priority:-1 extents:1 across:19800072k
[   77.034541] EXT3 FS on sda3, internal journal
[   77.807248] kjournald starting.  Commit interval 5 seconds
[   77.807703] EXT3 FS on sda1, internal journal
[   77.807708] EXT3-fs: mounted filesystem with ordered data mode.
[   77.846128] kjournald starting.  Commit interval 5 seconds
[   77.854193] EXT3 FS on dm-0, internal journal
[   77.854196] EXT3-fs: mounted filesystem with ordered data mode.
[   78.763382] No dock devices found.
[   80.809077] NET: Registered protocol family 10
[   80.809273] lo: Disabled Privacy Extensions
[   81.743522] ppdev: user-space parallel port driver
[   81.874517] audit(1220265532.364:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6187 profile="/usr/sbin/cupsd" namespace="default"
[   84.455481] Bluetooth: Core ver 2.11
[   84.455559] NET: Registered protocol family 31
[   84.455560] Bluetooth: HCI device and connection manager initialized
[   84.455564] Bluetooth: HCI socket layer initialized
[   84.469526] Bluetooth: L2CAP ver 2.9
[   84.469531] Bluetooth: L2CAP socket layer initialized
[   84.510055] Bluetooth: RFCOMM socket layer initialized
[   84.510068] Bluetooth: RFCOMM TTY layer initialized
[   84.510070] Bluetooth: RFCOMM ver 1.8
[   85.640045] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   86.557826] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   86.557831] [fglrx] Reserved FB block: Unshared offset:ff7f000, size:80000 
[   91.034558] eth0: no IPv6 routers present
[   92.116584] hda-intel: Invalid position buffer, using LPIB read method instead.

```

hopefully someone can point me in the right direction, the DVD-RW is plugged into the promise controller not the SB600 controller.  I would try it in the SB600, but I would like to try out the other controller as I would at some point like to utilise my eSATA ports both of which are located on the promise controller.

---

### Post by porchrat on 2008-09-01
Is there anyone out there that can help?

---

### Post by porchrat on 2008-09-01
Just in case anyone is reading this I have moved the DVD-RW drive to the SB600 controller now and it recognises it straight away.  I'm starting to get worried that my promise controller may be faulty.

Are there any suggestions or experiences anyone can offer?  Can ubuntu run these 2 particular harddrive controllers at once?  I haven't read anything that would lead me to believe it can't, but one never knows.

---

### Post by porchrat on 2008-09-01
Nevermind...figured out that there are currently no drivers for this promise controller from the manufacturer that runs with a 2.6.24 kernel.

---


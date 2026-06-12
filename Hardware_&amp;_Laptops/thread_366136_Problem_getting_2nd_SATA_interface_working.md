---
title: "Problem getting 2nd SATA interface working"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by HiredGun79 on 2007-02-20
Hello,

I'm trying to get a file server set up with 5 SATA II drives. My motherboard has two 4-port SATA controllers - an Intel ICH7 that uses the pii driver and a Marvell 6145 controller. The Marvell interface is not working. I've tried a variety of drivers in the kernel for the Marvell, including the legacy driver. I installed Ubuntu Server, then recompiled the 2.6.20 kernel for my system.

Since I'm pretty sure I have the right driver for the Marvell in the kernel, I have a suspicion that it's not an incorrect driver, that it's some sort of conflict in the motherboard. Oh yeah, motherboard is a new Intel 975X2 board. 

I need to get the 5th drive working so I can complete my file server and get a nice RAID 5 running to do some video editing, photo sharing, etc. etc.

In the next three messages, I'll paste the output from dmesg, lspci -vvvxxx and my kernel .config file (I'll provide .config file if needed - it's HUGE!).

Thanks for all the help in advance.

Take care and have a great day,
Tony

---

### Post by HiredGun79 on 2007-02-20
dmesg output
------------------------------------------

[    0.000000] Linux version 2.6.20-latest3 (root@fileserver) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #1 SMP Mon Feb 19 11:49:02 EST 2007
[    0.000000] Command line: root=/dev/sda1 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ee1b000 (usable)
[    0.000000]  BIOS-e820: 000000001ee1b000 - 000000001eeb4000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001eeb4000 - 000000001fd8a000 (usable)
[    0.000000]  BIOS-e820: 000000001fd8a000 - 000000001fd92000 (reserved)
[    0.000000]  BIOS-e820: 000000001fd92000 - 000000001fe2c000 (usable)
[    0.000000]  BIOS-e820: 000000001fe2c000 - 000000001fe30000 (reserved)
[    0.000000]  BIOS-e820: 000000001fe30000 - 000000001feac000 (usable)
[    0.000000]  BIOS-e820: 000000001feac000 - 000000001feae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feae000 - 000000001fef2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fef2000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (usable)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 143) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 126491) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 126644, 130442) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130450, 130604) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130608, 130732) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130815, 130816) 5 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 INTEL                                 ) @ 0x00000000000fe020
[    0.000000] ACPI: RSDT (v001 INTEL  D975XBX2 0x0000091d      0x01000013) @ 0x000000001fefd038
[    0.000000] ACPI: FADT (v001 INTEL  D975XBX2 0x0000091d MSFT 0x01000013) @ 0x000000001fefc000
[    0.000000] ACPI: MADT (v001 INTEL  D975XBX2 0x0000091d MSFT 0x01000013) @ 0x000000001fef7000
[    0.000000] ACPI: WDDT (v001 INTEL  D975XBX2 0x0000091d MSFT 0x01000013) @ 0x000000001fef6000
[    0.000000] ACPI: MCFG (v001 INTEL  D975XBX2 0x0000091d MSFT 0x01000013) @ 0x000000001fef5000
[    0.000000] ACPI: SSDT (v001 INTEL     CpuPm 0x0000091d MSFT 0x01000013) @ 0x000000001fef4000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu0Ist 0x0000091d MSFT 0x01000013) @ 0x000000001fef3000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu1Ist 0x0000091d MSFT 0x01000013) @ 0x000000001fef2000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu2Ist 0x0000091d MSFT 0x01000013) @ 0x000000001fead000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu3Ist 0x0000091d MSFT 0x01000013) @ 0x000000001feac000
[    0.000000] ACPI: DSDT (v001 INTEL  D975XBX2 0x0000091d MSFT 0x01000013) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001ff00000
[    0.000000] Entering add_active_range(0, 0, 143) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 126491) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 126644, 130442) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130450, 130604) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130608, 130732) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 130815, 130816) 5 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001ff00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0:        0 ->      143
[    0.000000]     0:      256 ->   126491
[    0.000000]     0:   126644 ->   130442
[    0.000000]     0:   130450 ->   130604
[    0.000000]     0:   130608 ->   130732
[    0.000000]     0:   130815 ->   130816
[    0.000000] On node 0 totalpages: 130455
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1235 pages reserved
[    0.000000]   DMA zone: 2692 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1732 pages used for memmap
[    0.000000]   DMA32 zone: 124740 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000008f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Nosave address range: 000000001ee1b000 - 000000001eeb4000
[    0.000000] Nosave address range: 000000001fd8a000 - 000000001fd92000
[    0.000000] Nosave address range: 000000001fe2c000 - 000000001fe30000
[    0.000000] Nosave address range: 000000001feac000 - 000000001feae000
[    0.000000] Nosave address range: 000000001feae000 - 000000001fef2000
[    0.000000] Nosave address range: 000000001fef2000 - 000000001feff000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 33920 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 127432
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[   30.450849] Console: colour VGA+ 80x25
[   30.451185] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   30.451444] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   30.451495] Checking aperture...
[   30.456333] Memory: 504152k/523264k available (2512k kernel code, 17668k reserved, 1429k data, 308k init)
[   30.535938] Calibrating delay using timer specific routine.. 5605.48 BogoMIPS (lpj=11210962)
[   30.536011] Security Framework v1.0.0 initialized
[   30.536017] SELinux:  Disabled at boot.
[   30.536050] Mount-cache hash table entries: 256
[   30.536223] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   30.536226] CPU: L2 cache: 2048K
[   30.536229] CPU 0/0 -> Node 0
[   30.536231] using mwait in idle threads.
[   30.536233] CPU: Physical Processor ID: 0
[   30.536235] CPU: Processor Core ID: 0
[   30.536246] CPU0: Thermal monitoring enabled (TM1)
[   30.536260] SMP alternatives: switching to UP code
[   30.536529] ACPI: Core revision 20060707
[   30.581166] Using local APIC timer interrupts.
[   30.616814] result 12500671
[   30.616816] Detected 12.500 MHz APIC timer.
[   30.620072] SMP alternatives: switching to SMP code
[   30.620108] Booting processor 1/2 APIC 0x1
[   30.630739] Initializing CPU#1
[   30.707613] Calibrating delay using timer specific routine.. 5600.71 BogoMIPS (lpj=11201426)
[   30.707625] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   30.707627] CPU: L2 cache: 2048K
[   30.707630] CPU 1/1 -> Node 0
[   30.707632] CPU: Physical Processor ID: 0
[   30.707634] CPU: Processor Core ID: 1
[   30.707645] CPU1: Thermal monitoring enabled (TM1)
[   30.708042]               Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
[   30.711633] Brought up 2 CPUs
[   30.711674] testing NMI watchdog ... OK.
[   30.751648] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   30.751655] time.c: Detected 2800.156 MHz processor.
[   31.094394] migration_cost=1557
[   31.094784] NET: Registered protocol family 16
[   31.094881] ACPI: bus type pci registered
[   31.094888] PCI: Using configuration type 1
[   31.099798] ACPI: Interpreter enabled
[   31.099801] ACPI: Using IOAPIC for interrupt routing
[   31.100332] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.100340] PCI: Probing PCI hardware (bus 00)
[   31.100362] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   31.102473] Boot video device is 0000:01:00.0
[   31.103124] PCI: Transparent bridge - 0000:00:1e.0
[   31.103196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.107815] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   31.108441] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   31.108725] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   31.109002] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   31.109276] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   31.109562] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   31.109839] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   31.110116] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   31.110390] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   31.112012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   31.112557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   31.112867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[   31.114267] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.114487] SCSI subsystem initialized
[   31.114533] libata version 2.00 loaded.
[   31.114631] PCI: Using ACPI for IRQ routing
[   31.114634] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.114742] PCI-GART: No AMD northbridge found.
[   31.115157] PCI: Bridge: 0000:00:01.0
[   31.115160]   IO window: 3000-3fff
[   31.115165]   MEM window: 30300000-303fffff
[   31.115168]   PREFETCH window: 20000000-2fffffff
[   31.115172] PCI: Bridge: 0000:00:1c.0
[   31.115174]   IO window: disabled.
[   31.115179]   MEM window: 30500000-305fffff
[   31.115183]   PREFETCH window: disabled.
[   31.115188] PCI: Bridge: 0000:00:1c.4
[   31.115191]   IO window: 2000-2fff
[   31.115197]   MEM window: 30200000-302fffff
[   31.115201]   PREFETCH window: 30600000-306fffff
[   31.115206] PCI: Bridge: 0000:00:1c.5
[   31.115209]   IO window: 1000-1fff
[   31.115214]   MEM window: 30100000-301fffff
[   31.115217]   PREFETCH window: disabled.
[   31.115223] PCI: Bridge: 0000:00:1e.0
[   31.115224]   IO window: disabled.
[   31.115229]   MEM window: 30000000-300fffff
[   31.115233]   PREFETCH window: disabled.
[   31.115251] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.115256] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.115275] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.115281] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.115298] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   31.115303] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.115321] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   31.115326] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   31.115337] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.115382] NET: Registered protocol family 2
[   31.152624] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   31.152733] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[   31.152830] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[   31.152876] TCP: Hash tables configured (established 16384 bind 8192)
[   31.152879] TCP reno registered
[   31.164709] checking if image is initramfs... it is
[   31.566416] Freeing initrd memory: 4624k freed
[   31.570082] audit: initializing netlink socket (disabled)
[   31.570097] audit(1171907684.092:1): initialized
[   31.570407] VFS: Disk quotas dquot_6.5.1
[   31.570444] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   31.570517] io scheduler noop registered
[   31.570520] io scheduler anticipatory registered
[   31.570522] io scheduler deadline registered
[   31.570557] io scheduler cfq registered (default)
[   31.570961] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.571008] assign_interrupt_mode Found MSI capability
[   31.571055] Allocate Port Service[0000:00:01.0:pcie00]
[   31.571183] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.571226] assign_interrupt_mode Found MSI capability
[   31.571259] Allocate Port Service[0000:00:1c.0:pcie00]
[   31.571313] Allocate Port Service[0000:00:1c.0:pcie02]
[   31.571439] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.571485] assign_interrupt_mode Found MSI capability
[   31.571521] Allocate Port Service[0000:00:1c.4:pcie00]
[   31.571582] Allocate Port Service[0000:00:1c.4:pcie02]
[   31.571705] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   31.571751] assign_interrupt_mode Found MSI capability
[   31.571787] Allocate Port Service[0000:00:1c.5:pcie00]
[   31.571852] Allocate Port Service[0000:00:1c.5:pcie02]
[   31.572399] vga16fb: initializing
[   31.572403] vga16fb: mapped to 0xffff8100000a0000
[   31.687203] Console: switching to colour frame buffer device 80x30
[   31.690386] fb0: VGA16 VGA frame buffer device
[   31.726607] Real Time Clock Driver v1.12ac
[   31.726675] Linux agpgart interface v0.101 (c) Dave Jones
[   31.726738] intelfb: Framebuffer driver for Intel(R) 830M/845G/852GM/855GM/865G/915G/915GM/945G/945GM chipsets
[   31.726746] intelfb: Version 0.9.4
[   31.726799] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.726945] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.728256] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.728259] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2
[   31.728262] Copyright (c) 1999-2006 Intel Corporation.
[   31.728349] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.728365] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   31.785634] e1000: 0000:04:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:26:28:69
[   31.846289] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   31.846411] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.846416] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.846619] ata_piix 0000:00:1f.1: version 2.00ac7
[   31.846632] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   31.846647] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.846721] ata1: PATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x40B0 irq 14
[   31.846762] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x40B8 irq 15
[   31.846780] scsi0 : ata_piix
[   32.012163] ATA: abnormal status 0x7F on port 0x1F7
[   32.173834] ata1.01: ATAPI, max MWDMA2
[   32.337534] ata1.01: configured for MWDMA2
[   32.337548] scsi1 : ata_piix
[   32.337637] ata2: port disabled. ignoring.
[   32.339296] scsi 0:0:1:0: CD-ROM                     32X12X48 CD-RW   1.11 PQ: 0 ANSI: 5
[   32.339424] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   32.339457] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   32.339476] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   32.339504] ata3: SATA max UDMA/133 cmd 0x40C8 ctl 0x40E6 bmdma 0x40A0 irq 19
[   32.339533] ata4: SATA max UDMA/133 cmd 0x40C0 ctl 0x40E2 bmdma 0x40A8 irq 19
[   32.339546] scsi2 : ata_piix
[   32.501205] ata3.00: ATA-7, max UDMA/133, 156301488 sectors: LBA48 NCQ (depth 0/32)
[   32.501209] ata3.00: ata3: dev 0 multi count 16
[   32.509196] ata3.01: ATA-7, max UDMA/133, 625142448 sectors: LBA48 NCQ (depth 0/32)
[   32.509200] ata3.01: ata3: dev 1 multi count 16
[   32.517197] ata3.00: configured for UDMA/133
[   32.525198] ata3.01: configured for UDMA/133
[   32.525203] scsi3 : ata_piix
[   32.688900] ata4.00: ATA-7, max UDMA/133, 625142448 sectors: LBA48 NCQ (depth 0/32)
[   32.688903] ata4.00: ata4: dev 0 multi count 16
[   32.696892] ata4.01: ATA-7, max UDMA/133, 625142448 sectors: LBA48 NCQ (depth 0/32)
[   32.696894] ata4.01: ata4: dev 1 multi count 16
[   32.704893] ata4.00: configured for UDMA/133
[   32.712894] ata4.01: configured for UDMA/133
[   32.712982] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-00MS 10.0 PQ: 0 ANSI: 5
[   32.713133] scsi 2:0:1:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   32.713279] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   32.713431] scsi 3:0:1:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   32.713581] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.713595] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   32.713623] ata5: PATA max UDMA/100 cmd 0x2018 ctl 0x2026 bmdma 0x2000 irq 16
[   32.713653] ata6: PATA max UDMA/133 cmd 0x2010 ctl 0x2022 bmdma 0x2008 irq 16
[   32.713665] scsi4 : pata_marvell
[   32.713741] BAR5:00:04 01:7F 02:22 03:C8 04:02 05:00 06:00 07:80 08:00 09:00 0A:00 0B:00 0C:1F 0D:00 0E:00 0F:00 
[   32.878655] ATA: abnormal status 0x7F on port 0x201F
[   32.878668] scsi5 : pata_marvell
[   32.878730] BAR5:00:04 01:7F 02:22 03:C8 04:02 05:00 06:00 07:80 08:00 09:00 0A:00 0B:00 0C:1F 0D:00 0E:00 0F:00 
[   33.042342] ATA: abnormal status 0x7F on port 0x2017
[   33.042477] PNP: No PS/2 controller found. Probing ports directly.
[   33.045359] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.045364] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.045506] mice: PS/2 mouse device common for all mice
[   33.045562] md: linear personality registered for level -1
[   33.045565] md: raid0 personality registered for level 0
[   33.045567] md: raid1 personality registered for level 1
[   33.045569] md: raid10 personality registered for level 10
[   33.092836] input: AT Translated Set 2 keyboard as /class/input/input0
[   33.111145] raid6: int64x1   1148 MB/s
[   33.179017] raid6: int64x2   1660 MB/s
[   33.246888] raid6: int64x4   2178 MB/s
[   33.314776] raid6: int64x8   1518 MB/s
[   33.382633] raid6: sse2x1    2096 MB/s
[   33.450502] raid6: sse2x2    3064 MB/s
[   33.518393] raid6: sse2x4    2682 MB/s
[   33.518396] raid6: using algorithm sse2x2 (3064 MB/s)
[   33.518398] md: raid6 personality registered for level 6
[   33.518401] md: raid5 personality registered for level 5
[   33.518403] md: raid4 personality registered for level 4
[   33.518406] raid5: automatically using best checksumming function: generic_sse
[   33.538338]    generic_sse:  4278.000 MB/sec
[   33.538341] raid5: using function: generic_sse (4278.000 MB/sec)
[   33.538438] TCP cubic registered
[   33.538450] NET: Registered protocol family 1
[   33.538457] NET: Registered protocol family 8
[   33.538460] NET: Registered protocol family 20
[   33.538652] ACPI: (supports S0 S1 S3 S4 S5)
[   33.538710] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   33.538790] Freeing unused kernel memory: 308k freed
[   33.610584] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   33.610594] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   34.026262] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   34.026281] sda: Write Protect is off
[   34.026284] sda: Mode Sense: 00 3a 00 00
[   34.026311] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.026377] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   34.026393] sda: Write Protect is off
[   34.026395] sda: Mode Sense: 00 3a 00 00
[   34.026420] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.026426]  sda: sda1 sda2 < sda5 >
[   34.052397] sd 2:0:0:0: Attached scsi disk sda
[   34.053696] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   34.053714] sdb: Write Protect is off
[   34.053717] sdb: Mode Sense: 00 3a 00 00
[   34.053742] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.053801] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   34.053816] sdb: Write Protect is off
[   34.053819] sdb: Mode Sense: 00 3a 00 00
[   34.053844] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.053847]  sdb:
[   34.067592] sd 2:0:1:0: Attached scsi disk sdb
[   34.069162] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   34.069179] sdc: Write Protect is off
[   34.069181] sdc: Mode Sense: 00 3a 00 00
[   34.069206] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.069260] SCSI device sdc: 625142448 512-byte hdwr sectors (320073 MB)
[   34.069275] sdc: Write Protect is off
[   34.069278] sdc: Mode Sense: 00 3a 00 00
[   34.069302] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.069306]  sdc:
[   34.083352] sd 3:0:0:0: Attached scsi disk sdc
[   34.084778] SCSI device sdd: 625142448 512-byte hdwr sectors (320073 MB)
[   34.084796] sdd: Write Protect is off
[   34.084799] sdd: Mode Sense: 00 3a 00 00
[   34.084824] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.084886] SCSI device sdd: 625142448 512-byte hdwr sectors (320073 MB)
[   34.084900] sdd: Write Protect is off
[   34.084903] sdd: Mode Sense: 00 3a 00 00
[   34.084928] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.084931]  sdd:
[   34.096975] sd 3:0:1:0: Attached scsi disk sdd
[   34.383620] ide0: I/O resource 0x3F6-0x3F6 not free.
[   34.383779] ide0: ports already in use, skipping probe
[   34.383934] ide1: I/O resource 0x376-0x376 not free.
[   34.384085] ide1: ports already in use, skipping probe
[   34.420754] usbcore: registered new interface driver usbfs
[   34.420786] usbcore: registered new interface driver hub
[   34.424896] usbcore: registered new device driver usb
[   34.426845] ieee1394: Initialized config rom entry `ip1394'
[   34.428006] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   34.478115] USB Universal Host Controller Interface driver v3.0
[   34.478713] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[30004000-300047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   34.478893] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   34.478909] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.478913] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.479537] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   34.479567] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00004080
[   34.480216] usb usb1: configuration #1 chosen from 1 choice
[   34.480426] hub 1-0:1.0: USB hub found
[   34.480434] hub 1-0:1.0: 2 ports detected
[   34.583484] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   34.583501] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.583505] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.583542] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   34.583573] ehci_hcd 0000:00:1d.7: debug port 1
[   34.583580] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   34.583587] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x30404400
[   34.587457] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.587550] usb usb2: configuration #1 chosen from 1 choice
[   34.587581] hub 2-0:1.0: USB hub found
[   34.587588] hub 2-0:1.0: 8 ports detected
[   34.692290] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   34.692302] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.692306] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.692337] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   34.692363] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004060
[   34.692472] usb usb3: configuration #1 chosen from 1 choice
[   34.692499] hub 3-0:1.0: USB hub found
[   34.692506] hub 3-0:1.0: 2 ports detected
[   34.798612] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   34.798624] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.798628] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.798653] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   34.798678] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004040
[   34.798784] usb usb4: configuration #1 chosen from 1 choice
[   34.798812] hub 4-0:1.0: USB hub found
[   34.798819] hub 4-0:1.0: 2 ports detected
[   34.902396] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   34.902407] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   34.902411] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   34.902440] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   34.902463] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00004020
[   34.902562] usb usb5: configuration #1 chosen from 1 choice
[   34.902589] hub 5-0:1.0: USB hub found
[   34.902595] hub 5-0:1.0: 2 ports detected
[   35.045685] Attempting manual resume
[   35.080135] kjournald starting.  Commit interval 5 seconds
[   35.080147] EXT3-fs: mounted filesystem with ordered data mode.
[   35.747103] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001bc8ac1]
[   38.356372] input: PC Speaker as /class/input/input1
[   38.405039] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.411431] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.031301] scsi 0:0:1:0: Attached scsi generic sg0 type 5
[   39.031333] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   39.031360] sd 2:0:1:0: Attached scsi generic sg2 type 0
[   39.031385] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   39.031413] sd 3:0:1:0: Attached scsi generic sg4 type 0
[   39.065000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   39.065029] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   39.073744] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   39.073751] Uniform CD-ROM driver Revision: 3.20
[   39.073819] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   39.105685] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   39.327523] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[   39.916580] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[   39.917115] parport0: irq 7 detected
[   40.011039] lp0: using parport0 (polling).
[   40.185091] NET: Registered protocol family 17
[   40.264312] Adding 1485972k swap on /dev/disk/by-uuid/42d8baf2-5ed1-45b4-9f3d-92a8795948b3.  Priority:-1 extents:1 across:1485972k
[   40.369620] EXT3 FS on sda1, internal journal
[   44.883621] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   45.023105] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   45.032252] NFSD: starting 90-second grace period
[   45.531983] NET: Registered protocol family 10
[   45.532099] lo: Disabled Privacy Extensions
[   56.137177] eth0: no IPv6 routers present

---

### Post by HiredGun79 on 2007-02-20
lspci -vvvxxx
-------------------------
00:00.0 Host bridge: Intel Corporation 975X Express Memory Controller Hub
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information
00: 86 80 7c 27 06 00 90 20 00 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00
40: 01 90 d1 fe 01 40 d1 fe 03 00 00 f0 01 80 d1 fe
50: 00 00 02 00 03 00 00 00 00 00 00 00 00 00 00 00
60: 01 30 d1 fe 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 10 11 11 11 11 33 33 00 ff 03 00 00 20 1a 39 00
a0: 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 91 00 00 00
e0: 09 00 09 21 c9 40 0a 98 0c 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 00 00 00 00 00 00

00:01.0 PCI bridge: Intel Corporation 975X Express PCI Express Root Port (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 30300000-303fffff
	Prefetchable memory behind bridge: 0000000020000000-000000002ff00000
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [88] #0d [0000]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
		Address: fee00000  Data: 4049
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 2
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 0, PowerLimit 75.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
00: 86 80 7d 27 07 04 10 00 00 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 30 30 00 20
20: 30 30 30 30 01 20 f1 2f 00 00 00 00 00 00 00 00
30: 00 00 00 00 88 00 00 00 00 00 00 00 ff 01 18 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 02
80: 01 90 02 c8 00 00 00 00 0d 80 00 00 86 80 00 00
90: 05 a0 01 00 00 00 e0 fe 49 40 00 00 00 00 00 00
a0: 10 00 41 01 00 00 00 00 0f 00 01 00 01 25 01 02
b0: 40 00 01 11 80 25 00 00 c0 01 48 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 01 00 00 00 00 00 86 0f 00 00 00 00 00 00

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Unknown device 0419
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 30400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0
00: 86 80 d8 27 06 00 10 00 01 00 03 04 10 00 00 00
10: 04 00 40 30 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 19 04
30: 00 00 00 00 50 00 00 00 00 00 00 00 09 01 00 00
40: 01 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 60 42 c8 00 00 00 00 00 00 00 00 00 00 00 00
60: 05 70 80 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 10 00 91 00 00 00 00 00 00 08 10 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: 30500000-305fffff
	Prefetchable memory behind bridge: 00000000fff00000-0000000000000000
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x4, ASPM L0s L1, Port 1
		Link: Latency L0s <1us, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 1, PowerLimit 25.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
		Address: fee00000  Data: 4051
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: 86 80 d0 27 07 04 10 00 01 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 02 02 00 f0 00 00 20
20: 50 30 50 30 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 01 04 00
40: 10 80 41 01 c0 0f 00 00 0f 00 10 00 41 4c 11 01
50: 00 00 01 10 e0 0c 08 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 05 90 01 00 00 00 e0 fe 51 40 00 00 00 00 00 00
90: 0d a0 00 00 86 80 d0 27 00 00 00 00 00 00 00 00
a0: 01 00 02 c8 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00
e0: 00 00 c7 00 06 07 08 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 30200000-302fffff
	Prefetchable memory behind bridge: 0000000030600000-0000000030600000
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 5
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 5, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
		Address: fee00000  Data: 4059
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: 86 80 e0 27 07 04 10 00 01 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 03 03 00 20 20 00 00
20: 20 30 20 30 61 30 61 30 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 01 04 00
40: 10 80 41 01 c0 0f 00 00 0f 00 11 00 11 2c 11 05
50: 40 00 11 30 60 05 28 00 00 00 48 01 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 05 90 01 00 00 00 e0 fe 59 40 00 00 00 00 00 00
90: 0d a0 00 00 86 80 e0 27 00 00 00 00 00 00 00 00
a0: 01 00 02 c8 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00
e0: 00 00 c7 00 06 07 08 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 30100000-301fffff
	Prefetchable memory behind bridge: 00000000fff00000-0000000000000000
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 6
		Link: Latency L0s <256ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
		Slot: Number 6, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Unknown, PwrInd Unknown, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-
	Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
		Address: fee00000  Data: 4061
	Capabilities: [90] #0d [0000]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: 86 80 e2 27 07 04 10 00 01 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 04 00 10 10 00 00
20: 10 30 10 30 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 02 04 00
40: 10 80 41 01 c0 0f 00 00 0f 00 10 00 11 2c 11 06
50: 40 00 11 30 60 05 30 00 00 00 48 01 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 05 90 01 00 00 00 e0 fe 61 40 00 00 00 00 00 00
90: 0d a0 00 00 86 80 e2 27 00 00 00 00 00 00 00 00
a0: 01 00 02 c8 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 11 80 00 00 00 00
e0: 00 00 c7 00 06 07 08 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at 4080 [size=32]
00: 86 80 c8 27 05 00 80 02 01 00 03 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 81 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 2f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 4060 [size=32]
00: 86 80 c9 27 05 00 80 02 01 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 61 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 02 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 2f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 4040 [size=32]
00: 86 80 ca 27 05 00 80 02 01 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 41 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 03 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 2f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at 4020 [size=32]
00: 86 80 cb 27 05 00 80 02 01 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 21 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 04 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 2f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at 30404400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port
00: 86 80 cc 27 06 00 90 02 01 20 03 0c 00 00 00 00
10: 00 44 40 30 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 58 c2 c9 00 00 00 00 0a 00 a0 20 00 00 00 00
60: 20 20 ff 01 00 00 00 00 01 00 00 00 00 00 08 c0
70: 00 00 c7 3f 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 aa ff 00 ff 00 ff 00 20 00 00 88
e0: 00 00 00 00 db b6 6d 00 00 00 00 00 00 00 00 00
f0: 00 80 00 09 88 85 40 00 86 0f 01 00 06 17 02 20

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: 30000000-300fffff
	Prefetchable memory behind bridge: 00000000fff00000-0000000000000000
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [50] #0d [0000]
00: 86 80 4e 24 07 00 10 00 e1 01 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 05 05 20 f0 00 80 22
20: 00 30 00 30 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 04 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 12 00 00
50: 0d 00 00 00 86 80 42 58 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information
00: 86 80 b0 27 07 00 10 02 01 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00
40: 01 04 00 00 80 00 00 00 01 05 00 00 10 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 8b 8a 8b 8b d0 00 00 00 80 8a 89 8b 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 0f 14 81 06 7c 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 02 04 00 30 00 00 00 13 00 00 00 00 03 00 00
b0: 00 00 f0 00 00 00 00 00 00 00 00 08 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 33 22 11 00 67 45 00 00 c0 c0 00 00 02 00 00 00
e0: 09 00 0c 10 00 00 00 00 00 00 00 00 00 00 00 00
f0: 01 c0 d1 fe 00 00 00 00 86 0f 01 00 00 00 00 00

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 40b0 [size=16]
00: 86 80 df 27 05 00 80 02 01 8a 01 01 00 00 00 00
10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00
20: b1 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 01 00 00
40: 30 c0 00 00 0b 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 40c8 [size=8]
	Region 1: I/O ports at 40e4 [size=4]
	Region 2: I/O ports at 40c0 [size=8]
	Region 3: I/O ports at 40e0 [size=4]
	Region 4: I/O ports at 40a0 [size=16]
	Region 5: Memory at 30404000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
00: 86 80 c0 27 07 00 b0 02 01 8f 01 01 00 00 00 00
10: c9 40 00 00 e5 40 00 00 c1 40 00 00 e1 40 00 00
20: a1 40 00 00 00 40 40 30 00 00 00 00 86 80 42 58
30: 00 00 00 00 70 00 00 00 00 00 00 00 0b 02 00 00
40: 88 80 88 80 00 00 00 00 0f 00 11 11 00 00 00 00
50: 00 00 00 00 00 f0 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 01 00 02 40 00 00 00 00 00 00 00 00 00 00 00 00
80: 05 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 ff 02 80 01 00 40 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 0f 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 4000 [size=32]
00: 86 80 da 27 01 00 80 02 01 00 05 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 40 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 02 00 00
40: 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 86 0f 01 00 00 00 00 00

01:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] (prog-if 00 [VGA])
	Subsystem: ATI Technologies Inc Unknown device 2302
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at 20000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at 30300000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at 3000 [size=256]
	Expansion ROM at 30320000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <128ns, L1 <2us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <128ns, L1 <1us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
	Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
00: 02 10 4b 5e 07 00 10 00 00 00 00 03 10 00 80 00
10: 0c 00 00 20 00 00 00 00 04 00 30 30 00 00 00 00
20: 01 30 00 00 00 00 00 00 00 00 00 00 02 10 02 23
30: 00 00 fe ff 50 00 00 00 00 00 00 00 0b 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 02 10 02 23
50: 01 58 02 06 00 00 00 00 10 80 01 00 60 02 2c 01
60: 10 09 00 00 01 1d 00 00 40 00 01 11 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

01:00.1 Display controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)] Secondary
	Subsystem: ATI Technologies Inc Unknown device 2303
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Region 0: Memory at 30310000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <128ns, L1 <2us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <128ns, L1 <1us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
00: 02 10 6b 5e 07 00 10 00 00 00 80 03 10 00 00 00
10: 04 00 31 30 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 02 10 03 23
30: 00 00 00 00 50 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 58 02 06 00 00 00 00 10 00 01 00 40 02 00 00
60: 00 00 00 00 01 1d 00 00 00 00 01 11 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

03:00.0 SATA controller: Marvell Technology Group Ltd. Unknown device 6145 (rev a1) (prog-if 8f)
	Subsystem: Marvell Technology Group Ltd. Unknown device 6145
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (2000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 2018 [size=8]
	Region 1: I/O ports at 2024 [size=4]
	Region 2: I/O ports at 2010 [size=8]
	Region 3: I/O ports at 2020 [size=4]
	Region 4: I/O ports at 2000 [size=16]
	Region 5: Memory at 30200000 (32-bit, non-prefetchable) [size=1K]
	Expansion ROM at 30600000 [disabled] [size=256K]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s unlimited, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s <256ns, L1 unlimited
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
00: ab 11 45 61 07 00 10 00 a1 8f 06 01 10 00 00 00
10: 19 20 00 00 25 20 00 00 11 20 00 00 21 20 00 00
20: 01 20 00 00 00 00 20 30 00 00 00 00 ab 11 45 61
30: 00 00 fc ff 48 00 00 00 00 00 00 00 0b 01 08 00
40: 24 f9 f0 00 1f 80 00 00 01 50 02 5a 00 20 00 13
50: 05 e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 50 c4 21 40 b0 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 10 00 11 00 c0 0f 0c 00 00 24 01 00 11 a4 03 00
f0: 40 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00

04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Intel Corporation Unknown device 30a5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 507
	Region 0: Memory at 30100000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at 1000 [size=32]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable+
		Address: 00000000fee00000  Data: 4089
	Capabilities: [e0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM unknown, Port 0
		Link: Latency L0s <128ns, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
00: 86 80 9a 10 07 04 10 00 00 00 00 02 10 00 00 00
10: 00 00 10 30 00 00 00 00 01 10 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 a5 30
30: 00 00 00 00 c8 00 00 00 00 00 00 00 0a 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 01 d0 22 c8 00 20 00 0f
d0: 05 e0 81 00 00 00 e0 fe 00 00 00 00 89 40 00 00
e0: 10 00 01 00 c1 0c 00 00 10 28 10 00 11 10 07 00
f0: 40 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00

05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Intel Corporation Unknown device 5842
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at 30004000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+
00: 4c 10 24 80 16 00 10 02 00 10 00 0c 10 20 00 00
10: 00 40 00 30 00 00 00 30 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 42 58
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 02 04
40: 00 00 00 00 01 00 02 7e 00 80 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 08 00 00 00
f0: 10 00 00 00 86 10 00 00 86 80 42 58 00 00 00 00

---

### Post by Ebbex on 2007-02-26
That SATA controller is not yet supported under linux. However, there is a patch out there. You might want to check out this link.

[http://www.mail-archive.com/linux-ide@vger.kernel.org/msg03129.html](http://www.mail-archive.com/linux-ide@vger.kernel.org/msg03129.html)
Remember to disable CONFIG_PCI_MSI and CONFIG_PCI_MMCONFIG.

I have had success with this patch.

Now if I could only get dmraid to work on newer kernels... (dmraid looks for the raid45 module, which was recently renamed raid456) Seems there's more to it than just a simple string replace.

---


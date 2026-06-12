---
title: "No Sound Toshiba P105-6114"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by eric_c351 on 2007-05-02
:confused: I can't get any sound to work using Feisty Fawn on my Toshiba P105-S6114.  I tried a few of the dsdt's from [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) and followed the instructions on [http://ubuntuforums.org/showthread.php?p=2555605](http://ubuntuforums.org/showthread.php?p=2555605).  I still have no sound at all.  I did get sound to work with ACPI off in Edgy.  

dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000008000 end: 00000000000e4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000018000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007f590000 end: 000000007f690000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007f690000 size: 000000000000c000 end: 000000007f69c000 type: 3
[    0.000000] copy_e820_map() start: 000000007f69c000 size: 0000000000064000 end: 000000007f700000 type: 4
[    0.000000] copy_e820_map() start: 000000007f700000 size: 0000000000900000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f69c000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7690
[    0.000000] Entering add_active_range(0, 0, 521872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521872
[    0.000000] On node 0 totalpages: 521872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290211 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 TOSQCI                                ) @ 0x000f75d0
[    0.000000] ACPI: XSDT (v001 TOSQCI TOSQCI00 0x06040000  LTP 0x00000000) @ 0x7f6920b4
[    0.000000] ACPI: FADT (v003 TOSQCI TOSQCI00 0x06040000 ALAN 0x00000001) @ 0x7f69bc2a
[    0.000000] ACPI: MADT (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7f69bd1e
[    0.000000] ACPI: HPET (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7f69bd86
[    0.000000] ACPI: MCFG (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x7f69bdbe
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x7f69bdfa
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7f69be62
[    0.000000] ACPI: SLIC (v001 TOSQCI TOSQCI00 0x06040000  LTP 0x00000000) @ 0x7f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Tst 0x00003000 INTL 0x20060912) @ 0x7f6926b4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu1Tst 0x00003000 INTL 0x20060912) @ 0x7f69260e
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060912) @ 0x7f692128
[    0.000000] ACPI: DSDT (v001 TOSQCI   Denver 0x06040000 MSFT 0x03000001) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Detected 1672.367 MHz processor.
[   18.617018] Built 1 zonelists.  Total pages: 517795
[   18.617022] Kernel command line: root=UUID=cabe099a-7017-41c2-829f-47b57a9b119e ro quiet splash
[   18.617167] mapped APIC to ffffd000 (fee00000)
[   18.617169] mapped IOAPIC to ffffc000 (fec00000)
[   18.617172] Enabling fast FPU save and restore... done.
[   18.617174] Enabling unmasked SIMD FPU exception support... done.
[   18.617182] Initializing CPU#0
[   18.617254] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.618888] Console: colour VGA+ 80x25
[   18.619166] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.619461] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.696322] Memory: 2058600k/2087488k available (1992k kernel code, 27648k reserved, 893k data, 328k init, 1169984k highmem)
[   18.696331] virtual kernel memory layout:
[   18.696332]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.696334]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.696335]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.696336]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.696337]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   18.696338]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   18.696339]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   18.696342] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.696519] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.696525] hpet0: 3 64-bit timers, 14318180 Hz
[   18.697530] Using HPET for base-timer
[   18.776473] Calibrating delay using timer specific routine.. 3348.13 BogoMIPS (lpj=6696266)
[   18.776515] Security Framework v1.0.0 initialized
[   18.776521] SELinux:  Disabled at boot.
[   18.776538] Mount-cache hash table entries: 512
[   18.776682] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   18.776689] monitor/mwait feature present.
[   18.776691] using mwait in idle threads.
[   18.776696] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.776698] CPU: L2 cache: 2048K
[   18.776701] CPU: Physical Processor ID: 0
[   18.776703] CPU: Processor Core ID: 0
[   18.776704] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   18.776714] Compat vDSO mapped to ffffe000.
[   18.776719] Remapping vsyscall page to ffffe000
[   18.776731] Checking 'hlt' instruction... OK.
[   18.792571] SMP alternatives: switching to UP code
[   18.792937] Early unpacking initramfs... done
[   19.111154] ACPI: Core revision 20060707
[   19.136551] ACPI: Looking for DSDT in initramfs... successfully read 32131 bytes from /DSDT.aml.
[   19.136609] ACPI (tbget-0297): Table [DSDT] replaced by host OS [20060707]
[   19.153867] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   19.153886] SMP alternatives: switching to SMP code
[   19.153969] Booting processor 1/1 eip 3000
[   19.164394] Initializing CPU#1
[   19.244181] Calibrating delay using timer specific routine.. 3344.46 BogoMIPS (lpj=6688936)
[   19.244188] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   19.244193] monitor/mwait feature present.
[   19.244196] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.244198] CPU: L2 cache: 2048K
[   19.244200] CPU: Physical Processor ID: 0
[   19.244201] CPU: Processor Core ID: 1
[   19.244203] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   19.244658] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   19.244680] Total of 2 processors activated (6692.60 BogoMIPS).
[   19.244872] ENABLING IO-APIC IRQs
[   19.245074] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.392088] checking TSC synchronization across 2 CPUs: passed.
[    0.004001] Brought up 2 CPUs
[    0.068792] migration_cost=26
[    0.069058] Booting paravirtualized kernel on bare hardware
[    0.069157] Time:  4:58:29  Date: 04/02/107
[    0.069185] NET: Registered protocol family 16
[    0.069268] EISA bus registered
[    0.069272] ACPI: bus type pci registered
[    0.094370] PCI: PCI BIOS revision 2.10 entry at 0xfd704, last bus=11
[    0.094372] PCI: Using configuration type 1
[    0.094374] Setting up standard PCI resources
[    0.099841] ACPI: Interpreter enabled
[    0.099843] ACPI: Using IOAPIC for interrupt routing
[    0.100247] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.100252] PCI: Probing PCI hardware (bus 00)
[    0.101013] Boot video device is 0000:00:02.0
[    0.101680] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.101685] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.102709] PCI: Firmware left 0000:0a:08.0 e100 interrupts enabled, disabling
[    0.102804] PCI: Transparent bridge - 0000:00:1e.0
[    0.102879] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[    0.102881] Please report the result to linux-kernel to fix this permanently
[    0.102949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.113112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.113373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.113631] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.114992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.115553] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.115812] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.116077] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.116330] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.116581] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.116832] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.117087] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.117338] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.191110] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.191119] pnp: PnP ACPI init
[    0.193420] pnp: PnP ACPI: found 10 devices
[    0.193423] PnPBIOS: Disabled by ACPI PNP
[    0.193467] PCI: Using ACPI for IRQ routing
[    0.193470] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.193473] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    0.193475] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    0.193477] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[    0.193480] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    0.193482] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    0.193484] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    0.193486] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    0.193488] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    0.193490] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[    0.226175] NET: Registered protocol family 8
[    0.226177] NET: Registered protocol family 20
[    0.226712] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.226717] PCI: Bridge: 0000:00:1c.0
[    0.226718]   IO window: disabled.
[    0.226724]   MEM window: disabled.
[    0.226729]   PREFETCH window: disabled.
[    0.226746] PCI: Bridge: 0000:00:1c.1
[    0.226747]   IO window: disabled.
[    0.226753]   MEM window: 8c000000-8c0fffff
[    0.226758]   PREFETCH window: disabled.
[    0.226763] PCI: Bridge: 0000:00:1c.2
[    0.226765]   IO window: disabled.
[    0.226770]   MEM window: disabled.
[    0.226774]   PREFETCH window: disabled.
[    0.226783] PCI: Bus 11, cardbus bridge: 0000:0a:04.0
[    0.226785]   IO window: 00002400-000024ff
[    0.226790]   IO window: 00002800-000028ff
[    0.226796]   PREFETCH window: 88000000-8bffffff
[    0.226801]   MEM window: 90000000-93ffffff
[    0.226806] PCI: Bridge: 0000:00:1e.0
[    0.226809]   IO window: 2000-2fff
[    0.226815]   MEM window: d0000000-d00fffff
[    0.226820]   PREFETCH window: 88000000-8bffffff
[    0.226849] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.226858] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.226881] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[    0.226886] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.226893] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.226917] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.226925] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.226936] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[    0.226942] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.226959] PCI: Enabling device 0000:0a:04.0 (0000 -> 0003)
[    0.226963] ACPI: PCI Interrupt 0000:0a:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.226971] PCI: Setting latency timer of device 0000:0a:04.0 to 64
[    0.227000] NET: Registered protocol family 2
[    0.279870] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.279968] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.280433] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.280687] TCP: Hash tables configured (established 131072 bind 65536)
[    0.280690] TCP reno registered
[    0.295938] checking if image is initramfs... it is
[    0.922344] Freeing initrd memory: 6782k freed
[    0.922530] Simple Boot Flag at 0x36 set to 0x1
[    0.923007] audit: initializing netlink socket (disabled)
[    0.923023] audit(1178081909.684:1): initialized
[    0.923126] highmem bounce pool size: 64 pages
[    0.923214] VFS: Disk quotas dquot_6.5.1
[    0.923235] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.923285] io scheduler noop registered
[    0.923287] io scheduler anticipatory registered
[    0.923289] io scheduler deadline registered
[    0.923301] io scheduler cfq registered (default)
[    8.918434] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[    8.918704] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.918764] assign_interrupt_mode Found MSI capability
[    8.918767] Allocate Port Service[0000:00:1c.0:pcie00]
[    8.918799] Allocate Port Service[0000:00:1c.0:pcie02]
[    8.918920] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    8.918979] assign_interrupt_mode Found MSI capability
[    8.918981] Allocate Port Service[0000:00:1c.1:pcie00]
[    8.919011] Allocate Port Service[0000:00:1c.1:pcie02]
[    8.919133] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    8.919191] assign_interrupt_mode Found MSI capability
[    8.919193] Allocate Port Service[0000:00:1c.2:pcie00]
[    8.919223] Allocate Port Service[0000:00:1c.2:pcie02]
[    8.919399] isapnp: Scanning for PnP cards...
[    9.273139] isapnp: No Plug & Play device found
[    9.293779] Real Time Clock Driver v1.12ac
[    9.293842] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.294484] mice: PS/2 mouse device common for all mice
[    9.295008] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.295233] input: Macintosh mouse button emulation as /class/input/input0
[    9.295266] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.295270] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.295559] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.297651] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.297655] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.297766] EISA: Probing bus 0 at eisa.0
[    9.297772] Cannot allocate resource for EISA slot 1
[    9.297776] Cannot allocate resource for EISA slot 2
[    9.297803] EISA: Detected 0 cards.
[    9.327968] TCP cubic registered
[    9.327976] NET: Registered protocol family 1
[    9.327998] Starting balanced_irq
[    9.328006] Using IPI No-Shortcut mode
[    9.328116] ACPI: (supports S0 S3 S4 S5)
[    9.328162]   Magic number: 7:7:969
[    9.328425] Freeing unused kernel memory: 328k freed
[    9.330125] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.330257] Time: tsc clocksource has been installed.
[   10.535737] Capability LSM initialized
[   10.571669] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[   10.571920] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[   10.572504] Monitor-Mwait will be used to enter C-1 state
[   10.572506] Monitor-Mwait will be used to enter C-2 state
[   10.572509] Monitor-Mwait will be used to enter C-3 state
[   10.572515] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.573007] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   10.573218] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[   10.573893] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   11.168000] Time: hpet clocksource has been installed.
[   11.172000] ACPI: Thermal Zone [THRM] (60 C)
[   11.516000] usbcore: registered new interface driver usbfs
[   11.516000] usbcore: registered new interface driver hub
[   11.520000] usbcore: registered new device driver usb
[   11.520000] USB Universal Host Controller Interface driver v3.0
[   11.520000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   11.520000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.520000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.520000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.520000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   11.520000] usb usb1: configuration #1 chosen from 1 choice
[   11.520000] hub 1-0:1.0: USB hub found
[   11.520000] hub 1-0:1.0: 2 ports detected
[   11.584000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   11.584000] e100: Copyright(c) 1999-2006 Intel Corporation
[   11.608000] SCSI subsystem initialized
[   11.624000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   11.624000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.624000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.624000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.624000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   11.624000] usb usb2: configuration #1 chosen from 1 choice
[   11.624000] hub 2-0:1.0: USB hub found
[   11.624000] hub 2-0:1.0: 2 ports detected
[   11.632000] libata version 2.20 loaded.
[   11.636000] ieee1394: Initialized config rom entry `ip1394'
[   11.728000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.728000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.728000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.728000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.728000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   11.728000] usb usb3: configuration #1 chosen from 1 choice
[   11.728000] hub 3-0:1.0: USB hub found
[   11.728000] hub 3-0:1.0: 2 ports detected
[   11.832000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   11.832000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.832000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.832000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.832000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   11.832000] usb usb4: configuration #1 chosen from 1 choice
[   11.832000] hub 4-0:1.0: USB hub found
[   11.832000] hub 4-0:1.0: 2 ports detected
[   11.936000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   11.936000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.936000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.936000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   11.936000] ehci_hcd 0000:00:1d.7: debug port 1
[   11.936000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.936000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0544000
[   11.940000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.940000] usb usb5: configuration #1 chosen from 1 choice
[   11.940000] hub 5-0:1.0: USB hub found
[   11.940000] hub 5-0:1.0: 8 ports detected
[   12.044000] ACPI: PCI Interrupt 0000:0a:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   12.044000] PCI: Setting latency timer of device 0000:0a:08.0 to 64
[   12.068000] e100: eth0: e100_probe: addr 0xd0006000, irq 21, MAC addr 00:16:36:AA:58:32
[   12.072000] PCI: Enabling device 0000:0a:04.1 (0000 -> 0002)
[   12.072000] ACPI: PCI Interrupt 0000:0a:04.1[A] -> GSI 17 (level, low) -> IRQ 16
[   12.072000] PCI: Setting latency timer of device 0000:0a:04.1 to 64
[   12.120000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0007000-d00077ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.120000] ata_piix 0000:00:1f.2: version 2.10ac1
[   12.120000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   12.276000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   12.276000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.276000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[   12.276000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[   12.276000] scsi0 : ata_piix
[   12.440000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   12.440000] ata1.00: ATA-7: FUJITSU MHV2160BT PL, 00000050, max UDMA/100
[   12.440000] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   12.448000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   12.448000] ata1.00: configured for UDMA/100
[   12.448000] scsi1 : ata_piix
[   12.576000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   12.752000] usb 3-1: configuration #1 chosen from 1 choice
[   12.768000] ata2.00: ATAPI, max UDMA/33
[   12.932000] ata2.00: configured for UDMA/33
[   12.932000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2160B 0000 PQ: 0 ANSI: 5
[   12.932000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.60 PQ: 0 ANSI: 5
[   12.944000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   12.944000] sda: Write Protect is off
[   12.944000] sda: Mode Sense: 00 3a 00 00
[   12.944000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.944000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   12.944000] sda: Write Protect is off
[   12.944000] sda: Mode Sense: 00 3a 00 00
[   12.944000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.944000]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.952000] Uniform CD-ROM driver Revision: 3.20
[   12.952000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.952000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.952000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.004000]  sda5 >
[   13.004000] sd 0:0:0:0: Attached scsi disk sda
[   13.228000] Attempting manual resume
[   13.228000] swsusp: Resume From Partition 8:5
[   13.228000] PM: Checking swsusp image.
[   13.228000] PM: Resume from disk failed.
[   13.276000] kjournald starting.  Commit interval 5 seconds
[   13.276000] EXT3-fs: mounted filesystem with ordered data mode.
[   24.680000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   25.024000] NET: Registered protocol family 10
[   25.024000] lo: Disabled Privacy Extensions
[   25.540000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.544000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.608000] intel_rng: FWH not detected
[   25.628000] Yenta: CardBus bridge found at 0000:0a:04.0 [1179:ff31]
[   25.628000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   25.628000] Yenta: Routing CardBus interrupts to PCI
[   25.628000] Yenta TI: socket 0000:0a:04.0, mfunc 0x01a21b22, devctl 0x66
[   25.672000] Linux agpgart interface v0.102 (c) Dave Jones
[   25.688000] iTCO_vendor_support: vendor-support=0
[   25.700000] agpgart: Detected an Intel 945GM Chipset.
[   25.700000] agpgart: Detected 7932K stolen memory.
[   25.716000] agpgart: AGP aperture is 256M @ 0xc0000000
[   25.720000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   25.720000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.720000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.860000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   25.860000] Socket status: 30000006
[   25.860000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   25.860000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   25.860000] cs: IO port probe 0x2000-0x2fff: clean.
[   25.860000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   25.860000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   25.860000] PCI: Enabling device 0000:0a:04.2 (0000 -> 0002)
[   25.860000] ACPI: PCI Interrupt 0000:0a:04.2[A] -> GSI 17 (level, low) -> IRQ 16
[   25.860000] PCI: Setting latency timer of device 0000:0a:04.2 to 64
[   25.892000] ieee80211_crypt: registered algorithm 'NULL'
[   25.892000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   25.892000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.004000] sdhci: Secure Digital Host Controller Interface driver
[   26.004000] sdhci: Copyright(c) Pierre Ossman
[   26.004000] sdhci: SDHCI controller found at 0000:0a:04.3 [104c:803c] (rev 0)
[   26.004000] PCI: Enabling device 0000:0a:04.3 (0000 -> 0002)
[   26.004000] ACPI: PCI Interrupt 0000:0a:04.3[A] -> GSI 17 (level, low) -> IRQ 16
[   26.004000] PCI: Setting latency timer of device 0000:0a:04.3 to 64
[   26.004000] mmc0: SDHCI at 0xd0007800 irq 16 DMA
[   26.044000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   26.044000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   26.044000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   26.044000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   26.044000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   26.044000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   26.292000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   26.292000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   26.412000] cs: IO port probe 0x100-0x3af: clean.
[   26.416000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.416000] cs: IO port probe 0x820-0x8ff: clean.
[   26.416000] cs: IO port probe 0xc00-0xcf7: clean.
[   26.416000] cs: IO port probe 0xa00-0xaff: clean.
[   26.544000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   26.544000] synaptics: Toshiba Satellite P105 detected, limiting rate to 40pps.
[   26.580000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   26.856000] lp: driver loaded but no devices found
[   26.904000] Adding 6048432k swap on /dev/disk/by-uuid/6325f98e-5f11-432c-a63b-90e0fe1721eb.  Priority:-1 extents:1 across:6048432k
[   27.072000] EXT3 FS on sda1, internal journal
[   27.964000] ipw3945: Radio Frequency Kill Switch is On:
[   27.964000] Kill switch must be turned off for wireless networking to work.
[   28.052000] No dock devices found.
[   28.088000] ibm_acpi: ec object not found
[   28.136000] ACPI: AC Adapter [ACAD] (on-line)
[   28.252000] Using specific hotkey driver
[   28.284000] input: Power Button (FF) as /class/input/input3
[   28.284000] ACPI: Power Button (FF) [PWRF]
[   28.284000] input: Lid Switch as /class/input/input4
[   28.284000] ACPI: Lid Switch [LID]
[   28.284000] input: Power Button (CM) as /class/input/input5
[   28.284000] ACPI: Power Button (CM) [PWRB]
[   28.316000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   28.428000] ACPI: Battery Slot [BAT1] (battery present)
[   28.456000] wmi_add device=c2190400
[   28.456000] calling WQBA
[   28.468000] pcc_acpi: loading...
[   35.232000] eth0: no IPv6 routers present
[   35.336000] [drm] Initialized drm 1.1.0 20060810
[   35.460000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   35.460000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.676000] ppdev: user-space parallel port driver
[   38.640000] apm: BIOS not found.
[   39.164000] Bluetooth: Core ver 2.11
[   39.164000] NET: Registered protocol family 31
[   39.164000] Bluetooth: HCI device and connection manager initialized
[   39.164000] Bluetooth: HCI socket layer initialized
[   39.240000] Bluetooth: L2CAP ver 2.8
[   39.240000] Bluetooth: L2CAP socket layer initialized
[   39.356000] Bluetooth: RFCOMM socket layer initialized
[   39.356000] Bluetooth: RFCOMM TTY layer initialized
[   39.356000] Bluetooth: RFCOMM ver 1.8

lspci
00:00.0 0600: 8086:27a0 (rev 03)
	Subsystem: 1179:ff31
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
	Subsystem: 1179:ff31
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 0380: 8086:27a6 (rev 03)
	Subsystem: 1179:ff31
	Flags: bus master, fast devsel, latency 0
	Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 1179:ff31
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 0604: 8086:27d0 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:1c.1 0604: 8086:27d2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 8c000000-8c0fffff
	Capabilities: <access denied>

00:1c.2 0604: 8086:27d4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1d.0 0c03: 8086:27c8 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]

00:1d.1 0c03: 8086:27c9 (rev 02) (prog-if 00 [UHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1840 [size=32]

00:1d.2 0c03: 8086:27ca (rev 02) (prog-if 00 [UHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]

00:1d.3 0c03: 8086:27cb (rev 02) (prog-if 00 [UHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20 [EHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d00fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: <access denied>

00:1f.0 0601: 8086:27b9 (rev 02)
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 80 [Master])
	Subsystem: 1179:ff31
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18b0 [size=16]
	Capabilities: <access denied>

00:1f.3 0c05: 8086:27da (rev 02)
	Subsystem: 1179:ff31
	Flags: medium devsel, IRQ 11
	I/O ports at 18c0 [size=32]

03:00.0 0280: 8086:4222 (rev 02)
	Subsystem: 8086:1040
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 8c000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

0a:04.0 0607: 104c:8039
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00002400-000024ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

0a:04.1 0c00: 104c:803a (prog-if 10 [OHCI])
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d0007000 (32-bit, non-prefetchable) [size=2K]
	Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

0a:04.2 0180: 104c:803b
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

0a:04.3 0805: 104c:803c (prog-if 01)
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at d0007800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0a:08.0 0200: 8086:1092 (rev 02)
	Subsystem: 1179:ff31
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at d0006000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>

interrupts
           CPU0       CPU1       
  0:       3730     197558   IO-APIC-edge      timer
  1:        586          0   IO-APIC-edge      i8042
  8:         58          0   IO-APIC-edge      rtc
  9:      50778      33549   IO-APIC-fasteoi   acpi
 12:      71278          0   IO-APIC-edge      i8042
 14:       9762          0   IO-APIC-edge      libata
 15:       8627          0   IO-APIC-edge      libata
 16:          9          0   IO-APIC-fasteoi   ohci1394, yenta, tifm_7xx1, sdhci:slot0, ipw3945
 17:      56419          0   IO-APIC-fasteoi   uhci_hcd:usb4, i915@pci:0000:00:02.0
 18:         34          0   IO-APIC-fasteoi   uhci_hcd:usb3
 19:          2          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:       1718          0   IO-APIC-fasteoi   eth0
 22:       2821          0   IO-APIC-fasteoi   HDA Intel
NMI:          0          0 
LOC:     201143     201143 
ERR:          0
MIS:          0

sndstat
Mixers:
0: Conexant CX20551 (Waikiki)

asound
Names of available sound cards:
Intel

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 30 [100%] [on]
  Front Right: Playback 30 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Line-In',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic Bypass',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 30
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'ExtMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]

---


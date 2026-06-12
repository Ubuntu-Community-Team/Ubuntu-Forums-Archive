---
title: "Error Message At Bootup"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by Opeth115 on 2007-07-15
When i boot up i get this error message complaining that it is unable to allocate mem resources.  I would really like to know what this means because im wondering if it is hindering anything form performing at its full capacity...

here is my dmesg output i highlight the actual error message

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000008f000 end: 000000000008f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000008f000 size: 0000000000011000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007ddc8000 end: 000000007dec8000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007dec8000 size: 0000000000057000 end: 000000007df1f000 type: 4
[    0.000000] copy_e820_map() start: 000000007df1f000 size: 0000000000edb000 end: 000000007edfa000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007edfa000 size: 000000000000d000 end: 000000007ee07000 type: 2
[    0.000000] copy_e820_map() start: 000000007ee07000 size: 00000000000a2000 end: 000000007eea9000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007eea9000 size: 0000000000005000 end: 000000007eeae000 type: 3
[    0.000000] copy_e820_map() start: 000000007eeae000 size: 0000000000044000 end: 000000007eef2000 type: 4
[    0.000000] copy_e820_map() start: 000000007eef2000 size: 0000000000001000 end: 000000007eef3000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007eef3000 size: 000000000000c000 end: 000000007eeff000 type: 3
[    0.000000] copy_e820_map() start: 000000007eeff000 size: 0000000000001000 end: 000000007ef00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ef00000 size: 0000000000100000 end: 000000007f000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dec8000 (usable)
[    0.000000]  BIOS-e820: 000000007dec8000 - 000000007df1f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007df1f000 - 000000007edfa000 (usable)
[    0.000000]  BIOS-e820: 000000007edfa000 - 000000007ee07000 (reserved)
[    0.000000]  BIOS-e820: 000000007ee07000 - 000000007eea9000 (usable)
[    0.000000]  BIOS-e820: 000000007eea9000 - 000000007eeae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeae000 - 000000007eef2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007eef2000 - 000000007eef3000 (usable)
[    0.000000]  BIOS-e820: 000000007eef3000 - 000000007eeff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
[    0.000000]  BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1135MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe200
[    0.000000] Entering add_active_range(0, 0, 519936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   519936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   519936
[    0.000000] On node 0 totalpages: 519936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2270 pages used for memmap
[    0.000000]   HighMem zone: 288290 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 INTEL                                 ) @ 0x000fe020
[    0.000000] ACPI: RSDT (v001 INTEL  DP965LT  0x00000671      0x01000013) @ 0x7eefd038
[    0.000000] ACPI: FADT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eefc000
[    0.000000] ACPI: MADT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef6000
[    0.000000] ACPI: WDDT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef5000
[    0.000000] ACPI: MCFG (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef4000
[    0.000000] ACPI: ASF! (v032 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef3000
[    0.000000] ACPI: SSDT (v001 INTEL     CpuPm 0x00000671 MSFT 0x01000013) @ 0x7eead000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu0Ist 0x00000671 MSFT 0x01000013) @ 0x7eeac000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu1Ist 0x00000671 MSFT 0x01000013) @ 0x7eeab000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu2Ist 0x00000671 MSFT 0x01000013) @ 0x7eeaa000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu3Ist 0x00000671 MSFT 0x01000013) @ 0x7eea9000
[    0.000000] ACPI: DSDT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f000000:80f00000)
[    0.000000] Detected 1864.886 MHz processor.
[   18.216011] Built 1 zonelists.  Total pages: 515874
[   18.216014] Kernel command line: root=UUID=f732cb1b-5374-41c7-b92e-fc902f4a5b46 ro quiet splash rootflags=data=writeback profile
[   18.216150] mapped APIC to ffffd000 (fee00000)
[   18.216152] mapped IOAPIC to ffffc000 (fec00000)
[   18.216154] Enabling fast FPU save and restore... done.
[   18.216156] Enabling unmasked SIMD FPU exception support... done.
[   18.216162] Initializing CPU#0
[   18.216204] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.217411] Console: colour VGA+ 80x25
[   18.217590] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.217819] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.284057] Memory: 2049972k/2079744k available (1992k kernel code, 27588k reserved, 900k data, 328k init, 1161500k highmem)
[   18.284065] virtual kernel memory layout:
[   18.284066]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.284067]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.284068]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.284069]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.284070]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.284071]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.284072]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.284075] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.360187] Calibrating delay using timer specific routine.. 3732.58 BogoMIPS (lpj=7465164)
[   18.360220] Security Framework v1.0.0 initialized
[   18.360225] SELinux:  Disabled at boot.
[   18.360239] Mount-cache hash table entries: 512
[   18.360349] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.360356] monitor/mwait feature present.
[   18.360358] using mwait in idle threads.
[   18.360361] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.360363] CPU: L2 cache: 2048K
[   18.360366] CPU: Physical Processor ID: 0
[   18.360367] CPU: Processor Core ID: 0
[   18.360369] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.360377] Compat vDSO mapped to ffffe000.
[   18.360380] Remapping vsyscall page to ffffe000
[   18.360390] Checking 'hlt' instruction... OK.
[   18.376273] SMP alternatives: switching to UP code
[   18.376580] Early unpacking initramfs... done
[   18.661868] ACPI: Core revision 20060707
[   18.662627] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.665449] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   18.665464] SMP alternatives: switching to SMP code
[   18.665518] Booting processor 1/1 eip 3000
[   18.675883] Initializing CPU#1
[   18.756122] Calibrating delay using timer specific routine.. 3729.88 BogoMIPS (lpj=7459775)
[   18.756127] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.756132] monitor/mwait feature present.
[   18.756134] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.756136] CPU: L2 cache: 2048K
[   18.756138] CPU: Physical Processor ID: 0
[   18.756139] CPU: Processor Core ID: 1
[   18.756140] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.756521] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   18.756538] Total of 2 processors activated (7462.46 BogoMIPS).
[   18.756677] ENABLING IO-APIC IRQs
[   18.756841] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.904105] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.068939] migration_cost=21
[    0.069163] Booting paravirtualized kernel on bare hardware
[    0.069224] Time:  1:35:34  Date: 06/14/107
[    0.069246] NET: Registered protocol family 16
[    0.069313] EISA bus registered
[    0.069319] ACPI: bus type pci registered
[    0.070688] PCI: Using configuration type 1
[    0.070690] Setting up standard PCI resources
[    0.078734] ACPI: Interpreter enabled
[    0.078736] ACPI: Using IOAPIC for interrupt routing
[    0.079115] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.079123] PCI: Probing PCI hardware (bus 00)
[    0.079137] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.080681] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.080685] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[    0.080867] Boot video device is 0000:01:00.0
[    0.081402] PCI: Transparent bridge - 0000:00:1e.0
[    0.081475] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.085997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.086576] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.086780] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.086976] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.087173] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.087375] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.087572] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.087769] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.087966] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.089368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.089572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.089772] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.089973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.090178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.091426] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.091434] pnp: PnP ACPI init
[    0.093941] pnp: PnP ACPI: found 12 devices
[    0.093945] PnPBIOS: Disabled by ACPI PNP
[    0.093983] PCI: Using ACPI for IRQ routing
[    0.093985] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.094064] NET: Registered protocol family 8
[    0.094065] NET: Registered protocol family 20
[    0.094137] pnp: 00:06: ioport range 0x500-0x53f has been reserved
[    0.094140] pnp: 00:06: ioport range 0x400-0x47f could not be reserved
[    0.094142] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
**[SIZE="4"][    0.094410] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0[/SIZE]**
[    0.094445] PCI: Bridge: 0000:00:01.0
[    0.094447]   IO window: 2000-2fff
[    0.094450]   MEM window: 90000000-91ffffff
[    0.094453]   PREFETCH window: 80000000-8fffffff
[    0.094456] PCI: Bridge: 0000:00:1c.0
[    0.094458]   IO window: disabled.
[    0.094462]   MEM window: 92300000-923fffff
[    0.094465]   PREFETCH window: disabled.
[    0.094469] PCI: Bridge: 0000:00:1c.1
[    0.094471]   IO window: 1000-1fff
[    0.094475]   MEM window: 92100000-921fffff
[    0.094478]   PREFETCH window: disabled.
[    0.094482] PCI: Bridge: 0000:00:1c.2
[    0.094483]   IO window: disabled.
[    0.094487]   MEM window: 92400000-924fffff
[    0.094490]   PREFETCH window: disabled.
[    0.094494] PCI: Bridge: 0000:00:1c.3
[    0.094495]   IO window: disabled.
[    0.094499]   MEM window: 92500000-925fffff
[    0.094502]   PREFETCH window: disabled.
[    0.094506] PCI: Bridge: 0000:00:1c.4
[    0.094507]   IO window: disabled.
[    0.094511]   MEM window: 92600000-926fffff
[    0.094514]   PREFETCH window: disabled.
[    0.094518] PCI: Bridge: 0000:00:1e.0
[    0.094519]   IO window: disabled.
[    0.094523]   MEM window: 92000000-920fffff
[    0.094526]   PREFETCH window: disabled.
[    0.094538] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.094543] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.094558] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.094562] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.094577] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.094581] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.094596] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.094601] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.094616] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    0.094620] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.094634] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[    0.094639] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.094648] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.094669] NET: Registered protocol family 2
[    0.140258] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.140336] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.140712] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.140899] TCP: Hash tables configured (established 131072 bind 65536)
[    0.140901] TCP reno registered
[    0.156423] checking if image is initramfs... it is
[    0.717540] Freeing initrd memory: 6777k freed
[    0.718044] audit: initializing netlink socket (disabled)
[    0.718057] audit(1184376934.488:1): initialized
[    0.718137] highmem bounce pool size: 64 pages
[    0.718204] VFS: Disk quotas dquot_6.5.1
[    0.718219] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.718259] io scheduler noop registered
[    0.718262] io scheduler anticipatory registered
[    0.718263] io scheduler deadline registered
[    0.718272] io scheduler cfq registered (default)
[    0.718698] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.718728] assign_interrupt_mode Found MSI capability
[    0.718730] Allocate Port Service[0000:00:01.0:pcie00]
[    0.718804] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.718839] assign_interrupt_mode Found MSI capability
[    0.718842] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.718873] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.718955] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.718990] assign_interrupt_mode Found MSI capability
[    0.718992] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.719020] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.719101] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.719137] assign_interrupt_mode Found MSI capability
[    0.719139] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.719165] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.719249] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.719284] assign_interrupt_mode Found MSI capability
[    0.719286] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.719315] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.719399] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.719435] assign_interrupt_mode Found MSI capability
[    0.719436] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.719463] Allocate Port Service[0000:00:1c.4:pcie02]
[    0.719597] isapnp: Scanning for PnP cards...
[    1.072440] isapnp: No Plug & Play device found
[    1.090408] Real Time Clock Driver v1.12ac
[    1.090452] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.090562] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.091107] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.091256] mice: PS/2 mouse device common for all mice
[    1.091730] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.091854] input: Macintosh mouse button emulation as /class/input/input0
[    1.091887] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.091890] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.092057] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.094943] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.094947] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.095051] EISA: Probing bus 0 at eisa.0
[    1.095057] Cannot allocate resource for EISA slot 1
[    1.095059] Cannot allocate resource for EISA slot 2
[    1.095060] Cannot allocate resource for EISA slot 3
[    1.095077] EISA: Detected 0 cards.
[    1.124246] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.125145] TCP cubic registered
[    1.125151] NET: Registered protocol family 1
[    1.125168] Starting balanced_irq
[    1.125174] Using IPI No-Shortcut mode
[    1.125250] ACPI: (supports S0 S3 S4 S5)
[    1.125285]   Magic number: 15:189:559
[    1.125316]   hash matches device ptya5
[    1.125453] Freeing unused kernel memory: 328k freed
[    1.127810] Time: tsc clocksource has been installed.
[    2.307893] Capability LSM initialized
[    2.342305] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.342388] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.342394] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.342401] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.686415] usbcore: registered new interface driver usbfs
[    2.686434] usbcore: registered new interface driver hub
[    2.706124] SCSI subsystem initialized
[    2.706235] usbcore: registered new device driver usb
[    2.706947] USB Universal Host Controller Interface driver v3.0
[    2.706983] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.706992] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    2.706995] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.707080] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.707104] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030a0
[    2.707188] usb usb1: configuration #1 chosen from 1 choice
[    2.707209] hub 1-0:1.0: USB hub found
[    2.707214] hub 1-0:1.0: 2 ports detected
[    2.715513] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    2.715516] Copyright (c) 1999-2006 Intel Corporation.
[    2.719642] libata version 2.20 loaded.
[    2.759083] ieee1394: Initialized config rom entry `ip1394'
[    2.811085] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[    2.811094] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    2.811097] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.811190] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.811216] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00003080
[    2.811559] usb usb2: configuration #1 chosen from 1 choice
[    2.811677] hub 2-0:1.0: USB hub found
[    2.811682] hub 2-0:1.0: 2 ports detected
[    2.919677] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    2.919684] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    2.919687] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.919704] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    2.919727] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00003060
[    2.919796] usb usb3: configuration #1 chosen from 1 choice
[    2.919816] hub 3-0:1.0: USB hub found
[    2.919820] hub 3-0:1.0: 2 ports detected
[    3.023964] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.023972] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.023975] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.023995] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.024019] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
[    3.024098] usb usb4: configuration #1 chosen from 1 choice
[    3.024121] hub 4-0:1.0: USB hub found
[    3.024126] hub 4-0:1.0: 2 ports detected
[    3.128901] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.128909] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.128913] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.128933] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.128957] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
[    3.129035] usb usb5: configuration #1 chosen from 1 choice
[    3.129059] hub 5-0:1.0: USB hub found
[    3.129074] hub 5-0:1.0: 2 ports detected
[    3.234041] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 22
[    3.234052] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    3.262559] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:0a:4d:63
[    3.356408] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.356485] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    3.356498] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.356501] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.356528] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.356553] ehci_hcd 0000:00:1a.7: debug port 1
[    3.356558] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.356564] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x92225400
[    3.360452] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.360519] usb usb6: configuration #1 chosen from 1 choice
[    3.360541] hub 6-0:1.0: USB hub found
[    3.360546] hub 6-0:1.0: 4 ports detected
[    3.467304] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    3.467314] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.467317] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.467340] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.467365] ehci_hcd 0000:00:1d.7: debug port 1
[    3.467371] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.467376] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x92225000
[    3.471263] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.471325] usb usb7: configuration #1 chosen from 1 choice
[    3.471346] hub 7-0:1.0: USB hub found
[    3.471351] hub 7-0:1.0: 6 ports detected
[    3.571842] ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[    3.621582] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[92004000-920047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.622953] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.622969] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    3.623221] ata1: PATA max UDMA/100 cmd 0x00011018 ctl 0x00011026 bmdma 0x00011000 irq 17
[    3.623234] scsi0 : pata_marvell
[    3.624135] BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
[    4.107964] ata1.00: ATAPI, max UDMA/66
[    4.107968] ata1.01: ATAPI, max UDMA/33
[    4.273472] ata1.00: configured for UDMA/66
[    4.439131] ata1.01: configured for UDMA/33
[    4.442424] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[    4.446169] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    4.446422] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.446427] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    4.446447] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[    4.446461] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.446485] ata2: SATA max UDMA/133 cmd 0x00013138 ctl 0x0001314e bmdma 0x00013110 irq 19
[    4.446503] ata3: SATA max UDMA/133 cmd 0x00013130 ctl 0x0001314a bmdma 0x00013118 irq 19
[    4.446510] scsi1 : ata_piix
[    4.610286] ATA: abnormal status 0x7F on port 0x0001313f
[    4.610294] scsi2 : ata_piix
[    4.791280] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    4.791285] ata3.00: ATA-7: WDC WD4000KS-00MNB0, 07.02E07, max UDMA/133
[    4.791289] ata3.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.802094] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    4.802099] ata3.00: configured for UDMA/133
[    4.802241] scsi 2:0:0:0: Direct-Access     ATA      WDC WD4000KS-00M 07.0 PQ: 0 ANSI: 5
[    4.802356] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    4.802373] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[    4.802385] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    4.802406] ata4: SATA max UDMA/133 cmd 0x00013128 ctl 0x00013146 bmdma 0x000130f0 irq 19
[    4.802424] ata5: SATA max UDMA/133 cmd 0x00013120 ctl 0x00013142 bmdma 0x000130f8 irq 19
[    4.802430] scsi3 : ata_piix
[    4.894611] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001d98f6c]
[    4.969464] ATA: abnormal status 0x7F on port 0x0001312f
[    4.969474] scsi4 : ata_piix
[    5.134252] ATA: abnormal status 0x7F on port 0x00013127
[    5.156651] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.156655] Uniform CD-ROM driver Revision: 3.20
[    5.156698] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.168414] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    5.168448] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    5.168617] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    5.168626] sda: Write Protect is off
[    5.168628] sda: Mode Sense: 00 3a 00 00
[    5.168641] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.168674] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    5.168682] sda: Write Protect is off
[    5.168684] sda: Mode Sense: 00 3a 00 00
[    5.168696] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.168699]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.172273] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    5.172289] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.173997]  sda1 sda2 < sda5 > sda3 sda4
[    5.198361] sd 2:0:0:0: Attached scsi disk sda
[    5.393266] Attempting manual resume
[    5.393269] swsusp: Resume From Partition 8:5
[    5.393271] PM: Checking swsusp image.
[    5.393465] PM: Resume from disk failed.
[    5.419255] kjournald starting.  Commit interval 5 seconds
[    5.419260] EXT3-fs: mounted filesystem with writeback data mode.
[   27.389686] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   27.394389] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   27.394392] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   28.469029] input: PC Speaker as /class/input/input2
[   28.508008] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.509280] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.513442] Linux agpgart interface v0.102 (c) Dave Jones
[   28.534421] parport: PnPBIOS parport detected.
[   28.534474] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   28.537231] agpgart: Detected an Intel 965G Chipset.
[   28.549146] agpgart: AGP aperture is 256M @ 0x0
[   28.563220] iTCO_vendor_support: vendor-support=0
[   28.604219] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   28.745549] logips2pp: Detected unknown logitech mouse model 1
[   28.764851] nvidia: module license 'NVIDIA' taints kernel.
[   29.017279] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.017287] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   29.017442] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   29.111318] input: PS/2 Logitech Mouse as /class/input/input3
[   29.114252] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
[   29.114283] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.134944] NET: Registered protocol family 17
[   29.194882] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   29.194898] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   29.859456] fuse init (API version 7.8)
[   29.887801] lp0: using parport0 (interrupt-driven).
[   30.078586] Adding 6024332k swap on /dev/disk/by-uuid/9e149e3b-abbe-432b-80d9-0894876c2d71.  Priority:-1 extents:1 across:6024332k
[   30.317693] EXT3 FS on sda1, internal journal
[   30.778385] kjournald starting.  Commit interval 5 seconds
[   30.790836] EXT3 FS on sda4, internal journal
[   30.790841] EXT3-fs: mounted filesystem with ordered data mode.
[   30.809869] kjournald starting.  Commit interval 5 seconds
[   30.848855] EXT3 FS on sda3, internal journal
[   30.848861] EXT3-fs: mounted filesystem with ordered data mode.
[   36.403188] Using specific hotkey driver
[   36.480428] ibm_acpi: ec object not found
[   36.602148] No dock devices found.
[   36.643520] input: Power Button (FF) as /class/input/input4
[   36.643541] ACPI: Power Button (FF) [PWRF]
[   36.643573] input: Sleep Button (CM) as /class/input/input5
[   36.643592] ACPI: Sleep Button (CM) [SLPB]
[   36.718392] pcc_acpi: loading...
[   40.783166] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   40.783170] apm: disabled - APM is not SMP safe.
[42799.902935] Bluetooth: Core ver 2.11
[42799.902982] NET: Registered protocol family 31
[42799.902984] Bluetooth: HCI device and connection manager initialized
[42799.902987] Bluetooth: HCI socket layer initialized
[42853.139442] atkbd.c: Unknown key pressed (translated set 2, code 0x8b on isa0060/serio0).
[42853.139447] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
[42853.162406] atkbd.c: Unknown key released (translated set 2, code 0x8b on isa0060/serio0).
[42853.162409] atkbd.c: Use 'setkeycodes e00b <keycode>' to make it known.
```

also here is my output of lspci if it will help at all

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by Opeth115 on 2007-07-16
anybody know anything about my problem?

---

### Post by dabl on 2007-07-16
It's been a known/documented bug for some time:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55416](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55416)

On my Intel D975XBX motherboard, I've been looking at that error every boot for the past 8 months. AFAIK, it does not cause any problem with performance of the system -- all PCI devices work fine and I don't find any evidence of hardware or software issues, so I'm calling it a "feature"......  :roll:

---

### Post by Opeth115 on 2007-07-16
so there is nothing i can do to fix it?  and ur sure it does not cause problems with my performance?

---

### Post by dabl on 2007-07-16
> **Opeth115 said:**
> ur sure it does not cause problems with my performance?

I'm afraid only YOU can make that determination.  I cannot find any issues on my system (Ubuntu 7.04 64-bit low-latency, Kubuntu 7.04 32-bit).

As far as "fixing", every once in awhile I google the error message to see if there are any "fixes", but I have not looked lately.  If you find one, post it please! :)


EDIT:  Here's more: [http://bugzilla.kernel.org/show_bug.cgi?id=7917](http://bugzilla.kernel.org/show_bug.cgi?id=7917)

This means that it is a Linux kernel bug, not limited to *buntu.

---


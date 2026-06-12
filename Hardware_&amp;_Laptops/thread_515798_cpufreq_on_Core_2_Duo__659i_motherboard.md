---
title: "cpufreq on Core 2 Duo / 659i motherboard"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by jamesshuang on 2007-08-02
Hello everyone, I'm at my wit's end with this silly problem. I just built a new computer, Core 2 E4400 on an EVGA nvidia 650i Ultra motherboard. I can't seem to get speedstep working at all. The computer is stably overclocked from 2.0 ghz to 3.0 ghz. Cpu-Z in Vista shows the multiplier being reduced to 6x from 10x when it's downclocking, and the processor cools off there. However, trying to load speedstep-centrino or acpi-cpufreq under Feisty results in a "No such device" error. I also tried under 64-bit Gutsy, and still the same error. Does anyone have any idea what's happening? :confused:

The strange thing is, speedstep is currently enabled in bios, but Vista was showing downclocking even when speedstep was disabled. Is Vista using some strange downclocking method that I'm not aware of? Also, the motherboard said something about using TM1 & TM2 on the same page as enabling Speedstep, and the dmesg log does indicated something about TM2 (thermal monitoring).

---

### Post by anubhavrocks on 2007-08-02
post the output of 
```
dmesg
```

---

### Post by jamesshuang on 2007-08-02
Sorry it's really long...

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fdf0000 end: 000000007fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fef0000 size: 0000000000003000 end: 000000007fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fef3000 size: 000000000000d000 end: 000000007ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000d0000000 size: 0000000020000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3ee0
[    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524016
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524016
[    0.000000] On node 0 totalpages: 524016
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7e10
[    0.000000] ACPI: RSDT (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef3040
[    0.000000] ACPI: FADT (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef30c0
[    0.000000] ACPI: HPET (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef79c0
[    0.000000] ACPI: WDRT (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef7a40
[    0.000000] ACPI: MCFG (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef7b00
[    0.000000] ACPI: MADT (v001 Nvidia NVDAACPI 0x42302e31 NVDA 0x00000000) @ 0x7fef78c0
[    0.000000] ACPI: DSDT (v001 NVIDIA NVDAACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET timers must be located in memory.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:50100000)
[    0.000000] Detected 3000.123 MHz processor.
[   14.664648] Built 1 zonelists.  Total pages: 519923
[   14.664651] Kernel command line: root=UUID=fb82c3ae-54e8-4087-af12-b75437c96463 ro quiet splash
[   14.664730] mapped APIC to ffffd000 (fee00000)
[   14.664731] mapped IOAPIC to ffffc000 (fec00000)
[   14.664733] Enabling fast FPU save and restore... done.
[   14.664734] Enabling unmasked SIMD FPU exception support... done.
[   14.664738] Initializing CPU#0
[   14.664780] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.664830] spurious 8259A interrupt: IRQ7.
[   14.666206] Console: colour VGA+ 80x25
[   14.666384] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.666561] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.708858] Memory: 2067020k/2096064k available (1992k kernel code, 27716k reserved, 900k data, 328k init, 1178560k highmem)
[   14.708864] virtual kernel memory layout:
[   14.708864]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.708865]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.708865]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.708866]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.708867]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   14.708867]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   14.708868]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   14.708870] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.788673] Calibrating delay using timer specific routine.. 6005.14 BogoMIPS (lpj=12010298)
[   14.788696] Security Framework v1.0.0 initialized
[   14.788700] SELinux:  Disabled at boot.
[   14.788709] Mount-cache hash table entries: 512
[   14.788792] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   14.788797] monitor/mwait feature present.
[   14.788798] using mwait in idle threads.
[   14.788801] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.788802] CPU: L2 cache: 2048K
[   14.788803] CPU: Physical Processor ID: 0
[   14.788804] CPU: Processor Core ID: 0
[   14.788805] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   14.788811] Compat vDSO mapped to ffffe000.
[   14.788814] Remapping vsyscall page to ffffe000
[   14.788821] Checking 'hlt' instruction... OK.
[   14.804737] SMP alternatives: switching to UP code
[   14.804975] Early unpacking initramfs... done
[   14.981976] ACPI: Core revision 20060707
[   14.984795] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.987197] CPU0: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   14.987206] SMP alternatives: switching to SMP code
[   14.987252] Booting processor 1/1 eip 3000
[   14.997528] Initializing CPU#1
[   15.076406] Calibrating delay using timer specific routine.. 6000.45 BogoMIPS (lpj=12000914)
[   15.076410] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   15.076413] monitor/mwait feature present.
[   15.076415] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.076416] CPU: L2 cache: 2048K
[   15.076417] CPU: Physical Processor ID: 0
[   15.076418] CPU: Processor Core ID: 1
[   15.076419] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   15.076662] CPU1: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   15.076674] Total of 2 processors activated (12005.60 BogoMIPS).
[   15.076895] ENABLING IO-APIC IRQs
[   15.077075] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.224278] checking TSC synchronization across 2 CPUs: passed.
[    0.003995] Brought up 2 CPUs
[    0.217985] migration_cost=47
[    0.218133] Booting paravirtualized kernel on bare hardware
[    0.218185] Time: 16:56:53  Date: 07/02/107
[    0.218203] NET: Registered protocol family 16
[    0.218249] EISA bus registered
[    0.218251] ACPI: bus type pci registered
[    0.223851] PCI: PCI BIOS revision 3.00 entry at 0xfa670, last bus=4
[    0.223852] PCI: Using configuration type 1
[    0.223853] Setting up standard PCI resources
[    0.230378] ACPI: Interpreter enabled
[    0.230379] ACPI: Using IOAPIC for interrupt routing
[    0.230746] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.230749] PCI: Probing PCI hardware (bus 00)
[    0.232013] Boot video device is 0000:01:00.0
[    0.232210] PCI: Transparent bridge - 0000:00:10.0
[    0.232247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.278553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.280573] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.280756] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.280942] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.281127] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.281310] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 10 *11 14 15)
[    0.281493] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.281677] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.281859] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.282043] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.282225] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.282408] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.282594] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.282777] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.282959] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.283143] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.283328] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.283511] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.283695] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.283884] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.284115] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.284340] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.284563] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.284788] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.285011] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0, disabled.
[    0.285234] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[    0.285457] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.285682] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.285906] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.286130] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.286353] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.286579] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22 23) *0, disabled.
[    0.286804] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.287030] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.287255] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.287481] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.287707] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.287937] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.288162] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.288287] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.288291] pnp: PnP ACPI init
[    0.290801] pnp: PnP ACPI: found 14 devices
[    0.290803] PnPBIOS: Disabled by ACPI PNP
[    0.290829] PCI: Using ACPI for IRQ routing
[    0.290831] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.464059] NET: Registered protocol family 8
[    0.464060] NET: Registered protocol family 20
[    0.464314] pnp: 00:00: ioport range 0x1000-0x107f could not be reserved
[    0.464316] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.464317] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[    0.464319] pnp: 00:00: ioport range 0x1480-0x14ff could not be reserved
[    0.464320] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[    0.464322] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.464502] PCI: Bridge: 0000:00:03.0
[    0.464504]   IO window: a000-afff
[    0.464506]   MEM window: ca000000-cdffffff
[    0.464508]   PREFETCH window: b0000000-bfffffff
[    0.464511] PCI: Bridge: 0000:00:06.0
[    0.464512]   IO window: 8000-8fff
[    0.464514]   MEM window: cfd00000-cfdfffff
[    0.464516]   PREFETCH window: cfa00000-cfafffff
[    0.464518] PCI: Bridge: 0000:00:07.0
[    0.464519]   IO window: b000-bfff
[    0.464521]   MEM window: cf900000-cf9fffff
[    0.464523]   PREFETCH window: cfe00000-cfefffff
[    0.464525] PCI: Bridge: 0000:00:10.0
[    0.464527]   IO window: 9000-9fff
[    0.464530]   MEM window: cfc00000-cfcfffff
[    0.464532]   PREFETCH window: cfb00000-cfbfffff
[    0.464541] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.464547] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.464553] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.464560] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.464575] NET: Registered protocol family 2
[    0.511745] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.511835] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.512152] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512298] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512300] TCP reno registered
[    0.527863] checking if image is initramfs... it is
[    0.877008] Freeing initrd memory: 6777k freed
[    0.877389] audit: initializing netlink socket (disabled)
[    0.877399] audit(1186073814.484:1): initialized
[    0.877462] highmem bounce pool size: 64 pages
[    0.877515] VFS: Disk quotas dquot_6.5.1
[    0.877525] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.877554] io scheduler noop registered
[    0.877555] io scheduler anticipatory registered
[    0.877556] io scheduler deadline registered
[    0.877563] io scheduler cfq registered (default)
[    0.899663] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.899689] assign_interrupt_mode Found MSI capability
[    0.899690] Allocate Port Service[0000:00:03.0:pcie00]
[    0.899745] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.899771] assign_interrupt_mode Found MSI capability
[    0.899772] Allocate Port Service[0000:00:06.0:pcie00]
[    0.899827] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.899853] assign_interrupt_mode Found MSI capability
[    0.899854] Allocate Port Service[0000:00:07.0:pcie00]
[    0.899934] isapnp: Scanning for PnP cards...
[    1.252412] isapnp: No Plug & Play device found
[    1.263824] Real Time Clock Driver v1.12ac
[    1.263920] hpet_acpi_add: no address or irqs in _CRS
[    1.263931] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.264036] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.264413] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.264523] mice: PS/2 mouse device common for all mice
[    1.264834] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.264919] input: Macintosh mouse button emulation as /class/input/input0
[    1.264939] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.264942] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.265078] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.265079] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.267881] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.267883] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.267949] EISA: Probing bus 0 at eisa.0
[    1.267954] Cannot allocate resource for EISA slot 1
[    1.267969] Cannot allocate resource for EISA slot 8
[    1.267970] EISA: Detected 0 cards.
[    1.298052] TCP cubic registered
[    1.298058] NET: Registered protocol family 1
[    1.298072] Starting balanced_irq
[    1.298075] Using IPI No-Shortcut mode
[    1.298140] ACPI: (supports<6>input: AT Translated Set 2 keyboard as /class/input/input1
[    1.298144]  S0 S1 S3 S4 S5)
[    1.298177]   Magic number: 3:748:943
[    1.298207]   hash matches device ptyye
[    1.298228]   hash matches device tty0
[    1.298229]   hash matches device console
[    1.298351] Freeing unused kernel memory: 328k freed
[    1.298797] Time: tsc clocksource has been installed.
[    2.416970] Capability LSM initialized
[    2.437918] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.437929] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.437933] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.681206] usbcore: registered new interface driver usbfs
[    2.681221] usbcore: registered new interface driver hub
[    2.681235] usbcore: registered new device driver usb
[    2.681972] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[    2.681977] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
[    2.681984] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    2.681986] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.682066] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.682081] ehci_hcd 0000:00:0b.1: debug port 1
[    2.682084] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[    2.682090] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xcfffe000
[    2.682096] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.682142] usb usb1: configuration #1 chosen from 1 choice
[    2.682155] hub 1-0:1.0: USB hub found
[    2.682158] hub 1-0:1.0: 8 ports detected
[    2.694191] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.713366] SCSI subsystem initialized
[    2.721363] libata version 2.20 loaded.
[    2.724501] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    2.764744] FDC 0 is a post-1991 82077
[    2.789712] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    2.789716] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 17
[    2.789725] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    2.789727] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.789745] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.789755] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xcffff000
[    2.851392] usb usb2: configuration #1 chosen from 1 choice
[    2.851409] hub 2-0:1.0: USB hub found
[    2.851415] hub 2-0:1.0: 8 ports detected
[    2.954083] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    2.954087] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[    2.954091] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    2.954096] forcedeth: using HIGHDMA
[    3.275541] usb 2-7: new low speed USB device using ohci_hcd and address 2
[    3.476891] eth0: forcedeth.c: subsystem: 010de:0162 bound to 0000:00:14.0
[    3.478119] sata_nv 0000:00:0e.0: version 3.3
[    3.478377] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.478381] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[    3.478393] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    3.478619] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001e000 irq 19
[    3.478831] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001e008 irq 19
[    3.478839] scsi0 : sata_nv
[    3.494788] usb 2-7: configuration #1 chosen from 1 choice
[    3.503123] usbcore: registered new interface driver hiddev
[    3.509792] input: Logitech USB Receiver as /class/input/input2
[    3.509811] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-7
[    3.509818] usbcore: registered new interface driver usbhid
[    3.509820] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    3.947176] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.995252] ata1.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    3.995257] ata1.00: ATA-7: ST3300620AS, 3.AAE, max UDMA/133
[    3.995259] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.061808] ata1.00: ata_hpa_resize 1: sectors = 586072368, hpa_sectors = 586072368
[    4.061812] ata1.00: configured for UDMA/133
[    4.061819] scsi1 : sata_nv
[    4.373124] ata2: SATA link down (SStatus 0 SControl 300)
[    4.383523] ATA: abnormal status 0x7F on port 0x00010977
[    4.383586] scsi 0:0:0:0: Direct-Access     ATA      ST3300620AS      3.AA PQ: 0 ANSI: 5
[    4.384207] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    4.384209] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[    4.384221] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[    4.384240] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001cc00 irq 16
[    4.384256] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001cc08 irq 16
[    4.384261] scsi2 : sata_nv
[    4.698965] ata3: SATA link down (SStatus 0 SControl 300)
[    4.709363] ATA: abnormal status 0x7F on port 0x000109e7
[    4.709370] scsi3 : sata_nv
[    5.020226] ata4: SATA link down (SStatus 0 SControl 300)
[    5.030624] ATA: abnormal status 0x7F on port 0x00010967
[    5.032257] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    5.032270] NFORCE-MCP51: chipset revision 161
[    5.032271] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    5.032276] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[    5.032281]     ide0: BM-DMA at 0xf400-0xf407, BIOS settings: hda:DMA, hdb:DMA
[    5.032289] Probing IDE interface ide0...
[    5.041634] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    5.041641] sda: Write Protect is off
[    5.041642] sda: Mode Sense: 00 3a 00 00
[    5.041650] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.041674] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[    5.041679] sda: Write Protect is off
[    5.041680] sda: Mode Sense: 00 3a 00 00
[    5.041688] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.041690]  sda: sda1 sda2 sda3 sda4
[    5.068648] sd 0:0:0:0: Attached scsi disk sda
[    5.070958] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.348022] Attempting manual resume
[    5.348024] swsusp: Resume From Partition 8:3
[    5.348025] PM: Checking swsusp image.
[    5.348211] PM: Resume from disk failed.
[    5.362314] kjournald starting.  Commit interval 5 seconds
[    5.362321] EXT3-fs: mounted filesystem with ordered data mode.
[    5.769382] hda: SONY DVD RW DRU-510A, ATAPI CD/DVD-ROM drive
[    6.438619] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.728542] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.729905] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.776543] input: PC Speaker as /class/input/input3
[   11.852789] i2c_adapter i2c-0: nForce2 SMBus adapter at 0xfc00
[   11.852856] i2c_adapter i2c-1: nForce2 SMBus adapter at 0xf800
[   11.917502] Linux agpgart interface v0.102 (c) Dave Jones
[   12.078115] nvidia: module license 'NVIDIA' taints kernel.
[   12.332155] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   12.332161] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [AXV5] -> GSI 16 (level, low) -> IRQ 20
[   12.332168] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   12.332246] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   12.333357] NET: Registered protocol family 17
[   12.334996] hda: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
[   12.335001] Uniform CD-ROM driver Revision: 3.20
[   12.460594] ACPI: PCI Interrupt Link [APCI] enabled at IRQ 22
[   12.460597] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [APCI] -> GSI 22 (level, low) -> IRQ 17
[   12.460607] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   12.672013] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   12.915091] fuse init (API version 7.8)
[   12.940001] lp: driver loaded but no devices found
[   13.912599] Adding 2000084k swap on /dev/disk/by-uuid/f266af25-04d4-4ab3-a287-b505dc09d127.  Priority:-1 extents:1 across:2000084k
[   14.012983] EXT3 FS on sda2, internal journal
[   14.140645] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   14.140772] SGI XFS Quota Management subsystem
[   14.205705] XFS mounting filesystem sda4
[   14.286486] Ending clean XFS mount for filesystem: sda4
[   15.859103] NET: Registered protocol family 10
[   15.859156] lo: Disabled Privacy Extensions
[   19.742242] No dock devices found.
[   19.745373] input: Power Button (FF) as /class/input/input4
[   19.745388] ACPI: Power Button (FF) [PWRF]
[   19.745408] input: Power Button (CM) as /class/input/input5
[   19.745419] ACPI: Power Button (CM) [PWRB]
[   19.809153] ibm_acpi: ec object not found
[   19.840224] Using specific hotkey driver
[   19.945076] pcc_acpi: loading...
[   24.505781] ppdev: user-space parallel port driver
[   25.019563] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   25.019566] apm: disabled - APM is not SMP safe.
[   25.514963] Bluetooth: Core ver 2.11
[   25.514994] NET: Registered protocol family 31
[   25.514995] Bluetooth: HCI device and connection manager initialized
[   25.514996] Bluetooth: HCI socket layer initialized
[   25.526682] Bluetooth: L2CAP ver 2.8
[   25.526684] Bluetooth: L2CAP socket layer initialized
[   25.533331] Bluetooth: RFCOMM socket layer initialized
[   25.533339] Bluetooth: RFCOMM TTY layer initialized
[   25.533340] Bluetooth: RFCOMM ver 1.8
[   39.418272] eth0: no IPv6 routers present
```

---

### Post by anubhavrocks on 2007-08-03
I think this is a kernel bug,can you perhaphs try a different kernel version perhaps
```
sudo apt-get install linux-image-2.6.17-11-generic 
```

---

### Post by Bachstelze on 2007-08-03
> **jamesshuang said:**
> However, trying to load speedstep-centrino or acpi-cpufreq under Feisty results in a "No such device" error. I also tried under 64-bit Gutsy, and still the same error. Does anyone have any idea what's happening? :confused:

What's happening is simply that the driver doesn't support your CPU yet.

---


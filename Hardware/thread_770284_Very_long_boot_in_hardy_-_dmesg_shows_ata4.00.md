---
title: "Very long boot in hardy - dmesg shows ata4.00"
date: 2008-04-27
forum: Hardware
---

### Post by tjansson on 2008-04-27
After a clean install of Ubuntu 8.04 on my machine the boot up process is stalling at certain point bootprocess making very slow ~ 4 minutes. I didn't experience the same problem in 7.10. 

My computer consist of:
Asus P5W DH motherboard
Core 2 Duo E6600 @ 3.1 GHz
2 Gb ram. 
Hitachi DeskStar T7K500 320 GB sata harddisk
LiteOn LH-18A1H - DVD drive
Club 3D X1950XT graphics card

When I look through dmesg I found what I belive is the problem namely

```

[   38.395437] usb 5-7.3: configuration #1 chosen from 1 choice
[   65.943437] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

```

Which doesn't end before way later:
```

[  206.659578] ata4: reset failed, giving up
[  206.659587] ata4: EH complete
[  206.659599] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

```

Basic googling didn't seem to give me a answer, so I hope that someone in here have experienced the same or know the solution? 

The full dmesg:
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524160) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524160
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524160
[    0.000000] On node 0 totalpages: 524160
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292481 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAF00 checksum 0
[    0.000000] ACPI: RSDP 000FAF00, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF80000, 0040 (r1 A_M_I_ OEMRSDT  12000726 MSFT       97)
[    0.000000] ACPI: FACP 7FF80200, 0081 (r1 A_M_I_ OEMFACP  12000726 MSFT       97)
[    0.000000] ACPI: DSDT 7FF80590, 9560 (r1  A0543 A0543000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FF8E000, 0040
[    0.000000] ACPI: APIC 7FF80390, 0080 (r1 A_M_I_ OEMAPIC  12000726 MSFT       97)
[    0.000000] ACPI: OEMB 7FF8E040, 0066 (r1 A_M_I_ AMI_OEM  12000726 MSFT       97)
[    0.000000] ACPI: HPET 7FF89AF0, 0038 (r1 A_M_I_ OEMHPET  12000726 MSFT       97)
[    0.000000] ACPI: MCFG 7FF89B30, 003C (r1 A_M_I_ OEMMCFG  12000726 MSFT       97)
[    0.000000] ACPI: SSDT 7FF8E0B0, 01C6 (r1    AMI   CPU1PM        1 INTL 20060113)
[    0.000000] ACPI: SSDT 7FF8E280, 013A (r1    AMI   CPU2PM        1 INTL 20060113)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520065
[    0.000000] Kernel command line: root=UUID=9a036eac-db91-4a54-937f-2bf007e61459 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3117.878 MHz processor.
[   30.314085] Console: colour VGA+ 80x25
[   30.314088] console [tty0] enabled
[   30.314286] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.314470] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.367769] Memory: 2066340k/2096640k available (2157k kernel code, 29044k reserved, 998k data, 364k init, 1179136k highmem)
[   30.367773] virtual kernel memory layout:
[   30.367773]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.367774]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.367775]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.367775]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.367776]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   30.367776]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   30.367777]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   30.367779] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.367815] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   30.367903] hpet clockevent registered
[   30.447800] Calibrating delay using timer specific routine.. 6239.72 BogoMIPS (lpj=12479459)
[   30.447817] Security Framework initialized
[   30.447822] SELinux:  Disabled at boot.
[   30.447833] AppArmor: AppArmor initialized
[   30.447835] Failure registering capabilities with primary security module.
[   30.447841] Mount-cache hash table entries: 512
[   30.447938] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   30.447944] monitor/mwait feature present.
[   30.447945] using mwait in idle threads.
[   30.447948] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.447949] CPU: L2 cache: 4096K
[   30.447951] CPU: Physical Processor ID: 0
[   30.447952] CPU: Processor Core ID: 0
[   30.447953] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   30.447959] Compat vDSO mapped to ffffe000.
[   30.447969] Checking 'hlt' instruction... OK.
[   30.464021] SMP alternatives: switching to UP code
[   30.465015] Early unpacking initramfs... done
[   30.655883] ACPI: Core revision 20070126
[   30.655918] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.670427] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   30.670440] SMP alternatives: switching to SMP code
[   30.670892] Booting processor 1/1 eip 3000
[   30.681071] Initializing CPU#1
[   30.759378] Calibrating delay using timer specific routine.. 6235.57 BogoMIPS (lpj=12471155)
[   30.759382] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   30.759385] monitor/mwait feature present.
[   30.759387] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.759388] CPU: L2 cache: 4096K
[   30.759389] CPU: Physical Processor ID: 0
[   30.759390] CPU: Processor Core ID: 1
[   30.759391] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   30.759857] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   30.759870] Total of 2 processors activated (12475.30 BogoMIPS).
[   30.760006] ENABLING IO-APIC IRQs
[   30.760162] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.923158] APIC calibration not consistent with PM Timer: 115ms instead of 100ms
[   30.923160] APIC delta adjusted to PM-Timer: 2165128 (2511515)
[   30.923233] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.943219] Brought up 2 CPUs
[   30.943237] CPU0 attaching sched-domain:
[   30.943238]  domain 0: span 03
[   30.943239]   groups: 01 02
[   30.943241] CPU1 attaching sched-domain:
[   30.943242]  domain 0: span 03
[   30.943243]   groups: 02 01
[   30.943387] net_namespace: 64 bytes
[   30.943393] Booting paravirtualized kernel on bare hardware
[   30.943665] Time: 12:24:59  Date: 04/27/08
[   30.943682] NET: Registered protocol family 16
[   30.943801] EISA bus registered
[   30.943804] ACPI: bus type pci registered
[   30.943944] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   30.943945] PCI: Using configuration type 1
[   30.943946] Setting up standard PCI resources
[   30.952358] ACPI: EC: Look up EC in DSDT
[   30.957250] ACPI: Interpreter enabled
[   30.957252] ACPI: (supports S0 S1 S3 S4 S5)
[   30.957260] ACPI: Using IOAPIC for interrupt routing
[   30.961098] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.961519] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   30.961522] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   30.962112] PCI: Transparent bridge - 0000:00:1e.0
[   30.962136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.962220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   30.962271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   30.962338] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   30.962389] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   30.962433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   30.963913] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.963985] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   30.964056] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   30.964127] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   30.964198] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   30.964268] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   30.964339] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.964410] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.964484] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  AD, should be A4 [20070126]
[   30.964491] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.964509] pnp: PnP ACPI init
[   30.964513] ACPI: bus type pnp registered
[   30.966325] pnp: PnP ACPI: found 15 devices
[   30.966327] ACPI: ACPI bus type pnp unregistered
[   30.966329] PnPBIOS: Disabled by ACPI PNP
[   30.966467] PCI: Using ACPI for IRQ routing
[   30.966469] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.995072] NET: Registered protocol family 8
[   30.995074] NET: Registered protocol family 20
[   30.995093] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   30.995095] hpet0: 3 64-bit timers, 14318180 Hz
[   30.996114] AppArmor: AppArmor Filesystem Enabled
[   30.999063] Time: tsc clocksource has been installed.
[   31.015063] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   31.015068] system 00:07: ioport range 0x290-0x297 has been reserved
[   31.015071] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   31.015072] system 00:08: ioport range 0x800-0x87f has been reserved
[   31.015073] system 00:08: ioport range 0x400-0x41f has been reserved
[   31.015075] system 00:08: ioport range 0x480-0x4bf has been reserved
[   31.015076] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   31.015078] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   31.015079] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   31.015081] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   31.015082] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   31.015086] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   31.015087] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[   31.015091] system 00:0d: iomem range 0xf0000000-0xf3ffffff has been reserved
[   31.015095] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   31.015096] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   31.015097] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   31.015099] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[   31.015100] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   31.015120] Switched to high resolution mode on CPU 1
[   31.019038] Switched to high resolution mode on CPU 0
[   31.045308] PCI: Bridge: 0000:00:01.0
[   31.045310]   IO window: c000-cfff
[   31.045312]   MEM window: ff900000-ff9fffff
[   31.045313]   PREFETCH window: cff00000-efefffff
[   31.045315] PCI: Bridge: 0000:00:1c.0
[   31.045316]   IO window: disabled.
[   31.045319]   MEM window: disabled.
[   31.045321]   PREFETCH window: cfe00000-cfefffff
[   31.045324] PCI: Bridge: 0000:00:1c.3
[   31.045325]   IO window: b000-bfff
[   31.045328]   MEM window: ff800000-ff8fffff
[   31.045330]   PREFETCH window: disabled.
[   31.045333] PCI: Bridge: 0000:00:1c.4
[   31.045335]   IO window: a000-afff
[   31.045338]   MEM window: ff700000-ff7fffff
[   31.045340]   PREFETCH window: disabled.
[   31.045343] PCI: Bridge: 0000:00:1e.0
[   31.045343]   IO window: disabled.
[   31.045346]   MEM window: ff600000-ff6fffff
[   31.045348]   PREFETCH window: disabled.
[   31.045358] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.045361] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.045372] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.045375] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.045387] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[   31.045390] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   31.045402] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   31.045405] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.045412] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.045418] NET: Registered protocol family 2
[   31.086951] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.087068] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.087351] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.087505] TCP: Hash tables configured (established 131072 bind 65536)
[   31.087506] TCP reno registered
[   31.098975] checking if image is initramfs... it is
[   31.475151] Freeing initrd memory: 7690k freed
[   31.475694] audit: initializing netlink socket (disabled)
[   31.475705] audit(1209299098.960:1): initialized
[   31.475864] highmem bounce pool size: 64 pages
[   31.477024] VFS: Disk quotas dquot_6.5.1
[   31.477071] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.477160] io scheduler noop registered
[   31.477161] io scheduler anticipatory registered
[   31.477162] io scheduler deadline registered
[   31.477168] io scheduler cfq registered (default)
[   31.477239] Boot video device is 0000:05:00.0
[   31.477305] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.477326] assign_interrupt_mode Found MSI capability
[   31.477345] Allocate Port Service[0000:00:01.0:pcie00]
[   31.477391] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.477419] assign_interrupt_mode Found MSI capability
[   31.477442] Allocate Port Service[0000:00:1c.0:pcie00]
[   31.477462] Allocate Port Service[0000:00:1c.0:pcie02]
[   31.477517] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   31.477545] assign_interrupt_mode Found MSI capability
[   31.477568] Allocate Port Service[0000:00:1c.3:pcie00]
[   31.477622] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   31.477650] assign_interrupt_mode Found MSI capability
[   31.477673] Allocate Port Service[0000:00:1c.4:pcie00]
[   31.477827] isapnp: Scanning for PnP cards...
[   31.830312] isapnp: No Plug & Play device found
[   31.844568] Real Time Clock Driver v1.12ac
[   31.844702] hpet_resources: 0xfed00000 is busy
[   31.844728] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.844822] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.845226] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.845656] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.845697] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.845753] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   31.845754] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   31.846155] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.873911] mice: PS/2 mouse device common for all mice
[   31.873976] EISA: Probing bus 0 at eisa.0
[   31.873997] EISA: Detected 0 cards.
[   31.873999] cpuidle: using governor ladder
[   31.874000] cpuidle: using governor menu
[   31.874052] NET: Registered protocol family 1
[   31.874070] Using IPI No-Shortcut mode
[   31.874097] registered taskstats version 1
[   31.874163]   Magic number: 4:662:431
[   31.874197] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.874199] EDD information not available.
[   31.874312] Freeing unused kernel memory: 364k freed
[   31.903772] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.991393] fuse init (API version 7.9)
[   33.002162] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._OSC] (Node f7c45198), AE_ALREADY_EXISTS
[   33.002168] ACPI: Marking method _OSC as Serialized
[   33.002193] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f7c45180), AE_ALREADY_EXISTS
[   33.002196] ACPI: Marking method _PDC as Serialized
[   33.002232] ACPI: Processor [CPU1] (supports 8 throttling states)
[   33.002321] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._OSC] (Node f7c45270), AE_ALREADY_EXISTS
[   33.002325] ACPI: Marking method _OSC as Serialized
[   33.002344] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f7c45258), AE_ALREADY_EXISTS
[   33.002347] ACPI: Marking method _PDC as Serialized
[   33.002392] ACPI: Processor [CPU2] (supports 8 throttling states)
[   33.002400] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.002406] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.176221] usbcore: registered new interface driver usbfs
[   33.176236] usbcore: registered new interface driver hub
[   33.181774] usbcore: registered new device driver usb
[   33.182578] USB Universal Host Controller Interface driver v3.0
[   33.182620] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   33.182627] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   33.182629] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   33.182796] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   33.182818] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000e480
[   33.182894] usb usb1: configuration #1 chosen from 1 choice
[   33.182907] hub 1-0:1.0: USB hub found
[   33.182910] hub 1-0:1.0: 2 ports detected
[   33.211961] SCSI subsystem initialized
[   33.216059] libata version 3.00 loaded.
[   33.248832] Floppy drive(s): fd0 is 1.44M
[   33.269566] FDC 0 is a post-1991 82077
[   33.288018] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 19
[   33.288026] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   33.288028] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   33.288043] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   33.288065] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e800
[   33.288131] usb usb2: configuration #1 chosen from 1 choice
[   33.288144] hub 2-0:1.0: USB hub found
[   33.288147] hub 2-0:1.0: 2 ports detected
[   33.391871] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   33.391879] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   33.391882] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   33.391896] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   33.391916] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
[   33.391978] usb usb3: configuration #1 chosen from 1 choice
[   33.391991] hub 3-0:1.0: USB hub found
[   33.391994] hub 3-0:1.0: 2 ports detected
[   33.495724] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[   33.495732] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   33.495734] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   33.495748] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   33.495770] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
[   33.495835] usb usb4: configuration #1 chosen from 1 choice
[   33.495849] hub 4-0:1.0: USB hub found
[   33.495852] hub 4-0:1.0: 2 ports detected
[   33.527620] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   33.595727] ata_piix 0000:00:1f.1: version 2.12
[   33.595739] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 21
[   33.595760] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   33.596172] scsi0 : ata_piix
[   33.596199] scsi1 : ata_piix
[   33.596876] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   33.596878] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   33.702198] usb 1-2: configuration #1 chosen from 1 choice
[   33.947046] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   34.120012] usb 3-1: configuration #1 chosen from 1 choice
[   34.262923] ata1.00: ATAPI: SONY    CD-RW  CRX175A1, 5YS2, max UDMA/33
[   34.262939] ata1.01: ATAPI: LITE-ON DVDRW LH-18A1H, HL01, max UDMA/66
[   34.262949] ata1.01: limited to UDMA/33 due to 40-wire cable
[   34.362480] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   34.427634] ata1.00: configured for UDMA/33
[   34.524468] usb 4-1: configuration #1 chosen from 1 choice
[   34.528425] hub 4-1:1.0: USB hub found
[   34.530411] hub 4-1:1.0: 4 ports detected
[   34.614375] ata1.01: configured for UDMA/33
[   34.780882] scsi 0:0:0:0: CD-ROM            SONY     CD-RW  CRX175A1  5YS2 PQ: 0 ANSI: 5
[   34.781867] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LH-18A1H   HL01 PQ: 0 ANSI: 5
[   34.781907] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   34.846989] usb 4-1.3: new full speed USB device using uhci_hcd and address 3
[   34.937713] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 22
[   34.937732] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   34.937756] scsi2 : ata_piix
[   34.937834] scsi3 : ata_piix
[   34.937853] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 22
[   34.937854] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 22
[   34.975862] usb 4-1.3: configuration #1 chosen from 1 choice
[   34.985810] usbcore: registered new interface driver hiddev
[   34.991545] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[   35.013616] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[   35.021407] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[   35.030808] hiddev97hidraw2: USB HID v1.10 Device [T-wins ASUS DH Remote] on usb-0000:00:1d.2-1
[   35.030816] usbcore: registered new interface driver usbhid
[   35.030817] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.101826] ata3.00: ATA-7: Hitachi HDT725032VLA360, V54OA52A, max UDMA/133
[   35.101829] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   35.117809] ata3.00: configured for UDMA/133
[   35.776844] ata4.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[   35.776846] ata4.00: 640 sectors, multi 1: LBA 
[   35.776850] ata4.00: Drive reports diagnostics failure. This may indicate a drive
[   35.776852] ata4.00: fault or invalid emulation. Contact drive vendor for information.
[   35.776855] ata4.00: device is on DMA blacklist, disabling DMA
[   35.777187] ata4.00: configured for PIO4
[   35.777256] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   35.777332] scsi 3:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[   35.777536] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   35.777545] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   35.777550] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   35.777565] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   35.781451] ehci_hcd 0000:00:1d.7: debug port 1
[   35.781455] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   35.781458] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffafbc00
[   35.797523] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.797582] usb usb5: configuration #1 chosen from 1 choice
[   35.797597] hub 5-0:1.0: USB hub found
[   35.797600] hub 5-0:1.0: 8 ports detected
[   35.864460] usb 1-2: USB disconnect, address 2
[   35.901481] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 23
[   35.951091] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[ff6ff800-ff6fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   35.959104] Driver 'sd' needs updating - please use bus_type methods
[   35.959165] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   35.959172] sd 2:0:0:0: [sda] Write Protect is off
[   35.959173] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.959182] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.959211] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   35.959216] sd 2:0:0:0: [sda] Write Protect is off
[   35.959217] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.959226] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.959228]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   35.963305] sr0: scsi3-mmc drive: 149x/40x writer cd/rw xa/form2 cdda tray
[   35.963307] Uniform CD-ROM driver Revision: 3.20
[   35.963331] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   35.970621] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.970644] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   35.971051]  sda1 sda2 < sda5 sda6 > sda3
[   35.985786] sd 2:0:0:0: [sda] Attached SCSI disk
[   35.985815] sd 3:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   35.985821] sd 3:0:0:0: [sdb] Write Protect is off
[   35.985822] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.985832] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   35.985853] sd 3:0:0:0: [sdb] 640 512-byte hardware sectors (0 MB)
[   35.985859] sd 3:0:0:0: [sdb] Write Protect is off
[   35.985860] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   35.985869] sd 3:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   35.985870]  sdb:<6>usb 3-1: USB disconnect, address 2
[   36.173022] usb 4-1: USB disconnect, address 2
[   36.173024] usb 4-1.3: USB disconnect, address 3
[   36.963935] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   37.100044] usb 5-7: configuration #1 chosen from 1 choice
[   37.100255] hub 5-7:1.0: USB hub found
[   37.100493] hub 5-7:1.0: 4 ports detected
[   37.218650] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000fbed6e]
[   37.442280] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   37.625948] usb 1-2: configuration #1 chosen from 1 choice
[   37.639015] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input3
[   37.666998] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[   37.674866] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[   37.913638] usb 3-1: new low speed USB device using uhci_hcd and address 3
[   38.086707] usb 3-1: configuration #1 chosen from 1 choice
[   38.099715] hiddev97hidraw2: USB HID v1.10 Device [T-wins ASUS DH Remote] on usb-0000:00:1d.2-1
[   38.297397] usb 5-7.3: new high speed USB device using ehci_hcd and address 5
[   38.395437] usb 5-7.3: configuration #1 chosen from 1 choice
[   65.943437] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   65.943443] ata4.00: cmd c4/00:08:00:00:00/00:00:00:00:00/e0 tag 0 pio 4096 in
[   65.943444]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   65.943446] ata4.00: status: { DRDY }
[   65.943455] ata4: soft resetting link
[   66.285231] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   66.285233] ata4.00: revalidation failed (errno=-5)
[   66.285234] ata4: failed to recover some devices, retrying in 5 secs
[   71.280153] ata4: soft resetting link
[   71.625456] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   71.625457] ata4.00: revalidation failed (errno=-5)
[   71.625459] ata4: failed to recover some devices, retrying in 5 secs
[   76.620870] ata4: soft resetting link
[   81.809791] ata4: port is slow to respond, please be patient (Status 0xd0)
[   86.619234] ata4: SRST failed (errno=-16)
[   86.619237] ata4: soft resetting link
[   91.812153] ata4: port is slow to respond, please be patient (Status 0xd0)
[   96.617603] ata4: SRST failed (errno=-16)
[   96.617605] ata4: soft resetting link
[  101.806528] ata4: port is slow to respond, please be patient (Status 0xd0)
[  131.613890] ata4: SRST failed (errno=-16)
[  131.613892] ata4: soft resetting link
[  136.636042] ata4: SRST failed (errno=-16)
[  136.636045] ata4: reset failed, giving up
[  136.636047] ata4.00: disabled
[  141.668182] ata4: port is slow to respond, please be patient (Status 0xd0)
[  146.645397] ata4: device not ready (errno=-16), forcing hardreset
[  146.645399] ata4: soft resetting link
[  151.834322] ata4: port is slow to respond, please be patient (Status 0xd0)
[  156.643768] ata4: SRST failed (errno=-16)
[  156.643770] ata4: soft resetting link
[  161.832691] ata4: port is slow to respond, please be patient (Status 0xd0)
[  166.642134] ata4: SRST failed (errno=-16)
[  166.642135] ata4: soft resetting link
[  171.831060] ata4: port is slow to respond, please be patient (Status 0xd0)
[  201.638422] ata4: SRST failed (errno=-16)
[  201.638425] ata4: soft resetting link
[  206.659576] ata4: SRST failed (errno=-16)
[  206.659578] ata4: reset failed, giving up
[  206.659587] ata4: EH complete
[  206.659599] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659602] end_request: I/O error, dev sdb, sector 0
[  206.659605] Buffer I/O error on device sdb, logical block 0
[  206.659630] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659633] end_request: I/O error, dev sdb, sector 0
[  206.659634] Buffer I/O error on device sdb, logical block 0
[  206.659649] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659651] end_request: I/O error, dev sdb, sector 0
[  206.659652] Buffer I/O error on device sdb, logical block 0
[  206.659664] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659666] end_request: I/O error, dev sdb, sector 0
[  206.659667] Buffer I/O error on device sdb, logical block 0
[  206.659677] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659679] end_request: I/O error, dev sdb, sector 0
[  206.659681] Buffer I/O error on device sdb, logical block 0
[  206.659685] ldm_validate_partition_table(): Disk read failed.
[  206.659693] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659695] end_request: I/O error, dev sdb, sector 0
[  206.659696] Buffer I/O error on device sdb, logical block 0
[  206.659706] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659708] end_request: I/O error, dev sdb, sector 0
[  206.659709] Buffer I/O error on device sdb, logical block 0
[  206.659719] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659721] end_request: I/O error, dev sdb, sector 0
[  206.659722] Buffer I/O error on device sdb, logical block 0
[  206.659732] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659734] end_request: I/O error, dev sdb, sector 0
[  206.659735] Buffer I/O error on device sdb, logical block 0
[  206.659739] Dev sdb: unable to read RDB block 0
[  206.659747] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659749] end_request: I/O error, dev sdb, sector 0
[  206.659750] Buffer I/O error on device sdb, logical block 0
[  206.659760] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659762] end_request: I/O error, dev sdb, sector 0
[  206.659779] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659781] end_request: I/O error, dev sdb, sector 24
[  206.659789] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659791] end_request: I/O error, dev sdb, sector 24
[  206.659800] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659802] end_request: I/O error, dev sdb, sector 0
[  206.659812] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.659814] end_request: I/O error, dev sdb, sector 0
[  206.659818]  unable to read partition table
[  206.659854] sd 3:0:0:0: [sdb] Attached SCSI disk
[  206.664718] sr 0:0:0:0: Attached scsi generic sg0 type 5
[  206.664730] sr 0:0:1:0: Attached scsi generic sg1 type 5
[  206.664742] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  206.664752] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  206.695249] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.695252] end_request: I/O error, dev sdb, sector 0
[  206.695265] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  206.695268] end_request: I/O error, dev sdb, sector 0
[  206.827809] Attempting manual resume
[  206.827811] swsusp: Resume From Partition 8:5
[  206.827812] PM: Checking swsusp image.
[  206.827911] PM: Resume from disk failed.
[  206.863197] kjournald starting.  Commit interval 5 seconds
[  206.863200] EXT3-fs: mounted filesystem with ordered data mode.
[  211.074363] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  211.074367] end_request: I/O error, dev sdb, sector 0
[  211.074377] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  211.074379] end_request: I/O error, dev sdb, sector 0
[  211.596013] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  211.705842] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  211.722083] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  211.739729] iTCO_vendor_support: vendor-support=0
[  211.753709] EDAC MC: Ver: 2.1.0 Apr 10 2008
[  211.800001] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  211.800058] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[  211.800082] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  211.825720] EDAC i82975x: ECC disabled on both channels.
[  211.839665] input: Power Button (FF) as /devices/virtual/input/input5
[  211.840783] intel_rng: FWH not detected
[  211.893470] ACPI: Power Button (FF) [PWRF]
[  211.893525] input: Power Button (CM) as /devices/virtual/input/input6
[  211.957387] ACPI: Power Button (CM) [PWRB]
[  212.266744] Linux agpgart interface v0.102
[  212.336570] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[  212.336580] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  212.336599] sky2 0000:03:00.0: v1.20 addr 0xff8fc000 irq 17 Yukon-EC (0xb6) rev 2
[  212.337295] sky2 eth0: addr 00:18:f3:cd:8a:b6
[  212.337310] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  212.337316] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  212.337332] sky2 0000:02:00.0: v1.20 addr 0xff7fc000 irq 16 Yukon-EC (0xb6) rev 2
[  212.337584] sky2 eth1: addr 00:18:f3:cd:78:a0
[  212.391825] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 17
[  212.391840] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  212.394802] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  212.409551] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[  212.409572] [fglrx] ASYNCIO init succeed!
[  212.410872] [fglrx] PAT is enabled successfully!
[  212.410890] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[  212.772568] phy0: Selected rate control algorithm 'simple'
[  212.837707] phy0: hwaddr 00:15:af:0b:b9:53, rtl8187 V1 + rtl8225z2
[  212.837719] usbcore: registered new interface driver rtl8187
[  212.930849] loop: module loaded
[  212.964689] lp: driver loaded but no devices found
[  213.045378] w83627ehf: Found W83627DHG chip at 0x290
[  213.076177] Adding 2104472k swap on /dev/sda5.  Priority:-1 extents:1 across:2104472k
[  213.600401] EXT3 FS on sda3, internal journal
[  213.694708] device-mapper: uevent: version 1.0.3
[  213.694728] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[  214.392546] kjournald starting.  Commit interval 5 seconds
[  214.399274] EXT3 FS on sda6, internal journal
[  214.399277] EXT3-fs: mounted filesystem with ordered data mode.
[  214.733749] ip_tables: (C) 2000-2006 Netfilter Core Team
[  216.301565] No dock devices found.
[  217.197656] NET: Registered protocol family 10
[  217.197806] lo: Disabled Privacy Extensions
[  217.432664] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  217.432667] apm: disabled - APM is not SMP safe.
[  217.626947] ppdev: user-space parallel port driver
[  217.705746] audit(1209292085.816:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=10764 profile="/usr/sbin/cupsd" namespace="default"
[  219.597554] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  219.597562] end_request: I/O error, dev sdb, sector 0
[  219.597564] printk: 15 messages suppressed.
[  219.597566] Buffer I/O error on device sdb, logical block 0
[  219.597570] Buffer I/O error on device sdb, logical block 1
[  219.597583] sd 3:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  219.597588] end_request: I/O error, dev sdb, sector 0
[  219.709103] Bluetooth: Core ver 2.11
[  219.709174] NET: Registered protocol family 31
[  219.709176] Bluetooth: HCI device and connection manager initialized
[  219.709179] Bluetooth: HCI socket layer initialized
[  219.730895] Bluetooth: L2CAP ver 2.9
[  219.730899] Bluetooth: L2CAP socket layer initialized
[  219.769783] Bluetooth: RFCOMM socket layer initialized
[  219.769795] Bluetooth: RFCOMM TTY layer initialized
[  219.769796] Bluetooth: RFCOMM ver 1.8
[  221.563670] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  224.431431] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[  224.431436] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  224.431439] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[  224.431442] [fglrx] Reserve Block - 3 offset =  0Xffbf000 length = 0X40000
[  224.466958] [fglrx] interrupt source 20008000 successfully enabled
[  224.466963] [fglrx] enable ID = 0x00000008
[  224.466973] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  224.467023] [fglrx] interrupt source 10000000 successfully enabled
[  224.467025] [fglrx] enable ID = 0x00000009
[  224.467028] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  228.122401] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  228.147854] sky2 eth1: enabling interface
[  228.151049] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  228.159358] sky2 eth0: enabling interface
[  228.162526] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  229.220186] NET: Registered protocol family 17
[  229.843305] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  229.844984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  246.101801] eth0: no IPv6 routers present

```

---

### Post by BattlePanic on 2008-04-27
This sounds similar to a problem that appeared after my upgrade to Hardy.  I'm finding that the boot process is taking much longer than it ever did in Gutsy.

My system seems to pause fairly early on in the boot sequence.  This area of my dmesg log seems to be where there's a significant gap between entries.  Note the the timestamps.

```
[   12.029758] ata_piix 0000:00:1f.1: version 2.12
[   12.029775] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   12.039041] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.039493] scsi0 : ata_piix
[   12.049235] scsi1 : ata_piix
[   12.058589] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   12.067587] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   12.403447] ata1.00: ATA-6: TOSHIBA MK1031GAS, AA204A, max UDMA/100
[   12.412357] ata1.00: 195371568 sectors, multi 16: LBA48 
[   12.421239] ata1.01: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[   12.435326] ata1.00: configured for UDMA/100
[   12.514700] Clocksource tsc unstable (delta = -31417908463 ns)
[   12.523852] Time: hpet clocksource has been installed.
[   12.534548] ata1.01: configured for UDMA/33
[   12.543458] ata2: port disabled. ignoring.
[   12.543588] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1031GA AA20 PQ: 0 ANSI: 5
[   12.553229] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
```

Actually, the pause feels much longer than the timestamps would suggest.  I'm not sure why this would be.  Actually I don't know where these timestamps come from nor how to convert them to seconds.

It looks like the long pause is related to the detection and configuration of the disk drives.

I've included my full dmesg log below.

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003feea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feea000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7520 checksum 0
[    0.000000] ACPI: RSDP 000F7520, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3FEE58D2, 0044 (r1   Sony       J1 20050311 PTL         0)
[    0.000000] ACPI: APIC 3FEE9E78, 0068 (r1   Sony       J1 20050311 PTL        5F)
[    0.000000] ACPI: FACP 3FEE9EE0, 0084 (r2   Sony       J1 20050311 PTL        5F)
[    0.000000] ACPI: DSDT 3FEE6367, 3B11 (r1   Sony       J1 20050311 PTL  20030224)
[    0.000000] ACPI: FACS 3FEFAFC0, 0040
[    0.000000] ACPI: BOOT 3FEE9FD8, 0028 (r1   Sony       J1 20050311 PTL         1)
[    0.000000] ACPI: MCFG 3FEE9F9C, 003C (r1   Sony       J1 20050311 PTL        5F)
[    0.000000] ACPI: SSDT 3FEE618F, 01D4 (r1   Sony       J1 20050311 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE5D4A, 0277 (r1   Sony       J1 20050311 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE5B2F, 021B (r1   Sony       J1 20050311 PTL  20030224)
[    0.000000] ACPI: SSDT 3FEE5916, 0219 (r1   Sony       J1 20050311 PTL  20030224)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
[    0.000000] Kernel command line: root=UUID=133f14cf-4b0f-4456-8e61-7458389a7e94 ro vga=791
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.271 MHz processor.
[    7.150129] Console: colour dummy device 80x25
[    7.150134] console [tty0] enabled
[    7.150588] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.150988] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.179252] Memory: 1026200k/1047424k available (2157k kernel code, 20512k reserved, 998k data, 364k init, 129920k highmem)
[    7.179267] virtual kernel memory layout:
[    7.179268]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.179269]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.179270]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.179271]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.179272]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[    7.179273]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[    7.179275]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[    7.179296] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.179333] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.261894] Calibrating delay using timer specific routine.. 3728.54 BogoMIPS (lpj=7457080)
[    7.261922] Security Framework initialized
[    7.261930] SELinux:  Disabled at boot.
[    7.261945] AppArmor: AppArmor initialized
[    7.261951] Failure registering capabilities with primary security module.
[    7.261962] Mount-cache hash table entries: 512
[    7.262080] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    7.262093] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.262098] CPU: L2 cache: 2048K
[    7.262103] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[    7.262111] Compat vDSO mapped to ffffe000.
[    7.262124] Checking 'hlt' instruction... OK.
[    7.275560] SMP alternatives: switching to UP code
[    7.277268] Freeing SMP alternatives: 11k freed
[    7.277367] Early unpacking initramfs... done
[    7.613675] ACPI: Core revision 20070126
[    7.613730] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.623241] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    7.623274] Total of 1 processors activated (3728.54 BogoMIPS).
[    7.623473] ENABLING IO-APIC IRQs
[    7.623662] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    7.770488] Brought up 1 CPUs
[    7.770516] CPU0 attaching sched-domain:
[    7.770519]  domain 0: span 01
[    7.770520]   groups: 01
[    7.770683] net_namespace: 64 bytes
[    7.770693] Booting paravirtualized kernel on bare hardware
[    7.771148] Time:  7:28:38  Date: 04/27/08
[    7.771174] NET: Registered protocol family 16
[    7.771349] EISA bus registered
[    7.771378] ACPI: bus type pci registered
[    7.771842] PCI: PCI BIOS revision 2.10 entry at 0xfd91f, last bus=8
[    7.771847] PCI: Using configuration type 1
[    7.771851] Setting up standard PCI resources
[    7.869666] ACPI: EC: Look up EC in DSDT
[    7.873880] ACPI: Interpreter enabled
[    7.873885] ACPI: (supports S0 S3 S4 S5)
[    7.873899] ACPI: Using IOAPIC for interrupt routing
[    7.874318] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    7.978917] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    7.978923] ACPI: EC: driver started in interrupt mode
[    7.978960] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.979549] Force enabled HPET at base address 0xfed00000
[    7.979555] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    7.979562] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    7.980335] PCI: Transparent bridge - 0000:00:1e.0
[    7.980413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.980690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    7.980812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    7.984568] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    7.984652] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    7.984731] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    7.984811] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    7.984891] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    7.984969] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    7.985050] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    7.985130] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    7.985237] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.985266] pnp: PnP ACPI init
[    7.985274] ACPI: bus type pnp registered
[    7.987131] pnp: PnP ACPI: found 8 devices
[    7.987135] ACPI: ACPI bus type pnp unregistered
[    7.987140] PnPBIOS: Disabled by ACPI PNP
[    7.987327] PCI: Using ACPI for IRQ routing
[    7.987332] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.022060] NET: Registered protocol family 8
[    8.022064] NET: Registered protocol family 20
[    8.022210] hpet clockevent registered
[    8.022217] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    8.022223] hpet0: 3 64-bit timers, 14318180 Hz
[    8.023256] AppArmor: AppArmor Filesystem Enabled
[    8.026047] Time: tsc clocksource has been installed.
[    8.034066] system 00:04: ioport range 0x380-0x383 has been reserved
[    8.034071] system 00:04: ioport range 0x800-0x80f has been reserved
[    8.034076] system 00:04: ioport range 0x1000-0x107f has been reserved
[    8.034082] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    8.034087] system 00:04: ioport range 0x1640-0x164f has been reserved
[    8.034092] system 00:04: iomem range 0xf0008000-0xf000bfff could not be reserved
[    8.034099] system 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[    8.034105] system 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[    8.034111] system 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[    8.034117] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    8.064425] PCI: Bridge: 0000:00:01.0
[    8.064429]   IO window: disabled.
[    8.064433]   MEM window: 90000000-afffffff
[    8.064438]   PREFETCH window: c0000000-cfffffff
[    8.064450] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[    8.064454]   IO window: 00002400-000024ff
[    8.064462]   IO window: 00002800-000028ff
[    8.064470]   PREFETCH window: 50000000-53ffffff
[    8.064478]   MEM window: 54000000-57ffffff
[    8.064485] PCI: Bridge: 0000:00:1e.0
[    8.064489]   IO window: 2000-2fff
[    8.064497]   MEM window: b0000000-b00fffff
[    8.064502]   PREFETCH window: disabled.
[    8.064519] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.064528] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    8.064539] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.064559] PCI: Enabling device 0000:06:03.0 (0000 -> 0003)
[    8.064565] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[    8.064583] NET: Registered protocol family 2
[    8.101981] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.102181] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.102876] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.103264] TCP: Hash tables configured (established 131072 bind 65536)
[    8.103270] TCP reno registered
[    8.114047] checking if image is initramfs... it is
[    8.525275] Switched to high resolution mode on CPU 0
[    8.764357] Freeing initrd memory: 7409k freed
[    8.764580] Simple Boot Flag at 0x36 set to 0x1
[    8.764987] audit: initializing netlink socket (disabled)
[    8.765006] audit(1209281319.480:1): initialized
[    8.765170] highmem bounce pool size: 64 pages
[    8.766902] VFS: Disk quotas dquot_6.5.1
[    8.766978] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.767114] io scheduler noop registered
[    8.767119] io scheduler anticipatory registered
[    8.767123] io scheduler deadline registered
[    8.767135] io scheduler cfq registered (default)
[    8.767228] Boot video device is 0000:01:00.0
[    8.767240] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[    8.767349] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    8.767377] assign_interrupt_mode Found MSI capability
[    8.767406] Allocate Port Service[0000:00:01.0:pcie00]
[    8.767614] isapnp: Scanning for PnP cards...
[    9.121793] isapnp: No Plug & Play device found
[    9.145925] Real Time Clock Driver v1.12ac
[    9.146033] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.147088] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.147158] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    9.147245] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.152006] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.155297] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.155303] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.155308] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.155312] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.155316] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.164238] mice: PS/2 mouse device common for all mice
[    9.164341] EISA: Probing bus 0 at eisa.0
[    9.164351] Cannot allocate resource for EISA slot 1
[    9.164356] Cannot allocate resource for EISA slot 2
[    9.164387] EISA: Detected 0 cards.
[    9.164391] cpuidle: using governor ladder
[    9.164395] cpuidle: using governor menu
[    9.164483] NET: Registered protocol family 1
[    9.164511] Using IPI No-Shortcut mode
[    9.164546] registered taskstats version 1
[    9.164640]   Magic number: 4:682:471
[    9.164734] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.164739] EDD information not available.
[    9.164923] Freeing unused kernel memory: 364k freed
[    9.366720] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    9.379725] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 3072k, total 32768k
[    9.379733] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    9.379737] vesafb: protected mode interface info at c000:d360
[    9.379742] vesafb: pmi: set display start = c00cd396, set palette = c00cd400
[    9.379746] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    9.379761] vesafb: scrolling: redraw
[    9.379765] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    9.379868] Console: switching to colour frame buffer device 128x48
[    9.401096] fb0: VESA VGA frame buffer device
[    9.503223] fuse init (API version 7.9)
[   10.518119] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.518346] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.518615] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   10.520417] ACPI: Thermal Zone [THRM] (33 C)
[   11.060263] usbcore: registered new interface driver usbfs
[   11.060517] usbcore: registered new interface driver hub
[   11.073083] usbcore: registered new device driver usb
[   11.081067] USB Universal Host Controller Interface driver v3.0
[   11.081369] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   11.081681] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.081685] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.082229] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.082555] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001800
[   11.082910] usb usb1: configuration #1 chosen from 1 choice
[   11.091190] hub 1-0:1.0: USB hub found
[   11.100616] hub 1-0:1.0: 2 ports detected
[   11.165167] SCSI subsystem initialized
[   11.208946] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   11.217431] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.217436] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.225947] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.234565] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001820
[   11.243242] usb usb2: configuration #1 chosen from 1 choice
[   11.251894] hub 2-0:1.0: USB hub found
[   11.260847] hub 2-0:1.0: 2 ports detected
[   11.336646] libata version 3.00 loaded.
[   11.340636] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   11.349234] e100: Copyright(c) 1999-2006 Intel Corporation
[   11.384644] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   11.393270] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.393275] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.401820] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.410329] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001840
[   11.418767] usb usb3: configuration #1 chosen from 1 choice
[   11.427062] hub 3-0:1.0: USB hub found
[   11.435559] hub 3-0:1.0: 2 ports detected
[   11.544393] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   11.552707] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   11.552711] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   11.560956] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.569298] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   11.577957] usb usb4: configuration #1 chosen from 1 choice
[   11.586227] hub 4-0:1.0: USB hub found
[   11.594363] hub 4-0:1.0: 2 ports detected
[   11.704238] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   11.712571] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.712575] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.721901] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   11.734176] ehci_hcd 0000:00:1d.7: debug port 1
[   11.742281] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.742288] ehci_hcd 0000:00:1d.7: irq 17, io mem 0x80004000
[   11.763928] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.772060] usb usb5: configuration #1 chosen from 1 choice
[   11.780185] hub 5-0:1.0: USB hub found
[   11.788193] hub 5-0:1.0: 8 ports detected
[   11.899929] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   11.941828] e100: eth0: e100_probe: addr 0xb0007000, irq 20, MAC addr 00:01:4a:60:14:25
[   11.950249] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 18 (level, low) -> IRQ 19
[   12.008485] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[b0004000-b00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.029758] ata_piix 0000:00:1f.1: version 2.12
[   12.029775] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   12.039041] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.039493] scsi0 : ata_piix
[   12.049235] scsi1 : ata_piix
[   12.058589] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   12.067587] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   12.403447] ata1.00: ATA-6: TOSHIBA MK1031GAS, AA204A, max UDMA/100
[   12.412357] ata1.00: 195371568 sectors, multi 16: LBA48 
[   12.421239] ata1.01: ATAPI: MATSHITAUJ-840D, 1.00, max UDMA/33
[   12.435326] ata1.00: configured for UDMA/100
[   12.514700] Clocksource tsc unstable (delta = -31417908463 ns)
[   12.523852] Time: hpet clocksource has been installed.
[   12.534548] ata1.01: configured for UDMA/33
[   12.543458] ata2: port disabled. ignoring.
[   12.543588] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1031GA AA20 PQ: 0 ANSI: 5
[   12.553229] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.00 PQ: 0 ANSI: 5
[   12.576189] Driver 'sd' needs updating - please use bus_type methods
[   12.585353] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   12.594585] sd 0:0:0:0: [sda] Write Protect is off
[   12.603780] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.605205] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.614887] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   12.626112] Driver 'sr' needs updating - please use bus_type methods
[   12.635479] sd 0:0:0:0: [sda] Write Protect is off
[   12.644734] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.645075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.654541]  sda: sda1 sda2 < sda5 sda6 > sda3
[   12.669255] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.684218] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.693619] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   12.708427] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.717806] Uniform CD-ROM driver Revision: 3.20
[   12.727081] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   12.770695] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e5e27c]
[   12.855090] Attempting manual resume
[   12.864750] swsusp: Resume From Partition 8:6
[   12.864752] PM: Checking swsusp image.
[   12.864897] PM: Resume from disk failed.
[   12.897623] kjournald starting.  Commit interval 5 seconds
[   12.907209] EXT3-fs: mounted filesystem with ordered data mode.
[   15.271695] Linux agpgart interface v0.102
[   15.397056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.571364] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.700758] intel_rng: FWH not detected
[   16.033501] iTCO_vendor_support: vendor-support=0
[   16.068605] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   16.077199] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   16.085860] iTCO_wdt: No card detected
[   16.121127] input: Power Button (FF) as /devices/virtual/input/input2
[   16.144007] ACPI: Power Button (FF) [PWRF]
[   16.152664] input: Lid Switch as /devices/virtual/input/input3
[   16.167996] ACPI: Lid Switch [LID0]
[   16.176591] input: Power Button (CM) as /devices/virtual/input/input4
[   16.231856] ACPI: Power Button (CM) [PWRB]
[   16.294536] ACPI: Battery Slot [BAT0] (battery present)
[   16.304474] ACPI: AC Adapter [ADP1] (on-line)
[   16.385979] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   17.096689] Yenta: CardBus bridge found at 0000:06:03.0 [104d:818f]
[   17.105178] Yenta: Enabling burst memory read transactions
[   17.113585] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.121955] Yenta: Routing CardBus interrupts to PCI
[   17.130164] Yenta TI: socket 0000:06:03.0, mfunc 0x01001b22, devctl 0x64
[   17.190259] ieee80211_crypt: registered algorithm 'NULL'
[   17.246167] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.254621] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.370749] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   17.379418] Socket status: 30000006
[   17.387946] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   17.396678] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   17.405451] cs: IO port probe 0x2000-0x2fff: clean.
[   17.414299] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb00fffff
[   17.490036] nvidia: module license 'NVIDIA' taints kernel.
[   17.948980] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.957708] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.966545] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 22 (level, low) -> IRQ 21
[   18.020865] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.176876] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   18.200552] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   18.211328] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   18.232481] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   18.747760] sony-laptop: Sony Notebook Control Driver v0.5.
[   18.816451] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/SNY5001:00/input/input8
[   18.839534] input: Sony Vaio Jogdial as /devices/virtual/input/input9
[   19.604929] input: PS/2 Mouse as /devices/virtual/input/input10
[   19.688740] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   20.710927] cs: IO port probe 0x100-0x3af: clean.
[   20.723849] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.735520] cs: IO port probe 0x820-0x8ff: clean.
[   20.746921] cs: IO port probe 0xc00-0xcf7: clean.
[   20.758365] cs: IO port probe 0xa00-0xaff: clean.
[   20.937355] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   20.947952] ACPI: PCI Interrupt 0000:06:03.3[B] -> GSI 17 (level, low) -> IRQ 22
[   20.958575] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.969068] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.991847] tifm_core: MMC/SD card detected in socket 0:0
[   21.040767] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.051384] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   21.051496] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   21.306682] lp: driver loaded but no devices found
[   21.524764] Adding 570268k swap on /dev/sda6.  Priority:-1 extents:1 across:570268k
[   21.626316] EXT3 FS on sda3, internal journal
[   22.042357] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by BattlePanic on 2008-04-27
I should also add that I've found this problem occurs with Linux kernel version 2.6.24.16-generic.  While in GRUB, if I select the old kernel version 2.6.22.14-generic (which I was using for Gutsy) I don't run into this long pause.

A bit off topic, but there is definitely something weird happening with the timestamps.  The long pause lasts about 20 to 30 seconds but it is only represented by a value of 0.4 on the following entry's timestamp.  a difference of 0.4 is not proportional to the amount of real time taken as compared to the timestamps posted on all the other entries.  Although I'm not sure if it refers to the same thing, [this article]("http://lwn.net/Articles/209101/") seems to suggest that these timestamps values aren't necessarily an accurate measure of real time.

Does this mean that the processor is idle during this long pause?

---

### Post by BattlePanic on 2008-04-27
I came across [this posting]("http://bbs.archlinux.org/viewtopic.php?id=47039") in the Arch Linux forums which describes a similar problem.  A clear solution has yet to be found, though.

---

### Post by BattlePanic on 2008-04-30
I've discovered that passing the kernel the acpi=off option via grub eliminates the pause but then I also seem to lose gnome's power meter for my laptop and I can't detect the wireless networks that are in range.

I'd like to leave acpi on since it was probably turned on for a reason but this may be a clue as to why there it the long pause when booting.

---

### Post by tjansson on 2008-05-09
I think I might have found a solution in the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219312](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219312)

[I]Then you need to add 2 options in grub to get it booting correctly.
Add irqpoll and noprobe=ata4[/I]

---

### Post by saru411 on 2008-05-15
> **tjansson said:**
> 
[I]Then you need to add 2 options in grub to get it booting correctly.
Add irqpoll and noprobe=ata4[/I]

How would i do this in LILO? I gedit /etc/lilo.conf but I'm unsure of where to insert these commands.

---

### Post by tjansson on 2008-05-18
Even though the boot process is now only a minute long and not 5 minutes as before noprobe=ata4 there is still something fishy about the modprobe in in bootchart.

---

### Post by tjansson on 2008-05-18
saru411: It's been a while since I used a machine running lilo but as I remember it there is a file called /etc/lilo.conf which you should edit and afterwards run "lilo" to update lilo.

---

### Post by mbobak on 2008-05-19
> **tjansson said:**
> Even though the boot process is now only a minute long and not 5 minutes as before noprobe=ata4 there is still something fishy about the modprobe in in bootchart.


Still having problems here, after adding the boot options.

Also, how do I create one of those boot graphs?

-Mark

---

### Post by tjansson on 2008-05-20
The problem is not really gone it just seemed a little better. I created a bug repport on the subject which you should feel free to participate in:
[https://bugs.launchpad.net/ubuntu/+bug/231632](https://bugs.launchpad.net/ubuntu/+bug/231632)

The bootgraphs are real easy to create. Just install the package *bootchart*. Afterwards after each reboot a png image will be located in the folder:
/var/log/bootchart/

---

### Post by mccartyj on 2008-05-24
Same problem here... :(

Kinda hard to convince the wife to use linux when it takes 5-10 times longer to boot than windows.

---

### Post by tjansson on 2008-05-25
Seems that someone found a workaround:
[http://ubuntuforums.org/showpost.php?p=4774235&postcount=4](http://ubuntuforums.org/showpost.php?p=4774235&postcount=4)
it turned out that the problem could be resolved by changing the SATA Mode from IDE to RAID in BIOS. Now by system boots in 25 seconds.

---

### Post by outburst on 2008-05-27
I had system freezes and same exception on ata device, which I resolved disabling the promise controller of the motherboard P4C800 Deluxe. Hope this can help.

---

### Post by jonface on 2008-05-30
Using boot flags irqpoll and noprob=ata4.
Have tried enabling and disabling SATA raid in the bios but still the same thing. Ideas? Did not have this problem with 7.10. 


```

[  932.911907] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  932.911916] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  932.911917]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  932.911918]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  932.911920] ata4.00: status: { DRDY }
[  932.911932] ata4: soft resetting link
[  933.162101] ata4.00: configured for UDMA/33
[  933.162107] ata4: EH complete
[  947.880467] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  947.880476] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  947.880477]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  947.880478]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  947.880480] ata4.00: status: { DRDY }
[  947.880492] ata4: soft resetting link
[  948.129284] ata4.00: configured for UDMA/33
[  948.129294] ata4: EH complete
[  969.977686] ata4.00: qc timeout (cmd 0xa0)
[  969.977694] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  969.977701] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  969.977703]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  969.977704]          res 51/20:03:00:08:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  969.977706] ata4.00: status: { DRDY ERR }
[  969.977718] ata4: soft resetting link
[  970.226507] ata4.00: configured for UDMA/33
[  970.226522] ata4: EH complete
[  984.042477] ata4.00: limiting speed to UDMA/25:PIO4
[  984.042483] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  984.042490] ata4.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[  984.042491]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  984.042492]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  984.042495] ata4.00: status: { DRDY }
[  984.042507] ata4: soft resetting link
[  984.298669] ata4.00: configured for UDMA/25
[  984.298684] ata4: EH complete
[  999.017016] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  999.017026] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  999.017027]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  999.017028]          res 40/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[  999.017031] ata4.00: status: { DRDY }
[  999.017043] ata4: soft resetting link
[  999.265834] ata4.00: configured for UDMA/25
[  999.265844] ata4: EH complete
[ 1022.811236] ata4.00: qc timeout (cmd 0xa0)
[ 1022.811244] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1022.811251] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1022.811252]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1022.811253]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 1022.811256] ata4.00: status: { DRDY ERR }
[ 1022.811269] ata4: soft resetting link
[ 1023.060036] ata4.00: configured for UDMA/25
[ 1023.060049] ata4: EH complete
[ 1036.876024] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1036.876034] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1036.876035]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1036.876036]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1036.876039] ata4.00: status: { DRDY }
[ 1036.876052] ata4: soft resetting link
[ 1037.124844] ata4.00: configured for UDMA/25
[ 1037.124854] ata4: EH complete
[ 1050.940830] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1050.940840] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1050.940842]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1050.940843]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1050.940845] ata4.00: status: { DRDY }
[ 1050.940857] ata4: soft resetting link
[ 1051.189650] ata4.00: configured for UDMA/25
[ 1051.189663] ata4: EH complete
[ 1051.189671] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[ 1051.189677] sr: Sense Key : Aborted Command [current] [descriptor]
[ 1051.189681] sr: Add. Sense: No additional sense information
[ 1056.096708] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1056.096718] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1056.096720]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1056.096721]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1056.096723] ata4.00: status: { DRDY }
[ 1056.096736] ata4: soft resetting link
[ 1056.347145] ata4.00: configured for UDMA/25
[ 1056.347154] ata4: EH complete
[ 1061.854759] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1061.854767] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1061.854769]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1061.854770]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1061.854772] ata4.00: status: { DRDY }
[ 1061.854784] ata4: soft resetting link
[ 1062.103572] ata4.00: configured for UDMA/25
[ 1062.103579] ata4: EH complete
[ 1067.309374] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1067.309382] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1067.309384]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1067.309385]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1067.309387] ata4.00: status: { DRDY }
[ 1067.309399] ata4: soft resetting link
[ 1067.558192] ata4.00: configured for UDMA/25
[ 1067.558203] ata4: EH complete
[ 1072.465254] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1072.465262] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1072.465264]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1072.465265]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1072.465267] ata4.00: status: { DRDY }
[ 1072.465279] ata4: soft resetting link
[ 1072.714068] ata4.00: configured for UDMA/25
[ 1072.714077] ata4: EH complete
[ 1077.922956] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1077.922965] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1077.922966]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1077.922967]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1077.922969] ata4.00: status: { DRDY }
[ 1077.922981] ata4: soft resetting link
[ 1078.171768] ata4.00: configured for UDMA/25
[ 1078.171776] ata4: EH complete
[ 1083.078840] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1083.078848] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1083.078849]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1083.078850]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1083.078853] ata4.00: status: { DRDY }
[ 1083.078865] ata4: soft resetting link
[ 1083.327659] ata4.00: configured for UDMA/25
[ 1083.327672] ata4: EH complete
[ 1083.327431] sr 3:0:0:0: ioctl_internal_command return code = 8000002
[ 1083.327434]    : Sense Key : Aborted Command [current] [descriptor]
[ 1083.327437]    : Add. Sense: No additional sense information
[ 1098.112504] ata4.00: limiting speed to PIO4
[ 1098.112512] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1098.112520] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1098.112521]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1098.112522]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1098.112525] ata4.00: status: { DRDY }
[ 1098.112542] ata4: soft resetting link
[ 1098.595041] ata4.00: configured for PIO4
[ 1098.595050] ata4: EH complete


```

lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)


```

---

### Post by jonface on 2008-06-08
Gone back to 7.10, all problems gone :)

---

### Post by helpdeskdan on 2008-08-25
I get a failed to recover message as well:

[ 773.444685] usbcore: registered new interface driver hub
[ 773.472482] usbcore: registered new device driver usb
[ 773.500472] USB Universal Host Controller Interface driver v3.0
[ 773.689754] ata1.00: ATA-5: IBM-DJSA-210, JS2OAB0A, max UDMA/66
[ 773.689770] ata1.00: 19640880 sectors, multi 8: LBA
[ 773.732499] ata1.00: configured for UDMA/33
[ 773.817593] FDC 0 is a post-1991 82077
[ 774.000473] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[ 774.000488] ata2: failed to recover some devices, retrying in 5 secs

(Long, long pause occurs here)

[ 775.842993] Clocksource tsc unstable (delta = -1144855154 ns)
[ 775.846974] Time: acpi_pm clocksource has been installed.
[ 776.065298] ata2.00: ATAPI: SAMSUNG CD-ROM SN-124, q008, max UDMA/33, CDB intr

Similar to BattlePanic.  Strangly enough, hitting ctrl-alt f1 to take a look at it seems to unlock it.  Anyway, I added "acpi=off noapic" which seemed to fix it with little consequence. (The laptop battery is dead anyway, and I have hard coded the ssid so I wouldn't notice if either of these are affected.  

I thought I had found the bug here because it was so similar, but It appears I may be wrong: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244363](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244363)

Thanks to all for posting!

---


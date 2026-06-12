---
title: "Acer Aspire 5530G"
date: 2008-11-10
forum: Hardware
---

### Post by maron on 2008-11-10
I bought laptop Acer Aspire 5530G. And wifi and sound no work.
 I tried many instruction but no work. 
Sound:
HDA ATI SB Sound Card
ALC883 Analog ALSA Capture Device
wifi: don't find me

---

### Post by maron on 2008-11-10
lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Unknown device 9602
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
06:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)

```
demsg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fed0000 (usable)
[    0.000000]  BIOS-e820: 000000006fed0000 - 000000006fedc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fedc000 - 000000006fede000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fede000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 894MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f77c0
[    0.000000] Entering add_active_range(0, 0, 458448) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   458448
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   458448
[    0.000000] On node 0 totalpages: 458448
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1789 pages used for memmap
[    0.000000]   HighMem zone: 227283 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7700 checksum 0
[    0.000000] ACPI: RSDP 000F7700, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 6FED16C3, 005C (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: FACP 6FEDB79F, 00F4 (r3 AMD    ANT       6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 6FED171F, A080 (r1   Acer    SB700  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FEDDFC0, 0040
[    0.000000] ACPI: SLIC 6FEDB907, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
[    0.000000] ACPI: SSDT 6FEDBA7D, 0386 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 6FEDBE03, 005E (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 6FEDBE61, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 6FEDBE9D, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: ASF! 6FEDBED5, 012B (r32    DMA AMDTBL    6040000 PTL         1)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 1:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 1:3 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454867
[    0.000000] Kernel command line: root=UUID=1dbff48a-d2de-47ed-9093-cb8726bbef1b ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2000.114 MHz processor.
[   22.876688] Console: colour VGA+ 80x25
[   22.876691] console [tty0] enabled
[   22.876994] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.877360] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.943370] Memory: 1805596k/1833792k available (2177k kernel code, 27048k reserved, 1005k data, 368k init, 916288k highmem)
[   22.943378] virtual kernel memory layout:
[   22.943379]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.943380]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.943381]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.943382]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.943383]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   22.943385]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
[   22.943386]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
[   22.943389] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.943423] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   22.943855] hpet clockevent registered
[   23.023507] Calibrating delay using timer specific routine.. 3993.59 BogoMIPS (lpj=7987187)
[   23.023528] Security Framework initialized
[   23.023533] SELinux:  Disabled at boot.
[   23.023547] AppArmor: AppArmor initialized
[   23.023550] Failure registering capabilities with primary security module.
[   23.023559] Mount-cache hash table entries: 512
[   23.023668] Initializing cgroup subsys ns
[   23.023672] Initializing cgroup subsys cpuacct
[   23.023682] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000131f 00000000
[   23.023689] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.023692] CPU: L2 Cache: 512K (64 bytes/line)
[   23.023694] CPU 0(2) -> Core 0
[   23.023696] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020510 00002001 00000000 0000131f 00000000
[   23.023705] Compat vDSO mapped to ffffe000.
[   23.023715] Checking 'hlt' instruction... OK.
[   23.039839] SMP alternatives: switching to UP code
[   23.041520] Early unpacking initramfs... done
[   23.361198] ACPI: Core revision 20070126
[   23.361293] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.560046] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[   23.560067] SMP alternatives: switching to SMP code
[   23.560879] Booting processor 1/1 eip 3000
[   23.559189] Initializing CPU#1
[   23.637037] Calibrating delay using timer specific routine.. 3990.25 BogoMIPS (lpj=7980505)
[   23.637045] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000131f 00000000
[   23.637052] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.637054] CPU: L2 Cache: 512K (64 bytes/line)
[   23.637056] CPU 1(2) -> Core 1
[   23.637058] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020510 00002001 00000000 0000131f 00000000
[   23.648941] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[   23.648959] Total of 2 processors activated (7983.84 BogoMIPS).
[   23.649049] ENABLING IO-APIC IRQs
[   23.649252] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   23.796192] Brought up 2 CPUs
[   23.796218] CPU0 attaching sched-domain:
[   23.796220]  domain 0: span 03
[   23.796222]   groups: 01 02
[   23.796225] CPU1 attaching sched-domain:
[   23.796227]  domain 0: span 03
[   23.796229]   groups: 02 01
[   23.796426] net_namespace: 64 bytes
[   23.796434] Booting paravirtualized kernel on bare hardware
[   23.796878] Time: 19:28:01  Date: 11/10/08
[   23.796903] NET: Registered protocol family 16
[   23.797073] EISA bus registered
[   23.797077] ACPI: bus type pci registered
[   23.797555] PCI: PCI BIOS revision 3.00 entry at 0xfdab8, last bus=10
[   23.797557] PCI: Using configuration type 1
[   23.797566] Setting up standard PCI resources
[   23.799397] ACPI: EC: Look up EC in DSDT
[   23.803700] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   23.803703] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   23.824728] ACPI: Interpreter enabled
[   23.824731] ACPI: (supports S0 S3 S4 S5)
[   23.824743] ACPI: Using IOAPIC for interrupt routing
[   23.820148] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   23.892732] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   23.892735] ACPI: EC: driver started in interrupt mode
[   23.892900] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.895127] PCI: Transparent bridge - 0000:00:14.4
[   23.895165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.895473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[   23.895600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   23.895726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   23.895871] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   23.895966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   23.901686] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   23.901865] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   23.902075] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   23.902248] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   23.902458] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   23.902669] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   23.902856] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   23.903067] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   23.903271] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.903303] pnp: PnP ACPI init
[   23.903309] ACPI: bus type pnp registered
[   23.947901] pnp: PnP ACPI: found 12 devices
[   23.947903] ACPI: ACPI bus type pnp unregistered
[   23.947906] PnPBIOS: Disabled by ACPI PNP
[   23.948843] PCI: Using ACPI for IRQ routing
[   23.948845] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.948852] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   23.948854] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   23.948856] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
[   24.019470] NET: Registered protocol family 8
[   24.019472] NET: Registered protocol family 20
[   24.019610] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   24.019614] hpet0: 4 32-bit timers, 14318180 Hz
[   24.020659] AppArmor: AppArmor Filesystem Enabled
[   24.035075] Time: hpet clocksource has been installed.
[   24.035090] Switched to high resolution mode on CPU 0
[   24.023453] Switched to high resolution mode on CPU 1
[   24.032413] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.032416] system 00:01: iomem range 0xfec10000-0xfec10fff has been reserved
[   24.032419] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.032426] system 00:08: ioport range 0x220-0x22f has been reserved
[   24.032429] system 00:08: ioport range 0x40b-0x40b has been reserved
[   24.032432] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   24.032434] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   24.032437] system 00:08: ioport range 0x530-0x537 has been reserved
[   24.032440] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   24.032443] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   24.032445] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   24.032448] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   24.032451] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   24.032454] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[   24.032456] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[   24.032459] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   24.032462] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   24.032464] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   24.032467] system 00:08: ioport range 0x8000-0x805f has been reserved
[   24.032470] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   24.032472] system 00:08: ioport range 0x87f-0x87f has been reserved
[   24.032478] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   24.032481] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   24.032484] system 00:09: iomem range 0x0-0x0 could not be reserved
[   24.063728] PCI: Bridge: 0000:00:01.0
[   24.063730]   IO window: 9000-9fff
[   24.063734]   MEM window: afd00000-afefffff
[   24.063737]   PREFETCH window: d0000000-dfffffff
[   24.063743] PCI: Bridge: 0000:00:02.0
[   24.063745]   IO window: a000-afff
[   24.063748]   MEM window: afb00000-afbfffff
[   24.063751]   PREFETCH window: b0000000-bfffffff
[   24.063755] PCI: Bridge: 0000:00:04.0
[   24.063756]   IO window: disabled.
[   24.063759]   MEM window: disabled.
[   24.063762]   PREFETCH window: disabled.
[   24.063765] PCI: Bridge: 0000:00:07.0
[   24.063766]   IO window: disabled.
[   24.063770]   MEM window: f0200000-f02fffff
[   24.063772]   PREFETCH window: disabled.
[   24.063775] PCI: Bridge: 0000:00:09.0
[   24.063777]   IO window: disabled.
[   24.063780]   MEM window: f0300000-f03fffff
[   24.063783]   PREFETCH window: disabled.
[   24.063786] PCI: Bridge: 0000:00:14.4
[   24.063787]   IO window: disabled.
[   24.063826]   MEM window: disabled.
[   24.063830]   PREFETCH window: disabled.
[   24.063854] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
[   24.063858] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.063867] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   24.063872] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.063881] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 19 (level, low) -> IRQ 18
[   24.063885] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.063894] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   24.063898] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   24.063916] NET: Registered protocol family 2
[   24.100122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.100386] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.101086] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.101431] TCP: Hash tables configured (established 131072 bind 65536)
[   24.101433] TCP reno registered
[   24.112139] checking if image is initramfs... it is
[   24.736189] Freeing initrd memory: 7727k freed
[   24.738313] audit: initializing netlink socket (disabled)
[   24.738325] audit(1226345281.516:1): initialized
[   24.738702] highmem bounce pool size: 64 pages
[   24.744635] VFS: Disk quotas dquot_6.5.1
[   24.744897] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.745272] io scheduler noop registered
[   24.745274] io scheduler anticipatory registered
[   24.745276] io scheduler deadline registered
[   24.745289] io scheduler cfq registered (default)
[   24.745622] Boot video device is 0000:02:00.0
[   24.745773] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.745807] assign_interrupt_mode Found MSI capability
[   24.745843] Allocate Port Service[0000:00:02.0:pcie00]
[   24.746100] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.746130] assign_interrupt_mode Found MSI capability
[   24.746157] Allocate Port Service[0000:00:04.0:pcie00]
[   24.746198] Allocate Port Service[0000:00:04.0:pcie02]
[   24.746467] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.746496] assign_interrupt_mode Found MSI capability
[   24.746524] Allocate Port Service[0000:00:07.0:pcie00]
[   24.746593] Allocate Port Service[0000:00:07.0:pcie02]
[   24.746783] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   24.746812] assign_interrupt_mode Found MSI capability
[   24.746840] Allocate Port Service[0000:00:09.0:pcie00]
[   24.747708] isapnp: Scanning for PnP cards...
[   25.124145] isapnp: No Plug & Play device found
[   25.206637] Real Time Clock Driver v1.12ac
[   25.207152] hpet_resources: 0xfed00000 is busy
[   25.207207] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.210356] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.210562] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.210761] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   25.249589] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.249595] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.267059] mice: PS/2 mouse device common for all mice
[   25.267409] EISA: Probing bus 0 at eisa.0
[   25.267417] Cannot allocate resource for EISA slot 1
[   25.267443] Cannot allocate resource for EISA slot 8
[   25.267445] EISA: Detected 0 cards.
[   25.267448] cpuidle: using governor ladder
[   25.267450] cpuidle: using governor menu
[   25.267536] NET: Registered protocol family 1
[   25.267560] Using IPI No-Shortcut mode
[   25.267593] registered taskstats version 1
[   25.267725]   Magic number: 0:723:495
[   25.267880] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.267882] EDD information not available.
[   25.268120] Freeing unused kernel memory: 368k freed
[   25.268143] Write protecting the kernel read-only data: 801k
[   25.309678] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.484880] fuse init (API version 7.9)
[   26.518834] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.525583] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   26.544844] ACPI: Thermal Zone [THRM] (67 C)
[   26.568714] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   26.587574] ACPI: Thermal Zone [Z014] (0 C)
[   26.962137] tg3.c:v3.86 (November 9, 2007)
[   26.962161] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   26.962172] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   27.022025] SCSI subsystem initialized
[   27.057835] usbcore: registered new interface driver usbfs
[   27.057860] usbcore: registered new interface driver hub
[   27.057908] libata version 3.00 loaded.
[   27.059703] usbcore: registered new device driver usb
[   27.060745] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.528001] eth0: Tigon3 [partno(BCM95764M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:1e:ec:59:9b:2e
[   27.528009] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   27.528012] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   27.528132] ahci 0000:00:11.0: version 3.0
[   27.528195] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 20
[   27.528220] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   28.523014] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   28.523020] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part
[   28.523803] scsi0 : ahci
[   28.523881] scsi1 : ahci
[   28.523914] scsi2 : ahci
[   28.523948] scsi3 : ahci
[   28.523979] scsi4 : ahci
[   28.524010] scsi5 : ahci
[   28.524128] ata1: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd00 irq 20
[   28.524132] ata2: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffd80 irq 20
[   28.524136] ata3: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe00 irq 20
[   28.524140] ata4: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9ffe80 irq 20
[   28.524143] ata5: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9fff00 irq 20
[   28.524147] ata6: SATA max UDMA/133 abar m1024@0xfe9ffc00 port 0xfe9fff80 irq 20
[   28.996854] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.036487] ata1.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[   29.036492] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   29.038996] ata1.00: configured for UDMA/133
[   29.522481] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.680200] ata2.00: ATAPI: Slimtype DVD A  DS8A2S, 6A11, max UDMA/100
[   29.847482] ata2.00: configured for UDMA/100
[   30.171583] ata3: SATA link down (SStatus 0 SControl 300)
[   30.482194] ata4: SATA link down (SStatus 0 SControl 300)
[   30.792792] ata5: SATA link down (SStatus 0 SControl 300)
[   31.103408] ata6: SATA link down (SStatus 0 SControl 300)
[   31.103520] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[   31.094975] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A2S    6A11 PQ: 0 ANSI: 5
[   31.106836] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 17
[   31.106853] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   31.107171] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   31.107228] ohci_hcd 0000:00:12.0: irq 17, io mem 0xf0404000
[   31.119672] Driver 'sd' needs updating - please use bus_type methods
[   31.120560] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   31.120573] sd 0:0:0:0: [sda] Write Protect is off
[   31.120575] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.120591] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.120634] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   31.120642] sd 0:0:0:0: [sda] Write Protect is off
[   31.120644] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.120657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.120661]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   31.163264] usb usb1: configuration #1 chosen from 1 choice
[   31.163286] hub 1-0:1.0: USB hub found
[   31.163299] hub 1-0:1.0: 3 ports detected
[   31.165108]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[   31.208287] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.225345] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.225365] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   31.236933] sr0: scsi3-mmc drive: 24x/6x writer dvd-ram cd/rw xa/form2 cdda pop-up
[   31.236939] Uniform CD-ROM driver Revision: 3.20
[   31.237036] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   31.266778] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 17
[   31.266796] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   31.266820] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   31.266837] ohci_hcd 0000:00:12.1: irq 17, io mem 0xf0405000
[   31.326524] usb usb2: configuration #1 chosen from 1 choice
[   31.326549] hub 2-0:1.0: USB hub found
[   31.326592] hub 2-0:1.0: 3 ports detected
[   31.430108] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.430126] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.430150] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   31.430172] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf0406000
[   31.489776] usb usb3: configuration #1 chosen from 1 choice
[   31.489797] hub 3-0:1.0: USB hub found
[   31.489830] hub 3-0:1.0: 3 ports detected
[   31.593303] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
[   31.593314] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.593338] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   31.593351] ohci_hcd 0000:00:13.1: irq 16, io mem 0xf0407000
[   31.653059] usb usb4: configuration #1 chosen from 1 choice
[   31.653082] hub 4-0:1.0: USB hub found
[   31.653098] hub 4-0:1.0: 3 ports detected
[   31.740581] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   31.757565] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 19
[   31.757580] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   31.757610] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 5
[   31.757654] ehci_hcd 0000:00:12.2: debug port 1
[   31.757670] ehci_hcd 0000:00:12.2: irq 19, io mem 0xf0408000
[   31.768448] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.768564] usb usb5: configuration #1 chosen from 1 choice
[   31.768588] hub 5-0:1.0: USB hub found
[   31.768594] hub 5-0:1.0: 6 ports detected
[   31.872097] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 18
[   31.872116] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   31.872139] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[   31.872180] ehci_hcd 0000:00:13.2: debug port 1
[   31.872196] ehci_hcd 0000:00:13.2: irq 18, io mem 0xf0408400
[   31.883935] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.884019] usb usb6: configuration #1 chosen from 1 choice
[   31.884040] hub 6-0:1.0: USB hub found
[   31.884046] hub 6-0:1.0: 6 ports detected
[   32.034540] Attempting manual resume
[   32.034544] swsusp: Resume From Partition 8:8
[   32.034546] PM: Checking swsusp image.
[   32.034752] PM: Resume from disk failed.
[   32.099817] kjournald starting.  Commit interval 5 seconds
[   32.088141] EXT3-fs: mounted filesystem with ordered data mode.
[   32.381710] usb 5-6: new high speed USB device using ehci_hcd and address 2
[   32.790786] usb 5-6: configuration #1 chosen from 1 choice
[   33.334692] usb 3-2: new low speed USB device using ohci_hcd and address 2
[   33.552863] usb 3-2: configuration #1 chosen from 1 choice
[   39.573868] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.633970] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.901561] input: Power Button (FF) as /devices/virtual/input/input2
[   39.923908] ACPI: Power Button (FF) [PWRF]
[   39.923994] input: Power Button (CM) as /devices/virtual/input/input3
[   39.912595] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   39.955760] ACPI: Power Button (CM) [PWRB]
[   39.955846] input: Sleep Button (CM) as /devices/virtual/input/input4
[   39.987616] ACPI: Sleep Button (CM) [SLPB]
[   39.987704] input: Lid Switch as /devices/virtual/input/input5
[   39.987824] ACPI: Lid Switch [LID]
[   40.289691] ACPI: AC Adapter [ACAD] (on-line)
[   40.289780] ACPI: WMI-Acer: Mapper loaded
[   40.404673] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input6
[   40.422926] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[   40.587957] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2c/LNXVIDEO:01/input/input7
[   40.610088] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   40.640781] Linux agpgart interface v0.102
[   40.891702] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.955352] [fglrx] Maximum main memory to use for locked dma buffers: 1655 MBytes.
[   40.955373] [fglrx]   vendor: 1002 device: 9612 count: 1
[   40.955414] [fglrx]   vendor: 1002 device: 95c4 count: 2
[   40.955445] [fglrx] ioport: bar 1, base 0x9000, size: 0x100
[   40.955471] PCI: Enabling device 0000:01:05.0 (0006 -> 0007)
[   40.955479] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 16
[   40.955485] PCI: Setting latency timer of device 0000:01:05.0 to 64
[   40.955559] [fglrx] ioport: bar 4, base 0xa000, size: 0x100
[   40.955573] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   40.955579] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   40.955891] [fglrx] PAT is enabled successfully!
[   40.955931] [fglrx] module loaded - fglrx 8.54.3 [Oct  3 2008] with 2 minors
[   41.037605] ACPI: Battery Slot [BAT1] (battery present)
[   41.096234] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   41.123035] usbcore: registered new interface driver hiddev
[   41.127157] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb3/3-2/3-2:1.0/input/input8
[   41.151803] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:13.0-2
[   41.151823] usbcore: registered new interface driver usbhid
[   41.151827] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.166159] Linux video capture interface: v2.00
[   41.199279] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 19 (level, low) -> IRQ 18
[   41.199326] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   41.221134] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   41.247411] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0105)
[   41.518230] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   41.518237] acer_acpi: Detected Acer WMID interface
[   41.543162] acer_acpi: Unable to detect available devices
[   41.743701] usbcore: registered new interface driver uvcvideo
[   41.743707] USB Video Class driver (v0.1.0)
[   42.018639] input: PS/2 Mouse as /devices/virtual/input/input10
[   42.084588] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   42.890877] lp: driver loaded but no devices found
[   43.010166] Adding 2642652k swap on /dev/sda8.  Priority:-1 extents:1 across:2642652k
[   43.550647] EXT3 FS on sda7, internal journal
[   43.704304] device-mapper: uevent: version 1.0.3
[   43.704335] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   45.035948] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.444651] No dock devices found.
[   48.069440] apm: BIOS not found.
[   48.597148] ppdev: user-space parallel port driver
[   48.863159] audit(1226341706.115:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5337 profile="/usr/sbin/cupsd" namespace="default"
[   51.486766] [fglrx] GART Table is not in FRAME_BUFFER range
[   51.504603] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[   51.820238] [fglrx] Reserved FB block: Shared offset:0, size:1000000
[   51.820248] [fglrx] Reserved FB block: Unshared offset:ff72000, size:88000
[   51.820252] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000
[   52.615583] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : 2 (exp. 26).
[   53.830593] Bluetooth: Core ver 2.11
[   53.834217] NET: Registered protocol family 31
[   53.834224] Bluetooth: HCI device and connection manager initialized
[   53.834229] Bluetooth: HCI socket layer initialized
[   53.919411] Bluetooth: L2CAP ver 2.9
[   53.919416] Bluetooth: L2CAP socket layer initialized
[   53.979934] Bluetooth: RFCOMM socket layer initialized
[   53.979949] Bluetooth: RFCOMM TTY layer initialized
[   53.979951] Bluetooth: RFCOMM ver 1.8
[   55.389261] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   55.389267] tg3: eth0: Flow control is on for TX and on for RX.
[   57.626103] NET: Registered protocol family 17
[   58.881909] NET: Registered protocol family 10
[   58.882201] lo: Disabled Privacy Extensions
[   69.786333] eth0: no IPv6 routers present
[   72.776206] hda-intel: Invalid position buffer, using LPIB read method instead.

```

---

### Post by MachNine on 2008-11-14
I also got a Aspire 5530G and i got similar problems with this.

No sound in HH 8.04 but updated today to Intrepid 8.10 and the sound worked just fine for a moment until i installed ati drivers through envy and since then i couldn't get my sound working. HDA ATI SB soundcard with ALC888 realtek drivers.

No luck with realteks linuxdrivers and so on.

And when i try to compile ATI 8.11 drivers for linux my screens my X-server fails to load :(

The last thing i experienced is that when the sound worked i couldn't get any sound in my headphones, it's just like theres no signal at all throuigh the headphone output and when i plug them in the built-in speakers wont stop play. :( 

i need help as the fellow mate that started this thread needs.

Thanks all and i hope you can help us solve this. 

Best regards 
Michael

ps. can't post any printouts from the terminal since i'm on my stationary computer right now.

---

### Post by #nico# on 2009-01-18
Hallo maron && MachNine,

I've bought one too ... and had a lot of trouble with it.
Right now it seems, that I've solved most problems.

I'm using debian (lenny), so I guess this will aply to ubuntu as well.
My biggest problems: sound, wifi (wlan), webcam, sdcard-reader

### I've not solved the sdcard-reader problem right now.

**### The webcam**
# as root
rmmod uvcvideo
uvcvideo quirks=2
# now run cheese and enjoy

**### wifi (wlan), Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01), DEVICE-ID 14e4:4315**
- use module-assistant to build the latest ndiswrapper
- google for 10_WLAN_Broadcom_T77H030(4312).zip
- use "ndiswrapper -i bcmwl5.inf" (from the zip-file)
  "ndiswrapper -l" may give you:
bcmwl5 : driver installed
        device (14E4:4315) present
  if not try "ndiswrapper -a 14E4:4315 bcmwl5" and try again "ndiswrapper -l"
# I'm connected to a fritz!box, and am using WEP-Encryption, with only one key.
Here an excerpt from my /etc/network/interfaces:
iface wlan0 inet static
                address 192.168.0.101 # my adress
                gateway 192.168.0.1 # my router
                netmask 255.255.255.0
                broadcast 192.168.0.255
        wireless-rate 18M
        wireless-mode managed
        wireless-ap 00:1F:3F:18:2A:33 # MAC-adress of my router
        wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX # the wep-key
# make sure, you "chmod 600 /etc/network/interfaces"
- now try as root "ndiswrapper" and "ifup wlan0"
- if okay, add "ndiswrapper" to /etc/modules


**### Making the soundcard work: (this is an really ugly this)**
(1) I installed: (pkg / version)
libasound2      1.0.16-2
alsa-base       1.0.17.dfsg-4
alsa-oss        1.0.15-1
alsa-tools      1.0.16-2
alsa-tools-gui  1.0.16-2
alsa-utils      1.0.16-2
gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2
gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2
libasound2      1.0.16-2
linux-sound-base        1.0.17.dfsg-4

(2) Then I downloaded the latest alsa sources:
(a) alsa-driver-1.0.18a
(b) alsa-lib-1.0.18
(c) alsa-utils-1.0.18
  alsa-driver:
  - unpack
  - ./configure --with-cards=hda-intel
  - make all install **# this will overwrite files installed by (1)**
  alsa-lib, alsa-utils:
  - unpack
  - ./configure
  - make all install **# this will overwrite files installed by (1)**

(3) Run:
  alsaconf # as root, "hda-intel  ATI Technologies Inc SBx00 Azalia (Intel HDA)" worked for me
  gnome-alsamixer # uncheck "headphone"

I hope this helps.

---


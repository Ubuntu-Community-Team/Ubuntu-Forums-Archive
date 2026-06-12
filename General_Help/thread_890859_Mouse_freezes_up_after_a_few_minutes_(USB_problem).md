---
title: "Mouse freezes up after a few minutes (USB problem?)"
date: 2008-08-15
forum: General Help
---

### Post by david_G17 on 2008-08-15
Hi,

After I upgraded my Ubuntu box, I noticed that within 15 minutes of every time I boot the computer, the mouse freezes up.  I don't experience it in Windows, so I think it's software rather than hardware related.
Below are the outputs of "uname -a", "dmesg", and "lsmod"


Is there some way to restart whatever service controls the mouse?  I can still use my keyboard, but CTRL+ALT+BACKSPACE won't successfully restart X.  It freezes with just the background screen, but I can SSH into the box from another machine.

Any ideas?  Anything else that I could post which may lead to some insight into the problem?

I appreciate any help or ideas anyone has on this!



$uname -a
Linux ilsa 2.6.24-19-386 #1 Fri Jul 11 22:45:14 UTC 2008 i686 GNU/Linux






$dmesg
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-386 (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Fri Jul 11 22:45:14 UTC 2008 (Ubuntu 2.6.24-19.36-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5c60
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7720 checksum 0
[    0.000000] ACPI: RSDP 000F7720, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEF3040, 0038 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEF3180, 6FCF (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEF0000, 0040
[    0.000000] ACPI: MCFG 3FEFA2C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEFA1C0, 008E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 3FEFA340, 015C (r1 NVIDIA  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 3FEFA7D0, 0275 (r1 NVIDIA    CpuPm     3000 INTL 20040311)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259827
[    0.000000] Kernel command line: root=UUID=61d08a4e-b524-460c-b628-5692fccd7eda ro quiet splash acpi=force irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2400.179 MHz processor.
[   23.258974] spurious 8259A interrupt: IRQ7.
[   23.260230] Console: colour VGA+ 80x25
[   23.260232] console [tty0] enabled
[   23.260801] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.261201] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.280704] Memory: 1026088k/1047488k available (2079k kernel code, 20708k reserved, 973k data, 364k init, 129984k highmem)
[   23.280709] virtual kernel memory layout:
[   23.280710]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   23.280710]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.280711]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.280712]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.280713]       .init : 0xc03fe000 - 0xc0459000   ( 364 kB)
[   23.280713]       .data : 0xc0307d94 - 0xc03fb3a4   ( 973 kB)
[   23.280714]       .text : 0xc0100000 - 0xc0307d94   (2079 kB)
[   23.280716] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.280745] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.360654] Calibrating delay using timer specific routine.. 4806.39 BogoMIPS (lpj=9612796)
[   23.360671] Security Framework initialized
[   23.360677] SELinux:  Disabled at boot.
[   23.360685] AppArmor: AppArmor initialized
[   23.360688] Failure registering capabilities with primary security module.
[   23.360692] Mount-cache hash table entries: 512
[   23.360763] Initializing cgroup subsys ns
[   23.360767] Initializing cgroup subsys cpuacct
[   23.360774] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   23.360778] monitor/mwait feature present.
[   23.360779] using mwait in idle threads.
[   23.360781] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.360783] CPU: L2 cache: 4096K
[   23.360784] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   23.360789] Compat vDSO mapped to ffffe000.
[   23.360797] CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   23.360801] Checking 'hlt' instruction... OK.
[   23.377743] Freeing SMP alternatives: 0k freed
[   23.377814] Early unpacking initramfs... done
[   23.615872] ACPI: Core revision 20070126
[   23.615913] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.620823] ENABLING IO-APIC IRQs
[   23.621019] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   23.660706] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   23.660754] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   23.660756] ...trying to set up timer as Virtual Wire IRQ... failed.
[   23.700432] ...trying to set up timer as ExtINT IRQ... works.
[   23.943905] net_namespace: 64 bytes
[   23.943913] Booting paravirtualized kernel on bare hardware
[   23.944239] Time: 12:46:18  Date: 08/15/08
[   23.944254] NET: Registered protocol family 16
[   23.944365] EISA bus registered
[   23.944396] ACPI: bus type pci registered
[   23.950671] PCI: PCI BIOS revision 3.00 entry at 0xf2060, last bus=6
[   23.950672] PCI: Using configuration type 1
[   23.950685] Setting up standard PCI resources
[   23.953476] ACPI: EC: Look up EC in DSDT
[   23.959157] ACPI: Interpreter enabled
[   23.959159] ACPI: (supports S0 S1 S3 S4 S5)
[   23.959168] ACPI: Using IOAPIC for interrupt routing
[   23.966532] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.967939] PCI: Transparent bridge - 0000:00:10.0
[   23.967961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.968217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.051628] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   24.051781] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   24.051928] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   24.052078] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[   24.052224] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 *7 9 10 11 14 15)
[   24.052428] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.052574] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.052720] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.052867] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   24.053013] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053159] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053305] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053450] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053596] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053742] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.053889] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   24.054035] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[   24.054181] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.054328] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   24.054476] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   24.054648] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   24.054815] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   24.054981] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   24.055147] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   24.055312] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   24.055478] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   24.055644] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   24.055813] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   24.055979] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   24.056145] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   24.056369] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   24.056536] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   24.056704] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   24.056871] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   24.057037] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   24.057204] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   24.057370] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   24.057536] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   24.057702] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   24.057869] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   24.058035] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   24.058124] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.058142] pnp: PnP ACPI init
[   24.058146] ACPI: bus type pnp registered
[   24.061643] pnp: PnP ACPI: found 11 devices
[   24.061645] ACPI: ACPI bus type pnp unregistered
[   24.061648] PnPBIOS: Disabled by ACPI PNP
[   24.061766] PCI: Using ACPI for IRQ routing
[   24.061768] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.347337] NET: Registered protocol family 8
[   24.347339] NET: Registered protocol family 20
[   24.347386] AppArmor: AppArmor Filesystem Enabled
[   24.351367] Time: tsc clocksource has been installed.
[   24.359428] system 00:01: ioport range 0x4000-0x407f has been reserved
[   24.359430] system 00:01: ioport range 0x4080-0x40ff has been reserved
[   24.359433] system 00:01: ioport range 0x4400-0x447f has been reserved
[   24.359435] system 00:01: ioport range 0x4480-0x44ff has been reserved
[   24.359438] system 00:01: ioport range 0x4800-0x487f has been reserved
[   24.359440] system 00:01: ioport range 0x4880-0x48ff has been reserved
[   24.359445] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   24.359448] system 00:02: ioport range 0x800-0x87f has been reserved
[   24.359450] system 00:02: ioport range 0x290-0x297 has been reserved
[   24.359453] system 00:02: ioport range 0x880-0x88f has been reserved
[   24.359460] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.359466] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[   24.359469] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[   24.359471] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[   24.359474] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[   24.359476] system 00:0a: iomem range 0x3fef0000-0x3fefffff could not be reserved
[   24.359479] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[   24.359482] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   24.359485] system 00:0a: iomem range 0x100000-0x3feeffff could not be reserved
[   24.359487] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.359490] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.389756] PCI: Bridge: 0000:00:02.0
[   24.389757]   IO window: a000-afff
[   24.389760]   MEM window: d0000000-d2ffffff
[   24.389762]   PREFETCH window: c0000000-cfffffff
[   24.389764] PCI: Bridge: 0000:00:04.0
[   24.389765]   IO window: disabled.
[   24.389767]   MEM window: disabled.
[   24.389768]   PREFETCH window: disabled.
[   24.389771] PCI: Bridge: 0000:00:05.0
[   24.389771]   IO window: disabled.
[   24.389773]   MEM window: disabled.
[   24.389775]   PREFETCH window: disabled.
[   24.389777] PCI: Bridge: 0000:00:06.0
[   24.389778]   IO window: disabled.
[   24.389780]   MEM window: disabled.
[   24.389781]   PREFETCH window: disabled.
[   24.389783] PCI: Bridge: 0000:00:07.0
[   24.389784]   IO window: disabled.
[   24.389786]   MEM window: disabled.
[   24.389788]   PREFETCH window: disabled.
[   24.389791] PCI: Bridge: 0000:00:10.0
[   24.389792]   IO window: b000-bfff
[   24.389795]   MEM window: d3000000-d4ffffff
[   24.389797]   PREFETCH window: disabled.
[   24.389807] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.389813] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.389819] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   24.389825] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.389830] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.389838] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   24.389845] NET: Registered protocol family 2
[   24.427543] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.427798] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.428321] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   24.428444] TCP: Hash tables configured (established 131072 bind 65536)
[   24.428445] TCP reno registered
[   24.439641] checking if image is initramfs... it is
[   24.890904] Switched to high resolution mode on CPU 0
[   24.915601] Freeing initrd memory: 7871k freed
[   24.916136] audit: initializing netlink socket (disabled)
[   24.916158] audit(1218804378.236:1): initialized
[   24.916290] highmem bounce pool size: 64 pages
[   24.917433] VFS: Disk quotas dquot_6.5.1
[   24.917447] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.917558] io scheduler noop registered
[   24.917559] io scheduler anticipatory registered
[   24.917561] io scheduler deadline registered
[   24.917567] io scheduler cfq registered (default)
[   24.917675] pci 0000:00:09.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0f.0: Quirk disabling HT MSI mapping<6>pci 0000:00:10.0: Quirk disabling HT MSI mapping<7>Boot video device is 0000:01:00.0
[   24.930645] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.930670] assign_interrupt_mode Found MSI capability
[   24.930704] Allocate Port Service[0000:00:02.0:pcie00]
[   24.930749] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.930768] assign_interrupt_mode Found MSI capability
[   24.930783] Allocate Port Service[0000:00:04.0:pcie00]
[   24.930828] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   24.930847] assign_interrupt_mode Found MSI capability
[   24.930861] Allocate Port Service[0000:00:05.0:pcie00]
[   24.930906] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.930925] assign_interrupt_mode Found MSI capability
[   24.930939] Allocate Port Service[0000:00:06.0:pcie00]
[   24.930983] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.931002] assign_interrupt_mode Found MSI capability
[   24.931016] Allocate Port Service[0000:00:07.0:pcie00]
[   24.931156] isapnp: Scanning for PnP cards...
[   25.284009] isapnp: No Plug & Play device found
[   25.299529] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.300215] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.300258] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.300310] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   25.300312] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   25.300857] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.309967] mice: PS/2 mouse device common for all mice
[   25.310060] EISA: Probing bus 0 at eisa.0
[   25.310073] Cannot allocate resource for EISA slot 4
[   25.310075] Cannot allocate resource for EISA slot 5
[   25.310085] EISA: Detected 0 cards.
[   25.310088] cpuidle: using governor ladder
[   25.310197] NET: Registered protocol family 1
[   25.310217] Using IPI Shortcut mode
[   25.310246] registered taskstats version 1
[   25.310348]   Magic number: 4:646:784
[   25.310390]   hash matches device ptyq6
[   25.310414] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.310416] EDD information not available.
[   25.310855] Freeing unused kernel memory: 364k freed
[   25.337816] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.442567] loop: module loaded
[   26.448966] fuse init (API version 7.9)
[   26.459884] ACPI: Fan [FAN] (on)
[   26.465003] ACPI: Thermal Zone [THRM] (40 C)
[   26.477629] device-mapper: uevent: version 1.0.3
[   26.477652] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   27.246892] usbcore: registered new interface driver usbfs
[   27.246913] usbcore: registered new interface driver hub
[   27.258817] usbcore: registered new device driver usb
[   27.267513] SCSI subsystem initialized
[   27.287511] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   27.287853] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   27.287861] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   27.287871] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.287874] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   27.288183] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   27.288195] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xd5003000
[   27.302781] libata version 3.00 loaded.
[   27.344779] usb usb1: configuration #1 chosen from 1 choice
[   27.344795] hub 1-0:1.0: USB hub found
[   27.344801] hub 1-0:1.0: 8 ports detected
[   27.408949] Floppy drive(s): fd0 is 1.44M
[   27.426399] FDC 0 is a post-1991 82077
[   27.446915] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   27.446921] ACPI: PCI Interrupt 0000:06:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   27.446930] ohci_hcd 0000:06:07.0: OHCI Host Controller
[   27.446946] ohci_hcd 0000:06:07.0: new USB bus registered, assigned bus number 2
[   27.446956] ohci_hcd 0000:06:07.0: irq 17, io mem 0xd4005000
[   27.447236] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   27.447238] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 18
[   27.447243] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   27.447245] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   27.447258] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 3
[   27.447277] ehci_hcd 0000:00:0b.1: debug port 1
[   27.447281] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   27.447286] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xd5000000
[   27.458537] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.458611] usb usb3: configuration #1 chosen from 1 choice
[   27.458625] hub 3-0:1.0: USB hub found
[   27.458628] hub 3-0:1.0: 8 ports detected
[   27.562461] usb usb2: configuration #1 chosen from 1 choice
[   27.562477] hub 2-0:1.0: USB hub found
[   27.562481] hub 2-0:1.0: 3 ports detected
[   27.666548] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   27.666555] ACPI: PCI Interrupt 0000:06:07.1[B] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 19
[   27.666565] ohci_hcd 0000:06:07.1: OHCI Host Controller
[   27.666582] ohci_hcd 0000:06:07.1: new USB bus registered, assigned bus number 4
[   27.666592] ohci_hcd 0000:06:07.1: irq 19, io mem 0xd4006000
[   27.752156] usb usb4: configuration #1 chosen from 1 choice
[   27.752172] hub 4-0:1.0: USB hub found
[   27.752176] hub 4-0:1.0: 2 ports detected
[   27.854440] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   27.854444] ACPI: PCI Interrupt 0000:06:07.2[C] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   27.854451] ehci_hcd 0000:06:07.2: EHCI Host Controller
[   27.854466] ehci_hcd 0000:06:07.2: new USB bus registered, assigned bus number 5
[   27.854496] ehci_hcd 0000:06:07.2: irq 20, io mem 0xd4004000
[   27.865897] ehci_hcd 0000:06:07.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.865957] usb usb5: configuration #1 chosen from 1 choice
[   27.865972] hub 5-0:1.0: USB hub found
[   27.865975] hub 5-0:1.0: 5 ports detected
[   27.971871] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.972141] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   27.972144] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   27.972158] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.972164] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   27.972410] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   27.972412] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 22
[   27.972425] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   27.972430] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   27.974514] ACPI: PCI Interrupt 0000:06:0c.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 19
[   27.974541] skge 1.13 addr 0xd4000000 irq 19 chip Yukon-Lite rev 9
[   27.974726] skge eth0: addr 00:17:31:8a:cb:2f
[   27.975074] pata_amd 0000:00:0d.0: version 0.3.10
[   27.975092] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.980662] scsi0 : pata_amd
[   27.980990] scsi1 : pata_amd
[   27.981429] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   27.981431] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   28.389109] usb 3-2: new high speed USB device using ehci_hcd and address 3
[   28.524632] usb 3-2: configuration #1 chosen from 1 choice
[   28.641052] ata2.00: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[   28.641072] ata2.01: ATAPI: HL-DT-ST RW/DVD GCC-4522B, 1.08, max UDMA/33
[   28.708674] usbcore: registered new interface driver libusual
[   28.711574] Initializing USB Mass Storage driver...
[   28.812731] ata2.00: configured for UDMA/33
[   29.000416] ata2.01: configured for UDMA/33
[   29.001941] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.05 PQ: 0 ANSI: 5
[   29.002660] scsi 1:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4522B 1.08 PQ: 0 ANSI: 5
[   29.002764] sata_nv 0000:00:0e.0: version 3.5
[   29.002774] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   29.002800] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   29.003190] scsi2 : sata_nv
[   29.003421] scsi3 : sata_nv
[   29.003542] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 21
[   29.003544] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 21
[   29.007269] Driver 'sr' needs updating - please use bus_type methods
[   29.011627] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   29.011629] Uniform CD-ROM driver Revision: 3.20
[   29.011664] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.012193] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   29.014525] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   29.014563] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   29.017610] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   29.017621] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   29.245940] usb 1-1: configuration #1 chosen from 1 choice
[   29.467456] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.512707] ata3.00: ATA-7: ST3320620AS, 3.AAC, max UDMA/133
[   29.512710] ata3.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   29.551308] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   29.579250] ata3.00: configured for UDMA/133
[   29.775131] usb 1-6: configuration #1 chosen from 1 choice
[   29.787554] scsi4 : SCSI emulation for USB Mass Storage devices
[   29.787600] usbcore: registered new interface driver usb-storage
[   29.787602] USB Mass Storage support registered.
[   29.787605] usb-storage: device found at 3
[   29.787606] usb-storage: waiting for device to settle before scanning
[   29.787682] usbcore: registered new interface driver hiddev
[   29.796223] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
[   29.810937] input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:0b.0-6
[   29.810948] usbcore: registered new interface driver usbhid
[   29.810951] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.890787] ata4: SATA link down (SStatus 0 SControl 300)
[   29.901333] scsi 2:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   29.901377] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[   29.901397] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 22
[   29.901426] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   29.901620] scsi5 : sata_nv
[   29.901703] scsi6 : sata_nv
[   29.901828] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe800 irq 22
[   29.901830] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe808 irq 22
[   30.366064] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.374300] ata5.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[   30.374302] ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   30.390281] ata5.00: configured for UDMA/133
[   30.701532] ata6: SATA link down (SStatus 0 SControl 300)
[   30.712126] scsi 5:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   30.712168] scsi 5:0:0:0: Attached scsi generic sg3 type 0
[   30.716440] Driver 'sd' needs updating - please use bus_type methods
[   30.716474] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   30.716480] sd 2:0:0:0: [sda] Write Protect is off
[   30.716482] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.716491] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.716524] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   30.716529] sd 2:0:0:0: [sda] Write Protect is off
[   30.716531] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.716540] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.716542]  sda: sda1 sda2 sda3 < sda5 >
[   30.752211] sd 2:0:0:0: [sda] Attached SCSI disk
[   30.752247] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   30.752256] sd 5:0:0:0: [sdb] Write Protect is off
[   30.752258] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.752272] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.752304] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   30.752313] sd 5:0:0:0: [sdb] Write Protect is off
[   30.752315] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.752328] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.752331]  sdb: sdb1
[   30.774586] sd 5:0:0:0: [sdb] Attached SCSI disk
[   31.025281] EXT3-fs: INFO: recovery required on readonly filesystem.
[   31.025284] EXT3-fs: write access will be enabled during recovery.
[   34.779417] usb-storage: device scan complete
[   34.780783] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   34.782536] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   34.784533] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   34.786530] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   35.207878] sd 4:0:0:0: [sdc] 1008640 512-byte hardware sectors (516 MB)
[   35.210997] sd 4:0:0:0: [sdc] Write Protect is off
[   35.211000] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   35.211002] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   35.220856] sd 4:0:0:0: [sdc] 1008640 512-byte hardware sectors (516 MB)
[   35.223980] sd 4:0:0:0: [sdc] Write Protect is off
[   35.223982] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   35.223983] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   35.224029]  sdc: sdc1
[   35.226524] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   35.226557] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   35.230870] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   35.230893] sd 4:0:0:1: Attached scsi generic sg5 type 0
[   35.234861] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   35.234882] sd 4:0:0:2: Attached scsi generic sg6 type 0
[   35.238856] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   35.238877] sd 4:0:0:3: Attached scsi generic sg7 type 0
[   36.408811] kjournald starting.  Commit interval 5 seconds
[   36.408821] EXT3-fs: recovery complete.
[   36.425207] EXT3-fs: mounted filesystem with ordered data mode.
[   45.180066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.181645] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.251322] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   45.251342] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   45.660823] input: Power Button (FF) as /devices/virtual/input/input3
[   45.670353] ACPI: Power Button (FF) [PWRF]
[   45.670403] input: Power Button (CM) as /devices/virtual/input/input4
[   45.682337] ACPI: Power Button (CM) [PWRB]
[   45.713143] Linux agpgart interface v0.102
[   46.117863] nvidia: module license 'NVIDIA' taints kernel.
[   47.267126] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   47.267133] ACPI: PCI Interrupt 0000:06:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 23
[   47.270466] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-386/sound/alsa-driver/pci/emu10k1/emu10k1_main.c:226: Audigy2 value: Special config.
[   48.310314] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0704
[   48.310324] usbcore: registered new interface driver usblp
[   48.398480] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   48.398483] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 23
[   48.398490] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.398636] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   49.011661] skge eth0: enabling interface
[   49.015998] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   49.232410] Real Time Clock Driver v1.12ac
[   50.401484] NET: Registered protocol family 17
[   51.274927] skge eth0: Link is up at 10 Mbps, half duplex, flow control none
[   51.809703] lp: driver loaded but no devices found
[   52.010724] skge eth0: disabling interface
[   52.012965] skge eth0: enabling interface
[   52.047666] Adding 3036244k swap on /dev/sda5.  Priority:-1 extents:1 across:3036244k
[   52.351160] EXT3 FS on sda2, internal journal
[   52.484488] kjournald starting.  Commit interval 5 seconds
[   52.484494] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.491959] EXT3 FS on sdb1, internal journal
[   52.491962] EXT3-fs: recovery complete.
[   52.491964] EXT3-fs: mounted filesystem with ordered data mode.
[   52.734775] NET: Registered protocol family 10
[   52.734906] lo: Disabled Privacy Extensions
[   52.735090] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.886082] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.406479] No dock devices found.
[   54.276144] skge eth0: Link is up at 10 Mbps, half duplex, flow control none
[   54.276480] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   55.098106] ppdev: user-space parallel port driver
[   55.484392] audit(1218818809.761:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5876 profile="/usr/sbin/cupsd" namespace="default"
[   55.587613] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   55.587616] apm: overridden by ACPI.
[   64.593093] eth0: no IPv6 routers present






$lsmod
Module                  Size  Used by
nls_iso8859_1           4096  1 
nls_cp437               5760  1 
vfat                   13184  1 
fat                    52892  1 vfat
ppdev                   9348  0 
acpi_cpufreq            7820  0 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  1 
freq_table              4484  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7200  0 
video                  18832  0 
output                  3712  1 video
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
container               4736  0 
battery                13316  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
ipv6                  255172  12 
ac                      6020  0 
psmouse                39056  0 
parport_pc             35108  0 
lp                     11332  0 
parport                35912  3 ppdev,parport_pc,lp
af_packet              21636  2 
rtc                    13212  0 
pcspkr                  3072  0 
evdev                  11776  3 
usblp                  14592  0 
snd_emu10k1_synth       7168  0 
snd_emux_synth         35584  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6656  1 snd_emux_synth
snd_emu10k1           146624  1 snd_emu10k1_synth
snd_ac97_codec         99876  1 snd_emu10k1
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                75400  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  2 snd_emu10k1,snd_pcm
snd_util_mem            4736  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9476  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           3972  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
snd_rawmidi            24608  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51152  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8588  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7822720  18 
snd                    54692  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
agpgart                33328  1 nvidia
button                  8336  0 
i2c_nforce2             6656  0 
i2c_core               23696  2 nvidia,i2c_nforce2
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
ext3                  132872  2 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sd_mod                 29584  7 
usbhid                 30720  0 
hid                    36480  1 usbhid
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
usb_storage            72512  1 
libusual               18208  1 usb_storage
sata_nv                26504  3 
pata_amd               13316  0 
pata_acpi               7424  0 
floppy                 58116  0 
skge                   41616  0 
ata_generic             7428  0 
ehci_hcd               36748  0 
ohci_hcd               24196  0 
libata                159728  4 sata_nv,pata_amd,pata_acpi,ata_generic
scsi_mod              151180  5 sd_mod,sg,sr_mod,usb_storage,libata
usbcore               143724  7 usblp,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
dm_mirror              22912  0 
dm_snapshot            18592  0 
dm_mod                 60484  2 dm_mirror,dm_snapshot
thermal                15772  0 
processor              28080  2 acpi_cpufreq,thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  1 
loop                   17796  0

---


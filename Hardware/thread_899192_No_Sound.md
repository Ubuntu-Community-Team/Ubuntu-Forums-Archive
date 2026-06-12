---
title: "No Sound"
date: 2008-08-24
forum: Hardware
---

### Post by pacchiee on 2008-08-24
I basically installed Ubuntu 8.04 and later on upgraded it with Xubuntu-Desktop from Synaptic PM. Now, when I login using Xfce there is no sound at all. But everything sounds great if I log back in using Xclient. Rest works fine except sound.

I use G400 204832Q Lenovo Laptop. Me basically switching from Windows to Linux, have no clue whatsoever about this issue. Please help.

Thank You!

---

### Post by libra1780 on 2008-08-24
Hi! give us more details

open console and type
```

dmesg > dmesg.txt
lspci > lspci.txt
lsmod > lsmod.txt

```
be shure the prompt ends wirh ~$, otherwise type also 
```
cd ~$
```
before.
now there are 3 txt files in your personal folder. post them

---

### Post by pacchiee on 2008-08-24
>> dmesg.txt <<

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6470
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F63F0 checksum 0
[    0.000000] ACPI: RSDP 000F63F0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 1F6E588C, 0094 (r1 LENOVO CB-01     6040000  LTP        0)
[    0.000000] ACPI: FACP 1F6ECBC4, 00F4 (r3 LENOVO CB-01     6040000 ALAN        1)
[    0.000000] ACPI: DSDT 1F6E7627, 5529 (r1 LENOVO CB-01     6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6EDFC0, 0040
[    0.000000] ACPI: APIC 1F6ECCB8, 0068 (r1 LENOVO CB-01     6040000 LOHR       5A)
[    0.000000] ACPI: HPET 1F6ECD20, 0038 (r1 LENOVO CB-01     6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 1F6ECD58, 003C (r1 LENOVO CB-01     6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 1F6ECD94, 0032 (r1 LENOVO CB-01     6040000  TL         0)
[    0.000000] ACPI: SLIX 1F6ECDC6, 0176 (r1 LENOVO CB-01     6040000 TBD         1)
[    0.000000] ACPI: DBGP 1F6ECF3C, 0034 (r1 LENOVO CB-01     6040000 LOHR        0)
[    0.000000] ACPI: APIC 1F6ECF70, 0068 (r1 LENOVO CB-01     6040000  LTP        0)
[    0.000000] ACPI: BOOT 1F6ECFD8, 0028 (r1 LENOVO CB-01     6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F6E6FD8, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F6E6946, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F6E5EAC, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F6E5E06, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 1F6E5920, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=cf52e61a-989f-4c63-bb07-24b15d5efd80 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1729.233 MHz processor.
[   12.139943] Console: colour VGA+ 80x25
[   12.139950] console [tty0] enabled
[   12.140142] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.140480] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.157510] Memory: 498436k/514944k available (2177k kernel code, 15900k reserved, 1006k data, 368k init, 0k highmem)
[   12.157526] virtual kernel memory layout:
[   12.157528]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   12.157531]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.157534]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   12.157537]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[   12.157539]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   12.157542]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   12.157545]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   12.157552] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.157613] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   12.157766] hpet clockevent registered
[   12.237749] Calibrating delay using timer specific routine.. 3463.48 BogoMIPS (lpj=6926978)
[   12.237784] Security Framework initialized
[   12.237794] SELinux:  Disabled at boot.
[   12.237818] AppArmor: AppArmor initialized
[   12.237826] Failure registering capabilities with primary security module.
[   12.237842] Mount-cache hash table entries: 512
[   12.238044] Initializing cgroup subsys ns
[   12.238051] Initializing cgroup subsys cpuacct
[   12.238070] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   12.238086] monitor/mwait feature present.
[   12.238090] using mwait in idle threads.
[   12.238098] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.238104] CPU: L2 cache: 1024K
[   12.238109] CPU: Physical Processor ID: 0
[   12.238112] CPU: Processor Core ID: 0
[   12.238117] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   12.238136] Compat vDSO mapped to ffffe000.
[   12.238158] Checking 'hlt' instruction... OK.
[   12.254487] SMP alternatives: switching to UP code
[   12.258044] Early unpacking initramfs... done
[   13.012859] ACPI: Core revision 20070126
[   13.012972] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.038210] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   13.038244] SMP alternatives: switching to SMP code
[   13.039524] Booting processor 1/1 eip 3000
[   13.050273] Initializing CPU#1
[   13.129450] Calibrating delay using timer specific routine.. 3458.56 BogoMIPS (lpj=6917120)
[   13.129463] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   13.129475] monitor/mwait feature present.
[   13.129481] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.129485] CPU: L2 cache: 1024K
[   13.129489] CPU: Physical Processor ID: 0
[   13.129492] CPU: Processor Core ID: 1
[   13.129496] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   13.130197] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   13.130240] Total of 2 processors activated (6922.04 BogoMIPS).
[   13.130450] ENABLING IO-APIC IRQs
[   13.130677] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.277607] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   13.297641] Brought up 2 CPUs
[   13.297684] CPU0 attaching sched-domain:
[   13.297690]  domain 0: span 03
[   13.297694]   groups: 01 02
[   13.297701] CPU1 attaching sched-domain:
[   13.297705]  domain 0: span 03
[   13.297709]   groups: 02 01
[   13.298173] net_namespace: 64 bytes
[   13.298187] Booting paravirtualized kernel on bare hardware
[   13.299121] Time:  7:53:48  Date: 08/24/08
[   13.299175] NET: Registered protocol family 16
[   13.299585] EISA bus registered
[   13.299596] ACPI: bus type pci registered
[   13.299934] PCI: PCI BIOS revision 2.10 entry at 0xfd893, last bus=5
[   13.299939] PCI: Using configuration type 1
[   13.299956] Setting up standard PCI resources
[   13.338494] ACPI: EC: Look up EC in DSDT
[   13.342564] ACPI: BIOS _OSI(Linux) query ignored
[   13.342570] ACPI: DMI System Vendor: LENOVO
[   13.342574] ACPI: DMI Product Name: Lenovo 3000 G400                
[   13.342579] ACPI: DMI Product Version: C-Notebook XXXX                 
[   13.342584] ACPI: DMI Board Name: C460                            
[   13.342588] ACPI: DMI BIOS Vendor: LENOVO
[   13.342592] ACPI: DMI BIOS Date: 09/11/07
[   13.342595] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[   13.342600] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   13.343588] ACPI: Interpreter enabled
[   13.343595] ACPI: (supports S0 S3 S4 S5)
[   13.343627] ACPI: Using IOAPIC for interrupt routing
[   13.344549] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.442683] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   13.442690] ACPI: EC: driver started in interrupt mode
[   13.442785] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.443908] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   13.443916] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   13.445337] PCI: Transparent bridge - 0000:00:1e.0
[   13.445411] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.446076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   13.446347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   13.446618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   13.446911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   13.459941] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   13.460151] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.460357] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.460562] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.460772] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   13.460977] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   13.461180] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.461390] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   13.461710] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.461775] pnp: PnP ACPI init
[   13.461791] ACPI: bus type pnp registered
[   13.481704] pnp: PnP ACPI: found 11 devices
[   13.481709] ACPI: ACPI bus type pnp unregistered
[   13.481716] PnPBIOS: Disabled by ACPI PNP
[   13.482196] PCI: Using ACPI for IRQ routing
[   13.482203] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.529559] NET: Registered protocol family 8
[   13.529564] NET: Registered protocol family 20
[   13.529632] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.529641] hpet0: 3 64-bit timers, 14318180 Hz
[   13.530712] AppArmor: AppArmor Filesystem Enabled
[   13.533330] Time: tsc clocksource has been installed.
[   13.533355] Switched to high resolution mode on CPU 0
[   13.533552] Switched to high resolution mode on CPU 1
[   13.546341] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   13.546349] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   13.546356] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   13.546363] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   13.546370] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   13.546377] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   13.546384] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   13.546391] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   13.546410] system 00:06: ioport range 0x680-0x69f has been reserved
[   13.546416] system 00:06: ioport range 0x800-0x80f has been reserved
[   13.546423] system 00:06: ioport range 0x1000-0x107f has been reserved
[   13.546429] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   13.546435] system 00:06: ioport range 0x1640-0x164f has been reserved
[   13.546442] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[   13.546448] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   13.546461] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   13.546467] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   13.640353] PM-Timer running at invalid rate: 310% of normal - aborting.
[   13.640387] PCI: Bridge: 0000:00:1c.0
[   13.640393]   IO window: 2000-2fff
[   13.640403]   MEM window: d2000000-d3ffffff
[   13.640411]   PREFETCH window: d0000000-d1ffffff
[   13.640421] PCI: Bridge: 0000:00:1c.1
[   13.640424]   IO window: disabled.
[   13.640433]   MEM window: d4100000-d41fffff
[   13.640440]   PREFETCH window: disabled.
[   13.640449] PCI: Bridge: 0000:00:1c.2
[   13.640452]   IO window: disabled.
[   13.640461]   MEM window: d4000000-d40fffff
[   13.640468]   PREFETCH window: disabled.
[   13.640476] PCI: Bridge: 0000:00:1e.0
[   13.640480]   IO window: disabled.
[   13.640488]   MEM window: disabled.
[   13.640494]   PREFETCH window: disabled.
[   13.640541] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   13.640553] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.640588] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 20 (level, low) -> IRQ 17
[   13.640598] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.640632] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 21 (level, low) -> IRQ 18
[   13.640643] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.640663] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.640685] NET: Registered protocol family 2
[   13.678332] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   13.678736] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   13.678937] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   13.679134] TCP: Hash tables configured (established 16384 bind 16384)
[   13.679139] TCP reno registered
[   13.690465] checking if image is initramfs... it is
[   15.259771] Freeing initrd memory: 7290k freed
[   15.260041] Simple Boot Flag at 0x36 set to 0x1
[   15.261390] audit: initializing netlink socket (disabled)
[   15.261412] audit(1219564429.936:1): initialized
[   15.265874] VFS: Disk quotas dquot_6.5.1
[   15.266031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.266291] io scheduler noop registered
[   15.266296] io scheduler anticipatory registered
[   15.266300] io scheduler deadline registered
[   15.266324] io scheduler cfq registered (default)
[   15.266342] Boot video device is 0000:00:02.0
[   15.266662] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.266739] assign_interrupt_mode Found MSI capability
[   15.266805] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.266880] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.267037] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.267113] assign_interrupt_mode Found MSI capability
[   15.267175] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.267246] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.267404] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.267480] assign_interrupt_mode Found MSI capability
[   15.267542] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.267612] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.268102] isapnp: Scanning for PnP cards...
[   15.622897] isapnp: No Plug & Play device found
[   15.682341] Real Time Clock Driver v1.12ac
[   15.682746] hpet_resources: 0xfed00000 is busy
[   15.682802] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.685383] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.685525] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.685845] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.719269] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.719280] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.740681] mice: PS/2 mouse device common for all mice
[   15.740910] EISA: Probing bus 0 at eisa.0
[   15.740922] Cannot allocate resource for EISA slot 1
[   15.740928] Cannot allocate resource for EISA slot 2
[   15.740969] EISA: Detected 0 cards.
[   15.740974] cpuidle: using governor ladder
[   15.740978] cpuidle: using governor menu
[   15.741144] NET: Registered protocol family 1
[   15.741198] Using IPI No-Shortcut mode
[   15.741249] registered taskstats version 1
[   15.741427]   Magic number: 4:894:875
[   15.741561] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.741565] EDD information not available.
[   15.741823] Freeing unused kernel memory: 368k freed
[   15.759759] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.183097] fuse init (API version 7.9)
[   17.223932] ACPI: SSDT 1F6E6646, 0238 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   17.224430] ACPI: SSDT 1F6E610B, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   17.229077] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.229089] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.229628] ACPI: SSDT 1F6E687E, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   17.230076] ACPI: SSDT 1F6E65C1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   17.232047] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   17.232059] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.236315] ACPI: Thermal Zone [TZ00] (45 C)
[   17.976549] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   17.976579] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   17.997948] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   17.997978] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   17.998005] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   17.998033] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   18.043965] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   18.072680] usbcore: registered new interface driver usbfs
[   18.072726] usbcore: registered new interface driver hub
[   18.083810] usbcore: registered new device driver usb
[   18.086901] tg3.c:v3.86 (November 9, 2007)
[   18.086999] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[   18.087022] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   18.087337] USB Universal Host Controller Interface driver v3.0
[   18.360156] SCSI subsystem initialized
[   18.379341] libata version 3.00 loaded.
[   18.409052] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1b:38:9c:2e:1d
[   18.409068] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[   18.409074] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.410290] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   18.410311] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.410319] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.410665] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.410712] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   18.410979] usb usb1: configuration #1 chosen from 1 choice
[   18.411035] hub 1-0:1.0: USB hub found
[   18.411046] hub 1-0:1.0: 2 ports detected
[   18.511807] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   18.511828] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.511836] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.511893] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.511936] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[   18.512175] usb usb2: configuration #1 chosen from 1 choice
[   18.512232] hub 2-0:1.0: USB hub found
[   18.512242] hub 2-0:1.0: 2 ports detected
[   18.615754] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   18.615778] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.615787] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.615834] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.615879] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   18.616110] usb usb3: configuration #1 chosen from 1 choice
[   18.616164] hub 3-0:1.0: USB hub found
[   18.616175] hub 3-0:1.0: 2 ports detected
[   18.720723] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 22
[   18.720745] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.720753] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.720801] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.720845] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00001880
[   18.721079] usb usb4: configuration #1 chosen from 1 choice
[   18.721128] hub 4-0:1.0: USB hub found
[   18.721139] hub 4-0:1.0: 2 ports detected
[   18.824783] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   18.824807] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.824815] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.824867] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   18.828818] ehci_hcd 0000:00:1d.7: debug port 1
[   18.828830] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.828844] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd4544000
[   18.843504] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.843753] usb usb5: configuration #1 chosen from 1 choice
[   18.843805] hub 5-0:1.0: USB hub found
[   18.843818] hub 5-0:1.0: 8 ports detected
[   18.954002] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   18.954064] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.954087] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   18.960630] ata_piix 0000:00:1f.2: version 2.12
[   18.960641] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   19.116436] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   19.116501] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.120538] scsi0 : ata_piix
[   19.122095] scsi1 : ata_piix
[   19.123933] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   19.123940] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   19.288119] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[   19.288129] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.303918] ata1.00: configured for UDMA/100
[   19.323309] Clocksource tsc unstable (delta = -434475055 ns)
[   19.327693] Time: hpet clocksource has been installed.
[   19.372743] usb 5-6: new high speed USB device using ehci_hcd and address 2
[   19.516242] ata2.00: ATAPI: Optiarc DVD RW AD-7560A, D802, max UDMA/33
[   19.692094] ata2.00: configured for UDMA/33
[   19.692381] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[   19.693613] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  D802 PQ: 0 ANSI: 5
[   19.708178] Driver 'sd' needs updating - please use bus_type methods
[   19.708329] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.708355] sd 0:0:0:0: [sda] Write Protect is off
[   19.708361] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.708399] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.708494] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   19.708518] sd 0:0:0:0: [sda] Write Protect is off
[   19.708523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.708559] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.708577]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.735967]  sda1 sda2 sda3 < sda5 sda6 >
[   19.772712] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.781911] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.781920] Uniform CD-ROM driver Revision: 3.20
[   19.782025] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.783804] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.783858] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   20.058926] usb 5-6: configuration #1 chosen from 1 choice
[   20.121142] Attempting manual resume
[   20.121149] swsusp: Resume From Partition 8:5
[   20.121153] PM: Checking swsusp image.
[   20.121402] PM: Resume from disk failed.
[   20.177394] kjournald starting.  Commit interval 5 seconds
[   20.177424] EXT3-fs: mounted filesystem with ordered data mode.
[   20.482953] usbcore: registered new interface driver libusual
[   20.719614] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   20.878840] usb 4-1: configuration #1 chosen from 1 choice
[   20.972425] Initializing USB Mass Storage driver...
[   21.125221] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   21.288969] usb 4-2: configuration #1 chosen from 1 choice
[   21.292040] scsi2 : SCSI emulation for USB Mass Storage devices
[   21.292182] usbcore: registered new interface driver usb-storage
[   21.292189] USB Mass Storage support registered.
[   21.292345] usb-storage: device found at 2
[   21.292349] usb-storage: waiting for device to settle before scanning
[   26.268201] usb-storage: device scan complete
[   26.274606] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   26.276593] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   26.276745] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   28.336430] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.382038] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.588734] Linux agpgart interface v0.102
[   28.708347] agpgart: Detected an Intel 945GM Chipset.
[   28.709512] agpgart: Detected 7932K stolen memory.
[   28.728230] agpgart: AGP aperture is 256M @ 0xc0000000
[   29.229843] iTCO_vendor_support: vendor-support=0
[   29.256079] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   29.257529] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   29.257617] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.316248] input: Power Button (FF) as /devices/virtual/input/input2
[   29.339888] ACPI: Power Button (FF) [PWRF]
[   29.340028] input: Lid Switch as /devices/virtual/input/input3
[   29.340153] ACPI: Lid Switch [LID0]
[   29.340260] input: Power Button (CM) as /devices/virtual/input/input4
[   29.355913] ACPI: Power Button (CM) [PWRB]
[   29.356055] input: Sleep Button (CM) as /devices/virtual/input/input5
[   29.371863] ACPI: Sleep Button (CM) [SLPB]
[   29.462089] intel_rng: FWH not detected
[   30.372079] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   30.391472] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.397057] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   30.407465] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   30.856611] ACPI: AC Adapter [ACAD] (on-line)
[   31.266683] ACPI: Battery Slot [BAT1] (battery present)
[   31.432301] ACPI: WMI-Acer: Mapper loaded
[   31.648244] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   31.648293] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.224061] usbcore: registered new interface driver usbserial
[   32.224127] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   32.224237] usbcore: registered new interface driver usbserial_generic
[   32.224243] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   32.295962] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[   32.296040] airprime 4-1:1.0: airprime converter detected
[   32.296304] usb 4-1: airprime converter now attached to ttyUSB0
[   32.296477] usb 4-1: airprime converter now attached to ttyUSB1
[   32.296645] usb 4-1: airprime converter now attached to ttyUSB2
[   32.296663] airprime 4-1:1.1: airprime converter detected
[   32.296843] usb 4-1: airprime converter now attached to ttyUSB3
[   32.297012] usb 4-1: airprime converter now attached to ttyUSB4
[   32.297199] usb 4-1: airprime converter now attached to ttyUSB5
[   32.297217] airprime 4-1:1.2: airprime converter detected
[   32.297391] usb 4-1: airprime converter now attached to ttyUSB6
[   32.297563] usb 4-1: airprime converter now attached to ttyUSB7
[   32.297736] usb 4-1: airprime converter now attached to ttyUSB8
[   32.297758] usbcore: registered new interface driver airprime
[   32.568530] usbcore: registered new interface driver hiddev
[   32.582107] input: USB Mouse as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input8
[   32.602796] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.3-2
[   32.602830] usbcore: registered new interface driver usbhid
[   32.602838] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.675522] b43-phy0: Broadcom 4311 WLAN found
[   32.715612] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   32.715646] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   32.788271] phy0: Selected rate control algorithm 'simple'
[   32.870913] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   33.861254] input: PS/2 Mouse as /devices/virtual/input/input10
[   33.934747] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   35.952531] loop: module loaded
[   36.040040] lp: driver loaded but no devices found
[   36.285762] Adding 1172704k swap on /dev/sda5.  Priority:-1 extents:1 across:1172704k
[   36.782442] EXT3 FS on sda1, internal journal
[   37.729213] kjournald starting.  Commit interval 5 seconds
[   37.730880] EXT3 FS on sda2, internal journal
[   37.730889] EXT3-fs: mounted filesystem with ordered data mode.
[   37.764486] kjournald starting.  Commit interval 5 seconds
[   37.764796] EXT3 FS on sda6, internal journal
[   37.764804] EXT3-fs: mounted filesystem with ordered data mode.
[   38.657975] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.272532] No dock devices found.
[   42.546978] apm: BIOS not found.
[   44.601838] input: b43-phy0 as /devices/virtual/input/input12
[   44.779923] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   44.780031] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   46.844069] NET: Registered protocol family 10
[   46.844347] lo: Disabled Privacy Extensions
[   46.844781] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.174758] [drm] Initialized drm 1.1.0 20060810
[   47.311184] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   47.311203] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   47.311391] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.318665] input: b43-phy0 as /devices/virtual/input/input13
[   47.422940] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   47.422955] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   53.665639] input: b43-phy0 as /devices/virtual/input/input14
[   53.735863] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   53.735877] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   67.943390] CPU0 attaching NULL sched-domain.
[   67.943403] CPU1 attaching NULL sched-domain.
[   67.958573] CPU0 attaching sched-domain:
[   67.958584]  domain 0: span 03
[   67.958589]   groups: 01 02
[   67.958596] CPU1 attaching sched-domain:
[   67.958600]  domain 0: span 03
[   67.958606]   groups: 02 01
[   68.052568] CPU0 attaching NULL sched-domain.
[   68.052577] CPU1 attaching NULL sched-domain.
[   68.075312] CPU0 attaching sched-domain:
[   68.075317]  domain 0: span 03
[   68.075319]   groups: 01 02
[   68.075322] CPU1 attaching sched-domain:
[   68.075324]  domain 0: span 03
[   68.075326]   groups: 02 01
[   69.244916] input: b43-phy0 as /devices/virtual/input/input15
[   69.315368] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   69.315382] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   75.219561] input: b43-phy0 as /devices/virtual/input/input16
[   75.293076] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   75.293085] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   80.928817] input: b43-phy0 as /devices/virtual/input/input17
[   81.002021] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   81.002030] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   84.843135] input: b43-phy0 as /devices/virtual/input/input18
[   84.919201] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   84.919212] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   94.300509] input: b43-phy0 as /devices/virtual/input/input19
[   94.370434] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   94.370447] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[   99.173921] input: b43-phy0 as /devices/virtual/input/input20
[   99.248294] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[   99.248303] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  128.899945] input: b43-phy0 as /devices/virtual/input/input21
[  128.973327] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  128.973336] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  150.796992] PPP generic driver version 2.4.2
[  159.084159] PPP BSD Compression module registered
[  159.160589] PPP Deflate Compression module registered
[  173.703946] input: b43-phy0 as /devices/virtual/input/input22
[  174.212650] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  174.212665] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  269.871189] input: b43-phy0 as /devices/virtual/input/input23
[  269.944274] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  269.944283] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  357.631579] input: b43-phy0 as /devices/virtual/input/input24
[  357.697947] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  357.697961] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  436.873217] input: b43-phy0 as /devices/virtual/input/input25
[  436.948616] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  436.948627] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  525.783920] input: b43-phy0 as /devices/virtual/input/input26
[  525.856596] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  525.856608] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  563.382878] input: b43-phy0 as /devices/virtual/input/input27
[  563.456227] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  563.456236] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  595.045895] input: b43-phy0 as /devices/virtual/input/input28
[  595.123187] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  595.123197] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  642.882167] input: b43-phy0 as /devices/virtual/input/input29
[  642.995214] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  642.995223] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  709.679452] input: b43-phy0 as /devices/virtual/input/input30
[  709.753145] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  709.753155] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  786.574291] input: b43-phy0 as /devices/virtual/input/input31
[  786.650321] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  786.650330] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  859.238183] input: b43-phy0 as /devices/virtual/input/input32
[  859.256491] evdev: no more free evdev devices
[  859.256503] input: failed to attach handler evdev to device input32, error: -23
[  859.295265] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  859.295276] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  894.463953] input: b43-phy0 as /devices/virtual/input/input33
[  894.484298] evdev: no more free evdev devices
[  894.484314] input: failed to attach handler evdev to device input33, error: -23
[  894.523068] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  894.523084] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  923.025569] input: b43-phy0 as /devices/virtual/input/input34
[  923.046138] evdev: no more free evdev devices
[  923.046154] input: failed to attach handler evdev to device input34, error: -23
[  923.083632] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  923.083644] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[  954.303811] input: b43-phy0 as /devices/virtual/input/input35
[  954.324333] evdev: no more free evdev devices
[  954.324350] input: failed to attach handler evdev to device input35, error: -23
[  954.362852] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[  954.362869] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1031.685740] input: b43-phy0 as /devices/virtual/input/input36
[ 1031.712150] evdev: no more free evdev devices
[ 1031.712168] input: failed to attach handler evdev to device input36, error: -23
[ 1031.749637] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1031.749648] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1092.884396] input: b43-phy0 as /devices/virtual/input/input37
[ 1092.909084] evdev: no more free evdev devices
[ 1092.909094] input: failed to attach handler evdev to device input37, error: -23
[ 1092.941552] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1092.941561] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1164.111467] input: b43-phy0 as /devices/virtual/input/input38
[ 1164.139160] evdev: no more free evdev devices
[ 1164.139170] input: failed to attach handler evdev to device input38, error: -23
[ 1164.181088] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1164.181102] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1255.065356] input: b43-phy0 as /devices/virtual/input/input39
[ 1255.084244] evdev: no more free evdev devices
[ 1255.084257] input: failed to attach handler evdev to device input39, error: -23
[ 1255.121831] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1255.121840] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1345.655945] input: b43-phy0 as /devices/virtual/input/input40
[ 1345.682949] evdev: no more free evdev devices
[ 1345.682959] input: failed to attach handler evdev to device input40, error: -23
[ 1345.722560] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1345.722570] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1436.023075] input: b43-phy0 as /devices/virtual/input/input41
[ 1436.041918] evdev: no more free evdev devices
[ 1436.041930] input: failed to attach handler evdev to device input41, error: -23
[ 1436.080315] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1436.080325] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1526.542343] input: b43-phy0 as /devices/virtual/input/input42
[ 1526.571041] evdev: no more free evdev devices
[ 1526.571053] input: failed to attach handler evdev to device input42, error: -23
[ 1526.607605] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1526.607614] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1617.694081] input: b43-phy0 as /devices/virtual/input/input43
[ 1617.721791] evdev: no more free evdev devices
[ 1617.721802] input: failed to attach handler evdev to device input43, error: -23
[ 1617.760037] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1617.760046] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1709.096869] input: b43-phy0 as /devices/virtual/input/input44
[ 1709.127394] evdev: no more free evdev devices
[ 1709.127405] input: failed to attach handler evdev to device input44, error: -23
[ 1709.165306] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1709.165317] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1782.020609] input: b43-phy0 as /devices/virtual/input/input45
[ 1782.045155] evdev: no more free evdev devices
[ 1782.045171] input: failed to attach handler evdev to device input45, error: -23
[ 1782.078648] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1782.078662] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1802.147556] input: b43-phy0 as /devices/virtual/input/input46
[ 1802.168327] evdev: no more free evdev devices
[ 1802.168345] input: failed to attach handler evdev to device input46, error: -23
[ 1802.205649] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1802.205660] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1843.451196] input: b43-phy0 as /devices/virtual/input/input47
[ 1843.471773] evdev: no more free evdev devices
[ 1843.471784] input: failed to attach handler evdev to device input47, error: -23
[ 1843.509234] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1843.509244] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1869.761252] input: b43-phy0 as /devices/virtual/input/input48
[ 1869.781857] evdev: no more free evdev devices
[ 1869.781875] input: failed to attach handler evdev to device input48, error: -23
[ 1869.820331] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1869.820348] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1889.906645] input: b43-phy0 as /devices/virtual/input/input49
[ 1889.930375] evdev: no more free evdev devices
[ 1889.930392] input: failed to attach handler evdev to device input49, error: -23
[ 1889.968845] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1889.968861] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1910.324080] input: b43-phy0 as /devices/virtual/input/input50
[ 1910.343700] evdev: no more free evdev devices
[ 1910.343716] input: failed to attach handler evdev to device input50, error: -23
[ 1910.382184] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1910.382200] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1931.049982] input: b43-phy0 as /devices/virtual/input/input51
[ 1931.069648] evdev: no more free evdev devices
[ 1931.069663] input: failed to attach handler evdev to device input51, error: -23
[ 1931.114124] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1931.114132] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1951.344346] input: b43-phy0 as /devices/virtual/input/input52
[ 1951.364973] evdev: no more free evdev devices
[ 1951.364990] input: failed to attach handler evdev to device input52, error: -23
[ 1951.403454] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1951.403471] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1971.815314] input: b43-phy0 as /devices/virtual/input/input53
[ 1971.834962] evdev: no more free evdev devices
[ 1971.834974] input: failed to attach handler evdev to device input53, error: -23
[ 1971.872523] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1971.872532] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 1991.648901] input: b43-phy0 as /devices/virtual/input/input54
[ 1991.669479] evdev: no more free evdev devices
[ 1991.669491] input: failed to attach handler evdev to device input54, error: -23
[ 1991.707015] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 1991.707026] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2011.654024] input: b43-phy0 as /devices/virtual/input/input55
[ 2011.674371] evdev: no more free evdev devices
[ 2011.674387] input: failed to attach handler evdev to device input55, error: -23
[ 2011.712862] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2011.712879] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2031.671823] input: b43-phy0 as /devices/virtual/input/input56
[ 2031.692388] evdev: no more free evdev devices
[ 2031.692405] input: failed to attach handler evdev to device input56, error: -23
[ 2031.729828] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2031.729839] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2051.571612] input: b43-phy0 as /devices/virtual/input/input57
[ 2051.594127] evdev: no more free evdev devices
[ 2051.594137] input: failed to attach handler evdev to device input57, error: -23
[ 2051.631587] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2051.631596] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2071.731164] input: b43-phy0 as /devices/virtual/input/input58
[ 2071.750866] evdev: no more free evdev devices
[ 2071.750881] input: failed to attach handler evdev to device input58, error: -23
[ 2071.788306] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2071.788317] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2091.854929] input: b43-phy0 as /devices/virtual/input/input59
[ 2091.874636] evdev: no more free evdev devices
[ 2091.874652] input: failed to attach handler evdev to device input59, error: -23
[ 2091.913100] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2091.913116] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2112.014851] input: b43-phy0 as /devices/virtual/input/input60
[ 2112.035448] evdev: no more free evdev devices
[ 2112.035465] input: failed to attach handler evdev to device input60, error: -23
[ 2112.073958] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2112.073975] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2138.855277] input: b43-phy0 as /devices/virtual/input/input61
[ 2138.874978] evdev: no more free evdev devices
[ 2138.874994] input: failed to attach handler evdev to device input61, error: -23
[ 2138.918284] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2138.918293] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2164.844858] input: b43-phy0 as /devices/virtual/input/input62
[ 2164.868409] evdev: no more free evdev devices
[ 2164.868425] input: failed to attach handler evdev to device input62, error: -23
[ 2164.901890] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2164.901904] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2185.043837] input: b43-phy0 as /devices/virtual/input/input63
[ 2185.067556] evdev: no more free evdev devices
[ 2185.067572] input: failed to attach handler evdev to device input63, error: -23
[ 2185.104996] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2185.105007] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2205.240155] input: b43-phy0 as /devices/virtual/input/input64
[ 2205.264852] evdev: no more free evdev devices
[ 2205.264867] input: failed to attach handler evdev to device input64, error: -23
[ 2205.298329] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2205.298343] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2210.943247] CPU0 attaching NULL sched-domain.
[ 2210.943261] CPU1 attaching NULL sched-domain.
[ 2210.959828] CPU0 attaching sched-domain:
[ 2210.959837]  domain 0: span 03
[ 2210.959842]   groups: 01 02
[ 2210.959849]   domain 1: span 03
[ 2210.959853]    groups: 03
[ 2210.959858] CPU1 attaching sched-domain:
[ 2210.959862]  domain 0: span 03
[ 2210.959866]   groups: 02 01
[ 2210.959872]   domain 1: span 03
[ 2210.959876]    groups: 03
[ 2234.174078] input: b43-phy0 as /devices/virtual/input/input65
[ 2234.194397] evdev: no more free evdev devices
[ 2234.194413] input: failed to attach handler evdev to device input65, error: -23
[ 2234.232898] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2234.232914] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2256.207745] input: b43-phy0 as /devices/virtual/input/input66
[ 2256.227427] evdev: no more free evdev devices
[ 2256.227437] input: failed to attach handler evdev to device input66, error: -23
[ 2256.271876] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2256.271884] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2277.417882] input: b43-phy0 as /devices/virtual/input/input67
[ 2277.438661] evdev: no more free evdev devices
[ 2277.438679] input: failed to attach handler evdev to device input67, error: -23
[ 2277.476910] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2277.476926] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2297.837960] input: b43-phy0 as /devices/virtual/input/input68
[ 2297.858499] evdev: no more free evdev devices
[ 2297.858516] input: failed to attach handler evdev to device input68, error: -23
[ 2297.897109] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2297.897126] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2318.522117] input: b43-phy0 as /devices/virtual/input/input69
[ 2318.550770] evdev: no more free evdev devices
[ 2318.550786] input: failed to attach handler evdev to device input69, error: -23
[ 2318.584264] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2318.584278] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).
[ 2386.737036] input: b43-phy0 as /devices/virtual/input/input70
[ 2386.757653] evdev: no more free evdev devices
[ 2386.757670] input: failed to attach handler evdev to device input70, error: -23
[ 2386.796209] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[ 2386.796226] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).


>> lsmod.txt <<
Module                  Size  Used by
ppp_deflate             6784  0 
zlib_deflate           20760  1 ppp_deflate
bsd_comp                6912  0 
ppp_async              13312  1 
crc_ccitt               3072  1 ppp_async
ppp_generic            29588  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7040  1 ppp_generic
i915                   32512  2 
drm                    82452  3 i915
ipv6                  267780  19 
binfmt_misc            12808  1 
rfkill_input            5504  0 
acpi_cpufreq           10796  2 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  2 parport_pc,lp
loop                   18948  0 
joydev                 13120  0 
arc4                    2944  2 
evdev                  13056  28 
ecb                     4480  2 
blkcipher               8324  1 ecb
serio_raw               7940  0 
psmouse                40336  0 
pcspkr                  4224  0 
b43                   144420  0 
rfkill                  8592  61 rfkill_input,b43
usbhid                 31872  0 
mac80211              165652  1 b43
hid                    38784  1 usbhid
cfg80211               15112  1 mac80211
airprime                9988  1 
usbserial              35816  4 airprime
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_hda_intel         344728  1 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
wmi_acer                9644  0 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
battery                14212  0 
ac                      6916  0 
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              25492  1 
snd                    56996  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  3 drm,intel_agp
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
usb_storage            73664  0 
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
libusual               19108  1 usb_storage
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
ata_piix               19588  4 
pata_acpi               8320  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
tg3                   116228  0 
usbcore               146028  8 usbhid,airprime,usbserial,usb_storage,libusual,ehci_hcd,uhci_hcd
ssb                    34308  1 b43
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 


>> lspci.txt <<
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

---

### Post by libra1780 on 2008-08-24
the modules seem to be loaded correctly
try to chek the settings in control pannel for audio hardware..
check mixer
try amarok or something like, where you can change the audio hardware settings.. and the bargraph shows you that something is played

---


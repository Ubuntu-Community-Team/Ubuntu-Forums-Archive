---
title: "New kernel problems"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by LecJackS on 2009-01-18
When I upgraded to Intrepid it also has installed a new kernel (2.6.27-7), and when I restarted I began to notice problems.

First it was the loading. The ubuntu loading bar took charge as being 4 minutes static shortly after starting to load, then it has loaded normally.

Now, when the window appeared to enter user and pass, I realized that *the keyboard wasn't working, I moved the mouse to restart, and it neither worked.

I reset the computer, started with the previous kernel (2.6.24-21), and it booted normally.

I searched a little about the problem, but nothing appeared. I assumed it was because it was new, and take out someone asking the question, and then I waited, because it doesn't bother me much.

Not long ago came a new kernel (2.6.27-9), and as there was little time between the departure of the former and the previous, I thought they had solved, among others, my problem.

But no, the same thing happens. Takes about 4 minutes to load, then the usbs doesn't work, so I can't enter anything.

The disable of usb is for security? or is that I have a flaw? I find it very strange that so long to load (30-40 seconds is normal).


Thanks ;D


PD: Sorry for my english.

---

### Post by LecJackS on 2009-01-20
Nothing?

I have problems with vmware, because it uses another version of gcc, that is in the new kernels, but not this.

I need a solution, or a simple answer that says that the "new" kernels have a few bugs, or something similar.

---

### Post by LecJackS on 2009-01-24
Here is the bootchart:
[[IMG]http://img297.imageshack.us/img297/4539/intrepid200901241xp4.th.png[/IMG]](http://img297.imageshack.us/img297/4539/intrepid200901241xp4.png)

Look at that modprobe.

And now, the mouse and keyboard works, but the usb modem not.


**Edit:** ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x4fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37830000 - 37fefe32
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 4FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 4FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 4FFF30C0, 4561 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 4FFF0000, 0040
[    0.000000] ACPI: APIC 4FFF7640, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 383MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037830000 - 0037fefe32]          RAMDISK ==> [0037830000 - 0037fefe32]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0004fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0004fff0
[    0.000000] On node 0 totalpages: 327568
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 97424 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324688
[    0.000000] Kernel command line: root=UUID=6de76dad-7494-4f60-9e6c-27e5105d3fcb ro
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2079.509 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1284180k/1310656k available (2572k kernel code, 25228k reserved, 1160k data, 424k init, 393152k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 4159.01 BogoMIPS (lpj=8318036)
[    0.004186] Security Framework initialized
[    0.004265] SELinux:  Disabled at boot.
[    0.004366] AppArmor: AppArmor initialized
[    0.004447] Mount-cache hash table entries: 512
[    0.004718] Initializing cgroup subsys ns
[    0.004794] Initializing cgroup subsys cpuacct
[    0.004868] Initializing cgroup subsys memory
[    0.004956] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.005035] CPU: L2 Cache: 512K (64 bytes/line)
[    0.005123] Checking 'hlt' instruction... OK.
[    0.020391] SMP alternatives: switching to UP code
[    0.025624] Freeing SMP alternatives: 11k freed
[    0.025700] ACPI: Core revision 20080609
[    0.027327] ACPI: Checking initramfs for custom DSDT
[    0.345821] ENABLING IO-APIC IRQs
[    0.346083] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.385845] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[    0.388024] APIC calibration not consistent with PM Timer: 96ms instead of 100ms
[    0.388024] APIC delta adjusted to PM-Timer: 2079539 (1996469)
[    0.388024] Brought up 1 CPUs
[    0.388024] Total of 1 processors activated (4159.01 BogoMIPS).
[    0.388024] CPU0 attaching sched-domain:
[    0.388024]  domain 0: span 0 level CPU
[    0.388024]   groups: 0
[    0.388024] net_namespace: 840 bytes
[    0.388024] Booting paravirtualized kernel on bare hardware
[    0.388024] Time: 21:15:11  Date: 01/25/09
[    0.388024] NET: Registered protocol family 16
[    0.388024] EISA bus registered
[    0.388024] ACPI: bus type pci registered
[    0.417718] PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=3
[    0.417796] PCI: Using configuration type 1 for base access
[    0.419925] ACPI: EC: Look up EC in DSDT
[    0.427972] ACPI: Interpreter enabled
[    0.428031] ACPI: (supports S0 S1 S4 S5)
[    0.428314] ACPI: Using IOAPIC for interrupt routing
[    0.440079] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.440244] PCI: 0000:00:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.440265] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.440520] PCI: 0000:00:01.1 reg 10 io port: [e000, e01f]
[    0.440554] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.440632] pci 0000:00:01.1: PME# disabled
[    0.440730] PCI: 0000:00:02.0 reg 10 32bit mmio: [dd087000, dd087fff]
[    0.440763] pci 0000:00:02.0: supports D1
[    0.440765] pci 0000:00:02.0: supports D2
[    0.440768] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440847] pci 0000:00:02.0: PME# disabled
[    0.440939] PCI: 0000:00:02.1 reg 10 32bit mmio: [dd082000, dd082fff]
[    0.440972] pci 0000:00:02.1: supports D1
[    0.440974] pci 0000:00:02.1: supports D2
[    0.440976] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441055] pci 0000:00:02.1: PME# disabled
[    0.441153] PCI: 0000:00:02.2 reg 10 32bit mmio: [dd083000, dd0830ff]
[    0.441190] pci 0000:00:02.2: supports D1
[    0.441192] pci 0000:00:02.2: supports D2
[    0.441195] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441274] pci 0000:00:02.2: PME# disabled
[    0.441371] PCI: 0000:00:04.0 reg 10 32bit mmio: [dd086000, dd086fff]
[    0.441378] PCI: 0000:00:04.0 reg 14 io port: [e400, e407]
[    0.441407] pci 0000:00:04.0: supports D1
[    0.441409] pci 0000:00:04.0: supports D2
[    0.441411] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441490] pci 0000:00:04.0: PME# disabled
[    0.441582] PCI: 0000:00:05.0 reg 10 32bit mmio: [dd000000, dd07ffff]
[    0.441615] pci 0000:00:05.0: supports D1
[    0.441617] pci 0000:00:05.0: supports D2
[    0.441638] PCI: 0000:00:06.0 reg 10 io port: [d000, d0ff]
[    0.441645] PCI: 0000:00:06.0 reg 14 io port: [d400, d47f]
[    0.441651] PCI: 0000:00:06.0 reg 18 32bit mmio: [dd080000, dd080fff]
[    0.441677] pci 0000:00:06.0: supports D1
[    0.441678] pci 0000:00:06.0: supports D2
[    0.441736] PCI: 0000:00:09.0 reg 20 io port: [f000, f00f]
[    0.441778] PCI: 0000:00:0d.0 reg 10 32bit mmio: [dd084000, dd0847ff]
[    0.441785] PCI: 0000:00:0d.0 reg 14 32bit mmio: [dd085000, dd08503f]
[    0.441814] pci 0000:00:0d.0: supports D1
[    0.441816] pci 0000:00:0d.0: supports D2
[    0.441818] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.441897] pci 0000:00:0d.0: PME# disabled
[    0.442048] PCI: 0000:01:04.0 reg 10 32bit mmio: [dc000000, dc003fff]
[    0.442056] PCI: 0000:01:04.0 reg 14 io port: [a000, a0ff]
[    0.442085] PCI: 0000:01:04.0 reg 30 32bit mmio: [0, 1ffff]
[    0.442101] pci 0000:01:04.0: supports D1
[    0.442103] pci 0000:01:04.0: supports D2
[    0.442105] pci 0000:01:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.442185] pci 0000:01:04.0: PME# disabled
[    0.442293] PCI: 0000:01:0b.0 reg 10 io port: [a400, a407]
[    0.442301] PCI: 0000:01:0b.0 reg 14 io port: [a800, a803]
[    0.442309] PCI: 0000:01:0b.0 reg 18 io port: [ac00, ac07]
[    0.442316] PCI: 0000:01:0b.0 reg 1c io port: [b000, b003]
[    0.442324] PCI: 0000:01:0b.0 reg 20 io port: [b400, b40f]
[    0.442332] PCI: 0000:01:0b.0 reg 24 32bit mmio: [dc004000, dc0041ff]
[    0.442340] PCI: 0000:01:0b.0 reg 30 32bit mmio: [0, 7ffff]
[    0.442355] pci 0000:01:0b.0: supports D1
[    0.442357] pci 0000:01:0b.0: supports D2
[    0.442388] PCI: bridge 0000:00:08.0 io port: [a000, bfff]
[    0.442392] PCI: bridge 0000:00:08.0 32bit mmio: [db000000, dcffffff]
[    0.442426] PCI: 0000:03:00.0 reg 10 32bit mmio: [d9000000, d9ffffff]
[    0.442433] PCI: 0000:03:00.0 reg 14 32bit mmio: [d0000000, d7ffffff]
[    0.442453] PCI: 0000:03:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.442498] PCI: bridge 0000:00:1e.0 32bit mmio: [d9000000, daffffff]
[    0.442502] PCI: bridge 0000:00:1e.0 32bit mmio pref: [d0000000, d7ffffff]
[    0.442513] bus 00 -> node 0
[    0.442520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.442763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.443211] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.513793] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.514835] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.515773] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.516721] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.517657] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.518696] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.519635] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.520566] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.521506] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.522608] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.523549] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.524618] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.525560] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.526497] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.527434] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.528465] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.529477] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[    0.529914] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
[    0.530299] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[    0.530684] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    0.531069] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.531581] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.532213] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    0.532821] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.533429] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[    0.534036] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[    0.534643] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    0.535231] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    0.536269] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.536876] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
[    0.537483] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[    0.538140] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.538776] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.538896] pnp: PnP ACPI init
[    0.538974] ACPI: bus type pnp registered
[    0.546787] pnp: PnP ACPI: found 15 devices
[    0.546861] ACPI: ACPI bus type pnp unregistered
[    0.546937] PnPBIOS: Disabled by ACPI PNP
[    0.547483] PCI: Using ACPI for IRQ routing
[    0.547695] NET: Registered protocol family 8
[    0.547695] NET: Registered protocol family 20
[    0.547695] NetLabel: Initializing
[    0.547695] NetLabel:  domain hash size = 128
[    0.548034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.548124] NetLabel:  unlabeled traffic allowed by default
[    0.548499] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.548577]    actual entries 65620
[    0.548856] AppArmor: AppArmor Filesystem Enabled
[    0.548953] ACPI: RTC can wake from S4
[    0.549033] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.549033] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.549033] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.549033] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.549033] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.549033] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.549033] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.549033] system 00:01: ioport range 0x5500-0x553f has been reserved
[    0.549033] system 00:02: iomem range 0xd8800-0xdbfff has been reserved
[    0.549033] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[    0.549033] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.549033] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.549033] system 00:02: iomem range 0x4fff0000-0x4fffffff could not be reserved
[    0.549092] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.549186] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.549264] system 00:02: iomem range 0x100000-0x4ffeffff could not be reserved
[    0.549358] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.549452] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.549551] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.585894] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.585972] pci 0000:00:08.0:   IO window: 0xa000-0xbfff
[    0.586051] pci 0000:00:08.0:   MEM window: 0xdb000000-0xdcffffff
[    0.586129] pci 0000:00:08.0:   PREFETCH window: 0x00000060000000-0x000000600fffff
[    0.586228] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.586303] pci 0000:00:1e.0:   IO window: disabled
[    0.586380] pci 0000:00:1e.0:   MEM window: 0xd9000000-0xdaffffff
[    0.586457] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.586563] pci 0000:00:08.0: setting latency timer to 64
[    0.586571] bus: 00 index 0 io port: [0, ffff]
[    0.586644] bus: 00 index 1 mmio: [0, ffffffff]
[    0.586717] bus: 01 index 0 io port: [a000, bfff]
[    0.586791] bus: 01 index 1 mmio: [db000000, dcffffff]
[    0.586865] bus: 01 index 2 mmio: [60000000, 600fffff]
[    0.586940] bus: 01 index 3 mmio: [0, 0]
[    0.587012] bus: 03 index 0 mmio: [0, 0]
[    0.587084] bus: 03 index 1 mmio: [d9000000, daffffff]
[    0.587158] bus: 03 index 2 mmio: [d0000000, d7ffffff]
[    0.587232] bus: 03 index 3 mmio: [0, 0]
[    0.587314] NET: Registered protocol family 2
[    0.587524] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.587974] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.589523] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.590304] TCP: Hash tables configured (established 131072 bind 65536)
[    0.590383] TCP reno registered
[    0.590590] NET: Registered protocol family 1
[    0.590812] checking if image is initramfs... it is
[    1.088055] Switched to high resolution mode on CPU 0
[    1.277402] Freeing initrd memory: 7935k freed
[    1.278491] audit: initializing netlink socket (disabled)
[    1.278583] type=2000 audit(1232918111.276:1): initialized
[    1.284311] highmem bounce pool size: 64 pages
[    1.284391] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.287318] VFS: Disk quotas dquot_6.5.1
[    1.287499] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.287695] msgmni has been set to 1757
[    1.287914] io scheduler noop registered
[    1.287988] io scheduler anticipatory registered
[    1.288079] io scheduler deadline registered
[    1.288163] io scheduler cfq registered (default)
[    1.344100] pci 0000:03:00.0: Boot video device
[    1.344544] isapnp: Scanning for PnP cards...
[    1.698834] isapnp: No Plug & Play device found
[    1.746911] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.747262] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.747520] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    1.748281] 00:0a: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    1.748735] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.751017] brd: module loaded
[    1.751177] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.751495] PNP: No PS/2 controller found. Probing ports directly.
[    2.004396] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.004874] mice: PS/2 mouse device common for all mice
[    2.005129] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.005226] rtc0: alarms up to one year, y3k
[    2.005460] EISA: Probing bus 0 at eisa.0
[    2.005553] Cannot allocate resource for EISA slot 4
[    2.005628] Cannot allocate resource for EISA slot 5
[    2.005715] EISA: Detected 0 cards.
[    2.005788] cpuidle: using governor ladder
[    2.005860] cpuidle: using governor menu
[    2.006507] TCP cubic registered
[    2.006609] Using IPI No-Shortcut mode
[    2.006929] registered taskstats version 1
[    2.007133]   Magic number: 9:794:298
[    2.007251] tty ttywf: hash matches
[    2.007488] rtc_cmos 00:06: setting system clock to 2009-01-25 21:15:12 UTC (1232918112)
[    2.007584] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.007660] EDD information not available.
[    2.008225] Freeing unused kernel memory: 424k freed
[    2.008356] Write protecting the kernel text: 2576k
[    2.008464] Write protecting the kernel read-only data: 936k
[    2.182538] fuse init (API version 7.9)
[    2.208943] processor ACPI0007:00: registered as cooling_device0
[    3.138563] usbcore: registered new interface driver usbfs
[    3.138670] usbcore: registered new interface driver hub
[    3.156903] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.157423] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    3.157507] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    3.157606] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.157644] nv_probe: set workaround bit for reversed mac addr
[    3.173308] usbcore: registered new device driver usb
[    3.175737] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.200449] No dock devices found.
[    3.258194] SCSI subsystem initialized
[    3.337425] libata version 3.00 loaded.
[    3.676685] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:13:d4:46:76:9d
[    3.676788] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    3.677508] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    3.677593] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    3.677705] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.677709] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.677832] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.677951] ohci_hcd 0000:00:02.0: irq 21, io mem 0xdd087000
[    3.734348] usb usb1: configuration #1 chosen from 1 choice
[    3.734460] hub 1-0:1.0: USB hub found
[    3.734546] hub 1-0:1.0: 3 ports detected
[    3.940752] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    3.940842] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    3.940952] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    3.940956] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    3.941069] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.941187] ohci_hcd 0000:00:02.1: irq 20, io mem 0xdd082000
[    3.998455] usb usb2: configuration #1 chosen from 1 choice
[    3.998693] hub 2-0:1.0: USB hub found
[    3.998780] hub 2-0:1.0: 3 ports detected
[    4.116012] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    4.204740] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    4.204826] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    4.204936] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    4.204941] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    4.205056] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[    4.205185] ehci_hcd 0000:00:02.2: debug port 1
[    4.205262] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    4.205281] ehci_hcd 0000:00:02.2: irq 22, io mem 0xdd083000
[    4.304012] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.304588] usb usb3: configuration #1 chosen from 1 choice
[    4.304714] hub 3-0:1.0: USB hub found
[    4.304797] hub 3-0:1.0: 6 ports detected
[    4.512408] pata_amd 0000:00:09.0: version 0.3.10
[    4.512482] pata_amd 0000:00:09.0: setting latency timer to 64
[    4.512948] scsi0 : pata_amd
[    4.513848] scsi1 : pata_amd
[    4.514997] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.516302] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.672979] ata1.00: ATAPI: ASUS    CD-S520/A4, 1.31, max UDMA/33
[    4.673075] ata1.01: ATAPI: ASUS    CRW-5232AX, 1.00, max UDMA/33
[    4.673164] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c0c0c0) ACPI=0x701f (60:60:0x1f)
[    4.673170] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c0c0c0) ACPI=0x701f (60:60:0x1f)
[    4.688281] ata1.00: configured for UDMA/33
[    4.696396] ata1.01: configured for UDMA/33
[    4.700011] usb 1-2: device not accepting address 2, error -62
[    4.756017] hub 1-0:1.0: unable to enumerate USB device on port 2
[    4.868386] ata2.00: ATAPI: ASUS    DRW-1608P2, 1.17, max UDMA/66
[    4.868484] ata2.01: ATAPI: ASUS DVD-ROM DVD-E616P              0104, E1.04, max UDMA/66
[    4.868592] ata2: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc0c0c0c0) ACPI=0x701f (60:60:0x1f)
[    4.868598] ata2: nv_mode_filter: 0x1f39f&0x701f->0x701f, BIOS=0x7000 (0xc0c0c0c0) ACPI=0x701f (60:60:0x1f)
[    4.884331] ata2.00: configured for UDMA/33
[    4.900325] ata2.01: configured for UDMA/33
[    4.900703] scsi 0:0:0:0: CD-ROM            ASUS     CD-S520/A4       1.31 PQ: 0 ANSI: 5
[    4.901776] scsi 0:0:1:0: CD-ROM            ASUS     CRW-5232AX       1.00 PQ: 0 ANSI: 5
[    4.908351] scsi 1:0:0:0: CD-ROM            ASUS     DRW-1608P2       1.17 PQ: 0 ANSI: 5
[    4.910496] scsi 1:0:1:0: CD-ROM            ASUS     DVD-E616P        1.04 PQ: 0 ANSI: 5
[    4.911111] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[    4.911191] ohci1394 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 21 (level, high) -> IRQ 21
[    4.911290] ohci1394 0000:00:0d.0: setting latency timer to 64
[    4.963043] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[dd084000-dd0847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.973522] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    4.973612] skge 0000:01:04.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[    4.973755] skge 1.13 addr 0xdc000000 irq 17 chip Yukon-Lite rev 9
[    4.974214] skge eth1: addr 00:13:d4:46:82:5d
[    4.976423] sata_sil 0000:01:0b.0: version 2.3
[    4.976723] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    4.976811] sata_sil 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[    4.982562] scsi2 : sata_sil
[    4.984549] scsi3 : sata_sil
[    4.984711] ata3: SATA max UDMA/100 mmio m512@0xdc004000 tf 0xdc004080 irq 18
[    4.984792] ata4: SATA max UDMA/100 mmio m512@0xdc004000 tf 0xdc0040c0 irq 18
[    5.304044] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.312543] ata3.00: ATA-7: WDC WD1600JS-00MHB0, 02.01C03, max UDMA/133
[    5.312622] ata3.00: 312581808 sectors, multi 16: LBA48 
[    5.320528] ata3.00: configured for UDMA/100
[    5.640027] ata4: SATA link down (SStatus 0 SControl 310)
[    5.640255] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JS-00M 02.0 PQ: 0 ANSI: 5
[    5.662617] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    5.662744] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.662874] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    5.662992] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    5.663113] scsi 2:0:0:0: Attached scsi generic sg4 type 0
[    5.712384] Driver 'sr' needs updating - please use bus_type methods
[    5.715318] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    5.715404] Uniform CD-ROM driver Revision: 3.20
[    5.715597] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.717509] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    5.717658] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    5.736984] sr2: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    5.737192] sr 1:0:0:0: Attached scsi CD-ROM sr2
[    5.737733] Driver 'sd' needs updating - please use bus_type methods
[    5.741069] sr3: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.741274] sr 1:0:1:0: Attached scsi CD-ROM sr3
[    5.741407] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.741506] sd 2:0:0:0: [sda] Write Protect is off
[    5.741582] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.741618] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.741785] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.741881] sd 2:0:0:0: [sda] Write Protect is off
[    5.741956] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.741991] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.742091]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    5.796249] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.964029] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    6.082456] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[    6.211194] PM: Starting manual resume from disk
[    6.211271] PM: Resume from partition 8:5
[    6.211273] PM: Checking hibernation image.
[    6.211451] PM: Resume from disk failed.
[    6.236949] usb 2-1: configuration #1 chosen from 1 choice
[    6.266914] kjournald starting.  Commit interval 5 seconds
[    6.267018] EXT3-fs: mounted filesystem with ordered data mode.
[    6.352222] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000464d4d]
[    6.544032] usb 2-2: new full speed USB device using ohci_hcd and address 3
[    6.753878] usb 2-2: configuration #1 chosen from 1 choice
[    7.060032] usb 2-3: new low speed USB device using ohci_hcd and address 4
[    7.274813] usb 2-3: configuration #1 chosen from 1 choice
[    7.580017] usb 1-2: new low speed USB device using ohci_hcd and address 4
[    7.795834] usb 1-2: configuration #1 chosen from 1 choice
[   13.409464] udevd version 124 started
[   14.343748] Linux agpgart interface v0.103
[   14.409770] agpgart: Detected NVIDIA nForce2 chipset
[   14.556567] agpgart-nvidia 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   14.556817] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   14.556941] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   14.623218] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[   14.632040] ACPI: Power Button (FF) [PWRF]
[   14.632278] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[   14.648035] ACPI: Power Button (CM) [PWRB]
[   14.974028] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.023053] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.422380] parport_pc 00:0c: reported by Plug and Play ACPI
[   15.422524] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.729294] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   16.729379] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 20 (level, high) -> IRQ 20
[   16.729498] Intel ICH 0000:00:06.0: setting latency timer to 64
[   17.052023] intel8x0_measure_ac97_clock: measured 52749 usecs
[   17.052106] intel8x0: clocking to 47474
[   17.371627] usbcore: registered new interface driver hiddev
[   17.378758] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:02.1/usb2/2-3/2-3:1.0/input/input3
[   17.388367] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:02.1-3
[   17.395846] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input4
[   17.404272] input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-2
[   17.417566] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input5
[   17.428270] input,hidraw2: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:02.0-2
[   17.428598] usbcore: registered new interface driver usbhid
[   17.428694] usbhid: v2.6:USB HID core driver
[   17.514087] Linux video capture interface: v2.00
[   17.553261] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[   17.936310] BUG: unable to handle kernel NULL pointer dereference at 00000000
[   17.936493] IP: [<c037d695>] __mutex_lock_slowpath+0x35/0xb0
[   17.936623] *pde = 00000000 
[   17.936745] Oops: 0002 [#1] SMP 
[   17.936915] Modules linked in: sn9c102(+) videodev v4l1_compat speedtch(+) usbatm usbhid hid snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi parport_pc parport snd_seq_midi_event snd_seq snd_timer snd_seq_device shpchp pci_hotplug snd soundcore snd_page_alloc button i2c_nforce2 i2c_core nvidia_agp agpgart ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg ata_generic pata_acpi sata_sil pata_amd ohci1394 libata skge ieee1394 scsi_mod dock ehci_hcd ohci_hcd forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   17.940008] 
[   17.940008] Pid: 3375, comm: modprobe Not tainted (2.6.27-9-generic #1)
[   17.940008] EIP: 0060:[<c037d695>] EFLAGS: 00010246 CPU: 0
[   17.940008] EIP is at __mutex_lock_slowpath+0x35/0xb0
[   17.940008] EAX: f7b23c80 EBX: f7a1c46c ECX: f7a1c474 EDX: 00000000
[   17.940008] ESI: f7a1c470 EDI: 00000000 EBP: f7b23c98 ESP: f7b23c78
[   17.940008]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   17.940008] Process modprobe (pid: 3375, ti=f7b22000 task=f7aa3240 task.ti=f7b22000)
[   17.940008] Stack: f7aa3240 f7a1c474 f7a1c474 f6e54150 f6e540a4 f7a1c46c f7a1c400 00000000 
[   17.940008]        f7b23ca4 c037d4ec f78b9400 f7b23cc4 f8ab1074 f78b9400 f7a1c46c f78d3000 
[   17.940008]        f78b9400 f78b941c 00000000 f7b23ce0 f88b1880 f8b0d320 f78d3000 f78b9494 
[   17.940008] Call Trace:
[   17.940008]  [<c037d4ec>] ? mutex_lock+0x1c/0x20
[   17.940008]  [<f8ab1074>] ? usbatm_usb_disconnect+0x34/0x230 [usbatm]
[   17.940008]  [<f88b1880>] ? usb_unbind_interface+0x50/0xf0 [usbcore]
[   17.940008]  [<c02c3a19>] ? __device_release_driver+0x79/0xc0
[   17.940008]  [<c02c3b38>] ? device_release_driver+0x28/0x40
[   17.940008]  [<f88b19af>] ? usb_driver_release_interface+0x8f/0xa0 [usbcore]
[   17.940008]  [<f88b1a5b>] ? usb_forced_unbind_intf+0x1b/0x30 [usbcore]
[   17.940008]  [<f88a9f24>] ? usb_reset_device+0xa4/0x160 [usbcore]
[   17.940008]  [<f8b0b528>] ? speedtch_bind+0x398/0x5e0 [speedtch]
[   17.940008]  [<f8b0b190>] ? speedtch_bind+0x0/0x5e0 [speedtch]
[   17.940008]  [<f8ab29cd>] ? usbatm_usb_probe+0x11d/0x874 [usbatm]
[   17.940008]  [<c01c7075>] ? iput+0x25/0x60
[   17.940008]  [<c02001b8>] ? sysfs_add_one+0x18/0x50
[   17.940008]  [<c037d4e0>] ? mutex_lock+0x10/0x20
[   17.940008]  [<c037d488>] ? mutex_unlock+0x8/0x20
[   17.940008]  [<f88b0e19>] ? usb_autopm_do_device+0x69/0xf0 [usbcore]
[   17.940008]  [<f8b0a012>] ? speedtch_usb_probe+0x12/0x20 [speedtch]
[   17.940008]  [<f88b14e7>] ? usb_probe_interface+0xa7/0x140 [usbcore]
[   17.940008]  [<c0201107>] ? sysfs_create_link+0x17/0x20
[   17.940008]  [<c02c3d4e>] ? really_probe+0xee/0x190
[   17.940008]  [<f88b08a9>] ? usb_match_id+0x49/0x60 [usbcore]
[   17.940008]  [<c02c3e33>] ? driver_probe_device+0x43/0x60
[   17.940008]  [<c02c3ec9>] ? __driver_attach+0x79/0x80
[   17.940008]  [<c02c3593>] ? bus_for_each_dev+0x53/0x80
[   17.940008]  [<c02c3b6e>] ? driver_attach+0x1e/0x20
[   17.940008]  [<c02c3e50>] ? __driver_attach+0x0/0x80
[   17.940008]  [<c02c2f37>] ? bus_add_driver+0x1b7/0x230
[   17.940008]  [<c02c409e>] ? driver_register+0x6e/0x150
[   17.940008]  [<c012a571>] ? hrtick_start_fair+0x181/0x1a0
[   17.940008]  [<f88b17bc>] ? usb_register_driver+0x7c/0xf0 [usbcore]
[   17.940008]  [<f8856000>] ? speedtch_usb_init+0x0/0x1e [speedtch]
[   17.940008]  [<f885601c>] ? speedtch_usb_init+0x1c/0x1e [speedtch]
[   17.940008]  [<c0101120>] ? _stext+0x30/0x160
[   17.940008]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[   17.940008]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[   17.940008]  [<c015c208>] ? sys_init_module+0x88/0x1b0
[   17.940008]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[   17.940008]  =======================
[   17.940008] Code: 32 7c d8 ff 89 c3 8d 73 04 64 a1 00 c0 50 c0 89 45 e0 89 f0 e8 4d 10 00 00 8b 53 0c 8d 45 e8 8d 4b 08 89 4d e4 89 43 0c 89 4d e8 <89> 02 8b 45 e0 89 55 ec ba ff ff ff ff 89 45 f0 89 d0 87 03 83 
[   17.940008] EIP: [<c037d695>] __mutex_lock_slowpath+0x35/0xb0 SS:ESP 0068:f7b23c78
[   17.954184] ---[ end trace bb75a82338ed2409 ]---
[   18.298689] input: PC Speaker as /devices/platform/pcspkr/input/input6

/* ---- Here is the 3 minutes tilt, and then, a "Fail" appear ---- */

[  194.276396] loop: module loaded
[  194.320386] lp0: using parport0 (interrupt-driven).
[  194.753471] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[  195.096945] EXT3 FS on sda3, internal journal
[  196.092277] type=1505 audit(1232925506.903:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=12708
[  196.335314] type=1505 audit(1232925507.143:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=12713
[  196.335676] type=1505 audit(1232925507.143:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=12713
[  196.473618] ip_tables: (C) 2000-2006 Netfilter Core Team
[  197.004156] NET: Registered protocol family 10
[  197.004678] lo: Disabled Privacy Extensions
[  197.164534] warning: `ntpd' uses 32-bit capabilities (legacy support in use)
[  197.943683] ACPI: WMI: Mapper loaded
[  199.266357] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  199.266362] apm: overridden by ACPI.
[  199.417328] ppdev: user-space parallel port driver
[  206.964579] skge eth1: enabling interface
[  206.968176] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  206.970685] eth0: no link during initialization.
[  206.971223] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  217.981072] PPP generic driver version 2.4.2
[  218.017498] NET: Registered protocol family 17
```

Look at 18.298689

---

### Post by LecJackS on 2009-02-02
No problem with kernel 2.6.27-11 ;D!


Solved.

---


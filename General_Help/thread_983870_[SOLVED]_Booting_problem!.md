---
title: "[SOLVED] Booting problem!"
date: 2008-11-16
forum: General Help
---

### Post by Zalbor on 2008-11-16
I have two computers, and I've installed kubuntu 8.10 on both. One is a desktop and the other a laptop (Acer aspire 5920G).

On the laptop, booting rarely works as it's supposed to. Usually no splash screen appears, and once in a while it will start beeping without cease when booting.

Are there any solutions for this?

---

### Post by mgol on 2008-11-16
In GRUB selection menu (it may be hidden, You should then see a screen saying that You should press Esc to enter menu - do it) select the second option - this marked as 'recovery mode'. Then You should get the exact information about the error, post it here.

---

### Post by Zalbor on 2008-11-16
Thanks for the reply!

I tried recovery mode, but (just like when booting normally) the text moves too fast to read. As far as I managed, though, I didn't see anything like an error.

Is there some way to output that text into a file, maybe?

---

### Post by Peter09 on 2008-11-16
You can see your boot log by typing at the terminal

```
dmesg|more
```

---

### Post by Zalbor on 2008-11-16
I did look at dmesg, but it doesn't look like the text that appears when booting. If you think it can be helpful however, here:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee1000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37823000 - 37feff94
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7B50, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7FED387D, 007C (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDDC2A, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED4C20, 8F96 (r2 INTEL  CRESTLNE  6040000 MSFT  3000001)
[    0.000000] ACPI: FACS 7FEE0FC0, 0040
[    0.000000] ACPI: APIC 7FEDDD1E, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FEDDD86, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDDDBE, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 7FEDDDFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDDE62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7FEDDE8A, 0176 (r1 ACRSYS ACRPRDCT  6040000 acer        0)
[    0.000000] ACPI: SSDT 7FED4943, 02DD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED3E85, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED3DDF, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FED38F9, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [0037823000 - 0037feff94]          RAMDISK ==> [0037823000 - 0037feff94]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7b80] 000f7b80
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523887
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292018 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
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
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519281
[    0.000000] Kernel command line: root=UUID=e03c650a-44de-4c28-b93c-b7b1eb162d27 ro splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2200.044 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062432k/2095936k available (2572k kernel code, 32248k reserved, 1160k data, 424k init, 1178432k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.08 BogoMIPS (lpj=8800176)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017628] ACPI: Core revision 20080609
[    0.020736] ACPI: Checking initramfs for custom DSDT
[    0.303811] ENABLING IO-APIC IRQs
[    0.304019] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.344111] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[    0.348021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4400.15 BogoMIPS (lpj=8800319)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.432654] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[    0.433233] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436050] Brought up 2 CPUs
[    0.436114] Total of 2 processors activated (8800.24 BogoMIPS).
[    0.436201] CPU0 attaching sched-domain:
[    0.436204]  domain 0: span 0-1 level MC
[    0.436206]   groups: 0 1
[    0.436212] CPU1 attaching sched-domain:
[    0.436214]  domain 0: span 0-1 level MC
[    0.436216]   groups: 1 0
[    0.436287] net_namespace: 840 bytes
[    0.436287] Booting paravirtualized kernel on bare hardware
[    0.436390] Time: 16:37:10  Date: 11/16/08
[    0.436477] NET: Registered protocol family 16
[    0.436559] EISA bus registered
[    0.436559] ACPI: bus type pci registered
[    0.436559] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.436559] PCI: MCFG area at e0000000 reserved in E820
[    0.436559] PCI: Using MMCONFIG for extended config space
[    0.436559] PCI: Using configuration type 1 for base access
[    0.441042] ACPI: EC: Look up EC in DSDT
[    0.445228] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.446453] ACPI: Interpreter enabled
[    0.446522] ACPI: (supports S0 S3 S4 S5)
[    0.446806] ACPI: Using IOAPIC for interrupt routing
[    0.446928] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.960035] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.332376] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    1.332376] ACPI: EC: driver started in poll mode
[    1.332376] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.332376] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.332376] pci 0000:00:01.0: PME# disabled
[    1.332376] PCI: 0000:00:1a.0 reg 20 io port: [1800, 181f]
[    1.332410] PCI: 0000:00:1a.1 reg 20 io port: [1820, 183f]
[    1.332488] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f3504800, f3504bff]
[    1.332556] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    1.332627] pci 0000:00:1a.7: PME# disabled
[    1.332735] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f3500000, f3503fff]
[    1.332789] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.332861] pci 0000:00:1b.0: PME# disabled
[    1.332990] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.333061] pci 0000:00:1c.0: PME# disabled
[    1.333195] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.333265] pci 0000:00:1c.3: PME# disabled
[    1.333395] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    1.333465] pci 0000:00:1c.5: PME# disabled
[    1.336089] PCI: 0000:00:1d.0 reg 20 io port: [1840, 185f]
[    1.336170] PCI: 0000:00:1d.1 reg 20 io port: [1860, 187f]
[    1.336244] PCI: 0000:00:1d.2 reg 20 io port: [1880, 189f]
[    1.336320] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f3504c00, f3504fff]
[    1.336384] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.336454] pci 0000:00:1d.7: PME# disabled
[    1.336667] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    1.336750] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    1.336847] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    1.336856] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    1.336865] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    1.336874] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    1.336883] PCI: 0000:00:1f.1 reg 20 io port: [18a0, 18af]
[    1.336954] PCI: 0000:00:1f.2 reg 10 io port: [18d8, 18df]
[    1.336961] PCI: 0000:00:1f.2 reg 14 io port: [18cc, 18cf]
[    1.336969] PCI: 0000:00:1f.2 reg 18 io port: [18d0, 18d7]
[    1.336976] PCI: 0000:00:1f.2 reg 1c io port: [18c8, 18cb]
[    1.336984] PCI: 0000:00:1f.2 reg 20 io port: [18e0, 18ff]
[    1.336991] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f3504000, f35047ff]
[    1.337021] pci 0000:00:1f.2: PME# supported from D3hot
[    1.337091] pci 0000:00:1f.2: PME# disabled
[    1.337174] PCI: 0000:00:1f.3 reg 10 32bit mmio: [0, ff]
[    1.337198] PCI: 0000:00:1f.3 reg 20 io port: [1c00, 1c1f]
[    1.337273] PCI: 0000:01:00.0 reg 10 32bit mmio: [f2000000, f2ffffff]
[    1.337283] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    1.337307] PCI: 0000:01:00.0 reg 1c 64bit mmio: [f0000000, f1ffffff]
[    1.337316] PCI: 0000:01:00.0 reg 24 io port: [2000, 207f]
[    1.337325] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    1.337397] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    1.337400] PCI: bridge 0000:00:01.0 32bit mmio: [f0000000, f2ffffff]
[    1.337404] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    1.337460] PCI: bridge 0000:00:1c.0 io port: [0, fff]
[    1.337465] PCI: bridge 0000:00:1c.0 32bit mmio: [0, fffff]
[    1.337472] PCI: bridge 0000:00:1c.0 64bit mmio pref: [0, fffff]
[    1.337585] PCI: 0000:06:00.0 reg 10 64bit mmio: [0, 1fff]
[    1.337696] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    1.337792] pci 0000:06:00.0: PME# disabled
[    1.337902] PCI: bridge 0000:00:1c.3 io port: [0, fff]
[    1.337907] PCI: bridge 0000:00:1c.3 32bit mmio: [0, fffff]
[    1.337914] PCI: bridge 0000:00:1c.3 64bit mmio pref: [0, fffff]
[    1.338135] PCI: 0000:08:00.0 reg 10 64bit mmio: [0, ffff]
[    1.338286] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    1.338375] pci 0000:08:00.0: PME# disabled
[    1.338485] PCI: bridge 0000:00:1c.5 io port: [0, fff]
[    1.338489] PCI: bridge 0000:00:1c.5 32bit mmio: [0, fffff]
[    1.338497] PCI: bridge 0000:00:1c.5 64bit mmio pref: [0, fffff]
[    1.338562] PCI: 0000:0a:09.0 reg 10 32bit mmio: [f3200000, f32007ff]
[    1.338626] pci 0000:0a:09.0: supports D1
[    1.338628] pci 0000:0a:09.0: supports D2
[    1.338629] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.338701] pci 0000:0a:09.0: PME# disabled
[    1.338805] PCI: 0000:0a:09.1 reg 10 32bit mmio: [f3200800, f32008ff]
[    1.338870] pci 0000:0a:09.1: supports D1
[    1.338871] pci 0000:0a:09.1: supports D2
[    1.338873] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.338945] pci 0000:0a:09.1: PME# disabled
[    1.339048] PCI: 0000:0a:09.2 reg 10 32bit mmio: [f3200c00, f3200cff]
[    1.339106] pci 0000:0a:09.2: supports D1
[    1.339108] pci 0000:0a:09.2: supports D2
[    1.339110] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.339181] pci 0000:0a:09.2: PME# disabled
[    1.340071] PCI: 0000:0a:09.3 reg 10 32bit mmio: [f3201000, f32010ff]
[    1.340131] pci 0000:0a:09.3: supports D1
[    1.340133] pci 0000:0a:09.3: supports D2
[    1.340134] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.340207] pci 0000:0a:09.3: PME# disabled
[    1.340312] PCI: 0000:0a:09.4 reg 10 32bit mmio: [f3201400, f32014ff]
[    1.340378] pci 0000:0a:09.4: supports D1
[    1.340379] pci 0000:0a:09.4: supports D2
[    1.340381] pci 0000:0a:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    1.340454] pci 0000:0a:09.4: PME# disabled
[    1.340565] pci 0000:00:1e.0: transparent bridge
[    1.340638] PCI: bridge 0000:00:1e.0 32bit mmio: [f3200000, f32fffff]
[    1.340672] bus 00 -> node 0
[    1.340678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.341107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    1.341262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.341410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.341554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.341715] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.352760] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.356674] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.357521] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.358306] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.359159] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.360093] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.360880] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.361728] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    1.362463] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.362463] pnp: PnP ACPI init
[    1.362463] ACPI: bus type pnp registered
[    1.364356] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364356] pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364356] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364356] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364383] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364464] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364545] pnp 00:06: io resource (0x68-0x6f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364628] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364712] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364795] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364876] pnp 00:06: io resource (0x680-0x69f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.364959] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    1.365044] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365125] pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365207] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365289] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365371] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365453] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365535] pnp 00:06: io resource (0x68-0x6f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365618] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365700] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365781] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365864] pnp 00:06: io resource (0x680-0x69f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.365948] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.3 BAR 7 (0x0-0xfff), disabling
[    1.366032] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366114] pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366196] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366278] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366361] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366444] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366526] pnp 00:06: io resource (0x68-0x6f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366608] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366691] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366773] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366855] pnp 00:06: io resource (0x680-0x69f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.366938] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.5 BAR 7 (0x0-0xfff), disabling
[    1.368264] pnp: PnP ACPI: found 11 devices
[    1.368264] ACPI: ACPI bus type pnp unregistered
[    1.368264] PnPBIOS: Disabled by ACPI PNP
[    1.368324] PCI: Using ACPI for IRQ routing
[    1.368324] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    1.368324] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    1.368324] pci 0000:00:1c.0: BAR 9: can't allocate resource
[    1.368324] pci 0000:00:1c.3: BAR 7: can't allocate resource
[    1.368375] pci 0000:00:1c.3: BAR 8: can't allocate resource
[    1.368443] pci 0000:00:1c.3: BAR 9: can't allocate resource
[    1.368511] pci 0000:00:1c.5: BAR 7: can't allocate resource
[    1.368578] pci 0000:00:1c.5: BAR 8: can't allocate resource
[    1.368647] pci 0000:00:1c.5: BAR 9: can't allocate resource
[    1.376039] NET: Registered protocol family 8
[    1.376107] NET: Registered protocol family 20
[    1.376184] NetLabel: Initializing
[    1.376184] NetLabel:  domain hash size = 128
[    1.376184] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.376255] NetLabel:  unlabeled traffic allowed by default
[    1.376328] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.376596] hpet0: 3 64-bit timers, 14318180 Hz
[    1.378101] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.378170]    actual entries 65620
[    1.378313] AppArmor: AppArmor Filesystem Enabled
[    1.378402] ACPI: RTC can wake from S4
[    1.380039] Switched to high resolution mode on CPU 0
[    1.381369] Switched to high resolution mode on CPU 1
[    1.384018] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    1.384099] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    1.384179] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    1.384260] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    1.384341] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    1.384423] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    1.384504] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[    1.384585] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    1.384670] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    1.384753] system 00:06: ioport range 0x1000-0x107f has been reserved
[    1.384822] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    1.384892] system 00:06: ioport range 0x1640-0x164f has been reserved
[    1.384961] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    1.420081] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    1.420162] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.420230] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    1.420299] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf2ffffff
[    1.420369] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.420452] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.420520] pci 0000:00:1c.0:   IO window: disabled
[    1.420591] pci 0000:00:1c.0:   MEM window: disabled
[    1.420661] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.420767] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    1.420835] pci 0000:00:1c.3:   IO window: disabled
[    1.420905] pci 0000:00:1c.3:   MEM window: 0x88000000-0x880fffff
[    1.420975] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.421104] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    1.421173] pci 0000:00:1c.5:   IO window: disabled
[    1.421244] pci 0000:00:1c.5:   MEM window: 0x88100000-0x881fffff
[    1.421315] pci 0000:00:1c.5:   PREFETCH window: disabled
[    1.421389] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.421455] pci 0000:00:1e.0:   IO window: disabled
[    1.421526] pci 0000:00:1e.0:   MEM window: 0xf3200000-0xf32fffff
[    1.421597] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.421678] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.423372] pci 0000:00:01.0: setting latency timer to 64
[    1.423381] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.423455] pci 0000:00:1c.0: setting latency timer to 64
[    1.423463] pci 0000:00:1c.3: enabling device (0000 -> 0002)
[    1.423532] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.423605] pci 0000:00:1c.3: setting latency timer to 64
[    1.423613] pci 0000:00:1c.5: enabling device (0000 -> 0002)
[    1.423683] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.423756] pci 0000:00:1c.5: setting latency timer to 64
[    1.423764] pci 0000:00:1e.0: setting latency timer to 64
[    1.423768] bus: 00 index 0 io port: [0, ffff]
[    1.423835] bus: 00 index 1 mmio: [0, ffffffff]
[    1.423900] bus: 01 index 0 io port: [2000, 2fff]
[    1.423967] bus: 01 index 1 mmio: [f0000000, f2ffffff]
[    1.424041] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    1.424107] bus: 01 index 3 mmio: [0, 0]
[    1.424173] bus: 02 index 0 mmio: [0, fff]
[    1.424238] bus: 02 index 1 mmio: [0, fffff]
[    1.424303] bus: 02 index 2 mmio: [0, fffff]
[    1.424369] bus: 02 index 3 mmio: [0, 0]
[    1.424435] bus: 06 index 0 mmio: [0, fff]
[    1.424501] bus: 06 index 1 mmio: [88000000, 880fffff]
[    1.424569] bus: 06 index 2 mmio: [0, fffff]
[    1.424634] bus: 06 index 3 mmio: [0, 0]
[    1.424700] bus: 08 index 0 mmio: [0, fff]
[    1.424765] bus: 08 index 1 mmio: [88100000, 881fffff]
[    1.424833] bus: 08 index 2 mmio: [0, fffff]
[    1.424898] bus: 08 index 3 mmio: [0, 0]
[    1.424963] bus: 0a index 0 mmio: [0, 0]
[    1.425029] bus: 0a index 1 mmio: [f3200000, f32fffff]
[    1.425096] bus: 0a index 2 mmio: [0, 0]
[    1.425163] bus: 0a index 3 io port: [0, ffff]
[    1.425229] bus: 0a index 4 mmio: [0, ffffffff]
[    1.425300] NET: Registered protocol family 2
[    1.440044] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.440314] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.440698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.440915] TCP: Hash tables configured (established 131072 bind 65536)
[    1.440985] TCP reno registered
[    1.448053] NET: Registered protocol family 1
[    1.448213] checking if image is initramfs... it is
[    2.069787] Freeing initrd memory: 7987k freed
[    2.070026] Simple Boot Flag at 0x35 set to 0x1
[    2.070957] audit: initializing netlink socket (disabled)
[    2.071045] type=2000 audit(1226853432.068:1): initialized
[    2.076438] highmem bounce pool size: 64 pages
[    2.076510] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.078657] VFS: Disk quotas dquot_6.5.1
[    2.078797] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.078958] msgmni has been set to 1743
[    2.079127] io scheduler noop registered
[    2.079193] io scheduler anticipatory registered
[    2.079259] io scheduler deadline registered
[    2.079334] io scheduler cfq registered (default)
[    2.079574] pci 0000:01:00.0: Boot video device
[    2.079689] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.079725] pcieport-driver 0000:00:01.0: found MSI capability
[    2.079854] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.079888] pci_express 0000:00:01.0:pcie02: allocate port service
[    2.079921] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.080016] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.080127] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.080336] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.080373] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.080407] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.080601] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    2.080703] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.080903] pci_express 0000:00:1c.3:pcie00: allocate port service
[    2.080939] pci_express 0000:00:1c.3:pcie02: allocate port service
[    2.080971] pci_express 0000:00:1c.3:pcie03: allocate port service
[    2.081168] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    2.081276] pcieport-driver 0000:00:1c.5: found MSI capability
[    2.081482] pci_express 0000:00:1c.5:pcie00: allocate port service
[    2.081519] pci_express 0000:00:1c.5:pcie02: allocate port service
[    2.081552] pci_express 0000:00:1c.5:pcie03: allocate port service
[    2.081948] isapnp: Scanning for PnP cards...
[    2.439207] isapnp: No Plug & Play device found
[    2.467940] hpet_resources: 0xfed00000 is busy
[    2.468003] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.470013] brd: module loaded
[    2.470170] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.470390] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.473374] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.474737] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.474842] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.474944] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.475045] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.475146] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.475567] mice: PS/2 mouse device common for all mice
[    2.475776] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.475912] rtc0: alarms up to one month, y3k, hpet irqs
[    2.476125] EISA: Probing bus 0 at eisa.0
[    2.476229] Cannot allocate resource for EISA slot 1
[    2.476329] Cannot allocate resource for EISA slot 2
[    2.476465] EISA: Detected 0 cards.
[    2.476564] cpuidle: using governor ladder
[    2.476662] cpuidle: using governor menu
[    2.477218] TCP cubic registered
[    2.477338] Using IPI No-Shortcut mode
[    2.477583] registered taskstats version 1
[    2.477793]   Magic number: 0:511:641
[    2.477969] rtc_cmos 00:07: setting system clock to 2008-11-16 16:37:13 UTC (1226853433)
[    2.478083] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.478183] EDD information not available.
[    2.478502] Freeing unused kernel memory: 424k freed
[    2.478631] Write protecting the kernel text: 2576k
[    2.478759] Write protecting the kernel read-only data: 936k
[    2.513254] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.580320] fuse init (API version 7.9)
[    2.621445] ACPI: SSDT 7FED4601, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.622173] ACPI: SSDT 7FED40E4, 0498 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.624853] Monitor-Mwait will be used to enter C-1 state
[    2.624855] Monitor-Mwait will be used to enter C-2 state
[    2.624857] Monitor-Mwait will be used to enter C-3 state
[    2.625064] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.625529] processor ACPI0007:00: registered as cooling_device0
[    2.625620] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.626207] ACPI: SSDT 7FED487B, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.626845] ACPI: SSDT 7FED457C, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.628313] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.628770] processor ACPI0007:01: registered as cooling_device1
[    2.628864] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.631016] Marking TSC unstable due to TSC halts in idle
[    2.772655] thermal LNXTHERM:01: registered as thermal_zone0
[    2.916346] ACPI: Thermal Zone [THRM] (52 C)
[    3.001026] Clocksource tsc unstable (delta = -270571954 ns)
[    3.137540] usbcore: registered new interface driver usbfs
[    3.137656] usbcore: registered new interface driver hub
[    3.143875] usbcore: registered new device driver usb
[    3.147855] USB Universal Host Controller Interface driver v3.0
[    3.147996] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.148123] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.148129] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.148265] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.148421] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.148645] usb usb1: configuration #1 chosen from 1 choice
[    3.148768] hub 1-0:1.0: USB hub found
[    3.148867] hub 1-0:1.0: 2 ports detected
[    3.244222] No dock devices found.
[    3.264187] SCSI subsystem initialized
[    3.285159] libata version 3.00 loaded.
[    3.360327] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.360444] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.360450] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.360571] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.360732] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    3.360917] usb usb2: configuration #1 chosen from 1 choice
[    3.361041] hub 2-0:1.0: USB hub found
[    3.361150] hub 2-0:1.0: 2 ports detected
[    3.469042] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.568706] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.568826] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.568831] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.568947] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    3.572975] ehci_hcd 0000:00:1a.7: debug port 1
[    3.573111] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.573125] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3504800
[    3.596248] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.596469] usb usb3: configuration #1 chosen from 1 choice
[    3.596592] hub 3-0:1.0: USB hub found
[    3.596691] hub 3-0:1.0: 4 ports detected
[    3.804611] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.804724] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.804730] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.804847] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    3.804997] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    3.805166] usb usb4: configuration #1 chosen from 1 choice
[    3.805288] hub 4-0:1.0: USB hub found
[    3.805387] hub 4-0:1.0: 2 ports detected
[    4.001151] usb 1-2: device not accepting address 2, error -71
[    4.012423] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.012537] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.012543] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.012663] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    4.012811] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    4.012980] usb usb5: configuration #1 chosen from 1 choice
[    4.013102] hub 5-0:1.0: USB hub found
[    4.013203] hub 5-0:1.0: 2 ports detected
[    4.056195] hub 1-0:1.0: unable to enumerate USB device on port 2
[    4.220400] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.220516] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.220521] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.220637] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    4.220781] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    4.220952] usb usb6: configuration #1 chosen from 1 choice
[    4.221069] hub 6-0:1.0: USB hub found
[    4.221167] hub 6-0:1.0: 2 ports detected
[    4.296174] usb 3-2: new high speed USB device using ehci_hcd and address 2
[    4.324688] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.324790] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.324794] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.324905] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.328911] ehci_hcd 0000:00:1d.7: debug port 1
[    4.329009] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.329014] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3504c00
[    4.420103] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.420337] usb usb7: configuration #1 chosen from 1 choice
[    4.420442] hub 7-0:1.0: USB hub found
[    4.420534] hub 7-0:1.0: 6 ports detected
[    4.437654] usb 3-2: configuration #1 chosen from 1 choice
[    4.548184] usb 3-3: new high speed USB device using ehci_hcd and address 3
[    4.629861] ahci 0000:00:1f.2: version 3.0
[    4.629880] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.630112] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    4.630223] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    4.630340] ahci 0000:00:1f.2: setting latency timer to 64
[    4.630928] scsi0 : ahci
[    4.631150] scsi1 : ahci
[    4.631344] scsi2 : ahci
[    4.631537] ata1: SATA max UDMA/133 abar m2048@0xf3504000 port 0xf3504100 irq 219
[    4.631647] ata2: DUMMY
[    4.631743] ata3: DUMMY
[    4.683343] usb 3-3: configuration #1 chosen from 1 choice
[    4.948167] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.949380] ata1.00: _GTF unexpected object type 0x1
[    4.949670] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    4.949779] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.952098] ata1.00: _GTF unexpected object type 0x1
[    4.952442] ata1.00: configured for UDMA/133
[    4.968367] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    4.968638] tg3.c:v3.94 (August 14, 2008)
[    4.968796] tg3 0000:08:00.0: enabling device (0000 -> 0002)
[    4.968897] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.969018] tg3 0000:08:00.0: setting latency timer to 64
[    4.969289] ohci1394 0000:0a:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.017510] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:24:b4:a7:3f
[    5.017626] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    5.017739] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.022104] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f3200000-f32007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.030895] ata_piix 0000:00:1f.1: version 2.12
[    5.030905] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.031047] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.031762] scsi3 : ata_piix
[    5.031940] scsi4 : ata_piix
[    5.032743] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    5.032846] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    5.057046] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.074595] Driver 'sd' needs updating - please use bus_type methods
[    5.074828] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.074961] sd 0:0:0:0: [sda] Write Protect is off
[    5.075060] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.075117] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.075321] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.075455] sd 0:0:0:0: [sda] Write Protect is off
[    5.075550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.075612] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.075728]  sda: sda1 sda2 sda3 < sda5<6>usb 7-3: new high speed USB device using ehci_hcd and address 3
[    5.129377]  sda6 sda7 > sda4
[    5.142342] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.196607] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[    5.212466] ata4.00: configured for UDMA/33
[    5.262603] usb 7-3: configuration #1 chosen from 1 choice
[    5.385115] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    5.385365] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[    5.404700] Driver 'sr' needs updating - please use bus_type methods
[    5.415933] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.416073] Uniform CD-ROM driver Revision: 3.20
[    5.416392] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.500110] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    5.677343] usb 4-2: configuration #1 chosen from 1 choice
[    5.682211] usbcore: registered new interface driver libusual
[    5.690423] Initializing USB Mass Storage driver...
[    5.692649] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.696174] usbcore: registered new interface driver usb-storage
[    5.696281] USB Mass Storage support registered.
[    5.696390] usb-storage: device found at 3
[    5.696392] usb-storage: waiting for device to settle before scanning
[    5.696544] usbcore: registered new interface driver hiddev
[    5.709515] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb4/4-2/4-2:1.0/input/input2
[    5.709851] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[    5.710304] usbcore: registered new interface driver usbhid
[    5.710403] usbhid: v2.6:USB HID core driver
[    5.830318] kjournald starting.  Commit interval 5 seconds
[    5.830370] EXT3-fs: mounted filesystem with ordered data mode.
[    6.296485] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0083806c00]
[   10.692380] usb-storage: device scan complete
[   10.693057] scsi 5:0:0:0: Direct-Access     WDC WD80 0UE-11KVT0       01.0 PQ: 0 ANSI: 0
[   10.694400] sd 5:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   10.695453] sd 5:0:0:0: [sdb] Write Protect is off
[   10.695535] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.695537] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   10.696517] sd 5:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   10.697482] sd 5:0:0:0: [sdb] Write Protect is off
[   10.697564] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.697572] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   10.697652]  sdb: sdb1 sdb3
[   10.698578] sd 5:0:0:0: [sdb] Attached SCSI disk
[   10.698726] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   11.560240] udevd version 124 started
[   11.908677] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.072526] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.107785] Linux agpgart interface v0.103
[   12.185062] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.209038] ACPI: Power Button (FF) [PWRF]
[   12.454873] cfg80211: Using static regulatory domain info
[   12.454979] cfg80211: Regulatory domain: US
[   12.455078] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.455189] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   12.455292] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.455395] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.457160] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.457260] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   12.457360] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   12.457461] cfg80211: Calling CRDA for country: US
[   12.791389] nvidia: module license 'NVIDIA' taints kernel.
[   13.074412] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.074529] nvidia 0000:01:00.0: setting latency timer to 64
[   13.074720] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   13.111383] iTCO_vendor_support: vendor-support=0
[   13.176891] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.176995] ricoh-mmc: Copyright(c) Philip Langdale
[   13.178099] ricoh-mmc: Ricoh MMC controller found at 0000:0a:09.2 [1180:0843] (rev 12)
[   13.178238] ricoh-mmc: Controller is now disabled.
[   13.199619] Linux video capture interface: v2.00
[   13.213923] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.229893] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.285252] ACPI: Battery Slot [BAT1] (battery present)
[   13.285680] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   13.314308] ACPI: Lid Switch [LID]
[   13.314513] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   13.362318] ACPI: Power Button (CM) [PWRB]
[   13.362579] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   13.369153] sdhci: Secure Digital Host Controller Interface driver
[   13.369256] sdhci: Copyright(c) Pierre Ossman
[   13.372291] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 22)
[   13.372443] sdhci-pci 0000:0a:09.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.373568] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.375751] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[   13.412985] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   13.413221] ACPI: Sleep Button (CM) [SLPB]
[   13.420246] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-2/3-2:1.0/input/input8
[   13.445171] usbcore: registered new interface driver uvcvideo
[   13.445267] USB Video Class driver (v0.1.0)
[   13.601157] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.601278] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.603072] iwlagn 0000:06:00.0: enabling device (0000 -> 0002)
[   13.603203] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.603341] iwlagn 0000:06:00.0: setting latency timer to 64
[   13.603389] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.650799] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[   13.653070] iwlagn 0000:06:00.0: PCI INT A disabled
[   13.695164] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.831633] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1e0b1, caps: 0xc04751/0xe0500f
[   13.868525] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input9
[   13.904326] ACPI: AC Adapter [ACAD] (on-line)
[   13.904755] ACPI: WMI: Mapper loaded
[   14.005603] acpi device:04: registered as cooling_device2
[   14.006156] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input10
[   14.007814] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.293726] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.487597] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.487752] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.547692] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   14.586450] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   14.645442] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   14.645620] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.615266] lp: driver loaded but no devices found
[   16.267325] EXT3 FS on sda6, internal journal
[  130.314509] kjournald starting.  Commit interval 5 seconds
[  130.314861] EXT3 FS on sda7, internal journal
[  130.314868] EXT3-fs: mounted filesystem with ordered data mode.
[  132.105265] Adding 786424k swap on /swapfile.  Priority:-1 extents:210 across:940640k
[  132.406054] type=1505 audit(1226846362.944:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4278
[  132.406234] type=1505 audit(1226846362.944:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4278
[  132.649079] ip_tables: (C) 2000-2006 Netfilter Core Team
[  133.981113] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  134.038383] apm: BIOS not found.
[  134.179445] ppdev: user-space parallel port driver
[  138.006028] Bluetooth: Core ver 2.13
[  138.007916] NET: Registered protocol family 31
[  138.007930] Bluetooth: HCI device and connection manager initialized
[  138.007937] Bluetooth: HCI socket layer initialized
[  138.031874] Bluetooth: L2CAP ver 2.11
[  138.031891] Bluetooth: L2CAP socket layer initialized
[  138.095231] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  138.095249] Bluetooth: BNEP filters: protocol multicast
[  138.126263] Bridge firewalling registered
[  138.126572] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  138.153592] Bluetooth: RFCOMM socket layer initialized
[  138.160714] Bluetooth: RFCOMM TTY layer initialized
[  138.160728] Bluetooth: RFCOMM ver 1.10
[  138.161018] Bluetooth: SCO (Voice Link) ver 0.6
[  138.161026] Bluetooth: SCO socket layer initialized
[  142.662126] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  142.662213] iwlagn 0000:06:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[  142.665797] firmware: requesting iwlwifi-4965-2-lbm.ucode
[  142.960493] Registered led device: iwl-phy0:radio
[  142.960547] Registered led device: iwl-phy0:assoc
[  142.960586] Registered led device: iwl-phy0:RX
[  142.960624] Registered led device: iwl-phy0:TX
[  143.124367] NET: Registered protocol family 17
[  143.866128] wlan0: authenticate with AP 00:14:7f:23:f1:67
[  143.867903] wlan0: authenticated
[  143.867912] wlan0: associate with AP 00:14:7f:23:f1:67
[  143.870459] wlan0: RX AssocResp from 00:14:7f:23:f1:67 (capab=0x401 status=0 aid=1)
[  143.870467] wlan0: associated
[  143.898250] wlan0: disassociating by local choice (reason=3)
[  192.496651] wlan0: authenticate with AP 00:c0:49:62:97:6c
[  192.498463] wlan0: authenticated
[  192.498473] wlan0: associate with AP 00:c0:49:62:97:6c
[  192.500934] wlan0: RX AssocResp from 00:c0:49:62:97:6c (capab=0x411 status=0 aid=4)
[  192.500941] wlan0: associated
[  194.620392] padlock: VIA PadLock not detected.
[  298.496144] CE: hpet increasing min_delta_ns to 15000 nsec
[  825.451026] NET: Registered protocol family 10
[  825.454743] lo: Disabled Privacy Extensions
[  825.458294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  835.537023] wlan0: no IPv6 routers present
[ 1005.328814] CE: hpet increasing min_delta_ns to 22500 nsec
```

This time it booted with no splash (my boot options is "splash" without "quiet") but there was no beeping.

---

### Post by Zalbor on 2008-11-19
No ideas?

---

### Post by Zalbor on 2008-11-20
I tried to change kernel edition and see if it changed anything, but linux-image-386 has no restricted modules any more...

---

### Post by chrisvw on 2008-11-23
> **Zalbor said:**
> On the laptop, booting rarely works as it's supposed to. Usually no splash screen appears, and once in a while it will start beeping without cease when booting.

Does the beeping only happen while your laptop is hot? Or does it happen even when cold?

Does the beeping stop after booting?

Your laptop may be overheating. Check your temperatures in the BIOS, if it has such a feature.

---

### Post by Zalbor on 2008-12-19
It seems that this too was a grub issue. I re-added the "quiet" option in menu.lst, and behold: all problems are gone (along with the informative text, unfortunately).

[Grub in intrepid is definitely very buggy...](http://ubuntuforums.org/showthread.php?t=966305)

---


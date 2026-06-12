---
title: "ran memtest 100  cycles where to next to troubleshoot kernel panic?"
date: 2008-10-24
forum: General Help
---

### Post by josephellengar on 2008-10-24
Thanks.  Memtest came up completely clean.  I am in ibex right now.  These kernel panics are getting really annoying.  They are happening more and more frequently and sysrq is not working on my computer.

---

### Post by dcstar on 2008-10-25
> **idigchess said:**
> Thanks.  Memtest came up completely clean.  I am in ibex right now.  These kernel panics are getting really annoying.  They are happening more and more frequently and sysrq is not working on my computer.

Memory is only a small quantity of the components on a PC motherboard. Testing memory does not stress the CPU, the I/O busses or myriad other things that may be the problem.

Monitor all temperatures on your system and try to see if any component if too hot, get a power filter and see if that helps.

---

### Post by ciscosurfer on 2008-10-25
> **idigchess said:**
> Thanks.  Memtest came up completely clean.  I am in ibex right now.  These kernel panics are getting really annoying.  They are happening more and more frequently and sysrq is not working on my computer.What are you system specs?  Did you make any adjustments to your system prior to the kernel panic?  Checking your logs in /var/log might shed some light on your issue (boot with a live cd if you can't get in otherwise).  You can issue dmesg in a terminal; this prints or controls the kernel ring buffer -- it will show your bootup messages```
dmesg
```dmesg is found under /var/log as well.  You may also find [this link]("http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/") helpful.  It's an older page, but the troubleshooting tactics are still quite sound.

---

### Post by josephellengar on 2008-10-25
> **ciscosurfer said:**
> What are you system specs?  Did you make any adjustments to your system prior to the kernel panic?  Checking your logs in /var/log might shed some light on your issue (boot with a live cd if you can't get in otherwise).  You can issue dmesg in a terminal; this prints or controls the kernel ring buffer -- it will show your bootup messages```
dmesg
```dmesg is found under /var/log as well.  You may also find [this link]("http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/") helpful.  It's an older page, but the troubleshooting tactics are still quite sound.

I have attached the specs in the txt file.  (i had to get rid of the list of boots to reach the correct size)  I didnt make any major changes to my computer before th panics started.  In fact, I even upgraded to ibex after the panics began, in an attempt to stop them.  There was no log from one of the panic times.  I had seen that article before, but didn't really get it, which is why I came here.  Any help you could give me would be greatly appreciated.  Thanks!

---

### Post by ciscosurfer on 2008-10-25
idigchess,

Can you post the output of dmesg.  For example, this will provide you with a file you can attach to your next post:```
dmesg > dmesg.kernelpanic
```Now you can look at this file using any number of paging utitlies, search tools, and/or editors, searching for specic words that could aid in the discovery of your problem.  For example, you might do something like this:```
grep panic dmesg.kernelpanic
```This means you want to search for the word "panic" somewhere w/in the file you just created.

You may also want to use the System Log tool provided under **System > Administration > System Log**.  You can then open up the file you created, or open the original under located in the /var/log/ directory.

These will also be helpful:```
man grep
man dmesg
```Btw, any luck with the link I provided you in the my last post?

---

### Post by josephellengar on 2008-10-26
> **ciscosurfer said:**
> idigchess,

Can you post the output of dmesg.  For example, this will provide you with a file you can attach to your next post:```
dmesg > dmesg.kernelpanic
```Now you can look at this file using any number of paging utitlies, search tools, and/or editors, searching for specic words that could aid in the discovery of your problem.  For example, you might do something like this:```
grep panic dmesg.kernelpanic
```This means you want to search for the word "panic" somewhere w/in the file you just created.

You may also want to use the System Log tool provided under **System > Administration > System Log**.  You can then open up the file you created, or open the original under located in the /var/log/ directory.

These will also be helpful:```
man grep
man dmesg
```Btw, any luck with the link I provided you in the my last post?

I pasted the output of dmesg below.  I had to paste it because the file was too large to attach.  I couldn't find panic anywhere in it, but I haven't had a panic for two days, so the log might not go back that far.  I looked in all of the logs mentioned in the link you gave and found nother.  But, thank you very much for all of your help.
EDIT: sory about the smilies.  I guess that's just the way the code worked out in the log.

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=c260499c-b40a-48da-a8be-e88ae8b67d9c ro splash vga=normal 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff15000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff15000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 3ff00000 @ 8000-b000
[    0.000000] last_map_addr: 3ff00000 end: 3ff00000
[    0.000000] RAMDISK: 377c5000 - 37fef3e1
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F88F0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3FF0BD23, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 3FF14D10, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3FF0BD5F, 8FB1 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FF15FC0, 0040
[    0.000000] ACPI: SSDT 3FF14D84, 0182 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 3FF14F06, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 3FF14F42, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 3FF14F7A, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FF14FD8, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [0000000000009000 -  0000000000010fdf] pages 8
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377c5000 - 0037fef3e1]          RAMDISK ==> [00377c5000 - 0037fef3e1]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f8920] 000f8920
[    0.000000]  [ffffe20000000000-ffffe20000ffffff] PMD -> [ffff880001200000-ffff8800021fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003ff00
[    0.000000] On node 0 totalpages: 261789
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 253764 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255873
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=c260499c-b40a-48da-a8be-e88ae8b67d9c ro splash vga=normal 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1607.295 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 1a38000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1015252k/1047552k available (3112k kernel code, 31904k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.59 BogoMIPS (lpj=6429180)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] tseg: 003ff80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004032] ACPI: Core revision 20080609
[    0.006993] ACPI: Checking initramfs for custom DSDT
[    0.444692] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.486001] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.486175] Using local APIC timer interrupts.
[    0.488032] APIC timer calibration result 12556998
[    0.488035] Detected 12.556 MHz APIC timer.
[    0.488300] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3214.63 BogoMIPS (lpj=6429265)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.576207] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.576221] Brought up 2 CPUs
[    0.576223] Total of 2 processors activated (6429.22 BogoMIPS).
[    0.576403] CPU0 attaching sched-domain:
[    0.576406]  domain 0: span 0-1 level CPU
[    0.576409]   groups: 0 1
[    0.576412]   domain 1: span 0-1 level NODE
[    0.576415]    groups: 0-1
[    0.576419] CPU1 attaching sched-domain:
[    0.576421]  domain 0: span 0-1 level CPU
[    0.576423]   groups: 1 0
[    0.576426]   domain 1: span 0-1 level NODE
[    0.576428]    groups: 0-1
[    0.576847] net_namespace: 1552 bytes
[    0.576853] Booting paravirtualized kernel on bare hardware
[    0.577080] Time: 20:23:55  Date: 10/25/08
[    0.577121] NET: Registered protocol family 16
[    0.004000] Switch to broadcast mode on CPU1
[    0.577410] Switch to broadcast mode on CPU0
[    0.577410] node 0 link 0: io port [1000, fffff]
[    0.577410] TOM: 0000000040000000 aka 1024M
[    0.577410] node 0 link 0: mmio [e0000000, efffffff]
[    0.577410] node 0 link 0: mmio [a0000, bffff]
[    0.577410] node 0 link 0: mmio [40000000, fe0bffff]
[    0.577410] bus: [00,ff] on node 0 link 0
[    0.577410] bus: 00 index 0 io port: [0, ffff]
[    0.577410] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.577410] bus: 00 index 2 mmio: [a0000, bffff]
[    0.577410] ACPI: bus type pci registered
[    0.577410] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.577410] PCI: MCFG area at e0000000 reserved in E820
[    0.577410] PCI: Using MMCONFIG at e0000000 - e06fffff
[    0.577410] PCI: Using configuration type 1 for base access
[    0.577410] ACPI: EC: Look up EC in DSDT
[    0.583600] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.584179] ACPI: Interpreter enabled
[    0.584245] ACPI: (supports S0 S3 S4 S5)
[    0.584521] ACPI: Using IOAPIC for interrupt routing
[    0.584711] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.608218] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.608218] ACPI: EC: driver started in interrupt mode
[    0.608315] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.608315] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.608337] pci 0000:00:02.0: PME# disabled
[    0.608418] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.608478] pci 0000:00:03.0: PME# disabled
[    0.608558] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.608618] pci 0000:00:04.0: PME# disabled
[    0.608826] PCI: 0000:00:0a.0 reg 10 io port: [1d00, 1d7f]
[    0.608888] PCI: 0000:00:0a.1 reg 20 io port: [3040, 307f]
[    0.608893] PCI: 0000:00:0a.1 reg 24 io port: [3000, 303f]
[    0.608913] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.608975] pci 0000:00:0a.1: PME# disabled
[    0.609058] PCI: 0000:00:0a.3 reg 10 32bit mmio: [c0040000, c007ffff]
[    0.609096] PCI: 0000:00:0b.0 reg 10 32bit mmio: [c0004000, c0004fff]
[    0.609096] pci 0000:00:0b.0: supports D1
[    0.609096] pci 0000:00:0b.0: supports D2
[    0.609096] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609096] pci 0000:00:0b.0: PME# disabled
[    0.609096] PCI: 0000:00:0b.1 reg 10 32bit mmio: [c0005000, c00050ff]
[    0.609096] pci 0000:00:0b.1: supports D1
[    0.609096] pci 0000:00:0b.1: supports D2
[    0.609096] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609096] pci 0000:00:0b.1: PME# disabled
[    0.609096] PCI: 0000:00:0d.0 reg 20 io port: [3080, 308f]
[    0.609096] PCI: 0000:00:0e.0 reg 10 io port: [30c0, 30c7]
[    0.609096] PCI: 0000:00:0e.0 reg 14 io port: [30b4, 30b7]
[    0.609096] PCI: 0000:00:0e.0 reg 18 io port: [30b8, 30bf]
[    0.609096] PCI: 0000:00:0e.0 reg 1c io port: [30b0, 30b3]
[    0.609096] PCI: 0000:00:0e.0 reg 20 io port: [3090, 309f]
[    0.609096] PCI: 0000:00:0e.0 reg 24 32bit mmio: [c0006000, c0006fff]
[    0.609096] PCI: 0000:00:10.1 reg 10 32bit mmio: [c0000000, c0003fff]
[    0.609096] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.609096] pci 0000:00:10.1: PME# disabled
[    0.609096] PCI: 0000:00:14.0 reg 10 32bit mmio: [c0008000, c0008fff]
[    0.609096] PCI: 0000:00:14.0 reg 14 io port: [30e0, 30e7]
[    0.609096] pci 0000:00:14.0: supports D1
[    0.609096] pci 0000:00:14.0: supports D2
[    0.609096] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609096] pci 0000:00:14.0: PME# disabled
[    0.609096] PCI: bridge 0000:00:02.0 io port: [4000, 4fff]
[    0.609096] PCI: bridge 0000:00:02.0 32bit mmio: [c2000000, c3ffffff]
[    0.609096] PCI: bridge 0000:00:02.0 64bit mmio pref: [c8200000, c83fffff]
[    0.609096] PCI: 0000:03:00.0 reg 10 32bit mmio: [c4000000, c4003fff]
[    0.609124] pci 0000:03:00.0: supports D1
[    0.609126] pci 0000:03:00.0: supports D2
[    0.609162] PCI: bridge 0000:00:03.0 32bit mmio: [c4000000, c5ffffff]
[    0.609187] PCI: 0000:05:00.0 reg 10 32bit mmio: [c7000000, c7ffffff]
[    0.609192] PCI: 0000:05:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.609202] PCI: 0000:05:00.0 reg 1c 64bit mmio: [c6000000, c6ffffff]
[    0.609209] PCI: 0000:05:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.609255] PCI: bridge 0000:00:04.0 32bit mmio: [c6000000, c7ffffff]
[    0.609260] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, dfffffff]
[    0.609293] PCI: 0000:07:05.0 reg 10 32bit mmio: [c8000000, c80007ff]
[    0.609328] pci 0000:07:05.0: supports D1
[    0.609329] pci 0000:07:05.0: supports D2
[    0.609332] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609393] pci 0000:07:05.0: PME# disabled
[    0.609471] PCI: 0000:07:05.1 reg 10 32bit mmio: [c8000800, c80008ff]
[    0.609505] pci 0000:07:05.1: supports D1
[    0.609508] pci 0000:07:05.1: supports D2
[    0.609510] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609571] pci 0000:07:05.1: PME# disabled
[    0.609649] PCI: 0000:07:05.2 reg 10 32bit mmio: [c8000c00, c8000cff]
[    0.609683] pci 0000:07:05.2: supports D1
[    0.609685] pci 0000:07:05.2: supports D2
[    0.609687] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609749] pci 0000:07:05.2: PME# disabled
[    0.609827] PCI: 0000:07:05.3 reg 10 32bit mmio: [c8001000, c80010ff]
[    0.609861] pci 0000:07:05.3: supports D1
[    0.609863] pci 0000:07:05.3: supports D2
[    0.609866] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.609927] pci 0000:07:05.3: PME# disabled
[    0.610005] PCI: 0000:07:05.4 reg 10 32bit mmio: [c8001400, c80014ff]
[    0.610040] pci 0000:07:05.4: supports D1
[    0.610042] pci 0000:07:05.4: supports D2
[    0.610044] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.610106] pci 0000:07:05.4: PME# disabled
[    0.610192] pci 0000:00:10.0: transparent bridge
[    0.610251] PCI: bridge 0000:00:10.0 32bit mmio: [c8000000, c80fffff]
[    0.610271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.610427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.610469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.610520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.610569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.666009] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.666009] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.666009] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.666009] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.667921] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[    0.668445] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.669032] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.669613] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.670193] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.670691] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.671231] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.671771] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.672339] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.672878] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.673459] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.674039] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.674619] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.675211] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.675757] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.680103] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.680162] pnp: PnP ACPI init
[    0.680162] ACPI: bus type pnp registered
[    0.681297] pnp: PnP ACPI: found 13 devices
[    0.681357] ACPI: ACPI bus type pnp unregistered
[    0.684063] PCI: Using ACPI for IRQ routing
[    0.700043] NET: Registered protocol family 8
[    0.700101] NET: Registered protocol family 20
[    0.704075] NetLabel: Initializing
[    0.704130] NetLabel:  domain hash size = 128
[    0.704187] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.704263] NetLabel:  unlabeled traffic allowed by default
[    0.704411] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.704416] hpet0: 3 32-bit timers, 25000000 Hz
[    0.707163] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.707223]    actual entries 65586
[    0.707420] AppArmor: AppArmor Filesystem Enabled
[    0.708070] Switched to high resolution mode on CPU 0
[    0.708084] Switched to high resolution mode on CPU 1
[    0.708101] ACPI: RTC can wake from S4
[    0.721068] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.721144] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.721215] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.721286] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.721358] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.721423] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.721501] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.721561] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.721622] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.721682] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.721742] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.721802] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.721863] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.721928] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.721988] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.722048] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.727846] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.727908] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.727968] pci 0000:00:02.0:   MEM window: 0xc2000000-0xc3ffffff
[    0.728032] pci 0000:00:02.0:   PREFETCH window: 0x000000c8200000-0x000000c83fffff
[    0.728114] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.728173] pci 0000:00:03.0:   IO window: disabled
[    0.728231] pci 0000:00:03.0:   MEM window: 0xc4000000-0xc5ffffff
[    0.728291] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.728354] pci 0000:05:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.728425] pci 0000:00:04.0: PCI bridge, secondary bus 0000:05
[    0.728484] pci 0000:00:04.0:   IO window: disabled
[    0.728542] pci 0000:00:04.0:   MEM window: 0xc6000000-0xc7ffffff
[    0.728602] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.728675] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.728733] pci 0000:00:10.0:   IO window: disabled
[    0.728793] pci 0000:00:10.0:   MEM window: 0xc8000000-0xc80fffff
[    0.728853] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.728921] pci 0000:00:02.0: setting latency timer to 64
[    0.728927] pci 0000:00:03.0: setting latency timer to 64
[    0.728933] pci 0000:00:04.0: setting latency timer to 64
[    0.728939] pci 0000:00:10.0: setting latency timer to 64
[    0.728942] bus: 00 index 0 io port: [0, ffff]
[    0.729000] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.729067] bus: 01 index 0 io port: [4000, 4fff]
[    0.729125] bus: 01 index 1 mmio: [c2000000, c3ffffff]
[    0.729183] bus: 01 index 2 mmio: [c8200000, c83fffff]
[    0.729240] bus: 01 index 3 mmio: [0, 0]
[    0.729296] bus: 03 index 0 mmio: [0, 0]
[    0.729352] bus: 03 index 1 mmio: [c4000000, c5ffffff]
[    0.729410] bus: 03 index 2 mmio: [0, 0]
[    0.729466] bus: 03 index 3 mmio: [0, 0]
[    0.729522] bus: 05 index 0 mmio: [0, 0]
[    0.729578] bus: 05 index 1 mmio: [c6000000, c7ffffff]
[    0.729636] bus: 05 index 2 mmio: [d0000000, dfffffff]
[    0.729694] bus: 05 index 3 mmio: [0, 0]
[    0.729750] bus: 07 index 0 mmio: [0, 0]
[    0.729806] bus: 07 index 1 mmio: [c8000000, c80fffff]
[    0.729863] bus: 07 index 2 mmio: [0, 0]
[    0.729919] bus: 07 index 3 io port: [0, ffff]
[    0.729977] bus: 07 index 4 mmio: [0, ffffffffffffffff]
[    0.730051] NET: Registered protocol family 2
[    0.769147] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.769857] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.771539] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.772309] TCP: Hash tables configured (established 131072 bind 65536)
[    0.772370] TCP reno registered
[    0.781145] NET: Registered protocol family 1
[    0.781349] checking if image is initramfs... it is
[    1.837448] Freeing initrd memory: 8360k freed
[    1.843425] Simple Boot Flag at 0x36 set to 0x1
[    1.844948] audit: initializing netlink socket (disabled)
[    1.845030] type=2000 audit(1224966235.845:1): initialized
[    1.852367] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.855841] VFS: Disk quotas dquot_6.5.1
[    1.856060] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.856269] msgmni has been set to 1999
[    1.856500] io scheduler noop registered
[    1.856558] io scheduler anticipatory registered
[    1.856615] io scheduler deadline registered
[    1.856839] io scheduler cfq registered (default)
[    1.856911] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.857023] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.857090] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.857157] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.857237] pci 0000:00:09.0: Enabling HT MSI Mapping
[    2.076093] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    2.076162] pci 0000:00:10.0: Enabling HT MSI Mapping
[    2.076232] pci 0000:00:10.1: Enabling HT MSI Mapping
[    2.076314] pci 0000:05:00.0: Boot video device
[    2.076500] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.076526] pcieport-driver 0000:00:02.0: found MSI capability
[    2.076611] pci_express 0000:00:02.0:pcie00: allocate port service
[    2.076684] pci_express 0000:00:02.0:pcie03: allocate port service
[    2.076790] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.076814] pcieport-driver 0000:00:03.0: found MSI capability
[    2.076890] pci_express 0000:00:03.0:pcie00: allocate port service
[    2.076956] pci_express 0000:00:03.0:pcie03: allocate port service
[    2.077095] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.077119] pcieport-driver 0000:00:04.0: found MSI capability
[    2.077195] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.077267] pci_express 0000:00:04.0:pcie03: allocate port service
[    2.135196] hpet_resources: 0xfed00000 is busy
[    2.135336] Linux agpgart interface v0.103
[    2.135399] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.139021] brd: module loaded
[    2.139183] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.139445] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.158209] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.158277] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.176235] mice: PS/2 mouse device common for all mice
[    2.176501] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    2.176604] rtc0: alarms up to one year, y3k, hpet irqs
[    2.176726] cpuidle: using governor ladder
[    2.176783] cpuidle: using governor menu
[    2.177372] TCP cubic registered
[    2.177811] registered taskstats version 1
[    2.178061]   Magic number: 12:847:397
[    2.178210] mem random: hash matches
[    2.178337] rtc_cmos 00:09: setting system clock to 2008-10-25 20:23:57 UTC (1224966237)
[    2.178409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.178468] EDD information not available.
[    2.178581] Freeing unused kernel memory: 536k freed
[    2.178945] Write protecting the kernel read-only data: 4348k
[    2.206939] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.384840] fuse init (API version 7.9)
[    2.467859] ACPI: processor limited to max C-state 1
[    2.468104] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.468208] processor ACPI0007:00: registered as cooling_device0
[    2.468455] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.468539] processor ACPI0007:01: registered as cooling_device1
[    2.501836] thermal LNXTHERM:01: registered as thermal_zone0
[    2.503279] ACPI: Thermal Zone [THRM] (52 C)
[    3.034884] usbcore: registered new interface driver usbfs
[    3.034919] usbcore: registered new interface driver hub
[    3.034978] usbcore: registered new device driver usb
[    3.050908] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.051506] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    3.051522] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    3.051536] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    3.051541] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.051602] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.051640] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    3.060546] No dock devices found.
[    3.076750] SCSI subsystem initialized
[    3.110201] usb usb1: configuration #1 chosen from 1 choice
[    3.110239] hub 1-0:1.0: USB hub found
[    3.110254] hub 1-0:1.0: 8 ports detected
[    3.120408] libata version 3.00 loaded.
[    3.217438] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.217446] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    3.217460] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.217464] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.217502] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    3.217540] ehci_hcd 0000:00:0b.1: debug port 1
[    3.217545] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.217554] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    3.232030] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.232228] usb usb2: configuration #1 chosen from 1 choice
[    3.232265] hub 2-0:1.0: USB hub found
[    3.232278] hub 2-0:1.0: 8 ports detected
[    3.336385] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.336452] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    3.336994] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    3.337008] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    3.337031] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.337041] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.337163] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.337677] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    3.337686] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    3.337691] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.337717] nv_probe: set workaround bit for reversed mac addr
[    3.860984] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:79:b6:eb
[    3.860991] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    3.866211] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    3.866228] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    3.921946] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[c8000000-c80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.929304] pata_amd 0000:00:0d.0: version 0.3.10
[    3.929370] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.929492] scsi0 : pata_amd
[    3.929637] scsi1 : pata_amd
[    3.930614] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    3.930617] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    4.206954] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.02, max MWDMA2
[    4.206973] ata1: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    4.463025] ata1.00: configured for MWDMA2
[    4.463086] ata2: port disabled. ignoring.
[    4.463143] isa bounce pool size: 16 pages
[    4.467535] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.02 PQ: 0 ANSI: 5
[    4.468115] sata_nv 0000:00:0e.0: version 3.5
[    4.468132] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    4.468137] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.468185] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.469688] scsi2 : sata_nv
[    4.470111] scsi3 : sata_nv
[    4.470382] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    4.470387] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    4.478581] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.497174] Driver 'sr' needs updating - please use bus_type methods
[    4.509634] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.509642] Uniform CD-ROM driver Revision: 3.20
[    4.509881] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.103121] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.231396] ata3.00: ATA-8: WDC WD1200BEVS-60UST0, 01.01A01, max UDMA/100
[    5.231401] ata3.00: 234441648 sectors, multi 16: LBA48 
[    5.359408] ata3.00: configured for UDMA/100
[    5.486184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0008349af00]
[    5.882094] ata4: SATA link down (SStatus 0 SControl 300)
[    5.882268] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[    5.882490] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.912456] Driver 'sd' needs updating - please use bus_type methods
[    5.912604] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.912629] sd 2:0:0:0: [sda] Write Protect is off
[    5.912632] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.912670] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.912761] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.912783] sd 2:0:0:0: [sda] Write Protect is off
[    5.912786] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.912823] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.912828]  sda: sda1 < sda5 sda6 > sda2
[    5.984655] sd 2:0:0:0: [sda] Attached SCSI disk
[   12.987818] kjournald starting.  Commit interval 5 seconds
[   12.987838] EXT3-fs: mounted filesystem with ordered data mode.
[   21.593331] udevd version 124 started
[   22.651268] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.702727] ricoh-mmc: Ricoh MMC Controller disabling driver
[   22.702733] ricoh-mmc: Copyright(c) Philip Langdale
[   22.702779] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   22.702799] ricoh-mmc: Controller is now disabled.
[   22.792593] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.902785] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   22.902838] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   22.909338] sdhci: Secure Digital Host Controller Interface driver
[   22.909344] sdhci: Copyright(c) Pierre Ossman
[   22.956980] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   22.957582] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   22.957598] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   22.957722] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   23.070977] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   23.088033] ACPI: Power Button (FF) [PWRF]
[   23.088145] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   23.120041] ACPI: Power Button (CM) [PWRB]
[   23.120217] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   23.152070] ACPI: Sleep Button (CM) [SLPB]
[   23.152252] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   23.152737] ACPI: Lid Switch [LID]
[   23.153900] ACPI: AC Adapter [ACAD] (on-line)
[   23.525617] ACPI: Battery Slot [BAT0] (battery present)
[   23.525985] ACPI: WMI: Mapper loaded
[   23.788654] acpi device:24: registered as cooling_device2
[   23.789027] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input6
[   23.817050] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   23.820467] acpi device:2a: registered as cooling_device3
[   23.820836] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/device:28/input/input7
[   23.849051] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.003562] nvidia: module license 'NVIDIA' taints kernel.
[   24.274689] nvidia 0000:05:00.0: power state changed by ACPI to D0
[   24.275252] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 16
[   24.275267] nvidia 0000:05:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, high) -> IRQ 16
[   24.275276] nvidia 0000:05:00.0: setting latency timer to 64
[   24.275514] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   24.280135] ieee80211_crypt: registered algorithm 'NULL'
[   24.402639] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   24.402656] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[   24.402662] wl 0000:03:00.0: setting latency timer to 64
[   24.410148] ieee80211_crypt: registered algorithm 'TKIP'
[   24.435007] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   24.435263] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.6
[   24.488001] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   24.488036] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   24.488077] HDA Intel 0000:00:10.1: setting latency timer to 64
[   25.169638] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.234919] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   26.515762] lp: driver loaded but no devices found
[   27.575816] EXT3 FS on sda6, internal journal
[   28.993607] type=1505 audit(1224980663.863:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4444
[   29.199397] type=1505 audit(1224980664.067:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4449
[   29.199663] type=1505 audit(1224980664.067:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4449
[   29.417475] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.337342] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[   31.337413] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[   31.337418] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   32.555824] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.157549] NET: Registered protocol family 10
[   33.159277] lo: Disabled Privacy Extensions
[   33.713843] ppdev: user-space parallel port driver
[   36.705751] RPC: Registered udp transport module.
[   36.705759] RPC: Registered tcp transport module.
[   36.779859] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   36.960876] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   36.968215] NFSD: starting 90-second grace period
[   38.004028] Clocksource tsc unstable (delta = -73805863 ns)
[   44.951276] eth0: no link during initialization.
[   44.952733] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.862462] NET: Registered protocol family 17
[   50.509027] eth1: no IPv6 routers present
[   85.416559] CPU0 attaching NULL sched-domain.
[   85.416595] CPU1 attaching NULL sched-domain.
[   85.425141] CPU0 attaching sched-domain:
[   85.425155]  domain 0: span 0-1 level CPU
[   85.425163]   groups: 0 1
[   85.425172]   domain 1: span 0-1 level NODE
[   85.425178]    groups: 0-1
[   85.425186] CPU1 attaching sched-domain:
[   85.425191]  domain 0: span 0-1 level CPU
[   85.425195]   groups: 1 0
[   85.425202]   domain 1: span 0-1 level NODE
[   85.425207]    groups: 0-1
[  152.437418] type=1503 audit(1224980787.307:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6824/net/" pid=6824 profile="/usr/sbin/cupsd"
[  153.590454] type=1503 audit(1224980788.459:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6828/net/" pid=6828 profile="/usr/sbin/cupsd"
[  153.590504] type=1503 audit(1224980788.459:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590512] type=1503 audit(1224980788.459:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590519] type=1503 audit(1224980788.459:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590527] type=1503 audit(1224980788.459:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590535] type=1503 audit(1224980788.459:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590543] type=1503 audit(1224980788.459:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590550] type=1503 audit(1224980788.459:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  153.590558] type=1503 audit(1224980788.459:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6828 profile="/usr/sbin/cupsd"
[  197.281826] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  197.281835] vboxdrv: Successfully done.
[  197.281838] vboxdrv: Found 2 processor cores.
[  197.282603] vboxdrv: fAsync=1 offMin=0x1b30b8 offMax=0x1b30b8
[  197.282946] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  197.282953] vboxdrv: Successfully loaded version 2.0.2_OSE (interface 0x00090000).

---

### Post by blazemore on 2008-10-26
I used to have kernel panic with Ndiswrapper, are you using that?
Also, is your system a laptop? If so, are you using it in a well ventilated area? (IE not on bedsheets) It might be an idea to clean out your vents with compressed air. In my experience, Linux doesn't run too well on flaky, overheating hardware.

---

### Post by josephellengar on 2008-10-26
> **blazemore said:**
> I used to have kernel panic with Ndiswrapper, are you using that?
Also, is your system a laptop? If so, are you using it in a well ventilated area? (IE not on bedsheets) It might be an idea to clean out your vents with compressed air. In my experience, Linux doesn't run too well on flaky, overheating hardware.

Nope, not using ndiswrapper.  My system is a laptop, but I use it on top of a blower.  Also, I recently had the hard drive and the motherboard replaced, so I don't htink that this is flaky or overheated.  Thank you very much for your help.

---

### Post by ciscosurfer on 2008-10-26
It's possible the new replacements weren't installed correctly.  Just another thought.  And I'm not sure if you already mentioned this, but if that dmesg log didn't provide any clues as to the panic, you should check the older dmesg logs as well.

---

### Post by josephellengar on 2008-10-26
> **ciscosurfer said:**
> It's possible the new replacements weren't installed correctly.  Just another thought.  And I'm not sure if you already mentioned this, but if that dmesg log didn't provide any clues as to the panic, you should check the older dmesg logs as well.

That's a good idea.  I haven't had one in a while.  How do I check the old dmesg logs?  I think that the replacements were done correctly because HP did them and the problems did not start directly after they were done.  Also, Windows works fine.  I haven't had any crashes or BSODs.

---

### Post by ciscosurfer on 2008-10-26
> **idigchess said:**
> That's a good idea.  I haven't had one in a while.  How do I check the old dmesg logs?  I think that the replacements were done correctly because HP did them and the problems did not start directly after they were done.  Also, Windows works fine.  I haven't had any crashes or BSODs.Keep searching the forums here for 'kernel panic' etc. b/c there are a few threads already that may also help you out.  But I like a good challenge, so read on!

You would check these logs the same way you did before.  Go to /var/log/ and view them using an editor or the like.  The logs will rotate via a logrotate script that essentially runs daily and checks various configs under /etc/logrotate.d/ which tell logrotate basically what to do for those particular apps.  The main /etc/logrotate.conf script will typically tell your system to keep a backlog of logs for 4 weeks unless overriden by specific apps requests/requirements.  That was probably more than cared to know.  Let's head back to /var/log/ and see what we've got laying around, for example dmesg, dmesg.0, dmesg.1, maybe a compressed log or two, dmesg.0.gz or dmesg.1.gz perhaps.  So a general rule of thumb is to check your logs immediately upon noticing an error lest they get "overwritten" or rotated "out of commision" by a new set of logs.  If your kernel panics happened relatively recently, you should be able to glean those aiee! (hard kernel panic) or oops (soft kernel panic) messages from one of the log files.  Of note, if you're going to grep for instances, then I would suggest doing what's called a 'case-insensitive' search using the -i switch.  Like:```
cat dmesg > dmesg.kernelpanic
cat dmesg.kernelpanic | grep -i "panic\|oops\|aiee"
less dmesg.kernelpanic  #now press the forward slash key aka question mark and then type in any word or phrase you are looking for.  Use 'p' and 'n' to go back and forward in your search, use the spacebar to page through one page at a time or the Enter key to go line by line.  When you're finished, hit 'q'
```Those are few more ways you can do this on the command line.  I think the System Log app under System > Administration > System Log still works great though if you're hesistant in a terminal.  (I use a console for almost everything, but a great GUI app is a great GUI app, y'know?)  Okay, here's another guide you can take a look at to keep you busy: [http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/](http://rhcelinuxguide.wordpress.com/2006/06/01/linux-kernel-panic-prevent-cardiac-arrest/)

If an authorized reseller or HP themselves did the repairs, then you're probably okay.  This doesn't mean however that a new component didn't have some kind of failure that went unnoticed until your first panic.  This is possible, but unlikely.  The fact that Windows runs solid *may* rule out any hardware problems that could exist.  But that's unclear at this point.

Panics can occur for a variety of reasons that we've mentioned already, but try to think back to the last time it happened and the time before that.  What exactly were you doing before your box decided to call it a day.  Were you switching back and forth between tty's, running similar commands when doing so?  Were you taxing your cpu to the point of burnout?  Did you plug in some truly exotic piece of external hardware while the system was running?  I've seen machines puke like this. We'll continue to troubleshoot this puppy if you're feeling adventurous but at least you're up and running now, so that's good :-)

---

### Post by josephellengar on 2008-10-30
Thank you very much.  I have been unable to find anything in any of these logs, but I haven't had a panic in a while, so next time I have one I'll check all the logs again.  Do you mind if I contact you again if I find something and can't figure out how to fix it?  Thanks again for your help.

---

### Post by ciscosurfer on 2008-10-31
> **idigchess said:**
> Thank you very much.  I have been unable to find anything in any of these logs, but I haven't had a panic in a while, so next time I have one I'll check all the logs again.  Do you mind if I contact you again if I find something and can't figure out how to fix it?  Thanks again for your help.Absolutely and no problem. :-)

---


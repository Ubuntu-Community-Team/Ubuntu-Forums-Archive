---
title: "Constant Freezing, hard shutdowns, many programs."
date: 2008-11-02
forum: General Help
---

### Post by carl99fan on 2008-11-02
I am experiencing many many freezes/crashes.
I am using:
HP Amd X2 4200+ 2.2ghz
1Gb ddr2 533mhz
Nvida integrated 6100

At first I thought it was Mozilla, but it is happening now even with NO programs running.

It keeps getting worse and worse. I have searched the threads and I don't seem to have a similar problem to the ones I found.

My knowledge of linux is limited.

I am not using up all my ram, looking at the system monitor it seems that my processor is not even working very hard.

screen darkens, and most of the time it never comes back. If I let the unit sit I hear the fans kick into high gear but it never seems to come back to me. any help would be appreciated.
I am using Hardy 8.04

---

### Post by userundefine on 2008-11-02
I've been experiencing similar issues.  I posted about it [here]("http://ubuntuforums.org/showthread.php?t=966054").  I recommend you go through your logs (/var/log/kern.log, /var/log/messages) and see if you find messages from the time when the freezes happen.  If they're similar to mine, you can contribute to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292751") I've filed.

---

### Post by carl99fan on 2008-11-02
I will start looking.
I found the files but they are HUGE.
thanks.
I will report anything I can find.

---

### Post by userundefine on 2008-11-02
You can search the files from the command line.  If you know what time exactly your crashes happened, it's easier.  For example, if you have a lockup, and you have to do a hard reboot, look at the time.  Then, the first thing you should do when you reboot is go look at the files.  Go to the end, then scroll up to look for the time (or search).

---

### Post by carl99fan on 2008-11-02
I searched for a few phrases and I have not found anything like the messages you got but I will check it out next time it happens.
I have been up and running for about an hour now, longest run of the day.

---

### Post by carl99fan on 2008-11-02
Here is some LOG after a crash.

I see a few things but I don't know what I am looking at to be honest.

```
 Nov  2 18:32:28 kenny-desktop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Nov  2 18:32:28 kenny-desktop kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Nov  2 18:32:28 kenny-desktop kernel: Symbols match kernel version 2.6.24.
Nov  2 18:32:28 kenny-desktop kernel: Loaded 34275 symbols from 88 modules.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] 62MB HIGHMEM available.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] 896MB LOWMEM available.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] found SMP MP-table at 000f5ac0
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Zone PFN ranges:
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   DMA             0 ->     4096
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   HighMem    229376 ->   245488
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]     0:        0 ->   245488
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] On node 0 totalpages: 245488
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   HighMem zone: 125 pages used for memmap
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] DMI present.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7680 checksum 0
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: RSDP 000F7680, 0014 (r0 HP-CPC)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: RSDT 3BEF3040, 0034 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: FACP 3BEF30C0, 0074 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: DSDT 3BEF3180, 6F9C (r1 HP-CPC AWRDACPI     1000 MSFT  100000E)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: FACS 3BEF0000, 0040
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: SSDT 3BEFA240, 0206 (r1 HP-CPC POWERNOW        1  LTP        1)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: MCFG 3BEFA4C0, 003C (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: APIC 3BEFA180, 007C (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Processor #0 15:11 APIC version 16
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Processor #1 15:11 APIC version 16
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: IRQ14 used by override.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] ACPI: IRQ15 used by override.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Kernel command line: root=UUID=89496fae-bf27-4662-bff7-cf358b59799b ro quiet splash
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Initializing CPU#0
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [    0.000000] Detected 2204.629 MHz processor.
Nov  2 18:32:28 kenny-desktop kernel: [   17.734097] spurious 8259A interrupt: IRQ7.
Nov  2 18:32:28 kenny-desktop kernel: [   17.737109] Console: colour VGA+ 80x25
Nov  2 18:32:28 kenny-desktop kernel: [   17.737112] console [tty0] enabled
Nov  2 18:32:28 kenny-desktop kernel: [   17.737494] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   17.737890] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756478] Memory: 961024k/981952k available (2177k kernel code, 20368k reserved, 1005k data, 368k init, 64448k highmem)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756485] virtual kernel memory layout:
Nov  2 18:32:28 kenny-desktop kernel: [   17.756486]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756487]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756488]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756489]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756490]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756491]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756492]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Nov  2 18:32:28 kenny-desktop kernel: [   17.756495] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  2 18:32:28 kenny-desktop kernel: [   17.756524] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Nov  2 18:32:28 kenny-desktop kernel: [   17.836468] Calibrating delay using timer specific routine.. 4413.22 BogoMIPS (lpj=8826440)
Nov  2 18:32:28 kenny-desktop kernel: [   17.836492] Security Framework initialized
Nov  2 18:32:28 kenny-desktop kernel: [   17.836498] SELinux:  Disabled at boot.
Nov  2 18:32:28 kenny-desktop kernel: [   17.836511] AppArmor: AppArmor initialized
Nov  2 18:32:28 kenny-desktop kernel: [   17.836515] Failure registering capabilities with primary security module.
Nov  2 18:32:28 kenny-desktop kernel: [   17.836522] Mount-cache hash table entries: 512
Nov  2 18:32:28 kenny-desktop kernel: [   17.836631] Initializing cgroup subsys ns
Nov  2 18:32:28 kenny-desktop kernel: [   17.836634] Initializing cgroup subsys cpuacct
Nov  2 18:32:28 kenny-desktop kernel: [   17.836643] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
Nov  2 18:32:28 kenny-desktop kernel: [   17.836651] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov  2 18:32:28 kenny-desktop kernel: [   17.836653] CPU: L2 Cache: 512K (64 bytes/line)
Nov  2 18:32:28 kenny-desktop kernel: [   17.836655] CPU 0(2) -> Core 0
Nov  2 18:32:28 kenny-desktop kernel: [   17.836657] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
Nov  2 18:32:28 kenny-desktop kernel: [   17.836666] Compat vDSO mapped to ffffe000.
Nov  2 18:32:28 kenny-desktop kernel: [   17.836676] Checking 'hlt' instruction... OK.
Nov  2 18:32:28 kenny-desktop kernel: [   17.852734] SMP alternatives: switching to UP code
Nov  2 18:32:28 kenny-desktop kernel: [   17.853908] Early unpacking initramfs... done
Nov  2 18:32:28 kenny-desktop kernel: [   18.145128] ACPI: Core revision 20070126
Nov  2 18:32:28 kenny-desktop kernel: [   18.145203] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov  2 18:32:28 kenny-desktop kernel: [   18.149619] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
Nov  2 18:32:28 kenny-desktop kernel: [   18.149636] SMP alternatives: switching to SMP code
Nov  2 18:32:28 kenny-desktop kernel: [   18.150092] Booting processor 1/1 eip 3000
Nov  2 18:32:28 kenny-desktop kernel: [   18.160600] Initializing CPU#1
Nov  2 18:32:28 kenny-desktop kernel: [   18.240603] Calibrating delay using timer specific routine.. 4409.52 BogoMIPS (lpj=8819056)
Nov  2 18:32:28 kenny-desktop kernel: [   18.240609] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
Nov  2 18:32:28 kenny-desktop kernel: [   18.240615] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov  2 18:32:28 kenny-desktop kernel: [   18.240617] CPU: L2 Cache: 512K (64 bytes/line)
Nov  2 18:32:28 kenny-desktop kernel: [   18.240619] CPU 1(2) -> Core 1
Nov  2 18:32:28 kenny-desktop kernel: [   18.240620] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001f 00000000
Nov  2 18:32:28 kenny-desktop kernel: [   18.240292] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
Nov  2 18:32:28 kenny-desktop kernel: [   18.240306] Total of 2 processors activated (8822.74 BogoMIPS).
Nov  2 18:32:28 kenny-desktop kernel: [   18.240602] ENABLING IO-APIC IRQs
Nov  2 18:32:28 kenny-desktop kernel: [   18.240837] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov  2 18:32:28 kenny-desktop kernel: [   18.280538] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Nov  2 18:32:28 kenny-desktop kernel: [   18.280583] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
Nov  2 18:32:28 kenny-desktop kernel: [   18.280585] ...trying to set up timer as Virtual Wire IRQ... failed.
Nov  2 18:32:28 kenny-desktop kernel: [   18.320266] ...trying to set up timer as ExtINT IRQ... works.
Nov  2 18:32:28 kenny-desktop kernel: [   18.563869] Brought up 2 CPUs
Nov  2 18:32:28 kenny-desktop kernel: [   18.563925] CPU0 attaching sched-domain:
Nov  2 18:32:28 kenny-desktop kernel: [   18.563927]  domain 0: span 03
Nov  2 18:32:28 kenny-desktop kernel: [   18.563929]   groups: 01 02
Nov  2 18:32:28 kenny-desktop kernel: [   18.563931] CPU1 attaching sched-domain:
Nov  2 18:32:28 kenny-desktop kernel: [   18.563933]  domain 0: span 03
Nov  2 18:32:28 kenny-desktop kernel: [   18.563934]   groups: 02 01
Nov  2 18:32:28 kenny-desktop kernel: [   18.564116] net_namespace: 64 bytes
Nov  2 18:32:28 kenny-desktop kernel: [   18.564123] Booting paravirtualized kernel on bare hardware
Nov  2 18:32:28 kenny-desktop kernel: [   18.564519] Time: 23:32:02  Date: 11/02/08
Nov  2 18:32:28 kenny-desktop kernel: [   18.564545] NET: Registered protocol family 16
Nov  2 18:32:28 kenny-desktop kernel: [   18.564701] EISA bus registered
Nov  2 18:32:28 kenny-desktop kernel: [   18.564704] ACPI: bus type pci registered
Nov  2 18:32:28 kenny-desktop kernel: [   18.571190] PCI: PCI BIOS revision 3.00 entry at 0xf2060, last bus=3
Nov  2 18:32:28 kenny-desktop kernel: [   18.571192] PCI: Using configuration type 1
Nov  2 18:32:28 kenny-desktop kernel: [   18.571201] Setting up standard PCI resources
Nov  2 18:32:28 kenny-desktop kernel: [   18.576599] ACPI: EC: Look up EC in DSDT
Nov  2 18:32:28 kenny-desktop kernel: [   18.583580] ACPI: Interpreter enabled
Nov  2 18:32:28 kenny-desktop kernel: [   18.583583] ACPI: (supports S0 S1 S3 S4 S5)
Nov  2 18:32:28 kenny-desktop kernel: [   18.583595] ACPI: Using IOAPIC for interrupt routing
Nov  2 18:32:28 kenny-desktop kernel: [   18.593015] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  2 18:32:28 kenny-desktop kernel: [   18.593972] PCI: Transparent bridge - 0000:00:10.0
Nov  2 18:32:28 kenny-desktop kernel: [   18.593989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov  2 18:32:28 kenny-desktop kernel: [   18.594273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov  2 18:32:28 kenny-desktop kernel: [   18.691151] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.691356] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.691559] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.691767] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.691969] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.692171] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.692376] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
Nov  2 18:32:28 kenny-desktop kernel: [   18.692579] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.692782] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.692985] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.693191] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
Nov  2 18:32:28 kenny-desktop kernel: [   18.693392] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.693595] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
Nov  2 18:32:28 kenny-desktop kernel: [   18.693797] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.694000] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.694202] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.694404] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.694606] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.694809] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
Nov  2 18:32:28 kenny-desktop kernel: [   18.695012] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
Nov  2 18:32:28 kenny-desktop kernel: [   18.695244] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.695470] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.695697] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.695924] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.696148] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.696374] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.696599] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
Nov  2 18:32:28 kenny-desktop kernel: [   18.696825] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.697050] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.697276] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.697501] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Nov  2 18:32:28 kenny-desktop kernel: [   18.697728] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.697954] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.698180] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
Nov  2 18:32:28 kenny-desktop kernel: [   18.698406] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.698632] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.698858] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.699084] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.699311] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Nov  2 18:32:28 kenny-desktop kernel: [   18.699538] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Nov  2 18:32:28 kenny-desktop kernel: [   18.699766] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Nov  2 18:32:28 kenny-desktop kernel: [   18.699896] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  2 18:32:28 kenny-desktop kernel: [   18.699920] pnp: PnP ACPI init
Nov  2 18:32:28 kenny-desktop kernel: [   18.699927] ACPI: bus type pnp registered
Nov  2 18:32:28 kenny-desktop kernel: [   18.704439] pnpacpi: exceeded the max number of mem resources: 12
Nov  2 18:32:28 kenny-desktop kernel: [   18.704496] pnp: PnP ACPI: found 10 devices
Nov  2 18:32:28 kenny-desktop kernel: [   18.704498] ACPI: ACPI bus type pnp unregistered
Nov  2 18:32:28 kenny-desktop kernel: [   18.704501] PnPBIOS: Disabled by ACPI PNP
Nov  2 18:32:28 kenny-desktop kernel: [   18.704682] PCI: Using ACPI for IRQ routing
Nov  2 18:32:28 kenny-desktop kernel: [   18.704686] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov  2 18:32:28 kenny-desktop kernel: [   18.787556] NET: Registered protocol family 8
Nov  2 18:32:28 kenny-desktop kernel: [   18.787558] NET: Registered protocol family 20
Nov  2 18:32:28 kenny-desktop kernel: [   18.787615] AppArmor: AppArmor Filesystem Enabled
Nov  2 18:32:28 kenny-desktop kernel: [   18.799566] system 00:01: ioport range 0x4000-0x407f has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799569] system 00:01: ioport range 0x4080-0x40ff has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799571] system 00:01: ioport range 0x4400-0x447f has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799574] system 00:01: ioport range 0x4480-0x44ff has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799576] system 00:01: ioport range 0x4800-0x487f has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799578] system 00:01: ioport range 0x4880-0x48ff has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799581] system 00:01: ioport range 0x2000-0x207f has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799583] system 00:01: ioport range 0x2080-0x20ff has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799586] system 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799591] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799593] system 00:02: ioport range 0x800-0x87f has been reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799600] system 00:08: iomem range 0xf0000000-0xf3ffffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799605] system 00:09: iomem range 0xf0000-0xf3fff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799607] system 00:09: iomem range 0xf4000-0xf7fff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799609] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799612] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799614] system 00:09: iomem range 0x3bef0000-0x3befffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799617] system 00:09: iomem range 0xffff0000-0xffffffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799619] system 00:09: iomem range 0x0-0x9ffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799622] system 00:09: iomem range 0x100000-0x3beeffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799624] system 00:09: iomem range 0x3bf00000-0x3fefffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799627] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799629] system 00:09: iomem range 0xfee00000-0xfeefffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.799632] system 00:09: iomem range 0xfefff000-0xfeffffff could not be reserved
Nov  2 18:32:28 kenny-desktop kernel: [   18.829936] PCI: Bridge: 0000:00:02.0
Nov  2 18:32:28 kenny-desktop kernel: [   18.829938]   IO window: b000-bfff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829941]   MEM window: fde00000-fdefffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829943]   PREFETCH window: fdb00000-fdbfffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829945] PCI: Bridge: 0000:00:04.0
Nov  2 18:32:28 kenny-desktop kernel: [   18.829947]   IO window: 9000-9fff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829949]   MEM window: fda00000-fdafffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829951]   PREFETCH window: fd900000-fd9fffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829954] PCI: Bridge: 0000:00:10.0
Nov  2 18:32:28 kenny-desktop kernel: [   18.829956]   IO window: a000-afff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829959]   MEM window: fdd00000-fddfffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829961]   PREFETCH window: fdc00000-fdcfffff
Nov  2 18:32:28 kenny-desktop kernel: [   18.829974] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   18.829980] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   18.829986] PCI: Setting latency timer of device 0000:00:10.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   18.829996] NET: Registered protocol family 2
Nov  2 18:32:28 kenny-desktop kernel: [   18.831508] Time: acpi_pm clocksource has been installed.
Nov  2 18:32:28 kenny-desktop kernel: [   18.831525] Switched to high resolution mode on CPU 0
Nov  2 18:32:28 kenny-desktop kernel: [   18.832162] Switched to high resolution mode on CPU 1
Nov  2 18:32:28 kenny-desktop kernel: [   18.867501] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   18.867764] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   18.868703] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   18.869200] TCP: Hash tables configured (established 131072 bind 65536)
Nov  2 18:32:28 kenny-desktop kernel: [   18.869203] TCP reno registered
Nov  2 18:32:28 kenny-desktop kernel: [   18.879559] checking if image is initramfs... it is
Nov  2 18:32:28 kenny-desktop kernel: [   19.442400] Freeing initrd memory: 7711k freed
Nov  2 18:32:28 kenny-desktop kernel: [   19.443737] audit: initializing netlink socket (disabled)
Nov  2 18:32:28 kenny-desktop kernel: [   19.443751] audit(1225668722.424:1): initialized
Nov  2 18:32:28 kenny-desktop kernel: [   19.443897] highmem bounce pool size: 64 pages
Nov  2 18:32:28 kenny-desktop kernel: [   19.445563] VFS: Disk quotas dquot_6.5.1
Nov  2 18:32:28 kenny-desktop kernel: [   19.445625] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  2 18:32:28 kenny-desktop kernel: [   19.445740] io scheduler noop registered
Nov  2 18:32:28 kenny-desktop kernel: [   19.445742] io scheduler anticipatory registered
Nov  2 18:32:28 kenny-desktop kernel: [   19.445744] io scheduler deadline registered
Nov  2 18:32:28 kenny-desktop kernel: [   19.445756] io scheduler cfq registered (default)
Nov  2 18:32:28 kenny-desktop kernel: [   19.445767] pci 0000:00:00.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.445794] pci 0000:00:02.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.445802] pci 0000:00:04.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.445809] Boot video device is 0000:00:05.0
Nov  2 18:32:28 kenny-desktop kernel: [   19.445829] pci 0000:00:09.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.475377] pci 0000:00:0e.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.475387] pci 0000:00:0f.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.475395] pci 0000:00:10.0: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.475405] pci 0000:00:10.1: Enabling HT MSI Mapping
Nov  2 18:32:28 kenny-desktop kernel: [   19.475519] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   19.475538] assign_interrupt_mode Found MSI capability
Nov  2 18:32:28 kenny-desktop kernel: [   19.475556] Allocate Port Service[0000:00:02.0:pcie00]
Nov  2 18:32:28 kenny-desktop kernel: [   19.475610] PCI: Setting latency timer of device 0000:00:04.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   19.475628] assign_interrupt_mode Found MSI capability
Nov  2 18:32:28 kenny-desktop kernel: [   19.475641] Allocate Port Service[0000:00:04.0:pcie00]
Nov  2 18:32:28 kenny-desktop kernel: [   19.475842] isapnp: Scanning for PnP cards...
Nov  2 18:32:28 kenny-desktop kernel: [   19.828320] isapnp: No Plug & Play device found
Nov  2 18:32:28 kenny-desktop kernel: [   19.855303] Real Time Clock Driver v1.12ac
Nov  2 18:32:28 kenny-desktop kernel: [   19.855421] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov  2 18:32:28 kenny-desktop kernel: [   19.856467] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov  2 18:32:28 kenny-desktop kernel: [   19.856526] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov  2 18:32:28 kenny-desktop kernel: [   19.856604] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov  2 18:32:28 kenny-desktop kernel: [   19.856606] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Nov  2 18:32:28 kenny-desktop kernel: [   19.857119] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  2 18:32:28 kenny-desktop kernel: [   19.875977] mice: PS/2 mouse device common for all mice
Nov  2 18:32:28 kenny-desktop kernel: [   19.876087] EISA: Probing bus 0 at eisa.0
Nov  2 18:32:28 kenny-desktop kernel: [   19.876095] Cannot allocate resource for EISA slot 2
Nov  2 18:32:28 kenny-desktop kernel: [   19.876099] Cannot allocate resource for EISA slot 4
Nov  2 18:32:28 kenny-desktop kernel: [   19.876111] EISA: Detected 0 cards.
Nov  2 18:32:28 kenny-desktop kernel: [   19.876114] cpuidle: using governor ladder
Nov  2 18:32:28 kenny-desktop kernel: [   19.876115] cpuidle: using governor menu
Nov  2 18:32:28 kenny-desktop kernel: [   19.876199] NET: Registered protocol family 1
Nov  2 18:32:28 kenny-desktop kernel: [   19.876225] Using IPI No-Shortcut mode
Nov  2 18:32:28 kenny-desktop kernel: [   19.876257] registered taskstats version 1
Nov  2 18:32:28 kenny-desktop kernel: [   19.876378]   Magic number: 0:100:554
Nov  2 18:32:28 kenny-desktop kernel: [   19.876452]   hash matches device ptya0
Nov  2 18:32:28 kenny-desktop kernel: [   19.876515]   hash matches device PNP0C01:00
Nov  2 18:32:28 kenny-desktop kernel: [   19.876527]   hash matches device PNP0C0F:05
Nov  2 18:32:28 kenny-desktop kernel: [   19.876542] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  2 18:32:28 kenny-desktop kernel: [   19.876544] EDD information not available.
Nov  2 18:32:28 kenny-desktop kernel: [   19.876808] Freeing unused kernel memory: 368k freed
Nov  2 18:32:28 kenny-desktop kernel: [   19.876833] Write protecting the kernel read-only data: 801k
Nov  2 18:32:28 kenny-desktop kernel: [   19.918321] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov  2 18:32:28 kenny-desktop kernel: [   21.070519] fuse init (API version 7.9)
Nov  2 18:32:28 kenny-desktop kernel: [   21.081845] ACPI: Fan [FAN] (on)
Nov  2 18:32:28 kenny-desktop kernel: [   21.089908] ACPI: Thermal Zone [THRM] (40 C)
Nov  2 18:32:28 kenny-desktop kernel: [   21.491526] usbcore: registered new interface driver usbfs
Nov  2 18:32:28 kenny-desktop kernel: [   21.491549] usbcore: registered new interface driver hub
Nov  2 18:32:28 kenny-desktop kernel: [   21.491572] usbcore: registered new device driver usb
Nov  2 18:32:28 kenny-desktop kernel: [   21.492454] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov  2 18:32:28 kenny-desktop kernel: [   21.492899] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
Nov  2 18:32:28 kenny-desktop kernel: [   21.492910] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
Nov  2 18:32:28 kenny-desktop kernel: [   21.492921] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   21.492925] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Nov  2 18:32:28 kenny-desktop kernel: [   21.493219] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
Nov  2 18:32:28 kenny-desktop kernel: [   21.493237] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfe02f000
Nov  2 18:32:28 kenny-desktop kernel: [   21.532053] SCSI subsystem initialized
Nov  2 18:32:28 kenny-desktop kernel: [   21.550643] usb usb1: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   21.550667] hub 1-0:1.0: USB hub found
Nov  2 18:32:28 kenny-desktop kernel: [   21.550675] hub 1-0:1.0: 8 ports detected
Nov  2 18:32:28 kenny-desktop kernel: [   21.563845] libata version 3.00 loaded.
Nov  2 18:32:28 kenny-desktop kernel: [   21.653156] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Nov  2 18:32:28 kenny-desktop kernel: [   21.653562] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Nov  2 18:32:28 kenny-desktop kernel: [   21.653572] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 22 (level, low) -> IRQ 17
Nov  2 18:32:28 kenny-desktop kernel: [   21.653579] PCI: Setting latency timer of device 0000:00:14.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   21.956080] usb 1-2: new low speed USB device using ohci_hcd and address 2
Nov  2 18:32:28 kenny-desktop kernel: [   22.170551] usb 1-2: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   22.173788] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:ed:47:1c
Nov  2 18:32:28 kenny-desktop kernel: [   22.173792] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Nov  2 18:32:28 kenny-desktop kernel: [   22.173384] sata_nv 0000:00:0e.0: version 3.5
Nov  2 18:32:28 kenny-desktop kernel: [   22.173782] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
Nov  2 18:32:28 kenny-desktop kernel: [   22.173792] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 18
Nov  2 18:32:28 kenny-desktop kernel: [   22.173841] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   22.174648] scsi0 : sata_nv
Nov  2 18:32:28 kenny-desktop kernel: [   22.175581] scsi1 : sata_nv
Nov  2 18:32:28 kenny-desktop kernel: [   22.175730] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 18
Nov  2 18:32:28 kenny-desktop kernel: [   22.175733] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 18
Nov  2 18:32:28 kenny-desktop kernel: [   22.477060] usb 1-8: new full speed USB device using ohci_hcd and address 3
Nov  2 18:32:28 kenny-desktop kernel: [   22.639902] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:32:28 kenny-desktop kernel: [   22.649032] ata1.00: ATA-7: ST3250824AS, 3.AHH, max UDMA/100
Nov  2 18:32:28 kenny-desktop kernel: [   22.649034] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 0/32)
Nov  2 18:32:28 kenny-desktop kernel: [   22.665011] ata1.00: configured for UDMA/100
Nov  2 18:32:28 kenny-desktop kernel: [   22.691006] usb 1-8: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   22.693487] usbcore: registered new interface driver hiddev
Nov  2 18:32:28 kenny-desktop kernel: [   22.701170] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input2
Nov  2 18:32:28 kenny-desktop kernel: [   22.732829] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:0b.0-2
Nov  2 18:32:28 kenny-desktop kernel: [   22.732855] usbcore: registered new interface driver usbhid
Nov  2 18:32:28 kenny-desktop kernel: [   22.732859] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov  2 18:32:28 kenny-desktop kernel: [   22.733068] usbcore: registered new interface driver libusual
Nov  2 18:32:28 kenny-desktop kernel: [   22.737048] Initializing USB Mass Storage driver...
Nov  2 18:32:28 kenny-desktop kernel: [   22.737114] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  2 18:32:28 kenny-desktop kernel: [   22.737169] usbcore: registered new interface driver usb-storage
Nov  2 18:32:28 kenny-desktop kernel: [   22.737172] USB Mass Storage support registered.
Nov  2 18:32:28 kenny-desktop kernel: [   22.737245] usb-storage: device found at 3
Nov  2 18:32:28 kenny-desktop kernel: [   22.737247] usb-storage: waiting for device to settle before scanning
Nov  2 18:32:28 kenny-desktop kernel: [   22.975524] ata2: SATA link down (SStatus 0 SControl 310)
Nov  2 18:32:28 kenny-desktop kernel: [   22.985504] scsi 0:0:0:0: Direct-Access     ATA      ST3250824AS      3.AH PQ: 0 ANSI: 5
Nov  2 18:32:28 kenny-desktop kernel: [   22.985964] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
Nov  2 18:32:28 kenny-desktop kernel: [   22.985974] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 19
Nov  2 18:32:28 kenny-desktop kernel: [   22.986016] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   22.986309] scsi3 : sata_nv
Nov  2 18:32:28 kenny-desktop kernel: [   22.986423] scsi4 : sata_nv
Nov  2 18:32:28 kenny-desktop kernel: [   22.986575] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 19
Nov  2 18:32:28 kenny-desktop kernel: [   22.986578] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 19
Nov  2 18:32:28 kenny-desktop kernel: [   23.294609] ata3: SATA link down (SStatus 0 SControl 310)
Nov  2 18:32:28 kenny-desktop kernel: [   23.614256] ata4: SATA link down (SStatus 0 SControl 310)
Nov  2 18:32:28 kenny-desktop kernel: [   23.625696] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
Nov  2 18:32:28 kenny-desktop kernel: [   23.625700] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 16
Nov  2 18:32:28 kenny-desktop kernel: [   23.625716] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   23.625719] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Nov  2 18:32:28 kenny-desktop kernel: [   23.625763] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
Nov  2 18:32:28 kenny-desktop kernel: [   23.625798] ehci_hcd 0000:00:0b.1: debug port 1
Nov  2 18:32:28 kenny-desktop kernel: [   23.625801] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Nov  2 18:32:28 kenny-desktop kernel: [   23.625808] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfe02e000
Nov  2 18:32:28 kenny-desktop kernel: [   23.626165] usb 1-2: USB disconnect, address 2
Nov  2 18:32:28 kenny-desktop kernel: [   23.635784] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  2 18:32:28 kenny-desktop kernel: [   23.635872] usb usb2: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   23.635891] hub 2-0:1.0: USB hub found
Nov  2 18:32:28 kenny-desktop kernel: [   23.635896] hub 2-0:1.0: 8 ports detected
Nov  2 18:32:28 kenny-desktop kernel: [   23.739717] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Nov  2 18:32:28 kenny-desktop kernel: [   23.739729] ACPI: PCI Interrupt 0000:03:05.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
Nov  2 18:32:28 kenny-desktop kernel: [   23.791401] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fddff000-fddff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
Nov  2 18:32:28 kenny-desktop kernel: [   23.798407] usb 1-8: USB disconnect, address 3
Nov  2 18:32:28 kenny-desktop kernel: [   23.798565] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   23.809583] pata_amd 0000:00:0d.0: version 0.3.10
Nov  2 18:32:28 kenny-desktop kernel: [   23.809638] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   23.810274] scsi5 : pata_amd
Nov  2 18:32:28 kenny-desktop kernel: [   23.810853] scsi6 : pata_amd
Nov  2 18:32:28 kenny-desktop kernel: [   23.811415] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
Nov  2 18:32:28 kenny-desktop kernel: [   23.811418] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
Nov  2 18:32:28 kenny-desktop kernel: [   23.816292] Driver 'sd' needs updating - please use bus_type methods
Nov  2 18:32:28 kenny-desktop kernel: [   23.816378] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:32:28 kenny-desktop kernel: [   23.816389] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:32:28 kenny-desktop kernel: [   23.816391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:32:28 kenny-desktop kernel: [   23.816405] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:32:28 kenny-desktop kernel: [   23.816452] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:32:28 kenny-desktop kernel: [   23.816459] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:32:28 kenny-desktop kernel: [   23.816461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:32:28 kenny-desktop kernel: [   23.816472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:32:28 kenny-desktop kernel: [   23.816475]  sda: sda1 sda2 < sda5 >
Nov  2 18:32:28 kenny-desktop kernel: [   23.861577] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  2 18:32:28 kenny-desktop kernel: [   23.865686] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov  2 18:32:28 kenny-desktop kernel: [   24.309780] ata6.00: ATAPI: ATAPI   DVD A  DH16AYH, YH13, max UDMA/66
Nov  2 18:32:28 kenny-desktop kernel: [   24.309793] ata6.00: limited to UDMA/33 due to 40-wire cable
Nov  2 18:32:28 kenny-desktop kernel: [   24.497510] ata6.00: configured for UDMA/33
Nov  2 18:32:28 kenny-desktop kernel: [   24.498925] scsi 6:0:0:0: CD-ROM            ATAPI    DVD A  DH16AYH   YH13 PQ: 0 ANSI: 5
Nov  2 18:32:28 kenny-desktop kernel: [   24.498997] scsi 6:0:0:0: Attached scsi generic sg1 type 5
Nov  2 18:32:28 kenny-desktop kernel: [   24.505566] Driver 'sr' needs updating - please use bus_type methods
Nov  2 18:32:28 kenny-desktop kernel: [   24.511369] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Nov  2 18:32:28 kenny-desktop kernel: [   24.511372] Uniform CD-ROM driver Revision: 3.20
Nov  2 18:32:28 kenny-desktop kernel: [   24.511406] sr 6:0:0:0: Attached scsi CD-ROM sr0
Nov  2 18:32:28 kenny-desktop kernel: [   24.618982] Attempting manual resume
Nov  2 18:32:28 kenny-desktop kernel: [   24.618986] swsusp: Resume From Partition 8:5
Nov  2 18:32:28 kenny-desktop kernel: [   24.618988] PM: Checking swsusp image.
Nov  2 18:32:28 kenny-desktop kernel: [   24.619155] PM: Resume from disk failed.
Nov  2 18:32:28 kenny-desktop kernel: [   24.633526] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov  2 18:32:28 kenny-desktop kernel: [   24.633531] EXT3-fs: write access will be enabled during recovery.
Nov  2 18:32:28 kenny-desktop kernel: [   24.650677] usb 1-2: new low speed USB device using ohci_hcd and address 4
Nov  2 18:32:28 kenny-desktop kernel: [   24.863198] usb 1-2: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   24.875928] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input3
Nov  2 18:32:28 kenny-desktop kernel: [   24.894454] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:0b.0-2
Nov  2 18:32:28 kenny-desktop kernel: [   25.068784] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000beef6e]
Nov  2 18:32:28 kenny-desktop kernel: [   25.198074] usb 1-8: new full speed USB device using ohci_hcd and address 5
Nov  2 18:32:28 kenny-desktop kernel: [   25.413185] usb 1-8: configuration #1 chosen from 1 choice
Nov  2 18:32:28 kenny-desktop kernel: [   25.416226] scsi7 : SCSI emulation for USB Mass Storage devices
Nov  2 18:32:28 kenny-desktop kernel: [   25.415720] usb-storage: device found at 5
Nov  2 18:32:28 kenny-desktop kernel: [   25.415723] usb-storage: waiting for device to settle before scanning
Nov  2 18:32:28 kenny-desktop kernel: [   25.996464] kjournald starting.  Commit interval 5 seconds
Nov  2 18:32:28 kenny-desktop kernel: [   25.997038] EXT3-fs: sda1: orphan cleanup on readonly fs
Nov  2 18:32:28 kenny-desktop kernel: [   26.018250] ext3_orphan_cleanup: deleting unreferenced inode 13304500
Nov  2 18:32:28 kenny-desktop kernel: [   26.124256] ext3_orphan_cleanup: deleting unreferenced inode 14966805
Nov  2 18:32:28 kenny-desktop kernel: [   26.143873] ext3_orphan_cleanup: deleting unreferenced inode 5521413
Nov  2 18:32:28 kenny-desktop kernel: [   26.143881] ext3_orphan_cleanup: deleting unreferenced inode 5521412
Nov  2 18:32:28 kenny-desktop kernel: [   26.143887] ext3_orphan_cleanup: deleting unreferenced inode 5521411
Nov  2 18:32:28 kenny-desktop kernel: [   26.143893] ext3_orphan_cleanup: deleting unreferenced inode 5521410
Nov  2 18:32:28 kenny-desktop kernel: [   26.143898] ext3_orphan_cleanup: deleting unreferenced inode 5521409
Nov  2 18:32:28 kenny-desktop kernel: [   26.143902] EXT3-fs: sda1: 7 orphan inodes deleted
Nov  2 18:32:28 kenny-desktop kernel: [   26.143904] EXT3-fs: recovery complete.
Nov  2 18:32:28 kenny-desktop kernel: [   26.147543] EXT3-fs: mounted filesystem with ordered data mode.
Nov  2 18:32:28 kenny-desktop kernel: [   30.408935] usb-storage: device scan complete
Nov  2 18:32:28 kenny-desktop kernel: [   30.415345] scsi 7:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.422336] scsi 7:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.429325] scsi 7:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.436324] scsi 7:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.447349] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Nov  2 18:32:28 kenny-desktop kernel: [   30.447372] sd 7:0:0:0: Attached scsi generic sg2 type 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.458315] sd 7:0:0:1: [sdc] Attached SCSI removable disk
Nov  2 18:32:28 kenny-desktop kernel: [   30.458335] sd 7:0:0:1: Attached scsi generic sg3 type 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.469300] sd 7:0:0:2: [sdd] Attached SCSI removable disk
Nov  2 18:32:28 kenny-desktop kernel: [   30.469319] sd 7:0:0:2: Attached scsi generic sg4 type 0
Nov  2 18:32:28 kenny-desktop kernel: [   30.480286] sd 7:0:0:3: [sde] Attached SCSI removable disk
Nov  2 18:32:28 kenny-desktop kernel: [   30.480307] sd 7:0:0:3: Attached scsi generic sg5 type 0
Nov  2 18:32:28 kenny-desktop kernel: [   37.403068] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  2 18:32:28 kenny-desktop kernel: [   37.442984] nf_conntrack version 0.5.0 (15360 buckets, 61440 max)
Nov  2 18:32:28 kenny-desktop kernel: [   38.060088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  2 18:32:28 kenny-desktop kernel: [   38.090393] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  2 18:32:28 kenny-desktop kernel: [   38.183581] input: Power Button (FF) as /devices/virtual/input/input4
Nov  2 18:32:28 kenny-desktop kernel: [   38.207811] ACPI: Power Button (FF) [PWRF]
Nov  2 18:32:28 kenny-desktop kernel: [   38.207933] input: Power Button (CM) as /devices/virtual/input/input5
Nov  2 18:32:28 kenny-desktop kernel: [   38.241444] ACPI: Power Button (CM) [PWRB]
Nov  2 18:32:28 kenny-desktop kernel: [   38.245778] Linux agpgart interface v0.102
Nov  2 18:32:28 kenny-desktop kernel: [   38.291623] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Nov  2 18:32:28 kenny-desktop kernel: [   38.291642] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Nov  2 18:32:28 kenny-desktop kernel: [   38.437791] nvidia: module license 'NVIDIA' taints kernel.
Nov  2 18:32:28 kenny-desktop kernel: [   39.055836] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
Nov  2 18:32:28 kenny-desktop kernel: [   39.055849] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 21
Nov  2 18:32:28 kenny-desktop kernel: [   39.055856] PCI: Setting latency timer of device 0000:00:05.0 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   39.056092] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Nov  2 18:32:28 kenny-desktop kernel: [   39.521319] input: PC Speaker as /devices/platform/pcspkr/input/input6
Nov  2 18:32:28 kenny-desktop kernel: [   40.038104] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
Nov  2 18:32:28 kenny-desktop kernel: [   40.038110] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
Nov  2 18:32:28 kenny-desktop kernel: [   40.038136] PCI: Setting latency timer of device 0000:00:10.1 to 64
Nov  2 18:32:28 kenny-desktop kernel: [   40.072497] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Nov  2 18:32:28 kenny-desktop kernel: [   41.260731] lp: driver loaded but no devices found
Nov  2 18:32:28 kenny-desktop kernel: [   41.367462] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
Nov  2 18:32:28 kenny-desktop kernel: [   41.928887] EXT3 FS on sda1, internal journal
Nov  2 18:32:28 kenny-desktop kernel: [   42.113423] device-mapper: uevent: version 1.0.3
Nov  2 18:32:28 kenny-desktop kernel: [   42.113451] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
Nov  2 18:32:28 kenny-desktop kernel: [   43.929296] No dock devices found.
Nov  2 18:32:28 kenny-desktop kernel: [   44.255382] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
Nov  2 18:32:28 kenny-desktop kernel: [   44.254891] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
Nov  2 18:32:28 kenny-desktop kernel: [   44.254895] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
Nov  2 18:32:28 kenny-desktop kernel: [   44.254897] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
Nov  2 18:32:28 kenny-desktop kernel: [   44.254899] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Nov  2 18:32:30 kenny-desktop kernel: [   47.068812] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov  2 18:32:30 kenny-desktop kernel: [   47.068818] apm: disabled - APM is not SMP safe.
Nov  2 18:32:31 kenny-desktop kernel: [   47.247837] ppdev: user-space parallel port driver
Nov  2 18:32:31 kenny-desktop kernel: [   47.618736] audit(1225668751.523:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5583 profile="/usr/sbin/cupsd" namespace="default"
Nov  2 18:32:32 kenny-desktop kernel: [   48.634240] NET: Registered protocol family 10
Nov  2 18:32:32 kenny-desktop kernel: [   48.634787] lo: Disabled Privacy Extensions
Nov  2 18:32:32 kenny-desktop kernel: [   48.713638] Clocksource tsc unstable (delta = -85112548 ns)
Nov  2 18:32:37 kenny-desktop kernel: [   50.695486] Bluetooth: Core ver 2.11
Nov  2 18:32:37 kenny-desktop kernel: [   50.695740] NET: Registered protocol family 31
Nov  2 18:32:37 kenny-desktop kernel: [   50.695742] Bluetooth: HCI device and connection manager initialized
Nov  2 18:32:37 kenny-desktop kernel: [   50.695746] Bluetooth: HCI socket layer initialized
Nov  2 18:32:37 kenny-desktop kernel: [   50.731148] Bluetooth: L2CAP ver 2.9
Nov  2 18:32:37 kenny-desktop kernel: [   50.731152] Bluetooth: L2CAP socket layer initialized
Nov  2 18:32:37 kenny-desktop kernel: [   50.824324] Bluetooth: RFCOMM socket layer initialized
Nov  2 18:32:37 kenny-desktop kernel: [   50.824334] Bluetooth: RFCOMM TTY layer initialized
Nov  2 18:32:37 kenny-desktop kernel: [   50.824336] Bluetooth: RFCOMM ver 1.8
Nov  2 18:32:37 kenny-desktop kernel: [   50.944558] NET: Registered protocol family 17
Nov  2 18:32:44 kenny-desktop kernel: [   54.163348] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=152 DF PROTO=TCP SPT=64048 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:32:47 kenny-desktop kernel: [   55.521911] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=218 DF PROTO=TCP SPT=64048 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:32:49 kenny-desktop kernel: [   56.116739] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.22.25.3 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1961 DF PROTO=TCP SPT=65197 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:32:50 kenny-desktop kernel: [   56.971239] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=249 DF PROTO=TCP SPT=64049 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:32:53 kenny-desktop kernel: [   57.944978] eth0: no IPv6 routers present
Nov  2 18:32:53 kenny-desktop kernel: [   58.246201] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=301 DF PROTO=TCP SPT=64048 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:32:53 kenny-desktop kernel: [   58.327918] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=115 ID=303 DF PROTO=TCP SPT=64049 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:32:57 kenny-desktop kernel: [   60.146777] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=198.105.194.180 DST=72.240.205.252 LEN=47 TOS=0x00 PREC=0x00 TTL=50 ID=33543 DF PROTO=TCP SPT=80 DPT=35758 WINDOW=5840 RES=0x00 ACK PSH URGP=0 
Nov  2 18:32:59 kenny-desktop kernel: [   61.751723] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=384 DF PROTO=TCP SPT=64049 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:33:06 kenny-desktop kernel: [   67.494081] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=121.97.244.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=16612 DF PROTO=TCP SPT=4233 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:33:09 kenny-desktop kernel: [   70.288707] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=121.97.244.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=17405 DF PROTO=TCP SPT=4233 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:33:12 kenny-desktop kernel: [   73.523934] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=121.97.244.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=18545 DF PROTO=TCP SPT=4234 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:33:15 kenny-desktop kernel: [   76.433448] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=121.97.244.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=19675 DF PROTO=TCP SPT=4234 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:33:21 kenny-desktop kernel: [   82.401208] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=121.97.244.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=22407 DF PROTO=TCP SPT=4234 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:33:50 kenny-desktop kernel: [   98.238698] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=198.105.194.180 DST=72.240.205.252 LEN=143 TOS=0x00 PREC=0x00 TTL=50 ID=9933 DF PROTO=TCP SPT=80 DPT=57618 WINDOW=5840 RES=0x00 ACK PSH URGP=0 
Nov  2 18:34:04 kenny-desktop kernel: [   99.919351] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  2 18:34:04 kenny-desktop kernel: [   99.919358] ata1: SError: { 10B8B Dispar }
Nov  2 18:34:04 kenny-desktop kernel: [   99.919364] ata1.00: cmd 35/00:08:b7:25:8d/00:00:1c:00:00/e0 tag 0 dma 4096 out
Nov  2 18:34:04 kenny-desktop kernel: [   99.919365]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Nov  2 18:34:04 kenny-desktop kernel: [   99.919367] ata1.00: status: { DRDY }
Nov  2 18:34:04 kenny-desktop kernel: [  102.349515] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  2 18:34:04 kenny-desktop kernel: [  104.485461] ata1: device not ready (errno=-16), forcing hardreset
Nov  2 18:34:04 kenny-desktop kernel: [  104.485466] ata1: hard resetting link
Nov  2 18:34:04 kenny-desktop kernel: [  104.701600] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:34:04 kenny-desktop kernel: [  104.712581] ata1.00: configured for UDMA/100
Nov  2 18:34:04 kenny-desktop kernel: [  104.712589] ata1: EH complete
Nov  2 18:34:04 kenny-desktop kernel: [  104.712822] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:34:04 kenny-desktop kernel: [  104.712491] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:34:04 kenny-desktop kernel: [  104.712494] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:34:04 kenny-desktop kernel: [  104.712600] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:34:06 kenny-desktop kernel: [  105.537580] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=198.105.194.180 DST=72.240.205.252 LEN=47 TOS=0x00 PREC=0x00 TTL=50 ID=33545 DF PROTO=TCP SPT=80 DPT=35758 WINDOW=5840 RES=0x00 ACK PSH URGP=0 
Nov  2 18:34:07 kenny-desktop kernel: [  105.810937] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=24285 DF PROTO=TCP SPT=2756 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:08 kenny-desktop kernel: [  106.899944] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=53678 DF PROTO=TCP SPT=3920 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:10 kenny-desktop kernel: [  108.279253] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=24600 DF PROTO=TCP SPT=2756 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:11 kenny-desktop kernel: [  109.851872] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=54093 DF PROTO=TCP SPT=3920 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:13 kenny-desktop kernel: [  110.820081] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=24910 DF PROTO=TCP SPT=2757 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:14 kenny-desktop kernel: [  111.516206] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=54734 DF PROTO=TCP SPT=3921 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:16 kenny-desktop kernel: [  112.152516] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=25253 DF PROTO=TCP SPT=2757 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:17 kenny-desktop kernel: [  112.868123] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=55528 DF PROTO=TCP SPT=3921 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:22 kenny-desktop kernel: [  114.845877] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=25909 DF PROTO=TCP SPT=2757 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:34:23 kenny-desktop kernel: [  115.573731] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=57016 DF PROTO=TCP SPT=3921 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
```

---

### Post by userundefine on 2008-11-02
yikes!  Please edit that and wrap it in [ CODE ] tags.  This will make it much more readable and keep the formatting.

Also, was there anything BEFORE the start of the part of this log?  Because from the very beginning it looks like you've just started the booting process.  What will help you is to know what was logged JUST BEFORE you booted, meaning if you pressed the button to turn the comp off and then back on, what caused the lockup would be the last thing in the log (if it *did* log it).  Look for what was just before the part you posted.

---

### Post by carl99fan on 2008-11-02
I don't think what we are looking for is there.
here is the code just before the one I posted earlier.

```
Nov  2 17:27:54 kenny-desktop kernel: [  398.655407] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=198.105.194.180 DST=72.240.205.252 LEN=202 TOS=0x00 PREC=0x00 TTL=50 ID=54595 DF PROTO=TCP SPT=80 DPT=47133 WINDOW=5840 RES=0x00 ACK PSH URGP=0 
Nov  2 17:29:54 kenny-desktop kernel: [  454.826086] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=198.105.194.180 DST=72.240.205.252 LEN=202 TOS=0x00 PREC=0x00 TTL=50 ID=54596 DF PROTO=TCP SPT=80 DPT=47133 WINDOW=5840 RES=0x00 ACK PSH URGP=0 
Nov  2 17:41:30 kenny-desktop kernel: [  806.021130] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.26.172.49 DST=72.240.205.252 LEN=63 TOS=0x00 PREC=0x00 TTL=113 ID=28742 PROTO=UDP SPT=47543 DPT=49121 LEN=43 
Nov  2 17:53:32 kenny-desktop kernel: [ 1211.205646] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.26.248.114 DST=72.240.205.252 LEN=63 TOS=0x00 PREC=0x00 TTL=113 ID=2962 PROTO=UDP SPT=36127 DPT=49121 LEN=43 
Nov  2 17:57:24 kenny-desktop kernel: [ 1332.778277] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=82.10.90.191 DST=72.240.205.252 LEN=59 TOS=0x00 PREC=0x00 TTL=113 ID=41226 PROTO=UDP SPT=36609 DPT=49121 LEN=39 
Nov  2 18:09:37 kenny-desktop kernel: [ 1825.806051] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.197.189.55 DST=72.240.205.252 LEN=201 TOS=0x00 PREC=0x00 TTL=114 ID=8213 PROTO=UDP SPT=63349 DPT=42967 LEN=181 
Nov  2 18:09:46 kenny-desktop kernel: [ 1834.218879] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.201.166.141 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=115 ID=54246 PROTO=UDP SPT=1031 DPT=42967 LEN=31 
Nov  2 18:09:46 kenny-desktop kernel: [ 1834.241974] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=36355 PROTO=UDP SPT=5891 DPT=42967 LEN=31 
Nov  2 18:09:46 kenny-desktop kernel: [ 1834.244829] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.124.201.88 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=115 ID=16347 PROTO=UDP SPT=5814 DPT=42967 LEN=31 
Nov  2 18:09:47 kenny-desktop kernel: [ 1834.274301] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=173.32.111.12 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=41470 PROTO=UDP SPT=31678 DPT=42967 LEN=31 
Nov  2 18:09:47 kenny-desktop kernel: [ 1834.464332] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.68.72.231 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=41140 PROTO=UDP SPT=35785 DPT=42967 LEN=31 
Nov  2 18:09:47 kenny-desktop kernel: [ 1834.507474] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=71.201.42.128 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=115 ID=42176 PROTO=UDP SPT=60155 DPT=42967 LEN=31 
Nov  2 18:09:47 kenny-desktop kernel: [ 1834.546077] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.102.136.211 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=111 ID=50438 PROTO=UDP SPT=50307 DPT=42967 LEN=31 
Nov  2 18:09:47 kenny-desktop kernel: [ 1834.930784] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.17.126.136 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=1977 PROTO=UDP SPT=55154 DPT=42967 LEN=31 
Nov  2 18:09:49 kenny-desktop kernel: [ 1836.682520] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=111 ID=21561 PROTO=UDP SPT=4039 DPT=42967 LEN=31 
Nov  2 18:09:50 kenny-desktop kernel: [ 1836.725647] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=22820 DF PROTO=TCP SPT=54172 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:09:50 kenny-desktop kernel: [ 1836.813312] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=116 ID=9319 PROTO=UDP SPT=27314 DPT=42967 LEN=31 
Nov  2 18:09:50 kenny-desktop kernel: [ 1836.846261] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.226.76.254 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=22220 DF PROTO=TCP SPT=3251 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:09:50 kenny-desktop kernel: [ 1836.847238] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.176.17.182 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=115 ID=26197 PROTO=UDP SPT=2262 DPT=42967 LEN=31 
Nov  2 18:09:50 kenny-desktop kernel: [ 1836.881330] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.7.241.35 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=118 ID=11897 PROTO=UDP SPT=29896 DPT=42967 LEN=31 
Nov  2 18:09:50 kenny-desktop kernel: [ 1837.050732] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=12.217.45.185 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=32253 PROTO=UDP SPT=33855 DPT=42967 LEN=31 
Nov  2 18:09:51 kenny-desktop kernel: [ 1838.317091] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=99.252.125.188 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=111 ID=23656 PROTO=UDP SPT=6956 DPT=42967 LEN=31 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.172097] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=23070 DF PROTO=TCP SPT=54172 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.296918] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.226.76.254 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=22552 DF PROTO=TCP SPT=3251 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.306003] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.141.240.35 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=110 ID=39002 PROTO=UDP SPT=29406 DPT=42967 LEN=31 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.370192] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.124.211.137 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=54152 DF PROTO=TCP SPT=3926 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.638846] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=189.103.161.3 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=35297 DF PROTO=TCP SPT=1890 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:09:53 kenny-desktop kernel: [ 1839.732905] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.163.65.230 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=116 ID=27802 PROTO=UDP SPT=46236 DPT=42967 LEN=31 
Nov  2 18:09:56 kenny-desktop kernel: [ 1841.817422] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=23311 DF PROTO=TCP SPT=54173 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:09:56 kenny-desktop kernel: [ 1841.916991] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.226.76.254 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=22822 DF PROTO=TCP SPT=3252 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:09:56 kenny-desktop kernel: [ 1842.008558] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.124.211.137 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=55056 DF PROTO=TCP SPT=3926 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:09:56 kenny-desktop kernel: [ 1842.251920] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=189.103.161.3 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=35508 DF PROTO=TCP SPT=1890 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:09:59 kenny-desktop kernel: [ 1843.466571] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=23517 DF PROTO=TCP SPT=54172 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:09:59 kenny-desktop kernel: [ 1843.466594] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=23518 DF PROTO=TCP SPT=54173 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:09:59 kenny-desktop kernel: [ 1843.502637] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.226.76.254 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=23073 DF PROTO=TCP SPT=3252 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:10:01 kenny-desktop kernel: [ 1844.730826] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.125.138.198 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=12216 DF PROTO=TCP SPT=51850 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:02 kenny-desktop kernel: [ 1844.909084] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.124.211.137 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=56629 DF PROTO=TCP SPT=3927 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:02 kenny-desktop kernel: [ 1845.088520] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=189.103.161.3 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=35943 DF PROTO=TCP SPT=1894 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:04 kenny-desktop kernel: [ 1846.091309] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.125.138.198 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=12908 DF PROTO=TCP SPT=51850 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:05 kenny-desktop kernel: [ 1846.190873] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=23957 DF PROTO=TCP SPT=54173 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:05 kenny-desktop kernel: [ 1846.240613] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.226.76.254 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=23599 DF PROTO=TCP SPT=3252 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:10:07 kenny-desktop kernel: [ 1847.769109] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.125.138.198 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=13658 DF PROTO=TCP SPT=51851 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:08 kenny-desktop kernel: [ 1848.093572] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.124.211.137 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=59307 DF PROTO=TCP SPT=3927 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:08 kenny-desktop kernel: [ 1848.586070] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=189.103.161.3 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=36308 DF PROTO=TCP SPT=1894 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:09 kenny-desktop kernel: [ 1849.720816] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=61764 DF PROTO=TCP SPT=3030 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:10 kenny-desktop kernel: [ 1850.492338] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.125.138.198 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=14385 DF PROTO=TCP SPT=51851 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:12 kenny-desktop kernel: [ 1852.143728] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=62532 DF PROTO=TCP SPT=3030 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:15 kenny-desktop kernel: [ 1854.878367] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=63073 DF PROTO=TCP SPT=3035 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:16 kenny-desktop kernel: [ 1855.104017] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.170.185.143 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=119 ID=21813 PROTO=UDP SPT=7708 DPT=42967 LEN=31 
Nov  2 18:10:16 kenny-desktop kernel: [ 1855.312286] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.125.138.198 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=15823 DF PROTO=TCP SPT=51851 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:18 kenny-desktop kernel: [ 1856.843137] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=63665 DF PROTO=TCP SPT=3035 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:24 kenny-desktop kernel: [ 1862.414741] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.63.220.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=42384 DF PROTO=TCP SPT=3614 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:24 kenny-desktop kernel: [ 1862.874732] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=65368 DF PROTO=TCP SPT=3035 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:27 kenny-desktop kernel: [ 1865.402269] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.63.220.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=42620 DF PROTO=TCP SPT=3614 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:29 kenny-desktop kernel: [ 1867.895839] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=17218 DF PROTO=TCP SPT=51138 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:30 kenny-desktop kernel: [ 1868.289379] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.63.220.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=42856 DF PROTO=TCP SPT=3616 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:31 kenny-desktop kernel: [ 1869.203442] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.240.213.181 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=34102 DF PROTO=TCP SPT=62318 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:32 kenny-desktop kernel: [ 1870.451183] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=17365 DF PROTO=TCP SPT=51138 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:33 kenny-desktop kernel: [ 1870.753469] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.63.220.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=43136 DF PROTO=TCP SPT=3616 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:34 kenny-desktop kernel: [ 1871.622844] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.240.213.181 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=34585 DF PROTO=TCP SPT=62318 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:35 kenny-desktop kernel: [ 1872.909166] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=110 ID=17454 DF PROTO=TCP SPT=51141 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:37 kenny-desktop kernel: [ 1874.107156] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.240.213.181 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=35070 DF PROTO=TCP SPT=62319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:37 kenny-desktop kernel: [ 1874.278674] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.66.83.200 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=13798 DF PROTO=TCP SPT=51097 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:38 kenny-desktop kernel: [ 1875.463617] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=17571 DF PROTO=TCP SPT=51138 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:38 kenny-desktop kernel: [ 1875.469918] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=110 ID=17573 DF PROTO=TCP SPT=51141 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:39 kenny-desktop kernel: [ 1875.847564] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.63.220.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=43653 DF PROTO=TCP SPT=3616 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:40 kenny-desktop kernel: [ 1876.664096] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=12781 DF PROTO=TCP SPT=49960 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:40 kenny-desktop kernel: [ 1876.810244] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.240.213.181 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=35531 DF PROTO=TCP SPT=62319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:40 kenny-desktop kernel: [ 1877.096028] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.66.83.200 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=14005 DF PROTO=TCP SPT=51097 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:43 kenny-desktop kernel: [ 1879.176724] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=12986 DF PROTO=TCP SPT=49960 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:43 kenny-desktop kernel: [ 1879.612338] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.66.83.200 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=14224 DF PROTO=TCP SPT=51098 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:44 kenny-desktop kernel: [ 1880.884049] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.182.121.82 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=110 ID=17885 DF PROTO=TCP SPT=51141 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:46 kenny-desktop kernel: [ 1882.099630] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=13158 DF PROTO=TCP SPT=49961 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:46 kenny-desktop kernel: [ 1882.273677] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.240.213.181 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=36386 DF PROTO=TCP SPT=62319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:46 kenny-desktop kernel: [ 1882.541066] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.66.83.200 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=14411 DF PROTO=TCP SPT=51098 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:49 kenny-desktop kernel: [ 1884.648663] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=13369 DF PROTO=TCP SPT=49960 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:49 kenny-desktop kernel: [ 1884.657035] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=13371 DF PROTO=TCP SPT=49961 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:49 kenny-desktop kernel: [ 1885.183461] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.108.198.89 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=59011 DF PROTO=TCP SPT=31462 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:52 kenny-desktop kernel: [ 1887.482941] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.66.83.200 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=14824 DF PROTO=TCP SPT=51098 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:52 kenny-desktop kernel: [ 1887.719323] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.108.198.89 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=59367 DF PROTO=TCP SPT=31462 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:53 kenny-desktop kernel: [ 1887.946272] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=39705 DF PROTO=TCP SPT=4999 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:55 kenny-desktop kernel: [ 1889.562547] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.188.187.222 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=13711 DF PROTO=TCP SPT=49961 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:10:55 kenny-desktop kernel: [ 1890.203284] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.108.198.89 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=59777 DF PROTO=TCP SPT=31464 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:56 kenny-desktop kernel: [ 1890.404224] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=40357 DF PROTO=TCP SPT=4999 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:57 kenny-desktop kernel: [ 1891.797889] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=45205 DF PROTO=TCP SPT=3967 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:58 kenny-desktop kernel: [ 1892.644105] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.108.198.89 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=60174 DF PROTO=TCP SPT=31464 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:10:59 kenny-desktop kernel: [ 1892.850668] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=40939 DF PROTO=TCP SPT=1027 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:00 kenny-desktop kernel: [ 1894.262894] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=45362 DF PROTO=TCP SPT=3967 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:02 kenny-desktop kernel: [ 1895.239769] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=41770 DF PROTO=TCP SPT=1027 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:03 kenny-desktop kernel: [ 1896.702332] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=45516 DF PROTO=TCP SPT=3968 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:04 kenny-desktop kernel: [ 1897.463326] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.108.198.89 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=61000 DF PROTO=TCP SPT=31464 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:06 kenny-desktop kernel: [ 1899.115103] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=45672 DF PROTO=TCP SPT=3968 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:08 kenny-desktop kernel: [ 1900.171031] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.125.173.225 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=42955 DF PROTO=TCP SPT=1027 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:12 kenny-desktop kernel: [ 1903.961665] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.119.196.102 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=46003 DF PROTO=TCP SPT=3968 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.226792] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.224.30.13 DST=72.240.205.252 LEN=105 TOS=0x00 PREC=0x00 TTL=117 ID=30567 PROTO=UDP SPT=38182 DPT=42967 LEN=85 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.362515] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=99.175.94.170 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=117 ID=16182 PROTO=UDP SPT=46064 DPT=42967 LEN=31 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.368778] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.68.177.214 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=118 ID=6400 PROTO=UDP SPT=27125 DPT=42967 LEN=31 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.403195] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.229.99.28 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=118 ID=19604 PROTO=UDP SPT=22307 DPT=42967 LEN=31 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.427008] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=71.195.20.202 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=116 ID=3586 PROTO=UDP SPT=32968 DPT=42967 LEN=31 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.577488] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=201.83.17.123 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=117 ID=9233 PROTO=UDP SPT=38736 DPT=42967 LEN=31 
Nov  2 18:11:13 kenny-desktop kernel: [ 1904.623782] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=116 ID=27286 PROTO=UDP SPT=29859 DPT=42967 LEN=31 
Nov  2 18:11:18 kenny-desktop kernel: [ 1908.458268] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.72.105.154 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=11074 PROTO=UDP SPT=6192 DPT=42967 LEN=31 
Nov  2 18:11:18 kenny-desktop kernel: [ 1909.020757] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=201.106.7.29 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=116 ID=43799 PROTO=UDP SPT=63840 DPT=42967 LEN=31 
Nov  2 18:11:26 kenny-desktop kernel: [ 1915.054450] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=112 ID=10246 PROTO=UDP SPT=41248 DPT=42967 LEN=31 
Nov  2 18:11:53 kenny-desktop kernel: [ 1938.862176] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.190.41.170 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=13974 PROTO=UDP SPT=16735 DPT=42967 LEN=31 
Nov  2 18:12:23 kenny-desktop kernel: [ 1964.979887] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.93.252.110 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=107 ID=53726 PROTO=UDP SPT=49134 DPT=42967 LEN=31 
Nov  2 18:12:30 kenny-desktop kernel: [ 1972.168775] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.189.146.109 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=107 ID=65449 PROTO=UDP SPT=40189 DPT=42967 LEN=31 
Nov  2 18:12:30 kenny-desktop kernel: [ 1972.257943] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.189.174.55 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=49984 DF PROTO=TCP SPT=1585 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:12:30 kenny-desktop kernel: [ 1972.723850] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=5433 DF PROTO=TCP SPT=49388 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:33 kenny-desktop kernel: [ 1975.179860] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.189.174.55 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=50494 DF PROTO=TCP SPT=1585 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:12:33 kenny-desktop kernel: [ 1975.712622] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=5561 DF PROTO=TCP SPT=49388 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:36 kenny-desktop kernel: [ 1978.245826] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.189.174.55 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=50839 DF PROTO=TCP SPT=1589 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:12:36 kenny-desktop kernel: [ 1978.719014] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=5704 DF PROTO=TCP SPT=49389 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:39 kenny-desktop kernel: [ 1981.213605] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.189.174.55 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=51169 DF PROTO=TCP SPT=1589 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:12:39 kenny-desktop kernel: [ 1981.708239] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=5825 DF PROTO=TCP SPT=49388 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:39 kenny-desktop kernel: [ 1981.710737] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=5826 DF PROTO=TCP SPT=49389 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:45 kenny-desktop kernel: [ 1986.858945] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.189.174.55 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=51587 DF PROTO=TCP SPT=1589 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:12:45 kenny-desktop kernel: [ 1987.317477] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.232.174.27 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=6008 DF PROTO=TCP SPT=49389 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:12:57 kenny-desktop kernel: [ 1998.295236] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=52 TOS=0x08 PREC=0x80 TTL=115 ID=802 DF PROTO=TCP SPT=52562 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:00 kenny-desktop kernel: [ 2000.497875] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=52 TOS=0x08 PREC=0x80 TTL=115 ID=1040 DF PROTO=TCP SPT=52562 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:03 kenny-desktop kernel: [ 2003.286743] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=52 TOS=0x08 PREC=0x80 TTL=115 ID=1305 DF PROTO=TCP SPT=52568 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:06 kenny-desktop kernel: [ 2006.401530] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=42301 DF PROTO=TCP SPT=2224 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:13:07 kenny-desktop kernel: [ 2007.098052] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=52 TOS=0x08 PREC=0x80 TTL=115 ID=1503 DF PROTO=TCP SPT=52568 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:07 kenny-desktop kernel: [ 2007.098313] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=48 TOS=0x08 PREC=0x80 TTL=115 ID=1502 DF PROTO=TCP SPT=52562 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:09 kenny-desktop kernel: [ 2008.838864] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=42703 DF PROTO=TCP SPT=2224 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:13:12 kenny-desktop kernel: [ 2010.634441] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=92.41.226.176 DST=72.240.205.252 LEN=48 TOS=0x08 PREC=0x80 TTL=115 ID=1812 DF PROTO=TCP SPT=52568 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:12 kenny-desktop kernel: [ 2011.290928] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=43207 DF PROTO=TCP SPT=2225 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:13:15 kenny-desktop kernel: [ 2014.154167] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=43572 DF PROTO=TCP SPT=2225 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260668] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260675] ata1.00: BMDMA stat 0x5
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260677] ata1: SError: { 10B8B Dispar BadCRC }
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260683] ata1.00: cmd 25/00:58:3f:99:1e/00:00:1b:00:00/e0 tag 0 dma 45056 in
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260684]          res 51/84:58:3f:99:1e/84:00:1b:00:00/e0 Emask 0x10 (ATA bus error)
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260687] ata1.00: status: { DRDY ERR }
Nov  2 18:13:16 kenny-desktop kernel: [ 2015.260688] ata1.00: error: { ICRC ABRT }
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.571577] ata1: soft resetting link
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.727424] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.906380] ata1.00: configured for UDMA/100
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.906397] ata1: EH complete
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.927287] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.927779] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.927783] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:13:17 kenny-desktop kernel: [ 2015.928456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:13:20 kenny-desktop kernel: [ 2018.624009] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.22.86.114 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=26777 DF PROTO=TCP SPT=62278 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:13:20 kenny-desktop kernel: [ 2019.024717] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=23120 DF PROTO=TCP SPT=49796 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:21 kenny-desktop kernel: [ 2019.861903] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=142.161.210.236 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=44410 DF PROTO=TCP SPT=2225 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:13:23 kenny-desktop kernel: [ 2021.526737] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.22.86.114 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=27033 DF PROTO=TCP SPT=62279 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:13:23 kenny-desktop kernel: [ 2021.762852] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=23213 DF PROTO=TCP SPT=49796 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:26 kenny-desktop kernel: [ 2024.135158] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.22.86.114 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=27851 DF PROTO=TCP SPT=62280 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:13:26 kenny-desktop kernel: [ 2024.216852] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=23310 DF PROTO=TCP SPT=49797 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:29 kenny-desktop kernel: [ 2026.597369] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.22.86.114 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=28652 DF PROTO=TCP SPT=62280 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:13:29 kenny-desktop kernel: [ 2026.695216] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=111 ID=23409 DF PROTO=TCP SPT=49797 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:29 kenny-desktop kernel: [ 2026.695245] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=23408 DF PROTO=TCP SPT=49796 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:35 kenny-desktop kernel: [ 2031.491285] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.22.86.114 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=29795 DF PROTO=TCP SPT=62281 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:13:35 kenny-desktop kernel: [ 2031.870720] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=98.24.53.5 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=23610 DF PROTO=TCP SPT=49797 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:13:43 kenny-desktop kernel: [ 2039.076040] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=54334 DF PROTO=TCP SPT=2495 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:13:46 kenny-desktop kernel: [ 2041.542096] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=55971 DF PROTO=TCP SPT=2495 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:13:49 kenny-desktop kernel: [ 2043.980142] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=58072 DF PROTO=TCP SPT=2501 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:13:52 kenny-desktop kernel: [ 2046.386229] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=59808 DF PROTO=TCP SPT=2501 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:13:58 kenny-desktop kernel: [ 2051.995673] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=63428 DF PROTO=TCP SPT=2501 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:03 kenny-desktop kernel: [ 2055.935307] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=99.239.0.43 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=114 ID=15883 PROTO=UDP SPT=6348 DPT=42967 LEN=40 
Nov  2 18:14:16 kenny-desktop kernel: [ 2068.245584] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=1516 DF PROTO=TCP SPT=1516 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.190989] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=1834 DF PROTO=TCP SPT=1516 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823065] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823071] ata1.00: BMDMA stat 0x5
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823074] ata1: SError: { 10B8B Dispar BadCRC }
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823079] ata1.00: cmd 25/00:b8:cf:e0:8e/00:00:1c:00:00/e0 tag 0 dma 94208 in
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823081]          res 51/84:b8:cf:e0:8e/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823093] ata1.00: status: { DRDY ERR }
Nov  2 18:14:19 kenny-desktop kernel: [ 2071.823095] ata1.00: error: { ICRC ABRT }
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.136373] ata1: soft resetting link
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.290627] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.313828] ata1.00: configured for UDMA/100
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.313847] ata1: EH complete
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.326866] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.328398] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.328401] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:14:20 kenny-desktop kernel: [ 2072.396181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:14:22 kenny-desktop kernel: [ 2074.236063] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=2104 DF PROTO=TCP SPT=1517 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:25 kenny-desktop kernel: [ 2077.118556] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=2333 DF PROTO=TCP SPT=1517 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:31 kenny-desktop kernel: [ 2083.149760] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=2877 DF PROTO=TCP SPT=1517 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:14:35 kenny-desktop kernel: [ 2087.149744] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=71.190.249.178 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=112 ID=50800 PROTO=UDP SPT=23819 DPT=42967 LEN=31 
Nov  2 18:15:57 kenny-desktop kernel: [ 2161.698665] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.226.17.41 DST=72.240.205.252 LEN=63 TOS=0x00 PREC=0x00 TTL=117 ID=310 PROTO=UDP SPT=20254 DPT=49121 LEN=43 
Nov  2 18:17:01 kenny-desktop kernel: [ 2222.382144] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.229.189.229 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=49739 DF PROTO=TCP SPT=1156 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:04 kenny-desktop kernel: [ 2224.818011] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.229.189.229 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=50016 DF PROTO=TCP SPT=1156 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:07 kenny-desktop kernel: [ 2227.304769] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.229.189.229 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=50503 DF PROTO=TCP SPT=1157 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:08 kenny-desktop kernel: [ 2228.063438] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16454 DF PROTO=TCP SPT=1286 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:10 kenny-desktop kernel: [ 2229.860682] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.229.189.229 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=50732 DF PROTO=TCP SPT=1157 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:11 kenny-desktop kernel: [ 2230.411260] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16675 DF PROTO=TCP SPT=1286 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:14 kenny-desktop kernel: [ 2232.901538] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=16913 DF PROTO=TCP SPT=1287 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:16 kenny-desktop kernel: [ 2234.792811] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.229.189.229 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=51294 DF PROTO=TCP SPT=1157 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:17 kenny-desktop kernel: [ 2235.326236] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17117 DF PROTO=TCP SPT=1287 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:17:23 kenny-desktop kernel: [ 2240.508385] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=17527 DF PROTO=TCP SPT=1287 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:19:34 kenny-desktop kernel: [ 2351.604953] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=15954 DF PROTO=TCP SPT=60860 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:34 kenny-desktop kernel: [ 2352.054519] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.13.182.186 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=31271 DF PROTO=TCP SPT=52570 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:35 kenny-desktop kernel: [ 2352.299320] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=174.153.0.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=25717 DF PROTO=TCP SPT=52366 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:37 kenny-desktop kernel: [ 2353.928626] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.170.185.143 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=119 ID=719 DF PROTO=TCP SPT=52330 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:37 kenny-desktop kernel: [ 2354.274115] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=16289 DF PROTO=TCP SPT=60860 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:37 kenny-desktop kernel: [ 2354.762683] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=174.153.0.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=25914 DF PROTO=TCP SPT=52366 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:37 kenny-desktop kernel: [ 2354.773612] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.13.182.186 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=31825 DF PROTO=TCP SPT=52570 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:38 kenny-desktop kernel: [ 2355.054202] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=4301 DF PROTO=TCP SPT=54247 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:40 kenny-desktop kernel: [ 2356.478043] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.170.185.143 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=119 ID=919 DF PROTO=TCP SPT=52330 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:40 kenny-desktop kernel: [ 2356.828680] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=16612 DF PROTO=TCP SPT=60861 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:40 kenny-desktop kernel: [ 2357.378616] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.13.182.186 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=116 ID=32417 DF PROTO=TCP SPT=52571 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:43 kenny-desktop kernel: [ 2359.812280] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=16910 DF PROTO=TCP SPT=60861 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:43 kenny-desktop kernel: [ 2359.812305] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=16909 DF PROTO=TCP SPT=60860 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:43 kenny-desktop kernel: [ 2360.254484] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.13.182.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=399 DF PROTO=TCP SPT=52570 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:46 kenny-desktop kernel: [ 2361.947301] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=75.170.185.143 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=1287 DF PROTO=TCP SPT=52330 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:47 kenny-desktop kernel: [ 2362.976241] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=5066 DF PROTO=TCP SPT=54248 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:47 kenny-desktop kernel: [ 2362.976500] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=5065 DF PROTO=TCP SPT=54247 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:49 kenny-desktop kernel: [ 2364.716371] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.121.96.85 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=17602 DF PROTO=TCP SPT=60861 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:49 kenny-desktop kernel: [ 2365.162443] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=24.13.182.186 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=1989 DF PROTO=TCP SPT=52571 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:50 kenny-desktop kernel: [ 2365.382626] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=174.153.0.104 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=26654 DF PROTO=TCP SPT=52367 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:52 kenny-desktop kernel: [ 2367.494485] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=64430 DF PROTO=TCP SPT=3134 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:19:53 kenny-desktop kernel: [ 2367.981401] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.127.213.242 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=5506 DF PROTO=TCP SPT=54248 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:19:55 kenny-desktop kernel: [ 2370.320823] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=64911 DF PROTO=TCP SPT=3134 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:19:58 kenny-desktop kernel: [ 2372.985894] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=103 DF PROTO=TCP SPT=3135 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:01 kenny-desktop kernel: [ 2375.361485] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.44.35.169 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=28172 PROTO=UDP SPT=10091 DPT=42967 LEN=31 
Nov  2 18:20:01 kenny-desktop kernel: [ 2375.362469] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=637 DF PROTO=TCP SPT=3135 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:02 kenny-desktop kernel: [ 2375.688335] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.44.35.169 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=114 ID=28180 PROTO=UDP SPT=10091 DPT=42967 LEN=31 
Nov  2 18:20:07 kenny-desktop kernel: [ 2380.292570] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.104.72.243 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=1668 DF PROTO=TCP SPT=3135 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:08 kenny-desktop kernel: [ 2380.837576] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.115.245.166 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=30828 DF PROTO=TCP SPT=2512 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:09 kenny-desktop kernel: [ 2381.505978] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.67.175.112 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=112 ID=34670 DF PROTO=TCP SPT=2890 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:10 kenny-desktop kernel: [ 2382.836871] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=156.34.54.205 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=18173 DF PROTO=TCP SPT=60490 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:11 kenny-desktop kernel: [ 2383.284681] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.115.245.166 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=30980 DF PROTO=TCP SPT=2512 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:12 kenny-desktop kernel: [ 2383.906491] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.67.175.112 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=112 ID=35060 DF PROTO=TCP SPT=2890 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:13 kenny-desktop kernel: [ 2385.287524] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=156.34.54.205 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=18308 DF PROTO=TCP SPT=60490 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:14 kenny-desktop kernel: [ 2385.735698] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.115.245.166 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=31137 DF PROTO=TCP SPT=2513 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:15 kenny-desktop kernel: [ 2386.246312] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.67.175.112 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=112 ID=35273 DF PROTO=TCP SPT=2891 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:16 kenny-desktop kernel: [ 2387.741862] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=156.34.54.205 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=18378 DF PROTO=TCP SPT=60491 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:17 kenny-desktop kernel: [ 2388.050631] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.115.245.166 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=31337 DF PROTO=TCP SPT=2513 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:18 kenny-desktop kernel: [ 2388.668551] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.67.175.112 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=112 ID=35500 DF PROTO=TCP SPT=2891 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:19 kenny-desktop kernel: [ 2390.191270] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=156.34.54.205 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=117 ID=18528 DF PROTO=TCP SPT=60491 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:23 kenny-desktop kernel: [ 2392.982086] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.115.245.166 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=31858 DF PROTO=TCP SPT=2513 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:24 kenny-desktop kernel: [ 2393.625248] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=66.67.175.112 DST=72.240.205.252 LEN=60 TOS=0x00 PREC=0x00 TTL=112 ID=36011 DF PROTO=TCP SPT=2891 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:24 kenny-desktop kernel: [ 2394.321742] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.46.214.16 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=4745 DF PROTO=TCP SPT=3786 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:20:25 kenny-desktop kernel: [ 2395.095787] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=156.34.54.205 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=18815 DF PROTO=TCP SPT=60491 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:27 kenny-desktop kernel: [ 2396.541622] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.46.214.16 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=4949 DF PROTO=TCP SPT=3786 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:20:30 kenny-desktop kernel: [ 2399.211871] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.46.214.16 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=5228 DF PROTO=TCP SPT=3787 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:20:33 kenny-desktop kernel: [ 2402.141130] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.46.214.16 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=5486 DF PROTO=TCP SPT=3787 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:20:34 kenny-desktop kernel: [ 2402.288363] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.57.215.26 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=34269 DF PROTO=TCP SPT=4236 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:20:36 kenny-desktop kernel: [ 2404.711929] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.57.215.26 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=34684 DF PROTO=TCP SPT=4236 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:20:39 kenny-desktop kernel: [ 2407.335978] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=69.46.214.16 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=6014 DF PROTO=TCP SPT=3787 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:20:40 kenny-desktop kernel: [ 2407.683971] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.57.215.26 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=34835 DF PROTO=TCP SPT=4237 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:20:43 kenny-desktop kernel: [ 2410.426290] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.57.215.26 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=34996 DF PROTO=TCP SPT=4237 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:20:48 kenny-desktop kernel: [ 2415.042834] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=10687 DF PROTO=TCP SPT=51855 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:48 kenny-desktop kernel: [ 2415.335644] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=68.57.215.26 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=35565 DF PROTO=TCP SPT=4237 DPT=42967 WINDOW=64240 RES=0x00 SYN URGP=0 
Nov  2 18:20:49 kenny-desktop kernel: [ 2415.490664] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.249.84.228 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=12363 DF PROTO=TCP SPT=1316 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:51 kenny-desktop kernel: [ 2417.489564] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=10731 DF PROTO=TCP SPT=51855 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:52 kenny-desktop kernel: [ 2417.926263] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.249.84.228 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=12693 DF PROTO=TCP SPT=1316 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:54 kenny-desktop kernel: [ 2420.415976] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=10779 DF PROTO=TCP SPT=51856 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:56 kenny-desktop kernel: [ 2422.083669] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.249.84.228 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=12994 DF PROTO=TCP SPT=1319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:20:57 kenny-desktop kernel: [ 2423.142769] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=10837 DF PROTO=TCP SPT=51855 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:57 kenny-desktop kernel: [ 2423.151546] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=113 ID=10838 DF PROTO=TCP SPT=51856 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:20:59 kenny-desktop kernel: [ 2424.966356] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.249.84.228 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=13683 DF PROTO=TCP SPT=1319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:21:03 kenny-desktop kernel: [ 2428.057745] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=96.253.95.104 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=10929 DF PROTO=TCP SPT=51856 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:05 kenny-desktop kernel: [ 2429.344802] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=26369 DF PROTO=TCP SPT=51662 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:05 kenny-desktop kernel: [ 2429.596939] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.249.84.228 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=120 ID=14338 DF PROTO=TCP SPT=1319 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:21:08 kenny-desktop kernel: [ 2431.895912] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=26623 DF PROTO=TCP SPT=51662 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:11 kenny-desktop kernel: [ 2434.896746] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=26833 DF PROTO=TCP SPT=51663 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:14 kenny-desktop kernel: [ 2437.891294] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=27027 DF PROTO=TCP SPT=51662 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:14 kenny-desktop kernel: [ 2437.896692] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=52 TOS=0x00 PREC=0x00 TTL=109 ID=27028 DF PROTO=TCP SPT=51663 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:20 kenny-desktop kernel: [ 2443.309136] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.132.163.193 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=109 ID=27525 DF PROTO=TCP SPT=51663 DPT=42967 WINDOW=8192 RES=0x00 SYN URGP=0 
Nov  2 18:21:34 kenny-desktop kernel: [ 2455.296453] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=61912 DF PROTO=TCP SPT=62176 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:21:37 kenny-desktop kernel: [ 2458.022465] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=62150 DF PROTO=TCP SPT=62176 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:21:40 kenny-desktop kernel: [ 2461.048549] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=62369 DF PROTO=TCP SPT=62179 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:21:43 kenny-desktop kernel: [ 2463.940297] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=62569 DF PROTO=TCP SPT=62179 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:21:49 kenny-desktop kernel: [ 2468.957513] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.188.169.141 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=111 ID=62968 DF PROTO=TCP SPT=62179 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:22:53 kenny-desktop kernel: [ 2529.551410] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=59798 DF PROTO=TCP SPT=1737 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:22:55 kenny-desktop kernel: [ 2530.991640] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.86.123.58 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1239 DF PROTO=TCP SPT=4951 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:22:56 kenny-desktop kernel: [ 2532.558650] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=60011 DF PROTO=TCP SPT=1737 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:22:58 kenny-desktop kernel: [ 2533.863829] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.86.123.58 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1344 DF PROTO=TCP SPT=4951 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:22:59 kenny-desktop kernel: [ 2535.538947] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=60232 DF PROTO=TCP SPT=1738 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:01 kenny-desktop kernel: [ 2536.982542] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.86.123.58 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1467 DF PROTO=TCP SPT=4952 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:02 kenny-desktop kernel: [ 2538.485744] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=60457 DF PROTO=TCP SPT=1738 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:03 kenny-desktop kernel: [ 2539.267546] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=27047 DF PROTO=TCP SPT=3230 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:04 kenny-desktop kernel: [ 2539.991071] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.86.123.58 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1680 DF PROTO=TCP SPT=4952 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:06 kenny-desktop kernel: [ 2542.178432] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=28322 DF PROTO=TCP SPT=3230 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:08 kenny-desktop kernel: [ 2544.520389] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=65.185.175.144 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=60946 DF PROTO=TCP SPT=1738 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:09 kenny-desktop kernel: [ 2545.257621] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=29709 DF PROTO=TCP SPT=3241 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:10 kenny-desktop kernel: [ 2546.027410] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=67.86.123.58 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=2253 DF PROTO=TCP SPT=4952 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:12 kenny-desktop kernel: [ 2548.206157] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=30906 DF PROTO=TCP SPT=3241 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:18 kenny-desktop kernel: [ 2553.650548] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=45527 DF PROTO=TCP SPT=1341 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:23:18 kenny-desktop kernel: [ 2554.236956] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=76.113.79.241 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=32523 DF PROTO=TCP SPT=3241 DPT=42967 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  2 18:23:21 kenny-desktop kernel: [ 2556.717503] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=45778 DF PROTO=TCP SPT=1341 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:23:24 kenny-desktop kernel: [ 2559.632930] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=46020 DF PROTO=TCP SPT=1342 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:23:26 kenny-desktop kernel: [ 2562.513738] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=46228 DF PROTO=TCP SPT=1342 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:23:32 kenny-desktop kernel: [ 2568.562976] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=70.2.77.56 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=113 ID=46661 DF PROTO=TCP SPT=1342 DPT=42967 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov  2 18:25:28 kenny-desktop kernel: [ 2671.614933] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  2 18:25:28 kenny-desktop kernel: [ 2671.614940] ata1: SError: { 10B8B Dispar }
Nov  2 18:25:28 kenny-desktop kernel: [ 2671.614945] ata1.00: cmd ca/00:10:cf:00:01/00:00:00:00:00/e0 tag 0 dma 8192 out
Nov  2 18:25:28 kenny-desktop kernel: [ 2671.614946]          res 40/00:b8:cf:e0:8e/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  2 18:25:28 kenny-desktop kernel: [ 2671.614949] ata1.00: status: { DRDY }
Nov  2 18:25:34 kenny-desktop kernel: [ 2674.045403] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  2 18:25:38 kenny-desktop kernel: [ 2676.181043] ata1: device not ready (errno=-16), forcing hardreset
Nov  2 18:25:38 kenny-desktop kernel: [ 2676.181048] ata1: hard resetting link
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.397185] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.408166] ata1.00: configured for UDMA/100
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.408175] ata1: EH complete
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.411721] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.411772] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.411775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:25:39 kenny-desktop kernel: [ 2676.411889] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:26:22 kenny-desktop kernel: [ 2719.070844] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x1980000 action 0x2 frozen
Nov  2 18:26:33 kenny-desktop kernel: [ 2719.070855] ata1: SError: { 10B8B Dispar LinkSeq TrStaTrns }
Nov  2 18:26:33 kenny-desktop kernel: [ 2719.070863] ata1.00: cmd ca/00:08:1f:33:02/00:00:00:00:00/e0 tag 0 dma 4096 out
Nov  2 18:26:33 kenny-desktop kernel: [ 2719.070864]          res 40/00:b8:cf:e0:8e/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  2 18:26:33 kenny-desktop kernel: [ 2719.070867] ata1.00: status: { DRDY }
Nov  2 18:26:33 kenny-desktop kernel: [ 2724.425260] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.087046] ata1: device not ready (errno=-16), forcing hardreset
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.087053] ata1: hard resetting link
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.558171] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.582303] ata1.00: configured for UDMA/100
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.582317] ata1: EH complete
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.582625] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.582738] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.582741] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:26:33 kenny-desktop kernel: [ 2729.606567] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.326998] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x580000 action 0x2
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327006] ata1.00: BMDMA stat 0x4
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327009] ata1: SError: { 10B8B Dispar Handshk }
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327015] ata1.00: cmd ca/00:08:ff:27:03/00:00:00:00:00/e0 tag 0 dma 4096 out
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327017]          res 51/84:08:ff:27:03/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327020] ata1.00: status: { DRDY ERR }
Nov  2 18:26:43 kenny-desktop kernel: [ 2740.327022] ata1.00: error: { ICRC ABRT }
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.635419] ata1: soft resetting link
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.794149] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.820365] ata1.00: configured for UDMA/100
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.820386] ata1: EH complete
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.823777] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.823793] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.823796] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:26:44 kenny-desktop kernel: [ 2740.824065] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 18:27:23 kenny-desktop kernel: [ 2778.606149] ata1.00: limiting speed to UDMA/66:PIO4
Nov  2 18:27:34 kenny-desktop kernel: [ 2778.606155] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  2 18:27:34 kenny-desktop kernel: [ 2778.606160] ata1: SError: { 10B8B Dispar }
Nov  2 18:27:34 kenny-desktop kernel: [ 2778.606165] ata1.00: cmd ca/00:10:df:28:04/00:00:00:00:00/e0 tag 0 dma 8192 out
Nov  2 18:27:34 kenny-desktop kernel: [ 2778.606166]          res 40/00:08:ff:27:03/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  2 18:27:34 kenny-desktop kernel: [ 2778.606169] ata1.00: status: { DRDY }
Nov  2 18:27:34 kenny-desktop kernel: [ 2781.035874] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.219715] ata1: device not ready (errno=-16), forcing hardreset
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.219720] ata1: hard resetting link
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.435858] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.446832] ata1.00: configured for UDMA/66
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.446845] ata1: EH complete
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.467042] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.467132] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.467135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 18:27:34 kenny-desktop kernel: [ 2784.464693] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
```

Hope this is better.

---

### Post by userundefine on 2008-11-03
Yes, it appears our problems probably don't have the same cause.  There does seem to be a lot of network output in your logs, though.  More than I've seen.  I've heard people lay the cause of lockups at network manager's doorstep before, though here I don't know if that's what's giving you problems or not.

---

### Post by carl99fan on 2008-11-03
I noticed something after a crash last night.

I understand we may not have the same problem but you seem to know what your looking at.

```
Nov  3 00:08:15 kenny-desktop kernel: [  317.906595] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:08:33 kenny-desktop kernel: [  317.906601] ata1: SError: { 10B8B Dispar }
Nov  3 00:08:33 kenny-desktop kernel: [  317.906607] ata1.00: cmd 35/00:00:0f:36:84/00:04:07:00:00/e0 tag 0 dma 524288 out
Nov  3 00:08:33 kenny-desktop kernel: [  317.906608]          res 40/00:00:5f:f2:89/84:01:1c:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:08:33 kenny-desktop kernel: [  317.906611] ata1.00: status: { DRDY }
Nov  3 00:08:33 kenny-desktop kernel: [  320.336360] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:08:33 kenny-desktop kernel: [  322.472752] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:08:33 kenny-desktop kernel: [  322.472757] ata1: hard resetting link
Nov  3 00:08:33 kenny-desktop kernel: [  322.688445] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:08:33 kenny-desktop kernel: [  322.699884] ata1.00: configured for UDMA/33
Nov  3 00:08:33 kenny-desktop kernel: [  322.699897] ata1: EH complete
Nov  3 00:08:33 kenny-desktop kernel: [  322.702886] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:08:33 kenny-desktop kernel: [  322.712642] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:08:33 kenny-desktop kernel: [  322.712647] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:08:33 kenny-desktop kernel: [  322.723112] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:09:04 kenny-desktop kernel: [  345.466089] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:09:04 kenny-desktop kernel: [  345.466096] ata1: SError: { 10B8B Dispar }
Nov  3 00:09:04 kenny-desktop kernel: [  345.466102] ata1.00: cmd 25/00:20:67:e0:8e/00:01:1c:00:00/e0 tag 0 dma 147456 in
Nov  3 00:09:04 kenny-desktop kernel: [  345.466104]          res 40/00:00:5f:f2:89/84:01:1c:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:09:04 kenny-desktop kernel: [  345.466106] ata1.00: status: { DRDY }
Nov  3 00:09:09 kenny-desktop kernel: [  347.901166] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:09:14 kenny-desktop kernel: [  350.011810] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:09:14 kenny-desktop kernel: [  350.011815] ata1: hard resetting link
Nov  3 00:09:14 kenny-desktop kernel: [  350.227846] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:09:14 kenny-desktop kernel: [  350.240632] ata1.00: configured for UDMA/33
Nov  3 00:09:14 kenny-desktop kernel: [  350.240640] ata1: EH complete
Nov  3 00:09:14 kenny-desktop kernel: [  350.253641] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:09:14 kenny-desktop kernel: [  350.261079] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:09:14 kenny-desktop kernel: [  350.261082] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:09:14 kenny-desktop kernel: [  350.261106] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:10:29 kenny-desktop kernel: [  370.887563] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:10:29 kenny-desktop kernel: [  370.887569] ata1.00: BMDMA stat 0x5
Nov  3 00:10:29 kenny-desktop kernel: [  370.887572] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:10:29 kenny-desktop kernel: [  370.887577] ata1.00: cmd 25/00:80:7f:d4:57/00:00:1c:00:00/e0 tag 0 dma 65536 in
Nov  3 00:10:29 kenny-desktop kernel: [  370.887578]          res 51/84:80:7f:d4:57/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:10:29 kenny-desktop kernel: [  370.887581] ata1.00: status: { DRDY ERR }
Nov  3 00:10:29 kenny-desktop kernel: [  370.887582] ata1.00: error: { ICRC ABRT }
Nov  3 00:10:29 kenny-desktop kernel: [  371.139840] ata1: soft resetting link
Nov  3 00:10:29 kenny-desktop kernel: [  371.267354] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:10:29 kenny-desktop kernel: [  371.287085] ata1.00: configured for UDMA/33
Nov  3 00:10:29 kenny-desktop kernel: [  371.287095] ata1: EH complete
Nov  3 00:10:29 kenny-desktop kernel: [  371.302365] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:10:29 kenny-desktop kernel: [  371.323070] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:10:29 kenny-desktop kernel: [  371.323075] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:10:30 kenny-desktop kernel: [  371.323113] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:10:30 kenny-desktop kernel: [  373.406577] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:10:30 kenny-desktop kernel: [  373.406583] ata1.00: BMDMA stat 0x5
Nov  3 00:10:30 kenny-desktop kernel: [  373.406586] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:10:30 kenny-desktop kernel: [  373.406591] ata1.00: cmd c8/00:00:87:e3:3c/00:00:00:00:00/e0 tag 0 dma 131072 in
Nov  3 00:10:30 kenny-desktop kernel: [  373.406593]          res 51/84:00:87:e3:3c/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:10:30 kenny-desktop kernel: [  373.406595] ata1.00: status: { DRDY ERR }
Nov  3 00:10:30 kenny-desktop kernel: [  373.406597] ata1.00: error: { ICRC ABRT }
Nov  3 00:10:30 kenny-desktop kernel: [  373.663767] ata1: soft resetting link
Nov  3 00:10:30 kenny-desktop kernel: [  373.788015] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:10:30 kenny-desktop kernel: [  373.807769] ata1.00: configured for UDMA/33
Nov  3 00:10:30 kenny-desktop kernel: [  373.807784] ata1: EH complete
Nov  3 00:10:30 kenny-desktop kernel: [  373.842972] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:10:30 kenny-desktop kernel: [  373.843014] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:10:30 kenny-desktop kernel: [  373.843016] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:10:30 kenny-desktop kernel: [  373.843030] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:10:30 kenny-desktop kernel: [  383.596816] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=13926 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  384.052720] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=14114 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  384.505912] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=14324 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  384.958304] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=14535 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  385.414015] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=14742 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  385.867791] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=14960 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  386.320353] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=15143 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  386.775473] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=15331 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  387.228469] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=15542 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  387.682416] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=15743 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  388.137735] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=15943 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  388.590725] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16110 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  388.888882] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:10:30 kenny-desktop kernel: [  388.888889] ata1: SError: { 10B8B Dispar }
Nov  3 00:10:30 kenny-desktop kernel: [  388.888894] ata1.00: cmd c8/00:00:8f:e8:3c/00:00:00:00:00/e0 tag 0 dma 131072 in
Nov  3 00:10:30 kenny-desktop kernel: [  388.888896]          res 40/00:00:87:e3:3c/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:10:30 kenny-desktop kernel: [  388.888899] ata1.00: status: { DRDY }
Nov  3 00:10:30 kenny-desktop kernel: [  389.044678] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16314 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  389.498828] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16527 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  389.952006] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16738 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  390.408882] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16942 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  390.861081] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17149 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  391.317763] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17342 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  391.323995] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:10:30 kenny-desktop kernel: [  391.769185] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17525 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  392.224308] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17755 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  392.679224] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17948 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:10:30 kenny-desktop kernel: [  393.434528] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:10:30 kenny-desktop kernel: [  393.434534] ata1: hard resetting link
Nov  3 00:10:30 kenny-desktop kernel: [  393.650679] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:10:30 kenny-desktop kernel: [  393.661650] ata1.00: configured for UDMA/33
Nov  3 00:10:30 kenny-desktop kernel: [  393.661659] ata1: EH complete
Nov  3 00:10:30 kenny-desktop kernel: [  393.679021] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:10:30 kenny-desktop kernel: [  393.685959] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:10:30 kenny-desktop kernel: [  393.685966] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:10:30 kenny-desktop kernel: [  393.688824] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:10:39 kenny-desktop kernel: [  404.025555] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:10:39 kenny-desktop kernel: [  404.025564] ata1.00: BMDMA stat 0x5
Nov  3 00:10:39 kenny-desktop kernel: [  404.025567] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:10:39 kenny-desktop kernel: [  404.025574] ata1.00: cmd 25/00:a8:27:a5:71/00:01:19:00:00/e0 tag 0 dma 217088 in
Nov  3 00:10:39 kenny-desktop kernel: [  404.025575]          res 51/84:a8:27:a5:71/84:01:19:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:10:39 kenny-desktop kernel: [  404.025578] ata1.00: status: { DRDY ERR }
Nov  3 00:10:39 kenny-desktop kernel: [  404.025580] ata1.00: error: { ICRC ABRT }
Nov  3 00:10:39 kenny-desktop kernel: [  404.241495] ata1: soft resetting link
Nov  3 00:10:39 kenny-desktop kernel: [  404.312338] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:10:39 kenny-desktop kernel: [  404.323313] ata1.00: configured for UDMA/33
Nov  3 00:10:39 kenny-desktop kernel: [  404.323329] ata1: EH complete
Nov  3 00:10:39 kenny-desktop kernel: [  404.338958] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:10:39 kenny-desktop kernel: [  404.339153] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:10:39 kenny-desktop kernel: [  404.339156] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:10:39 kenny-desktop kernel: [  404.349548] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:11:11 kenny-desktop kernel: [  418.563448] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:11:11 kenny-desktop kernel: [  418.563455] ata1: SError: { 10B8B Dispar }
Nov  3 00:11:11 kenny-desktop kernel: [  418.563461] ata1.00: cmd 25/00:c8:7f:6c:61/00:00:19:00:00/e0 tag 0 dma 102400 in
Nov  3 00:11:11 kenny-desktop kernel: [  418.563462]          res 40/00:a8:27:a5:71/84:01:19:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:11:11 kenny-desktop kernel: [  418.563465] ata1.00: status: { DRDY }
Nov  3 00:11:16 kenny-desktop kernel: [  420.993640] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:11:21 kenny-desktop kernel: [  423.129604] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:11:21 kenny-desktop kernel: [  423.129610] ata1: hard resetting link
Nov  3 00:11:21 kenny-desktop kernel: [  423.345302] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:11:21 kenny-desktop kernel: [  423.356275] ata1.00: configured for UDMA/33
Nov  3 00:11:21 kenny-desktop kernel: [  423.356288] ata1: EH complete
Nov  3 00:11:21 kenny-desktop kernel: [  423.363014] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:11:21 kenny-desktop kernel: [  423.363155] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:11:21 kenny-desktop kernel: [  423.363158] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:11:21 kenny-desktop kernel: [  423.377737] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:11:59 kenny-desktop kernel: [  445.547103] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:11:59 kenny-desktop kernel: [  445.547109] ata1.00: BMDMA stat 0x4
Nov  3 00:11:59 kenny-desktop kernel: [  445.547112] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:11:59 kenny-desktop kernel: [  445.547118] ata1.00: cmd 25/00:08:87:61:74/00:00:1c:00:00/e0 tag 0 dma 4096 in
Nov  3 00:11:59 kenny-desktop kernel: [  445.547119]          res 51/84:00:8e:61:74/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:11:59 kenny-desktop kernel: [  445.547122] ata1.00: status: { DRDY ERR }
Nov  3 00:11:59 kenny-desktop kernel: [  445.547124] ata1.00: error: { ICRC ABRT }
Nov  3 00:11:59 kenny-desktop kernel: [  445.688333] ata1: soft resetting link
Nov  3 00:11:59 kenny-desktop kernel: [  445.758725] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:11:59 kenny-desktop kernel: [  445.769698] ata1.00: configured for UDMA/33
Nov  3 00:11:59 kenny-desktop kernel: [  445.769711] ata1: EH complete
Nov  3 00:11:59 kenny-desktop kernel: [  445.780187] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:11:59 kenny-desktop kernel: [  445.787132] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:11:59 kenny-desktop kernel: [  445.787136] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:11:59 kenny-desktop kernel: [  445.791749] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:13:10 kenny-desktop kernel: [  479.575745] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:13:10 kenny-desktop kernel: [  479.575751] ata1.00: BMDMA stat 0x4
Nov  3 00:13:10 kenny-desktop kernel: [  479.575754] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:13:10 kenny-desktop kernel: [  479.575759] ata1.00: cmd 25/00:08:47:c8:6f/00:00:1b:00:00/e0 tag 0 dma 4096 in
Nov  3 00:13:10 kenny-desktop kernel: [  479.575760]          res 51/84:00:4e:c8:6f/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:13:10 kenny-desktop kernel: [  479.575764] ata1.00: status: { DRDY ERR }
Nov  3 00:13:10 kenny-desktop kernel: [  479.575765] ata1.00: error: { ICRC ABRT }
Nov  3 00:13:10 kenny-desktop kernel: [  479.716248] ata1: soft resetting link
Nov  3 00:13:10 kenny-desktop kernel: [  479.787091] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:13:10 kenny-desktop kernel: [  479.797620] ata1.00: configured for UDMA/33
Nov  3 00:13:10 kenny-desktop kernel: [  479.797635] ata1: EH complete
Nov  3 00:13:10 kenny-desktop kernel: [  479.810058] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:13:10 kenny-desktop kernel: [  479.810169] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:13:10 kenny-desktop kernel: [  479.810172] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:13:10 kenny-desktop kernel: [  479.813432] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:13:17 kenny-desktop kernel: [  482.915490] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:13:17 kenny-desktop kernel: [  482.915496] ata1.00: BMDMA stat 0x5
Nov  3 00:13:17 kenny-desktop kernel: [  482.915499] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:13:17 kenny-desktop kernel: [  482.915504] ata1.00: cmd 25/00:30:b7:64:08/00:00:1c:00:00/e0 tag 0 dma 24576 in
Nov  3 00:13:17 kenny-desktop kernel: [  482.915506]          res 51/84:30:b7:64:08/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:13:18 kenny-desktop kernel: [  482.915509] ata1.00: status: { DRDY ERR }
Nov  3 00:13:18 kenny-desktop kernel: [  482.915511] ata1.00: error: { ICRC ABRT }
Nov  3 00:13:18 kenny-desktop kernel: [  483.056413] ata1: soft resetting link
Nov  3 00:13:18 kenny-desktop kernel: [  483.127256] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:13:18 kenny-desktop kernel: [  483.138242] ata1.00: configured for UDMA/33
Nov  3 00:13:18 kenny-desktop kernel: [  483.138259] ata1: EH complete
Nov  3 00:13:18 kenny-desktop kernel: [  483.148624] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:13:18 kenny-desktop kernel: [  483.150383] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:13:18 kenny-desktop kernel: [  483.150392] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:13:18 kenny-desktop kernel: [  483.173649] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:13:33 kenny-desktop kernel: [  490.128282] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:13:33 kenny-desktop kernel: [  490.128288] ata1.00: BMDMA stat 0x5
Nov  3 00:13:33 kenny-desktop kernel: [  490.128291] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:13:33 kenny-desktop kernel: [  490.128297] ata1.00: cmd 25/00:38:47:fe:1a/00:00:1c:00:00/e0 tag 0 dma 28672 in
Nov  3 00:13:33 kenny-desktop kernel: [  490.128298]          res 51/84:38:47:fe:1a/84:00:1c:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:13:33 kenny-desktop kernel: [  490.128301] ata1.00: status: { DRDY ERR }
Nov  3 00:13:33 kenny-desktop kernel: [  490.128303] ata1.00: error: { ICRC ABRT }
Nov  3 00:13:33 kenny-desktop kernel: [  490.268921] ata1: soft resetting link
Nov  3 00:13:33 kenny-desktop kernel: [  490.339314] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:13:33 kenny-desktop kernel: [  490.350286] ata1.00: configured for UDMA/33
Nov  3 00:13:33 kenny-desktop kernel: [  490.350301] ata1: EH complete
Nov  3 00:13:33 kenny-desktop kernel: [  490.360661] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:13:33 kenny-desktop kernel: [  490.364163] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:13:33 kenny-desktop kernel: [  490.364167] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:13:33 kenny-desktop kernel: [  490.370858] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:14:40 kenny-desktop kernel: [  524.042680] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:14:40 kenny-desktop kernel: [  524.042687] ata1: SError: { 10B8B Dispar }
Nov  3 00:14:40 kenny-desktop kernel: [  524.042693] ata1.00: cmd 25/00:00:ff:bb:fc/00:01:1b:00:00/e0 tag 0 dma 131072 in
Nov  3 00:14:40 kenny-desktop kernel: [  524.042694]          res 40/00:38:47:fe:1a/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:14:40 kenny-desktop kernel: [  524.042698] ata1.00: status: { DRDY }
Nov  3 00:14:45 kenny-desktop kernel: [  526.473324] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:14:50 kenny-desktop kernel: [  528.609290] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:14:50 kenny-desktop kernel: [  528.609296] ata1: hard resetting link
Nov  3 00:14:50 kenny-desktop kernel: [  528.825435] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:14:50 kenny-desktop kernel: [  528.836415] ata1.00: configured for UDMA/33
Nov  3 00:14:50 kenny-desktop kernel: [  528.836429] ata1: EH complete
Nov  3 00:14:50 kenny-desktop kernel: [  528.843404] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:14:50 kenny-desktop kernel: [  528.850943] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:14:50 kenny-desktop kernel: [  528.850947] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:14:50 kenny-desktop kernel: [  528.856428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:14:56 kenny-desktop kernel: [  533.404681] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:14:56 kenny-desktop kernel: [  533.404688] ata1.00: BMDMA stat 0x4
Nov  3 00:14:56 kenny-desktop kernel: [  533.404691] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:14:56 kenny-desktop kernel: [  533.404696] ata1.00: cmd 25/00:08:b7:65:56/00:00:1c:00:00/e0 tag 0 dma 4096 in
Nov  3 00:14:56 kenny-desktop kernel: [  533.404698]          res 51/84:00:be:65:56/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:14:56 kenny-desktop kernel: [  533.404700] ata1.00: status: { DRDY ERR }
Nov  3 00:14:56 kenny-desktop kernel: [  533.404702] ata1.00: error: { ICRC ABRT }
Nov  3 00:14:56 kenny-desktop kernel: [  533.685434] ata1: soft resetting link
Nov  3 00:14:56 kenny-desktop kernel: [  533.812953] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:14:56 kenny-desktop kernel: [  533.831878] ata1.00: configured for UDMA/33
Nov  3 00:14:56 kenny-desktop kernel: [  533.831888] ata1: EH complete
Nov  3 00:14:56 kenny-desktop kernel: [  533.847546] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:14:56 kenny-desktop kernel: [  533.852817] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:14:56 kenny-desktop kernel: [  533.852821] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:14:56 kenny-desktop kernel: [  533.864653] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:15:19 kenny-desktop kernel: [  549.666188] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  3 00:15:19 kenny-desktop kernel: [  549.666194] ata1.00: BMDMA stat 0x5
Nov  3 00:15:19 kenny-desktop kernel: [  549.666197] ata1: SError: { 10B8B Dispar BadCRC }
Nov  3 00:15:19 kenny-desktop kernel: [  549.666202] ata1.00: cmd 25/00:98:7f:78:a9/00:00:19:00:00/e0 tag 0 dma 77824 in
Nov  3 00:15:19 kenny-desktop kernel: [  549.666203]          res 51/84:98:7f:78:a9/84:00:19:00:00/e0 Emask 0x10 (ATA bus error)
Nov  3 00:15:19 kenny-desktop kernel: [  549.666205] ata1.00: status: { DRDY ERR }
Nov  3 00:15:19 kenny-desktop kernel: [  549.666207] ata1.00: error: { ICRC ABRT }
Nov  3 00:15:19 kenny-desktop kernel: [  549.806916] ata1: soft resetting link
Nov  3 00:15:19 kenny-desktop kernel: [  549.877311] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:15:19 kenny-desktop kernel: [  549.964573] ata1.00: configured for UDMA/33
Nov  3 00:15:19 kenny-desktop kernel: [  549.964583] ata1: EH complete
Nov  3 00:15:19 kenny-desktop kernel: [  549.980262] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:15:19 kenny-desktop kernel: [  549.986469] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:15:19 kenny-desktop kernel: [  549.986475] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:15:20 kenny-desktop kernel: [  549.990818] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:15:51 kenny-desktop kernel: [  564.152046] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:16:02 kenny-desktop kernel: [  564.152052] ata1: SError: { 10B8B Dispar }
Nov  3 00:16:02 kenny-desktop kernel: [  564.152057] ata1.00: cmd 25/00:90:37:d7:aa/00:00:19:00:00/e0 tag 0 dma 73728 in
Nov  3 00:16:02 kenny-desktop kernel: [  564.152058]          res 40/00:98:7f:78:a9/84:00:19:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:16:02 kenny-desktop kernel: [  564.152061] ata1.00: status: { DRDY }
Nov  3 00:16:02 kenny-desktop kernel: [  566.581792] ata1: port is slow to respond, please be patient (Status 0xd0)
Nov  3 00:16:02 kenny-desktop kernel: [  568.717758] ata1: device not ready (errno=-16), forcing hardreset
Nov  3 00:16:02 kenny-desktop kernel: [  568.717763] ata1: hard resetting link
Nov  3 00:16:02 kenny-desktop kernel: [  568.933905] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  3 00:16:02 kenny-desktop kernel: [  568.944880] ata1.00: configured for UDMA/33
Nov  3 00:16:02 kenny-desktop kernel: [  568.944888] ata1: EH complete
Nov  3 00:16:02 kenny-desktop kernel: [  568.959374] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  3 00:16:02 kenny-desktop kernel: [  568.959474] sd 0:0:0:0: [sda] Write Protect is off
Nov  3 00:16:02 kenny-desktop kernel: [  568.959477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  3 00:16:02 kenny-desktop kernel: [  568.964850] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  3 00:16:21 kenny-desktop kernel: [  581.564170] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16049 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:22 kenny-desktop kernel: [  582.369380] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16250 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:23 kenny-desktop kernel: [  583.332136] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16471 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:24 kenny-desktop kernel: [  584.075619] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16658 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:25 kenny-desktop kernel: [  584.894840] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=16838 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:26 kenny-desktop kernel: [  585.711964] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17019 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:27 kenny-desktop kernel: [  586.691088] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17190 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:28 kenny-desktop kernel: [  587.346910] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17309 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:29 kenny-desktop kernel: [  588.162272] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17456 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:30 kenny-desktop kernel: [  588.980098] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17583 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:31 kenny-desktop kernel: [  589.796872] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17734 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:31 kenny-desktop kernel: [  590.439019] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=216.146.47.45 DST=72.240.205.252 LEN=48 TOS=0x00 PREC=0x00 TTL=121 ID=10070 PROTO=TCP SPT=60198 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0 
Nov  3 00:16:32 kenny-desktop kernel: [  590.614344] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=17872 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:33 kenny-desktop kernel: [  591.356574] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=18002 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:34 kenny-desktop kernel: [  591.809752] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=18138 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:35 kenny-desktop kernel: [  592.265094] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=18273 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:36 kenny-desktop kernel: [  592.766569] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=18435 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
Nov  3 00:16:37 kenny-desktop kernel: [  593.763556] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00 SRC=72.231.16.70 DST=72.240.205.252 LEN=51 TOS=0x00 PREC=0x00 TTL=113 ID=18564 PROTO=UDP SPT=6346 DPT=42967 LEN=31 
```

This is the part I thought might be of interest.
```
Nov  3 00:10:30 kenny-desktop kernel: [  388.888882] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x180000 action 0x2 frozen
Nov  3 00:10:30 kenny-desktop kernel: [  388.888889] ata1: SError: { 10B8B Dispar }
Nov  3 00:10:30 kenny-desktop kernel: [  388.888894] ata1.00: cmd c8/00:00:8f:e8:3c/00:00:00:00:00/e0 tag 0 dma 131072 in
Nov  3 00:10:30 kenny-desktop kernel: [  388.888896]          res 40/00:00:87:e3:3c/84:00:1c:00:00/e0 Emask 0x4 (timeout)
Nov  3 00:10:30 kenny-desktop kernel: [  388.888899] ata1.00: status: { DRDY }
Nov  3 00:10:30 kenny-desktop kernel: [  389.044678] Inbound IN=eth0 OUT= MAC=00:17:31:ed:47:1c:00:30:b8:c6:1c:90:08:00
```

I don't know but I see the word frozen!! lol
Thanks to anybody who can read this code.

---

### Post by carl99fan on 2008-11-03
Typing from memory I remember seeing some like the following after hitting the "restart" button.
EXT-fs Error device sdat1 EXT_find_entry <67>sd.0.0.0.0[sda  that's all I remember.

by the way the restart/shutdown screen had lost if graphics.
and when I would click any quicklaunch icons, of even try to open stuff from the main menu I was given a message that directory not found ...

---

### Post by carl99fan on 2008-11-03
I think I am going to upgrade to 8.10 just in case that may help.

I also could go to the 64 bit version but not really a solution right now as I do not have a way to backup my data at this time.

---

### Post by carl99fan on 2008-11-05
Well that sure did not work...

It crashed, and I could not restart. I used the live cd to get all my files and I installed the 64 bit 8.04

It just crashed while using mozilla.

Here is the code.
```
Nov  5 12:13:04 kenny-desktop kernel: [   45.703473] lo: Disabled Privacy Extensions
Nov  5 12:13:15 kenny-desktop kernel: [   50.575411] eth0: no IPv6 routers present
Nov  5 13:23:57 kenny-desktop kernel: [ 3315.959284] npviewer.bin[6500]: segfault at 2c rip f6b7f31a rsp ffca8680 error 4
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.730996] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x380000 action 0x2
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731004] ata1.00: BMDMA stat 0x4
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731007] ata1: SError: { 10B8B Dispar BadCRC }
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731013] ata1.00: cmd 25/00:08:17:73:a0/00:00:19:00:00/e0 tag 0 dma 4096 in
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731014]          res 51/84:00:1e:73:a0/84:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731017] ata1.00: status: { DRDY ERR }
Nov  5 16:18:16 kenny-desktop kernel: [ 9262.731018] ata1.00: error: { ICRC ABRT }
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.042451] ata1: soft resetting link
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.199295] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.239475] ata1.00: configured for UDMA/100
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.239493] ata1: EH complete
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.283709] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.290735] sd 0:0:0:0: [sda] Write Protect is off
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.290741] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  5 16:18:16 kenny-desktop kernel: [ 9263.300899] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```
SOMEBODY PLEASE HELP. I see errors but I don't know what they are.

maybe a hard drive problem? :confused:

---


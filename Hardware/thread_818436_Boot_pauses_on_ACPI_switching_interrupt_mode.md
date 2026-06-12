---
title: "Boot pauses on ACPI switching interrupt mode"
date: 2008-06-04
forum: Hardware
---

### Post by Hero of Time on 2008-06-04
Hi all,

I'm having some issues with the boot process of my Hardy on my laptop. I had it from Feisty. Went to Gutsy and still had it and now with Hardy the same thing. Whenever I boot, the whole process halts for a moment with the message ACPI: EC: non-query interrupt received, switching to interrupt mode. It stays there for 20 seconds. I'm wondering how I can fix this. 20 seconds is pretty much for booting. Below is the first part of dmesg.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
[    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fe9b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe9b000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7860
[    0.000000] Entering add_active_range(0, 0, 523920) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523920
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523920
[    0.000000] On node 0 totalpages: 523920
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292243 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F77B0 checksum 0
[    0.000000] ACPI: RSDP 000F77B0, 0014 (r0 FSC   )
[    0.000000] ACPI: RSDT 7FE94EFF, 0044 (r1 PTLTD  PC        6040000  LTP        0)
[    0.000000] ACPI: FACP 7FE9AE20, 0074 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 7FE95ADE, 5342 (r1 UW____ F29_____  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7FE9BFC0, 0040
[    0.000000] ACPI: APIC 7FE9AE94, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FE9AEFC, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FE9AF34, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: APIC 7FE9AF70, 0068 (r1 FSC    PC        6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FE9AFD8, 0028 (r1 FSC    PC        6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FE958D4, 020A (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE94F43, 04F6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Fujitsu Siemens
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519827
[    0.000000] Kernel command line: root=UUID=fcae836a-f9f9-4db4-a129-4f3d897b9e2e ro 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.528 MHz processor.
[   17.435033] Console: colour VGA+ 80x25
[   17.435037] console [tty0] enabled
[   17.438565] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.438966] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.563041] Memory: 2065828k/2095680k available (2176k kernel code, 28504k reserved, 1006k data, 368k init, 1178176k highmem)
[   17.563109] virtual kernel memory layout:
[   17.563110]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.563111]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.563113]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.563114]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.563115]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   17.563117]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   17.563118]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   17.563486] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.563615] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.563822] hpet clockevent registered
[   17.643706] Calibrating delay using timer specific routine.. 3328.90 BogoMIPS (lpj=6657802)
[   17.643819] Security Framework initialized
[   17.643871] SELinux:  Disabled at boot.
[   17.643929] AppArmor: AppArmor initialized
[   17.643977] Failure registering capabilities with primary security module.
[   17.644034] Mount-cache hash table entries: 512
[   17.644204] Initializing cgroup subsys ns
[   17.644254] Initializing cgroup subsys cpuacct
[   17.644309] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   17.644317] monitor/mwait feature present.
[   17.644363] using mwait in idle threads.
[   17.644411] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.644492] CPU: L2 cache: 2048K
[   17.644538] CPU: Physical Processor ID: 0
[   17.644583] CPU: Processor Core ID: 0
[   17.644630] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   17.644640] Compat vDSO mapped to ffffe000.
[   17.644697] Checking 'hlt' instruction... OK.
[   17.660117] SMP alternatives: switching to UP code
[   17.661978] Early unpacking initramfs... done
[   17.995168] ACPI: Core revision 20070126
[   17.995270] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.998942] CPU0: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[   17.999121] SMP alternatives: switching to SMP code
[   17.999864] Booting processor 1/1 eip 3000
[   18.010123] Initializing CPU#1
[   18.087020] Calibrating delay using timer specific routine.. 3325.05 BogoMIPS (lpj=6650116)
[   18.087028] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   18.087033] monitor/mwait feature present.
[   18.087037] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.087039] CPU: L2 cache: 2048K
[   18.087041] CPU: Physical Processor ID: 0
[   18.087042] CPU: Processor Core ID: 1
[   18.087044] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   18.087598] CPU1: Intel Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08
[   18.088106] Total of 2 processors activated (6653.95 BogoMIPS).
[   18.088349] ENABLING IO-APIC IRQs
[   18.088585] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.234919] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   18.254993] Brought up 2 CPUs
[   18.255063] CPU0 attaching sched-domain:
[   18.255066]  domain 0: span 03
[   18.255068]   groups: 01 02
[   18.255071] CPU1 attaching sched-domain:
[   18.255073]  domain 0: span 03
[   18.255075]   groups: 02 01
[   18.255325] net_namespace: 64 bytes
[   18.255380] Booting paravirtualized kernel on bare hardware
[   18.255906] Time: 19:21:38  Date: 06/04/08
[   18.255981] NET: Registered protocol family 16
[   18.256235] EISA bus registered
[   18.256283] ACPI: bus type pci registered
[   18.295194] PCI: PCI BIOS revision 2.10 entry at 0xfd833, last bus=5
[   18.295243] PCI: Using configuration type 1
[   18.295290] Setting up standard PCI resources
[   18.297258] ACPI: EC: Look up EC in DSDT
[   18.298940] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   18.299528] ACPI: Interpreter enabled
[   18.299576] ACPI: (supports S0 S3 S4 S5)
[   18.299776] ACPI: Using IOAPIC for interrupt routing
[   18.300101] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   36.277585] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   36.277637] ACPI: EC: driver started in interrupt mode
[   36.277735] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.278502] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   36.278555] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   36.279645] PCI: Transparent bridge - 0000:00:1e.0

```
BIOS is already the latest version.
I have a Fujitsu-Siemens Amilo Pi 1536 laptop.
The install has all the latest updates, kernel 2.6.24-18-generic.

---

### Post by Hero of Time on 2008-06-06
Anyone has any ideas?

---

### Post by Hero of Time on 2008-06-09
Nobody?

---

### Post by sheps999 on 2008-07-12
Bump, because I'm also having this problem, and have held off installing Ubuntu because of it :|

---

### Post by sheps999 on 2008-07-12
*bump*

---

### Post by sheps999 on 2008-08-29
Another bump.

Any one know what's causing this problem (the ACPI one, that is)?

---

### Post by IntuitiveNipple on 2008-08-29
In terms of the results in the dmesg log, everything is fine, the EC (Embedded Controller) is initialising as it should, in the optimum mode.

As to why it takes around 20 seconds for the GPE (General Purpose Event) interrupt to either be generated, or to be handled, is more complex.

I've got intimate knowledge of the code that handles this since I was working on a recent bug ([[Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled or AC power is connected](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/191137/comments/107)) that would hang many Sony Vaios totally at that point.

The latest kernel updates (2.6.24-20) fixes the issue I worked on and I wouldn't be surprised if it also fixed the symptom you're experiencing.

---

### Post by sheps999 on 2008-08-29
Thanks for the info. I'll update, and see if it changes anything ;)

---

### Post by sheps999 on 2008-08-29
Noop, fraid not. I updated to the latest kernel (2.6.24-21-generic) through Synaptic, but nothing happened, I'm afraid.

I forgot to mention (not sure if it's important), but my laptop hangs at this interrupt point whether on "quiet" mode or not, and on battery or AC power. Just every boot-time.

---

### Post by IntuitiveNipple on 2008-08-30
Thanks for testing and the report. I think it is possible you're affected by another by-product of the patches. At this point please [open a bug report in Launchpad](https://bugs.launchpad.net/ubuntu/+source/linux), assign it to the "linux" package, and subscribe the "Kernel ACPI Team" so I get notified of it.

We can then do some diagnosis and maybe discover what is going on and whether there is already an upstream patch (more recent kernel patch) to deal with, or whether it is a newly discovered issue.

---

### Post by sheps999 on 2008-08-30
No problem.

Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263140)

:)

---

### Post by ijavid on 2008-09-04
hi,

i have similar problem with my asus m51tr notebook, if you have got any solution please report it.

thx

---

### Post by IntuitiveNipple on 2008-09-04
> **sheps999 said:**
> No problem.

Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263140)

:)
Thanks. I'll track it and when I get time to focus on it I'll post some questions there to help narrow this down. 

Any-one else with the same issue should [add a comment to the Launchpad bug #263140](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263140) so we can see how many are effected and keep the diagnosis and fix process in one place.

---

### Post by msheppard on 2009-02-07
Experiencing similar problem.

Found some help suggesting adding noacpi to the boot line - which did not work, but eventually stumpled upon the option "acpi=no" and the machine boots now.

Having some mouse issues though - and USB mouse doesn't work - but I'm clueless what acpi even means, so I'm researching that now.

To get into boot mode use this instruction: 
[https://answers.launchpad.net/ubuntu/+question/23973](https://answers.launchpad.net/ubuntu/+question/23973)

But instead of "noapic noacpi" replace with "acpi=no"

---


---
title: "Random crashing - how to determine the cause?"
date: 2012-06-08
forum: Hardware
---

### Post by Sunships on 2012-06-08
Hi all,

My computer has started crashing randomly in the past two weeks. It crashes in both Ubuntu, Windows and during boot, so the problem is not OS-specific, and I believe it is therefore due to a hardware fault. 

I have cleaned all the dust out of the case and checked all the connections, but the computer still crashes/hangs, with no discernible pattern. What can I do to find out which component is faulty? I have seen the commands dmesg and cat /var/log/syslog mentioned in other threads. Are there any other commands I should use following the next crash? Could updating my BIOS help?

As always, thanks for your help and time.

---

### Post by ahallubuntu on 2012-06-08
It could be a lot of things.  The way you determine the cause is to test one thing at a time.  Test the RAM, the hard drive, and the power supply if you can.  Remove or unplug any unnecessary components from the motherboard e.g. extra cards and such.

You can also try simple re-seating cards and the RAM.

Inspect the CPU heat sink and make sure it's on securely.  I've seen the plastic mounting bracket CRACK in a few cases and the heat sink can't make a tight connection to the CPU and could cause it to overheat.  It could be a lot of things.
 
Once you have tested everything easy like the above and ruled it out, you generally just assume it's the motherboard.

A great CD with utilities to test stuff: the Ultimate Boot CD:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Download the ISO image file, burn it (AS AN IMAGE) to a blank CD, and boot it on your problem system.  The Ultimate Boot CD has a few "burn in" utilities that stress the CPU and heat it up.  If you can run one of them for a half hour without a crash, the CPU is probably NOT overheating...

Test the RAM with Memtest (on any Ubuntu CD or on the Ultimate Boot CD).  Let Memtest run for a few minutes - if it doesn't fail then, it's probably not the RAM.

Test the hard drive with Parted Magic (included on UBCD).  Check SmartControl after you start Parted Magic, and look for any Attributes in red.  If there are any serious ones (pending sector errors for example), that's probably your problem.

If you get random crashes during any of the above testing, that makes it sound like CPU overheat, bad power supply, or bad motherboard.

Look on the motherboard for bulging capacitors - a sign of a bad motherboard.  Google "bad caps" for images of what they might look like.

---

### Post by Sunships on 2012-06-08
Excellent, thank you ahallubuntu! Lots of things to try. I'll give them a go and see what happens.

---

### Post by Redblade20XX on 2012-06-08
Just an aside... you mentioned /var/log. This is the location where your system logs are located. You can check these logs to see what might be a problem if it's on the software side.

-Red

---

### Post by Sunships on 2012-06-09
Thanks Redblade, next time it crashes I'll post the logs for data-mining.

---

### Post by Sunships on 2012-06-09
Alright, I tried as many of the above suggestions as I could. Here is my current progress. To summarise, I haven't had any crashes since removing the cards from the motherboard, everything looks fine during visual inspection, but the CPU stress tests give funny results - not sure that these are working properly (screenshot below) Any advice on what to try next??

GENERAL CHECKING - I re-seated everything and checked all the connections. Nothing wrong there. 

MOTHERBOARD/CPU/HEAT SINK - I inspected the motherboard and the CPU/heat sink. The capacitors all look tip-top, and I didn't see anything wrong with the CPU/heat sink assembly - I didn't dismantle it though, as the fan is a real pain in the neck to re-attach - I'd prefer to leave messing with that until I've conclusively ruled out everything else.

CARDS - I removed the two cards which were plugged into the motherboard - one is the graphics card, the other is a card with some USB 3.0 ports. Some history is relevant here: Before the computer started crashing I lost all output from the graphics card, leading me to initially suspect that this was the cause of the problem. My retailer tested the graphics card and informed me that it was working fine, and I still experienced some crashes/hanging when it was removed. Removing the graphics card therefore alters the profile of the crashes, but doesn't completely solve the problem. However, I have not seen any crashes since removing BOTH cards, so maybe this is something to investigate further?

POWER SUPPLY - I don't have another machine in which to test this. How can I confirm that it is working properly?

UBCD tests:

RAM - I ran memtest. I let it go for just under half an hour, during which time it came up with no errors.

HARD DRIVE - The hard drive is made by Seagate. I found DOS tools for Seagate on the UBCD, and ran both short and long DSTs with that - both passed. I also ran a short test with GSmartControl - also passed. None of the Attributes showed any faults either. I didn't run the long test in GSmartControl as it will take another two hours, but can do so.

CPU - I tried CPU Burn-in, Marsenne Prime and Stress. For each test I got output similar to this within a second or two of selection: 


[IMG]http://i.imgur.com/ChYlb.jpg[/IMG]

..and the computer becomes unresponsive, with flashing cursor. Does this mean that the CPU is failing the tests/is the source of the problem, or that the tests are just failing to run properly due to a fault with my disk?

Once again, thanks for your help!

---

### Post by Sunships on 2012-06-10
Alright, I removed both PCI cards (the graphics card and USB3 card) to see what effect this would have - I was able to use the system all day yesterday with no crashing at all, which suggests that their presence in the system exacerbates/causes the problem.

I tried running the system with just the graphics card installed and not the USB3 card - the computer commenced crashing, once again. I have attached /var/log/syslog - ctashes occur around 11:02:23 and 11:03:34.

Does this make sense to anyone? The retailer tested my graphics card earlier this week and found no faults, so does this definitely implicate the motherboard/CPU as the source of the problem?

/var/log/syslog:

```
Jun 10 10:36:48 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 10 10:36:49 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 10 10:37:49 turk anacron[1124]: Job `cron.daily' terminated (mailing output)
Jun 10 10:37:49 turk anacron[1124]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun 10 10:37:49 turk anacron[1124]: Normal exit (1 job run)
Jun 10 10:53:08 turk kernel: Kernel logging (proc) stopped.
Jun 10 10:53:08 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jun 10 11:00:20 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:00:20 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="961" x-info="http://www.rsyslog.com"] start
Jun 10 11:00:20 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:00:20 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:00:20 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:00:20 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:00:20 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:00:20 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:00:20 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:00:20 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:00:20 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:00:20 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:00:20 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:00:20 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:00:20 turk kernel: [    0.000000] DMI present.
Jun 10 11:00:20 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:00:20 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:00:20 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:00:20 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:00:20 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:00:20 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   3 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   4 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   5 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   6 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   7 disabled
Jun 10 11:00:20 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:00:20 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:00:20 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:00:20 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:00:20 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:00:20 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:00:20 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:00:20 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:00:20 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:00:20 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:00:20 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:00:20 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:00:20 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:00:20 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:00:20 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:00:20 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:00:20 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:00:20 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:00:20 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:00:20 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:00:20 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:00:20 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:00:20 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:00:20 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:00:20 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:00:20 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:00:20 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:00:20 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:00:20 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:00:20 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:00:20 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:00:20 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:00:20 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:00:20 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:00:20 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:00:20 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:00:20 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:00:20 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:00:20 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:00:20 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:00:20 turk kernel: [    0.000000] Node 0: aperture @ 1302000000 size 32 MB
Jun 10 11:00:20 turk kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jun 10 11:00:20 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:00:20 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:00:20 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:00:20 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:00:20 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:00:20 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:00:20 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:00:20 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:00:20 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:00:20 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:00:20 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:00:20 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:00:20 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:00:20 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:00:20 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:00:20 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:00:20 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:00:20 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:00:20 turk kernel: [    0.000000] Detected 3214.292 MHz processor.
Jun 10 11:00:20 turk kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.58 BogoMIPS (lpj=12857168)
Jun 10 11:00:20 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:00:20 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:00:20 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:00:20 turk kernel: [    0.004039] Yama: becoming mindful.
Jun 10 11:00:20 turk kernel: [    0.004343] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:00:20 turk kernel: [    0.008824] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:00:20 turk kernel: [    0.009436] Mount-cache hash table entries: 256
Jun 10 11:00:20 turk kernel: [    0.009538] Initializing cgroup subsys cpuacct
Jun 10 11:00:20 turk kernel: [    0.009542] Initializing cgroup subsys memory
Jun 10 11:00:20 turk kernel: [    0.009549] Initializing cgroup subsys devices
Jun 10 11:00:20 turk kernel: [    0.009550] Initializing cgroup subsys freezer
Jun 10 11:00:20 turk kernel: [    0.009552] Initializing cgroup subsys blkio
Jun 10 11:00:20 turk kernel: [    0.009557] Initializing cgroup subsys perf_event
Jun 10 11:00:20 turk kernel: [    0.009580] tseg: 0000000000
Jun 10 11:00:20 turk kernel: [    0.009590] CPU: Physical Processor ID: 0
Jun 10 11:00:20 turk kernel: [    0.009591] CPU: Processor Core ID: 0
Jun 10 11:00:20 turk kernel: [    0.009593] mce: CPU supports 6 MCE banks
Jun 10 11:00:20 turk kernel: [    0.010751] ACPI: Core revision 20110623
Jun 10 11:00:20 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:00:20 turk kernel: [    0.020382] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:00:20 turk kernel: [    0.060495] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:00:20 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:00:20 turk kernel: [    0.064003] ... version:                0
Jun 10 11:00:20 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:00:20 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:00:20 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:00:20 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:00:20 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:00:20 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:00:20 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:00:20 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.152084]  #2
Jun 10 11:00:20 turk kernel: [    0.152085] smpboot cpu 2: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.244079]  #3
Jun 10 11:00:20 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.336051] Brought up 4 CPUs
Jun 10 11:00:20 turk kernel: [    0.336053] Total of 4 processors activated (25714.37 BogoMIPS).
Jun 10 11:00:20 turk kernel: [    0.340159] devtmpfs: initialized
Jun 10 11:00:20 turk kernel: [    0.341186] EVM: security.selinux
Jun 10 11:00:20 turk kernel: [    0.341187] EVM: security.SMACK64
Jun 10 11:00:20 turk kernel: [    0.341188] EVM: security.capability
Jun 10 11:00:20 turk kernel: [    0.341284] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:00:20 turk kernel: [    0.341284] print_constraints: dummy: 
Jun 10 11:00:20 turk kernel: [    0.341284] RTC time: 10:00:00, date: 06/10/12
Jun 10 11:00:20 turk kernel: [    0.341284] NET: Registered protocol family 16
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: io port [1000, ffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] TOM: 00000000d0000000 aka 3328M
Jun 10 11:00:20 turk kernel: [    0.341284] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:00:20 turk kernel: [    0.341284] TOM2: 0000000130000000 aka 4864M
Jun 10 11:00:20 turk kernel: [    0.341284] bus: [00, 07] on node 0 link 0
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] Extended Config Space enabled on 1 nodes
Jun 10 11:00:20 turk kernel: [    0.341284] ACPI: bus type pci registered
Jun 10 11:00:20 turk kernel: [    0.341284] Trying to unpack rootfs image as initramfs...
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: not using MMCONFIG
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: Using configuration type 1 for base access
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: Using configuration type 1 for extended access
Jun 10 11:00:20 turk kernel: [    0.341461] bio: create slab <bio-0> at 0
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Module Device)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Processor Device)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:00:20 turk kernel: [    0.344473] ACPI: EC: Look up EC in DSDT
Jun 10 11:00:20 turk kernel: [    0.380085] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:00:20 turk kernel: [    0.552580] ACPI: Interpreter enabled
Jun 10 11:00:20 turk kernel: [    0.552586] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:00:20 turk kernel: [    0.552602] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:00:20 turk kernel: [    0.552621] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:00:20 turk kernel: [    0.553992] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:00:20 turk kernel: [    0.557742] Freeing initrd memory: 13844k freed
Jun 10 11:00:20 turk kernel: [    0.646051] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:00:20 turk kernel: [    0.646149] ACPI: No dock devices found.
Jun 10 11:00:20 turk kernel: [    0.646150] HEST: Table not found.
Jun 10 11:00:20 turk kernel: [    0.646153] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:00:20 turk kernel: [    0.646209] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:00:20 turk kernel: [    0.646324] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.646326] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.646328] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.646330] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.646331] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.646333] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.646345] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.646387] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646416] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646418] pci 0000:00:02.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646433] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646461] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646463] pci 0000:00:07.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646475] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646502] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646504] pci 0000:00:09.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646515] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646542] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646544] pci 0000:00:0a.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646568] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.646586] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:00:20 turk kernel: [    0.646594] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:00:20 turk kernel: [    0.646603] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:00:20 turk kernel: [    0.646611] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:00:20 turk kernel: [    0.646619] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:00:20 turk kernel: [    0.646627] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:00:20 turk kernel: [    0.646645] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:00:20 turk kernel: [    0.646696] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646708] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:00:20 turk kernel: [    0.646769] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646785] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:00:20 turk kernel: [    0.646856] pci 0000:00:12.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.646857] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.646860] pci 0000:00:12.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646878] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646889] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:00:20 turk kernel: [    0.646950] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646966] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:00:20 turk kernel: [    0.647037] pci 0000:00:13.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.647038] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.647041] pci 0000:00:13.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647058] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:00:20 turk kernel: [    0.647124] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.647138] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:00:20 turk kernel: [    0.647146] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:00:20 turk kernel: [    0.647155] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:00:20 turk kernel: [    0.647163] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:00:20 turk kernel: [    0.647171] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:00:20 turk kernel: [    0.647221] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:00:20 turk kernel: [    0.647240] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:00:20 turk kernel: [    0.647296] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.647299] pci 0000:00:14.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647310] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:00:20 turk kernel: [    0.647376] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.647411] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647423] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:00:20 turk kernel: [    0.647481] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647492] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:00:20 turk kernel: [    0.647553] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647569] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:00:20 turk kernel: [    0.647640] pci 0000:00:16.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.647641] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.647644] pci 0000:00:16.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647660] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647673] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647683] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647693] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647706] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647749] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:00:20 turk kernel: [    0.647757] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:00:20 turk kernel: [    0.647767] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.647776] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.647783] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:00:20 turk kernel: [    0.647789] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:00:20 turk kernel: [    0.647840] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:00:20 turk kernel: [    0.647849] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:00:20 turk kernel: [    0.652059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:00:20 turk kernel: [    0.652064] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.652066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.652069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.652115] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:00:20 turk kernel: [    0.652144] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:00:20 turk kernel: [    0.652159] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:00:20 turk kernel: [    0.652284] pci 0000:02:00.0: supports D2
Jun 10 11:00:20 turk kernel: [    0.652285] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.652291] pci 0000:02:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.660063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:00:20 turk kernel: [    0.660067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.660069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.660115] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.660137] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:00:20 turk kernel: [    0.660152] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:00:20 turk kernel: [    0.660166] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:00:20 turk kernel: [    0.660181] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:00:20 turk kernel: [    0.660195] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:00:20 turk kernel: [    0.660223] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:00:20 turk kernel: [    0.660297] pci 0000:03:00.0: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.660298] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.660304] pci 0000:03:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.668061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:00:20 turk kernel: [    0.668065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.668067] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.668102] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:00:20 turk kernel: [    0.668116] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:00:20 turk kernel: [    0.668135] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.668147] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.668199] pci 0000:04:00.0: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.668200] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.668204] pci 0000:04:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.676059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:00:20 turk kernel: [    0.676063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.676067] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.676121] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676129] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676131] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676132] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676134] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676136] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676137] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:00:20 turk kernel: [    0.676253] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:00:20 turk kernel: [    0.676275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:00:20 turk kernel: [    0.676291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:00:20 turk kernel: [    0.676310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:00:20 turk kernel: [    0.676329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:00:20 turk kernel: [    0.676364]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:00:20 turk kernel: [    0.676366]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:00:20 turk kernel: [    0.676368] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:00:20 turk kernel: [    0.679423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679468] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679511] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679552] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679584] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679611] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679636] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679660] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: loaded
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:00:20 turk kernel: [    0.679735] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:00:20 turk kernel: [    0.679735] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:00:20 turk kernel: [    0.679735] SCSI subsystem initialized
Jun 10 11:00:20 turk kernel: [    0.679735] libata version 3.00 loaded.
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new interface driver usbfs
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new interface driver hub
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new device driver usb
Jun 10 11:00:20 turk kernel: [    0.680068] PCI: Using ACPI for IRQ routing
Jun 10 11:00:20 turk kernel: [    0.687446] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:00:20 turk kernel: [    0.687514] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:00:20 turk kernel: [    0.687516] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:00:20 turk kernel: [    0.687584] NetLabel: Initializing
Jun 10 11:00:20 turk kernel: [    0.687585] NetLabel:  domain hash size = 128
Jun 10 11:00:20 turk kernel: [    0.687586] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:00:20 turk kernel: [    0.687594] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:00:20 turk kernel: [    0.687622] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:00:20 turk kernel: [    0.687622] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:00:20 turk kernel: [    0.689066] Switching to clocksource hpet
Jun 10 11:00:20 turk kernel: [    0.692695] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:00:20 turk kernel: [    0.692711] pnp: PnP ACPI init
Jun 10 11:00:20 turk kernel: [    0.692721] ACPI: bus type pnp registered
Jun 10 11:00:20 turk kernel: [    0.692795] pnp 00:00: [bus 00-ff]
Jun 10 11:00:20 turk kernel: [    0.692797] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:00:20 turk kernel: [    0.692799] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:00:20 turk kernel: [    0.692800] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:00:20 turk kernel: [    0.692802] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:00:20 turk kernel: [    0.692803] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:00:20 turk kernel: [    0.692805] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:00:20 turk kernel: [    0.692807] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:00:20 turk kernel: [    0.692841] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:00:20 turk kernel: [    0.692894] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.692896] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.692928] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.693418] pnp 00:02: [dma 4]
Jun 10 11:00:20 turk kernel: [    0.693420] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:00:20 turk kernel: [    0.693421] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:00:20 turk kernel: [    0.693423] pnp 00:02: [io  0x0087]
Jun 10 11:00:20 turk kernel: [    0.693424] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:00:20 turk kernel: [    0.693425] pnp 00:02: [io  0x008f]
Jun 10 11:00:20 turk kernel: [    0.693426] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:00:20 turk kernel: [    0.693447] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:00:20 turk kernel: [    0.693453] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:00:20 turk kernel: [    0.693461] pnp 00:03: [irq 8]
Jun 10 11:00:20 turk kernel: [    0.693482] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:00:20 turk kernel: [    0.693487] pnp 00:04: [io  0x0061]
Jun 10 11:00:20 turk kernel: [    0.693508] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:00:20 turk kernel: [    0.693513] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:00:20 turk kernel: [    0.693517] pnp 00:05: [irq 13]
Jun 10 11:00:20 turk kernel: [    0.693536] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:00:20 turk kernel: [    0.693983] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:00:20 turk kernel: [    0.693986] pnp 00:06: [irq 7]
Jun 10 11:00:20 turk kernel: [    0.693988] pnp 00:06: [dma 0 disabled]
Jun 10 11:00:20 turk kernel: [    0.694153] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:00:20 turk kernel: [    0.694179] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:00:20 turk kernel: [    0.694202] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:00:20 turk kernel: [    0.694526] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:00:20 turk kernel: [    0.694529] pnp 00:08: [irq 4]
Jun 10 11:00:20 turk kernel: [    0.694530] pnp 00:08: [dma 0 disabled]
Jun 10 11:00:20 turk kernel: [    0.694594] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:00:20 turk kernel: [    0.694640] pnp 00:09: [io  0x0060]
Jun 10 11:00:20 turk kernel: [    0.694641] pnp 00:09: [io  0x0064]
Jun 10 11:00:20 turk kernel: [    0.694644] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:00:20 turk kernel: [    0.694646] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:00:20 turk kernel: [    0.694682] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.694684] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694686] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.694776] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:00:20 turk kernel: [    0.694778] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:00:20 turk kernel: [    0.694779] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:00:20 turk kernel: [    0.694780] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:00:20 turk kernel: [    0.694782] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:00:20 turk kernel: [    0.694783] pnp 00:0a: [io  0x0080]
Jun 10 11:00:20 turk kernel: [    0.694784] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:00:20 turk kernel: [    0.694785] pnp 00:0a: [io  0x0088]
Jun 10 11:00:20 turk kernel: [    0.694787] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:00:20 turk kernel: [    0.694788] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:00:20 turk kernel: [    0.694789] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:00:20 turk kernel: [    0.694790] pnp 00:0a: [io  0x00b1]
Jun 10 11:00:20 turk kernel: [    0.694791] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:00:20 turk kernel: [    0.694793] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:00:20 turk kernel: [    0.694794] pnp 00:0a: [io  0x040b]
Jun 10 11:00:20 turk kernel: [    0.694795] pnp 00:0a: [io  0x04d6]
Jun 10 11:00:20 turk kernel: [    0.694796] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:00:20 turk kernel: [    0.694798] pnp 00:0a: [io  0x0c14]
Jun 10 11:00:20 turk kernel: [    0.694799] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:00:20 turk kernel: [    0.694800] pnp 00:0a: [io  0x0c52]
Jun 10 11:00:20 turk kernel: [    0.694801] pnp 00:0a: [io  0x0c6c]
Jun 10 11:00:20 turk kernel: [    0.694802] pnp 00:0a: [io  0x0c6f]
Jun 10 11:00:20 turk kernel: [    0.694803] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:00:20 turk kernel: [    0.694805] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:00:20 turk kernel: [    0.694806] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:00:20 turk kernel: [    0.694807] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:00:20 turk kernel: [    0.694808] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:00:20 turk kernel: [    0.694810] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:00:20 turk kernel: [    0.694811] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:00:20 turk kernel: [    0.694812] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.694814] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:00:20 turk kernel: [    0.694815] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:00:20 turk kernel: [    0.694816] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:00:20 turk kernel: [    0.694818] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:00:20 turk kernel: [    0.694819] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:00:20 turk kernel: [    0.694820] pnp 00:0a: [io  0x0060]
Jun 10 11:00:20 turk kernel: [    0.694821] pnp 00:0a: [io  0x0064]
Jun 10 11:00:20 turk kernel: [    0.694823] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:00:20 turk kernel: [    0.694824] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:00:20 turk kernel: [    0.694826] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:00:20 turk kernel: [    0.694827] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:00:20 turk kernel: [    0.694830] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.694905] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694907] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694908] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694910] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694912] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694914] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694915] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694917] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694918] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694920] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694922] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694924] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694926] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694927] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694929] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694931] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694934] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694936] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694938] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694939] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694941] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694943] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694945] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694947] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694949] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694952] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695049] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.695050] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:00:20 turk kernel: [    0.695052] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:00:20 turk kernel: [    0.695053] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:00:20 turk kernel: [    0.695054] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:00:20 turk kernel: [    0.695089] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695091] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695093] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695094] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695096] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695125] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:00:20 turk kernel: [    0.695158] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695160] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695227] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:00:20 turk kernel: [    0.695229] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:00:20 turk kernel: [    0.695230] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:00:20 turk kernel: [    0.695232] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:00:20 turk kernel: [    0.695233] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:00:20 turk kernel: [    0.695268] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695270] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695272] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695274] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695276] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695278] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:00:20 turk kernel: [    0.695343] pnp: PnP ACPI: found 14 devices
Jun 10 11:00:20 turk kernel: [    0.695344] ACPI: ACPI bus type pnp unregistered
Jun 10 11:00:20 turk kernel: [    0.701735] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:00:20 turk kernel: [    0.701753] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:00:20 turk kernel: [    0.701756] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.701758] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.701761] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701764] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:00:20 turk kernel: [    0.701766] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.701768] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.701772] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:00:20 turk kernel: [    0.701773] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.701776] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701779] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:00:20 turk kernel: [    0.701781] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.701784] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701787] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:00:20 turk kernel: [    0.701806] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    0.701809] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701815] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    0.701817] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701823] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    0.701825] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701828] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    0.701830] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701836] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.701838] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.701840] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.701841] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.701843] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.701845] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701846] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.701848] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.701850] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701852] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.701854] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.701856] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.701857] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701859] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.701861] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701863] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.701865] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.701867] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.701868] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.701870] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.701872] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701901] NET: Registered protocol family 2
Jun 10 11:00:20 turk kernel: [    0.702008] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:00:20 turk kernel: [    0.702902] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:00:20 turk kernel: [    0.705370] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:00:20 turk kernel: [    0.705677] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:00:20 turk kernel: [    0.705679] TCP reno registered
Jun 10 11:00:20 turk kernel: [    0.705686] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:00:20 turk kernel: [    0.705715] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:00:20 turk kernel: [    0.705806] NET: Registered protocol family 1
Jun 10 11:00:20 turk kernel: [    0.705835] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.524036] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.524048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.524089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.524094] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.604039] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.604049] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.604089] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.604103] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.684032] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:00:20 turk kernel: [    1.684042] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.764040] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.764050] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.764090] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.764109] pci 0000:01:00.0: Boot video device
Jun 10 11:00:20 turk kernel: [    1.764125] PCI: CLS 64 bytes, default 64
Jun 10 11:00:20 turk kernel: [    1.765385] PCI-DMA: Disabling AGP.
Jun 10 11:00:20 turk kernel: [    1.765458] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:00:20 turk kernel: [    1.765459] PCI-DMA: using GART IOMMU.
Jun 10 11:00:20 turk kernel: [    1.765462] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:00:20 turk kernel: [    1.768918] IBS: LVT offset 1 assigned
Jun 10 11:00:20 turk kernel: [    1.768935] perf: AMD IBS detected (0x0000001f)
Jun 10 11:00:20 turk kernel: [    1.769046] audit: initializing netlink socket (disabled)
Jun 10 11:00:20 turk kernel: [    1.769060] type=2000 audit(1339322401.764:1): initialized
Jun 10 11:00:20 turk kernel: [    1.793136] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:00:20 turk kernel: [    1.812150] VFS: Disk quotas dquot_6.5.2
Jun 10 11:00:20 turk kernel: [    1.812192] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:00:20 turk kernel: [    1.812614] fuse init (API version 7.17)
Jun 10 11:00:20 turk kernel: [    1.812681] msgmni has been set to 7901
Jun 10 11:00:20 turk kernel: [    1.813004] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:00:20 turk kernel: [    1.813031] io scheduler noop registered
Jun 10 11:00:20 turk kernel: [    1.813033] io scheduler deadline registered
Jun 10 11:00:20 turk kernel: [    1.813053] io scheduler cfq registered (default)
Jun 10 11:00:20 turk kernel: [    1.813174] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813202] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813282] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813300] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813365] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813384] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813445] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813462] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:00:20 turk kernel: [    1.813532] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:00:20 turk kernel: [    1.813624] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:00:20 turk kernel: [    1.813628] ACPI: Power Button [PWRB]
Jun 10 11:00:20 turk kernel: [    1.813656] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:00:20 turk kernel: [    1.813658] ACPI: Power Button [PWRF]
Jun 10 11:00:20 turk kernel: [    1.996934] ERST: Table is not found!
Jun 10 11:00:20 turk kernel: [    1.996936] GHES: HEST is not enabled!
Jun 10 11:00:20 turk kernel: [    1.997012] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:00:20 turk kernel: [    2.017420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:00:20 turk kernel: [    2.064783] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:00:20 turk kernel: [    2.112219] Linux agpgart interface v0.103
Jun 10 11:00:20 turk kernel: [    2.113254] brd: module loaded
Jun 10 11:00:20 turk kernel: [    2.113782] loop: module loaded
Jun 10 11:00:20 turk kernel: [    2.113927] ahci 0000:00:11.0: version 3.0
Jun 10 11:00:20 turk kernel: [    2.113937] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    2.113987] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    2.114058] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:00:20 turk kernel: [    2.114060] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:00:20 turk kernel: [    2.114472] scsi0 : ahci
Jun 10 11:00:20 turk kernel: [    2.114539] scsi1 : ahci
Jun 10 11:00:20 turk kernel: [    2.114590] scsi2 : ahci
Jun 10 11:00:20 turk kernel: [    2.114641] scsi3 : ahci
Jun 10 11:00:20 turk kernel: [    2.114709] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:00:20 turk kernel: [    2.114712] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:00:20 turk kernel: [    2.114714] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:00:20 turk kernel: [    2.114717] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:00:20 turk kernel: [    2.114849] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.114869] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.114930] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.114947] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.114956] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    2.115244] Fixed MDIO Bus: probed
Jun 10 11:00:20 turk kernel: [    2.115258] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:00:20 turk kernel: [    2.115259] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:00:20 turk kernel: [    2.115298] PPP generic driver version 2.4.2
Jun 10 11:00:20 turk kernel: [    2.115370] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:00:20 turk kernel: [    2.115407] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.115417] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.115460] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:00:20 turk kernel: [    2.115466] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.115480] QUIRK: Enable AMD PLL fix
Jun 10 11:00:20 turk kernel: [    2.115489] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.115505] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:00:20 turk kernel: [    2.124040] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.124142] hub 1-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.124146] hub 1-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.124246] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.124259] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.124292] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:00:20 turk kernel: [    2.124298] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.124314] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.124325] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:00:20 turk kernel: [    2.136041] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.136130] hub 2-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.136133] hub 2-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.136237] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.136248] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.136282] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:00:20 turk kernel: [    2.136288] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.136304] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.136314] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:00:20 turk kernel: [    2.148040] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.148125] hub 3-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.148127] hub 3-0:1.0: 4 ports detected
Jun 10 11:00:20 turk kernel: [    2.148189] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:00:20 turk kernel: [    2.148245] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.148258] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.148291] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:00:20 turk kernel: [    2.148312] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:00:20 turk kernel: [    2.208098] hub 4-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.208103] hub 4-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.208211] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.208222] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.208258] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:00:20 turk kernel: [    2.208270] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:00:20 turk kernel: [    2.268098] hub 5-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.268103] hub 5-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.268209] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.268220] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.268253] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:00:20 turk kernel: [    2.268265] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:00:20 turk kernel: [    2.328118] hub 6-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.328124] hub 6-0:1.0: 2 ports detected
Jun 10 11:00:20 turk kernel: [    2.328228] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.328240] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.328274] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:00:20 turk kernel: [    2.328286] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:00:20 turk kernel: [    2.388145] hub 7-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.388150] hub 7-0:1.0: 4 ports detected
Jun 10 11:00:20 turk kernel: [    2.388216] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:00:20 turk kernel: [    2.388263] usbcore: registered new interface driver libusual
Jun 10 11:00:20 turk kernel: [    2.388287] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:00:20 turk kernel: [    2.388645] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:00:20 turk kernel: [    2.388651] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:00:20 turk kernel: [    2.388774] mousedev: PS/2 mouse device common for all mice
Jun 10 11:00:20 turk kernel: [    2.388879] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:00:20 turk kernel: [    2.388957] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:00:20 turk kernel: [    2.388978] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:00:20 turk kernel: [    2.389031] device-mapper: uevent: version 1.0.3
Jun 10 11:00:20 turk kernel: [    2.389078] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:00:20 turk kernel: [    2.389084] cpuidle: using governor ladder
Jun 10 11:00:20 turk kernel: [    2.389085] cpuidle: using governor menu
Jun 10 11:00:20 turk kernel: [    2.389087] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:00:20 turk kernel: [    2.389229] TCP cubic registered
Jun 10 11:00:20 turk kernel: [    2.389295] NET: Registered protocol family 10
Jun 10 11:00:20 turk kernel: [    2.389603] NET: Registered protocol family 17
Jun 10 11:00:20 turk kernel: [    2.389614] Registering the dns_resolver key type
Jun 10 11:00:20 turk kernel: [    2.389722] PM: Hibernation image not present or could not be loaded.
Jun 10 11:00:20 turk kernel: [    2.389729] registered taskstats version 1
Jun 10 11:00:20 turk kernel: [    2.404088]   Magic number: 0:770:21
Jun 10 11:00:20 turk kernel: [    2.404136] pcieport 0000:00:09.0: hash matches
Jun 10 11:00:20 turk kernel: [    2.404180] rtc_cmos 00:03: setting system clock to 2012-06-10 10:00:02 UTC (1339322402)
Jun 10 11:00:20 turk kernel: [    2.404194] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:00:20 turk kernel: [    2.404218] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:00:20 turk kernel: [    2.404219] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:00:20 turk kernel: [    2.404220] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:00:20 turk kernel: [    2.404222] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:00:20 turk kernel: [    2.404643] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:00:20 turk kernel: [    2.404645] EDD information not available.
Jun 10 11:00:20 turk kernel: [    2.432093] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.436066] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.604036] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.604062] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.605184] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:00:20 turk kernel: [    2.605187] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:00:20 turk kernel: [    2.605653] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:00:20 turk kernel: [    2.606451] ata1.00: configured for UDMA/133
Jun 10 11:00:20 turk kernel: [    2.606592] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:00:20 turk kernel: [    2.606719] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:00:20 turk kernel: [    2.606736] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:00:20 turk kernel: [    2.606819] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:00:20 turk kernel: [    2.606821] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:00:20 turk kernel: [    2.606869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:00:20 turk kernel: [    2.607568] ata2.00: configured for UDMA/100
Jun 10 11:00:20 turk kernel: [    2.609373] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:00:20 turk kernel: [    2.611498] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:00:20 turk kernel: [    2.611501] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:00:20 turk kernel: [    2.611595] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:00:20 turk kernel: [    2.611657] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:00:20 turk kernel: [    2.658346]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:00:20 turk kernel: [    2.658827] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:00:20 turk kernel: [    2.659892] Freeing unused kernel memory: 920k freed
Jun 10 11:00:20 turk kernel: [    2.660077] Write protecting the kernel read-only data: 12288k
Jun 10 11:00:20 turk kernel: [    2.664009] Freeing unused kernel memory: 1608k freed
Jun 10 11:00:20 turk kernel: [    2.667175] Freeing unused kernel memory: 1196k freed
Jun 10 11:00:20 turk kernel: [    2.697568] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:00:20 turk kernel: [    2.697588] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.697641] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.698480] scsi4 : pata_via
Jun 10 11:00:20 turk kernel: [    2.699196] scsi5 : pata_via
Jun 10 11:00:20 turk kernel: [    2.699312] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:00:20 turk kernel: [    2.699314] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:00:20 turk kernel: [    2.700059] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:00:20 turk kernel: [    2.700259] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:00:20 turk kernel: [    2.700275] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.700301] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.700342] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    2.700654] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc9000065e000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:00:20 turk kernel: [    2.700656] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:00:20 turk kernel: [    2.709877] scsi6 : pata_atiixp
Jun 10 11:00:20 turk kernel: [    2.710277] scsi7 : pata_atiixp
Jun 10 11:00:20 turk kernel: [    2.710684] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:00:20 turk kernel: [    2.710686] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:00:20 turk kernel: [    2.768027] Refined TSC clocksource calibration: 3214.267 MHz.
Jun 10 11:00:20 turk kernel: [    2.768036] Switching to clocksource tsc
Jun 10 11:00:20 turk kernel: [    3.021527] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    3.021534] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    3.030208] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:00:20 turk kernel: [    3.030299] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:00:20 turk kernel: [    3.030310] usbcore: registered new interface driver usbhid
Jun 10 11:00:20 turk kernel: [    3.030311] usbhid: USB HID core driver
Jun 10 11:00:20 turk kernel: [    3.084079] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:00:20 turk kernel: [    3.132037] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:00:20 turk kernel: [    3.314226] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:00:20 turk kernel: [    3.314299] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:00:20 turk kernel: [    3.333131] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:00:20 turk kernel: [    3.333194] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:00:20 turk kernel: [    3.584091] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:00:20 turk kernel: [    3.670411] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:00:20 turk kernel: [   15.184901] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk kernel: [   15.212732] lp: driver loaded but no devices found
Jun 10 11:00:20 turk kernel: [   15.223056] wmi: Mapper loaded
Jun 10 11:00:20 turk kernel: [   15.245792] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:00:20 turk kernel: [   15.245841] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:00:20 turk kernel: [   15.261141] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:00:20 turk kernel: [   15.261143] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:00:20 turk kernel: [   15.261387] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:00:20 turk kernel: [   15.261442] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:00:20 turk kernel: [   15.270531] MCE: In-kernel MCE decoding enabled.
Jun 10 11:00:20 turk kernel: [   15.270971] EDAC MC: Ver: 2.1.0
Jun 10 11:00:20 turk kernel: [   15.271946] AMD64 EDAC driver v3.4.0
Jun 10 11:00:20 turk kernel: [   15.273187] EDAC amd64: DRAM ECC disabled.
Jun 10 11:00:20 turk kernel: [   15.273193] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:00:20 turk kernel: [   15.273194]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:00:20 turk kernel: [   15.273195]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:00:20 turk kernel: [   15.273557] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:00:20 turk kernel: [   15.280351] type=1400 audit(1339322415.372:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.280708] type=1400 audit(1339322415.372:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.280916] type=1400 audit(1339322415.372:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.315076] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:00:20 turk kernel: [   15.340270] lp0: using parport0 (interrupt-driven).
Jun 10 11:00:20 turk kernel: [   15.351212] ppdev: user-space parallel port driver
Jun 10 11:00:20 turk kernel: [   15.365545] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:00:20 turk kernel: [   15.365609] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:00:20 turk kernel: [   15.365656] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:00:20 turk kernel: [   15.365700] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:00:20 turk kernel: [   15.365744] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:00:20 turk kernel: [   15.365788] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:00:20 turk kernel: [   15.365831] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:00:20 turk kernel: [   15.365875] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:00:20 turk kernel: [   15.366098] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [   15.366101] hda_intel: Disabling MSI
Jun 10 11:00:20 turk kernel: [   15.366131] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [   15.728188] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:00:20 turk kernel: [   15.728191] Disabling lock debugging due to kernel taint
Jun 10 11:00:20 turk kernel: [   16.196021] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.220020] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.244026] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.268032] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.268100] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:00:20 turk kernel: [   16.268167] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:00:20 turk kernel: [   16.268216] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:00:20 turk kernel: [   16.268264] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:00:20 turk kernel: [   16.268621] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [   16.268628] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [   16.268632] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:00:20 turk kernel: [   16.268825] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:00:20 turk kernel: [   16.712058] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:00:20 turk kernel: [   16.712061] vesafb: scrolling: redraw
Jun 10 11:00:20 turk kernel: [   16.712063] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:00:20 turk kernel: [   16.716329] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:00:20 turk kernel: [   16.716491] Console: switching to colour frame buffer device 80x30
Jun 10 11:00:20 turk kernel: [   16.716501] fb0: VESA VGA frame buffer device
Jun 10 11:00:20 turk kernel: [   17.180278] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:00:20 turk kernel: [   17.329797] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:00:20 turk kernel: [   20.559233] init: failsafe main process (933) killed by TERM signal
Jun 10 11:00:20 turk kernel: [   20.579738] Bluetooth: Core ver 2.16
Jun 10 11:00:20 turk kernel: [   20.579754] NET: Registered protocol family 31
Jun 10 11:00:20 turk kernel: [   20.579755] Bluetooth: HCI device and connection manager initialized
Jun 10 11:00:20 turk kernel: [   20.579757] Bluetooth: HCI socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.579759] Bluetooth: L2CAP socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.579762] Bluetooth: SCO socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.581057] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:00:20 turk kernel: [   20.581059] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:00:20 turk NetworkManager[980]: <info> NetworkManager (version 0.9.4.0) is starting...
Jun 10 11:00:20 turk NetworkManager[980]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 10 11:00:20 turk kernel: [   20.650729] type=1400 audit(1339322420.740:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1000 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.651158] type=1400 audit(1339322420.740:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1000 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.651795] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:00:20 turk kernel: [   20.651798] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.651799] Bluetooth: RFCOMM ver 1.11
Jun 10 11:00:20 turk NetworkManager[980]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 10 11:00:20 turk NetworkManager[980]: <info> DNS: loaded plugin dnsmasq
Jun 10 11:00:20 turk avahi-daemon[1011]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully dropped root privileges.
Jun 10 11:00:20 turk avahi-daemon[1011]: avahi-daemon 0.6.30 starting up.
Jun 10 11:00:20 turk dbus[957]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully called chroot().
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully dropped remaining capabilities.
Jun 10 11:00:20 turk avahi-daemon[1011]: Loading service file /services/udisks.service.
Jun 10 11:00:20 turk polkitd[1015]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:00:20 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: init!
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:00:20 turk NetworkManager[980]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:00:20 turk NetworkManager[980]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: (39508784) ... get_connections.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: (39508784) ... get_connections (managed=false): return empty list.
Jun 10 11:00:20 turk NetworkManager[980]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:00:20 turk NetworkManager[980]: <info> modem-manager is now available
Jun 10 11:00:20 turk NetworkManager[980]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:00:20 turk NetworkManager[980]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> Networking is enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): carrier is OFF
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): now managed
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): bringing up device.
Jun 10 11:00:20 turk kernel: [   20.727733] type=1400 audit(1339322420.816:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1041 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728015] type=1400 audit(1339322420.816:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728387] type=1400 audit(1339322420.820:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728595] type=1400 audit(1339322420.820:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.730676] type=1400 audit(1339322420.820:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1045 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.730756] type=1400 audit(1339322420.820:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.731095] type=1400 audit(1339322420.820:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1045 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.731231] type=1400 audit(1339322420.820:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
Jun 10 11:00:20 turk anacron[1121]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:20 turk cron[1105]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:00:20 turk acpid: starting up with proc fs
Jun 10 11:00:20 turk cron[1133]: (CRON) STARTUP (fork ok)
Jun 10 11:00:20 turk acpid: 35 rules loaded
Jun 10 11:00:20 turk acpid: waiting for events: event logging is off
Jun 10 11:00:20 turk cron[1133]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:00:20 turk kernel: [   20.859531] r8169 0000:04:00.0: eth0: link down
Jun 10 11:00:20 turk kernel: [   20.859544] r8169 0000:04:00.0: eth0: link down
Jun 10 11:00:20 turk kernel: [   20.859889] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk avahi-daemon[1011]: Network interface enumeration completed.
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): preparing device.
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:00:20 turk avahi-daemon[1011]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 10 11:00:20 turk avahi-daemon[1011]: Server startup complete. Host name is turk.local. Local service cookie is 85714046.
Jun 10 11:00:20 turk avahi-daemon[1011]: Service "turk" (/services/udisks.service) successfully established.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:00:20 turk kernel: [   20.860152] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk kernel: [   20.867930] vboxdrv: Found 4 processor cores.
Jun 10 11:00:20 turk kernel: [   20.868649] vboxdrv: fAsync=0 offMin=0x3f0 offMax=0x1670
Jun 10 11:00:20 turk kernel: [   20.868703] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:00:20 turk kernel: [   20.868704] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:00:20 turk kernel: [   20.874950] vboxpci: IOMMU not found (not registered)
Jun 10 11:00:21 turk acpid: client connected from 1237[0:0]
Jun 10 11:00:21 turk acpid: 1 client rule loaded
Jun 10 11:00:21 turk anacron[1121]: Normal exit (0 jobs run)
Jun 10 11:00:21 turk anacron[1265]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:21 turk anacron[1265]: Normal exit (0 jobs run)
Jun 10 11:00:21 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:00:21 turk udev-configure-printer: Failed to get parent
Jun 10 11:00:21 turk udev-configure-printer: add /module/lp
Jun 10 11:00:21 turk udev-configure-printer: Failed to get parent
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:00:22 turk kernel: [   22.442408] r8169 0000:04:00.0: eth0: link up
Jun 10 11:00:22 turk kernel: [   22.442720] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:00:22 turk NetworkManager[980]: <info> dhclient started with pid 1396
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:00:22 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:00:22 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:00:22 turk dhclient: All rights reserved.
Jun 10 11:00:22 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:00:22 turk dhclient: 
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:00:22 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:00:22 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:00:22 turk dhclient: Sending on   Socket/fallback
Jun 10 11:00:22 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:00:22 turk acpid: client connected from 1237[0:0]
Jun 10 11:00:22 turk acpid: 1 client rule loaded
Jun 10 11:00:22 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:00:22 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:00:22 turk dbus[957]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:00:22 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:00:22 turk accounts-daemon[1407]: started daemon version 0.6.15
Jun 10 11:00:23 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:00:23 turk dhclient: bound to 192.168.1.103 -- renewal in 33704 seconds.
Jun 10 11:00:23 turk NetworkManager[980]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:00:23 turk NetworkManager[980]: <info>   address 192.168.1.103
Jun 10 11:00:23 turk NetworkManager[980]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:00:23 turk NetworkManager[980]: <info>   gateway 192.168.1.1
Jun 10 11:00:23 turk NetworkManager[980]: <info>   nameserver '194.168.4.100'
Jun 10 11:00:23 turk NetworkManager[980]: <info>   nameserver '194.168.8.100'
Jun 10 11:00:23 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:00:23 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:00:23 turk avahi-daemon[1011]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Jun 10 11:00:23 turk avahi-daemon[1011]: New relevant interface eth0.IPv4 for mDNS.
Jun 10 11:00:23 turk avahi-daemon[1011]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:00:23 turk anacron[1617]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:23 turk anacron[1617]: Normal exit (0 jobs run)
Jun 10 11:00:23 turk avahi-daemon[1011]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::22cf:30ff:fe19:d13c.
Jun 10 11:00:23 turk avahi-daemon[1011]: New relevant interface eth0.IPv6 for mDNS.
Jun 10 11:00:23 turk avahi-daemon[1011]: Registering new address record for fe80::22cf:30ff:fe19:d13c on eth0.*.
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:00:24 turk dbus[957]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:00:24 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully called chroot.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully dropped privileges.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully limited resources.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Canary thread running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Watchdog thread running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully made thread 1742 of process 1742 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:00:24 turk NetworkManager[980]: <info> DNS: starting dnsmasq...
Jun 10 11:00:24 turk NetworkManager[980]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:00:24 turk dnsmasq[1748]: started, version 2.59 cache disabled
Jun 10 11:00:24 turk dnsmasq[1748]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:00:24 turk dnsmasq[1748]: using nameserver 194.168.8.100#53
Jun 10 11:00:24 turk dnsmasq[1748]: using nameserver 194.168.4.100#53
Jun 10 11:00:24 turk NetworkManager[980]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:00:24 turk NetworkManager[980]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:00:24 turk NetworkManager[980]: <info> Activation (eth0) successful, device activated.
Jun 10 11:00:24 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:00:24 turk dbus[957]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:00:24 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully made thread 1829 of process 1742 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:00:25 turk rtkit-daemon[1744]: Successfully made thread 1830 of process 1742 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:00:25 turk rtkit-daemon[1744]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:00:26 turk dbus[957]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:00:26 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:00:33 turk ntpdate[1808]: step time server 91.189.94.4 offset 0.795759 sec
Jun 10 11:00:33 turk kernel: [   32.624006] eth0: no IPv6 routers present
Jun 10 11:00:42 turk goa[2108]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:00:43 turk NetworkManager[980]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:01:04 turk kernel: [   63.206162] NVRM: Xid (0000:01:00): 32, Channel ID 00000005 intr 00040000
Jun 10 11:01:06 turk kernel: [   65.206369] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jun 10 11:01:08 turk kernel: [   67.206387] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jun 10 11:02:23 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:02:23 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1033" x-info="http://www.rsyslog.com"] start
Jun 10 11:02:23 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:02:23 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:02:23 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:02:23 turk dbus[990]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jun 10 11:02:23 turk polkitd[1064]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:02:23 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: init!
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:02:23 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:02:23 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:02:23 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:02:23 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:02:23 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:02:23 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:02:23 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:02:23 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:02:23 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:02:23 turk kernel: [    0.000000] DMI present.
Jun 10 11:02:23 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:02:23 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:02:23 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:02:23 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:02:23 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:02:23 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   3 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   4 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   5 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   6 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   7 disabled
Jun 10 11:02:23 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:02:23 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:02:23 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:02:23 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:02:23 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:02:23 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:02:23 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:02:23 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:02:23 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:02:23 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:02:23 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:02:23 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:02:23 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:02:23 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:02:23 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:02:23 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:02:23 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:02:23 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:02:23 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:02:23 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:02:23 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:02:23 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:02:23 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:02:23 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:02:23 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:02:23 turk NetworkManager[1032]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: (25504560) ... get_connections.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: (25504560) ... get_connections (managed=false): return empty list.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:02:23 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:02:23 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:02:23 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:02:23 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:02:23 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:02:23 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:02:23 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:02:23 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:02:23 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:02:23 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:02:23 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:02:23 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:02:23 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:02:23 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:02:23 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:02:23 turk kernel: [    0.000000] Node 0: aperture @ c4000000 size 32 MB
Jun 10 11:02:23 turk kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Jun 10 11:02:23 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:02:23 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:02:23 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:02:23 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:02:23 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:02:23 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:02:23 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:02:23 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:02:23 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:02:23 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:02:23 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:02:23 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:02:23 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:02:23 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:02:23 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:02:23 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:02:23 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:02:23 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:02:23 turk kernel: [    0.000000] Detected 3214.121 MHz processor.
Jun 10 11:02:23 turk kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.24 BogoMIPS (lpj=12856484)
Jun 10 11:02:23 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:02:23 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:02:23 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:02:23 turk kernel: [    0.004038] Yama: becoming mindful.
Jun 10 11:02:23 turk kernel: [    0.004343] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:02:23 turk kernel: [    0.008811] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:02:23 turk kernel: [    0.009413] Mount-cache hash table entries: 256
Jun 10 11:02:23 turk kernel: [    0.009513] Initializing cgroup subsys cpuacct
Jun 10 11:02:23 turk kernel: [    0.009518] Initializing cgroup subsys memory
Jun 10 11:02:23 turk kernel: [    0.009525] Initializing cgroup subsys devices
Jun 10 11:02:23 turk kernel: [    0.009527] Initializing cgroup subsys freezer
Jun 10 11:02:23 turk kernel: [    0.009528] Initializing cgroup subsys blkio
Jun 10 11:02:23 turk kernel: [    0.009533] Initializing cgroup subsys perf_event
Jun 10 11:02:23 turk kernel: [    0.009556] tseg: 0000000000
Jun 10 11:02:23 turk kernel: [    0.009565] CPU: Physical Processor ID: 0
Jun 10 11:02:23 turk kernel: [    0.009566] CPU: Processor Core ID: 0
Jun 10 11:02:23 turk kernel: [    0.009568] mce: CPU supports 6 MCE banks
Jun 10 11:02:23 turk kernel: [    0.010724] ACPI: Core revision 20110623
Jun 10 11:02:23 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:02:23 turk kernel: [    0.020381] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:02:23 turk kernel: [    0.063097] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:02:23 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:02:23 turk kernel: [    0.064003] ... version:                0
Jun 10 11:02:23 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:02:23 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:02:23 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:02:23 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:02:23 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:02:23 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:02:23 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:02:23 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.152083]  #2
Jun 10 11:02:23 turk kernel: [    0.152084] smpboot cpu 2: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.244079]  #3
Jun 10 11:02:23 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.336047] Brought up 4 CPUs
Jun 10 11:02:23 turk kernel: [    0.336049] Total of 4 processors activated (25714.02 BogoMIPS).
Jun 10 11:02:23 turk kernel: [    0.340158] devtmpfs: initialized
Jun 10 11:02:23 turk kernel: [    0.341186] EVM: security.selinux
Jun 10 11:02:23 turk kernel: [    0.341187] EVM: security.SMACK64
Jun 10 11:02:23 turk kernel: [    0.341188] EVM: security.capability
Jun 10 11:02:23 turk kernel: [    0.341284] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:02:23 turk kernel: [    0.341284] print_constraints: dummy: 
Jun 10 11:02:23 turk kernel: [    0.341284] RTC time: 10:02:02, date: 06/10/12
Jun 10 11:02:23 turk kernel: [    0.341284] NET: Registered protocol family 16
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: io port [1000, ffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] TOM: 00000000d0000000 aka 3328M
Jun 10 11:02:23 turk kernel: [    0.341284] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:02:23 turk kernel: [    0.341284] TOM2: 0000000130000000 aka 4864M
Jun 10 11:02:23 turk kernel: [    0.341284] bus: [00, 07] on node 0 link 0
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] Extended Config Space enabled on 1 nodes
Jun 10 11:02:23 turk kernel: [    0.341284] ACPI: bus type pci registered
Jun 10 11:02:23 turk kernel: [    0.341284] Trying to unpack rootfs image as initramfs...
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: not using MMCONFIG
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: Using configuration type 1 for base access
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: Using configuration type 1 for extended access
Jun 10 11:02:23 turk kernel: [    0.341456] bio: create slab <bio-0> at 0
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Module Device)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Processor Device)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:02:23 turk kernel: [    0.344428] ACPI: EC: Look up EC in DSDT
Jun 10 11:02:23 turk kernel: [    0.380091] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:02:23 turk kernel: [    0.548577] ACPI: Interpreter enabled
Jun 10 11:02:23 turk kernel: [    0.548582] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:02:23 turk kernel: [    0.548599] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:02:23 turk kernel: [    0.548620] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:02:23 turk kernel: [    0.549993] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:02:23 turk kernel: [    0.556884] Freeing initrd memory: 13844k freed
Jun 10 11:02:23 turk kernel: [    0.642053] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:02:23 turk kernel: [    0.642150] ACPI: No dock devices found.
Jun 10 11:02:23 turk kernel: [    0.642151] HEST: Table not found.
Jun 10 11:02:23 turk kernel: [    0.642154] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:02:23 turk kernel: [    0.642210] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:02:23 turk kernel: [    0.642325] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.642327] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.642329] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.642331] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.642332] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.642334] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.642346] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.642388] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642417] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642419] pci 0000:00:02.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642434] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642462] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642464] pci 0000:00:07.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642475] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642503] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642505] pci 0000:00:09.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642516] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642543] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642545] pci 0000:00:0a.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642569] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.642587] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:02:23 turk kernel: [    0.642595] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:02:23 turk kernel: [    0.642603] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:02:23 turk kernel: [    0.642612] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:02:23 turk kernel: [    0.642620] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:02:23 turk kernel: [    0.642628] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:02:23 turk kernel: [    0.642646] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:02:23 turk kernel: [    0.642697] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642708] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:02:23 turk kernel: [    0.642770] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642786] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:02:23 turk kernel: [    0.642857] pci 0000:00:12.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.642858] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.642861] pci 0000:00:12.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642879] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642890] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:02:23 turk kernel: [    0.642951] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642967] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:02:23 turk kernel: [    0.643037] pci 0000:00:13.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.643039] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.643042] pci 0000:00:13.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643059] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:02:23 turk kernel: [    0.643125] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.643139] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:02:23 turk kernel: [    0.643147] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:02:23 turk kernel: [    0.643155] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:02:23 turk kernel: [    0.643163] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:02:23 turk kernel: [    0.643172] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:02:23 turk kernel: [    0.643222] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:02:23 turk kernel: [    0.643240] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:02:23 turk kernel: [    0.643297] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.643300] pci 0000:00:14.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643311] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:02:23 turk kernel: [    0.643377] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.643412] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643424] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:02:23 turk kernel: [    0.643482] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643493] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:02:23 turk kernel: [    0.643554] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643570] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:02:23 turk kernel: [    0.643641] pci 0000:00:16.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.643643] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.643646] pci 0000:00:16.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643662] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643674] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643684] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643694] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643707] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643751] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:02:23 turk kernel: [    0.643759] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:02:23 turk kernel: [    0.643769] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.643778] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.643785] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:02:23 turk kernel: [    0.643791] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:02:23 turk kernel: [    0.643842] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:02:23 turk kernel: [    0.643850] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:02:23 turk kernel: [    0.648059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:02:23 turk kernel: [    0.648063] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.648066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.648069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.648117] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:02:23 turk kernel: [    0.648146] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:02:23 turk kernel: [    0.648161] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:02:23 turk kernel: [    0.648286] pci 0000:02:00.0: supports D2
Jun 10 11:02:23 turk kernel: [    0.648287] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.648293] pci 0000:02:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.656063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:02:23 turk kernel: [    0.656067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.656069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.656116] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.656137] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:02:23 turk kernel: [    0.656156] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:02:23 turk kernel: [    0.656170] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:02:23 turk kernel: [    0.656185] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:02:23 turk kernel: [    0.656199] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:02:23 turk kernel: [    0.656227] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:02:23 turk kernel: [    0.656301] pci 0000:03:00.0: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.656303] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.656308] pci 0000:03:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.664061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:02:23 turk kernel: [    0.664065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.664067] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.664102] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:02:23 turk kernel: [    0.664114] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:02:23 turk kernel: [    0.664133] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.664145] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.664197] pci 0000:04:00.0: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.664198] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.664202] pci 0000:04:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.672059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:02:23 turk kernel: [    0.672063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.672066] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.672121] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672128] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672130] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672132] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672134] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672135] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672137] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:02:23 turk kernel: [    0.672245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:02:23 turk kernel: [    0.672266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:02:23 turk kernel: [    0.672283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:02:23 turk kernel: [    0.672302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:02:23 turk kernel: [    0.672321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:02:23 turk kernel: [    0.672356]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:02:23 turk kernel: [    0.672358]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:02:23 turk kernel: [    0.672360] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:02:23 turk kernel: [    0.675416] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675460] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675503] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675545] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675577] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675628] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675652] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: loaded
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:02:23 turk kernel: [    0.675727] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:02:23 turk kernel: [    0.675727] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:02:23 turk kernel: [    0.675727] SCSI subsystem initialized
Jun 10 11:02:23 turk kernel: [    0.675727] libata version 3.00 loaded.
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new interface driver usbfs
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new interface driver hub
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new device driver usb
Jun 10 11:02:23 turk kernel: [    0.676060] PCI: Using ACPI for IRQ routing
Jun 10 11:02:23 turk kernel: [    0.683442] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:02:23 turk kernel: [    0.683509] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:02:23 turk kernel: [    0.683511] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:02:23 turk kernel: [    0.683580] NetLabel: Initializing
Jun 10 11:02:23 turk kernel: [    0.683581] NetLabel:  domain hash size = 128
Jun 10 11:02:23 turk kernel: [    0.683582] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:02:23 turk kernel: [    0.683590] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:02:23 turk kernel: [    0.683618] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:02:23 turk kernel: [    0.683618] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:02:23 turk kernel: [    0.685067] Switching to clocksource hpet
Jun 10 11:02:23 turk kernel: [    0.688702] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:02:23 turk kernel: [    0.688717] pnp: PnP ACPI init
Jun 10 11:02:23 turk kernel: [    0.688727] ACPI: bus type pnp registered
Jun 10 11:02:23 turk kernel: [    0.688802] pnp 00:00: [bus 00-ff]
Jun 10 11:02:23 turk kernel: [    0.688804] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:02:23 turk kernel: [    0.688806] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:02:23 turk kernel: [    0.688808] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:02:23 turk kernel: [    0.688809] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:02:23 turk kernel: [    0.688811] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:02:23 turk kernel: [    0.688812] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:02:23 turk kernel: [    0.688814] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:02:23 turk kernel: [    0.688850] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:02:23 turk kernel: [    0.688904] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.688905] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.688938] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.689432] pnp 00:02: [dma 4]
Jun 10 11:02:23 turk kernel: [    0.689433] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:02:23 turk kernel: [    0.689435] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:02:23 turk kernel: [    0.689436] pnp 00:02: [io  0x0087]
Jun 10 11:02:23 turk kernel: [    0.689437] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:02:23 turk kernel: [    0.689439] pnp 00:02: [io  0x008f]
Jun 10 11:02:23 turk kernel: [    0.689440] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:02:23 turk kernel: [    0.689461] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:02:23 turk kernel: [    0.689467] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:02:23 turk kernel: [    0.689475] pnp 00:03: [irq 8]
Jun 10 11:02:23 turk kernel: [    0.689496] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:02:23 turk kernel: [    0.689501] pnp 00:04: [io  0x0061]
Jun 10 11:02:23 turk kernel: [    0.689522] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:02:23 turk kernel: [    0.689527] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:02:23 turk kernel: [    0.689531] pnp 00:05: [irq 13]
Jun 10 11:02:23 turk kernel: [    0.689550] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:02:23 turk kernel: [    0.689997] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:02:23 turk kernel: [    0.690001] pnp 00:06: [irq 7]
Jun 10 11:02:23 turk kernel: [    0.690002] pnp 00:06: [dma 0 disabled]
Jun 10 11:02:23 turk kernel: [    0.690167] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:02:23 turk kernel: [    0.690194] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:02:23 turk kernel: [    0.690217] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:02:23 turk kernel: [    0.690540] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:02:23 turk kernel: [    0.690544] pnp 00:08: [irq 4]
Jun 10 11:02:23 turk kernel: [    0.690545] pnp 00:08: [dma 0 disabled]
Jun 10 11:02:23 turk kernel: [    0.690608] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:02:23 turk kernel: [    0.690654] pnp 00:09: [io  0x0060]
Jun 10 11:02:23 turk kernel: [    0.690655] pnp 00:09: [io  0x0064]
Jun 10 11:02:23 turk kernel: [    0.690658] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:02:23 turk kernel: [    0.690659] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:02:23 turk kernel: [    0.690696] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.690698] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690700] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.690791] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:02:23 turk kernel: [    0.690792] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:02:23 turk kernel: [    0.690793] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:02:23 turk kernel: [    0.690795] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:02:23 turk kernel: [    0.690796] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:02:23 turk kernel: [    0.690797] pnp 00:0a: [io  0x0080]
Jun 10 11:02:23 turk kernel: [    0.690798] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:02:23 turk kernel: [    0.690799] pnp 00:0a: [io  0x0088]
Jun 10 11:02:23 turk kernel: [    0.690801] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:02:23 turk kernel: [    0.690802] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:02:23 turk kernel: [    0.690803] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:02:23 turk kernel: [    0.690804] pnp 00:0a: [io  0x00b1]
Jun 10 11:02:23 turk kernel: [    0.690806] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:02:23 turk kernel: [    0.690807] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:02:23 turk kernel: [    0.690808] pnp 00:0a: [io  0x040b]
Jun 10 11:02:23 turk kernel: [    0.690809] pnp 00:0a: [io  0x04d6]
Jun 10 11:02:23 turk kernel: [    0.690811] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:02:23 turk kernel: [    0.690812] pnp 00:0a: [io  0x0c14]
Jun 10 11:02:23 turk kernel: [    0.690813] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:02:23 turk kernel: [    0.690814] pnp 00:0a: [io  0x0c52]
Jun 10 11:02:23 turk kernel: [    0.690815] pnp 00:0a: [io  0x0c6c]
Jun 10 11:02:23 turk kernel: [    0.690816] pnp 00:0a: [io  0x0c6f]
Jun 10 11:02:23 turk kernel: [    0.690818] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:02:23 turk kernel: [    0.690819] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:02:23 turk kernel: [    0.690820] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:02:23 turk kernel: [    0.690821] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:02:23 turk kernel: [    0.690823] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:02:23 turk kernel: [    0.690824] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:02:23 turk kernel: [    0.690825] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:02:23 turk kernel: [    0.690827] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.690828] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:02:23 turk kernel: [    0.690829] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:02:23 turk kernel: [    0.690831] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:02:23 turk kernel: [    0.690832] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:02:23 turk kernel: [    0.690833] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:02:23 turk kernel: [    0.690834] pnp 00:0a: [io  0x0060]
Jun 10 11:02:23 turk kernel: [    0.690836] pnp 00:0a: [io  0x0064]
Jun 10 11:02:23 turk kernel: [    0.690837] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:02:23 turk kernel: [    0.690838] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:02:23 turk kernel: [    0.690840] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:02:23 turk kernel: [    0.690841] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:02:23 turk kernel: [    0.690844] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.690919] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690921] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690923] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690925] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690926] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690928] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690930] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690931] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690933] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690935] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690936] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690938] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690940] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690942] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690944] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690945] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690949] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690950] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690952] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690954] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690956] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690958] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690960] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690962] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690964] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690966] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691063] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.691065] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:02:23 turk kernel: [    0.691066] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:02:23 turk kernel: [    0.691068] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:02:23 turk kernel: [    0.691069] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:02:23 turk kernel: [    0.691104] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691106] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691108] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691110] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691112] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691140] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:02:23 turk kernel: [    0.691175] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691177] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691244] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:02:23 turk kernel: [    0.691245] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:02:23 turk kernel: [    0.691247] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:02:23 turk kernel: [    0.691248] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:02:23 turk kernel: [    0.691250] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:02:23 turk kernel: [    0.691285] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691287] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691288] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691290] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691292] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691294] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:02:23 turk kernel: [    0.691359] pnp: PnP ACPI: found 14 devices
Jun 10 11:02:23 turk kernel: [    0.691361] ACPI: ACPI bus type pnp unregistered
Jun 10 11:02:23 turk kernel: [    0.697740] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:02:23 turk kernel: [    0.697759] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:02:23 turk kernel: [    0.697761] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.697763] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.697766] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697769] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:02:23 turk kernel: [    0.697770] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.697773] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.697776] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:02:23 turk kernel: [    0.697778] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.697780] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697783] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:02:23 turk kernel: [    0.697785] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.697788] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697791] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:02:23 turk kernel: [    0.697809] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    0.697812] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697818] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    0.697821] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697826] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    0.697828] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697831] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    0.697833] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697839] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.697840] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.697842] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.697844] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.697845] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.697847] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697848] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.697850] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.697852] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697854] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.697856] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.697857] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.697859] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697861] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.697863] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697865] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.697866] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.697868] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.697870] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.697872] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.697873] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697902] NET: Registered protocol family 2
Jun 10 11:02:23 turk kernel: [    0.698010] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:02:23 turk kernel: [    0.698908] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:02:23 turk kernel: [    0.701339] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:02:23 turk kernel: [    0.701646] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:02:23 turk kernel: [    0.701648] TCP reno registered
Jun 10 11:02:23 turk kernel: [    0.701655] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:02:23 turk kernel: [    0.701683] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:02:23 turk kernel: [    0.701769] NET: Registered protocol family 1
Jun 10 11:02:23 turk kernel: [    0.701798] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.508037] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.508048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.508089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.508095] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.588040] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.588050] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.588090] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.588104] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.668034] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:02:23 turk kernel: [    1.668043] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.748042] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.748052] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.748091] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.748110] pci 0000:01:00.0: Boot video device
Jun 10 11:02:23 turk kernel: [    1.748127] PCI: CLS 64 bytes, default 64
Jun 10 11:02:23 turk kernel: [    1.749389] PCI-DMA: Disabling AGP.
Jun 10 11:02:23 turk kernel: [    1.749461] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:02:23 turk kernel: [    1.749463] PCI-DMA: using GART IOMMU.
Jun 10 11:02:23 turk kernel: [    1.749465] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:02:23 turk kernel: [    1.752912] IBS: LVT offset 1 assigned
Jun 10 11:02:23 turk kernel: [    1.752928] perf: AMD IBS detected (0x0000001f)
Jun 10 11:02:23 turk kernel: [    1.753040] audit: initializing netlink socket (disabled)
Jun 10 11:02:23 turk kernel: [    1.753054] type=2000 audit(1339322523.748:1): initialized
Jun 10 11:02:23 turk kernel: [    1.777115] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:02:23 turk kernel: [    1.796097] VFS: Disk quotas dquot_6.5.2
Jun 10 11:02:23 turk kernel: [    1.796140] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:02:23 turk kernel: [    1.796561] fuse init (API version 7.17)
Jun 10 11:02:23 turk kernel: [    1.796626] msgmni has been set to 7901
Jun 10 11:02:23 turk kernel: [    1.796951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:02:23 turk kernel: [    1.796978] io scheduler noop registered
Jun 10 11:02:23 turk kernel: [    1.796979] io scheduler deadline registered
Jun 10 11:02:23 turk kernel: [    1.797000] io scheduler cfq registered (default)
Jun 10 11:02:23 turk kernel: [    1.797118] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797147] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797227] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797245] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797310] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797328] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797389] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797406] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797459] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:02:23 turk kernel: [    1.797475] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:02:23 turk kernel: [    1.797567] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:02:23 turk kernel: [    1.797571] ACPI: Power Button [PWRB]
Jun 10 11:02:23 turk kernel: [    1.797599] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:02:23 turk kernel: [    1.797601] ACPI: Power Button [PWRF]
Jun 10 11:02:23 turk kernel: [    1.981030] ERST: Table is not found!
Jun 10 11:02:23 turk kernel: [    1.981032] GHES: HEST is not enabled!
Jun 10 11:02:23 turk kernel: [    1.981117] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:02:23 turk kernel: [    2.001529] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:02:23 turk kernel: [    2.048779] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:02:23 turk kernel: [    2.096216] Linux agpgart interface v0.103
Jun 10 11:02:23 turk kernel: [    2.097260] brd: module loaded
Jun 10 11:02:23 turk kernel: [    2.097796] loop: module loaded
Jun 10 11:02:23 turk kernel: [    2.097935] ahci 0000:00:11.0: version 3.0
Jun 10 11:02:23 turk kernel: [    2.097943] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    2.097990] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    2.098059] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:02:23 turk kernel: [    2.098062] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:02:23 turk kernel: [    2.098464] scsi0 : ahci
Jun 10 11:02:23 turk kernel: [    2.098526] scsi1 : ahci
Jun 10 11:02:23 turk kernel: [    2.098576] scsi2 : ahci
Jun 10 11:02:23 turk kernel: [    2.098625] scsi3 : ahci
Jun 10 11:02:23 turk kernel: [    2.098690] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:02:23 turk kernel: [    2.098693] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:02:23 turk kernel: [    2.098695] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:02:23 turk kernel: [    2.098698] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:02:23 turk kernel: [    2.098824] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.098842] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.098908] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.098927] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.098937] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    2.099227] Fixed MDIO Bus: probed
Jun 10 11:02:23 turk kernel: [    2.099241] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:02:23 turk kernel: [    2.099242] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:02:23 turk kernel: [    2.099278] PPP generic driver version 2.4.2
Jun 10 11:02:23 turk kernel: [    2.099346] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:02:23 turk kernel: [    2.099385] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.099396] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.099432] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:02:23 turk kernel: [    2.099439] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.099452] QUIRK: Enable AMD PLL fix
Jun 10 11:02:23 turk kernel: [    2.099462] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.099478] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:02:23 turk kernel: [    2.108037] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.108135] hub 1-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.108138] hub 1-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.108243] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.108255] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.108287] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:02:23 turk kernel: [    2.108293] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.108309] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.108320] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:02:23 turk kernel: [    2.120042] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.120134] hub 2-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.120137] hub 2-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.120240] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.120251] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.120283] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:02:23 turk kernel: [    2.120289] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.120305] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.120316] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:02:23 turk kernel: [    2.132041] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.132131] hub 3-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.132134] hub 3-0:1.0: 4 ports detected
Jun 10 11:02:23 turk kernel: [    2.132197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:02:23 turk kernel: [    2.132249] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.132261] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.132293] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:02:23 turk kernel: [    2.132315] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:02:23 turk kernel: [    2.192104] hub 4-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.192109] hub 4-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.192214] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.192225] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.192263] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:02:23 turk kernel: [    2.192275] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:02:23 turk kernel: [    2.252101] hub 5-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.252106] hub 5-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.252209] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.252221] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.252253] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:02:23 turk kernel: [    2.252266] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:02:23 turk kernel: [    2.312123] hub 6-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.312128] hub 6-0:1.0: 2 ports detected
Jun 10 11:02:23 turk kernel: [    2.312231] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.312243] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.312275] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:02:23 turk kernel: [    2.312287] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:02:23 turk kernel: [    2.372134] hub 7-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.372140] hub 7-0:1.0: 4 ports detected
Jun 10 11:02:23 turk kernel: [    2.372201] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:02:23 turk kernel: [    2.372249] usbcore: registered new interface driver libusual
Jun 10 11:02:23 turk kernel: [    2.372273] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:02:23 turk kernel: [    2.372626] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:02:23 turk kernel: [    2.372632] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:02:23 turk kernel: [    2.372741] mousedev: PS/2 mouse device common for all mice
Jun 10 11:02:23 turk kernel: [    2.372854] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:02:23 turk kernel: [    2.372933] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:02:23 turk kernel: [    2.372956] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:02:23 turk kernel: [    2.373008] device-mapper: uevent: version 1.0.3
Jun 10 11:02:23 turk kernel: [    2.373055] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:02:23 turk kernel: [    2.373060] cpuidle: using governor ladder
Jun 10 11:02:23 turk kernel: [    2.373061] cpuidle: using governor menu
Jun 10 11:02:23 turk kernel: [    2.373062] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:02:23 turk kernel: [    2.373206] TCP cubic registered
Jun 10 11:02:23 turk kernel: [    2.373271] NET: Registered protocol family 10
Jun 10 11:02:23 turk kernel: [    2.373575] NET: Registered protocol family 17
Jun 10 11:02:23 turk kernel: [    2.373585] Registering the dns_resolver key type
Jun 10 11:02:23 turk kernel: [    2.373693] PM: Hibernation image not present or could not be loaded.
Jun 10 11:02:23 turk kernel: [    2.373700] registered taskstats version 1
Jun 10 11:02:23 turk kernel: [    2.387994]   Magic number: 0:770:21
Jun 10 11:02:23 turk kernel: [    2.388061] pcieport 0000:00:09.0: hash matches
Jun 10 11:02:23 turk kernel: [    2.388106] rtc_cmos 00:03: setting system clock to 2012-06-10 10:02:04 UTC (1339322524)
Jun 10 11:02:23 turk kernel: [    2.388120] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:02:23 turk kernel: [    2.388146] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:02:23 turk kernel: [    2.388148] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:02:23 turk kernel: [    2.388149] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:02:23 turk kernel: [    2.388150] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:02:23 turk kernel: [    2.388587] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:02:23 turk kernel: [    2.388589] EDD information not available.
Jun 10 11:02:23 turk kernel: [    2.416071] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.416102] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.588039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.588063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.589162] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:02:23 turk kernel: [    2.589164] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:02:23 turk kernel: [    2.589673] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:02:23 turk kernel: [    2.590428] ata1.00: configured for UDMA/133
Jun 10 11:02:23 turk kernel: [    2.590566] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:02:23 turk kernel: [    2.590694] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:02:23 turk kernel: [    2.590703] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:02:23 turk kernel: [    2.590799] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:02:23 turk kernel: [    2.590802] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:02:23 turk kernel: [    2.590836] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:02:23 turk kernel: [    2.591567] ata2.00: configured for UDMA/100
Jun 10 11:02:23 turk kernel: [    2.593395] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:02:23 turk kernel: [    2.595448] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:02:23 turk kernel: [    2.595451] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:02:23 turk kernel: [    2.595542] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:02:23 turk kernel: [    2.595608] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:02:23 turk kernel: [    2.651185]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:02:23 turk kernel: [    2.651669] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:02:23 turk kernel: [    2.652744] Freeing unused kernel memory: 920k freed
Jun 10 11:02:23 turk kernel: [    2.652907] Write protecting the kernel read-only data: 12288k
Jun 10 11:02:23 turk kernel: [    2.656850] Freeing unused kernel memory: 1608k freed
Jun 10 11:02:23 turk kernel: [    2.660021] Freeing unused kernel memory: 1196k freed
Jun 10 11:02:23 turk kernel: [    2.684061] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:02:23 turk kernel: [    2.691102] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:02:23 turk kernel: [    2.691120] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.691147] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.691186] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    2.691505] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc9000065e000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:02:23 turk kernel: [    2.691507] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:02:23 turk kernel: [    2.691659] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:02:23 turk kernel: [    2.691670] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.691714] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.692961] scsi4 : pata_via
Jun 10 11:02:23 turk kernel: [    2.693037] scsi5 : pata_via
Jun 10 11:02:23 turk kernel: [    2.693147] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:02:23 turk kernel: [    2.693149] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:02:23 turk kernel: [    2.706659] scsi6 : pata_atiixp
Jun 10 11:02:23 turk kernel: [    2.706769] scsi7 : pata_atiixp
Jun 10 11:02:23 turk kernel: [    2.707184] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:02:23 turk kernel: [    2.707186] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:02:23 turk kernel: [    2.752062] Refined TSC clocksource calibration: 3214.273 MHz.
Jun 10 11:02:23 turk kernel: [    2.752066] Switching to clocksource tsc
Jun 10 11:02:23 turk kernel: [    3.016708] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    3.016716] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    3.026205] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:02:23 turk kernel: [    3.026291] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:02:23 turk kernel: [    3.026302] usbcore: registered new interface driver usbhid
Jun 10 11:02:23 turk kernel: [    3.026303] usbhid: USB HID core driver
Jun 10 11:02:23 turk kernel: [    3.080083] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:02:23 turk kernel: [    3.116032] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:02:23 turk kernel: [    3.205360] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Jun 10 11:02:23 turk kernel: [    3.205363] EXT4-fs (sda7): write access will be enabled during recovery
Jun 10 11:02:23 turk kernel: [    3.298218] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:02:23 turk kernel: [    3.298288] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:02:23 turk kernel: [    3.317125] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:02:23 turk kernel: [    3.317188] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:02:23 turk kernel: [    3.339975] EXT4-fs (sda7): orphan cleanup on readonly fs
Jun 10 11:02:23 turk kernel: [    3.339980] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523389
Jun 10 11:02:23 turk kernel: [    3.339997] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523379
Jun 10 11:02:23 turk kernel: [    3.340016] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523376
Jun 10 11:02:23 turk kernel: [    3.340038] EXT4-fs (sda7): 3 orphan inodes deleted
Jun 10 11:02:23 turk kernel: [    3.340039] EXT4-fs (sda7): recovery complete
Jun 10 11:02:23 turk kernel: [    3.580080] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:02:23 turk kernel: [    3.617271] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:02:23 turk kernel: [   14.736309] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk kernel: [   14.777379] lp: driver loaded but no devices found
Jun 10 11:02:23 turk kernel: [   14.780178] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:02:23 turk kernel: [   14.780180] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:02:23 turk kernel: [   14.780548] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:02:23 turk kernel: [   14.780641] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:02:23 turk kernel: [   14.784784] wmi: Mapper loaded
Jun 10 11:02:23 turk kernel: [   14.796938] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:02:23 turk kernel: [   14.837746] MCE: In-kernel MCE decoding enabled.
Jun 10 11:02:23 turk kernel: [   14.839413] EDAC MC: Ver: 2.1.0
Jun 10 11:02:23 turk kernel: [   14.839904] AMD64 EDAC driver v3.4.0
Jun 10 11:02:23 turk kernel: [   14.841671] type=1400 audit(1339322536.950:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.842029] type=1400 audit(1339322536.950:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.842235] type=1400 audit(1339322536.950:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.843336] EDAC amd64: DRAM ECC disabled.
Jun 10 11:02:23 turk kernel: [   14.843343] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:02:23 turk kernel: [   14.843344]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:02:23 turk kernel: [   14.843345]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:02:23 turk kernel: [   14.853757] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:02:23 turk kernel: [   14.853807] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:02:23 turk kernel: [   14.882598] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:02:23 turk kernel: [   14.912916] ppdev: user-space parallel port driver
Jun 10 11:02:23 turk kernel: [   14.927819] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:02:23 turk kernel: [   14.927932] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:02:23 turk kernel: [   14.927984] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:02:23 turk kernel: [   14.928037] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:02:23 turk kernel: [   14.928144] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:02:23 turk kernel: [   14.928188] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:02:23 turk kernel: [   14.928230] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:02:23 turk kernel: [   14.928278] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:02:23 turk kernel: [   14.928498] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [   14.928501] hda_intel: Disabling MSI
Jun 10 11:02:23 turk kernel: [   14.928531] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [   14.948165] lp0: using parport0 (interrupt-driven).
Jun 10 11:02:23 turk kernel: [   15.612793] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:02:23 turk kernel: [   15.612796] Disabling lock debugging due to kernel taint
Jun 10 11:02:23 turk kernel: [   15.764026] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.788030] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.812030] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.836032] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.836103] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:02:23 turk kernel: [   15.836166] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:02:23 turk kernel: [   15.836213] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:02:23 turk kernel: [   15.836259] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:02:23 turk kernel: [   15.836727] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [   15.836734] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [   15.836737] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:02:23 turk kernel: [   15.836963] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:02:23 turk kernel: [   15.947302] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:02:23 turk kernel: [   15.947304] vesafb: scrolling: redraw
Jun 10 11:02:23 turk kernel: [   15.947306] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:02:23 turk kernel: [   15.951566] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:02:23 turk kernel: [   15.951734] Console: switching to colour frame buffer device 80x30
Jun 10 11:02:23 turk kernel: [   15.951745] fb0: VESA VGA frame buffer device
Jun 10 11:02:23 turk kernel: [   16.817792] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:02:23 turk kernel: [   18.470683] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:02:23 turk kernel: [   20.797569] init: failsafe main process (971) killed by TERM signal
Jun 10 11:02:23 turk kernel: [   21.049050] Bluetooth: Core ver 2.16
Jun 10 11:02:23 turk kernel: [   21.049069] NET: Registered protocol family 31
Jun 10 11:02:23 turk kernel: [   21.049071] Bluetooth: HCI device and connection manager initialized
Jun 10 11:02:23 turk kernel: [   21.049073] Bluetooth: HCI socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.049074] Bluetooth: L2CAP socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.049078] Bluetooth: SCO socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.050846] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:02:23 turk kernel: [   21.050848] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:02:23 turk kernel: [   21.062695] type=1400 audit(1339322543.170:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.063205] type=1400 audit(1339322543.170:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.066853] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:02:23 turk kernel: [   21.066857] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.066859] Bluetooth: RFCOMM ver 1.11
Jun 10 11:02:23 turk kernel: [   21.073963] type=1400 audit(1339322543.182:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1078 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074048] type=1400 audit(1339322543.182:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074416] type=1400 audit(1339322543.182:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074609] type=1400 audit(1339322543.182:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076227] type=1400 audit(1339322543.186:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1082 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076646] type=1400 audit(1339322543.186:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1082 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076900] type=1400 audit(1339322543.186:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1083 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.077332] type=1400 audit(1339322543.186:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1083 comm="apparmor_parser"
Jun 10 11:02:23 turk NetworkManager[1032]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:02:23 turk NetworkManager[1032]: <info> modem-manager is now available
Jun 10 11:02:23 turk NetworkManager[1032]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Networking is enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): carrier is OFF
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): now managed
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): bringing up device.
Jun 10 11:02:23 turk cron[1146]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:02:23 turk anacron[1170]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:23 turk acpid: starting up with proc fs
Jun 10 11:02:23 turk acpid: 35 rules loaded
Jun 10 11:02:23 turk acpid: waiting for events: event logging is off
Jun 10 11:02:23 turk cron[1173]: (CRON) STARTUP (fork ok)
Jun 10 11:02:23 turk cron[1173]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:02:23 turk kernel: [   21.276401] vboxdrv: Found 4 processor cores.
Jun 10 11:02:23 turk kernel: [   21.276842] vboxdrv: fAsync=0 offMin=0x50e offMax=0x1522
Jun 10 11:02:23 turk kernel: [   21.276891] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:02:23 turk kernel: [   21.276893] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:02:23 turk kernel: [   21.283467] vboxpci: IOMMU not found (not registered)
Jun 10 11:02:23 turk kernel: [   21.295509] r8169 0000:04:00.0: eth0: link down
Jun 10 11:02:23 turk kernel: [   21.295522] r8169 0000:04:00.0: eth0: link down
Jun 10 11:02:23 turk kernel: [   21.295855] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): preparing device.
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:02:23 turk anacron[1170]: Normal exit (0 jobs run)
Jun 10 11:02:23 turk kernel: [   21.296185] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk acpid: client connected from 1268[0:0]
Jun 10 11:02:23 turk acpid: 1 client rule loaded
Jun 10 11:02:23 turk anacron[1306]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:23 turk anacron[1306]: Normal exit (0 jobs run)
Jun 10 11:02:23 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:02:23 turk udev-configure-printer: Failed to get parent
Jun 10 11:02:23 turk udev-configure-printer: add /module/lp
Jun 10 11:02:23 turk udev-configure-printer: Failed to get parent
Jun 10 11:02:25 turk acpid: client connected from 1268[0:0]
Jun 10 11:02:25 turk acpid: 1 client rule loaded
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:02:25 turk kernel: [   22.986340] r8169 0000:04:00.0: eth0: link up
Jun 10 11:02:25 turk kernel: [   22.986645] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:02:25 turk NetworkManager[1032]: <info> dhclient started with pid 1435
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:02:25 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:02:25 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:02:25 turk dhclient: All rights reserved.
Jun 10 11:02:25 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:02:25 turk dhclient: 
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:02:25 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:02:25 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:02:25 turk dhclient: Sending on   Socket/fallback
Jun 10 11:02:25 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:02:25 turk accounts-daemon[1444]: started daemon version 0.6.15
Jun 10 11:02:25 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:02:25 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:02:25 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:02:25 turk dhclient: bound to 192.168.1.103 -- renewal in 42518 seconds.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   address 192.168.1.103
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   gateway 192.168.1.1
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   nameserver '194.168.4.100'
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   nameserver '194.168.8.100'
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:02:25 turk anacron[1654]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:25 turk anacron[1654]: Normal exit (0 jobs run)
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully called chroot.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully dropped privileges.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully limited resources.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Watchdog thread running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Canary thread running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully made thread 1779 of process 1779 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> DNS: starting dnsmasq...
Jun 10 11:02:26 turk NetworkManager[1032]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:02:26 turk dnsmasq[1787]: started, version 2.59 cache disabled
Jun 10 11:02:26 turk dnsmasq[1787]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:02:26 turk dnsmasq[1787]: using nameserver 194.168.8.100#53
Jun 10 11:02:26 turk dnsmasq[1787]: using nameserver 194.168.4.100#53
Jun 10 11:02:26 turk NetworkManager[1032]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Activation (eth0) successful, device activated.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully made thread 1866 of process 1779 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:02:27 turk rtkit-daemon[1781]: Successfully made thread 1867 of process 1779 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:02:27 turk rtkit-daemon[1781]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:02:28 turk dbus[990]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:02:28 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:02:35 turk ntpdate[1847]: step time server 91.189.94.4 offset 0.653363 sec
Jun 10 11:02:36 turk kernel: [   33.256017] eth0: no IPv6 routers present
Jun 10 11:02:43 turk goa[2148]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:02:45 turk NetworkManager[1032]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:03:01 turk kernel: [   58.235358] do_general_protection: 27 callbacks suppressed
Jun 10 11:03:01 turk kernel: [   58.235361] ubuntuone-login[2211] general protection ip:577e28 sp:7fff53d75bf0 error:0 in python2.7[400000+272000]
Jun 10 11:03:29 turk dbus[990]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun 10 11:03:29 turk kernel: [   87.221333] apt-check[2239]: segfault at 8a65c0 ip 00000000008a65c0 sp 00007fff2ce66478 error 15 in python2.7[872000+69000]
Jun 10 11:03:30 turk AptDaemon: INFO: Initializing daemon
Jun 10 11:03:30 turk AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 10 11:03:30 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 10 11:03:30 turk AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 10 11:03:30 turk AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:03:30 turk AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:03:34 turk AptDaemon.PackageKit: INFO: Get updates()
Jun 10 11:03:34 turk AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:14:59 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:14:59 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="996" x-info="http://www.rsyslog.com"] start
Jun 10 11:14:59 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:14:59 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:14:59 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:14:59 turk polkitd[1016]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:14:59 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: init!
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:14:59 turk NetworkManager[984]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:14:59 turk NetworkManager[984]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:14:59 turk NetworkManager[984]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:14:59 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:14:59 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:14:59 turk NetworkManager[984]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:14:59 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:14:59 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:14:59 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:14:59 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:14:59 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:14:59 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:14:59 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:14:59 turk kernel: [    0.000000] DMI present.
Jun 10 11:14:59 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:14:59 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:14:59 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:14:59 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:14:59 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:14:59 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   3 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   4 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   5 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   6 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   7 disabled
Jun 10 11:14:59 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:14:59 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:14:59 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:14:59 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:14:59 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: (19754800) ... get_connections.
Jun 10 11:14:59 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: (19754800) ... get_connections (managed=false): return empty list.
Jun 10 11:14:59 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:14:59 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:14:59 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:14:59 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:14:59 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:14:59 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:14:59 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:14:59 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:14:59 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:14:59 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:14:59 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:14:59 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:14:59 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:14:59 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:14:59 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:14:59 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:14:59 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:14:59 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:14:59 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:14:59 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:14:59 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:14:59 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:14:59 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:14:59 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:14:59 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:14:59 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:14:59 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:14:59 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:14:59 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:14:59 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:14:59 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:14:59 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:14:59 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:14:59 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:14:59 turk kernel: [    0.000000] Node 0: aperture @ c4000000 size 32 MB
Jun 10 11:14:59 turk kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Jun 10 11:14:59 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:14:59 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:14:59 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:14:59 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:14:59 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:14:59 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:14:59 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:14:59 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:14:59 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:14:59 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:14:59 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:14:59 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:14:59 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:14:59 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:14:59 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:14:59 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:14:59 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:14:59 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:14:59 turk kernel: [    0.000000] Detected 3214.213 MHz processor.
Jun 10 11:14:59 turk kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.42 BogoMIPS (lpj=12856852)
Jun 10 11:14:59 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:14:59 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:14:59 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:14:59 turk kernel: [    0.004039] Yama: becoming mindful.
Jun 10 11:14:59 turk kernel: [    0.004344] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:14:59 turk kernel: [    0.008811] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:14:59 turk kernel: [    0.009422] Mount-cache hash table entries: 256
Jun 10 11:14:59 turk kernel: [    0.009525] Initializing cgroup subsys cpuacct
Jun 10 11:14:59 turk kernel: [    0.009529] Initializing cgroup subsys memory
Jun 10 11:14:59 turk kernel: [    0.009536] Initializing cgroup subsys devices
Jun 10 11:14:59 turk kernel: [    0.009538] Initializing cgroup subsys freezer
Jun 10 11:14:59 turk kernel: [    0.009539] Initializing cgroup subsys blkio
Jun 10 11:14:59 turk kernel: [    0.009545] Initializing cgroup subsys perf_event
Jun 10 11:14:59 turk kernel: [    0.009568] tseg: 0000000000
Jun 10 11:14:59 turk kernel: [    0.009578] CPU: Physical Processor ID: 0
Jun 10 11:14:59 turk kernel: [    0.009579] CPU: Processor Core ID: 0
Jun 10 11:14:59 turk kernel: [    0.009581] mce: CPU supports 6 MCE banks
Jun 10 11:14:59 turk kernel: [    0.010738] ACPI: Core revision 20110623
Jun 10 11:14:59 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:14:59 turk kernel: [    0.020381] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:14:59 turk kernel: [    0.063135] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:14:59 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:14:59 turk kernel: [    0.064003] ... version:                0
Jun 10 11:14:59 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:14:59 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:14:59 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:14:59 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:14:59 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:14:59 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:14:59 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:14:59 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.152081]  #2
Jun 10 11:14:59 turk kernel: [    0.152082] smpboot cpu 2: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.244079]  #3
Jun 10 11:14:59 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.336047] Brought up 4 CPUs
Jun 10 11:14:59 turk kernel: [    0.336049] Total of 4 processors activated (25714.23 BogoMIPS).
Jun 10 11:14:59 turk kernel: [    0.340158] devtmpfs: initialized
Jun 10 11:14:59 turk kernel: [    0.341187] EVM: security.selinux
Jun 10 11:14:59 turk kernel: [    0.341188] EVM: security.SMACK64
Jun 10 11:14:59 turk kernel: [    0.341189] EVM: security.capability
Jun 10 11:14:59 turk kernel: [    0.341285] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:14:59 turk kernel: [    0.341285] print_constraints: dummy: 
Jun 10 11:14:59 turk kernel: [    0.341285] RTC time: 10:14:36, date: 06/10/12
Jun 10 11:14:59 turk kernel: [    0.341285] NET: Registered protocol family 16
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: io port [1000, ffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] TOM: 00000000d0000000 aka 3328M
Jun 10 11:14:59 turk kernel: [    0.341285] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:14:59 turk kernel: [    0.341285] TOM2: 0000000130000000 aka 4864M
Jun 10 11:14:59 turk kernel: [    0.341285] bus: [00, 07] on node 0 link 0
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] Extended Config Space enabled on 1 nodes
Jun 10 11:14:59 turk kernel: [    0.341285] ACPI: bus type pci registered
Jun 10 11:14:59 turk kernel: [    0.341285] Trying to unpack rootfs image as initramfs...
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: not using MMCONFIG
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: Using configuration type 1 for base access
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: Using configuration type 1 for extended access
Jun 10 11:14:59 turk kernel: [    0.341457] bio: create slab <bio-0> at 0
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Module Device)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Processor Device)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:14:59 turk kernel: [    0.344427] ACPI: EC: Look up EC in DSDT
Jun 10 11:14:59 turk kernel: [    0.380092] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:14:59 turk kernel: [    0.548579] ACPI: Interpreter enabled
Jun 10 11:14:59 turk kernel: [    0.548584] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:14:59 turk kernel: [    0.548601] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:14:59 turk kernel: [    0.548619] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:14:59 turk kernel: [    0.549990] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:14:59 turk kernel: [    0.557708] Freeing initrd memory: 13844k freed
Jun 10 11:14:59 turk kernel: [    0.642049] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:14:59 turk kernel: [    0.642147] ACPI: No dock devices found.
Jun 10 11:14:59 turk kernel: [    0.642148] HEST: Table not found.
Jun 10 11:14:59 turk kernel: [    0.642151] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:14:59 turk kernel: [    0.642207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:14:59 turk kernel: [    0.642322] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.642324] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:14:59 turk kernel: [    0.642326] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.642328] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.642329] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.642331] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.642343] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.642385] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642414] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642417] pci 0000:00:02.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642431] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642459] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk NetworkManager[984]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:14:59 turk kernel: [    0.642461] pci 0000:00:07.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642473] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642500] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642502] pci 0000:00:09.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642513] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642541] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642543] pci 0000:00:0a.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642567] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.642585] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:14:59 turk kernel: [    0.642593] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:14:59 turk kernel: [    0.642601] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:14:59 turk kernel: [    0.642610] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:14:59 turk kernel: [    0.642618] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:14:59 turk kernel: [    0.642626] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:14:59 turk kernel: [    0.642644] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:14:59 turk kernel: [    0.642695] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642706] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:14:59 turk kernel: [    0.642767] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642783] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:14:59 turk kernel: [    0.642854] pci 0000:00:12.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.642855] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.642859] pci 0000:00:12.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642876] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642887] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:14:59 turk kernel: [    0.642948] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642964] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:14:59 turk kernel: [    0.643035] pci 0000:00:13.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.643036] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.643039] pci 0000:00:13.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643056] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:14:59 turk NetworkManager[984]: <info> modem-manager is now available
Jun 10 11:14:59 turk kernel: [    0.643122] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.643136] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:14:59 turk kernel: [    0.643144] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:14:59 turk kernel: [    0.643152] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:14:59 turk kernel: [    0.643160] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:14:59 turk kernel: [    0.643169] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:14:59 turk kernel: [    0.643219] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:14:59 turk kernel: [    0.643237] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:14:59 turk kernel: [    0.643293] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.643297] pci 0000:00:14.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643307] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:14:59 turk kernel: [    0.643373] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.643408] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643420] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:14:59 turk kernel: [    0.643477] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643489] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:14:59 turk kernel: [    0.643549] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643566] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:14:59 turk kernel: [    0.643636] pci 0000:00:16.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.643638] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.643641] pci 0000:00:16.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643657] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643669] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643679] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643689] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643703] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643745] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:14:59 turk kernel: [    0.643754] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:14:59 turk kernel: [    0.643764] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.643773] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.643780] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:14:59 turk kernel: [    0.643786] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:14:59 turk kernel: [    0.643836] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:14:59 turk kernel: [    0.643845] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:14:59 turk kernel: [    0.648059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:14:59 turk kernel: [    0.648063] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.648066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.648069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.648114] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:14:59 turk kernel: [    0.648143] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:14:59 turk kernel: [    0.648158] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:14:59 turk kernel: [    0.648284] pci 0000:02:00.0: supports D2
Jun 10 11:14:59 turk kernel: [    0.648285] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.648291] pci 0000:02:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.656063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:14:59 turk kernel: [    0.656067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.656069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.656119] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.656141] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:14:59 turk kernel: [    0.656156] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:14:59 turk kernel: [    0.656170] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:14:59 turk kernel: [    0.656185] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:14:59 turk kernel: [    0.656199] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:14:59 turk kernel: [    0.656227] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:14:59 turk kernel: [    0.656302] pci 0000:03:00.0: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.656303] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.656308] pci 0000:03:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.664061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:14:59 turk kernel: [    0.664065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.664068] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.664103] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:14:59 turk kernel: [    0.664114] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:14:59 turk kernel: [    0.664133] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.664146] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.664197] pci 0000:04:00.0: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.664199] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.664202] pci 0000:04:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.672059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:14:59 turk kernel: [    0.672063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.672066] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.672120] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672128] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672130] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672134] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672136] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672137] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672139] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:14:59 turk kernel: [    0.672252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:14:59 turk kernel: [    0.672273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:14:59 turk kernel: [    0.672290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:14:59 turk kernel: [    0.672308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:14:59 turk kernel: [    0.672328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:14:59 turk kernel: [    0.672363]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:14:59 turk kernel: [    0.672365]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:14:59 turk kernel: [    0.672367] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:14:59 turk kernel: [    0.675423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675467] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675510] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675552] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675584] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675610] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675635] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675660] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: loaded
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:14:59 turk kernel: [    0.675734] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:14:59 turk kernel: [    0.675734] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:14:59 turk kernel: [    0.675734] SCSI subsystem initialized
Jun 10 11:14:59 turk kernel: [    0.675734] libata version 3.00 loaded.
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new interface driver usbfs
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new interface driver hub
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new device driver usb
Jun 10 11:14:59 turk kernel: [    0.676068] PCI: Using ACPI for IRQ routing
Jun 10 11:14:59 turk kernel: [    0.683419] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:14:59 turk kernel: [    0.683486] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:14:59 turk kernel: [    0.683488] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:14:59 turk kernel: [    0.683557] NetLabel: Initializing
Jun 10 11:14:59 turk kernel: [    0.683558] NetLabel:  domain hash size = 128
Jun 10 11:14:59 turk kernel: [    0.683559] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:14:59 turk kernel: [    0.683567] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:14:59 turk kernel: [    0.683594] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:14:59 turk kernel: [    0.683594] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:14:59 turk kernel: [    0.685065] Switching to clocksource hpet
Jun 10 11:14:59 turk kernel: [    0.688698] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:14:59 turk kernel: [    0.688714] pnp: PnP ACPI init
Jun 10 11:14:59 turk kernel: [    0.688724] ACPI: bus type pnp registered
Jun 10 11:14:59 turk kernel: [    0.688799] pnp 00:00: [bus 00-ff]
Jun 10 11:14:59 turk kernel: [    0.688801] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:14:59 turk kernel: [    0.688803] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:14:59 turk kernel: [    0.688804] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:14:59 turk kernel: [    0.688806] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:14:59 turk kernel: [    0.688807] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:14:59 turk kernel: [    0.688809] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:14:59 turk kernel: [    0.688810] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:14:59 turk kernel: [    0.688846] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:14:59 turk kernel: [    0.688899] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.688901] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.688934] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.689423] pnp 00:02: [dma 4]
Jun 10 11:14:59 turk kernel: [    0.689425] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:14:59 turk kernel: [    0.689426] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:14:59 turk kernel: [    0.689428] pnp 00:02: [io  0x0087]
Jun 10 11:14:59 turk kernel: [    0.689429] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:14:59 turk kernel: [    0.689430] pnp 00:02: [io  0x008f]
Jun 10 11:14:59 turk kernel: [    0.689431] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:14:59 turk kernel: [    0.689452] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:14:59 turk kernel: [    0.689458] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:14:59 turk kernel: [    0.689466] pnp 00:03: [irq 8]
Jun 10 11:14:59 turk kernel: [    0.689487] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:14:59 turk kernel: [    0.689492] pnp 00:04: [io  0x0061]
Jun 10 11:14:59 turk kernel: [    0.689512] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:14:59 turk kernel: [    0.689518] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:14:59 turk kernel: [    0.689521] pnp 00:05: [irq 13]
Jun 10 11:14:59 turk kernel: [    0.689540] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:14:59 turk kernel: [    0.689987] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:14:59 turk kernel: [    0.689991] pnp 00:06: [irq 7]
Jun 10 11:14:59 turk kernel: [    0.689992] pnp 00:06: [dma 0 disabled]
Jun 10 11:14:59 turk kernel: [    0.690157] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:14:59 turk kernel: [    0.690182] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:14:59 turk kernel: [    0.690204] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:14:59 turk kernel: [    0.690527] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:14:59 turk kernel: [    0.690530] pnp 00:08: [irq 4]
Jun 10 11:14:59 turk kernel: [    0.690532] pnp 00:08: [dma 0 disabled]
Jun 10 11:14:59 turk kernel: [    0.690594] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:14:59 turk kernel: [    0.690640] pnp 00:09: [io  0x0060]
Jun 10 11:14:59 turk kernel: [    0.690641] pnp 00:09: [io  0x0064]
Jun 10 11:14:59 turk kernel: [    0.690644] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:14:59 turk kernel: [    0.690646] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:14:59 turk kernel: [    0.690682] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.690684] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690686] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.690777] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:14:59 turk kernel: [    0.690778] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:14:59 turk kernel: [    0.690779] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:14:59 turk kernel: [    0.690780] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:14:59 turk kernel: [    0.690782] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:14:59 turk kernel: [    0.690783] pnp 00:0a: [io  0x0080]
Jun 10 11:14:59 turk kernel: [    0.690784] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:14:59 turk kernel: [    0.690785] pnp 00:0a: [io  0x0088]
Jun 10 11:14:59 turk kernel: [    0.690787] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:14:59 turk kernel: [    0.690788] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:14:59 turk kernel: [    0.690789] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:14:59 turk kernel: [    0.690790] pnp 00:0a: [io  0x00b1]
Jun 10 11:14:59 turk kernel: [    0.690792] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:14:59 turk kernel: [    0.690793] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:14:59 turk kernel: [    0.690794] pnp 00:0a: [io  0x040b]
Jun 10 11:14:59 turk kernel: [    0.690795] pnp 00:0a: [io  0x04d6]
Jun 10 11:14:59 turk kernel: [    0.690796] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:14:59 turk kernel: [    0.690798] pnp 00:0a: [io  0x0c14]
Jun 10 11:14:59 turk kernel: [    0.690799] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:14:59 turk kernel: [    0.690800] pnp 00:0a: [io  0x0c52]
Jun 10 11:14:59 turk kernel: [    0.690801] pnp 00:0a: [io  0x0c6c]
Jun 10 11:14:59 turk kernel: [    0.690802] pnp 00:0a: [io  0x0c6f]
Jun 10 11:14:59 turk kernel: [    0.690803] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:14:59 turk kernel: [    0.690805] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:14:59 turk kernel: [    0.690806] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:14:59 turk kernel: [    0.690807] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:14:59 turk kernel: [    0.690808] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:14:59 turk kernel: [    0.690810] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:14:59 turk kernel: [    0.690811] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:14:59 turk kernel: [    0.690812] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.690814] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:14:59 turk kernel: [    0.690815] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:14:59 turk kernel: [    0.690816] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:14:59 turk kernel: [    0.690818] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:14:59 turk kernel: [    0.690819] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:14:59 turk kernel: [    0.690820] pnp 00:0a: [io  0x0060]
Jun 10 11:14:59 turk kernel: [    0.690821] pnp 00:0a: [io  0x0064]
Jun 10 11:14:59 turk kernel: [    0.690823] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:14:59 turk kernel: [    0.690824] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:14:59 turk kernel: [    0.690825] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:14:59 turk kernel: [    0.690827] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:14:59 turk kernel: [    0.690830] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.690905] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690907] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690909] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690910] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690912] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690914] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690915] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690917] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690919] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690920] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690922] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690924] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690926] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690928] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690929] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690931] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690934] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690936] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690938] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690940] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690942] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690944] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690946] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690948] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690950] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690952] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691049] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.691051] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:14:59 turk kernel: [    0.691052] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:14:59 turk kernel: [    0.691054] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:14:59 turk kernel: [    0.691055] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:14:59 turk kernel: [    0.691090] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691092] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691094] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691096] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691098] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691126] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:14:59 turk kernel: [    0.691160] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691162] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691229] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:14:59 turk kernel: [    0.691230] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:14:59 turk kernel: [    0.691232] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:14:59 turk kernel: [    0.691233] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:14:59 turk kernel: [    0.691235] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:14:59 turk kernel: [    0.691270] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691272] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691274] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691276] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691278] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691280] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:14:59 turk kernel: [    0.691344] pnp: PnP ACPI: found 14 devices
Jun 10 11:14:59 turk kernel: [    0.691346] ACPI: ACPI bus type pnp unregistered
Jun 10 11:14:59 turk kernel: [    0.697722] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:14:59 turk kernel: [    0.697741] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:14:59 turk kernel: [    0.697743] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.697745] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.697747] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697750] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:14:59 turk kernel: [    0.697752] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.697754] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.697758] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:14:59 turk kernel: [    0.697759] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.697762] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697765] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:14:59 turk kernel: [    0.697767] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.697770] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697773] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:14:59 turk kernel: [    0.697791] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    0.697794] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697800] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    0.697803] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697808] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    0.697810] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697813] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    0.697815] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697821] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.697822] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:14:59 turk kernel: [    0.697824] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.697825] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.697827] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.697829] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697830] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.697832] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.697834] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697836] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.697837] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.697839] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.697841] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697843] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.697845] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697846] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.697848] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:14:59 turk NetworkManager[984]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:14:59 turk kernel: [    0.697850] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.697852] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.697853] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.697855] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697883] NET: Registered protocol family 2
Jun 10 11:14:59 turk kernel: [    0.697990] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:14:59 turk kernel: [    0.698869] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:14:59 turk kernel: [    0.701302] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:14:59 turk kernel: [    0.701606] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:14:59 turk kernel: [    0.701608] TCP reno registered
Jun 10 11:14:59 turk kernel: [    0.701615] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:14:59 turk kernel: [    0.701643] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:14:59 turk kernel: [    0.701730] NET: Registered protocol family 1
Jun 10 11:14:59 turk kernel: [    0.701759] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.520037] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.520048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.520089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.520095] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.600038] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.600049] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.600089] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.600102] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.680033] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:14:59 turk kernel: [    1.680042] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.760040] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.760050] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.760090] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.760109] pci 0000:01:00.0: Boot video device
Jun 10 11:14:59 turk kernel: [    1.760125] PCI: CLS 64 bytes, default 64
Jun 10 11:14:59 turk kernel: [    1.761382] PCI-DMA: Disabling AGP.
Jun 10 11:14:59 turk kernel: [    1.761455] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:14:59 turk kernel: [    1.761456] PCI-DMA: using GART IOMMU.
Jun 10 11:14:59 turk kernel: [    1.761458] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:14:59 turk kernel: [    1.764901] IBS: LVT offset 1 assigned
Jun 10 11:14:59 turk kernel: [    1.764918] perf: AMD IBS detected (0x0000001f)
Jun 10 11:14:59 turk kernel: [    1.765030] audit: initializing netlink socket (disabled)
Jun 10 11:14:59 turk kernel: [    1.765044] type=2000 audit(1339323277.760:1): initialized
Jun 10 11:14:59 turk kernel: [    1.789108] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:14:59 turk kernel: [    1.808128] VFS: Disk quotas dquot_6.5.2
Jun 10 11:14:59 turk kernel: [    1.808170] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:14:59 turk kernel: [    1.808592] fuse init (API version 7.17)
Jun 10 11:14:59 turk kernel: [    1.808657] msgmni has been set to 7901
Jun 10 11:14:59 turk kernel: [    1.808983] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:14:59 turk kernel: [    1.809010] io scheduler noop registered
Jun 10 11:14:59 turk kernel: [    1.809011] io scheduler deadline registered
Jun 10 11:14:59 turk kernel: [    1.809032] io scheduler cfq registered (default)
Jun 10 11:14:59 turk kernel: [    1.809153] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809182] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809261] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809279] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809345] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809363] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809423] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809441] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809493] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:14:59 turk kernel: [    1.809510] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:14:59 turk kernel: [    1.809602] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:14:59 turk kernel: [    1.809606] ACPI: Power Button [PWRB]
Jun 10 11:14:59 turk kernel: [    1.809634] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:14:59 turk kernel: [    1.809636] ACPI: Power Button [PWRF]
Jun 10 11:14:59 turk kernel: [    1.993031] ERST: Table is not found!
Jun 10 11:14:59 turk kernel: [    1.993033] GHES: HEST is not enabled!
Jun 10 11:14:59 turk kernel: [    1.993117] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:14:59 turk kernel: [    2.013530] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:14:59 turk kernel: [    2.060779] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:14:59 turk kernel: [    2.104211] Linux agpgart interface v0.103
Jun 10 11:14:59 turk kernel: [    2.105254] brd: module loaded
Jun 10 11:14:59 turk kernel: [    2.105789] loop: module loaded
Jun 10 11:14:59 turk kernel: [    2.105926] ahci 0000:00:11.0: version 3.0
Jun 10 11:14:59 turk kernel: [    2.105935] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    2.105982] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    2.106051] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:14:59 turk kernel: [    2.106054] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:14:59 turk kernel: [    2.106458] scsi0 : ahci
Jun 10 11:14:59 turk kernel: [    2.106521] scsi1 : ahci
Jun 10 11:14:59 turk kernel: [    2.106570] scsi2 : ahci
Jun 10 11:14:59 turk kernel: [    2.106619] scsi3 : ahci
Jun 10 11:14:59 turk kernel: [    2.106685] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:14:59 turk kernel: [    2.106687] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:14:59 turk kernel: [    2.106690] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:14:59 turk kernel: [    2.106692] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:14:59 turk kernel: [    2.106820] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.106837] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.106907] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.106926] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.106935] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    2.107227] Fixed MDIO Bus: probed
Jun 10 11:14:59 turk kernel: [    2.107241] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:14:59 turk kernel: [    2.107242] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:14:59 turk kernel: [    2.107279] PPP generic driver version 2.4.2
Jun 10 11:14:59 turk kernel: [    2.107346] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:14:59 turk kernel: [    2.107385] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.107395] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.107430] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:14:59 turk kernel: [    2.107437] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.107450] QUIRK: Enable AMD PLL fix
Jun 10 11:14:59 turk kernel: [    2.107460] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.107476] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:14:59 turk kernel: [    2.116041] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.116140] hub 1-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.116143] hub 1-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.116248] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.116260] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.116292] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:14:59 turk kernel: [    2.116298] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.116314] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.116325] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:14:59 turk kernel: [    2.128034] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.128126] hub 2-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.128129] hub 2-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.128244] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.128255] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.128288] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:14:59 turk kernel: [    2.128294] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.128310] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.128320] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:14:59 turk kernel: [    2.140033] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.140124] hub 3-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.140127] hub 3-0:1.0: 4 ports detected
Jun 10 11:14:59 turk kernel: [    2.140199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:14:59 turk kernel: [    2.140255] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.140267] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.140299] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:14:59 turk kernel: [    2.140321] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:14:59 turk kernel: [    2.200100] hub 4-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.200106] hub 4-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.200210] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.200223] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.200261] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:14:59 turk kernel: [    2.200273] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:14:59 turk kernel: [    2.260095] hub 5-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.260101] hub 5-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.260203] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.260215] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.260246] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:14:59 turk kernel: [    2.260259] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:14:59 turk kernel: [    2.320116] hub 6-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.320121] hub 6-0:1.0: 2 ports detected
Jun 10 11:14:59 turk kernel: [    2.320224] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.320236] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.320268] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:14:59 turk kernel: [    2.320281] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:14:59 turk kernel: [    2.380117] hub 7-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.380122] hub 7-0:1.0: 4 ports detected
Jun 10 11:14:59 turk kernel: [    2.380184] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:14:59 turk kernel: [    2.380232] usbcore: registered new interface driver libusual
Jun 10 11:14:59 turk kernel: [    2.380256] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:14:59 turk kernel: [    2.380611] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:14:59 turk kernel: [    2.380616] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:14:59 turk kernel: [    2.380723] mousedev: PS/2 mouse device common for all mice
Jun 10 11:14:59 turk kernel: [    2.380836] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:14:59 turk kernel: [    2.380915] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:14:59 turk kernel: [    2.380937] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:14:59 turk kernel: [    2.380989] device-mapper: uevent: version 1.0.3
Jun 10 11:14:59 turk kernel: [    2.381037] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:14:59 turk kernel: [    2.381042] cpuidle: using governor ladder
Jun 10 11:14:59 turk kernel: [    2.381043] cpuidle: using governor menu
Jun 10 11:14:59 turk kernel: [    2.381045] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:14:59 turk kernel: [    2.381188] TCP cubic registered
Jun 10 11:14:59 turk kernel: [    2.381253] NET: Registered protocol family 10
Jun 10 11:14:59 turk kernel: [    2.381558] NET: Registered protocol family 17
Jun 10 11:14:59 turk kernel: [    2.381568] Registering the dns_resolver key type
Jun 10 11:14:59 turk kernel: [    2.381679] PM: Hibernation image not present or could not be loaded.
Jun 10 11:14:59 turk kernel: [    2.381686] registered taskstats version 1
Jun 10 11:14:59 turk kernel: [    2.395990]   Magic number: 0:976:223
Jun 10 11:14:59 turk kernel: [    2.396100] rtc_cmos 00:03: setting system clock to 2012-06-10 10:14:39 UTC (1339323279)
Jun 10 11:14:59 turk kernel: [    2.396114] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:14:59 turk kernel: [    2.396140] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:14:59 turk kernel: [    2.396142] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:14:59 turk kernel: [    2.396143] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:14:59 turk kernel: [    2.396144] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:14:59 turk kernel: [    2.396578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:14:59 turk kernel: [    2.396581] EDD information not available.
Jun 10 11:14:59 turk kernel: [    2.424051] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.424100] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.596033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.597154] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:14:59 turk kernel: [    2.597156] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:14:59 turk kernel: [    2.598425] ata1.00: configured for UDMA/133
Jun 10 11:14:59 turk kernel: [    2.598564] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:14:59 turk kernel: [    2.598693] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:14:59 turk kernel: [    2.598697] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:14:59 turk kernel: [    2.598775] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:14:59 turk kernel: [    2.598777] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:14:59 turk kernel: [    2.598819] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:14:59 turk kernel: [    2.600042] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.601666] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:14:59 turk kernel: [    2.603559] ata2.00: configured for UDMA/100
Jun 10 11:14:59 turk kernel: [    2.605370] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:14:59 turk kernel: [    2.607489] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:14:59 turk kernel: [    2.607491] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:14:59 turk kernel: [    2.607589] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:14:59 turk kernel: [    2.607652] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:14:59 turk kernel: [    2.655836]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:14:59 turk kernel: [    2.656338] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:14:59 turk kernel: [    2.657404] Freeing unused kernel memory: 920k freed
Jun 10 11:14:59 turk kernel: [    2.657567] Write protecting the kernel read-only data: 12288k
Jun 10 11:14:59 turk kernel: [    2.661515] Freeing unused kernel memory: 1608k freed
Jun 10 11:14:59 turk kernel: [    2.664699] Freeing unused kernel memory: 1196k freed
Jun 10 11:14:59 turk kernel: [    2.692069] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:14:59 turk kernel: [    2.694791] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    2.694799] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696251] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:14:59 turk kernel: [    2.696266] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.696317] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696548] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:14:59 turk kernel: [    2.696559] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.696578] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696617] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    2.696894] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc90000660000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:14:59 turk kernel: [    2.696896] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:14:59 turk kernel: [    2.697191] scsi4 : pata_via
Jun 10 11:14:59 turk kernel: [    2.697286] scsi5 : pata_via
Jun 10 11:14:59 turk kernel: [    2.697419] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:14:59 turk kernel: [    2.697421] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:14:59 turk kernel: [    2.707832] scsi6 : pata_atiixp
Jun 10 11:14:59 turk kernel: [    2.707908] scsi7 : pata_atiixp
Jun 10 11:14:59 turk kernel: [    2.708355] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:14:59 turk kernel: [    2.708357] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:14:59 turk kernel: [    2.756092] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:14:59 turk kernel: [    2.764045] Refined TSC clocksource calibration: 3214.276 MHz.
Jun 10 11:14:59 turk kernel: [    2.764050] Switching to clocksource tsc
Jun 10 11:14:59 turk kernel: [    3.030225] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:14:59 turk kernel: [    3.030314] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:14:59 turk kernel: [    3.030325] usbcore: registered new interface driver usbhid
Jun 10 11:14:59 turk kernel: [    3.030326] usbhid: USB HID core driver
Jun 10 11:14:59 turk kernel: [    3.124023] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:14:59 turk kernel: [    3.256079] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:14:59 turk kernel: [    3.306222] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:14:59 turk kernel: [    3.306290] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:14:59 turk kernel: [    3.325129] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:14:59 turk kernel: [    3.325194] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:14:59 turk kernel: [    3.383002] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Jun 10 11:14:59 turk kernel: [    3.383005] EXT4-fs (sda7): write access will be enabled during recovery
Jun 10 11:14:59 turk kernel: [    4.183086] EXT4-fs (sda7): orphan cleanup on readonly fs
Jun 10 11:14:59 turk kernel: [    4.183093] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523360
Jun 10 11:14:59 turk kernel: [    4.183111] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523359
Jun 10 11:14:59 turk kernel: [    4.183139] EXT4-fs (sda7): 2 orphan inodes deleted
Jun 10 11:14:59 turk kernel: [    4.183141] EXT4-fs (sda7): recovery complete
Jun 10 11:14:59 turk kernel: [    4.418346] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:14:59 turk kernel: [   15.482395] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:14:59 turk kernel: [   15.525140] lp: driver loaded but no devices found
Jun 10 11:14:59 turk kernel: [   15.526617] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:14:59 turk kernel: [   15.538254] wmi: Mapper loaded
Jun 10 11:14:59 turk kernel: [   15.560562] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:14:59 turk kernel: [   15.560611] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:14:59 turk kernel: [   15.568947] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:14:59 turk kernel: [   15.568950] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:14:59 turk kernel: [   15.569170] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:14:59 turk kernel: [   15.569230] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:14:59 turk kernel: [   15.580429] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:14:59 turk kernel: [   15.588674] MCE: In-kernel MCE decoding enabled.
Jun 10 11:14:59 turk kernel: [   15.589169] EDAC MC: Ver: 2.1.0
Jun 10 11:14:59 turk kernel: [   15.590594] AMD64 EDAC driver v3.4.0
Jun 10 11:14:59 turk kernel: [   15.594282] type=1400 audit(1339323292.694:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.594641] type=1400 audit(1339323292.694:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.594830] type=1400 audit(1339323292.694:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.633249] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:14:59 turk kernel: [   15.633332] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:14:59 turk kernel: [   15.633377] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:14:59 turk kernel: [   15.633429] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:14:59 turk kernel: [   15.633472] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:14:59 turk kernel: [   15.633514] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:14:59 turk kernel: [   15.633556] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:14:59 turk kernel: [   15.633595] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:14:59 turk kernel: [   15.636834] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [   15.636837] hda_intel: Disabling MSI
Jun 10 11:14:59 turk kernel: [   15.636868] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [   15.639563] EDAC amd64: DRAM ECC disabled.
Jun 10 11:14:59 turk kernel: [   15.639570] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:14:59 turk kernel: [   15.639571]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:14:59 turk kernel: [   15.639572]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:14:59 turk kernel: [   15.653340] ppdev: user-space parallel port driver
Jun 10 11:14:59 turk kernel: [   15.656294] lp0: using parport0 (interrupt-driven).
Jun 10 11:14:59 turk kernel: [   16.225120] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:14:59 turk kernel: [   16.225123] Disabling lock debugging due to kernel taint
Jun 10 11:14:59 turk kernel: [   16.476019] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.500034] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.524010] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.552035] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.552103] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:14:59 turk kernel: [   16.552171] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:14:59 turk kernel: [   16.552222] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:14:59 turk kernel: [   16.552267] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:14:59 turk kernel: [   16.552619] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [   16.552627] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [   16.552630] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:14:59 turk kernel: [   16.552781] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:14:59 turk kernel: [   16.859334] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:14:59 turk kernel: [   16.859337] vesafb: scrolling: redraw
Jun 10 11:14:59 turk kernel: [   16.859339] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:14:59 turk kernel: [   16.863621] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:14:59 turk kernel: [   16.863763] Console: switching to colour frame buffer device 80x30
Jun 10 11:14:59 turk kernel: [   16.863773] fb0: VESA VGA frame buffer device
Jun 10 11:14:59 turk NetworkManager[984]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk kernel: [   17.352445] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:14:59 turk kernel: [   19.931462] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:14:59 turk kernel: [   22.258243] init: failsafe main process (929) killed by TERM signal
Jun 10 11:14:59 turk kernel: [   22.527430] Bluetooth: Core ver 2.16
Jun 10 11:14:59 turk kernel: [   22.527503] NET: Registered protocol family 31
Jun 10 11:14:59 turk kernel: [   22.527505] Bluetooth: HCI device and connection manager initialized
Jun 10 11:14:59 turk kernel: [   22.527507] Bluetooth: HCI socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.527508] Bluetooth: L2CAP socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.527537] Bluetooth: SCO socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.534871] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:14:59 turk kernel: [   22.534874] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:14:59 turk kernel: [   22.535079] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:14:59 turk kernel: [   22.535085] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.535086] Bluetooth: RFCOMM ver 1.11
Jun 10 11:14:59 turk kernel: [   22.535256] type=1400 audit(1339323299.634:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=997 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.535728] type=1400 audit(1339323299.634:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=997 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549237] type=1400 audit(1339323299.650:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549647] type=1400 audit(1339323299.650:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1032 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549873] type=1400 audit(1339323299.650:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.550085] type=1400 audit(1339323299.650:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.551872] type=1400 audit(1339323299.650:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1038 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.552333] type=1400 audit(1339323299.654:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1038 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.552511] type=1400 audit(1339323299.654:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1040 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.554587] type=1400 audit(1339323299.654:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1036 comm="apparmor_parser"
Jun 10 11:14:59 turk NetworkManager[984]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <info> Networking is enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): carrier is OFF
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): now managed
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): bringing up device.
Jun 10 11:14:59 turk acpid: starting up with proc fs
Jun 10 11:14:59 turk cron[1102]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:14:59 turk acpid: 35 rules loaded
Jun 10 11:14:59 turk acpid: waiting for events: event logging is off
Jun 10 11:14:59 turk anacron[1127]: Anacron 2.3 started on 2012-06-10
Jun 10 11:14:59 turk cron[1128]: (CRON) STARTUP (fork ok)
Jun 10 11:14:59 turk cron[1128]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:14:59 turk anacron[1127]: Normal exit (0 jobs run)
Jun 10 11:14:59 turk kernel: [   22.723984] vboxdrv: Found 4 processor cores.
Jun 10 11:14:59 turk acpid: client connected from 1154[0:0]
Jun 10 11:14:59 turk acpid: 1 client rule loaded
Jun 10 11:14:59 turk kernel: [   22.724228] vboxdrv: fAsync=0 offMin=0x396 offMax=0x1600
Jun 10 11:14:59 turk kernel: [   22.724279] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:14:59 turk kernel: [   22.724280] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:14:59 turk kernel: [   22.739160] vboxpci: IOMMU not found (not registered)
Jun 10 11:14:59 turk kernel: [   22.787486] r8169 0000:04:00.0: eth0: link down
Jun 10 11:14:59 turk kernel: [   22.787499] r8169 0000:04:00.0: eth0: link down
Jun 10 11:14:59 turk kernel: [   22.787830] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): preparing device.
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:14:59 turk NetworkManager[984]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:14:59 turk kernel: [   22.788148] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:15:00 turk anacron[1262]: Anacron 2.3 started on 2012-06-10
Jun 10 11:15:00 turk anacron[1262]: Normal exit (0 jobs run)
Jun 10 11:15:00 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:15:00 turk udev-configure-printer: Failed to get parent
Jun 10 11:15:00 turk udev-configure-printer: add /module/lp
Jun 10 11:15:00 turk udev-configure-printer: Failed to get parent
Jun 10 11:15:01 turk acpid: client connected from 1154[0:0]
Jun 10 11:15:01 turk acpid: 1 client rule loaded
Jun 10 11:15:01 turk dbus[947]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:15:01 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:15:01 turk accounts-daemon[1397]: started daemon version 0.6.15
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:15:01 turk NetworkManager[984]: <info> dhclient started with pid 1401
Jun 10 11:15:01 turk kernel: [   24.408599] r8169 0000:04:00.0: eth0: link up
Jun 10 11:15:01 turk kernel: [   24.408950] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:15:01 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:15:01 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:15:01 turk dhclient: All rights reserved.
Jun 10 11:15:01 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:15:01 turk dhclient: 
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:15:01 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:15:01 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:15:01 turk dhclient: Sending on   Socket/fallback
Jun 10 11:15:01 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:15:01 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:15:01 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:15:01 turk dbus[947]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:15:01 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:15:01 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:15:01 turk dhclient: bound to 192.168.1.103 -- renewal in 32725 seconds.
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:15:01 turk NetworkManager[984]: <info>   address 192.168.1.103
Jun 10 11:15:01 turk NetworkManager[984]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:15:01 turk NetworkManager[984]: <info>   gateway 192.168.1.1
Jun 10 11:15:01 turk NetworkManager[984]: <info>   nameserver '194.168.4.100'
Jun 10 11:15:01 turk NetworkManager[984]: <info>   nameserver '194.168.8.100'
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:15:02 turk anacron[1610]: Anacron 2.3 started on 2012-06-10
Jun 10 11:15:02 turk anacron[1610]: Normal exit (0 jobs run)
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully called chroot.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully dropped privileges.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully limited resources.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Canary thread running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Watchdog thread running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully made thread 1736 of process 1736 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:15:02 turk NetworkManager[984]: <info> DNS: starting dnsmasq...
Jun 10 11:15:02 turk NetworkManager[984]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:15:02 turk dnsmasq[1743]: started, version 2.59 cache disabled
Jun 10 11:15:02 turk dnsmasq[1743]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:15:02 turk dnsmasq[1743]: using nameserver 194.168.8.100#53
Jun 10 11:15:02 turk dnsmasq[1743]: using nameserver 194.168.4.100#53
Jun 10 11:15:02 turk NetworkManager[984]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:15:02 turk NetworkManager[984]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:15:02 turk NetworkManager[984]: <info> Activation (eth0) successful, device activated.
Jun 10 11:15:02 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:15:03 turk rtkit-daemon[1738]: Successfully made thread 1822 of process 1736 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Successfully made thread 1823 of process 1736 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:15:04 turk dbus[947]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:15:04 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:15:11 turk ntpdate[1803]: adjust time server 91.189.94.4 offset -0.127551 sec
Jun 10 11:15:12 turk kernel: [   34.944007] eth0: no IPv6 routers present
Jun 10 11:15:19 turk goa[2141]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:15:22 turk NetworkManager[984]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:16:05 turk dbus[947]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun 10 11:16:05 turk AptDaemon: INFO: Initializing daemon
Jun 10 11:16:06 turk AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 10 11:16:06 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 10 11:16:06 turk AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 10 11:16:06 turk AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
Jun 10 11:16:06 turk AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
Jun 10 11:16:08 turk AptDaemon.PackageKit: INFO: Get updates()
Jun 10 11:16:09 turk AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
```

---

### Post by db260179 on 2012-06-10
Hi, your bios version is quite old. 1404, newest version is 1704

[http://uk.asus.com/Motherboards/AMD_AM3/M4A88TDM_EVOUSB3/#download](http://uk.asus.com/Motherboards/AMD_AM3/M4A88TDM_EVOUSB3/#download)

Unlikely reason for your problems but always good to keep up to date.

As you have tested your RAM and HDD, I would say your most likely problem now is the motherboard,cpu and power supply.

It is always good to buy a power supply tester. I had a faulty psu once which caused random crashing. What is the wattage rating? i.e. 500W?

In rare cases the cpu could be faulty. I find the motherboard and psu are the usual suspects.

I recommend you buy a power tester first, then a motherboard - hopefully one will resolve your issue.

Hope this helps you?

And good luck!

> **Sunships said:**
> Alright, I removed both PCI cards (the graphics card and USB3 card) to see what effect this would have - I was able to use the system all day yesterday with no crashing at all, which suggests that their presence in the system exacerbates/causes the problem.

I tried running the system with just the graphics card installed and not the USB3 card - the computer commenced crashing, once again. I have attached /var/log/syslog - ctashes occur around 11:02:23 and 11:03:34.

Does this make sense to anyone? The retailer tested my graphics card earlier this week and found no faults, so does this definitely implicate the motherboard/CPU as the source of the problem?

/var/log/syslog:

```
Jun 10 10:36:48 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 10 10:36:49 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 10 10:37:49 turk anacron[1124]: Job `cron.daily' terminated (mailing output)
Jun 10 10:37:49 turk anacron[1124]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun 10 10:37:49 turk anacron[1124]: Normal exit (1 job run)
Jun 10 10:53:08 turk kernel: Kernel logging (proc) stopped.
Jun 10 10:53:08 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="982" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jun 10 11:00:20 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:00:20 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="961" x-info="http://www.rsyslog.com"] start
Jun 10 11:00:20 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:00:20 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:00:20 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:00:20 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:00:20 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:00:20 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:00:20 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:00:20 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:00:20 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:00:20 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:00:20 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:00:20 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:00:20 turk kernel: [    0.000000] DMI present.
Jun 10 11:00:20 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:00:20 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:00:20 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:00:20 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:00:20 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:00:20 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:00:20 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:00:20 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:00:20 turk kernel: [    0.000000]   3 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   4 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   5 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   6 disabled
Jun 10 11:00:20 turk kernel: [    0.000000]   7 disabled
Jun 10 11:00:20 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:00:20 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:00:20 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:00:20 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:00:20 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:00:20 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:00:20 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:00:20 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:00:20 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:00:20 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:00:20 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:00:20 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:00:20 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:00:20 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:00:20 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:00:20 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:00:20 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:00:20 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:00:20 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:00:20 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:00:20 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:00:20 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:00:20 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:00:20 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:00:20 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:00:20 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:00:20 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:00:20 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:00:20 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:00:20 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:00:20 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:00:20 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:00:20 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:00:20 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:00:20 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:00:20 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:00:20 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:00:20 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:00:20 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:00:20 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:00:20 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:00:20 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:00:20 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:00:20 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:00:20 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:00:20 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:00:20 turk kernel: [    0.000000] Node 0: aperture @ 1302000000 size 32 MB
Jun 10 11:00:20 turk kernel: [    0.000000] Aperture beyond 4GB. Ignoring.
Jun 10 11:00:20 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:00:20 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:00:20 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:00:20 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:00:20 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:00:20 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:00:20 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:00:20 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:00:20 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:00:20 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:00:20 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:00:20 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:00:20 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:00:20 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:00:20 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:00:20 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:00:20 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:00:20 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:00:20 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:00:20 turk kernel: [    0.000000] Detected 3214.292 MHz processor.
Jun 10 11:00:20 turk kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.58 BogoMIPS (lpj=12857168)
Jun 10 11:00:20 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:00:20 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:00:20 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:00:20 turk kernel: [    0.004039] Yama: becoming mindful.
Jun 10 11:00:20 turk kernel: [    0.004343] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:00:20 turk kernel: [    0.008824] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:00:20 turk kernel: [    0.009436] Mount-cache hash table entries: 256
Jun 10 11:00:20 turk kernel: [    0.009538] Initializing cgroup subsys cpuacct
Jun 10 11:00:20 turk kernel: [    0.009542] Initializing cgroup subsys memory
Jun 10 11:00:20 turk kernel: [    0.009549] Initializing cgroup subsys devices
Jun 10 11:00:20 turk kernel: [    0.009550] Initializing cgroup subsys freezer
Jun 10 11:00:20 turk kernel: [    0.009552] Initializing cgroup subsys blkio
Jun 10 11:00:20 turk kernel: [    0.009557] Initializing cgroup subsys perf_event
Jun 10 11:00:20 turk kernel: [    0.009580] tseg: 0000000000
Jun 10 11:00:20 turk kernel: [    0.009590] CPU: Physical Processor ID: 0
Jun 10 11:00:20 turk kernel: [    0.009591] CPU: Processor Core ID: 0
Jun 10 11:00:20 turk kernel: [    0.009593] mce: CPU supports 6 MCE banks
Jun 10 11:00:20 turk kernel: [    0.010751] ACPI: Core revision 20110623
Jun 10 11:00:20 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:00:20 turk kernel: [    0.020382] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:00:20 turk kernel: [    0.060495] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:00:20 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:00:20 turk kernel: [    0.064003] ... version:                0
Jun 10 11:00:20 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:00:20 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:00:20 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:00:20 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:00:20 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:00:20 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:00:20 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:00:20 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.152084]  #2
Jun 10 11:00:20 turk kernel: [    0.152085] smpboot cpu 2: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.244079]  #3
Jun 10 11:00:20 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:00:20 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:00:20 turk kernel: [    0.336051] Brought up 4 CPUs
Jun 10 11:00:20 turk kernel: [    0.336053] Total of 4 processors activated (25714.37 BogoMIPS).
Jun 10 11:00:20 turk kernel: [    0.340159] devtmpfs: initialized
Jun 10 11:00:20 turk kernel: [    0.341186] EVM: security.selinux
Jun 10 11:00:20 turk kernel: [    0.341187] EVM: security.SMACK64
Jun 10 11:00:20 turk kernel: [    0.341188] EVM: security.capability
Jun 10 11:00:20 turk kernel: [    0.341284] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:00:20 turk kernel: [    0.341284] print_constraints: dummy: 
Jun 10 11:00:20 turk kernel: [    0.341284] RTC time: 10:00:00, date: 06/10/12
Jun 10 11:00:20 turk kernel: [    0.341284] NET: Registered protocol family 16
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: io port [1000, ffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] TOM: 00000000d0000000 aka 3328M
Jun 10 11:00:20 turk kernel: [    0.341284] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:00:20 turk kernel: [    0.341284] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:00:20 turk kernel: [    0.341284] TOM2: 0000000130000000 aka 4864M
Jun 10 11:00:20 turk kernel: [    0.341284] bus: [00, 07] on node 0 link 0
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:00:20 turk kernel: [    0.341284] Extended Config Space enabled on 1 nodes
Jun 10 11:00:20 turk kernel: [    0.341284] ACPI: bus type pci registered
Jun 10 11:00:20 turk kernel: [    0.341284] Trying to unpack rootfs image as initramfs...
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: not using MMCONFIG
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: Using configuration type 1 for base access
Jun 10 11:00:20 turk kernel: [    0.341284] PCI: Using configuration type 1 for extended access
Jun 10 11:00:20 turk kernel: [    0.341461] bio: create slab <bio-0> at 0
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Module Device)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Processor Device)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:00:20 turk kernel: [    0.341461] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:00:20 turk kernel: [    0.344473] ACPI: EC: Look up EC in DSDT
Jun 10 11:00:20 turk kernel: [    0.380085] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:00:20 turk kernel: [    0.552580] ACPI: Interpreter enabled
Jun 10 11:00:20 turk kernel: [    0.552586] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:00:20 turk kernel: [    0.552602] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:00:20 turk kernel: [    0.552621] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:00:20 turk kernel: [    0.553992] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:00:20 turk kernel: [    0.557742] Freeing initrd memory: 13844k freed
Jun 10 11:00:20 turk kernel: [    0.646051] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:00:20 turk kernel: [    0.646149] ACPI: No dock devices found.
Jun 10 11:00:20 turk kernel: [    0.646150] HEST: Table not found.
Jun 10 11:00:20 turk kernel: [    0.646153] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:00:20 turk kernel: [    0.646209] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:00:20 turk kernel: [    0.646324] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.646326] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.646328] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.646330] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.646331] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.646333] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.646345] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.646387] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646416] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646418] pci 0000:00:02.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646433] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646461] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646463] pci 0000:00:07.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646475] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646502] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646504] pci 0000:00:09.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646515] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.646542] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.646544] pci 0000:00:0a.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646568] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.646586] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:00:20 turk kernel: [    0.646594] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:00:20 turk kernel: [    0.646603] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:00:20 turk kernel: [    0.646611] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:00:20 turk kernel: [    0.646619] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:00:20 turk kernel: [    0.646627] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:00:20 turk kernel: [    0.646645] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:00:20 turk kernel: [    0.646696] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646708] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:00:20 turk kernel: [    0.646769] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646785] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:00:20 turk kernel: [    0.646856] pci 0000:00:12.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.646857] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.646860] pci 0000:00:12.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.646878] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646889] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:00:20 turk kernel: [    0.646950] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.646966] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:00:20 turk kernel: [    0.647037] pci 0000:00:13.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.647038] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.647041] pci 0000:00:13.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647058] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:00:20 turk kernel: [    0.647124] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.647138] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:00:20 turk kernel: [    0.647146] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:00:20 turk kernel: [    0.647155] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:00:20 turk kernel: [    0.647163] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:00:20 turk kernel: [    0.647171] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:00:20 turk kernel: [    0.647221] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:00:20 turk kernel: [    0.647240] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:00:20 turk kernel: [    0.647296] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.647299] pci 0000:00:14.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647310] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:00:20 turk kernel: [    0.647376] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:00:20 turk kernel: [    0.647411] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647423] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:00:20 turk kernel: [    0.647481] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647492] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:00:20 turk kernel: [    0.647553] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:00:20 turk kernel: [    0.647569] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:00:20 turk kernel: [    0.647640] pci 0000:00:16.2: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.647641] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.647644] pci 0000:00:16.2: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.647660] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647673] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647683] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647693] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647706] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:00:20 turk kernel: [    0.647749] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:00:20 turk kernel: [    0.647757] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:00:20 turk kernel: [    0.647767] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.647776] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.647783] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:00:20 turk kernel: [    0.647789] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:00:20 turk kernel: [    0.647840] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:00:20 turk kernel: [    0.647849] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:00:20 turk kernel: [    0.652059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:00:20 turk kernel: [    0.652064] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.652066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.652069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.652115] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:00:20 turk kernel: [    0.652144] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:00:20 turk kernel: [    0.652159] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:00:20 turk kernel: [    0.652284] pci 0000:02:00.0: supports D2
Jun 10 11:00:20 turk kernel: [    0.652285] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.652291] pci 0000:02:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.660063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:00:20 turk kernel: [    0.660067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.660069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.660115] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:00:20 turk kernel: [    0.660137] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:00:20 turk kernel: [    0.660152] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:00:20 turk kernel: [    0.660166] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:00:20 turk kernel: [    0.660181] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:00:20 turk kernel: [    0.660195] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:00:20 turk kernel: [    0.660223] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:00:20 turk kernel: [    0.660297] pci 0000:03:00.0: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.660298] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:00:20 turk kernel: [    0.660304] pci 0000:03:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.668061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:00:20 turk kernel: [    0.668065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.668067] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.668102] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:00:20 turk kernel: [    0.668116] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:00:20 turk kernel: [    0.668135] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.668147] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.668199] pci 0000:04:00.0: supports D1 D2
Jun 10 11:00:20 turk kernel: [    0.668200] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:00:20 turk kernel: [    0.668204] pci 0000:04:00.0: PME# disabled
Jun 10 11:00:20 turk kernel: [    0.676059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:00:20 turk kernel: [    0.676063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.676067] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.676121] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676129] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676131] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676132] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676134] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676136] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676137] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:00:20 turk kernel: [    0.676159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:00:20 turk kernel: [    0.676253] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:00:20 turk kernel: [    0.676275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:00:20 turk kernel: [    0.676291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:00:20 turk kernel: [    0.676310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:00:20 turk kernel: [    0.676329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:00:20 turk kernel: [    0.676364]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:00:20 turk kernel: [    0.676366]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:00:20 turk kernel: [    0.676368] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:00:20 turk kernel: [    0.679423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679468] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679511] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679552] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:00:20 turk kernel: [    0.679584] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679611] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679636] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679660] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: loaded
Jun 10 11:00:20 turk kernel: [    0.679735] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:00:20 turk kernel: [    0.679735] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:00:20 turk kernel: [    0.679735] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:00:20 turk kernel: [    0.679735] SCSI subsystem initialized
Jun 10 11:00:20 turk kernel: [    0.679735] libata version 3.00 loaded.
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new interface driver usbfs
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new interface driver hub
Jun 10 11:00:20 turk kernel: [    0.679735] usbcore: registered new device driver usb
Jun 10 11:00:20 turk kernel: [    0.680068] PCI: Using ACPI for IRQ routing
Jun 10 11:00:20 turk kernel: [    0.687446] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:00:20 turk kernel: [    0.687514] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:00:20 turk kernel: [    0.687516] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:00:20 turk kernel: [    0.687584] NetLabel: Initializing
Jun 10 11:00:20 turk kernel: [    0.687585] NetLabel:  domain hash size = 128
Jun 10 11:00:20 turk kernel: [    0.687586] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:00:20 turk kernel: [    0.687594] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:00:20 turk kernel: [    0.687622] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:00:20 turk kernel: [    0.687622] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:00:20 turk kernel: [    0.689066] Switching to clocksource hpet
Jun 10 11:00:20 turk kernel: [    0.692695] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:00:20 turk kernel: [    0.692711] pnp: PnP ACPI init
Jun 10 11:00:20 turk kernel: [    0.692721] ACPI: bus type pnp registered
Jun 10 11:00:20 turk kernel: [    0.692795] pnp 00:00: [bus 00-ff]
Jun 10 11:00:20 turk kernel: [    0.692797] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:00:20 turk kernel: [    0.692799] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:00:20 turk kernel: [    0.692800] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:00:20 turk kernel: [    0.692802] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:00:20 turk kernel: [    0.692803] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:00:20 turk kernel: [    0.692805] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:00:20 turk kernel: [    0.692807] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:00:20 turk kernel: [    0.692841] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:00:20 turk kernel: [    0.692894] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.692896] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.692928] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.693418] pnp 00:02: [dma 4]
Jun 10 11:00:20 turk kernel: [    0.693420] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:00:20 turk kernel: [    0.693421] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:00:20 turk kernel: [    0.693423] pnp 00:02: [io  0x0087]
Jun 10 11:00:20 turk kernel: [    0.693424] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:00:20 turk kernel: [    0.693425] pnp 00:02: [io  0x008f]
Jun 10 11:00:20 turk kernel: [    0.693426] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:00:20 turk kernel: [    0.693447] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:00:20 turk kernel: [    0.693453] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:00:20 turk kernel: [    0.693461] pnp 00:03: [irq 8]
Jun 10 11:00:20 turk kernel: [    0.693482] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:00:20 turk kernel: [    0.693487] pnp 00:04: [io  0x0061]
Jun 10 11:00:20 turk kernel: [    0.693508] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:00:20 turk kernel: [    0.693513] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:00:20 turk kernel: [    0.693517] pnp 00:05: [irq 13]
Jun 10 11:00:20 turk kernel: [    0.693536] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:00:20 turk kernel: [    0.693983] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:00:20 turk kernel: [    0.693986] pnp 00:06: [irq 7]
Jun 10 11:00:20 turk kernel: [    0.693988] pnp 00:06: [dma 0 disabled]
Jun 10 11:00:20 turk kernel: [    0.694153] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:00:20 turk kernel: [    0.694179] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:00:20 turk kernel: [    0.694202] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:00:20 turk kernel: [    0.694526] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:00:20 turk kernel: [    0.694529] pnp 00:08: [irq 4]
Jun 10 11:00:20 turk kernel: [    0.694530] pnp 00:08: [dma 0 disabled]
Jun 10 11:00:20 turk kernel: [    0.694594] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:00:20 turk kernel: [    0.694640] pnp 00:09: [io  0x0060]
Jun 10 11:00:20 turk kernel: [    0.694641] pnp 00:09: [io  0x0064]
Jun 10 11:00:20 turk kernel: [    0.694644] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:00:20 turk kernel: [    0.694646] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:00:20 turk kernel: [    0.694682] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.694684] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694686] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.694776] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:00:20 turk kernel: [    0.694778] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:00:20 turk kernel: [    0.694779] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:00:20 turk kernel: [    0.694780] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:00:20 turk kernel: [    0.694782] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:00:20 turk kernel: [    0.694783] pnp 00:0a: [io  0x0080]
Jun 10 11:00:20 turk kernel: [    0.694784] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:00:20 turk kernel: [    0.694785] pnp 00:0a: [io  0x0088]
Jun 10 11:00:20 turk kernel: [    0.694787] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:00:20 turk kernel: [    0.694788] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:00:20 turk kernel: [    0.694789] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:00:20 turk kernel: [    0.694790] pnp 00:0a: [io  0x00b1]
Jun 10 11:00:20 turk kernel: [    0.694791] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:00:20 turk kernel: [    0.694793] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:00:20 turk kernel: [    0.694794] pnp 00:0a: [io  0x040b]
Jun 10 11:00:20 turk kernel: [    0.694795] pnp 00:0a: [io  0x04d6]
Jun 10 11:00:20 turk kernel: [    0.694796] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:00:20 turk kernel: [    0.694798] pnp 00:0a: [io  0x0c14]
Jun 10 11:00:20 turk kernel: [    0.694799] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:00:20 turk kernel: [    0.694800] pnp 00:0a: [io  0x0c52]
Jun 10 11:00:20 turk kernel: [    0.694801] pnp 00:0a: [io  0x0c6c]
Jun 10 11:00:20 turk kernel: [    0.694802] pnp 00:0a: [io  0x0c6f]
Jun 10 11:00:20 turk kernel: [    0.694803] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:00:20 turk kernel: [    0.694805] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:00:20 turk kernel: [    0.694806] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:00:20 turk kernel: [    0.694807] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:00:20 turk kernel: [    0.694808] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:00:20 turk kernel: [    0.694810] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:00:20 turk kernel: [    0.694811] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:00:20 turk kernel: [    0.694812] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.694814] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:00:20 turk kernel: [    0.694815] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:00:20 turk kernel: [    0.694816] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:00:20 turk kernel: [    0.694818] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:00:20 turk kernel: [    0.694819] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:00:20 turk kernel: [    0.694820] pnp 00:0a: [io  0x0060]
Jun 10 11:00:20 turk kernel: [    0.694821] pnp 00:0a: [io  0x0064]
Jun 10 11:00:20 turk kernel: [    0.694823] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:00:20 turk kernel: [    0.694824] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:00:20 turk kernel: [    0.694826] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:00:20 turk kernel: [    0.694827] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:00:20 turk kernel: [    0.694830] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.694905] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694907] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694908] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694910] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694912] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694914] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694915] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694917] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694918] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694920] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694922] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694924] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694926] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694927] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694929] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694931] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694934] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694936] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694938] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694939] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694941] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694943] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694945] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694947] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694949] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.694952] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695049] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:00:20 turk kernel: [    0.695050] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:00:20 turk kernel: [    0.695052] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:00:20 turk kernel: [    0.695053] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:00:20 turk kernel: [    0.695054] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:00:20 turk kernel: [    0.695089] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695091] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695093] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695094] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695096] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695125] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:00:20 turk kernel: [    0.695158] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:00:20 turk kernel: [    0.695160] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:00:20 turk kernel: [    0.695227] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:00:20 turk kernel: [    0.695229] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:00:20 turk kernel: [    0.695230] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:00:20 turk kernel: [    0.695232] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:00:20 turk kernel: [    0.695233] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:00:20 turk kernel: [    0.695268] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695270] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695272] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695274] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695276] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:00:20 turk kernel: [    0.695278] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:00:20 turk kernel: [    0.695343] pnp: PnP ACPI: found 14 devices
Jun 10 11:00:20 turk kernel: [    0.695344] ACPI: ACPI bus type pnp unregistered
Jun 10 11:00:20 turk kernel: [    0.701735] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:00:20 turk kernel: [    0.701753] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:00:20 turk kernel: [    0.701756] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.701758] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.701761] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701764] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:00:20 turk kernel: [    0.701766] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.701768] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.701772] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:00:20 turk kernel: [    0.701773] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.701776] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701779] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:00:20 turk kernel: [    0.701781] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.701784] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701787] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:00:20 turk kernel: [    0.701806] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    0.701809] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701815] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    0.701817] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701823] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    0.701825] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701828] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    0.701830] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    0.701836] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.701838] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.701840] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.701841] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.701843] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.701845] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701846] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:00:20 turk kernel: [    0.701848] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:00:20 turk kernel: [    0.701850] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701852] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:00:20 turk kernel: [    0.701854] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:00:20 turk kernel: [    0.701856] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:00:20 turk kernel: [    0.701857] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701859] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:00:20 turk kernel: [    0.701861] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:00:20 turk kernel: [    0.701863] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:00:20 turk kernel: [    0.701865] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:00:20 turk kernel: [    0.701867] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:00:20 turk kernel: [    0.701868] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:00:20 turk kernel: [    0.701870] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:00:20 turk kernel: [    0.701872] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:00:20 turk kernel: [    0.701901] NET: Registered protocol family 2
Jun 10 11:00:20 turk kernel: [    0.702008] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:00:20 turk kernel: [    0.702902] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:00:20 turk kernel: [    0.705370] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:00:20 turk kernel: [    0.705677] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:00:20 turk kernel: [    0.705679] TCP reno registered
Jun 10 11:00:20 turk kernel: [    0.705686] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:00:20 turk kernel: [    0.705715] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:00:20 turk kernel: [    0.705806] NET: Registered protocol family 1
Jun 10 11:00:20 turk kernel: [    0.705835] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.524036] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.524048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.524089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.524094] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.604039] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.604049] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.604089] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.604103] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.684032] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:00:20 turk kernel: [    1.684042] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    1.764040] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    1.764050] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    1.764090] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:00:20 turk kernel: [    1.764109] pci 0000:01:00.0: Boot video device
Jun 10 11:00:20 turk kernel: [    1.764125] PCI: CLS 64 bytes, default 64
Jun 10 11:00:20 turk kernel: [    1.765385] PCI-DMA: Disabling AGP.
Jun 10 11:00:20 turk kernel: [    1.765458] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:00:20 turk kernel: [    1.765459] PCI-DMA: using GART IOMMU.
Jun 10 11:00:20 turk kernel: [    1.765462] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:00:20 turk kernel: [    1.768918] IBS: LVT offset 1 assigned
Jun 10 11:00:20 turk kernel: [    1.768935] perf: AMD IBS detected (0x0000001f)
Jun 10 11:00:20 turk kernel: [    1.769046] audit: initializing netlink socket (disabled)
Jun 10 11:00:20 turk kernel: [    1.769060] type=2000 audit(1339322401.764:1): initialized
Jun 10 11:00:20 turk kernel: [    1.793136] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:00:20 turk kernel: [    1.812150] VFS: Disk quotas dquot_6.5.2
Jun 10 11:00:20 turk kernel: [    1.812192] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:00:20 turk kernel: [    1.812614] fuse init (API version 7.17)
Jun 10 11:00:20 turk kernel: [    1.812681] msgmni has been set to 7901
Jun 10 11:00:20 turk kernel: [    1.813004] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:00:20 turk kernel: [    1.813031] io scheduler noop registered
Jun 10 11:00:20 turk kernel: [    1.813033] io scheduler deadline registered
Jun 10 11:00:20 turk kernel: [    1.813053] io scheduler cfq registered (default)
Jun 10 11:00:20 turk kernel: [    1.813174] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813202] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813282] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813300] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813365] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813384] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813445] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    1.813462] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    1.813515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:00:20 turk kernel: [    1.813532] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:00:20 turk kernel: [    1.813624] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:00:20 turk kernel: [    1.813628] ACPI: Power Button [PWRB]
Jun 10 11:00:20 turk kernel: [    1.813656] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:00:20 turk kernel: [    1.813658] ACPI: Power Button [PWRF]
Jun 10 11:00:20 turk kernel: [    1.996934] ERST: Table is not found!
Jun 10 11:00:20 turk kernel: [    1.996936] GHES: HEST is not enabled!
Jun 10 11:00:20 turk kernel: [    1.997012] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:00:20 turk kernel: [    2.017420] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:00:20 turk kernel: [    2.064783] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:00:20 turk kernel: [    2.112219] Linux agpgart interface v0.103
Jun 10 11:00:20 turk kernel: [    2.113254] brd: module loaded
Jun 10 11:00:20 turk kernel: [    2.113782] loop: module loaded
Jun 10 11:00:20 turk kernel: [    2.113927] ahci 0000:00:11.0: version 3.0
Jun 10 11:00:20 turk kernel: [    2.113937] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    2.113987] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    2.114058] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:00:20 turk kernel: [    2.114060] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:00:20 turk kernel: [    2.114472] scsi0 : ahci
Jun 10 11:00:20 turk kernel: [    2.114539] scsi1 : ahci
Jun 10 11:00:20 turk kernel: [    2.114590] scsi2 : ahci
Jun 10 11:00:20 turk kernel: [    2.114641] scsi3 : ahci
Jun 10 11:00:20 turk kernel: [    2.114709] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:00:20 turk kernel: [    2.114712] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:00:20 turk kernel: [    2.114714] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:00:20 turk kernel: [    2.114717] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:00:20 turk kernel: [    2.114849] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.114869] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.114930] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.114947] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.114956] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:00:20 turk kernel: [    2.115244] Fixed MDIO Bus: probed
Jun 10 11:00:20 turk kernel: [    2.115258] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:00:20 turk kernel: [    2.115259] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:00:20 turk kernel: [    2.115298] PPP generic driver version 2.4.2
Jun 10 11:00:20 turk kernel: [    2.115370] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:00:20 turk kernel: [    2.115407] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.115417] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.115460] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:00:20 turk kernel: [    2.115466] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.115480] QUIRK: Enable AMD PLL fix
Jun 10 11:00:20 turk kernel: [    2.115489] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.115505] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:00:20 turk kernel: [    2.124040] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.124142] hub 1-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.124146] hub 1-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.124246] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.124259] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.124292] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:00:20 turk kernel: [    2.124298] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.124314] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.124325] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:00:20 turk kernel: [    2.136041] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.136130] hub 2-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.136133] hub 2-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.136237] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.136248] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.136282] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:00:20 turk kernel: [    2.136288] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:00:20 turk kernel: [    2.136304] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:00:20 turk kernel: [    2.136314] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:00:20 turk kernel: [    2.148040] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:00:20 turk kernel: [    2.148125] hub 3-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.148127] hub 3-0:1.0: 4 ports detected
Jun 10 11:00:20 turk kernel: [    2.148189] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:00:20 turk kernel: [    2.148245] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.148258] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.148291] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:00:20 turk kernel: [    2.148312] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:00:20 turk kernel: [    2.208098] hub 4-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.208103] hub 4-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.208211] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.208222] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.208258] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:00:20 turk kernel: [    2.208270] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:00:20 turk kernel: [    2.268098] hub 5-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.268103] hub 5-0:1.0: 5 ports detected
Jun 10 11:00:20 turk kernel: [    2.268209] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.268220] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.268253] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:00:20 turk kernel: [    2.268265] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:00:20 turk kernel: [    2.328118] hub 6-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.328124] hub 6-0:1.0: 2 ports detected
Jun 10 11:00:20 turk kernel: [    2.328228] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.328240] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:00:20 turk kernel: [    2.328274] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:00:20 turk kernel: [    2.328286] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:00:20 turk kernel: [    2.388145] hub 7-0:1.0: USB hub found
Jun 10 11:00:20 turk kernel: [    2.388150] hub 7-0:1.0: 4 ports detected
Jun 10 11:00:20 turk kernel: [    2.388216] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:00:20 turk kernel: [    2.388263] usbcore: registered new interface driver libusual
Jun 10 11:00:20 turk kernel: [    2.388287] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:00:20 turk kernel: [    2.388645] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:00:20 turk kernel: [    2.388651] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:00:20 turk kernel: [    2.388774] mousedev: PS/2 mouse device common for all mice
Jun 10 11:00:20 turk kernel: [    2.388879] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:00:20 turk kernel: [    2.388957] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:00:20 turk kernel: [    2.388978] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:00:20 turk kernel: [    2.389031] device-mapper: uevent: version 1.0.3
Jun 10 11:00:20 turk kernel: [    2.389078] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:00:20 turk kernel: [    2.389084] cpuidle: using governor ladder
Jun 10 11:00:20 turk kernel: [    2.389085] cpuidle: using governor menu
Jun 10 11:00:20 turk kernel: [    2.389087] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:00:20 turk kernel: [    2.389229] TCP cubic registered
Jun 10 11:00:20 turk kernel: [    2.389295] NET: Registered protocol family 10
Jun 10 11:00:20 turk kernel: [    2.389603] NET: Registered protocol family 17
Jun 10 11:00:20 turk kernel: [    2.389614] Registering the dns_resolver key type
Jun 10 11:00:20 turk kernel: [    2.389722] PM: Hibernation image not present or could not be loaded.
Jun 10 11:00:20 turk kernel: [    2.389729] registered taskstats version 1
Jun 10 11:00:20 turk kernel: [    2.404088]   Magic number: 0:770:21
Jun 10 11:00:20 turk kernel: [    2.404136] pcieport 0000:00:09.0: hash matches
Jun 10 11:00:20 turk kernel: [    2.404180] rtc_cmos 00:03: setting system clock to 2012-06-10 10:00:02 UTC (1339322402)
Jun 10 11:00:20 turk kernel: [    2.404194] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:00:20 turk kernel: [    2.404218] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:00:20 turk kernel: [    2.404219] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:00:20 turk kernel: [    2.404220] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:00:20 turk kernel: [    2.404222] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:00:20 turk kernel: [    2.404643] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:00:20 turk kernel: [    2.404645] EDD information not available.
Jun 10 11:00:20 turk kernel: [    2.432093] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.436066] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.604036] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.604062] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:00:20 turk kernel: [    2.605184] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:00:20 turk kernel: [    2.605187] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:00:20 turk kernel: [    2.605653] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:00:20 turk kernel: [    2.606451] ata1.00: configured for UDMA/133
Jun 10 11:00:20 turk kernel: [    2.606592] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:00:20 turk kernel: [    2.606719] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:00:20 turk kernel: [    2.606736] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:00:20 turk kernel: [    2.606819] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:00:20 turk kernel: [    2.606821] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:00:20 turk kernel: [    2.606869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:00:20 turk kernel: [    2.607568] ata2.00: configured for UDMA/100
Jun 10 11:00:20 turk kernel: [    2.609373] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:00:20 turk kernel: [    2.611498] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:00:20 turk kernel: [    2.611501] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:00:20 turk kernel: [    2.611595] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:00:20 turk kernel: [    2.611657] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:00:20 turk kernel: [    2.658346]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:00:20 turk kernel: [    2.658827] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:00:20 turk kernel: [    2.659892] Freeing unused kernel memory: 920k freed
Jun 10 11:00:20 turk kernel: [    2.660077] Write protecting the kernel read-only data: 12288k
Jun 10 11:00:20 turk kernel: [    2.664009] Freeing unused kernel memory: 1608k freed
Jun 10 11:00:20 turk kernel: [    2.667175] Freeing unused kernel memory: 1196k freed
Jun 10 11:00:20 turk kernel: [    2.697568] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:00:20 turk kernel: [    2.697588] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:00:20 turk kernel: [    2.697641] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.698480] scsi4 : pata_via
Jun 10 11:00:20 turk kernel: [    2.699196] scsi5 : pata_via
Jun 10 11:00:20 turk kernel: [    2.699312] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:00:20 turk kernel: [    2.699314] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:00:20 turk kernel: [    2.700059] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:00:20 turk kernel: [    2.700259] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:00:20 turk kernel: [    2.700275] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [    2.700301] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    2.700342] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:00:20 turk kernel: [    2.700654] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc9000065e000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:00:20 turk kernel: [    2.700656] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:00:20 turk kernel: [    2.709877] scsi6 : pata_atiixp
Jun 10 11:00:20 turk kernel: [    2.710277] scsi7 : pata_atiixp
Jun 10 11:00:20 turk kernel: [    2.710684] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:00:20 turk kernel: [    2.710686] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:00:20 turk kernel: [    2.768027] Refined TSC clocksource calibration: 3214.267 MHz.
Jun 10 11:00:20 turk kernel: [    2.768036] Switching to clocksource tsc
Jun 10 11:00:20 turk kernel: [    3.021527] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [    3.021534] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [    3.030208] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:00:20 turk kernel: [    3.030299] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:00:20 turk kernel: [    3.030310] usbcore: registered new interface driver usbhid
Jun 10 11:00:20 turk kernel: [    3.030311] usbhid: USB HID core driver
Jun 10 11:00:20 turk kernel: [    3.084079] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:00:20 turk kernel: [    3.132037] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:00:20 turk kernel: [    3.314226] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:00:20 turk kernel: [    3.314299] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:00:20 turk kernel: [    3.333131] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:00:20 turk kernel: [    3.333194] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:00:20 turk kernel: [    3.584091] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:00:20 turk kernel: [    3.670411] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:00:20 turk kernel: [   15.184901] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk kernel: [   15.212732] lp: driver loaded but no devices found
Jun 10 11:00:20 turk kernel: [   15.223056] wmi: Mapper loaded
Jun 10 11:00:20 turk kernel: [   15.245792] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:00:20 turk kernel: [   15.245841] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:00:20 turk kernel: [   15.261141] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:00:20 turk kernel: [   15.261143] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:00:20 turk kernel: [   15.261387] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:00:20 turk kernel: [   15.261442] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:00:20 turk kernel: [   15.270531] MCE: In-kernel MCE decoding enabled.
Jun 10 11:00:20 turk kernel: [   15.270971] EDAC MC: Ver: 2.1.0
Jun 10 11:00:20 turk kernel: [   15.271946] AMD64 EDAC driver v3.4.0
Jun 10 11:00:20 turk kernel: [   15.273187] EDAC amd64: DRAM ECC disabled.
Jun 10 11:00:20 turk kernel: [   15.273193] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:00:20 turk kernel: [   15.273194]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:00:20 turk kernel: [   15.273195]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:00:20 turk kernel: [   15.273557] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:00:20 turk kernel: [   15.280351] type=1400 audit(1339322415.372:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.280708] type=1400 audit(1339322415.372:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.280916] type=1400 audit(1339322415.372:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=487 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   15.315076] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:00:20 turk kernel: [   15.340270] lp0: using parport0 (interrupt-driven).
Jun 10 11:00:20 turk kernel: [   15.351212] ppdev: user-space parallel port driver
Jun 10 11:00:20 turk kernel: [   15.365545] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:00:20 turk kernel: [   15.365609] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:00:20 turk kernel: [   15.365656] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:00:20 turk kernel: [   15.365700] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:00:20 turk kernel: [   15.365744] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:00:20 turk kernel: [   15.365788] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:00:20 turk kernel: [   15.365831] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:00:20 turk kernel: [   15.365875] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:00:20 turk kernel: [   15.366098] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:00:20 turk kernel: [   15.366101] hda_intel: Disabling MSI
Jun 10 11:00:20 turk kernel: [   15.366131] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [   15.728188] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:00:20 turk kernel: [   15.728191] Disabling lock debugging due to kernel taint
Jun 10 11:00:20 turk kernel: [   16.196021] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.220020] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.244026] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.268032] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:00:20 turk kernel: [   16.268100] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:00:20 turk kernel: [   16.268167] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:00:20 turk kernel: [   16.268216] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:00:20 turk kernel: [   16.268264] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:00:20 turk kernel: [   16.268621] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:00:20 turk kernel: [   16.268628] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:00:20 turk kernel: [   16.268632] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:00:20 turk kernel: [   16.268825] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:00:20 turk kernel: [   16.712058] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:00:20 turk kernel: [   16.712061] vesafb: scrolling: redraw
Jun 10 11:00:20 turk kernel: [   16.712063] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:00:20 turk kernel: [   16.716329] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:00:20 turk kernel: [   16.716491] Console: switching to colour frame buffer device 80x30
Jun 10 11:00:20 turk kernel: [   16.716501] fb0: VESA VGA frame buffer device
Jun 10 11:00:20 turk kernel: [   17.180278] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:00:20 turk kernel: [   17.329797] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:00:20 turk kernel: [   20.559233] init: failsafe main process (933) killed by TERM signal
Jun 10 11:00:20 turk kernel: [   20.579738] Bluetooth: Core ver 2.16
Jun 10 11:00:20 turk kernel: [   20.579754] NET: Registered protocol family 31
Jun 10 11:00:20 turk kernel: [   20.579755] Bluetooth: HCI device and connection manager initialized
Jun 10 11:00:20 turk kernel: [   20.579757] Bluetooth: HCI socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.579759] Bluetooth: L2CAP socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.579762] Bluetooth: SCO socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.581057] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:00:20 turk kernel: [   20.581059] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:00:20 turk NetworkManager[980]: <info> NetworkManager (version 0.9.4.0) is starting...
Jun 10 11:00:20 turk NetworkManager[980]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 10 11:00:20 turk kernel: [   20.650729] type=1400 audit(1339322420.740:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1000 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.651158] type=1400 audit(1339322420.740:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1000 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.651795] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:00:20 turk kernel: [   20.651798] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:00:20 turk kernel: [   20.651799] Bluetooth: RFCOMM ver 1.11
Jun 10 11:00:20 turk NetworkManager[980]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 10 11:00:20 turk NetworkManager[980]: <info> DNS: loaded plugin dnsmasq
Jun 10 11:00:20 turk avahi-daemon[1011]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully dropped root privileges.
Jun 10 11:00:20 turk avahi-daemon[1011]: avahi-daemon 0.6.30 starting up.
Jun 10 11:00:20 turk dbus[957]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully called chroot().
Jun 10 11:00:20 turk avahi-daemon[1011]: Successfully dropped remaining capabilities.
Jun 10 11:00:20 turk avahi-daemon[1011]: Loading service file /services/udisks.service.
Jun 10 11:00:20 turk polkitd[1015]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:00:20 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: init!
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:00:20 turk NetworkManager[980]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:00:20 turk NetworkManager[980]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: (39508784) ... get_connections.
Jun 10 11:00:20 turk NetworkManager[980]:    SCPlugin-Ifupdown: (39508784) ... get_connections (managed=false): return empty list.
Jun 10 11:00:20 turk NetworkManager[980]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:00:20 turk NetworkManager[980]: <info> modem-manager is now available
Jun 10 11:00:20 turk NetworkManager[980]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:00:20 turk NetworkManager[980]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <info> Networking is enabled by state file
Jun 10 11:00:20 turk NetworkManager[980]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): carrier is OFF
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): now managed
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): bringing up device.
Jun 10 11:00:20 turk kernel: [   20.727733] type=1400 audit(1339322420.816:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1041 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728015] type=1400 audit(1339322420.816:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728387] type=1400 audit(1339322420.820:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.728595] type=1400 audit(1339322420.820:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1042 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.730676] type=1400 audit(1339322420.820:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1045 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.730756] type=1400 audit(1339322420.820:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.731095] type=1400 audit(1339322420.820:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1045 comm="apparmor_parser"
Jun 10 11:00:20 turk kernel: [   20.731231] type=1400 audit(1339322420.820:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
Jun 10 11:00:20 turk anacron[1121]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:20 turk cron[1105]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:00:20 turk acpid: starting up with proc fs
Jun 10 11:00:20 turk cron[1133]: (CRON) STARTUP (fork ok)
Jun 10 11:00:20 turk acpid: 35 rules loaded
Jun 10 11:00:20 turk acpid: waiting for events: event logging is off
Jun 10 11:00:20 turk cron[1133]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:00:20 turk kernel: [   20.859531] r8169 0000:04:00.0: eth0: link down
Jun 10 11:00:20 turk kernel: [   20.859544] r8169 0000:04:00.0: eth0: link down
Jun 10 11:00:20 turk kernel: [   20.859889] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk avahi-daemon[1011]: Network interface enumeration completed.
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): preparing device.
Jun 10 11:00:20 turk NetworkManager[980]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:00:20 turk avahi-daemon[1011]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 10 11:00:20 turk avahi-daemon[1011]: Server startup complete. Host name is turk.local. Local service cookie is 85714046.
Jun 10 11:00:20 turk avahi-daemon[1011]: Service "turk" (/services/udisks.service) successfully established.
Jun 10 11:00:20 turk NetworkManager[980]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:00:20 turk kernel: [   20.860152] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:00:20 turk kernel: [   20.867930] vboxdrv: Found 4 processor cores.
Jun 10 11:00:20 turk kernel: [   20.868649] vboxdrv: fAsync=0 offMin=0x3f0 offMax=0x1670
Jun 10 11:00:20 turk kernel: [   20.868703] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:00:20 turk kernel: [   20.868704] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:00:20 turk kernel: [   20.874950] vboxpci: IOMMU not found (not registered)
Jun 10 11:00:21 turk acpid: client connected from 1237[0:0]
Jun 10 11:00:21 turk acpid: 1 client rule loaded
Jun 10 11:00:21 turk anacron[1121]: Normal exit (0 jobs run)
Jun 10 11:00:21 turk anacron[1265]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:21 turk anacron[1265]: Normal exit (0 jobs run)
Jun 10 11:00:21 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:00:21 turk udev-configure-printer: Failed to get parent
Jun 10 11:00:21 turk udev-configure-printer: add /module/lp
Jun 10 11:00:21 turk udev-configure-printer: Failed to get parent
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:00:22 turk kernel: [   22.442408] r8169 0000:04:00.0: eth0: link up
Jun 10 11:00:22 turk kernel: [   22.442720] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:00:22 turk NetworkManager[980]: <info> dhclient started with pid 1396
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:00:22 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:00:22 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:00:22 turk dhclient: All rights reserved.
Jun 10 11:00:22 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:00:22 turk dhclient: 
Jun 10 11:00:22 turk NetworkManager[980]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:00:22 turk NetworkManager[980]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:00:22 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:00:22 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:00:22 turk dhclient: Sending on   Socket/fallback
Jun 10 11:00:22 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:00:22 turk acpid: client connected from 1237[0:0]
Jun 10 11:00:22 turk acpid: 1 client rule loaded
Jun 10 11:00:22 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:00:22 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:00:22 turk dbus[957]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:00:22 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:00:22 turk accounts-daemon[1407]: started daemon version 0.6.15
Jun 10 11:00:23 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:00:23 turk dhclient: bound to 192.168.1.103 -- renewal in 33704 seconds.
Jun 10 11:00:23 turk NetworkManager[980]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:00:23 turk NetworkManager[980]: <info>   address 192.168.1.103
Jun 10 11:00:23 turk NetworkManager[980]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:00:23 turk NetworkManager[980]: <info>   gateway 192.168.1.1
Jun 10 11:00:23 turk NetworkManager[980]: <info>   nameserver '194.168.4.100'
Jun 10 11:00:23 turk NetworkManager[980]: <info>   nameserver '194.168.8.100'
Jun 10 11:00:23 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:00:23 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:00:23 turk avahi-daemon[1011]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.103.
Jun 10 11:00:23 turk avahi-daemon[1011]: New relevant interface eth0.IPv4 for mDNS.
Jun 10 11:00:23 turk avahi-daemon[1011]: Registering new address record for 192.168.1.103 on eth0.IPv4.
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:00:23 turk anacron[1617]: Anacron 2.3 started on 2012-06-10
Jun 10 11:00:23 turk anacron[1617]: Normal exit (0 jobs run)
Jun 10 11:00:23 turk avahi-daemon[1011]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::22cf:30ff:fe19:d13c.
Jun 10 11:00:23 turk avahi-daemon[1011]: New relevant interface eth0.IPv6 for mDNS.
Jun 10 11:00:23 turk avahi-daemon[1011]: Registering new address record for fe80::22cf:30ff:fe19:d13c on eth0.*.
Jun 10 11:00:23 turk dbus[957]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:00:23 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:00:24 turk dbus[957]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:00:24 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully called chroot.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully dropped privileges.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully limited resources.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Canary thread running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Watchdog thread running.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully made thread 1742 of process 1742 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:00:24 turk NetworkManager[980]: <info> DNS: starting dnsmasq...
Jun 10 11:00:24 turk NetworkManager[980]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:00:24 turk dnsmasq[1748]: started, version 2.59 cache disabled
Jun 10 11:00:24 turk dnsmasq[1748]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:00:24 turk dnsmasq[1748]: using nameserver 194.168.8.100#53
Jun 10 11:00:24 turk dnsmasq[1748]: using nameserver 194.168.4.100#53
Jun 10 11:00:24 turk NetworkManager[980]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:00:24 turk NetworkManager[980]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:00:24 turk NetworkManager[980]: <info> Activation (eth0) successful, device activated.
Jun 10 11:00:24 turk NetworkManager[980]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:00:24 turk dbus[957]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:00:24 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:00:24 turk rtkit-daemon[1744]: Successfully made thread 1829 of process 1742 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:00:24 turk rtkit-daemon[1744]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:00:25 turk rtkit-daemon[1744]: Successfully made thread 1830 of process 1742 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:00:25 turk rtkit-daemon[1744]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:00:26 turk dbus[957]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:00:26 turk dbus[957]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:00:33 turk ntpdate[1808]: step time server 91.189.94.4 offset 0.795759 sec
Jun 10 11:00:33 turk kernel: [   32.624006] eth0: no IPv6 routers present
Jun 10 11:00:42 turk goa[2108]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:00:43 turk NetworkManager[980]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:00:43 turk NetworkManager[980]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:01:04 turk kernel: [   63.206162] NVRM: Xid (0000:01:00): 32, Channel ID 00000005 intr 00040000
Jun 10 11:01:06 turk kernel: [   65.206369] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jun 10 11:01:08 turk kernel: [   67.206387] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jun 10 11:02:23 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:02:23 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1033" x-info="http://www.rsyslog.com"] start
Jun 10 11:02:23 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:02:23 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:02:23 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:02:23 turk dbus[990]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jun 10 11:02:23 turk polkitd[1064]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:02:23 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: init!
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:02:23 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:02:23 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:02:23 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:02:23 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:02:23 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:02:23 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:02:23 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:02:23 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:02:23 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:02:23 turk kernel: [    0.000000] DMI present.
Jun 10 11:02:23 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:02:23 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:02:23 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:02:23 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:02:23 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:02:23 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:02:23 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:02:23 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:02:23 turk kernel: [    0.000000]   3 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   4 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   5 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   6 disabled
Jun 10 11:02:23 turk kernel: [    0.000000]   7 disabled
Jun 10 11:02:23 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:02:23 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:02:23 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:02:23 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:02:23 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:02:23 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:02:23 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:02:23 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:02:23 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:02:23 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:02:23 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:02:23 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:02:23 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:02:23 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:02:23 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:02:23 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:02:23 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:02:23 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:02:23 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:02:23 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:02:23 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:02:23 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:02:23 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:02:23 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:02:23 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:02:23 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:02:23 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:02:23 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:02:23 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:02:23 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:02:23 turk NetworkManager[1032]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: (25504560) ... get_connections.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:02:23 turk NetworkManager[1032]:    SCPlugin-Ifupdown: (25504560) ... get_connections (managed=false): return empty list.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:02:23 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:02:23 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:02:23 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:02:23 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:02:23 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:02:23 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:02:23 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:02:23 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:02:23 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:02:23 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:02:23 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:02:23 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:02:23 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:02:23 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:02:23 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:02:23 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:02:23 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:02:23 turk kernel: [    0.000000] Node 0: aperture @ c4000000 size 32 MB
Jun 10 11:02:23 turk kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Jun 10 11:02:23 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:02:23 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:02:23 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:02:23 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:02:23 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:02:23 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:02:23 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:02:23 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:02:23 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:02:23 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:02:23 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:02:23 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:02:23 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:02:23 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:02:23 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:02:23 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:02:23 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:02:23 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:02:23 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:02:23 turk kernel: [    0.000000] Detected 3214.121 MHz processor.
Jun 10 11:02:23 turk kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.24 BogoMIPS (lpj=12856484)
Jun 10 11:02:23 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:02:23 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:02:23 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:02:23 turk kernel: [    0.004038] Yama: becoming mindful.
Jun 10 11:02:23 turk kernel: [    0.004343] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:02:23 turk kernel: [    0.008811] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:02:23 turk kernel: [    0.009413] Mount-cache hash table entries: 256
Jun 10 11:02:23 turk kernel: [    0.009513] Initializing cgroup subsys cpuacct
Jun 10 11:02:23 turk kernel: [    0.009518] Initializing cgroup subsys memory
Jun 10 11:02:23 turk kernel: [    0.009525] Initializing cgroup subsys devices
Jun 10 11:02:23 turk kernel: [    0.009527] Initializing cgroup subsys freezer
Jun 10 11:02:23 turk kernel: [    0.009528] Initializing cgroup subsys blkio
Jun 10 11:02:23 turk kernel: [    0.009533] Initializing cgroup subsys perf_event
Jun 10 11:02:23 turk kernel: [    0.009556] tseg: 0000000000
Jun 10 11:02:23 turk kernel: [    0.009565] CPU: Physical Processor ID: 0
Jun 10 11:02:23 turk kernel: [    0.009566] CPU: Processor Core ID: 0
Jun 10 11:02:23 turk kernel: [    0.009568] mce: CPU supports 6 MCE banks
Jun 10 11:02:23 turk kernel: [    0.010724] ACPI: Core revision 20110623
Jun 10 11:02:23 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:02:23 turk kernel: [    0.020381] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:02:23 turk kernel: [    0.063097] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:02:23 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:02:23 turk kernel: [    0.064003] ... version:                0
Jun 10 11:02:23 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:02:23 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:02:23 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:02:23 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:02:23 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:02:23 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:02:23 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:02:23 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.152083]  #2
Jun 10 11:02:23 turk kernel: [    0.152084] smpboot cpu 2: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.244079]  #3
Jun 10 11:02:23 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:02:23 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:02:23 turk kernel: [    0.336047] Brought up 4 CPUs
Jun 10 11:02:23 turk kernel: [    0.336049] Total of 4 processors activated (25714.02 BogoMIPS).
Jun 10 11:02:23 turk kernel: [    0.340158] devtmpfs: initialized
Jun 10 11:02:23 turk kernel: [    0.341186] EVM: security.selinux
Jun 10 11:02:23 turk kernel: [    0.341187] EVM: security.SMACK64
Jun 10 11:02:23 turk kernel: [    0.341188] EVM: security.capability
Jun 10 11:02:23 turk kernel: [    0.341284] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:02:23 turk kernel: [    0.341284] print_constraints: dummy: 
Jun 10 11:02:23 turk kernel: [    0.341284] RTC time: 10:02:02, date: 06/10/12
Jun 10 11:02:23 turk kernel: [    0.341284] NET: Registered protocol family 16
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: io port [1000, ffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] TOM: 00000000d0000000 aka 3328M
Jun 10 11:02:23 turk kernel: [    0.341284] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:02:23 turk kernel: [    0.341284] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:02:23 turk kernel: [    0.341284] TOM2: 0000000130000000 aka 4864M
Jun 10 11:02:23 turk kernel: [    0.341284] bus: [00, 07] on node 0 link 0
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:02:23 turk kernel: [    0.341284] Extended Config Space enabled on 1 nodes
Jun 10 11:02:23 turk kernel: [    0.341284] ACPI: bus type pci registered
Jun 10 11:02:23 turk kernel: [    0.341284] Trying to unpack rootfs image as initramfs...
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: not using MMCONFIG
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: Using configuration type 1 for base access
Jun 10 11:02:23 turk kernel: [    0.341284] PCI: Using configuration type 1 for extended access
Jun 10 11:02:23 turk kernel: [    0.341456] bio: create slab <bio-0> at 0
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Module Device)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Processor Device)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:02:23 turk kernel: [    0.341456] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:02:23 turk kernel: [    0.344428] ACPI: EC: Look up EC in DSDT
Jun 10 11:02:23 turk kernel: [    0.380091] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:02:23 turk kernel: [    0.548577] ACPI: Interpreter enabled
Jun 10 11:02:23 turk kernel: [    0.548582] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:02:23 turk kernel: [    0.548599] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:02:23 turk kernel: [    0.548620] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:02:23 turk kernel: [    0.549993] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:02:23 turk kernel: [    0.556884] Freeing initrd memory: 13844k freed
Jun 10 11:02:23 turk kernel: [    0.642053] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:02:23 turk kernel: [    0.642150] ACPI: No dock devices found.
Jun 10 11:02:23 turk kernel: [    0.642151] HEST: Table not found.
Jun 10 11:02:23 turk kernel: [    0.642154] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:02:23 turk kernel: [    0.642210] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:02:23 turk kernel: [    0.642325] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.642327] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.642329] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.642331] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.642332] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.642334] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.642346] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.642388] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642417] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642419] pci 0000:00:02.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642434] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642462] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642464] pci 0000:00:07.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642475] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642503] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642505] pci 0000:00:09.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642516] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.642543] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.642545] pci 0000:00:0a.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642569] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.642587] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:02:23 turk kernel: [    0.642595] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:02:23 turk kernel: [    0.642603] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:02:23 turk kernel: [    0.642612] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:02:23 turk kernel: [    0.642620] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:02:23 turk kernel: [    0.642628] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:02:23 turk kernel: [    0.642646] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:02:23 turk kernel: [    0.642697] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642708] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:02:23 turk kernel: [    0.642770] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642786] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:02:23 turk kernel: [    0.642857] pci 0000:00:12.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.642858] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.642861] pci 0000:00:12.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.642879] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642890] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:02:23 turk kernel: [    0.642951] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.642967] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:02:23 turk kernel: [    0.643037] pci 0000:00:13.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.643039] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.643042] pci 0000:00:13.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643059] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:02:23 turk kernel: [    0.643125] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.643139] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:02:23 turk kernel: [    0.643147] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:02:23 turk kernel: [    0.643155] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:02:23 turk kernel: [    0.643163] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:02:23 turk kernel: [    0.643172] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:02:23 turk kernel: [    0.643222] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:02:23 turk kernel: [    0.643240] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:02:23 turk kernel: [    0.643297] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.643300] pci 0000:00:14.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643311] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:02:23 turk kernel: [    0.643377] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:02:23 turk kernel: [    0.643412] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643424] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:02:23 turk kernel: [    0.643482] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643493] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:02:23 turk kernel: [    0.643554] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:02:23 turk kernel: [    0.643570] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:02:23 turk kernel: [    0.643641] pci 0000:00:16.2: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.643643] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.643646] pci 0000:00:16.2: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.643662] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643674] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643684] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643694] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643707] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:02:23 turk kernel: [    0.643751] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:02:23 turk kernel: [    0.643759] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:02:23 turk kernel: [    0.643769] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.643778] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.643785] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:02:23 turk kernel: [    0.643791] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:02:23 turk kernel: [    0.643842] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:02:23 turk kernel: [    0.643850] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:02:23 turk kernel: [    0.648059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:02:23 turk kernel: [    0.648063] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.648066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.648069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.648117] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:02:23 turk kernel: [    0.648146] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:02:23 turk kernel: [    0.648161] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:02:23 turk kernel: [    0.648286] pci 0000:02:00.0: supports D2
Jun 10 11:02:23 turk kernel: [    0.648287] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.648293] pci 0000:02:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.656063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:02:23 turk kernel: [    0.656067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.656069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.656116] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:02:23 turk kernel: [    0.656137] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:02:23 turk kernel: [    0.656156] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:02:23 turk kernel: [    0.656170] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:02:23 turk kernel: [    0.656185] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:02:23 turk kernel: [    0.656199] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:02:23 turk kernel: [    0.656227] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:02:23 turk kernel: [    0.656301] pci 0000:03:00.0: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.656303] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:02:23 turk kernel: [    0.656308] pci 0000:03:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.664061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:02:23 turk kernel: [    0.664065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.664067] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.664102] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:02:23 turk kernel: [    0.664114] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:02:23 turk kernel: [    0.664133] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.664145] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.664197] pci 0000:04:00.0: supports D1 D2
Jun 10 11:02:23 turk kernel: [    0.664198] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:02:23 turk kernel: [    0.664202] pci 0000:04:00.0: PME# disabled
Jun 10 11:02:23 turk kernel: [    0.672059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:02:23 turk kernel: [    0.672063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.672066] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.672121] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672128] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672130] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672132] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672134] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672135] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672137] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:02:23 turk kernel: [    0.672151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:02:23 turk kernel: [    0.672245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:02:23 turk kernel: [    0.672266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:02:23 turk kernel: [    0.672283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:02:23 turk kernel: [    0.672302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:02:23 turk kernel: [    0.672321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:02:23 turk kernel: [    0.672356]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:02:23 turk kernel: [    0.672358]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:02:23 turk kernel: [    0.672360] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:02:23 turk kernel: [    0.675416] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675460] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675503] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675545] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:02:23 turk kernel: [    0.675577] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675628] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675652] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: loaded
Jun 10 11:02:23 turk kernel: [    0.675727] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:02:23 turk kernel: [    0.675727] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:02:23 turk kernel: [    0.675727] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:02:23 turk kernel: [    0.675727] SCSI subsystem initialized
Jun 10 11:02:23 turk kernel: [    0.675727] libata version 3.00 loaded.
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new interface driver usbfs
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new interface driver hub
Jun 10 11:02:23 turk kernel: [    0.675727] usbcore: registered new device driver usb
Jun 10 11:02:23 turk kernel: [    0.676060] PCI: Using ACPI for IRQ routing
Jun 10 11:02:23 turk kernel: [    0.683442] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:02:23 turk kernel: [    0.683509] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:02:23 turk kernel: [    0.683511] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:02:23 turk kernel: [    0.683580] NetLabel: Initializing
Jun 10 11:02:23 turk kernel: [    0.683581] NetLabel:  domain hash size = 128
Jun 10 11:02:23 turk kernel: [    0.683582] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:02:23 turk kernel: [    0.683590] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:02:23 turk kernel: [    0.683618] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:02:23 turk kernel: [    0.683618] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:02:23 turk kernel: [    0.685067] Switching to clocksource hpet
Jun 10 11:02:23 turk kernel: [    0.688702] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:02:23 turk kernel: [    0.688717] pnp: PnP ACPI init
Jun 10 11:02:23 turk kernel: [    0.688727] ACPI: bus type pnp registered
Jun 10 11:02:23 turk kernel: [    0.688802] pnp 00:00: [bus 00-ff]
Jun 10 11:02:23 turk kernel: [    0.688804] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:02:23 turk kernel: [    0.688806] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:02:23 turk kernel: [    0.688808] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:02:23 turk kernel: [    0.688809] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:02:23 turk kernel: [    0.688811] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:02:23 turk kernel: [    0.688812] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:02:23 turk kernel: [    0.688814] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:02:23 turk kernel: [    0.688850] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:02:23 turk kernel: [    0.688904] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.688905] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.688938] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.689432] pnp 00:02: [dma 4]
Jun 10 11:02:23 turk kernel: [    0.689433] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:02:23 turk kernel: [    0.689435] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:02:23 turk kernel: [    0.689436] pnp 00:02: [io  0x0087]
Jun 10 11:02:23 turk kernel: [    0.689437] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:02:23 turk kernel: [    0.689439] pnp 00:02: [io  0x008f]
Jun 10 11:02:23 turk kernel: [    0.689440] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:02:23 turk kernel: [    0.689461] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:02:23 turk kernel: [    0.689467] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:02:23 turk kernel: [    0.689475] pnp 00:03: [irq 8]
Jun 10 11:02:23 turk kernel: [    0.689496] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:02:23 turk kernel: [    0.689501] pnp 00:04: [io  0x0061]
Jun 10 11:02:23 turk kernel: [    0.689522] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:02:23 turk kernel: [    0.689527] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:02:23 turk kernel: [    0.689531] pnp 00:05: [irq 13]
Jun 10 11:02:23 turk kernel: [    0.689550] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:02:23 turk kernel: [    0.689997] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:02:23 turk kernel: [    0.690001] pnp 00:06: [irq 7]
Jun 10 11:02:23 turk kernel: [    0.690002] pnp 00:06: [dma 0 disabled]
Jun 10 11:02:23 turk kernel: [    0.690167] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:02:23 turk kernel: [    0.690194] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:02:23 turk kernel: [    0.690217] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:02:23 turk kernel: [    0.690540] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:02:23 turk kernel: [    0.690544] pnp 00:08: [irq 4]
Jun 10 11:02:23 turk kernel: [    0.690545] pnp 00:08: [dma 0 disabled]
Jun 10 11:02:23 turk kernel: [    0.690608] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:02:23 turk kernel: [    0.690654] pnp 00:09: [io  0x0060]
Jun 10 11:02:23 turk kernel: [    0.690655] pnp 00:09: [io  0x0064]
Jun 10 11:02:23 turk kernel: [    0.690658] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:02:23 turk kernel: [    0.690659] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:02:23 turk kernel: [    0.690696] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.690698] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690700] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.690791] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:02:23 turk kernel: [    0.690792] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:02:23 turk kernel: [    0.690793] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:02:23 turk kernel: [    0.690795] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:02:23 turk kernel: [    0.690796] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:02:23 turk kernel: [    0.690797] pnp 00:0a: [io  0x0080]
Jun 10 11:02:23 turk kernel: [    0.690798] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:02:23 turk kernel: [    0.690799] pnp 00:0a: [io  0x0088]
Jun 10 11:02:23 turk kernel: [    0.690801] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:02:23 turk kernel: [    0.690802] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:02:23 turk kernel: [    0.690803] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:02:23 turk kernel: [    0.690804] pnp 00:0a: [io  0x00b1]
Jun 10 11:02:23 turk kernel: [    0.690806] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:02:23 turk kernel: [    0.690807] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:02:23 turk kernel: [    0.690808] pnp 00:0a: [io  0x040b]
Jun 10 11:02:23 turk kernel: [    0.690809] pnp 00:0a: [io  0x04d6]
Jun 10 11:02:23 turk kernel: [    0.690811] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:02:23 turk kernel: [    0.690812] pnp 00:0a: [io  0x0c14]
Jun 10 11:02:23 turk kernel: [    0.690813] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:02:23 turk kernel: [    0.690814] pnp 00:0a: [io  0x0c52]
Jun 10 11:02:23 turk kernel: [    0.690815] pnp 00:0a: [io  0x0c6c]
Jun 10 11:02:23 turk kernel: [    0.690816] pnp 00:0a: [io  0x0c6f]
Jun 10 11:02:23 turk kernel: [    0.690818] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:02:23 turk kernel: [    0.690819] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:02:23 turk kernel: [    0.690820] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:02:23 turk kernel: [    0.690821] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:02:23 turk kernel: [    0.690823] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:02:23 turk kernel: [    0.690824] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:02:23 turk kernel: [    0.690825] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:02:23 turk kernel: [    0.690827] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.690828] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:02:23 turk kernel: [    0.690829] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:02:23 turk kernel: [    0.690831] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:02:23 turk kernel: [    0.690832] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:02:23 turk kernel: [    0.690833] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:02:23 turk kernel: [    0.690834] pnp 00:0a: [io  0x0060]
Jun 10 11:02:23 turk kernel: [    0.690836] pnp 00:0a: [io  0x0064]
Jun 10 11:02:23 turk kernel: [    0.690837] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:02:23 turk kernel: [    0.690838] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:02:23 turk kernel: [    0.690840] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:02:23 turk kernel: [    0.690841] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:02:23 turk kernel: [    0.690844] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.690919] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690921] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690923] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690925] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690926] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690928] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690930] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690931] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690933] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690935] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690936] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690938] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690940] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690942] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690944] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690945] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690949] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690950] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690952] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690954] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690956] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690958] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690960] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690962] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690964] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.690966] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691063] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:02:23 turk kernel: [    0.691065] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:02:23 turk kernel: [    0.691066] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:02:23 turk kernel: [    0.691068] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:02:23 turk kernel: [    0.691069] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:02:23 turk kernel: [    0.691104] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691106] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691108] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691110] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691112] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691140] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:02:23 turk kernel: [    0.691175] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:02:23 turk kernel: [    0.691177] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:02:23 turk kernel: [    0.691244] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:02:23 turk kernel: [    0.691245] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:02:23 turk kernel: [    0.691247] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:02:23 turk kernel: [    0.691248] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:02:23 turk kernel: [    0.691250] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:02:23 turk kernel: [    0.691285] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691287] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691288] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691290] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691292] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:02:23 turk kernel: [    0.691294] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:02:23 turk kernel: [    0.691359] pnp: PnP ACPI: found 14 devices
Jun 10 11:02:23 turk kernel: [    0.691361] ACPI: ACPI bus type pnp unregistered
Jun 10 11:02:23 turk kernel: [    0.697740] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:02:23 turk kernel: [    0.697759] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:02:23 turk kernel: [    0.697761] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.697763] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.697766] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697769] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:02:23 turk kernel: [    0.697770] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.697773] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.697776] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:02:23 turk kernel: [    0.697778] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.697780] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697783] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:02:23 turk kernel: [    0.697785] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.697788] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697791] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:02:23 turk kernel: [    0.697809] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    0.697812] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697818] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    0.697821] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697826] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    0.697828] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697831] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    0.697833] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    0.697839] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.697840] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.697842] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.697844] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.697845] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.697847] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697848] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:02:23 turk kernel: [    0.697850] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:02:23 turk kernel: [    0.697852] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697854] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:02:23 turk kernel: [    0.697856] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:02:23 turk kernel: [    0.697857] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:02:23 turk kernel: [    0.697859] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697861] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:02:23 turk kernel: [    0.697863] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:02:23 turk kernel: [    0.697865] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:02:23 turk kernel: [    0.697866] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:02:23 turk kernel: [    0.697868] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:02:23 turk kernel: [    0.697870] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:02:23 turk kernel: [    0.697872] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:02:23 turk kernel: [    0.697873] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:02:23 turk kernel: [    0.697902] NET: Registered protocol family 2
Jun 10 11:02:23 turk kernel: [    0.698010] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:02:23 turk kernel: [    0.698908] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:02:23 turk kernel: [    0.701339] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:02:23 turk kernel: [    0.701646] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:02:23 turk kernel: [    0.701648] TCP reno registered
Jun 10 11:02:23 turk kernel: [    0.701655] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:02:23 turk kernel: [    0.701683] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:02:23 turk kernel: [    0.701769] NET: Registered protocol family 1
Jun 10 11:02:23 turk kernel: [    0.701798] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.508037] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.508048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.508089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.508095] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.588040] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.588050] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.588090] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.588104] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.668034] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:02:23 turk kernel: [    1.668043] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    1.748042] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    1.748052] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    1.748091] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:02:23 turk kernel: [    1.748110] pci 0000:01:00.0: Boot video device
Jun 10 11:02:23 turk kernel: [    1.748127] PCI: CLS 64 bytes, default 64
Jun 10 11:02:23 turk kernel: [    1.749389] PCI-DMA: Disabling AGP.
Jun 10 11:02:23 turk kernel: [    1.749461] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:02:23 turk kernel: [    1.749463] PCI-DMA: using GART IOMMU.
Jun 10 11:02:23 turk kernel: [    1.749465] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:02:23 turk kernel: [    1.752912] IBS: LVT offset 1 assigned
Jun 10 11:02:23 turk kernel: [    1.752928] perf: AMD IBS detected (0x0000001f)
Jun 10 11:02:23 turk kernel: [    1.753040] audit: initializing netlink socket (disabled)
Jun 10 11:02:23 turk kernel: [    1.753054] type=2000 audit(1339322523.748:1): initialized
Jun 10 11:02:23 turk kernel: [    1.777115] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:02:23 turk kernel: [    1.796097] VFS: Disk quotas dquot_6.5.2
Jun 10 11:02:23 turk kernel: [    1.796140] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:02:23 turk kernel: [    1.796561] fuse init (API version 7.17)
Jun 10 11:02:23 turk kernel: [    1.796626] msgmni has been set to 7901
Jun 10 11:02:23 turk kernel: [    1.796951] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:02:23 turk kernel: [    1.796978] io scheduler noop registered
Jun 10 11:02:23 turk kernel: [    1.796979] io scheduler deadline registered
Jun 10 11:02:23 turk kernel: [    1.797000] io scheduler cfq registered (default)
Jun 10 11:02:23 turk kernel: [    1.797118] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797147] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797227] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797245] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797310] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797328] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797389] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    1.797406] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    1.797459] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:02:23 turk kernel: [    1.797475] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:02:23 turk kernel: [    1.797567] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:02:23 turk kernel: [    1.797571] ACPI: Power Button [PWRB]
Jun 10 11:02:23 turk kernel: [    1.797599] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:02:23 turk kernel: [    1.797601] ACPI: Power Button [PWRF]
Jun 10 11:02:23 turk kernel: [    1.981030] ERST: Table is not found!
Jun 10 11:02:23 turk kernel: [    1.981032] GHES: HEST is not enabled!
Jun 10 11:02:23 turk kernel: [    1.981117] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:02:23 turk kernel: [    2.001529] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:02:23 turk kernel: [    2.048779] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:02:23 turk kernel: [    2.096216] Linux agpgart interface v0.103
Jun 10 11:02:23 turk kernel: [    2.097260] brd: module loaded
Jun 10 11:02:23 turk kernel: [    2.097796] loop: module loaded
Jun 10 11:02:23 turk kernel: [    2.097935] ahci 0000:00:11.0: version 3.0
Jun 10 11:02:23 turk kernel: [    2.097943] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    2.097990] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    2.098059] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:02:23 turk kernel: [    2.098062] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:02:23 turk kernel: [    2.098464] scsi0 : ahci
Jun 10 11:02:23 turk kernel: [    2.098526] scsi1 : ahci
Jun 10 11:02:23 turk kernel: [    2.098576] scsi2 : ahci
Jun 10 11:02:23 turk kernel: [    2.098625] scsi3 : ahci
Jun 10 11:02:23 turk kernel: [    2.098690] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:02:23 turk kernel: [    2.098693] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:02:23 turk kernel: [    2.098695] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:02:23 turk kernel: [    2.098698] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:02:23 turk kernel: [    2.098824] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.098842] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.098908] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.098927] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.098937] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:02:23 turk kernel: [    2.099227] Fixed MDIO Bus: probed
Jun 10 11:02:23 turk kernel: [    2.099241] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:02:23 turk kernel: [    2.099242] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:02:23 turk kernel: [    2.099278] PPP generic driver version 2.4.2
Jun 10 11:02:23 turk kernel: [    2.099346] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:02:23 turk kernel: [    2.099385] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.099396] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.099432] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:02:23 turk kernel: [    2.099439] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.099452] QUIRK: Enable AMD PLL fix
Jun 10 11:02:23 turk kernel: [    2.099462] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.099478] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:02:23 turk kernel: [    2.108037] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.108135] hub 1-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.108138] hub 1-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.108243] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.108255] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.108287] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:02:23 turk kernel: [    2.108293] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.108309] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.108320] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:02:23 turk kernel: [    2.120042] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.120134] hub 2-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.120137] hub 2-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.120240] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.120251] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.120283] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:02:23 turk kernel: [    2.120289] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:02:23 turk kernel: [    2.120305] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:02:23 turk kernel: [    2.120316] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:02:23 turk kernel: [    2.132041] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:02:23 turk kernel: [    2.132131] hub 3-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.132134] hub 3-0:1.0: 4 ports detected
Jun 10 11:02:23 turk kernel: [    2.132197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:02:23 turk kernel: [    2.132249] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.132261] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.132293] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:02:23 turk kernel: [    2.132315] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:02:23 turk kernel: [    2.192104] hub 4-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.192109] hub 4-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.192214] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.192225] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.192263] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:02:23 turk kernel: [    2.192275] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:02:23 turk kernel: [    2.252101] hub 5-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.252106] hub 5-0:1.0: 5 ports detected
Jun 10 11:02:23 turk kernel: [    2.252209] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.252221] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.252253] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:02:23 turk kernel: [    2.252266] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:02:23 turk kernel: [    2.312123] hub 6-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.312128] hub 6-0:1.0: 2 ports detected
Jun 10 11:02:23 turk kernel: [    2.312231] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.312243] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:02:23 turk kernel: [    2.312275] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:02:23 turk kernel: [    2.312287] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:02:23 turk kernel: [    2.372134] hub 7-0:1.0: USB hub found
Jun 10 11:02:23 turk kernel: [    2.372140] hub 7-0:1.0: 4 ports detected
Jun 10 11:02:23 turk kernel: [    2.372201] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:02:23 turk kernel: [    2.372249] usbcore: registered new interface driver libusual
Jun 10 11:02:23 turk kernel: [    2.372273] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:02:23 turk kernel: [    2.372626] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:02:23 turk kernel: [    2.372632] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:02:23 turk kernel: [    2.372741] mousedev: PS/2 mouse device common for all mice
Jun 10 11:02:23 turk kernel: [    2.372854] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:02:23 turk kernel: [    2.372933] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:02:23 turk kernel: [    2.372956] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:02:23 turk kernel: [    2.373008] device-mapper: uevent: version 1.0.3
Jun 10 11:02:23 turk kernel: [    2.373055] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:02:23 turk kernel: [    2.373060] cpuidle: using governor ladder
Jun 10 11:02:23 turk kernel: [    2.373061] cpuidle: using governor menu
Jun 10 11:02:23 turk kernel: [    2.373062] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:02:23 turk kernel: [    2.373206] TCP cubic registered
Jun 10 11:02:23 turk kernel: [    2.373271] NET: Registered protocol family 10
Jun 10 11:02:23 turk kernel: [    2.373575] NET: Registered protocol family 17
Jun 10 11:02:23 turk kernel: [    2.373585] Registering the dns_resolver key type
Jun 10 11:02:23 turk kernel: [    2.373693] PM: Hibernation image not present or could not be loaded.
Jun 10 11:02:23 turk kernel: [    2.373700] registered taskstats version 1
Jun 10 11:02:23 turk kernel: [    2.387994]   Magic number: 0:770:21
Jun 10 11:02:23 turk kernel: [    2.388061] pcieport 0000:00:09.0: hash matches
Jun 10 11:02:23 turk kernel: [    2.388106] rtc_cmos 00:03: setting system clock to 2012-06-10 10:02:04 UTC (1339322524)
Jun 10 11:02:23 turk kernel: [    2.388120] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:02:23 turk kernel: [    2.388146] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:02:23 turk kernel: [    2.388148] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:02:23 turk kernel: [    2.388149] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:02:23 turk kernel: [    2.388150] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:02:23 turk kernel: [    2.388587] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:02:23 turk kernel: [    2.388589] EDD information not available.
Jun 10 11:02:23 turk kernel: [    2.416071] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.416102] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.588039] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.588063] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:02:23 turk kernel: [    2.589162] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:02:23 turk kernel: [    2.589164] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:02:23 turk kernel: [    2.589673] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:02:23 turk kernel: [    2.590428] ata1.00: configured for UDMA/133
Jun 10 11:02:23 turk kernel: [    2.590566] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:02:23 turk kernel: [    2.590694] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:02:23 turk kernel: [    2.590703] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:02:23 turk kernel: [    2.590799] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:02:23 turk kernel: [    2.590802] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:02:23 turk kernel: [    2.590836] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:02:23 turk kernel: [    2.591567] ata2.00: configured for UDMA/100
Jun 10 11:02:23 turk kernel: [    2.593395] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:02:23 turk kernel: [    2.595448] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:02:23 turk kernel: [    2.595451] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:02:23 turk kernel: [    2.595542] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:02:23 turk kernel: [    2.595608] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:02:23 turk kernel: [    2.651185]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:02:23 turk kernel: [    2.651669] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:02:23 turk kernel: [    2.652744] Freeing unused kernel memory: 920k freed
Jun 10 11:02:23 turk kernel: [    2.652907] Write protecting the kernel read-only data: 12288k
Jun 10 11:02:23 turk kernel: [    2.656850] Freeing unused kernel memory: 1608k freed
Jun 10 11:02:23 turk kernel: [    2.660021] Freeing unused kernel memory: 1196k freed
Jun 10 11:02:23 turk kernel: [    2.684061] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:02:23 turk kernel: [    2.691102] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:02:23 turk kernel: [    2.691120] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [    2.691147] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.691186] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:02:23 turk kernel: [    2.691505] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc9000065e000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:02:23 turk kernel: [    2.691507] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:02:23 turk kernel: [    2.691659] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:02:23 turk kernel: [    2.691670] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:02:23 turk kernel: [    2.691714] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    2.692961] scsi4 : pata_via
Jun 10 11:02:23 turk kernel: [    2.693037] scsi5 : pata_via
Jun 10 11:02:23 turk kernel: [    2.693147] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:02:23 turk kernel: [    2.693149] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:02:23 turk kernel: [    2.706659] scsi6 : pata_atiixp
Jun 10 11:02:23 turk kernel: [    2.706769] scsi7 : pata_atiixp
Jun 10 11:02:23 turk kernel: [    2.707184] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:02:23 turk kernel: [    2.707186] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:02:23 turk kernel: [    2.752062] Refined TSC clocksource calibration: 3214.273 MHz.
Jun 10 11:02:23 turk kernel: [    2.752066] Switching to clocksource tsc
Jun 10 11:02:23 turk kernel: [    3.016708] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [    3.016716] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [    3.026205] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:02:23 turk kernel: [    3.026291] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:02:23 turk kernel: [    3.026302] usbcore: registered new interface driver usbhid
Jun 10 11:02:23 turk kernel: [    3.026303] usbhid: USB HID core driver
Jun 10 11:02:23 turk kernel: [    3.080083] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:02:23 turk kernel: [    3.116032] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:02:23 turk kernel: [    3.205360] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Jun 10 11:02:23 turk kernel: [    3.205363] EXT4-fs (sda7): write access will be enabled during recovery
Jun 10 11:02:23 turk kernel: [    3.298218] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:02:23 turk kernel: [    3.298288] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:02:23 turk kernel: [    3.317125] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:02:23 turk kernel: [    3.317188] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:02:23 turk kernel: [    3.339975] EXT4-fs (sda7): orphan cleanup on readonly fs
Jun 10 11:02:23 turk kernel: [    3.339980] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523389
Jun 10 11:02:23 turk kernel: [    3.339997] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523379
Jun 10 11:02:23 turk kernel: [    3.340016] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523376
Jun 10 11:02:23 turk kernel: [    3.340038] EXT4-fs (sda7): 3 orphan inodes deleted
Jun 10 11:02:23 turk kernel: [    3.340039] EXT4-fs (sda7): recovery complete
Jun 10 11:02:23 turk kernel: [    3.580080] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:02:23 turk kernel: [    3.617271] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:02:23 turk kernel: [   14.736309] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk kernel: [   14.777379] lp: driver loaded but no devices found
Jun 10 11:02:23 turk kernel: [   14.780178] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:02:23 turk kernel: [   14.780180] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:02:23 turk kernel: [   14.780548] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:02:23 turk kernel: [   14.780641] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:02:23 turk kernel: [   14.784784] wmi: Mapper loaded
Jun 10 11:02:23 turk kernel: [   14.796938] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:02:23 turk kernel: [   14.837746] MCE: In-kernel MCE decoding enabled.
Jun 10 11:02:23 turk kernel: [   14.839413] EDAC MC: Ver: 2.1.0
Jun 10 11:02:23 turk kernel: [   14.839904] AMD64 EDAC driver v3.4.0
Jun 10 11:02:23 turk kernel: [   14.841671] type=1400 audit(1339322536.950:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.842029] type=1400 audit(1339322536.950:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.842235] type=1400 audit(1339322536.950:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=616 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   14.843336] EDAC amd64: DRAM ECC disabled.
Jun 10 11:02:23 turk kernel: [   14.843343] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:02:23 turk kernel: [   14.843344]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:02:23 turk kernel: [   14.843345]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:02:23 turk kernel: [   14.853757] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:02:23 turk kernel: [   14.853807] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:02:23 turk kernel: [   14.882598] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:02:23 turk kernel: [   14.912916] ppdev: user-space parallel port driver
Jun 10 11:02:23 turk kernel: [   14.927819] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:02:23 turk kernel: [   14.927932] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:02:23 turk kernel: [   14.927984] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:02:23 turk kernel: [   14.928037] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:02:23 turk kernel: [   14.928144] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:02:23 turk kernel: [   14.928188] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:02:23 turk kernel: [   14.928230] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:02:23 turk kernel: [   14.928278] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:02:23 turk kernel: [   14.928498] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:02:23 turk kernel: [   14.928501] hda_intel: Disabling MSI
Jun 10 11:02:23 turk kernel: [   14.928531] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [   14.948165] lp0: using parport0 (interrupt-driven).
Jun 10 11:02:23 turk kernel: [   15.612793] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:02:23 turk kernel: [   15.612796] Disabling lock debugging due to kernel taint
Jun 10 11:02:23 turk kernel: [   15.764026] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.788030] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.812030] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.836032] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:02:23 turk kernel: [   15.836103] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:02:23 turk kernel: [   15.836166] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:02:23 turk kernel: [   15.836213] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:02:23 turk kernel: [   15.836259] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:02:23 turk kernel: [   15.836727] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:02:23 turk kernel: [   15.836734] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:02:23 turk kernel: [   15.836737] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:02:23 turk kernel: [   15.836963] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:02:23 turk kernel: [   15.947302] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:02:23 turk kernel: [   15.947304] vesafb: scrolling: redraw
Jun 10 11:02:23 turk kernel: [   15.947306] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:02:23 turk kernel: [   15.951566] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:02:23 turk kernel: [   15.951734] Console: switching to colour frame buffer device 80x30
Jun 10 11:02:23 turk kernel: [   15.951745] fb0: VESA VGA frame buffer device
Jun 10 11:02:23 turk kernel: [   16.817792] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:02:23 turk kernel: [   18.470683] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:02:23 turk kernel: [   20.797569] init: failsafe main process (971) killed by TERM signal
Jun 10 11:02:23 turk kernel: [   21.049050] Bluetooth: Core ver 2.16
Jun 10 11:02:23 turk kernel: [   21.049069] NET: Registered protocol family 31
Jun 10 11:02:23 turk kernel: [   21.049071] Bluetooth: HCI device and connection manager initialized
Jun 10 11:02:23 turk kernel: [   21.049073] Bluetooth: HCI socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.049074] Bluetooth: L2CAP socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.049078] Bluetooth: SCO socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.050846] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:02:23 turk kernel: [   21.050848] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:02:23 turk kernel: [   21.062695] type=1400 audit(1339322543.170:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1046 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.063205] type=1400 audit(1339322543.170:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1046 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.066853] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:02:23 turk kernel: [   21.066857] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:02:23 turk kernel: [   21.066859] Bluetooth: RFCOMM ver 1.11
Jun 10 11:02:23 turk kernel: [   21.073963] type=1400 audit(1339322543.182:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1078 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074048] type=1400 audit(1339322543.182:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074416] type=1400 audit(1339322543.182:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.074609] type=1400 audit(1339322543.182:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1079 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076227] type=1400 audit(1339322543.186:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1082 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076646] type=1400 audit(1339322543.186:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1082 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.076900] type=1400 audit(1339322543.186:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1083 comm="apparmor_parser"
Jun 10 11:02:23 turk kernel: [   21.077332] type=1400 audit(1339322543.186:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1083 comm="apparmor_parser"
Jun 10 11:02:23 turk NetworkManager[1032]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:02:23 turk NetworkManager[1032]: <info> modem-manager is now available
Jun 10 11:02:23 turk NetworkManager[1032]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Networking is enabled by state file
Jun 10 11:02:23 turk NetworkManager[1032]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): carrier is OFF
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): now managed
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): bringing up device.
Jun 10 11:02:23 turk cron[1146]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:02:23 turk anacron[1170]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:23 turk acpid: starting up with proc fs
Jun 10 11:02:23 turk acpid: 35 rules loaded
Jun 10 11:02:23 turk acpid: waiting for events: event logging is off
Jun 10 11:02:23 turk cron[1173]: (CRON) STARTUP (fork ok)
Jun 10 11:02:23 turk cron[1173]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:02:23 turk kernel: [   21.276401] vboxdrv: Found 4 processor cores.
Jun 10 11:02:23 turk kernel: [   21.276842] vboxdrv: fAsync=0 offMin=0x50e offMax=0x1522
Jun 10 11:02:23 turk kernel: [   21.276891] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:02:23 turk kernel: [   21.276893] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:02:23 turk kernel: [   21.283467] vboxpci: IOMMU not found (not registered)
Jun 10 11:02:23 turk kernel: [   21.295509] r8169 0000:04:00.0: eth0: link down
Jun 10 11:02:23 turk kernel: [   21.295522] r8169 0000:04:00.0: eth0: link down
Jun 10 11:02:23 turk kernel: [   21.295855] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): preparing device.
Jun 10 11:02:23 turk NetworkManager[1032]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:02:23 turk NetworkManager[1032]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:02:23 turk anacron[1170]: Normal exit (0 jobs run)
Jun 10 11:02:23 turk kernel: [   21.296185] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:02:23 turk acpid: client connected from 1268[0:0]
Jun 10 11:02:23 turk acpid: 1 client rule loaded
Jun 10 11:02:23 turk anacron[1306]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:23 turk anacron[1306]: Normal exit (0 jobs run)
Jun 10 11:02:23 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:02:23 turk udev-configure-printer: Failed to get parent
Jun 10 11:02:23 turk udev-configure-printer: add /module/lp
Jun 10 11:02:23 turk udev-configure-printer: Failed to get parent
Jun 10 11:02:25 turk acpid: client connected from 1268[0:0]
Jun 10 11:02:25 turk acpid: 1 client rule loaded
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:02:25 turk kernel: [   22.986340] r8169 0000:04:00.0: eth0: link up
Jun 10 11:02:25 turk kernel: [   22.986645] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:02:25 turk NetworkManager[1032]: <info> dhclient started with pid 1435
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:02:25 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:02:25 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:02:25 turk dhclient: All rights reserved.
Jun 10 11:02:25 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:02:25 turk dhclient: 
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:02:25 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:02:25 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:02:25 turk dhclient: Sending on   Socket/fallback
Jun 10 11:02:25 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:02:25 turk accounts-daemon[1444]: started daemon version 0.6.15
Jun 10 11:02:25 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:02:25 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:02:25 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:02:25 turk dhclient: bound to 192.168.1.103 -- renewal in 42518 seconds.
Jun 10 11:02:25 turk NetworkManager[1032]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   address 192.168.1.103
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   gateway 192.168.1.1
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   nameserver '194.168.4.100'
Jun 10 11:02:25 turk NetworkManager[1032]: <info>   nameserver '194.168.8.100'
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:02:25 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:02:25 turk dbus[990]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:02:25 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:02:25 turk anacron[1654]: Anacron 2.3 started on 2012-06-10
Jun 10 11:02:25 turk anacron[1654]: Normal exit (0 jobs run)
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully called chroot.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully dropped privileges.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully limited resources.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Watchdog thread running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Canary thread running.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully made thread 1779 of process 1779 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> DNS: starting dnsmasq...
Jun 10 11:02:26 turk NetworkManager[1032]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:02:26 turk dnsmasq[1787]: started, version 2.59 cache disabled
Jun 10 11:02:26 turk dnsmasq[1787]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:02:26 turk dnsmasq[1787]: using nameserver 194.168.8.100#53
Jun 10 11:02:26 turk dnsmasq[1787]: using nameserver 194.168.4.100#53
Jun 10 11:02:26 turk NetworkManager[1032]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Activation (eth0) successful, device activated.
Jun 10 11:02:26 turk NetworkManager[1032]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:02:26 turk dbus[990]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:02:26 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:02:26 turk rtkit-daemon[1781]: Successfully made thread 1866 of process 1779 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:02:26 turk rtkit-daemon[1781]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:02:27 turk rtkit-daemon[1781]: Successfully made thread 1867 of process 1779 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:02:27 turk rtkit-daemon[1781]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:02:28 turk dbus[990]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:02:28 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:02:35 turk ntpdate[1847]: step time server 91.189.94.4 offset 0.653363 sec
Jun 10 11:02:36 turk kernel: [   33.256017] eth0: no IPv6 routers present
Jun 10 11:02:43 turk goa[2148]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:02:45 turk NetworkManager[1032]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:02:45 turk NetworkManager[1032]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:03:01 turk kernel: [   58.235358] do_general_protection: 27 callbacks suppressed
Jun 10 11:03:01 turk kernel: [   58.235361] ubuntuone-login[2211] general protection ip:577e28 sp:7fff53d75bf0 error:0 in python2.7[400000+272000]
Jun 10 11:03:29 turk dbus[990]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun 10 11:03:29 turk kernel: [   87.221333] apt-check[2239]: segfault at 8a65c0 ip 00000000008a65c0 sp 00007fff2ce66478 error 15 in python2.7[872000+69000]
Jun 10 11:03:30 turk AptDaemon: INFO: Initializing daemon
Jun 10 11:03:30 turk AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 10 11:03:30 turk dbus[990]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 10 11:03:30 turk AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 10 11:03:30 turk AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:03:30 turk AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:03:34 turk AptDaemon.PackageKit: INFO: Get updates()
Jun 10 11:03:34 turk AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/470272343af74219b223a32aacb820f6
Jun 10 11:14:59 turk kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 10 11:14:59 turk rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="996" x-info="http://www.rsyslog.com"] start
Jun 10 11:14:59 turk rsyslogd: rsyslogd's groupid changed to 103
Jun 10 11:14:59 turk rsyslogd: rsyslogd's userid changed to 101
Jun 10 11:14:59 turk rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 10 11:14:59 turk polkitd[1016]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jun 10 11:14:59 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: init!
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 11:14:59 turk NetworkManager[984]:    SCPluginIfupdown: management mode: unmanaged
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0)
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: end _init.
Jun 10 11:14:59 turk NetworkManager[984]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:14:59 turk NetworkManager[984]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 11:14:59 turk kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 11:14:59 turk kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 11:14:59 turk NetworkManager[984]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:14:59 turk kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 (Ubuntu 3.2.0-24.39-generic 3.2.16)
Jun 10 11:14:59 turk kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:14:59 turk kernel: [    0.000000] KERNEL supported cpus:
Jun 10 11:14:59 turk kernel: [    0.000000]   Intel GenuineIntel
Jun 10 11:14:59 turk kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 11:14:59 turk kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 11:14:59 turk kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff98000 (ACPI data)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cff98000 - 00000000cffd0000 (ACPI NVS)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000] NX (Execute Disable) protection: active
Jun 10 11:14:59 turk kernel: [    0.000000] DMI present.
Jun 10 11:14:59 turk kernel: [    0.000000] DMI: System manufacturer System Product Name/M4A88TD-M EVO, BIOS 1404    05/28/2010
Jun 10 11:14:59 turk kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jun 10 11:14:59 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:14:59 turk kernel: [    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR default type: uncachable
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 11:14:59 turk kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   A0000-EFFFF uncachable
Jun 10 11:14:59 turk kernel: [    0.000000]   F0000-FFFFF write-protect
Jun 10 11:14:59 turk kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 11:14:59 turk kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
Jun 10 11:14:59 turk kernel: [    0.000000]   3 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   4 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   5 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   6 disabled
Jun 10 11:14:59 turk kernel: [    0.000000]   7 disabled
Jun 10 11:14:59 turk kernel: [    0.000000] TOM2: 0000000130000000 aka 4864M
Jun 10 11:14:59 turk kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 11:14:59 turk kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 11:14:59 turk kernel: [    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x400000000
Jun 10 11:14:59 turk kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Jun 10 11:14:59 turk kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: (19754800) ... get_connections.
Jun 10 11:14:59 turk kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Jun 10 11:14:59 turk NetworkManager[984]:    SCPlugin-Ifupdown: (19754800) ... get_connections (managed=false): return empty list.
Jun 10 11:14:59 turk kernel: [    0.000000] Using GB pages for direct mapping
Jun 10 11:14:59 turk kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cff80000
Jun 10 11:14:59 turk kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Jun 10 11:14:59 turk kernel: [    0.000000]  00c0000000 - 00cfe00000 page 2M
Jun 10 11:14:59 turk kernel: [    0.000000]  00cfe00000 - 00cff80000 page 4k
Jun 10 11:14:59 turk kernel: [    0.000000] kernel direct mapping tables up to cff80000 @ 1fffd000-20000000
Jun 10 11:14:59 turk kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Jun 10 11:14:59 turk kernel: [    0.000000]  0100000000 - 0130000000 page 2M
Jun 10 11:14:59 turk kernel: [    0.000000] kernel direct mapping tables up to 130000000 @ cff7e000-cff80000
Jun 10 11:14:59 turk kernel: [    0.000000] RAMDISK: 364e6000 - 3726b000
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: RSDP 00000000000fb580 00024 (v02 ACPIAM)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: XSDT 00000000cff80100 0005C (v01 052810 XSDT1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: FACP 00000000cff80290 000F4 (v03 052810 FACP1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: DSDT 00000000cff80450 0F2AC (v01  A1581 A1581001 00000001 INTL 20060113)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: FACS 00000000cff98000 00040
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: APIC 00000000cff80390 0007C (v01 052810 APIC1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: MCFG 00000000cff80410 0003C (v01 052810 OEMMCFG  20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: OEMB 00000000cff98040 00072 (v01 052810 OEMB1134 20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: SRAT 00000000cff8f8a0 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: HPET 00000000cff8f990 00038 (v01 052810 OEMHPET  20100528 MSFT 00000097)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: SSDT 00000000cff8f9d0 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 0-a0000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
Jun 10 11:14:59 turk kernel: [    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
Jun 10 11:14:59 turk kernel: [    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
Jun 10 11:14:59 turk kernel: [    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
Jun 10 11:14:59 turk kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
Jun 10 11:14:59 turk kernel: [    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
Jun 10 11:14:59 turk kernel: [    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b600000-ffff88012f5fffff] on node 0
Jun 10 11:14:59 turk kernel: [    0.000000] Zone PFN ranges:
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal   0x00100000 -> 0x00130000
Jun 10 11:14:59 turk kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 11:14:59 turk kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00000100 -> 0x000cff80
Jun 10 11:14:59 turk kernel: [    0.000000]     0: 0x00100000 -> 0x00130000
Jun 10 11:14:59 turk kernel: [    0.000000] On node 0 totalpages: 1048334
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 5 pages reserved
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal zone: 3072 pages used for memmap
Jun 10 11:14:59 turk kernel: [    0.000000]   Normal zone: 193536 pages, LIFO batch:31
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jun 10 11:14:59 turk kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 11:14:59 turk kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 11:14:59 turk kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun 10 11:14:59 turk kernel: [    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
Jun 10 11:14:59 turk kernel: [    0.000000] nr_irqs_gsi: 40
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff98000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cff98000 - 00000000cffd0000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ffa00000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Jun 10 11:14:59 turk kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2fa00000)
Jun 10 11:14:59 turk kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 11:14:59 turk kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
Jun 10 11:14:59 turk kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012fc00000 s83072 r8192 d23424 u262144
Jun 10 11:14:59 turk kernel: [    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
Jun 10 11:14:59 turk kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
Jun 10 11:14:59 turk kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028873
Jun 10 11:14:59 turk kernel: [    0.000000] Policy zone: Normal
Jun 10 11:14:59 turk kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=0377d65b-5932-4d49-af07-208cca2d118e ro quiet splash vt.handoff=7
Jun 10 11:14:59 turk kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jun 10 11:14:59 turk kernel: [    0.000000] Checking aperture...
Jun 10 11:14:59 turk kernel: [    0.000000] No AGP bridge found
Jun 10 11:14:59 turk kernel: [    0.000000] Node 0: aperture @ c4000000 size 32 MB
Jun 10 11:14:59 turk kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Jun 10 11:14:59 turk kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Jun 10 11:14:59 turk kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Jun 10 11:14:59 turk kernel: [    0.000000] This costs you 64 MB of RAM
Jun 10 11:14:59 turk kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jun 10 11:14:59 turk kernel: [    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
Jun 10 11:14:59 turk kernel: [    0.000000] Memory: 3965868k/4980736k available (6567k kernel code, 787400k absent, 227468k reserved, 6636k data, 920k init)
Jun 10 11:14:59 turk kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
Jun 10 11:14:59 turk kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 11:14:59 turk kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jun 10 11:14:59 turk kernel: [    0.000000] NR_IRQS:16640 nr_irqs:728 16
Jun 10 11:14:59 turk kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 11:14:59 turk kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jun 10 11:14:59 turk kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jun 10 11:14:59 turk kernel: [    0.000000] Console: colour dummy device 80x25
Jun 10 11:14:59 turk kernel: [    0.000000] console [tty0] enabled
Jun 10 11:14:59 turk kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Jun 10 11:14:59 turk kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 11:14:59 turk kernel: [    0.000000] hpet clockevent registered
Jun 10 11:14:59 turk kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 11:14:59 turk kernel: [    0.000000] Detected 3214.213 MHz processor.
Jun 10 11:14:59 turk kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.42 BogoMIPS (lpj=12856852)
Jun 10 11:14:59 turk kernel: [    0.004007] pid_max: default: 32768 minimum: 301
Jun 10 11:14:59 turk kernel: [    0.004026] Security Framework initialized
Jun 10 11:14:59 turk kernel: [    0.004037] AppArmor: AppArmor initialized
Jun 10 11:14:59 turk kernel: [    0.004039] Yama: becoming mindful.
Jun 10 11:14:59 turk kernel: [    0.004344] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 10 11:14:59 turk kernel: [    0.008811] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 10 11:14:59 turk kernel: [    0.009422] Mount-cache hash table entries: 256
Jun 10 11:14:59 turk kernel: [    0.009525] Initializing cgroup subsys cpuacct
Jun 10 11:14:59 turk kernel: [    0.009529] Initializing cgroup subsys memory
Jun 10 11:14:59 turk kernel: [    0.009536] Initializing cgroup subsys devices
Jun 10 11:14:59 turk kernel: [    0.009538] Initializing cgroup subsys freezer
Jun 10 11:14:59 turk kernel: [    0.009539] Initializing cgroup subsys blkio
Jun 10 11:14:59 turk kernel: [    0.009545] Initializing cgroup subsys perf_event
Jun 10 11:14:59 turk kernel: [    0.009568] tseg: 0000000000
Jun 10 11:14:59 turk kernel: [    0.009578] CPU: Physical Processor ID: 0
Jun 10 11:14:59 turk kernel: [    0.009579] CPU: Processor Core ID: 0
Jun 10 11:14:59 turk kernel: [    0.009581] mce: CPU supports 6 MCE banks
Jun 10 11:14:59 turk kernel: [    0.010738] ACPI: Core revision 20110623
Jun 10 11:14:59 turk kernel: [    0.016009] ftrace: allocating 27050 entries in 107 pages
Jun 10 11:14:59 turk kernel: [    0.020381] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 11:14:59 turk kernel: [    0.063135] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
Jun 10 11:14:59 turk kernel: [    0.064003] Performance Events: AMD PMU driver.
Jun 10 11:14:59 turk kernel: [    0.064003] ... version:                0
Jun 10 11:14:59 turk kernel: [    0.064003] ... bit width:              48
Jun 10 11:14:59 turk kernel: [    0.064003] ... generic registers:      4
Jun 10 11:14:59 turk kernel: [    0.064003] ... value mask:             0000ffffffffffff
Jun 10 11:14:59 turk kernel: [    0.064003] ... max period:             00007fffffffffff
Jun 10 11:14:59 turk kernel: [    0.064003] ... fixed-purpose events:   0
Jun 10 11:14:59 turk kernel: [    0.064003] ... event mask:             000000000000000f
Jun 10 11:14:59 turk kernel: [    0.064003] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.064003] Booting Node   0, Processors  #1
Jun 10 11:14:59 turk kernel: [    0.064003] smpboot cpu 1: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.152023] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.152081]  #2
Jun 10 11:14:59 turk kernel: [    0.152082] smpboot cpu 2: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.244027] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.244079]  #3
Jun 10 11:14:59 turk kernel: [    0.244080] smpboot cpu 3: start_ip = 99000
Jun 10 11:14:59 turk kernel: [    0.336033] NMI watchdog enabled, takes one hw-pmu counter.
Jun 10 11:14:59 turk kernel: [    0.336047] Brought up 4 CPUs
Jun 10 11:14:59 turk kernel: [    0.336049] Total of 4 processors activated (25714.23 BogoMIPS).
Jun 10 11:14:59 turk kernel: [    0.340158] devtmpfs: initialized
Jun 10 11:14:59 turk kernel: [    0.341187] EVM: security.selinux
Jun 10 11:14:59 turk kernel: [    0.341188] EVM: security.SMACK64
Jun 10 11:14:59 turk kernel: [    0.341189] EVM: security.capability
Jun 10 11:14:59 turk kernel: [    0.341285] PM: Registering ACPI NVS region at cff98000 (229376 bytes)
Jun 10 11:14:59 turk kernel: [    0.341285] print_constraints: dummy: 
Jun 10 11:14:59 turk kernel: [    0.341285] RTC time: 10:14:36, date: 06/10/12
Jun 10 11:14:59 turk kernel: [    0.341285] NET: Registered protocol family 16
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: io port [1000, ffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] TOM: 00000000d0000000 aka 3328M
Jun 10 11:14:59 turk kernel: [    0.341285] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [a0000, bffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [d0000000, dfffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [e0000000, efffffff] ==> none
Jun 10 11:14:59 turk kernel: [    0.341285] node 0 link 0: mmio [f0000000, ffdfffff]
Jun 10 11:14:59 turk kernel: [    0.341285] TOM2: 0000000130000000 aka 4864M
Jun 10 11:14:59 turk kernel: [    0.341285] bus: [00, 07] on node 0 link 0
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 0 [io  0x0000-0xffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
Jun 10 11:14:59 turk kernel: [    0.341285] Extended Config Space enabled on 1 nodes
Jun 10 11:14:59 turk kernel: [    0.341285] ACPI: bus type pci registered
Jun 10 11:14:59 turk kernel: [    0.341285] Trying to unpack rootfs image as initramfs...
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: not using MMCONFIG
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: Using configuration type 1 for base access
Jun 10 11:14:59 turk kernel: [    0.341285] PCI: Using configuration type 1 for extended access
Jun 10 11:14:59 turk kernel: [    0.341457] bio: create slab <bio-0> at 0
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Module Device)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Processor Device)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(3.0 _SCP Extensions)
Jun 10 11:14:59 turk kernel: [    0.341457] ACPI: Added _OSI(Processor Aggregator Device)
Jun 10 11:14:59 turk kernel: [    0.344427] ACPI: EC: Look up EC in DSDT
Jun 10 11:14:59 turk kernel: [    0.380092] ACPI: Executed 3 blocks of module-level executable AML code
Jun 10 11:14:59 turk kernel: [    0.548579] ACPI: Interpreter enabled
Jun 10 11:14:59 turk kernel: [    0.548584] ACPI: (supports S0 S1 S3 S4 S5)
Jun 10 11:14:59 turk kernel: [    0.548601] ACPI: Using IOAPIC for interrupt routing
Jun 10 11:14:59 turk kernel: [    0.548619] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jun 10 11:14:59 turk kernel: [    0.549990] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Jun 10 11:14:59 turk kernel: [    0.557708] Freeing initrd memory: 13844k freed
Jun 10 11:14:59 turk kernel: [    0.642049] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Jun 10 11:14:59 turk kernel: [    0.642147] ACPI: No dock devices found.
Jun 10 11:14:59 turk kernel: [    0.642148] HEST: Table not found.
Jun 10 11:14:59 turk kernel: [    0.642151] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jun 10 11:14:59 turk kernel: [    0.642207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jun 10 11:14:59 turk kernel: [    0.642322] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.642324] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jun 10 11:14:59 turk kernel: [    0.642326] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.642328] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.642329] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.642331] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.642343] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.642385] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642414] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642417] pci 0000:00:02.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642431] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642459] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk NetworkManager[984]:    Ifupdown: get unmanaged devices count: 0
Jun 10 11:14:59 turk kernel: [    0.642461] pci 0000:00:07.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642473] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642500] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642502] pci 0000:00:09.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642513] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.642541] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.642543] pci 0000:00:0a.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642567] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.642585] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
Jun 10 11:14:59 turk kernel: [    0.642593] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
Jun 10 11:14:59 turk kernel: [    0.642601] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
Jun 10 11:14:59 turk kernel: [    0.642610] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
Jun 10 11:14:59 turk kernel: [    0.642618] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
Jun 10 11:14:59 turk kernel: [    0.642626] pci 0000:00:11.0: reg 24: [mem 0xfbfffc00-0xfbffffff]
Jun 10 11:14:59 turk kernel: [    0.642644] pci 0000:00:11.0: set SATA to AHCI mode
Jun 10 11:14:59 turk kernel: [    0.642695] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642706] pci 0000:00:12.0: reg 10: [mem 0xfbffe000-0xfbffefff]
Jun 10 11:14:59 turk kernel: [    0.642767] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642783] pci 0000:00:12.2: reg 10: [mem 0xfbfff800-0xfbfff8ff]
Jun 10 11:14:59 turk kernel: [    0.642854] pci 0000:00:12.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.642855] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.642859] pci 0000:00:12.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.642876] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642887] pci 0000:00:13.0: reg 10: [mem 0xfbffd000-0xfbffdfff]
Jun 10 11:14:59 turk kernel: [    0.642948] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.642964] pci 0000:00:13.2: reg 10: [mem 0xfbfff400-0xfbfff4ff]
Jun 10 11:14:59 turk kernel: [    0.643035] pci 0000:00:13.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.643036] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.643039] pci 0000:00:13.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643056] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Jun 10 11:14:59 turk NetworkManager[984]: <info> modem-manager is now available
Jun 10 11:14:59 turk kernel: [    0.643122] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.643136] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Jun 10 11:14:59 turk kernel: [    0.643144] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Jun 10 11:14:59 turk kernel: [    0.643152] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Jun 10 11:14:59 turk kernel: [    0.643160] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Jun 10 11:14:59 turk kernel: [    0.643169] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Jun 10 11:14:59 turk kernel: [    0.643219] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
Jun 10 11:14:59 turk kernel: [    0.643237] pci 0000:00:14.2: reg 10: [mem 0xfbff8000-0xfbffbfff 64bit]
Jun 10 11:14:59 turk kernel: [    0.643293] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.643297] pci 0000:00:14.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643307] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Jun 10 11:14:59 turk kernel: [    0.643373] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Jun 10 11:14:59 turk kernel: [    0.643408] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643420] pci 0000:00:14.5: reg 10: [mem 0xfbffc000-0xfbffcfff]
Jun 10 11:14:59 turk kernel: [    0.643477] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643489] pci 0000:00:16.0: reg 10: [mem 0xfbff7000-0xfbff7fff]
Jun 10 11:14:59 turk kernel: [    0.643549] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Jun 10 11:14:59 turk kernel: [    0.643566] pci 0000:00:16.2: reg 10: [mem 0xfbfff000-0xfbfff0ff]
Jun 10 11:14:59 turk kernel: [    0.643636] pci 0000:00:16.2: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.643638] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.643641] pci 0000:00:16.2: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.643657] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643669] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643679] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643689] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643703] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Jun 10 11:14:59 turk kernel: [    0.643745] pci 0000:01:00.0: [10de:0e22] type 0 class 0x000300
Jun 10 11:14:59 turk kernel: [    0.643754] pci 0000:01:00.0: reg 10: [mem 0xfc000000-0xfdffffff]
Jun 10 11:14:59 turk kernel: [    0.643764] pci 0000:01:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.643773] pci 0000:01:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.643780] pci 0000:01:00.0: reg 24: [io  0xbc00-0xbc7f]
Jun 10 11:14:59 turk kernel: [    0.643786] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
Jun 10 11:14:59 turk kernel: [    0.643836] pci 0000:01:00.1: [10de:0beb] type 0 class 0x000403
Jun 10 11:14:59 turk kernel: [    0.643845] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
Jun 10 11:14:59 turk kernel: [    0.648059] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:14:59 turk kernel: [    0.648063] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.648066] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.648069] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.648114] pci 0000:02:00.0: [1106:3403] type 0 class 0x000c00
Jun 10 11:14:59 turk kernel: [    0.648143] pci 0000:02:00.0: reg 10: [mem 0xfeaff800-0xfeafffff 64bit]
Jun 10 11:14:59 turk kernel: [    0.648158] pci 0000:02:00.0: reg 18: [io  0xc800-0xc8ff]
Jun 10 11:14:59 turk kernel: [    0.648284] pci 0000:02:00.0: supports D2
Jun 10 11:14:59 turk kernel: [    0.648285] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.648291] pci 0000:02:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.656063] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:14:59 turk kernel: [    0.656067] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.656069] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.656119] pci 0000:03:00.0: [1106:0415] type 0 class 0x000101
Jun 10 11:14:59 turk kernel: [    0.656141] pci 0000:03:00.0: reg 10: [io  0xdc00-0xdc07]
Jun 10 11:14:59 turk kernel: [    0.656156] pci 0000:03:00.0: reg 14: [io  0xd880-0xd883]
Jun 10 11:14:59 turk kernel: [    0.656170] pci 0000:03:00.0: reg 18: [io  0xd800-0xd807]
Jun 10 11:14:59 turk kernel: [    0.656185] pci 0000:03:00.0: reg 1c: [io  0xd480-0xd483]
Jun 10 11:14:59 turk kernel: [    0.656199] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
Jun 10 11:14:59 turk kernel: [    0.656227] pci 0000:03:00.0: reg 30: [mem 0xfebe0000-0xfebeffff pref]
Jun 10 11:14:59 turk kernel: [    0.656302] pci 0000:03:00.0: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.656303] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
Jun 10 11:14:59 turk kernel: [    0.656308] pci 0000:03:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.664061] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:14:59 turk kernel: [    0.664065] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.664068] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.664103] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jun 10 11:14:59 turk kernel: [    0.664114] pci 0000:04:00.0: reg 10: [io  0xe800-0xe8ff]
Jun 10 11:14:59 turk kernel: [    0.664133] pci 0000:04:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.664146] pci 0000:04:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.664197] pci 0000:04:00.0: supports D1 D2
Jun 10 11:14:59 turk kernel: [    0.664199] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 11:14:59 turk kernel: [    0.664202] pci 0000:04:00.0: PME# disabled
Jun 10 11:14:59 turk kernel: [    0.672059] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:14:59 turk kernel: [    0.672063] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.672066] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.672120] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672128] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672130] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672134] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672136] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672137] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672139] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jun 10 11:14:59 turk kernel: [    0.672158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 11:14:59 turk kernel: [    0.672252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Jun 10 11:14:59 turk kernel: [    0.672273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Jun 10 11:14:59 turk kernel: [    0.672290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
Jun 10 11:14:59 turk kernel: [    0.672308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
Jun 10 11:14:59 turk kernel: [    0.672328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
Jun 10 11:14:59 turk kernel: [    0.672363]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jun 10 11:14:59 turk kernel: [    0.672365]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jun 10 11:14:59 turk kernel: [    0.672367] ACPI _OSC control for PCIe not granted, disabling ASPM
Jun 10 11:14:59 turk kernel: [    0.675423] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675467] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675510] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675552] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 9 10 *11 14 15)
Jun 10 11:14:59 turk kernel: [    0.675584] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675610] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675635] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675660] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: loaded
Jun 10 11:14:59 turk kernel: [    0.675734] vgaarb: bridge control possible 0000:01:00.0
Jun 10 11:14:59 turk kernel: [    0.675734] i2c-core: driver [aat2870] using legacy suspend method
Jun 10 11:14:59 turk kernel: [    0.675734] i2c-core: driver [aat2870] using legacy resume method
Jun 10 11:14:59 turk kernel: [    0.675734] SCSI subsystem initialized
Jun 10 11:14:59 turk kernel: [    0.675734] libata version 3.00 loaded.
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new interface driver usbfs
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new interface driver hub
Jun 10 11:14:59 turk kernel: [    0.675734] usbcore: registered new device driver usb
Jun 10 11:14:59 turk kernel: [    0.676068] PCI: Using ACPI for IRQ routing
Jun 10 11:14:59 turk kernel: [    0.683419] PCI: pci_cache_line_size set to 64 bytes
Jun 10 11:14:59 turk kernel: [    0.683486] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Jun 10 11:14:59 turk kernel: [    0.683488] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
Jun 10 11:14:59 turk kernel: [    0.683557] NetLabel: Initializing
Jun 10 11:14:59 turk kernel: [    0.683558] NetLabel:  domain hash size = 128
Jun 10 11:14:59 turk kernel: [    0.683559] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 11:14:59 turk kernel: [    0.683567] NetLabel:  unlabeled traffic allowed by default
Jun 10 11:14:59 turk kernel: [    0.683594] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 10 11:14:59 turk kernel: [    0.683594] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jun 10 11:14:59 turk kernel: [    0.685065] Switching to clocksource hpet
Jun 10 11:14:59 turk kernel: [    0.688698] AppArmor: AppArmor Filesystem Enabled
Jun 10 11:14:59 turk kernel: [    0.688714] pnp: PnP ACPI init
Jun 10 11:14:59 turk kernel: [    0.688724] ACPI: bus type pnp registered
Jun 10 11:14:59 turk kernel: [    0.688799] pnp 00:00: [bus 00-ff]
Jun 10 11:14:59 turk kernel: [    0.688801] pnp 00:00: [io  0x0cf8-0x0cff]
Jun 10 11:14:59 turk kernel: [    0.688803] pnp 00:00: [io  0x0000-0x0cf7 window]
Jun 10 11:14:59 turk kernel: [    0.688804] pnp 00:00: [io  0x0d00-0xffff window]
Jun 10 11:14:59 turk kernel: [    0.688806] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jun 10 11:14:59 turk kernel: [    0.688807] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Jun 10 11:14:59 turk kernel: [    0.688809] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
Jun 10 11:14:59 turk kernel: [    0.688810] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Jun 10 11:14:59 turk kernel: [    0.688846] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jun 10 11:14:59 turk kernel: [    0.688899] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.688901] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.688934] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.689423] pnp 00:02: [dma 4]
Jun 10 11:14:59 turk kernel: [    0.689425] pnp 00:02: [io  0x0000-0x000f]
Jun 10 11:14:59 turk kernel: [    0.689426] pnp 00:02: [io  0x0081-0x0083]
Jun 10 11:14:59 turk kernel: [    0.689428] pnp 00:02: [io  0x0087]
Jun 10 11:14:59 turk kernel: [    0.689429] pnp 00:02: [io  0x0089-0x008b]
Jun 10 11:14:59 turk kernel: [    0.689430] pnp 00:02: [io  0x008f]
Jun 10 11:14:59 turk kernel: [    0.689431] pnp 00:02: [io  0x00c0-0x00df]
Jun 10 11:14:59 turk kernel: [    0.689452] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jun 10 11:14:59 turk kernel: [    0.689458] pnp 00:03: [io  0x0070-0x0071]
Jun 10 11:14:59 turk kernel: [    0.689466] pnp 00:03: [irq 8]
Jun 10 11:14:59 turk kernel: [    0.689487] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jun 10 11:14:59 turk kernel: [    0.689492] pnp 00:04: [io  0x0061]
Jun 10 11:14:59 turk kernel: [    0.689512] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Jun 10 11:14:59 turk kernel: [    0.689518] pnp 00:05: [io  0x00f0-0x00ff]
Jun 10 11:14:59 turk kernel: [    0.689521] pnp 00:05: [irq 13]
Jun 10 11:14:59 turk kernel: [    0.689540] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Jun 10 11:14:59 turk kernel: [    0.689987] pnp 00:06: [io  0x0378-0x037f]
Jun 10 11:14:59 turk kernel: [    0.689991] pnp 00:06: [irq 7]
Jun 10 11:14:59 turk kernel: [    0.689992] pnp 00:06: [dma 0 disabled]
Jun 10 11:14:59 turk kernel: [    0.690157] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
Jun 10 11:14:59 turk kernel: [    0.690182] pnp 00:07: [mem 0xfed00000-0xfed003ff]
Jun 10 11:14:59 turk kernel: [    0.690204] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
Jun 10 11:14:59 turk kernel: [    0.690527] pnp 00:08: [io  0x03f8-0x03ff]
Jun 10 11:14:59 turk kernel: [    0.690530] pnp 00:08: [irq 4]
Jun 10 11:14:59 turk kernel: [    0.690532] pnp 00:08: [dma 0 disabled]
Jun 10 11:14:59 turk kernel: [    0.690594] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Jun 10 11:14:59 turk kernel: [    0.690640] pnp 00:09: [io  0x0060]
Jun 10 11:14:59 turk kernel: [    0.690641] pnp 00:09: [io  0x0064]
Jun 10 11:14:59 turk kernel: [    0.690644] pnp 00:09: [mem 0xfec00000-0xfec00fff]
Jun 10 11:14:59 turk kernel: [    0.690646] pnp 00:09: [mem 0xfee00000-0xfee00fff]
Jun 10 11:14:59 turk kernel: [    0.690682] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.690684] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690686] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.690777] pnp 00:0a: [io  0x0010-0x001f]
Jun 10 11:14:59 turk kernel: [    0.690778] pnp 00:0a: [io  0x0022-0x003f]
Jun 10 11:14:59 turk kernel: [    0.690779] pnp 00:0a: [io  0x0062-0x0063]
Jun 10 11:14:59 turk kernel: [    0.690780] pnp 00:0a: [io  0x0065-0x006f]
Jun 10 11:14:59 turk kernel: [    0.690782] pnp 00:0a: [io  0x0072-0x007f]
Jun 10 11:14:59 turk kernel: [    0.690783] pnp 00:0a: [io  0x0080]
Jun 10 11:14:59 turk kernel: [    0.690784] pnp 00:0a: [io  0x0084-0x0086]
Jun 10 11:14:59 turk kernel: [    0.690785] pnp 00:0a: [io  0x0088]
Jun 10 11:14:59 turk kernel: [    0.690787] pnp 00:0a: [io  0x008c-0x008e]
Jun 10 11:14:59 turk kernel: [    0.690788] pnp 00:0a: [io  0x0090-0x009f]
Jun 10 11:14:59 turk kernel: [    0.690789] pnp 00:0a: [io  0x00a2-0x00bf]
Jun 10 11:14:59 turk kernel: [    0.690790] pnp 00:0a: [io  0x00b1]
Jun 10 11:14:59 turk kernel: [    0.690792] pnp 00:0a: [io  0x00e0-0x00ef]
Jun 10 11:14:59 turk kernel: [    0.690793] pnp 00:0a: [io  0x04d0-0x04d1]
Jun 10 11:14:59 turk kernel: [    0.690794] pnp 00:0a: [io  0x040b]
Jun 10 11:14:59 turk kernel: [    0.690795] pnp 00:0a: [io  0x04d6]
Jun 10 11:14:59 turk kernel: [    0.690796] pnp 00:0a: [io  0x0c00-0x0c01]
Jun 10 11:14:59 turk kernel: [    0.690798] pnp 00:0a: [io  0x0c14]
Jun 10 11:14:59 turk kernel: [    0.690799] pnp 00:0a: [io  0x0c50-0x0c51]
Jun 10 11:14:59 turk kernel: [    0.690800] pnp 00:0a: [io  0x0c52]
Jun 10 11:14:59 turk kernel: [    0.690801] pnp 00:0a: [io  0x0c6c]
Jun 10 11:14:59 turk kernel: [    0.690802] pnp 00:0a: [io  0x0c6f]
Jun 10 11:14:59 turk kernel: [    0.690803] pnp 00:0a: [io  0x0cd0-0x0cd1]
Jun 10 11:14:59 turk kernel: [    0.690805] pnp 00:0a: [io  0x0cd2-0x0cd3]
Jun 10 11:14:59 turk kernel: [    0.690806] pnp 00:0a: [io  0x0cd4-0x0cd5]
Jun 10 11:14:59 turk kernel: [    0.690807] pnp 00:0a: [io  0x0cd6-0x0cd7]
Jun 10 11:14:59 turk kernel: [    0.690808] pnp 00:0a: [io  0x0cd8-0x0cdf]
Jun 10 11:14:59 turk kernel: [    0.690810] pnp 00:0a: [io  0x0b00-0x0b3f]
Jun 10 11:14:59 turk kernel: [    0.690811] pnp 00:0a: [io  0x0800-0x089f]
Jun 10 11:14:59 turk kernel: [    0.690812] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.690814] pnp 00:0a: [io  0x0b00-0x0b1f]
Jun 10 11:14:59 turk kernel: [    0.690815] pnp 00:0a: [io  0x0b20-0x0b3f]
Jun 10 11:14:59 turk kernel: [    0.690816] pnp 00:0a: [io  0x0900-0x090f]
Jun 10 11:14:59 turk kernel: [    0.690818] pnp 00:0a: [io  0x0910-0x091f]
Jun 10 11:14:59 turk kernel: [    0.690819] pnp 00:0a: [io  0xfe00-0xfefe]
Jun 10 11:14:59 turk kernel: [    0.690820] pnp 00:0a: [io  0x0060]
Jun 10 11:14:59 turk kernel: [    0.690821] pnp 00:0a: [io  0x0064]
Jun 10 11:14:59 turk kernel: [    0.690823] pnp 00:0a: [mem 0xffb80000-0xffbfffff]
Jun 10 11:14:59 turk kernel: [    0.690824] pnp 00:0a: [mem 0xfec10000-0xfec1001f]
Jun 10 11:14:59 turk kernel: [    0.690825] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Jun 10 11:14:59 turk kernel: [    0.690827] pnp 00:0a: [mem 0xfed80000-0xfed80fff]
Jun 10 11:14:59 turk kernel: [    0.690830] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.690905] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690907] system 00:0a: [io  0x040b] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690909] system 00:0a: [io  0x04d6] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690910] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690912] system 00:0a: [io  0x0c14] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690914] system 00:0a: [io  0x0c50-0x0c51] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690915] system 00:0a: [io  0x0c52] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690917] system 00:0a: [io  0x0c6c] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690919] system 00:0a: [io  0x0c6f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690920] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690922] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690924] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690926] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690928] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690929] system 00:0a: [io  0x0b00-0x0b3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690931] system 00:0a: [io  0x0800-0x089f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690934] system 00:0a: [io  0x0b00-0x0b1f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690936] system 00:0a: [io  0x0b20-0x0b3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690938] system 00:0a: [io  0x0900-0x090f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690940] system 00:0a: [io  0x0910-0x091f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690942] system 00:0a: [io  0xfe00-0xfefe] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690944] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690946] system 00:0a: [mem 0xfec10000-0xfec1001f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690948] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690950] system 00:0a: [mem 0xfed80000-0xfed80fff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.690952] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691049] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
Jun 10 11:14:59 turk kernel: [    0.691051] pnp 00:0b: [io  0x0230-0x023f]
Jun 10 11:14:59 turk kernel: [    0.691052] pnp 00:0b: [io  0x0290-0x029f]
Jun 10 11:14:59 turk kernel: [    0.691054] pnp 00:0b: [io  0x0300-0x030f]
Jun 10 11:14:59 turk kernel: [    0.691055] pnp 00:0b: [io  0x0a30-0x0a3f]
Jun 10 11:14:59 turk kernel: [    0.691090] system 00:0b: [io  0x0230-0x023f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691092] system 00:0b: [io  0x0290-0x029f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691094] system 00:0b: [io  0x0300-0x030f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691096] system 00:0b: [io  0x0a30-0x0a3f] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691098] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691126] pnp 00:0c: [mem 0xe0000000-0xefffffff]
Jun 10 11:14:59 turk kernel: [    0.691160] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
Jun 10 11:14:59 turk kernel: [    0.691162] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Jun 10 11:14:59 turk kernel: [    0.691229] pnp 00:0d: [mem 0x00000000-0x0009ffff]
Jun 10 11:14:59 turk kernel: [    0.691230] pnp 00:0d: [mem 0x000c0000-0x000cffff]
Jun 10 11:14:59 turk kernel: [    0.691232] pnp 00:0d: [mem 0x000e0000-0x000fffff]
Jun 10 11:14:59 turk kernel: [    0.691233] pnp 00:0d: [mem 0x00100000-0xcfffffff]
Jun 10 11:14:59 turk kernel: [    0.691235] pnp 00:0d: [mem 0xfec00000-0xffffffff]
Jun 10 11:14:59 turk kernel: [    0.691270] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691272] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691274] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691276] system 00:0d: [mem 0x00100000-0xcfffffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691278] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
Jun 10 11:14:59 turk kernel: [    0.691280] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Jun 10 11:14:59 turk kernel: [    0.691344] pnp: PnP ACPI: found 14 devices
Jun 10 11:14:59 turk kernel: [    0.691346] ACPI: ACPI bus type pnp unregistered
Jun 10 11:14:59 turk kernel: [    0.697722] PCI: max bus depth: 1 pci_try_num: 2
Jun 10 11:14:59 turk kernel: [    0.697741] pci 0000:00:02.0: PCI bridge to [bus 01-01]
Jun 10 11:14:59 turk kernel: [    0.697743] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.697745] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.697747] pci 0000:00:02.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697750] pci 0000:00:07.0: PCI bridge to [bus 02-02]
Jun 10 11:14:59 turk kernel: [    0.697752] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.697754] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.697758] pci 0000:00:09.0: PCI bridge to [bus 03-03]
Jun 10 11:14:59 turk kernel: [    0.697759] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.697762] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697765] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
Jun 10 11:14:59 turk kernel: [    0.697767] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.697770] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697773] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Jun 10 11:14:59 turk kernel: [    0.697791] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    0.697794] pci 0000:00:02.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697800] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    0.697803] pci 0000:00:07.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697808] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    0.697810] pci 0000:00:09.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697813] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    0.697815] pci 0000:00:0a.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    0.697821] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.697822] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jun 10 11:14:59 turk kernel: [    0.697824] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.697825] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.697827] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.697829] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697830] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
Jun 10 11:14:59 turk kernel: [    0.697832] pci_bus 0000:01: resource 1 [mem 0xfc000000-0xfe9fffff]
Jun 10 11:14:59 turk kernel: [    0.697834] pci_bus 0000:01: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697836] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Jun 10 11:14:59 turk kernel: [    0.697837] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
Jun 10 11:14:59 turk kernel: [    0.697839] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Jun 10 11:14:59 turk kernel: [    0.697841] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697843] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
Jun 10 11:14:59 turk kernel: [    0.697845] pci_bus 0000:04: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
Jun 10 11:14:59 turk kernel: [    0.697846] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jun 10 11:14:59 turk kernel: [    0.697848] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Jun 10 11:14:59 turk NetworkManager[984]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 10 11:14:59 turk kernel: [    0.697850] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jun 10 11:14:59 turk kernel: [    0.697852] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
Jun 10 11:14:59 turk kernel: [    0.697853] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
Jun 10 11:14:59 turk kernel: [    0.697855] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
Jun 10 11:14:59 turk kernel: [    0.697883] NET: Registered protocol family 2
Jun 10 11:14:59 turk kernel: [    0.697990] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 11:14:59 turk kernel: [    0.698869] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 10 11:14:59 turk kernel: [    0.701302] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 10 11:14:59 turk kernel: [    0.701606] TCP: Hash tables configured (established 524288 bind 65536)
Jun 10 11:14:59 turk kernel: [    0.701608] TCP reno registered
Jun 10 11:14:59 turk kernel: [    0.701615] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:14:59 turk kernel: [    0.701643] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Jun 10 11:14:59 turk kernel: [    0.701730] NET: Registered protocol family 1
Jun 10 11:14:59 turk kernel: [    0.701759] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.520037] pci 0000:00:12.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.520048] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.520089] pci 0000:00:12.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.520095] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.600038] pci 0000:00:13.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.600049] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.600089] pci 0000:00:13.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.600102] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.680033] pci 0000:00:14.5: PCI INT C disabled
Jun 10 11:14:59 turk kernel: [    1.680042] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    1.760040] pci 0000:00:16.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    1.760050] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    1.760090] pci 0000:00:16.2: PCI INT B disabled
Jun 10 11:14:59 turk kernel: [    1.760109] pci 0000:01:00.0: Boot video device
Jun 10 11:14:59 turk kernel: [    1.760125] PCI: CLS 64 bytes, default 64
Jun 10 11:14:59 turk kernel: [    1.761382] PCI-DMA: Disabling AGP.
Jun 10 11:14:59 turk kernel: [    1.761455] PCI-DMA: aperture base @ c4000000 size 65536 KB
Jun 10 11:14:59 turk kernel: [    1.761456] PCI-DMA: using GART IOMMU.
Jun 10 11:14:59 turk kernel: [    1.761458] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Jun 10 11:14:59 turk kernel: [    1.764901] IBS: LVT offset 1 assigned
Jun 10 11:14:59 turk kernel: [    1.764918] perf: AMD IBS detected (0x0000001f)
Jun 10 11:14:59 turk kernel: [    1.765030] audit: initializing netlink socket (disabled)
Jun 10 11:14:59 turk kernel: [    1.765044] type=2000 audit(1339323277.760:1): initialized
Jun 10 11:14:59 turk kernel: [    1.789108] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jun 10 11:14:59 turk kernel: [    1.808128] VFS: Disk quotas dquot_6.5.2
Jun 10 11:14:59 turk kernel: [    1.808170] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 10 11:14:59 turk kernel: [    1.808592] fuse init (API version 7.17)
Jun 10 11:14:59 turk kernel: [    1.808657] msgmni has been set to 7901
Jun 10 11:14:59 turk kernel: [    1.808983] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 11:14:59 turk kernel: [    1.809010] io scheduler noop registered
Jun 10 11:14:59 turk kernel: [    1.809011] io scheduler deadline registered
Jun 10 11:14:59 turk kernel: [    1.809032] io scheduler cfq registered (default)
Jun 10 11:14:59 turk kernel: [    1.809153] pcieport 0000:00:02.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809182] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809261] pcieport 0000:00:07.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809279] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809345] pcieport 0000:00:09.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809363] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809423] pcieport 0000:00:0a.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    1.809441] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    1.809493] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 11:14:59 turk kernel: [    1.809510] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 11:14:59 turk kernel: [    1.809602] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jun 10 11:14:59 turk kernel: [    1.809606] ACPI: Power Button [PWRB]
Jun 10 11:14:59 turk kernel: [    1.809634] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 11:14:59 turk kernel: [    1.809636] ACPI: Power Button [PWRF]
Jun 10 11:14:59 turk kernel: [    1.993031] ERST: Table is not found!
Jun 10 11:14:59 turk kernel: [    1.993033] GHES: HEST is not enabled!
Jun 10 11:14:59 turk kernel: [    1.993117] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jun 10 11:14:59 turk kernel: [    2.013530] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:14:59 turk kernel: [    2.060779] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 10 11:14:59 turk kernel: [    2.104211] Linux agpgart interface v0.103
Jun 10 11:14:59 turk kernel: [    2.105254] brd: module loaded
Jun 10 11:14:59 turk kernel: [    2.105789] loop: module loaded
Jun 10 11:14:59 turk kernel: [    2.105926] ahci 0000:00:11.0: version 3.0
Jun 10 11:14:59 turk kernel: [    2.105935] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    2.105982] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    2.106051] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
Jun 10 11:14:59 turk kernel: [    2.106054] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jun 10 11:14:59 turk kernel: [    2.106458] scsi0 : ahci
Jun 10 11:14:59 turk kernel: [    2.106521] scsi1 : ahci
Jun 10 11:14:59 turk kernel: [    2.106570] scsi2 : ahci
Jun 10 11:14:59 turk kernel: [    2.106619] scsi3 : ahci
Jun 10 11:14:59 turk kernel: [    2.106685] ata1: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd00 irq 44
Jun 10 11:14:59 turk kernel: [    2.106687] ata2: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffd80 irq 44
Jun 10 11:14:59 turk kernel: [    2.106690] ata3: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe00 irq 44
Jun 10 11:14:59 turk kernel: [    2.106692] ata4: SATA max UDMA/133 abar m1024@0xfbfffc00 port 0xfbfffe80 irq 44
Jun 10 11:14:59 turk kernel: [    2.106820] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.106837] pata_acpi 0000:00:14.1: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.106907] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.106926] pata_acpi 0000:03:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.106935] pata_acpi 0000:03:00.0: PCI INT A disabled
Jun 10 11:14:59 turk kernel: [    2.107227] Fixed MDIO Bus: probed
Jun 10 11:14:59 turk kernel: [    2.107241] tun: Universal TUN/TAP device driver, 1.6
Jun 10 11:14:59 turk kernel: [    2.107242] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 11:14:59 turk kernel: [    2.107279] PPP generic driver version 2.4.2
Jun 10 11:14:59 turk kernel: [    2.107346] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 11:14:59 turk kernel: [    2.107385] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.107395] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.107430] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Jun 10 11:14:59 turk kernel: [    2.107437] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.107450] QUIRK: Enable AMD PLL fix
Jun 10 11:14:59 turk kernel: [    2.107460] ehci_hcd 0000:00:12.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.107476] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff800
Jun 10 11:14:59 turk kernel: [    2.116041] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.116140] hub 1-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.116143] hub 1-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.116248] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.116260] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.116292] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Jun 10 11:14:59 turk kernel: [    2.116298] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.116314] ehci_hcd 0000:00:13.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.116325] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfbfff400
Jun 10 11:14:59 turk kernel: [    2.128034] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.128126] hub 2-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.128129] hub 2-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.128244] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.128255] ehci_hcd 0000:00:16.2: EHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.128288] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Jun 10 11:14:59 turk kernel: [    2.128294] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jun 10 11:14:59 turk kernel: [    2.128310] ehci_hcd 0000:00:16.2: debug port 1
Jun 10 11:14:59 turk kernel: [    2.128320] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfbfff000
Jun 10 11:14:59 turk kernel: [    2.140033] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Jun 10 11:14:59 turk kernel: [    2.140124] hub 3-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.140127] hub 3-0:1.0: 4 ports detected
Jun 10 11:14:59 turk kernel: [    2.140199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 11:14:59 turk kernel: [    2.140255] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.140267] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.140299] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Jun 10 11:14:59 turk kernel: [    2.140321] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfbffe000
Jun 10 11:14:59 turk kernel: [    2.200100] hub 4-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.200106] hub 4-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.200210] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.200223] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.200261] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Jun 10 11:14:59 turk kernel: [    2.200273] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffd000
Jun 10 11:14:59 turk kernel: [    2.260095] hub 5-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.260101] hub 5-0:1.0: 5 ports detected
Jun 10 11:14:59 turk kernel: [    2.260203] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.260215] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.260246] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
Jun 10 11:14:59 turk kernel: [    2.260259] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbffc000
Jun 10 11:14:59 turk kernel: [    2.320116] hub 6-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.320121] hub 6-0:1.0: 2 ports detected
Jun 10 11:14:59 turk kernel: [    2.320224] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.320236] ohci_hcd 0000:00:16.0: OHCI Host Controller
Jun 10 11:14:59 turk kernel: [    2.320268] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
Jun 10 11:14:59 turk kernel: [    2.320281] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfbff7000
Jun 10 11:14:59 turk kernel: [    2.380117] hub 7-0:1.0: USB hub found
Jun 10 11:14:59 turk kernel: [    2.380122] hub 7-0:1.0: 4 ports detected
Jun 10 11:14:59 turk kernel: [    2.380184] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 11:14:59 turk kernel: [    2.380232] usbcore: registered new interface driver libusual
Jun 10 11:14:59 turk kernel: [    2.380256] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jun 10 11:14:59 turk kernel: [    2.380611] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 11:14:59 turk kernel: [    2.380616] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 11:14:59 turk kernel: [    2.380723] mousedev: PS/2 mouse device common for all mice
Jun 10 11:14:59 turk kernel: [    2.380836] rtc_cmos 00:03: RTC can wake from S4
Jun 10 11:14:59 turk kernel: [    2.380915] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jun 10 11:14:59 turk kernel: [    2.380937] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jun 10 11:14:59 turk kernel: [    2.380989] device-mapper: uevent: version 1.0.3
Jun 10 11:14:59 turk kernel: [    2.381037] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Jun 10 11:14:59 turk kernel: [    2.381042] cpuidle: using governor ladder
Jun 10 11:14:59 turk kernel: [    2.381043] cpuidle: using governor menu
Jun 10 11:14:59 turk kernel: [    2.381045] EFI Variables Facility v0.08 2004-May-17
Jun 10 11:14:59 turk kernel: [    2.381188] TCP cubic registered
Jun 10 11:14:59 turk kernel: [    2.381253] NET: Registered protocol family 10
Jun 10 11:14:59 turk kernel: [    2.381558] NET: Registered protocol family 17
Jun 10 11:14:59 turk kernel: [    2.381568] Registering the dns_resolver key type
Jun 10 11:14:59 turk kernel: [    2.381679] PM: Hibernation image not present or could not be loaded.
Jun 10 11:14:59 turk kernel: [    2.381686] registered taskstats version 1
Jun 10 11:14:59 turk kernel: [    2.395990]   Magic number: 0:976:223
Jun 10 11:14:59 turk kernel: [    2.396100] rtc_cmos 00:03: setting system clock to 2012-06-10 10:14:39 UTC (1339323279)
Jun 10 11:14:59 turk kernel: [    2.396114] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
Jun 10 11:14:59 turk kernel: [    2.396140] powernow-k8:    0 : pstate 0 (3200 MHz)
Jun 10 11:14:59 turk kernel: [    2.396142] powernow-k8:    1 : pstate 1 (2500 MHz)
Jun 10 11:14:59 turk kernel: [    2.396143] powernow-k8:    2 : pstate 2 (2100 MHz)
Jun 10 11:14:59 turk kernel: [    2.396144] powernow-k8:    3 : pstate 3 (800 MHz)
Jun 10 11:14:59 turk kernel: [    2.396578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 11:14:59 turk kernel: [    2.396581] EDD information not available.
Jun 10 11:14:59 turk kernel: [    2.424051] ata4: SATA link down (SStatus 0 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.424100] ata3: SATA link down (SStatus 0 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.596033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.597154] ata1.00: ATA-8: ST31000528AS, CC38, max UDMA/133
Jun 10 11:14:59 turk kernel: [    2.597156] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 10 11:14:59 turk kernel: [    2.598425] ata1.00: configured for UDMA/133
Jun 10 11:14:59 turk kernel: [    2.598564] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
Jun 10 11:14:59 turk kernel: [    2.598693] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 11:14:59 turk kernel: [    2.598697] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 10 11:14:59 turk kernel: [    2.598775] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 11:14:59 turk kernel: [    2.598777] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 11:14:59 turk kernel: [    2.598819] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 11:14:59 turk kernel: [    2.600042] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 11:14:59 turk kernel: [    2.601666] ata2.00: ATAPI: Optiarc DVD RW AD-7260S, 1.01, max UDMA/100
Jun 10 11:14:59 turk kernel: [    2.603559] ata2.00: configured for UDMA/100
Jun 10 11:14:59 turk kernel: [    2.605370] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.01 PQ: 0 ANSI: 5
Jun 10 11:14:59 turk kernel: [    2.607489] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 11:14:59 turk kernel: [    2.607491] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun 10 11:14:59 turk kernel: [    2.607589] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 10 11:14:59 turk kernel: [    2.607652] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 10 11:14:59 turk kernel: [    2.655836]  sda: sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
Jun 10 11:14:59 turk kernel: [    2.656338] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 11:14:59 turk kernel: [    2.657404] Freeing unused kernel memory: 920k freed
Jun 10 11:14:59 turk kernel: [    2.657567] Write protecting the kernel read-only data: 12288k
Jun 10 11:14:59 turk kernel: [    2.661515] Freeing unused kernel memory: 1608k freed
Jun 10 11:14:59 turk kernel: [    2.664699] Freeing unused kernel memory: 1196k freed
Jun 10 11:14:59 turk kernel: [    2.692069] usb 4-1: new low-speed USB device number 2 using ohci_hcd
Jun 10 11:14:59 turk kernel: [    2.694791] firewire_ohci 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [    2.694799] firewire_ohci 0000:02:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696251] pata_via 0000:03:00.0: version 0.3.4
Jun 10 11:14:59 turk kernel: [    2.696266] pata_via 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 11:14:59 turk kernel: [    2.696317] pata_via 0000:03:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696548] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 11:14:59 turk kernel: [    2.696559] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [    2.696578] r8169 0000:04:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [    2.696617] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
Jun 10 11:14:59 turk kernel: [    2.696894] r8169 0000:04:00.0: eth0: RTL8168e/8111e at 0xffffc90000660000, 20:cf:30:19:d1:3c, XID 0c100000 IRQ 45
Jun 10 11:14:59 turk kernel: [    2.696896] r8169 0000:04:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jun 10 11:14:59 turk kernel: [    2.697191] scsi4 : pata_via
Jun 10 11:14:59 turk kernel: [    2.697286] scsi5 : pata_via
Jun 10 11:14:59 turk kernel: [    2.697419] ata5: PATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
Jun 10 11:14:59 turk kernel: [    2.697421] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
Jun 10 11:14:59 turk kernel: [    2.707832] scsi6 : pata_atiixp
Jun 10 11:14:59 turk kernel: [    2.707908] scsi7 : pata_atiixp
Jun 10 11:14:59 turk kernel: [    2.708355] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun 10 11:14:59 turk kernel: [    2.708357] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun 10 11:14:59 turk kernel: [    2.756092] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Jun 10 11:14:59 turk kernel: [    2.764045] Refined TSC clocksource calibration: 3214.276 MHz.
Jun 10 11:14:59 turk kernel: [    2.764050] Switching to clocksource tsc
Jun 10 11:14:59 turk kernel: [    3.030225] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input2
Jun 10 11:14:59 turk kernel: [    3.030314] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
Jun 10 11:14:59 turk kernel: [    3.030325] usbcore: registered new interface driver usbhid
Jun 10 11:14:59 turk kernel: [    3.030326] usbhid: USB HID core driver
Jun 10 11:14:59 turk kernel: [    3.124023] usb 4-2: new low-speed USB device number 3 using ohci_hcd
Jun 10 11:14:59 turk kernel: [    3.256079] firewire_core: created device fw0: GUID 001e8c0000db7e62, S400
Jun 10 11:14:59 turk kernel: [    3.306222] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input3
Jun 10 11:14:59 turk kernel: [    3.306290] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:12.0-2/input0
Jun 10 11:14:59 turk kernel: [    3.325129] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input4
Jun 10 11:14:59 turk kernel: [    3.325194] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:12.0-2/input1
Jun 10 11:14:59 turk kernel: [    3.383002] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
Jun 10 11:14:59 turk kernel: [    3.383005] EXT4-fs (sda7): write access will be enabled during recovery
Jun 10 11:14:59 turk kernel: [    4.183086] EXT4-fs (sda7): orphan cleanup on readonly fs
Jun 10 11:14:59 turk kernel: [    4.183093] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523360
Jun 10 11:14:59 turk kernel: [    4.183111] EXT4-fs (sda7): ext4_orphan_cleanup: deleting unreferenced inode 523359
Jun 10 11:14:59 turk kernel: [    4.183139] EXT4-fs (sda7): 2 orphan inodes deleted
Jun 10 11:14:59 turk kernel: [    4.183141] EXT4-fs (sda7): recovery complete
Jun 10 11:14:59 turk kernel: [    4.418346] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:14:59 turk kernel: [   15.482395] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:14:59 turk kernel: [   15.525140] lp: driver loaded but no devices found
Jun 10 11:14:59 turk kernel: [   15.526617] Adding 1952764k swap on /dev/sda5.  Priority:-1 extents:1 across:1952764k 
Jun 10 11:14:59 turk kernel: [   15.538254] wmi: Mapper loaded
Jun 10 11:14:59 turk kernel: [   15.560562] parport_pc 00:06: reported by Plug and Play ACPI
Jun 10 11:14:59 turk kernel: [   15.560611] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 10 11:14:59 turk kernel: [   15.568947] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMRG [io 0xb00-0xb2f]
Jun 10 11:14:59 turk kernel: [   15.568950] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jun 10 11:14:59 turk kernel: [   15.569170] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Jun 10 11:14:59 turk kernel: [   15.569230] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Jun 10 11:14:59 turk kernel: [   15.580429] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 11:14:59 turk kernel: [   15.588674] MCE: In-kernel MCE decoding enabled.
Jun 10 11:14:59 turk kernel: [   15.589169] EDAC MC: Ver: 2.1.0
Jun 10 11:14:59 turk kernel: [   15.590594] AMD64 EDAC driver v3.4.0
Jun 10 11:14:59 turk kernel: [   15.594282] type=1400 audit(1339323292.694:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.594641] type=1400 audit(1339323292.694:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.594830] type=1400 audit(1339323292.694:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=531 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   15.633249] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
Jun 10 11:14:59 turk kernel: [   15.633332] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
Jun 10 11:14:59 turk kernel: [   15.633377] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
Jun 10 11:14:59 turk kernel: [   15.633429] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
Jun 10 11:14:59 turk kernel: [   15.633472] input: HDA ATI SB Line-Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
Jun 10 11:14:59 turk kernel: [   15.633514] input: HDA ATI SB Line-Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Jun 10 11:14:59 turk kernel: [   15.633556] input: HDA ATI SB Line-Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Jun 10 11:14:59 turk kernel: [   15.633595] input: HDA ATI SB Line-Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Jun 10 11:14:59 turk kernel: [   15.636834] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 11:14:59 turk kernel: [   15.636837] hda_intel: Disabling MSI
Jun 10 11:14:59 turk kernel: [   15.636868] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [   15.639563] EDAC amd64: DRAM ECC disabled.
Jun 10 11:14:59 turk kernel: [   15.639570] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 10 11:14:59 turk kernel: [   15.639571]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 10 11:14:59 turk kernel: [   15.639572]  (Note that use of the override may cause unknown side effects.)
Jun 10 11:14:59 turk kernel: [   15.653340] ppdev: user-space parallel port driver
Jun 10 11:14:59 turk kernel: [   15.656294] lp0: using parport0 (interrupt-driven).
Jun 10 11:14:59 turk kernel: [   16.225120] nvidia: module license 'NVIDIA' taints kernel.
Jun 10 11:14:59 turk kernel: [   16.225123] Disabling lock debugging due to kernel taint
Jun 10 11:14:59 turk kernel: [   16.476019] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.500034] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.524010] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.552035] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jun 10 11:14:59 turk kernel: [   16.552103] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
Jun 10 11:14:59 turk kernel: [   16.552171] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
Jun 10 11:14:59 turk kernel: [   16.552222] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
Jun 10 11:14:59 turk kernel: [   16.552267] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
Jun 10 11:14:59 turk kernel: [   16.552619] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 10 11:14:59 turk kernel: [   16.552627] nvidia 0000:01:00.0: setting latency timer to 64
Jun 10 11:14:59 turk kernel: [   16.552630] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 10 11:14:59 turk kernel: [   16.552781] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.49  Mon Apr 30 23:46:33 PDT 2012
Jun 10 11:14:59 turk kernel: [   16.859334] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun 10 11:14:59 turk kernel: [   16.859337] vesafb: scrolling: redraw
Jun 10 11:14:59 turk kernel: [   16.859339] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun 10 11:14:59 turk kernel: [   16.863621] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
Jun 10 11:14:59 turk kernel: [   16.863763] Console: switching to colour frame buffer device 80x30
Jun 10 11:14:59 turk kernel: [   16.863773] fb0: VESA VGA frame buffer device
Jun 10 11:14:59 turk NetworkManager[984]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk kernel: [   17.352445] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
Jun 10 11:14:59 turk kernel: [   19.931462] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Jun 10 11:14:59 turk kernel: [   22.258243] init: failsafe main process (929) killed by TERM signal
Jun 10 11:14:59 turk kernel: [   22.527430] Bluetooth: Core ver 2.16
Jun 10 11:14:59 turk kernel: [   22.527503] NET: Registered protocol family 31
Jun 10 11:14:59 turk kernel: [   22.527505] Bluetooth: HCI device and connection manager initialized
Jun 10 11:14:59 turk kernel: [   22.527507] Bluetooth: HCI socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.527508] Bluetooth: L2CAP socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.527537] Bluetooth: SCO socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.534871] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 10 11:14:59 turk kernel: [   22.534874] Bluetooth: BNEP filters: protocol multicast
Jun 10 11:14:59 turk kernel: [   22.535079] Bluetooth: RFCOMM TTY layer initialized
Jun 10 11:14:59 turk kernel: [   22.535085] Bluetooth: RFCOMM socket layer initialized
Jun 10 11:14:59 turk kernel: [   22.535086] Bluetooth: RFCOMM ver 1.11
Jun 10 11:14:59 turk kernel: [   22.535256] type=1400 audit(1339323299.634:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=997 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.535728] type=1400 audit(1339323299.634:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=997 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549237] type=1400 audit(1339323299.650:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549647] type=1400 audit(1339323299.650:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1032 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.549873] type=1400 audit(1339323299.650:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.550085] type=1400 audit(1339323299.650:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1033 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.551872] type=1400 audit(1339323299.650:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1038 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.552333] type=1400 audit(1339323299.654:12): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1038 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.552511] type=1400 audit(1339323299.654:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1040 comm="apparmor_parser"
Jun 10 11:14:59 turk kernel: [   22.554587] type=1400 audit(1339323299.654:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1036 comm="apparmor_parser"
Jun 10 11:14:59 turk NetworkManager[984]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <info> Networking is enabled by state file
Jun 10 11:14:59 turk NetworkManager[984]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): carrier is OFF
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): now managed
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): bringing up device.
Jun 10 11:14:59 turk acpid: starting up with proc fs
Jun 10 11:14:59 turk cron[1102]: (CRON) INFO (pidfile fd = 3)
Jun 10 11:14:59 turk acpid: 35 rules loaded
Jun 10 11:14:59 turk acpid: waiting for events: event logging is off
Jun 10 11:14:59 turk anacron[1127]: Anacron 2.3 started on 2012-06-10
Jun 10 11:14:59 turk cron[1128]: (CRON) STARTUP (fork ok)
Jun 10 11:14:59 turk cron[1128]: (CRON) INFO (Running @reboot jobs)
Jun 10 11:14:59 turk anacron[1127]: Normal exit (0 jobs run)
Jun 10 11:14:59 turk kernel: [   22.723984] vboxdrv: Found 4 processor cores.
Jun 10 11:14:59 turk acpid: client connected from 1154[0:0]
Jun 10 11:14:59 turk acpid: 1 client rule loaded
Jun 10 11:14:59 turk kernel: [   22.724228] vboxdrv: fAsync=0 offMin=0x396 offMax=0x1600
Jun 10 11:14:59 turk kernel: [   22.724279] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jun 10 11:14:59 turk kernel: [   22.724280] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
Jun 10 11:14:59 turk kernel: [   22.739160] vboxpci: IOMMU not found (not registered)
Jun 10 11:14:59 turk kernel: [   22.787486] r8169 0000:04:00.0: eth0: link down
Jun 10 11:14:59 turk kernel: [   22.787499] r8169 0000:04:00.0: eth0: link down
Jun 10 11:14:59 turk kernel: [   22.787830] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): preparing device.
Jun 10 11:14:59 turk NetworkManager[984]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 10 11:14:59 turk NetworkManager[984]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:0a.0/0000:04:00.0/net/eth0
Jun 10 11:14:59 turk kernel: [   22.788148] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 10 11:15:00 turk anacron[1262]: Anacron 2.3 started on 2012-06-10
Jun 10 11:15:00 turk anacron[1262]: Normal exit (0 jobs run)
Jun 10 11:15:00 turk udev-configure-printer: add /devices/pnp0/00:06/printer/lp0
Jun 10 11:15:00 turk udev-configure-printer: Failed to get parent
Jun 10 11:15:00 turk udev-configure-printer: add /module/lp
Jun 10 11:15:00 turk udev-configure-printer: Failed to get parent
Jun 10 11:15:01 turk acpid: client connected from 1154[0:0]
Jun 10 11:15:01 turk acpid: 1 client rule loaded
Jun 10 11:15:01 turk dbus[947]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun 10 11:15:01 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun 10 11:15:01 turk accounts-daemon[1397]: started daemon version 0.6.15
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): carrier now ON (device state 20)
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Auto-activating connection 'Wired connection 1'.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) starting connection 'Wired connection 1'
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 10 11:15:01 turk NetworkManager[984]: <info> dhclient started with pid 1401
Jun 10 11:15:01 turk kernel: [   24.408599] r8169 0000:04:00.0: eth0: link up
Jun 10 11:15:01 turk kernel: [   24.408950] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Beginning IP6 addrconf.
Jun 10 11:15:01 turk dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jun 10 11:15:01 turk dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jun 10 11:15:01 turk dhclient: All rights reserved.
Jun 10 11:15:01 turk dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 10 11:15:01 turk dhclient: 
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 10 11:15:01 turk dhclient: Listening on LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:15:01 turk dhclient: Sending on   LPF/eth0/20:cf:30:19:d1:3c
Jun 10 11:15:01 turk dhclient: Sending on   Socket/fallback
Jun 10 11:15:01 turk dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jun 10 11:15:01 turk dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67
Jun 10 11:15:01 turk dhclient: DHCPOFFER of 192.168.1.103 from 192.168.1.1
Jun 10 11:15:01 turk dbus[947]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun 10 11:15:01 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun 10 11:15:01 turk dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Jun 10 11:15:01 turk dhclient: bound to 192.168.1.103 -- renewal in 32725 seconds.
Jun 10 11:15:01 turk NetworkManager[984]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 10 11:15:01 turk NetworkManager[984]: <info>   address 192.168.1.103
Jun 10 11:15:01 turk NetworkManager[984]: <info>   prefix 24 (255.255.255.0)
Jun 10 11:15:01 turk NetworkManager[984]: <info>   gateway 192.168.1.1
Jun 10 11:15:01 turk NetworkManager[984]: <info>   nameserver '194.168.4.100'
Jun 10 11:15:01 turk NetworkManager[984]: <info>   nameserver '194.168.8.100'
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 10 11:15:01 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun 10 11:15:02 turk anacron[1610]: Anacron 2.3 started on 2012-06-10
Jun 10 11:15:02 turk anacron[1610]: Normal exit (0 jobs run)
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully called chroot.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully dropped privileges.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully limited resources.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Canary thread running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Watchdog thread running.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Successfully made thread 1736 of process 1736 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:15:02 turk rtkit-daemon[1738]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 11:15:02 turk NetworkManager[984]: <info> DNS: starting dnsmasq...
Jun 10 11:15:02 turk NetworkManager[984]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 10 11:15:02 turk dnsmasq[1743]: started, version 2.59 cache disabled
Jun 10 11:15:02 turk dnsmasq[1743]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 10 11:15:02 turk dnsmasq[1743]: using nameserver 194.168.8.100#53
Jun 10 11:15:02 turk dnsmasq[1743]: using nameserver 194.168.4.100#53
Jun 10 11:15:02 turk NetworkManager[984]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 10 11:15:02 turk NetworkManager[984]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun 10 11:15:02 turk NetworkManager[984]: <info> Activation (eth0) successful, device activated.
Jun 10 11:15:02 turk NetworkManager[984]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 10 11:15:02 turk dbus[947]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 10 11:15:02 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 10 11:15:03 turk rtkit-daemon[1738]: Successfully made thread 1822 of process 1736 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Successfully made thread 1823 of process 1736 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:15:03 turk rtkit-daemon[1738]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 11:15:04 turk dbus[947]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun 10 11:15:04 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun 10 11:15:11 turk ntpdate[1803]: adjust time server 91.189.94.4 offset -0.127551 sec
Jun 10 11:15:12 turk kernel: [   34.944007] eth0: no IPv6 routers present
Jun 10 11:15:19 turk goa[2141]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun 10 11:15:22 turk NetworkManager[984]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 10 11:15:22 turk NetworkManager[984]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 10 11:16:05 turk dbus[947]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun 10 11:16:05 turk AptDaemon: INFO: Initializing daemon
Jun 10 11:16:06 turk AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 10 11:16:06 turk dbus[947]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 10 11:16:06 turk AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 10 11:16:06 turk AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
Jun 10 11:16:06 turk AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
Jun 10 11:16:08 turk AptDaemon.PackageKit: INFO: Get updates()
Jun 10 11:16:09 turk AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/cd24acc474e84bab8eca13226f375149
```

---

### Post by Sunships on 2012-06-10
> **db260179 said:**
> Hi, your bios version is quite old. 1404, newest version is 1704

[http://uk.asus.com/Motherboards/AMD_AM3/M4A88TDM_EVOUSB3/#download](http://uk.asus.com/Motherboards/AMD_AM3/M4A88TDM_EVOUSB3/#download)

Unlikely reason for your problems but always good to keep up to date.

As you have tested your RAM and HDD, I would say your most likely problem now is the motherboard,cpu and power supply.

It is always good to buy a power supply tester. I had a faulty psu once which caused random crashing. What is the wattage rating? i.e. 500W?

In rare cases the cpu could be faulty. I find the motherboard and psu are the usual suspects.

I recommend you buy a power tester first, then a motherboard - hopefully one will resolve your issue.

Hope this helps you?

And good luck!

Thanks db260179!! 

My power supply is 600W. I will try updating the BIOS first, and then look into testing the power supply if that doesn't help, as you suggest.

Thanks for replying!

---

### Post by ahallubuntu on 2012-06-10
The graphics card consumes more power and puts more stress on the power supply, so if the power supply is on the verge of failing, just having it plugged in could make it worse.  Or, the graphics card itself could be bad.

Sometimes even a power supply tester won't show that it is bad.  Power supplies can fail in a variety of ways.  I have had at least one that looked fine on a tester fail under load.  The only way I verified that the power supply was the issue was by swapping it with another one.  I look for replacement power supplies on sale and buy them cheap - it's nice to have a spare sitting around.  Name brands are best though.  I prefer not to get no-name generic power supplies.

FYI, from what you said above, it's not clear whether you ran the CPU stress tester properly.  It's not something you run for just one or two seconds - you should let it run for ten minutes and let the CPU get really hot.  (When the CPU is running at full speed, not only will it get hot, it will also draw a lot more power than when idle.)  Start the test and test status should print every few seconds; it may take longer to print the next prime number each time.  That's OK; just tap the Enter key to make sure the system hasn't locked up.

---

### Post by Sunships on 2012-06-10
> **ahallubuntu said:**
> 
FYI, from what you said above, it's not clear whether you ran the CPU stress tester properly.  It's not something you run for just one or two seconds - you should let it run for ten minutes and let the CPU get really hot.  (When the CPU is running at full speed, not only will it get hot, it will also draw a lot more power than when idle.)  Start the test and test status should print every few seconds; it may take longer to print the next prime number each time.  That's OK; just tap the Enter key to make sure the system hasn't locked up.

Hi  again ahallubuntu, I left the CPU test for about ten to fifteen minutes the first time - what is in the screenshot above is all that appears. The cursor flashes, does not move to a new line when I press enter, and no test updates are printed on screen as you mention. This happens with all three of the CPU tests I have tried. does this mean the problem is with the cpu?

---

### Post by ahallubuntu on 2012-06-10
It could mean the CPU is overheating and locking up.  Or again, it could mean the power supply is bad; a flaky power supply can cause system lockups like this, and the CPU running at full power puts a heavier load on the power supply.

CPUs can fail but it's highly unusual especially in the scenario you describe.  A CPU should either fail completely or not fail.

It could mean the test is incompatible with your CPU, though I've never had that problem with any system I've tried to run these tests on.  You've tried several tests, too.  So I'd guess that isn't the issue.

---

### Post by Sunships on 2012-06-10
> **ahallubuntu said:**
> It could mean the CPU is overheating and locking up.  Or again, it could mean the power supply is bad; a flaky power supply can cause system lockups like this, and the CPU running at full power puts a heavier load on the power supply.

CPUs can fail but it's highly unusual especially in the scenario you describe.  A CPU should either fail completely or not fail.

It could mean the test is incompatible with your CPU, though I've never had that problem with any system I've tried to run these tests on.  You've tried several tests, too.  So I'd guess that isn't the issue.

It's an AMD CPU...nothing too unusual, I don't think. I have just updated the BIOS, and put the graphics card back in to see if this still provokes crashes. If this update hasn't settled the issue then I will present the various results to my retailer and see what they say. I think many of my components are still under warranty, so fingers crossed I can get a replacement.

Thanks for your time and considerate replies, everyone. I'll hopefully be able to post a positive update and mark this thread solved very soon :)

---

### Post by Sunships on 2012-07-27
Hello again! Updating the BIOS didn't solve any problems, and a PSU tester gadget didn't show any errors either. 

On the advice of my components retailer I took my system to my local computer repair shop, who told me that the RAM was faulty - despite it not producing errors in memtest. I had the RAM replaced twice, and this did not solve the problem - funnily enough, although I didn't see any errors with the first set of RAM (see previous posts above) both the replacement sets of RAM did give errors in memtest - LOTS of errors, like 100000s-1000000s of errors if left to run overnight.

This in turn led me to believe that either the motherboard or processor was faulty. With Google-searching indicating the motherboard as being the much more likely candidate to fail I returned this under RMA for testing, and it passed with no faults, leaving only the CPU to send back. 

Before doing so, I thought I may as well clean off and replace the thermal paste, and see if that had any effect, since I was going to be dismantling the whole thing anyway. I had dreaded doing this, but reassembling it all was much, much more easy than when I first set up the system. Anyway, I replaced the existing paste which came pre-applied to the heat sink with some Arctic MX-3 and lo and behold, the system has not crashed since! I'm still using the same replacement RAM that gave me millions of errors too! 

I haven't run memtest again yet, but may do so just to see if I do get any errors. For now, I am just counting my blessings!

**TL, DR; suspected RAM issue turns out to be fixed by application of fresh thermal paste. Hooray!**

---


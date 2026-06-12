---
title: "ThinkPad R52 heats up extensively and then shuts down hard"
date: 2010-10-29
forum: Hardware
---

### Post by olafurg on 2010-10-29
Having some trouble with a friend's computer. Just replaced Windows Vista with Ubuntu 10.10 and it's giving us some trouble. It keeps randomly shutting down, definitely connected to some heat issues. No problem whatsoever before, running Vista.

So here's the situation.
[LIST=1]
[*]Turn on the computer.
[*]Do stuff, install programs etc.
[*]Heat gets up to 80-90°C as we've noticed, more heat depending on the hard work given to it.
[*]Eventually a hard shutdown and the computer feels really hot.
[/LIST]

The fan seems to be working, gets on and everything. 

Please help with this as it's my friend's first experience with Ubuntu and I'd rather not fail this experiment with some strange problem like this. This should be basic stuff.

If more info needed, please let me know.

Thanks a lot.

Here's a part of the syslog file:

```
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Quiting due to inactivity
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Shutdown was requested
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Initializing daemon
Oct 29 19:03:29 jakob-R52 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'wine1.2')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Oct 29 19:03:33 jakob-R52 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:33 jakob-R52 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:35 jakob-R52 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:36 jakob-R52 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'wine1.2')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Oct 29 19:07:42 jakob-R52 pulseaudio[1439]: ratelimit.c: 1 events suppressed
Oct 29 19:13:30 jakob-R52 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:15:54 jakob-R52 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'skysentials')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Oct 29 19:16:00 jakob-R52 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:00 jakob-R52 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:02 jakob-R52 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:03 jakob-R52 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'skysentials')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.587748] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.587752] Disabling lock debugging due to kernel taint
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.588312] CPU0: Core temperature/speed normal
Oct 29 19:16:07 jakob-R52 kernel: [ 6184.435746] Critical temperature reached (100 C), shutting down.
Oct 29 19:16:07 jakob-R52 kernel: Kernel logging (proc) stopped.
Oct 29 19:16:08 jakob-R52 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="714" x-info="http://www.rsyslog.com"] exiting on signal 15.
Oct 29 19:18:36 jakob-R52 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 29 19:18:36 jakob-R52 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="661" x-info="http://www.rsyslog.com"] (re)start
Oct 29 19:18:36 jakob-R52 rsyslogd: rsyslogd's groupid changed to 103
Oct 29 19:18:36 jakob-R52 rsyslogd: rsyslogd's userid changed to 101
Oct 29 19:18:35 jakob-R52 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fef5000 (ACPI data)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003fef5000 - 000000003ff00000 (ACPI NVS)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] DMI present.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x100000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR default type: uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   00000-9FFFF write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   D0000-DBFFF uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DC000-DFFFF write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   E0000-FFFFF write-protect
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR variable ranges enabled:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   1 base 03FF00000 mask FFFF00000 uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   2 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   3 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   4 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   5 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   6 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   7 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PAT not supported by CPU.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] modified physical RAM map:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000100000 - 000000003fee0000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003fee0000 - 000000003fef5000 (ACPI data)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003fef5000 - 000000003ff00000 (ACPI NVS)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003ff00000 - 0000000040000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] RAMDISK: 2f523000 - 2ff68000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: RSDP 000f6bf0 00024 (v02 IBM   )
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: XSDT 3fee701e 0005C (v01 IBM    TP-76    00001080  LTP 00000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: FACP 3fee7100 000F4 (v03 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20100428/tbfadt-526)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20100428/tbfadt-557)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: DSDT 3fee72e7 0DADC (v01 IBM    TP-76    00001080 MSFT 0100000E)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: FACS 3fef6000 00040
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: SSDT 3fee72b4 00033 (v01 IBM    TP-76    00001080 MSFT 0100000E)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: ECDT 3fef4dc3 00052 (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: TCPA 3fef4e15 00032 (v01 IBM    TP-76    00001080 PTL  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: APIC 3fef4e47 0005A (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: MCFG 3fef4ea1 0003E (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: BOOT 3fef4fd8 00028 (v01 IBM    TP-76    00001080  LTP 00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 134MB HIGHMEM available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 887MB LOWMEM available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   low ram: 0 - 377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Zone PFN ranges:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003fee0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Movable zone start PFN for each node
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000100 -> 0x0003fee0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] On node 0 totalpages: 261744
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001020
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem zone: 270 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem zone: 34260 pages, LIFO batch:7
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Using APIC driver default
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] nr_irqs_gsi: 40
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u4194304
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] pcpu-alloc: [0] 0 
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259698
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e83319a1-12bf-4690-8876-33491fab41f4 ro quiet splash
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing CPU#0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] allocated 5237100 bytes of page_cgroup
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Subtract (49 early reservations)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #3 [002f523000 - 002ff68000]         RAMDISK
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #4 [000009f000 - 0000100000]   BIOS reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #5 [00009a1000 - 00009a4128]             BRK
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #10 [0001001000 - 0001801000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #11 [0001801000 - 0001801004]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #12 [0001801040 - 0001801100]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #13 [0001801100 - 0001801154]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #14 [0001801180 - 0001804180]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #15 [0001804180 - 0001804190]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #16 [00018041c0 - 0001804dc0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #17 [0001804dc0 - 0001804de7]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #18 [0001804e00 - 0001804ff8]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #19 [0001805000 - 0001805040]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #20 [0001805040 - 0001805080]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #21 [0001805080 - 00018050c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #22 [00018050c0 - 0001805100]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #23 [0001805100 - 0001805140]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #24 [0001805140 - 0001805180]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #25 [0001805180 - 00018051c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #26 [00018051c0 - 0001805200]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #27 [0001805200 - 0001805240]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #28 [0001805240 - 0001805280]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #29 [0001805280 - 00018052c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #30 [00018052c0 - 0001805300]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #31 [0001805300 - 0001805340]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #32 [0001805340 - 0001805380]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #33 [0001805380 - 00018053c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #34 [00018053c0 - 00018053d0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #35 [0001805400 - 0001805410]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #36 [0001805440 - 00018054aa]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #37 [00018054c0 - 000180552a]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #38 [0001c00000 - 0001c0e000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #39 [0001807540 - 0001807544]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #40 [0001807580 - 0001807584]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #41 [00018075c0 - 00018075c4]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #42 [0001807600 - 0001807604]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #43 [0001807640 - 00018076f0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #44 [0001807700 - 00018077a8]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #45 [00018077c0 - 000180b7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #46 [000180b7c0 - 000188b7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #47 [000188b7c0 - 00018cb7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #48 [0001c0e000 - 000210c96c]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003fee0)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Memory: 1013404k/1047424k available (4928k kernel code, 33572k reserved, 2336k data, 684k init, 138120k highmem)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] virtual kernel memory layout:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Hierarchical RCU implementation.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Extended CMOS year: 2000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] console [tty0] enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Fast TSC calibration using PIT
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Detected 798.153 MHz processor.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1596.30 BogoMIPS (lpj=3192612)
Oct 29 19:18:36 jakob-R52 kernel: [    0.008020] pid_max: default: 32768 minimum: 301
Oct 29 19:18:36 jakob-R52 kernel: [    0.008067] Security Framework initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.008106] AppArmor: AppArmor initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.008111] Yama: becoming mindful.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008239] Mount-cache hash table entries: 512
Oct 29 19:18:36 jakob-R52 kernel: [    0.008502] Initializing cgroup subsys ns
Oct 29 19:18:36 jakob-R52 kernel: [    0.008511] Initializing cgroup subsys cpuacct
Oct 29 19:18:36 jakob-R52 kernel: [    0.008522] Initializing cgroup subsys memory
Oct 29 19:18:36 jakob-R52 kernel: [    0.008545] Initializing cgroup subsys devices
Oct 29 19:18:36 jakob-R52 kernel: [    0.008551] Initializing cgroup subsys freezer
Oct 29 19:18:36 jakob-R52 kernel: [    0.008557] Initializing cgroup subsys net_cls
Oct 29 19:18:36 jakob-R52 kernel: [    0.008619] mce: CPU supports 5 MCE banks
Oct 29 19:18:36 jakob-R52 kernel: [    0.008637] CPU0: Thermal monitoring enabled (TM2)
Oct 29 19:18:36 jakob-R52 kernel: [    0.008652] Performance Events: p6 PMU driver.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008670] ... version:                0
Oct 29 19:18:36 jakob-R52 kernel: [    0.008675] ... bit width:              32
Oct 29 19:18:36 jakob-R52 kernel: [    0.008680] ... generic registers:      2
Oct 29 19:18:36 jakob-R52 kernel: [    0.008685] ... value mask:             00000000ffffffff
Oct 29 19:18:36 jakob-R52 kernel: [    0.008691] ... max period:             000000007fffffff
Oct 29 19:18:36 jakob-R52 kernel: [    0.008697] ... fixed-purpose events:   0
Oct 29 19:18:36 jakob-R52 kernel: [    0.008702] ... event mask:             0000000000000003
Oct 29 19:18:36 jakob-R52 kernel: [    0.010558] SMP alternatives: switching to UP code
Oct 29 19:18:36 jakob-R52 kernel: [    0.027622] Freeing SMP alternatives: 24k freed
Oct 29 19:18:36 jakob-R52 kernel: [    0.027642] ACPI: Core revision 20100428
Oct 29 19:18:36 jakob-R52 kernel: [    0.056015] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 29 19:18:36 jakob-R52 kernel: [    0.056026] ftrace: allocating 21758 entries in 43 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.064096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 29 19:18:36 jakob-R52 kernel: [    0.064499] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 29 19:18:36 jakob-R52 kernel: [    0.105224] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Brought up 1 CPUs
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Total of 1 processors activated (1596.30 BogoMIPS).
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] devtmpfs: initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] regulator: core version 0.5
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Time: 19:18:22  Date: 10/29/10
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] NET: Registered protocol family 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.108153] EISA bus registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.108170] ACPI: bus type pci registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.108318] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.108328] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Oct 29 19:18:36 jakob-R52 kernel: [    0.108333] PCI: Using MMCONFIG for extended config space
Oct 29 19:18:36 jakob-R52 kernel: [    0.108338] PCI: Using configuration type 1 for base access
Oct 29 19:18:36 jakob-R52 kernel: [    0.110720] bio: create slab <bio-0> at 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.115738] ACPI: EC: EC description table is found, configuring boot EC
Oct 29 19:18:36 jakob-R52 kernel: [    0.147920] ACPI: Interpreter enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.147928] ACPI: (supports S0 S3 S4 S5)
Oct 29 19:18:36 jakob-R52 kernel: [    0.147989] ACPI: Using IOAPIC for interrupt routing
Oct 29 19:18:36 jakob-R52 kernel: [    0.168423] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Oct 29 19:18:36 jakob-R52 kernel: [    0.168526] ACPI: Power Resource [PUBS] (on)
Oct 29 19:18:36 jakob-R52 kernel: [    0.173871] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Oct 29 19:18:36 jakob-R52 kernel: [    0.173882] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Oct 29 19:18:36 jakob-R52 kernel: [    0.173942] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Oct 29 19:18:36 jakob-R52 kernel: [    0.174082] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174090] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174098] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174106] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174114] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174123] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174248] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174256] pci 0000:00:01.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174411] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174420] pci 0000:00:1c.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174541] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174550] pci 0000:00:1c.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174632] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174714] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174792] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174870] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174945] pci 0000:00:1d.7: reg 10: [mem 0xa8000000-0xa80003ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175020] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175030] pci 0000:00:1d.7: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175157] pci 0000:00:1e.2: reg 10: [io  0x1c00-0x1cff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175169] pci 0000:00:1e.2: reg 14: [io  0x1880-0x18bf]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175182] pci 0000:00:1e.2: reg 18: [mem 0xa8000800-0xa80009ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175196] pci 0000:00:1e.2: reg 1c: [mem 0xa8000400-0xa80004ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175245] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175253] pci 0000:00:1e.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175298] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175311] pci 0000:00:1e.3: reg 14: [io  0x2000-0x207f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175372] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175381] pci 0000:00:1e.3: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175492] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.175505] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Oct 29 19:18:36 jakob-R52 kernel: [    0.175515] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Oct 29 19:18:36 jakob-R52 kernel: [    0.175524] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
Oct 29 19:18:36 jakob-R52 kernel: [    0.175533] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef
Oct 29 19:18:36 jakob-R52 kernel: [    0.175584] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175597] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175609] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175621] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175634] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175678] pci 0000:00:1f.2: PME# supported from D3hot
Oct 29 19:18:36 jakob-R52 kernel: [    0.175687] pci 0000:00:1f.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175760] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175869] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175880] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175891] pci 0000:01:00.0: reg 18: [mem 0xa8100000-0xa810ffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175915] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175943] pci 0000:01:00.0: supports D1 D2
Oct 29 19:18:36 jakob-R52 kernel: [    0.175960] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 29 19:18:36 jakob-R52 kernel: [    0.175977] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175985] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175994] pci 0000:00:01.0:   bridge window [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176008] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176142] pci 0000:02:00.0: reg 10: [mem 0xa8200000-0xa820ffff 64bit]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176252] pci 0000:02:00.0: PME# supported from D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176262] pci 0000:02:00.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176290] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 29 19:18:36 jakob-R52 kernel: [    0.176310] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176319] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176330] pci 0000:00:1c.0:   bridge window [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176343] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176419] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176429] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176438] pci 0000:00:1c.2:   bridge window [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176452] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176539] pci 0000:04:00.0: reg 10: [mem 0xa8400000-0xa8400fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176575] pci 0000:04:00.0: supports D1 D2
Oct 29 19:18:36 jakob-R52 kernel: [    0.176581] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176591] pci 0000:04:00.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176665] pci 0000:04:02.0: reg 10: [mem 0xa8401000-0xa8401fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176753] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176763] pci 0000:04:02.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176841] pci 0000:00:1e.0: PCI bridge to [bus 04-07] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176851] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176861] pci 0000:00:1e.0:   bridge window [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176874] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176882] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176889] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176983] pci_bus 0000:00: on NUMA node 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.176995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.189797] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.190243] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.190684] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.191123] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.191562] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192020] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192462] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192900] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.193063] HEST: Table is not found!
Oct 29 19:18:36 jakob-R52 kernel: [    0.193227] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Oct 29 19:18:36 jakob-R52 kernel: [    0.193236] vgaarb: loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.193619] SCSI subsystem initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.193709] libata version 3.00 loaded.
Oct 29 19:18:36 jakob-R52 kernel: [    0.193834] usbcore: registered new interface driver usbfs
Oct 29 19:18:36 jakob-R52 kernel: [    0.193865] usbcore: registered new interface driver hub
Oct 29 19:18:36 jakob-R52 kernel: [    0.193927] usbcore: registered new device driver usb
Oct 29 19:18:36 jakob-R52 kernel: [    0.194219] ACPI: WMI: Mapper loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.194223] PCI: Using ACPI for IRQ routing
Oct 29 19:18:36 jakob-R52 kernel: [    0.194230] PCI: pci_cache_line_size set to 64 bytes
Oct 29 19:18:36 jakob-R52 kernel: [    0.194355] Expanded resource reserved due to conflict with Adapter ROM
Oct 29 19:18:36 jakob-R52 kernel: [    0.194364] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194371] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194377] reserve RAM buffer: 000000003fee0000 - 000000003fffffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194583] NetLabel: Initializing
Oct 29 19:18:36 jakob-R52 kernel: [    0.194588] NetLabel:  domain hash size = 128
Oct 29 19:18:36 jakob-R52 kernel: [    0.194592] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 29 19:18:36 jakob-R52 kernel: [    0.194621] NetLabel:  unlabeled traffic allowed by default
Oct 29 19:18:36 jakob-R52 kernel: [    0.194961] hpet clockevent registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.194970] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct 29 19:18:36 jakob-R52 kernel: [    0.194982] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.194994] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Oct 29 19:18:36 jakob-R52 kernel: [    0.200039] Switching to clocksource tsc
Oct 29 19:18:36 jakob-R52 kernel: [    0.224792] AppArmor: AppArmor Filesystem Enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.224827] pnp: PnP ACPI init
Oct 29 19:18:36 jakob-R52 kernel: [    0.224865] ACPI: bus type pnp registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.232767] pnp: PnP ACPI: found 14 devices
Oct 29 19:18:36 jakob-R52 kernel: [    0.232774] ACPI: ACPI bus type pnp unregistered
Oct 29 19:18:36 jakob-R52 kernel: [    0.232782] PnPBIOS: Disabled by ACPI PNP
Oct 29 19:18:36 jakob-R52 kernel: [    0.232810] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232819] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232828] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232836] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232844] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232852] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232860] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232869] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232877] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232885] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232893] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232901] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232909] system 00:00: [mem 0x00100000-0x3fffffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232918] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232936] system 00:02: [io  0x1000-0x107f] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232944] system 00:02: [io  0x1180-0x11bf] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232951] system 00:02: [io  0x15e0-0x15ef] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232959] system 00:02: [io  0x1600-0x1641] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232967] system 00:02: [io  0x1644-0x167f] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232975] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232983] system 00:02: [mem 0xf0008000-0xf000bfff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232991] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.233000] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.233008] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.271292] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271303] pci 0000:00:1c.0: BAR 13: assigned [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271313] pci 0000:01:00.0: BAR 6: assigned [mem 0xa8120000-0xa813ffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271321] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271328] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271337] pci 0000:00:01.0:   bridge window [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271346] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271356] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271364] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271376] pci 0000:00:1c.0:   bridge window [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271386] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271399] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271407] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271418] pci 0000:00:1c.2:   bridge window [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271428] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271444] pci 0000:04:00.0: BAR 15: assigned [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271452] pci 0000:04:00.0: BAR 16: assigned [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271459] pci 0000:04:00.0: BAR 13: assigned [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271466] pci 0000:04:00.0: BAR 14: assigned [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271473] pci 0000:04:00.0: CardBus bridge to [bus 05-06]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271479] pci 0000:04:00.0:   bridge window [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271490] pci 0000:04:00.0:   bridge window [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271501] pci 0000:04:00.0:   bridge window [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271512] pci 0000:04:00.0:   bridge window [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271522] pci 0000:00:1e.0: PCI bridge to [bus 04-07]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271530] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271541] pci 0000:00:1e.0:   bridge window [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271551] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271577]   alloc irq_desc for 16 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271582]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271595] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.271604] pci 0000:00:01.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271620]   alloc irq_desc for 20 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271625]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271635] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 29 19:18:36 jakob-R52 kernel: [    0.271644] pci 0000:00:1c.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271661]   alloc irq_desc for 22 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271666]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271674] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Oct 29 19:18:36 jakob-R52 kernel: [    0.271683] pci 0000:00:1c.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271698] pci 0000:00:1e.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271720] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.271732] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271739] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271746] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271753] pci_bus 0000:01: resource 1 [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271760] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271767] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271774] pci_bus 0000:02: resource 1 [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271781] pci_bus 0000:02: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271788] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271795] pci_bus 0000:03: resource 1 [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271802] pci_bus 0000:03: resource 2 [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271809] pci_bus 0000:04: resource 0 [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271816] pci_bus 0000:04: resource 1 [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271823] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271830] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271837] pci_bus 0000:04: resource 5 [mem 0x00000000-0xffffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271844] pci_bus 0000:05: resource 0 [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271850] pci_bus 0000:05: resource 1 [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271857] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271864] pci_bus 0000:05: resource 3 [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271952] NET: Registered protocol family 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.272099] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.272644] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274157] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274922] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274928] TCP reno registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.274936] UDP hash table entries: 512 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274962] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.275148] NET: Registered protocol family 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.275341] pci 0000:01:00.0: Boot video device
Oct 29 19:18:36 jakob-R52 kernel: [    0.275366] PCI: CLS 32 bytes, default 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.275506] Simple Boot Flag at 0x35 set to 0x1
Oct 29 19:18:36 jakob-R52 kernel: [    0.275711] cpufreq-nforce2: No nForce2 chipset.
Oct 29 19:18:36 jakob-R52 kernel: [    0.275784] Scanning for low memory corruption every 60 seconds
Oct 29 19:18:36 jakob-R52 kernel: [    0.276142] audit: initializing netlink socket (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.276164] type=2000 audit(1288379901.272:1): initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.304867] Trying to unpack rootfs image as initramfs...
Oct 29 19:18:36 jakob-R52 kernel: [    0.340635] highmem bounce pool size: 64 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.340649] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.344544] VFS: Disk quotas dquot_6.5.2
Oct 29 19:18:36 jakob-R52 kernel: [    0.344690] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.352090] fuse init (API version 7.14)
Oct 29 19:18:36 jakob-R52 kernel: [    0.352324] msgmni has been set to 1709
Oct 29 19:18:36 jakob-R52 kernel: [    0.356140] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 29 19:18:36 jakob-R52 kernel: [    0.356148] io scheduler noop registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.356153] io scheduler deadline registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.356188] io scheduler cfq registered (default)
Oct 29 19:18:36 jakob-R52 kernel: [    0.356439] pcieport 0000:00:01.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356480]   alloc irq_desc for 40 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356486]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356502] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.356622] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356677]   alloc irq_desc for 41 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356683]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356697] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.356873] pcieport 0000:00:1c.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356929]   alloc irq_desc for 42 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356934]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356947] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.357170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 19:18:36 jakob-R52 kernel: [    0.357358] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 29 19:18:36 jakob-R52 kernel: [    0.357963] ACPI: AC Adapter [AC] (on-line)
Oct 29 19:18:36 jakob-R52 kernel: [    0.358157] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Oct 29 19:18:36 jakob-R52 kernel: [    0.359409] ACPI: Lid Switch [LID]
Oct 29 19:18:36 jakob-R52 kernel: [    0.359548] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Oct 29 19:18:36 jakob-R52 kernel: [    0.359561] ACPI: Sleep Button [SLPB]
Oct 29 19:18:36 jakob-R52 kernel: [    0.359697] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 29 19:18:36 jakob-R52 kernel: [    0.359706] ACPI: Power Button [PWRF]
Oct 29 19:18:36 jakob-R52 kernel: [    0.360273] ACPI: acpi_idle registered with cpuidle
Oct 29 19:18:36 jakob-R52 kernel: [    0.361061] Marking TSC unstable due to TSC halts in idle
Oct 29 19:18:36 jakob-R52 kernel: [    0.369919] Switching to clocksource hpet
Oct 29 19:18:36 jakob-R52 kernel: [    0.385108] thermal LNXTHERM:01: registered as thermal_zone0
Oct 29 19:18:36 jakob-R52 kernel: [    0.385130] ACPI: Thermal Zone [THM0] (93 C)
Oct 29 19:18:36 jakob-R52 kernel: [    0.385280] ERST: Table is not found!
Oct 29 19:18:36 jakob-R52 kernel: [    0.385552] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.388104] serial 00:0a: activated
Oct 29 19:18:36 jakob-R52 kernel: [    0.388469] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Oct 29 19:18:36 jakob-R52 kernel: [    0.389397]   alloc irq_desc for 23 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.389404]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.389439] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Oct 29 19:18:36 jakob-R52 kernel: [    0.389451] serial 0000:00:1e.3: PCI INT B disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.399251] brd: module loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.400049] isapnp: Scanning for PnP cards...
Oct 29 19:18:36 jakob-R52 kernel: [    0.410170] loop: module loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.411236] ata_piix 0000:00:1f.2: version 2.13
Oct 29 19:18:36 jakob-R52 kernel: [    0.411282] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Oct 29 19:18:36 jakob-R52 kernel: [    0.411427] ata_piix 0000:00:1f.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.458904] scsi0 : ata_piix
Oct 29 19:18:36 jakob-R52 kernel: [    0.461432] scsi1 : ata_piix
Oct 29 19:18:36 jakob-R52 kernel: [    0.463686] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
Oct 29 19:18:36 jakob-R52 kernel: [    0.463695] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
Oct 29 19:18:36 jakob-R52 kernel: [    0.465694] Fixed MDIO Bus: probed
Oct 29 19:18:36 jakob-R52 kernel: [    0.465894] PPP generic driver version 2.4.2
Oct 29 19:18:36 jakob-R52 kernel: [    0.466334] tun: Universal TUN/TAP device driver, 1.6
Oct 29 19:18:36 jakob-R52 kernel: [    0.466340] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 29 19:18:36 jakob-R52 kernel: [    0.466739] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.473228] ACPI: Battery Slot [BAT0] (battery present)
Oct 29 19:18:36 jakob-R52 kernel: [    0.473472] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.474807] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.474824]   alloc irq_desc for 19 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.474830]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.474843] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 29 19:18:36 jakob-R52 kernel: [    0.474869] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.474877] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.474967] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.475018] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.478915] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Oct 29 19:18:36 jakob-R52 kernel: [    0.478952] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xa8000000
Oct 29 19:18:36 jakob-R52 kernel: [    0.500035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 29 19:18:36 jakob-R52 kernel: [    0.500336] hub 1-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.500349] hub 1-0:1.0: 8 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.500518] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.500553] uhci_hcd: USB Universal Host Controller Interface driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.500897] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.501158] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.501174] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.501189] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.501197] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.501299] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.501360] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Oct 29 19:18:36 jakob-R52 kernel: [    0.501638] hub 2-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.501649] hub 2-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.502046] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.502294] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.502310]   alloc irq_desc for 17 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502316]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502327] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 29 19:18:36 jakob-R52 kernel: [    0.502340] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.502347] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.502442] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Oct 29 19:18:36 jakob-R52 kernel: [    0.502495] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Oct 29 19:18:36 jakob-R52 kernel: [    0.502769] hub 3-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.502779] hub 3-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.502896]   alloc irq_desc for 18 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502901]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502912] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 29 19:18:36 jakob-R52 kernel: [    0.502924] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.502931] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.503010] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Oct 29 19:18:36 jakob-R52 kernel: [    0.503066] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Oct 29 19:18:36 jakob-R52 kernel: [    0.503348] hub 4-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.503358] hub 4-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.503475] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 29 19:18:36 jakob-R52 kernel: [    0.503488] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.503495] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.503577] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Oct 29 19:18:36 jakob-R52 kernel: [    0.503612] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
Oct 29 19:18:36 jakob-R52 kernel: [    0.503880] hub 5-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.503891] hub 5-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.504217] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Oct 29 19:18:36 jakob-R52 kernel: [    0.516905] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.516920] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 19:18:36 jakob-R52 kernel: [    0.517187] mice: PS/2 mouse device common for all mice
Oct 29 19:18:36 jakob-R52 kernel: [    0.517527] rtc_cmos 00:06: RTC can wake from S4
Oct 29 19:18:36 jakob-R52 kernel: [    0.517619] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Oct 29 19:18:36 jakob-R52 kernel: [    0.517662] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 29 19:18:36 jakob-R52 kernel: [    0.517927] device-mapper: uevent: version 1.0.3
Oct 29 19:18:36 jakob-R52 kernel: [    0.521803] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Oct 29 19:18:36 jakob-R52 kernel: [    0.524282] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Oct 29 19:18:36 jakob-R52 kernel: [    0.528391] device-mapper: multipath: version 1.1.1 loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.528398] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.528682] EISA: Probing bus 0 at eisa.0
Oct 29 19:18:36 jakob-R52 kernel: [    0.528694] Cannot allocate resource for EISA slot 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.528701] Cannot allocate resource for EISA slot 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.528707] Cannot allocate resource for EISA slot 3
Oct 29 19:18:36 jakob-R52 kernel: [    0.528713] Cannot allocate resource for EISA slot 4
Oct 29 19:18:36 jakob-R52 kernel: [    0.528719] Cannot allocate resource for EISA slot 5
Oct 29 19:18:36 jakob-R52 kernel: [    0.528724] Cannot allocate resource for EISA slot 6
Oct 29 19:18:36 jakob-R52 kernel: [    0.528730] Cannot allocate resource for EISA slot 7
Oct 29 19:18:36 jakob-R52 kernel: [    0.528736] Cannot allocate resource for EISA slot 8
Oct 29 19:18:36 jakob-R52 kernel: [    0.528741] EISA: Detected 0 cards.
Oct 29 19:18:36 jakob-R52 kernel: [    0.580727] cpuidle: using governor ladder
Oct 29 19:18:36 jakob-R52 kernel: [    0.580868] cpuidle: using governor menu
Oct 29 19:18:36 jakob-R52 kernel: [    0.581544] TCP cubic registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.581884] NET: Registered protocol family 10
Oct 29 19:18:36 jakob-R52 kernel: [    0.582696] lo: Disabled Privacy Extensions
Oct 29 19:18:36 jakob-R52 kernel: [    0.583214] NET: Registered protocol family 17
Oct 29 19:18:36 jakob-R52 kernel: [    0.585062] P-state transition latency capped at 20 uS
Oct 29 19:18:36 jakob-R52 kernel: [    0.585473] Using IPI No-Shortcut mode
Oct 29 19:18:36 jakob-R52 kernel: [    0.585677] PM: Resume from disk failed.
Oct 29 19:18:36 jakob-R52 kernel: [    0.585700] registered taskstats version 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.586122]   Magic number: 14:491:345
Oct 29 19:18:36 jakob-R52 kernel: [    0.586166] tty tty62: hash matches
Oct 29 19:18:36 jakob-R52 kernel: [    0.586265] rtc_cmos 00:06: setting system clock to 2010-10-29 19:18:22 UTC (1288379902)
Oct 29 19:18:36 jakob-R52 kernel: [    0.586273] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 29 19:18:36 jakob-R52 kernel: [    0.586278] EDD information not available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.668587] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 1.04, max UDMA/33
Oct 29 19:18:36 jakob-R52 kernel: [    0.668761] ata1.00: ATA-6: FUJITSU MHT2080AT, 8431, max UDMA/100
Oct 29 19:18:36 jakob-R52 kernel: [    0.668769] ata1.00: 156301488 sectors, multi 16: LBA 
Oct 29 19:18:36 jakob-R52 kernel: [    0.668803] ata1.00: applying bridge limits
Oct 29 19:18:36 jakob-R52 kernel: [    0.685087] ata2.00: configured for UDMA/33
Oct 29 19:18:36 jakob-R52 kernel: [    0.694105] ata1.00: configured for UDMA/100
Oct 29 19:18:36 jakob-R52 kernel: [    0.843925] usb 1-3: new high speed USB device using ehci_hcd and address 2
Oct 29 19:18:36 jakob-R52 kernel: [    1.043232] hub 1-3:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    1.044026] hub 1-3:1.0: 4 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    1.108427] isapnp: No Plug & Play device found
Oct 29 19:18:36 jakob-R52 kernel: [    1.108897] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 8431 PQ: 0 ANSI: 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.109250] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 19:18:36 jakob-R52 kernel: [    1.109563] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Oct 29 19:18:36 jakob-R52 kernel: [    1.109693] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:18:36 jakob-R52 kernel: [    1.109701] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 29 19:18:36 jakob-R52 kernel: [    1.109759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:18:36 jakob-R52 kernel: [    1.110097]  sda:
Oct 29 19:18:36 jakob-R52 kernel: [    1.114641] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 1.04 PQ: 0 ANSI: 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.127662] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 19:18:36 jakob-R52 kernel: [    1.127671] Uniform CD-ROM driver Revision: 3.20
Oct 29 19:18:36 jakob-R52 kernel: [    1.127912] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 29 19:18:36 jakob-R52 kernel: [    1.128070] sr 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.144359]  sda1 sda2 < sda5 >
Oct 29 19:18:36 jakob-R52 kernel: [    1.173620] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 29 19:18:36 jakob-R52 kernel: [    1.404983] usb 3-2: new full speed USB device using uhci_hcd and address 2
Oct 29 19:18:36 jakob-R52 kernel: [    1.514282] Freeing initrd memory: 10516k freed
Oct 29 19:18:36 jakob-R52 kernel: [    1.524439] Freeing unused kernel memory: 684k freed
Oct 29 19:18:36 jakob-R52 kernel: [    1.525374] Write protecting the kernel text: 4932k
Oct 29 19:18:36 jakob-R52 kernel: [    1.525467] Write protecting the kernel read-only data: 1976k
Oct 29 19:18:36 jakob-R52 kernel: [    1.572186] udev[69]: starting version 163
Oct 29 19:18:36 jakob-R52 kernel: [    1.704204] usb 1-3.1: new low speed USB device using ehci_hcd and address 4
Oct 29 19:18:36 jakob-R52 kernel: [    1.908248] usb 1-3.3: new low speed USB device using ehci_hcd and address 5
Oct 29 19:18:36 jakob-R52 kernel: [    2.092979] Floppy drive(s): fd0 is 1.44M
Oct 29 19:18:36 jakob-R52 kernel: [    2.108215] usb 1-3.4: new high speed USB device using ehci_hcd and address 6
Oct 29 19:18:36 jakob-R52 kernel: [    2.112613] FDC 0 is a National Semiconductor PC87306
Oct 29 19:18:36 jakob-R52 kernel: [    2.123706] tg3.c:v3.110 (April 9, 2010)
Oct 29 19:18:36 jakob-R52 kernel: [    2.123736] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    2.123753] tg3 0000:02:00.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    2.254227] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:0a:e4:c0:bd:cd
Oct 29 19:18:36 jakob-R52 kernel: [    2.254239] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Oct 29 19:18:36 jakob-R52 kernel: [    2.254248] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 29 19:18:36 jakob-R52 kernel: [    2.254256] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Oct 29 19:18:36 jakob-R52 kernel: [    2.256928] usbcore: registered new interface driver hiddev
Oct 29 19:18:36 jakob-R52 kernel: [    2.261984] input: Kensington Kensington USB Wheel Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input4
Oct 29 19:18:36 jakob-R52 kernel: [    2.262434] generic-usb 0003:047D:1012.0001: input,hidraw0: USB HID v1.00 Mouse [Kensington Kensington USB Wheel Mouse] on usb-0000:00:1d.7-3.1/input0
Oct 29 19:18:36 jakob-R52 kernel: [    2.269490] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
Oct 29 19:18:36 jakob-R52 kernel: [    2.270345] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.7-3.3/input0
Oct 29 19:18:36 jakob-R52 kernel: [    2.270663] usbcore: registered new interface driver usbhid
Oct 29 19:18:36 jakob-R52 kernel: [    2.270670] usbhid: USB HID core driver
Oct 29 19:18:36 jakob-R52 kernel: [    2.314913] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Oct 29 19:18:36 jakob-R52 kernel: [    5.236093] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
Oct 29 19:18:36 jakob-R52 kernel: [    6.663895] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Oct 29 19:18:36 jakob-R52 kernel: [    7.100200] udev[351]: starting version 163
Oct 29 19:18:36 jakob-R52 kernel: [    9.719426] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
Oct 29 19:18:36 jakob-R52 kernel: [    9.719432] serio: Synaptics pass-through port at isa0060/serio1/input0
Oct 29 19:18:36 jakob-R52 kernel: [    9.761710] parport_pc 00:0b: reported by Plug and Play ACPI
Oct 29 19:18:36 jakob-R52 kernel: [    9.761766] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Oct 29 19:18:36 jakob-R52 kernel: [    9.766249] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Oct 29 19:18:36 jakob-R52 kernel: [    9.840502] Linux agpgart interface v0.103
Oct 29 19:18:36 jakob-R52 kernel: [    9.927912] Non-volatile memory driver v1.3
Oct 29 19:18:36 jakob-R52 kernel: [    9.937490] ppdev: user-space parallel port driver
Oct 29 19:18:36 jakob-R52 kernel: [   10.055228] Linux video capture interface: v2.00
Oct 29 19:18:36 jakob-R52 kernel: [   10.485086] lib80211: common routines for IEEE802.11 drivers
Oct 29 19:18:36 jakob-R52 kernel: [   10.485090] lib80211_crypt: registered algorithm 'NULL'
Oct 29 19:18:36 jakob-R52 kernel: [   10.494278] intel_rng: FWH not detected
Oct 29 19:18:36 jakob-R52 kernel: [   10.527768] lp0: using parport0 (interrupt-driven).
Oct 29 19:18:36 jakob-R52 kernel: [   10.540301] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
Oct 29 19:18:36 jakob-R52 kernel: [   10.540433] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Oct 29 19:18:36 jakob-R52 kernel: [   10.877794] irda_init()
Oct 29 19:18:36 jakob-R52 kernel: [   10.877809] NET: Registered protocol family 23
Oct 29 19:18:36 jakob-R52 kernel: [   10.927793] [drm] Initialized drm 1.1.0 20060810
Oct 29 19:18:36 jakob-R52 kernel: [   10.966825] yenta_cardbus 0000:04:00.0: CardBus bridge found [1014:0532]
Oct 29 19:18:36 jakob-R52 kernel: [   11.047050] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
Oct 29 19:18:36 jakob-R52 kernel: [   11.047081] usb 3-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
Oct 29 19:18:36 jakob-R52 kernel: [   11.090852] usb 3-2: PAS202BCB image sensor detected
Oct 29 19:18:36 jakob-R52 kernel: [   11.092659] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c38, PCI irq 16
Oct 29 19:18:36 jakob-R52 kernel: [   11.092663] yenta_cardbus 0000:04:00.0: Socket status: 30000006
Oct 29 19:18:36 jakob-R52 kernel: [   11.092672] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [   11.092676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x8fff: excluding 0x5000-0x50ff 0x5400-0x54ff
Oct 29 19:18:36 jakob-R52 kernel: [   11.114848] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [   11.114852] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa8400000-0xb7ffffff: excluding 0xa8400000-0xa8bfffff 0xabc00000-0xb03fffff
Oct 29 19:18:36 jakob-R52 kernel: [   11.114876] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [   11.114879] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0000000-0xd7ffffff: excluding 0xd0000000-0xd7ffffff
Oct 29 19:18:36 jakob-R52 kernel: [   11.454864] usb 3-2: Initialization succeeded
Oct 29 19:18:36 jakob-R52 kernel: [   11.454961] usb 3-2: V4L2 device registered as video0
Oct 29 19:18:36 jakob-R52 kernel: [   11.454989] usbcore: registered new interface driver zc0301
Oct 29 19:18:36 jakob-R52 kernel: [   11.472708] cfg80211: Calling CRDA to update world regulatory domain
Oct 29 19:18:36 jakob-R52 kernel: [   11.547354] type=1400 audit(1288379913.456:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.547996] type=1400 audit(1288379913.456:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.548367] type=1400 audit(1288379913.460:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.551399] nsc-ircc 00:0c: activated
Oct 29 19:18:36 jakob-R52 kernel: [   11.551403] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Oct 29 19:18:36 jakob-R52 kernel: [   11.551485] nsc-ircc, chip->init
Oct 29 19:18:36 jakob-R52 kernel: [   11.551498] nsc-ircc, Found chip at base=0x02e
Oct 29 19:18:36 jakob-R52 kernel: [   11.551535] nsc-ircc, driver loaded (Dag Brattli)
Oct 29 19:18:36 jakob-R52 kernel: [   11.553141] IrDA: Registered device irda0
Oct 29 19:18:36 jakob-R52 kernel: [   11.553144] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Oct 29 19:18:36 jakob-R52 kernel: [   12.234492] libipw: 802.11 data/management/control stack, git-1.1.13
Oct 29 19:18:36 jakob-R52 kernel: [   12.234496] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct 29 19:18:36 jakob-R52 kernel: [   12.386405] psmouse serio2: ID: 10 00 64
Oct 29 19:18:36 jakob-R52 kernel: [   12.534845] [drm] radeon defaulting to kernel modesetting.
Oct 29 19:18:36 jakob-R52 kernel: [   12.534849] [drm] radeon kernel modesetting enabled.
Oct 29 19:18:36 jakob-R52 kernel: [   12.534974] radeon 0000:01:00.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [   12.535012] radeon 0000:01:00.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [   12.535022] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [   12.535029] radeon 0000:01:00.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [   12.537873] [drm] initializing kernel modesetting (RV380 0x1002:0x5460).
Oct 29 19:18:36 jakob-R52 kernel: [   12.537990] [drm] register mmio base: 0xA8100000
Oct 29 19:18:36 jakob-R52 kernel: [   12.537993] [drm] register mmio size: 65536
Oct 29 19:18:36 jakob-R52 kernel: [   12.538188] [drm] Generation 2 PCI interface, using max accessible memory
Oct 29 19:18:36 jakob-R52 kernel: [   12.538194] radeon 0000:01:00.0: VRAM: 64M 0xC0000000 - 0xC3FFFFFF (64M used)
Oct 29 19:18:36 jakob-R52 kernel: [   12.538198] radeon 0000:01:00.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
Oct 29 19:18:36 jakob-R52 kernel: [   12.538243]   alloc irq_desc for 43 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.538245]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.538258] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [   12.538264] radeon 0000:01:00.0: radeon: using MSI.
Oct 29 19:18:36 jakob-R52 kernel: [   12.538296] [drm] radeon: irq initialized.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539271] [drm] Detected VRAM RAM=64M, BAR=128M
Oct 29 19:18:36 jakob-R52 kernel: [   12.539276] [drm] RAM width 64bits DDR
Oct 29 19:18:36 jakob-R52 kernel: [   12.539381] [TTM] Zone  kernel: Available graphics memory: 443254 kiB.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539384] [TTM] Zone highmem: Available graphics memory: 512314 kiB.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539386] [TTM] Initializing pool allocator.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539409] [drm] radeon: 64M of VRAM memory ready
Oct 29 19:18:36 jakob-R52 kernel: [   12.539412] [drm] radeon: 512M of GTT memory ready.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539437] [drm] GART: num cpu pages 131072, num gpu pages 131072
Oct 29 19:18:36 jakob-R52 kernel: [   12.540184] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Oct 29 19:18:36 jakob-R52 kernel: [   12.541546] [drm] PCIE GART of 512M enabled (table at 0xC0040000).
Oct 29 19:18:36 jakob-R52 kernel: [   12.542260] [drm] Loading R300 Microcode
Oct 29 19:18:36 jakob-R52 kernel: [   12.588841] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Oct 29 19:18:36 jakob-R52 kernel: [   12.588845] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Oct 29 19:18:36 jakob-R52 kernel: [   12.588955]   alloc irq_desc for 21 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.588957]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.588966] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 29 19:18:36 jakob-R52 kernel: [   12.589051] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Oct 29 19:18:36 jakob-R52 kernel: [   12.666784] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Oct 29 19:18:36 jakob-R52 kernel: [   12.666788] thinkpad_acpi: http://ibm-acpi.sf.net/
Oct 29 19:18:36 jakob-R52 kernel: [   12.666790] thinkpad_acpi: ThinkPad BIOS 76ET28WW (1.08 ), EC 76HT11WW-1.01
Oct 29 19:18:36 jakob-R52 kernel: [   12.666793] thinkpad_acpi: IBM ThinkPad R52, model 18494PU
Oct 29 19:18:36 jakob-R52 kernel: [   12.666795] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Oct 29 19:18:36 jakob-R52 kernel: [   12.666797] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Oct 29 19:18:36 jakob-R52 kernel: [   12.668613] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Oct 29 19:18:36 jakob-R52 kernel: [   12.675371] Registered led device: tpacpi::thinklight
Oct 29 19:18:36 jakob-R52 kernel: [   12.675929] Registered led device: tpacpi::power
Oct 29 19:18:36 jakob-R52 kernel: [   12.676497] Registered led device: tpacpi::standby
Oct 29 19:18:36 jakob-R52 kernel: [   12.682974] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Oct 29 19:18:36 jakob-R52 kernel: [   12.687060] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
Oct 29 19:18:36 jakob-R52 kernel: [   12.687587] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input8
Oct 29 19:18:36 jakob-R52 kernel: [   13.181930] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 29 19:18:36 jakob-R52 kernel: [   13.201773] usbcore: registered new interface driver snd-usb-audio
Oct 29 19:18:36 jakob-R52 kernel: [   13.261183] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Oct 29 19:18:36 jakob-R52 kernel: [   13.262904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Oct 29 19:18:36 jakob-R52 kernel: [   13.263628] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Oct 29 19:18:36 jakob-R52 kernel: [   13.264371] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Oct 29 19:18:36 jakob-R52 kernel: [   13.265046] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
```

---

### Post by olafurg on 2010-11-01
Anyone? Any details missing perhaps? Please ...

---

### Post by coffee412 on 2010-11-01
> **olafurg said:**
> Having some trouble with a friend's computer. Just replaced Windows Vista with Ubuntu 10.10 and it's giving us some trouble. It keeps randomly shutting down, definitely connected to some heat issues. No problem whatsoever before, running Vista.

So here's the situation.
[LIST=1]
[*]Turn on the computer.
[*]Do stuff, install programs etc.
[*]Heat gets up to 80-90°C as we've noticed, more heat depending on the hard work given to it.
[*]Eventually a hard shutdown and the computer feels really hot.
[/LIST]

The fan seems to be working, gets on and everything. 

Please help with this as it's my friend's first experience with Ubuntu and I'd rather not fail this experiment with some strange problem like this. This should be basic stuff.

If more info needed, please let me know.

Thanks a lot.

Here's a part of the syslog file:

```
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Quiting due to inactivity
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Shutdown was requested
Oct 29 19:00:11 jakob-R52 AptDaemon: INFO: Initializing daemon
Oct 29 19:03:29 jakob-R52 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'wine1.2')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Oct 29 19:03:33 jakob-R52 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:33 jakob-R52 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:35 jakob-R52 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:03:36 jakob-R52 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'wine1.2')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Oct 29 19:07:42 jakob-R52 pulseaudio[1439]: ratelimit.c: 1 events suppressed
Oct 29 19:13:30 jakob-R52 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/c46d5c13c75a456eabe370c4a08400de
Oct 29 19:15:54 jakob-R52 AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'skysentials')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Oct 29 19:16:00 jakob-R52 AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:00 jakob-R52 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:02 jakob-R52 AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/d9719d5febd74929896ded99dc73f089
Oct 29 19:16:03 jakob-R52 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'skysentials')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.587748] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.587752] Disabling lock debugging due to kernel taint
Oct 29 19:16:03 jakob-R52 kernel: [ 6180.588312] CPU0: Core temperature/speed normal
Oct 29 19:16:07 jakob-R52 kernel: [ 6184.435746] Critical temperature reached (100 C), shutting down.
Oct 29 19:16:07 jakob-R52 kernel: Kernel logging (proc) stopped.
Oct 29 19:16:08 jakob-R52 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="714" x-info="http://www.rsyslog.com"] exiting on signal 15.
Oct 29 19:18:36 jakob-R52 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 29 19:18:36 jakob-R52 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="661" x-info="http://www.rsyslog.com"] (re)start
Oct 29 19:18:36 jakob-R52 rsyslogd: rsyslogd's groupid changed to 103
Oct 29 19:18:36 jakob-R52 rsyslogd: rsyslogd's userid changed to 101
Oct 29 19:18:35 jakob-R52 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fef5000 (ACPI data)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003fef5000 - 000000003ff00000 (ACPI NVS)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] DMI present.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x100000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR default type: uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   00000-9FFFF write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   D0000-DBFFF uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DC000-DFFFF write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   E0000-FFFFF write-protect
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] MTRR variable ranges enabled:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   1 base 03FF00000 mask FFFF00000 uncachable
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   2 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   3 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   4 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   5 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   6 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   7 disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PAT not supported by CPU.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] modified physical RAM map:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 0000000000100000 - 000000003fee0000 (usable)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003fee0000 - 000000003fef5000 (ACPI data)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003fef5000 - 000000003ff00000 (ACPI NVS)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 000000003ff00000 - 0000000040000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] RAMDISK: 2f523000 - 2ff68000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: RSDP 000f6bf0 00024 (v02 IBM   )
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: XSDT 3fee701e 0005C (v01 IBM    TP-76    00001080  LTP 00000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: FACP 3fee7100 000F4 (v03 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20100428/tbfadt-526)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20100428/tbfadt-557)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: DSDT 3fee72e7 0DADC (v01 IBM    TP-76    00001080 MSFT 0100000E)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: FACS 3fef6000 00040
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: SSDT 3fee72b4 00033 (v01 IBM    TP-76    00001080 MSFT 0100000E)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: ECDT 3fef4dc3 00052 (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: TCPA 3fef4e15 00032 (v01 IBM    TP-76    00001080 PTL  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: APIC 3fef4e47 0005A (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: MCFG 3fef4ea1 0003E (v01 IBM    TP-76    00001080 IBM  00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: BOOT 3fef4fd8 00028 (v01 IBM    TP-76    00001080  LTP 00000001)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 134MB HIGHMEM available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] 887MB LOWMEM available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   low ram: 0 - 377fe000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Zone PFN ranges:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003fee0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Movable zone start PFN for each node
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     0: 0x00000100 -> 0x0003fee0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] On node 0 totalpages: 261744
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001020
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   DMA zone: 3952 pages, LIFO batch:0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem zone: 270 pages used for memmap
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   HighMem zone: 34260 pages, LIFO batch:7
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Using APIC driver default
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] nr_irqs_gsi: 40
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36416 r0 d20928 u4194304
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] pcpu-alloc: [0] 0 
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259698
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e83319a1-12bf-4690-8876-33491fab41f4 ro quiet splash
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing CPU#0
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] allocated 5237100 bytes of page_cgroup
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Subtract (49 early reservations)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #3 [002f523000 - 002ff68000]         RAMDISK
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #4 [000009f000 - 0000100000]   BIOS reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #5 [00009a1000 - 00009a4128]             BRK
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #10 [0001001000 - 0001801000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #11 [0001801000 - 0001801004]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #12 [0001801040 - 0001801100]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #13 [0001801100 - 0001801154]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #14 [0001801180 - 0001804180]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #15 [0001804180 - 0001804190]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #16 [00018041c0 - 0001804dc0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #17 [0001804dc0 - 0001804de7]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #18 [0001804e00 - 0001804ff8]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #19 [0001805000 - 0001805040]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #20 [0001805040 - 0001805080]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #21 [0001805080 - 00018050c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #22 [00018050c0 - 0001805100]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #23 [0001805100 - 0001805140]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #24 [0001805140 - 0001805180]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #25 [0001805180 - 00018051c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #26 [00018051c0 - 0001805200]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #27 [0001805200 - 0001805240]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #28 [0001805240 - 0001805280]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #29 [0001805280 - 00018052c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #30 [00018052c0 - 0001805300]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #31 [0001805300 - 0001805340]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #32 [0001805340 - 0001805380]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #33 [0001805380 - 00018053c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #34 [00018053c0 - 00018053d0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #35 [0001805400 - 0001805410]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #36 [0001805440 - 00018054aa]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #37 [00018054c0 - 000180552a]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #38 [0001c00000 - 0001c0e000]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #39 [0001807540 - 0001807544]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #40 [0001807580 - 0001807584]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #41 [00018075c0 - 00018075c4]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #42 [0001807600 - 0001807604]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #43 [0001807640 - 00018076f0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #44 [0001807700 - 00018077a8]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #45 [00018077c0 - 000180b7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #46 [000180b7c0 - 000188b7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #47 [000188b7c0 - 00018cb7c0]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]   #48 [0001c0e000 - 000210c96c]         BOOTMEM
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003fee0)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Memory: 1013404k/1047424k available (4928k kernel code, 33572k reserved, 2336k data, 684k init, 138120k highmem)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] virtual kernel memory layout:
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Hierarchical RCU implementation.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Extended CMOS year: 2000
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] console [tty0] enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Fast TSC calibration using PIT
Oct 29 19:18:36 jakob-R52 kernel: [    0.000000] Detected 798.153 MHz processor.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1596.30 BogoMIPS (lpj=3192612)
Oct 29 19:18:36 jakob-R52 kernel: [    0.008020] pid_max: default: 32768 minimum: 301
Oct 29 19:18:36 jakob-R52 kernel: [    0.008067] Security Framework initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.008106] AppArmor: AppArmor initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.008111] Yama: becoming mindful.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008239] Mount-cache hash table entries: 512
Oct 29 19:18:36 jakob-R52 kernel: [    0.008502] Initializing cgroup subsys ns
Oct 29 19:18:36 jakob-R52 kernel: [    0.008511] Initializing cgroup subsys cpuacct
Oct 29 19:18:36 jakob-R52 kernel: [    0.008522] Initializing cgroup subsys memory
Oct 29 19:18:36 jakob-R52 kernel: [    0.008545] Initializing cgroup subsys devices
Oct 29 19:18:36 jakob-R52 kernel: [    0.008551] Initializing cgroup subsys freezer
Oct 29 19:18:36 jakob-R52 kernel: [    0.008557] Initializing cgroup subsys net_cls
Oct 29 19:18:36 jakob-R52 kernel: [    0.008619] mce: CPU supports 5 MCE banks
Oct 29 19:18:36 jakob-R52 kernel: [    0.008637] CPU0: Thermal monitoring enabled (TM2)
Oct 29 19:18:36 jakob-R52 kernel: [    0.008652] Performance Events: p6 PMU driver.
Oct 29 19:18:36 jakob-R52 kernel: [    0.008670] ... version:                0
Oct 29 19:18:36 jakob-R52 kernel: [    0.008675] ... bit width:              32
Oct 29 19:18:36 jakob-R52 kernel: [    0.008680] ... generic registers:      2
Oct 29 19:18:36 jakob-R52 kernel: [    0.008685] ... value mask:             00000000ffffffff
Oct 29 19:18:36 jakob-R52 kernel: [    0.008691] ... max period:             000000007fffffff
Oct 29 19:18:36 jakob-R52 kernel: [    0.008697] ... fixed-purpose events:   0
Oct 29 19:18:36 jakob-R52 kernel: [    0.008702] ... event mask:             0000000000000003
Oct 29 19:18:36 jakob-R52 kernel: [    0.010558] SMP alternatives: switching to UP code
Oct 29 19:18:36 jakob-R52 kernel: [    0.027622] Freeing SMP alternatives: 24k freed
Oct 29 19:18:36 jakob-R52 kernel: [    0.027642] ACPI: Core revision 20100428
Oct 29 19:18:36 jakob-R52 kernel: [    0.056015] ftrace: converting mcount calls to 0f 1f 44 00 00
Oct 29 19:18:36 jakob-R52 kernel: [    0.056026] ftrace: allocating 21758 entries in 43 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.064096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 29 19:18:36 jakob-R52 kernel: [    0.064499] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 29 19:18:36 jakob-R52 kernel: [    0.105224] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Brought up 1 CPUs
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Total of 1 processors activated (1596.30 BogoMIPS).
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] devtmpfs: initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] regulator: core version 0.5
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] Time: 19:18:22  Date: 10/29/10
Oct 29 19:18:36 jakob-R52 kernel: [    0.108000] NET: Registered protocol family 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.108153] EISA bus registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.108170] ACPI: bus type pci registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.108318] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Oct 29 19:18:36 jakob-R52 kernel: [    0.108328] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Oct 29 19:18:36 jakob-R52 kernel: [    0.108333] PCI: Using MMCONFIG for extended config space
Oct 29 19:18:36 jakob-R52 kernel: [    0.108338] PCI: Using configuration type 1 for base access
Oct 29 19:18:36 jakob-R52 kernel: [    0.110720] bio: create slab <bio-0> at 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.115738] ACPI: EC: EC description table is found, configuring boot EC
Oct 29 19:18:36 jakob-R52 kernel: [    0.147920] ACPI: Interpreter enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.147928] ACPI: (supports S0 S3 S4 S5)
Oct 29 19:18:36 jakob-R52 kernel: [    0.147989] ACPI: Using IOAPIC for interrupt routing
Oct 29 19:18:36 jakob-R52 kernel: [    0.168423] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Oct 29 19:18:36 jakob-R52 kernel: [    0.168526] ACPI: Power Resource [PUBS] (on)
Oct 29 19:18:36 jakob-R52 kernel: [    0.173871] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Oct 29 19:18:36 jakob-R52 kernel: [    0.173882] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Oct 29 19:18:36 jakob-R52 kernel: [    0.173942] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Oct 29 19:18:36 jakob-R52 kernel: [    0.174082] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174090] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174098] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174106] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174114] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174123] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
Oct 29 19:18:36 jakob-R52 kernel: [    0.174248] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174256] pci 0000:00:01.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174411] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174420] pci 0000:00:1c.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174541] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.174550] pci 0000:00:1c.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.174632] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174714] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174792] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174870] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.174945] pci 0000:00:1d.7: reg 10: [mem 0xa8000000-0xa80003ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175020] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175030] pci 0000:00:1d.7: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175157] pci 0000:00:1e.2: reg 10: [io  0x1c00-0x1cff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175169] pci 0000:00:1e.2: reg 14: [io  0x1880-0x18bf]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175182] pci 0000:00:1e.2: reg 18: [mem 0xa8000800-0xa80009ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175196] pci 0000:00:1e.2: reg 1c: [mem 0xa8000400-0xa80004ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175245] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175253] pci 0000:00:1e.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175298] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175311] pci 0000:00:1e.3: reg 14: [io  0x2000-0x207f]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175372] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.175381] pci 0000:00:1e.3: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175492] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Oct 29 19:18:36 jakob-R52 kernel: [    0.175505] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
Oct 29 19:18:36 jakob-R52 kernel: [    0.175515] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
Oct 29 19:18:36 jakob-R52 kernel: [    0.175524] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
Oct 29 19:18:36 jakob-R52 kernel: [    0.175533] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef
Oct 29 19:18:36 jakob-R52 kernel: [    0.175584] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175597] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175609] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175621] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175634] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175678] pci 0000:00:1f.2: PME# supported from D3hot
Oct 29 19:18:36 jakob-R52 kernel: [    0.175687] pci 0000:00:1f.2: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.175760] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175869] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175880] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175891] pci 0000:01:00.0: reg 18: [mem 0xa8100000-0xa810ffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175915] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175943] pci 0000:01:00.0: supports D1 D2
Oct 29 19:18:36 jakob-R52 kernel: [    0.175960] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 29 19:18:36 jakob-R52 kernel: [    0.175977] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175985] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.175994] pci 0000:00:01.0:   bridge window [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176008] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176142] pci 0000:02:00.0: reg 10: [mem 0xa8200000-0xa820ffff 64bit]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176252] pci 0000:02:00.0: PME# supported from D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176262] pci 0000:02:00.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176290] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Oct 29 19:18:36 jakob-R52 kernel: [    0.176310] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176319] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176330] pci 0000:00:1c.0:   bridge window [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176343] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176419] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176429] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176438] pci 0000:00:1c.2:   bridge window [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176452] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176539] pci 0000:04:00.0: reg 10: [mem 0xa8400000-0xa8400fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176575] pci 0000:04:00.0: supports D1 D2
Oct 29 19:18:36 jakob-R52 kernel: [    0.176581] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176591] pci 0000:04:00.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176665] pci 0000:04:02.0: reg 10: [mem 0xa8401000-0xa8401fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176753] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
Oct 29 19:18:36 jakob-R52 kernel: [    0.176763] pci 0000:04:02.0: PME# disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.176841] pci 0000:00:1e.0: PCI bridge to [bus 04-07] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176851] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176861] pci 0000:00:1e.0:   bridge window [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176874] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.176882] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176889] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
Oct 29 19:18:36 jakob-R52 kernel: [    0.176983] pci_bus 0000:00: on NUMA node 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.176995] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177499] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.177892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Oct 29 19:18:36 jakob-R52 kernel: [    0.189797] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.190243] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.190684] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.191123] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.191562] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192020] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192462] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.192900] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Oct 29 19:18:36 jakob-R52 kernel: [    0.193063] HEST: Table is not found!
Oct 29 19:18:36 jakob-R52 kernel: [    0.193227] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Oct 29 19:18:36 jakob-R52 kernel: [    0.193236] vgaarb: loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.193619] SCSI subsystem initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.193709] libata version 3.00 loaded.
Oct 29 19:18:36 jakob-R52 kernel: [    0.193834] usbcore: registered new interface driver usbfs
Oct 29 19:18:36 jakob-R52 kernel: [    0.193865] usbcore: registered new interface driver hub
Oct 29 19:18:36 jakob-R52 kernel: [    0.193927] usbcore: registered new device driver usb
Oct 29 19:18:36 jakob-R52 kernel: [    0.194219] ACPI: WMI: Mapper loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.194223] PCI: Using ACPI for IRQ routing
Oct 29 19:18:36 jakob-R52 kernel: [    0.194230] PCI: pci_cache_line_size set to 64 bytes
Oct 29 19:18:36 jakob-R52 kernel: [    0.194355] Expanded resource reserved due to conflict with Adapter ROM
Oct 29 19:18:36 jakob-R52 kernel: [    0.194364] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194371] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194377] reserve RAM buffer: 000000003fee0000 - 000000003fffffff 
Oct 29 19:18:36 jakob-R52 kernel: [    0.194583] NetLabel: Initializing
Oct 29 19:18:36 jakob-R52 kernel: [    0.194588] NetLabel:  domain hash size = 128
Oct 29 19:18:36 jakob-R52 kernel: [    0.194592] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 29 19:18:36 jakob-R52 kernel: [    0.194621] NetLabel:  unlabeled traffic allowed by default
Oct 29 19:18:36 jakob-R52 kernel: [    0.194961] hpet clockevent registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.194970] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct 29 19:18:36 jakob-R52 kernel: [    0.194982] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 29 19:18:36 jakob-R52 kernel: [    0.194994] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Oct 29 19:18:36 jakob-R52 kernel: [    0.200039] Switching to clocksource tsc
Oct 29 19:18:36 jakob-R52 kernel: [    0.224792] AppArmor: AppArmor Filesystem Enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.224827] pnp: PnP ACPI init
Oct 29 19:18:36 jakob-R52 kernel: [    0.224865] ACPI: bus type pnp registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.232767] pnp: PnP ACPI: found 14 devices
Oct 29 19:18:36 jakob-R52 kernel: [    0.232774] ACPI: ACPI bus type pnp unregistered
Oct 29 19:18:36 jakob-R52 kernel: [    0.232782] PnPBIOS: Disabled by ACPI PNP
Oct 29 19:18:36 jakob-R52 kernel: [    0.232810] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232819] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232828] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232836] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232844] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232852] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232860] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232869] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232877] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232885] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232893] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232901] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232909] system 00:00: [mem 0x00100000-0x3fffffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232918] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232936] system 00:02: [io  0x1000-0x107f] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232944] system 00:02: [io  0x1180-0x11bf] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232951] system 00:02: [io  0x15e0-0x15ef] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232959] system 00:02: [io  0x1600-0x1641] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232967] system 00:02: [io  0x1644-0x167f] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232975] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232983] system 00:02: [mem 0xf0008000-0xf000bfff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.232991] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.233000] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.233008] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Oct 29 19:18:36 jakob-R52 kernel: [    0.271292] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271303] pci 0000:00:1c.0: BAR 13: assigned [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271313] pci 0000:01:00.0: BAR 6: assigned [mem 0xa8120000-0xa813ffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271321] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271328] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271337] pci 0000:00:01.0:   bridge window [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271346] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271356] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271364] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271376] pci 0000:00:1c.0:   bridge window [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271386] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271399] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271407] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271418] pci 0000:00:1c.2:   bridge window [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271428] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271444] pci 0000:04:00.0: BAR 15: assigned [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271452] pci 0000:04:00.0: BAR 16: assigned [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271459] pci 0000:04:00.0: BAR 13: assigned [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271466] pci 0000:04:00.0: BAR 14: assigned [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271473] pci 0000:04:00.0: CardBus bridge to [bus 05-06]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271479] pci 0000:04:00.0:   bridge window [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271490] pci 0000:04:00.0:   bridge window [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271501] pci 0000:04:00.0:   bridge window [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271512] pci 0000:04:00.0:   bridge window [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271522] pci 0000:00:1e.0: PCI bridge to [bus 04-07]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271530] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271541] pci 0000:00:1e.0:   bridge window [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271551] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271577]   alloc irq_desc for 16 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271582]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271595] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.271604] pci 0000:00:01.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271620]   alloc irq_desc for 20 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271625]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271635] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 29 19:18:36 jakob-R52 kernel: [    0.271644] pci 0000:00:1c.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271661]   alloc irq_desc for 22 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271666]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.271674] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Oct 29 19:18:36 jakob-R52 kernel: [    0.271683] pci 0000:00:1c.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271698] pci 0000:00:1e.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.271720] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.271732] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271739] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271746] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271753] pci_bus 0000:01: resource 1 [mem 0xa8100000-0xa81fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271760] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc7ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271767] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271774] pci_bus 0000:02: resource 1 [mem 0xa8200000-0xa82fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271781] pci_bus 0000:02: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271788] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271795] pci_bus 0000:03: resource 1 [mem 0xa8300000-0xa83fffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271802] pci_bus 0000:03: resource 2 [mem 0xc8000000-0xc80fffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271809] pci_bus 0000:04: resource 0 [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271816] pci_bus 0000:04: resource 1 [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271823] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271830] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271837] pci_bus 0000:04: resource 5 [mem 0x00000000-0xffffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271844] pci_bus 0000:05: resource 0 [io  0x5000-0x50ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271850] pci_bus 0000:05: resource 1 [io  0x5400-0x54ff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271857] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xd3ffffff pref]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271864] pci_bus 0000:05: resource 3 [mem 0xac000000-0xafffffff]
Oct 29 19:18:36 jakob-R52 kernel: [    0.271952] NET: Registered protocol family 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.272099] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.272644] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274157] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274922] TCP: Hash tables configured (established 131072 bind 65536)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274928] TCP reno registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.274936] UDP hash table entries: 512 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.274962] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.275148] NET: Registered protocol family 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.275341] pci 0000:01:00.0: Boot video device
Oct 29 19:18:36 jakob-R52 kernel: [    0.275366] PCI: CLS 32 bytes, default 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.275506] Simple Boot Flag at 0x35 set to 0x1
Oct 29 19:18:36 jakob-R52 kernel: [    0.275711] cpufreq-nforce2: No nForce2 chipset.
Oct 29 19:18:36 jakob-R52 kernel: [    0.275784] Scanning for low memory corruption every 60 seconds
Oct 29 19:18:36 jakob-R52 kernel: [    0.276142] audit: initializing netlink socket (disabled)
Oct 29 19:18:36 jakob-R52 kernel: [    0.276164] type=2000 audit(1288379901.272:1): initialized
Oct 29 19:18:36 jakob-R52 kernel: [    0.304867] Trying to unpack rootfs image as initramfs...
Oct 29 19:18:36 jakob-R52 kernel: [    0.340635] highmem bounce pool size: 64 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.340649] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Oct 29 19:18:36 jakob-R52 kernel: [    0.344544] VFS: Disk quotas dquot_6.5.2
Oct 29 19:18:36 jakob-R52 kernel: [    0.344690] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 29 19:18:36 jakob-R52 kernel: [    0.352090] fuse init (API version 7.14)
Oct 29 19:18:36 jakob-R52 kernel: [    0.352324] msgmni has been set to 1709
Oct 29 19:18:36 jakob-R52 kernel: [    0.356140] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 29 19:18:36 jakob-R52 kernel: [    0.356148] io scheduler noop registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.356153] io scheduler deadline registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.356188] io scheduler cfq registered (default)
Oct 29 19:18:36 jakob-R52 kernel: [    0.356439] pcieport 0000:00:01.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356480]   alloc irq_desc for 40 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356486]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356502] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.356622] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356677]   alloc irq_desc for 41 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356683]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356697] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.356873] pcieport 0000:00:1c.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.356929]   alloc irq_desc for 42 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356934]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.356947] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [    0.357170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 29 19:18:36 jakob-R52 kernel: [    0.357358] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 29 19:18:36 jakob-R52 kernel: [    0.357963] ACPI: AC Adapter [AC] (on-line)
Oct 29 19:18:36 jakob-R52 kernel: [    0.358157] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Oct 29 19:18:36 jakob-R52 kernel: [    0.359409] ACPI: Lid Switch [LID]
Oct 29 19:18:36 jakob-R52 kernel: [    0.359548] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Oct 29 19:18:36 jakob-R52 kernel: [    0.359561] ACPI: Sleep Button [SLPB]
Oct 29 19:18:36 jakob-R52 kernel: [    0.359697] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Oct 29 19:18:36 jakob-R52 kernel: [    0.359706] ACPI: Power Button [PWRF]
Oct 29 19:18:36 jakob-R52 kernel: [    0.360273] ACPI: acpi_idle registered with cpuidle
Oct 29 19:18:36 jakob-R52 kernel: [    0.361061] Marking TSC unstable due to TSC halts in idle
Oct 29 19:18:36 jakob-R52 kernel: [    0.369919] Switching to clocksource hpet
Oct 29 19:18:36 jakob-R52 kernel: [    0.385108] thermal LNXTHERM:01: registered as thermal_zone0
Oct 29 19:18:36 jakob-R52 kernel: [    0.385130] ACPI: Thermal Zone [THM0] (93 C)
Oct 29 19:18:36 jakob-R52 kernel: [    0.385280] ERST: Table is not found!
Oct 29 19:18:36 jakob-R52 kernel: [    0.385552] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.388104] serial 00:0a: activated
Oct 29 19:18:36 jakob-R52 kernel: [    0.388469] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Oct 29 19:18:36 jakob-R52 kernel: [    0.389397]   alloc irq_desc for 23 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.389404]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.389439] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Oct 29 19:18:36 jakob-R52 kernel: [    0.389451] serial 0000:00:1e.3: PCI INT B disabled
Oct 29 19:18:36 jakob-R52 kernel: [    0.399251] brd: module loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.400049] isapnp: Scanning for PnP cards...
Oct 29 19:18:36 jakob-R52 kernel: [    0.410170] loop: module loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.411236] ata_piix 0000:00:1f.2: version 2.13
Oct 29 19:18:36 jakob-R52 kernel: [    0.411282] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Oct 29 19:18:36 jakob-R52 kernel: [    0.411427] ata_piix 0000:00:1f.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.458904] scsi0 : ata_piix
Oct 29 19:18:36 jakob-R52 kernel: [    0.461432] scsi1 : ata_piix
Oct 29 19:18:36 jakob-R52 kernel: [    0.463686] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
Oct 29 19:18:36 jakob-R52 kernel: [    0.463695] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
Oct 29 19:18:36 jakob-R52 kernel: [    0.465694] Fixed MDIO Bus: probed
Oct 29 19:18:36 jakob-R52 kernel: [    0.465894] PPP generic driver version 2.4.2
Oct 29 19:18:36 jakob-R52 kernel: [    0.466334] tun: Universal TUN/TAP device driver, 1.6
Oct 29 19:18:36 jakob-R52 kernel: [    0.466340] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 29 19:18:36 jakob-R52 kernel: [    0.466739] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.473228] ACPI: Battery Slot [BAT0] (battery present)
Oct 29 19:18:36 jakob-R52 kernel: [    0.473472] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.474807] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.474824]   alloc irq_desc for 19 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.474830]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.474843] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 29 19:18:36 jakob-R52 kernel: [    0.474869] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.474877] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.474967] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.475018] ehci_hcd 0000:00:1d.7: debug port 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.478915] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Oct 29 19:18:36 jakob-R52 kernel: [    0.478952] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xa8000000
Oct 29 19:18:36 jakob-R52 kernel: [    0.500035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 29 19:18:36 jakob-R52 kernel: [    0.500336] hub 1-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.500349] hub 1-0:1.0: 8 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.500518] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.500553] uhci_hcd: USB Universal Host Controller Interface driver
Oct 29 19:18:36 jakob-R52 kernel: [    0.500897] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.501158] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.501174] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    0.501189] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.501197] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.501299] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.501360] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Oct 29 19:18:36 jakob-R52 kernel: [    0.501638] hub 2-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.501649] hub 2-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.502046] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.502294] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [    0.502310]   alloc irq_desc for 17 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502316]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502327] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 29 19:18:36 jakob-R52 kernel: [    0.502340] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.502347] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.502442] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Oct 29 19:18:36 jakob-R52 kernel: [    0.502495] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Oct 29 19:18:36 jakob-R52 kernel: [    0.502769] hub 3-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.502779] hub 3-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.502896]   alloc irq_desc for 18 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502901]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [    0.502912] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 29 19:18:36 jakob-R52 kernel: [    0.502924] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.502931] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.503010] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Oct 29 19:18:36 jakob-R52 kernel: [    0.503066] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Oct 29 19:18:36 jakob-R52 kernel: [    0.503348] hub 4-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.503358] hub 4-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.503475] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 29 19:18:36 jakob-R52 kernel: [    0.503488] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    0.503495] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 29 19:18:36 jakob-R52 kernel: [    0.503577] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Oct 29 19:18:36 jakob-R52 kernel: [    0.503612] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
Oct 29 19:18:36 jakob-R52 kernel: [    0.503880] hub 5-0:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    0.503891] hub 5-0:1.0: 2 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    0.504217] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Oct 29 19:18:36 jakob-R52 kernel: [    0.516905] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.516920] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 29 19:18:36 jakob-R52 kernel: [    0.517187] mice: PS/2 mouse device common for all mice
Oct 29 19:18:36 jakob-R52 kernel: [    0.517527] rtc_cmos 00:06: RTC can wake from S4
Oct 29 19:18:36 jakob-R52 kernel: [    0.517619] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Oct 29 19:18:36 jakob-R52 kernel: [    0.517662] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 29 19:18:36 jakob-R52 kernel: [    0.517927] device-mapper: uevent: version 1.0.3
Oct 29 19:18:36 jakob-R52 kernel: [    0.521803] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Oct 29 19:18:36 jakob-R52 kernel: [    0.524282] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Oct 29 19:18:36 jakob-R52 kernel: [    0.528391] device-mapper: multipath: version 1.1.1 loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.528398] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 29 19:18:36 jakob-R52 kernel: [    0.528682] EISA: Probing bus 0 at eisa.0
Oct 29 19:18:36 jakob-R52 kernel: [    0.528694] Cannot allocate resource for EISA slot 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.528701] Cannot allocate resource for EISA slot 2
Oct 29 19:18:36 jakob-R52 kernel: [    0.528707] Cannot allocate resource for EISA slot 3
Oct 29 19:18:36 jakob-R52 kernel: [    0.528713] Cannot allocate resource for EISA slot 4
Oct 29 19:18:36 jakob-R52 kernel: [    0.528719] Cannot allocate resource for EISA slot 5
Oct 29 19:18:36 jakob-R52 kernel: [    0.528724] Cannot allocate resource for EISA slot 6
Oct 29 19:18:36 jakob-R52 kernel: [    0.528730] Cannot allocate resource for EISA slot 7
Oct 29 19:18:36 jakob-R52 kernel: [    0.528736] Cannot allocate resource for EISA slot 8
Oct 29 19:18:36 jakob-R52 kernel: [    0.528741] EISA: Detected 0 cards.
Oct 29 19:18:36 jakob-R52 kernel: [    0.580727] cpuidle: using governor ladder
Oct 29 19:18:36 jakob-R52 kernel: [    0.580868] cpuidle: using governor menu
Oct 29 19:18:36 jakob-R52 kernel: [    0.581544] TCP cubic registered
Oct 29 19:18:36 jakob-R52 kernel: [    0.581884] NET: Registered protocol family 10
Oct 29 19:18:36 jakob-R52 kernel: [    0.582696] lo: Disabled Privacy Extensions
Oct 29 19:18:36 jakob-R52 kernel: [    0.583214] NET: Registered protocol family 17
Oct 29 19:18:36 jakob-R52 kernel: [    0.585062] P-state transition latency capped at 20 uS
Oct 29 19:18:36 jakob-R52 kernel: [    0.585473] Using IPI No-Shortcut mode
Oct 29 19:18:36 jakob-R52 kernel: [    0.585677] PM: Resume from disk failed.
Oct 29 19:18:36 jakob-R52 kernel: [    0.585700] registered taskstats version 1
Oct 29 19:18:36 jakob-R52 kernel: [    0.586122]   Magic number: 14:491:345
Oct 29 19:18:36 jakob-R52 kernel: [    0.586166] tty tty62: hash matches
Oct 29 19:18:36 jakob-R52 kernel: [    0.586265] rtc_cmos 00:06: setting system clock to 2010-10-29 19:18:22 UTC (1288379902)
Oct 29 19:18:36 jakob-R52 kernel: [    0.586273] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 29 19:18:36 jakob-R52 kernel: [    0.586278] EDD information not available.
Oct 29 19:18:36 jakob-R52 kernel: [    0.668587] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 1.04, max UDMA/33
Oct 29 19:18:36 jakob-R52 kernel: [    0.668761] ata1.00: ATA-6: FUJITSU MHT2080AT, 8431, max UDMA/100
Oct 29 19:18:36 jakob-R52 kernel: [    0.668769] ata1.00: 156301488 sectors, multi 16: LBA 
Oct 29 19:18:36 jakob-R52 kernel: [    0.668803] ata1.00: applying bridge limits
Oct 29 19:18:36 jakob-R52 kernel: [    0.685087] ata2.00: configured for UDMA/33
Oct 29 19:18:36 jakob-R52 kernel: [    0.694105] ata1.00: configured for UDMA/100
Oct 29 19:18:36 jakob-R52 kernel: [    0.843925] usb 1-3: new high speed USB device using ehci_hcd and address 2
Oct 29 19:18:36 jakob-R52 kernel: [    1.043232] hub 1-3:1.0: USB hub found
Oct 29 19:18:36 jakob-R52 kernel: [    1.044026] hub 1-3:1.0: 4 ports detected
Oct 29 19:18:36 jakob-R52 kernel: [    1.108427] isapnp: No Plug & Play device found
Oct 29 19:18:36 jakob-R52 kernel: [    1.108897] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080A 8431 PQ: 0 ANSI: 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.109250] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 29 19:18:36 jakob-R52 kernel: [    1.109563] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Oct 29 19:18:36 jakob-R52 kernel: [    1.109693] sd 0:0:0:0: [sda] Write Protect is off
Oct 29 19:18:36 jakob-R52 kernel: [    1.109701] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 29 19:18:36 jakob-R52 kernel: [    1.109759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 29 19:18:36 jakob-R52 kernel: [    1.110097]  sda:
Oct 29 19:18:36 jakob-R52 kernel: [    1.114641] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 1.04 PQ: 0 ANSI: 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.127662] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 29 19:18:36 jakob-R52 kernel: [    1.127671] Uniform CD-ROM driver Revision: 3.20
Oct 29 19:18:36 jakob-R52 kernel: [    1.127912] sr 1:0:0:0: Attached scsi CD-ROM sr0
Oct 29 19:18:36 jakob-R52 kernel: [    1.128070] sr 1:0:0:0: Attached scsi generic sg1 type 5
Oct 29 19:18:36 jakob-R52 kernel: [    1.144359]  sda1 sda2 < sda5 >
Oct 29 19:18:36 jakob-R52 kernel: [    1.173620] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 29 19:18:36 jakob-R52 kernel: [    1.404983] usb 3-2: new full speed USB device using uhci_hcd and address 2
Oct 29 19:18:36 jakob-R52 kernel: [    1.514282] Freeing initrd memory: 10516k freed
Oct 29 19:18:36 jakob-R52 kernel: [    1.524439] Freeing unused kernel memory: 684k freed
Oct 29 19:18:36 jakob-R52 kernel: [    1.525374] Write protecting the kernel text: 4932k
Oct 29 19:18:36 jakob-R52 kernel: [    1.525467] Write protecting the kernel read-only data: 1976k
Oct 29 19:18:36 jakob-R52 kernel: [    1.572186] udev[69]: starting version 163
Oct 29 19:18:36 jakob-R52 kernel: [    1.704204] usb 1-3.1: new low speed USB device using ehci_hcd and address 4
Oct 29 19:18:36 jakob-R52 kernel: [    1.908248] usb 1-3.3: new low speed USB device using ehci_hcd and address 5
Oct 29 19:18:36 jakob-R52 kernel: [    2.092979] Floppy drive(s): fd0 is 1.44M
Oct 29 19:18:36 jakob-R52 kernel: [    2.108215] usb 1-3.4: new high speed USB device using ehci_hcd and address 6
Oct 29 19:18:36 jakob-R52 kernel: [    2.112613] FDC 0 is a National Semiconductor PC87306
Oct 29 19:18:36 jakob-R52 kernel: [    2.123706] tg3.c:v3.110 (April 9, 2010)
Oct 29 19:18:36 jakob-R52 kernel: [    2.123736] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [    2.123753] tg3 0000:02:00.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [    2.254227] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:0a:e4:c0:bd:cd
Oct 29 19:18:36 jakob-R52 kernel: [    2.254239] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Oct 29 19:18:36 jakob-R52 kernel: [    2.254248] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Oct 29 19:18:36 jakob-R52 kernel: [    2.254256] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Oct 29 19:18:36 jakob-R52 kernel: [    2.256928] usbcore: registered new interface driver hiddev
Oct 29 19:18:36 jakob-R52 kernel: [    2.261984] input: Kensington Kensington USB Wheel Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.1/1-3.1:1.0/input/input4
Oct 29 19:18:36 jakob-R52 kernel: [    2.262434] generic-usb 0003:047D:1012.0001: input,hidraw0: USB HID v1.00 Mouse [Kensington Kensington USB Wheel Mouse] on usb-0000:00:1d.7-3.1/input0
Oct 29 19:18:36 jakob-R52 kernel: [    2.269490] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
Oct 29 19:18:36 jakob-R52 kernel: [    2.270345] generic-usb 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.7-3.3/input0
Oct 29 19:18:36 jakob-R52 kernel: [    2.270663] usbcore: registered new interface driver usbhid
Oct 29 19:18:36 jakob-R52 kernel: [    2.270670] usbhid: USB HID core driver
Oct 29 19:18:36 jakob-R52 kernel: [    2.314913] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Oct 29 19:18:36 jakob-R52 kernel: [    5.236093] Adding 3069948k swap on /dev/sda5.  Priority:-1 extents:1 across:3069948k 
Oct 29 19:18:36 jakob-R52 kernel: [    6.663895] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Oct 29 19:18:36 jakob-R52 kernel: [    7.100200] udev[351]: starting version 163
Oct 29 19:18:36 jakob-R52 kernel: [    9.719426] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
Oct 29 19:18:36 jakob-R52 kernel: [    9.719432] serio: Synaptics pass-through port at isa0060/serio1/input0
Oct 29 19:18:36 jakob-R52 kernel: [    9.761710] parport_pc 00:0b: reported by Plug and Play ACPI
Oct 29 19:18:36 jakob-R52 kernel: [    9.761766] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Oct 29 19:18:36 jakob-R52 kernel: [    9.766249] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Oct 29 19:18:36 jakob-R52 kernel: [    9.840502] Linux agpgart interface v0.103
Oct 29 19:18:36 jakob-R52 kernel: [    9.927912] Non-volatile memory driver v1.3
Oct 29 19:18:36 jakob-R52 kernel: [    9.937490] ppdev: user-space parallel port driver
Oct 29 19:18:36 jakob-R52 kernel: [   10.055228] Linux video capture interface: v2.00
Oct 29 19:18:36 jakob-R52 kernel: [   10.485086] lib80211: common routines for IEEE802.11 drivers
Oct 29 19:18:36 jakob-R52 kernel: [   10.485090] lib80211_crypt: registered algorithm 'NULL'
Oct 29 19:18:36 jakob-R52 kernel: [   10.494278] intel_rng: FWH not detected
Oct 29 19:18:36 jakob-R52 kernel: [   10.527768] lp0: using parport0 (interrupt-driven).
Oct 29 19:18:36 jakob-R52 kernel: [   10.540301] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
Oct 29 19:18:36 jakob-R52 kernel: [   10.540433] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Oct 29 19:18:36 jakob-R52 kernel: [   10.877794] irda_init()
Oct 29 19:18:36 jakob-R52 kernel: [   10.877809] NET: Registered protocol family 23
Oct 29 19:18:36 jakob-R52 kernel: [   10.927793] [drm] Initialized drm 1.1.0 20060810
Oct 29 19:18:36 jakob-R52 kernel: [   10.966825] yenta_cardbus 0000:04:00.0: CardBus bridge found [1014:0532]
Oct 29 19:18:36 jakob-R52 kernel: [   11.047050] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
Oct 29 19:18:36 jakob-R52 kernel: [   11.047081] usb 3-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
Oct 29 19:18:36 jakob-R52 kernel: [   11.090852] usb 3-2: PAS202BCB image sensor detected
Oct 29 19:18:36 jakob-R52 kernel: [   11.092659] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c38, PCI irq 16
Oct 29 19:18:36 jakob-R52 kernel: [   11.092663] yenta_cardbus 0000:04:00.0: Socket status: 30000006
Oct 29 19:18:36 jakob-R52 kernel: [   11.092672] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [io  0x5000-0x8fff]
Oct 29 19:18:36 jakob-R52 kernel: [   11.092676] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x8fff: excluding 0x5000-0x50ff 0x5400-0x54ff
Oct 29 19:18:36 jakob-R52 kernel: [   11.114848] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xa8400000-0xb7ffffff]
Oct 29 19:18:36 jakob-R52 kernel: [   11.114852] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa8400000-0xb7ffffff: excluding 0xa8400000-0xa8bfffff 0xabc00000-0xb03fffff
Oct 29 19:18:36 jakob-R52 kernel: [   11.114876] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge window: [mem 0xd0000000-0xd7ffffff 64bit pref]
Oct 29 19:18:36 jakob-R52 kernel: [   11.114879] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0000000-0xd7ffffff: excluding 0xd0000000-0xd7ffffff
Oct 29 19:18:36 jakob-R52 kernel: [   11.454864] usb 3-2: Initialization succeeded
Oct 29 19:18:36 jakob-R52 kernel: [   11.454961] usb 3-2: V4L2 device registered as video0
Oct 29 19:18:36 jakob-R52 kernel: [   11.454989] usbcore: registered new interface driver zc0301
Oct 29 19:18:36 jakob-R52 kernel: [   11.472708] cfg80211: Calling CRDA to update world regulatory domain
Oct 29 19:18:36 jakob-R52 kernel: [   11.547354] type=1400 audit(1288379913.456:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.547996] type=1400 audit(1288379913.456:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.548367] type=1400 audit(1288379913.460:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
Oct 29 19:18:36 jakob-R52 kernel: [   11.551399] nsc-ircc 00:0c: activated
Oct 29 19:18:36 jakob-R52 kernel: [   11.551403] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
Oct 29 19:18:36 jakob-R52 kernel: [   11.551485] nsc-ircc, chip->init
Oct 29 19:18:36 jakob-R52 kernel: [   11.551498] nsc-ircc, Found chip at base=0x02e
Oct 29 19:18:36 jakob-R52 kernel: [   11.551535] nsc-ircc, driver loaded (Dag Brattli)
Oct 29 19:18:36 jakob-R52 kernel: [   11.553141] IrDA: Registered device irda0
Oct 29 19:18:36 jakob-R52 kernel: [   11.553144] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Oct 29 19:18:36 jakob-R52 kernel: [   12.234492] libipw: 802.11 data/management/control stack, git-1.1.13
Oct 29 19:18:36 jakob-R52 kernel: [   12.234496] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Oct 29 19:18:36 jakob-R52 kernel: [   12.386405] psmouse serio2: ID: 10 00 64
Oct 29 19:18:36 jakob-R52 kernel: [   12.534845] [drm] radeon defaulting to kernel modesetting.
Oct 29 19:18:36 jakob-R52 kernel: [   12.534849] [drm] radeon kernel modesetting enabled.
Oct 29 19:18:36 jakob-R52 kernel: [   12.534974] radeon 0000:01:00.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [   12.535012] radeon 0000:01:00.0: power state changed by ACPI to D0
Oct 29 19:18:36 jakob-R52 kernel: [   12.535022] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 29 19:18:36 jakob-R52 kernel: [   12.535029] radeon 0000:01:00.0: setting latency timer to 64
Oct 29 19:18:36 jakob-R52 kernel: [   12.537873] [drm] initializing kernel modesetting (RV380 0x1002:0x5460).
Oct 29 19:18:36 jakob-R52 kernel: [   12.537990] [drm] register mmio base: 0xA8100000
Oct 29 19:18:36 jakob-R52 kernel: [   12.537993] [drm] register mmio size: 65536
Oct 29 19:18:36 jakob-R52 kernel: [   12.538188] [drm] Generation 2 PCI interface, using max accessible memory
Oct 29 19:18:36 jakob-R52 kernel: [   12.538194] radeon 0000:01:00.0: VRAM: 64M 0xC0000000 - 0xC3FFFFFF (64M used)
Oct 29 19:18:36 jakob-R52 kernel: [   12.538198] radeon 0000:01:00.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
Oct 29 19:18:36 jakob-R52 kernel: [   12.538243]   alloc irq_desc for 43 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.538245]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.538258] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
Oct 29 19:18:36 jakob-R52 kernel: [   12.538264] radeon 0000:01:00.0: radeon: using MSI.
Oct 29 19:18:36 jakob-R52 kernel: [   12.538296] [drm] radeon: irq initialized.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539271] [drm] Detected VRAM RAM=64M, BAR=128M
Oct 29 19:18:36 jakob-R52 kernel: [   12.539276] [drm] RAM width 64bits DDR
Oct 29 19:18:36 jakob-R52 kernel: [   12.539381] [TTM] Zone  kernel: Available graphics memory: 443254 kiB.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539384] [TTM] Zone highmem: Available graphics memory: 512314 kiB.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539386] [TTM] Initializing pool allocator.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539409] [drm] radeon: 64M of VRAM memory ready
Oct 29 19:18:36 jakob-R52 kernel: [   12.539412] [drm] radeon: 512M of GTT memory ready.
Oct 29 19:18:36 jakob-R52 kernel: [   12.539437] [drm] GART: num cpu pages 131072, num gpu pages 131072
Oct 29 19:18:36 jakob-R52 kernel: [   12.540184] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Oct 29 19:18:36 jakob-R52 kernel: [   12.541546] [drm] PCIE GART of 512M enabled (table at 0xC0040000).
Oct 29 19:18:36 jakob-R52 kernel: [   12.542260] [drm] Loading R300 Microcode
Oct 29 19:18:36 jakob-R52 kernel: [   12.588841] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Oct 29 19:18:36 jakob-R52 kernel: [   12.588845] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Oct 29 19:18:36 jakob-R52 kernel: [   12.588955]   alloc irq_desc for 21 on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.588957]   alloc kstat_irqs on node -1
Oct 29 19:18:36 jakob-R52 kernel: [   12.588966] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 29 19:18:36 jakob-R52 kernel: [   12.589051] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Oct 29 19:18:36 jakob-R52 kernel: [   12.666784] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Oct 29 19:18:36 jakob-R52 kernel: [   12.666788] thinkpad_acpi: http://ibm-acpi.sf.net/
Oct 29 19:18:36 jakob-R52 kernel: [   12.666790] thinkpad_acpi: ThinkPad BIOS 76ET28WW (1.08 ), EC 76HT11WW-1.01
Oct 29 19:18:36 jakob-R52 kernel: [   12.666793] thinkpad_acpi: IBM ThinkPad R52, model 18494PU
Oct 29 19:18:36 jakob-R52 kernel: [   12.666795] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Oct 29 19:18:36 jakob-R52 kernel: [   12.666797] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Oct 29 19:18:36 jakob-R52 kernel: [   12.668613] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Oct 29 19:18:36 jakob-R52 kernel: [   12.675371] Registered led device: tpacpi::thinklight
Oct 29 19:18:36 jakob-R52 kernel: [   12.675929] Registered led device: tpacpi::power
Oct 29 19:18:36 jakob-R52 kernel: [   12.676497] Registered led device: tpacpi::standby
Oct 29 19:18:36 jakob-R52 kernel: [   12.682974] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Oct 29 19:18:36 jakob-R52 kernel: [   12.687060] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
Oct 29 19:18:36 jakob-R52 kernel: [   12.687587] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input8
Oct 29 19:18:36 jakob-R52 kernel: [   13.181930] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
Oct 29 19:18:36 jakob-R52 kernel: [   13.201773] usbcore: registered new interface driver snd-usb-audio
Oct 29 19:18:36 jakob-R52 kernel: [   13.261183] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
Oct 29 19:18:36 jakob-R52 kernel: [   13.262904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
Oct 29 19:18:36 jakob-R52 kernel: [   13.263628] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Oct 29 19:18:36 jakob-R52 kernel: [   13.264371] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Oct 29 19:18:36 jakob-R52 kernel: [   13.265046] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
```


Please post the following info and Ill help:

1. Is this a laptop or tower?
2. Manufactuer - If its dell post your tag or service number. HP - post model.

Oops, Missed it. I got it.

---

### Post by coffee412 on 2010-11-01
> **olafurg said:**
> Anyone? Any details missing perhaps? Please ...

I tell you, Most laptops that have overheat issues (no matter what the OS) are caused by dust in the cooling fan and vents, Poor design for heat exchange. Either open up the laptop if you feel comfortable with it or take it to someone that can and get it cleaned out. Most all laptops I service have clogged vents and poor heat transfer designs. I realize that you probably didnt have this problem with windoze but linux requires good equipment. Windoze kinda glosses over stuff. If you have weak hardware or problems with your hardware then linux is going to point that out right away. 

WAIT A MINUTE !

> Oct 29 19:16:03 jakob-R52 kernel: [ 6180.588312] CPU0: Core temperature/speed normal
Oct 29 19:16:07 jakob-R52 kernel: [ 6184.435746] Critical temperature reached (100 C), shutting down.

4 seconds to overheat? Not likely. looks like a kernel or ACPI issue. If you have done an update on it then at boot hit the shift key and choose an other kernel to boot. See if you still have the problem.
If you have not updated yet see if you can get thru an update after letting it cool down for awhile. In the updates just select the new kernel if there is one. Then reboot after update and see if issue is still there. Then you can finish your updates.

---

### Post by olafurg on 2010-11-03
Thanks a million for the help.

I'll check this out straight when I get home after work. But I think it must be that the latest kernel must be installed since the computer was just updated with Maverick. But anyways I'll check it out, and hope for the best.

Also, I think the guy is using the computer in a dock, with the computer closed, so that might be an additional heating problem as well. 

I'll let you know what I find out. Thanks again!

---

### Post by cpcgm on 2010-12-01
Any news?

---

### Post by olafurg on 2010-12-04
He went back to Windows but I think there were still heat problems with it - so it's a hardware problem. Haven't had any more news.

Consider this solved, for now.

---

### Post by mal205 on 2010-12-04
Some of your syslog output says that the laptop is not at the latest BIOS level. It would be worth fixing that.

```

Oct 29 19:18:36 jakob-R52 kernel: [   12.666784] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Oct 29 19:18:36 jakob-R52 kernel: [   12.666788] thinkpad_acpi: http://ibm-acpi.sf.net/
Oct 29 19:18:36 jakob-R52 kernel: [   12.666790] thinkpad_acpi: ThinkPad BIOS 76ET28WW (1.08 ), EC 76HT11WW-1.01
Oct 29 19:18:36 jakob-R52 kernel: [   12.666793] thinkpad_acpi: IBM ThinkPad R52, model 18494PU
Oct 29 19:18:36 jakob-R52 kernel: [   12.666795] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Oct 29 19:18:36 jakob-R52 kernel: [   12.666797] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Oct 29 19:18:36 jakob-R52 kernel: [   12.668613] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
```

---

### Post by cpcgm on 2010-12-04
Well, I'm having the exact same problem and I'm pretty sure it's not a hardware problem. The computer is sometimes shutting down at degrees about 70 ° C but I can compile code at 80 ° C. According to Intel the CPU can work until 100 ° C. I don't get the BIOS message.

---

### Post by ell02 on 2010-12-04
Perhaps a search for the think wiki might help.It does have a fair amount of linux thinkpad stuff.Also type thinkpad into synapttic and you get some specific packages like thinkfan and smapi.
I have no cure for anything but perhaps a direction that will lead somewhere.
I use a T400 without problems and it flies with Lubuntu on it.

---

### Post by cpcgm on 2010-12-04
I'm using Arch Linux, I just stumbled upon this thread. The problem appeared about a week ago so it's probably a bug. I just thought someone might have a clue about what it could be.

---

### Post by SNYP40A1 on 2011-02-09
Find an air compressor.  Go to a local gas station that has an air pump for $0.25 if necessary.  When the tank fills up, press the nozzel against your cooling fan and pull the trigger.  This should cause a huge dust cloud and your computer will start running cooler.

---

### Post by cpcgm on 2011-02-09
My computer is not running hot when it's shutting down.

---


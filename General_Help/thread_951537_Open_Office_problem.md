---
title: "Open Office problem"
date: 2008-10-18
forum: General Help
---

### Post by billbog on 2008-10-18
Hello - I think this issue should be addressed urgently. When I attempt to save an open office document (.odt) it fails to do so . When I open the saved document it comes up with wallpaper.(appearances) the original document has disappeared.Can someone tell me what is going on ? The most important thing with a computer is that it should save documents reliably isn't it. Everyone wants to do that.I am probably doing something stupid but then other stupid people will do the same so can we resolve this.

---

### Post by billbog on 2008-10-18
I  show Sys.log & usr.log
Sys.log
Oct 18 08:50:44 bill syslogd 1.5.0#1ubuntu1: restart.
Oct 18 08:50:44 bill anacron[5396]: Job `cron.daily' terminated
Oct 18 08:50:44 bill anacron[5396]: Job `cron.monthly' started
Oct 18 08:50:44 bill anacron[6278]: Updated timestamp for job `cron.monthly' to 2008-10-18
Oct 18 08:54:17 bill anacron[5396]: Job `cron.monthly' terminated
Oct 18 08:54:17 bill anacron[5396]: Normal exit (2 jobs run)
Oct 18 09:08:36 bill -- MARK --
Oct 18 09:17:01 bill /USR/SBIN/CRON[14632]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 09:28:36 bill -- MARK --
Oct 18 09:48:36 bill -- MARK --
Oct 18 10:02:40 bill pulseaudio[14785]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 10:13:54 bill init: tty4 main process (4478) killed by TERM signal
Oct 18 10:13:54 bill init: tty5 main process (4479) killed by TERM signal
Oct 18 10:13:54 bill init: tty2 main process (4481) killed by TERM signal
Oct 18 10:13:54 bill init: tty3 main process (4483) killed by TERM signal
Oct 18 10:13:54 bill init: tty6 main process (4485) killed by TERM signal
Oct 18 10:13:54 bill init: tty1 main process (5534) killed by TERM signal
Oct 18 10:13:57 bill gdm[5353]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Oct 18 10:13:57 bill gdm[5353]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Oct 18 10:13:57 bill avahi-daemon[4935]: Got SIGTERM, quitting.
Oct 18 10:13:57 bill avahi-daemon[4935]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Oct 18 10:13:58 bill kernel: [ 6359.402607] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 18 10:13:59 bill exiting on signal 15
Oct 18 11:52:02 bill syslogd 1.5.0#1ubuntu1: restart.
Oct 18 11:52:02 bill kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 18 11:52:02 bill kernel: Loaded 27890 symbols from /boot/System.map-2.6.24-21-generic.
Oct 18 11:52:02 bill kernel: Symbols match kernel version 2.6.24.
Oct 18 11:52:02 bill kernel: Loaded 15113 symbols from 84 modules.
Oct 18 11:52:02 bill kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 18 11:52:02 bill kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 18 11:52:02 bill kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
Oct 18 11:52:02 bill kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Oct 18 11:52:02 bill kernel: [    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
Oct 18 11:52:02 bill kernel: [    0.000000] 127MB HIGHMEM available.
Oct 18 11:52:02 bill kernel: [    0.000000] 896MB LOWMEM available.
Oct 18 11:52:02 bill kernel: [    0.000000] Entering add_active_range(0, 0, 261936) 0 entries of 256 used
Oct 18 11:52:02 bill kernel: [    0.000000] Zone PFN ranges:
Oct 18 11:52:02 bill kernel: [    0.000000]   DMA             0 ->     4096
Oct 18 11:52:02 bill kernel: [    0.000000]   Normal       4096 ->   229376
Oct 18 11:52:02 bill kernel: [    0.000000]   HighMem    229376 ->   261936
Oct 18 11:52:02 bill kernel: [    0.000000] Movable zone start PFN for each node
Oct 18 11:52:02 bill kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 18 11:52:02 bill kernel: [    0.000000]     0:        0 ->   261936
Oct 18 11:52:02 bill kernel: [    0.000000] On node 0 totalpages: 261936
Oct 18 11:52:02 bill kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 18 11:52:02 bill kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 18 11:52:02 bill kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 18 11:52:02 bill kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 18 11:52:02 bill kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 18 11:52:02 bill kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Oct 18 11:52:02 bill kernel: [    0.000000]   HighMem zone: 32306 pages, LIFO batch:7
Oct 18 11:52:02 bill kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 18 11:52:02 bill kernel: [    0.000000] DMI 2.3 present.
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F9BC0 checksum 0
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: RSDP 000F9BC0, 0014 (r0 ACPIAM)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: RSDT 3FF30000, 0030 (r1 A M I  OEMRSDT  10000428 MSFT       97)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: FACP 3FF30200, 0081 (r2 A M I  OEMFACP  10000428 MSFT       97)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: DSDT 3FF30360, 342A (r1  P4V88 P4V88001        1 INTL  2002026)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: FACS 3FF40000, 0040
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: APIC 3FF30300, 0052 (r1 A M I  OEMAPIC  10000428 MSFT       97)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: OEMB 3FF40040, 003F (r1 A M I  OEMBIOS  10000428 MSFT       97)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 18 11:52:02 bill kernel: [    0.000000] Processor #0 15:3 APIC version 20
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 18 11:52:02 bill kernel: [    0.000000] Processor #1 15:3 APIC version 20
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 18 11:52:02 bill kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 18 11:52:02 bill kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 18 11:52:02 bill kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 18 11:52:02 bill kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 18 11:52:02 bill kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bffc0000)
Oct 18 11:52:02 bill kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 18 11:52:02 bill kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Oct 18 11:52:02 bill kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Oct 18 11:52:02 bill kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259890
Oct 18 11:52:02 bill kernel: [    0.000000] Kernel command line: root=UUID=abbc2dcf-d813-42f9-bb6c-9bcb7a0271e1 ro quiet splash
Oct 18 11:52:02 bill kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 18 11:52:02 bill kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 18 11:52:02 bill kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 18 11:52:02 bill kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 18 11:52:02 bill kernel: [    0.000000] Initializing CPU#0
Oct 18 11:52:02 bill kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 18 11:52:02 bill kernel: [    0.000000] Detected 2991.807 MHz processor.
Oct 18 11:52:02 bill kernel: [   21.768040] Console: colour VGA+ 80x25
Oct 18 11:52:02 bill kernel: [   21.768043] console [tty0] enabled
Oct 18 11:52:02 bill kernel: [   21.768550] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 18 11:52:02 bill kernel: [   21.769007] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 18 11:52:02 bill kernel: [   21.795165] Memory: 1026604k/1047744k available (2177k kernel code, 20488k reserved, 1006k data, 368k init, 130240k highmem)
Oct 18 11:52:02 bill kernel: [   21.795174] virtual kernel memory layout:
Oct 18 11:52:02 bill kernel: [   21.795175]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 18 11:52:02 bill kernel: [   21.795176]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 18 11:52:02 bill kernel: [   21.795177]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 18 11:52:02 bill kernel: [   21.795178]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 18 11:52:02 bill kernel: [   21.795179]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 18 11:52:02 bill kernel: [   21.795180]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
Oct 18 11:52:02 bill kernel: [   21.795181]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
Oct 18 11:52:02 bill kernel: [   21.795184] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 18 11:52:02 bill kernel: [   21.795229] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 18 11:52:02 bill kernel: [   21.875200] Calibrating delay using timer specific routine.. 5991.81 BogoMIPS (lpj=11983626)
Oct 18 11:52:02 bill kernel: [   21.875229] Security Framework initialized
Oct 18 11:52:02 bill kernel: [   21.875237] SELinux:  Disabled at boot.
Oct 18 11:52:02 bill kernel: [   21.875253] AppArmor: AppArmor initialized
Oct 18 11:52:02 bill kernel: [   21.875257] Failure registering capabilities with primary security module.
Oct 18 11:52:02 bill kernel: [   21.875267] Mount-cache hash table entries: 512
Oct 18 11:52:02 bill kernel: [   21.875409] Initializing cgroup subsys ns
Oct 18 11:52:02 bill kernel: [   21.875415] Initializing cgroup subsys cpuacct
Oct 18 11:52:02 bill kernel: [   21.875430] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Oct 18 11:52:02 bill kernel: [   21.875439] monitor/mwait feature present.
Oct 18 11:52:02 bill kernel: [   21.875441] using mwait in idle threads.
Oct 18 11:52:02 bill kernel: [   21.875447] CPU: Trace cache: 12K uops, L1 D cache: 16K
Oct 18 11:52:02 bill kernel: [   21.875450] CPU: L2 cache: 1024K
Oct 18 11:52:02 bill kernel: [   21.875453] CPU: Physical Processor ID: 0
Oct 18 11:52:02 bill kernel: [   21.875455] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
Oct 18 11:52:02 bill kernel: [   21.875467] Compat vDSO mapped to ffffe000.
Oct 18 11:52:02 bill kernel: [   21.875484] Checking 'hlt' instruction... OK.
Oct 18 11:52:02 bill kernel: [   21.891662] SMP alternatives: switching to UP code
Oct 18 11:52:02 bill kernel: [   21.893614] Early unpacking initramfs... done
Oct 18 11:52:02 bill kernel: [   22.188651] ACPI: Core revision 20070126
Oct 18 11:52:02 bill kernel: [   22.188698] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 18 11:52:02 bill kernel: [   22.190696] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
Oct 18 11:52:02 bill kernel: [   22.190716] SMP alternatives: switching to SMP code
Oct 18 11:52:02 bill kernel: [   22.191535] Booting processor 1/1 eip 3000
Oct 18 11:52:02 bill kernel: [   22.201718] Initializing CPU#1
Oct 18 11:52:02 bill kernel: [   22.278891] Calibrating delay using timer specific routine.. 5983.87 BogoMIPS (lpj=11967742)
Oct 18 11:52:02 bill kernel: [   22.278902] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Oct 18 11:52:02 bill kernel: [   22.278910] monitor/mwait feature present.
Oct 18 11:52:02 bill kernel: [   22.278916] CPU: Trace cache: 12K uops, L1 D cache: 16K
Oct 18 11:52:02 bill kernel: [   22.278919] CPU: L2 cache: 1024K
Oct 18 11:52:02 bill kernel: [   22.278922] CPU: Physical Processor ID: 0
Oct 18 11:52:02 bill kernel: [   22.278924] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043180 0000441d 00000000 00000000 00000000
Oct 18 11:52:02 bill kernel: [   22.279304] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 04
Oct 18 11:52:02 bill kernel: [   22.279351] Total of 2 processors activated (11975.68 BogoMIPS).
Oct 18 11:52:02 bill kernel: [   22.280104] ENABLING IO-APIC IRQs
Oct 18 11:52:02 bill kernel: [   22.280433] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 18 11:52:02 bill kernel: [   22.426931] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 18 11:52:02 bill kernel: [   22.446933] Brought up 2 CPUs
Oct 18 11:52:02 bill kernel: [   22.447019] CPU0 attaching sched-domain:
Oct 18 11:52:02 bill kernel: [   22.447022]  domain 0: span 03
Oct 18 11:52:02 bill kernel: [   22.447024]   groups: 01 02
Oct 18 11:52:02 bill kernel: [   22.447028]   domain 1: span 03
Oct 18 11:52:02 bill kernel: [   22.447030]    groups: 03
Oct 18 11:52:02 bill kernel: [   22.447033] CPU1 attaching sched-domain:
Oct 18 11:52:02 bill kernel: [   22.447034]  domain 0: span 03
Oct 18 11:52:02 bill kernel: [   22.447036]   groups: 02 01
Oct 18 11:52:02 bill kernel: [   22.447039]   domain 1: span 03
Oct 18 11:52:02 bill kernel: [   22.447041]    groups: 03
Oct 18 11:52:02 bill kernel: [   22.447319] net_namespace: 64 bytes
Oct 18 11:52:02 bill kernel: [   22.447328] Booting paravirtualized kernel on bare hardware
Oct 18 11:52:02 bill kernel: [   22.447935] Time: 10:51:41  Date: 10/18/08
Oct 18 11:52:02 bill kernel: [   22.447962] NET: Registered protocol family 16
Oct 18 11:52:02 bill kernel: [   22.448228] EISA bus registered
Oct 18 11:52:02 bill kernel: [   22.448235] ACPI: bus type pci registered
Oct 18 11:52:02 bill kernel: [   22.448400] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Oct 18 11:52:02 bill kernel: [   22.448403] PCI: Using configuration type 1
Oct 18 11:52:02 bill kernel: [   22.448413] Setting up standard PCI resources
Oct 18 11:52:02 bill kernel: [   22.461018] ACPI: EC: Look up EC in DSDT
Oct 18 11:52:02 bill kernel: [   22.464965] ACPI: Interpreter enabled
Oct 18 11:52:02 bill kernel: [   22.464968] ACPI: (supports S0 S1 S3 S4 S5)
Oct 18 11:52:02 bill kernel: [   22.464987] ACPI: Using IOAPIC for interrupt routing
Oct 18 11:52:02 bill kernel: [   22.472686] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 18 11:52:02 bill kernel: [   22.473870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 18 11:52:02 bill kernel: [   22.480425] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
Oct 18 11:52:02 bill kernel: [   22.480532] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
Oct 18 11:52:02 bill kernel: [   22.480634] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
Oct 18 11:52:02 bill kernel: [   22.480737] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Oct 18 11:52:02 bill kernel: [   22.480840] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Oct 18 11:52:02 bill kernel: [   22.480942] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Oct 18 11:52:02 bill kernel: [   22.481044] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Oct 18 11:52:02 bill kernel: [   22.481149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
Oct 18 11:52:02 bill kernel: [   22.481291] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D3, should be C5 [20070126]
Oct 18 11:52:02 bill kernel: [   22.481298] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 18 11:52:02 bill kernel: [   22.481339] pnp: PnP ACPI init
Oct 18 11:52:02 bill kernel: [   22.481348] ACPI: bus type pnp registered
Oct 18 11:52:02 bill kernel: [   22.485535] pnp: PnP ACPI: found 14 devices
Oct 18 11:52:02 bill kernel: [   22.485539] ACPI: ACPI bus type pnp unregistered
Oct 18 11:52:02 bill kernel: [   22.485543] PnPBIOS: Disabled by ACPI PNP
Oct 18 11:52:02 bill kernel: [   22.485879] PCI: Using ACPI for IRQ routing
Oct 18 11:52:02 bill kernel: [   22.485883] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 18 11:52:02 bill kernel: [   22.506909] NET: Registered protocol family 8
Oct 18 11:52:02 bill kernel: [   22.506912] NET: Registered protocol family 20
Oct 18 11:52:02 bill kernel: [   22.506990] AppArmor: AppArmor Filesystem Enabled
Oct 18 11:52:02 bill kernel: [   22.510733] Time: tsc clocksource has been installed.
Oct 18 11:52:02 bill kernel: [   22.522922] system 00:08: ioport range 0x295-0x296 has been reserved
Oct 18 11:52:02 bill kernel: [   22.522926] system 00:08: ioport range 0x3e0-0x3e7 has been reserved
Oct 18 11:52:02 bill kernel: [   22.522928] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 18 11:52:02 bill kernel: [   22.522931] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 18 11:52:02 bill kernel: [   22.522933] system 00:08: ioport range 0x400-0x41f has been reserved
Oct 18 11:52:02 bill kernel: [   22.522943] system 00:09: iomem range 0xfec80000-0xfec800ff has been reserved
Oct 18 11:52:02 bill kernel: [   22.522946] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
Oct 18 11:52:02 bill kernel: [   22.522948] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 18 11:52:02 bill kernel: [   22.522951] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
Oct 18 11:52:02 bill kernel: [   22.522961] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Oct 18 11:52:02 bill kernel: [   22.522963] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
Oct 18 11:52:02 bill kernel: [   22.522966] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Oct 18 11:52:02 bill kernel: [   22.522969] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
Oct 18 11:52:02 bill kernel: [   22.522972] system 00:0d: iomem range 0x0-0x0 could not be reserved
Oct 18 11:52:02 bill kernel: [   22.553502] PCI: Bridge: 0000:00:01.0
Oct 18 11:52:02 bill kernel: [   22.553505]   IO window: disabled.
Oct 18 11:52:02 bill kernel: [   22.553510]   MEM window: fca00000-feafffff
Oct 18 11:52:02 bill kernel: [   22.553514]   PREFETCH window: d7f00000-f7efffff
Oct 18 11:52:02 bill kernel: [   22.553538] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 18 11:52:02 bill kernel: [   22.553550] NET: Registered protocol family 2
Oct 18 11:52:02 bill kernel: [   22.590890] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 18 11:52:02 bill kernel: [   22.591219] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 18 11:52:02 bill kernel: [   22.591821] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 18 11:52:02 bill kernel: [   22.592209] TCP: Hash tables configured (established 131072 bind 65536)
Oct 18 11:52:02 bill kernel: [   22.592212] TCP reno registered
Oct 18 11:52:02 bill kernel: [   22.603008] checking if image is initramfs... it is
Oct 18 11:52:02 bill kernel: [   23.054327] Switched to high resolution mode on CPU 0
Oct 18 11:52:02 bill kernel: [   23.054461] Switched to high resolution mode on CPU 1
Oct 18 11:52:02 bill kernel: [   23.185141] Freeing initrd memory: 7321k freed
Oct 18 11:52:02 bill kernel: [   23.186099] audit: initializing netlink socket (disabled)
Oct 18 11:52:02 bill kernel: [   23.186115] audit(1224327101.268:1): initialized
Oct 18 11:52:02 bill kernel: [   23.186334] highmem bounce pool size: 64 pages
Oct 18 11:52:02 bill kernel: [   23.188781] VFS: Disk quotas dquot_6.5.1
Oct 18 11:52:02 bill kernel: [   23.188885] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 18 11:52:02 bill kernel: [   23.189041] io scheduler noop registered
Oct 18 11:52:02 bill kernel: [   23.189044] io scheduler anticipatory registered
Oct 18 11:52:02 bill kernel: [   23.189047] io scheduler deadline registered
Oct 18 11:52:02 bill kernel: [   23.189059] io scheduler cfq registered (default)
Oct 18 11:52:02 bill kernel: [   23.189073] PCI: VIA PCI bridge detected. Disabling DAC.
Oct 18 11:52:02 bill kernel: [   23.189147] PCI: Bypassing VIA 8237 APIC De-Assert Message
Oct 18 11:52:02 bill kernel: [   23.189170] Boot video device is 0000:01:00.0
Oct 18 11:52:02 bill kernel: [   23.189517] isapnp: Scanning for PnP cards...
Oct 18 11:52:02 bill kernel: [   23.540928] isapnp: No Plug & Play device found
Oct 18 11:52:02 bill kernel: [   23.578331] Real Time Clock Driver v1.12ac
Oct 18 11:52:02 bill kernel: [   23.578454] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 18 11:52:02 bill kernel: [   23.578574] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 18 11:52:02 bill kernel: [   23.579501] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 18 11:52:02 bill kernel: [   23.580488] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 18 11:52:02 bill kernel: [   23.580568] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 18 11:52:02 bill kernel: [   23.580707] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Oct 18 11:52:02 bill kernel: [   23.581123] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 18 11:52:02 bill kernel: [   23.581131] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 18 11:52:02 bill kernel: [   23.590070] mice: PS/2 mouse device common for all mice
Oct 18 11:52:02 bill kernel: [   23.590231] EISA: Probing bus 0 at eisa.0
Oct 18 11:52:02 bill kernel: [   23.590270] EISA: Detected 0 cards.
Oct 18 11:52:02 bill kernel: [   23.590274] cpuidle: using governor ladder
Oct 18 11:52:02 bill kernel: [   23.590276] cpuidle: using governor menu
Oct 18 11:52:02 bill kernel: [   23.590370] NET: Registered protocol family 1
Oct 18 11:52:02 bill kernel: [   23.590401] Using IPI No-Shortcut mode
Oct 18 11:52:02 bill kernel: [   23.590433] registered taskstats version 1
Oct 18 11:52:02 bill kernel: [   23.590529]   Magic number: 12:774:881
Oct 18 11:52:02 bill kernel: [   23.590592]   hash matches device ptyx5
Oct 18 11:52:02 bill kernel: [   23.590647] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 18 11:52:02 bill kernel: [   23.590649] EDD information not available.
Oct 18 11:52:02 bill kernel: [   23.590913] Freeing unused kernel memory: 368k freed
Oct 18 11:52:02 bill kernel: [   23.608323] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 18 11:52:02 bill kernel: [   24.841047] fuse init (API version 7.9)
Oct 18 11:52:02 bill kernel: [   24.864993] ACPI: Processor [CPU1] (supports 16 throttling states)
Oct 18 11:52:02 bill kernel: [   25.366909] SCSI subsystem initialized
Oct 18 11:52:02 bill kernel: [   25.429385] usbcore: registered new interface driver usbfs
Oct 18 11:52:02 bill kernel: [   25.429422] usbcore: registered new interface driver hub
Oct 18 11:52:02 bill kernel: [   25.441284] libata version 3.00 loaded.
Oct 18 11:52:02 bill kernel: [   25.445422] usbcore: registered new device driver usb
Oct 18 11:52:02 bill kernel: [   25.453892] sata_via 0000:00:0f.0: version 2.3
Oct 18 11:52:02 bill kernel: [   25.453921] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
Oct 18 11:52:02 bill kernel: [   25.453970] sata_via 0000:00:0f.0: routed to hard irq line 10
Oct 18 11:52:02 bill kernel: [   25.473328] scsi0 : sata_via
Oct 18 11:52:02 bill kernel: [   25.475971] USB Universal Host Controller Interface driver v3.0
Oct 18 11:52:02 bill kernel: [   25.489285] scsi1 : sata_via
Oct 18 11:52:02 bill kernel: [   25.489355] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 16
Oct 18 11:52:02 bill kernel: [   25.489360] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 16
Oct 18 11:52:02 bill kernel: [   25.495490] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Oct 18 11:52:02 bill kernel: [   25.614543] Floppy drive(s): fd0 is 1.44M
Oct 18 11:52:02 bill kernel: [   25.633051] FDC 0 is a post-1991 82077
Oct 18 11:52:02 bill kernel: [   25.693078] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Oct 18 11:52:02 bill kernel: [   25.904901] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Oct 18 11:52:02 bill kernel: [   25.915937] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
Oct 18 11:52:02 bill kernel: [   25.915959] uhci_hcd 0000:00:10.0: UHCI Host Controller
Oct 18 11:52:02 bill kernel: [   25.916323] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Oct 18 11:52:02 bill kernel: [   25.916364] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000c000
Oct 18 11:52:02 bill kernel: [   25.916573] usb usb1: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   25.916627] hub 1-0:1.0: USB hub found
Oct 18 11:52:02 bill kernel: [   25.916638] hub 1-0:1.0: 2 ports detected
Oct 18 11:52:02 bill kernel: [   26.021021] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
Oct 18 11:52:02 bill kernel: [   26.021040] uhci_hcd 0000:00:10.1: UHCI Host Controller
Oct 18 11:52:02 bill kernel: [   26.021087] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Oct 18 11:52:02 bill kernel: [   26.021118] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000c400
Oct 18 11:52:02 bill kernel: [   26.021280] usb usb2: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   26.021309] hub 2-0:1.0: USB hub found
Oct 18 11:52:02 bill kernel: [   26.021316] hub 2-0:1.0: 2 ports detected
Oct 18 11:52:02 bill kernel: [   26.124842] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
Oct 18 11:52:02 bill kernel: [   26.124864] uhci_hcd 0000:00:10.2: UHCI Host Controller
Oct 18 11:52:02 bill kernel: [   26.124905] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Oct 18 11:52:02 bill kernel: [   26.124933] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000c800
Oct 18 11:52:02 bill kernel: [   26.125118] usb usb3: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   26.125158] hub 3-0:1.0: USB hub found
Oct 18 11:52:02 bill kernel: [   26.125168] hub 3-0:1.0: 2 ports detected
Oct 18 11:52:02 bill kernel: [   26.227769] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
Oct 18 11:52:02 bill kernel: [   26.227786] uhci_hcd 0000:00:10.3: UHCI Host Controller
Oct 18 11:52:02 bill kernel: [   26.227825] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Oct 18 11:52:02 bill kernel: [   26.227854] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000cc00
Oct 18 11:52:02 bill kernel: [   26.228017] usb usb4: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   26.228057] hub 4-0:1.0: USB hub found
Oct 18 11:52:02 bill kernel: [   26.228065] hub 4-0:1.0: 2 ports detected
Oct 18 11:52:02 bill kernel: [   26.332320] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
Oct 18 11:52:02 bill kernel: [   26.332777] eth0: VIA Rhine II at 0xfebffc00, 00:0b:6a:b6:5d:0d, IRQ 18.
Oct 18 11:52:02 bill kernel: [   26.333494] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
Oct 18 11:52:02 bill kernel: [   26.333990] pata_via 0000:00:0f.1: version 0.3.3
Oct 18 11:52:02 bill kernel: [   26.334031] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
Oct 18 11:52:02 bill kernel: [   26.334179] scsi2 : pata_via
Oct 18 11:52:02 bill kernel: [   26.334279] scsi3 : pata_via
Oct 18 11:52:02 bill kernel: [   26.337684] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Oct 18 11:52:02 bill kernel: [   26.337689] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Oct 18 11:52:02 bill kernel: [   26.507953] ata3.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
Oct 18 11:52:02 bill kernel: [   26.507958] ata3.00: 320173056 sectors, multi 16: LBA48 
Oct 18 11:52:02 bill kernel: [   26.508160] ata3.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
Oct 18 11:52:02 bill kernel: [   26.508163] ata3.01: 160086528 sectors, multi 16: LBA 
Oct 18 11:52:02 bill kernel: [   26.523769] ata3.00: configured for UDMA/133
Oct 18 11:52:02 bill kernel: [   26.544743] ata3.01: configured for UDMA/133
Oct 18 11:52:02 bill kernel: [   26.771156] usb 3-1: new full speed USB device using uhci_hcd and address 2
Oct 18 11:52:02 bill kernel: [   26.863480] ata4.00: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
Oct 18 11:52:02 bill kernel: [   26.970467] usb 3-1: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   27.035226] ata4.00: configured for UDMA/33
Oct 18 11:52:02 bill kernel: [   27.035374] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
Oct 18 11:52:02 bill kernel: [   27.035547] scsi 2:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
Oct 18 11:52:02 bill kernel: [   27.037034] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
Oct 18 11:52:02 bill kernel: [   27.037223] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
Oct 18 11:52:02 bill kernel: [   27.037241] ehci_hcd 0000:00:10.4: EHCI Host Controller
Oct 18 11:52:02 bill kernel: [   27.037288] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Oct 18 11:52:02 bill kernel: [   27.037341] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfebff800
Oct 18 11:52:02 bill kernel: [   27.047928] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 18 11:52:02 bill kernel: [   27.048139] usb usb5: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   27.048181] hub 5-0:1.0: USB hub found
Oct 18 11:52:02 bill kernel: [   27.048193] hub 5-0:1.0: 8 ports detected
Oct 18 11:52:02 bill kernel: [   27.176503] Driver 'sd' needs updating - please use bus_type methods
Oct 18 11:52:02 bill kernel: [   27.176632] sd 2:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Oct 18 11:52:02 bill kernel: [   27.176653] sd 2:0:0:0: [sda] Write Protect is off
Oct 18 11:52:02 bill kernel: [   27.176658] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 18 11:52:02 bill kernel: [   27.176693] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 11:52:02 bill kernel: [   27.176786] sd 2:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Oct 18 11:52:02 bill kernel: [   27.176810] sd 2:0:0:0: [sda] Write Protect is off
Oct 18 11:52:02 bill kernel: [   27.176815] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 18 11:52:02 bill kernel: [   27.176854] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 11:52:02 bill kernel: [   27.176862]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Oct 18 11:52:02 bill kernel: [   27.190138]  sda1 sda2 < sda5 >
Oct 18 11:52:02 bill kernel: [   27.210733] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 18 11:52:02 bill kernel: [   27.210831] sd 2:0:1:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
Oct 18 11:52:02 bill kernel: [   27.210854] sd 2:0:1:0: [sdb] Write Protect is off
Oct 18 11:52:02 bill kernel: [   27.210859] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Oct 18 11:52:02 bill kernel: [   27.210893] sd 2:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 11:52:02 bill kernel: [   27.210973] sd 2:0:1:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
Oct 18 11:52:02 bill kernel: [   27.210992] sd 2:0:1:0: [sdb] Write Protect is off
Oct 18 11:52:02 bill kernel: [   27.210996] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Oct 18 11:52:02 bill kernel: [   27.211028] sd 2:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 11:52:02 bill kernel: [   27.211033]  sdb: sdb1 sdb2 < sdb5 >
Oct 18 11:52:02 bill kernel: [   27.259067] sd 2:0:1:0: [sdb] Attached SCSI disk
Oct 18 11:52:02 bill kernel: [   27.266585] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Oct 18 11:52:02 bill kernel: [   27.266592] Uniform CD-ROM driver Revision: 3.20
Oct 18 11:52:02 bill kernel: [   27.266672] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct 18 11:52:02 bill kernel: [   27.267932] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 18 11:52:02 bill kernel: [   27.267967] sd 2:0:1:0: Attached scsi generic sg1 type 0
Oct 18 11:52:02 bill kernel: [   27.267998] sr 3:0:0:0: Attached scsi generic sg2 type 5
Oct 18 11:52:02 bill kernel: [   27.354692] usb 3-1: USB disconnect, address 2
Oct 18 11:52:02 bill kernel: [   27.709136] Attempting manual resume
Oct 18 11:52:02 bill kernel: [   27.709141] swsusp: Resume From Partition 8:5
Oct 18 11:52:02 bill kernel: [   27.709143] PM: Checking swsusp image.
Oct 18 11:52:02 bill kernel: [   27.709380] PM: Resume from disk failed.
Oct 18 11:52:02 bill kernel: [   27.761405] kjournald starting.  Commit interval 5 seconds
Oct 18 11:52:02 bill kernel: [   27.761418] EXT3-fs: mounted filesystem with ordered data mode.
Oct 18 11:52:02 bill kernel: [   28.201959] usb 3-1: new full speed USB device using uhci_hcd and address 3
Oct 18 11:52:02 bill kernel: [   28.406319] usb 3-1: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   28.646583] usb 4-2: new full speed USB device using uhci_hcd and address 2
Oct 18 11:52:02 bill kernel: [   29.503454] usb 4-2: configuration #1 chosen from 1 choice
Oct 18 11:52:02 bill kernel: [   36.103606] input: PC Speaker as /devices/platform/pcspkr/input/input2
Oct 18 11:52:02 bill kernel: [   36.188302] Linux agpgart interface v0.102
Oct 18 11:52:02 bill kernel: [   36.270948] parport_pc 00:06: reported by Plug and Play ACPI
Oct 18 11:52:02 bill kernel: [   36.271049] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Oct 18 11:52:02 bill kernel: [   36.309412] agpgart: Detected VIA PT880 chipset
Oct 18 11:52:02 bill kernel: [   36.313765] agpgart: AGP aperture is 64M @ 0xf8000000
Oct 18 11:52:02 bill kernel: [   36.353357] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 18 11:52:02 bill kernel: [   36.375194] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 18 11:52:02 bill kernel: [   36.886987] input: Power Button (FF) as /devices/virtual/input/input3
Oct 18 11:52:02 bill kernel: [   36.930699] ACPI: Power Button (FF) [PWRF]
Oct 18 11:52:02 bill kernel: [   36.930845] input: Power Button (CM) as /devices/virtual/input/input4
Oct 18 11:52:02 bill kernel: [   36.978656] ACPI: Power Button (CM) [PWRB]
Oct 18 11:52:02 bill kernel: [   38.437283] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Oct 18 11:52:02 bill kernel: [   38.704255] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x3002
Oct 18 11:52:02 bill kernel: [   38.704283] usbcore: registered new interface driver usblp
Oct 18 11:52:02 bill kernel: [   38.733028] usbcore: registered new interface driver libusual
Oct 18 11:52:02 bill kernel: [   38.766245] Initializing USB Mass Storage driver...
Oct 18 11:52:02 bill kernel: [   38.766949] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 18 11:52:02 bill kernel: [   38.769104] usbcore: registered new interface driver usb-storage
Oct 18 11:52:02 bill kernel: [   38.769114] USB Mass Storage support registered.
Oct 18 11:52:02 bill kernel: [   38.769210] usb-storage: device found at 2
Oct 18 11:52:02 bill kernel: [   38.769213] usb-storage: waiting for device to settle before scanning
Oct 18 11:52:02 bill kernel: [   38.814758] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
Oct 18 11:52:02 bill kernel: [   38.814915] PCI: Setting latency timer of device 0000:00:11.5 to 64
Oct 18 11:52:02 bill kernel: [   40.325831] loop: module loaded
Oct 18 11:52:02 bill kernel: [   40.348977] lp0: using parport0 (interrupt-driven).
Oct 18 11:52:02 bill kernel: [   40.426176] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
Oct 18 11:52:02 bill kernel: [   40.995538] EXT3 FS on sda1, internal journal
Oct 18 11:52:02 bill kernel: [   42.190138] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 18 11:52:02 bill kernel: [   42.644651] No dock devices found.
Oct 18 11:52:02 bill kernel: [   43.768241] usb-storage: device scan complete
Oct 18 11:52:02 bill kernel: [   43.768354] scsi 4:0:0:0: Direct-Access     Datafab  KECF-USB         0113 PQ: 0 ANSI: 2
Oct 18 11:52:02 bill kernel: [   43.774218] sd 4:0:0:0: [sdc] 504321 512-byte hardware sectors (258 MB)
Oct 18 11:52:02 bill NetworkManager: <info>  starting... 
Oct 18 11:52:02 bill kernel: [   43.785338] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
Oct 18 11:52:02 bill kernel: [   43.785348] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Oct 18 11:52:02 bill kernel: [   43.794205] sd 4:0:0:0: [sdc] 504321 512-byte hardware sectors (258 MB)
Oct 18 11:52:02 bill kernel: [   43.802186] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
Oct 18 11:52:02 bill kernel: [   43.802195] sd 4:0:0:0: [sdc] Assuming drive cache: write through
Oct 18 11:52:02 bill kernel: [   43.802203]  sdc: sdc1
Oct 18 11:52:02 bill kernel: [   43.811271] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Oct 18 11:52:02 bill kernel: [   43.811349] sd 4:0:0:0: Attached scsi generic sg3 type 0
Oct 18 11:52:02 bill avahi-daemon[4974]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Oct 18 11:52:02 bill avahi-daemon[4974]: Successfully dropped root privileges.
Oct 18 11:52:02 bill avahi-daemon[4974]: avahi-daemon 0.6.22 starting up.
Oct 18 11:52:02 bill avahi-daemon[4974]: Successfully called chroot().
Oct 18 11:52:02 bill avahi-daemon[4974]: Successfully dropped remaining capabilities.
Oct 18 11:52:02 bill avahi-daemon[4974]: No service file found in /etc/avahi/services.
Oct 18 11:52:02 bill avahi-daemon[4974]: Network interface enumeration completed.
Oct 18 11:52:02 bill avahi-daemon[4974]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 18 11:52:02 bill avahi-daemon[4974]: Server startup complete. Host name is bill.local. Local service cookie is 2018256068.
Oct 18 11:52:02 bill kernel: [   43.999491] apm: BIOS not found.
Oct 18 11:52:02 bill kernel: [   44.051969] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:02 bill kernel: [   44.051980] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:02 bill kernel: [   44.051986] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:02 bill kernel: [   44.051996] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:02 bill kernel: [   44.052001] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:02 bill kernel: [   44.087953] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:02 bill kernel: [   44.087967] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:02 bill kernel: [   44.087981] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:02 bill kernel: [   44.087989] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:02 bill kernel: [   44.087995] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:02 bill kernel: [   44.108009] ppdev: user-space parallel port driver
Oct 18 11:52:02 bill kernel: [   44.128910] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:02 bill kernel: [   44.128923] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:02 bill kernel: [   44.128930] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:02 bill kernel: [   44.128938] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:02 bill kernel: [   44.128950] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:02 bill kernel: [   44.164882] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:02 bill kernel: [   44.164891] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:02 bill kernel: [   44.164898] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:02 bill kernel: [   44.164906] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:02 bill kernel: [   44.164911] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:02 bill kernel: [   44.200855] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:02 bill kernel: [   44.200866] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:02 bill kernel: [   44.200874] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:02 bill kernel: [   44.200883] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:02 bill kernel: [   44.200888] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:03 bill kernel: [   44.260806] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:03 bill kernel: [   44.260818] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:03 bill kernel: [   44.260824] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:03 bill kernel: [   44.260831] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:03 bill kernel: [   44.260838] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:03 bill kernel: [   44.296784] sd 4:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct 18 11:52:03 bill kernel: [   44.296795] sd 4:0:0:0: [sdc] Sense Key : Hardware Error [current] 
Oct 18 11:52:03 bill kernel: [   44.296802] sd 4:0:0:0: [sdc] Add. Sense: Data phase error
Oct 18 11:52:03 bill kernel: [   44.296810] end_request: I/O error, dev sdc, sector 504320
Oct 18 11:52:03 bill kernel: [   44.296815] Buffer I/O error on device sdc, logical block 504320
Oct 18 11:52:03 bill kernel: [   44.342939] audit(1224327123.093:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5017 profile="/usr/sbin/cupsd" namespace="default"
Oct 18 11:52:03 bill dhcdbd: Started up.
Oct 18 11:52:05 bill kernel: [   46.738128] cdrom: This disc doesn't have any tracks I recognize!
Oct 18 11:52:05 bill kernel: [   46.764040] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Oct 18 11:52:05 bill NetworkManager: <info>  eth0: Device is fully-supported using driver 'via-rhine'. 
Oct 18 11:52:05 bill NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 18 11:52:05 bill NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 18 11:52:05 bill NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 18 11:52:05 bill NetworkManager: <info>  Deactivating device eth0. 
Oct 18 11:52:05 bill NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 18 11:52:05 bill NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 18 11:52:05 bill hcid[5281]: Bluetooth HCI daemon
Oct 18 11:52:05 bill kernel: [   46.840248] Bluetooth: Core ver 2.11
Oct 18 11:52:05 bill kernel: [   46.840571] NET: Registered protocol family 31
Oct 18 11:52:05 bill kernel: [   46.840576] Bluetooth: HCI device and connection manager initialized
Oct 18 11:52:05 bill kernel: [   46.840581] Bluetooth: HCI socket layer initialized
Oct 18 11:52:05 bill hcid[5281]: Starting SDP server
Oct 18 11:52:05 bill kernel: [   46.855259] Bluetooth: L2CAP ver 2.9
Oct 18 11:52:05 bill kernel: [   46.855266] Bluetooth: L2CAP socket layer initialized
Oct 18 11:52:05 bill hcid[5281]: Created local server at unix:abstract=/var/run/dbus-dWVaLke9ME,guid=00f3c52643a410ca04aa7e0048f9bfd5
Oct 18 11:52:05 bill audio[5298]: Bluetooth Audio daemon
Oct 18 11:52:05 bill input[5300]: Bluetooth Input daemon
Oct 18 11:52:05 bill input[5300]: Registered input manager path:/org/bluez/input
Oct 18 11:52:05 bill audio[5298]: Unix socket created: 5
Oct 18 11:52:05 bill audio[5298]: audio.conf: Key file does not have key 'Enable'
Oct 18 11:52:05 bill audio[5298]: audio.conf: Key file does not have key 'Disable'
Oct 18 11:52:05 bill kernel: [   46.913087] Bluetooth: RFCOMM socket layer initialized
Oct 18 11:52:05 bill kernel: [   46.913105] Bluetooth: RFCOMM TTY layer initialized
Oct 18 11:52:05 bill kernel: [   46.913108] Bluetooth: RFCOMM ver 1.8
Oct 18 11:52:05 bill audio[5298]: add_service_record: got record id 0x10000
Oct 18 11:52:05 bill audio[5298]: audio.conf: Key file does not have key 'Disable'
Oct 18 11:52:05 bill audio[5298]: audio.conf: Key file does not have group 'A2DP'
Oct 18 11:52:05 bill last message repeated 3 times
Oct 18 11:52:05 bill audio[5298]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Oct 18 11:52:05 bill audio[5298]: add_service_record: got record id 0x10001
Oct 18 11:52:05 bill audio[5298]: add_service_record: got record id 0x10002
Oct 18 11:52:05 bill audio[5298]: add_service_record: got record id 0x10003
Oct 18 11:52:05 bill audio[5298]: Registered manager path:/org/bluez/audio
Oct 18 11:52:06 bill hal_lpadmin: add
Oct 18 11:52:06 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 18 11:52:06 bill NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 18 11:52:06 bill NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 18 11:52:06 bill NetworkManager: <debug> [1224327126.534569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) started... 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 18 11:52:06 bill NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 18 11:52:07 bill NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 18 11:52:07 bill NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 18 11:52:07 bill NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 18 11:52:07 bill hal_lpadmin: URIs: ['hp:/usb/PhotoSmart_P1000?serial=ES09F1802SHP', 'usb://HP/PHOTOSMART%20P1000?serial=ES09F1802SHP', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_3002_ES09F1802SHP_if0_printer_ES09F1802SHP']
Oct 18 11:52:08 bill python: hp-makeuri[5394]: error: Device does not support fax.
Oct 18 11:52:08 bill hal_lpadmin: HPLIP Fax URIs: None
Oct 18 11:52:08 bill hal_lpadmin: Not adding printer: billsprinter already exists
Oct 18 11:52:08 bill hal_lpadmin: Not adding printer: PHOTOSMART_P1000 already exists
Oct 18 11:52:08 bill anacron[5417]: Anacron 2.3 started on 2008-10-18
Oct 18 11:52:08 bill NetworkManager: <debug> [1224327128.101857] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3002_ES09F1802SHP_if0_printer_ES09F1802SHP'). 
Oct 18 11:52:08 bill anacron[5417]: Normal exit (0 jobs run)
Oct 18 11:52:08 bill /usr/sbin/cron[5446]: (CRON) INFO (pidfile fd = 3)
Oct 18 11:52:08 bill /usr/sbin/cron[5447]: (CRON) STARTUP (fork ok)
Oct 18 11:52:08 bill /usr/sbin/cron[5447]: (CRON) INFO (Running @reboot jobs)
Oct 18 11:52:08 bill NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct 18 11:52:08 bill kernel: [   50.011933] NET: Registered protocol family 17
Oct 18 11:52:08 bill dhclient: DHCPREQUEST of 192.168.1.68 on eth0 to 255.255.255.255 port 67
Oct 18 11:52:08 bill dhclient: DHCPACK of 192.168.1.68 from 192.168.1.254
Oct 18 11:52:08 bill avahi-daemon[4974]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Oct 18 11:52:08 bill avahi-daemon[4974]: New relevant interface eth0.IPv4 for mDNS.
Oct 18 11:52:08 bill avahi-daemon[4974]: Registering new address record for 192.168.1.68 on eth0.IPv4.
Oct 18 11:52:08 bill dhclient: bound to 192.168.1.68 -- renewal in 38658 seconds.
Oct 18 11:52:08 bill NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Oct 18 11:52:08 bill NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 18 11:52:08 bill NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 18 11:52:09 bill NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 18 11:52:09 bill NetworkManager: <info>    address 192.168.1.68 
Oct 18 11:52:09 bill NetworkManager: <info>    netmask 255.255.255.0 
Oct 18 11:52:09 bill NetworkManager: <info>    broadcast 192.168.1.255 
Oct 18 11:52:09 bill NetworkManager: <info>    gateway 192.168.1.254 
Oct 18 11:52:09 bill NetworkManager: <info>    nameserver 192.168.1.254 
Oct 18 11:52:09 bill NetworkManager: <info>    domain name 'home' 
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 18 11:52:09 bill NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 18 11:52:09 bill NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 18 11:52:09 bill NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 18 11:52:09 bill avahi-daemon[4974]: Withdrawing address record for 192.168.1.68 on eth0.
Oct 18 11:52:09 bill avahi-daemon[4974]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Oct 18 11:52:09 bill avahi-daemon[4974]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 18 11:52:09 bill avahi-daemon[4974]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.68.
Oct 18 11:52:09 bill avahi-daemon[4974]: New relevant interface eth0.IPv4 for mDNS.
Oct 18 11:52:09 bill avahi-daemon[4974]: Registering new address record for 192.168.1.68 on eth0.IPv4.
Oct 18 11:52:10 bill NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 18 11:52:10 bill NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 18 11:52:10 bill NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct 18 11:52:10 bill NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct 18 11:52:10 bill NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 18 11:52:11 bill kernel: [   52.677902] NET: Registered protocol family 10
Oct 18 11:52:11 bill kernel: [   52.678364] lo: Disabled Privacy Extensions
Oct 18 11:52:10 bill ntpdate[5619]: step time server 91.189.94.4 offset -0.885532 sec
Oct 18 11:52:12 bill avahi-daemon[4974]: Registering new address record for fe80::20b:6aff:feb6:5d0d on eth0.*.
Oct 18 11:52:21 bill pulseaudio[5702]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 11:52:21 bill kernel: [   63.520249] eth0: no IPv6 routers present
Oct 18 11:52:23 bill hcid[5281]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Oct 18 11:52:23 bill hcid[5281]: Default authorization agent (:1.22, /org/bluez/auth) registered
Oct 18 11:52:26 bill NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 18 11:52:26 bill NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 18 11:52:30 bill hald: mounted /dev/sdc1 on behalf of uid 1000
Oct 18 11:56:19 bill hald: unmounted /dev/sdc1 from '/media/disk' on behalf of uid 0
Oct 18 11:56:19 bill NetworkManager: <debug> [1224327379.097043] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_5A65_4488'). 
Oct 18 12:12:01 bill -- MARK --
Oct 18 12:17:01 bill /USR/SBIN/CRON[6550]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 12:32:01 bill -- MARK --
Oct 18 12:52:01 bill -- MARK --
Oct 18 13:12:01 bill -- MARK --
Oct 18 13:17:01 bill /USR/SBIN/CRON[6561]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 13:30:42 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:30:42 bill kernel: [ 5959.413602] usblp0: removed
Oct 18 13:30:43 bill hal_lpadmin: remove
Oct 18 13:30:43 bill NetworkManager: <debug> [1224333043.352918] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3002_ES09F1802SHP_if0_printer_ES09F1802SHP'). 
Oct 18 13:31:01 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:46:16 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:46:25 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 

usr.log
Oct 16 10:54:15 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 10:55:46 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 11:34:18 bill dhcdbd: Started up.
Oct 16 11:34:21 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 16 11:34:23 bill python: hp-makeuri[5426]: error: Device does not support fax.
Oct 16 11:34:24 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 16 11:34:24 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 16 11:34:24 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 16 11:34:24 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 16 11:36:30 bill pulseaudio[5673]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 16 13:01:29 bill pulseaudio[6575]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 16 13:21:26 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 13:21:48 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 13:52:03 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 13:52:24 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:09:16 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:09:38 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:21:14 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:21:28 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:28:42 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 14:28:54 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 15:01:46 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 15:02:20 bill last message repeated 3 times
Oct 16 15:11:31 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 15:11:53 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 16 21:17:00 bill dhcdbd: Started up.
Oct 16 21:17:03 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 16 21:17:05 bill python: hp-makeuri[5433]: error: Device does not support fax.
Oct 16 21:17:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 16 21:17:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 16 21:17:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 16 21:17:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 16 21:17:17 bill pulseaudio[5692]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 17 06:52:16 bill dhcdbd: Started up.
Oct 17 06:52:41 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 17 06:52:49 bill python: hp-makeuri[5512]: error: Device does not support fax.
Oct 17 06:52:52 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 17 06:52:52 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 17 06:52:52 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 17 06:52:52 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 17 06:53:02 bill pulseaudio[5659]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 17 18:34:15 bill dhcdbd: Started up.
Oct 17 18:34:25 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 17 18:34:28 bill python: hp-makeuri[5461]: error: Device does not support fax.
Oct 17 18:34:31 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 17 18:34:31 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 17 18:34:31 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 17 18:34:31 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 17 18:34:41 bill pulseaudio[5724]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 17 21:00:44 bill dhcdbd: Started up.
Oct 17 21:00:47 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 17 21:00:48 bill python: hp-makeuri[5370]: error: Device does not support fax.
Oct 17 21:00:53 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 17 21:00:53 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 17 21:00:53 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 17 21:00:53 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 17 21:02:57 bill pulseaudio[5685]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 17 21:36:28 bill pulseaudio[7739]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 08:28:39 bill dhcdbd: Started up.
Oct 18 08:28:42 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 18 08:28:45 bill python: hp-makeuri[5415]: error: Device does not support fax.
Oct 18 08:28:47 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 18 08:28:47 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 18 08:28:47 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 18 08:28:47 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 18 08:29:00 bill pulseaudio[5704]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 10:02:40 bill pulseaudio[14785]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 11:52:03 bill dhcdbd: Started up.
Oct 18 11:52:06 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 18 11:52:08 bill python: hp-makeuri[5394]: error: Device does not support fax.
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 18 11:52:09 bill dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct 18 11:52:21 bill pulseaudio[5702]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Oct 18 13:30:42 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:31:01 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:46:16 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Oct 18 13:46:25 bill PhotoSmart_P1000?serial=ES09F1802SHP: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused

---


---
title: "Misterious Hung ups"
date: 2008-09-16
forum: General Help
---

### Post by Gokudan on 2008-09-16
Hi there!

I'm new to linux, i am currently using Ubuntu 8.04 LTS (with the latest kernel), i have a dell xps m1710 with a 7900GS (dedicated memory), i use compiz fusion and installed the video drivers through EnvyNG 1.1.1 (nvidia drivers 173.14.12)

    Well, the problem is that my pc is hungin up a lot, well at least not the whole OS, but i get some misterious apps hungups, for example, let's say i am using amarok, i use it fine for hours with no problem but then i close it for a few minutes, then decide to open it again and nothing, the same happens with amsn or pidgin, even with FireFox 3.01 or even the appointments and task tool on the bar, u know the tool with the time and day of the month, strangely i have no issues yet with World of Warcraft.

    Also sometimes i hear music with my headset and then all of a sudden i hear sound no more, the same happens with the speakers, i have to reboot to fix the problem.

    also i have issues, that when i use the pc all day when i click on the icon that give the turn off, restart, log off, switch users, etc. options it simply does not work, and sometimes i cames up but it does not allow me to do anything, even if i press Ctrl + Alt + Supr, nothing happens, and then i have to manually turn off the PC.

Any thoughts?? I'm about to quit using Ubuntu since Right Now i have better system stability with XP and even Vista than with ubuntu since in a whole work day i only have to reboot with them once and with ubuntu i need to reboot or manually turn off the PC at least 7 to 10 times.


Thanks for the help.
Br's
Gokudan.

---

### Post by jualin on 2008-09-16
Have you made any changes to your Ubuntu configuration besides installing the video drivers with Envyng? Are you running the latest updates? Just a shot in the dark.

---

### Post by Gokudan on 2008-09-16
Hi Jualin,

     After two weeks from a fresh install of Ubuntu 8.04 LTS i started getting this hung ups, i was not having this problem with the previous version of ubuntu, i have all the latest updates.

Can a virus be doing this? since i had an infected file, but erased it some days ago, i also updated the kernel and everything else (including pidgin, amarok, etc), but i updated everything so fast that i do not kept the track of everything i updated....

Should i try a fresh install without updating kernel to the latest?

BR's
GD

---

### Post by Gokudan on 2008-09-17
*bump from sir bump-a-lot*

---

### Post by jualin on 2008-09-17
I am almost sure that you can dismiss the "virus" posibility since viruses in Linux are very uncommon (almost never happens). One can pretty much argue that Linux has almost no viruses in the wild. Now maybe a fresh install would be the best way to "fix" the problem quickly. However maybe someone else has another suggestion.
Also you may want to check the kernel messages which sometimes tell you what's going on during the hang. To do this go to the terminal and type > gedit /var/log/dmesg. That should give you a long file with a lot of stuff, that may help you identify your problem. Hope this helps!

---

### Post by Gokudan on 2008-09-18
Hi Jualin,

    Thank you for the tip, here's what i got:


> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed9c00 (usable)
[    0.000000]  BIOS-e820: 000000007fed9c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 523993) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523993
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523993
[    0.000000] On node 0 totalpages: 523993
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292316 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
[    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 7FEDA18A, 0044 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: FACP 7FEDB000, 0074 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: DSDT 7FEDBC00, 4B19 (r1 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FEEA400, 0040
[    0.000000] ACPI: HPET 7FEDB700, 0038 (r1 DELL    M07            1 ASL        61)
[    0.000000] ACPI: APIC 7FEDB800, 0068 (r1 DELL    M07     27D70402 ASL        47)
[    0.000000] ACPI: MCFG 7FEDB7C0, 003E (r16 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SLIC 7FEDB89C, 0176 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: OSFR 7FEDAE00, 002C (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: BOOT 7FEDB3C0, 0028 (r1 DELL    M07     27D70402 ASL        61)
[    0.000000] ACPI: SSDT 7FEDA211, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519900
[    0.000000] Kernel command line: root=UUID=08d17859-8092-4b25-a32d-51998abfac66 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2163.854 MHz processor.
[   12.916386] Console: colour VGA+ 80x25
[   12.916392] console [tty0] enabled
[   12.916723] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.917157] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.074354] Memory: 2065948k/2095972k available (2177k kernel code, 28704k reserved, 1006k data, 368k init, 1178468k highmem)
[   13.074365] virtual kernel memory layout:
[   13.074367]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.074369]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.074370]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.074372]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.074373]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   13.074375]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   13.074377]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   13.074382] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.074439] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.074568] hpet clockevent registered
[   13.154534] Calibrating delay using timer specific routine.. 4333.31 BogoMIPS (lpj=8666620)
[   13.154565] Security Framework initialized
[   13.154573] SELinux:  Disabled at boot.
[   13.154593] AppArmor: AppArmor initialized
[   13.154599] Failure registering capabilities with primary security module.
[   13.154612] Mount-cache hash table entries: 512
[   13.154792] Initializing cgroup subsys ns
[   13.154799] Initializing cgroup subsys cpuacct
[   13.154815] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   13.154827] monitor/mwait feature present.
[   13.154830] using mwait in idle threads.
[   13.154836] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.154840] CPU: L2 cache: 4096K
[   13.154844] CPU: Physical Processor ID: 0
[   13.154847] CPU: Processor Core ID: 0
[   13.154850] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   13.154865] Compat vDSO mapped to ffffe000.
[   13.154885] Checking 'hlt' instruction... OK.
[   13.171147] SMP alternatives: switching to UP code
[   13.173794] Early unpacking initramfs... done
[   13.742628] ACPI: Core revision 20070126
[   13.742689] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.746692] CPU0: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz stepping 06
[   13.746716] SMP alternatives: switching to SMP code
[   13.748757] Booting processor 1/1 eip 3000
[   15.596529] Initializing CPU#1
[   15.675146] Calibrating delay using timer specific routine.. 4327.62 BogoMIPS (lpj=8655242)
[   15.675156] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   15.675165] monitor/mwait feature present.
[   15.675169] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.675172] CPU: L2 cache: 4096K
[   15.675176] CPU: Physical Processor ID: 0
[   15.675178] CPU: Processor Core ID: 1
[   15.675180] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000000
[   13.839438] CPU1: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz stepping 06
[   13.839471] Total of 2 processors activated (8660.93 BogoMIPS).
[   13.839674] ENABLING IO-APIC IRQs
[   13.839882] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.986256] checking TSC synchronization [CPU#0 -> CPU#1]:
[   14.006258] Measured 3976891932 cycles TSC warp between CPUs, turning off TSC clock.
[   14.006263] Marking TSC unstable due to: check_tsc_sync_source failed.
[   14.006282] Brought up 2 CPUs
[   14.006316] CPU0 attaching sched-domain:
[   14.006320]  domain 0: span 03
[   14.006323]   groups: 01 02
[   14.006328] CPU1 attaching sched-domain:
[   14.006330]  domain 0: span 03
[   14.006333]   groups: 02 01
[   15.843687] net_namespace: 64 bytes
[   15.843704] Booting paravirtualized kernel on bare hardware
[   15.844453] Time:  9:00:58  Date: 09/18/08
[   15.844495] NET: Registered protocol family 16
[   15.844829] EISA bus registered
[   15.844837] ACPI: bus type pci registered
[   15.873547] PCI: PCI BIOS revision 2.10 entry at 0xfb016, last bus=14
[   15.873551] PCI: Using configuration type 1
[   15.873577] Setting up standard PCI resources
[   14.045491] ACPI: EC: Look up EC in DSDT
[   14.063644] ACPI: SSDT 7FEDA1CE, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[   14.063911] ACPI: Interpreter enabled
[   14.063917] ACPI: (supports S0 S3 S4 S5)
[   14.065015] ACPI: Using IOAPIC for interrupt routing
[   15.928915] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.929959] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.929966] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   15.931939] PCI: Transparent bridge - 0000:00:1e.0
[   15.932008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.932644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   15.932799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   15.933063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.933254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.933439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[   15.933568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   15.966797] ACPI: PCI Interrupt Link [LNKA] (IRQs *9 10 11)
[   15.966977] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[   15.967154] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[   15.967338] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[   15.967513] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   15.967693] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   15.967872] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   15.968051] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   15.968304] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.968357] pnp: PnP ACPI init
[   15.968370] ACPI: bus type pnp registered
[   15.994781] pnpacpi: exceeded the max number of mem resources: 12
[   16.021028] pnp: PnP ACPI: found 12 devices
[   16.021032] ACPI: ACPI bus type pnp unregistered
[   16.021038] PnPBIOS: Disabled by ACPI PNP
[   14.184452] PCI: Using ACPI for IRQ routing
[   14.184456] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.281942] NET: Registered protocol family 8
[   14.281946] NET: Registered protocol family 20
[   14.282004] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.282011] hpet0: 3 64-bit timers, 14318180 Hz
[   14.283064] AppArmor: AppArmor Filesystem Enabled
[   14.285931] Time: hpet clocksource has been installed.
[   14.285952] Switched to high resolution mode on CPU 0
[   16.123109] Switched to high resolution mode on CPU 1
[   16.138921] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[   16.138926] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[   16.138931] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[   16.138936] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   16.138941] system 00:00: iomem range 0x100000-0x7fed9bff could not be reserved
[   16.138946] system 00:00: iomem range 0x7fed9c00-0x7fefffff could not be reserved
[   16.138950] system 00:00: iomem range 0x7ff00000-0x7fffffff could not be reserved
[   16.138955] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
[   16.138960] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   16.138965] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   16.138970] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   16.138975] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[   16.138987] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   16.138991] system 00:02: ioport range 0x1000-0x1005 has been reserved
[   16.138996] system 00:02: ioport range 0x1008-0x100f has been reserved
[   16.139006] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[   16.139011] system 00:03: ioport range 0x1006-0x1007 has been reserved
[   16.139015] system 00:03: ioport range 0x100a-0x1059 could not be reserved
[   16.139020] system 00:03: ioport range 0x1060-0x107f has been reserved
[   16.139024] system 00:03: ioport range 0x1080-0x10bf has been reserved
[   16.139028] system 00:03: ioport range 0x10c0-0x10df has been reserved
[   16.139033] system 00:03: ioport range 0x1010-0x102f has been reserved
[   16.139037] system 00:03: ioport range 0x809-0x809 has been reserved
[   16.139051] system 00:08: ioport range 0xc80-0xcff could not be reserved
[   16.139056] system 00:08: ioport range 0x910-0x91f has been reserved
[   16.139060] system 00:08: ioport range 0x920-0x92f has been reserved
[   16.139064] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[   16.139068] system 00:08: ioport range 0x930-0x97f has been reserved
[   16.139081] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[   16.169827] PCI: Bridge: 0000:00:01.0
[   16.169831]   IO window: e000-efff
[   16.169837]   MEM window: ed000000-efefffff
[   16.169842]   PREFETCH window: d0000000-dfffffff
[   16.169848] PCI: Bridge: 0000:00:1c.0
[   16.169850]   IO window: disabled.
[   16.169858]   MEM window: disabled.
[   16.169863]   PREFETCH window: disabled.
[   16.169871] PCI: Bridge: 0000:00:1c.1
[   16.169873]   IO window: disabled.
[   16.169881]   MEM window: ecf00000-ecffffff
[   16.169887]   PREFETCH window: disabled.
[   16.169894] PCI: Bridge: 0000:00:1c.2
[   16.169896]   IO window: disabled.
[   16.169904]   MEM window: ece00000-ecefffff
[   16.169910]   PREFETCH window: disabled.
[   16.169917] PCI: Bridge: 0000:00:1c.3
[   16.169922]   IO window: d000-dfff
[   16.169929]   MEM window: ecc00000-ecdfffff
[   16.169936]   PREFETCH window: e0000000-e01fffff
[   16.169944] PCI: Bridge: 0000:00:1e.0
[   16.169946]   IO window: disabled.
[   16.169954]   MEM window: ecb00000-ecbfffff
[   16.169960]   PREFETCH window: disabled.
[   16.169985] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.169993] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.170023] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.170031] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.170063] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   16.170071] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.170102] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.170111] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.170142] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   16.170151] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.170169] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.170186] NET: Registered protocol family 2
[   16.215894] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.216241] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.216914] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.217216] TCP: Hash tables configured (established 131072 bind 65536)
[   16.217220] TCP reno registered
[   16.227990] checking if image is initramfs... it is
[   17.349223] Freeing initrd memory: 7322k freed
[   17.349433] Simple Boot Flag at 0x79 set to 0x1
[   17.350569] audit: initializing netlink socket (disabled)
[   17.350587] audit(1221728459.313:1): initialized
[   15.513939] highmem bounce pool size: 64 pages
[   15.517435] VFS: Disk quotas dquot_6.5.1
[   15.517567] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.517774] io scheduler noop registered
[   15.517778] io scheduler anticipatory registered
[   15.517781] io scheduler deadline registered
[   15.517799] io scheduler cfq registered (default)
[   15.517946] Boot video device is 0000:01:00.0
[   15.518127] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.518191] assign_interrupt_mode Found MSI capability
[   15.518238] Allocate Port Service[0000:00:01.0:pcie00]
[   15.518373] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.518447] assign_interrupt_mode Found MSI capability
[   15.518505] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.518563] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.518706] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.518780] assign_interrupt_mode Found MSI capability
[   15.518838] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.518897] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.519045] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.519118] assign_interrupt_mode Found MSI capability
[   15.519177] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.519234] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.519384] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.519457] assign_interrupt_mode Found MSI capability
[   15.519516] Allocate Port Service[0000:00:1c.3:pcie00]
[   15.519573] Allocate Port Service[0000:00:1c.3:pcie02]
[   15.520006] isapnp: Scanning for PnP cards...
[   15.875044] isapnp: No Plug & Play device found
[   15.919416] Real Time Clock Driver v1.12ac
[   15.919643] hpet_resources: 0xfed00000 is busy
[   15.919720] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.921679] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.921790] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.921959] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.925055] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.925063] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.949060] mice: PS/2 mouse device common for all mice
[   15.949255] EISA: Probing bus 0 at eisa.0
[   15.949330] EISA: Mainboard FW_FFFF detected.
[   15.949407] Cannot allocate resource for EISA slot 1
[   15.949447] EISA: Detected 0 cards.
[   15.949451] cpuidle: using governor ladder
[   15.949454] cpuidle: using governor menu
[   15.949573] NET: Registered protocol family 1
[   15.949615] Using IPI No-Shortcut mode
[   15.949654] registered taskstats version 1
[   15.949829]   Magic number: 8:285:20
[   15.949902] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.949906] EDD information not available.
[   15.950123] Freeing unused kernel memory: 368k freed
[   17.789267] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.149759] fuse init (API version 7.9)
[   17.349261] ACPI: SSDT 7FEDA938, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   17.349582] ACPI: SSDT 7FEDA6ED, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   17.350465] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.350474] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.350839] ACPI: SSDT 7FEDAB7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   17.351138] ACPI: SSDT 7FEDA8B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   19.189139] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.189148] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.195812] ACPI: Thermal Zone [THM] (25 C)
[   19.822676] tg3.c:v3.86 (November 9, 2007)
[   19.822753] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   19.822769] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   19.842951] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:1c:23:0d:67:48
[   19.842963] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   19.842967] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.026298] usbcore: registered new interface driver usbfs
[   18.026331] usbcore: registered new interface driver hub
[   18.026377] usbcore: registered new device driver usb
[   18.028350] USB Universal Host Controller Interface driver v3.0
[   18.028415] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   18.028429] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.028435] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.028707] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.028748] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[   18.028945] usb usb1: configuration #1 chosen from 1 choice
[   18.028983] hub 1-0:1.0: USB hub found
[   18.028991] hub 1-0:1.0: 2 ports detected
[   19.918039] SCSI subsystem initialized
[   19.951061] libata version 3.00 loaded.
[   18.131835] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   18.131850] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   18.131857] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   18.131893] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   18.131932] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[   18.132117] usb usb2: configuration #1 chosen from 1 choice
[   18.132157] hub 2-0:1.0: USB hub found
[   18.132165] hub 2-0:1.0: 2 ports detected
[   18.235746] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   18.235761] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   18.235768] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   18.235804] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   18.235841] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[   18.236023] usb usb3: configuration #1 chosen from 1 choice
[   18.236062] hub 3-0:1.0: USB hub found
[   18.236070] hub 3-0:1.0: 2 ports detected
[   18.339733] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[   18.339748] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   18.339754] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   18.339794] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   18.339831] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[   18.340012] usb usb4: configuration #1 chosen from 1 choice
[   18.340053] hub 4-0:1.0: USB hub found
[   18.340060] hub 4-0:1.0: 2 ports detected
[   18.372551] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   20.280661] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   18.443686] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   18.443704] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.443710] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.445345] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   18.449269] ehci_hcd 0000:00:1d.7: debug port 1
[   18.449278] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.449286] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[   20.333409] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ecbff800-ecbfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   18.499459] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.499629] usb usb5: configuration #1 chosen from 1 choice
[   18.499670] hub 5-0:1.0: USB hub found
[   18.499679] hub 5-0:1.0: 8 ports detected
[   18.603689] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   18.603734] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.603754] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   18.614257] ata_piix 0000:00:1f.2: version 2.12
[   18.614265] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   18.614289] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   18.614327] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.614424] scsi0 : ata_piix
[   18.614497] scsi1 : ata_piix
[   18.615771] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   18.615776] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   20.617899] ata1.00: ATA-7: Hitachi HTS721010G9SA00, MCZOC11H, max UDMA/100
[   20.617907] ata1.00: 195371568 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   20.633904] ata1.00: configured for UDMA/100
[   18.895227] usb 1-1: device not accepting address 2, error -71
[   20.798751] ata2.00: ATAPI: Optiarc DVD+/-RW AD-5540A, 103C, max UDMA/33
[   18.968452] Clocksource tsc unstable (delta = -226807533 ns)
[   20.811112] ata2.00: configured for UDMA/33
[   18.974399] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72101 MCZO PQ: 0 ANSI: 5
[   18.975562] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-5540A 103C PQ: 0 ANSI: 5
[   18.985887] Driver 'sd' needs updating - please use bus_type methods
[   18.985988] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   18.986008] sd 0:0:0:0: [sda] Write Protect is off
[   18.986012] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.986041] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.986112] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   18.986129] sd 0:0:0:0: [sda] Write Protect is off
[   18.986132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.986161] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.986166]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   19.005126]  sda1 sda2 sda3 < sda5 sda6 >
[   19.034008] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.876578] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   20.876585] Uniform CD-ROM driver Revision: 3.20
[   20.876662] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.041439] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.041474] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.060978] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   19.289090] usb 1-1: configuration #1 chosen from 1 choice
[   19.291979] hub 1-1:1.0: USB hub found
[   19.293915] hub 1-1:1.0: 4 ports detected
[   21.179414] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc0000ba8d581]
[   19.348622] Attempting manual resume
[   19.348628] swsusp: Resume From Partition 8:5
[   19.348630] PM: Checking swsusp image.
[   19.348892] PM: Resume from disk failed.
[   21.237197] kjournald starting.  Commit interval 5 seconds
[   19.400267] EXT3-fs: mounted filesystem with ordered data mode.
[   19.593562] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   19.721337] usb 1-1.2: configuration #1 chosen from 1 choice
[   19.723173] hub 1-1.2:1.0: USB hub found
[   19.725102] hub 1-1.2:1.0: 3 ports detected
[   20.027669] usb 1-1.4: new full speed USB device using uhci_hcd and address 6
[   20.162406] usb 1-1.4: configuration #1 chosen from 1 choice
[   20.164335] hub 1-1.4:1.0: USB hub found
[   20.166183] hub 1-1.4:1.0: 3 ports detected
[   20.489004] usb 1-1.2.2: new full speed USB device using uhci_hcd and address 7
[   20.606271] usb 1-1.2.2: configuration #1 chosen from 1 choice
[   20.811161] usb 1-1.4.1: new full speed USB device using uhci_hcd and address 8
[   20.934539] usb 1-1.4.1: configuration #1 chosen from 1 choice
[   21.136052] usb 1-1.4.2: new full speed USB device using uhci_hcd and address 9
[   21.265747] usb 1-1.4.2: configuration #1 chosen from 1 choice
[   21.469767] usb 1-1.4.3: new full speed USB device using uhci_hcd and address 10
[   21.598976] usb 1-1.4.3: configuration #1 chosen from 1 choice
[   29.808673] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.876852] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.146511] intel_rng: FWH not detected
[   28.182948] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   28.360860] Linux agpgart interface v0.102
[   28.618251] iTCO_vendor_support: vendor-support=0
[   28.661013] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.862301] ACPI: Battery Slot [BAT0] (battery present)
[   28.862860] ACPI: AC Adapter [AC] (off-line)
[   28.931740] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000
[   28.969638] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3
[   28.992679] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   28.992739] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   29.062216] input: Lid Switch as /devices/virtual/input/input4
[   29.062841] ACPI: Lid Switch [LID]
[   29.062922] input: Power Button (CM) as /devices/virtual/input/input5
[   29.077960] ACPI: Power Button (CM) [PBTN]
[   29.078057] input: Sleep Button (CM) as /devices/virtual/input/input6
[   29.110144] ACPI: Sleep Button (CM) [SBTN]
[   29.110463] ACPI: WMI-Acer: Mapper loaded
[   29.317979] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   29.405742] usb 1-2: new full speed USB device using uhci_hcd and address 11
[   29.587946] usb 1-2: configuration #1 chosen from 1 choice
[   30.109296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2b/LNXVIDEO:00/input/input7
[   30.145341] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.507122] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   30.507128] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   30.507285] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.507304] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   30.507331] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   32.383113] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.383118] ricoh-mmc: Copyright(c) Philip Langdale
[   32.626982] sdhci: Secure Digital Host Controller Interface driver
[   32.626987] sdhci: Copyright(c) Pierre Ossman
[   31.154453] nvidia: module license 'NVIDIA' taints kernel.
[   33.373651] Bluetooth: Core ver 2.11
[   33.374383] NET: Registered protocol family 31
[   33.374386] Bluetooth: HCI device and connection manager initialized
[   33.374392] Bluetooth: HCI socket layer initialized
[   31.580988] Bluetooth: HCI USB driver ver 2.9
[   31.585219] usbcore: registered new interface driver hci_usb
[   31.585414] usbcore: registered new interface driver hiddev
[   31.588167] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.4/1-1.4.2/1-1.4.2:1.0/input/input8
[   31.632549] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.0-1.4.2
[   33.474203] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.4/1-1.4.3/1-1.4.3:1.0/input/input9
[   33.518495] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.0-1.4.3
[   33.521067] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input10
[   31.737461] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   31.742874] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input11
[   31.788502] input,hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   31.788527] usbcore: registered new interface driver usbhid
[   31.788532] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.909031] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
[   34.909049] ricoh-mmc: Controller is now disabled.
[   34.909228] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   34.909254] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.175410] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   35.030651] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   35.030677] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   35.030757] mmc0: SDHCI at 0xecbff400 irq 18 DMA
[   33.196014] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   35.038538] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.038548] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   35.038697] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   33.758222] lp: driver loaded but no devices found
[   35.797463] Adding 4000144k swap on /dev/sda5.  Priority:-1 extents:1 across:4000144k
[   33.997048] EXT3 FS on sda6, internal journal
[   36.119625] kjournald starting.  Commit interval 5 seconds
[   34.283059] EXT3 FS on sda2, internal journal
[   34.283070] EXT3-fs: mounted filesystem with ordered data mode.
[   34.936013] ip_tables: (C) 2000-2006 Netfilter Core Team


I'll try to search this over the forum, but basically i'm clueless lol.

Thanks for the help.

BR's
Gokudan

Edit: Typos.

---

### Post by jualin on 2008-09-19
Maybe that's the problem.> [ 18.985887] Driver 'sd' needs updating - please use bus_type methods I haven't reached that "Linux Knowledge" stage yet so I can't tell you for sure. Maybe someone in the forum can confirm this.

---


---
title: "[SOLVED] Bootup Progress Bar"
date: 2008-11-17
forum: General Help
---

### Post by TopEnder on 2008-11-17
Hi, & Thanks in Advance,

During the boot process and about a 1/3 of the way through the progress bar pauses and changes to scrolling text/script. It displays some minor [COLOR="Red"]errors[/COLOR], as the scrolling text scrolls to fast to read what the error is about. Is ther anyway to either pause the scrolling script or to view the script if stored in a logfile.  

Thanks TopEnder

---

### Post by bigbrovar on 2008-11-17
desmg would show ur the boot of logs and errors .. open terminal and run this ```
dmesg
``` inother to see the out put in a text file so u can easily read it .. and post it here run  this  in terminal ```
dmesg > dmesg.txt 
``` this would then put the out put of dmesg into a txt file called dmesg.txt which you can find in your home directory (home folder)

---

### Post by TopEnder on 2008-11-17
Thanks for your reply,  there is a lot in the following I do not understand.  The PPP: VJ decompression error is one I would like to correct it possible  & I cannot find the other error yet.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:09:30 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] Command line: root=UUID=a04d38bf-a78f-407a-911b-85b9bf56e20e ro quiet splash acpi=noirq
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f5e0000 (usable)
[    0.000000]  BIOS-e820: 000000007f5e0000 - 000000007f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5e3000 - 000000007f5f0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5f0000 - 000000007f600000 (reserved)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 521696) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F68E0 checksum 0
[    0.000000] ACPI: RSDP 000F68E0, 0014 (r0    ASI)
[    0.000000] ACPI: RSDT 7F5E3040, 0040 (r1    ASI     V270 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7F5E30C0, 0074 (r1    ASI     V270 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7F5E3180, 40DF (r1     00       00     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7F5E0000, 0040
[    0.000000] ACPI: SLIC 7F5E73C0, 0176 (r1    ASI     V270 42302E31 GBTU  1010101)
[    0.000000] ACPI: HPET 7F5E7580, 0038 (r1    ASI     V270 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7F5E7600, 003C (r1    ASI     V270 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7F5E72C0, 0084 (r1    ASI     V270 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7F5E7680, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7F5E7B10, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007f5e0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 521696) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007f5e0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   521696
[    0.000000] On node 0 totalpages: 521599
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7076 pages used for memmap
[    0.000000]   DMA32 zone: 510524 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #4 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f600000:50a00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513247
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=a04d38bf-a78f-407a-911b-85b9bf56e20e ro quiet splash acpi=noirq
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   26.690159] time.c: Detected 2333.332 MHz processor.
[   26.691186] Console: colour VGA+ 80x25
[   26.691190] console [tty0] enabled
[   26.691204] Checking aperture...
[   26.691211] Calgary: detecting Calgary via BIOS EBDA area
[   26.691213] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   26.708348] Memory: 2045164k/2086784k available (2490k kernel code, 41232k reserved, 1318k data, 320k init)
[   26.708380] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   26.787959] Calibrating delay using timer specific routine.. 4669.85 BogoMIPS (lpj=9339714)
[   26.787987] Security Framework initialized
[   26.787992] SELinux:  Disabled at boot.
[   26.788002] AppArmor: AppArmor initialized
[   26.788005] Failure registering capabilities with primary security module.
[   26.788164] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   26.789213] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.789680] Mount-cache hash table entries: 256
[   26.789788] Initializing cgroup subsys ns
[   26.789794] Initializing cgroup subsys cpuacct
[   26.789806] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.789808] CPU: L2 cache: 4096K
[   26.789809] CPU 0/0 -> Node 0
[   26.789811] using mwait in idle threads.
[   26.789812] CPU: Physical Processor ID: 0
[   26.789813] CPU: Processor Core ID: 0
[   26.789820] CPU0: Thermal monitoring enabled (TM2)
[   26.789831] SMP alternatives: switching to UP code
[   26.790514] Early unpacking initramfs... done
[   27.084216] ACPI: Core revision 20070126
[   27.084247] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.195748] ExtINT not setup in hardware but reported by MP table
[   27.235934] Using local APIC timer interrupts.
[   27.278711] APIC timer calibration result 20833311
[   27.278712] Detected 20.833 MHz APIC timer.
[   27.278778] SMP alternatives: switching to SMP code
[   27.279387] Booting processor 1/2 APIC 0x1
[   27.289731] Initializing CPU#1
[   27.366544] Calibrating delay using timer specific routine.. 4666.69 BogoMIPS (lpj=9333392)
[   27.366550] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.366551] CPU: L2 cache: 4096K
[   27.366553] CPU 1/1 -> Node 0
[   27.366554] CPU: Physical Processor ID: 0
[   27.366555] CPU: Processor Core ID: 1
[   27.366560] CPU1: Thermal monitoring enabled (TM2)
[   27.366993] Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[   27.367032] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   27.387340] Brought up 2 CPUs
[   27.387405] CPU0 attaching sched-domain:
[   27.387407]  domain 0: span 03
[   27.387408]   groups: 01 02
[   27.387411]   domain 1: span 03
[   27.387412]    groups: 03
[   27.387414] CPU1 attaching sched-domain:
[   27.387415]  domain 0: span 03
[   27.387416]   groups: 02 01
[   27.387418]   domain 1: span 03
[   27.387419]    groups: 03
[   27.387606] net_namespace: 120 bytes
[   27.387892] Time: 18:22:20  Date: 11/17/08
[   27.387911] NET: Registered protocol family 16
[   27.388059] ACPI: bus type pci registered
[   27.388115] PCI: Using configuration type 1
[   27.389043] ACPI: EC: Look up EC in DSDT
[   27.392162] ACPI: Interpreter enabled
[   27.392166] ACPI: (supports S0 S3 S4 S5)
[   27.392183] ACPI: Using PIC for interrupt routing
[   27.395623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.396042] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   27.396045] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   27.396286] PCI: Transparent bridge - 0000:00:1e.0
[   27.396304] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.396462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   27.396531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   27.403584] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.403609] pnp: PnP ACPI init
[   27.403614] ACPI: bus type pnp registered
[   27.403986] pnp: IRQ 8 override to level, low
[   27.403988] PCI: setting IRQ 8 as level-triggered
[   27.405381] pnpacpi: exceeded the max number of mem resources: 12
[   27.405481] pnp: PnP ACPI: found 13 devices
[   27.405482] ACPI: ACPI bus type pnp unregistered
[   27.405665] PCI: Probing PCI hardware
[   27.405668] sysfs: duplicate filename 'bridge' can not be created
[   27.405669] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   27.405672] Pid: 1, comm: swapper Not tainted 2.6.24-21-generic #1
[   27.405673] 
[   27.405674] Call Trace:
[   27.405680]  [<ffffffff80303cb8>] sysfs_add_one+0xb8/0xf0
[   27.405682]  [<ffffffff80304cb3>] sysfs_create_link+0xa3/0x140
[   27.405686]  [<ffffffff8035891a>] pci_bus_add_devices+0x7a/0x150
[   27.405689]  [<ffffffff8060329e>] pci_legacy_init+0x5e/0x110
[   27.405693]  [<ffffffff805e0a74>] kernel_init+0x164/0x350
[   27.405696]  [<ffffffff8020d198>] child_rip+0xa/0x12
[   27.405698]  [<ffffffff805e0910>] kernel_init+0x0/0x350
[   27.405700]  [<ffffffff8020d18e>] child_rip+0x0/0x12
[   27.405701] 
[   27.405702] pci 0000:00:1c.0: Error creating sysfs bridge symlink, continuing...
[   27.405736] sysfs: duplicate filename 'bridge' can not be created
[   27.405738] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
[   27.405740] Pid: 1, comm: swapper Not tainted 2.6.24-21-generic #1
[   27.405741] 
[   27.405741] Call Trace:
[   27.405743]  [<ffffffff80303cb8>] sysfs_add_one+0xb8/0xf0
[   27.405745]  [<ffffffff80304cb3>] sysfs_create_link+0xa3/0x140
[   27.405747]  [<ffffffff8035891a>] pci_bus_add_devices+0x7a/0x150
[   27.405749]  [<ffffffff8060329e>] pci_legacy_init+0x5e/0x110
[   27.405751]  [<ffffffff805e0a74>] kernel_init+0x164/0x350
[   27.405754]  [<ffffffff8020d198>] child_rip+0xa/0x12
[   27.405756]  [<ffffffff805e0910>] kernel_init+0x0/0x350
[   27.405757]  [<ffffffff8020d18e>] child_rip+0x0/0x12
[   27.405758] 
[   27.405759] pci 0000:00:1e.0: Error creating sysfs bridge symlink, continuing...
[   27.405877] PCI: Discovered primary peer bus ff [IRQ]
[   27.405881] PCI: Using IRQ router PIIX/ICH [8086/27b8] at 0000:00:1f.0
[   27.405886] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 16
[   27.405889] PCI->APIC IRQ transform: 0000:00:1b.0[A] -> IRQ 16
[   27.405891] PCI->APIC IRQ transform: 0000:00:1c.0[A] -> IRQ 16
[   27.405893] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 23
[   27.405895] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   27.405898] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   27.405900] PCI->APIC IRQ transform: 0000:00:1d.3[D] -> IRQ 16
[   27.405903] PCI->APIC IRQ transform: 0000:00:1d.7[A] -> IRQ 23
[   27.405907] PCI->APIC IRQ transform: 0000:00:1f.2[B] -> IRQ 19
[   27.405909] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 19
[   27.405912] PCI->APIC IRQ transform: 0000:02:00.0[A] -> IRQ 20
[   27.414545] NET: Registered protocol family 8
[   27.414546] NET: Registered protocol family 20
[   27.414574] PCI-GART: No AMD northbridge found.
[   27.414578] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.414581] hpet0: 3 64-bit timers, 14318180 Hz
[   27.415611] AppArmor: AppArmor Filesystem Enabled
[   27.418500] Time: tsc clocksource has been installed.
[   27.418506] Switched to high resolution mode on CPU 0
[   27.419334] Switched to high resolution mode on CPU 1
[   27.426502] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   27.426504] system 00:01: ioport range 0x290-0x29f has been reserved
[   27.426507] system 00:01: ioport range 0x800-0x87f has been reserved
[   27.426509] system 00:01: ioport range 0x290-0x294 has been reserved
[   27.426511] system 00:01: ioport range 0x880-0x88f has been reserved
[   27.426518] system 00:09: ioport range 0x400-0x4bf could not be reserved
[   27.426523] system 00:0a: iomem range 0xd0000000-0xdfffffff could not be reserved
[   27.426527] system 00:0b: iomem range 0xcb400-0xcbfff has been reserved
[   27.426530] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   27.426532] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   27.426534] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   27.426536] system 00:0b: iomem range 0x7f5e0000-0x7f5fffff could not be reserved
[   27.426539] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   27.426541] system 00:0b: iomem range 0x100000-0x7f5dffff could not be reserved
[   27.426543] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.426545] system 00:0b: iomem range 0xfed13000-0xfed1dfff has been reserved
[   27.426548] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[   27.426550] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.426552] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[   27.426856] PCI: Bridge: 0000:00:1c.0
[   27.426858]   IO window: c000-cfff
[   27.426861]   MEM window: disabled.
[   27.426864]   PREFETCH window: disabled.
[   27.426867] PCI: Bridge: 0000:00:1e.0
[   27.426869]   IO window: d000-dfff
[   27.426872]   MEM window: f0100000-f01fffff
[   27.426874]   PREFETCH window: disabled.
[   27.426893] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.426902] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.426908] NET: Registered protocol family 2
[   27.462487] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   27.462974] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   27.464149] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   27.464590] TCP: Hash tables configured (established 262144 bind 65536)
[   27.464592] TCP reno registered
[   27.474532] checking if image is initramfs... it is
[   28.052904] Freeing initrd memory: 7545k freed
[   28.055901] audit: initializing netlink socket (disabled)
[   28.055917] audit(1226946140.208:1): initialized
[   28.057436] VFS: Disk quotas dquot_6.5.1
[   28.057486] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   28.057576] io scheduler noop registered
[   28.057577] io scheduler anticipatory registered
[   28.057579] io scheduler deadline registered
[   28.057651] io scheduler cfq registered (default)
[   28.057659] Boot video device is 0000:00:02.0
[   28.059482] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.059513] assign_interrupt_mode Found MSI capability
[   28.059540] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.059567] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.076906] Real Time Clock Driver v1.12ac
[   28.077028] hpet_resources: 0xfed00000 is busy
[   28.077055] Linux agpgart interface v0.102
[   28.077057] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.077157] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.077889] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.078130] 0000:02:00.0: ttyS1 at I/O 0xd008 (irq = 20) is a 16450
[   28.078222] 0000:02:00.0: ttyS2 at I/O 0xd010 (irq = 20) is a 8250
[   28.078314] 0000:02:00.0: ttyS3 at I/O 0xd018 (irq = 20) is a 16450
[   28.078347] Couldn't register serial port 0000:02:00.0: -28
[   28.078775] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.078820] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.078917] PNP: No PS/2 controller found. Probing ports directly.
[   28.079195] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.079199] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.093718] mice: PS/2 mouse device common for all mice
[   28.093748] cpuidle: using governor ladder
[   28.093750] cpuidle: using governor menu
[   28.093861] NET: Registered protocol family 1
[   28.093928] registered taskstats version 1
[   28.093992]   Magic number: 0:42:393
[   28.094046] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   28.094048] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.094049] EDD information not available.
[   28.094055] Freeing unused kernel memory: 320k freed
[   28.094944] Write protecting the kernel read-only data: 1036k
[   29.252928] fuse init (API version 7.9)
[   29.265390] ACPI: Processor [CPU0] (supports 8 throttling states)
[   29.265486] ACPI: SSDT 7F5E7A80, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   29.265591] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.265602] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.265611] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.334345] usbcore: registered new interface driver usbfs
[   29.334362] usbcore: registered new interface driver hub
[   29.334565] usbcore: registered new device driver usb
[   29.335508] USB Universal Host Controller Interface driver v3.0
[   29.335552] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.335555] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.335727] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.335751] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
[   29.335853] usb usb1: configuration #1 chosen from 1 choice
[   29.335870] hub 1-0:1.0: USB hub found
[   29.335874] hub 1-0:1.0: 2 ports detected
[   29.438507] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.438511] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.438528] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.438551] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
[   29.438622] usb usb2: configuration #1 chosen from 1 choice
[   29.438639] hub 2-0:1.0: USB hub found
[   29.438643] hub 2-0:1.0: 2 ports detected
[   29.492651] SCSI subsystem initialized
[   29.501121] libata version 3.00 loaded.
[   29.542320] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.542324] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.542341] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.542364] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
[   29.542440] usb usb3: configuration #1 chosen from 1 choice
[   29.542455] hub 3-0:1.0: USB hub found
[   29.542459] hub 3-0:1.0: 2 ports detected
[   29.646085] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.646088] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.646106] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   29.646128] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
[   29.646202] usb usb4: configuration #1 chosen from 1 choice
[   29.646217] hub 4-0:1.0: USB hub found
[   29.646221] hub 4-0:1.0: 2 ports detected
[   29.750728] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.750734] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.750767] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.754673] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   29.754679] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0284000
[   29.781749] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   29.794240] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.794331] usb usb5: configuration #1 chosen from 1 choice
[   29.794351] hub 5-0:1.0: USB hub found
[   29.794357] hub 5-0:1.0: 8 ports detected
[   29.897702] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   29.900315] ata_piix 0000:00:1f.2: version 2.12
[   29.900319] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   29.900345] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   29.900416] scsi0 : ata_piix
[   29.900446] scsi1 : ata_piix
[   29.900928] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   29.900930] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   30.097274] ata1.00: HPA unlocked: 160084415 -> 160086528, native 160086528
[   30.097278] ata1.00: ATA-7: Maxtor 6Y080M0, YAR51EW0, max UDMA/133
[   30.097281] ata1.00: 160086528 sectors, multi 16: LBA 
[   30.105259] ata1.01: HPA unlocked: 312579695 -> 312581808, native 312581808
[   30.105262] ata1.01: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   30.105264] ata1.01: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.121423] ata1.00: configured for UDMA/133
[   30.137897] ata1.01: configured for UDMA/133
[   30.345125] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   30.465207] ata2.00: ATA-7: HDS728080PLA380, PF2OA6BA, max UDMA/133
[   30.465210] ata2.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.465224] ata2.01: ATAPI: SONY    DVD RW AW-G170S, 1.73, max UDMA/66
[   30.481182] ata2.00: configured for UDMA/133
[   30.524804] usb 5-4: configuration #1 chosen from 1 choice
[   30.656179] ata2.01: configured for UDMA/66
[   30.656257] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080M0   YAR5 PQ: 0 ANSI: 5
[   30.656331] scsi 0:0:1:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   30.656398] scsi 1:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[   30.657273] scsi 1:0:1:0: CD-ROM            SONY     DVD RW AW-G170S  1.73 PQ: 0 ANSI: 5
[   30.662666] Driver 'sd' needs updating - please use bus_type methods
[   30.662715] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   30.662723] sd 0:0:0:0: [sda] Write Protect is off
[   30.662725] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.662737] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.662771] sd 0:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
[   30.662778] sd 0:0:0:0: [sda] Write Protect is off
[   30.662780] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.662791] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.662793]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   30.687279]  sda1 sda2
[   30.687332] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.687376] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   30.687385] sd 0:0:1:0: [sdb] Write Protect is off
[   30.687387] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   30.687400] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.687431] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   30.687443] sd 0:0:1:0: [sdb] Write Protect is off
[   30.687445] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   30.687456] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.687458]  sdb: sdb1 sdb2 sdb3
[   30.721300] sd 0:0:1:0: [sdb] Attached SCSI disk
[   30.721339] sd 1:0:0:0: [sdc] 160836480 512-byte hardware sectors (82348 MB)
[   30.721347] sd 1:0:0:0: [sdc] Write Protect is off
[   30.721349] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   30.721362] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.721390] sd 1:0:0:0: [sdc] 160836480 512-byte hardware sectors (82348 MB)
[   30.721398] sd 1:0:0:0: [sdc] Write Protect is off
[   30.721400] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   30.721418] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.721420]  sdc: sdc1 sdc2
[   30.733457] sd 1:0:0:0: [sdc] Attached SCSI disk
[   30.737255] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.737270] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   30.737282] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   30.737294] sr 1:0:1:0: Attached scsi generic sg3 type 5
[   30.741262] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   30.741265] Uniform CD-ROM driver Revision: 3.20
[   30.741296] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   30.948011] usbcore: registered new interface driver libusual
[   30.951205] Initializing USB Mass Storage driver...
[   31.069362] Attempting manual resume
[   31.069364] swsusp: Resume From Partition 8:18
[   31.069365] PM: Checking swsusp image.
[   31.069478] PM: Resume from disk failed.
[   31.074199] ReiserFS: sdb3: found reiserfs format "3.6" with standard journal
[   31.074205] ReiserFS: sdb3: using ordered data mode
[   31.079521] ReiserFS: sdb3: journal params: device sdb3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   31.079893] ReiserFS: sdb3: checking transaction log (sdb3)
[   31.138497] ReiserFS: sdb3: Using r5 hash to sort names
[   31.187430] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   31.401825] usb 3-1: configuration #1 chosen from 1 choice
[   31.404890] scsi2 : SCSI emulation for USB Mass Storage devices
[   31.404940] usbcore: registered new interface driver usb-storage
[   31.404944] USB Mass Storage support registered.
[   31.405072] usb-storage: device found at 2
[   31.405073] usb-storage: waiting for device to settle before scanning
[   31.642539] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   31.823962] usb 4-1: configuration #1 chosen from 1 choice
[   36.398255] usb-storage: device scan complete
[   36.402361] scsi 2:0:0:0: Direct-Access     Generic  Flash HS-CF      3.95 PQ: 0 ANSI: 0
[   36.406227] scsi 2:0:0:1: Direct-Access     Generic  Flash HS-MS      3.95 PQ: 0 ANSI: 0
[   36.409996] scsi 2:0:0:2: Direct-Access     Generic  Flash HS-SM      3.95 PQ: 0 ANSI: 0
[   36.413215] scsi 2:0:0:3: Direct-Access     Generic  Flash HS-SD/MMC  3.95 PQ: 0 ANSI: 0
[   36.417725] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[   36.417752] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   36.422209] sd 2:0:0:1: [sde] Attached SCSI removable disk
[   36.422231] sd 2:0:0:1: Attached scsi generic sg5 type 0
[   36.427085] sd 2:0:0:2: [sdf] Attached SCSI removable disk
[   36.427108] sd 2:0:0:2: Attached scsi generic sg6 type 0
[   36.477746] sd 2:0:0:3: [sdg] Attached SCSI removable disk
[   36.477780] sd 2:0:0:3: Attached scsi generic sg7 type 0
[   39.360971] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.411559] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   39.772067] agpgart: Detected an Intel G33 Chipset.
[   39.773521] agpgart: Detected 7164K stolen memory.
[   39.786098] agpgart: AGP aperture is 256M @ 0xe0000000
[   40.089103] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.144830] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.268204] input: Power Button (FF) as /devices/virtual/input/input1
[   40.299281] iTCO_vendor_support: vendor-support=0
[   40.300589] ACPI: Power Button (FF) [PWRF]
[   40.300641] input: Power Button (CM) as /devices/virtual/input/input2
[   40.369246] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   40.372417] ACPI: Power Button (CM) [PWRB]
[   40.449679] parport_pc 00:08: reported by Plug and Play ACPI
[   40.449740] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.457628] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   40.457682] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   40.457708] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.559312] intel_rng: FWH not detected
[   40.849351] Linux video capture interface: v2.00
[   41.087141] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[   41.236012] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   41.268443] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   41.412223] usbcore: registered new interface driver gspca
[   41.412227] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   41.412326] usbcore: registered new interface driver hiddev
[   41.426309] input: Liteon Microsoft® Wireless Receiver 700 v2.0 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input4
[   41.474753] input,hidraw0: USB HID v1.11 Keyboard [Liteon Microsoft® Wireless Receiver 700 v2.0] on usb-0000:00:1d.3-1
[   41.498249] input: Liteon Microsoft® Wireless Receiver 700 v2.0 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.1/input/input5
[   41.594012] input,hidraw1: USB HID v1.11 Mouse [Liteon Microsoft® Wireless Receiver 700 v2.0] on usb-0000:00:1d.3-1
[   41.594031] usbcore: registered new interface driver usbhid
[   41.594034] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.594297] usbcore: registered new interface driver snd-usb-audio
[   42.105010] lp0: using parport0 (interrupt-driven).
[   42.145535] Adding 2000084k swap on /dev/sdb2.  Priority:-1 extents:1 across:2000084k
[   72.780701] kjournald starting.  Commit interval 5 seconds
[   72.787756] EXT3 FS on sdc1, internal journal
[   72.787760] EXT3-fs: mounted filesystem with ordered data mode.
[   72.811907] kjournald starting.  Commit interval 5 seconds
[   72.819179] EXT3 FS on sdb1, internal journal
[   72.819181] EXT3-fs: mounted filesystem with ordered data mode.
[   73.655955] No dock devices found.
[   74.673873] ppdev: user-space parallel port driver
[   74.882143] audit(1226911987.926:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8366 profile="/usr/sbin/cupsd" namespace="default"
[   78.614031] Bluetooth: Core ver 2.11
[   78.614345] NET: Registered protocol family 31
[   78.614348] Bluetooth: HCI device and connection manager initialized
[   78.614351] Bluetooth: HCI socket layer initialized
[   78.637044] Bluetooth: L2CAP ver 2.9
[   78.637047] Bluetooth: L2CAP socket layer initialized
[   78.672182] Bluetooth: RFCOMM socket layer initialized
[   78.672195] Bluetooth: RFCOMM TTY layer initialized
[   78.672197] Bluetooth: RFCOMM ver 1.8
[   79.925558] [drm] Initialized drm 1.1.0 20060810
[   79.928666] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   79.928710] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   80.195735] set status page addr 0x00033000
[   90.673736] NET: Registered protocol family 10
[   90.673956] lo: Disabled Privacy Extensions
[  816.779384] PPP generic driver version 2.4.2
[  846.183812] PPP BSD Compression module registered
[  846.211316] PPP Deflate Compression module registered
[  949.908008] Inbound IN=ppp0 OUT= MAC= SRC=144.134.41.141 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=47960 DF PROTO=TCP SPT=58364 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 1081.279314] PPP: VJ decompression error
[ 1081.534809] PPP: VJ decompression error
[ 1081.662555] PPP: VJ decompression error
[ 1081.790307] PPP: VJ decompression error
[ 1081.918039] PPP: VJ decompression error
[ 1082.045829] PPP: VJ decompression error
[ 1082.169553] PPP: VJ decompression error
[ 1082.425009] PPP: VJ decompression error
[ 1082.552746] PPP: VJ decompression error
[ 1082.680991] PPP: VJ decompression error
[ 1082.808230] PPP: VJ decompression error
[ 1082.932482] PPP: VJ decompression error
[ 1083.063719] PPP: VJ decompression error
[ 1083.187467] PPP: VJ decompression error
[ 1083.315209] PPP: VJ decompression error
[ 1083.442951] PPP: VJ decompression error
[ 1083.570694] PPP: VJ decompression error
[ 1083.698438] PPP: VJ decompression error
[ 1083.826704] PPP: VJ decompression error
[ 1083.950432] PPP: VJ decompression error
[ 1084.078222] PPP: VJ decompression error
[ 1084.205417] PPP: VJ decompression error
[ 1097.434789] Inbound IN=ppp0 OUT= MAC= SRC=80.128.101.112 DST=144.134.109.26 LEN=60 TOS=0x00 PREC=0x00 TTL=50 ID=3711 DF PROTO=TCP SPT=3027 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[ 1131.459894] PPP: VJ decompression error
[ 1131.586464] PPP: VJ decompression error
[ 1131.713707] PPP: VJ decompression error
[ 1131.841465] PPP: VJ decompression error
[ 1132.228669] PPP: VJ decompression error
[ 1132.356910] PPP: VJ decompression error
[ 1132.480737] PPP: VJ decompression error
[ 1132.608399] PPP: VJ decompression error
[ 1132.863890] PPP: VJ decompression error
[ 1132.979771] PPP: VJ decompression error
[ 1133.234639] PPP: VJ decompression error
[ 1133.362380] PPP: VJ decompression error
[ 1173.074401] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.200 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60337 DPT=1026 LEN=600 
[ 1173.134258] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.200 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60337 DPT=1027 LEN=600 
[ 1173.973090] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=51351 DPT=1026 LEN=600 
[ 1195.397400] PPP: VJ decompression error
[ 1195.796595] PPP: VJ decompression error
[ 1195.924335] PPP: VJ decompression error
[ 1218.558767] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=56656 DPT=1027 LEN=601 
[ 1218.982404] Inbound IN=ppp0 OUT= MAC= SRC=24.86.138.43 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=19311 DF PROTO=TCP SPT=14521 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 1224.128026] PPP: VJ decompression error
[ 1224.511282] PPP: VJ decompression error
[ 1224.890790] PPP: VJ decompression error
[ 1225.145767] PPP: VJ decompression error
[ 1225.401460] PPP: VJ decompression error
[ 1225.525273] PPP: VJ decompression error
[ 1225.784204] PPP: VJ decompression error
[ 1226.039667] PPP: VJ decompression error
[ 1237.991587] PPP: VJ decompression error
[ 1238.802170] PPP: VJ decompression error
[ 1238.930197] PPP: VJ decompression error
[ 1239.054190] PPP: VJ decompression error
[ 1258.095620] PPP: VJ decompression error
[ 1258.342606] PPP: VJ decompression error
[ 1258.470349] PPP: VJ decompression error
[ 1258.598080] PPP: VJ decompression error
[ 1280.270410] PPP: VJ decompression error
[ 1280.278881] PPP: VJ decompression error
[ 1299.391900] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=57330 DPT=1027 LEN=601 
[ 1309.675184] PPP: VJ decompression error
[ 1310.537486] PPP: VJ decompression error
[ 1310.665946] PPP: VJ decompression error
[ 1345.443118] PPP: VJ decompression error
[ 1345.570847] PPP: VJ decompression error
[ 1345.698602] PPP: VJ decompression error
[ 1345.826333] PPP: VJ decompression error
[ 1345.954074] PPP: VJ decompression error
[ 1548.665699] Inbound IN=ppp0 OUT= MAC= SRC=24.86.138.43 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=36023 DF PROTO=TCP SPT=32349 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 1678.615892] Inbound IN=ppp0 OUT= MAC= SRC=62.5.142.185 DST=144.134.109.26 LEN=60 TOS=0x00 PREC=0x00 TTL=30 ID=63938 DF PROTO=TCP SPT=4033 DPT=23 WINDOW=5840 RES=0x00 SYN URGP=0 
[ 1758.315293] PPP: VJ decompression error
[ 1829.064785] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=39025 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 1848.238143] PPP: VJ decompression error
[ 1848.278063] PPP: VJ decompression error
[ 1856.537423] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=39026 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 1873.807116] PPP: VJ decompression error
[ 1873.934362] PPP: VJ decompression error
[ 1874.189858] PPP: VJ decompression error
[ 1874.317599] PPP: VJ decompression error
[ 1874.573075] PPP: VJ decompression error
[ 1874.700816] PPP: VJ decompression error
[ 1874.824565] PPP: VJ decompression error
[ 1874.952309] PPP: VJ decompression error
[ 1889.272516] PPP: VJ decompression error
[ 1889.399705] PPP: VJ decompression error
[ 1913.570519] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=39027 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 1917.375746] PPP: VJ decompression error
[ 1948.919810] Inbound IN=ppp0 OUT= MAC= SRC=75.127.194.242 DST=144.134.109.26 LEN=61 TOS=0x00 PREC=0x00 TTL=110 ID=29394 PROTO=ICMP TYPE=8 CODE=0 ID=58284 SEQ=26455 
[ 1951.973644] Inbound IN=ppp0 OUT= MAC= SRC=75.127.194.242 DST=144.134.109.26 LEN=61 TOS=0x00 PREC=0x00 TTL=110 ID=29869 PROTO=ICMP TYPE=8 CODE=0 ID=58284 SEQ=34904 
[ 1954.416227] PPP: VJ decompression error
[ 1954.675694] PPP: VJ decompression error
[ 1954.803437] PPP: VJ decompression error
[ 1954.927784] PPP: VJ decompression error
[ 1955.054927] PPP: VJ decompression error
[ 1963.547107] PPP: VJ decompression error
[ 1963.749409] PPP: VJ decompression error
[ 1963.937533] PPP: VJ decompression error
[ 1969.785269] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=39028 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2029.664631] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=39029 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2055.600383] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.201 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=56722 DPT=1027 LEN=600 
[ 2089.543994] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=37881 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2149.423864] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=37882 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2162.508995] Inbound IN=ppp0 OUT= MAC= SRC=219.111.220.32 DST=144.134.109.26 LEN=61 TOS=0x00 PREC=0x00 TTL=108 ID=34420 PROTO=ICMP TYPE=8 CODE=0 ID=256 SEQ=20880 
[ 2164.668624] Inbound IN=ppp0 OUT= MAC= SRC=219.111.220.32 DST=144.134.109.26 LEN=61 TOS=0x00 PREC=0x00 TTL=108 ID=34651 PROTO=ICMP TYPE=8 CODE=0 ID=256 SEQ=10897 
[ 2209.282760] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=37883 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2248.296642] PPP: VJ decompression error
[ 2248.423882] PPP: VJ decompression error
[ 2265.697968] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.234 DST=144.134.109.26 LEN=598 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=35308 DPT=1026 LEN=578 
[ 2269.182080] Inbound IN=ppp0 OUT= MAC= SRC=144.135.19.149 DST=144.134.109.26 LEN=576 TOS=0x00 PREC=0x00 TTL=54 ID=37884 DF PROTO=TCP SPT=81 DPT=4753 WINDOW=33232 RES=0x00 ACK PSH URGP=0 
[ 2275.193973] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=35749 DPT=1026 LEN=601 
[ 2278.072181] Inbound IN=ppp0 OUT= MAC= SRC=144.134.41.141 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=46514 DF PROTO=TCP SPT=53950 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 2285.157878] PPP: VJ decompression error
[ 2285.286117] PPP: VJ decompression error
[ 2285.413361] PPP: VJ decompression error
[ 2285.541104] PPP: VJ decompression error
[ 2285.665717] PPP: VJ decompression error
[ 2285.796641] PPP: VJ decompression error
[ 2288.004143] PPP: VJ decompression error
[ 2288.131882] PPP: VJ decompression error
[ 2288.259625] PPP: VJ decompression error
[ 2288.387369] PPP: VJ decompression error
[ 2288.515112] PPP: VJ decompression error
[ 2288.642854] PPP: VJ decompression error
[ 2288.770595] PPP: VJ decompression error
[ 2288.894348] PPP: VJ decompression error
[ 2289.022089] PPP: VJ decompression error
[ 2289.151329] PPP: VJ decompression error
[ 2289.405339] PPP: VJ decompression error
[ 2289.533620] PPP: VJ decompression error
[ 2289.784554] PPP: VJ decompression error
[ 2289.912296] PPP: VJ decompression error
[ 2290.040039] PPP: VJ decompression error
[ 2290.168279] PPP: VJ decompression error
[ 2295.576886] PPP: VJ decompression error
[ 2295.628772] PPP: VJ decompression error
[ 2299.948080] PPP: VJ decompression error
[ 2300.072352] PPP: VJ decompression error
[ 2300.200069] PPP: VJ decompression error
[ 2300.327812] PPP: VJ decompression error
[ 2300.455553] PPP: VJ decompression error
[ 2300.583299] PPP: VJ decompression error
[ 2300.707195] PPP: VJ decompression error
[ 2300.834792] PPP: VJ decompression error
[ 2300.962237] PPP: VJ decompression error
[ 2301.089778] PPP: VJ decompression error
[ 2301.218025] PPP: VJ decompression error
[ 2301.473106] PPP: VJ decompression error
[ 2301.724501] PPP: VJ decompression error
[ 2301.852245] PPP: VJ decompression error
[ 2301.980485] PPP: VJ decompression error
[ 2302.107728] PPP: VJ decompression error
[ 2302.235469] PPP: VJ decompression error
[ 2302.363211] PPP: VJ decompression error
[ 2302.491211] PPP: VJ decompression error
[ 2418.609031] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=36705 DPT=1027 LEN=601 
[ 2506.456559] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60372 DPT=1027 LEN=600 
[ 2506.568315] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60372 DPT=1026 LEN=600 
[ 2506.675593] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60372 DPT=1027 LEN=600 
[ 2539.697085] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=17992 DF PROTO=TCP SPT=4580 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2542.343752] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=18080 DF PROTO=TCP SPT=4580 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2543.613186] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=18126 DF PROTO=TCP SPT=4588 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2547.469920] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=18233 DF PROTO=TCP SPT=4588 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 2549.042865] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=18343 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 2551.449399] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=18406 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 2555.042161] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=18450 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 2767.589951] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=37950 DF PROTO=TCP SPT=14249 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 2845.374447] Inbound IN=ppp0 OUT= MAC= SRC=24.86.138.43 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=32955 DF PROTO=TCP SPT=36034 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 2917.428051] PPP: VJ decompression error
[ 2917.555791] PPP: VJ decompression error
[ 2917.683534] PPP: VJ decompression error
[ 2917.811275] PPP: VJ decompression error
[ 2917.943010] PPP: VJ decompression error
[ 2918.070752] PPP: VJ decompression error
[ 2918.198495] PPP: VJ decompression error
[ 2918.326241] PPP: VJ decompression error
[ 2918.453981] PPP: VJ decompression error
[ 2918.577731] PPP: VJ decompression error
[ 2918.705474] PPP: VJ decompression error
[ 2918.833717] PPP: VJ decompression error
[ 2918.960961] PPP: VJ decompression error
[ 2919.088701] PPP: VJ decompression error
[ 2919.216449] PPP: VJ decompression error
[ 2919.228915] PPP: VJ decompression error
[ 2919.232902] PPP: VJ decompression error
[ 2922.569755] PPP: VJ decompression error
[ 2922.693458] PPP: VJ decompression error
[ 2922.948928] PPP: VJ decompression error
[ 2963.475281] PPP: VJ decompression error
[ 2963.603518] PPP: VJ decompression error
[ 2963.731258] PPP: VJ decompression error
[ 2963.859001] PPP: VJ decompression error
[ 2973.267568] Inbound IN=ppp0 OUT= MAC= SRC=24.86.138.43 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=39072 DF PROTO=TCP SPT=42829 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 3008.348872] PPP: VJ decompression error
[ 3008.476614] PPP: VJ decompression error
[ 3008.604854] PPP: VJ decompression error
[ 3008.728104] PPP: VJ decompression error
[ 3008.855849] PPP: VJ decompression error
[ 3008.983594] PPP: VJ decompression error
[ 3009.111336] PPP: VJ decompression error
[ 3057.485893] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=40978 DPT=1026 LEN=601 
[ 3098.555147] PPP: VJ decompression error
[ 3098.810622] PPP: VJ decompression error
[ 3098.938362] PPP: VJ decompression error
[ 3099.066127] PPP: VJ decompression error
[ 3099.189853] PPP: VJ decompression error
[ 3120.052350] Inbound IN=ppp0 OUT= MAC= SRC=91.189.94.12 DST=144.134.109.26 LEN=1500 TOS=0x00 PREC=0x00 TTL=38 ID=23141 DF PROTO=TCP SPT=80 DPT=43853 WINDOW=8307 RES=0x00 ACK URGP=0 
[ 3158.031683] PPP: VJ decompression error
[ 3158.159050] PPP: VJ decompression error
[ 3159.448466] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=41631 DPT=1026 LEN=601 
[ 3218.142205] PPP: VJ decompression error
[ 3218.261958] PPP: VJ decompression error
[ 3223.080755] PPP: VJ decompression error
[ 3223.200011] PPP: VJ decompression error
[ 3236.137951] PPP: VJ decompression error
[ 3236.257705] PPP: VJ decompression error
[ 3236.377965] PPP: VJ decompression error
[ 3236.497221] PPP: VJ decompression error
[ 3236.616980] PPP: VJ decompression error
[ 3236.736741] PPP: VJ decompression error
[ 3348.822948] Inbound IN=ppp0 OUT= MAC= SRC=144.134.81.31 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=55 ID=8755 DF PROTO=TCP SPT=58744 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 3419.616795] PPP: VJ decompression error
[ 3442.210783] PPP: VJ decompression error
[ 3442.342518] PPP: VJ decompression error
[ 3442.466263] PPP: VJ decompression error
[ 3442.594004] PPP: VJ decompression error
[ 3442.722248] PPP: VJ decompression error
[ 3442.849494] PPP: VJ decompression error
[ 3442.977233] PPP: VJ decompression error
[ 3443.100988] PPP: VJ decompression error
[ 3443.228726] PPP: VJ decompression error
[ 3443.356469] PPP: VJ decompression error
[ 3443.484210] PPP: VJ decompression error
[ 3443.611954] PPP: VJ decompression error
[ 3443.740207] PPP: VJ decompression error
[ 3443.867441] PPP: VJ decompression error
[ 3444.119496] PPP: VJ decompression error
[ 3444.246929] PPP: VJ decompression error
[ 3444.354993] PPP: VJ decompression error
[ 3493.080293] PPP: VJ decompression error
[ 3493.204050] PPP: VJ decompression error
[ 3493.331784] PPP: VJ decompression error
[ 3493.459527] PPP: VJ decompression error
[ 3493.591262] PPP: VJ decompression error
[ 3493.719009] PPP: VJ decompression error
[ 3493.846746] PPP: VJ decompression error
[ 3493.978490] PPP: VJ decompression error
[ 3494.102734] PPP: VJ decompression error
[ 3494.227276] PPP: VJ decompression error
[ 3494.358247] PPP: VJ decompression error
[ 3494.481969] PPP: VJ decompression error
[ 3494.609711] PPP: VJ decompression error
[ 3494.736951] PPP: VJ decompression error
[ 3494.784849] PPP: VJ decompression error
[ 3544.604483] PPP: VJ decompression error
[ 3557.938123] PPP: VJ decompression error
[ 3558.065367] PPP: VJ decompression error
[ 3558.193108] PPP: VJ decompression error
[ 3558.320851] PPP: VJ decompression error
[ 3578.492714] PPP: VJ decompression error
[ 3578.620456] PPP: VJ decompression error
[ 3578.747703] PPP: VJ decompression error
[ 3578.871447] PPP: VJ decompression error
[ 3642.783116] PPP: VJ decompression error
[ 3672.575222] PPP: VJ decompression error
[ 3672.874065] PPP: VJ decompression error
[ 3673.001806] PPP: VJ decompression error
[ 3673.125556] PPP: VJ decompression error
[ 3673.253296] PPP: VJ decompression error
[ 3675.600758] PPP: VJ decompression error
[ 3675.728311] PPP: VJ decompression error
[ 3848.895458] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=41339 DPT=1026 LEN=600 
[ 3930.630786] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=52039 DPT=1026 LEN=601 
[ 3930.694638] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=52039 DPT=1027 LEN=601 
[ 4002.222537] PPP: VJ decompression error
[ 4009.092688] PPP: VJ decompression error
[ 4033.172271] PPP: VJ decompression error
[ 4033.299921] PPP: VJ decompression error
[ 4084.389001] PPP: VJ decompression error
[ 4084.516751] PPP: VJ decompression error
[ 4084.704356] PPP: VJ decompression error
[ 4084.828102] PPP: VJ decompression error
[ 4091.714256] Inbound IN=ppp0 OUT= MAC= SRC=144.134.81.31 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=55 ID=46721 DF PROTO=TCP SPT=28805 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 4099.734614] PPP: VJ decompression error
[ 4100.660232] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.200 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=52941 DPT=1026 LEN=600 
[ 4142.631724] PPP: VJ decompression error
[ 4145.761840] PPP: VJ decompression error
[ 4281.767869] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=49159 DPT=1026 LEN=601 
[ 4291.982749] PPP: VJ decompression error
[ 4300.836940] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=54611 DPT=1027 LEN=601 
[ 4300.952698] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=54611 DPT=1026 LEN=601 
[ 4301.056489] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=54611 DPT=1026 LEN=601 
[ 4336.253574] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=33048 DF PROTO=TCP SPT=1069 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 4338.900247] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=33082 DF PROTO=TCP SPT=1069 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 4340.109802] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=33102 DF PROTO=TCP SPT=1070 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 4349.846190] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=33200 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 4351.910026] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=33221 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 4356.141502] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=33252 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 4412.256443] PPP: VJ decompression error
[ 4412.380693] PPP: VJ decompression error
[ 4412.507939] PPP: VJ decompression error
[ 4412.635676] PPP: VJ decompression error
[ 4412.763421] PPP: VJ decompression error
[ 4412.891164] PPP: VJ decompression error
[ 4413.018906] PPP: VJ decompression error
[ 4413.146652] PPP: VJ decompression error
[ 4413.274889] PPP: VJ decompression error
[ 4915.164479] Inbound IN=ppp0 OUT= MAC= SRC=144.134.53.201 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=46647 DF PROTO=TCP SPT=20992 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 4921.282931] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=53451 DPT=1026 LEN=601 
[ 5025.421101] PPP: VJ decompression error
[ 5025.561323] PPP: VJ decompression error
[ 5025.768404] PPP: VJ decompression error
[ 5025.892154] PPP: VJ decompression error
[ 5056.957576] Inbound IN=ppp0 OUT= MAC= SRC=144.134.41.141 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=39937 DF PROTO=TCP SPT=40486 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 5212.875471] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=50766 DPT=1026 LEN=600 
[ 5212.987221] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=50766 DPT=1027 LEN=600 
[ 5213.055081] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=50766 DPT=1027 LEN=600 
[ 5228.779413] PPP: VJ decompression error
[ 5229.034891] PPP: VJ decompression error
[ 5229.058831] PPP: VJ decompression error
[ 5240.635518] PPP: VJ decompression error
[ 5240.763257] PPP: VJ decompression error
[ 5240.891000] PPP: VJ decompression error
[ 5241.018742] PPP: VJ decompression error
[ 5241.142492] PPP: VJ decompression error
[ 5241.270237] PPP: VJ decompression error
[ 5241.397980] PPP: VJ decompression error
[ 5241.526242] PPP: VJ decompression error
[ 5241.653464] PPP: VJ decompression error
[ 5241.781208] PPP: VJ decompression error
[ 5241.908949] PPP: VJ decompression error
[ 5242.032702] PPP: VJ decompression error
[ 5542.960086] PPP: VJ decompression error
[ 5543.090665] PPP: VJ decompression error
[ 5543.214472] PPP: VJ decompression error
[ 5543.341668] PPP: VJ decompression error
[ 5543.597645] PPP: VJ decompression error
[ 5543.980874] PPP: VJ decompression error
[ 5544.232299] PPP: VJ decompression error
[ 5544.359609] PPP: VJ decompression error
[ 5544.487847] PPP: VJ decompression error
[ 5544.615928] PPP: VJ decompression error
[ 5544.743352] PPP: VJ decompression error
[ 5544.870628] PPP: VJ decompression error
[ 5545.122072] PPP: VJ decompression error
[ 5545.250313] PPP: VJ decompression error
[ 5545.377555] PPP: VJ decompression error
[ 5545.507278] PPP: VJ decompression error
[ 5545.633123] PPP: VJ decompression error
[ 5545.757293] PPP: VJ decompression error
[ 5545.888528] PPP: VJ decompression error
[ 5597.784486] PPP: VJ decompression error
[ 5610.491385] PPP: VJ decompression error
[ 5610.618168] PPP: VJ decompression error
[ 5610.873666] PPP: VJ decompression error
[ 5611.001365] PPP: VJ decompression error
[ 5611.253343] PPP: VJ decompression error
[ 5611.381108] PPP: VJ decompression error
[ 5611.508826] PPP: VJ decompression error
[ 5611.761016] PPP: VJ decompression error
[ 5612.144692] PPP: VJ decompression error
[ 5612.270790] PPP: VJ decompression error
[ 5612.654017] PPP: VJ decompression error
[ 5612.781759] PPP: VJ decompression error
[ 5612.909802] PPP: VJ decompression error
[ 5613.033251] PPP: VJ decompression error
[ 5613.160993] PPP: VJ decompression error
[ 5613.288738] PPP: VJ decompression error
[ 5613.416478] PPP: VJ decompression error
[ 5613.544220] PPP: VJ decompression error
[ 5629.037031] PPP: VJ decompression error
[ 5629.160760] PPP: VJ decompression error
[ 5629.289067] PPP: VJ decompression error
[ 5629.422439] PPP: VJ decompression error
[ 5629.672231] PPP: VJ decompression error
[ 5629.800162] PPP: VJ decompression error
[ 5629.927217] PPP: VJ decompression error
[ 5630.054962] PPP: VJ decompression error
[ 5630.183203] PPP: VJ decompression error
[ 5640.618201] Inbound IN=ppp0 OUT= MAC= SRC=144.134.53.201 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=19823 DF PROTO=TCP SPT=56965 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 5712.029831] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=58742 DF PROTO=TCP SPT=22886 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 5759.593981] PPP: VJ decompression error
[ 5759.893376] PPP: VJ decompression error
[ 5759.893379] PPP: VJ decompression error
[ 6070.990636] Inbound IN=ppp0 OUT= MAC= SRC=144.134.53.201 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=42916 DF PROTO=TCP SPT=13897 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6121.612647] Inbound IN=ppp0 OUT= MAC= SRC=144.134.177.143 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=55 ID=58892 DF PROTO=TCP SPT=53530 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6132.977750] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=46002 DF PROTO=TCP SPT=1461 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6135.317034] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=46020 DF PROTO=TCP SPT=1461 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6136.430786] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=46027 DF PROTO=TCP SPT=1463 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6139.432739] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=46046 DF PROTO=TCP SPT=1463 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 6151.600213] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=46173 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 6153.596203] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=46195 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 6157.628081] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=46226 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 6176.557945] Inbound IN=ppp0 OUT= MAC= SRC=144.134.53.201 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=48544 DF PROTO=TCP SPT=19237 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6187.388131] Inbound IN=ppp0 OUT= MAC= SRC=144.134.35.84 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=13962 DF PROTO=TCP SPT=12139 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6245.299460] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=34060 DPT=1027 LEN=601 
[ 6446.658281] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=31428 DF PROTO=TCP SPT=57180 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6518.041962] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=35147 DF PROTO=TCP SPT=60518 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6596.284332] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60233 DPT=1026 LEN=600 
[ 6596.352176] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60233 DPT=1027 LEN=600 
[ 6596.408059] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.195 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=60233 DPT=1026 LEN=600 
[ 6696.733936] PPP: VJ decompression error
[ 6696.861680] PPP: VJ decompression error
[ 6696.989421] PPP: VJ decompression error
[ 6697.118345] PPP: VJ decompression error
[ 6697.245914] PPP: VJ decompression error
[ 6697.372652] PPP: VJ decompression error
[ 6697.496900] PPP: VJ decompression error
[ 6697.624642] PPP: VJ decompression error
[ 6697.752421] PPP: VJ decompression error
[ 6697.851680] PPP: VJ decompression error
[ 6780.046604] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=37728 DPT=1026 LEN=601 
[ 6816.125418] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=50636 DF PROTO=TCP SPT=9985 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 6834.863648] PPP: VJ decompression error
[ 6835.003363] PPP: VJ decompression error
[ 6835.131109] PPP: VJ decompression error
[ 6979.309653] Inbound IN=ppp0 OUT= MAC= SRC=144.138.215.145 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=59008 DF PROTO=TCP SPT=17588 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 7061.247580] Inbound IN=ppp0 OUT= MAC= SRC=144.134.41.141 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=62413 DF PROTO=TCP SPT=57913 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 7085.850378] Inbound IN=ppp0 OUT= MAC= SRC=202.97.238.200 DST=144.134.109.26 LEN=620 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=45870 DPT=1027 LEN=600 
[ 7143.968997] PPP: VJ decompression error
[ 7144.093208] PPP: VJ decompression error
[ 7144.220485] PPP: VJ decompression error
[ 7144.348195] PPP: VJ decompression error
[ 7144.603625] PPP: VJ decompression error
[ 7144.731362] PPP: VJ decompression error
[ 7201.077844] PPP: VJ decompression error
[ 7306.920622] Inbound IN=ppp0 OUT= MAC= SRC=222.183.228.31 DST=144.134.109.26 LEN=404 TOS=0x00 PREC=0x00 TTL=105 ID=25896 PROTO=UDP SPT=2224 DPT=1434 LEN=384 
[ 7488.267246] PPP: VJ decompression error
[ 7488.394985] PPP: VJ decompression error
[ 7488.522728] PPP: VJ decompression error
[ 7488.650471] PPP: VJ decompression error
[ 7488.778214] PPP: VJ decompression error
[ 7488.902061] PPP: VJ decompression error
[ 7489.029712] PPP: VJ decompression error
[ 7489.157949] PPP: VJ decompression error
[ 7489.285693] PPP: VJ decompression error
[ 7489.412953] PPP: VJ decompression error
[ 7489.664440] PPP: VJ decompression error
[ 7489.919919] PPP: VJ decompression error
[ 7490.175473] PPP: VJ decompression error
[ 7490.303705] PPP: VJ decompression error
[ 7490.430895] PPP: VJ decompression error
[ 7490.682399] PPP: VJ decompression error
[ 7490.810124] PPP: VJ decompression error
[ 7490.937866] PPP: VJ decompression error
[ 7491.065606] PPP: VJ decompression error
[ 7491.190341] PPP: VJ decompression error
[ 7550.622147] Inbound IN=ppp0 OUT= MAC= SRC=144.134.41.141 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=16461 DF PROTO=TCP SPT=11490 DPT=135 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 7554.170869] PPP: VJ decompression error
[ 7630.233234] PPP: VJ decompression error
[ 7630.492709] PPP: VJ decompression error
[ 7630.757486] PPP: VJ decompression error
[ 7667.118913] PPP: VJ decompression error
[ 7667.494151] PPP: VJ decompression error
[ 7667.522094] PPP: VJ decompression error
[ 7667.921300] PPP: VJ decompression error
[ 7668.097438] PPP: VJ decompression error
[ 7705.393833] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=43899 DPT=1026 LEN=601 
[ 7710.299914] PPP: VJ decompression error
[ 7727.278594] PPP: VJ decompression error
[ 7732.978253] Inbound IN=ppp0 OUT= MAC= SRC=144.134.35.84 DST=144.134.109.26 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=33966 DF PROTO=TCP SPT=24271 DPT=139 WINDOW=60352 RES=0x00 SYN URGP=0 
[ 7737.518344] PPP: VJ decompression error
[ 7738.986627] PPP: VJ decompression error
[ 7739.246104] PPP: VJ decompression error
[ 7739.357372] PPP: VJ decompression error
[ 7748.239983] PPP: VJ decompression error
[ 7748.367227] PPP: VJ decompression error
[ 7754.455460] PPP: VJ decompression error
[ 7754.579212] PPP: VJ decompression error
[ 7770.686818] PPP: VJ decompression error
[ 7770.937753] PPP: VJ decompression error
[ 7771.061501] PPP: VJ decompression error
[ 7929.386555] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=59412 DF PROTO=TCP SPT=2017 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7932.156958] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=59429 DF PROTO=TCP SPT=2017 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7932.907435] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=59436 DF PROTO=TCP SPT=2018 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7935.893945] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=59456 DF PROTO=TCP SPT=2018 DPT=39515 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 7948.232561] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=59560 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 7949.837338] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=59589 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 7953.821314] Inbound IN=ppp0 OUT= MAC= SRC=144.134.109.21 DST=144.134.109.26 LEN=122 TOS=0x00 PREC=0x00 TTL=127 ID=59616 PROTO=UDP SPT=32088 DPT=39515 LEN=102 
[ 7967.849063] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.166 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=52876 DPT=1027 LEN=601 
[ 7992.411555] PPP: VJ decompression error
[ 7992.547277] PPP: VJ decompression error
[ 8013.880313] PPP: VJ decompression error
[ 8014.367726] PPP: VJ decompression error
[ 8014.507536] PPP: VJ decompression error
[ 8014.682681] PPP: VJ decompression error
[ 8014.810423] PPP: VJ decompression error
[ 8080.941209] PPP: VJ decompression error
[ 8110.832977] PPP: VJ decompression error
[ 8110.956721] PPP: VJ decompression error
[ 8111.084463] PPP: VJ decompression error
[ 8111.212206] PPP: VJ decompression error
[ 8139.280185] PPP: VJ decompression error
[ 8139.539639] PPP: VJ decompression error
[ 8139.666879] PPP: VJ decompression error
[ 8139.794622] PPP: VJ decompression error
[ 8154.677236] Inbound IN=ppp0 OUT= MAC= SRC=60.15.177.163 DST=144.134.109.26 LEN=621 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=UDP SPT=46852 DPT=1027 LEN=601 
[ 8168.201392] PPP: VJ decompression error
[ 8172.412900] PPP: VJ decompression error
[ 8173.339043] PPP: VJ decompression error
[ 8173.431352] PPP: VJ decompression error
```

thanks, TopEnder

---

### Post by caljohnsmith on 2008-11-17
Are you running PPPoE or similar on your computer to connect to the internet? I think that's what those PPP errors might be about. What happened before you started having the booting problem? I assume you don't have a fresh install, is that true? Also, can you still log into Ubuntu OK, or don't you get that far?

---

### Post by TopEnder on 2008-11-17
Hi, Not sure what it is called, I am using a dialup external modem (Hayes Accura)to connect to the internet it is configured by using pppconfig. I also have a Winmodem installed on the PC for those times I need to use Windows. There is also a Network Icom in the top bar, I not sure if this has any connection to my  "PPP: VJ decompression error" I have tried to configure the modem using the networtool but run into trouble and reverted back to the pppconfig.  I can login to Ubuntu 8,04 and access all programs and the Internet Bootup appears normal except it drops from the Progress Bar to script/text the all appears normal except some time loading Ubuntu pages is very slow.  So far I have not had to do a fresh installation since installing 8.04 in April 2008. Thanks, TopEnder

---


---
title: "How to mount usb device when it is not detected"
date: 2008-08-13
forum: Hardware
---

### Post by evillan on 2008-08-13
Hi

I have a mp3 player with a flash drive. The file system is FAT32.
When I insert in the usb port, the device is not detected automatically.

I tried the guide: [https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting](https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting)

```

xx:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

```

According to the guide, the usb device should be called something like /dev/sdb1. I also tried the same command without the usb drive plugged in, it outputs exactly the same.

What should I do?

---

### Post by phidia on 2008-08-13
After you plug in the drive/mp3player open a terminal and enter > dmesg you can also enter the fdisk command you posted but dmesg should show the drive too.

Post the output of that. There is also an Ubuntu wiki guide on audio devices [here]("https://help.ubuntu.com/community/PortableDevices"). If that's a lot to digest though don't worry just post back here.

---

### Post by evillan on 2008-08-14
The output of dmesg:

```
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7640
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7500 checksum 0
[    0.000000] ACPI: RSDP 000F7500, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3F691BD8, 0044 (r1 FSC    PC       20070214  LTP        0)
[    0.000000] ACPI: FACP 3F697CAA, 0074 (r1 FUJ___ DW1_____ 20070214 LOHR       5A)
[    0.000000] ACPI: DSDT 3F692626, 5684 (r1 FUJ___ DW1_____ 20070214 MSFT  100000E)
[    0.000000] ACPI: FACS 3F698FC0, 0040
[    0.000000] ACPI: APIC 3F697D1E, 0068 (r1 FUJ___ DW1_____ 20070214 LOHR       5A)
[    0.000000] ACPI: HPET 3F697D86, 0038 (r1 FUJ___ DW1_____ 20070214 LOHR       5A)
[    0.000000] ACPI: MCFG 3F697DBE, 003C (r1 FUJ___ DW1_____ 20070214 LOHR       5A)
[    0.000000] ACPI: APIC 3F697DFA, 0068 (r1 FUJ___ DW1_____ 20070214  LTP        0)
[    0.000000] ACPI: BOOT 3F697E62, 0028 (r1 FUJ___ DW1_____ 20070214  LTP        1)
[    0.000000] ACPI: SLIC 3F697E8A, 0176 (r1 FSC    PC       20070214  LTP        0)
[    0.000000] ACPI: SSDT 3F691C1C, 0500 (r1  PmRef    CpuPm     3000 INTL 20050228)
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
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257699
[    0.000000] Kernel command line: root=UUID=5d120492-5029-4832-a084-7bd339310896 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.664 MHz processor.
[   20.532225] Console: colour VGA+ 80x25
[   20.532229] console [tty0] enabled
[   20.532534] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.532897] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.559069] Memory: 1017656k/1038912k available (2177k kernel code, 20568k reserved, 1006k data, 368k init, 121408k highmem)
[   20.559076] virtual kernel memory layout:
[   20.559077]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.559079]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.559080]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.559081]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.559082]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.559083]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   20.559084]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   20.559088] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.559122] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.559258] hpet clockevent registered
[   20.639150] Calibrating delay using timer specific routine.. 3729.42 BogoMIPS (lpj=7458847)
[   20.639169] Security Framework initialized
[   20.639175] SELinux:  Disabled at boot.
[   20.639189] AppArmor: AppArmor initialized
[   20.639193] Failure registering capabilities with primary security module.
[   20.639201] Mount-cache hash table entries: 512
[   20.639311] Initializing cgroup subsys ns
[   20.639315] Initializing cgroup subsys cpuacct
[   20.639325] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   20.639332] monitor/mwait feature present.
[   20.639333] using mwait in idle threads.
[   20.639338] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.639340] CPU: L2 cache: 2048K
[   20.639342] CPU: Physical Processor ID: 0
[   20.639344] CPU: Processor Core ID: 0
[   20.639346] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   20.639355] Compat vDSO mapped to ffffe000.
[   20.639366] Checking 'hlt' instruction... OK.
[   20.655510] SMP alternatives: switching to UP code
[   20.657225] Early unpacking initramfs... done
[   20.990432] ACPI: Core revision 20070126
[   20.990489] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.010659] CPU0: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   21.010676] SMP alternatives: switching to SMP code
[   21.011353] Booting processor 1/1 eip 3000
[   21.021601] Initializing CPU#1
[   21.098487] Calibrating delay using timer specific routine.. 3725.15 BogoMIPS (lpj=7450305)
[   21.098495] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
[   21.098500] monitor/mwait feature present.
[   21.098503] CPU: L1 I cache: 32K, L1 D cache: 32K
[   21.098505] CPU: L2 cache: 2048K
[   21.098507] CPU: Physical Processor ID: 0
[   21.098508] CPU: Processor Core ID: 1
[   21.098510] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
[   21.099116] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   21.099139] Total of 2 processors activated (7454.57 BogoMIPS).
[   21.099336] ENABLING IO-APIC IRQs
[   21.099530] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.246398] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   21.266390] Brought up 2 CPUs
[   21.266415] CPU0 attaching sched-domain:
[   21.266418]  domain 0: span 03
[   21.266420]   groups: 01 02
[   21.266423] CPU1 attaching sched-domain:
[   21.266424]  domain 0: span 03
[   21.266426]   groups: 02 01
[   21.266677] net_namespace: 64 bytes
[   21.266685] Booting paravirtualized kernel on bare hardware
[   21.267455] Time:  4:54:26  Date: 08/14/08
[   21.267484] NET: Registered protocol family 16
[   21.267695] EISA bus registered
[   21.267699] ACPI: bus type pci registered
[   21.267915] PCI: PCI BIOS revision 2.10 entry at 0xfd88b, last bus=7
[   21.267917] PCI: Using configuration type 1
[   21.267931] Setting up standard PCI resources
[   21.271870] ACPI: EC: Look up EC in DSDT
[   21.273435] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   21.273687] ACPI: Interpreter enabled
[   21.273690] ACPI: (supports S0 S3 S4 S5)
[   21.273704] ACPI: Using IOAPIC for interrupt routing
[   21.273972] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   21.279018] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   21.279020] ACPI: EC: driver started in interrupt mode
[   21.279059] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.279876] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   21.279881] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   21.281210] PCI: Transparent bridge - 0000:00:1e.0
[   21.281253] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.281559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   21.281676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   21.281791] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   21.281916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   21.289030] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.289123] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[   21.289213] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   21.289303] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.289392] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   21.289482] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   21.289572] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   21.289661] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[   21.289795] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.289827] pnp: PnP ACPI init
[   21.289833] ACPI: bus type pnp registered
[   21.291594] pnp: PnP ACPI: found 9 devices
[   21.291597] ACPI: ACPI bus type pnp unregistered
[   21.291600] PnPBIOS: Disabled by ACPI PNP
[   21.291848] PCI: Using ACPI for IRQ routing
[   21.291851] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.350267] NET: Registered protocol family 8
[   21.350269] NET: Registered protocol family 20
[   21.350305] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   21.350309] hpet0: 3 64-bit timers, 14318180 Hz
[   21.351343] AppArmor: AppArmor Filesystem Enabled
[   21.354128] Time: tsc clocksource has been installed.
[   21.354145] Switched to high resolution mode on CPU 0
[   21.354258] Switched to high resolution mode on CPU 1
[   21.367109] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.367112] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   21.367115] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   21.367118] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   21.367121] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   21.367124] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   21.367127] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   21.367135] system 00:05: ioport range 0x800-0x80f has been reserved
[   21.367137] system 00:05: ioport range 0x1000-0x107f has been reserved
[   21.367140] system 00:05: ioport range 0x1180-0x11bf has been reserved
[   21.397543] PCI: Bridge: 0000:00:1c.0
[   21.397546]   IO window: 2000-2fff
[   21.397552]   MEM window: da000000-dbffffff
[   21.397557]   PREFETCH window: d4000000-d5ffffff
[   21.397563] PCI: Bridge: 0000:00:1c.1
[   21.397566]   IO window: 3000-3fff
[   21.397572]   MEM window: d6000000-d7ffffff
[   21.397576]   PREFETCH window: d0000000-d1ffffff
[   21.397582] PCI: Bridge: 0000:00:1c.2
[   21.397585]   IO window: 4000-4fff
[   21.397591]   MEM window: d8000000-d9ffffff
[   21.397595]   PREFETCH window: d2000000-d3ffffff
[   21.397602] PCI: Bridge: 0000:00:1e.0
[   21.397605]   IO window: 5000-5fff
[   21.397611]   MEM window: dc000000-dc0fffff
[   21.397615]   PREFETCH window: disabled.
[   21.397648] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   21.397655] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.397679] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   21.397685] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.397709] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.397715] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.397726] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   21.397732] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.397743] NET: Registered protocol family 2
[   21.435035] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.435247] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.435935] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.436286] TCP: Hash tables configured (established 131072 bind 65536)
[   21.436289] TCP reno registered
[   21.447113] checking if image is initramfs... it is
[   22.107910] Freeing initrd memory: 7460k freed
[   22.108101] Simple Boot Flag value 0x82 read from CMOS RAM was invalid
[   22.108104] Simple Boot Flag at 0x36 set to 0x1
[   22.108814] audit: initializing netlink socket (disabled)
[   22.108828] audit(1218689666.408:1): initialized
[   22.109029] highmem bounce pool size: 64 pages
[   22.111052] VFS: Disk quotas dquot_6.5.1
[   22.111127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.111265] io scheduler noop registered
[   22.111267] io scheduler anticipatory registered
[   22.111269] io scheduler deadline registered
[   22.111280] io scheduler cfq registered (default)
[   22.111293] Boot video device is 0000:00:02.0
[   22.111391] PCI: Firmware left 0000:07:08.0 e100 interrupts enabled, disabling
[   22.111518] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   22.111575] assign_interrupt_mode Found MSI capability
[   22.111624] Allocate Port Service[0000:00:1c.0:pcie00]
[   22.111663] Allocate Port Service[0000:00:1c.0:pcie02]
[   22.111763] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   22.111819] assign_interrupt_mode Found MSI capability
[   22.111865] Allocate Port Service[0000:00:1c.1:pcie00]
[   22.111901] Allocate Port Service[0000:00:1c.1:pcie02]
[   22.112002] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   22.112058] assign_interrupt_mode Found MSI capability
[   22.112103] Allocate Port Service[0000:00:1c.2:pcie00]
[   22.112141] Allocate Port Service[0000:00:1c.2:pcie02]
[   22.112411] isapnp: Scanning for PnP cards...
[   22.466287] isapnp: No Plug & Play device found
[   22.493464] Real Time Clock Driver v1.12ac
[   22.494008] hpet_resources: 0xfed00000 is busy
[   22.494039] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.495266] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.495333] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.495430] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2F] at 0x60,0x64 irq 1,12
[   22.498314] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.498319] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.516666] mice: PS/2 mouse device common for all mice
[   22.516783] EISA: Probing bus 0 at eisa.0
[   22.516792] Cannot allocate resource for EISA slot 1
[   22.516794] Cannot allocate resource for EISA slot 2
[   22.516796] Cannot allocate resource for EISA slot 3
[   22.516798] Cannot allocate resource for EISA slot 4
[   22.516801] Cannot allocate resource for EISA slot 5
[   22.516815] EISA: Detected 0 cards.
[   22.516818] cpuidle: using governor ladder
[   22.516820] cpuidle: using governor menu
[   22.516908] NET: Registered protocol family 1
[   22.516937] Using IPI No-Shortcut mode
[   22.516970] registered taskstats version 1
[   22.517089]   Magic number: 4:376:919
[   22.517184] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.517186] EDD information not available.
[   22.517395] Freeing unused kernel memory: 368k freed
[   22.545954] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.731369] fuse init (API version 7.9)
[   23.750666] ACPI: SSDT 3F692371, 022C (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   23.751080] ACPI: SSDT 3F69211C, 01D0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   23.751494] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.751498] ACPI: Processor [CPU0] (supports 8 throttling states)
[   23.751714] ACPI: SSDT 3F69259D, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[   23.751898] ACPI: SSDT 3F6922EC, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[   23.752378] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   23.752383] ACPI: Processor [CPU1] (supports 8 throttling states)
[   23.757437] ACPI: Thermal Zone [TZ00] (35 C)
[   24.119275] usbcore: registered new interface driver usbfs
[   24.119301] usbcore: registered new interface driver hub
[   24.131709] usbcore: registered new device driver usb
[   24.163461] SCSI subsystem initialized
[   24.177371] USB Universal Host Controller Interface driver v3.0
[   24.177433] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   24.177444] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.177449] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.177709] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.177744] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   24.177887] usb usb1: configuration #1 chosen from 1 choice
[   24.177911] hub 1-0:1.0: USB hub found
[   24.177916] hub 1-0:1.0: 2 ports detected
[   24.189392] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   24.189395] e100: Copyright(c) 1999-2006 Intel Corporation
[   24.232972] libata version 3.00 loaded.
[   24.278094] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   24.278107] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   24.278111] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   24.278135] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   24.278168] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   24.278278] usb usb2: configuration #1 chosen from 1 choice
[   24.278301] hub 2-0:1.0: USB hub found
[   24.278306] hub 2-0:1.0: 2 ports detected
[   24.381937] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.381948] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   24.381953] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   24.381977] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   24.382010] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   24.382117] usb usb3: configuration #1 chosen from 1 choice
[   24.382139] hub 3-0:1.0: USB hub found
[   24.382144] hub 3-0:1.0: 2 ports detected
[   24.485785] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   24.485796] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   24.485801] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   24.485823] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   24.485856] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   24.485964] usb usb4: configuration #1 chosen from 1 choice
[   24.485987] hub 4-0:1.0: USB hub found
[   24.485991] hub 4-0:1.0: 2 ports detected
[   24.590393] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   24.590457] PCI: Setting latency timer of device 0000:07:08.0 to 64
[   24.617554] e100: eth0: e100_probe: addr 0xdc000000, irq 21, MAC addr 00:1b:24:1f:68:b8
[   24.617585] PCI: Enabling device 0000:07:09.0 (0000 -> 0002)
[   24.617592] ACPI: PCI Interrupt 0000:07:09.0[A] -> GSI 20 (level, low) -> IRQ 21
[   24.617601] PCI: Setting latency timer of device 0000:07:09.0 to 64
[   24.670315] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[dc001000-dc0017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   24.674422] ahci 0000:00:1f.2: version 3.0
[   24.674453] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   24.674506] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x5) don't match, using nr_ports
[   24.674509] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   24.693388] Clocksource tsc unstable (delta = -96090611 ns)
[   24.697376] Time: hpet clocksource has been installed.
[   24.861136] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   24.861146] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   24.861156] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.861558] scsi0 : ahci
[   24.861794] scsi1 : ahci
[   24.861934] scsi2 : ahci
[   24.862074] scsi3 : ahci
[   24.862159] ata1: SATA max UDMA/133 abar m1024@0xdc444400 port 0xdc444500 irq 220
[   24.862163] ata2: SATA max UDMA/133 abar m1024@0xdc444400 port 0xdc444580 irq 220
[   24.862166] ata3: SATA max UDMA/133 abar m1024@0xdc444400 port 0xdc444600 irq 220
[   24.862170] ata4: SATA max UDMA/133 abar m1024@0xdc444400 port 0xdc444680 irq 220
[   24.882375] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240000117992]
[   24.897127] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.946814] ata1.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
[   24.946817] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 1)
[   24.947777] ata1.00: configured for UDMA/133
[   24.961690] ata2: SATA link down (SStatus 0 SControl 0)
[   24.974958] ata3: SATA link down (SStatus 0 SControl 300)
[   24.989288] ata4: SATA link down (SStatus 0 SControl 0)
[   24.989579] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[   24.989924] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   24.989938] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   24.989942] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   24.989974] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   24.993896] ehci_hcd 0000:00:1d.7: debug port 1
[   24.993904] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   24.993911] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[   24.997827] Driver 'sd' needs updating - please use bus_type methods
[   24.999933] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.000166] usb usb5: configuration #1 chosen from 1 choice
[   25.000217] hub 5-0:1.0: USB hub found
[   25.000229] hub 5-0:1.0: 8 ports detected
[   25.000701] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   25.000729] sd 0:0:0:0: [sda] Write Protect is off
[   25.000735] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.000773] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.000868] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   25.000891] sd 0:0:0:0: [sda] Write Protect is off
[   25.000897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.000928] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.000931]  sda: sda1 sda2 < sda5 >
[   25.073133] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.077752] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.101562] ata_piix 0000:00:1f.1: version 2.12
[   25.101584] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   25.101627] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.102134] scsi4 : ata_piix
[   25.102593] scsi5 : ata_piix
[   25.103058] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   25.103061] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   25.280296] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WW01, max UDMA/33
[   25.286355] ata5.00: configured for UDMA/33
[   25.286441] ata6: port disabled. ignoring.
[   25.288541] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WW01 PQ: 0 ANSI: 5
[   25.288616] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   25.299771] Driver 'sr' needs updating - please use bus_type methods
[   25.306684] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.306688] Uniform CD-ROM driver Revision: 3.20
[   25.306752] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   25.357389] Attempting manual resume
[   25.357393] swsusp: Resume From Partition 8:5
[   25.357394] PM: Checking swsusp image.
[   25.357521] PM: Resume from disk failed.
[   25.424248] kjournald starting.  Commit interval 5 seconds
[   25.424273] EXT3-fs: mounted filesystem with ordered data mode.
[   33.795559] Linux agpgart interface v0.102
[   33.907603] iTCO_vendor_support: vendor-support=0
[   33.994528] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.033863] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.109650] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.109753] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   34.109791] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.163005] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.220552] agpgart: Detected an Intel 945GM Chipset.
[   34.221547] agpgart: Detected 7932K stolen memory.
[   34.239245] agpgart: AGP aperture is 256M @ 0xc0000000
[   34.260367] ACPI: Battery Slot [BAT1] (battery absent)
[   34.305662] intel_rng: FWH not detected
[   34.393179] input: Power Button (FF) as /devices/virtual/input/input3
[   34.443491] ACPI: Power Button (FF) [PWRF]
[   34.443551] input: Power Button (CM) as /devices/virtual/input/input4
[   34.507399] ACPI: Power Button (CM) [PWRB]
[   34.507458] input: Sleep Button (CM) as /devices/virtual/input/input5
[   34.575299] ACPI: Sleep Button (CM) [SLPB]
[   34.575360] input: Lid Switch as /devices/virtual/input/input6
[   34.607517] ACPI: Lid Switch [LID]
[   34.608471] ACPI: AC Adapter [ACAD] (on-line)
[   34.726073] sdhci: Secure Digital Host Controller Interface driver
[   34.726078] sdhci: Copyright(c) Pierre Ossman
[   34.726122] sdhci: SDHCI controller found at 0000:07:09.1 [1180:0822] (rev 19)
[   34.726142] PCI: Enabling device 0000:07:09.1 (0000 -> 0002)
[   34.726153] ACPI: PCI Interrupt 0000:07:09.1[B] -> GSI 21 (level, low) -> IRQ 22
[   34.726174] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   34.726183] PCI: Setting latency timer of device 0000:07:09.1 to 64
[   34.726233] mmc0: SDHCI at 0xdc001800 irq 22 DMA
[   34.809669] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   34.813731] ricoh-mmc: Ricoh MMC Controller disabling driver
[   34.813735] ricoh-mmc: Copyright(c) Philip Langdale
[   34.813778] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 1)
[   34.813791] ricoh-mmc: Controller is now disabled.
[   34.861919] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.862471] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   34.921803] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   35.080327] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   35.080332] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.080490] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   35.080506] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   35.080532] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   35.273763] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   35.273792] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.367057] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   35.399637] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   35.887467] iwl3945: Radio Frequency Kill Switch is On:
[   35.887470] Kill switch must be turned off for wireless networking to work.
[   35.892353] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   35.902404] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   35.922373] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   35.949922] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   35.969883] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   36.089794] lp: driver loaded but no devices found
[   36.190137] ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 19 (level, low) -> IRQ 20
[   36.259566] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   36.679575] EXT3 FS on sda1, internal journal
[   37.651848] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.623063] ACPI: ACPI Dock Station Driver 
[   40.262881] ppdev: user-space parallel port driver
[   40.712961] audit(1218689688.538:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5058 profile="/usr/sbin/cupsd" namespace="default"
[   40.799081] apm: BIOS not found.
[   44.168722] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   44.328654] Bluetooth: Core ver 2.11
[   44.328811] NET: Registered protocol family 31
[   44.328815] Bluetooth: HCI device and connection manager initialized
[   44.328824] Bluetooth: HCI socket layer initialized
[   44.400138] Bluetooth: L2CAP ver 2.9
[   44.400147] Bluetooth: L2CAP socket layer initialized
[   44.489007] Bluetooth: RFCOMM socket layer initialized
[   44.489029] Bluetooth: RFCOMM TTY layer initialized
[   44.489034] Bluetooth: RFCOMM ver 1.8
[   46.716148] [drm] Initialized drm 1.1.0 20060810
[   46.742163] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   46.742182] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.742307] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.311132] NET: Registered protocol family 17
[   58.800485] NET: Registered protocol family 10
[   58.800949] lo: Disabled Privacy Extensions
[   69.087058] CPU0 attaching NULL sched-domain.
[   69.087070] CPU1 attaching NULL sched-domain.
[   69.099471] CPU0 attaching sched-domain:
[   69.099484]  domain 0: span 03
[   69.099488]   groups: 01 02
[   69.099495] CPU1 attaching sched-domain:
[   69.099499]  domain 0: span 03
[   69.099503]   groups: 02 01
[   70.877776] eth0: no IPv6 routers present
[  370.275934] usb 5-1: new high speed USB device using ehci_hcd and address 2
[  374.375787] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[  374.375819] hub 5-0:1.0: hub_port_status failed (err = -32)

```

It seems like it detects the usb device and then something fails.

---


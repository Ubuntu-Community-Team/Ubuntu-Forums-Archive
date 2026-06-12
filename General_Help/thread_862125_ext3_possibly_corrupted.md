---
title: "ext3 possibly corrupted"
date: 2008-07-17
forum: General Help
---

### Post by toucher5 on 2008-07-17
Here is what my /var/log/messages file says.


```

Jul 17 00:02:08 bigbox -- MARK --
Jul 17 00:22:08 bigbox -- MARK --
Jul 17 00:38:45 bigbox kernel: [ 5891.716668] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 17 00:38:47 bigbox exiting on signal 15
Jul 17 07:06:21 bigbox syslogd 1.5.0#1ubuntu1: restart.
Jul 17 07:06:21 bigbox kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jul 17 07:06:21 bigbox kernel: Loaded 27704 symbols from /boot/System.map-2.6.24-16-generic.
Jul 17 07:06:21 bigbox kernel: Symbols match kernel version 2.6.24.
Jul 17 07:06:21 bigbox kernel: Loaded 14349 symbols from 80 modules.
Jul 17 07:06:22 bigbox kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jul 17 07:06:22 bigbox kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000027e73000 (usable)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 0000000027e73000 - 0000000027e75000 (ACPI NVS)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 0000000027e75000 - 0000000027e94000 (ACPI data)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 0000000027e94000 - 0000000027f00000 (reserved)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jul 17 07:06:22 bigbox kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jul 17 07:06:22 bigbox kernel: [    0.000000] 0MB HIGHMEM available.
Jul 17 07:06:22 bigbox kernel: [    0.000000] 638MB LOWMEM available.
Jul 17 07:06:22 bigbox kernel: [    0.000000] found SMP MP-table at 000fe710
Jul 17 07:06:22 bigbox kernel: [    0.000000] Zone PFN ranges:
Jul 17 07:06:22 bigbox kernel: [    0.000000]   DMA             0 ->     4096
Jul 17 07:06:22 bigbox kernel: [    0.000000]   Normal       4096 ->   163443
Jul 17 07:06:22 bigbox kernel: [    0.000000]   HighMem    163443 ->   163443
Jul 17 07:06:22 bigbox kernel: [    0.000000] Movable zone start PFN for each node
Jul 17 07:06:22 bigbox kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 17 07:06:22 bigbox kernel: [    0.000000]     0:        0 ->   163443
Jul 17 07:06:22 bigbox kernel: [    0.000000] DMI 2.3 present.
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FD530 checksum 0
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: RSDP 000FD530, 0014 (r0 DELL  )
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: RSDT 000FD544, 0034 (r1 DELL    4500S          6 ASL        61)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: FACP 000FD578, 0074 (r1 DELL    4500S          6 ASL        61)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: DSDT FFFD4E9C, 22E4 (r1   DELL    dt_ex     1000 MSFT  100000D)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: FACS 27E73000, 0040
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: SSDT FFFD7180, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: APIC 000FD5EC, 005C (r1 DELL    4500S          6 ASL        61)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: BOOT 000FD648, 0028 (r1 DELL    4500S          6 ASL        61)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 17 07:06:22 bigbox kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jul 17 07:06:22 bigbox kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 17 07:06:22 bigbox kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 17 07:06:22 bigbox kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 17 07:06:22 bigbox kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 17 07:06:22 bigbox kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 27f00000:d6d00000)
Jul 17 07:06:22 bigbox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jul 17 07:06:22 bigbox kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jul 17 07:06:22 bigbox kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 162167
Jul 17 07:06:22 bigbox kernel: [    0.000000] Kernel command line: root=UUID=b44d1a81-ca59-4f26-a853-1c0cedfed974 ro quiet splash
Jul 17 07:06:22 bigbox kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jul 17 07:06:22 bigbox kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jul 17 07:06:22 bigbox kernel: [    0.000000] Initializing CPU#0
Jul 17 07:06:22 bigbox kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jul 17 07:06:22 bigbox kernel: [    0.000000] Detected 1800.078 MHz processor.
Jul 17 07:06:22 bigbox kernel: [   13.407703] Console: colour VGA+ 80x25
Jul 17 07:06:22 bigbox kernel: [   13.407711] console [tty0] enabled
Jul 17 07:06:22 bigbox kernel: [   13.408744] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 17 07:06:22 bigbox kernel: [   13.409782] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 17 07:06:22 bigbox kernel: [   13.432003] Memory: 635428k/653772k available (2157k kernel code, 17732k reserved, 998k data, 364k init, 0k highmem)
Jul 17 07:06:22 bigbox kernel: [   13.432015] virtual kernel memory layout:
Jul 17 07:06:22 bigbox kernel: [   13.432017]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jul 17 07:06:22 bigbox kernel: [   13.432019]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jul 17 07:06:22 bigbox kernel: [   13.432021]     vmalloc : 0xe8800000 - 0xff7fe000   ( 367 MB)
Jul 17 07:06:22 bigbox kernel: [   13.432022]     lowmem  : 0xc0000000 - 0xe7e73000   ( 638 MB)
Jul 17 07:06:22 bigbox kernel: [   13.432024]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
Jul 17 07:06:22 bigbox kernel: [   13.432025]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
Jul 17 07:06:22 bigbox kernel: [   13.432027]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
Jul 17 07:06:22 bigbox kernel: [   13.432032] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 17 07:06:22 bigbox kernel: [   13.432085] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jul 17 07:06:22 bigbox kernel: [   13.511993] Calibrating delay using timer specific routine.. 3604.20 BogoMIPS (lpj=7208412)
Jul 17 07:06:22 bigbox kernel: [   13.512030] Security Framework initialized
Jul 17 07:06:22 bigbox kernel: [   13.512039] SELinux:  Disabled at boot.
Jul 17 07:06:22 bigbox kernel: [   13.512060] AppArmor: AppArmor initialized
Jul 17 07:06:22 bigbox kernel: [   13.512066] Failure registering capabilities with primary security module.
Jul 17 07:06:22 bigbox kernel: [   13.512078] Mount-cache hash table entries: 512
Jul 17 07:06:22 bigbox kernel: [   13.512294] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 17 07:06:22 bigbox kernel: [   13.512298] CPU: L2 cache: 512K
Jul 17 07:06:22 bigbox kernel: [   13.512302] CPU: Hyper-Threading is disabled
Jul 17 07:06:22 bigbox kernel: [   13.512323] Compat vDSO mapped to ffffe000.
Jul 17 07:06:22 bigbox kernel: [   13.512341] Checking 'hlt' instruction... OK.
Jul 17 07:06:22 bigbox kernel: [   13.528569] SMP alternatives: switching to UP code
Jul 17 07:06:22 bigbox kernel: [   13.531009] Freeing SMP alternatives: 11k freed
Jul 17 07:06:22 bigbox kernel: [   13.531214] Early unpacking initramfs... done
Jul 17 07:06:22 bigbox kernel: [   14.049415] ACPI: Core revision 20070126
Jul 17 07:06:22 bigbox kernel: [   14.061584] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jul 17 07:06:22 bigbox kernel: [   14.086088] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 04
Jul 17 07:06:22 bigbox kernel: [   14.086143] Total of 1 processors activated (3604.20 BogoMIPS).
Jul 17 07:06:22 bigbox kernel: [   14.086291] ENABLING IO-APIC IRQs
Jul 17 07:06:22 bigbox kernel: [   14.086488] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 17 07:06:22 bigbox kernel: [   14.231002] Brought up 1 CPUs
Jul 17 07:06:22 bigbox kernel: [   14.231323] net_namespace: 64 bytes
Jul 17 07:06:22 bigbox kernel: [   14.231340] Booting paravirtualized kernel on bare hardware
Jul 17 07:06:22 bigbox kernel: [   14.232275] Time: 11:04:52  Date: 07/17/08
Jul 17 07:06:22 bigbox kernel: [   14.232316] NET: Registered protocol family 16
Jul 17 07:06:22 bigbox kernel: [   14.232657] EISA bus registered
Jul 17 07:06:22 bigbox kernel: [   14.232691] ACPI: bus type pci registered
Jul 17 07:06:22 bigbox kernel: [   14.259458] PCI: PCI BIOS revision 2.10 entry at 0xfbe4e, last bus=1
Jul 17 07:06:22 bigbox kernel: [   14.259462] PCI: Using configuration type 1
Jul 17 07:06:22 bigbox kernel: [   14.259465] Setting up standard PCI resources
Jul 17 07:06:22 bigbox kernel: [   14.290031] ACPI: Interpreter enabled
Jul 17 07:06:22 bigbox kernel: [   14.290037] ACPI: (supports S0 S1 S3 S4 S5)
Jul 17 07:06:22 bigbox kernel: [   14.290065] ACPI: Using IOAPIC for interrupt routing
Jul 17 07:06:22 bigbox kernel: [   14.316709] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 17 07:06:22 bigbox kernel: [   14.317295] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jul 17 07:06:22 bigbox kernel: [   14.317298] * this clock source is slow. If you are sure your timer does not have
Jul 17 07:06:22 bigbox kernel: [   14.317300] * this bug, please use "acpi_pm_good" to disable the workaround
Jul 17 07:06:22 bigbox kernel: [   14.317357] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Jul 17 07:06:22 bigbox kernel: [   14.317362] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Jul 17 07:06:22 bigbox kernel: [   14.317810] PCI: Transparent bridge - 0000:00:1e.0
Jul 17 07:06:22 bigbox kernel: [   14.351506] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Jul 17 07:06:22 bigbox kernel: [   14.351864] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Jul 17 07:06:22 bigbox kernel: [   14.352222] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Jul 17 07:06:22 bigbox kernel: [   14.352586] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Jul 17 07:06:22 bigbox kernel: [   14.352939] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul 17 07:06:22 bigbox kernel: [   14.353296] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul 17 07:06:22 bigbox kernel: [   14.353651] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Jul 17 07:06:22 bigbox kernel: [   14.354009] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
Jul 17 07:06:22 bigbox kernel: [   14.354278] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 17 07:06:22 bigbox kernel: [   14.354332] pnp: PnP ACPI init
Jul 17 07:06:22 bigbox kernel: [   14.354345] ACPI: bus type pnp registered
Jul 17 07:06:22 bigbox kernel: [   14.378729] pnp: PnP ACPI: found 12 devices
Jul 17 07:06:22 bigbox kernel: [   14.378734] ACPI: ACPI bus type pnp unregistered
Jul 17 07:06:22 bigbox kernel: [   14.378741] PnPBIOS: Disabled by ACPI PNP
Jul 17 07:06:22 bigbox kernel: [   14.379112] PCI: Using ACPI for IRQ routing
Jul 17 07:06:22 bigbox kernel: [   14.379117] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 17 07:06:22 bigbox kernel: [   14.394708] NET: Registered protocol family 8
Jul 17 07:06:22 bigbox kernel: [   14.394712] NET: Registered protocol family 20
Jul 17 07:06:22 bigbox kernel: [   14.394821] AppArmor: AppArmor Filesystem Enabled
Jul 17 07:06:22 bigbox kernel: [   14.398681] Time: tsc clocksource has been installed.
Jul 17 07:06:22 bigbox kernel: [   14.406731] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406736] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406740] system 00:00: iomem range 0x1000000-0x27e72fff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406744] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406749] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406753] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406758] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406762] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.406781] system 00:0b: ioport range 0x800-0x85f has been reserved
Jul 17 07:06:22 bigbox kernel: [   14.406785] system 00:0b: ioport range 0xc00-0xc7f has been reserved
Jul 17 07:06:22 bigbox kernel: [   14.406789] system 00:0b: ioport range 0x860-0x8ff could not be reserved
Jul 17 07:06:22 bigbox kernel: [   14.437430] PCI: Bridge: 0000:00:1e.0
Jul 17 07:06:22 bigbox kernel: [   14.437436]   IO window: e000-efff
Jul 17 07:06:22 bigbox kernel: [   14.437444]   MEM window: ff800000-ff9fffff
Jul 17 07:06:22 bigbox kernel: [   14.437450]   PREFETCH window: disabled.
Jul 17 07:06:22 bigbox kernel: [   14.437487] NET: Registered protocol family 2
Jul 17 07:06:22 bigbox kernel: [   14.474702] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jul 17 07:06:22 bigbox kernel: [   14.475261] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 17 07:06:22 bigbox kernel: [   14.476739] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jul 17 07:06:22 bigbox kernel: [   14.477676] TCP: Hash tables configured (established 131072 bind 65536)
Jul 17 07:06:22 bigbox kernel: [   14.477684] TCP reno registered
Jul 17 07:06:22 bigbox kernel: [   14.486865] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Jul 17 07:06:22 bigbox kernel: [   14.974316]  it is
Jul 17 07:06:22 bigbox kernel: [   15.513114] Freeing initrd memory: 7703k freed
Jul 17 07:06:22 bigbox kernel: [   15.513396] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Jul 17 07:06:22 bigbox kernel: [   15.513400] Simple Boot Flag at 0x7a set to 0x1
Jul 17 07:06:22 bigbox kernel: [   15.514045] audit: initializing netlink socket (disabled)
Jul 17 07:06:22 bigbox kernel: [   15.514069] audit(1216292693.980:1): initialized
Jul 17 07:06:22 bigbox kernel: [   15.517418] VFS: Disk quotas dquot_6.5.1
Jul 17 07:06:22 bigbox kernel: [   15.517550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 17 07:06:22 bigbox kernel: [   15.517778] io scheduler noop registered
Jul 17 07:06:22 bigbox kernel: [   15.517782] io scheduler anticipatory registered
Jul 17 07:06:22 bigbox kernel: [   15.517785] io scheduler deadline registered
Jul 17 07:06:22 bigbox kernel: [   15.517806] io scheduler cfq registered (default)
Jul 17 07:06:22 bigbox kernel: [   15.518326] isapnp: Scanning for PnP cards...
Jul 17 07:06:22 bigbox kernel: [   15.872250] isapnp: No Plug & Play device found
Jul 17 07:06:22 bigbox kernel: [   15.922970] Real Time Clock Driver v1.12ac
Jul 17 07:06:22 bigbox kernel: [   15.923114] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jul 17 07:06:22 bigbox kernel: [   15.923265] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 17 07:06:22 bigbox kernel: [   15.924781] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 17 07:06:22 bigbox kernel: [   15.925069] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 17 (level, low) -> IRQ 16
Jul 17 07:06:22 bigbox kernel: [   15.926864] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 17 07:06:22 bigbox kernel: [   15.926977] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jul 17 07:06:22 bigbox kernel: [   15.927150] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Jul 17 07:06:22 bigbox kernel: [   15.929704] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 17 07:06:22 bigbox kernel: [   15.929711] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 17 07:06:22 bigbox kernel: [   15.936405] mice: PS/2 mouse device common for all mice
Jul 17 07:06:22 bigbox kernel: [   15.936598] EISA: Probing bus 0 at eisa.0
Jul 17 07:06:22 bigbox kernel: [   15.936640] EISA: Detected 0 cards.
Jul 17 07:06:22 bigbox kernel: [   15.936645] cpuidle: using governor ladder
Jul 17 07:06:22 bigbox kernel: [   15.936649] cpuidle: using governor menu
Jul 17 07:06:22 bigbox kernel: [   15.936801] NET: Registered protocol family 1
Jul 17 07:06:22 bigbox kernel: [   15.936847] Using IPI No-Shortcut mode
Jul 17 07:06:22 bigbox kernel: [   15.936896] registered taskstats version 1
Jul 17 07:06:22 bigbox kernel: [   15.937032]   Magic number: 0:960:74
Jul 17 07:06:22 bigbox kernel: [   15.937189] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 17 07:06:22 bigbox kernel: [   15.937191] EDD information not available.
Jul 17 07:06:22 bigbox kernel: [   15.937774] Freeing unused kernel memory: 364k freed
Jul 17 07:06:22 bigbox kernel: [   15.976219] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 17 07:06:22 bigbox kernel: [   17.404133] fuse init (API version 7.9)
Jul 17 07:06:22 bigbox kernel: [   18.715974] usbcore: registered new interface driver usbfs
Jul 17 07:06:22 bigbox kernel: [   18.716011] usbcore: registered new interface driver hub
Jul 17 07:06:22 bigbox kernel: [   18.735880] usbcore: registered new device driver usb
Jul 17 07:06:22 bigbox kernel: [   18.748308] USB Universal Host Controller Interface driver v3.0
Jul 17 07:06:22 bigbox kernel: [   18.748407] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
Jul 17 07:06:22 bigbox kernel: [   18.748429] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 17 07:06:22 bigbox kernel: [   18.748829] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jul 17 07:06:22 bigbox kernel: [   18.748865] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
Jul 17 07:06:22 bigbox kernel: [   18.749089] usb usb1: configuration #1 chosen from 1 choice
Jul 17 07:06:22 bigbox kernel: [   18.749126] hub 1-0:1.0: USB hub found
Jul 17 07:06:22 bigbox kernel: [   18.749135] hub 1-0:1.0: 2 ports detected
Jul 17 07:06:22 bigbox kernel: [   18.851819] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
Jul 17 07:06:22 bigbox kernel: [   18.851843] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 17 07:06:22 bigbox kernel: [   18.851886] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jul 17 07:06:22 bigbox kernel: [   18.851919] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
Jul 17 07:06:22 bigbox kernel: [   18.852091] usb usb2: configuration #1 chosen from 1 choice
Jul 17 07:06:22 bigbox kernel: [   18.852129] hub 2-0:1.0: USB hub found
Jul 17 07:06:22 bigbox kernel: [   18.852139] hub 2-0:1.0: 2 ports detected
Jul 17 07:06:22 bigbox kernel: [   18.955682] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Jul 17 07:06:22 bigbox kernel: [   18.955707] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 17 07:06:22 bigbox kernel: [   18.955745] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Jul 17 07:06:22 bigbox kernel: [   18.955780] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
Jul 17 07:06:22 bigbox kernel: [   18.955952] usb usb3: configuration #1 chosen from 1 choice
Jul 17 07:06:22 bigbox kernel: [   18.955992] hub 3-0:1.0: USB hub found
Jul 17 07:06:22 bigbox kernel: [   18.956002] hub 3-0:1.0: 2 ports detected
Jul 17 07:06:22 bigbox kernel: [   19.059549] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
Jul 17 07:06:22 bigbox kernel: [   19.059578] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jul 17 07:06:22 bigbox kernel: [   19.059616] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Jul 17 07:06:22 bigbox kernel: [   19.063527] ehci_hcd 0000:00:1d.7: debug port 1
Jul 17 07:06:22 bigbox kernel: [   19.063556] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa00800
Jul 17 07:06:22 bigbox kernel: [   19.067782] SCSI subsystem initialized
Jul 17 07:06:22 bigbox kernel: [   19.082168] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jul 17 07:06:22 bigbox kernel: [   19.082378] usb usb4: configuration #1 chosen from 1 choice
Jul 17 07:06:22 bigbox kernel: [   19.082419] hub 4-0:1.0: USB hub found
Jul 17 07:06:22 bigbox kernel: [   19.082436] hub 4-0:1.0: 6 ports detected
Jul 17 07:06:22 bigbox kernel: [   19.175190] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Jul 17 07:06:22 bigbox kernel: [   19.183473] ACPI: PCI Interrupt 0000:01:07.0[A] -> GSI 16 (level, low) -> IRQ 17
Jul 17 07:06:22 bigbox kernel: [   19.189119] eth0: VIA Rhine III at 0xff8ffc00, 00:1c:f0:16:42:dc, IRQ 17.
Jul 17 07:06:22 bigbox kernel: [   19.189835] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
Jul 17 07:06:22 bigbox kernel: [   19.228404] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Jul 17 07:06:22 bigbox kernel: [   19.228414] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
Jul 17 07:06:22 bigbox kernel: [   19.247068] scsi0 : ata_piix
Jul 17 07:06:22 bigbox kernel: [   19.263095] scsi1 : ata_piix
Jul 17 07:06:22 bigbox kernel: [   19.263173] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jul 17 07:06:22 bigbox kernel: [   19.263178] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jul 17 07:06:22 bigbox kernel: [   19.321955] Floppy drive(s): fd0 is 1.44M
Jul 17 07:06:22 bigbox kernel: [   19.337010] FDC 0 is a post-1991 82077
Jul 17 07:06:22 bigbox kernel: [   19.427271] ata1.00: ATA-7: Maxtor 2B020H1, WAK21R90, max UDMA/100
Jul 17 07:06:22 bigbox kernel: [   19.427278] ata1.00: 39062500 sectors, multi 8: LBA48 
Jul 17 07:06:22 bigbox kernel: [   19.443187] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   19.802615] ata2.00: ATAPI: _NEC CD-RW NR-7900A, 1.08, max UDMA/33
Jul 17 07:06:22 bigbox kernel: [   20.014209] ata2.00: configured for UDMA/33
Jul 17 07:06:22 bigbox kernel: [   20.014401] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2B020H1   WAK2 PQ: 0 ANSI: 5
Jul 17 07:06:22 bigbox kernel: [   20.017238] scsi 1:0:0:0: CD-ROM            _NEC     NR-7900A         1.08 PQ: 0 ANSI: 5
Jul 17 07:06:22 bigbox kernel: [   22.554512] Driver 'sd' needs updating - please use bus_type methods
Jul 17 07:06:22 bigbox kernel: [   22.556423] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   22.556447] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   22.556485] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   22.556567] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   22.556585] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   22.556619] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   22.556625]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jul 17 07:06:22 bigbox kernel: [   22.572458]  sda2 < sda5 sda6 sda7 sda8 >
Jul 17 07:06:22 bigbox kernel: [   22.620482] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 17 07:06:22 bigbox kernel: [   22.633797] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 17 07:06:22 bigbox kernel: [   22.633829] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 17 07:06:22 bigbox kernel: [   22.655836] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jul 17 07:06:22 bigbox kernel: [   22.655845] Uniform CD-ROM driver Revision: 3.20
Jul 17 07:06:22 bigbox kernel: [   25.078396]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   25.102231] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   25.102247] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   27.161500]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   27.182923] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   27.182943] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   29.233593]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   29.255647] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   29.255670] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   31.305687]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   31.328401] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   31.328427] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   33.388804]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   33.413086] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   33.413106] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   35.471920]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   35.493810] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   35.493835] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:22 bigbox kernel: [   35.493840] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:22 bigbox kernel: [   35.493847] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:22 bigbox kernel: [   35.493850]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:22 bigbox kernel: [   35.493864]         00 ef bd d0 
Jul 17 07:06:22 bigbox kernel: [   35.493870] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:22 bigbox kernel: [   35.493879] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:22 bigbox kernel: [   35.493959] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   37.543860]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   37.566535] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   37.566556] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   39.615934]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   39.639243] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   39.639266] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   41.699042]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   41.719976] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   41.719993] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   43.771131]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   43.792694] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   43.792711] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   45.843226]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   45.865413] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   45.865430] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   47.915316]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   47.938142] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   47.938161] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:22 bigbox kernel: [   47.938167] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:22 bigbox kernel: [   47.938174] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:22 bigbox kernel: [   47.938177]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:22 bigbox kernel: [   47.938191]         00 ef bd d0 
Jul 17 07:06:22 bigbox kernel: [   47.938197] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:22 bigbox kernel: [   47.938206] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:22 bigbox kernel: [   47.938210] printk: 6 messages suppressed.
Jul 17 07:06:22 bigbox kernel: [   47.938236] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   47.938348] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   49.987431]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   50.010870] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   50.010887] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   52.070631]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   52.091583] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   52.091600] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   54.142726]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   54.164330] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   54.164352] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   56.214814]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   56.237041] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   56.237058] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   58.286907]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   58.309798] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   58.309820] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   60.359003]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   60.382516] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   60.382535] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:22 bigbox kernel: [   60.382541] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:22 bigbox kernel: [   60.382548] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:22 bigbox kernel: [   60.382551]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:22 bigbox kernel: [   60.382565]         00 ef bd d2 
Jul 17 07:06:22 bigbox kernel: [   60.382571] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:22 bigbox kernel: [   60.382580] end_request: I/O error, dev sda, sector 15711698
Jul 17 07:06:22 bigbox kernel: [   60.382778] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   60.383943] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   60.435253] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   60.435298] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   60.435319] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   60.435355] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   60.820307] Attempting manual resume
Jul 17 07:06:22 bigbox kernel: [   60.886471] kjournald starting.  Commit interval 5 seconds
Jul 17 07:06:22 bigbox kernel: [   60.886494] EXT3-fs: mounted filesystem with ordered data mode.
Jul 17 07:06:22 bigbox kernel: [   70.904030] Linux agpgart interface v0.102
Jul 17 07:06:22 bigbox kernel: [   70.968448] agpgart: Detected an Intel 830M Chipset.
Jul 17 07:06:22 bigbox kernel: [   70.968623] agpgart: Detected 892K stolen memory.
Jul 17 07:06:22 bigbox kernel: [   71.021405] agpgart: AGP aperture is 128M @ 0xf0000000
Jul 17 07:06:22 bigbox kernel: [   71.132211] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 17 07:06:22 bigbox kernel: [   71.496668] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 17 07:06:22 bigbox kernel: [   71.552561] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Jul 17 07:06:22 bigbox kernel: [   71.772276] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jul 17 07:06:22 bigbox kernel: [   71.828068] iTCO_vendor_support: vendor-support=0
Jul 17 07:06:22 bigbox kernel: [   71.884859] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jul 17 07:06:22 bigbox kernel: [   71.885066] iTCO_wdt: No card detected
Jul 17 07:06:22 bigbox kernel: [   72.149987] input: Power Button (FF) as /devices/virtual/input/input3
Jul 17 07:06:22 bigbox kernel: [   72.159510] ACPI: Power Button (FF) [PWRF]
Jul 17 07:06:22 bigbox kernel: [   72.159696] input: Power Button (CM) as /devices/virtual/input/input4
Jul 17 07:06:22 bigbox kernel: [   72.175487] ACPI: Power Button (CM) [VBTN]
Jul 17 07:06:22 bigbox kernel: [   74.544186]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   74.560141] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   74.560164] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   76.616266]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   76.640832] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   76.640852] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   78.699349]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   78.721551] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   78.721559] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   80.771442]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   80.794271] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   80.794279] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   82.843533]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   82.867002] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   82.867009] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   84.926647]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   84.947723] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   84.947743] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:22 bigbox kernel: [   84.947748] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:22 bigbox kernel: [   84.947756] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:22 bigbox kernel: [   84.947759]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:22 bigbox kernel: [   84.947773]         00 ef bd d0 
Jul 17 07:06:22 bigbox kernel: [   84.947779] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:22 bigbox kernel: [   84.947787] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:22 bigbox kernel: [   84.948106] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   84.961119] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   84.972514] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   84.983610] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   84.983646] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   84.983664] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   84.983698] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   85.158036] parport_pc 00:0a: reported by Plug and Play ACPI
Jul 17 07:06:22 bigbox kernel: [   85.158095] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Jul 17 07:06:22 bigbox kernel: [   87.285226]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   87.300006] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   87.300019] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   89.357276]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   89.380728] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   89.380735] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   91.440391]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   91.461452] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   91.461460] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   93.512483]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   93.534181] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   93.534189] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   95.584574]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   95.606900] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   95.606908] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   97.656667]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:22 bigbox kernel: [   97.679620] ata1.00: configured for UDMA/100
Jul 17 07:06:22 bigbox kernel: [   97.679634] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:22 bigbox kernel: [   97.679640] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:22 bigbox kernel: [   97.679647] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:22 bigbox kernel: [   97.679650]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:22 bigbox kernel: [   97.679664]         00 ef bd d0 
Jul 17 07:06:22 bigbox kernel: [   97.679670] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:22 bigbox kernel: [   97.679679] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:22 bigbox kernel: [   97.679683] printk: 11 messages suppressed.
Jul 17 07:06:22 bigbox kernel: [   97.679879] ata1: EH complete
Jul 17 07:06:22 bigbox kernel: [   97.698498] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   97.698634] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   97.698672] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   97.698708] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:22 bigbox kernel: [   97.698726] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:06:22 bigbox kernel: [   97.698760] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:06:22 bigbox kernel: [   98.130379] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 16
Jul 17 07:06:22 bigbox kernel: [   98.451145] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jul 17 07:06:22 bigbox kernel: [   98.476595] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jul 17 07:06:22 bigbox kernel: [   98.501917] intel8x0_measure_ac97_clock: measured 54809 usecs
Jul 17 07:06:22 bigbox kernel: [   98.501924] intel8x0: clocking to 48000
Jul 17 07:06:22 bigbox kernel: [   99.301152] lp0: using parport0 (interrupt-driven).
Jul 17 07:06:22 bigbox kernel: [   99.381646] Adding 851404k swap on /dev/sda5.  Priority:-1 extents:1 across:851404k
Jul 17 07:06:22 bigbox kernel: [   99.446983] Adding 506008k swap on /dev/sda7.  Priority:-2 extents:1 across:506008k
Jul 17 07:06:22 bigbox kernel: [   99.926342] EXT3 FS on sda8, internal journal
Jul 17 07:06:22 bigbox kernel: [  101.170534] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 17 07:06:22 bigbox kernel: [  101.901613] No dock devices found.
Jul 17 07:06:22 bigbox kernel: [  103.609891] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 17 07:06:22 bigbox kernel: [  103.609900] apm: overridden by ACPI.
Jul 17 07:06:22 bigbox kernel: [  103.789928] ppdev: user-space parallel port driver
Jul 17 07:06:23 bigbox kernel: [  104.920158] audit(1216292783.749:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5780 profile="/usr/sbin/cupsd" namespace="default"
Jul 17 07:06:24 bigbox dhcdbd: Started up.
Jul 17 07:06:25 bigbox kernel: [  106.992283] audit(1216292785.821:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5991 profile="/usr/sbin/cupsd" namespace="default"
Jul 17 07:06:27 bigbox kernel: [  109.042325]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:28 bigbox kernel: [  109.417114] ata1.00: configured for UDMA/100
Jul 17 07:06:28 bigbox kernel: [  109.417131] ata1: EH complete
Jul 17 07:06:30 bigbox kernel: [  111.467087]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:30 bigbox kernel: [  111.481830] ata1.00: configured for UDMA/100
Jul 17 07:06:30 bigbox kernel: [  111.481847] ata1: EH complete
Jul 17 07:06:32 bigbox kernel: [  113.539175]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:32 bigbox kernel: [  113.554557] ata1.00: configured for UDMA/100
Jul 17 07:06:32 bigbox kernel: [  113.554573] ata1: EH complete
Jul 17 07:06:34 bigbox kernel: [  115.611266]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:34 bigbox kernel: [  115.627285] ata1.00: configured for UDMA/100
Jul 17 07:06:34 bigbox kernel: [  115.627301] ata1: EH complete
Jul 17 07:06:36 bigbox kernel: [  117.683357]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:36 bigbox kernel: [  117.708001] ata1.00: configured for UDMA/100
Jul 17 07:06:36 bigbox kernel: [  117.708023] ata1: EH complete
Jul 17 07:06:38 bigbox kernel: [  119.766492]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:38 bigbox kernel: [  119.788729] ata1.00: configured for UDMA/100
Jul 17 07:06:38 bigbox kernel: [  119.788755] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:38 bigbox kernel: [  119.788761] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:38 bigbox kernel: [  119.788768] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:38 bigbox kernel: [  119.788772]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:38 bigbox kernel: [  119.788786]         00 ef bd d0 
Jul 17 07:06:38 bigbox kernel: [  119.788793] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:38 bigbox kernel: [  119.788801] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:38 bigbox kernel: [  119.788806] printk: 1 messages suppressed.
Jul 17 07:06:38 bigbox kernel: [  119.789081] ata1: EH complete
Jul 17 07:06:40 bigbox kernel: [  121.849445]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:40 bigbox kernel: [  121.873424] ata1.00: configured for UDMA/100
Jul 17 07:06:40 bigbox kernel: [  121.873442] ata1: EH complete
Jul 17 07:06:42 bigbox kernel: [  123.932552]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:42 bigbox kernel: [  123.954144] ata1.00: configured for UDMA/100
Jul 17 07:06:42 bigbox kernel: [  123.954167] ata1: EH complete
Jul 17 07:06:44 bigbox kernel: [  126.004622]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:44 bigbox kernel: [  126.026864] ata1.00: configured for UDMA/100
Jul 17 07:06:44 bigbox kernel: [  126.026879] ata1: EH complete
Jul 17 07:06:46 bigbox kernel: [  128.076740]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:46 bigbox kernel: [  128.099596] ata1.00: configured for UDMA/100
Jul 17 07:06:46 bigbox kernel: [  128.099617] ata1: EH complete
Jul 17 07:06:49 bigbox kernel: [  130.159851]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:49 bigbox kernel: [  130.184324] ata1.00: configured for UDMA/100
Jul 17 07:06:49 bigbox kernel: [  130.184347] ata1: EH complete
Jul 17 07:06:51 bigbox kernel: [  132.242961]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:51 bigbox kernel: [  132.265019] ata1.00: configured for UDMA/100
Jul 17 07:06:51 bigbox kernel: [  132.265042] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:06:51 bigbox kernel: [  132.265048] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:06:51 bigbox kernel: [  132.265055] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:06:51 bigbox kernel: [  132.265059]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:06:51 bigbox kernel: [  132.265073]         00 ef bd d0 
Jul 17 07:06:51 bigbox kernel: [  132.265080] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:06:51 bigbox kernel: [  132.265088] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:06:51 bigbox kernel: [  132.265093] printk: 12 messages suppressed.
Jul 17 07:06:51 bigbox kernel: [  132.265164] ata1: EH complete
Jul 17 07:06:51 bigbox kernel: [  132.265274] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:06:53 bigbox kernel: [  134.315087]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:53 bigbox kernel: [  134.337748] ata1.00: configured for UDMA/100
Jul 17 07:06:53 bigbox kernel: [  134.337769] ata1: EH complete
Jul 17 07:06:55 bigbox kernel: [  136.387174]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:55 bigbox kernel: [  136.410495] ata1.00: configured for UDMA/100
Jul 17 07:06:55 bigbox kernel: [  136.410518] ata1: EH complete
Jul 17 07:06:57 bigbox kernel: [  138.470278]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:57 bigbox kernel: [  138.491195] ata1.00: configured for UDMA/100
Jul 17 07:06:57 bigbox kernel: [  138.491215] ata1: EH complete
Jul 17 07:06:59 bigbox kernel: [  140.542387]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:06:59 bigbox kernel: [  140.563919] ata1.00: configured for UDMA/100
Jul 17 07:06:59 bigbox kernel: [  140.563937] ata1: EH complete
Jul 17 07:07:01 bigbox kernel: [  142.614474]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:07:01 bigbox kernel: [  142.636665] ata1.00: configured for UDMA/100
Jul 17 07:07:01 bigbox kernel: [  142.636679] ata1: EH complete
Jul 17 07:07:03 bigbox kernel: [  144.686568]          res 51/40:00:d2:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:07:03 bigbox kernel: [  144.709394] ata1.00: configured for UDMA/100
Jul 17 07:07:03 bigbox kernel: [  144.709415] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:07:03 bigbox kernel: [  144.709421] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:07:03 bigbox kernel: [  144.709428] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:07:03 bigbox kernel: [  144.709432]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:07:03 bigbox kernel: [  144.709446]         00 ef bd d2 
Jul 17 07:07:03 bigbox kernel: [  144.709451] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:07:03 bigbox kernel: [  144.709460] end_request: I/O error, dev sda, sector 15711698
Jul 17 07:07:03 bigbox kernel: [  144.709658] ata1: EH complete
Jul 17 07:07:03 bigbox kernel: [  144.710138] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:07:03 bigbox kernel: [  144.745208] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:07:03 bigbox kernel: [  144.745677] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:07:03 bigbox kernel: [  144.745893] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:07:03 bigbox kernel: [  144.777083] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:07:03 bigbox kernel: [  144.852639] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jul 17 07:07:03 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 17 07:07:04 bigbox kernel: [  145.323355] Bluetooth: Core ver 2.11
Jul 17 07:07:04 bigbox kernel: [  145.326111] NET: Registered protocol family 31
Jul 17 07:07:04 bigbox kernel: [  145.326118] Bluetooth: HCI device and connection manager initialized
Jul 17 07:07:04 bigbox kernel: [  145.326124] Bluetooth: HCI socket layer initialized
Jul 17 07:07:04 bigbox kernel: [  145.628390] Bluetooth: L2CAP ver 2.9
Jul 17 07:07:04 bigbox kernel: [  145.628397] Bluetooth: L2CAP socket layer initialized
Jul 17 07:07:04 bigbox kernel: [  145.690423] Bluetooth: RFCOMM socket layer initialized
Jul 17 07:07:04 bigbox kernel: [  145.690449] Bluetooth: RFCOMM TTY layer initialized
Jul 17 07:07:04 bigbox kernel: [  145.690453] Bluetooth: RFCOMM ver 1.8
Jul 17 07:07:06 bigbox kernel: [  147.820243] NET: Registered protocol family 17
Jul 17 07:07:08 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 17 07:07:08 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 17 07:07:08 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 17 07:07:08 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 17 07:07:08 bigbox dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 17 07:07:08 bigbox kernel: [  149.457912] [drm] Initialized drm 1.1.0 20060810
Jul 17 07:07:08 bigbox kernel: [  149.464950] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Jul 17 07:07:08 bigbox kernel: [  149.465085] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul 17 07:07:09 bigbox kernel: [  150.642060] NET: Registered protocol family 10
Jul 17 07:07:09 bigbox kernel: [  150.643352] lo: Disabled Privacy Extensions
Jul 17 07:26:20 bigbox -- MARK --
Jul 17 07:41:04 bigbox syslogd 1.5.0#1ubuntu1: restart.
Jul 17 07:41:45 bigbox kernel: [ 2224.247869] audit(1216294905.912:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7754 profile="/usr/sbin/cupsd" namespace="default"
Jul 17 07:43:48 bigbox kernel: [ 2346.700813] end_request: I/O error, dev fd0, sector 0
Jul 17 07:43:48 bigbox kernel: [ 2346.732753] end_request: I/O error, dev fd0, sector 0
Jul 17 07:43:50 bigbox kernel: [ 2349.114807]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:43:51 bigbox kernel: [ 2349.169531] ata1.00: configured for UDMA/100
Jul 17 07:43:51 bigbox kernel: [ 2349.169564] ata1: EH complete
Jul 17 07:43:53 bigbox kernel: [ 2351.230988]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:43:53 bigbox kernel: [ 2351.254360] ata1.00: configured for UDMA/100
Jul 17 07:43:53 bigbox kernel: [ 2351.254393] ata1: EH complete
Jul 17 07:43:55 bigbox kernel: [ 2353.314551]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:43:55 bigbox kernel: [ 2353.339964] ata1.00: configured for UDMA/100
Jul 17 07:43:55 bigbox kernel: [ 2353.339999] ata1: EH complete
Jul 17 07:43:57 bigbox kernel: [ 2355.397250]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:43:57 bigbox kernel: [ 2355.419493] ata1.00: configured for UDMA/100
Jul 17 07:43:57 bigbox kernel: [ 2355.419536] ata1: EH complete
Jul 17 07:43:59 bigbox kernel: [ 2357.480554]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:43:59 bigbox kernel: [ 2357.504436] ata1.00: configured for UDMA/100
Jul 17 07:43:59 bigbox kernel: [ 2357.504472] ata1: EH complete
Jul 17 07:44:01 bigbox kernel: [ 2359.563480]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:01 bigbox kernel: [ 2359.584903] ata1.00: configured for UDMA/100
Jul 17 07:44:01 bigbox kernel: [ 2359.584939] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:44:01 bigbox kernel: [ 2359.584945] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:44:01 bigbox kernel: [ 2359.584953] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:44:01 bigbox kernel: [ 2359.584956]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:44:01 bigbox kernel: [ 2359.584970]         00 ef bd d0 
Jul 17 07:44:01 bigbox kernel: [ 2359.584976] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:44:01 bigbox kernel: [ 2359.584986] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:44:01 bigbox kernel: [ 2359.585023] ata1: EH complete
Jul 17 07:44:03 bigbox kernel: [ 2361.647856]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:03 bigbox kernel: [ 2361.670914] ata1.00: configured for UDMA/100
Jul 17 07:44:03 bigbox kernel: [ 2361.670948] ata1: EH complete
Jul 17 07:44:05 bigbox kernel: [ 2363.729744]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:05 bigbox kernel: [ 2363.763674] ata1.00: configured for UDMA/100
Jul 17 07:44:05 bigbox kernel: [ 2363.763703] ata1: EH complete
Jul 17 07:44:07 bigbox kernel: [ 2365.825133]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:07 bigbox kernel: [ 2365.848640] ata1.00: configured for UDMA/100
Jul 17 07:44:07 bigbox kernel: [ 2365.848675] ata1: EH complete
Jul 17 07:44:09 bigbox kernel: [ 2367.907007]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:09 bigbox kernel: [ 2367.923753] ata1.00: configured for UDMA/100
Jul 17 07:44:09 bigbox kernel: [ 2367.923793] ata1: EH complete
Jul 17 07:44:11 bigbox kernel: [ 2369.979177]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:11 bigbox kernel: [ 2370.000466] ata1.00: configured for UDMA/100
Jul 17 07:44:11 bigbox kernel: [ 2370.000502] ata1: EH complete
Jul 17 07:44:13 bigbox kernel: [ 2372.051235]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:13 bigbox kernel: [ 2372.073193] ata1.00: configured for UDMA/100
Jul 17 07:44:13 bigbox kernel: [ 2372.073232] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:44:13 bigbox kernel: [ 2372.073239] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:44:13 bigbox kernel: [ 2372.073246] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:44:13 bigbox kernel: [ 2372.073250]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:44:13 bigbox kernel: [ 2372.073264]         00 ef bd d4 
Jul 17 07:44:13 bigbox kernel: [ 2372.073270] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:44:13 bigbox kernel: [ 2372.073279] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:44:13 bigbox kernel: [ 2372.073323] ata1: EH complete
Jul 17 07:44:13 bigbox kernel: [ 2372.073528] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:44:13 bigbox kernel: [ 2372.074184] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:44:51 bigbox kernel: [ 2372.078087] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:44:51 bigbox kernel: [ 2374.189473]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2374.230029] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2374.230060] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2376.284913]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2376.308015] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2376.308044] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2378.366759]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2378.393613] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2378.393644] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2380.449871]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2380.463933] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2380.463968] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2382.521964]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2382.536978] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2382.537009] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2384.595134]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2384.613404] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2384.613444] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:44:51 bigbox kernel: [ 2384.613451] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:44:51 bigbox kernel: [ 2384.613458] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:44:51 bigbox kernel: [ 2384.613462]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:44:51 bigbox kernel: [ 2384.613476]         00 ef bd d0 
Jul 17 07:44:51 bigbox kernel: [ 2384.613484] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:44:51 bigbox kernel: [ 2384.613493] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:44:51 bigbox kernel: [ 2384.613543] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2386.666158]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2386.682436] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2386.682468] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2388.738253]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2388.754797] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2388.754818] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2390.810355]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2390.831517] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2390.831538] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2392.882457]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2392.904247] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2392.904267] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2394.954559]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2394.976977] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2394.976999] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2397.026664]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2397.049707] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2397.049731] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:44:51 bigbox kernel: [ 2397.049736] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:44:51 bigbox kernel: [ 2397.049743] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:44:51 bigbox kernel: [ 2397.049746]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:44:51 bigbox kernel: [ 2397.049760]         00 ef bd d0 
Jul 17 07:44:51 bigbox kernel: [ 2397.049765] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:44:51 bigbox kernel: [ 2397.049774] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:44:51 bigbox kernel: [ 2397.049802] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2397.049917] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:44:51 bigbox kernel: [ 2399.109771]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2399.130417] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2399.130432] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2401.181875]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2401.203145] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2401.203161] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2403.253980]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2403.275873] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2403.275890] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2405.326082]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2405.348601] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2405.348617] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2407.398205]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2407.421327] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2407.421349] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2409.481328]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:51 bigbox kernel: [ 2409.502053] ata1.00: configured for UDMA/100
Jul 17 07:44:51 bigbox kernel: [ 2409.502076] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:44:51 bigbox kernel: [ 2409.502081] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:44:51 bigbox kernel: [ 2409.502089] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:44:51 bigbox kernel: [ 2409.502092]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:44:51 bigbox kernel: [ 2409.502106]         00 ef bd d4 
Jul 17 07:44:51 bigbox kernel: [ 2409.502111] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:44:51 bigbox kernel: [ 2409.502120] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:44:51 bigbox kernel: [ 2409.502149] ata1: EH complete
Jul 17 07:44:51 bigbox kernel: [ 2409.502373] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:44:51 bigbox kernel: [ 2409.533542] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:44:51 bigbox kernel: [ 2409.564857] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:44:51 bigbox kernel: [ 2409.576044] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:44:51 bigbox kernel: [ 2409.596859] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:44:53 bigbox kernel: [ 2411.784927]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:53 bigbox kernel: [ 2411.806425] ata1.00: configured for UDMA/100
Jul 17 07:44:53 bigbox kernel: [ 2411.806443] ata1: EH complete
Jul 17 07:44:55 bigbox kernel: [ 2413.857013]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:55 bigbox kernel: [ 2413.879153] ata1.00: configured for UDMA/100
Jul 17 07:44:55 bigbox kernel: [ 2413.879176] ata1: EH complete
Jul 17 07:44:57 bigbox kernel: [ 2415.929116]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:44:57 bigbox kernel: [ 2415.951882] ata1.00: configured for UDMA/100
Jul 17 07:44:57 bigbox kernel: [ 2415.951907] ata1: EH complete
Jul 17 07:44:59 bigbox kernel: [ 2418.012241]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:00 bigbox kernel: [ 2418.036613] ata1.00: configured for UDMA/100
Jul 17 07:45:00 bigbox kernel: [ 2418.036645] ata1: EH complete
Jul 17 07:45:02 bigbox kernel: [ 2420.095365]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:02 bigbox kernel: [ 2420.117286] ata1.00: configured for UDMA/100
Jul 17 07:45:02 bigbox kernel: [ 2420.117309] ata1: EH complete
Jul 17 07:45:04 bigbox kernel: [ 2422.167469]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:04 bigbox kernel: [ 2422.190013] ata1.00: configured for UDMA/100
Jul 17 07:45:04 bigbox kernel: [ 2422.190039] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:45:04 bigbox kernel: [ 2422.190045] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:45:04 bigbox kernel: [ 2422.190053] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:45:04 bigbox kernel: [ 2422.190056]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:45:04 bigbox kernel: [ 2422.190071]         00 ef bd d0 
Jul 17 07:45:04 bigbox kernel: [ 2422.190077] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:45:04 bigbox kernel: [ 2422.190086] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:45:04 bigbox kernel: [ 2422.190130] ata1: EH complete
Jul 17 07:45:04 bigbox kernel: [ 2422.190188] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:45:04 bigbox kernel: [ 2422.190214] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:45:04 bigbox kernel: [ 2422.190250] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:45:04 bigbox kernel: [ 2422.190285] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:45:04 bigbox kernel: [ 2422.190304] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:45:04 bigbox kernel: [ 2422.190337] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:45:06 bigbox kernel: [ 2424.250572]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:06 bigbox kernel: [ 2424.274742] ata1.00: configured for UDMA/100
Jul 17 07:45:06 bigbox kernel: [ 2424.274761] ata1: EH complete
Jul 17 07:45:08 bigbox kernel: [ 2426.333697]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:08 bigbox kernel: [ 2426.355438] ata1.00: configured for UDMA/100
Jul 17 07:45:08 bigbox kernel: [ 2426.355463] ata1: EH complete
Jul 17 07:45:10 bigbox kernel: [ 2428.405807]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:10 bigbox kernel: [ 2428.428166] ata1.00: configured for UDMA/100
Jul 17 07:45:10 bigbox kernel: [ 2428.428191] ata1: EH complete
Jul 17 07:45:12 bigbox kernel: [ 2430.477903]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:12 bigbox kernel: [ 2430.500894] ata1.00: configured for UDMA/100
Jul 17 07:45:12 bigbox kernel: [ 2430.500918] ata1: EH complete
Jul 17 07:45:14 bigbox kernel: [ 2432.561034]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:14 bigbox kernel: [ 2432.585603] ata1.00: configured for UDMA/100
Jul 17 07:45:14 bigbox kernel: [ 2432.585626] ata1: EH complete
Jul 17 07:45:16 bigbox kernel: [ 2434.644157]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:16 bigbox kernel: [ 2434.666324] ata1.00: configured for UDMA/100
Jul 17 07:45:16 bigbox kernel: [ 2434.666349] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:45:16 bigbox kernel: [ 2434.666355] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:45:16 bigbox kernel: [ 2434.666362] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:45:16 bigbox kernel: [ 2434.666366]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:45:16 bigbox kernel: [ 2434.666380]         00 ef bd d0 
Jul 17 07:45:16 bigbox kernel: [ 2434.666385] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:45:16 bigbox kernel: [ 2434.666394] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:45:16 bigbox kernel: [ 2434.666431] ata1: EH complete
Jul 17 07:45:16 bigbox kernel: [ 2434.689956] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:45:16 bigbox kernel: [ 2434.690165] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:45:16 bigbox kernel: [ 2434.715802] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:45:16 bigbox kernel: [ 2434.733412] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:45:16 bigbox kernel: [ 2434.749040] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:45:16 bigbox kernel: [ 2434.764021] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:45:18 bigbox kernel: [ 2436.849455]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:19 bigbox kernel: [ 2437.142444] ata1.00: configured for UDMA/100
Jul 17 07:45:19 bigbox kernel: [ 2437.142479] ata1: EH complete
Jul 17 07:45:21 bigbox kernel: [ 2439.196177]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:21 bigbox kernel: [ 2439.223420] ata1.00: configured for UDMA/100
Jul 17 07:45:21 bigbox kernel: [ 2439.223458] ata1: EH complete
Jul 17 07:45:23 bigbox kernel: [ 2441.279314]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:23 bigbox kernel: [ 2441.304256] ata1.00: configured for UDMA/100
Jul 17 07:45:23 bigbox kernel: [ 2441.304302] ata1: EH complete
Jul 17 07:45:25 bigbox kernel: [ 2443.362434]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:25 bigbox kernel: [ 2443.384905] ata1.00: configured for UDMA/100
Jul 17 07:45:25 bigbox kernel: [ 2443.384943] ata1: EH complete
Jul 17 07:45:27 bigbox kernel: [ 2445.434535]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:27 bigbox kernel: [ 2445.449316] ata1.00: configured for UDMA/100
Jul 17 07:45:27 bigbox kernel: [ 2445.449351] ata1: EH complete
Jul 17 07:45:29 bigbox kernel: [ 2447.506641]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:29 bigbox kernel: [ 2447.530084] ata1.00: configured for UDMA/100
Jul 17 07:45:29 bigbox kernel: [ 2447.530127] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:45:29 bigbox kernel: [ 2447.530133] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:45:29 bigbox kernel: [ 2447.530141] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:45:29 bigbox kernel: [ 2447.530144]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:45:29 bigbox kernel: [ 2447.530159]         00 ef bd d4 
Jul 17 07:45:29 bigbox kernel: [ 2447.530165] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:45:29 bigbox kernel: [ 2447.530174] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:45:29 bigbox kernel: [ 2447.530230] ata1: EH complete
Jul 17 07:45:31 bigbox kernel: [ 2449.589769]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:31 bigbox kernel: [ 2449.611146] ata1.00: configured for UDMA/100
Jul 17 07:45:31 bigbox kernel: [ 2449.611185] ata1: EH complete
Jul 17 07:45:33 bigbox kernel: [ 2451.661871]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:33 bigbox kernel: [ 2451.684410] ata1.00: configured for UDMA/100
Jul 17 07:45:33 bigbox kernel: [ 2451.684442] ata1: EH complete
Jul 17 07:45:35 bigbox kernel: [ 2453.733980]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:35 bigbox kernel: [ 2453.756445] ata1.00: configured for UDMA/100

Jul 17 07:45:35 bigbox kernel: [ 2453.756483] ata1: EH complete
Jul 17 07:45:37 bigbox kernel: [ 2455.817102]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:37 bigbox kernel: [ 2455.840955] ata1.00: configured for UDMA/100
Jul 17 07:45:37 bigbox kernel: [ 2455.840989] ata1: EH complete
Jul 17 07:45:39 bigbox kernel: [ 2457.900224]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:39 bigbox kernel: [ 2457.922016] ata1.00: configured for UDMA/100
Jul 17 07:45:39 bigbox kernel: [ 2457.922058] ata1: EH complete
Jul 17 07:45:42 bigbox kernel: [ 2459.972330]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:42 bigbox kernel: [ 2459.995125] ata1.00: configured for UDMA/100
Jul 17 07:45:42 bigbox kernel: [ 2459.995161] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:45:42 bigbox kernel: [ 2459.995167] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:45:42 bigbox kernel: [ 2459.995174] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:45:42 bigbox kernel: [ 2459.995178]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:45:42 bigbox kernel: [ 2459.995192]         00 ef bd d0 
Jul 17 07:45:42 bigbox kernel: [ 2459.995198] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:45:42 bigbox kernel: [ 2459.995207] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:45:42 bigbox kernel: [ 2459.995243] ata1: EH complete
Jul 17 07:45:42 bigbox kernel: [ 2459.995351] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:45:44 bigbox kernel: [ 2462.055452]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:44 bigbox kernel: [ 2462.079556] ata1.00: configured for UDMA/100
Jul 17 07:45:44 bigbox kernel: [ 2462.079600] ata1: EH complete
Jul 17 07:45:46 bigbox kernel: [ 2464.138575]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:46 bigbox kernel: [ 2464.160057] ata1.00: configured for UDMA/100
Jul 17 07:45:46 bigbox kernel: [ 2464.160097] ata1: EH complete
Jul 17 07:45:48 bigbox kernel: [ 2466.210687]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:48 bigbox kernel: [ 2466.232603] ata1.00: configured for UDMA/100
Jul 17 07:45:48 bigbox kernel: [ 2466.232655] ata1: EH complete
Jul 17 07:45:50 bigbox kernel: [ 2468.282783]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:50 bigbox kernel: [ 2468.309030] ata1.00: configured for UDMA/100
Jul 17 07:45:50 bigbox kernel: [ 2468.309062] ata1: EH complete
Jul 17 07:45:52 bigbox kernel: [ 2470.365915]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:52 bigbox kernel: [ 2470.390198] ata1.00: configured for UDMA/100
Jul 17 07:45:52 bigbox kernel: [ 2470.390230] ata1: EH complete
Jul 17 07:45:54 bigbox kernel: [ 2472.450116]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:45:54 bigbox kernel: [ 2472.474705] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2472.474745] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2472.474751] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2472.474759] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2472.474762]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2472.474776]         00 ef bd d4 
Jul 17 07:47:09 bigbox kernel: [ 2472.474782] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2472.474791] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:47:09 bigbox kernel: [ 2472.474832] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2472.475125] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2472.476554] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2474.576265]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2474.615510] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2474.615557] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2476.670423]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2476.688051] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2476.688084] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2478.742518]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2478.756768] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2478.756804] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2480.814625]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2480.829502] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2480.829539] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2482.887399]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2482.902300] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2482.902349] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2484.958802]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2484.976741] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2484.976776] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2484.976783] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2484.976790] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2484.976794]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2484.976807]         00 ef bd d0 
Jul 17 07:47:09 bigbox kernel: [ 2484.976814] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2484.976823] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:47:09 bigbox kernel: [ 2484.976868] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2487.030910]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2487.052623] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2487.052656] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2489.103021]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2489.120418] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2489.120453] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2491.175124]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2491.193151] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2491.193185] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2493.247223]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2493.262658] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2493.262690] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2495.321141]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2495.338800] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2495.338837] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2497.391436]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2497.401324] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2497.401358] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2497.401365] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2497.401375] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2497.401378]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2497.401392]         00 ef bd d0 
Jul 17 07:47:09 bigbox kernel: [ 2497.401399] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2497.401407] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:47:09 bigbox kernel: [ 2497.401441] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2497.403044] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2499.452515]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2499.468095] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2499.468128] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2501.524811]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2501.541018] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2501.541055] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2503.598639]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2503.617712] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2503.617749] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2505.668820]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2505.686285] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2505.686321] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2507.740919]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2507.757215] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2507.757248] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2509.813030]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2509.828015] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2509.828052] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2509.828059] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2509.828066] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2509.828070]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2509.828084]         00 ef bd d4 
Jul 17 07:47:09 bigbox kernel: [ 2509.828090] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2509.828099] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:47:09 bigbox kernel: [ 2509.828137] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2509.829821] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2509.868260] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2509.868571] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2509.868593] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2509.868628] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2511.995365]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2512.012234] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2512.012251] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2514.067459]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2514.088940] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2514.088961] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2516.139560]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2516.161664] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2516.161684] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2518.211663]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2518.234403] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2518.234431] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2520.283767]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2520.307119] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2520.307140] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2522.366898]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2522.387853] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2522.387877] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2522.387882] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2522.387890] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2522.387893]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2522.387907]         00 ef bd d0 
Jul 17 07:47:09 bigbox kernel: [ 2522.387912] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2522.387921] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:47:09 bigbox kernel: [ 2522.387961] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2522.407958] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2522.408178] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2522.408219] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2522.408255] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2522.408274] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2522.408308] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2524.450005]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2524.472550] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2524.472565] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2526.522107]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2526.545274] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2526.545295] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2528.605233]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2528.625987] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2528.626009] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2530.677336]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2530.698714] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2530.698736] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2532.749433]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2532.771443] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2532.771464] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2534.821545]          res 51/40:00:d0:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2534.844251] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2534.844274] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2534.844279] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2534.844286] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2534.844290]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2534.844304]         00 ef bd d0 
Jul 17 07:47:09 bigbox kernel: [ 2534.844309] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2534.844318] end_request: I/O error, dev sda, sector 15711696
Jul 17 07:47:09 bigbox kernel: [ 2534.844346] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2534.860299] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2534.860326] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2534.860363] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2534.860398] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2534.860416] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2534.860450] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2537.059083]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2537.124595] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2537.124609] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2539.175243]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2539.193321] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2539.193332] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2541.247358]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2541.262044] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2541.262060] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2543.319449]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2543.334773] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2543.334786] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2545.391551]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2545.415480] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2545.415491] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2547.474688]          res 51/40:00:d4:bd:ef/00:00:00:00:00/e0 Emask 0x9 (media error)
Jul 17 07:47:09 bigbox kernel: [ 2547.492204] ata1.00: configured for UDMA/100
Jul 17 07:47:09 bigbox kernel: [ 2547.492221] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 17 07:47:09 bigbox kernel: [ 2547.492228] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul 17 07:47:09 bigbox kernel: [ 2547.492235] Descriptor sense data with sense descriptors (in hex):
Jul 17 07:47:09 bigbox kernel: [ 2547.492238]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul 17 07:47:09 bigbox kernel: [ 2547.492252]         00 ef bd d4 
Jul 17 07:47:09 bigbox kernel: [ 2547.492258] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2547.492267] end_request: I/O error, dev sda, sector 15711700
Jul 17 07:47:09 bigbox kernel: [ 2547.492345] ata1: EH complete
Jul 17 07:47:09 bigbox kernel: [ 2547.511878] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2547.538391] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2547.553381] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:09 bigbox kernel: [ 2547.554020] sd 0:0:0:0: [sda] 39062500 512-byte hardware sectors (20000 MB)
Jul 17 07:47:09 bigbox kernel: [ 2547.554363] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 07:47:09 bigbox kernel: [ 2547.554909] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 07:47:26 bigbox pulseaudio[7970]: pid.c: Stale PID file, overwriting.
Jul 17 08:07:39 bigbox -- MARK --
Jul 17 08:27:39 bigbox -- MARK --

```

Any help would be great.

---

### Post by hal8000 on 2008-07-17
Does Ubuntu boot and reach the desktop, or are you returned to a login shell?
If yes the file system gets checked automatically every several reboots, and should repair any errors.
If you are logging in to a command prompt then it may be necessary to run
fsck.ext3 manually.

---

### Post by toucher5 on 2008-07-31
no the only way I can do anything is by live cd.:confused:

---

### Post by articpenguin on 2008-07-31
I dont think your ext3 partition is corrupted because it would say recovering journal or filesystem needs recovery on boot.

I did notice 
47.492258] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul 17 07:47:09 bigbox kernel: [ 2547.492267] end_request: I/O error, dev sda, sector 15711700

Seems your harddrive has a bad sector. do you have access to smart or something?

Try running this from the terminal and post what you get

> sudo smartctl -a /dev/sda1

---


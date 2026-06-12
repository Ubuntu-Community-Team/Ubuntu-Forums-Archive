---
title: "Boot freezes w/o ac adapter"
date: 2008-04-29
forum: Hardware
---

### Post by guruofquality on 2008-04-29
Hey,

I have a crazy problem. I just updated my sisters laptop to hardy. Its your run-of-the-mill 32bit toshiba satellite laptop. (Satellite L35 - S2366) 

Basically, when the ac adapter is not plugged in, ie battery power, the laptop freezes at boot. It gets to the grub menu, kernel seems to be loading, and it freezes with the message on the screen:

Starting up...
Loading, please wait...

Or sometimes it gets to the splash screen, and then goes to this black screen and freezes with this message:

* Reading files needed to boot... [ OK ]
* Preparing restricted drivers... [ OK ]
* Setting the system clock
* Starting basic networking...

It always freezes with one of those messages, unless its on ac power. I tried adding noapic to the kernel options but that seemed to make the kernel unbootable even with the ac adapter plugged in. 

Any idea? Any more kernel options to try?

---

### Post by guruofquality on 2008-05-01
The solution was to install windows XP.

---

### Post by guruofquality on 2008-05-16
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[    0.000000]  BIOS-e820: 000000001be80000 - 000000001be96000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001be96000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7130
[    0.000000] Entering add_active_range(0, 0, 114304) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114304
[    0.000000]   HighMem    114304 ->   114304
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114304
[    0.000000] On node 0 totalpages: 114304
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109347 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7070 checksum 0
[    0.000000] ACPI: RSDP 000F7070, 0014 (r0 TOSQCI)
[    0.000000] ACPI: RSDT 1BE8F523, 0038 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: FACP 1BE95D7C, 0074 (r1 ATI    Bonefish  6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1BE8FF80, 5DFC (r1 TOSQCI L10       6040000 MSFT  2000002)
[    0.000000] ACPI: FACS 1BE96FC0, 0040
[    0.000000] ACPI: APIC 1BE95DF0, 005E (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 1BE95E4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 1BE95E8A, 0176 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: SSDT 1BE8F55B, 0535 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:c4000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113411
[    0.000000] Kernel command line: root=UUID=8b4a7a13-2a9e-4a5c-a666-c57236eb5152 ro single
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1600.011 MHz processor.
[  183.577167] Console: colour VGA+ 80x25
[  183.577172] console [tty0] enabled
[  183.580833] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  183.581236] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  183.593346] Memory: 440860k/457216k available (2157k kernel code, 15816k reserved, 998k data, 364k init, 0k highmem)
[  183.593415] virtual kernel memory layout:
[  183.593416]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[  183.593418]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  183.593419]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[  183.593420]     lowmem  : 0xc0000000 - 0xdbe80000   ( 446 MB)
[  183.593422]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[  183.593423]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[  183.593425]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[  183.593798] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  183.593928] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[  183.673890] Calibrating delay using timer specific routine.. 3204.97 BogoMIPS (lpj=6409942)
[  183.674009] Security Framework initialized
[  183.674063] SELinux:  Disabled at boot.
[  183.674125] AppArmor: AppArmor initialized
[  183.674174] Failure registering capabilities with primary security module.
[  183.674231] Mount-cache hash table entries: 512
[  183.674414] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[  183.674424] monitor/mwait feature present.
[  183.674473] using mwait in idle threads.
[  183.674524] CPU: L1 I cache: 32K, L1 D cache: 32K
[  183.674609] CPU: L2 cache: 1024K
[  183.674656] CPU: Physical Processor ID: 0
[  183.674703] CPU: Processor Core ID: 0
[  183.674749] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000 00000000
[  183.674759] Compat vDSO mapped to ffffe000.
[  183.674818] Checking 'hlt' instruction... OK.
[  183.690355] SMP alternatives: switching to UP code
[  183.692434] Early unpacking initramfs... done
[  184.089820] ACPI: Core revision 20070126
[  184.089943] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  184.794074] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[  184.794264] SMP alternatives: switching to SMP code
[  184.795145] Booting processor 1/1 eip 3000
[  184.805439] Initializing CPU#1
[  184.884045] Calibrating delay using timer specific routine.. 3200.27 BogoMIPS (lpj=6400550)
[  184.884054] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[  184.884060] monitor/mwait feature present.
[  184.884064] CPU: L1 I cache: 32K, L1 D cache: 32K
[  184.884067] CPU: L2 cache: 1024K
[  184.884069] CPU: Physical Processor ID: 0
[  184.884071] CPU: Processor Core ID: 1
[  184.884073] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000 00000000
[  184.884601] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[  184.885115] Total of 2 processors activated (6405.24 BogoMIPS).
[  184.885342] ENABLING IO-APIC IRQs
[  184.885591] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[  185.031975] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[  185.052059] Brought up 2 CPUs
[  185.052130] CPU0 attaching sched-domain:
[  185.052133]  domain 0: span 03
[  185.052135]   groups: 01 02
[  185.052139] CPU1 attaching sched-domain:
[  185.052141]  domain 0: span 03
[  185.052142]   groups: 02 01
[  185.052473] net_namespace: 64 bytes
[  185.052529] Booting paravirtualized kernel on bare hardware
[  185.053147] Time:  3:57:29  Date: 05/16/08
[  185.053225] NET: Registered protocol family 16
[  185.053569] EISA bus registered
[  185.053622] ACPI: bus type pci registered
[  185.080919] PCI: PCI BIOS revision 2.10 entry at 0xfd494, last bus=14
[  185.080973] PCI: Using configuration type 1
[  185.081020] Setting up standard PCI resources
[  185.083526] ACPI: EC: Look up EC in DSDT
[  185.086385] ACPI Error (dswload-0664): [\___] Namespace lookup failure, AE_NOT_FOUND
[  185.086522] ACPI Exception (psloop-0225): AE_NOT_FOUND, During name lookup/catalog [20070126]
[  185.086654] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._INI] (Node db0246c0), AE_NOT_FOUND
[  185.086872] ACPI: Interpreter enabled
[  185.086923] ACPI: (supports S0 S3 S4 S5)
[  185.087130] ACPI: Using IOAPIC for interrupt routing
[  185.169271] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[  185.169328] ACPI: EC: driver started in poll mode
[  185.169440] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  185.170922] PCI: Transparent bridge - 0000:00:14.4
[  185.171069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  185.171324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[  185.171458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[  185.173679] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[  185.174069] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[  185.174456] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[  185.174848] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[  185.175236] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[  185.175628] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[  185.176016] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[  185.176403] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[  185.176826] Linux Plug and Play Support v0.97 (c) Adam Belay
[  185.176916] pnp: PnP ACPI init
[  185.176971] ACPI: bus type pnp registered
[  185.178898] pnp: PnP ACPI: found 10 devices
[  185.178950] ACPI: ACPI bus type pnp unregistered
[  185.178999] PnPBIOS: Disabled by ACPI PNP
[  185.179392] PCI: Using ACPI for IRQ routing
[  185.179443] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  185.239529] NET: Registered protocol family 8
[  185.239579] NET: Registered protocol family 20
[  185.239715] AppArmor: AppArmor Filesystem Enabled
[  185.243514] Time: tsc clocksource has been installed.
[  185.255786] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[  185.255853] system 00:08: ioport range 0x1080-0x1080 has been reserved
[  185.255903] system 00:08: ioport range 0x200-0x20f has been reserved
[  185.255953] system 00:08: ioport range 0x40b-0x40b has been reserved
[  185.256003] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[  185.256052] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[  185.256102] system 00:08: ioport range 0x530-0x537 has been reserved
[  185.256152] system 00:08: ioport range 0xc00-0xc01 has been reserved
[  185.256201] system 00:08: ioport range 0xc14-0xc14 has been reserved
[  185.256251] system 00:08: ioport range 0xc50-0xc52 has been reserved
[  185.256300] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[  185.256350] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[  185.256400] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[  185.256449] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[  185.256499] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[  185.256549] system 00:08: ioport range 0x8000-0x805f could not be reserved
[  185.257103] system 00:08: ioport range 0x8210-0x821f has been reserved
[  185.257153] system 00:08: ioport range 0xf40-0xf47 has been reserved
[  185.257202] system 00:08: ioport range 0x280-0x293 has been reserved
[  185.257252] system 00:08: ioport range 0x87f-0x87f has been reserved
[  185.257305] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[  185.257356] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[  185.257412] system 00:09: iomem range 0xc0004800-0xc00057ff has been reserved
[  185.257462] system 00:09: iomem range 0x0-0xfff could not be reserved
[  185.288044] PCI: Bridge: 0000:00:01.0
[  185.288093]   IO window: 9000-9fff
[  185.288141]   MEM window: d0000000-d00fffff
[  185.288190]   PREFETCH window: d8000000-dfffffff
[  185.288247] PCI: Bus 10, cardbus bridge: 0000:09:01.0
[  185.288295]   IO window: 0000a400-0000a4ff
[  185.288346]   IO window: 0000a800-0000a8ff
[  185.288397]   PREFETCH window: 24000000-27ffffff
[  185.288449]   MEM window: 28000000-2bffffff
[  185.288501] PCI: Bridge: 0000:00:14.4
[  185.288549]   IO window: a000-afff
[  185.288601]   MEM window: d0100000-d01fffff
[  185.288651]   PREFETCH window: disabled.
[  185.288742] PCI: Enabling device 0000:09:01.0 (0000 -> 0003)
[  185.288796] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 16
[  185.288908] NET: Registered protocol family 2
[  185.335694] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  185.335968] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[  185.336154] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[  185.336332] TCP: Hash tables configured (established 16384 bind 16384)
[  185.336385] TCP reno registered
[  185.347760] checking if image is initramfs... it is
[  185.790694] Switched to high resolution mode on CPU 0
[  185.790912] Switched to high resolution mode on CPU 1
[  186.144271] Freeing initrd memory: 7687k freed
[  186.145571] audit: initializing netlink socket (disabled)
[  186.145642] audit(1210910249.732:1): initialized
[  186.148599] VFS: Disk quotas dquot_6.5.1
[  186.148759] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  186.148995] io scheduler noop registered
[  186.149046] io scheduler anticipatory registered
[  186.149093] io scheduler deadline registered
[  186.149151] io scheduler cfq registered (default)
[  186.149261] Boot video device is 0000:01:05.0
[  186.149664] isapnp: Scanning for PnP cards...
[  186.506583] isapnp: No Plug & Play device found
[  186.543469] Real Time Clock Driver v1.12ac
[  186.543677] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  186.545318] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  186.545474] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[  186.545658] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[  186.549079] serio: i8042 KBD port at 0x60,0x64 irq 1
[  186.549132] serio: i8042 AUX port at 0x60,0x64 irq 12
[  186.565512] mice: PS/2 mouse device common for all mice
[  186.565723] EISA: Probing bus 0 at eisa.0
[  186.565781] Cannot allocate resource for EISA slot 1
[  186.565860] Cannot allocate resource for EISA slot 8
[  186.565908] EISA: Detected 0 cards.
[  186.565956] cpuidle: using governor ladder
[  186.566003] cpuidle: using governor menu
[  186.566165] NET: Registered protocol family 1
[  186.566247] Using IPI No-Shortcut mode
[  186.566332] registered taskstats version 1
[  186.566506]   Magic number: 8:951:967
[  186.566568]   hash matches device ttyb8
[  186.566763] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[  186.566814] EDD information not available.
[  186.567231] Freeing unused kernel memory: 364k freed
[  186.598119] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[  186.777610] fuse init (API version 7.9)
[  186.802485] ACPI: SSDT 1BE8FD11, 01E8 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[  186.803405] ACPI: SSDT 1BE8FA90, 01FC (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[  186.803887] ACPI: Processor [CPU0] (supports 8 throttling states)
[  186.804250] ACPI: SSDT 1BE8FEF9, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[  186.804572] ACPI: SSDT 1BE8FC8C, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[  186.805038] ACPI: Processor [CPU1] (supports 8 throttling states)
[  186.812891] ACPI: EC: non-query interrupt received, switching to interrupt mode
[  186.819261] ACPI: Thermal Zone [THRM] (57 C)
[  187.205608] usbcore: registered new interface driver usbfs
[  187.205708] usbcore: registered new interface driver hub
[  187.206919] SCSI subsystem initialized
[  187.215934] usbcore: registered new device driver usb
[  187.231762] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  187.231840] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[  187.231972] ohci_hcd 0000:00:13.0: OHCI Host Controller
[  187.232445] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[  187.232553] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd0404000
[  187.256304] libata version 3.00 loaded.
[  187.288386] usb usb1: configuration #1 chosen from 1 choice
[  187.288473] hub 1-0:1.0: USB hub found
[  187.288530] hub 1-0:1.0: 4 ports detected
[  187.291342] 8139too Fast Ethernet driver 0.9.28
[  187.392191] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[  187.392320] ohci_hcd 0000:00:13.1: OHCI Host Controller
[  187.392403] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[  187.392481] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd0405000
[  187.448131] usb usb2: configuration #1 chosen from 1 choice
[  187.448229] hub 2-0:1.0: USB hub found
[  187.448293] hub 2-0:1.0: 4 ports detected
[  187.551992] sata_sil 0000:00:12.0: version 2.3
[  187.552023] ACPI: PCI Interrupt 0000:09:02.0[A] -> PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[  187.552086] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[  187.552238] GSI 21 (level, low) -> IRQ 21
[  187.552497] scsi0 : sata_sil
[  187.552737] scsi1 : sata_sil
[  187.553134] ata1: SATA max UDMA/100 mmio m512@0xd0407000 tf 0xd0407080 irq 18
[  187.553327] ata2: SATA max UDMA/100 mmio m512@0xd0407000 tf 0xd04070c0 irq 18
[  187.553704] eth0: RealTek RTL8139 at 0xa000, 00:1b:24:20:b1:b1, IRQ 21
[  187.553764] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[  187.557569] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[  188.019058] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  188.027669] ata1.00: ATA-7: TOSHIBA MK8037GSX, DL230M, max UDMA/100
[  188.027720] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[  188.036647] ata1.00: configured for UDMA/100
[  188.346503] ata2: SATA link down (SStatus 0 SControl 300)
[  188.346755] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8037GS DL23 PQ: 0 ANSI: 5
[  188.347320] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[  188.347452] ehci_hcd 0000:00:13.2: EHCI Host Controller
[  188.347544] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[  188.347661] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0406000
[  188.358477] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  188.358679] usb usb3: configuration #1 chosen from 1 choice
[  188.358764] hub 3-0:1.0: USB hub found
[  188.358825] hub 3-0:1.0: 8 ports detected
[  188.463170] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[  188.463348] PCI: Setting latency timer of device 0000:00:14.1 to 64
[  188.463366] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[  188.468250] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[  188.468494] scsi2 : pata_atiixp
[  188.468612] scsi3 : pata_atiixp
[  188.469062] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[  188.469129] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[  188.469239] ata3: port disabled. ignoring.
[  188.502334] Driver 'sd' needs updating - please use bus_type methods
[  188.503856] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[  188.503927] sd 0:0:0:0: [sda] Write Protect is off
[  188.503976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  188.503997] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  188.504111] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[  188.504173] sd 0:0:0:0: [sda] Write Protect is off
[  188.504221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  188.504240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  188.504299]  sda: sda1 sda2 sda3
[  188.537426] sd 0:0:0:0: [sda] Attached SCSI disk
[  188.543178] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  188.787379] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.10, max UDMA/33
[  188.798655] Attempting manual resume
[  188.798704] swsusp: Resume From Partition 8:1
[  188.798706] PM: Checking swsusp image.
[  188.798948] PM: Resume from disk failed.
[  188.810944] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[  188.811024] ReiserFS: sda2: using ordered data mode
[  188.822473] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  188.823233] ReiserFS: sda2: checking transaction log (sda2)
[  188.849982] ReiserFS: sda2: Using r5 hash to sort names
[  188.962063] ata4.00: configured for UDMA/33
[  188.964056] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.10 PQ: 0 ANSI: 5
[  188.964206] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[  190.047963] WARNING: at /build/buildd/linux-2.6.24/lib/kref.c:33 kref_get()
[  190.048022] Pid: 52, comm: kacpi_notify Not tainted 2.6.24-16-generic #1
[  190.048080]  [<c021185d>] kref_get+0x3d/0x40
[  190.048173]  [<c021098f>] kobject_get+0xf/0x20
[  190.048259]  [<c0210df6>] kobject_add+0x36/0x1b0
[  190.048346]  [<c0211001>] kobject_register+0x21/0x50
[  190.048432]  [<c0290d3c>] cpuidle_add_state_sysfs+0x8c/0x110
[  190.048523]  [<c0235c6f>] acpi_os_execute_notify+0x0/0x2b
[  190.048611]  [<c0290184>] cpuidle_enable_device+0x54/0xd0
[  190.048698]  [<dc869171>] acpi_processor_cst_has_changed+0x40/0x53 [processor]
[  190.048806]  [<dc867798>] acpi_processor_notify+0x8b/0xf4 [processor]
[  190.048897]  [<c0315b5a>] schedule+0x20a/0x600
[  190.048985]  [<c023b3e3>] acpi_ev_notify_dispatch+0x4c/0x55
[  190.049075]  [<c0235c91>] acpi_os_execute_notify+0x22/0x2b
[  190.049176]  [<c013cdbf>] run_workqueue+0xbf/0x160
[  190.049272]  [<c013d860>] worker_thread+0x0/0xe0
[  190.049364]  [<c013d8e4>] worker_thread+0x84/0xe0
[  190.049454]  [<c0140b70>] autoremove_wake_function+0x0/0x40
[  190.049549]  [<c013d860>] worker_thread+0x0/0xe0
[  190.049641]  [<c01408b2>] kthread+0x42/0x70
[  190.049732]  [<c0140870>] kthread+0x0/0x70
[  190.049831]  [<c0105677>] kernel_thread_helper+0x7/0x10
[  190.049930]  =======================
[  190.049990] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000020
[  190.050086] printing eip: c01d2a1a *pde = 00000000 
[  190.050214] Oops: 0000 [#1] SMP 
[  190.050334] Modules linked in: reiserfs sg sd_mod pata_atiixp ata_generic 8139cp pata_acpi 8139too mii sata_sil ehci_hcd ohci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  190.051361] 
[  190.051406] Pid: 52, comm: kacpi_notify Not tainted (2.6.24-16-generic #1)
[  190.051456] EIP: 0060:[<c01d2a1a>] EFLAGS: 00010246 CPU: 1
[  190.051507] EIP is at sysfs_addrm_start+0x2a/0xb0
[  190.051555] EAX: c03f1580 EBX: 00000000 ECX: 00000000 EDX: d9a5e000
[  190.051604] ESI: d9a5feb0 EDI: d9a5fec0 EBP: 00000000 ESP: d9a5fe9c
[  190.051653]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  190.051702] Process kacpi_notify (pid: 52, ti=d9a5e000 task=d9a505a0 task.ti=d9a5e000)
[  190.051755] Stack: db8c3814 db8c3814 db8d0330 fffffff4 c01d2edf 00000000 00000000 00000000 
[  190.052146]        00000000 db8c3814 db8c3814 00000000 00000000 c01d2f59 d9a5fed8 c021098f 
[  190.052537]        db8c3814 c0210e53 c03c46f6 00000007 db9ec1c8 d9a5ff20 db0279d8 db8c3814 
[  190.052928] Call Trace:
[  190.053015]  [<c01d2edf>] create_dir+0x3f/0x90
[  190.053102]  [<c01d2f59>] sysfs_create_dir+0x29/0x50
[  190.053189]  [<c021098f>] kobject_get+0xf/0x20
[  190.053275]  [<c0210e53>] kobject_add+0x93/0x1b0
[  190.053362]  [<c0211001>] kobject_register+0x21/0x50
[  190.053448]  [<c0290d3c>] cpuidle_add_state_sysfs+0x8c/0x110
[  190.053537]  [<c0235c6f>] acpi_os_execute_notify+0x0/0x2b
[  190.053624]  [<c0290184>] cpuidle_enable_device+0x54/0xd0
[  190.053712]  [<dc869171>] acpi_processor_cst_has_changed+0x40/0x53 [processor]
[  190.053810]  [<dc867798>] acpi_processor_notify+0x8b/0xf4 [processor]
[  190.053900]  [<c0315b5a>] schedule+0x20a/0x600
[  190.053987]  [<c023b3e3>] acpi_ev_notify_dispatch+0x4c/0x55
[  190.054075]  [<c0235c91>] acpi_os_execute_notify+0x22/0x2b
[  190.054161]  [<c013cdbf>] run_workqueue+0xbf/0x160
[  190.054248]  [<c013d860>] worker_thread+0x0/0xe0
[  190.054334]  [<c013d8e4>] worker_thread+0x84/0xe0
[  190.054421]  [<c0140b70>] autoremove_wake_function+0x0/0x40
[  190.054508]  [<c013d860>] worker_thread+0x0/0xe0
[  190.054594]  [<c01408b2>] kthread+0x42/0x70
[  190.054679]  [<c0140870>] kthread+0x0/0x70
[  190.054764]  [<c0105677>] kernel_thread_helper+0x7/0x10
[  190.054851]  =======================
[  190.054897] Code: 00 83 ec 10 b9 04 00 00 00 89 74 24 08 89 c6 31 c0 89 5c 24 04 89 d3 89 7c 24 0c 89 f7 f3 ab b8 80 15 3f c0 89 16 e8 f6 3a 14 00 <8b> 53 20 b9 b0 25 1d c0 a1 c4 77 4d c0 89 1c 24 e8 71 df fc ff 
[  190.057390] EIP: [<c01d2a1a>] sysfs_addrm_start+0x2a/0xb0 SS:ESP 0068:d9a5fe9c
[  190.057531] ---[ end trace eac81a487fb986a0 ]---

---

### Post by salefish on 2008-07-06
I have the same laptop with the exact same problem. I haven't found all the drivers I need in XP or I would have switched

---


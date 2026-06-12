---
title: "errors and long pauses while booting"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by tuggy on 2007-11-29
Hello,

I just installed Ubuntu Gutsy in my new laptop (LG E200), and configured everything with some work (specially wireless).
Now I have very strange problems while booting. In 3 different stages the computer pauses for a very looong time, which makes the boot process longer than 3-5minutes

The first one is imediately after booting where the only message displayed is
```
Loading, please wait...
```
After that, the next pause is
```
kinit: no resume available, doing normal boot...
```
and finally
```
* Load hardware driver
hda_intel: azg_get_response timeout, switching to single_cmd mode
```

Can anyone give me any tips on how to solve this problem?

The laptop has an integrated Ati Mobility Xpress 1250.
I've tried booting with noapic and noacpi options, but no changes at all.

thanks

---

### Post by lusis89 on 2007-11-29
try booting with   brokenmodules=hda_intel 
this tells the kernel to not load the hda_intel module and see if it's quickier to boot...
and post the output of the 'dmesg' command

(also try to append "verbose" and remove "spash" from the kernel line in grub menu to get verbose output during boot)

---

### Post by IF-Rit on 2007-11-29
brokenmodules??
where can i find it??

---

### Post by tuggy on 2007-11-29
dmesg:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe80000 (usable)
[    0.000000]  BIOS-e820: 000000006fe80000 - 000000006fe98000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fe98000 - 000000006fe9a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fe9a000 - 0000000070000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 894MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7ec0
[    0.000000] Entering add_active_range(0, 0, 458368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   458368
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   458368
[    0.000000] On node 0 totalpages: 458368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1789 pages used for memmap
[    0.000000]   HighMem zone: 227203 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7E90 checksum 0
[    0.000000] ACPI: RSDP 000F7E90, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 6FE89E86, 006C (r1 LGE    LGPC      6040000  LTP        0)
[    0.000000] ACPI: TCPA 6FE97C9C, 0032 (r2 INTEL            6040000 PTEC        0)
[    0.000000] ACPI: FACP 6FE97CCE, 00F4 (r3 ATI    Alfonsin  6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 6FE8D774, A4B4 (r1    LGE  LHOTSE2  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 6FE99FC0, 0040
[    0.000000] ACPI: SLIC 6FE97DC2, 0176 (r1 LGE    LGPC      6040000 YSB         1)
[    0.000000] ACPI: APIC 6FE97F38, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 6FE97F8C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 6FE97FC8, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: SSDT 6FE8B39D, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 6FE8B2F7, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 6FE89EF2, 1405 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x43538310 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: ATI      Product ID: RS600 Board  APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 33 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 70000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 454787
[    0.000000] Kernel command line: root=UUID=7f741f9a-1d1c-4d49-8f89-84b2fa052a29 ro verbose noacpi noapic  irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.659 MHz processor.
[   14.383294] Console: colour VGA+ 80x25
[   14.386962] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.387527] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.517996] Memory: 1806000k/1833472k available (2015k kernel code, 26112k reserved, 916k data, 364k init, 915968k highmem)
[   14.518071] virtual kernel memory layout:
[   14.518073]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.518075]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.518077]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.518079]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.518081]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.518083]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   14.518085]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   14.518471] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.518621] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.518841] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   14.519083] hpet0: 4 32-bit timers, 14318180 Hz
[   14.600073] Calibrating delay using timer specific routine.. 3346.37 BogoMIPS (lpj=6692754)
[   14.600204] Security Framework v1.0.0 initialized
[   14.600261] SELinux:  Disabled at boot.
[   14.600328] Mount-cache hash table entries: 512
[   14.600564] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   14.600576] monitor/mwait feature present.
[   14.600627] using mwait in idle threads.
[   14.600680] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.600769] CPU: L2 cache: 2048K
[   14.600819] CPU: Physical Processor ID: 0
[   14.600868] CPU: Processor Core ID: 0
[   14.600917] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   14.600933] Compat vDSO mapped to ffffe000.
[   14.601000] Checking 'hlt' instruction... OK.
[   14.616257] SMP alternatives: switching to UP code
[   14.616987] Early unpacking initramfs... done
[   15.165378] ACPI: Core revision 20070126
[   15.165518] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.170817] ACPI: setting ELCR to 0200 (from 0c00)
[   16.247378] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   16.247524] SMP alternatives: switching to SMP code
[   16.247666] Booting processor 1/1 eip 3000
[   16.258122] Initializing CPU#1
[   16.337350] Calibrating delay using timer specific routine.. 3325.03 BogoMIPS (lpj=6650066)
[   16.337359] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   16.337368] monitor/mwait feature present.
[   16.337372] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.337375] CPU: L2 cache: 2048K
[   16.337379] CPU: Physical Processor ID: 0
[   16.337381] CPU: Processor Core ID: 1
[   16.337384] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   16.338192] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   16.338679] Total of 2 processors activated (6671.41 BogoMIPS).
[   16.445359] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.465443] Brought up 2 CPUs
[   16.533665] migration_cost=57
[   16.533971] Booting paravirtualized kernel on bare hardware
[   16.534106] Time: 14:26:03  Date: 10/29/107
[   16.534180] NET: Registered protocol family 16
[   16.534344] EISA bus registered
[   16.534396] ACPI: bus type pci registered
[   16.552816] PCI: PCI BIOS revision 3.00 entry at 0xfdde6, last bus=13
[   16.552868] PCI: Using configuration type 1
[   16.552917] Setting up standard PCI resources
[   16.558226] ACPI: EC: Look up EC in DSDT
[   16.560873] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   16.564958] ACPI: System BIOS is requesting _OSI(Linux)
[   16.565010] ACPI: Please test with "acpi_osi=!Linux"
[   16.565012] Please send dmidecode to linux-acpi@vger.kernel.org
[   16.574178] ACPI: Interpreter enabled
[   16.574230] ACPI: (supports S0 S3 S4 S5)
[   16.574487] ACPI: Using PIC for interrupt routing
[   16.586201] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   16.586331] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.586400] PCI: Probing PCI hardware (bus 00)
[   16.588443] PCI: Transparent bridge - 0000:00:14.4
[   16.588575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.589029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   16.589308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   16.589577] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   16.589882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.590036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.595207] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[   16.595635] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   16.596059] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   16.596483] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[   16.596911] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.597457] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.597967] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[   16.598389] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.599263] ACPI: Power Resource [CTHT] (off)
[   16.599323] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.599386] pnp: PnP ACPI init
[   16.599447] ACPI: bus type pnp registered
[   16.605444] pnp: PnP ACPI: found 11 devices
[   16.605495] ACPI: ACPI bus type pnp unregistered
[   16.605549] PnPBIOS: Disabled by ACPI PNP
[   16.605661] PCI: Using ACPI for IRQ routing
[   16.605712] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.605776] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   16.605829] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   16.704904] NET: Registered protocol family 8
[   16.704954] NET: Registered protocol family 20
[   16.705076] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   16.705129] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   16.705192] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   16.705244] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   16.705297] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   16.705354] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   16.705408] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.705468] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   16.705521] pnp: 00:09: iomem range 0xffb83020-0xffb8401f has been reserved
[   16.708825] Time: tsc clocksource has been installed.
[   16.708885] Switched to high resolution mode on CPU 0
[   16.709055] Switched to high resolution mode on CPU 1
[   16.735987] PCI: Bridge: 0000:00:01.0
[   16.736038]   IO window: 9000-9fff
[   16.736090]   MEM window: cfe00000-cfefffff
[   16.736142]   PREFETCH window: d0000000-dfffffff
[   16.736194] PCI: Bridge: 0000:00:04.0
[   16.736244]   IO window: a000-afff
[   16.736297]   MEM window: f0400000-f04fffff
[   16.736347]   PREFETCH window: disabled.
[   16.736399] PCI: Bridge: 0000:00:06.0
[   16.736447]   IO window: disabled.
[   16.736498]   MEM window: disabled.
[   16.736548]   PREFETCH window: disabled.
[   16.736600] PCI: Bridge: 0000:00:07.0
[   16.736648]   IO window: disabled.
[   16.736700]   MEM window: f0300000-f03fffff
[   16.737553]   PREFETCH window: disabled.
[   16.737605] PCI: Bridge: 0000:00:14.4
[   16.737653]   IO window: disabled.
[   16.737706]   MEM window: disabled.
[   16.737758]   PREFETCH window: disabled.
[   16.737835] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.737851] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.737866] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   16.737890] NET: Registered protocol family 2
[   16.788691] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.788820] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.789908] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.790320] TCP: Hash tables configured (established 131072 bind 65536)
[   16.790373] TCP reno registered
[   16.804876] checking if image is initramfs... it is
[   17.884319] Freeing initrd memory: 7049k freed
[   17.885248] audit: initializing netlink socket (disabled)
[   17.885319] audit(1196346362.996:1): initialized
[   17.885508] highmem bounce pool size: 64 pages
[   17.888536] VFS: Disk quotas dquot_6.5.1
[   17.888656] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.888846] io scheduler noop registered
[   17.888896] io scheduler anticipatory registered
[   17.888946] io scheduler deadline registered
[   17.889014] io scheduler cfq registered (default)
[   17.889166] Boot video device is 0000:01:05.0
[   17.889295] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.889347] assign_interrupt_mode Found MSI capability
[   17.889400] Allocate Port Service[0000:00:04.0:pcie00]
[   17.889520] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   17.889572] assign_interrupt_mode Found MSI capability
[   17.889623] Allocate Port Service[0000:00:06.0:pcie00]
[   17.889736] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   17.889788] assign_interrupt_mode Found MSI capability
[   17.889839] Allocate Port Service[0000:00:07.0:pcie00]
[   17.890056] isapnp: Scanning for PnP cards...
[   18.243688] isapnp: No Plug & Play device found
[   18.276474] Real Time Clock Driver v1.12ac
[   18.276933] hpet_resources: 0xfed00000 is busy
[   18.276966] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.278650] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.278896] input: Macintosh mouse button emulation as /class/input/input0
[   18.279074] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.283140] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.286202] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.286268] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.286322] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.286374] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.286425] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.287017] mice: PS/2 mouse device common for all mice
[   18.287262] EISA: Probing bus 0 at eisa.0
[   18.287321] Cannot allocate resource for EISA slot 1
[   18.287412] Cannot allocate resource for EISA slot 8
[   18.287462] EISA: Detected 0 cards.
[   18.287635] TCP cubic registered
[   18.287699] NET: Registered protocol family 1
[   18.287776] Using IPI No-Shortcut mode
[   18.288102]   Magic number: 15:70:436
[   18.288598] Freeing unused kernel memory: 364k freed
[   18.301421] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.586414] AppArmor: AppArmor initialized<5>audit(1196346363.496:2):  type=1505 info="AppArmor initialized" pid=1217
[   18.596460] fuse init (API version 7.8)
[   18.605343] Failure registering capabilities with primary security module.
[   18.630379] ACPI: Transitioning device [FAN0] to D3
[   18.630432] ACPI: Transitioning device [FAN0] to D3
[   18.630485] ACPI: Fan [FAN0] (off)
[   18.638525] ACPI: SSDT 6FE8BB99, 021F (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   18.639556] ACPI: SSDT 6FE8B5FC, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   18.640356] Monitor-Mwait will be used to enter C-1 state
[   18.640361] Monitor-Mwait will be used to enter C-2 state
[   18.640368] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.640533] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.641166] ACPI: SSDT 6FE8BDB8, 01B0 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[   18.641788] ACPI: SSDT 6FE8BB14, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[   18.642547] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   18.642713] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.642853] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643003] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643150] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643296] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643442] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643589] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.932000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.936000] Time: hpet clocksource has been installed.
[    2.936000] ACPI: Thermal Zone [TZ1] (40 C)
[    3.688000] usbcore: registered new interface driver usbfs
[    3.688000] usbcore: registered new interface driver hub
[    3.688000] usbcore: registered new device driver usb
[    3.688000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.688000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    3.688000] PCI: setting IRQ 10 as level-triggered
[    3.688000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.688000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.688000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.688000] ohci_hcd 0000:00:13.0: irq 10, io mem 0xf0004000
[    3.696000] SCSI subsystem initialized
[    3.736000] libata version 2.21 loaded.
[    3.784000] usb usb1: configuration #1 chosen from 1 choice
[    3.784000] hub 1-0:1.0: USB hub found
[    3.784000] hub 1-0:1.0: 2 ports detected
[    3.888000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.888000] PCI: setting IRQ 11 as level-triggered
[    3.888000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.888000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.888000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.888000] ohci_hcd 0000:00:13.1: irq 11, io mem 0xf0005000
[    3.944000] usb usb2: configuration #1 chosen from 1 choice
[    3.944000] hub 2-0:1.0: USB hub found
[    3.944000] hub 2-0:1.0: 2 ports detected
[    4.048000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.048000] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.048000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    4.048000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.048000] ohci_hcd 0000:00:13.2: irq 11, io mem 0xf0006000
[    4.104000] usb usb3: configuration #1 chosen from 1 choice
[    4.104000] hub 3-0:1.0: USB hub found
[    4.104000] hub 3-0:1.0: 2 ports detected
[    4.208000] ACPI: PCI Interrupt 0000:00:13.3[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.208000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.208000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    4.208000] ohci_hcd 0000:00:13.3: irq 11, io mem 0xf0007000
[    4.264000] usb usb4: configuration #1 chosen from 1 choice
[    4.264000] hub 4-0:1.0: USB hub found
[    4.264000] hub 4-0:1.0: 2 ports detected
[    4.368000] ACPI: PCI Interrupt 0000:00:13.4[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.368000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.368000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    4.368000] ohci_hcd 0000:00:13.4: irq 11, io mem 0xf0008000
[    4.424000] usb usb5: configuration #1 chosen from 1 choice
[    4.424000] hub 5-0:1.0: USB hub found
[    4.424000] hub 5-0:1.0: 2 ports detected
[    4.532000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.532000] ACPI: PCI Interrupt 0000:00:13.5[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.532000] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.532000] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    4.532000] ehci_hcd 0000:00:13.5: debug port 1
[    4.532000] ehci_hcd 0000:00:13.5: irq 11, io mem 0xf0209400
[    4.536000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.536000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.680000] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    4.680000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.680000] usb usb6: configuration #1 chosen from 1 choice
[    4.680000] hub 6-0:1.0: USB hub found
[    4.680000] hub 6-0:1.0: 10 ports detected
[    4.804000] ahci 0000:00:12.0: version 2.2
[    4.804000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[    4.804000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[    4.804000] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.476000] usb 6-9: new high speed USB device using ehci_hcd and address 3
[    5.712000] usb 6-9: configuration #1 chosen from 1 choice
[    5.808000] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.808000] ahci 0000:00:12.0: flags: ncq ilck pm led clo pmp pio slum part 
[    5.808000] scsi0 : ahci
[    5.808000] scsi1 : ahci
[    5.808000] scsi2 : ahci
[    5.808000] scsi3 : ahci
[    5.808000] ata1: SATA max UDMA/133 cmd 0xf887c100 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata2: SATA max UDMA/133 cmd 0xf887c180 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata3: SATA max UDMA/133 cmd 0xf887c200 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata4: SATA max UDMA/133 cmd 0xf887c280 ctl 0x00000000 bmdma 0x00000000 irq 11
[    6.028000] usb 4-2: new full speed USB device using ohci_hcd and address 3
[    6.288000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.288000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    6.288000] ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.288000] ata1.00: configured for UDMA/100
[    6.332000] usb 4-2: configuration #1 chosen from 1 choice
[    6.600000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.912000] ata3: SATA link down (SStatus 0 SControl 300)
[    7.224000] ata4: SATA link down (SStatus 0 SControl 300)
[    7.224000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    7.224000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    7.224000] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    7.224000] SB600_PATA: chipset revision 0
[    7.224000] SB600_PATA: not 100% native mode: will probe irqs later
[    7.224000]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[    7.224000] Probing IDE interface ide0...
[    7.240000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.240000] sd 0:0:0:0: [sda] Write Protect is off
[    7.240000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.240000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.240000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.240000] sd 0:0:0:0: [sda] Write Protect is off
[    7.240000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.240000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.240000]  sda: sda1 sda2 sda3
[    7.672000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.680000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.916000] Attempting manual resume
[    7.916000] swsusp: Resume From Partition 8:2
[    7.916000] PM: Checking swsusp image.
[    7.916000] PM: Resume from disk failed.
[    7.960000] hda: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
[    7.976000] kjournald starting.  Commit interval 5 seconds
[    7.976000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.296000] hda: selected mode 0x42
[    8.296000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.724000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.992000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   21.196000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   21.196000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.196000] sky2 0000:02:00.0: v1.18 addr 0xf0400000 irq 10 Yukon-FE (0xb7) rev 3
[   21.196000] sky2 eth0: addr 00:e0:91:34:1a:1a
[   21.216000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.332000] input: PC Speaker as /class/input/input2
[   21.832000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.840000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   21.876000] [fglrx] Maximum main memory to use for locked dma buffers: 1655 MBytes.
[   21.876000] [fglrx] ASYNCIO init succeed!
[   21.876000] [fglrx] PAT is enabled successfully!
[   21.884000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.908000] [fglrx] module loaded - fglrx 8.43.2 [Nov  9 2007] on minor 0
[   21.928000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   21.928000] Uniform CD-ROM driver Revision: 3.20
[   21.944000] Linux video capture interface: v2.00
[   22.044000] uvcvideo: Found UVC 1.00 device LG Webcam (0c45:62c0)
[   22.048000] usbcore: registered new interface driver uvcvideo
[   22.048000] USB Video Class driver (v0.1.0)
[   22.320000] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   22.512000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   22.612000] ACPI: PCI Interrupt 0000:01:05.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.788000] lp: driver loaded but no devices found
[   29.832000] ndiswrapper version 1.45 loaded (smp=yes)
[   29.908000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   29.912000] ACPI: PCI Interrupt 0000:08:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.912000] ndiswrapper (ZwClose:2247): closing handle 0xf792e328 not implemented
[   29.912000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   30.324000] ndiswrapper: using IRQ 11
[   30.528000] wlan0: ethernet device 00:15:af:47:d3:10 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   30.536000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.540000] usbcore: registered new interface driver ndiswrapper
[   30.608000] Adding 522104k swap on /dev/sda2.  Priority:-1 extents:1 across:522104k
[   31.048000] EXT3 FS on sda1, internal journal
[   31.768000] kjournald starting.  Commit interval 5 seconds
[   31.768000] EXT3 FS on sda3, internal journal
[   31.768000] EXT3-fs: mounted filesystem with ordered data mode.
[   32.924000] ACPI: Battery Slot [CMB0] (battery present)
[   33.064000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   33.072000] No dock devices found.
[   33.116000] ACPI: AC Adapter [AC] (on-line)
[   33.180000] input: Power Button (FF) as /class/input/input4
[   33.180000] ACPI: Power Button (FF) [PWRF]
[   33.180000] input: Sleep Button (CM) as /class/input/input5
[   33.180000] ACPI: Sleep Button (CM) [SLPB]
[   33.180000] input: Lid Switch as /class/input/input6
[   33.180000] ACPI: Lid Switch [LID0]
[   33.180000] input: Power Button (CM) as /class/input/input7
[   33.180000] ACPI: Power Button (CM) [PWRB]
[   34.344000] ppdev: user-space parallel port driver
[   34.548000] sky2 eth0: enabling interface
[   34.632000] audit(1196346395.437:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5415 profile="/usr/sbin/cupsd"
[   34.684000] apm: BIOS not found.
[   34.912000] Failure registering capabilities with primary security module.
[   35.936000] NET: Registered protocol family 10
[   35.936000] lo: Disabled Privacy Extensions
[   35.936000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.936000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.044000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   39.136000] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[   39.136000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   39.136000] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
[   45.164000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  178.576000] NET: Registered protocol family 17
[  180.596000] hda: lost interrupt
[  181.756000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.088000] wlan0: no IPv6 routers present
[  210.992000] wlan0: no IPv6 routers present
[  495.680000] hda: lost interrupt
[  601.952000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  613.180000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  623.280000] wlan0: no IPv6 routers present
[  636.204000] wlan0: no IPv6 routers present
```

---

### Post by kunaal on 2008-04-06
Not sure if you problem was solved. I have the same problem with my LG RD405 (running Gutsy). In my case it is intermittent, sometimes it boots where as some times it hangs in different places, for some reason holding the enter key down causes the m/c to boot:confused:.

I tried booting with "acpi_osi=!Linux" (you can add this to the kernel parameters in /boot/grub/menu.lst). This seems to be working for me.

Regards,
Kunaal

---

### Post by dino99 on 2008-04-07
> **tuggy said:**
> dmesg:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe80000 (usable)
[    0.000000]  BIOS-e820: 000000006fe80000 - 000000006fe98000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fe98000 - 000000006fe9a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fe9a000 - 0000000070000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 894MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7ec0
[    0.000000] Entering add_active_range(0, 0, 458368) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   458368
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   458368
[    0.000000] On node 0 totalpages: 458368
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1789 pages used for memmap
[    0.000000]   HighMem zone: 227203 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7E90 checksum 0
[    0.000000] ACPI: RSDP 000F7E90, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 6FE89E86, 006C (r1 LGE    LGPC      6040000  LTP        0)
[    0.000000] ACPI: TCPA 6FE97C9C, 0032 (r2 INTEL            6040000 PTEC        0)
[    0.000000] ACPI: FACP 6FE97CCE, 00F4 (r3 ATI    Alfonsin  6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 6FE8D774, A4B4 (r1    LGE  LHOTSE2  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 6FE99FC0, 0040
[    0.000000] ACPI: SLIC 6FE97DC2, 0176 (r1 LGE    LGPC      6040000 YSB         1)
[    0.000000] ACPI: APIC 6FE97F38, 0054 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 6FE97F8C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 6FE97FC8, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: SSDT 6FE8B39D, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 6FE8B2F7, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 6FE89EF2, 1405 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x43538310 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: ATI      Product ID: RS600 Board  APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 33 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 70000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 454787
[    0.000000] Kernel command line: root=UUID=7f741f9a-1d1c-4d49-8f89-84b2fa052a29 ro verbose noacpi noapic  irqpoll
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.659 MHz processor.
[   14.383294] Console: colour VGA+ 80x25
[   14.386962] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.387527] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.517996] Memory: 1806000k/1833472k available (2015k kernel code, 26112k reserved, 916k data, 364k init, 915968k highmem)
[   14.518071] virtual kernel memory layout:
[   14.518073]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.518075]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.518077]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.518079]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.518081]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.518083]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   14.518085]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   14.518471] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.518621] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.518841] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   14.519083] hpet0: 4 32-bit timers, 14318180 Hz
[   14.600073] Calibrating delay using timer specific routine.. 3346.37 BogoMIPS (lpj=6692754)
[   14.600204] Security Framework v1.0.0 initialized
[   14.600261] SELinux:  Disabled at boot.
[   14.600328] Mount-cache hash table entries: 512
[   14.600564] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   14.600576] monitor/mwait feature present.
[   14.600627] using mwait in idle threads.
[   14.600680] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.600769] CPU: L2 cache: 2048K
[   14.600819] CPU: Physical Processor ID: 0
[   14.600868] CPU: Processor Core ID: 0
[   14.600917] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   14.600933] Compat vDSO mapped to ffffe000.
[   14.601000] Checking 'hlt' instruction... OK.
[   14.616257] SMP alternatives: switching to UP code
[   14.616987] Early unpacking initramfs... done
[   15.165378] ACPI: Core revision 20070126
[   15.165518] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.170817] ACPI: setting ELCR to 0200 (from 0c00)
[   16.247378] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   16.247524] SMP alternatives: switching to SMP code
[   16.247666] Booting processor 1/1 eip 3000
[   16.258122] Initializing CPU#1
[   16.337350] Calibrating delay using timer specific routine.. 3325.03 BogoMIPS (lpj=6650066)
[   16.337359] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   16.337368] monitor/mwait feature present.
[   16.337372] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.337375] CPU: L2 cache: 2048K
[   16.337379] CPU: Physical Processor ID: 0
[   16.337381] CPU: Processor Core ID: 1
[   16.337384] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   16.338192] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
[   16.338679] Total of 2 processors activated (6671.41 BogoMIPS).
[   16.445359] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.465443] Brought up 2 CPUs
[   16.533665] migration_cost=57
[   16.533971] Booting paravirtualized kernel on bare hardware
[   16.534106] Time: 14:26:03  Date: 10/29/107
[   16.534180] NET: Registered protocol family 16
[   16.534344] EISA bus registered
[   16.534396] ACPI: bus type pci registered
[   16.552816] PCI: PCI BIOS revision 3.00 entry at 0xfdde6, last bus=13
[   16.552868] PCI: Using configuration type 1
[   16.552917] Setting up standard PCI resources
[   16.558226] ACPI: EC: Look up EC in DSDT
[   16.560873] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   16.564958] ACPI: System BIOS is requesting _OSI(Linux)
[   16.565010] ACPI: Please test with "acpi_osi=!Linux"
[   16.565012] Please send dmidecode to linux-acpi@vger.kernel.org
[   16.574178] ACPI: Interpreter enabled
[   16.574230] ACPI: (supports S0 S3 S4 S5)
[   16.574487] ACPI: Using PIC for interrupt routing
[   16.586201] ACPI: EC: GPE=0x1d, ports=0x66, 0x62
[   16.586331] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.586400] PCI: Probing PCI hardware (bus 00)
[   16.588443] PCI: Transparent bridge - 0000:00:14.4
[   16.588575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.589029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   16.589308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   16.589577] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   16.589882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.590036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.595207] ACPI: PCI Interrupt Link [LNKA] (IRQs *10 11)
[   16.595635] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
[   16.596059] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[   16.596483] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[   16.596911] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.597457] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.597967] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[   16.598389] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.599263] ACPI: Power Resource [CTHT] (off)
[   16.599323] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.599386] pnp: PnP ACPI init
[   16.599447] ACPI: bus type pnp registered
[   16.605444] pnp: PnP ACPI: found 11 devices
[   16.605495] ACPI: ACPI bus type pnp unregistered
[   16.605549] PnPBIOS: Disabled by ACPI PNP
[   16.605661] PCI: Using ACPI for IRQ routing
[   16.605712] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.605776] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   16.605829] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   16.704904] NET: Registered protocol family 8
[   16.704954] NET: Registered protocol family 20
[   16.705076] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   16.705129] pnp: 00:01: iomem range 0x0-0x0 could not be reserved
[   16.705192] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   16.705244] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   16.705297] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   16.705354] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   16.705408] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.705468] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[   16.705521] pnp: 00:09: iomem range 0xffb83020-0xffb8401f has been reserved
[   16.708825] Time: tsc clocksource has been installed.
[   16.708885] Switched to high resolution mode on CPU 0
[   16.709055] Switched to high resolution mode on CPU 1
[   16.735987] PCI: Bridge: 0000:00:01.0
[   16.736038]   IO window: 9000-9fff
[   16.736090]   MEM window: cfe00000-cfefffff
[   16.736142]   PREFETCH window: d0000000-dfffffff
[   16.736194] PCI: Bridge: 0000:00:04.0
[   16.736244]   IO window: a000-afff
[   16.736297]   MEM window: f0400000-f04fffff
[   16.736347]   PREFETCH window: disabled.
[   16.736399] PCI: Bridge: 0000:00:06.0
[   16.736447]   IO window: disabled.
[   16.736498]   MEM window: disabled.
[   16.736548]   PREFETCH window: disabled.
[   16.736600] PCI: Bridge: 0000:00:07.0
[   16.736648]   IO window: disabled.
[   16.736700]   MEM window: f0300000-f03fffff
[   16.737553]   PREFETCH window: disabled.
[   16.737605] PCI: Bridge: 0000:00:14.4
[   16.737653]   IO window: disabled.
[   16.737706]   MEM window: disabled.
[   16.737758]   PREFETCH window: disabled.
[   16.737835] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.737851] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.737866] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   16.737890] NET: Registered protocol family 2
[   16.788691] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.788820] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.789908] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.790320] TCP: Hash tables configured (established 131072 bind 65536)
[   16.790373] TCP reno registered
[   16.804876] checking if image is initramfs... it is
[   17.884319] Freeing initrd memory: 7049k freed
[   17.885248] audit: initializing netlink socket (disabled)
[   17.885319] audit(1196346362.996:1): initialized
[   17.885508] highmem bounce pool size: 64 pages
[   17.888536] VFS: Disk quotas dquot_6.5.1
[   17.888656] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.888846] io scheduler noop registered
[   17.888896] io scheduler anticipatory registered
[   17.888946] io scheduler deadline registered
[   17.889014] io scheduler cfq registered (default)
[   17.889166] Boot video device is 0000:01:05.0
[   17.889295] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.889347] assign_interrupt_mode Found MSI capability
[   17.889400] Allocate Port Service[0000:00:04.0:pcie00]
[   17.889520] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   17.889572] assign_interrupt_mode Found MSI capability
[   17.889623] Allocate Port Service[0000:00:06.0:pcie00]
[   17.889736] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   17.889788] assign_interrupt_mode Found MSI capability
[   17.889839] Allocate Port Service[0000:00:07.0:pcie00]
[   17.890056] isapnp: Scanning for PnP cards...
[   18.243688] isapnp: No Plug & Play device found
[   18.276474] Real Time Clock Driver v1.12ac
[   18.276933] hpet_resources: 0xfed00000 is busy
[   18.276966] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.278650] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.278896] input: Macintosh mouse button emulation as /class/input/input0
[   18.279074] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   18.283140] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.286202] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.286268] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.286322] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.286374] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.286425] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.287017] mice: PS/2 mouse device common for all mice
[   18.287262] EISA: Probing bus 0 at eisa.0
[   18.287321] Cannot allocate resource for EISA slot 1
[   18.287412] Cannot allocate resource for EISA slot 8
[   18.287462] EISA: Detected 0 cards.
[   18.287635] TCP cubic registered
[   18.287699] NET: Registered protocol family 1
[   18.287776] Using IPI No-Shortcut mode
[   18.288102]   Magic number: 15:70:436
[   18.288598] Freeing unused kernel memory: 364k freed
[   18.301421] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.586414] AppArmor: AppArmor initialized<5>audit(1196346363.496:2):  type=1505 info="AppArmor initialized" pid=1217
[   18.596460] fuse init (API version 7.8)
[   18.605343] Failure registering capabilities with primary security module.
[   18.630379] ACPI: Transitioning device [FAN0] to D3
[   18.630432] ACPI: Transitioning device [FAN0] to D3
[   18.630485] ACPI: Fan [FAN0] (off)
[   18.638525] ACPI: SSDT 6FE8BB99, 021F (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   18.639556] ACPI: SSDT 6FE8B5FC, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   18.640356] Monitor-Mwait will be used to enter C-1 state
[   18.640361] Monitor-Mwait will be used to enter C-2 state
[   18.640368] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   18.640533] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.641166] ACPI: SSDT 6FE8BDB8, 01B0 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[   18.641788] ACPI: SSDT 6FE8BB14, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[   18.642547] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   18.642713] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.642853] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643003] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643150] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643296] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643442] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.643589] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.932000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.936000] Time: hpet clocksource has been installed.
[    2.936000] ACPI: Thermal Zone [TZ1] (40 C)
[    3.688000] usbcore: registered new interface driver usbfs
[    3.688000] usbcore: registered new interface driver hub
[    3.688000] usbcore: registered new device driver usb
[    3.688000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.688000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    3.688000] PCI: setting IRQ 10 as level-triggered
[    3.688000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.688000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.688000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.688000] ohci_hcd 0000:00:13.0: irq 10, io mem 0xf0004000
[    3.696000] SCSI subsystem initialized
[    3.736000] libata version 2.21 loaded.
[    3.784000] usb usb1: configuration #1 chosen from 1 choice
[    3.784000] hub 1-0:1.0: USB hub found
[    3.784000] hub 1-0:1.0: 2 ports detected
[    3.888000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.888000] PCI: setting IRQ 11 as level-triggered
[    3.888000] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.888000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.888000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.888000] ohci_hcd 0000:00:13.1: irq 11, io mem 0xf0005000
[    3.944000] usb usb2: configuration #1 chosen from 1 choice
[    3.944000] hub 2-0:1.0: USB hub found
[    3.944000] hub 2-0:1.0: 2 ports detected
[    4.048000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    4.048000] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.048000] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    4.048000] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.048000] ohci_hcd 0000:00:13.2: irq 11, io mem 0xf0006000
[    4.104000] usb usb3: configuration #1 chosen from 1 choice
[    4.104000] hub 3-0:1.0: USB hub found
[    4.104000] hub 3-0:1.0: 2 ports detected
[    4.208000] ACPI: PCI Interrupt 0000:00:13.3[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.208000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.208000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    4.208000] ohci_hcd 0000:00:13.3: irq 11, io mem 0xf0007000
[    4.264000] usb usb4: configuration #1 chosen from 1 choice
[    4.264000] hub 4-0:1.0: USB hub found
[    4.264000] hub 4-0:1.0: 2 ports detected
[    4.368000] ACPI: PCI Interrupt 0000:00:13.4[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    4.368000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.368000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    4.368000] ohci_hcd 0000:00:13.4: irq 11, io mem 0xf0008000
[    4.424000] usb usb5: configuration #1 chosen from 1 choice
[    4.424000] hub 5-0:1.0: USB hub found
[    4.424000] hub 5-0:1.0: 2 ports detected
[    4.532000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    4.532000] ACPI: PCI Interrupt 0000:00:13.5[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.532000] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.532000] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    4.532000] ehci_hcd 0000:00:13.5: debug port 1
[    4.532000] ehci_hcd 0000:00:13.5: irq 11, io mem 0xf0209400
[    4.536000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.536000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.680000] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    4.680000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.680000] usb usb6: configuration #1 chosen from 1 choice
[    4.680000] hub 6-0:1.0: USB hub found
[    4.680000] hub 6-0:1.0: 10 ports detected
[    4.804000] ahci 0000:00:12.0: version 2.2
[    4.804000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[    4.804000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[    4.804000] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    5.476000] usb 6-9: new high speed USB device using ehci_hcd and address 3
[    5.712000] usb 6-9: configuration #1 chosen from 1 choice
[    5.808000] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    5.808000] ahci 0000:00:12.0: flags: ncq ilck pm led clo pmp pio slum part 
[    5.808000] scsi0 : ahci
[    5.808000] scsi1 : ahci
[    5.808000] scsi2 : ahci
[    5.808000] scsi3 : ahci
[    5.808000] ata1: SATA max UDMA/133 cmd 0xf887c100 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata2: SATA max UDMA/133 cmd 0xf887c180 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata3: SATA max UDMA/133 cmd 0xf887c200 ctl 0x00000000 bmdma 0x00000000 irq 11
[    5.808000] ata4: SATA max UDMA/133 cmd 0xf887c280 ctl 0x00000000 bmdma 0x00000000 irq 11
[    6.028000] usb 4-2: new full speed USB device using ohci_hcd and address 3
[    6.288000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.288000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    6.288000] ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.288000] ata1.00: configured for UDMA/100
[    6.332000] usb 4-2: configuration #1 chosen from 1 choice
[    6.600000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.912000] ata3: SATA link down (SStatus 0 SControl 300)
[    7.224000] ata4: SATA link down (SStatus 0 SControl 300)
[    7.224000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    7.224000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    7.224000] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    7.224000] SB600_PATA: chipset revision 0
[    7.224000] SB600_PATA: not 100% native mode: will probe irqs later
[    7.224000]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[    7.224000] Probing IDE interface ide0...
[    7.240000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.240000] sd 0:0:0:0: [sda] Write Protect is off
[    7.240000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.240000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.240000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    7.240000] sd 0:0:0:0: [sda] Write Protect is off
[    7.240000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.240000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.240000]  sda: sda1 sda2 sda3
[    7.672000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.680000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.916000] Attempting manual resume
[    7.916000] swsusp: Resume From Partition 8:2
[    7.916000] PM: Checking swsusp image.
[    7.916000] PM: Resume from disk failed.
[    7.960000] hda: HL-DT-ST DVDRAM GSA-T20N, ATAPI CD/DVD-ROM drive
[    7.976000] kjournald starting.  Commit interval 5 seconds
[    7.976000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.296000] hda: selected mode 0x42
[    8.296000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.724000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.992000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   21.196000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   21.196000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.196000] sky2 0000:02:00.0: v1.18 addr 0xf0400000 irq 10 Yukon-FE (0xb7) rev 3
[   21.196000] sky2 eth0: addr 00:e0:91:34:1a:1a
[   21.216000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.332000] input: PC Speaker as /class/input/input2
[   21.832000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.840000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   21.876000] [fglrx] Maximum main memory to use for locked dma buffers: 1655 MBytes.
[   21.876000] [fglrx] ASYNCIO init succeed!
[   21.876000] [fglrx] PAT is enabled successfully!
[   21.884000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   21.908000] [fglrx] module loaded - fglrx 8.43.2 [Nov  9 2007] on minor 0
[   21.928000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   21.928000] Uniform CD-ROM driver Revision: 3.20
[   21.944000] Linux video capture interface: v2.00
[   22.044000] uvcvideo: Found UVC 1.00 device LG Webcam (0c45:62c0)
[   22.048000] usbcore: registered new interface driver uvcvideo
[   22.048000] USB Video Class driver (v0.1.0)
[   22.320000] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   22.512000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   22.612000] ACPI: PCI Interrupt 0000:01:05.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.788000] lp: driver loaded but no devices found
[   29.832000] ndiswrapper version 1.45 loaded (smp=yes)
[   29.908000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   29.912000] ACPI: PCI Interrupt 0000:08:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   29.912000] ndiswrapper (ZwClose:2247): closing handle 0xf792e328 not implemented
[   29.912000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   30.324000] ndiswrapper: using IRQ 11
[   30.528000] wlan0: ethernet device 00:15:af:47:d3:10 using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   30.536000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.540000] usbcore: registered new interface driver ndiswrapper
[   30.608000] Adding 522104k swap on /dev/sda2.  Priority:-1 extents:1 across:522104k
[   31.048000] EXT3 FS on sda1, internal journal
[   31.768000] kjournald starting.  Commit interval 5 seconds
[   31.768000] EXT3 FS on sda3, internal journal
[   31.768000] EXT3-fs: mounted filesystem with ordered data mode.
[   32.924000] ACPI: Battery Slot [CMB0] (battery present)
[   33.064000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   33.072000] No dock devices found.
[   33.116000] ACPI: AC Adapter [AC] (on-line)
[   33.180000] input: Power Button (FF) as /class/input/input4
[   33.180000] ACPI: Power Button (FF) [PWRF]
[   33.180000] input: Sleep Button (CM) as /class/input/input5
[   33.180000] ACPI: Sleep Button (CM) [SLPB]
[   33.180000] input: Lid Switch as /class/input/input6
[   33.180000] ACPI: Lid Switch [LID0]
[   33.180000] input: Power Button (CM) as /class/input/input7
[   33.180000] ACPI: Power Button (CM) [PWRB]
[   34.344000] ppdev: user-space parallel port driver
[   34.548000] sky2 eth0: enabling interface
[   34.632000] audit(1196346395.437:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5415 profile="/usr/sbin/cupsd"
[   34.684000] apm: BIOS not found.
[   34.912000] Failure registering capabilities with primary security module.
[   35.936000] NET: Registered protocol family 10
[   35.936000] lo: Disabled Privacy Extensions
[   35.936000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.936000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.044000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   39.136000] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[   39.136000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   39.136000] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
[   45.164000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  178.576000] NET: Registered protocol family 17
[  180.596000] hda: lost interrupt
[  181.756000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  192.088000] wlan0: no IPv6 routers present
[  210.992000] wlan0: no IPv6 routers present
[  495.680000] hda: lost interrupt
[  601.952000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  613.180000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  623.280000] wlan0: no IPv6 routers present
[  636.204000] wlan0: no IPv6 routers present
```



As you can see, dmesg show you several errors. First, you'd better to boot with new kernel 2.6.24-15 witch is bugless and then, if you still have problem, fill a bug report on launchpad (give some explanations and add what is request for solving bugs ( see : [https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures) for help)

---


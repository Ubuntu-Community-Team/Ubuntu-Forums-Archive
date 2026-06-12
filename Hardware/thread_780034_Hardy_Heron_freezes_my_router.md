---
title: "Hardy Heron freezes my router"
date: 2008-05-03
forum: Hardware
---

### Post by damotor on 2008-05-03
Hi everybody.
I have a PC runing Hardy with a P4P800-X motherboard connected to a SMC7004VWBR router. My PC is runing Hardy Heron and whenever I start or shut it down my router becomes frozen and I have to restart it. I never had this problem with neither gutsy nor feisty, windows won't froze it neither.

What can I do? PLease.

---

### Post by CREEPING DEATH on 2008-05-03
It's more likely a failing router, google the model number and read some reviews.
My personal preference in the WRT54GL, the L is for Linux!

CD

---

### Post by damotor on 2008-05-03
Well, yeah, I know it isn't the best router but for years I had debian, windows and several versions of ubuntu installed and I never had this problem. I also realized that when I shut down the computer some errors related with the network appear in the screen.

---

### Post by damotor on 2008-05-07
Here is the dmesg output:
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffb0000 - 000000001ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffba0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 130992) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130992
[    0.000000]   HighMem    130992 ->   130992
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130992
[    0.000000] On node 0 totalpages: 130992
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125905 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FACA0 checksum 0
[    0.000000] ACPI: RSDP 000FACA0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FFB0000, 0030 (r1 A M I  OEMRSDT   6000523 MSFT       97)
[    0.000000] ACPI: FACP 1FFB0200, 0081 (r2 A M I  OEMFACP   6000523 MSFT       97)
[    0.000000] ACPI: DSDT 1FFB03F0, 376B (r1  AH004 AH004001        1 INTL  2002026)
[    0.000000] ACPI: FACS 1FFC0000, 0040
[    0.000000] ACPI: APIC 1FFB0390, 005C (r1 A M I  OEMAPIC   6000523 MSFT       97)
[    0.000000] ACPI: OEMB 1FFC0040, 003F (r1 A M I  OEMBIOS   6000523 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfba0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129969
[    0.000000] Kernel command line: root=UUID=1954e5e9-ffbd-4f2b-921a-439d6312524b ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2399.827 MHz processor.
[   25.986764] Console: colour VGA+ 80x25
[   25.986769] console [tty0] enabled
[   25.987112] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.987667] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.000325] Memory: 506404k/523968k available (2157k kernel code, 16960k reserved, 998k data, 364k init, 0k highmem)
[   26.000335] virtual kernel memory layout:
[   26.000336]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.000338]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.000339]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   26.000340]     lowmem  : 0xc0000000 - 0xdffb0000   ( 511 MB)
[   26.000341]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   26.000342]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   26.000343]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   26.000347] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.000392] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.080286] Calibrating delay using timer specific routine.. 4804.11 BogoMIPS (lpj=9608223)
[   26.080323] Security Framework initialized
[   26.080331] SELinux:  Disabled at boot.
[   26.080351] AppArmor: AppArmor initialized
[   26.080357] Failure registering capabilities with primary security module.
[   26.080371] Mount-cache hash table entries: 512
[   26.080578] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   26.080597] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   26.080601] CPU: L2 cache: 128K
[   26.080604] CPU: Hyper-Threading is disabled
[   26.080607] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   26.080622] Compat vDSO mapped to ffffe000.
[   26.080640] Checking 'hlt' instruction... OK.
[   26.096722] SMP alternatives: switching to UP code
[   26.098667] Freeing SMP alternatives: 11k freed
[   26.098838] Early unpacking initramfs... done
[   26.528197] ACPI: Core revision 20070126
[   26.528269] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.530369] CPU0: Intel(R) Celeron(R) CPU 2.40GHz stepping 09
[   26.530420] Total of 1 processors activated (4804.11 BogoMIPS).
[   26.530563] ENABLING IO-APIC IRQs
[   26.530760] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.675439] Brought up 1 CPUs
[   26.675473] CPU0 attaching sched-domain:
[   26.675478]  domain 0: span 01
[   26.675480]   groups: 01
[   26.675878] net_namespace: 64 bytes
[   26.675893] Booting paravirtualized kernel on bare hardware
[   26.676790] Time: 10:22:27  Date: 05/07/08
[   26.676841] NET: Registered protocol family 16
[   26.677529] EISA bus registered
[   26.677573] ACPI: bus type pci registered
[   26.677919] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   26.677925] PCI: Using configuration type 1
[   26.677927] Setting up standard PCI resources
[   26.696472] ACPI: EC: Look up EC in DSDT
[   26.701149] ACPI: Interpreter enabled
[   26.701158] ACPI: (supports S0 S1 S3 S4 S5)
[   26.701184] ACPI: Using IOAPIC for interrupt routing
[   26.713835] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.714522] Force enabled HPET at base address 0xfed00000
[   26.714531] PCI: Enabled i801 SMBus device
[   26.714538] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   26.714542] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   26.715188] PCI: Transparent bridge - 0000:00:1e.0
[   26.715231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.715414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   26.718865] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.719005] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.719141] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.719333] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.719485] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.719620] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.719755] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.719887] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.720231] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  1D, should be 0E [20070126]
[   26.720241] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.720353] pnp: PnP ACPI init
[   26.720372] ACPI: bus type pnp registered
[   26.728328] pnp: PnP ACPI: found 15 devices
[   26.728335] ACPI: ACPI bus type pnp unregistered
[   26.728341] PnPBIOS: Disabled by ACPI PNP
[   26.729159] PCI: Using ACPI for IRQ routing
[   26.729166] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.747247] NET: Registered protocol family 8
[   26.747252] NET: Registered protocol family 20
[   26.747487] hpet clockevent registered
[   26.747497] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   26.747502] hpet0: 3 64-bit timers, 14318180 Hz
[   26.748570] AppArmor: AppArmor Filesystem Enabled
[   26.751215] Time: tsc clocksource has been installed.
[   26.759365] system 00:07: ioport range 0x680-0x6ff has been reserved
[   26.759371] system 00:07: ioport range 0x290-0x297 has been reserved
[   26.759382] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   26.759385] system 00:08: ioport range 0x800-0x87f has been reserved
[   26.759388] system 00:08: ioport range 0x400-0x41f has been reserved
[   26.759391] system 00:08: ioport range 0x480-0x4bf has been reserved
[   26.759396] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   26.759400] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   26.759408] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.759411] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   26.759423] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   26.759426] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   26.759429] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   26.759432] system 00:0e: iomem range 0x100000-0x1ffeffff could not be reserved
[   26.759435] system 00:0e: iomem range 0xfff00000-0xffffffff could not be reserved
[   26.790756] PCI: Bridge: 0000:00:01.0
[   26.790763]   IO window: c000-cfff
[   26.790770]   MEM window: ff800000-ff8fffff
[   26.790774]   PREFETCH window: e7f00000-f7efffff
[   26.790781] PCI: Bridge: 0000:00:1e.0
[   26.790785]   IO window: d000-dfff
[   26.790791]   MEM window: ff900000-ff9fffff
[   26.790795]   PREFETCH window: disabled.
[   26.790816] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   26.790838] NET: Registered protocol family 2
[   26.827206] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   26.827528] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   26.827650] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   26.827808] TCP: Hash tables configured (established 16384 bind 16384)
[   26.827814] TCP reno registered
[   26.839308] checking if image is initramfs... it is
[   27.250422] Switched to high resolution mode on CPU 0
[   27.695773] Freeing initrd memory: 8352k freed
[   27.697261] audit: initializing netlink socket (disabled)
[   27.697285] audit(1210155747.592:1): initialized
[   27.702508] VFS: Disk quotas dquot_6.5.1
[   27.702703] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.703055] io scheduler noop registered
[   27.703060] io scheduler anticipatory registered
[   27.703062] io scheduler deadline registered
[   27.703095] io scheduler cfq registered (default)
[   27.703196] Boot video device is 0000:01:00.0
[   27.704044] isapnp: Scanning for PnP cards...
[   28.057730] isapnp: No Plug & Play device found
[   28.211243] Real Time Clock Driver v1.12ac
[   28.211503] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.211730] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.212110] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.214056] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.214953] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.217415] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.217581] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.217870] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   28.220231] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.220240] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.225073] mice: PS/2 mouse device common for all mice
[   28.225461] EISA: Probing bus 0 at eisa.0
[   28.225501] EISA: Detected 0 cards.
[   28.225506] cpuidle: using governor ladder
[   28.225509] cpuidle: using governor menu
[   28.225649] NET: Registered protocol family 1
[   28.225699] Using IPI No-Shortcut mode
[   28.225751] registered taskstats version 1
[   28.225877]   Magic number: 8:400:375
[   28.226037] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.226039] EDD information not available.
[   28.226542] Freeing unused kernel memory: 364k freed
[   28.256800] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   29.630934] fuse init (API version 7.9)
[   29.677754] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.708416] device-mapper: uevent: version 1.0.3
[   29.708549] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   29.743886] md: linear personality registered for level -1
[   29.753633] md: multipath personality registered for level -4
[   29.763161] md: raid0 personality registered for level 0
[   29.773784] md: raid1 personality registered for level 1
[   29.784468] xor: automatically using best checksumming function: pIII_sse
[   29.802043]    pIII_sse  :  3073.000 MB/sec
[   29.802047] xor: using function: pIII_sse (3073.000 MB/sec)
[   29.803379] async_tx: api initialized (async)
[   29.873922] raid6: int32x1    605 MB/s
[   29.941873] raid6: int32x2    711 MB/s
[   30.009700] raid6: int32x4    894 MB/s
[   30.077588] raid6: int32x8    545 MB/s
[   30.145472] raid6: mmxx1     1971 MB/s
[   30.213361] raid6: mmxx2     2481 MB/s
[   30.281240] raid6: sse1x1    1173 MB/s
[   30.349130] raid6: sse1x2    2176 MB/s
[   30.417018] raid6: sse2x1    1746 MB/s
[   30.484910] raid6: sse2x2    2692 MB/s
[   30.484913] raid6: using algorithm sse2x2 (2692 MB/s)
[   30.484919] md: raid6 personality registered for level 6
[   30.484921] md: raid5 personality registered for level 5
[   30.484923] md: raid4 personality registered for level 4
[   30.533139] md: raid10 personality registered for level 10
[   31.571219] usbcore: registered new interface driver usbfs
[   31.571262] usbcore: registered new interface driver hub
[   31.591098] usbcore: registered new device driver usb
[   31.599088] USB Universal Host Controller Interface driver v3.0
[   31.599188] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.599207] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   31.599213] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   31.599772] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   31.599814] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ef00
[   31.600053] usb usb1: configuration #1 chosen from 1 choice
[   31.600097] hub 1-0:1.0: USB hub found
[   31.600111] hub 1-0:1.0: 2 ports detected
[   31.703024] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   31.703046] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   31.703051] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   31.703105] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   31.703140] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ef20
[   31.703346] usb usb2: configuration #1 chosen from 1 choice
[   31.703390] hub 2-0:1.0: USB hub found
[   31.703402] hub 2-0:1.0: 2 ports detected
[   31.704165] SCSI subsystem initialized
[   31.786068] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.791381] libata version 3.00 loaded.
[   31.806847] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   31.806866] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   31.806872] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   31.806928] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   31.806969] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef40
[   31.807180] usb usb3: configuration #1 chosen from 1 choice
[   31.807237] hub 3-0:1.0: USB hub found
[   31.807250] hub 3-0:1.0: 2 ports detected
[   31.883240] Floppy drive(s): fd0 is 1.44M
[   31.902338] FDC 0 is a post-1991 82077
[   31.910671] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   31.910692] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   31.910698] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   31.910752] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   31.910783] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef80
[   31.910972] usb usb4: configuration #1 chosen from 1 choice
[   31.911025] hub 4-0:1.0: USB hub found
[   31.911038] hub 4-0:1.0: 2 ports detected
[   31.942499] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   32.014792] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   32.014819] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   32.014824] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   32.014885] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   32.018814] ehci_hcd 0000:00:1d.7: debug port 1
[   32.018823] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   32.018838] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaffc00
[   32.070239] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.070440] usb usb5: configuration #1 chosen from 1 choice
[   32.070488] hub 5-0:1.0: USB hub found
[   32.070500] hub 5-0:1.0: 8 ports detected
[   32.174432] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   32.174439] 8139cp 0000:02:05.0: Try the "8139too" driver instead.
[   32.179773] 8139too Fast Ethernet driver 0.9.28
[   32.179866] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
[   32.180656] eth0: RealTek RTL8139 at 0xd800, 00:15:f2:cb:f0:f0, IRQ 20
[   32.180661] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   32.186585] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   32.186595] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   32.186659] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   32.186679] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   32.192857] ata_piix 0000:00:1f.1: version 2.12
[   32.192882] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   32.192944] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   32.194612] scsi0 : ata_piix
[   32.196235] scsi1 : ata_piix
[   32.197878] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   32.197883] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   32.378011] ata1.00: HPA unlocked: 117229295 -> 117231408, native 117231408
[   32.378020] ata1.00: ATA-5: ST360021A, 3.10, max UDMA/100
[   32.378023] ata1.00: 117231408 sectors, multi 16: LBA 
[   32.378279] ata1.01: ATA-7: Maxtor 6E040L0, NAR61EA0, max UDMA/133
[   32.378284] ata1.01: 80293248 sectors, multi 16: LBA 
[   32.394111] ata1.00: configured for UDMA/100
[   32.410156] ata1.01: configured for UDMA/100
[   32.465563] usb 1-2: device not accepting address 2, error -71
[   32.885333] ata2.00: ATAPI: LG       DVD-ROM DRD-8160B, 1.01, max UDMA/33
[   32.885366] ata2.01: ATAPI: AOPEN   CD-RW CRW2440, 2.08, max MWDMA2
[   33.048969] ata2.00: configured for UDMA/33
[   33.180367] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   33.220547] ata2.01: configured for MWDMA2
[   33.220750] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.10 PQ: 0 ANSI: 5
[   33.220981] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[   33.221664] scsi 1:0:0:0: CD-ROM            LG       DVD-ROM DRD8160B 1.01 PQ: 0 ANSI: 5
[   33.223506] scsi 1:0:1:0: CD-ROM            AOPEN    CD-RW CRW2440    2.08 PQ: 0 ANSI: 5
[   33.240377] Driver 'sd' needs updating - please use bus_type methods
[   33.240531] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   33.240571] sd 0:0:0:0: [sda] Write Protect is off
[   33.240575] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.240632] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.240759] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   33.240796] sd 0:0:0:0: [sda] Write Protect is off
[   33.240799] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.240855] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.240863]  sda: sda1 sda2 sda3
[   33.262798] Driver 'sr' needs updating - please use bus_type methods
[   33.274698] sd 0:0:0:0: [sda] Attached SCSI disk
[   33.274855] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   33.274896] sd 0:0:1:0: [sdb] Write Protect is off
[   33.274900] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   33.274956] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.275082] sd 0:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   33.275119] sd 0:0:1:0: [sdb] Write Protect is off
[   33.275122] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   33.275177] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.275185]  sdb: sdb1
[   33.279073] sd 0:0:1:0: [sdb] Attached SCSI disk
[   33.296758] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   33.296765] Uniform CD-ROM driver Revision: 3.20
[   33.296845] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   33.299439] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.299471] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   33.299532] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   33.299572] sr 1:0:1:0: Attached scsi generic sg3 type 5
[   33.301800] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   33.301888] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   33.394036] usb 1-2: configuration #1 chosen from 1 choice
[   33.946586] kjournald starting.  Commit interval 5 seconds
[   33.946613] EXT3-fs: mounted filesystem with ordered data mode.
[   44.615835] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.690158] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   46.198330] Linux agpgart interface v0.102
[   46.259439] agpgart: Detected an Intel 865 Chipset.
[   46.263732] agpgart: AGP aperture is 64M @ 0xf8000000
[   46.314179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.374234] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.901780] input: Power Button (FF) as /devices/virtual/input/input2
[   46.913104] ACPI: Power Button (FF) [PWRF]
[   46.913320] input: Power Button (CM) as /devices/virtual/input/input3
[   46.929049] ACPI: Power Button (CM) [PWRB]
[   48.198940] iTCO_vendor_support: vendor-support=0
[   48.238875] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   48.239127] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   48.239230] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   48.498411] intel_rng: FWH not detected
[   48.791477] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   49.309318] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   50.293092] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input5
[   50.421716] parport_pc 00:06: reported by Plug and Play ACPI
[   50.421769] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   50.541293] NET: Registered protocol family 17
[   50.724140] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   50.724187] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   51.149908] intel8x0_measure_ac97_clock: measured 55915 usecs
[   51.149914] intel8x0: clocking to 48000
[   53.318640] lp0: using parport0 (interrupt-driven).
[   53.484090] Adding 1469936k swap on /dev/sda3.  Priority:-1 extents:1 across:1469936k
[   53.494648] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.494923] EXT3 FS on sda2, internal journal
[   57.425139] NET: Registered protocol family 10
[   57.425644] lo: Disabled Privacy Extensions
[   57.603133] No dock devices found.
[   62.848327] [drm] Initialized drm 1.1.0 20060810
[   62.877698] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   63.303213] ppdev: user-space parallel port driver
[   63.593528] audit(1210148584.431:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5653 profile="/usr/sbin/cupsd" namespace="default"
[   63.666061] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   63.666069] apm: overridden by ACPI.
[   64.695464] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   64.695491] agpgart: Device is in legacy mode, falling back to 2.x
[   64.695501] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   64.695538] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   64.936204] Bluetooth: Core ver 2.11
[   64.937862] NET: Registered protocol family 31
[   64.937870] Bluetooth: HCI device and connection manager initialized
[   64.937876] Bluetooth: HCI socket layer initialized
[   64.974801] Bluetooth: L2CAP ver 2.9
[   64.974808] Bluetooth: L2CAP socket layer initialized
[   65.091188] Bluetooth: RFCOMM socket layer initialized
[   65.091214] Bluetooth: RFCOMM TTY layer initialized
[   65.091216] Bluetooth: RFCOMM ver 1.8
[   65.208659] [drm] Setting GART location based on new memory map
[   65.208740] [drm] writeback test succeeded in 1 usecs
[   68.069202] eth0: no IPv6 routers present
[  319.179649] eth0: link down
[  323.227639] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  740.220648] eth0: link down
[  769.741873] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```
Notice there are several 'eth0: link down' and I made this just after starting Ubuntu.

---

### Post by cracker on 2008-05-08
When you receive those messages, it generally means your cable has become unplugged or the device on the other end of the cable has brought its interface down, or otherwise completely failed. You might try running an older version of Ubuntu via liveCD a few times, but I have to agree with the others here, it's most likely just burned out, timing being coincidental.

---


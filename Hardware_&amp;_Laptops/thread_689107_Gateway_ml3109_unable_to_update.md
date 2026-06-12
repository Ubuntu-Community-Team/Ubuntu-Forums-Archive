---
title: "Gateway ml3109 unable to update"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by tdpeek3 on 2008-02-06
I recently purchased a Gateway ML3109 and realized i hated vista.  (poor performace)  I decided to install Ubuntu so that i could easily write programs in C, and use the gcc compiler.

My problem is that I cant access anything without it freezing on me.  Anything includes, wireless, desktop background, and update manager.  The only thing that seems to work is my wired internet but it freezes once i try to do anything other than that.  I even tried to update the OS to see if that would fix any problems, but even that freezes every time i open it.  I am not sure what is going on, and as i am a new Linux user any help would be appreciated.

I read somewhere that there is a log file that can come in handy when dealing with bugs.  If someone could help me access that file I should be able to post it in hopes of a speedy resolution.

Thanks to all!

---

### Post by Yellow Pasque on 2008-02-06
Go to a terminal and type: dmesg
Post the output in a [ code ][ /code ] block (no spaces in between the brackets.

---

### Post by tdpeek3 on 2008-02-27
```
trey@Judas:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007be80000 (usable)
[    0.000000]  BIOS-e820: 000000007be80000 - 000000007be96000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007be96000 - 000000007bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf00000 - 000000007c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1086MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7250
[    0.000000] Entering add_active_range(0, 0, 507520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507520
[    0.000000] On node 0 totalpages: 507520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2173 pages used for memmap
[    0.000000]   HighMem zone: 275971 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7220 checksum 0
[    0.000000] ACPI: RSDP 000F7220, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 7BE8F787, 003C (r1 GATEWA SYSTEM    6040000  LTP        0)
[    0.000000] ACPI: FACP 7BE95D8A, 0074 (r1 ATI    Bonefish  6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 7BE8FEE8, 5EA2 (r1 GATEWA SYSTEM    6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7BE96FC0, 0040
[    0.000000] ACPI: SLIC 7BE95DFE, 0176 (r1 GATEWA SYSTEM    6040000 *TK*        1)
[    0.000000] ACPI: APIC 7BE95F74, 0050 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 7BE95FC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SSDT 7BE8FCF8, 01F0 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    0.000000] ACPI: SSDT 7BE8F7C3, 0535 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:64000000)
[    0.000000] Built 1 zonelists.  Total pages: 503555
[    0.000000] Kernel command line: root=UUID=8c361c8f-ce4f-47e6-8674-d1e6da28e853 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.317 MHz processor.
[   15.449604] Console: colour VGA+ 80x25
[   15.450792] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.451423] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.554092] Memory: 2001256k/2030080k available (2015k kernel code, 27628k reserved, 915k data, 364k init, 1112576k highmem)
[   15.554102] virtual kernel memory layout:
[   15.554103]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.554104]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.554105]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.554106]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.554108]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.554109]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   15.554110]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   15.554113] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.554195] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.634176] Calibrating delay using timer specific routine.. 3197.24 BogoMIPS (lpj=6394490)
[   15.634237] Security Framework v1.0.0 initialized
[   15.634252] SELinux:  Disabled at boot.
[   15.634271] Mount-cache hash table entries: 512
[   15.634519] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[   15.634530] monitor/mwait feature present.
[   15.634532] using mwait in idle threads.
[   15.634540] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.634542] CPU: L2 cache: 1024K
[   15.634546] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[   15.634564] Compat vDSO mapped to ffffe000.
[   15.634585] Checking 'hlt' instruction... OK.
[   15.650408] SMP alternatives: switching to UP code
[   15.650888] Freeing SMP alternatives: 11k freed
[   15.651245] Early unpacking initramfs... done
[   15.996312] ACPI: Core revision 20070126
[   15.996372] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.405914] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[   16.405944] Total of 1 processors activated (3197.24 BogoMIPS).
[   16.406120] ENABLING IO-APIC IRQs
[   16.406317] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   16.553519] Brought up 1 CPUs
[   16.553634] Booting paravirtualized kernel on bare hardware
[   16.553723] Time: 13:37:50  Date: 01/27/108
[   16.553745] NET: Registered protocol family 16
[   16.553828] EISA bus registered
[   16.553848] ACPI: bus type pci registered
[   16.595399] PCI: PCI BIOS revision 2.10 entry at 0xfd5c4, last bus=10
[   16.595401] PCI: Using configuration type 1
[   16.595403] Setting up standard PCI resources
[   16.599420] ACPI: EC: Look up EC in DSDT
[   16.600278] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   16.602777] ACPI: Interpreter enabled
[   16.602781] ACPI: (supports S0 S3 S4 S5)
[   16.602796] ACPI: Using IOAPIC for interrupt routing
[   16.607900] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   16.607951] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.607962] PCI: Probing PCI hardware (bus 00)
[   16.609387] PCI: Transparent bridge - 0000:00:14.4
[   16.609457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.609673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   16.609786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   16.609911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.610023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.611978] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   16.612097] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   16.612209] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   16.612320] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   16.612430] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.612540] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.612650] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   16.612760] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.612870] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   16.612970] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.612982] pnp: PnP ACPI init
[   16.612996] ACPI: bus type pnp registered
[   16.615286] pnp: PnP ACPI: found 10 devices
[   16.615289] ACPI: ACPI bus type pnp unregistered
[   16.615295] PnPBIOS: Disabled by ACPI PNP
[   16.615350] PCI: Using ACPI for IRQ routing
[   16.615353] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.636126] NET: Registered protocol family 8
[   16.636128] NET: Registered protocol family 20
[   16.636197] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.636206] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   16.636209] pnp: 00:08: ioport range 0x200-0x20f has been reserved
[   16.636211] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   16.636214] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   16.636219] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   16.636222] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.636225] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   16.637422] Time: tsc clocksource has been installed.
[   16.666486] PCI: Bridge: 0000:00:01.0
[   16.666489]   IO window: 9000-9fff
[   16.666494]   MEM window: d0000000-d00fffff
[   16.666497]   PREFETCH window: d8000000-dfffffff
[   16.666502] PCI: Bridge: 0000:00:04.0
[   16.666504]   IO window: a000-afff
[   16.666509]   MEM window: d0100000-d01fffff
[   16.666512]   PREFETCH window: disabled.
[   16.666515] PCI: Bridge: 0000:00:05.0
[   16.666518]   IO window: 6000-7fff
[   16.666522]   MEM window: b0000000-b1ffffff
[   16.666526]   PREFETCH window: b2000000-b3ffffff
[   16.666530] PCI: Bridge: 0000:00:14.4
[   16.666536]   IO window: b000-bfff
[   16.666544]   MEM window: d0200000-d02fffff
[   16.666549]   PREFETCH window: disabled.
[   16.666576] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.666588] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.666608] NET: Registered protocol family 2
[   16.705427] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.705627] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.707970] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.709124] TCP: Hash tables configured (established 131072 bind 65536)
[   16.709128] TCP reno registered
[   16.717619] checking if image is initramfs... it is
[   17.169026] Switched to high resolution mode on CPU 0
[   17.402857] Freeing initrd memory: 7056k freed
[   17.403508] audit: initializing netlink socket (disabled)
[   17.403539] audit(1204119470.076:1): initialized
[   17.403632] highmem bounce pool size: 64 pages
[   17.405475] VFS: Disk quotas dquot_6.5.1
[   17.405523] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.405638] io scheduler noop registered
[   17.405640] io scheduler anticipatory registered
[   17.405642] io scheduler deadline registered
[   17.405657] io scheduler cfq registered (default)
[   17.405720] Boot video device is 0000:01:05.0
[   17.405814] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.405855] assign_interrupt_mode Found MSI capability
[   17.405859] Allocate Port Service[0000:00:04.0:pcie00]
[   17.405889] Allocate Port Service[0000:00:04.0:pcie02]
[   17.405967] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   17.406007] assign_interrupt_mode Found MSI capability
[   17.406010] Allocate Port Service[0000:00:05.0:pcie00]
[   17.406041] Allocate Port Service[0000:00:05.0:pcie02]
[   17.406185] isapnp: Scanning for PnP cards...
[   17.763273] isapnp: No Plug & Play device found
[   17.786081] Real Time Clock Driver v1.12ac
[   17.786232] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.787416] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.787663] input: Macintosh mouse button emulation as /class/input/input0
[   17.787743] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   17.792237] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.792245] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.792433] mice: PS/2 mouse device common for all mice
[   17.792563] EISA: Probing bus 0 at eisa.0
[   17.792577] Cannot allocate resource for EISA slot 1
[   17.792597] Cannot allocate resource for EISA slot 6
[   17.792599] Cannot allocate resource for EISA slot 7
[   17.792601] Cannot allocate resource for EISA slot 8
[   17.792603] EISA: Detected 0 cards.
[   17.792732] TCP cubic registered
[   17.792752] NET: Registered protocol family 1
[   17.792782] Using IPI No-Shortcut mode
[   17.792969]   Magic number: 12:961:635
[   17.793057]   hash matches device ptyce
[   17.793540] Freeing unused kernel memory: 364k freed
[   17.832524] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.988130] AppArmor: AppArmor initialized<5>audit(1204119471.576:2):  type=1505 info="AppArmor initialized" pid=1200
[   18.996534] fuse init (API version 7.8)
[   19.001319] Failure registering capabilities with primary security module.
[   19.015856] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.015862] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.015873] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.956000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.960000] Time: acpi_pm clocksource has been installed.
[    2.960000] ACPI: Thermal Zone [THRM] (30 C)
[    3.496000] usbcore: registered new interface driver usbfs
[    3.496000] usbcore: registered new interface driver hub
[    3.496000] usbcore: registered new device driver usb
[    3.496000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.496000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.496000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.496000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.496000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xd0504000
[    3.564000] usb usb1: configuration #1 chosen from 1 choice
[    3.564000] hub 1-0:1.0: USB hub found
[    3.564000] hub 1-0:1.0: 4 ports detected
[    3.588000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.588000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.668000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.668000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.668000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.668000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xd0505000
[    3.728000] usb usb2: configuration #1 chosen from 1 choice
[    3.728000] hub 2-0:1.0: USB hub found
[    3.728000] hub 2-0:1.0: 4 ports detected
[    3.832000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.832000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.832000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.832000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xd0506000
[    3.832000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.832000] usb usb3: configuration #1 chosen from 1 choice
[    3.832000] hub 3-0:1.0: USB hub found
[    3.832000] hub 3-0:1.0: 8 ports detected
[    3.936000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    3.936000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[    3.936000] ATIIXP: chipset revision 128
[    3.936000] ATIIXP: not 100% native mode: will probe irqs later
[    3.936000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA
[    3.936000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:pio, hdd:pio
[    3.936000] Probing IDE interface ide0...
[    4.224000] hda: ST980815A, ATA DISK drive
[    5.008000] hdb: HL-DT-STCD-RW/DVD DRIVE GCC-T10N, ATAPI CD/DVD-ROM drive
[    5.064000] hda: selected mode 0x45
[    5.064000] hdb: selected mode 0x42
[    5.064000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.068000] Probing IDE interface ide1...
[    5.104000] Clocksource tsc unstable (delta = -208538259 ns)
[    5.640000] SCSI subsystem initialized
[    5.648000] libata version 2.21 loaded.
[    5.656000] hda: max request size: 512KiB
[    5.664000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    5.664000] hda: cache flushes supported
[    5.664000]  hda: hda1 hda2 hda3 < hda5 >
[    5.732000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    5.732000] Uniform CD-ROM driver Revision: 3.20
[    6.140000] Attempting manual resume
[    6.140000] swsusp: Resume From Partition 3:5
[    6.140000] PM: Checking swsusp image.
[    6.140000] PM: Resume from disk failed.
[    6.156000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.156000] EXT3-fs: write access will be enabled during recovery.
[    7.912000] kjournald starting.  Commit interval 5 seconds
[    7.912000] EXT3-fs: recovery complete.
[    7.912000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.064000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.108000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.112000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.888000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   16.888000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.888000] sky2 0000:02:00.0: v1.18 addr 0xd0100000 irq 17 Yukon-FE (0xb7) rev 1
[   16.892000] sky2 eth0: addr 00:03:25:3d:70:8c
[   16.904000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   16.964000] input: PC Speaker as /class/input/input2
[   17.448000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   17.572000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   17.608000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.396000] si3054: cannot initialize. EXT MID = 0000
[   18.756000] loop: module loaded
[   18.820000] lp: driver loaded but no devices found
[   18.912000] ndiswrapper version 1.45 loaded (smp=yes)
[   18.984000] ndiswrapper: driver net8185 (Realtek,02/01/2007,5.1097.0201.2007) loaded
[   18.988000] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 22 (level, low) -> IRQ 18
[   19.256000] ndiswrapper: using IRQ 18
[   19.920000] wlan0: ethernet device 00:c0:a8:ef:d3:7b using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 10EC:8185.5.conf
[   19.920000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.920000] usbcore: registered new interface driver ndiswrapper
[   19.964000] Adding 1156640k swap on /dev/hda5.  Priority:-1 extents:1 across:1156640k
[   20.256000] EXT3 FS on hda2, internal journal
[   21.212000] No dock devices found.
[   21.260000] input: Power Button (FF) as /class/input/input4
[   21.264000] ACPI: Power Button (FF) [PWRF]
[   21.296000] input: Power Button (CM) as /class/input/input5
[   21.300000] ACPI: Power Button (CM) [PWRB]
[   21.328000] input: Lid Switch as /class/input/input6
[   21.336000] ACPI: Lid Switch [LID0]
[   21.364000] input: Sleep Button (CM) as /class/input/input7
[   21.368000] ACPI: Sleep Button (CM) [SLPB]
[   21.384000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.448000] ACPI: AC Adapter [AC] (on-line)
[   21.480000] ACPI: Battery Slot [BAT0] (battery present)
[   21.496000] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: found ejectable bay
[   21.496000] ACPI: \_SB_.PCI0.IDE_.SECD.S_D0: Adding notify handler
[   21.496000] ACPI: Bay [\_SB_.PCI0.IDE_.SECD.S_D0] Added
[   21.496000] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: found ejectable bay
[   21.496000] ACPI: \_SB_.PCI0.IDE_.SECD.S_D1: Adding notify handler
[   21.496000] ACPI: Bay [\_SB_.PCI0.IDE_.SECD.S_D1] Added
[   22.720000] ppdev: user-space parallel port driver
[   22.780000] sky2 eth0: enabling interface
[   23.080000] audit(1204137493.415:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4668 profile="/usr/sbin/cupsd"
[   23.216000] apm: BIOS not found.
[   23.460000] Failure registering capabilities with primary security module.
[   23.652000] Bluetooth: Core ver 2.11
[   23.652000] NET: Registered protocol family 31
[   23.652000] Bluetooth: HCI device and connection manager initialized
[   23.652000] Bluetooth: HCI socket layer initialized
[   23.672000] Bluetooth: L2CAP ver 2.8
[   23.672000] Bluetooth: L2CAP socket layer initialized
[   23.748000] Bluetooth: RFCOMM socket layer initialized
[   23.748000] Bluetooth: RFCOMM TTY layer initialized
[   23.748000] Bluetooth: RFCOMM ver 1.8
[   25.220000] [fglrx] Maximum main memory to use for locked dma buffers: 1837 MBytes.
[   25.220000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   25.232000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 19
[   27.064000] [fglrx] total      GART = 130023424
[   27.064000] [fglrx] free       GART = 114032640
[   27.064000] [fglrx] max single GART = 114032640
[   27.064000] [fglrx] total      LFB  = 67108864
[   27.064000] [fglrx] free       LFB  = 52719616
[   27.064000] [fglrx] max single LFB  = 52719616
[   27.064000] [fglrx] total      Inv  = 0
[   27.064000] [fglrx] free       Inv  = 0
[   27.064000] [fglrx] max single Inv  = 0
[   27.064000] [fglrx] total      TIM  = 0
[   33.148000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   55.688000] NET: Registered protocol family 17
[   73.216000] NET: Registered protocol family 10
[   73.216000] lo: Disabled Privacy Extensions
[   73.216000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.676000] wlan0: no IPv6 routers present
[  102.036000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  105.268000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  121.088000] wlan0: no IPv6 routers present
trey@Judas:~$ 
trey@Judas:~$
```

---

### Post by tdpeek3 on 2008-02-27
wow, ok i got help with the wireless, but now there are certain times where it still freezes, i actually started a new thread since the update problem was solved.

[http://ubuntuforums.org/showthread.php?t=709470&highlight=ml3109](http://ubuntuforums.org/showthread.php?t=709470&highlight=ml3109)

---


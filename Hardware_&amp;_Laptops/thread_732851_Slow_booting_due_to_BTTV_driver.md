---
title: "Slow booting due to BTTV driver"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by 50cc on 2008-03-23
I set up a new PC with an AD-Link framegrabber and Ubuntu 7.10 server. I followed the instructions that came with the framegrabber, but still the PC boots very slow. I eventually get a failed status on 'loading hardware drivers' after a timeout of several minutes.

I have the idea that there is something going wrong with the I2C part of the modules but I'm not sure what this module does.

This is the card I'm using: 
[http://www.adlinktech.com/PD/web/PD_detail.php?cKind=FN&pid=247&seq=&id=&sid=](http://www.adlinktech.com/PD/web/PD_detail.php?cKind=FN&pid=247&seq=&id=&sid=)

These are the instructions I followed (including succesfully building and installing the drivers), only difference is I added the lines to /etc/modprobe.d/devfsd:
> 
-----------------------------
Make bttv work on your system
-----------------------------

Open a Terminal. Type the following command:
	# cd v4l-dvb-20070609
	# make clean
	# make
	# make install
	# vi /etc/modprobe.conf

Add the following lines to modprobe.conf:
	alias char-major-81 bttv
	options bttv card=134,134,134,134

Restart the computer.


This is the dmesg output:
```

[    0.000000] Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 08:27:05 UTC 2008 (Ubuntu 2.6.22-14.52-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ef90000 (usable)
[    0.000000]  BIOS-e820: 000000003ef90000 - 000000003ef9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ef9e000 - 000000003efe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003efe0000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 111MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 257936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   257936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   257936
[    0.000000] On node 0 totalpages: 257936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 223 pages used for memmap
[    0.000000]   HighMem zone: 28337 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAFE0 checksum 0
[    0.000000] ACPI: RSDP 000FAFE0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3EF90000, 003C (r1 A_M_I_ OEMRSDT   8000728 MSFT       97)
[    0.000000] ACPI: FACP 3EF90200, 0084 (r2 A_M_I_ OEMFACP   8000728 MSFT       97)
[    0.000000] ACPI: DSDT 3EF905C0, 8111 (r1  A0547 A0547000        0 INTL 20060113)
[    0.000000] ACPI: FACS 3EF9E000, 0040
[    0.000000] ACPI: APIC 3EF90390, 006C (r1 A_M_I_ OEMAPIC   8000728 MSFT       97)
[    0.000000] ACPI: MCFG 3EF90400, 003C (r1 A_M_I_ OEMMCFG   8000728 MSFT       97)
[    0.000000] ACPI: OEMB 3EF9E040, 007B (r1 A_M_I_ AMI_OEM   8000728 MSFT       97)
[    0.000000] ACPI: HPET 3EF986E0, 0038 (r1 A_M_I_ OEMHPET   8000728 MSFT       97)
[    0.000000] ACPI: GSCI 3EF9E0C0, 2024 (r1 A_M_I_ GMCHSCI   8000728 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a202 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f000000:bfe00000)
[    0.000000] Built 1 zonelists.  Total pages: 255921
[    0.000000] Kernel command line: root=UUID=af57dc82-0511-433b-a787-0e34a8484e64 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.016 MHz processor.
[   28.668105] Console: colour VGA+ 80x25
[   28.668366] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.668723] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.694902] Memory: 1011356k/1031744k available (2047k kernel code, 19732k reserved, 920k data, 364k init, 114240k highmem)
[   28.694911] virtual kernel memory layout:
[   28.694913]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.694914]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   28.694915]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   28.694916]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.694917]       .init : 0xc03eb000 - 0xc0446000   ( 364 kB)
[   28.694919]       .data : 0xc02ffd96 - 0xc03e5f04   ( 920 kB)
[   28.694920]       .text : 0xc0100000 - 0xc02ffd96   (2047 kB)
[   28.694923] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.694962] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   28.695111] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   28.695117] hpet0: 3 64-bit timers, 14318180 Hz
[   28.845892] Calibrating delay using timer specific routine.. 3202.00 BogoMIPS (lpj=16010024)
[   28.845916] Security Framework v1.0.0 initialized
[   28.845923] SELinux:  Disabled at boot.
[   28.845936] Mount-cache hash table entries: 512
[   28.846065] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   28.846074] monitor/mwait feature present.
[   28.846075] using mwait in idle threads.
[   28.846080] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.846082] CPU: L2 cache: 512K
[   28.846085] CPU: Physical Processor ID: 0
[   28.846087] CPU: Processor Core ID: 0
[   28.846088] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   28.846099] Compat vDSO mapped to ffffe000.
[   28.846112] Checking 'hlt' instruction... OK.
[   28.885957] SMP alternatives: switching to UP code
[   28.886380] Early unpacking initramfs... done
[   29.201351] ACPI: Core revision 20070126
[   29.201410] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.215917] CPU0: Intel(R) Celeron(R) CPU        E1200  @ 1.60GHz stepping 0d
[   29.215933] SMP alternatives: switching to SMP code
[   29.216029] Booting processor 1/1 eip 3000
[   29.226117] Initializing CPU#1
[   29.375051] Calibrating delay using timer specific routine.. 3199.97 BogoMIPS (lpj=15999867)
[   29.375058] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   29.375063] monitor/mwait feature present.
[   29.375066] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.375068] CPU: L2 cache: 512K
[   29.375070] CPU: Physical Processor ID: 0
[   29.375072] CPU: Processor Core ID: 1
[   29.375073] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   29.375406] CPU1: Intel(R) Celeron(R) CPU        E1200  @ 1.60GHz stepping 0d
[   29.375428] Total of 2 processors activated (6401.97 BogoMIPS).
[   29.375570] ENABLING IO-APIC IRQs
[   29.375743] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.594793] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.614778] Brought up 2 CPUs
[   29.623587] migration_cost=14
[   29.623716] Booting paravirtualized kernel on bare hardware
[   29.623774] Time: 19:31:11  Date: 02/22/108
[   29.623794] NET: Registered protocol family 16
[   29.623884] EISA bus registered
[   29.623890] ACPI: bus type pci registered
[   29.624036] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   29.624038] PCI: Using configuration type 1
[   29.624041] Setting up standard PCI resources
[   29.633643] ACPI: EC: Look up EC in DSDT
[   29.638776] ACPI: Interpreter enabled
[   29.638780] ACPI: (supports S0 S1 S3 S4 S5)
[   29.638800] ACPI: Using IOAPIC for interrupt routing
[   29.649141] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.649159] PCI: Probing PCI hardware (bus 00)
[   29.649880] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   29.649885] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   29.650664] PCI: Transparent bridge - 0000:00:1e.0
[   29.651473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.651661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   29.651789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   29.651889] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   29.670355] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   29.670498] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   29.670637] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   29.670775] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   29.670914] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.671056] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.671196] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   29.671335] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   29.671480] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.671497] pnp: PnP ACPI init
[   29.671507] ACPI: bus type pnp registered
[   29.674861] pnp: PnP ACPI: found 15 devices
[   29.674864] ACPI: ACPI bus type pnp unregistered
[   29.674869] PnPBIOS: Disabled by ACPI PNP
[   29.674927] PCI: Using ACPI for IRQ routing
[   29.674930] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.692931] NET: Registered protocol family 8
[   29.692933] NET: Registered protocol family 20
[   29.692943] NetLabel: Initializing
[   29.692945] NetLabel:  domain hash size = 128
[   29.692947] NetLabel:  protocols = UNLABELED CIPSOv4
[   29.692961] NetLabel:  unlabeled traffic allowed by default
[   29.693021] pnp: 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   29.693032] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   29.693038] pnp: 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   29.693044] pnp: 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   29.693048] pnp: 00:08: iomem range 0xff9fa000-0xff9fafff has been reserved
[   29.693051] pnp: 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[   29.693058] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   29.693062] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   29.693069] pnp: 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   29.693075] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   29.693078] pnp: 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[   29.693081] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   29.693084] pnp: 00:0e: iomem range 0x100000-0x3effffff could not be reserved
[   29.694554] Time: tsc clocksource has been installed.
[   29.694569] Switched to high resolution mode on CPU 0
[   29.694647] Switched to high resolution mode on CPU 1
[   29.723378] PCI: Bridge: 0000:00:1c.0
[   29.723379]   IO window: disabled.
[   29.723384]   MEM window: disabled.
[   29.723388]   PREFETCH window: bfd00000-bfdfffff
[   29.723393] PCI: Bridge: 0000:00:1c.4
[   29.723396]   IO window: a000-afff
[   29.723401]   MEM window: ff600000-ff6fffff
[   29.723405]   PREFETCH window: disabled.
[   29.723409] PCI: Bridge: 0000:00:1c.5
[   29.723412]   IO window: 9000-9fff
[   29.723417]   MEM window: ff500000-ff5fffff
[   29.723420]   PREFETCH window: disabled.
[   29.723426] PCI: Bridge: 0000:04:00.0
[   29.723428]   IO window: disabled.
[   29.723433]   MEM window: disabled.
[   29.723437]   PREFETCH window: bfe00000-bfefffff
[   29.723443] PCI: Bridge: 0000:00:1e.0
[   29.723446]   IO window: b000-bfff
[   29.723450]   MEM window: ff700000-ff7fffff
[   29.723454]   PREFETCH window: bfe00000-bfefffff
[   29.723483] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.723489] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   29.723506] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   29.723511] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   29.723529] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   29.723534] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   29.723544] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   29.723569] NET: Registered protocol family 2
[   29.844366] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.844454] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   29.845396] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.845722] TCP: Hash tables configured (established 131072 bind 65536)
[   29.845726] TCP reno registered
[   29.884443] checking if image is initramfs... it is
[   30.508543] Freeing initrd memory: 6913k freed
[   30.509149] audit: initializing netlink socket (disabled)
[   30.509163] audit(1206214271.360:1): initialized
[   30.509229] highmem bounce pool size: 64 pages
[   30.511265] VFS: Disk quotas dquot_6.5.1
[   30.511325] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.511429] io scheduler noop registered
[   30.511431] io scheduler anticipatory registered
[   30.511433] io scheduler deadline registered (default)
[   30.511453] io scheduler cfq registered
[   30.511468] Boot video device is 0000:00:02.0
[   40.487626] 0000:00:1a.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   40.487932] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   40.487973] assign_interrupt_mode Found MSI capability
[   40.487976] Allocate Port Service[0000:00:1c.0:pcie00]
[   40.488015] Allocate Port Service[0000:00:1c.0:pcie02]
[   40.488094] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   40.488134] assign_interrupt_mode Found MSI capability
[   40.488136] Allocate Port Service[0000:00:1c.4:pcie00]
[   40.488172] Allocate Port Service[0000:00:1c.4:pcie02]
[   40.488250] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   40.488290] assign_interrupt_mode Found MSI capability
[   40.488292] Allocate Port Service[0000:00:1c.5:pcie00]
[   40.488325] Allocate Port Service[0000:00:1c.5:pcie02]
[   40.488494] isapnp: Scanning for PnP cards...
[   40.843754] isapnp: No Plug & Play device found
[   40.874086] Real Time Clock Driver v1.12ac
[   40.874265] hpet_resources: 0xfed00000 is busy
[   40.874313] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   40.874410] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.875201] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   40.875987] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   40.876109] input: Macintosh mouse button emulation as /class/input/input0
[   40.876193] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   40.878896] serio: i8042 KBD port at 0x60,0x64 irq 1
[   40.878902] serio: i8042 AUX port at 0x60,0x64 irq 12
[   40.879047] mice: PS/2 mouse device common for all mice
[   40.879163] EISA: Probing bus 0 at eisa.0
[   40.879197] EISA: Detected 0 cards.
[   40.879284] TCP cubic registered
[   40.879300] NET: Registered protocol family 1
[   40.879323] Using IPI No-Shortcut mode
[   40.879525]   Magic number: 0:129:547
[   40.879761] Freeing unused kernel memory: 364k freed
[   41.061946] AppArmor: AppArmor initialized<5>audit(1206214281.860:2):  type=1505 info="AppArmor initialized" pid=1140
[   41.068604] fuse init (API version 7.8)
[   41.073816] Failure registering capabilities with primary security module.
[   41.137308] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   41.137321] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   41.782708] usbcore: registered new interface driver usbfs
[   41.782737] usbcore: registered new interface driver hub
[   41.782778] usbcore: registered new device driver usb
[   41.783985] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   41.784000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   41.784005] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   41.784151] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   41.784184] ehci_hcd 0000:00:1a.7: debug port 1
[   41.784190] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   41.784201] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xff9fb800
[   41.788086] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   41.788210] usb usb1: configuration #1 chosen from 1 choice
[   41.788238] hub 1-0:1.0: USB hub found
[   41.788246] hub 1-0:1.0: 4 ports detected
[   41.795639] USB Universal Host Controller Interface driver v3.0
[   41.813719] SCSI subsystem initialized
[   41.819149] libata version 2.21 loaded.
[   41.895567] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   41.895584] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   41.895587] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   41.895612] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   41.895641] ehci_hcd 0000:00:1d.7: debug port 1
[   41.895647] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   41.895657] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xff9fb400
[   41.899547] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   41.899645] usb usb2: configuration #1 chosen from 1 choice
[   41.899672] hub 2-0:1.0: USB hub found
[   41.899680] hub 2-0:1.0: 6 ports detected
[   42.005566] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.005581] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   42.005585] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   42.005622] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   42.005653] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d880
[   42.005774] usb usb3: configuration #1 chosen from 1 choice
[   42.005806] hub 3-0:1.0: USB hub found
[   42.005813] hub 3-0:1.0: 2 ports detected
[   42.115208] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
[   42.115229] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   42.115233] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   42.115267] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   42.115297] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000dc00
[   42.115410] usb usb4: configuration #1 chosen from 1 choice
[   42.115439] hub 4-0:1.0: USB hub found
[   42.115447] hub 4-0:1.0: 2 ports detected
[   42.225186] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   42.225198] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   42.225203] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   42.225240] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   42.225264] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000d400
[   42.225384] usb usb5: configuration #1 chosen from 1 choice
[   42.225414] hub 5-0:1.0: USB hub found
[   42.225421] hub 5-0:1.0: 2 ports detected
[   42.334870] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   42.334890] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   42.334894] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   42.334925] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   42.334951] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000d480
[   42.335075] usb usb6: configuration #1 chosen from 1 choice
[   42.335105] hub 6-0:1.0: USB hub found
[   42.335116] hub 6-0:1.0: 2 ports detected
[   42.444740] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   42.444753] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   42.444757] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   42.444785] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   42.444811] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[   42.444932] usb usb7: configuration #1 chosen from 1 choice
[   42.444964] hub 7-0:1.0: USB hub found
[   42.444971] hub 7-0:1.0: 2 ports detected
[   42.555116] ata_piix 0000:00:1f.2: version 2.11
[   42.555125] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   42.555153] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   42.555194] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   42.555310] scsi0 : ata_piix
[   42.555374] scsi1 : ata_piix
[   42.555482] ata1: SATA max UDMA/133 cmd 0x0001e880 ctl 0x0001e802 bmdma 0x0001e080 irq 20
[   42.555487] ata2: SATA max UDMA/133 cmd 0x0001e480 ctl 0x0001e402 bmdma 0x0001e088 irq 20
[   42.781417] ata1.00: ATA-7: MAXTOR STM380215AS, 3.AAC, max UDMA/133
[   42.781423] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   42.784025] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   42.864576] ata1.00: configured for UDMA/133
[   42.968247] usb 5-1: configuration #1 chosen from 1 choice
[   42.971174] hub 5-1:1.0: USB hub found
[   42.974130] hub 5-1:1.0: 3 ports detected
[   43.363114] usb 5-2: new low speed USB device using uhci_hcd and address 3
[   43.363297] ata2.00: ATAPI: LITE-ON DVDRW SHM-165S6S, QS02, max UDMA/100
[   43.542344] usb 5-2: configuration #1 chosen from 1 choice
[   43.562986] ata2.00: configured for UDMA/100
[   43.563096] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM380215 3.AA PQ: 0 ANSI: 5
[   43.564086] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHM-165S6S QS02 PQ: 0 ANSI: 5
[   43.564176] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   43.564209] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 20
[   43.564256] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   43.564299] scsi2 : ata_piix
[   43.564363] scsi3 : ata_piix
[   43.564472] ata3: SATA max UDMA/133 cmd 0x0001d080 ctl 0x0001d002 bmdma 0x0001c800 irq 20
[   43.564477] ata4: SATA max UDMA/133 cmd 0x0001cc00 ctl 0x0001c882 bmdma 0x0001c808 irq 20
[   43.783846] usb 5-1.1: new full speed USB device using uhci_hcd and address 4
[   43.904669] r8169 Gigabit Ethernet driver 2.2LK loaded
[   43.904698] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.904720] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   43.904935] eth0: RTL8168b/8111b at 0xf8844000, 00:1d:60:96:40:eb, XID 38000000 IRQ 16
[   43.906048] PCI: Enabling device 0000:01:00.1 (0000 -> 0001)
[   43.906058] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 18 (level, low) -> IRQ 18
[   43.906107] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   43.906171] scsi4 : pata_jmicron
[   43.906240] scsi5 : pata_jmicron
[   43.906348] ata5: PATA max UDMA/100 cmd 0x00019c00 ctl 0x00019882 bmdma 0x00019400 irq 18
[   43.906352] ata6: PATA max UDMA/100 cmd 0x00019800 ctl 0x00019482 bmdma 0x00019408 irq 18
[   43.930727] usb 5-1.1: configuration #1 chosen from 1 choice
[   43.942743] usbcore: registered new interface driver hiddev
[   43.955820] input: Logitech Optical USB Mouse as /class/input/input1
[   43.955843] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-2
[   43.958842] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input2
[   43.958854] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.0-1.1
[   43.964629] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input3
[   43.964640] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.0-1.1
[   43.964658] usbcore: registered new interface driver usbhid
[   43.964662] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.233770] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 19 (level, low) -> IRQ 20
[   44.286870] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[ff7ff800-ff7fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   44.291959] ahci 0000:01:00.0: version 2.2
[   44.291989] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   44.306527] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   44.306541] sd 0:0:0:0: [sda] Write Protect is off
[   44.306544] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.306559] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.306615] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   44.306625] sd 0:0:0:0: [sda] Write Protect is off
[   44.306627] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.306642] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.306647]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   44.312507] Uniform CD-ROM driver Revision: 3.20
[   44.312570] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   44.317410] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.317434] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   44.326334]  sda1 sda2
[   44.326754] sd 0:0:0:0: [sda] Attached SCSI disk
[   44.713090] Attempting manual resume
[   44.713093] swsusp: Resume From Partition 8:1
[   44.713095] PM: Checking swsusp image.
[   44.725859] PM: Resume from disk failed.
[   44.748845] EXT3-fs: INFO: recovery required on readonly filesystem.
[   44.748849] EXT3-fs: write access will be enabled during recovery.
[   45.300142] ahci 0000:01:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   45.300148] ahci 0000:01:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   45.300156] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   45.300336] scsi6 : ahci
[   45.300413] scsi7 : ahci
[   45.300488] ata7: SATA max UDMA/133 cmd 0xf88b8100 ctl 0x00000000 bmdma 0x00000000 irq 17
[   45.300494] ata8: SATA max UDMA/133 cmd 0xf88b8180 ctl 0x00000000 bmdma 0x00000000 irq 17
[   45.609719] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800017cd32b]
[   45.629575] ata7: SATA link down (SStatus 0 SControl 300)
[   45.959062] ata8: SATA link down (SStatus 0 SControl 300)
[   46.610781] kjournald starting.  Commit interval 5 seconds
[   46.610792] EXT3-fs: sda2: orphan cleanup on readonly fs
[   46.610802] ext3_orphan_cleanup: deleting unreferenced inode 6701064
[   46.610832] ext3_orphan_cleanup: deleting unreferenced inode 6701063
[   46.610841] ext3_orphan_cleanup: deleting unreferenced inode 6701062
[   46.610850] ext3_orphan_cleanup: deleting unreferenced inode 6701061
[   46.610860] ext3_orphan_cleanup: deleting unreferenced inode 6701058
[   46.610867] EXT3-fs: sda2: 5 orphan inodes deleted
[   46.610870] EXT3-fs: recovery complete.
[   46.649007] EXT3-fs: mounted filesystem with ordered data mode.
[   50.338912] r8169: eth0: link down
[   51.932699] heci: Intel(R) AMT Management Interface - version 3.1.0.31
[   51.932703] heci: Copyright (c) 2003 - 2007 Intel Corporation.
[   51.932742] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   51.932749] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   51.932962] heci: link layer has been established.
[   52.039816] heci: heci driver initialization successful.
[   52.080933] input: PC Speaker as /class/input/input4
[   52.163125] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.206356] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.247826] Linux agpgart interface v0.102 (c) Dave Jones
[   52.281588] agpgart: Detected an Intel 965G Chipset.
[   52.281921] agpgart: Detected 7676K stolen memory.
[   52.295679] agpgart: AGP aperture is 256M @ 0xd0000000
[   52.316225] iTCO_vendor_support: vendor-support=0
[   52.324948] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   52.325032] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
[   52.325070] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   52.835186] Linux video capture interface: v2.00
[   52.920185] usbcore: registered new interface driver xpad
[   52.920190] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   53.008015] bttv: driver version 0.9.17 loaded
[   53.008019] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   53.008085] bttv: Bt8xx card found (0).
[   53.008110] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.008125] bttv0: Bt878 (rev 17) at 0000:05:04.0, irq: 16, latency: 64, mmio: 0xbfefe000
[   53.008141] bttv0: using: Adlink RTV24 [card=134,insmod option]
[   53.008168] bttv0: gpio: en=00000000, out=00000000 in=00e7ffff [init]
[   53.008171] bttv0: Adlink RTV-24 initialisation in progress ...
[   53.098259] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   53.098292] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   53.107815] bttv0: Adlink RTV-24 initialisation complete.
[   53.108213] bttv0: using tuner=-1
[   53.108216] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   53.109119] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   53.109738] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   53.110355] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   53.111005] bttv0: registered device video0
[   53.111023] bttv0: registered device vbi0
[   53.111046] bttv0: PLL: 28636363 => 35468950 .. ok
[   53.147763] bttv: Bt8xx card found (1).
[   53.147791] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   53.147808] bttv1: Bt878 (rev 17) at 0000:05:05.0, irq: 17, latency: 64, mmio: 0xbfefc000
[   53.147825] bttv1: using: Adlink RTV24 [card=134,insmod option]
[   53.147854] bttv1: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   53.147857] bttv1: Adlink RTV-24 initialisation in progress ...
[   53.247591] bttv1: Adlink RTV-24 initialisation complete.
[   53.407385] NET: Registered protocol family 17
[   53.846642] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[   69.222504] bttv1: using tuner=-1
[   69.222508] bttv1: i2c: checking for MSP34xx @ 0x80... not found
[   85.197424] bttv1: i2c: checking for TDA9875 @ 0xb0... <6>NET: Registered protocol family 10
[   88.181267] lo: Disabled Privacy Extensions
[   88.181321] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  101.172340] not found
[  101.172344] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[  117.147257] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[  133.122212] bttv1: registered device video1
[  133.122231] bttv1: registered device vbi1
[  133.122255] bttv1: PLL: 28636363 => 35468950 .. ok
[  133.162136] bttv: Bt8xx card found (2).
[  133.162165] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[  133.162183] bttv2: Bt878 (rev 17) at 0000:05:06.0, irq: 18, latency: 64, mmio: 0xbfefa000
[  133.162202] bttv2: using: Adlink RTV24 [card=134,insmod option]
[  133.162230] bttv2: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  133.162233] bttv2: Adlink RTV-24 initialisation in progress ...
[  133.261959] bttv2: Adlink RTV-24 initialisation complete.
[  149.236875] bttv2: using tuner=-1
[  149.236879] bttv2: i2c: checking for MSP34xx @ 0x80... not found
[  165.211790] bttv2: i2c: checking for TDA9875 @ 0xb0... not found
[  181.186707] bttv2: i2c: checking for TDA7432 @ 0x8a... not found
[  197.161624] bttv2: i2c: checking for TDA9887 @ 0x86... not found
[  213.136579] bttv2: registered device video2
[  213.136607] bttv2: registered device vbi2
[  213.136630] bttv2: PLL: 28636363 => 35468950 .. ok
[  213.176519] bttv: Bt8xx card found (3).
[  213.176546] ACPI: PCI Interrupt 0000:05:07.0[A] -> GSI 19 (level, low) -> IRQ 20
[  213.176562] bttv3: Bt878 (rev 17) at 0000:05:07.0, irq: 20, latency: 64, mmio: 0xbfef8000
[  213.176582] bttv3: using: Adlink RTV24 [card=134,insmod option]
[  213.176612] bttv3: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  213.176615] bttv3: Adlink RTV-24 initialisation in progress ...
[  213.276331] bttv3: Adlink RTV-24 initialisation complete.
[  229.251238] bttv3: using tuner=-1
[  229.251243] bttv3: i2c: checking for MSP34xx @ 0x80... <6>loop: module loaded
[  245.226154] not found
[  245.226159] bttv3: i2c: checking for TDA9875 @ 0xb0... not found
[  261.201075] bttv3: i2c: checking for TDA7432 @ 0x8a... not found
[  277.175992] bttv3: i2c: checking for TDA9887 @ 0x86... not found
[  293.150953] bttv3: registered device video3
[  293.150977] bttv3: registered device vbi3
[  293.151001] bttv3: PLL: 28636363 => 35468950 .. ok
[  293.191142] lp: driver loaded but no devices found
[  293.221891] bt878: AUDIO driver version 0.0.0 loaded
[  293.221946] bt878: Bt878 AUDIO function found (0).
[  293.221971] ACPI: PCI Interrupt 0000:05:04.1[A] -> GSI 16 (level, low) -> IRQ 16
[  293.221979] bt878_probe: card id=[0x0], Unknown card.
[  293.221980] Exiting..
[  293.221986] ACPI: PCI interrupt for device 0000:05:04.1 disabled
[  293.221990] bt878: probe of 0000:05:04.1 failed with error -22
[  293.221996] bt878: Bt878 AUDIO function found (0).
[  293.222013] ACPI: PCI Interrupt 0000:05:05.1[A] -> GSI 17 (level, low) -> IRQ 17
[  293.222020] bt878_probe: card id=[0x0], Unknown card.
[  293.222021] Exiting..
[  293.222026] ACPI: PCI interrupt for device 0000:05:05.1 disabled
[  293.222029] bt878: probe of 0000:05:05.1 failed with error -22
[  293.222034] bt878: Bt878 AUDIO function found (0).
[  293.222052] ACPI: PCI Interrupt 0000:05:06.1[A] -> GSI 18 (level, low) -> IRQ 18
[  293.222058] bt878_probe: card id=[0x0], Unknown card.
[  293.222059] Exiting..
[  293.222064] ACPI: PCI interrupt for device 0000:05:06.1 disabled
[  293.222067] bt878: probe of 0000:05:06.1 failed with error -22
[  293.222072] bt878: Bt878 AUDIO function found (0).
[  293.222090] ACPI: PCI Interrupt 0000:05:07.1[A] -> GSI 19 (level, low) -> IRQ 20
[  293.222097] bt878_probe: card id=[0x0], Unknown card.
[  293.222098] Exiting..
[  293.222103] ACPI: PCI interrupt for device 0000:05:07.1 disabled
[  293.222106] bt878: probe of 0000:05:07.1 failed with error -22
[  293.468923] Adding 1951856k swap on /dev/sda1.  Priority:-1 extents:1 across:1951856k
[  293.727718] EXT3 FS on sda2, internal journal
[  341.438422] r8169: eth0: link up
[  341.440725] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  343.703779] r8169: eth0: link down
[  345.291200] r8169: eth0: link up
[  351.908123] eth0: no IPv6 routers present

```

Thanks for reading!

---

### Post by 50cc on 2008-03-26
I tried using the kernel's own BTTV driver for this card, but then the system boots even slower.... Any help?? :confused:

---

### Post by 50cc on 2008-04-14
We finally found the solution for the slow booting, which was in fact due to the bttv card.

With some exellent help from [CT Systems]("http://www.ctsystems.eu") we found the solution, this is what we added to the /etc/modprobe.d/ directory:

We created a file 'devfsd' and added the following:

```

alias char-major-81 bttv
options bttv card=134,134,134,134
options bttv tuner=0,0,0,0
options bttv autoload=0,0,0,0
options bttv radio=0,0,0,0

```

The machine now boots in 90 seconds instead of 300+!

---


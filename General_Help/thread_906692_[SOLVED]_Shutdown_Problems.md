---
title: "[SOLVED] Shutdown Problems"
date: 2008-08-31
forum: General Help
---

### Post by robmetal82 on 2008-08-31
Hello,

I am using Ubuntu 8.04 and having problems when my computer goes to shutdown. I dual boot with XP and that has no issues with shutting down. Luckily I get an error message after I hit shutdown. Here it is-

Network Manager: <info> Caught termination signal
                 <debug> [1219924255.135117] nm-print-open-socks (): Open Sockets List:
                 <debug> [1219924255.135117] nm-print-open-socks (): Open Sockets List:
                 <info> Deactivating Device eth0
                 <WARN> nm_dbus_init(): libhal shutdown failed-connection is closed
                 <WARN> nm_dbus_init(): libhal shutdown failed-connection is closed could not get the system bus. Make sure the message bus is running!
                 nm_dbus_signal_device_status_change:assertion 'cb-data->data->dbus_connection' failed
                 nm_dbus_signal_device_status_change:assertion 'cb-data->data->dbus_connection' failed


When I hit shutdown the screen goes black for a about 30 seconds then this message pops up and nothing happens after that. If I can provide anymore information please let me know. 

Thank you,

Rob

---

### Post by robmetal82 on 2008-09-01
Anyone out there have any ideas about this problem?

---

### Post by porchrat on 2008-09-01
That problem is experienced by a lot of people running linux let alone ubuntu.  Network manager tries to shutdown and needs to use dbus and hal daemons (programs running in the background) to do so properly.  Problem is dbus and hal are turned off before the network manager so you always get that error.

That isn't the reason linux halts but doesn't power off your machine completely though.

try posting the ouput from this:

```
sudo dmesg
```

Could be an ACPI issue.

---

### Post by robmetal82 on 2008-09-01
Here is the output-


rob1@Rob:~$ sudo dmesg
[sudo] password for rob1: 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000cc000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fcf0000 (usable)
[    0.000000]  BIOS-e820: 000000002fcf0000 - 000000002fcff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fcff000 - 000000002fd00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fd00000 - 000000002fe80000 (usable)
[    0.000000]  BIOS-e820: 000000002fe80000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6570
[    0.000000] Entering add_active_range(0, 0, 196224) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196224
[    0.000000]   HighMem    196224 ->   196224
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196224
[    0.000000] On node 0 totalpages: 196224
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1501 pages used for memmap
[    0.000000]   Normal zone: 190627 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:   Product ID: 845G  Board APIC at: 0xFEE00000
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] I/O APIC #1 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 000000000009f000
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000cc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000cc000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000002fcf0000 - 000000002fcff000
[    0.000000] swsusp: Registered nosave memory region: 000000002fcff000 - 000000002fd00000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194691
[    0.000000] Kernel command line: root=UUID=3306cad7-cec5-4676-a246-6488d27a9734 ro acpi=off apm=off quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2486.795 MHz processor.
[   21.793277] Console: colour VGA+ 80x25
[   21.793282] console [tty0] enabled
[   21.794223] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.795631] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.815163] Memory: 765440k/784896k available (2176k kernel code, 18808k reserved, 1006k data, 368k init, 0k highmem)
[   21.815174] virtual kernel memory layout:
[   21.815175]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   21.815176]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.815177]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   21.815179]     lowmem  : 0xc0000000 - 0xefe80000   ( 766 MB)
[   21.815180]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   21.815181]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   21.815182]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   21.815185] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.815235] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.895111] Calibrating delay using timer specific routine.. 4978.06 BogoMIPS (lpj=9956138)
[   21.895145] Security Framework initialized
[   21.895154] SELinux:  Disabled at boot.
[   21.895170] AppArmor: AppArmor initialized
[   21.895176] Failure registering capabilities with primary security module.
[   21.895187] Mount-cache hash table entries: 512
[   21.895377] Initializing cgroup subsys ns
[   21.895387] Initializing cgroup subsys cpuacct
[   21.895404] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   21.895420] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.895423] CPU: L2 cache: 128K
[   21.895425] CPU: Hyper-Threading is disabled
[   21.895428] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   21.895444] Compat vDSO mapped to ffffe000.
[   21.895463] Checking 'hlt' instruction... OK.
[   21.911550] SMP alternatives: switching to UP code
[   21.913571] Freeing SMP alternatives: 11k freed
[   21.913762] Early unpacking initramfs... done
[   22.312799] CPU0: Intel(R) Celeron(R) CPU 2.50GHz stepping 09
[   22.312850] Total of 1 processors activated (4978.06 BogoMIPS).
[   22.312914] ExtINT not setup in hardware but reported by MP table
[   22.312996] ENABLING IO-APIC IRQs
[   22.313198] ..TIMER: vector=0x31 apic1=-1 pin1=-1 apic2=0 pin2=0
[   22.313201] ...trying to set up timer (IRQ0) through the 8259A ... 
[   22.313204] ..... (found pin 0) ...works.
[   22.565973] Brought up 1 CPUs
[   22.566008] CPU0 attaching sched-domain:
[   22.566013]  domain 0: span 01
[   22.566015]   groups: 01
[   22.566447] net_namespace: 64 bytes
[   22.566460] Booting paravirtualized kernel on bare hardware
[   22.567253] Time: 17:36:32  Date: 08/31/08
[   22.567301] NET: Registered protocol family 16
[   22.568073] EISA bus registered
[   22.570331] PCI: PCI BIOS revision 2.10 entry at 0xfd994, last bus=2
[   22.570334] PCI: Using configuration type 1
[   22.570336] Setting up standard PCI resources
[   22.600254] ACPI: Interpreter disabled.
[   22.600261] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.600377] pnp: PnP ACPI: disabled
[   22.600384] PnPBIOS: Scanning system for PnP BIOS support...
[   22.600407] PnPBIOS: Found PnP BIOS installation structure at 0xc00f65e0
[   22.600410] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9893, dseg 0x400
[   22.604837] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[   22.605740] PCI: Probing PCI hardware
[   22.605758] PCI: Probing PCI hardware (bus 00)
[   22.606422] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   22.606425] * this clock source is slow. If you are sure your timer does not have
[   22.606426] * this bug, please use "acpi_pm_good" to disable the workaround
[   22.606476] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   22.606481] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   22.607019] PCI: Transparent bridge - 0000:00:1e.0
[   22.608931] PCI: Using IRQ router PIIX/ICH [8086/24c0] at 0000:00:1f.0
[   22.608947] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 16
[   22.608951] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 16
[   22.608956] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 19
[   22.608960] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 18
[   22.608964] PCI->APIC IRQ transform: 0000:00:1d.7[D] -> IRQ 23
[   22.608972] PCI->APIC IRQ transform: 0000:00:1f.1[A] -> IRQ 17
[   22.608976] PCI->APIC IRQ transform: 0000:00:1f.3[B] -> IRQ 17
[   22.608981] PCI->APIC IRQ transform: 0000:00:1f.5[B] -> IRQ 17
[   22.608985] PCI->APIC IRQ transform: 0000:02:02.0[A] -> IRQ 17
[   22.608989] PCI->APIC IRQ transform: 0000:02:0a.0[A] -> IRQ 22
[   22.608993] PCI->APIC IRQ transform: 0000:02:0b.0[A] -> IRQ 23
[   22.625774] NET: Registered protocol family 8
[   22.625778] NET: Registered protocol family 20
[   22.625976] AppArmor: AppArmor Filesystem Enabled
[   22.626120] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   22.626130] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[   22.626133] system 00:01: iomem range 0xf0000-0xfffff could not be reserved
[   22.626136] system 00:01: iomem range 0xe5000-0xeffff has been reserved
[   22.626139] system 00:01: iomem range 0x100000-0x2fbfffff could not be reserved
[   22.626154] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   22.626157] system 00:0a: ioport range 0x1000-0x105f has been reserved
[   22.626160] system 00:0a: ioport range 0x1060-0x107f has been reserved
[   22.626163] system 00:0a: ioport range 0x1180-0x11bf has been reserved
[   22.626172] system 00:0c: iomem range 0xe0000-0xe3fff has been reserved
[   22.626180] system 00:0d: iomem range 0xe4000-0xe4fff has been reserved
[   22.626186] system 00:0f: iomem range 0xcb200-0xcb7ff has been reserved
[   22.627609] PCI: Bridge: 0000:00:1e.0
[   22.627615]   IO window: 2000-2fff
[   22.627621]   MEM window: e8100000-e81fffff
[   22.627626]   PREFETCH window: disabled.
[   22.627643] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.627665] NET: Registered protocol family 2
[   22.629738] Time: tsc clocksource has been installed.
[   22.661796] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.662333] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.664069] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.664936] TCP: Hash tables configured (established 131072 bind 65536)
[   22.664942] TCP reno registered
[   22.673889] checking if image is initramfs... it is
[   23.422440] Freeing initrd memory: 7726k freed
[   23.424076] audit: initializing netlink socket (disabled)
[   23.424101] audit(1220204192.504:1): initialized
[   23.429610] VFS: Disk quotas dquot_6.5.1
[   23.429826] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.430318] io scheduler noop registered
[   23.430323] io scheduler anticipatory registered
[   23.430325] io scheduler deadline registered
[   23.430359] io scheduler cfq registered (default)
[   23.430379] Boot video device is 0000:00:02.0
[   23.431190] isapnp: Scanning for PnP cards...
[   23.784778] isapnp: No Plug & Play device found
[   23.943205] Real Time Clock Driver v1.12ac
[   23.943490] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.943714] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.945989] 00:15: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.948630] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.948804] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.949115] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   23.952345] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.952355] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.955599] mice: PS/2 mouse device common for all mice
[   23.956028] EISA: Probing bus 0 at eisa.0
[   23.956037] Cannot allocate resource for EISA slot 1
[   23.956041] Cannot allocate resource for EISA slot 2
[   23.956065] EISA: Detected 0 cards.
[   23.956070] cpuidle: using governor ladder
[   23.956073] cpuidle: using governor menu
[   23.956214] NET: Registered protocol family 1
[   23.956264] Using IPI No-Shortcut mode
[   23.956327] registered taskstats version 1
[   23.956442]   Magic number: 4:726:644
[   23.956577] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.956579] EDD information not available.
[   23.957202] Freeing unused kernel memory: 368k freed
[   23.991236] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.480305] fuse init (API version 7.9)
[   25.800918] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   26.734608] usbcore: registered new interface driver usbfs
[   26.734650] usbcore: registered new interface driver hub
[   26.746721] usbcore: registered new device driver usb
[   26.765878] USB Universal Host Controller Interface driver v3.0
[   26.765983] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.765989] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.766431] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.766471] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[   26.766698] usb usb1: configuration #1 chosen from 1 choice
[   26.766740] hub 1-0:1.0: USB hub found
[   26.766754] hub 1-0:1.0: 2 ports detected
[   26.859956] SCSI subsystem initialized
[   26.870250] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.870258] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.870308] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.870344] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[   26.870511] usb usb2: configuration #1 chosen from 1 choice
[   26.870557] hub 2-0:1.0: USB hub found
[   26.870571] hub 2-0:1.0: 2 ports detected
[   26.960420] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.973621] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.973629] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.973678] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.973713] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   26.973898] usb usb3: configuration #1 chosen from 1 choice
[   26.973946] hub 3-0:1.0: USB hub found
[   26.973958] hub 3-0:1.0: 2 ports detected
[   26.974003] libata version 3.00 loaded.
[   27.077607] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.077615] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.077676] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   27.081614] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.081629] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8080000
[   27.109170] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   27.121204] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.121399] usb usb4: configuration #1 chosen from 1 choice
[   27.121451] hub 4-0:1.0: USB hub found
[   27.121462] hub 4-0:1.0: 6 ports detected
[   27.225281] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   27.225289] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   27.229094] sata_sil 0000:02:0a.0: version 2.3
[   27.244998] 8139too Fast Ethernet driver 0.9.28
[   27.255033] scsi0 : sata_sil
[   27.276835] scsi1 : sata_sil
[   27.276912] ata1: SATA max UDMA/100 mmio m512@0xe8110400 tf 0xe8110480 irq 22
[   27.276916] ata2: SATA max UDMA/100 mmio m512@0xe8110400 tf 0xe81104c0 irq 22
[   27.370401] Floppy drive(s): fd0 is 1.44M
[   27.388421] FDC 0 is a post-1991 82077
[   27.588257] ata1: SATA link down (SStatus 0 SControl 310)
[   27.755949] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   27.922459] usb 1-1: configuration #1 chosen from 1 choice
[   28.055377] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   28.106124] ata2.00: ATA-7: ST3160812AS, 3.AAH, max UDMA/133
[   28.106130] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.172634] ata2.00: configured for UDMA/100
[   28.172870] scsi 1:0:0:0: Direct-Access     ATA      ST3160812AS      3.AA PQ: 0 ANSI: 5
[   28.178028] eth0: RealTek RTL8139 at 0x2000, 00:40:2b:65:b0:81, IRQ 17
[   28.178033] eth0:  Identified 8139 chip type 'RTL-8101'
[   28.183237] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   28.183304] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.189615] ata_piix 0000:00:1f.1: version 2.12
[   28.189700] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.196646] scsi2 : ata_piix
[   28.198345] scsi3 : ata_piix
[   28.198425] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[   28.198429] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[   28.359244] ata3.00: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[   28.359250] ata3.00: 80293248 sectors, multi 16: LBA 
[   28.375187] ata3.00: configured for UDMA/100
[   28.850152] ata4.00: ATAPI: Memorex DVD-ROM 16X v2, GWS2, max UDMA/33
[   28.850182] ata4.01: ATAPI: YAMAHA  CRW2200E, 1.0E, max UDMA/33
[   29.013730] ata4.00: configured for UDMA/33
[   29.177562] ata4.01: configured for UDMA/33
[   29.177763] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[   29.178548] scsi 3:0:0:0: CD-ROM            Memorex  DVD-ROM 16X v2   GWS2 PQ: 0 ANSI: 5
[   29.179248] scsi 3:0:1:0: CD-ROM            YAMAHA   CRW2200E         1.0E PQ: 0 ANSI: 2
[   30.873091] Driver 'sd' needs updating - please use bus_type methods
[   30.873250] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.873283] sd 1:0:0:0: [sda] Write Protect is off
[   30.873287] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.873335] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.873458] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   30.873492] sd 1:0:0:0: [sda] Write Protect is off
[   30.873496] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.873544] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.873551]  sda:<6>usbcore: registered new interface driver hiddev
[   30.889130]  sda1 sda2 <<6>input: HP Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
[   30.909086]  sda5 >
[   30.909239] sd 1:0:0:0: [sda] Attached SCSI disk
[   30.909376] sd 2:0:0:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   30.909408] sd 2:0:0:0: [sdb] Write Protect is off
[   30.909412] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.909460] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.909576] sd 2:0:0:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[   30.909605] sd 2:0:0:0: [sdb] Write Protect is off
[   30.909609] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   30.909656] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.909662]  sdb: sdb1
[   30.912132] sd 2:0:0:0: [sdb] Attached SCSI disk
[   30.919385] input,hidraw0: USB HID v1.00 Mouse [HP Mouse] on usb-0000:00:1d.0-1
[   30.919414] usbcore: registered new interface driver usbhid
[   30.919419] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   30.929945] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   30.929977] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   30.930006] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[   30.930035] scsi 3:0:1:0: Attached scsi generic sg3 type 5
[   30.970552] Driver 'sr' needs updating - please use bus_type methods
[   30.976438] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[   30.976445] Uniform CD-ROM driver Revision: 3.20
[   30.976527] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   30.984050] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   30.984135] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   32.024986] Attempting manual resume
[   32.024993] swsusp: Resume From Partition 8:5
[   32.024994] PM: Checking swsusp image.
[   32.035663] PM: Resume from disk failed.
[   32.135485] kjournald starting.  Commit interval 5 seconds
[   32.135512] EXT3-fs: mounted filesystem with ordered data mode.
[   41.281926] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.405713] nf_conntrack version 0.5.0 (12288 buckets, 49152 max)
[   43.573546] Linux agpgart interface v0.102
[   43.637979] agpgart: Detected an Intel 830M Chipset.
[   43.638092] agpgart: Detected 892K stolen memory.
[   43.813135] agpgart: AGP aperture is 128M @ 0xf0000000
[   43.841173] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   43.899282] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.937533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.976770] iTCO_vendor_support: vendor-support=0
[   44.011828] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   44.012080] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   44.012091] iTCO_wdt: No card detected
[   44.124436] intel_rng: FWH not detected
[   44.292242] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   46.426793] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   46.649843] parport_pc 00:11: reported by Plug and Play BIOS
[   46.649901] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   46.747377] intel8x0_measure_ac97_clock: measured 54920 usecs
[   46.747382] intel8x0: clocking to 48000
[   52.264939] lp0: using parport0 (interrupt-driven).
[   52.404493] i2c-adapter i2c-2: found SMSC47M192 or compatible, version 2, stepping A0
[   52.855958] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
[   53.626394] EXT3 FS on sda1, internal journal
[   54.201182] device-mapper: uevent: version 1.0.3
[   54.201230] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   57.933958] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   57.934075] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   57.934337] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   57.934481] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   59.513163] ppdev: user-space parallel port driver
[   59.707605] audit(1220218629.925:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4821 profile="/usr/sbin/cupsd" namespace="default"
[   59.798275] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   62.588055] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   62.754795] Bluetooth: Core ver 2.11
[   62.755840] NET: Registered protocol family 31
[   62.755849] Bluetooth: HCI device and connection manager initialized
[   62.755855] Bluetooth: HCI socket layer initialized
[   62.788595] Bluetooth: L2CAP ver 2.9
[   62.788603] Bluetooth: L2CAP socket layer initialized
[   62.881421] Bluetooth: RFCOMM socket layer initialized
[   62.881451] Bluetooth: RFCOMM TTY layer initialized
[   62.881455] Bluetooth: RFCOMM ver 1.8
[   64.892195] [drm] Initialized drm 1.1.0 20060810
[   64.897545] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   64.897685] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   65.927867] NET: Registered protocol family 17
[   71.410618] NET: Registered protocol family 10
[   71.411655] lo: Disabled Privacy Extensions
[   81.428632] eth0: no IPv6 routers present
rob1@Rob:~$

---

### Post by porchrat on 2008-09-01
this could be your problem:

> Kernel command line: root=UUID=3306cad7-cec5-4676-a246-6488d27a9734 ro acpi=off apm=off quiet splash

ACPI stands for Advanced Configuration and Power Interface and without it your hardware will not turn itself off.  I recommend removing the "acpi=off" from your /boot/grub/menu.lst file

```
sudo gedit /boot/grub/menu.lst
```

Another possibility is to replace "acpi=off" with "acpi=force"

Hopefully that will help.

It is best to create a backup of the menu.lst before editing it.

Do this by typing:

```
sudo mkdir /boot/grub/backup
cp /boot/grub/menu.lst /boot/grub/backup/menu.lst.bak
```

Your backup is now stored in /boot/grub/backup leaving you free to modify your orginial menu.lst

---

### Post by robmetal82 on 2008-09-01
Taking the acpi=off out of the menu.lst file worked. Thank you very much for your help :guitar:

---

### Post by porchrat on 2008-09-01
No problem I'm glad I could help.

please mark the thread as solved

---


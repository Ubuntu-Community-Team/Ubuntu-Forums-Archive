---
title: "Playing a DVD error Buffer I/O error on device"
date: 2008-06-07
forum: Hardware
---

### Post by eamonnf on 2008-06-07
I am trying to watch a dvd on my new machine (MSI Titan 700).  I have inserted the dvd (which is a bought region 2 dvd) into the drive and i cannot access it using Totem.  

Does anyone know anything i can try to get this working?

thanks,

I ran dmesg and got:

```
[   82.029688] UDF-fs: Partition marked readonly; forcing readonly mount
[   82.080310] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Spirited_1', timestamp 2036/02/07 02:58 (103c)
[  154.365537] end_request: I/O error, dev sr0, sector 39796
[  154.365547] Buffer I/O error on device sr0, logical block 9949
[  154.365558] Buffer I/O error on device sr0, logical block 9950
[  154.365563] Buffer I/O error on device sr0, logical block 9951
[  154.365568] Buffer I/O error on device sr0, logical block 9952
[  154.365573] Buffer I/O error on device sr0, logical block 9953
[  154.365578] Buffer I/O error on device sr0, logical block 9954
[  154.365582] Buffer I/O error on device sr0, logical block 9955
[  154.365588] Buffer I/O error on device sr0, logical block 9956
[  154.365593] Buffer I/O error on device sr0, logical block 9957
[  154.365598] Buffer I/O error on device sr0, logical block 9958
[  154.394036] end_request: I/O error, dev sr0, sector 40048
[  154.531075] end_request: I/O error, dev sr0, sector 179192
[  154.649615] end_request: I/O error, dev sr0, sector 179196

```

The drive is an Optiarc DVD RW AD-7530B, NX02, max UDMA/33.

When i run mount it reports that the dvd is mounted as the following:

```
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=eamonnf)

```

My user has privelidges.

here is some (maybe) useful info:
```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9ccb2926-1923-49ab-a293-cdd2ffa2730b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1d68638d-4305-4f76-b87c-a84632613ad7 /home           ext3    relatime        0       2
# /dev/sda2
UUID=e3f1f51b-7733-468e-ba45-df7e86a7abbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

my full dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bef0000 (usable)
[    0.000000]  BIOS-e820: 000000003bef0000 - 000000003bef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3700
[    0.000000] Entering add_active_range(0, 0, 245488) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245488
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245488
[    0.000000] On node 0 totalpages: 245488
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31


[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15987 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7680 checksum 0
[    0.000000] ACPI: RSDP 000F7680, 0014 (r0 CN700 )
[    0.000000] ACPI: RSDT 3BEF3000, 002C (r1 CN700  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3BEF3080, 0074 (r1 CN700  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3BEF3100, 5259 (r1 CN700  AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 3BEF0000, 0040
[    0.000000] ACPI: APIC 3BEF8380, 005A (r1 CN700  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bf00000:c2d00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243571
[    0.000000] Kernel command line: root=UUID=9ccb2926-1923-49ab-a293-cdd2ffa2730b ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.092 MHz processor.
[   14.238269] Console: colour VGA+ 80x25
[   14.238274] console [tty0] enabled
[   14.238879] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.239862] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.284100] Memory: 961408k/981952k available (2176k kernel code, 19892k reserved, 1006k data, 368k init, 64448k highmem)
[   14.284115] virtual kernel memory layout:
[   14.284117]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.284119]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.284122]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.284124]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.284126]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   14.284129]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   14.284131]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   14.284137] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.284192] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.364182] Calibrating delay using timer specific routine.. 3994.68 BogoMIPS (lpj=7989364)
[   14.364214] Security Framework initialized
[   14.364223] SELinux:  Disabled at boot.
[   14.364250] AppArmor: AppArmor initialized
[   14.364256] Failure registering capabilities with primary security module.
[   14.364268] Mount-cache hash table entries: 512
[   14.364399] Initializing cgroup subsys ns
[   14.364404] Initializing cgroup subsys cpuacct
[   14.364417] CPU: After generic identify, caps: a7c9bbff 00100000 00000000 00000000 00004181 00000000 00000000 00000000
[   14.364430] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.364435] CPU: L2 Cache: 128K (64 bytes/line)
[   14.364438] CPU: After all inits, caps: 27c9bbff 00100000 00000000 00000000 00004181 0000ffcc 00000000 00000000
[   14.364451] Compat vDSO mapped to ffffe000.
[   14.364469] Checking 'hlt' instruction... OK.
[   14.380593] SMP alternatives: switching to UP code
[   14.382076] Freeing SMP alternatives: 11k freed
[   14.382243] Early unpacking initramfs... done
[   15.017422] ACPI: Core revision 20070126
[   15.017515] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.022011] CPU0: Centaur VIA C7-D Processor 2000MHz stepping 00
[   15.022074] Total of 1 processors activated (3994.68 BogoMIPS).
[   15.022923] ENABLING IO-APIC IRQs
[   15.023243] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.167857] Brought up 1 CPUs
[   15.167923] CPU0 attaching sched-domain:
[   15.167928]  domain 0: span 01
[   15.167931]   groups: 01
[   15.168154] net_namespace: 64 bytes
[   15.168166] Booting paravirtualized kernel on bare hardware
[   15.168813] Time: 20:47:23  Date: 06/07/08
[   15.168846] NET: Registered protocol family 16
[   15.169073] EISA bus registered
[   15.169109] ACPI: bus type pci registered
[   15.177234] PCI: PCI BIOS revision 2.10 entry at 0xf9310, last bus=1
[   15.177238] PCI: Using configuration type 1
[   15.177242] Setting up standard PCI resources
[   15.183064] ACPI: EC: Look up EC in DSDT
[   15.190895] ACPI: Interpreter enabled
[   15.190902] ACPI: (supports S0 S1 S4 S5)
[   15.190920] ACPI: Using IOAPIC for interrupt routing
[   15.199385] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.200457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.254666] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[   15.254907] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   15.255148] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
[   15.255365] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.255575] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.255792] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.255996] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.256199] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.256449] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   15.256683] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   15.256917] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   15.257193] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[   15.257361] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.257400] pnp: PnP ACPI init
[   15.257413] ACPI: bus type pnp registered
[   15.262295] pnp: PnP ACPI: found 11 devices
[   15.262300] ACPI: ACPI bus type pnp unregistered
[   15.262307] PnPBIOS: Disabled by ACPI PNP
[   15.262581] PCI: Using ACPI for IRQ routing
[   15.262587] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.279753] NET: Registered protocol family 8
[   15.279756] NET: Registered protocol family 20
[   15.279835] AppArmor: AppArmor Filesystem Enabled
[   15.283742] Time: tsc clocksource has been installed.
[   15.291791] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   15.291797] system 00:00: iomem range 0x3bef0000-0x3befffff could not be reserved
[   15.291803] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   15.291808] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   15.291813] system 00:00: iomem range 0x100000-0x3beeffff could not be reserved
[   15.291819] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.291824] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.291830] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[   15.291840] system 00:02: ioport range 0x400-0x47f has been reserved
[   15.291845] system 00:02: ioport range 0x500-0x50f has been reserved
[   15.291856] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   15.322345] PCI: Bridge: 0000:00:01.0
[   15.322349]   IO window: e000-efff
[   15.322355]   MEM window: fb000000-fcffffff
[   15.322361]   PREFETCH window: f4000000-f7ffffff
[   15.322379] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.322399] NET: Registered protocol family 2
[   15.359815] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.360233] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.361559] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.362216] TCP: Hash tables configured (established 131072 bind 65536)
[   15.362221] TCP reno registered
[   15.371889] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   15.958718]  it is
[   16.638221] Freeing initrd memory: 7275k freed
[   16.639411] audit: initializing netlink socket (disabled)
[   16.639441] audit(1212871644.252:1): initialized
[   16.639807] highmem bounce pool size: 64 pages
[   16.642571] VFS: Disk quotas dquot_6.5.1
[   16.642669] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.642836] io scheduler noop registered
[   16.642840] io scheduler anticipatory registered
[   16.642844] io scheduler deadline registered
[   16.642860] io scheduler cfq registered (default)
[   16.642881] PCI: VIA PCI bridge detected. Disabling DAC.
[   16.642973] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   16.642983] Boot video device is 0000:01:00.0
[   16.643313] isapnp: Scanning for PnP cards...
[   16.997334] isapnp: No Plug & Play device found
[   17.033395] Real Time Clock Driver v1.12ac
[   17.033508] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.033631] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.033813] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.034434] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.034859] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.035991] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.036082] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.036196] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   17.036201] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   17.036337] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.046848] mice: PS/2 mouse device common for all mice
[   17.047007] EISA: Probing bus 0 at eisa.0
[   17.047051] EISA: Detected 0 cards.
[   17.047055] cpuidle: using governor ladder
[   17.047059] cpuidle: using governor menu
[   17.047210] NET: Registered protocol family 1
[   17.047249] Using IPI No-Shortcut mode
[   17.047288] registered taskstats version 1
[   17.047443]   Magic number: 12:881:800
[   17.047579]   hash matches device ptyr8
[   17.047641] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.047644] EDD information not available.
[   17.048028] Freeing unused kernel memory: 368k freed
[   17.074803] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.487062] fuse init (API version 7.9)
[   18.516670] ACPI: Fan [FAN] (on)
[   18.528637] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.528646] ACPI: Processor [CPU0] (supports 2 throttling states)
[   18.530989] ACPI: Thermal Zone [THRM] (64 C)
[   19.784785] r8169 Gigabit Ethernet driver 2.2LK loaded
[   19.784810] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
[   19.786424] eth0: RTL8169sc/8110sc at 0xf883c000, 00:1d:92:81:13:d7, XID 18000000 IRQ 16
[   19.973169] usbcore: registered new interface driver usbfs
[   19.973197] usbcore: registered new interface driver hub
[   19.982027] SCSI subsystem initialized
[   20.021523] usbcore: registered new device driver usb
[   20.077116] USB Universal Host Controller Interface driver v3.0
[   20.077528] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   20.077537] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   20.077552] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   20.077949] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   20.077985] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000f900
[   20.078158] usb usb1: configuration #1 chosen from 1 choice
[   20.078189] hub 1-0:1.0: USB hub found
[   20.078196] hub 1-0:1.0: 2 ports detected
[   20.097048] libata version 3.00 loaded.
[   20.181116] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   20.181133] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   20.181162] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   20.181188] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000f800
[   20.181325] usb usb2: configuration #1 chosen from 1 choice
[   20.181360] hub 2-0:1.0: USB hub found
[   20.181367] hub 2-0:1.0: 2 ports detected
[   20.285081] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   20.285098] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   20.285132] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   20.285158] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000f700
[   20.285300] usb usb3: configuration #1 chosen from 1 choice
[   20.285333] hub 3-0:1.0: USB hub found
[   20.285339] hub 3-0:1.0: 2 ports detected
[   20.389050] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   20.389066] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   20.389100] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   20.389126] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000f600
[   20.389272] usb usb4: configuration #1 chosen from 1 choice
[   20.389303] hub 4-0:1.0: USB hub found
[   20.389310] hub 4-0:1.0: 2 ports detected
[   20.493156] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   20.493175] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   20.493213] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   20.493270] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfdffe000
[   20.548830] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   20.560837] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.560993] usb usb5: configuration #1 chosen from 1 choice
[   20.561025] hub 5-0:1.0: USB hub found
[   20.561034] hub 5-0:1.0: 8 ports detected
[   20.671188] sata_via 0000:00:0f.0: version 2.3
[   20.671526] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   20.671535] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 18
[   20.671583] sata_via 0000:00:0f.0: routed to hard irq line 11
[   20.675057] scsi0 : sata_via
[   20.676427] scsi1 : sata_via
[   20.678243] ata1: SATA max UDMA/133 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 18
[   20.678249] ata2: SATA max UDMA/133 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 18
[   20.880628] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.090636] ata1.00: ATA-8: WDC WD1200BEVS-22UST0, 01.01A01, max UDMA/133
[   21.090643] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   21.105715] ata1.00: configured for UDMA/133
[   21.308369] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   21.319098] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 01.0 PQ: 0 ANSI: 5
[   21.320425] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 18
[   21.320486] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   21.337589] pata_via 0000:00:0f.1: version 0.3.3
[   21.337617] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 18
[   21.343427] scsi2 : pata_via
[   21.352349] scsi3 : pata_via
[   21.353847] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[   21.353853] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[   21.405589] Driver 'sd' needs updating - please use bus_type methods
[   21.405683] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.405698] sd 0:0:0:0: [sda] Write Protect is off
[   21.405703] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.405723] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.405777] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   21.405789] sd 0:0:0:0: [sda] Write Protect is off
[   21.405793] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.405811] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.405817]  sda: sda1 sda2 sda3
[   21.466492] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.474456] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.572223] hub 5-0:1.0: over-current change on port 5
[   21.676397] hub 5-0:1.0: over-current change on port 6
[   21.688514] ata3.00: ATAPI: Optiarc DVD RW AD-7530B, NX02, max UDMA/33
[   21.774998] Attempting manual resume
[   21.775004] swsusp: Resume From Partition 8:2
[   21.775007] PM: Checking swsusp image.
[   21.775241] PM: Resume from disk failed.
[   21.780101] hub 5-0:1.0: over-current change on port 7
[   21.832059] kjournald starting.  Commit interval 5 seconds
[   21.832077] EXT3-fs: mounted filesystem with ordered data mode.
[   21.884049] hub 5-0:1.0: over-current change on port 8
[   21.892265] ata3.00: configured for UDMA/33
[   21.892311] ata4: port disabled. ignoring.
[   21.931044] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[   21.931164] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   22.227838] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   22.406869] usb 1-2: configuration #1 chosen from 1 choice
[   30.874993] Linux agpgart interface v0.102
[   30.939210] agpgart: Detected VIA VT3314 chipset
[   30.944753] agpgart: AGP aperture is 128M @ 0xe8000000
[   31.358753] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.418718] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.238386] input: Power Button (FF) as /devices/virtual/input/input2
[   32.250188] ACPI: Power Button (FF) [PWRF]
[   32.250332] input: Power Button (CM) as /devices/virtual/input/input3
[   32.266185] ACPI: Power Button (CM) [PWRB]
[   32.266365] input: Sleep Button (CM) as /devices/virtual/input/input4
[   32.282208] ACPI: Sleep Button (CM) [SLPB]
[   34.142467] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   36.391907] Driver 'sr' needs updating - please use bus_type methods
[   36.619803] sr0: scsi3-mmc drive: 188x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.619812] Uniform CD-ROM driver Revision: 3.20
[   36.619888] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   38.423133] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   38.423144] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 19
[   38.423318] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   38.518622] usbcore: registered new interface driver hiddev
[   38.534749] input: Mitsumi Electric Apple Optical USB Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input6
[   38.550771] input,hidraw0: USB HID v1.10 Mouse [Mitsumi Electric Apple Optical USB Mouse] on usb-0000:00:10.0-2
[   38.550796] usbcore: registered new interface driver usbhid
[   38.550802] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.316158] lp: driver loaded but no devices found
[   45.726165] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[   46.339586] EXT3 FS on sda1, internal journal
[   47.226149] kjournald starting.  Commit interval 5 seconds
[   47.226485] EXT3 FS on sda3, internal journal
[   47.226491] EXT3-fs: mounted filesystem with ordered data mode.
[   47.985513] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.537053] No dock devices found.
[   50.186668] NET: Registered protocol family 10
[   50.187247] lo: Disabled Privacy Extensions
[   50.443554] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.443562] apm: overridden by ACPI.
[   50.622575] ppdev: user-space parallel port driver
[   50.694177] audit(1212871678.575:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4721 profile="/usr/sbin/cupsd" namespace="default"
[   54.165615] r8169: eth0: link up
[   54.368180] Bluetooth: Core ver 2.11
[   54.369037] NET: Registered protocol family 31
[   54.369044] Bluetooth: HCI device and connection manager initialized
[   54.369050] Bluetooth: HCI socket layer initialized
[   54.489106] Bluetooth: L2CAP ver 2.9
[   54.489113] Bluetooth: L2CAP socket layer initialized
[   54.589985] Bluetooth: RFCOMM socket layer initialized
[   54.590247] Bluetooth: RFCOMM TTY layer initialized
[   54.590252] Bluetooth: RFCOMM ver 1.8
[   56.477153] [drm] Initialized drm 1.1.0 20060810
[   56.482197] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   56.482389] [drm] Initialized via 2.11.1 20070202 on minor 0
[   56.483352] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   56.483374] agpgart: Xorg tried to set rate=x12. Setting to AGP3 x8 mode.
[   56.483383] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.483446] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   57.472197] NET: Registered protocol family 17
[   70.505266] eth0: no IPv6 routers present
[   76.061501] [drm:via_mem_alloc] *ERROR* Unknown memory type allocation
[   76.066851] [drm:via_mem_alloc] *ERROR* Unknown memory type allocation
[   76.100554] [drm:via_mem_alloc] *ERROR* Unknown memory type allocation
[   82.029688] UDF-fs: Partition marked readonly; forcing readonly mount
[   82.080310] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Spirited_1', timestamp 2036/02/07 02:58 (103c)
[  154.365537] end_request: I/O error, dev sr0, sector 39796
[  154.365547] Buffer I/O error on device sr0, logical block 9949
[  154.365558] Buffer I/O error on device sr0, logical block 9950
[  154.365563] Buffer I/O error on device sr0, logical block 9951
[  154.365568] Buffer I/O error on device sr0, logical block 9952
[  154.365573] Buffer I/O error on device sr0, logical block 9953
[  154.365578] Buffer I/O error on device sr0, logical block 9954
[  154.365582] Buffer I/O error on device sr0, logical block 9955
[  154.365588] Buffer I/O error on device sr0, logical block 9956
[  154.365593] Buffer I/O error on device sr0, logical block 9957
[  154.365598] Buffer I/O error on device sr0, logical block 9958
[  154.394036] end_request: I/O error, dev sr0, sector 40048
[  154.531075] end_request: I/O error, dev sr0, sector 179192
[  154.649615] end_request: I/O error, dev sr0, sector 179196
[  585.482865] end_request: I/O error, dev sr0, sector 179196
[  585.482874] printk: 120 messages suppressed.
[  585.482879] Buffer I/O error on device sr0, logical block 44799
[  585.556775] end_request: I/O error, dev sr0, sector 179196
[  585.556785] Buffer I/O error on device sr0, logical block 44799
[  585.741147] end_request: I/O error, dev sr0, sector 16307172
[  585.741157] Buffer I/O error on device sr0, logical block 4076793
[  585.788699] end_request: I/O error, dev sr0, sector 16307172
[  585.788708] Buffer I/O error on device sr0, logical block 4076793
[  585.939171] end_request: I/O error, dev sr0, sector 179196
[  585.939181] Buffer I/O error on device sr0, logical block 44799
```

---

### Post by eamonnf on 2008-06-07
I have just tried a music cd and it will not play.  The cover art comes up but the tracks cannot be played.


edit//

I have just opened the box and there appears to be no loose cables.  I gave me a little shove nonetheless and it is still not working.

This is so weird as i just installed Ubuntu today!

---

### Post by mc4man on 2008-06-07
As far as dvd playback 2 things to ck., is a region set on the drive and do you have libdvdcss2 installed. Overall the default totem isn't well suited for dvd playback, use vlc and or install totem-xine. (and make it the default totem player)
If you haven't already done so add medibuntu to your software sources
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)   follow directions for the release of ubuntu your using (add repo, add key and update sources)
 double check in system -> admin -> software sources -> third party that medibuntu has been added, then run (see note first)
```
sudo apt-get install vlc libdvdcss2 totem-xine regionset
```
note: if you know the region has been set remove regionset. _If your running Gutsy you must first remove totem-gstreamer before installing totem-xine_ (in synaptic search _totem-gstreamer_)
After that is done run ( Hardy only) ```
sudo update-alternatives --config totem
``` choose option 2 (set totem-xine as default player) 
If your not sure about region then with a _dvd in drive_ run ```
regionset
``` If it shows no regionset set it to your region (2 ?)
Then try dvd playback
For troubleshooting best way is to open vlc from the terminal, playback a disk and ck. terminal output.
If you want the full set of plugins for totem run
```
sudo apt-get install ubuntu-restricted-extras 
```

It may be useful to post results of```
sudo lshw -C disk
``` if you have any add. playback issues (dvd or cd)

For future use it's always a good idea to post which ver. of ubuntu your using, basics are usually the same, specifics vary

---

### Post by eamonnf on 2008-06-08
thanks for the reply but i am not sure that the problem is specific to dvds.  I cannot play CDs back either!

BTW, I am using version 8.04

---

### Post by Claude.Hubert on 2008-06-08
I had exactly the same problem, with both CD and DVD drives. I went back to the computer I had burned the CD on, and burned the CD again, but this time on a different brand of CD media. The 2nd copy worked without any errors. I can only assume that the problem was the CD media (The original media was from Ricoh, the 2nd one was Memorex).

---


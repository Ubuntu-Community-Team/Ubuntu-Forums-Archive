---
title: "DVD-RW Disapeared"
date: 2008-04-23
forum: Hardware
---

### Post by misteral on 2008-04-23
Hello

After installing Hardy from a DVD image, my DVD is no longer mounting. When I boot up, my BIOS sees my dvd drive, I can boot from it, but Ubuntu won't recognize it. 

The drive is on the second channel, by itself. The connectors are all set firmly

```
sudo mount /media/cdrom
mount: special device /dev/hdd does not exist

```
Here is my fdisk-l:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bd6798b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18237   146488671   83  Linux
/dev/sda2           18238       30515    98623035    5  Extended
/dev/sda5           30163       30515     2835441   82  Linux swap / Solaris
/dev/sda6           18238       30162    95787499+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x951eec27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+  83  Linux
```


here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=73806faa-517d-4d21-9dda-fcefc226f816 /               ext3    errors=remount-ro 0       1
# /dev/hda6
UUID=0f230861-0810-414f-a5f8-1c7664c4616c /home           ext3    relatime        0       2
# /dev/hdb1
UUID=6803f852-63ba-4ffe-864d-5b1093949778 /media/hdb1     ext3    defaults        0       2
# /dev/hda5
UUID=3beff3ca-cc66-46f3-844f-034d0338924a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```



Here is my dmesg:

```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfc0000 (usable)
[    0.000000]  BIOS-e820: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 63MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 245696) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245696
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245696
[    0.000000] On node 0 totalpages: 245696
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 127 pages used for memmap
[    0.000000]   HighMem zone: 16193 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB870 checksum 0
[    0.000000] ACPI: RSDP 000FB870, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 3BFC0100, 0044 (r1 A M I  OEMXSDT   4000619 MSFT       97)
[    0.000000] ACPI: FACP 3BFC0290, 00F4 (r3 A M I  OEMFACP   4000619 MSFT       97)
[    0.000000] ACPI: DSDT 3BFC0440, 5683 (r1  A0368 A0368001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3BFCE000, 0040
[    0.000000] ACPI: APIC 3BFC0390, 0070 (r1 A M I  OEMAPIC   4000619 MSFT       97)
[    0.000000] ACPI: MCFG 3BFC0400, 003C (r1 A M I  OEMMCFG   4000619 MSFT       97)
[    0.000000] ACPI: OEMB 3BFCE040, 005B (r1 A M I  AMI_OEM   4000619 MSFT       97)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c2c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e5000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e5000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243777
[    0.000000] Kernel command line: root=UUID=73806faa-517d-4d21-9dda-fcefc226f816 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.189 MHz processor.
[   52.535098] spurious 8259A interrupt: IRQ7.
[   52.538060] Console: colour VGA+ 80x25
[   52.538063] console [tty0] enabled
[   52.538450] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   52.538859] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   52.557212] Memory: 961896k/982784k available (2157k kernel code, 20304k reserved, 998k data, 364k init, 65280k highmem)
[   52.557220] virtual kernel memory layout:
[   52.557221]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   52.557222]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   52.557223]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   52.557224]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   52.557225]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   52.557226]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   52.557227]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   52.557230] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   52.557261] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   52.637185] Calibrating delay using timer specific routine.. 4022.04 BogoMIPS (lpj=8044090)
[   52.637211] Security Framework initialized
[   52.637216] SELinux:  Disabled at boot.
[   52.637231] AppArmor: AppArmor initialized
[   52.637235] Failure registering capabilities with primary security module.
[   52.637243] Mount-cache hash table entries: 512
[   52.637362] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003 00000000
[   52.637370] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   52.637372] CPU: L2 Cache: 512K (64 bytes/line)
[   52.637375] CPU 0(2) -> Core 0
[   52.637377] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003 00000000
[   52.637386] Compat vDSO mapped to ffffe000.
[   52.637397] Checking 'hlt' instruction... OK.
[   52.653445] SMP alternatives: switching to UP code
[   52.654623] Early unpacking initramfs... done
[   52.973281] ACPI: Core revision 20070126
[   52.973340] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   52.975591] CPU0: AMD Athlon(tm)64 X2 Dual Core Processor  3800+ stepping 01
[   52.975607] SMP alternatives: switching to SMP code
[   52.976063] Booting processor 1/1 eip 3000
[   52.984304] Initializing CPU#1
[   53.062912] Calibrating delay using timer specific routine.. 4018.55 BogoMIPS (lpj=8037111)
[   53.062918] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003 00000000
[   53.062924] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   53.062926] CPU: L2 Cache: 512K (64 bytes/line)
[   53.062928] CPU 1(2) -> Core 1
[   53.062930] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003 00000000
[   53.064863] CPU1: AMD Athlon(tm)64 X2 Dual Core Processor  3800+ stepping 01
[   53.064878] Total of 2 processors activated (8040.60 BogoMIPS).
[   53.065178] ENABLING IO-APIC IRQs
[   53.065415] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   53.212578] Brought up 2 CPUs
[   53.212635] CPU0 attaching sched-domain:
[   53.212638]  domain 0: span 03
[   53.212639]   groups: 01 02
[   53.212642] CPU1 attaching sched-domain:
[   53.212644]  domain 0: span 03
[   53.212646]   groups: 02 01
[   53.212831] net_namespace: 64 bytes
[   53.212838] Booting paravirtualized kernel on bare hardware
[   53.213559] Time:  0:09:52  Date: 04/24/08
[   53.213585] NET: Registered protocol family 16
[   53.213744] EISA bus registered
[   53.213748] ACPI: bus type pci registered
[   53.214545] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   53.214547] PCI: Using configuration type 1
[   53.214549] Setting up standard PCI resources
[   53.221640] ACPI: EC: Look up EC in DSDT
[   53.226388] ACPI: Interpreter enabled
[   53.226390] ACPI: (supports S0 S1 S3 S4 S5)
[   53.226404] ACPI: Using IOAPIC for interrupt routing
[   53.234509] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   53.235539] PCI: Transparent bridge - 0000:00:10.0
[   53.235556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   53.235747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
[   53.235832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
[   53.235916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   53.236016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   53.245665] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   53.245858] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   53.246048] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   53.246238] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *5
[   53.246427] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   53.246616] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   53.246805] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[   53.246994] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   53.247183] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[   53.247373] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[   53.247562] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[   53.247752] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[   53.247943] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   53.248134] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   53.248326] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[   53.248544] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[   53.248736] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[   53.248926] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[   53.249154] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   53.249273] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  37, should be 2A [20070126]
[   53.249279] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.249304] pnp: PnP ACPI init
[   53.249311] ACPI: bus type pnp registered
[   53.254221] pnp: PnP ACPI: found 13 devices
[   53.254223] ACPI: ACPI bus type pnp unregistered
[   53.254226] PnPBIOS: Disabled by ACPI PNP
[   53.254406] PCI: Using ACPI for IRQ routing
[   53.254409] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   53.280402] NET: Registered protocol family 8
[   53.280403] NET: Registered protocol family 20
[   53.280464] AppArmor: AppArmor Filesystem Enabled
[   53.292410] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   53.292413] system 00:07: ioport range 0x800-0x80f has been reserved
[   53.292415] system 00:07: ioport range 0x500-0x57f has been reserved
[   53.292418] system 00:07: ioport range 0x580-0x5ff has been reserved
[   53.292421] system 00:07: ioport range 0x800-0x87f could not be reserved
[   53.292423] system 00:07: ioport range 0x880-0x8ff has been reserved
[   53.292426] system 00:07: ioport range 0x900-0x97f has been reserved
[   53.292428] system 00:07: ioport range 0x980-0x9ff has been reserved
[   53.292431] system 00:07: ioport range 0x2000-0x207f has been reserved
[   53.292434] system 00:07: ioport range 0x2080-0x20ff has been reserved
[   53.292437] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   53.292440] system 00:07: iomem range 0xfeb80000-0xfebbffff has been reserved
[   53.292442] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[   53.292448] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[   53.292451] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   53.292456] system 00:0a: ioport range 0x290-0x297 has been reserved
[   53.292461] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   53.292467] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   53.292469] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   53.292472] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   53.292475] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[   53.292478] system 00:0c: iomem range 0xff780000-0xffffffff could not be reserved
[   53.322784] PCI: Bridge: 0000:00:02.0
[   53.322786]   IO window: disabled.
[   53.322789]   MEM window: disabled.
[   53.322791]   PREFETCH window: disabled.
[   53.322793] PCI: Bridge: 0000:00:03.0
[   53.322795]   IO window: disabled.
[   53.322797]   MEM window: disabled.
[   53.322799]   PREFETCH window: disabled.
[   53.322801] PCI: Bridge: 0000:00:04.0
[   53.322802]   IO window: disabled.
[   53.322804]   MEM window: disabled.
[   53.322806]   PREFETCH window: disabled.
[   53.322809] PCI: Bridge: 0000:00:10.0
[   53.322811]   IO window: c000-cfff
[   53.322814]   MEM window: faa00000-faafffff
[   53.322816]   PREFETCH window: disabled.
[   53.322829] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.322836] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   53.322842] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   53.322850] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   53.322862] NET: Registered protocol family 2
[   53.324339] Time: acpi_pm clocksource has been installed.
[   53.324357] Switched to high resolution mode on CPU 0
[   53.322697] Switched to high resolution mode on CPU 1
[   53.360339] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   53.360613] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   53.361418] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   53.361822] TCP: Hash tables configured (established 131072 bind 65536)
[   53.361825] TCP reno registered
[   53.372385] checking if image is initramfs... it is
[   53.988412] Freeing initrd memory: 7678k freed
[   53.987450] audit: initializing netlink socket (disabled)
[   53.987463] audit(1208995792.332:1): initialized
[   53.987609] highmem bounce pool size: 64 pages
[   53.989368] VFS: Disk quotas dquot_6.5.1
[   53.989434] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   53.989546] io scheduler noop registered
[   53.989548] io scheduler anticipatory registered
[   53.989550] io scheduler deadline registered
[   53.989558] io scheduler cfq registered (default)
[   53.989572] Boot video device is 0000:00:05.0
[   54.414211] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   54.414234] assign_interrupt_mode Found MSI capability
[   54.414253] Allocate Port Service[0000:00:02.0:pcie00]
[   54.414314] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   54.414335] assign_interrupt_mode Found MSI capability
[   54.414350] Allocate Port Service[0000:00:03.0:pcie00]
[   54.414406] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   54.414427] assign_interrupt_mode Found MSI capability
[   54.414441] Allocate Port Service[0000:00:04.0:pcie00]
[   54.414651] isapnp: Scanning for PnP cards...
[   54.767632] isapnp: No Plug & Play device found
[   54.793357] Real Time Clock Driver v1.12ac
[   54.793465] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.793598] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.794155] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.794868] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.794930] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   54.795062] PNP: No PS/2 controller found. Probing ports directly.
[   54.797450] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.797455] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.813590] mice: PS/2 mouse device common for all mice
[   54.813705] EISA: Probing bus 0 at eisa.0
[   54.813714] Cannot allocate resource for EISA slot 2
[   54.813731] EISA: Detected 0 cards.
[   54.813734] cpuidle: using governor ladder
[   54.813737] cpuidle: using governor menu
[   54.813819] NET: Registered protocol family 1
[   54.813840] Using IPI No-Shortcut mode
[   54.813873] registered taskstats version 1
[   54.813997]   Magic number: 4:403:153
[   54.814043]   hash matches device ttyp7
[   54.814142] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   54.814144] EDD information not available.
[   54.814408] Freeing unused kernel memory: 364k freed
[   56.047240] fuse init (API version 7.9)
[   56.491573] usbcore: registered new interface driver usbfs
[   56.491597] usbcore: registered new interface driver hub
[   56.491629] usbcore: registered new device driver usb
[   56.500534] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   56.500894] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   56.500904] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 16
[   56.500918] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   56.500921] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   56.501172] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   56.501191] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfebde000
[   56.519898] SCSI subsystem initialized
[   56.527616] libata version 3.00 loaded.
[   56.558017] usb usb1: configuration #1 chosen from 1 choice
[   56.558040] hub 1-0:1.0: USB hub found
[   56.558048] hub 1-0:1.0: 8 ports detected
[   56.628280] Floppy drive(s): fd0 is 1.44M
[   56.647686] FDC 0 is a post-1991 82077
[   56.658688] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[   56.658701] ACPI: PCI Interrupt 0000:04:05.0[A] -> Link [LNKD] -> GSI 19 (level, low) -> IRQ 17
[   56.711378] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[faaff800-faafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   56.728110] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   56.728447] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   56.728458] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 22 (level, low) -> IRQ 18
[   56.728465] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   56.987306] usb 1-3: new low speed USB device using ohci_hcd and address 2
[   57.196388] usb 1-3: configuration #1 chosen from 1 choice
[   57.247356] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:17:31:4a:30:17
[   57.247361] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   57.247811] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[   57.247822] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 21 (level, low) -> IRQ 19
[   57.247833] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   57.247835] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   57.247867] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   57.247896] ehci_hcd 0000:00:0b.1: debug port 1
[   57.247900] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   57.247912] ehci_hcd 0000:00:0b.1: irq 19, io mem 0xfebdfc00
[   57.258916] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   57.259007] usb usb2: configuration #1 chosen from 1 choice
[   57.259027] hub 2-0:1.0: USB hub found
[   57.259032] hub 2-0:1.0: 8 ports detected
[   57.363010] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   57.363331] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[   57.363341] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 20
[   57.363359] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   57.363367] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   57.363625] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 23
[   57.363627] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 23 (level, low) -> IRQ 16
[   57.363644] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   57.363651] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   57.365668] sata_nv 0000:00:0e.0: version 3.5
[   57.365676] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 20
[   57.365702] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   57.366073] scsi0 : sata_nv
[   57.366117] scsi1 : sata_nv
[   57.366258] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe000 irq 20
[   57.366261] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[   57.391779] usbcore: registered new interface driver hiddev
[   57.390017] usb 1-3: USB disconnect, address 2
[   57.674354] ata1: SATA link down (SStatus 0 SControl 300)
[   57.887083] usbcore: registered new interface driver usbhid
[   57.887087] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   57.997904] ata2: SATA link down (SStatus 0 SControl 300)
[   58.008415] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 23 (level, low) -> IRQ 16
[   58.008460] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   58.008527] scsi2 : sata_nv
[   58.008585] scsi3 : sata_nv
[   58.008727] ata3: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[   58.008730] ata4: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[   58.008849] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000914769]
[   58.188870] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   58.317471] ata3: SATA link down (SStatus 0 SControl 300)
[   58.399809] usb 1-3: configuration #1 chosen from 1 choice
[   58.409861] input: Dynex 5-Button Wired Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input1
[   58.440587] input,hidraw0: USB HID v1.11 Mouse [Dynex 5-Button Wired Optical Mouse] on usb-0000:00:0b.0-3
[   58.637033] ata4: SATA link down (SStatus 0 SControl 300)
[   58.648219] pata_amd 0000:00:0d.0: version 0.3.10
[   58.648268] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   58.649365] scsi4 : pata_amd
[   58.649426] scsi5 : pata_amd
[   58.652657] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   58.652660] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   58.743119] usb 1-4: new low speed USB device using ohci_hcd and address 4
[   58.820875] ata5.00: ATA-7: Maxtor 6L250R0, BAJ41G20, max UDMA/133
[   58.820878] ata5.00: 490234752 sectors, multi 16: LBA48 
[   58.821079] ata5.01: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   58.821081] ata5.01: 160086528 sectors, multi 16: LBA 
[   58.836761] ata5.00: configured for UDMA/133
[   58.851368] ata5.01: configured for UDMA/133
[   58.959081] usb 1-4: configuration #1 chosen from 1 choice
[   58.970153] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input2
[   58.999817] input,hidraw1: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:0b.0-4
[   59.006175] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.1/input/input3
[   59.009664] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6L250R0   BAJ4 PQ: 0 ANSI: 5
[   59.009758] scsi 4:0:1:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   59.016264] Driver 'sd' needs updating - please use bus_type methods
[   59.016352] sd 4:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   59.016365] sd 4:0:0:0: [sda] Write Protect is off
[   59.016367] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.016383] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.016426] sd 4:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
[   59.016434] sd 4:0:0:0: [sda] Write Protect is off
[   59.016436] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.016449] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.016452]  sda: sda1 sda2 <<6>input,hidraw2: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:0b.0-4
[   59.063875]  sda5 sda6 >
[   59.063983] sd 4:0:0:0: [sda] Attached SCSI disk
[   59.064042] sd 4:0:1:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
[   59.064054] sd 4:0:1:0: [sdb] Write Protect is off
[   59.064056] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   59.064071] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.064114] sd 4:0:1:0: [sdb] 160086528 512-byte hardware sectors (81964 MB)
[   59.064122] sd 4:0:1:0: [sdb] Write Protect is off
[   59.064124] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   59.064137] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.064141]  sdb: sdb1
[   59.068053] sd 4:0:1:0: [sdb] Attached SCSI disk
[   59.074215] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   59.074234] sd 4:0:1:0: Attached scsi generic sg1 type 0
[   59.439423] Attempting manual resume
[   59.439426] swsusp: Resume From Partition 8:5
[   59.439428] PM: Checking swsusp image.
[   59.439580] PM: Resume from disk failed.
[   59.454147] EXT3-fs: INFO: recovery required on readonly filesystem.
[   59.454151] EXT3-fs: write access will be enabled during recovery.
[   59.826568] kjournald starting.  Commit interval 5 seconds
[   59.824826] EXT3-fs: sda1: orphan cleanup on readonly fs
[   59.824836] ext3_orphan_cleanup: deleting unreferenced inode 4899924
[   59.824861] EXT3-fs: sda1: 1 orphan inode deleted
[   59.824863] EXT3-fs: recovery complete.
[   59.826151] EXT3-fs: mounted filesystem with ordered data mode.
[   68.475567] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   68.546739] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   68.546756] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   68.702584] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   68.758615] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   68.838435] parport_pc 00:06: reported by Plug and Play ACPI
[   68.838563] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   68.890255] Linux agpgart interface v0.102
[   68.911071] input: Power Button (FF) as /devices/virtual/input/input5
[   68.942095] ACPI: Power Button (FF) [PWRF]
[   68.942242] input: Power Button (CM) as /devices/virtual/input/input6
[   68.966062] ACPI: Power Button (CM) [PWRB]
[   69.709505] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   69.709511] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 18
[   69.709537] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   71.503856] lp0: using parport0 (interrupt-driven).
[   71.562625] Adding 2835432k swap on /dev/sda5.  Priority:-1 extents:1 across:2835432k
[   72.094726] EXT3 FS on sda1, internal journal
[   72.205040] device-mapper: uevent: version 1.0.3
[   72.205076] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   75.117465] kjournald starting.  Commit interval 5 seconds
[   75.117625] EXT3 FS on sda6, internal journal
[   75.117629] EXT3-fs: mounted filesystem with ordered data mode.
[   75.133333] kjournald starting.  Commit interval 5 seconds
[   75.140702] EXT3 FS on sdb1, internal journal
[   75.140705] EXT3-fs: mounted filesystem with ordered data mode.
[   75.479939] ip_tables: (C) 2000-2006 Netfilter Core Team
[   75.832066] No dock devices found.
[   76.090456] powernow-k8: Found 1 AMD Athlon(tm)64 X2 Dual Core Processor  3800+ processors (2 cpu cores) (version 2.20.00)
[   76.092241] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[   76.092245] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[   76.092248] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   76.985961] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   76.985967] apm: disabled - APM is not SMP safe.
[   77.106729] ppdev: user-space parallel port driver
[   77.604726] audit(1208995817.173:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5179 profile="/usr/sbin/cupsd" namespace="default"
[   78.443040] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   78.443045] vboxdrv: Successfully done.
[   78.443823] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   78.443826] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).
[   78.551574] Clocksource tsc unstable (delta = -234012226 ns)
[   79.564687] Bluetooth: Core ver 2.11
[   79.564765] NET: Registered protocol family 31
[   79.564769] Bluetooth: HCI device and connection manager initialized
[   79.564773] Bluetooth: HCI socket layer initialized
[   79.573163] Bluetooth: L2CAP ver 2.9
[   79.573168] Bluetooth: L2CAP socket layer initialized
[   79.589859] Bluetooth: RFCOMM socket layer initialized
[   79.589872] Bluetooth: RFCOMM TTY layer initialized
[   79.589874] Bluetooth: RFCOMM ver 1.8
[   81.174844] NET: Registered protocol family 17

```

---

### Post by JohnMutXB on 2008-05-04
I seem to be having the same issue. My DVD-RW was working fine in Ubuntu 7.10, but in the upgrade to 8.04, it doesn't get mounted anymore. It still works outside of Ubuntu, and if you put a CD or DVD in, it will spin up and the lights work, but it doesn't seem to mount anywhere. I'm not sure if it's relevant, but I think I had a dvd playing while part of the 8.04 upgrade was installing. Since the original poster mentioned that he installed from a DVD, it seems that maybe it has something to do with the DVD drive being in use during some portion of the hardware detection process.

---

### Post by deemon5 on 2008-08-22
I just installed kubuntu from my dvd drive and now neither works, sound like I have the same problem as the above....  any ideas????  dvd drives worked with anouther linux  that uses kde, is the problem with kde4???

---

### Post by ejs7597 on 2008-08-23
I think it has to do with the new kernel. They have changed how the cdrom and dvd drives are mounted, but I haven't found a good answer yet. Mine shows up under /media now.

---

### Post by ozguitarplayer on 2008-11-27
there must be an answer, I have the same problem....anyone got a suggestion?

---

### Post by jonalexdeval on 2008-11-29
I'm having a similar problem.  Just installed kubuntu 8.10.  My external USB DVD-RW was working fine in Ubuntu GNOME 8.10, but now that I've installed the Kubuntu desktop it doesn't mount at all in Kubuntu.  In GNOME it mounts flawlessly.  My internal CD/DVD-ROM mounts fine in Kubuntu.

Kubuntu isn't detecting my wireless USB mouse either.  I'm a newbie to Ubuntu and Linux so could someone point me in the right direction?

---


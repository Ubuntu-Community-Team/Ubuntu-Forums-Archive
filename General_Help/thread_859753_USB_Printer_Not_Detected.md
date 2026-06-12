---
title: "USB Printer Not Detected"
date: 2008-07-14
forum: General Help
---

### Post by mkaminski on 2008-07-14
Hello,

I originally had gutsy gibbon installed working fine with my HP Laserjet 1018 and my HP PSC 2410. Then the printer connectivity would become temperamental, then eventually stop working at all. I upgraded to Hardy Heron and still have the same issue.

My ipod works fine, as you can see below in the lsusb output:

```

mike@desktop:~$ lsusb
Bus 005 Device 002: ID 05ac:1301 Apple Computer, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

dmesg output:

```

mike@desktop:~/foo2zjs$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3600
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7700 checksum 0
[    0.000000] ACPI: RSDP 000F7700, 0014 (r0 VIAK8M)
[    0.000000] ACPI: RSDT 3FEE3040, 002C (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE30C0, 0074 (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEE3180, 5224 (r1 VIAK8M AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEE0000, 0040
[    0.000000] ACPI: APIC 3FEE8400, 005A (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
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
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259811
[    0.000000] Kernel command line: root=UUID=55bfda3c-f114-4957-91dc-6f23bb04d55d ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1799.858 MHz processor.
[   20.805478] Console: colour VGA+ 80x25
[   20.805481] console [tty0] enabled
[   20.805906] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.806566] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.829323] Memory: 1026296k/1047424k available (2177k kernel code, 20448k reserved, 1006k data, 368k init, 129920k highmem)
[   20.829331] virtual kernel memory layout:
[   20.829332]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.829333]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.829334]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.829336]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.829337]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.829338]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   20.829339]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   20.829343] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.829380] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   20.909279] Calibrating delay using timer specific routine.. 3604.31 BogoMIPS (lpj=7208633)
[   20.909307] Security Framework initialized
[   20.909313] SELinux:  Disabled at boot.
[   20.909329] AppArmor: AppArmor initialized
[   20.909333] Failure registering capabilities with primary security module.
[   20.909341] Mount-cache hash table entries: 512
[   20.909455] Initializing cgroup subsys ns
[   20.909459] Initializing cgroup subsys cpuacct
[   20.909468] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   20.909476] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.909479] CPU: L2 Cache: 256K (64 bytes/line)
[   20.909482] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   20.909492] Compat vDSO mapped to ffffe000.
[   20.909502] Checking 'hlt' instruction... OK.
[   20.925526] SMP alternatives: switching to UP code
[   20.926604] Freeing SMP alternatives: 11k freed
[   20.926719] Early unpacking initramfs... done
[   21.266428] ACPI: Core revision 20070126
[   21.266493] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.269115] CPU0: AMD Sempron(tm) Processor 3100+ stepping 02
[   21.269139] Total of 1 processors activated (3604.31 BogoMIPS).
[   21.269641] ENABLING IO-APIC IRQs
[   21.269962] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   21.416508] Brought up 1 CPUs
[   21.416557] CPU0 attaching sched-domain:
[   21.416559]  domain 0: span 01
[   21.416561]   groups: 01
[   21.416715] net_namespace: 64 bytes
[   21.416720] Booting paravirtualized kernel on bare hardware
[   21.417182] Time: 19:59:19  Date: 07/14/08
[   21.417204] NET: Registered protocol family 16
[   21.417367] EISA bus registered
[   21.417401] ACPI: bus type pci registered
[   21.424965] PCI: PCI BIOS revision 2.10 entry at 0xf9ff0, last bus=1
[   21.424968] PCI: Using configuration type 1
[   21.424971] Setting up standard PCI resources
[   21.427645] ACPI: EC: Look up EC in DSDT
[   21.432519] ACPI: Interpreter enabled
[   21.432525] ACPI: (supports S0 S1 S4 S5)
[   21.432539] ACPI: Using IOAPIC for interrupt routing
[   21.438017] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.438917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.489198] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *7 10 11 12)
[   21.489349] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12)
[   21.489495] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[   21.489639] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
[   21.489765] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.489886] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.490007] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.490128] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   21.490277] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   21.490415] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   21.490553] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   21.490713] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
[   21.490809] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.490836] pnp: PnP ACPI init
[   21.490843] ACPI: bus type pnp registered
[   21.491079] pnpacpi: exceeded the max number of mem resources: 12
[   21.494267] pnp: PnP ACPI: found 12 devices
[   21.494269] ACPI: ACPI bus type pnp unregistered
[   21.494273] PnPBIOS: Disabled by ACPI PNP
[   21.494458] PCI: Using ACPI for IRQ routing
[   21.494461] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.524326] NET: Registered protocol family 8
[   21.524328] NET: Registered protocol family 20
[   21.524385] AppArmor: AppArmor Filesystem Enabled
[   21.528289] Time: tsc clocksource has been installed.
[   21.536311] system 00:00: iomem range 0xcd000-0xcffff has been reserved
[   21.536314] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   21.536317] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   21.536320] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   21.536323] system 00:00: iomem range 0x3ff00000-0x3fffffff has been reserved
[   21.536326] system 00:00: iomem range 0x3fee0000-0x3fefffff could not be reserved
[   21.536329] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   21.536332] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   21.536335] system 00:00: iomem range 0x100000-0x3fedffff could not be reserved
[   21.536338] system 00:00: iomem range 0x0-0x0 could not be reserved
[   21.536340] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   21.536343] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.536350] system 00:02: ioport range 0x4000-0x407f has been reserved
[   21.536353] system 00:02: ioport range 0x5000-0x500f has been reserved
[   21.536359] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   21.536362] system 00:03: ioport range 0x800-0x805 has been reserved
[   21.536364] system 00:03: ioport range 0x290-0x297 has been reserved
[   21.566680] PCI: Bridge: 0000:00:01.0
[   21.566682]   IO window: disabled.
[   21.566686]   MEM window: f0000000-f7ffffff
[   21.566689]   PREFETCH window: e0000000-efffffff
[   21.566704] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.566715] NET: Registered protocol family 2
[   21.604240] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.604531] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.605430] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.605865] TCP: Hash tables configured (established 131072 bind 65536)
[   21.605869] TCP reno registered
[   21.616279] checking if image is initramfs... it is
[   22.067427] Switched to high resolution mode on CPU 0
[   22.269851] Freeing initrd memory: 7312k freed
[   22.270392] audit: initializing netlink socket (disabled)
[   22.270404] audit(1216065559.336:1): initialized
[   22.270534] highmem bounce pool size: 64 pages
[   22.272126] VFS: Disk quotas dquot_6.5.1
[   22.272195] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.272320] io scheduler noop registered
[   22.272323] io scheduler anticipatory registered
[   22.272324] io scheduler deadline registered
[   22.272334] io scheduler cfq registered (default)
[   22.272347] PCI: VIA PCI bridge detected. Disabling DAC.
[   22.272424] Boot video device is 0000:01:00.0
[   22.272665] isapnp: Scanning for PnP cards...
[   22.626307] isapnp: No Plug & Play device found
[   22.652182] Real Time Clock Driver v1.12ac
[   22.652268] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.653255] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.653319] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.653402] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.653776] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.653780] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.658574] mice: PS/2 mouse device common for all mice
[   22.658679] EISA: Probing bus 0 at eisa.0
[   22.658697] Cannot allocate resource for EISA slot 4
[   22.658699] Cannot allocate resource for EISA slot 5
[   22.658713] EISA: Detected 0 cards.
[   22.658716] cpuidle: using governor ladder
[   22.658718] cpuidle: using governor menu
[   22.658798] NET: Registered protocol family 1
[   22.658822] Using IPI No-Shortcut mode
[   22.658852] registered taskstats version 1
[   22.658950]   Magic number: 0:516:1001
[   22.658958]   hash matches device ttye0
[   22.659074]   hash matches device 00:03
[   22.659092] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.659094] EDD information not available.
[   22.659326] Freeing unused kernel memory: 368k freed
[   22.686355] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.923429] fuse init (API version 7.9)
[   23.940770] ACPI: Fan [FAN] (on)
[   23.948469] ACPI: Thermal Zone [THRM] (40 C)
[   24.666998] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.667033] 8139cp 0000:00:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   24.667036] 8139cp 0000:00:0d.0: Try the "8139too" driver instead.
[   24.678972] 8139too Fast Ethernet driver 0.9.28
[   24.680293] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 19 (level, low) -> IRQ 16
[   24.680800] eth0: RealTek RTL8139 at 0xd000, 00:e0:4c:e3:f5:2c, IRQ 16
[   24.680803] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   24.691034] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 17
[   24.743732] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[f8012000-f80127ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.774966] SCSI subsystem initialized
[   24.834742] usbcore: registered new interface driver usbfs
[   24.834763] usbcore: registered new interface driver hub
[   24.842681] libata version 3.00 loaded.
[   24.850709] usbcore: registered new device driver usb
[   24.878642] USB Universal Host Controller Interface driver v3.0
[   24.929374] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   24.929383] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   24.929393] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   24.929595] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   24.929625] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000e200
[   24.929748] usb usb1: configuration #1 chosen from 1 choice
[   24.929769] hub 1-0:1.0: USB hub found
[   24.929774] hub 1-0:1.0: 2 ports detected
[   25.030443] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.030455] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   25.030479] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   25.030500] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000e300
[   25.030594] usb usb2: configuration #1 chosen from 1 choice
[   25.030614] hub 2-0:1.0: USB hub found
[   25.030619] hub 2-0:1.0: 2 ports detected
[   25.062246] FDC 0 is a post-1991 82077
[   25.134266] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.134279] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   25.134300] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.134321] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000e400
[   25.134427] usb usb3: configuration #1 chosen from 1 choice
[   25.134448] hub 3-0:1.0: USB hub found
[   25.134453] hub 3-0:1.0: 2 ports detected
[   25.238120] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.238133] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   25.238156] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   25.238177] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000e500
[   25.238283] usb usb4: configuration #1 chosen from 1 choice
[   25.238305] hub 4-0:1.0: USB hub found
[   25.238310] hub 4-0:1.0: 2 ports detected
[   25.342020] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
[   25.342034] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   25.342057] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   25.342094] ehci_hcd 0000:00:10.4: irq 18, io mem 0xf8011000
[   25.353795] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.353902] usb usb5: configuration #1 chosen from 1 choice
[   25.353924] hub 5-0:1.0: USB hub found
[   25.353930] hub 5-0:1.0: 8 ports detected
[   25.458145] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   25.458153] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   25.458205] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   25.458225] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   25.458246] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   25.462816] sata_via 0000:00:0f.0: version 2.3
[   25.462834] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   25.462872] sata_via 0000:00:0f.0: routed to hard irq line 10
[   25.467244] scsi0 : sata_via
[   25.469902] scsi1 : sata_via
[   25.469956] ata1: SATA max UDMA/133 cmd 0xe600 ctl 0xdc00 bmdma 0xdf00 irq 19
[   25.469959] ata2: SATA max UDMA/133 cmd 0xdd00 ctl 0xde00 bmdma 0xdf08 irq 19
[   25.673369] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.837244] ata1.00: ATA-7: WDC WD400JD-22LSA0, 06.01D06, max UDMA/133
[   25.837249] ata1.00: 78165360 sectors, multi 16: LBA48 
[   25.845218] ata1.00: configured for UDMA/133
[   26.048600] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   26.059997] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400JD-22LS 06.0 PQ: 0 ANSI: 5
[   26.060460] pata_via 0000:00:0f.1: version 0.3.3
[   26.060482] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
[   26.061512] scsi2 : pata_via
[   26.062100] scsi3 : pata_via
[   26.063137] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe100 irq 14
[   26.063141] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe108 irq 15
[   26.068995] Driver 'sd' needs updating - please use bus_type methods
[   26.069070] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   26.069081] sd 0:0:0:0: [sda] Write Protect is off
[   26.069083] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.069097] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.069135] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   26.069143] sd 0:0:0:0: [sda] Write Protect is off
[   26.069145] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.069157] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.069160]  sda: sda1 sda2 < sda5 >
[   26.097317] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.102902] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.196450] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[003067000006edd7]
[   26.421906] Attempting manual resume
[   26.421910] swsusp: Resume From Partition 8:5
[   26.421912] PM: Checking swsusp image.
[   26.422077] PM: Resume from disk failed.
[   26.463749] kjournald starting.  Commit interval 5 seconds
[   26.463762] EXT3-fs: mounted filesystem with ordered data mode.
[   26.747747] ata4.01: ATAPI: LITE-ON DVDRW SHW-160P6S, PS01, max UDMA/66
[   26.747761] ata4.01: limited to UDMA/33 due to 40-wire cable
[   26.935304] ata4.01: configured for UDMA/33
[   26.936154] scsi 3:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PS01 PQ: 0 ANSI: 5
[   26.936217] scsi 3:0:1:0: Attached scsi generic sg1 type 5
[   35.050832] Linux agpgart interface v0.102
[   35.304951] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   35.306255] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.352822] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.396789] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.432700] agpgart: Detected AGP bridge 0
[   35.436449] agpgart: AGP aperture is 128M @ 0xd8000000
[   35.692812] input: Power Button (FF) as /devices/virtual/input/input3
[   35.704191] ACPI: Power Button (FF) [PWRF]
[   35.704304] input: Power Button (CM) as /devices/virtual/input/input4
[   35.720167] ACPI: Power Button (CM) [PWRB]
[   35.720279] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.736137] ACPI: Sleep Button (CM) [SLPB]
[   36.588895] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   37.035336] NET: Registered protocol family 17
[   37.474596] Driver 'sr' needs updating - please use bus_type methods
[   37.485148] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   37.485153] Uniform CD-ROM driver Revision: 3.20
[   37.485229] sr 3:0:1:0: Attached scsi CD-ROM sr0
[   37.694310] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   37.694318] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   37.694453] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   37.935451] nvidia: module license 'NVIDIA' taints kernel.
[   38.446360] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   38.446592] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   40.364271] lp: driver loaded but no devices found
[   40.586492] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   41.147599] EXT3 FS on sda1, internal journal
[   42.544298] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.976225] RPC: Registered udp transport module.
[   42.976229] RPC: Registered tcp transport module.
[   43.473431] NET: Registered protocol family 10
[   43.473632] lo: Disabled Privacy Extensions
[   43.492963] No dock devices found.
[   43.972102] powernow-k8: Found 1 AMD Sempron(tm) Processor 3100+ processors (1 cpu cores) (version 2.20.00)
[   43.972137] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   43.972139] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   44.775084] ppdev: user-space parallel port driver
[   44.912883] audit(1216065582.696:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5010 profile="/usr/sbin/cupsd" namespace="default"
[   44.948958] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.948963] apm: overridden by ACPI.
[   45.848216] Bluetooth: Core ver 2.11
[   45.848803] NET: Registered protocol family 31
[   45.848808] Bluetooth: HCI device and connection manager initialized
[   45.848812] Bluetooth: HCI socket layer initialized
[   45.870327] Bluetooth: L2CAP ver 2.9
[   45.870332] Bluetooth: L2CAP socket layer initialized
[   45.923768] Bluetooth: RFCOMM socket layer initialized
[   45.923784] Bluetooth: RFCOMM TTY layer initialized
[   45.923786] Bluetooth: RFCOMM ver 1.8
[   47.021627] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   47.021908] agpgart: Device is in legacy mode, falling back to 2.x
[   47.022070] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   47.022288] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   88.531219] Marking TSC unstable due to: cpufreq changes.
[   88.544838] Time: acpi_pm clocksource has been installed.
[   88.945128] Clocksource tsc unstable (delta = -183884926 ns)
[   52.050921] eth0: no IPv6 routers present
[24405.411837] usb 5-4: new high speed USB device using ehci_hcd and address 2
[24405.545076] usb 5-4: configuration #1 chosen from 2 choices
[24405.761004] usbcore: registered new interface driver libusual
[24405.844876] Initializing USB Mass Storage driver...
[24405.866926] scsi4 : SCSI emulation for USB Mass Storage devices
[24405.882478] usbcore: registered new interface driver usb-storage
[24405.882787] USB Mass Storage support registered.
[24405.883179] usb-storage: device found at 2
[24405.883184] usb-storage: waiting for device to settle before scanning
[13541.807548] usb-storage: device scan complete
[13541.808039] scsi 4:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 2
[13541.819517] sd 4:0:0:0: [sdb] 495616 2048-byte hardware sectors (1015 MB)
[13541.820125] sd 4:0:0:0: [sdb] Write Protect is off
[13541.820129] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[13541.820131] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[13541.822243] sd 4:0:0:0: [sdb] 495616 2048-byte hardware sectors (1015 MB)
[13541.822869] sd 4:0:0:0: [sdb] Write Protect is off
[13541.822873] sd 4:0:0:0: [sdb] Mode Sense: 64 00 00 08
[13541.822876] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[13541.822881]  sdb: unknown partition table
[13541.851236] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[13541.851275] sd 4:0:0:0: Attached scsi generic sg2 type 0
[14013.431833] audit(1216085439.264:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=9253 profile="/usr/sbin/cupsd" namespace="default"
[14101.052164] audit(1216085558.452:4): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=9317 profile="/usr/sbin/cupsd" namespace="default"

```

I've tried restarting cups, reinstalling hplip w/ python, and still nothing. Any help?

---

### Post by mkaminski on 2008-07-14
fixed... had a "cabling" issue :)

---


---
title: "[SOLVED] touchpad, wlan, eth, bluetooth, all not working this morning when i booted"
date: 2008-08-22
forum: Hardware
---

### Post by bigstras on 2008-08-22
HELP!!
My gateway laptop was working perfectly last night.  I spent some time the other day trying to get my usb bluetooth card to transmit to my bluetooth headset.  I even got my cell phone to be able to act as a remote.  I dont know what I could have done.

It all worked, and then I started up my computer today.  Everything works fine in windows, so i know it's not a hardware problem.

Now the synaptics touchpad wont work.
It does not show up in /proc/bus/input/devices
I dont know if it did before, but the only thing that is there now is "macintosh mouse button emulation"

Wireless and wired networks also dont show up.
output from iwconfig is:
```
lo        no wireless extensions.

```
it used to have wlan0 and eth0 as well.

Bluetooth will not work, even though, at the bottom of dmesg, it is recognizing that something is being plugged into the usb port.

I've never really had a problem like this before, so I dont even know where to start.
uname -r ```
2.6.24-19-generic
```

below is the dmesg output, output from lspci, lsmod are attached.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003beb0000 (usable)
[    0.000000]  BIOS-e820: 000000003beb0000 - 000000003beb8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003beb8000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 62MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8220
[    0.000000] Entering add_active_range(0, 0, 245424) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245424
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245424
[    0.000000] On node 0 totalpages: 245424
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 125 pages used for memmap
[    0.000000]   HighMem zone: 15923 pages, LIFO batch:3
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8190 checksum 0
[    0.000000] ACPI: RSDP 000F8190, 0014 (r0 GATEWA)
[    0.000000] ACPI: RSDT 3BEB37C8, 0034 (r1 GATEWA M300     20060124  LTP        0)
[    0.000000] ACPI: FACP 3BEB7DDE, 0074 (r1 GATEWA M300     20060124 PTL        5F)
[    0.000000] ACPI: DSDT 3BEB37FC, 45E2 (r1 GATEWA M300     20060124 MSFT  100000E)
[    0.000000] ACPI: FACS 3BEB8FC0, 0040
[    0.000000] ACPI: SSDT 3BEB7E52, 0118 (r1 PTLTD  POWERNOW 20060124  LTP        1)
[    0.000000] ACPI: APIC 3BEB7F6A, 005A (r1 GATEWA M300     20060124  LTP        0)
[    0.000000] ACPI: MCFG 3BEB7FC4, 003C (r1 GATEWA M300     20060124  LTP        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ce000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ce000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243507
[    0.000000] Kernel command line: root=UUID=1da9cf06-d0fb-4398-8b72-51317f55c28e ro i8402.nomux=1 single
[    0.000000] Unknown boot option `i8402.nomux=1': ignoring
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2193.707 MHz processor.
[   14.181420] Console: colour VGA+ 80x25
[   14.181423] console [tty0] enabled
[   14.184499] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.185010] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.205309] Memory: 960772k/981696k available (2177k kernel code, 20292k reserved, 1006k data, 368k init, 64192k highmem)
[   14.205366] virtual kernel memory layout:
[   14.205367]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.205368]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.205369]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.205370]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.205371]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   14.205372]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   14.205373]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   14.205702] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.205814] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.285753] Calibrating delay using timer specific routine.. 4391.83 BogoMIPS (lpj=8783667)
[   14.285856] Security Framework initialized
[   14.285902] SELinux:  Disabled at boot.
[   14.285956] AppArmor: AppArmor initialized
[   14.285999] Failure registering capabilities with primary security module.
[   14.286048] Mount-cache hash table entries: 512
[   14.286188] Initializing cgroup subsys ns
[   14.286233] Initializing cgroup subsys cpuacct
[   14.286282] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   14.286290] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.286335] CPU: L2 Cache: 1024K (64 bytes/line)
[   14.286378] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   14.286386] Compat vDSO mapped to ffffe000.
[   14.286436] Checking 'hlt' instruction... OK.
[   14.302029] SMP alternatives: switching to UP code
[   14.303107] Freeing SMP alternatives: 11k freed
[   14.303255] Early unpacking initramfs... done
[   14.593106] ACPI: Core revision 20070126
[   14.593202] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.597076] CPU0: AMD Turion(tm) 64 Mobile Technology ML-40 stepping 02
[   14.597205] Total of 1 processors activated (4391.83 BogoMIPS).
[   14.597424] ENABLING IO-APIC IRQs
[   14.597645] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.745036] Brought up 1 CPUs
[   14.745095] CPU0 attaching sched-domain:
[   14.745097]  domain 0: span 01
[   14.745099]   groups: 01
[   14.745244] net_namespace: 64 bytes
[   14.745291] Booting paravirtualized kernel on bare hardware
[   14.745718] Time:  9:41:52  Date: 08/22/08
[   14.745780] NET: Registered protocol family 16
[   14.745967] EISA bus registered
[   14.746029] ACPI: bus type pci registered
[   14.746252] PCI: PCI BIOS revision 2.10 entry at 0xfd89d, last bus=5
[   14.746295] PCI: Using configuration type 1
[   14.746348] Setting up standard PCI resources
[   14.747564] ACPI: EC: Look up EC in DSDT
[   14.748621] ACPI: Interpreter enabled
[   14.748663] ACPI: (supports S0 S3 S4 S5)
[   14.748847] ACPI: Using IOAPIC for interrupt routing
[   14.749410] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.752943] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   14.752990] ACPI: EC: driver started in interrupt mode
[   14.753060] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.754586] PCI: Transparent bridge - 0000:00:14.4
[   14.754700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.754798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   14.754885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   14.754974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   14.756536] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   14.756857] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   14.757185] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   14.757504] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   14.757830] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   14.758155] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   14.758474] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   14.758794] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   14.759116] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   14.759511] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.759576] pnp: PnP ACPI init
[   14.759621] ACPI: bus type pnp registered
[   14.761739] pnp: PnP ACPI: found 10 devices
[   14.761781] ACPI: ACPI bus type pnp unregistered
[   14.761824] PnPBIOS: Disabled by ACPI PNP
[   14.762030] PCI: Using ACPI for IRQ routing
[   14.762073] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.792922] NET: Registered protocol family 8
[   14.792965] NET: Registered protocol family 20
[   14.793054] AppArmor: AppArmor Filesystem Enabled
[   14.796910] Time: tsc clocksource has been installed.
[   14.804921] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   14.804966] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   14.805016] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.805070] system 00:06: iomem range 0xe0000-0xfffff could not be reserved
[   14.805114] system 00:06: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.805164] system 00:06: iomem range 0x0-0xfff could not be reserved
[   14.805209] system 00:09: ioport range 0x1080-0x1080 has been reserved
[   14.805253] system 00:09: ioport range 0x220-0x22f has been reserved
[   14.805297] system 00:09: ioport range 0x40b-0x40b has been reserved
[   14.805341] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   14.805385] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[   14.805428] system 00:09: ioport range 0x530-0x537 has been reserved
[   14.805472] system 00:09: ioport range 0xc00-0xc01 has been reserved
[   14.805515] system 00:09: ioport range 0xc14-0xc14 has been reserved
[   14.805558] system 00:09: ioport range 0xc50-0xc52 has been reserved
[   14.805602] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[   14.805646] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[   14.805690] system 00:09: ioport range 0xcd4-0xcd5 has been reserved
[   14.805733] system 00:09: ioport range 0xcd6-0xcd7 has been reserved
[   14.805777] system 00:09: ioport range 0xcd8-0xcdf has been reserved
[   14.805821] system 00:09: ioport range 0x8000-0x805f has been reserved
[   14.805866] system 00:09: ioport range 0xf40-0xf47 has been reserved
[   14.805909] system 00:09: ioport range 0x280-0x293 has been reserved
[   14.805957] system 00:09: ioport range 0x87f-0x87f has been reserved
[   14.836244] PCI: Bridge: 0000:00:01.0
[   14.836285]   IO window: 9000-9fff
[   14.836328]   MEM window: d0100000-d01fffff
[   14.836370]   PREFETCH window: d4000000-d7ffffff
[   14.836413] PCI: Bridge: 0000:00:06.0
[   14.836455]   IO window: a000-afff
[   14.836497]   MEM window: d0200000-d02fffff
[   14.836539]   PREFETCH window: disabled.
[   14.836589] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   14.836631]   IO window: 0000b400-0000b4ff
[   14.836677]   IO window: 0000b800-0000b8ff
[   14.836722]   PREFETCH window: 50000000-53ffffff
[   14.836769]   MEM window: 54000000-57ffffff
[   14.836814] PCI: Bridge: 0000:00:14.4
[   14.836859]   IO window: b000-bfff
[   14.836904]   MEM window: d0300000-d03fffff
[   14.836949]   PREFETCH window: disabled.
[   14.837008] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   14.837032] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 23 (level, low) -> IRQ 16
[   14.837119] PCI: Setting latency timer of device 0000:05:09.0 to 64
[   14.837131] NET: Registered protocol family 2
[   14.876842] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.877155] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.878887] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.879555] TCP: Hash tables configured (established 131072 bind 65536)
[   14.879599] TCP reno registered
[   14.888908] checking if image is initramfs... it is
[   15.336012] Switched to high resolution mode on CPU 0
[   15.445506] Freeing initrd memory: 7673k freed
[   15.446129] audit: initializing netlink socket (disabled)
[   15.446182] audit(1219398112.136:1): initialized
[   15.446369] highmem bounce pool size: 64 pages
[   15.447796] VFS: Disk quotas dquot_6.5.1
[   15.447895] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.448044] io scheduler noop registered
[   15.448086] io scheduler anticipatory registered
[   15.448128] io scheduler deadline registered
[   15.448176] io scheduler cfq registered (default)
[   15.448225] PCI: MSI quirk detected. MSI deactivated.
[   16.102648] Boot video device is 0000:01:05.0
[   16.102744] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.102763] assign_interrupt_mode Found MSI capability
[   16.102806] Allocate Port Service[0000:00:06.0:pcie00]
[   16.102969] isapnp: Scanning for PnP cards...
[   16.456830] isapnp: No Plug & Play device found
[   16.477725] Real Time Clock Driver v1.12ac
[   16.477863] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.478331] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   16.478419] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   16.478965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.479067] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.479181] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.481626] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.481671] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.482193] mice: PS/2 mouse device common for all mice
[   16.482326] EISA: Probing bus 0 at eisa.0
[   16.482373] Cannot allocate resource for EISA slot 1
[   16.482441] Cannot allocate resource for EISA slot 8
[   16.482483] EISA: Detected 0 cards.
[   16.482526] cpuidle: using governor ladder
[   16.482567] cpuidle: using governor menu
[   16.482690] NET: Registered protocol family 1
[   16.482752] Using IPI No-Shortcut mode
[   16.482827] registered taskstats version 1
[   16.482966]   Magic number: 4:750:677
[   16.483215] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.483258] EDD information not available.
[   16.483760] Freeing unused kernel memory: 368k freed
[   16.517911] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.688277] fuse init (API version 7.9)
[   16.707194] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.707382] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.708872] ACPI: Thermal Zone [THRM] (77 C)
[   17.252673] usbcore: registered new interface driver usbfs
[   17.252744] usbcore: registered new interface driver hub
[   17.264626] usbcore: registered new device driver usb
[   17.276622] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.276676] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   17.276776] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.277089] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   17.277157] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0000000
[   17.304820] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.304874] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.336599] usb usb1: configuration #1 chosen from 1 choice
[   17.336671] hub 1-0:1.0: USB hub found
[   17.336722] hub 1-0:1.0: 4 ports detected
[   17.440413] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   17.440519] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.440581] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   17.440644] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd0001000
[   17.500294] usb usb2: configuration #1 chosen from 1 choice
[   17.500362] hub 2-0:1.0: USB hub found
[   17.500412] hub 2-0:1.0: 4 ports detected
[   17.604202] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[   17.604304] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.604372] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   17.604477] ehci_hcd 0000:00:13.2: irq 18, io mem 0xd0002000
[   17.743771] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   17.755760] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.755920] usb usb3: configuration #1 chosen from 1 choice
[   17.755980] hub 3-0:1.0: USB hub found
[   17.756026] hub 3-0:1.0: 8 ports detected
[   17.859725] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
[   17.859800] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[   17.859890] ATIIXP: not 100% native mode: will probe irqs later
[   17.859940]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   17.860070]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   17.860193] Probing IDE interface ide0...
[   18.482478] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   18.695225] usb 1-2: configuration #1 chosen from 1 choice
[   18.818312] hda: FUJITSU MHV2080AT PL, ATA DISK drive
[   18.818426] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   18.822081] hda: UDMA/100 mode selected
[   18.825645] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   18.896932] Probing IDE interface ide1...
[   20.303707] hdc: PHILIPS DVD+/-RW SDVD8820, ATAPI CD/DVD-ROM drive
[   20.303888] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   20.304200] hdc: UDMA/33 mode selected
[   20.308267] ide1 at 0x170-0x177,0x376 on irq 15
[   20.315598] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 21 (level, low) -> IRQ 21
[   20.365440] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0306800-d0306fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   20.367211] SCSI subsystem initialized
[   20.376139] libata version 3.00 loaded.
[   20.392349] hda: max request size: 128KiB
[   20.392721] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63
[   20.396885] hda: cache flushes supported
[   20.396964]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 >
[   20.474976] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   20.475230] Uniform CD-ROM driver Revision: 3.20
[   25.970437] kjournald starting.  Commit interval 5 seconds
[   25.970497] EXT3-fs: mounted filesystem with ordered data mode.
[   45.357735] EXT3 FS on hda5, internal journal
[   46.525874] kjournald starting.  Commit interval 60 seconds
[   46.526107] EXT3 FS on hda1, internal journal
[   46.526112] EXT3-fs: mounted filesystem with ordered data mode.
[   47.056609] kjournald starting.  Commit interval 60 seconds
[   47.056901] EXT3 FS on hda2, internal journal
[   47.056904] EXT3-fs: mounted filesystem with ordered data mode.
[   50.073650] Adding 1048568k swap on /extraswap.  Priority:-1 extents:298 across:1092560k
[  110.435714] audit(1219412607.928:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=10851 profile="/usr/sbin/cupsd" namespace="default"
[  992.183241] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  992.183250] usb 1-2: USB disconnect, address 3
[  993.162905] usb 1-2: new full speed USB device using ohci_hcd and address 5
[  993.376228] usb 1-2: configuration #1 chosen from 1 choice
```

Please help me!

---

### Post by bigstras on 2008-08-23
bump.  

Does anybody have ANY ideas as to how i can troubleshoot this.  

I assume since multiple things stopped woring at the same time that there is something tying all this together.

I use this computer for school, and I really need help getting it back up and running as soon as possible.

Thanks in advance.

---

### Post by libra1780 on 2008-08-23
first of all, your module list ist too short..
eth and wlan seem to be recognized, but modules are not loaded
maybe a depmod -a plus modprobe (insmod) of the required module fixes it

---

### Post by bigstras on 2008-08-24
yeah, i thought there was something missing there!  more like everything.  What would make it not load so many modules while its booting?  how can i diagnose where exactly the problem is?

---

### Post by libra1780 on 2008-08-24
missing dependencies for example. Blacklisted modules found in /etc/modprobe.d/blacklist* etc..

you fix the dependencies with 
```
sudo depmod -a
```
whitch searches in your kernel directory for loadable modules and their dependencies. a reboot and done
alternatively if you know your modules name you can load it directly into kernel, for ex. your ethernet card think should be
```
sudo modprobe sky2
```

now typing ifconfig you should see your ethernet card

if you have to hurry and you're a lucky guy you have an other kernel installed.. if so on boot hit esc and select the older kernel. each kernel has its modules..

---

### Post by bigstras on 2008-08-24
yep, you nailed it.  I booted it up, went to a console and typed depmod -a.  It took about 30 seconds to finish running the command, and i rebooted.  Everything *seems* to be back in order.
I wonder whatever happened to cause all that.  

Thanks so much for the help.

---

### Post by libra1780 on 2008-08-25
happens when handling some strange driver stuff, happened to me as well. :)

---


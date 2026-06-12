---
title: "Built in SD card reader"
date: 2008-09-11
forum: Hardware
---

### Post by Millay on 2008-09-11
Hi I have  a medion md96400 laptop which also has a built in SD card reader, I purchased a 2gb card for use with the laptop and phone, when I plug the card in it fails to mount. here is what the log says:

Sep 11 14:45:55 lounge-laptop kernel: [  275.754740] pccard: PCMCIA card inserted into slot 0
Sep 11 14:45:55 lounge-laptop kernel: [  275.754866] pcmcia: registering new device pcmcia0.0
Sep 11 14:45:55 lounge-laptop kernel: [  275.755005] 0.0: GetNextTuple: No more items
Sep 11 14:45:55 lounge-laptop kernel: [  275.755013] pata_pcmcia: probe of 0.0 failed with error -12
Sep 11 14:45:55 lounge-laptop kernel: [  275.944311] 0.0: GetNextTuple: No more items
Sep 11 14:45:55 lounge-laptop kernel: [  275.944322] pata_pcmcia: probe of 0.0 failed with error -12

Im still fairly new to linux/ubuntu so any help greatly apreciated.

---

### Post by phidia on 2008-09-11
With the card inserted open a terminal and try "dmesg" and "sudo fdisk -l".
Copy/paste the output here.

---

### Post by Millay on 2008-09-11
Hi thanks for replying 

output of dmesg is:

[    0.000000]  BIOS-e820: 000000001bf50000 - 000000001c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001c000000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114496) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F83B0 checksum 0
[    0.000000] ACPI: RSDP 000F83B0, 0014 (r0 MSI   )
[    0.000000] ACPI: RSDT 1BF40000, 003C (r1 MSI    1013     12152005 MSFT       97)
[    0.000000] ACPI: FACP 1BF40200, 0081 (r2 MSI    1013     12152005 MSFT       97)
[    0.000000] ACPI: DSDT 1BF403F0, 334A (r1    MSI     1013 12152005 INTL  2002026)
[    0.000000] ACPI: FACS 1BF50000, 0040
[    0.000000] ACPI: APIC 1BF40300, 0054 (r1 MSI    OEMAPIC  12152005 MSFT       97)
[    0.000000] ACPI: WDRT 1BF40360, 0047 (r1 MSI    MSI_OEM  12152005 MSFT       97)
[    0.000000] ACPI: MCFG 1BF403B0, 003C (r1 MSI    OEMMCFG  12152005 MSFT       97)
[    0.000000] ACPI: SSDT 1BF43740, 002B (r1 OEM_ID OEMTBLID        1 INTL  2002026)
[    0.000000] ACPI: OEMB 1BF50040, 0049 (r1 MSI    MSI_OEM  12152005 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001bf40000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 114496) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001bf40000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   114496
[    0.000000] On node 0 totalpages: 114399
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1217 pages reserved
[    0.000000]   DMA zone: 2726 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1509 pages used for memmap
[    0.000000]   DMA32 zone: 108891 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 111617
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=40d3897d-44ac-479b-bc84-1320ab7d847b ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[    8.755952] time.c: Detected 1591.838 MHz processor.
[    8.756842] Console: colour VGA+ 80x25
[    8.756845] console [tty0] enabled
[    8.756865] Checking aperture...
[    8.756869] CPU 0: aperture @ c0ec000000 size 32 MB
[    8.756871] Aperture too small (32 MB)
[    8.768927] No AGP bridge found
[    8.776851] Memory: 438796k/457984k available (2489k kernel code, 18800k reserved, 1318k data, 320k init)
[    8.776907] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.853900] Calibrating delay using timer specific routine.. 3187.17 BogoMIPS (lpj=6374352)
[    8.853950] Security Framework initialized
[    8.853961] SELinux:  Disabled at boot.
[    8.853980] AppArmor: AppArmor initialized
[    8.853985] Failure registering capabilities with primary security module.
[    8.854061] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    8.854751] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    8.855082] Mount-cache hash table entries: 256
[    8.855261] Initializing cgroup subsys ns
[    8.855266] Initializing cgroup subsys cpuacct
[    8.855281] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    8.855283] CPU: L2 Cache: 1024K (64 bytes/line)
[    8.855286] CPU 0/0 -> Node 0
[    8.855314] SMP alternatives: switching to UP code
[    8.856022] Freeing SMP alternatives: 24k freed
[    8.857311] Early unpacking initramfs... done
[    9.243577] ACPI: Core revision 20070126
[    9.243637] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.286141] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    9.326217] Using local APIC timer interrupts.
[    9.389016] APIC timer calibration result 12436217
[    9.389018] Detected 12.436 MHz APIC timer.
[    9.389080] Brought up 1 CPUs
[    9.389152] CPU0 attaching sched-domain:
[    9.389156]  domain 0: span 01
[    9.389158]   groups: 01
[    9.389335] net_namespace: 120 bytes
[    9.389812] Time: 13:39:30  Date: 09/11/08
[    9.389846] NET: Registered protocol family 16
[    9.390058] ACPI: bus type pci registered
[    9.390135] PCI: Using configuration type 1
[    9.391718] ACPI: EC: Look up EC in DSDT
[    9.393597] ACPI: Interpreter enabled
[    9.393600] ACPI: (supports S0 S1 S3 S4 S5)
[    9.393615] ACPI: Using IOAPIC for interrupt routing
[    9.395138] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.404836] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
[    9.404839] ACPI: EC: driver started in interrupt mode
[    9.404924] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.406393] PCI: Transparent bridge - 0000:00:14.4
[    9.406519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.406656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    9.406736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
[    9.411928] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.412021] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 *10 11 12 14 15)
[    9.412111] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 6 7 10 11 12 14 15)
[    9.412201] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12 14 15)
[    9.412291] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 *6 7 10 11 12 14 15)
[    9.412381] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 *7 10 11 12 14 15)
[    9.412471] ACPI: PCI Interrupt Link [LNKG] (IRQs *5 6 7 10 11 12 14 15)
[    9.412561] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    9.412672] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.412704] pnp: PnP ACPI init
[    9.412711] ACPI: bus type pnp registered
[    9.416071] pnp: PnP ACPI: found 11 devices
[    9.416074] ACPI: ACPI bus type pnp unregistered
[    9.416330] PCI: Using ACPI for IRQ routing
[    9.416333] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.425068] NET: Registered protocol family 8
[    9.425070] NET: Registered protocol family 20
[    9.425192] AppArmor: AppArmor Filesystem Enabled
[    9.429017] Time: tsc clocksource has been installed.
[    9.437051] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    9.437054] system 00:07: ioport range 0x40b-0x40b has been reserved
[    9.437057] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    9.437060] system 00:07: ioport range 0xc00-0xc01 has been reserved
[    9.437062] system 00:07: ioport range 0xc14-0xc14 has been reserved
[    9.437065] system 00:07: ioport range 0xc50-0xc51 has been reserved
[    9.437068] system 00:07: ioport range 0xc52-0xc52 has been reserved
[    9.437071] system 00:07: ioport range 0xc6c-0xc6c has been reserved
[    9.437073] system 00:07: ioport range 0xc6f-0xc6f has been reserved
[    9.437076] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
[    9.437079] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
[    9.437082] system 00:07: ioport range 0xcd8-0xcdf has been reserved
[    9.437085] system 00:07: ioport range 0x4000-0x407f has been reserved
[    9.437088] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[    9.437094] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    9.437097] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    9.437103] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    9.437109] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    9.437111] system 00:0a: iomem range 0xc0000-0xd37ff has been reserved
[    9.437114] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[    9.437117] system 00:0a: iomem range 0x100000-0x1fffffff could not be reserved
[    9.437120] system 00:0a: iomem range 0x0-0x0 could not be reserved
[    9.437531] PCI: Bridge: 0000:00:01.0
[    9.437533]   IO window: d000-dfff
[    9.437536]   MEM window: fbe00000-fbefffff
[    9.437539]   PREFETCH window: f0000000-faffffff
[    9.437558] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    9.437560]   IO window: 0000e000-0000e0ff
[    9.437566]   IO window: 0000e400-0000e4ff
[    9.437571]   PREFETCH window: 30000000-33ffffff
[    9.437577]   MEM window: 34000000-37ffffff
[    9.437583] PCI: Bus 4, cardbus bridge: 0000:02:04.1
[    9.437584]   IO window: 0000ec00-0000ecff
[    9.437590]   IO window: 00001000-000010ff
[    9.437595]   PREFETCH window: 38000000-3bffffff
[    9.437600]   MEM window: 3c000000-3fffffff
[    9.437606] PCI: Bridge: 0000:00:14.4
[    9.437609]   IO window: e000-efff
[    9.437615]   MEM window: fbf00000-fbffffff
[    9.437619]   PREFETCH window: disabled.
[    9.437660] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[    9.437683] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 20 (level, low) -> IRQ 20
[    9.437739] NET: Registered protocol family 2
[    9.473085] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    9.473345] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    9.473611] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    9.473864] TCP: Hash tables configured (established 16384 bind 16384)
[    9.473867] TCP reno registered
[    9.485131] checking if image is initramfs... it is
[    9.940801] Switched to high resolution mode on CPU 0
[   10.234046] Freeing initrd memory: 7549k freed
[   10.243642] audit: initializing netlink socket (disabled)
[   10.243659] audit(1221140370.396:1): initialized
[   10.245872] VFS: Disk quotas dquot_6.5.1
[   10.245952] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   10.246105] io scheduler noop registered
[   10.246108] io scheduler anticipatory registered
[   10.246111] io scheduler deadline registered
[   10.246223] io scheduler cfq registered (default)
[   10.246230] PCI: MSI quirk detected. MSI deactivated.
[   10.296977] Boot video device is 0000:01:05.0
[   10.326995] Real Time Clock Driver v1.12ac
[   10.327099] Linux agpgart interface v0.102
[   10.327102] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.327617] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   10.327629] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   10.328285] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.328356] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.328452] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   10.328804] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.328881] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.328886] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.328889] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.328891] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.328894] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.332835] mice: PS/2 mouse device common for all mice
[   10.332880] cpuidle: using governor ladder
[   10.332883] cpuidle: using governor menu
[   10.333045] NET: Registered protocol family 1
[   10.333154] registered taskstats version 1
[   10.333282]   Magic number: 8:355:685
[   10.333447] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   10.333451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.333454] EDD information not available.
[   10.333463] Freeing unused kernel memory: 320k freed
[   10.337362] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.552943] fuse init (API version 7.9)
[   11.575748] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.578223] Marking TSC unstable due to TSC halts in idle
[   11.579963] Time: acpi_pm clocksource has been installed.
[   11.580266] ACPI: Thermal Zone [THRM] (69 C)
[   12.159963] usbcore: registered new interface driver usbfs
[   12.159990] usbcore: registered new interface driver hub
[   12.175753] usbcore: registered new device driver usb
[   12.195721] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   12.195779] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   12.196137] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   12.196400] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   12.196431] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfbdfd000
[   12.247901] SCSI subsystem initialized
[   12.258928] usb usb1: configuration #1 chosen from 1 choice
[   12.258957] hub 1-0:1.0: USB hub found
[   12.258969] hub 1-0:1.0: 4 ports detected
[   12.323632] libata version 3.00 loaded.
[   12.331677] 8139too Fast Ethernet driver 0.9.28
[   12.359921] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   12.360319] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   12.360387] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   12.360410] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfbdfe000
[   12.419748] usb usb2: configuration #1 chosen from 1 choice
[   12.419778] hub 2-0:1.0: USB hub found
[   12.419790] hub 2-0:1.0: 4 ports detected
[   12.523800] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   12.524193] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   12.524263] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   12.524326] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbdff000
[   12.535554] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.535676] usb usb3: configuration #1 chosen from 1 choice
[   12.535702] hub 3-0:1.0: USB hub found
[   12.535710] hub 3-0:1.0: 8 ports detected
[   12.639956] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 18
[   12.641157] eth0: RealTek RTL8139 at 0xe800, 00:13:d3:f0:0d:82, IRQ 18
[   12.641160] eth0:  Identified 8139 chip type 'RTL-8101'
[   12.643915] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 21
[   12.696118] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   12.706325] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   12.712631] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.712688] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   12.714087] scsi0 : pata_atiixp
[   12.714733] scsi1 : pata_atiixp
[   12.715721] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   12.715725] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   12.880104] ata1.00: ATA-6: WDC WD600VE-00HDT0, 09.07D09, max UDMA/100
[   12.880110] ata1.00: 117210240 sectors, multi 16: LBA 
[   12.887870] ata1.00: configured for UDMA/100
[   13.207865] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.00, max UDMA/33
[   13.379766] ata2.00: configured for UDMA/33
[   13.379886] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600VE-00HD 09.0 PQ: 0 ANSI: 5
[   13.382131] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[   13.392704] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.392711] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.405329] Driver 'sd' needs updating - please use bus_type methods
[   13.405425] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.405437] sd 0:0:0:0: [sda] Write Protect is off
[   13.405440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.405455] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.405502] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.405511] sd 0:0:0:0: [sda] Write Protect is off
[   13.405514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.405528] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.405532]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.689994]  sda1 sda2 < sda5 >
[   13.720589] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.726575] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.726596] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.731821] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.731828] Uniform CD-ROM driver Revision: 3.20
[   13.731886] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.982942] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000d9a9fa]
[   13.992394] Attempting manual resume
[   13.992398] swsusp: Resume From Partition 8:5
[   13.992400] PM: Checking swsusp image.
[   13.992629] PM: Resume from disk failed.
[   14.053587] kjournald starting.  Commit interval 5 seconds
[   14.053603] EXT3-fs: mounted filesystem with ordered data mode.
[   25.090772] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.336736] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.376759] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.537494] msi-laptop: Identified laptop model 'Medion MD96100'.
[   26.542215] msi-laptop: driver 0.5 successfully loaded.
[   26.608613] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   26.736624] input: Power Button (FF) as /devices/virtual/input/input3
[   26.764487] ACPI: Power Button (FF) [PWRF]
[   26.764573] input: Lid Switch as /devices/virtual/input/input4
[   26.778350] ACPI: Lid Switch [LID0]
[   26.778424] input: Sleep Button (CM) as /devices/virtual/input/input5
[   26.808505] ACPI: Sleep Button (CM) [SLPB]
[   26.808580] input: Power Button (CM) as /devices/virtual/input/input6
[   26.836483] ACPI: Power Button (CM) [PWRB]
[   27.380256] Yenta: CardBus bridge found at 0000:02:04.0 [1462:0131]
[   27.513063] Yenta: ISA IRQ mask 0x0cb8, PCI irq 19
[   27.513070] Socket status: 30000810
[   27.513073] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   27.513077] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   27.568347] Yenta: CardBus bridge found at 0000:02:04.1 [1462:0131]
[   27.696932] Yenta: ISA IRQ mask 0x0cb8, PCI irq 20
[   27.696939] Socket status: 30000006
[   27.696942] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   27.696950] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   27.696953] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   28.203787] pccard: PCMCIA card inserted into slot 0
[   28.317012] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.407906] phy0: Selected rate control algorithm 'simple'
[   28.537567] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x116eb1, caps: 0xa04713/0x0
[   28.568244] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   28.643778] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   28.747563] [fglrx] Maximum main memory to use for locked dma buffers: 369 MBytes.
[   28.747601] [fglrx] ASYNCIO init succeed!
[   28.747940] [fglrx] PAT is enabled successfully!
[   28.748485] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   28.755024] ACPI: AC Adapter [ADP1] (on-line)
[   28.795766] ACPI: Battery Slot [BAT1] (battery present)
[   28.832280] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   29.348785] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   30.706543] cs: memory probe 0xfbf00000-0xfbffffff: excluding 0xfbf00000-0xfbf1ffff 0xfbff0000-0xfbffffff
[   30.712461] pcmcia: registering new device pcmcia0.0
[   31.028040] 0.0: GetNextTuple: No more items
[   31.028052] pata_pcmcia: probe of 0.0 failed with error -12
[   32.210003] lp: driver loaded but no devices found
[   32.468244] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
[   33.116762] EXT3 FS on sda1, internal journal
[   34.645762] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.223766] No dock devices found.
[   35.583602] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 processors (1 cpu cores) (version 2.20.00)
[   35.583650] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
[   35.583654] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[   35.583693] powernow-k8: ph2 null fid transition 0x8
[   36.937544] ppdev: user-space parallel port driver
[   37.231469] audit(1221140398.444:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4885 profile="/usr/sbin/cupsd" namespace="default"
[   38.271081] input: Unspecified device as /devices/virtual/input/input8
[   38.385820] eth0: link down
[   38.419046] Bluetooth: Core ver 2.11
[   38.421713] NET: Registered protocol family 31
[   38.421718] Bluetooth: HCI device and connection manager initialized
[   38.421723] Bluetooth: HCI socket layer initialized
[   38.451504] Bluetooth: L2CAP ver 2.9
[   38.451510] Bluetooth: L2CAP socket layer initialized
[   38.578519] Bluetooth: RFCOMM socket layer initialized
[   38.578541] Bluetooth: RFCOMM TTY layer initialized
[   38.578544] Bluetooth: RFCOMM ver 1.8
[   39.705544] Clocksource tsc unstable (delta = -216569107 ns)
[   40.235769] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   42.737913] [fglrx] GART Table is not in FRAME_BUFFER range 
[   42.737926] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   42.737930] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   42.907167] [fglrx] interrupt source 20008000 successfully enabled
[   42.907174] [fglrx] enable ID = 0x00000004
[   42.907588] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   58.016141] NET: Registered protocol family 10
[   58.016566] lo: Disabled Privacy Extensions
[   58.017107] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   58.017696] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.604019] NET: Registered protocol family 17
[   68.619401] wlan0: Initial auth_alg=0
[   68.619411] wlan0: authenticate with AP 00:18:f6:5c:fb:a9
[   68.620866] wlan0: RX authentication from 00:18:f6:5c:fb:a9 (alg=0 transaction=2 status=0)
[   68.620869] wlan0: authenticated
[   68.620872] wlan0: associate with AP 00:18:f6:5c:fb:a9
[   68.623503] wlan0: RX AssocResp from 00:18:f6:5c:fb:a9 (capab=0x411 status=0 aid=3)
[   68.623506] wlan0: associated
[   68.623585] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   68.623588] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   68.623591] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   68.623594] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   68.624317] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   75.846805] wlan0: no IPv6 routers present
[   83.193700] wlan0: no IPv6 routers present
[   88.718508] pccard: card ejected from slot 0
[  229.458748] pccard: PCMCIA card inserted into slot 0
[  229.458872] pcmcia: registering new device pcmcia0.0
[  229.459006] 0.0: GetNextTuple: No more items
[  229.459013] pata_pcmcia: probe of 0.0 failed with error -12
[  229.917576] 0.0: GetNextTuple: No more items
[  229.917587] pata_pcmcia: probe of 0.0 failed with error -12
[  272.003866] pccard: card ejected from slot 0
[  275.754740] pccard: PCMCIA card inserted into slot 0
[  275.754866] pcmcia: registering new device pcmcia0.0
[  275.755005] 0.0: GetNextTuple: No more items
[  275.755013] pata_pcmcia: probe of 0.0 failed with error -12
[  275.944311] 0.0: GetNextTuple: No more items
[  275.944322] pata_pcmcia: probe of 0.0 failed with error -12
[  388.932128] wlan0: switched to short barker preamble (BSSID=00:18:f6:5c:fb:a9)
[  754.004757] wlan0: switched to long barker preamble (BSSID=00:18:f6:5c:fb:a9)
[ 1438.991257] APIC error on CPU0: 00(40)
[ 4840.808845] npviewer.bin[5985]: segfault at 4 rip f6ee9d54 rsp ff807530 error 4
[ 5241.767188] pccard: card ejected from slot 0
[ 9035.610042] keyboard.c: can't emulate rawmode for keycode 240
[ 9035.624974] keyboard.c: can't emulate rawmode for keycode 240
[ 9259.079898] keyboard.c: can't emulate rawmode for keycode 240
[ 9259.094831] keyboard.c: can't emulate rawmode for keycode 240
[ 9667.764896] keyboard.c: can't emulate rawmode for keycode 240
[ 9667.779828] keyboard.c: can't emulate rawmode for keycode 240
[10097.329591] pccard: PCMCIA card inserted into slot 0
[10097.329718] pcmcia: registering new device pcmcia0.0
[10097.329853] 0.0: GetNextTuple: No more items
[10097.329862] pata_pcmcia: probe of 0.0 failed with error -12
[10097.599091] 0.0: GetNextTuple: No more items
[10097.599175] pata_pcmcia: probe of 0.0 failed with error -12


fdisk output:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe820e820

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7133    57295791   83  Linux
/dev/sda2            7134        7296     1309297+   5  Extended
/dev/sda5            7134        7296     1309266   82  Linux swap / Solaris


many thanks for any help

---

### Post by phidia on 2008-09-11
Googling this > pata_pcmcia: probe of 0.0 failed with error -12 provided some [hits]("http://www.google.com/search?q=pata_pcmcia%3A+probe+of+0.0+failed+with+error+-12&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a") but unfortunately nothing that had a workable solution for you.
You could report this at launchpad as a bug, but I don't know of a fix-there might be one though.

---

### Post by LiquidOC on 2008-09-29
I have a problem just like this....

dmesg output:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffd0000 - 000000003ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffdf000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262096) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262096
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262096
[    0.000000] On node 0 totalpages: 262096
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32465 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F55D0 checksum 0
[    0.000000] ACPI: RSDP 000F55D0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFD0000, 0030 (r1 A M I  OEMRSDT  12000302 MSFT       97)
[    0.000000] ACPI: FACP 3FFD0200, 0081 (r1 A M I  OEMFACP  12000302 MSFT       97)
[    0.000000] ACPI: DSDT 3FFD03F0, 3CA8 (r1  1ABFS 1ABFS001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFDF000, 0040
[    0.000000] ACPI: APIC 3FFD0390, 005C (r1 A M I  OEMAPIC  12000302 MSFT       97)
[    0.000000] ACPI: OEMB 3FFDF040, 0108 (r1 A M I  AMI_OEM  12000302 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260049
[    0.000000] Kernel command line: root=UUID=5cc92b9d-4823-43f6-b986-87dbdb060077 ro quiet
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.259 MHz processor.
[   33.536171] Console: colour VGA+ 80x25
[   33.536175] console [tty0] enabled
[   33.536794] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   33.537427] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   33.568614] Memory: 1027120k/1048384k available (2177k kernel code, 20636k reserved, 1006k data, 368k init, 130880k highmem)
[   33.568626] virtual kernel memory layout:
[   33.568626]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   33.568627]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   33.568628]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   33.568629]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   33.568630]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   33.568631]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   33.568632]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   33.568635] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   33.568695] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   33.648650] Calibrating delay using timer specific routine.. 6005.49 BogoMIPS (lpj=12010984)
[   33.648686] Security Framework initialized
[   33.648697] SELinux:  Disabled at boot.
[   33.648716] AppArmor: AppArmor initialized
[   33.648721] Failure registering capabilities with primary security module.
[   33.648730] Mount-cache hash table entries: 512
[   33.648900] Initializing cgroup subsys ns
[   33.648906] Initializing cgroup subsys cpuacct
[   33.648920] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   33.648934] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   33.648937] CPU: L2 cache: 512K
[   33.648939] CPU: Physical Processor ID: 0
[   33.648941] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   33.648955] Compat vDSO mapped to ffffe000.
[   33.648972] Checking 'hlt' instruction... OK.
[   33.665035] SMP alternatives: switching to UP code
[   33.666677] Early unpacking initramfs... done
[   33.953401] ACPI: Core revision 20070126
[   33.953465] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   33.955283] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   33.955305] SMP alternatives: switching to SMP code
[   33.956002] Booting processor 1/1 eip 3000
[   33.966100] Initializing CPU#1
[   34.044297] Calibrating delay using timer specific routine.. 6000.68 BogoMIPS (lpj=12001368)
[   34.044307] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   34.044317] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   34.044320] CPU: L2 cache: 512K
[   34.044322] CPU: Physical Processor ID: 0
[   34.044324] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   34.044588] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   34.044630] Total of 2 processors activated (12006.17 BogoMIPS).
[   34.044740] ENABLING IO-APIC IRQs
[   34.044914] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   34.192333] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   34.212333] Brought up 2 CPUs
[   34.212358] CPU0 attaching sched-domain:
[   34.212361]  domain 0: span 03
[   34.212363]   groups: 01 02
[   34.212367]   domain 1: span 03
[   34.212369]    groups: 03
[   34.212372] CPU1 attaching sched-domain:
[   34.212373]  domain 0: span 03
[   34.212375]   groups: 02 01
[   34.212379]   domain 1: span 03
[   34.212380]    groups: 03
[   34.212713] net_namespace: 64 bytes
[   34.212722] Booting paravirtualized kernel on bare hardware
[   34.213261] Time: 19:26:46  Date: 09/29/08
[   34.213298] NET: Registered protocol family 16
[   34.213580] EISA bus registered
[   34.213587] ACPI: bus type pci registered
[   34.215131] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   34.215133] PCI: Using configuration type 1
[   34.215142] Setting up standard PCI resources
[   34.254813] ACPI: EC: Look up EC in DSDT
[   34.256384] ACPI: Interpreter enabled
[   34.256387] ACPI: (supports S0 S1 S3 S4 S5)
[   34.256405] ACPI: Using IOAPIC for interrupt routing
[   34.270812] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   34.275524] ACPI: EC: GPE = 0xb, I/O: command/status = 0x66, data = 0x62
[   34.275527] ACPI: EC: driver started in interrupt mode
[   34.275599] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.275828] Enabling SiS 96x SMBus.
[   34.277113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.362141] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   34.362239] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[   34.362334] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   34.362438] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[   34.362539] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[   34.362636] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[   34.362735] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 7 10 11 12 14 15)
[   34.362834] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[   34.362998] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  19, should be 14 [20070126]
[   34.363005] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.363049] pnp: PnP ACPI init
[   34.363062] ACPI: bus type pnp registered
[   34.365689] pnp: PnP ACPI: found 10 devices
[   34.365692] ACPI: ACPI bus type pnp unregistered
[   34.365697] PnPBIOS: Disabled by ACPI PNP
[   34.366036] PCI: Using ACPI for IRQ routing
[   34.366041] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.388189] NET: Registered protocol family 8
[   34.388191] NET: Registered protocol family 20
[   34.388283] AppArmor: AppArmor Filesystem Enabled
[   34.392003] Time: tsc clocksource has been installed.
[   34.404213] system 00:07: ioport range 0x480-0x48f has been reserved
[   34.404216] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   34.404218] system 00:07: ioport range 0x800-0x87f has been reserved
[   34.404221] system 00:07: ioport range 0x880-0x8ff has been reserved
[   34.404223] system 00:07: ioport range 0xc00-0xc1f has been reserved
[   34.404228] system 00:07: iomem range 0xffe80000-0xffefffff has been reserved
[   34.404231] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[   34.404233] system 00:07: iomem range 0xfee00400-0xffbfffff has been reserved
[   34.404240] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   34.404243] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   34.404251] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[   34.404254] system 00:09: iomem range 0x0-0x0 could not be reserved
[   34.404257] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   34.404259] system 00:09: iomem range 0x100000-0x3fffffff could not be reserved
[   34.404262] system 00:09: iomem range 0x0-0x0 could not be reserved
[   34.434847] PCI: Bridge: 0000:00:01.0
[   34.434851]   IO window: d000-dfff
[   34.434857]   MEM window: dfe00000-dfefffff
[   34.434862]   PREFETCH window: cfd00000-dfcfffff
[   34.434869] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[   34.434871]   IO window: 00001000-000010ff
[   34.434876]   IO window: 00001400-000014ff
[   34.434881]   PREFETCH window: 50000000-53ffffff
[   34.434886]   MEM window: 54000000-57ffffff
[   34.434890] PCI: Bus 6, cardbus bridge: 0000:00:09.1
[   34.434892]   IO window: 00001800-000018ff
[   34.434897]   IO window: 00001c00-00001cff
[   34.434902]   PREFETCH window: 58000000-5bffffff
[   34.434906]   MEM window: 5c000000-5fffffff
[   34.434948] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   34.434966] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 16
[   34.434984] NET: Registered protocol family 2
[   34.472181] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   34.472546] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   34.473598] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   34.474295] TCP: Hash tables configured (established 131072 bind 65536)
[   34.474301] TCP reno registered
[   34.484314] checking if image is initramfs... it is
[   34.935533] Switched to high resolution mode on CPU 0
[   34.935680] Switched to high resolution mode on CPU 1
[   35.055890] Freeing initrd memory: 7467k freed
[   35.056674] audit: initializing netlink socket (disabled)
[   35.056694] audit(1222716406.368:1): initialized
[   35.056948] highmem bounce pool size: 64 pages
[   35.059489] VFS: Disk quotas dquot_6.5.1
[   35.059588] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   35.059771] io scheduler noop registered
[   35.059774] io scheduler anticipatory registered
[   35.059776] io scheduler deadline registered
[   35.059790] io scheduler cfq registered (default)
[   35.131324] Boot video device is 0000:01:00.0
[   35.131730] isapnp: Scanning for PnP cards...
[   35.485282] isapnp: No Plug & Play device found
[   35.525539] Real Time Clock Driver v1.12ac
[   35.525675] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.526416] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
[   35.526427] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   35.527338] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.527425] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   35.527566] PNP: PS/2 Controller [PNP030b:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   35.534748] i8042.c: Detected active multiplexing controller, rev 1.0.
[   35.537003] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.537010] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   35.537014] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   35.537018] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   35.537021] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   35.551000] mice: PS/2 mouse device common for all mice
[   35.551175] EISA: Probing bus 0 at eisa.0
[   35.551183] Cannot allocate resource for EISA slot 1
[   35.551213] EISA: Detected 0 cards.
[   35.551216] cpuidle: using governor ladder
[   35.551219] cpuidle: using governor menu
[   35.551325] NET: Registered protocol family 1
[   35.551373] Using IPI No-Shortcut mode
[   35.551417] registered taskstats version 1
[   35.551546]   Magic number: 8:588:446
[   35.551680] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   35.551682] EDD information not available.
[   35.552073] Freeing unused kernel memory: 368k freed
[   35.553531] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   35.793962] fuse init (API version 7.9)
[   35.820186] ACPI: Processor [CPU1] (supports 8 throttling states)
[   35.820221] ACPI: Processor [CPU2] (supports 8 throttling states)
[   35.821661] ACPI: Thermal Zone [THRM] (75 C)
[   36.032128] SCSI subsystem initialized
[   36.070426] libata version 3.00 loaded.
[   36.099140] pata_sis 0000:00:02.5: version 0.5.2
[   36.116312] scsi0 : pata_sis
[   36.126503] scsi1 : pata_sis
[   36.126949] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   36.126954] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   36.127006] ata1: port disabled. ignoring.
[   36.127069] ata2: port disabled. ignoring.
[   36.149616] ACPI: PCI Interrupt 0000:00:02.3[B] -> GSI 17 (level, low) -> IRQ 16
[   36.201462] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[dfff7000-dfff77ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[   36.430711] usbcore: registered new interface driver usbfs
[   36.430755] usbcore: registered new interface driver hub
[   36.450112] usbcore: registered new device driver usb
[   36.451350] sis900.c: v1.08.10 Apr. 2 2006
[   36.451464] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 18
[   36.453120] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   36.465205] 0000:00:04.0: Using transceiver found at address 1 as default
[   36.469035] eth0: SiS 900 PCI Fast Ethernet at 0xe800, IRQ 18, 00:03:0d:10:d4:73
[   36.477914] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   36.477945] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   36.478396] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[   36.478457] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   36.478472] ehci_hcd 0000:00:03.3: irq 19, io mem 0xdfffb000
[   36.490022] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.490242] usb usb1: configuration #1 chosen from 1 choice
[   36.490282] hub 1-0:1.0: USB hub found
[   36.490293] hub 1-0:1.0: 6 ports detected
[   36.490404] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.594250] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   36.594270] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   36.594310] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[   36.594331] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfff8000
[   36.652108] usb usb2: configuration #1 chosen from 1 choice
[   36.652149] hub 2-0:1.0: USB hub found
[   36.652162] hub 2-0:1.0: 2 ports detected
[   36.753972] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   36.753999] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   36.754047] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[   36.754072] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfff9000
[   36.811937] usb usb3: configuration #1 chosen from 1 choice
[   36.811991] hub 3-0:1.0: USB hub found
[   36.812006] hub 3-0:1.0: 2 ports detected
[   36.833711] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   36.913871] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 22
[   36.913900] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   36.913964] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[   36.913991] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfffa000
[   36.966144] usb 1-2: configuration #1 chosen from 1 choice
[   36.966255] hub 1-2:1.0: USB hub found
[   36.966334] hub 1-2:1.0: 4 ports detected
[   36.971808] usb usb4: configuration #1 chosen from 1 choice
[   36.971857] hub 4-0:1.0: USB hub found
[   36.971871] hub 4-0:1.0: 2 ports detected
[   37.309282] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   37.442095] usb 1-3: configuration #1 chosen from 1 choice
[   37.645090] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d5376601e55]
[   37.928654] usb 3-2: new low speed USB device using ohci_hcd and address 2
[   38.146439] usb 3-2: configuration #1 chosen from 1 choice
[   38.352319] usb 1-2.1: new full speed USB device using ehci_hcd and address 5
[   38.445253] usb 1-2.1: configuration #1 chosen from 1 choice
[   38.445793] hub 1-2.1:1.0: USB hub found
[   38.445966] hub 1-2.1:1.0: 3 ports detected
[   38.748010] usb 1-2.4: new high speed USB device using ehci_hcd and address 6
[   38.841195] usb 1-2.4: configuration #1 chosen from 1 choice
[   39.039818] usb 1-2.1.1: new full speed USB device using ehci_hcd and address 7
[   39.132880] usb 1-2.1.1: configuration #1 chosen from 1 choice
[   39.331497] usb 1-2.1.2: new low speed USB device using ehci_hcd and address 8
[   39.426553] usb 1-2.1.2: configuration #1 chosen from 1 choice
[   39.427210] usbcore: registered new interface driver libusual
[   39.429685] usbcore: registered new interface driver hiddev
[   39.438098] Initializing USB Mass Storage driver...
[   39.438217] scsi2 : SCSI emulation for USB Mass Storage devices
[   39.438315] usb-storage: device found at 3
[   39.438318] usb-storage: waiting for device to settle before scanning
[   39.440374] input: Cypress Semiconductor USB Multi Remote Controller as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input2
[   39.472269] input,hidraw0: USB HID v1.10 Mouse [Cypress Semiconductor USB Multi Remote Controller] on usb-0000:00:03.1-2
[   39.477039] input: Cypress Semiconductor USB Multi Remote Controller as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.1/input/input3
[   39.477077] input,hidraw1: USB HID v1.10 Device [Cypress Semiconductor USB Multi Remote Controller] on usb-0000:00:03.1-2
[   39.477233] scsi3 : SCSI emulation for USB Mass Storage devices
[   39.477357] usb-storage: device found at 6
[   39.477360] usb-storage: waiting for device to settle before scanning
[   39.478126] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2.1/1-2.1.1/1-2.1.1:1.0/input/input4
[   39.499254] input,hidraw2: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:03.3-2.1.1
[   39.501030] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2.1/1-2.1.1/1-2.1.1:1.1/input/input5
[   39.531174] input,hidraw3: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:03.3-2.1.1
[   39.532928] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.3/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.0/input/input6
[   39.551167] input,hidraw4: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:03.3-2.1.2
[   39.551202] usbcore: registered new interface driver usbhid
[   39.551211] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.552330] usbcore: registered new interface driver usb-storage
[   39.552338] USB Mass Storage support registered.
[   44.431062] usb-storage: device scan complete
[   44.431565] scsi 2:0:0:0: Direct-Access     WDC WD16 00BB-00FTA0           PQ: 0 ANSI: 0
[   44.438495] Driver 'sd' needs updating - please use bus_type methods
[   44.439683] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   44.440684] sd 2:0:0:0: [sda] Write Protect is off
[   44.440690] sd 2:0:0:0: [sda] Mode Sense: 33 00 00 00
[   44.440693] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   44.441913] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   44.442900] sd 2:0:0:0: [sda] Write Protect is off
[   44.442903] sd 2:0:0:0: [sda] Mode Sense: 33 00 00 00
[   44.442905] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   44.442949]  sda: sda1 sda2 sda3 sda4 <<7>usb-storage: device scan complete
[   44.472139] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB02 PQ: 0 ANSI: 0
[   44.479788]  sda5 sda6<4>Driver 'sr' needs updating - please use bus_type methods
[   44.493115]  sda7 >
[   44.493344] sd 2:0:0:0: [sda] Attached SCSI disk
[   44.500611] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   44.500651] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   44.507229] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   44.507237] Uniform CD-ROM driver Revision: 3.20
[   44.507330] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   45.089640] Attempting manual resume
[   45.089644] swsusp: Resume From Partition 8:6
[   45.089646] PM: Checking swsusp image.
[   45.090324] PM: Resume from disk failed.
[   45.107470] EXT3-fs: INFO: recovery required on readonly filesystem.
[   45.107478] EXT3-fs: write access will be enabled during recovery.
[   52.636598] kjournald starting.  Commit interval 5 seconds
[   52.636627] EXT3-fs: sda3: orphan cleanup on readonly fs
[   52.636636] ext3_orphan_cleanup: deleting unreferenced inode 338214
[   52.650394] ext3_orphan_cleanup: deleting unreferenced inode 338077
[   52.657803] EXT3-fs: sda3: 2 orphan inodes deleted
[   52.657805] EXT3-fs: recovery complete.
[   52.684748] EXT3-fs: mounted filesystem with ordered data mode.
[   69.752575] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   70.311335] Linux agpgart interface v0.102
[   70.642804] Yenta: CardBus bridge found at 0000:00:09.0 [1584:3005]
[   70.642842] Yenta O2: res at 0x94/0xD4: 00/ea
[   70.642845] Yenta O2: enabling read prefetch/write burst
[   70.714682] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   70.771380] Yenta: ISA IRQ mask 0x0ab8, PCI irq 16
[   70.771387] Socket status: 30000006
[   70.819969] Yenta: CardBus bridge found at 0000:00:09.1 [1584:3005]
[   70.951921] Yenta: ISA IRQ mask 0x0ab8, PCI irq 16
[   70.951927] Socket status: 30000006
[   70.962777] agpgart: Detected SiS chipset - id:1608
[   70.968160] agpgart: AGP aperture is 64M @ 0xe0000000
[   70.968281] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   70.968392] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   71.188390] input: Power Button (FF) as /devices/virtual/input/input8
[   71.229148] ACPI: Power Button (FF) [PWRF]
[   71.229254] input: Lid Switch as /devices/virtual/input/input9
[   71.245202] ACPI: Lid Switch [LID]
[   71.245314] input: Sleep Button (CM) as /devices/virtual/input/input10
[   71.289104] ACPI: Sleep Button (CM) [SLPB]
[   71.289194] input: Power Button (CM) as /devices/virtual/input/input11
[   71.333064] ACPI: Power Button (CM) [PWRB]
[   71.701328] ACPI: AC Adapter [AC0] (on-line)
[   72.108267] ACPI: Battery Slot [BAT0] (battery absent)
[   72.253655] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input12
[   72.280140] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   72.357231] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 16
[   72.417945] phy0: Selected rate control algorithm 'simple'
[   72.637158] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa36eb3, caps: 0x904713/0x10008
[   72.677829] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input13
[   72.758994] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   72.983663] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   72.983710] [fglrx] ASYNCIO init succeed!
[   72.983926] [fglrx] PAT is enabled successfully!
[   73.014676] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   73.296873] NET: Registered protocol family 17
[   73.652891] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
[   73.716856] eth0: Media Link On 100mbps full-duplex 
[   74.479035] intel8x0_measure_ac97_clock: measured 55347 usecs
[   74.479044] intel8x0: clocking to 48000
[   75.210391] udev: renamed network interface wlan0 to wlan1
[   75.387430] cs: IO port probe 0x100-0x3af: clean.
[   75.389266] cs: IO port probe 0x100-0x3af: clean.
[   75.391129] cs: IO port probe 0x3e0-0x4ff: clean.
[   75.391872] cs: IO port probe 0x3e0-0x4ff: clean.
[   75.392612] cs: IO port probe 0x820-0x8ff: clean.
[   75.392663] cs: IO port probe 0x820-0x8ff: clean.
[   75.392721] cs: IO port probe 0xc00-0xcf7: clean.
[   75.393353] cs: IO port probe 0xc00-0xcf7: clean.
[   75.394213] cs: IO port probe 0xa00-0xaff: clean.
[   75.394960] cs: IO port probe 0xa00-0xaff: clean.
[   76.254808] lp: driver loaded but no devices found
[   76.420717] Adding 1951824k swap on /dev/sda6.  Priority:-1 extents:1 across:1951824k
[   76.679459] EXT3 FS on sda3, internal journal
[   77.301445] kjournald starting.  Commit interval 5 seconds
[   77.302153] EXT3 FS on sda7, internal journal
[   77.302161] EXT3-fs: mounted filesystem with ordered data mode.
[   77.794820] ip_tables: (C) 2000-2006 Netfilter Core Team
[   79.929559] No dock devices found.
[   80.652756] NET: Registered protocol family 10
[   80.653428] lo: Disabled Privacy Extensions
[   82.028275] ppdev: user-space parallel port driver
[   82.298044] audit(1222716454.236:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5678 profile="/usr/sbin/cupsd" namespace="default"
[   82.298222] audit(1222716454.240:3): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/etc/krb5.conf" pid=5678 profile="/usr/sbin/cupsd" namespace="default"
[   82.410154] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   82.410163] apm: disabled - APM is not SMP safe.
[   84.704230] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   84.704241] vboxdrv: Successfully done.
[   84.704245] vboxdrv: Found 2 processor cores.
[   84.704274] vboxdrv: fAsync=0 u64DiffCores=1376.
[   84.705422] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   84.705433] vboxdrv: Successfully loaded version 1.6.0 (interface 0x00070001).
[   86.241877] input: Unspecified device as /devices/virtual/input/input14
[   86.276717] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   86.324257] Bluetooth: Core ver 2.11
[   86.324426] NET: Registered protocol family 31
[   86.324431] Bluetooth: HCI device and connection manager initialized
[   86.324437] Bluetooth: HCI socket layer initialized
[   86.354258] Bluetooth: L2CAP ver 2.9
[   86.354268] Bluetooth: L2CAP socket layer initialized
[   86.469680] Bluetooth: RFCOMM socket layer initialized
[   86.469701] Bluetooth: RFCOMM TTY layer initialized
[   86.469704] Bluetooth: RFCOMM ver 1.8
[   88.032001] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 23
[   89.305356] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   89.305367] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   89.305374] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[   89.305534] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   89.305559] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   89.305564] agpgart: SiS delay workaround: giving bridge time to recover.
[   89.320701] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   89.320720] [fglrx] AGP enabled,  AgpCommand = 0x1f004302 (selected caps)
[   89.326093] [fglrx] GART Table is not in FRAME_BUFFER range 
[   89.326110] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   89.326114] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[   89.438416] [fglrx] interrupt source 20008000 successfully enabled
[   89.438427] [fglrx] enable ID = 0x00000004
[   89.438444] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   89.438552] [fglrx] interrupt source 10000000 successfully enabled
[   89.438556] [fglrx] enable ID = 0x00000005
[   89.438561] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   90.806405] eth0: no IPv6 routers present

fdisk -l output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x644fa796

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       12748    51199155    7  HPFS/NTFS
/dev/sda3           12749       13356     4883760   83  Linux
/dev/sda4           13357       19457    49006282+   5  Extended
/dev/sda5           19178       19457     2249068+  82  Linux swap / Solaris
/dev/sda6           13357       13599     1951834+  82  Linux swap / Solaris
/dev/sda7           13600       19177    44805253+  83  Linux

Partition table entries are not in disk order


I have no idea what any of this means, so any help would be appreciated!

Thanks!

---


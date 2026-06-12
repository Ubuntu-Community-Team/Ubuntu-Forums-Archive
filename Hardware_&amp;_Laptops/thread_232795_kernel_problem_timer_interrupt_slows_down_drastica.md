---
title: "kernel problem: timer interrupt slows down drastically"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by ilia on 2006-08-09
Hi all! Probably someone has an idea, what to do...
I have Ubuntu Dapper Drake 6.06 installed on IBM NetVista machine, based in Intel 845G chipset. Sometimes the system suddenly becomes very slow. In text console keyboard works as regular (i.e. typing, changing VTs, etc.), but all HDD related (and non-cached) requests proceed very slow. X-window is useless in such a situation. I've paid an attention, that `sleep 1` can takes several minutes instead of a second. Examination of /proc/interrupts showed that timer interrupts occur very rarely: about 2 in a second, instead of normal 1000. dmesg almost always contains nothing interesting, but one time I've got an oops:

```

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[4294667.296000]  BIOS-e820: 000000003fef0000 - 000000003fefb000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003fefb000 - 000000003ff00000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003ff00000 - 000000003ff80000 (usable)
[4294667.296000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[4294667.296000] 127MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f61d0
[4294667.296000] On node 0 totalpages: 262016
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 32640 pages, LIFO batch:7
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6260
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x060400d0  LTP 0x00000000) @ 0x3fef7325
[4294667.296000] ACPI: FADT (v001 IBM    NETVISTA 0x060400d0 PTL  0x00000001) @ 0x3fefaee2
[4294667.296000] ACPI: TCPA (v001 IBM    NETVISTA 0x060400d0 PTL  0x00000001) @ 0x3fefaf56
[4294667.296000] ACPI: MADT (v001 PTLTD  	 APIC   0x060400d0  LTP 0x00000000) @ 0x3fefaf88
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x060400d0  LTP 0x00000001) @ 0x3fefafd8
[4294667.296000] ACPI: DSDT (v001    IBM Yelotail 0x060400d0 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:2 APIC version 20
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda7 ro irqpoll
[4294667.296000] Misrouted IRQ fixup and polling support enabled
[4294667.296000] This may significantly impact system performance
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2392.923 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.404000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.405000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.437000] Memory: 1028184k/1048064k available (1976k kernel code, 19152k reserved, 606k data, 288k init, 130496k highmem)
[4294667.437000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.498000] Calibrating delay using timer specific routine.. 4789.08 BogoMIPS (lpj=2394540)
[4294667.498000] Security Framework v1.0.0 initialized
[4294667.498000] SELinux:  Disabled at boot.
[4294667.498000] Mount-cache hash table entries: 512
[4294667.498000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.498000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.498000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.498000] CPU: L2 cache: 512K
[4294667.498000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[4294667.498000] mtrr: v2.0 (20020519)
[4294667.498000] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[4294667.498000] Enabling fast FPU save and restore... done.
[4294667.498000] Enabling unmasked SIMD FPU exception support... done.
[4294667.498000] Checking 'hlt' instruction... OK.
[4294667.502000] checking if image is initramfs... it is
[4294668.102000] Freeing initrd memory: 6837k freed
[4294668.115000] ACPI: Looking for DSDT ... not found!
[4294668.120000] ENABLING IO-APIC IRQs
[4294668.120000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294668.231000] NET: Registered protocol family 16
[4294668.231000] EISA bus registered
[4294668.231000] ACPI: bus type pci registered
[4294668.231000] PCI: PCI BIOS revision 2.10 entry at 0xfd98d, last bus=2
[4294668.231000] PCI: Using configuration type 1
[4294668.232000] ACPI: Subsystem revision 20051216
[4294668.234000] ACPI: Interpreter enabled
[4294668.234000] ACPI: Using IOAPIC for interrupt routing
[4294668.235000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.235000] PCI: Probing PCI hardware (bus 00)
[4294668.249000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294668.249000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[4294668.249000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.249000] Boot video device is 0000:01:00.0
[4294668.250000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.250000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[4294668.314000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[4294668.314000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[4294668.315000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[4294668.316000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[4294668.316000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[4294668.317000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294668.318000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[4294668.319000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[4294668.341000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294668.341000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.342000] pnp: PnP ACPI init
[4294668.382000] pnp: PnP ACPI: found 15 devices
[4294668.382000] PnPBIOS: Disabled by ACPI PNP
[4294668.382000] PCI: Using ACPI for IRQ routing
[4294668.382000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.388000] PCI: Bridge: 0000:00:01.0
[4294668.388000]   IO window: disabled.
[4294668.388000]   MEM window: c2000000-c3ffffff
[4294668.388000]   PREFETCH window: e0000000-e2ffffff
[4294668.388000] PCI: Bridge: 0000:00:1e.0
[4294668.389000]   IO window: 2000-2fff
[4294668.389000]   MEM window: c4000000-c40fffff
[4294668.389000]   PREFETCH window: disabled.
[4294668.389000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294668.389000] Simple Boot Flag at 0x6c set to 0x1
[4294668.389000] audit: initializing netlink socket (disabled)
[4294668.389000] audit(1154856708.388:1): initialized
[4294668.389000] highmem bounce pool size: 64 pages
[4294668.390000] VFS: Disk quotas dquot_6.5.1
[4294668.390000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.390000] Initializing Cryptographic API
[4294668.390000] io scheduler noop registered
[4294668.390000] io scheduler anticipatory registered
[4294668.390000] io scheduler deadline registered
[4294668.390000] io scheduler cfq registered
[4294668.390000] isapnp: Scanning for PnP cards...
[4294668.748000] isapnp: No Plug & Play device found
[4294668.764000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
[4294668.772000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.772000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.772000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.772000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.773000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.775000] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.775000] 00:0d: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.776000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.776000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.776000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.776000] mice: PS/2 mouse device common for all mice
[4294668.778000] EISA: Probing bus 0 at eisa.0
[4294668.778000] Cannot allocate resource for EISA slot 1
[4294668.778000] Cannot allocate resource for EISA slot 2
[4294668.778000] EISA: Detected 0 cards.
[4294668.778000] NET: Registered protocol family 2
[4294668.788000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.788000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[4294668.791000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.791000] TCP: Hash tables configured (established 262144 bind 65536)
[4294668.791000] TCP reno registered
[4294668.791000] TCP bic registered
[4294668.791000] NET: Registered protocol family 1
[4294668.791000] NET: Registered protocol family 8
[4294668.791000] NET: Registered protocol family 20
[4294668.791000] Using IPI Shortcut mode
[4294668.792000] ACPI wakeup devices: 
[4294668.792000] USB1 USB2 USB3 USBE SLOT  KBC COMA COMB 
[4294668.792000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.792000] Freeing unused kernel memory: 288k freed
[4294668.801000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294668.852000] Capability LSM initialized
[4294668.896000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294668.898000] ACPI: Thermal Zone [THM0] (45 C)
[4294669.435000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294669.435000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294669.435000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[4294669.436000] ICH4: chipset revision 1
[4294669.436000] ICH4: not 100% native mode: will probe irqs later
[4294669.436000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[4294669.436000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[4294669.436000] Probing IDE interface ide0...
[4294669.700000] hda: WDC WD800JB-00JJC0, ATA DISK drive
[4294670.312000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294670.323000] Probing IDE interface ide1...
[4294670.995000] hdc: LTN486S, ATAPI CD/DVD-ROM drive
[4294671.301000] ide1 at 0x170-0x177,0x376 on irq 15
[4294671.319000] hda: max request size: 128KiB
[4294671.319000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)
[4294671.320000] Uniform CD-ROM driver Revision: 3.20
[4294671.320000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294671.320000] hda: cache flushes supported
[4294671.320000]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 >
[4294671.726000] usbcore: registered new driver usbfs
[4294671.727000] usbcore: registered new driver hub
[4294671.728000] USB Universal Host Controller Interface driver v2.3
[4294671.729000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294671.730000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294671.730000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294671.730000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294671.730000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x00001800
[4294671.731000] hub 1-0:1.0: USB hub found
[4294671.731000] hub 1-0:1.0: 2 ports detected
[4294671.832000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[4294671.832000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294671.832000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294671.832000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294671.832000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001820
[4294671.832000] hub 2-0:1.0: USB hub found
[4294671.832000] hub 2-0:1.0: 2 ports detected
[4294671.933000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[4294671.933000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294671.933000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294671.933000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294671.933000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x00001840
[4294671.933000] hub 3-0:1.0: USB hub found
[4294671.933000] hub 3-0:1.0: 2 ports detected
[4294672.036000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[4294672.036000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294672.036000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294672.036000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294672.036000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294672.036000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xc0000000
[4294672.040000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294672.041000] hub 4-0:1.0: USB hub found
[4294672.041000] hub 4-0:1.0: 6 ports detected
[4294672.232000] Attempting manual resume
[4294672.247000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294672.247000] EXT3-fs: write access will be enabled during recovery.
[4294675.971000] EXT3-fs: recovery complete.
[4294675.971000] kjournald starting.  Commit interval 5 seconds
[4294675.978000] EXT3-fs: mounted filesystem with ordered data mode.
[4294684.835000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294684.838000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294684.881000] Linux agpgart interface v0.101 (c) Dave Jones
[4294684.883000] agpgart: Detected an Intel 845G Chipset.
[4294684.895000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294684.943000] hw_random: RNG not detected
[4294685.448000] Real Time Clock Driver v1.12
[4294685.496000] nvidia: module license 'NVIDIA' taints kernel.
[4294685.501000] NVRM: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this system is
[4294685.501000] NVRM:  supported through the NVIDIA Legacy drivers. Please
[4294685.501000] NVRM:  visit http://www.nvidia.com/object/unix.html for more
[4294685.501000] NVRM:  information.  The 1.0-8762 NVIDIA driver will ignore
[4294685.501000] NVRM:  this GPU.  Continuing probe...
[4294685.501000] NVRM: No NVIDIA graphics adapter found!
[4294685.574000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[4294685.574000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
[4294685.742000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[4294685.742000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294685.826000] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[4294685.889000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294685.889000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294685.890000] input: PC Speaker as /class/input/input2
[4294686.054000] intel8x0_measure_ac97_clock: measured 50784 usecs
[4294686.054000] intel8x0: clocking to 48000
[4294686.055000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 217
[4294686.081000] e100: eth0: e100_probe: addr 0xc4000000, irq 217, MAC addr 00:09:6B:4F:24:E9
[4294686.397000] ts: Compaq touchscreen protocol output
[4294686.543000] parport: PnPBIOS parport detected.
[4294686.543000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294686.593000] Floppy drive(s): fd0 is 1.44M
[4294686.608000] FDC 0 is a post-1991 82077
[4294686.721000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294686.767000] lp0: using parport0 (interrupt-driven).
[4294686.833000] Adding 4096532k swap on /dev/hda8.  Priority:-1 extents:1 across:4096532k
[4294686.879000] EXT3 FS on hda7, internal journal
[4294687.041000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.041000] md: bitmap version 4.39
[4294687.429000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294687.881000] cdrom: open failed.
[4294687.925000] NET: Registered protocol family 17
[4294688.408000] kjournald starting.  Commit interval 5 seconds
[4294688.409000] EXT3 FS on hda6, internal journal
[4294688.409000] EXT3-fs: mounted filesystem with ordered data mode.
[4294691.546000] NET: Registered protocol family 10
[4294691.546000] lo: Disabled Privacy Extensions
[4294691.546000] IPv6 over IPv4 tunneling driver
[4294695.591000] ACPI: Power Button (FF) [PWRF]
[4294695.591000] ACPI: Power Button (CM) [PWRB]
[4294695.720000] ibm_acpi: ec object not found
[4294695.745000] pcc_acpi: loading...
[4294699.014000] ppdev: user-space parallel port driver
[4294699.414000] IBM machine detected. Enabling interrupts during APM calls.
[4294699.414000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294699.414000] apm: overridden by ACPI.
[4294702.286000] eth0: no IPv6 routers present
[4294703.416000] Non-volatile memory driver v1.2
[4294703.433000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[4294704.975000] Bluetooth: Core ver 2.8
[4294704.975000] NET: Registered protocol family 31
[4294704.975000] Bluetooth: HCI device and connection manager initialized
[4294704.975000] Bluetooth: HCI socket layer initialized
[4294705.018000] Bluetooth: L2CAP ver 2.8
[4294705.018000] Bluetooth: L2CAP socket layer initialized
[4294705.031000] Bluetooth: RFCOMM socket layer initialized
[4294705.031000] Bluetooth: RFCOMM TTY layer initialized
[4294705.031000] Bluetooth: RFCOMM ver 1.7
[4295018.264000] ibm_acpi: ec object not found
[4313672.207000] BUG: soft lockup detected on CPU#0!
[4313672.207000] 
[4313672.207000] Pid: 0, comm:              swapper
[4313672.207000] EIP: 0060:[<c02523b5>] CPU: 0
[4313672.207000] EIP is at ide_inb+0x5/0x10
[4313672.207000]  EFLAGS: 00000212    Tainted: P       (2.6.15-23-386)
[4313672.207000] EAX: c041cad0 EBX: 011d719d ECX: 00000177 EDX: 00000177
[4313672.207000] ESI: 00000088 EDI: c041ca1c EBP: c041cab0 DS: 007b ES: 007b
[4313672.207000] CR0: 8005003b CR2: 0804a000 CR3: 09180000 CR4: 00000690
[4313672.207000]  [<c0252dad>] ide_wait_stat+0xfd/0x140
[4313672.207000]  [<c02515c4>] start_request+0xc4/0x2a0
[4313672.207000]  [<c0251ada>] ide_do_request+0x30a/0x410
[4313672.207000]  [<c0252226>] ide_intr+0x1e6/0x200
[4313672.207000]  [<f8872b00>] cdrom_read_intr+0x0/0x370 [ide_cd]
[4313672.207000]  [<c013e705>] handle_IRQ_event+0x35/0x70
[4313672.207000]  [<c013e7b3>] __do_IRQ+0x73/0xe0
[4313672.207000]  [<c010597a>] do_IRQ+0x1a/0x30
[4313672.207000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4313672.207000]  [<c0121520>] __do_softirq+0x30/0xb0
[4313672.207000]  [<c01215d5>] do_softirq+0x35/0x40
[4313672.207000]  [<c0121685>] irq_exit+0x35/0x40
[4313672.207000]  [<c010597f>] do_IRQ+0x1f/0x30
[4313672.207000]  [<c01040ea>] common_interrupt+0x1a/0x20
[4313672.207000]  [<c010106a>] default_idle+0x3a/0x70
[4313672.207000]  [<c01010dc>] cpu_idle+0x1c/0x60
[4313672.207000]  [<c03887c6>] start_kernel+0x176/0x1d0
[4313674.142000] hdc: status timeout: status=0xd0 { Busy }
[4313674.142000] ide: failed opcode was: unknown
[4313674.142000] hdc: DMA disabled
[4313674.142000] hdc: drive not ready for command
[4313674.192000] hdc: ATAPI reset complete
[4313674.192000] end_request: I/O error, dev hdc, sector 64
[4313674.192000] Buffer I/O error on device hdc, logical block 16
[4313674.905000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4313674.981000] ISO 9660 Extensions: RRIP_1991A
[4322909.487000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.

```

Here is how the /proc/interrupts looked then:
```

           CPU0
  0:   91822876    IO-APIC-edge  timer
  1:      82017    IO-APIC-edge  i8042
  7:          0    IO-APIC-edge  parport0
  8:          4    IO-APIC-edge  rtc
  9:          1   IO-APIC-level  acpi
 12:     920631    IO-APIC-edge  i8042
 14:     244382    IO-APIC-edge  ide0
 15:    2718353    IO-APIC-edge  ide1
177:          0   IO-APIC-level  uhci_hcd:usb3
185:          0   IO-APIC-level  uhci_hcd:usb1
193:          0   IO-APIC-level  uhci_hcd:usb2
201:          0   IO-APIC-level  ehci_hcd:usb4
209:       3150   IO-APIC-level  Intel 82801DB-ICH4
217:    1120159   IO-APIC-level  eth0
NMI:          0
LOC:   92422927
ERR:          0
MIS:          0

```

lscpi output is below:
```

0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

```

The problem have occured with the original Dapper kernel and the upgrade to 2.6.15-26-686 haven't helped.

Here is an output of `dpkg -l |grep linux-`
```
ii  linux-386                              2.6.15.22                             Complete Linux kernel on 386.
ii  linux-686-smp                          2.6.15.24                             Complete Linux kernel on PPro/Celeron/PII/PIII/P
ii  linux-headers-2.6.15-23                2.6.15-23.39                          Header files related to Linux kernel version 2.6
ii  linux-headers-2.6.15-23-386            2.6.15-23.39                          Linux kernel headers 2.6.15 on 386
ii  linux-image-2.6.15-23-386              2.6.15-23.39                          Linux kernel image for version 2.6.15 on 386.
ii  linux-image-2.6.15-26-686              2.6.15-26.46                          Linux kernel image for version 2.6.15 on PPro/Ce
ii  linux-image-386                        2.6.15.22                             Linux kernel image on 386.
ii  linux-image-686                        2.6.15.24                             Linux kernel image on PPro/Celeron/PII/PIII/PIV.
ii  linux-kernel-headers                   2.6.11.2-0ubuntu18                    Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.15-23-386 2.6.15.11-1                           Non-free Linux 2.6.15 modules on 386
ii  linux-restricted-modules-2.6.15-26-686 2.6.15.11-3                           Non-free Linux 2.6.15 modules on PPro/Celeron/PI
ii  linux-restricted-modules-386           2.6.15.22                             Restricted Linux modules on 386.
ii  linux-restricted-modules-686           2.6.15.24                             Restricted Linux modules on PPro/Celeron/PII/PII
ii  linux-restricted-modules-common        2.6.15.11-1                           Non-free Linux 2.6.15 modules helper script
ii  linux-sound-base                       1.0.10-4ubuntu4                       base package for ALSA and OSS sound systems

```

Any ideas?
Thanks.

---

### Post by pmg on 2007-05-13
Did you ever solve your problem, or learn more about it?  I installed Ubuntu a few months ago and I've started seeing the same problem, also on an IBM NetVista.  From searching the web, I've found some hits of problems that sound similar.  In all cases I saw, it occurred on IBM NetVista hardware on a Debian derived kernel.   One suggesting I saw was to disable apic (e.g. add noapic as a kernel option at boot time.)  This seems to have helped, but I'm not sure if it solved the problem.  (Other members of my family still see the problem, but I'm not sure if they are booting with the right entry on the grub boot menu that has the noapic option.)

-pmg

---

### Post by PersistentLurker on 2007-05-15
People reading this thread might also be interested in what could be a related problem on an Acer TravelMate 2303WLci: [http://ubuntuforums.org/showthread.php?p=2644272](http://ubuntuforums.org/showthread.php?p=2644272)

I'm hoping to pursue that issue until it's resolved. Maybe it would solve the problem reported hereby the original poster as well.

pmg, thanks for reporting your success with noacpi. Would happen to remember where you found those other references to this kind of problem?

---

### Post by PersistentLurker on 2007-05-15
> **PersistentLurker said:**
> People reading this thread might also be interested in what could be a related problem on an Acer TravelMate 2303WLci: [http://ubuntuforums.org/showthread.php?p=2644272](http://ubuntuforums.org/showthread.php?p=2644272)

I'm hoping to pursue that issue until it's resolved. Maybe it would solve the problem reported hereby the original poster as well.

pmg, thanks for reporting your success with noacpi. Would happen to remember where you found those other references to this kind of problem?

Never mind, I've now realized that my issue is a completely different one. Timer interrupt issues are not the cause of my HD troubles.

---

### Post by gp2x on 2007-05-20
so what did then? :)

---


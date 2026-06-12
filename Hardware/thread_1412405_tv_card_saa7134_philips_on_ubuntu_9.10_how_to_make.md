---
title: "tv card saa7134 philips on ubuntu 9.10 how to make it work"
date: 2010-02-21
forum: Hardware
---

### Post by midhatt on 2010-02-21
i have buy a tv card on box of the tv card is saa7130 but on chihp on card is saa7134,how to configure it to make work.
when run tv time there is only black screen.

when i type this  lspci
i get
Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

---

### Post by gfuggs on 2010-02-21
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

This is a good place to start.  They have detailed information and instructions to get things working.

What kind of card is it?

---

### Post by midhatt on 2010-02-22
pci
i read lot of tutorials but nothing to help with my card
does somone know how to set up this card

---

### Post by gfuggs on 2010-02-22
What does "sudo lspci -vnn" give you for your card?

---

### Post by midhatt on 2010-02-24
midhaat@midhaat-desktop:~$ sudo lspci -vnn
[sudo] password for midhaat: 
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [e4] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 2.0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=80
	Memory behind bridge: e0000000-e1ffffff
	Prefetchable memory behind bridge: f0000000-f8ffffff
	Kernel modules: shpchp

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=248
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: e2000000-e20fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12) (prog-if 80 [Master])
	Subsystem: IBM Device [1014:0234]
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1800 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
	Subsystem: IBM Device [1014:0234]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 12)
	Subsystem: IBM Device [1014:0234]
	Flags: medium devsel, IRQ 5
	I/O ports at 1810 [size=16]
	Kernel modules: i2c-i801

00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
	Subsystem: IBM Device [1014:0234]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 12)
	Subsystem: IBM Device [1014:0234]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1c00 [size=256]
	I/O ports at 1880 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev a1)
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at f8000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
	Subsystem: IBM Device [1014:0234]
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at e2000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: e100
	Kernel modules: e100

02:0e.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
	Subsystem: Philips Semiconductors Device [1131:0000]
	Flags: bus master, medium devsel, latency 123, IRQ 22
	Memory at e2001000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [40] Power Management version 1
	Kernel driver in use: saa7134
	Kernel modules: saa7134

---

### Post by gfuggs on 2010-02-24
I don't see 1131:0000 in this list:
[http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134")

Do you recognize your card by name anywhere in that list?

Do you see anything in dmesg if you "sudo modprobe saa7134"?

---

### Post by midhatt on 2010-02-24
there is nothing when i type:
 sudo modprobe saa7134
and i dont see my card in that list

---

### Post by gfuggs on 2010-02-24
First, do:
"sudo rmmod saa7134" if it says the module is in use by something, also rmmod whatever is using it.
Then do:
"sudo modprobe saa7134"

After you do that, do "dmesg".  Do you see anything useful at the end of the output?

---

### Post by midhatt on 2010-02-25
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00027f80
[    0.000000]   HighMem  0x00027f80 -> 0x00027f80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00027eb0
[    0.000000]     0: 0x00027f00 -> 0x00027f80
[    0.000000] On node 0 totalpages: 163531
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1247 pages used for memmap
[    0.000000]   Normal zone: 158289 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000027eb0000 - 0000000027efc000
[    0.000000] PM: Registered nosave memory: 0000000027efc000 - 0000000027efd000
[    0.000000] PM: Registered nosave memory: 0000000027efd000 - 0000000027f00000
[    0.000000] Allocating PCI resources starting at 28000000 (gap: 28000000:d6c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1504000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 162252
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-19-generic root=UUID=0a657ab1-e823-4945-97d0-e2f9747eb098 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3274240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 628372k/654848k available (4567k kernel code, 25300k reserved, 2141k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe8780000 - 0xff7fe000   ( 368 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xe7f80000   ( 639 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575c48 - 0xc078d408   (2141 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575c48   (4567 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1993.172 MHz processor.
[    0.001464] Console: colour VGA+ 80x25
[    0.001471] console [tty0] enabled
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3986.34 BogoMIPS (lpj=7972688)
[    0.004056] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004112] Mount-cache hash table entries: 512
[    0.004383] Initializing cgroup subsys ns
[    0.004394] Initializing cgroup subsys cpuacct
[    0.004401] Initializing cgroup subsys memory
[    0.004418] Initializing cgroup subsys freezer
[    0.004423] Initializing cgroup subsys net_cls
[    0.004457] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004463] CPU: L2 cache: 256K
[    0.004467] CPU: Hyper-Threading is disabled
[    0.004475] mce: CPU supports 4 MCE banks
[    0.004494] CPU0: Thermal monitoring enabled (TM1)
[    0.004514] Performance Counters: no PMU driver, software counters only.
[    0.004528] Checking 'hlt' instruction... OK.
[    0.021331] SMP alternatives: switching to UP code
[    0.032049] Freeing SMP alternatives: 19k freed
[    0.032098] ACPI: Core revision 20090521
[    0.048334] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088033] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 02
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (3986.34 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] Booting paravirtualized kernel on bare hardware
[    0.092001] regulator: core version 0.5
[    0.092001] Time: 14:39:43  Date: 02/25/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: PCI BIOS revision 2.10 entry at 0xfd933, last bus=2
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092214] bio: create slab <bio-0> at 0
[    0.093092] ACPI: EC: Look up EC in DSDT
[    0.111162] ACPI: Interpreter enabled
[    0.111174] ACPI: (supports S0 S1 S3 S4 S5)
[    0.111216] ACPI: Using IOAPIC for interrupt routing
[    0.148861] ACPI: No dock devices found.
[    0.150650] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.150743] pci 0000:00:00.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
[    0.150969] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.150975] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.151032] pci 0000:00:1f.1: reg 20 io port: [0x1800-0x180f]
[    0.151104] pci 0000:00:1f.2: reg 20 io port: [0x1820-0x183f]
[    0.151177] pci 0000:00:1f.3: reg 20 io port: [0x1810-0x181f]
[    0.151246] pci 0000:00:1f.4: reg 20 io port: [0x1840-0x185f]
[    0.151295] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.151305] pci 0000:00:1f.5: reg 14 io port: [0x1880-0x18bf]
[    0.151394] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe0ffffff]
[    0.151403] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.151428] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.151498] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.151504] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf8ffffff]
[    0.151562] pci 0000:02:08.0: reg 10 32bit mmio: [0xe2000000-0xe2000fff]
[    0.151571] pci 0000:02:08.0: reg 14 io port: [0x2000-0x203f]
[    0.151620] pci 0000:02:08.0: supports D1 D2
[    0.151623] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.151630] pci 0000:02:08.0: PME# disabled
[    0.151681] pci 0000:02:0e.0: reg 10 32bit mmio: [0xe2001000-0xe20013ff]
[    0.151735] pci 0000:02:0e.0: supports D1 D2
[    0.151769] pci 0000:00:1e.0: transparent bridge
[    0.151775] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.151782] pci 0000:00:1e.0: bridge 32bit mmio: [0xe2000000-0xe20fffff]
[    0.151800] pci_bus 0000:00: on NUMA node 0
[    0.151808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.151949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.152058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[    0.178307] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.178454] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.178595] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.178734] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.178883] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.179031] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.179181] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.179328] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.179743] SCSI subsystem initialized
[    0.179922] libata version 3.00 loaded.
[    0.180140] usbcore: registered new interface driver usbfs
[    0.180177] usbcore: registered new interface driver hub
[    0.180233] usbcore: registered new device driver usb
[    0.180522] ACPI: WMI: Mapper loaded
[    0.180528] PCI: Using ACPI for IRQ routing
[    0.180804] Bluetooth: Core ver 2.15
[    0.180908] NET: Registered protocol family 31
[    0.180912] Bluetooth: HCI device and connection manager initialized
[    0.180918] Bluetooth: HCI socket layer initialized
[    0.180922] NetLabel: Initializing
[    0.180925] NetLabel:  domain hash size = 128
[    0.180927] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.180954] NetLabel:  unlabeled traffic allowed by default
[    0.184747] pnp: PnP ACPI init
[    0.184807] ACPI: bus type pnp registered
[    0.237999] pnp: PnP ACPI: found 14 devices
[    0.238006] ACPI: ACPI bus type pnp unregistered
[    0.238013] PnPBIOS: Disabled by ACPI PNP
[    0.238044] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.238051] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
[    0.238056] system 00:01: ioport range 0x800-0x84f has been reserved
[    0.238061] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.238066] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.238074] system 00:01: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.272909] AppArmor: AppArmor Filesystem Enabled
[    0.272963] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.272967] pci 0000:00:01.0:   IO window: disabled
[    0.272975] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe1ffffff
[    0.272981] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf8ffffff
[    0.272988] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.272993] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.273003] pci 0000:00:1e.0:   MEM window: 0xe2000000-0xe20fffff
[    0.273009] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.273037] pci 0000:00:1e.0: setting latency timer to 64
[    0.273048] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.273052] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.273057] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe1ffffff]
[    0.273061] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf8ffffff]
[    0.273066] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.273070] pci_bus 0000:02: resource 1 mem: [0xe2000000-0xe20fffff]
[    0.273074] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.273078] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.273150] NET: Registered protocol family 2
[    0.273324] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.274081] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.276494] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277721] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277729] TCP reno registered
[    0.278041] NET: Registered protocol family 1
[    0.278212] Trying to unpack rootfs image as initramfs...
[    0.671923] Freeing initrd memory: 8226k freed
[    0.692823] Simple Boot Flag at 0x72 set to 0x1
[    0.692975] cpufreq-nforce2: No nForce2 chipset.
[    0.693025] Scanning for low memory corruption every 60 seconds
[    0.693246] audit: initializing netlink socket (disabled)
[    0.693300] type=2000 audit(1267108782.692:1): initialized
[    0.704596] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.707018] VFS: Disk quotas dquot_6.5.2
[    0.707158] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.708307] fuse init (API version 7.12)
[    0.708482] msgmni has been set to 1244
[    0.709006] alg: No test for stdrng (krng)
[    0.709038] io scheduler noop registered
[    0.709042] io scheduler anticipatory registered
[    0.709045] io scheduler deadline registered
[    0.709173] io scheduler cfq registered (default)
[    0.709258] pci 0000:01:00.0: Boot video device
[    0.709289] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.709444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.709484] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.709703] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.709711] ACPI: Power Button [PWRF]
[    0.709813] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1
[    0.709818] ACPI: Power Button [PWRB]
[    0.710096] processor LNXCPU:00: registered as cooling_device0
[    0.710103] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.732734] thermal LNXTHERM:01: registered as thermal_zone0
[    0.732752] ACPI: Thermal Zone [THM0] (12 C)
[    0.732868] isapnp: Scanning for PnP cards...
[    0.776128] Switched to high resolution mode on CPU 0
[    1.087388] isapnp: No Plug & Play device found
[    1.089430] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.089606] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.089734] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.090251] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.090420] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.092188] brd: module loaded
[    1.092992] loop: module loaded
[    1.093210] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.093438] ata_piix 0000:00:1f.1: version 2.13
[    1.093566] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.093796] scsi0 : ata_piix
[    1.094034] scsi1 : ata_piix
[    1.095706] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[    1.095712] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[    1.097294] Fixed MDIO Bus: probed
[    1.097364] PPP generic driver version 2.4.2
[    1.097598] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.097651] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.097674] uhci_hcd: USB Universal Host Controller Interface driver
[    1.097784]   alloc irq_desc for 19 on node -1
[    1.097789]   alloc kstat_irqs on node -1
[    1.097804] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.097822] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    1.097828] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    1.097965] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    1.098018] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00001820
[    1.098231] usb usb1: configuration #1 chosen from 1 choice
[    1.098290] hub 1-0:1.0: USB hub found
[    1.098313] hub 1-0:1.0: 2 ports detected
[    1.098423]   alloc irq_desc for 23 on node -1
[    1.098428]   alloc kstat_irqs on node -1
[    1.098440] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.098455] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    1.098461] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    1.098550] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    1.098599] uhci_hcd 0000:00:1f.4: irq 23, io base 0x00001840
[    1.098770] usb usb2: configuration #1 chosen from 1 choice
[    1.098825] hub 2-0:1.0: USB hub found
[    1.098846] hub 2-0:1.0: 2 ports detected
[    1.099056] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 1
[    1.099061] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.099409] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.099882] mice: PS/2 mouse device common for all mice
[    1.100099] rtc_cmos 00:04: RTC can wake from S4
[    1.100195] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.100232] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.100454] device-mapper: uevent: version 1.0.3
[    1.100701] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.100876] device-mapper: multipath: version 1.1.0 loaded
[    1.100884] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.101180] EISA: Probing bus 0 at eisa.0
[    1.101194] Cannot allocate resource for EISA slot 1
[    1.101198] Cannot allocate resource for EISA slot 2
[    1.101226] EISA: Detected 0 cards.
[    1.101353] cpuidle: using governor ladder
[    1.101357] cpuidle: using governor menu
[    1.102326] TCP cubic registered
[    1.102573] NET: Registered protocol family 10
[    1.103410] lo: Disabled Privacy Extensions
[    1.103936] NET: Registered protocol family 17
[    1.104047] Bluetooth: L2CAP ver 2.13
[    1.104051] Bluetooth: L2CAP socket layer initialized
[    1.104055] Bluetooth: SCO (Voice Link) ver 0.6
[    1.104058] Bluetooth: SCO socket layer initialized
[    1.104165] Bluetooth: RFCOMM TTY layer initialized
[    1.104171] Bluetooth: RFCOMM socket layer initialized
[    1.104174] Bluetooth: RFCOMM ver 1.11
[    1.104257] Using IPI No-Shortcut mode
[    1.104457] PM: Resume from disk failed.
[    1.104488] registered taskstats version 1
[    1.104644]   Magic number: 14:470:688
[    1.104776] rtc_cmos 00:04: setting system clock to 2010-02-25 14:39:44 UTC (1267108784)
[    1.104782] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.104785] EDD information not available.
[    1.119388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.256989] ata1.00: ATA-5: MAXTOR 6L040J2, A93.0500, max UDMA/133
[    1.256995] ata1.00: 78177792 sectors, multi 16: LBA 
[    1.272400] ata1.00: configured for UDMA/100
[    1.272646] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L040J2   A93. PQ: 0 ANSI: 5
[    1.272918] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.273037] sd 0:0:0:0: [sda] 78177792 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.273130] sd 0:0:0:0: [sda] Write Protect is off
[    1.273135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.273181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.273462]  sda:
[    1.280362] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8160B, 0009, max UDMA/66
[    1.280422] ata2.01: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
[    1.283347]  sda1 sda2 <
[    1.296293] ata2.00: configured for UDMA/66
[    1.296783]  sda5 sda6 >
[    1.303415] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.312312] ata2.01: configured for UDMA/66
[    1.318277] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8160B 0009 PQ: 0 ANSI: 5
[    1.328997] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[    1.329006] Uniform CD-ROM driver Revision: 3.20
[    1.329224] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.329347] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.330847] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.05 PQ: 0 ANSI: 5
[    1.335115] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.335316] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.335440] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.335503] Freeing unused kernel memory: 540k freed
[    1.336910] Write protecting the kernel text: 4568k
[    1.336964] Write protecting the kernel read-only data: 1836k
[    1.412090] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    1.569110] ramzswap: disk size set to 159400 kB
[    1.696928] Linux agpgart interface v0.103
[    1.724791] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    1.728933] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe4000000
[    1.733116] usb 1-1: configuration #1 chosen from 1 choice
[    1.793046] Floppy drive(s): fd0 is 1.44M
[    1.799981] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.799988] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.800139]   alloc irq_desc for 20 on node -1
[    1.800143]   alloc kstat_irqs on node -1
[    1.800159] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.824196] e100 0000:02:08.0: PME# disabled
[    1.837168] FDC 0 is a National Semiconductor PC87306
[    1.848606] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.005420] Adding 159396k swap on /dev/ramzswap0.  Priority:100 extents:1 across:159396k SSD
[    2.080261] e100: eth0: e100_probe: addr 0xe2000000, irq 20, MAC addr 00:02:55:d7:5f:4d
[    2.110874] usb 2-1: configuration #1 chosen from 1 choice
[    2.127006] usbcore: registered new interface driver hiddev
[    2.146955] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1f.4/usb2/2-1/2-1:1.0/input/input4
[    2.147142] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1f.4-1/input0
[    2.147186] usbcore: registered new interface driver usbhid
[    2.147192] usbhid: v2.6:USB HID core driver
[    3.036100] xor: automatically using best checksumming function: pIII_sse
[    3.056011]    pIII_sse  :  2547.000 MB/sec
[    3.056015] xor: using function: pIII_sse (2547.000 MB/sec)
[    3.096612] device-mapper: dm-raid45: initialized v0.2594b
[    3.564584] PM: Starting manual resume from disk
[    3.564596] PM: Resume from partition 8:5
[    3.564599] PM: Checking hibernation image.
[    3.565003] PM: Resume from disk failed.
[    3.573425] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.573436] EXT4-fs (sda6): write access will be enabled during recovery
[    3.582393] EXT4-fs (sda6): barriers enabled
[    6.961124] kjournald2 starting: pid 345, dev sda6:8, commit interval 5 seconds
[    6.961180] EXT4-fs (sda6): delayed allocation enabled
[    6.961187] EXT4-fs: file extents enabled
[    6.961823] EXT4-fs: mballoc enabled
[    6.961856] EXT4-fs (sda6): orphan cleanup on readonly fs
[    6.961875] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 15084
[    6.980623] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 264616
[    6.980650] EXT4-fs (sda6): 2 orphan inodes deleted
[    6.980656] EXT4-fs (sda6): recovery complete
[    7.134865] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   19.437186] Adding 489940k swap on /dev/sda5.  Priority:-1 extents:1 across:489940k 
[   19.455918] udev: starting version 147
[   19.637895] Linux video capture interface: v2.00
[   20.280684] saa7130/34: v4l2 driver version 0.2.15 loaded
[   20.280794]   alloc irq_desc for 22 on node -1
[   20.280799]   alloc kstat_irqs on node -1
[   20.280813] saa7134 0000:02:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.280825] saa7134[0]: found at 0000:02:0e.0, rev: 1, irq: 22, latency: 123, mmio: 0xe2001000
[   20.280838] saa7134[0]: subsystem: 1131:0000, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[   20.280872] saa7134[0]: board init: gpio is 804000
[   20.280883] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.285947] intel_rng: Firmware space is locked read-only. If you can't or
[   20.285951] intel_rng: don't want to disable this in firmware setup, and if
[   20.285953] intel_rng: you are certain that your system has a functional
[   20.285955] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   20.355533] parport_pc 00:0d: reported by Plug and Play ACPI
[   20.355722] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   20.384504] saa7134[0]: Huh, no eeprom present (err=-5)?
[   20.384516] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[   20.721574] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   20.721819] usbcore: registered new interface driver btusb
[   20.752277] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.824760] nvidia: module license 'NVIDIA' taints kernel.
[   20.824769] Disabling lock debugging due to kernel taint
[   21.092742] ppdev: user-space parallel port driver
[   21.229726]   alloc irq_desc for 16 on node -1
[   21.229733]   alloc kstat_irqs on node -1
[   21.229837] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.230615] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   21.232109] All bytes are equal. It is not a TEA5767
[   21.232331] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   21.268075] mt20xx 0-0060: microtune: companycode=3c3c part=3c rev=3c
[   21.268084] mt20xx 0-0060: microtune unknown found, not (yet?) supported, sorry :-/
[   21.268317] tuner 0-0060: Tuner has no way to set tv freq
[   21.268324] tuner 0-0060: Tuner has no way to set tv freq
[   21.268637] saa7134[0]: registered device video0 [v4l2]
[   21.268693] saa7134[0]: registered device vbi0
[   21.277809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.279741]   alloc irq_desc for 17 on node -1
[   21.279748]   alloc kstat_irqs on node -1
[   21.279765] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.279803] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.290820] tuner 0-0060: Tuner has no way to set tv freq
[   21.295102] tuner 0-0060: Tuner has no way to set tv freq
[   21.334335] saa7134 ALSA driver for DMA sound loaded
[   21.334368] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.334407] saa7134[0]/alsa: saa7134[0] at 0xe2001000 irq 22 registered as card -2
[   21.896036] intel8x0_measure_ac97_clock: measured 52539 usecs (2942 samples)
[   21.896045] intel8x0: clocking to 41145
[   24.128349] EXT4-fs (sda6): internal journal on sda6:8
[   25.220214] EXT4-fs (sda1): barriers enabled
[   25.223224] kjournald2 starting: pid 710, dev sda1:8, commit interval 5 seconds
[   25.223572] EXT4-fs (sda1): internal journal on sda1:8
[   25.223579] EXT4-fs (sda1): delayed allocation enabled
[   25.223585] EXT4-fs: file extents enabled
[   25.223923] EXT4-fs: mballoc enabled
[   25.223954] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   25.802772] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.000568] type=1505 audit(1267108809.395:2): operation="profile_load" pid=873 name=/usr/share/gdm/guest-session/Xsession
[   26.005334] type=1505 audit(1267108809.399:3): operation="profile_load" pid=877 name=/sbin/dhclient3
[   26.006157] type=1505 audit(1267108809.399:4): operation="profile_load" pid=877 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.006606] type=1505 audit(1267108809.399:5): operation="profile_load" pid=877 name=/usr/lib/connman/scripts/dhclient-script
[   26.063446] type=1505 audit(1267108809.455:6): operation="profile_load" pid=878 name=/usr/bin/evince
[   26.184821] type=1505 audit(1267108809.579:7): operation="profile_load" pid=878 name=/usr/bin/evince-previewer
[   26.209513] type=1505 audit(1267108809.603:8): operation="profile_load" pid=878 name=/usr/bin/evince-thumbnailer
[   26.259050] type=1505 audit(1267108809.651:9): operation="profile_load" pid=897 name=/usr/bin/freshclam
[   26.286576] type=1505 audit(1267108809.679:10): operation="profile_load" pid=898 name=/usr/lib/cups/backend/cups-pdf
[   26.287590] type=1505 audit(1267108809.679:11): operation="profile_load" pid=898 name=/usr/sbin/cupsd
[   26.891803] tuner 0-0060: Tuner has no way to set tv freq
[   26.911829] tuner 0-0060: Tuner has no way to set tv freq
[   27.526151] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   27.526178] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   27.526208] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   27.816211] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   27.820728] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.337761] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.337768] Bluetooth: BNEP filters: protocol multicast
[   30.408366] Bridge firewalling registered
[   38.552059] eth0: no IPv6 routers present
midhaat@midhaat-desktop:~$

---

### Post by gfuggs on 2010-02-25
> **midhatt said:**
> [   19.637895] Linux video capture interface: v2.00
[   20.280684] saa7130/34: v4l2 driver version 0.2.15 loaded
[   20.280794]   alloc irq_desc for 22 on node -1
[   20.280799]   alloc kstat_irqs on node -1
[   20.280813] saa7134 0000:02:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.280825] saa7134[0]: found at 0000:02:0e.0, rev: 1, irq: 22, latency: 123, mmio: 0xe2001000
[   20.280838] saa7134[0]: subsystem: 1131:0000, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[   20.280872] saa7134[0]: board init: gpio is 804000
[   20.280883] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   20.384504] saa7134[0]: Huh, no eeprom present (err=-5)?
[B][   21.232331] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   21.268075] mt20xx 0-0060: microtune: companycode=3c3c part=3c rev=3c
[   21.268084] mt20xx 0-0060: microtune unknown found, not (yet?) supported, sorry :-/[/B]
[   21.268317] tuner 0-0060: Tuner has no way to set tv freq
[   21.268324] tuner 0-0060: Tuner has no way to set tv freq
[   21.268637] saa7134[0]: registered device video0 [v4l2]
[   21.268693] saa7134[0]: registered device vbi0
[   21.277809] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.279741]   alloc irq_desc for 17 on node -1
[   21.279748]   alloc kstat_irqs on node -1
[   21.279765] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.279803] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.290820] tuner 0-0060: Tuner has no way to set tv freq
[   21.295102] tuner 0-0060: Tuner has no way to set tv freq
[   21.334335] saa7134 ALSA driver for DMA sound loaded
[   21.334368] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   21.334407] saa7134[0]/alsa: saa7134[0] at 0xe2001000 irq 22 registered as card -2
[   26.891803] tuner 0-0060: Tuner has no way to set tv freq
[   26.911829] tuner 0-0060: Tuner has no way to set tv freq

midhaat@midhaat-desktop:~$

It looks like this is what's keeping it from working.  Sorry, but I can't offer any suggestions other than to look into this message and see if you can figure out what's going on.  Good luck.

---


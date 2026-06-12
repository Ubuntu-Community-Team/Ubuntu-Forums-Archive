---
title: "shrill beeps (not from BIOS)"
date: 2008-07-11
forum: General Help
---

### Post by scholzilla on 2008-07-11
Though I have system beeps disabled on my laptop, I get about 5 shrill beeps about halfway through the ubuntu splash screen routine. I've been told by a computer repair guy that these are not BIOS beeps because such beeps would occur earlier (I guess that means when GRUB is loading). This problem occurs about a third of the times I start ubuntu. Just to be sure these beeps aren't from BIOS, I checked if my RAM is inserted properly and it is. Has anyone seen this?

---

### Post by dracayr on 2008-07-11
you mean the splash screen where the orange bar fills up? In that case, press esc when GRUB is loading and edit (press e) the line in your Ubuntu entry in which it says "splash". remove the "splash". then press esc and b and see if you get an error message when the beeps occur

dracayr

---

### Post by scholzilla on 2008-07-16
Yeah, I do mean that splash sceen. When I hit esc to follow your directions, I get a couple of options. Are you talking about deleting the entry that starts with initrd: or something like that? How do I restore it once I've removed it?

thanks again

---

### Post by NilsE on 2008-07-16
> **scholzilla said:**
> Yeah, I do mean that splash sceen. When I hit esc to follow your directions, I get a couple of options. Are you talking about deleting the entry that starts with initrd: or something like that? How do I restore it once I've removed it?

thanks again
NO, don't do that.  He is not suggesting you delete the entire line.  He is just saying remove the splash entry from the line.  Remember where it was so you can put it back the same way you removed it.

---

### Post by Steveway on 2008-07-16
On the next boot the first thing you should do is typing in the following command into a terminal:
dmesg
And post the output of it here.

---

### Post by scholzilla on 2008-07-17
OK, so I was finally able to reproduce the beeps. They don't occur every time I boot up, as I mentioned. Here's the output from dmesg. It's really long and seems like the clock is resetting?:

```
Log of dmesg 
Thu Jul 17 15:42:01 2008

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e80000 (usable)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037e92000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e92000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f85d0
[    0.000000] Entering add_active_range(0, 0, 228992) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   228992
[    0.000000]   HighMem    228992 ->   228992
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   228992
[    0.000000] On node 0 totalpages: 228992
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223139 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8530 checksum 0
[    0.000000] ACPI: RSDP 000F8530, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 37E8C396, 0038 (r1 GATEWA SYSTEM   20061101  LTP        0)
[    0.000000] ACPI: FACP 37E91BFA, 0074 (r1 GATEWA SYSTEM   20061101 ATI     F4240)
[    0.000000] ACPI: DSDT 37E8C3CE, 582C (r1 GATEWA SYSTEM   20061101 MSFT  100000E)
[    0.000000] ACPI: FACS 37E92FC0, 0040
[    0.000000] ACPI: SSDT 37E91C6E, 0182 (r1 GATEWA SYSTEM   20061101  LTP        1)
[    0.000000] ACPI: APIC 37E91DF0, 005E (r1 GATEWA SYSTEM   20061101  LTP        0)
[    0.000000] ACPI: MCFG 37E91E4E, 003C (r1 GATEWA SYSTEM   20061101  LTP        0)
[    0.000000] ACPI: SLIC 37E91E8A, 0176 (r1 GATEWA SYSTEM   20061101  LTP        0)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227203
[    0.000000] Kernel command line: root=UUID=5c8769ce-5d24-4653-aed5-0b45c385fff9 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.050 MHz processor.
[   16.017723] Console: colour VGA+ 80x25
[   16.017727] console [tty0] enabled
[   16.018059] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.018471] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.034887] Memory: 895996k/915968k available (2177k kernel code, 19468k reserved, 1006k data, 368k init, 0k highmem)
[   16.034896] virtual kernel memory layout:
[   16.034898]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.034899]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.034900]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.034902]     lowmem  : 0xc0000000 - 0xf7e80000   ( 894 MB)
[   16.034903]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.034904]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   16.034906]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   16.034909] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.034943] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.114899] Calibrating delay using timer specific routine.. 3195.77 BogoMIPS (lpj=6391545)
[   16.114924] Security Framework initialized
[   16.114930] SELinux:  Disabled at boot.
[   16.114943] AppArmor: AppArmor initialized
[   16.114948] Failure registering capabilities with primary security module.
[   16.114957] Mount-cache hash table entries: 512
[   16.115063] Initializing cgroup subsys ns
[   16.115067] Initializing cgroup subsys cpuacct
[   16.115076] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   16.115086] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.115089] CPU: L2 Cache: 512K (64 bytes/line)
[   16.115091] CPU 0(2) -> Core 0
[   16.115093] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   16.115103] Compat vDSO mapped to ffffe000.
[   16.115113] Checking 'hlt' instruction... OK.
[   16.131172] SMP alternatives: switching to UP code
[   16.132479] Early unpacking initramfs... done
[   16.509373] ACPI: Core revision 20070126
[   16.509445] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.979402] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
[   16.979422] SMP alternatives: switching to SMP code
[   16.979933] Booting processor 1/1 eip 3000
[   16.990611] Initializing CPU#1
[   17.070737] Calibrating delay using timer specific routine.. 3192.24 BogoMIPS (lpj=6384487)
[   17.070744] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   17.070752] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.070755] CPU: L2 Cache: 512K (64 bytes/line)
[   17.070757] CPU 1(2) -> Core 1
[   17.070759] AMD C1E detected late. 	Force timer broadcast.
[   17.070761] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   17.070274] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
[   17.070291] Total of 2 processors activated (6388.01 BogoMIPS).
[   17.070458] ENABLING IO-APIC IRQs
[   17.070642] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   17.110473] Brought up 2 CPUs
[   17.110500] CPU0 attaching sched-domain:
[   17.110503]  domain 0: span 03
[   17.110505]   groups: 01 02
[   17.110509] CPU1 attaching sched-domain:
[   17.110511]  domain 0: span 03
[   17.110513]   groups: 02 01
[   17.110727] net_namespace: 64 bytes
[   17.110737] Booting paravirtualized kernel on bare hardware
[   17.111249] Time:  0:46:23  Date: 07/17/08
[   17.111277] NET: Registered protocol family 16
[   17.111488] EISA bus registered
[   17.111493] ACPI: bus type pci registered
[   17.128419] PCI: BIOS BUG #81[49435000] found
[   17.128462] PCI: Using configuration type 1
[   17.128477] Setting up standard PCI resources
[   17.130344] ACPI: EC: Look up EC in DSDT
[   17.132711] ACPI: Interpreter enabled
[   17.132714] ACPI: (supports S0 S3 S4 S5)
[   17.132727] ACPI: Using IOAPIC for interrupt routing
[   17.137221] ACPI: EC: non-query interrupt received, switching to interrupt mo
de
[   17.138279] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   17.138282] ACPI: EC: driver started in interrupt mode
[   17.138333] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.139693] PCI: Transparent bridge - 0000:00:14.4
[   17.139781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.139949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   17.140083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   17.140189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   17.142607] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.142764] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.142918] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11) *0, disabled
[   17.143078] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143231] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143384] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143535] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143687] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143840] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 11) *0, disabled
.
[   17.143972] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.144010] pnp: PnP ACPI init
[   17.144017] ACPI: bus type pnp registered
[   17.146480] pnp: PnP ACPI: found 10 devices
[   17.146483] ACPI: ACPI bus type pnp unregistered
[   17.146486] PnPBIOS: Disabled by ACPI PNP
[   17.146749] PCI: Using ACPI for IRQ routing
[   17.146752] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, 
post a report
[   17.163021] NET: Registered protocol family 8
[   17.163023] NET: Registered protocol family 20
[   17.163098] AppArmor: AppArmor Filesystem Enabled
[   17.179039] system 00:01: iomem range 0xe0000000-0xefffffff could not be rese
rved
[   17.179042] system 00:01: iomem range 0xfec00000-0xfec00fff could not be rese
rved
[   17.179046] system 00:01: iomem range 0xfee00000-0xfee00fff could not be rese
rved
[   17.179055] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   17.179058] system 00:08: ioport range 0x220-0x22f has been reserved
[   17.179061] system 00:08: ioport range 0x40b-0x40b has been reserved
[   17.179064] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.179067] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   17.179070] system 00:08: ioport range 0x530-0x537 has been reserved
[   17.179073] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   17.179076] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   17.179079] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   17.179082] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   17.179086] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   17.179089] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   17.179092] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   17.179095] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   17.179098] system 00:08: ioport range 0x8000-0x805f has been reserved
[   17.179101] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   17.179104] system 00:08: ioport range 0x87f-0x87f has been reserved
[   17.179111] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   17.179115] system 00:09: iomem range 0xfff00000-0xffffffff could not be rese
rved
[   17.179118] system 00:09: iomem range 0x0-0xfff could not be reserved
[   17.209563] PCI: Bridge: 0000:00:01.0
[   17.209565]   IO window: 9000-9fff
[   17.209569]   MEM window: c0100000-c01fffff
[   17.209572]   PREFETCH window: c8000000-cfffffff
[   17.209575] PCI: Bridge: 0000:00:04.0
[   17.209577]   IO window: a000-afff
[   17.209580]   MEM window: c0200000-c02fffff
[   17.209583]   PREFETCH window: disabled.
[   17.209594] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[   17.209597]   IO window: 00001400-000014ff
[   17.209603]   IO window: 00001800-000018ff
[   17.209608]   PREFETCH window: 50000000-53ffffff
[   17.209615]   MEM window: 54000000-57ffffff
[   17.209620] PCI: Bridge: 0000:00:14.4
[   17.209622]   IO window: disabled.
[   17.209628]   MEM window: c0300000-c03fffff
[   17.209632]   PREFETCH window: disabled.
[   17.209652] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.209679] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 20 (level, low) -> IRQ
 16
[   17.209697] NET: Registered protocol family 2
[   17.210282] Time: acpi_pm clocksource has been installed.
[   17.210287] Clockevents: could not switch to one-shot mode: lapic is not func
tional.
[   17.210291] Could not switch to high resolution mode on CPU 0
[   17.214969] Clockevents: could not switch to one-shot mode: lapic is not func
tional.
[   17.214973] Could not switch to high resolution mode on CPU 1
[   17.247024] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.247328] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[   17.248070] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.248431] TCP: Hash tables configured (established 131072 bind 65536)
[   17.248434] TCP reno registered
[   17.263096] checking if image is initramfs... it is
[   17.994917] Freeing initrd memory: 7324k freed
[   17.995745] audit: initializing netlink socket (disabled)
[   17.995757] audit(1216255583.500:1): initialized
[   17.998078] VFS: Disk quotas dquot_6.5.1
[   17.998159] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.998308] io scheduler noop registered
[   17.998311] io scheduler anticipatory registered
[   17.998313] io scheduler deadline registered
[   17.998325] io scheduler cfq registered (default)
[   17.998332] PCI: MSI quirk detected. MSI deactivated.
[   17.998382] Boot video device is 0000:01:05.0
[   17.998522] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.998545] assign_interrupt_mode Found MSI capability
[   17.998549] Allocate Port Service[0000:00:04.0:pcie00]
[   17.998805] isapnp: Scanning for PnP cards...
[   18.352585] isapnp: No Plug & Play device found
[   18.384797] Real Time Clock Driver v1.12ac
[   18.384915] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing 
enabled
[   18.386234] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   18.386322] input: Macintosh mouse button emulation as /devices/virtual/input
/input0
[   18.386425] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq
 1,12
[   18.389179] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.389185] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.402005] mice: PS/2 mouse device common for all mice
[   18.402146] EISA: Probing bus 0 at eisa.0
[   18.402155] Cannot allocate resource for EISA slot 1
[   18.402186] Cannot allocate resource for EISA slot 8
[   18.402189] EISA: Detected 0 cards.
[   18.402192] cpuidle: using governor ladder
[   18.402194] cpuidle: using governor menu
[   18.402287] NET: Registered protocol family 1
[   18.402313] Using IPI No-Shortcut mode
[   18.402348] registered taskstats version 1
[   18.402449]   Magic number: 0:515:759
[   18.402599] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.402601] EDD information not available.
[   18.402856] Freeing unused kernel memory: 368k freed
[   18.430989] input: AT Translated Set 2 keyboard as /devices/platform/i8042/se
rio0/input/input1
[   19.650536] fuse init (API version 7.9)
[   19.672710] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.675150] ACPI: Thermal Zone [THRM] (26 C)
[   19.840191] usbcore: registered new interface driver usbfs
[   19.840216] usbcore: registered new interface driver hub
[   19.846294] usbcore: registered new device driver usb
[   19.848139] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[   19.848190] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ
 17
[   19.848205] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   19.848489] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus numbe
r 1
[   19.848516] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0004000
[   19.904202] usb usb1: configuration #1 chosen from 1 choice
[   19.904230] hub 1-0:1.0: USB hub found
[   19.904241] hub 1-0:1.0: 4 ports detected
[   20.008088] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ
 17
[   20.008108] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   20.008139] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus numbe
r 2
[   20.008158] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0005000
[   20.064047] usb usb2: configuration #1 chosen from 1 choice
[   20.064079] hub 2-0:1.0: USB hub found
[   20.064090] hub 2-0:1.0: 4 ports detected
[   20.075677] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.075682] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[   20.168040] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ
 17
[   20.168055] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   20.168088] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus numbe
r 3
[   20.168142] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0006000
[   20.179815] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[   20.179943] usb usb3: configuration #1 chosen from 1 choice
[   20.179967] hub 3-0:1.0: USB hub found
[   20.179974] hub 3-0:1.0: 8 ports detected
[   20.284024] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000
:00:14.1
[   20.284047] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ
 18
[   20.284056] ATIIXP: not 100% native mode: will probe irqs later
[   20.284066]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DM
A
[   20.284081] ATIIXP: simplex device: DMA disabled
[   20.284083] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   20.284087] Probing IDE interface ide0...
[   20.567483] usb 3-6: new high speed USB device using ehci_hcd and address 2
[   20.706757] usb 3-6: configuration #1 chosen from 1 choice
[   21.075490] hdb: HL-DT-ST DVDRAM GSA-T10N, ATAPI CD/DVD-ROM drive
[   21.411238] hda: Hitachi HTS541616J9AT00, ATA DISK drive
[   21.411253] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   21.411454] hda: UDMA/100 mode selected
[   21.411647] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   21.412479] hdb: UDMA/33 mode selected
[   21.413022] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   21.433900] Probing IDE interface ide1...
[   22.006391] ACPI: PCI Interrupt 0000:05:09.1[B] -> GSI 21 (level, low) -> IRQ
 21
[   22.056169] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0305000
-c03057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   22.057082] SCSI subsystem initialized
[   22.064791] libata version 3.00 loaded.
[   22.083287] hda: max request size: 512KiB
[   22.084399] hda: 312581808 sectors (160041 MB) w/7512KiB Cache, CHS=19457/255
/63
[   22.086274] hda: cache flushes supported
[   22.086310]  hda: hda1 hda2 < hda5 >
[   22.145200] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   22.145206] Uniform CD-ROM driver Revision: 3.20
[   22.703878] Attempting manual resume
[   22.703882] swsusp: Resume From Partition 3:5
[   22.703884] PM: Checking swsusp image.
[   22.711387] PM: Resume from disk failed.
[   22.781044] kjournald starting.  Commit interval 5 seconds
[   22.781710] EXT3-fs: mounted filesystem with ordered data mode.
[   23.338113] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b8036703d2a9]
[   31.483667] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.528156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.568213] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.674661] Linux agpgart interface v0.102
[   31.707325] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   31.872691] input: Power Button (FF) as /devices/virtual/input/input3
[   31.915059] ACPI: Power Button (FF) [PWRF]
[   31.915168] input: Lid Switch as /devices/virtual/input/input4
[   31.947315] ACPI: Lid Switch [LID]
[   31.947382] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.010974] ACPI: Sleep Button (CM) [SLPB]
[   32.011045] input: Power Button (CM) as /devices/virtual/input/input6
[   32.059675] Yenta: CardBus bridge found at 0000:05:09.0 [107b:0367]
[   32.059703] Yenta: Using CSCINT to route CSC interrupts to PCI
[   32.059706] Yenta: Routing CardBus interrupts to PCI
[   32.059712] Yenta TI: socket 0000:05:09.0, mfunc 0x01ac1b22, devctl 0x64
[   32.074921] ACPI: Power Button (CM) [PWRB]
[   32.216033] ACPI: AC Adapter [ACAD] (on-line)
[   32.302905] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   32.302911] Socket status: 30000006
[   32.302915] pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
[   32.342186] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 20 (level, low) -> IRQ
 16
[   32.349477] ACPI: Battery Slot [BAT1] (battery present)
[   32.655777] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ
 18
[   32.655792] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   32.655827] sky2 0000:02:00.0: v1.20 addr 0xc0200000 irq 18 Yukon-FE (0xb7) r
ev 1
[   32.656117] sky2 eth0: addr 00:e0:b8:d3:d8:d5
[   32.761255] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa047
13/0x10008
[   32.794067] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/seri
o1/input/input7
[   32.882747] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/dev
ice:18/LNXVIDEO:00/input/input8
[   32.938185] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.071258] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ
 18
[   33.360848] phy0: Selected rate control algorithm 'simple'
[   33.462733] phy0: hwaddr 00:c0:a8:d8:96:a1, rtl8187 V1 + rtl8225z2
[   33.462753] usbcore: registered new interface driver rtl8187
[   34.337535] cs: IO port probe 0x100-0x3af: clean.
[   34.339882] cs: IO port probe 0x3e0-0x4ff: clean.
[   34.340861] cs: IO port probe 0x820-0x8ff: clean.
[   34.341679] cs: IO port probe 0xc00-0xcf7: clean.
[   34.342556] cs: IO port probe 0xa00-0xaff: clean.
[   35.361409] lp: driver loaded but no devices found
[   35.513483] Adding 2642652k swap on /dev/hda5.  Priority:-1 extents:1 across:
2642652k
[   36.062282] EXT3 FS on hda1, internal journal
[   37.404183] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.875604] No dock devices found.
[   38.237180] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52
 processors (2 cpu cores) (version 2.20.00)
[   38.236593] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[   38.236599] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x14
[   39.051895] apm: BIOS not found.
[   39.214230] ppdev: user-space parallel port driver
[   39.336285] audit(1216255606.126:2): type=1503 operation="inode_permission" r
equested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4966 profile="/usr/sbi
n/cupsd" namespace="default"
[   39.906517] Clocksource tsc unstable (delta = -248021839 ns)
[   40.494157] Bluetooth: Core ver 2.11
[   40.494243] NET: Registered protocol family 31
[   40.494245] Bluetooth: HCI device and connection manager initialized
[   40.494250] Bluetooth: HCI socket layer initialized
[   40.521535] Bluetooth: L2CAP ver 2.9
[   40.521540] Bluetooth: L2CAP socket layer initialized
[   40.567746] Bluetooth: RFCOMM socket layer initialized
[   40.568016] Bluetooth: RFCOMM TTY layer initialized
[   40.568020] Bluetooth: RFCOMM ver 1.8
[   42.618655] hda-intel: Invalid position buffer, using LPIB read method instea
d.
[   42.838140] usb 3-3: new high speed USB device using ehci_hcd and address 3
[   43.001189] usb 3-3: configuration #1 chosen from 1 choice
[   45.379886] phy1: Selected rate control algorithm 'simple'
[   45.380263] usbcore: registered new interface driver rt73usb
[   45.408887] sky2 eth0: enabling interface
[   46.062639] NET: Registered protocol family 17
[   52.041651] NET: Registered protocol family 10
[   52.042121] lo: Disabled Privacy Extensions
[   52.042933] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.043759] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.044667] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   57.065298] CPU0 attaching NULL sched-domain.
[   57.065308] CPU1 attaching NULL sched-domain.
[   57.087460] CPU0 attaching sched-domain:
[   57.087471]  domain 0: span 03
[   57.087475]   groups: 01 02
[   57.087484] CPU1 attaching sched-domain:
[   57.087488]  domain 0: span 03
[   57.087491]   groups: 02 01
[   63.169699] wlan0: Initial auth_alg=0
[   63.169706] wlan0: authenticate with AP 00:17:3f:df:e6:c7
[   63.269365] wlan0: authenticate with AP 00:17:3f:df:e6:c7
[   63.369293] wlan0: authenticate with AP 00:17:3f:df:e6:c7
[   63.469219] wlan0: authentication with AP 00:17:3f:df:e6:c7 timed out
[  103.250524] wlan1: Initial auth_alg=0
[  103.250532] wlan1: authenticate with AP 00:17:3f:df:e6:c7
[  103.252103] wlan1: RX authentication from 00:17:3f:df:e6:c7 (alg=0 transactio
n=2 status=0)
[  103.252110] wlan1: authenticated
[  103.252114] wlan1: associate with AP 00:17:3f:df:e6:c7
[  103.256597] wlan1: RX AssocResp from 00:17:3f:df:e6:c7 (capab=0x421 status=0 
aid=1)
[  103.256603] wlan1: associated
[  103.256609] wlan1: CTS protection enabled (BSSID=00:17:3f:df:e6:c7)
[  103.256614] wlan1: switched to short barker preamble (BSSID=00:17:3f:df:e6:c7
)
[  103.259626] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  108.292264] wlan1: no IPv6 routers present
[  121.561723] wlan1: no IPv6 routers present
[  650.988827] wlan1: CTS protection disabled (BSSID=00:17:3f:df:e6:c7)
[  651.652491] wlan1: CTS protection enabled (BSSID=00:17:3f:df:e6:c7)
[  657.791213] wlan1: CTS protection disabled (BSSID=00:17:3f:df:e6:c7)
[  657.893515] wlan1: CTS protection enabled (BSSID=00:17:3f:df:e6:c7)
[ 2918.151117] sky2 eth0: disabling interface
[ 2918.155658] wlan1: deauthenticate(reason=3)
[ 2918.205158] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 2918.234083] usbcore: deregistering interface driver rtl8187
[ 2918.302096] usbcore: deregistering interface driver rt73usb
[ 2920.154138] PM: suspend-to-disk mode set to 'platform'
[ 2920.154249] swsusp: Marking nosave pages: 000000000009d000 - 0000000000100000
[ 2920.154256] swsusp: Basic memory bitmaps created
[ 2920.154259] Syncing filesystems ... done.
[ 2920.154285] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2920.155027] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) don
e.
[ 2920.251273] Shrinking memory... done (73843 pages freed)
[ 2921.366536] Freed 295372 kbytes in 1.11 seconds (266.10 MB/s)
[ 2921.366539] Suspending console(s)
[ 2922.781455] ACPI handle has no context!
[ 2922.781531] ACPI handle has no context!
[ 2922.781553] ACPI: PCI interrupt for device 0000:05:09.2 disabled
[ 2922.781561] ACPI handle has no context!
[ 2922.800623] ACPI handle has no context!
[ 2922.852524] ACPI: PCI interrupt for device 0000:00:14.2 disabled
[ 2922.872620] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[ 2922.888540] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[ 2922.888594] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[ 2922.888952] Disabling non-boot CPUs ...
[ 2922.888973] CPU0 attaching NULL sched-domain.
[ 2922.888975] CPU1 attaching NULL sched-domain.
[ 2923.013023] CPU 1 is now offline
[ 2923.013026] SMP alternatives: switching to UP code
[ 2923.014014] CPU0 attaching sched-domain:
[ 2923.014018]  domain 0: span 01
[ 2923.014020]   groups: 01
[ 2923.014202] CPU1 is down
[ 2923.014434] swsusp: critical section: 
[ 2923.046866] swsusp: Need to copy 87892 pages
[ 2923.046870] swsusp: Normal pages needed: 87892 + 1024 + 20, available pages: 
140994
[   36.551291] Enabling non-boot CPUs ...
[   36.551371] CPU0 attaching NULL sched-domain.
[   36.567261] SMP alternatives: switching to SMP code
[   36.567957] Booting processor 1/1 eip 3000
[   36.578558] Initializing CPU#1
[   36.655710] Calibrating delay using timer specific routine.. 3192.25 BogoMIPS
 (lpj=6384507)
[   36.655718] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f 00000000
[   36.655726] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.655728] CPU: L2 Cache: 512K (64 bytes/line)
[   36.655731] CPU 1(2) -> Core 1
[   36.655733] AMD C1E detected late. 	Force timer broadcast.
[   36.655735] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f 00000000
[   36.655327] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
[   36.655362] CPU0 attaching sched-domain:
[   36.655365]  domain 0: span 03
[   36.655367]   groups: 01 02
[   36.655370] CPU1 attaching sched-domain:
[   36.655372]  domain 0: span 03
[   36.655374]   groups: 02 01
[   36.656236] CPU1 is up
[   36.659722] Clockevents: could not switch to one-shot mode: lapic is not func
tional.
[   36.659725] Could not switch to high resolution mode on CPU 1
[   36.678598] PM: Writing back config space on device 0000:00:04.0 at offset 7 
(was a1a1, writing 2000a1a1)
[   36.678612] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   36.678628] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ
 17
[   36.699084] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ
 17
[   36.739048] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ
 17
[   36.739103] usb usb3: root hub lost power or was reset
[   36.739212] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ
 18
[   36.755041] PM: Writing back config space on device 0000:00:14.2 at offset f 
(was 10a, writing a)
[   36.755068] PM: Writing back config space on device 0000:00:14.2 at offset 1 
(was 4100006, writing 4100002)
[   36.755091] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ
 18
[   36.755253] PM: Writing back config space on device 0000:02:00.0 at offset 1 
(was 40100007, writing 100003)
[   36.755291] PM: Writing back config space on device 0000:05:09.0 at offset f 
(was 344010b, writing 5c0010b)
[   36.755320] PM: Writing back config space on device 0000:05:09.0 at offset 3 
(was 823208, writing 82a820)
[   36.771031] PM: Writing back config space on device 0000:05:09.1 at offset f 
(was 4030200, writing 403020b)
[   36.771057] PM: Writing back config space on device 0000:05:09.1 at offset 5 
(was 0, writing c0300000)
[   36.771064] PM: Writing back config space on device 0000:05:09.1 at offset 4 
(was 0, writing c0305000)
[   36.771071] PM: Writing back config space on device 0000:05:09.1 at offset 3 
(was 800000, writing 804008)
[   36.771080] PM: Writing back config space on device 0000:05:09.1 at offset 1 
(was 2100000, writing 2100016)
[   36.820745] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0305000
-c03057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   36.835022] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 20 (level, low) -> IRQ
 16
[   37.593192] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   37.594906] hda: UDMA/100 mode selected
[   37.597587] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   37.598429] hdb: UDMA/33 mode selected
[   37.598972] PM: Image restored successfully.
[   37.635832] Restarting tasks ... <6>usb 3-3: USB disconnect, address 3
[   37.654506] done.
[   37.654524] swsusp: Basic memory bitmaps freed
[   37.746260] usb 3-3: new high speed USB device using ehci_hcd and address 4
[   38.064186] usb 3-3: configuration #1 chosen from 1 choice
[   38.064441] usb 3-6: USB disconnect, address 2
[   38.174533] usb 3-6: new high speed USB device using ehci_hcd and address 5
[   38.312494] usb 3-6: configuration #1 chosen from 1 choice
[   40.328879] phy0: Selected rate control algorithm 'simple'
[   40.329488] phy0: hwaddr 00:c0:a8:d8:96:a1, rtl8187 V1 + rtl8225z2
[   40.329509] usbcore: registered new interface driver rtl8187
[   46.362541] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.372738] phy1: Selected rate control algorithm 'simple'
[   46.373469] usbcore: registered new interface driver rt73usb
[   46.430223] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ
 18
[   46.430238] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   46.430262] sky2 0000:02:00.0: v1.20 addr 0xc0200000 irq 18 Yukon-FE (0xb7) r
ev 1
[   46.431940] sky2 eth0: addr 00:e0:b8:d3:d8:d5
[   46.519207] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   46.530252] sky2 eth0: enabling interface
[   46.532806] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.926862] sky2 eth0: disabling interface
[   46.946654] sky2 eth0: enabling interface
[   46.949277] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.008641] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   51.568289] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.960245] wlan1: Initial auth_alg=0
[   57.960254] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[   57.961135] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   57.961141] wlan1: authenticated
[   57.961146] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[   57.962315] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[   57.962320] wlan1: associated
[   57.962324] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   57.964279] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   59.409252] wlan1: deauthenticate(reason=3)
[   61.941637] wlan0: Initial auth_alg=0
[   61.941653] wlan0: authenticate with AP 00:0f:3d:3d:e0:4e
[   61.942666] wlan0: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   61.942671] wlan0: authenticated
[   61.942675] wlan0: associate with AP 00:0f:3d:3d:e0:4e
[   61.944034] wlan0: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[   61.944039] wlan0: associated
[   61.944046] wlan0: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   61.945580] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.058793] wlan0: no IPv6 routers present
[  104.889094] wlan0: deauthenticate(reason=3)
[  106.969292] wlan1: Initial auth_alg=0
[  106.969302] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[  106.971811] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[  106.971818] wlan1: authenticated
[  106.971823] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[  106.974197] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[  106.974206] wlan1: associated
[  106.974214] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[  106.976729] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  108.632094] wlan1: deauthenticate(reason=3)
[  111.163518] wlan0: Initial auth_alg=0
[  111.163527] wlan0: authenticate with AP 00:0f:3d:3d:e0:4e
[  111.164591] wlan0: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[  111.164597] wlan0: authenticated
[  111.164600] wlan0: associate with AP 00:0f:3d:3d:e0:4e
[  111.165895] wlan0: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[  111.165901] wlan0: associated
[  111.165907] wlan0: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[  111.167347] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  119.451461] wlan0: no IPv6 routers present
[  119.548954] wlan0: deauthenticate(reason=3)
[  121.400679] wlan1: Initial auth_alg=0
[  121.400689] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[  121.401573] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[  121.401580] wlan1: authenticated
[  121.401584] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[  121.402752] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[  121.402758] wlan1: associated
[  121.402765] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[  121.404790] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  131.402394] wlan1: no IPv6 routers present
[ 2858.597545] wlan1: deauthenticate(reason=3)
[ 2861.356498] wlan0: Initial auth_alg=0
[ 2861.356508] wlan0: authenticate with AP 00:0f:3d:3d:e0:4e
[ 2861.358575] wlan0: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[ 2861.358581] wlan0: authenticated
[ 2861.358584] wlan0: associate with AP 00:0f:3d:3d:e0:4e
[ 2861.361310] wlan0: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[ 2861.361316] wlan0: associated
[ 2861.361322] wlan0: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[ 2861.362804] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2863.733251] wlan0: deauthenticate(reason=3)
[ 2865.175295] wlan1: Initial auth_alg=0
[ 2865.175303] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[ 2865.176193] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[ 2865.176198] wlan1: authenticated
[ 2865.176201] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[ 2865.177310] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[ 2865.177315] wlan1: associated
[ 2865.177319] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[ 2865.179555] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2865.695726] wlan1: deauthenticate(reason=3)
[ 2868.537175] wlan0: Initial auth_alg=0
[ 2868.537185] wlan0: authenticate with AP 00:0f:3d:3d:e0:4e
[ 2868.538808] wlan0: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[ 2868.538814] wlan0: authenticated
[ 2868.538818] wlan0: associate with AP 00:0f:3d:3d:e0:4e
[ 2868.540052] wlan0: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[ 2868.540058] wlan0: associated
[ 2868.540062] wlan0: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[ 2868.541516] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2872.929959] wlan0: deauthenticate(reason=3)
[ 2875.042105] wlan1: Initial auth_alg=0
[ 2875.042114] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[ 2875.043007] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[ 2875.043015] wlan1: authenticated
[ 2875.043020] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[ 2875.044428] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=2)
[ 2875.044434] wlan1: associated
[ 2875.044440] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[ 2875.046435] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2883.398011] wlan1: no IPv6 routers present
[ 3575.214826] sky2 eth0: disabling interface
[ 3575.249712] wlan1: deauthenticate(reason=3)
[ 3575.284776] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 3575.333891] usbcore: deregistering interface driver rtl8187
[ 3575.417024] usbcore: deregistering interface driver rt73usb
[ 3576.566863] PM: suspend-to-disk mode set to 'platform'
[ 3576.566976] swsusp: Marking nosave pages: 000000000009d000 - 0000000000100000
[ 3576.566984] swsusp: Basic memory bitmaps created
[ 3576.566987] Syncing filesystems ... done.
[ 3576.567024] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 3576.567696] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) don
e.
[ 3576.663299] Shrinking memory... done (94682 pages freed)
[ 3577.884358] Freed 378728 kbytes in 1.22 seconds (310.43 MB/s)
[ 3577.884362] Suspending console(s)
[ 3577.886182] ACPI handle has no context!
[ 3577.886252] ACPI handle has no context!
[ 3577.886272] ACPI: PCI interrupt for device 0000:05:09.2 disabled
[ 3577.886293] ACPI handle has no context!
[ 3577.902358] ACPI handle has no context!
[ 3577.934415] ACPI: PCI interrupt for device 0000:00:14.2 disabled
[ 3577.950369] ACPI: PCI interrupt for device 0000:00:13.2 disabled
[ 3577.966291] ACPI: PCI interrupt for device 0000:00:13.1 disabled
[ 3577.966345] ACPI: PCI interrupt for device 0000:00:13.0 disabled
[ 3577.966640] Disabling non-boot CPUs ...
[ 3577.966661] CPU0 attaching NULL sched-domain.
[ 3577.966663] CPU1 attaching NULL sched-domain.
[ 3578.086131] CPU 1 is now offline
[ 3578.086133] SMP alternatives: switching to UP code
[ 3578.087148] CPU0 attaching sched-domain:
[ 3578.087151]  domain 0: span 01
[ 3578.087153]   groups: 01
[ 3578.087384] CPU1 is down
[ 3578.087615] swsusp: critical section: 
[ 3578.126078] swsusp: Need to copy 110432 pages
[ 3578.126082] swsusp: Normal pages needed: 110432 + 1024 + 20, available pages:
 118458
[   41.082783] Enabling non-boot CPUs ...
[   41.082861] CPU0 attaching NULL sched-domain.
[   41.098754] SMP alternatives: switching to SMP code
[   41.099450] Booting processor 1/1 eip 3000
[   41.110003] Initializing CPU#1
[   41.187153] Calibrating delay using timer specific routine.. 3192.21 BogoMIPS
 (lpj=6384427)
[   41.187160] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f 00000000
[   41.187169] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   41.187171] CPU: L2 Cache: 512K (64 bytes/line)
[   41.187174] CPU 1(2) -> Core 1
[   41.187176] AMD C1E detected late. 	Force timer broadcast.
[   41.187178] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f 00000000
[   41.186819] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-52 stepping 02
[   41.186856] CPU0 attaching sched-domain:
[   41.186859]  domain 0: span 03
[   41.186861]   groups: 01 02
[   41.186864] CPU1 attaching sched-domain:
[   41.186866]  domain 0: span 03
[   41.186868]   groups: 02 01
[   41.187688] CPU1 is up
[   41.191166] Clockevents: could not switch to one-shot mode: lapic is not func
tional.
[   41.191169] Could not switch to high resolution mode on CPU 1
[   41.212872] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   41.212889] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ
 17
[   41.234572] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ
 17
[   41.274538] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ
 17
[   41.274593] usb usb3: root hub lost power or was reset
[   41.274703] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ
 18
[   41.290531] PM: Writing back config space on device 0000:00:14.2 at offset f 
(was 10a, writing a)
[   41.290559] PM: Writing back config space on device 0000:00:14.2 at offset 1 
(was 4100006, writing 4100002)
[   41.290581] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ
 18
[   41.290742] PM: Writing back config space on device 0000:02:00.0 at offset 1 
(was 40100007, writing 100003)
[   41.290781] PM: Writing back config space on device 0000:05:09.0 at offset f 
(was 344010b, writing 5c0010b)
[   41.290811] PM: Writing back config space on device 0000:05:09.0 at offset 3 
(was 823208, writing 82a820)
[   41.306518] PM: Writing back config space on device 0000:05:09.1 at offset f 
(was 4030200, writing 403020b)
[   41.306544] PM: Writing back config space on device 0000:05:09.1 at offset 5 
(was 0, writing c0300000)
[   41.306551] PM: Writing back config space on device 0000:05:09.1 at offset 4 
(was 0, writing c0305000)
[   41.306558] PM: Writing back config space on device 0000:05:09.1 at offset 3 
(was 800000, writing 804008)
[   41.306568] PM: Writing back config space on device 0000:05:09.1 at offset 1 
(was 2100000, writing 2100016)
[   41.356232] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0305000
-c03057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   41.370509] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 20 (level, low) -> IRQ
 16
[   42.124695] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   42.126430] hda: UDMA/100 mode selected
[   42.129110] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   42.129954] hdb: UDMA/33 mode selected
[   42.130497] PM: Image restored successfully.
[   42.178872] Restarting tasks ... <6>usb 3-3: USB disconnect, address 4
[   42.201225] done.
[   42.201245] swsusp: Basic memory bitmaps freed
[   42.289748] usb 3-3: new high speed USB device using ehci_hcd and address 6
[   42.610737] usb 3-3: configuration #1 chosen from 1 choice
[   42.610975] usb 3-6: USB disconnect, address 5
[   42.721956] usb 3-6: new high speed USB device using ehci_hcd and address 7
[   42.859970] usb 3-6: configuration #1 chosen from 1 choice
[   44.024963] phy0: Selected rate control algorithm 'simple'
[   44.025580] usbcore: registered new interface driver rt73usb
[   44.036612] udev: renamed network interface wlan0 to wlan1
[   44.458755] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   44.786733] phy1: Selected rate control algorithm 'simple'
[   44.787451] phy1: hwaddr 00:c0:a8:d8:96:a1, rtl8187 V1 + rtl8225z2
[   44.787470] usbcore: registered new interface driver rtl8187
[   44.862585] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ
 18
[   44.862602] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   44.862639] sky2 0000:02:00.0: v1.20 addr 0xc0200000 irq 18 Yukon-FE (0xb7) r
ev 1
[   50.131226] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.140548] sky2 eth0: addr 00:e0:b8:d3:d8:d5
[   50.166878] sky2 eth0: enabling interface
[   50.169507] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.598750] sky2 eth0: disabling interface
[   50.618468] sky2 eth0: enabling interface
[   50.621392] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.516690] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   55.559860] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   64.568732] wlan1: Initial auth_alg=0
[   64.568740] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[   64.569026] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   64.569034] wlan1: authenticated
[   64.569049] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[   64.570195] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=5)
[   64.570201] wlan1: associated
[   64.570208] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   64.572337] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   65.090758] wlan1: deauthenticate(reason=3)
[   68.868770] wlan1: Initial auth_alg=0
[   68.868779] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[   68.869668] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   68.869674] wlan1: authenticated
[   68.869679] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[   68.870785] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=5)
[   68.870790] wlan1: associated
[   68.870795] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   68.872795] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   79.451659] wlan1: no IPv6 routers present
[   82.550811] wlan1: deauthenticate(reason=3)
[   85.085296] wlan0: Initial auth_alg=0
[   85.085304] wlan0: authenticate with AP 00:0f:3d:3d:e0:4e
[   85.086229] wlan0: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   85.086234] wlan0: authenticated
[   85.086237] wlan0: associate with AP 00:0f:3d:3d:e0:4e
[   85.086978] wlan0: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=5)
[   85.086986] wlan0: associated
[   85.086993] wlan0: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   85.088485] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   90.248252] wlan0: deauthenticate(reason=3)
[   91.768632] wlan1: Initial auth_alg=0
[   91.768640] wlan1: authenticate with AP 00:0f:3d:3d:e0:4e
[   91.769533] wlan1: RX authentication from 00:0f:3d:3d:e0:4e (alg=0 transactio
n=2 status=0)
[   91.769540] wlan1: authenticated
[   91.769545] wlan1: associate with AP 00:0f:3d:3d:e0:4e
[   91.770647] wlan1: RX AssocResp from 00:0f:3d:3d:e0:4e (capab=0x421 status=0 
aid=5)
[   91.770652] wlan1: associated
[   91.770657] wlan1: switched to short barker preamble (BSSID=00:0f:3d:3d:e0:4e
)
[   91.772614] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  100.281450] wlan1: no IPv6 routers present

Thu Jul 17 15:42:01 2008
----------------
```

Please note that the BIOS error #81 message is a known bug and has not been associated with such beeps according to other posts. Your help is appreciated.

---

### Post by scholzilla on 2008-07-21
I'm still having issues with the problem in this thread. If anyone has the time for insights, I'd be much obliged. Thanks.

---

### Post by jazzgossen on 2008-07-22
This is just to say that I have the same problem, but I think it only happens when I resume from hibernation, and not at clean boots. It started happening with Ubuntu 8.04, and I have it on both my computers. 

I'll write back here if I figure out what is happening.

---

### Post by mininoteroolz on 2008-07-22
yes same problem here.. beeps while resuming from hibernation. It happens sometimes not all the time. It also complains that hibernation fails once in a while and the battery is all used up.

---

### Post by cszikszoy on 2008-07-22
I'll add a +1, me too, to all of the above.  I have about 5 fast, shrill beeps when resuming from hibernation with 8.04.  Can't really say this didn't happen before, because hibernation didn't work on my laptop before 8.04.

Has anyone filed a bug in launchpad?

I also get an error sometimes complaining about a "sleep problem".  Although it does not seem to always happen when the beeps occur after hibernation.

---

### Post by scholzilla on 2008-07-22
I think my problems predated hardy, though I won't swear by it. I do know I've done 2 fresh installs of the OS and both times the problem occurred. I have not filed a bug report because I didn't know that so many others were having this problem, but I will. I also get the "failure to sleep" message, but my beeps happen both with restarts and awakening from hibernation.


UPDATE: upon further thought, I'm sure that my problems predated Hardy. I have posted this bug on launchpad (Bug #250865) and would encourage others to subscribe to that thread.

---

### Post by mozillar on 2008-07-22
For those getting the shrill beeps & "Your computer failed to suspend" message when waking from suspend, here's a workaround:

uncheck "Use sound to notify in event of error" in
System->Preferences->Power Management->General

That quieted this issue for my laptop. This error would occur occasionally, despite always suspending just fine.

I'm curious if this addresses the issue for those hibernating too.

Yeah, it's kinda crude.

---

### Post by undoIT on 2008-07-25
> **mozillar said:**
> uncheck "Use sound to notify in event of error" in
System->Preferences->Power Management->General

Thank you. The beeps have been silenced!

I am getting this on both my Dell Latitude D830 and XPS M1330. It only occurs after hibernation. It happens every time on the D830 and seems to only happen occasionally on the M1330.

At least it will make a better first impression now if I go to show a friend how cool Ubuntu is and we are not greeted with five shrill beeps upon resuming from hibernation :P

---

### Post by scholzilla on 2008-08-18
Just so everyone knows: This is now a confirmed bug and is being worked on by the ubuntu developers: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250865]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250865")

---

### Post by cszikszoy on 2008-08-18
Thanks, I noticed that this morning as well.  I'll post my ACPI information when I get home.  Hopefully it will be helpful for whomever is working on this.

---


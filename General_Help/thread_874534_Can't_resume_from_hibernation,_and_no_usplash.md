---
title: "Can't resume from hibernation, and no usplash"
date: 2008-07-30
forum: General Help
---

### Post by jazzgossen on 2008-07-30
For a while now, I haven't been able to resume from hibernation, and even at clean boots, there is no graphical progress bar.

What happens at each boot (both clean and trying to resume) is that the Ubuntu splash shows up and the progress bar "bounces" back and forth, but when I think it should start its actual progress, I get dropped to text output with the text "swsusp: Marking nosave pages" (at the 19.59 mark in the syslog below) etc.

I'm posting my syslog from the time I pressed the shut-down icon and chose hibernation and the 40 first seconds after reboot. 

Does anybody see any problems here? (For this particular boot, there was also a routine fsck, but the same thing happens at other boots too.)

```
Jul 29 13:25:43 aenima gnome-power-manager: (martin) GNOME interaktiv utloggning.
Anledning: Strömknappen har använts.
Jul 29 13:25:50 aenima NetworkManager: <info>  Going to sleep. 
Jul 29 13:25:50 aenima dhclient: There is already a pid file
/var/run/dhclient.eth1.pid with pid 23920
Jul 29 13:25:50 aenima dhclient: killed old client process, removed PID file
Jul 29 13:25:50 aenima dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Jul 29 13:25:50 aenima avahi-daemon[5309]: Withdrawing address record for
192.168.1.103 on eth1.
Jul 29 13:25:50 aenima avahi-daemon[5309]: Leaving mDNS multicast group on interface
eth1.IPv4 with address 192.168.1.103.
Jul 29 13:25:50 aenima avahi-daemon[5309]: Interface eth1.IPv4 no longer relevant
for mDNS.
Jul 29 13:25:50 aenima dhcdbd:  dhclient 23920 down (9) but si_code == 0 and
releasing==0 !
Jul 29 13:25:50 aenima avahi-daemon[5309]: Withdrawing address record for
fe80::20c:f1ff:fe14:9337 on eth1.
Jul 29 13:25:51 aenima NetworkManager: <debug> [1217330751.051807]
nm_hal_device_removed(): Device removed (hal udi is
'/org/freedesktop/Hal/devices/net_00_11_43_5e_5b_06'). 
Jul 29 13:25:51 aenima kernel: [56199.975889] ACPI: PCI interrupt for device
0000:02:00.0 disabled
Jul 29 13:25:51 aenima NetworkManager: <debug> [1217330751.217835]
nm_hal_device_removed(): Device removed (hal udi is
'/org/freedesktop/Hal/devices/net_00_0c_f1_14_93_37'). 
Jul 29 13:25:51 aenima NetworkManager: <info>  Deactivating device eth1. 
Jul 29 13:25:51 aenima kernel: [56200.096363] ACPI: PCI interrupt for device
0000:02:03.0 disabled
Jul 29 13:25:51 aenima NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode():
error getting card mode on eth1: No such device 
Jul 29 13:25:53 aenima kernel: [21077.367238] PM: suspend-to-disk mode set to
'platform'
Jul 29 13:25:53 aenima kernel: [21077.367616] swsusp: Marking nosave pages:
000000000009f000 - 0000000000100000
Jul 29 13:25:53 aenima kernel: [21077.367623] swsusp: Basic memory bitmaps created
Jul 29 23:12:04 aenima syslogd 1.5.0#1ubuntu1: restart.
Jul 29 23:12:04 aenima kernel: Inspecting /boot/System.map-2.6.24-19-generic
Jul 29 23:12:04 aenima kernel: Loaded 27884 symbols from
/boot/System.map-2.6.24-19-generic.
Jul 29 23:12:04 aenima kernel: Symbols match kernel version 2.6.24.
Jul 29 23:12:04 aenima kernel: Loaded 30139 symbols from 91 modules.
Jul 29 23:12:04 aenima kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 29 23:12:04 aenima kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 29 23:12:04 aenima kernel: [    0.000000] Linux version 2.6.24-19-generic
(buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11
23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Jul 29 23:12:04 aenima kernel: [    0.000000] BIOS-provided physical RAM map:
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 0000000000000000 -
000000000009f000 (usable)
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 000000000009f000 -
00000000000a0000 (reserved)
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 0000000000100000 -
000000007ffae000 (usable)
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 000000007ffae000 -
0000000080000000 (reserved)
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 00000000feda0000 -
00000000fee00000 (reserved)
Jul 29 23:12:04 aenima kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 -
0000000100000000 (reserved)
Jul 29 23:12:04 aenima kernel: [    0.000000] 1151MB HIGHMEM available.
Jul 29 23:12:04 aenima kernel: [    0.000000] 896MB LOWMEM available.
Jul 29 23:12:04 aenima kernel: [    0.000000] Entering add_active_range(0, 0,
524206) 0 entries of 256 used
Jul 29 23:12:04 aenima kernel: [    0.000000] Zone PFN ranges:
Jul 29 23:12:04 aenima kernel: [    0.000000]   DMA             0 ->     4096
Jul 29 23:12:04 aenima kernel: [    0.000000]   Normal       4096 ->   229376
Jul 29 23:12:04 aenima kernel: [    0.000000]   HighMem    229376 ->   524206
Jul 29 23:12:04 aenima kernel: [    0.000000] Movable zone start PFN for each node
Jul 29 23:12:04 aenima kernel: [    0.000000] early_node_map[1] active PFN ranges
Jul 29 23:12:04 aenima kernel: [    0.000000]     0:        0 ->   524206
Jul 29 23:12:04 aenima kernel: [    0.000000] On node 0 totalpages: 524206
Jul 29 23:12:04 aenima kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 29 23:12:04 aenima kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 29 23:12:04 aenima kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Jul 29 23:12:04 aenima kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Jul 29 23:12:04 aenima kernel: [    0.000000]   Normal zone: 223520 pages, LIFO
batch:31
Jul 29 23:12:04 aenima kernel: [    0.000000]   HighMem zone: 2303 pages used for
memmap
Jul 29 23:12:04 aenima kernel: [    0.000000]   HighMem zone: 292527 pages, LIFO
batch:31
Jul 29 23:12:04 aenima kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jul 29 23:12:04 aenima kernel: [    0.000000] DMI 2.3 present.
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FDF00
checksum 0
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: RSDT 7FFF0000, 002C (r1 DELL   
CPi R   27D5011C ASL        61)
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: FACP 7FFF0400, 0074 (r1 DELL   
CPi R   27D5011C ASL        61)
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: DSDT 7FFF0C00, 2E30 (r1 INT430
SYSFexxx     1001 MSFT  100000E)
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: FACS 7FFFF800, 0040
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: ASF! 7FFF0800, 005B (r16 DELL   
CPi R   27D5011C ASL        61)
Jul 29 23:12:04 aenima kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jul 29 23:12:04 aenima kernel: [    0.000000] Allocating PCI resources starting at
88000000 (gap: 80000000:7eda0000)
Jul 29 23:12:04 aenima kernel: [    0.000000] swsusp: Registered nosave memory
region: 000000000009f000 - 00000000000a0000
Jul 29 23:12:04 aenima kernel: [    0.000000] swsusp: Registered nosave memory
region: 00000000000a0000 - 0000000000100000
Jul 29 23:12:04 aenima kernel: [    0.000000] Built 1 zonelists in Zone order,
mobility grouping on.  Total pages: 520111
Jul 29 23:12:04 aenima kernel: [    0.000000] Kernel command line:
root=UUID=05899d4d-d843-4389-ba4d-aade5e047bf2 ro quiet splash
Jul 29 23:12:04 aenima kernel: [    0.000000] Local APIC disabled by BIOS -- you can
enable it with "lapic"
Jul 29 23:12:04 aenima kernel: [    0.000000] mapped APIC to ffffb000 (02014000)
Jul 29 23:12:04 aenima kernel: [    0.000000] Enabling fast FPU save and restore...
done.
Jul 29 23:12:04 aenima kernel: [    0.000000] Enabling unmasked SIMD FPU exception
support... done.
Jul 29 23:12:04 aenima kernel: [    0.000000] Initializing CPU#0
Jul 29 23:12:04 aenima kernel: [    0.000000] PID hash table entries: 4096 (order:
12, 16384 bytes)
Jul 29 23:12:04 aenima kernel: [    0.000000] Detected 1594.883 MHz processor.
Jul 29 23:12:04 aenima kernel: [    8.100440] Console: colour VGA+ 80x25
Jul 29 23:12:04 aenima kernel: [    8.100445] console [tty0] enabled
Jul 29 23:12:04 aenima kernel: [    8.101074] Dentry cache hash table entries:
131072 (order: 7, 524288 bytes)
Jul 29 23:12:04 aenima kernel: [    8.101732] Inode-cache hash table entries: 65536
(order: 6, 262144 bytes)
Jul 29 23:12:04 aenima kernel: [    8.241890] Memory: 2066560k/2096824k available
(2177k kernel code, 28984k reserved, 1006k data, 368k init, 1179320k highmem)
Jul 29 23:12:04 aenima kernel: [    8.241901] virtual kernel memory layout:
Jul 29 23:12:04 aenima kernel: [    8.241902]     fixmap  : 0xfff4b000 - 0xfffff000 
 ( 720 kB)
Jul 29 23:12:04 aenima kernel: [    8.241903]     pkmap   : 0xff800000 - 0xffc00000 
 (4096 kB)
Jul 29 23:12:04 aenima kernel: [    8.241905]     vmalloc : 0xf8800000 - 0xff7fe000 
 ( 111 MB)
Jul 29 23:12:04 aenima kernel: [    8.241906]     lowmem  : 0xc0000000 - 0xf8000000 
 ( 896 MB)
Jul 29 23:12:04 aenima kernel: [    8.241907]       .init : 0xc0421000 - 0xc047d000 
 ( 368 kB)
Jul 29 23:12:04 aenima kernel: [    8.241909]       .data : 0xc0320474 - 0xc041bdc4 
 (1006 kB)
Jul 29 23:12:04 aenima kernel: [    8.241910]       .text : 0xc0100000 - 0xc0320474 
 (2177 kB)
Jul 29 23:12:04 aenima kernel: [    8.241914] Checking if this processor honours the
WP bit even in supervisor mode... Ok.
Jul 29 23:12:04 aenima kernel: [    8.241979] SLUB: Genslabs=11, HWalign=64,
Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jul 29 23:12:04 aenima kernel: [    8.322000] Calibrating delay using timer specific
routine.. 3192.09 BogoMIPS (lpj=6384188)
Jul 29 23:12:04 aenima kernel: [    8.322041] Security Framework initialized
Jul 29 23:12:04 aenima kernel: [    8.322053] SELinux:  Disabled at boot.
Jul 29 23:12:04 aenima kernel: [    8.322075] AppArmor: AppArmor initialized
Jul 29 23:12:04 aenima kernel: [    8.322080] Failure registering capabilities with
primary security module.
Jul 29 23:12:04 aenima kernel: [    8.322091] Mount-cache hash table entries: 512
Jul 29 23:12:04 aenima kernel: [    8.322270] Initializing cgroup subsys ns
Jul 29 23:12:04 aenima kernel: [    8.322279] Initializing cgroup subsys cpuacct
Jul 29 23:12:04 aenima kernel: [    8.322293] CPU: After generic identify, caps:
a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
Jul 29 23:12:04 aenima kernel: [    8.322307] CPU: L1 I cache: 32K, L1 D cache: 32K
Jul 29 23:12:04 aenima kernel: [    8.322310] CPU: L2 cache: 1024K
Jul 29 23:12:04 aenima kernel: [    8.322314] CPU: After all inits, caps: a7e9f9bf
00000000 00000000 00002040 00000180 00000000 00000000 00000000
Jul 29 23:12:04 aenima kernel: [    8.322326] Compat vDSO mapped to ffffe000.
Jul 29 23:12:04 aenima kernel: [    8.322343] Checking 'hlt' instruction... OK.
Jul 29 23:12:04 aenima kernel: [    8.338439] SMP alternatives: switching to UP code
Jul 29 23:12:04 aenima kernel: [    8.340555] Freeing SMP alternatives: 11k freed
Jul 29 23:12:04 aenima kernel: [    8.340691] Early unpacking initramfs... done
Jul 29 23:12:04 aenima kernel: [    8.751395] ACPI: Core revision 20070126
Jul 29 23:12:04 aenima kernel: [    8.751460] ACPI: Looking for DSDT in initramfs...
error, file /DSDT.aml not found.
Jul 29 23:12:04 aenima kernel: [    8.752931] ACPI: setting ELCR to 0200 (from 0800)
Jul 29 23:12:04 aenima kernel: [    8.755363] CPU0: Intel(R) Pentium(R) M processor
1600MHz stepping 05
Jul 29 23:12:04 aenima kernel: [    8.755369] SMP motherboard not detected.
Jul 29 23:12:04 aenima kernel: [    8.755372] Local APIC not detected. Using dummy
APIC emulation.
Jul 29 23:12:04 aenima kernel: [    8.755420] Brought up 1 CPUs
Jul 29 23:12:04 aenima kernel: [    8.755440] CPU0 attaching sched-domain:
Jul 29 23:12:04 aenima kernel: [    8.755443]  domain 0: span 01
Jul 29 23:12:04 aenima kernel: [    8.755445]   groups: 01
Jul 29 23:12:04 aenima kernel: [    8.755633] net_namespace: 64 bytes
Jul 29 23:12:04 aenima kernel: [    8.755646] Booting paravirtualized kernel on bare
hardware
Jul 29 23:12:04 aenima kernel: [    8.756276] Time: 23:09:26  Date: 07/29/08
Jul 29 23:12:04 aenima kernel: [    8.756304] NET: Registered protocol family 16
Jul 29 23:12:04 aenima kernel: [    8.756515] EISA bus registered
Jul 29 23:12:04 aenima kernel: [    8.756527] ACPI: bus type pci registered
Jul 29 23:12:04 aenima kernel: [    8.790363] PCI: PCI BIOS revision 2.10 entry at
0xfc96e, last bus=2
Jul 29 23:12:04 aenima kernel: [    8.790365] PCI: Using configuration type 1
Jul 29 23:12:04 aenima kernel: [    8.790389] Setting up standard PCI resources
Jul 29 23:12:04 aenima kernel: [    8.792590] ACPI: EC: Look up EC in DSDT
Jul 29 23:12:04 aenima kernel: [    8.798655] ACPI: Interpreter enabled
Jul 29 23:12:04 aenima kernel: [    8.798659] ACPI: (supports S0 S1 S3 S4 S5)
Jul 29 23:12:04 aenima kernel: [    8.798675] ACPI: Using PIC for interrupt routing
Jul 29 23:12:04 aenima kernel: [    8.810631] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 29 23:12:04 aenima kernel: [    8.811018] PCI quirk: region 0800-087f claimed by
ICH4 ACPI/GPIO/TCO
Jul 29 23:12:04 aenima kernel: [    8.811023] PCI quirk: region 0880-08bf claimed by
ICH4 GPIO
Jul 29 23:12:04 aenima kernel: [    8.811601] PCI: Transparent bridge - 0000:00:1e.0
Jul 29 23:12:04 aenima kernel: [    8.811701] ACPI: PCI Interrupt Routing Table
[\_SB_.PCI0._PRT]
Jul 29 23:12:04 aenima kernel: [    8.812037] ACPI: PCI Interrupt Routing Table
[\_SB_.PCI0.AGP_._PRT]
Jul 29 23:12:04 aenima kernel: [    8.812118] ACPI: PCI Interrupt Routing Table
[\_SB_.PCI0.PCIE._PRT]
Jul 29 23:12:04 aenima kernel: [    8.829106] ACPI: PCI Interrupt Link [LNKA] (IRQs
9 10 *11)
Jul 29 23:12:04 aenima kernel: [    8.829209] ACPI: PCI Interrupt Link [LNKB] (IRQs
5 7) *11
Jul 29 23:12:04 aenima kernel: [    8.829310] ACPI: PCI Interrupt Link [LNKC] (IRQs
9 10 *11)
Jul 29 23:12:04 aenima kernel: [    8.829411] ACPI: PCI Interrupt Link [LNKD] (IRQs
5 7 9 10 *11)
Jul 29 23:12:04 aenima kernel: [    8.829498] ACPI: PCI Interrupt Link [LNKE] (IRQs
3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jul 29 23:12:04 aenima kernel: [    8.829603] ACPI: PCI Interrupt Link [LNKH] (IRQs
3 4 5 6 7 9 10 *11 12 14 15)
Jul 29 23:12:04 aenima kernel: [    8.829719] Linux Plug and Play Support v0.97 (c)
Adam Belay
Jul 29 23:12:04 aenima kernel: [    8.829751] pnp: PnP ACPI init
Jul 29 23:12:04 aenima kernel: [    8.829759] ACPI: bus type pnp registered
Jul 29 23:12:04 aenima kernel: [    8.854793] pnp: PnP ACPI: found 13 devices
Jul 29 23:12:04 aenima kernel: [    8.854796] ACPI: ACPI bus type pnp unregistered
Jul 29 23:12:04 aenima kernel: [    8.854801] PnPBIOS: Disabled by ACPI PNP
Jul 29 23:12:04 aenima kernel: [    8.855021] PCI: Using ACPI for IRQ routing
Jul 29 23:12:04 aenima kernel: [    8.855024] PCI: If a device doesn't work, try
"pci=routeirq".  If it helps, post a report
Jul 29 23:12:04 aenima kernel: [    8.877972] NET: Registered protocol family 8
Jul 29 23:12:04 aenima kernel: [    8.877974] NET: Registered protocol family 20
Jul 29 23:12:04 aenima kernel: [    8.878041] AppArmor: AppArmor Filesystem Enabled
Jul 29 23:12:04 aenima kernel: [    8.881963] Time: tsc clocksource has been installed.
Jul 29 23:12:04 aenima kernel: [    8.890000] system 00:00: iomem range 0x0-0x9fbff
could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890004] system 00:00: iomem range
0x9fc00-0x9ffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890007] system 00:00: iomem range
0xc0000-0xcffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890010] system 00:00: iomem range
0xe0000-0xfffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890014] system 00:00: iomem range
0x100000-0x7ffeffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890017] system 00:00: iomem range
0x7fff0000-0x7fffffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890020] system 00:00: iomem range
0xfeda0000-0xfedfffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890024] system 00:00: iomem range
0xffb00000-0xffbfffff could not be reserved
Jul 29 23:12:04 aenima kernel: [    8.890031] system 00:02: ioport range 0x4d0-0x4d1
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890034] system 00:02: ioport range 0x800-0x805
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890037] system 00:02: ioport range 0x808-0x80f
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890043] system 00:03: ioport range
0xf400-0xf4fe has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890047] system 00:03: ioport range 0x806-0x807
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890050] system 00:03: ioport range 0x810-0x85f
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890053] system 00:03: ioport range 0x860-0x87f
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890056] system 00:03: ioport range 0x880-0x8bf
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890058] system 00:03: ioport range 0x8c0-0x8df
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890062] system 00:03: ioport range 0x8e0-0x8ff
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.890069] system 00:08: ioport range 0x900-0x97f
has been reserved
Jul 29 23:12:04 aenima kernel: [    8.920492] PCI: Bridge: 0000:00:01.0
Jul 29 23:12:04 aenima kernel: [    8.920495]   IO window: c000-cfff
Jul 29 23:12:04 aenima kernel: [    8.920498]   MEM window: fc000000-fdffffff
Jul 29 23:12:04 aenima kernel: [    8.920502]   PREFETCH window: f0000000-f3ffffff
Jul 29 23:12:04 aenima kernel: [    8.920516] PCI: Bus 3, cardbus bridge: 0000:02:01.0
Jul 29 23:12:04 aenima kernel: [    8.920519]   IO window: 0000d000-0000d0ff
Jul 29 23:12:04 aenima kernel: [    8.920523]   IO window: 0000d400-0000d4ff
Jul 29 23:12:04 aenima kernel: [    8.920527]   PREFETCH window: 8c000000-8fffffff
Jul 29 23:12:04 aenima kernel: [    8.920531]   MEM window: 90000000-93ffffff
Jul 29 23:12:04 aenima kernel: [    8.920534] PCI: Bus 7, cardbus bridge: 0000:02:01.1
Jul 29 23:12:04 aenima kernel: [    8.920536]   IO window: 0000d800-0000d8ff
Jul 29 23:12:04 aenima kernel: [    8.920540]   IO window: 0000dc00-0000dcff
Jul 29 23:12:04 aenima kernel: [    8.920544]   PREFETCH window: 94000000-97ffffff
Jul 29 23:12:04 aenima kernel: [    8.920548]   MEM window: 98000000-9bffffff
Jul 29 23:12:04 aenima kernel: [    8.920552] PCI: Bridge: 0000:00:1e.0
Jul 29 23:12:04 aenima kernel: [    8.920555]   IO window: d000-efff
Jul 29 23:12:04 aenima kernel: [    8.920560]   MEM window: f6000000-fbffffff
Jul 29 23:12:04 aenima kernel: [    8.920563]   PREFETCH window: disabled.
Jul 29 23:12:04 aenima kernel: [    8.920578] PCI: Setting latency timer of device
0000:00:1e.0 to 64
Jul 29 23:12:04 aenima kernel: [    8.920593] PCI: Enabling device 0000:02:01.0
(0000 -> 0003)
Jul 29 23:12:04 aenima kernel: [    8.920745] ACPI: PCI Interrupt Link [LNKD]
enabled at IRQ 11
Jul 29 23:12:04 aenima kernel: [    8.920748] PCI: setting IRQ 11 as level-triggered
Jul 29 23:12:04 aenima kernel: [    8.920752] ACPI: PCI Interrupt 0000:02:01.0[A] ->
Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [    8.920769] ACPI: PCI Interrupt 0000:02:01.1[A] ->
Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [    8.920785] NET: Registered protocol family 2
Jul 29 23:12:04 aenima kernel: [    8.958040] IP route cache hash table entries:
32768 (order: 5, 131072 bytes)
Jul 29 23:12:04 aenima kernel: [    8.958350] TCP established hash table entries:
131072 (order: 8, 1048576 bytes)
Jul 29 23:12:04 aenima kernel: [    8.959707] TCP bind hash table entries: 65536
(order: 7, 524288 bytes)
Jul 29 23:12:04 aenima kernel: [    8.960690] TCP: Hash tables configured
(established 131072 bind 65536)
Jul 29 23:12:04 aenima kernel: [    8.960694] TCP reno registered
Jul 29 23:12:04 aenima kernel: [    8.970175] checking if image is initramfs... it is
Jul 29 23:12:04 aenima kernel: [    9.421947] Switched to high resolution mode on CPU 0
Jul 29 23:12:04 aenima kernel: [    9.768093] Freeing initrd memory: 7632k freed
Jul 29 23:12:04 aenima kernel: [    9.768696] audit: initializing netlink socket
(disabled)
Jul 29 23:12:04 aenima kernel: [    9.768715] audit(1217372966.528:1): initialized
Jul 29 23:12:04 aenima kernel: [    9.768944] highmem bounce pool size: 64 pages
Jul 29 23:12:04 aenima kernel: [    9.771179] VFS: Disk quotas dquot_6.5.1
Jul 29 23:12:04 aenima kernel: [    9.771273] Dquot-cache hash table entries: 1024
(order 0, 4096 bytes)
Jul 29 23:12:04 aenima kernel: [    9.771439] io scheduler noop registered
Jul 29 23:12:04 aenima kernel: [    9.771442] io scheduler anticipatory registered
Jul 29 23:12:04 aenima kernel: [    9.771445] io scheduler deadline registered
Jul 29 23:12:04 aenima kernel: [    9.771462] io scheduler cfq registered (default)
Jul 29 23:12:04 aenima kernel: [    9.771545] Boot video device is 0000:01:00.0
Jul 29 23:12:04 aenima kernel: [    9.771876] isapnp: Scanning for PnP cards...
Jul 29 23:12:04 aenima kernel: [   10.124754] isapnp: No Plug & Play device found
Jul 29 23:12:04 aenima kernel: [   10.158131] Real Time Clock Driver v1.12ac
Jul 29 23:12:04 aenima kernel: [   10.158253] Serial: 8250/16550 driver $Revision:
1.90 $ 4 ports, IRQ sharing enabled
Jul 29 23:12:04 aenima kernel: [   10.158374] serial8250: ttyS0 at I/O 0x3f8 (irq =
4) is a 16550A
Jul 29 23:12:04 aenima kernel: [   10.159090] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is
a 16550A
Jul 29 23:12:04 aenima kernel: [   10.159461] ACPI: PCI Interrupt Link [LNKB]
enabled at IRQ 5
Jul 29 23:12:04 aenima kernel: [   10.159465] PCI: setting IRQ 5 as level-triggered
Jul 29 23:12:04 aenima kernel: [   10.159469] ACPI: PCI Interrupt 0000:00:1f.6[B] ->
Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Jul 29 23:12:04 aenima kernel: [   10.159479] ACPI: PCI interrupt for device
0000:00:1f.6 disabled
Jul 29 23:12:04 aenima kernel: [   10.160157] RAMDISK driver initialized: 16 RAM
disks of 65536K size 1024 blocksize
Jul 29 23:12:04 aenima kernel: [   10.160232] input: Macintosh mouse button
emulation as /devices/virtual/input/input0
Jul 29 23:12:04 aenima kernel: [   10.160344] PNP: PS/2 Controller
[PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 29 23:12:04 aenima kernel: [   10.165235] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 29 23:12:04 aenima kernel: [   10.165241] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 29 23:12:04 aenima kernel: [   10.165959] mice: PS/2 mouse device common for all
mice
Jul 29 23:12:04 aenima kernel: [   10.166072] EISA: Probing bus 0 at eisa.0
Jul 29 23:12:04 aenima kernel: [   10.166097] EISA: Detected 0 cards.
Jul 29 23:12:04 aenima kernel: [   10.166101] cpuidle: using governor ladder
Jul 29 23:12:04 aenima kernel: [   10.166103] cpuidle: using governor menu
Jul 29 23:12:04 aenima kernel: [   10.166212] NET: Registered protocol family 1
Jul 29 23:12:04 aenima kernel: [   10.166244] Using IPI No-Shortcut mode
Jul 29 23:12:04 aenima kernel: [   10.166278] registered taskstats version 1
Jul 29 23:12:04 aenima kernel: [   10.166409]   Magic number: 0:244:202
Jul 29 23:12:04 aenima kernel: [   10.166447]   hash matches device ttyt0
Jul 29 23:12:04 aenima kernel: [   10.166561] BIOS EDD facility v0.16 2004-Jun-25, 0
devices found
Jul 29 23:12:04 aenima kernel: [   10.166564] EDD information not available.
Jul 29 23:12:04 aenima kernel: [   10.166811] Freeing unused kernel memory: 368k freed
Jul 29 23:12:04 aenima kernel: [   10.170343] input: AT Translated Set 2 keyboard as
/devices/platform/i8042/serio0/input/input1
Jul 29 23:12:04 aenima kernel: [   12.313641] fuse init (API version 7.9)
Jul 29 23:12:04 aenima kernel: [   12.357778] ACPI: CPU0 (power states: C1[C1]
C2[C2] C3[C3] C4[C3])
Jul 29 23:12:04 aenima kernel: [   12.357786] ACPI: Processor [CPU0] (supports 8
throttling states)
Jul 29 23:12:04 aenima kernel: [   12.361646] ACPI: Thermal Zone [THM] (27 C)
Jul 29 23:12:04 aenima kernel: [   13.145461] usbcore: registered new interface
driver usbfs
Jul 29 23:12:04 aenima kernel: [   13.145490] usbcore: registered new interface
driver hub
Jul 29 23:12:04 aenima kernel: [   13.170790] usbcore: registered new device driver usb
Jul 29 23:12:04 aenima kernel: [   13.252026] SCSI subsystem initialized
Jul 29 23:12:04 aenima kernel: [   13.265399] USB Universal Host Controller
Interface driver v3.0
Jul 29 23:12:04 aenima kernel: [   13.265673] ACPI: PCI Interrupt Link [LNKA]
enabled at IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.265676] ACPI: PCI Interrupt 0000:00:1d.0[A] ->
Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.265689] PCI: Setting latency timer of device
0000:00:1d.0 to 64
Jul 29 23:12:04 aenima kernel: [   13.265694] uhci_hcd 0000:00:1d.0: UHCI Host
Controller
Jul 29 23:12:04 aenima kernel: [   13.266111] uhci_hcd 0000:00:1d.0: new USB bus
registered, assigned bus number 1
Jul 29 23:12:04 aenima kernel: [   13.266137] uhci_hcd 0000:00:1d.0: irq 11, io base
0x0000bf80
Jul 29 23:12:04 aenima kernel: [   13.266296] usb usb1: configuration #1 chosen from
1 choice
Jul 29 23:12:04 aenima kernel: [   13.266322] hub 1-0:1.0: USB hub found
Jul 29 23:12:04 aenima kernel: [   13.266328] hub 1-0:1.0: 2 ports detected
Jul 29 23:12:04 aenima kernel: [   13.369468] ACPI: PCI Interrupt 0000:00:1d.1[B] ->
Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.369484] PCI: Setting latency timer of device
0000:00:1d.1 to 64
Jul 29 23:12:04 aenima kernel: [   13.369489] uhci_hcd 0000:00:1d.1: UHCI Host
Controller
Jul 29 23:12:04 aenima kernel: [   13.369514] uhci_hcd 0000:00:1d.1: new USB bus
registered, assigned bus number 2
Jul 29 23:12:04 aenima kernel: [   13.369539] uhci_hcd 0000:00:1d.1: irq 11, io base
0x0000bf40
Jul 29 23:12:04 aenima kernel: [   13.369683] usb usb2: configuration #1 chosen from
1 choice
Jul 29 23:12:04 aenima kernel: [   13.369710] hub 2-0:1.0: USB hub found
Jul 29 23:12:04 aenima kernel: [   13.369716] hub 2-0:1.0: 2 ports detected
Jul 29 23:12:04 aenima kernel: [   13.397289] libata version 3.00 loaded.
Jul 29 23:12:04 aenima kernel: [   13.473651] ACPI: PCI Interrupt Link [LNKC]
enabled at IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.473657] ACPI: PCI Interrupt 0000:00:1d.2[C] ->
Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.473670] PCI: Setting latency timer of device
0000:00:1d.2 to 64
Jul 29 23:12:04 aenima kernel: [   13.473675] uhci_hcd 0000:00:1d.2: UHCI Host
Controller
Jul 29 23:12:04 aenima kernel: [   13.473702] uhci_hcd 0000:00:1d.2: new USB bus
registered, assigned bus number 3
Jul 29 23:12:04 aenima kernel: [   13.473727] uhci_hcd 0000:00:1d.2: irq 11, io base
0x0000bf20
Jul 29 23:12:04 aenima kernel: [   13.473858] usb usb3: configuration #1 chosen from
1 choice
Jul 29 23:12:04 aenima kernel: [   13.473885] hub 3-0:1.0: USB hub found
Jul 29 23:12:04 aenima kernel: [   13.473891] hub 3-0:1.0: 2 ports detected
Jul 29 23:12:04 aenima kernel: [   13.577540] tg3.c:v3.86 (November 9, 2007)
Jul 29 23:12:04 aenima kernel: [   13.577569] ACPI: PCI Interrupt 0000:02:00.0[A] ->
Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.577836] ACPI: PCI Interrupt Link [LNKH]
enabled at IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.577839] ACPI: PCI Interrupt 0000:00:1d.7[D] ->
Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.577848] PCI: Setting latency timer of device
0000:00:1d.7 to 64
Jul 29 23:12:04 aenima kernel: [   13.577852] ehci_hcd 0000:00:1d.7: EHCI Host
Controller
Jul 29 23:12:04 aenima kernel: [   13.577882] ehci_hcd 0000:00:1d.7: new USB bus
registered, assigned bus number 4
Jul 29 23:12:04 aenima kernel: [   13.581800] ehci_hcd 0000:00:1d.7: debug port 1
Jul 29 23:12:04 aenima kernel: [   13.581807] PCI: cache line size of 32 is not
supported by device 0000:00:1d.7
Jul 29 23:12:04 aenima kernel: [   13.581814] ehci_hcd 0000:00:1d.7: irq 11, io mem
0xf4fffc00
Jul 29 23:12:04 aenima kernel: [   13.661409] ehci_hcd 0000:00:1d.7: USB 2.0
started, EHCI 1.00, driver 10 Dec 2004
Jul 29 23:12:04 aenima kernel: [   13.661549] usb usb4: configuration #1 chosen from
1 choice
Jul 29 23:12:04 aenima kernel: [   13.661577] hub 4-0:1.0: USB hub found
Jul 29 23:12:04 aenima kernel: [   13.661584] hub 4-0:1.0: 6 ports detected
Jul 29 23:12:04 aenima kernel: [   13.673485] eth0: Tigon3 [partno(BCM95705A50) rev
3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:11:43:5e:5b:06
Jul 29 23:12:04 aenima kernel: [   13.673494] eth0: RXcsums[1] LinkChgREG[0]
MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Jul 29 23:12:04 aenima kernel: [   13.673497] eth0: dma_rwctrl[763f0000]
dma_mask[64-bit]
Jul 29 23:12:04 aenima kernel: [   13.765539] ACPI: PCI Interrupt 0000:02:01.2[A] ->
Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.815328] ohci1394: fw-host0: OHCI-1394 1.1
(PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jul 29 23:12:04 aenima kernel: [   13.820209] PCI: Enabling device 0000:00:1f.1
(0005 -> 0007)
Jul 29 23:12:04 aenima kernel: [   13.820220] ACPI: PCI Interrupt 0000:00:1f.1[A] ->
Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.820264] PCI: Setting latency timer of device
0000:00:1f.1 to 64
Jul 29 23:12:04 aenima kernel: [   13.820278] ACPI: PCI interrupt for device
0000:00:1f.1 disabled
Jul 29 23:12:04 aenima kernel: [   13.829877] ata_piix 0000:00:1f.1: version 2.12
Jul 29 23:12:04 aenima kernel: [   13.829897] ACPI: PCI Interrupt 0000:00:1f.1[A] ->
Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 29 23:12:04 aenima kernel: [   13.829939] PCI: Setting latency timer of device
0000:00:1f.1 to 64
Jul 29 23:12:04 aenima kernel: [   13.830794] scsi0 : ata_piix
Jul 29 23:12:04 aenima kernel: [   13.831343] scsi1 : ata_piix
Jul 29 23:12:04 aenima kernel: [   13.832451] ata1: PATA max UDMA/100 cmd 0x1f0 ctl
0x3f6 bmdma 0xbfa0 irq 14
Jul 29 23:12:04 aenima kernel: [   13.832454] ata2: PATA max UDMA/100 cmd 0x170 ctl
0x376 bmdma 0xbfa8 irq 15
Jul 29 23:12:04 aenima kernel: [   13.993822] ata1.00: ATA-6: HTS548040M9AT00,
MG2OA53A, max UDMA/100
Jul 29 23:12:04 aenima kernel: [   13.993828] ata1.00: 78140160 sectors, multi 8:
LBA48 
Jul 29 23:12:04 aenima kernel: [   14.009764] ata1.00: configured for UDMA/100
Jul 29 23:12:04 aenima kernel: [   14.329519] ata2.00: ATAPI: QSI CD-RW/DVD-ROM
SBW-242, UD30, max UDMA/33
Jul 29 23:12:04 aenima kernel: [   14.501427] ata2.00: configured for UDMA/33
Jul 29 23:12:04 aenima kernel: [   14.501563] scsi 0:0:0:0: Direct-Access     ATA   
  HTS548040M9AT00  MG2O PQ: 0 ANSI: 5
Jul 29 23:12:04 aenima kernel: [   14.502372] scsi 1:0:0:0: CD-ROM            QSI   
  CDRW/DVD SBW-242 UD30 PQ: 0 ANSI: 5
Jul 29 23:12:04 aenima kernel: [   14.514766] Driver 'sd' needs updating - please
use bus_type methods
Jul 29 23:12:04 aenima kernel: [   14.514863] sd 0:0:0:0: [sda] 78140160 512-byte
hardware sectors (40008 MB)
Jul 29 23:12:04 aenima kernel: [   14.514877] sd 0:0:0:0: [sda] Write Protect is off
Jul 29 23:12:04 aenima kernel: [   14.514880] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 29 23:12:04 aenima kernel: [   14.514898] sd 0:0:0:0: [sda] Write cache:
enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 23:12:04 aenima kernel: [   14.514947] sd 0:0:0:0: [sda] 78140160 512-byte
hardware sectors (40008 MB)
Jul 29 23:12:04 aenima kernel: [   14.514958] sd 0:0:0:0: [sda] Write Protect is off
Jul 29 23:12:04 aenima kernel: [   14.514960] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 29 23:12:04 aenima kernel: [   14.514976] sd 0:0:0:0: [sda] Write cache:
enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 23:12:04 aenima kernel: [   14.514980]  sda:<4>Driver 'sr' needs updating -
please use bus_type methods
Jul 29 23:12:04 aenima kernel: [   14.544915]  sda1 sda2 sda3 < sda5 sda6 > sda4
Jul 29 23:12:04 aenima kernel: [   14.597051] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 29 23:12:04 aenima kernel: [   14.606973] sd 0:0:0:0: Attached scsi generic sg0
type 0
Jul 29 23:12:04 aenima kernel: [   14.606996] sr 1:0:0:0: Attached scsi generic sg1
type 5
Jul 29 23:12:04 aenima kernel: [   14.609299] sr0: scsi3-mmc drive: 4x/24x writer
cd/rw xa/form2 cdda tray
Jul 29 23:12:04 aenima kernel: [   14.609305] Uniform CD-ROM driver Revision: 3.20
Jul 29 23:12:04 aenima kernel: [   14.609365] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 29 23:12:04 aenima kernel: [   15.089232] ieee1394: Host added:
ID:BUS[0-00:1023]  GUID[4a4fc0000d010430]
Jul 29 23:12:04 aenima kernel: [   15.417054] Clocksource tsc unstable (delta =
-882878661 ns)
Jul 29 23:12:04 aenima kernel: [   15.437050] Time: acpi_pm clocksource has been
installed.
Jul 29 23:12:04 aenima kernel: [   19.595656] swsusp: Marking nosave pages:
000000000009f000 - 0000000000100000
Jul 29 23:12:04 aenima kernel: [   19.595704] swsusp: Basic memory bitmaps created
Jul 29 23:12:04 aenima kernel: [   19.613327] swsusp: Basic memory bitmaps freed
Jul 29 23:12:04 aenima kernel: [   19.632521] EXT3-fs: INFO: recovery required on
readonly filesystem.
Jul 29 23:12:04 aenima kernel: [   19.632526] EXT3-fs: write access will be enabled
during recovery.
Jul 29 23:12:04 aenima kernel: [   24.528631] kjournald starting.  Commit interval 5
seconds
Jul 29 23:12:04 aenima kernel: [   24.528654] EXT3-fs: sda4: orphan cleanup on
readonly fs
Jul 29 23:12:04 aenima kernel: [   24.528661] ext3_orphan_cleanup: deleting
unreferenced inode 416031
Jul 29 23:12:04 aenima kernel: [   24.528689] EXT3-fs: sda4: 1 orphan inode deleted
Jul 29 23:12:04 aenima kernel: [   24.528691] EXT3-fs: recovery complete.
Jul 29 23:12:04 aenima kernel: [   24.547200] EXT3-fs: mounted filesystem with
ordered data mode.
Jul 29 23:12:04 aenima kernel: [   39.161816] input: PC Speaker as
/devices/platform/pcspkr/input/input2
Jul 29 23:12:04 aenima kernel: [   39.615886] pci_hotplug: PCI Hot Plug PCI Core
version: 0.5
Jul 29 23:12:04 aenima kernel: [   39.651405] input: PS/2 Mouse as
/devices/virtual/input/input3
Jul 29 23:12:04 aenima kernel: [   39.675307] shpchp: Standard Hot Plug PCI
Controller Driver version: 0.4
Jul 29 23:12:04 aenima kernel: [   39.697066] input: AlpsPS/2 ALPS GlidePoint as
/devices/platform/i8042/serio1/input/input4
Jul 29 23:12:04 aenima kernel: [   39.723337] parport_pc 00:0c: reported by Plug and
Play ACPI
Jul 29 23:12:04 aenima kernel: [   39.723388] parport0: PC-style at 0x378 (0x778),
irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 29 23:12:04 aenima kernel: [   39.786976] intel_rng: FWH not detected
Jul 29 23:12:04 aenima kernel: [   39.824378] Linux agpgart interface v0.102
Jul 29 23:12:04 aenima kernel: [   39.987025] dcdbas dcdbas: Dell Systems Management
Base Driver (version 5.6.0-3.2)
Jul 29 23:12:04 aenima kernel: [   40.067020] agpgart: Detected an Intel 855PM Chipset.
Jul 29 23:12:04 aenima kernel: [   40.075262] agpgart: AGP aperture is 128M @
0xe8000000
Jul 29 23:12:04 aenima kernel: [   40.227567] ACPI: AC Adapter [AC] (on-line)

```

---

### Post by prshah on 2008-07-30
> **jazzgossen said:**
> For a while now, I haven't been able to resume from hibernation, and even at clean boots, there is no graphical progress bar.


Take a look at [this post for a similar problem]("http://ubuntuforums.org/showpost.php?p=5189957&postcount=3") for solutions/suggestions. You can also review the entire thread if you run into problems.

---

### Post by jazzgossen on 2008-07-31
Thanks! However, my swap partition does get automatically mounted. Although I don't use its UUID. I have /dev/sda6 in fstab. Running "swapon -s" after boot also outputs "/dev/sda6". My "/etc/initramfs-tools/conf.d/resume" file contains "RESUME=/dev/sda6", and I have run "update-initramfs -u". Still no go.

And the kernel lines in menu.lst all have "quiet splash".

Edit: I changed the /dev/sda6 in initramfs-tools/conf.d/resume to the partition's UUID and ran update-initramfs. Still no change.

Edit again: I just tried uswsusp, and that worked. So for the time being, I guess I'll use that instead.

---


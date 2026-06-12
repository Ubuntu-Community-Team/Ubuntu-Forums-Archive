---
title: "Unable to Mount Audio Disc"
date: 2009-01-15
forum: Hardware
---

### Post by fwallace99 on 2009-01-15
Hi all, I have a DISTURBING problem that does not appear to be covered in the archives.

I randomly get a message "Unable to Mount Audio Disc; no files in media" at certain times. I don't have anything in the CD/DVD drive at this point.

My computer gets VERY slow and sometimes and sometimes not I will get a "Blank Disc" icon on the desktop. 

Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=91db3d50-8a4e-4595-b9cb-28b377c5fbee /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=a994f7a7-1db0-40e5-97fb-4cb0bccac63d none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto 0       0


Note that I've commented out the original one to try and prevent the random "Blank Disk" icon of a blank CD. It happens less often than before.

Whenever I get the "Unable to Mount Audio Disc" message I cannot eject the CD ROM/DVD ROM drive, and K3B no longer recognizes the drive. If I reboot it (K3B) does recognize the drive, and I can use the eject command to eject the CD/DVD drive.

What the heck is going on here? It does not seem to be related to /etc/fstab, which was done automagically by a clean install of Hardy Heron. 

Is there a known package that screws up your CD/DVD drive? My computer is at a crawl when this happens, and I have a full 2 Gigs of RAM, etc. It's speedy otherwise.

Thanks in advance for any help.

FYI I got this problem after about a year with Feisty Fawn which is why I upgraded via clean new install to Hardy Heron. I'm sure it's some package or something.

Could it be PulseAudio? I know that a lot of folks seem to have problems with Pulse, it's rep is that it slows machines down considerably.

---

### Post by 2hot6ft2 on 2009-01-15
I doubt that PulseAudio has anything to do with it. Since it did it with your previous OS version I would think it was a drive issue. Perhaps a loose connection.

---

### Post by fwallace99 on 2009-01-15
Not a loose connection. In the Feisty Fawn version, launching K3B would make the Blank Disc Icon go away.

It works fine with Puppy Linux. It's a Toshiba Laptop, Satellite A135-S2276.

I assume it's something having to do with Gnome, or communicating with Gnome, that locks up the DVD/CD drive.

If it was a loose connection, why would rebooting work? Moreover, why would I get:

A. SLOWWWWWWW Computer, with REAAALLLYYY big lag on keyboard input.
B. intermittent "Blank Disk" icon on the desktop, which I cannot eject via command line or through Gnome.
C. The "Unable to Mount Audio Disc" message ... when I don't DO anything (but work in Open Office or Firefox)?

ETA: here is the message I get with the random "Cannot Mount Audio Disc" message box:

Unable to Mount Audio Disc

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

I DO NOT HAVE ANYTHING IN THE DRIVE.

Is this something to do with HAL?

---

### Post by fwallace99 on 2009-01-16
Bumped to push up the queue:

I run dmesg and get a bunch of these:

[  603.031687] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.031695] ide: failed opcode was: unknown
[  603.031699] hdc: drive not ready for command


my CD/DVD ROM drive is /dev/hdc .

---

### Post by fwallace99 on 2009-01-17
There is a BUG in Ubuntu:

[https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

So adding to /etc/modules:

```
libata
ata_piix
piix
```

Will fix people having problems accessing the DVD/CD drive. 

Once I did this, I got the following for my dmesg:

```
42 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e80000 (usable)
[    0.000000]  BIOS-e820: 0000000077e80000 - 0000000077e90000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e90000 - 0000000077f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000078000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1022MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6a50
[    0.000000] Entering add_active_range(0, 0, 491136) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491136
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491136
[    0.000000] On node 0 totalpages: 491136
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2045 pages used for memmap
[    0.000000]   HighMem zone: 259715 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F69C0 checksum 0
[    0.000000] ACPI: RSDP 000F69C0, 0014 (r0 TOSCPL)
[    0.000000] ACPI: RSDT 77E87EA6, 0040 (r1 TOSCPL TOSCPL00  6040000  LTP        0)
[    0.000000] ACPI: FACP 77E8FD7C, 0074 (r1 TOSCPL SB450     6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 77E8A273, 5B09 (r1 TOSCPL    SB450  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 77E90FC0, 0040
[    0.000000] ACPI: SLIC 77E8FDF0, 0176 (r1 TOSCPL TOSCPL00  6040000 LOHR        0)
[    0.000000] ACPI: APIC 77E8FF66, 005E (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 77E8FFC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SSDT 77E89391, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 77E892EB, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 77E87EE6, 1405 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 78000000:68000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487299
[    0.000000] Kernel command line: root=UUID=91db3d50-8a4e-4595-b9cb-28b377c5fbee ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.152 MHz processor.
[   15.772767] Console: colour VGA+ 80x25
[   15.772773] console [tty0] enabled
[   15.773825] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.774578] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.906798] Memory: 1935652k/1964544k available (2178k kernel code, 27676k reserved, 1005k data, 368k init, 1047040k highmem)
[   15.906808] virtual kernel memory layout:
[   15.906809]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.906811]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.906812]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.906814]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.906815]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   15.906816]       .data : 0xc0320918 - 0xc041bdc4   (1005 kB)
[   15.906818]       .text : 0xc0100000 - 0xc0320918   (2178 kB)
[   15.906822] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.906900] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.986819] Calibrating delay using timer specific routine.. 3204.09 BogoMIPS (lpj=6408180)
[   15.986872] Security Framework initialized
[   15.986888] SELinux:  Disabled at boot.
[   15.986914] AppArmor: AppArmor initialized
[   15.986919] Failure registering capabilities with primary security module.
[   15.986931] Mount-cache hash table entries: 512
[   15.987137] Initializing cgroup subsys ns
[   15.987146] Initializing cgroup subsys cpuacct
[   15.987164] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[   15.987173] monitor/mwait feature present.
[   15.987175] using mwait in idle threads.
[   15.987180] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.987183] CPU: L2 cache: 1024K
[   15.987187] CPU: Physical Processor ID: 0
[   15.987189] CPU: Processor Core ID: 0
[   15.987192] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
[   15.987207] Compat vDSO mapped to ffffe000.
[   15.987227] Checking 'hlt' instruction... OK.
[   16.003264] SMP alternatives: switching to UP code
[   16.005380] Early unpacking initramfs... done
[   16.392391] ACPI: Core revision 20070126
[   16.392469] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.819040] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   16.819063] SMP alternatives: switching to SMP code
[   16.819912] Booting processor 1/1 eip 3000
[   16.830167] Initializing CPU#1
[   16.909460] Calibrating delay using timer specific routine.. 3200.41 BogoMIPS (lpj=6400838)
[   16.909469] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000 00000000
[   16.909475] monitor/mwait feature present.
[   16.909480] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.909482] CPU: L2 cache: 1024K
[   16.909484] CPU: Physical Processor ID: 0
[   16.909486] CPU: Processor Core ID: 1
[   16.909488] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00042940 0000c189 00000000 00000000 00000000
[   16.910079] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   16.910109] Total of 2 processors activated (6404.50 BogoMIPS).
[   16.910292] ENABLING IO-APIC IRQs
[   16.910498] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   17.057399] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.077391] Brought up 2 CPUs
[   17.077421] CPU0 attaching sched-domain:
[   17.077424]  domain 0: span 03
[   17.077426]   groups: 01 02
[   17.077430] CPU1 attaching sched-domain:
[   17.077432]  domain 0: span 03
[   17.077433]   groups: 02 01
[   17.077766] net_namespace: 64 bytes
[   17.077776] Booting paravirtualized kernel on bare hardware
[   17.078296] Time: 22:45:33  Date: 01/17/09
[   17.078332] NET: Registered protocol family 16
[   17.078598] EISA bus registered
[   17.078604] ACPI: bus type pci registered
[   17.096087] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[   17.096090] PCI: Using configuration type 1
[   17.096100] Setting up standard PCI resources
[   17.101018] ACPI: EC: Look up EC in DSDT
[   17.101864] ACPI Error (evregion-0316): No handler for Region [ERAM] (f7c4a4d8) [EmbeddedControl] [20070126]
[   17.101871] ACPI Error (exfldio-0289): Region EmbeddedControl(3) has no handler [20070126]
[   17.101877] ACPI Exception (dswexec-0462): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20070126]
[   17.101884] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.HTEV] (Node f7c45e58), AE_NOT_EXIST
[   17.101922] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f7c4bbe8), AE_NOT_EXIST
[   17.102988] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   17.113308] ACPI: Interpreter enabled
[   17.113314] ACPI: (supports S0 S3 S4 S5)
[   17.113344] ACPI: Using IOAPIC for interrupt routing
[   17.114890] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.174952] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[   17.174959] ACPI: EC: driver started in interrupt mode
[   17.175064] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.177020] PCI: Transparent bridge - 0000:00:14.4
[   17.177171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.177697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   17.178022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   17.178350] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   17.183262] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   17.183547] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   17.183827] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   17.184106] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   17.184384] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   17.184660] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   17.184939] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   17.185228] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   17.185508] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   17.185800] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.185867] pnp: PnP ACPI init
[   17.185882] ACPI: bus type pnp registered
[   17.209366] pnp: PnP ACPI: found 10 devices
[   17.209372] ACPI: ACPI bus type pnp unregistered
[   17.209379] PnPBIOS: Disabled by ACPI PNP
[   17.209900] PCI: Using ACPI for IRQ routing
[   17.209906] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.277110] NET: Registered protocol family 8
[   17.277114] NET: Registered protocol family 20
[   17.277242] AppArmor: AppArmor Filesystem Enabled
[   17.280943] Time: tsc clocksource has been installed.
[   17.297145] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   17.297170] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   17.297177] system 00:08: ioport range 0x220-0x22f has been reserved
[   17.297183] system 00:08: ioport range 0x40b-0x40b has been reserved
[   17.297190] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.297196] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   17.297202] system 00:08: ioport range 0x530-0x537 has been reserved
[   17.297208] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   17.297215] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   17.297221] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   17.297227] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   17.297233] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   17.297239] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   17.297246] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   17.297252] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   17.297258] system 00:08: ioport range 0x8000-0x805f has been reserved
[   17.297265] system 00:08: ioport range 0x8210-0x821f has been reserved
[   17.297271] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   17.297277] system 00:08: ioport range 0x280-0x293 has been reserved
[   17.297283] system 00:08: ioport range 0x87f-0x87f has been reserved
[   17.297290] system 00:08: ioport range 0xfd60-0xfddf has been reserved
[   17.297304] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   17.297311] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   17.297318] system 00:09: iomem range 0x0-0xfff could not be reserved
[   17.328196] PCI: Bridge: 0000:00:01.0
[   17.328202]   IO window: 9000-9fff
[   17.328210]   MEM window: c0000000-c00fffff
[   17.328216]   PREFETCH window: d0000000-dfffffff
[   17.328223] PCI: Bridge: 0000:00:06.0
[   17.328227]   IO window: disabled.
[   17.328233]   MEM window: c0100000-c01fffff
[   17.328239]   PREFETCH window: disabled.
[   17.328261] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[   17.328266]   IO window: 0000a400-0000a4ff
[   17.328275]   IO window: 0000a800-0000a8ff
[   17.328285]   PREFETCH window: 84000000-87ffffff
[   17.328294]   MEM window: 88000000-8bffffff
[   17.328303] PCI: Bridge: 0000:00:14.4
[   17.328309]   IO window: a000-afff
[   17.328320]   MEM window: f0200000-f02fffff
[   17.328328]   PREFETCH window: f0300000-f03fffff
[   17.328369] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   17.328411] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[   17.328440] NET: Registered protocol family 2
[   17.365098] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.365629] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.367291] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.368364] TCP: Hash tables configured (established 131072 bind 65536)
[   17.368370] TCP reno registered
[   17.377302] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.828284] Switched to high resolution mode on CPU 1
[   18.102546]  it is
[   18.884281] Freeing initrd memory: 7330k freed
[   18.886062] audit: initializing netlink socket (disabled)
[   18.886088] audit(1232232333.436:1): initialized
[   18.886549] highmem bounce pool size: 64 pages
[   18.890953] VFS: Disk quotas dquot_6.5.1
[   18.891117] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.891391] io scheduler noop registered
[   18.891396] io scheduler anticipatory registered
[   18.891401] io scheduler deadline registered
[   18.891425] io scheduler cfq registered (default)
[   18.891518] Boot video device is 0000:01:05.0
[   18.891751] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.891808] assign_interrupt_mode Found MSI capability
[   18.891868] Allocate Port Service[0000:00:06.0:pcie00]
[   18.891945] Allocate Port Service[0000:00:06.0:pcie02]
[   18.892438] isapnp: Scanning for PnP cards...
[   19.249514] isapnp: No Plug & Play device found
[   19.310435] Real Time Clock Driver v1.12ac
[   19.310679] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.313344] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.313487] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.313698] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   19.314169] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.314263] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.314273] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.314280] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.314286] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.314291] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.333976] mice: PS/2 mouse device common for all mice
[   19.334230] EISA: Probing bus 0 at eisa.0
[   19.334247] Cannot allocate resource for EISA slot 1
[   19.334292] Cannot allocate resource for EISA slot 8
[   19.334297] EISA: Detected 0 cards.
[   19.334303] cpuidle: using governor ladder
[   19.334308] cpuidle: using governor menu
[   19.334506] NET: Registered protocol family 1
[   19.334559] Using IPI No-Shortcut mode
[   19.334627] registered taskstats version 1
[   19.334840]   Magic number: 9:815:805
[   19.335039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.335044] EDD information not available.
[   19.335535] Freeing unused kernel memory: 368k freed
[   19.335596] Write protecting the kernel read-only data: 801k
[   19.338112] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.789448] fuse init (API version 7.9)
[   20.837496] ACPI: SSDT 77E89B8D, 0253 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   20.838801] ACPI: SSDT 77E895F0, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   20.843334] ACPI: CPU0 (power states: C1[C1] C3[C3])
[   20.843345] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.844154] ACPI: SSDT 77E89DE0, 009A (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[   20.844830] ACPI: SSDT 77E89B08, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[   20.846349] ACPI: CPU1 (power states: C1[C1] C3[C3])
[   20.846359] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.846388] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.846415] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.846437] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.846459] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.846480] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.846504] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.679386] usbcore: registered new interface driver usbfs
[   21.679438] usbcore: registered new interface driver hub
[   21.688489] usbcore: registered new device driver usb
[   21.703220] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.703308] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   21.703335] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   21.703744] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   21.703783] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0504000
[   21.759413] usb usb1: configuration #1 chosen from 1 choice
[   21.759469] hub 1-0:1.0: USB hub found
[   21.759489] hub 1-0:1.0: 4 ports detected
[   21.779702] SCSI subsystem initialized
[   21.849769] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.849780] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.855764] libata version 3.00 loaded.
[   21.855849] 8139too Fast Ethernet driver 0.9.28
[   21.863133] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   21.863163] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   21.863215] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   21.863245] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0505000
[   21.919133] usb usb2: configuration #1 chosen from 1 choice
[   21.919187] hub 2-0:1.0: USB hub found
[   21.919208] hub 2-0:1.0: 4 ports detected
[   22.022922] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
[   22.022962] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   22.022989] ATIIXP: not 100% native mode: will probe irqs later
[   22.022997] ATIIXP: IDE port disabled
[   22.023012]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[   22.023032] Probing IDE interface ide1...
[   23.092520] hdc: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[   23.092586] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   23.092910] hdc: UDMA/33 mode selected
[   23.093334] ide1 at 0x170-0x177,0x376 on irq 15
[   23.095828] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   23.095854] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   23.095917] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   23.095991] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0506000
[   23.104059] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.104282] usb usb3: configuration #1 chosen from 1 choice
[   23.104338] hub 3-0:1.0: USB hub found
[   23.104351] hub 3-0:1.0: 8 ports detected
[   23.210574] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 19
[   23.212134] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:92:fa:ec, IRQ 19
[   23.212141] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   23.217128] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   23.220972] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   23.220984] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[   23.221083] ACPI: PCI interrupt for device 0000:00:12.0 disabled
[   23.235969] sata_sil 0000:00:12.0: version 2.3
[   23.236039] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[   23.237091] scsi0 : sata_sil
[   23.237209] scsi1 : sata_sil
[   23.237729] ata1: SATA max UDMA/100 mmio m512@0xc0507000 tf 0xc0507080 irq 19
[   23.237737] ata2: SATA max UDMA/100 mmio m512@0xc0507000 tf 0xc05070c0 irq 19
[   23.268134] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   23.268152] Uniform CD-ROM driver Revision: 3.20
[   23.316725] Clocksource tsc unstable (delta = -581105206 ns)
[   23.320710] Time: acpi_pm clocksource has been installed.
[   23.583584] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.586674] ata1.00: ATA-7: TOSHIBA MK8037GSX, DL230M, max UDMA/100
[   23.586682] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.588927] ata1.00: configured for UDMA/100
[   23.804681] ata2: SATA link down (SStatus 0 SControl 300)
[   23.805028] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8037GS DL23 PQ: 0 ANSI: 5
[   23.819571] Driver 'sd' needs updating - please use bus_type methods
[   23.819735] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.819762] sd 0:0:0:0: [sda] Write Protect is off
[   23.819768] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.819806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.819905] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.819963] sd 0:0:0:0: [sda] Write Protect is off
[   23.819969] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.820007] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.820015]  sda: sda1 sda2
[   23.841170] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.850593] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.063810] Attempting manual resume
[   24.063818] swsusp: Resume From Partition 8:1
[   24.063822] PM: Checking swsusp image.
[   24.064102] PM: Resume from disk failed.
[   24.089488] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.089497] EXT3-fs: write access will be enabled during recovery.
[   24.129509] kjournald starting.  Commit interval 5 seconds
[   24.129527] EXT3-fs: recovery complete.
[   24.130324] EXT3-fs: mounted filesystem with ordered data mode.
[   32.717859] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   33.344695] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   33.405612] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.467146] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.516778] Linux agpgart interface v0.102
[   34.411203] input: Power Button (FF) as /devices/virtual/input/input3
[   34.458860] ACPI: Power Button (FF) [PWRF]
[   34.459031] input: Lid Switch as /devices/virtual/input/input4
[   34.490959] ACPI: Lid Switch [LID]
[   34.491117] input: Power Button (CM) as /devices/virtual/input/input5
[   34.538751] ACPI: Power Button (CM) [PWRB]
[   34.647542] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[   34.647592] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.647597] Yenta: Routing CardBus interrupts to PCI
[   34.647608] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[   34.879095] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   34.879107] Socket status: 30000006
[   34.879114] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   34.879120] cs: IO port probe 0xa000-0xafff: clean.
[   34.879783] pcmcia: parent PCI bridge Memory window: 0xf0200000 - 0xf02fffff
[   34.879790] pcmcia: parent PCI bridge Memory window: 0xf0300000 - 0xf03fffff
[   35.205820] ACPI: AC Adapter [ACAD] (on-line)
[   35.329945] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   35.329961] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[   35.360400] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   35.874714] ACPI: Battery Slot [BAT1] (battery present)
[   35.885760] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   36.455547] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input7
[   36.510935] ath_hal: module license 'Proprietary' taints kernel.
[   36.515546] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.526577] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   36.623257] [fglrx] Maximum main memory to use for locked dma buffers: 1776 MBytes.
[   36.623342] [fglrx] ASYNCIO init succeed!
[   36.624595] [fglrx] PAT is enabled successfully!
[   36.627271] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   36.711624] wlan: 0.9.4
[   36.763880] ath_pci: 0.9.4
[   36.763995] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   36.764015] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   37.353791] ath_rate_sample: 1.2 (0.9.4)
[   37.354814] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   37.354827] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   37.354848] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   37.354857] wifi0: mac 10.0 phy 6.1 radio 10.2
[   37.354870] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   37.354875] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   37.354879] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   37.354884] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   37.354888] wifi0: Use hw queue 8 for CAB traffic
[   37.354892] wifi0: Use hw queue 9 for beacons
[   37.424358] wifi0: Atheros 5424/2424: mem=0xc0100000, irq=20
[   38.766024] cs: IO port probe 0x100-0x3af: clean.
[   38.768713] cs: IO port probe 0x3e0-0x4ff: clean.
[   38.769899] cs: IO port probe 0x820-0x8ff: clean.
[   38.770867] cs: IO port probe 0xc00-0xcf7: clean.
[   38.772039] cs: IO port probe 0xa00-0xaff: clean.
[   39.058917] lp: driver loaded but no devices found
[   39.358203] Adding 2096440k swap on /dev/sda1.  Priority:-1 extents:1 across:2096440k
[  196.241859] EXT3 FS on sda2, internal journal
[  197.215291] ip_tables: (C) 2000-2006 Netfilter Core Team
[  197.781820] No dock devices found.
[  199.067581] apm: BIOS not found.
[  199.239198] ppdev: user-space parallel port driver
[  199.327173] audit(1232232533.691:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6467 profile="/usr/sbin/cupsd" namespace="default"
[  200.126375] eth0: link down
[  200.256357] Bluetooth: Core ver 2.11
[  200.257494] NET: Registered protocol family 31
[  200.257503] Bluetooth: HCI device and connection manager initialized
[  200.257513] Bluetooth: HCI socket layer initialized
[  200.309970] Bluetooth: L2CAP ver 2.9
[  200.309979] Bluetooth: L2CAP socket layer initialized
[  200.363375] Bluetooth: RFCOMM socket layer initialized
[  200.363406] Bluetooth: RFCOMM TTY layer initialized
[  200.363408] Bluetooth: RFCOMM ver 1.8
[  202.071715] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[  203.656180] [fglrx] GART Table is not in FRAME_BUFFER range 
[  203.656198] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  203.656205] [fglrx] Reserve Block - 1 offset =  0X7ff5000 length = 0Xb000
[  203.834811] [fglrx] interrupt source 10000000 successfully enabled
[  203.834821] [fglrx] enable ID = 0x00000004
[  203.834834] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  209.537137] hda-intel: Invalid position buffer, using LPIB read method instead.
[  216.214324] NET: Registered protocol family 10
[  216.215268] lo: Disabled Privacy Extensions
[  216.216623] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  226.109966] CPU0 attaching NULL sched-domain.
[  226.109976] CPU1 attaching NULL sched-domain.
[  226.137121] CPU0 attaching sched-domain:
[  226.137130]  domain 0: span 03
[  226.137132]   groups: 01 02
[  226.137136] CPU1 attaching sched-domain:
[  226.137138]  domain 0: span 03
[  226.137140]   groups: 02 01
[  226.730117] ath0: no IPv6 routers present
[  227.649289] NET: Registered protocol family 17
[  241.454303] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  241.455243] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  241.456972] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  241.457132] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  241.459094] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  241.459101] psmouse.c: issuing reconnect request
[  246.744257] ath0: no IPv6 routers present
[  247.083570] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  247.083592] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  247.083612] psmouse.c: bad data from KBC - timeout
[  247.098313] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  247.265809] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  247.428366] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  248.992384] psmouse.c: bad data from KBC - timeout
[  248.995844] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  248.997515] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  249.013339] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  249.171276] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  249.349390] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
floyd@Prytania:~$ 


```

Related note, if anyone has problems with their Synaptics Mouse, here is the fix:

[http://209.85.173.132/search?q=cache:wZFotbQV-UMJ:https://bugs.launchpad.net/ubuntu/%2Bsource/xserver-xorg-input-synaptics/%2Bbug/34501+psmouse.c:+TouchPad+at+isa0060/serio4/input0+lost+sync+at+byte+1&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a]("http://209.85.173.132/search?q=cache:wZFotbQV-UMJ:https://bugs.launchpad.net/ubuntu/%2Bsource/xserver-xorg-input-synaptics/%2Bbug/34501+psmouse.c:+TouchPad+at+isa0060/serio4/input0+lost+sync+at+byte+1&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a")

This link also works: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34501](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/34501)

> 

I am sorry I can't reproduce the whole changes I made to my box in these last few days, however this problem has disappeared for me so far.
One of the noticeable changes was the kernel upgrade to 2.6.24-21-generic and a line in /etc/X11/xorg.conf

        Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
...
        Option "Protocol" "auto"

which was formerly "auto-dev".
I am sure I have never set the protocol to -dev (which I guess uses developmental code), however I changed now to standard auto.
After one week of 8 hrs per day work on the machine I have not experienced any scroll loss, nor system freeze (syslog does not report any of the previous error messages either).

Maybe you should give it a try and check if this works for you as well.


That worked for me as well, it looks like the xorg maintainers left the dev code in the Synaptics touchpad. And it never got Q/A'd out of Hardy's Release.

---

### Post by PhilJ on 2009-01-18
Thanks for that fwallace99 great help. Also had to add 

ide-generic 

to /etc/modules

then played OK

cheers

philj

---

### Post by buddhacub1120 on 2009-07-01
> **fwallace99 said:**
> There is a BUG in Ubuntu:

[https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

So adding to /etc/modules:

```
libata
ata_piix
piix
```



how do i do this?

---


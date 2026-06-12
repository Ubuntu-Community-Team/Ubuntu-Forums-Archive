---
title: "new graphis card problems"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by jamesclayden on 2008-12-14
i had v8.04 working fine on my machine with an old graphics card (nvidia) but got a newer one (ATI) which booted fine first time. i then installed the ati drivers and rebooted when it asked. The screen was normal for all the load into ubuntu but after the ubuntu logo and progress bar diapered i got a plain black screen. The screen was getting a signal as it wasn't turning on to standby mode but all i could see was a plain black screen.

any help?

---

### Post by jamesclayden on 2008-12-15
i have got further with the problem. i went into recovery mode and ran the xconfig which seemed to un-install the ati driver and the booted fine. if i re-enabled the ati driver i got the exact same blank screen problem. i have pressed ctrl+alt+f1 at the blank screen but nothing happens. without the ati driver enabled i have problems with any games or visual effects.

i really need help.

---

### Post by Mark Phelps on 2008-12-15
Go into System --> Preferences --> Appearance --> Visual Effects and make sure that you have it set to "none".  Higher settings cause Compiz to be loaded and that has been known to cause problems with some ATI cards.

---

### Post by jamesclayden on 2008-12-15
i have tried that and i have tried the method on  [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). Exactly the same results every time, hangs on a blank screen after the loading page.

---

### Post by khelben1979 on 2008-12-15
What is the name of this new ATi card?

---

### Post by jamesclayden on 2008-12-15
x1950 pro. hope that helps

---

### Post by khelben1979 on 2008-12-16
I assume that the ATi driver were installed through the Ubuntu system and if that's the case, you should try and install the drivers directly from ATi instead. You'll find the drivers [here]("http://ati.amd.com/support/driver.HTML").

I must admit though, that I myself had problems with getting the drivers from ATi to work with Ubuntu Hardy a while ago and when I tried an older version of the drivers which was availabe through the Ubuntu install system, I was actually able to play Doom 3 with ATi Radeon 3200 inbuilt chipset.

So you could try the drivers from ATi, but be prepared on that they might not work if you're unlucky.

One thing which could be interesting in this case is that you post the output of what you get from [the dmesg tool]("http://en.wikipedia.org/wiki/Dmesg") in order for me (and others) to see what more hardware you have over there.

Seeing how your /etc/X11/xorg.conf looks like might also be interesting.

---

### Post by jamesclayden on 2008-12-16
I will try installing the other drivers.

when should i run the dmesg tool? when the system is not working properly i have no way to access terminal. would the results still be useful from my system straight after a recovery by xfig?

I will try to help you but i think i am in out of my depth.

---

### Post by khelben1979 on 2008-12-16
Running dmesg from a working terminal is the thing you need to do.

The purpose of using the dmesg tool here is mostly so I can see more in detail what hardware you have over there, not to see what malfunctions or not.

---

### Post by jamesclayden on 2008-12-16
i will run that tonight when i get home and post results here.

thank you

---

### Post by jamesclayden on 2008-12-16
i tried to install the other driver but had problems. Ubuntu recoverd it self after reset and un-did all my messing around. Here is dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008 (Ubuntu 2.6.24-22.45-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f52e0
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6DF0 checksum 0
[    0.000000] ACPI: RSDP 000F6DF0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 3FFF30C0, 464A (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF7740, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=CD11-4920 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2191.215 MHz processor.
[   41.514762] Console: colour VGA+ 80x25
[   41.514765] console [tty0] enabled
[   41.515242] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   41.515664] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   41.541605] Memory: 1027104k/1048512k available (2177k kernel code, 20704k reserved, 1005k data, 368k init, 131008k highmem)
[   41.541613] virtual kernel memory layout:
[   41.541614]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   41.541615]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   41.541616]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   41.541617]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   41.541618]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   41.541619]       .data : 0xc0320704 - 0xc041bdc4   (1005 kB)
[   41.541620]       .text : 0xc0100000 - 0xc0320704   (2177 kB)
[   41.541623] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   41.541665] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   41.621639] Calibrating delay using timer specific routine.. 4386.40 BogoMIPS (lpj=8772802)
[   41.621669] Security Framework initialized
[   41.621676] SELinux:  Disabled at boot.
[   41.621693] AppArmor: AppArmor initialized
[   41.621698] Failure registering capabilities with primary security module.
[   41.621707] Mount-cache hash table entries: 512
[   41.621833] Initializing cgroup subsys ns
[   41.621837] Initializing cgroup subsys cpuacct
[   41.621847] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   41.621855] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   41.621858] CPU: L2 Cache: 512K (64 bytes/line)
[   41.621861] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   41.621871] Compat vDSO mapped to ffffe000.
[   41.621882] Checking 'hlt' instruction... OK.
[   41.637845] SMP alternatives: switching to UP code
[   41.638827] Freeing SMP alternatives: 11k freed
[   41.638937] Early unpacking initramfs... done
[   41.943922] ACPI: Core revision 20070126
[   41.943995] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   41.946476] CPU0: AMD Athlon(tm) XP 3200+ stepping 00
[   41.946491] Total of 1 processors activated (4386.40 BogoMIPS).
[   41.946684] ENABLING IO-APIC IRQs
[   41.946879] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   42.093405] Brought up 1 CPUs
[   42.093433] CPU0 attaching sched-domain:
[   42.093436]  domain 0: span 01
[   42.093437]   groups: 01
[   42.093609] net_namespace: 64 bytes
[   42.093615] Booting paravirtualized kernel on bare hardware
[   42.094044] Time: 19:35:13  Date: 12/16/08
[   42.094069] NET: Registered protocol family 16
[   42.094268] EISA bus registered
[   42.094294] ACPI: bus type pci registered
[   42.126133] PCI: PCI BIOS revision 2.10 entry at 0xfaf50, last bus=2
[   42.126135] PCI: Using configuration type 1
[   42.126139] Setting up standard PCI resources
[   42.129847] ACPI: EC: Look up EC in DSDT
[   42.134661] ACPI: Interpreter enabled
[   42.134663] ACPI: (supports S0 S1 S4 S5)
[   42.134675] ACPI: Using IOAPIC for interrupt routing
[   42.142824] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   42.142893] PCI: nForce2 C1 Halt Disconnect fixup
[   42.143765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   42.143908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   42.144175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   42.184829] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   42.184980] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.185131] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   42.185280] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   42.185436] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.185586] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   42.185738] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   42.185886] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.186034] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.186182] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.186335] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.186484] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   42.186635] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   42.186786] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.186935] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.187083] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   42.187209] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[   42.187329] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   42.187444] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[   42.187558] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   42.187672] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   42.187837] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   42.188003] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   42.188166] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[   42.188330] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   42.188494] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[   42.188658] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   42.188773] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   42.188935] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   42.189098] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   42.189262] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   42.189435] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   42.189564] Linux Plug and Play Support v0.97 (c) Adam Belay
[   42.189595] pnp: PnP ACPI init
[   42.189603] ACPI: bus type pnp registered
[   42.194310] pnp: PnP ACPI: found 15 devices
[   42.194312] ACPI: ACPI bus type pnp unregistered
[   42.194316] PnPBIOS: Disabled by ACPI PNP
[   42.194543] PCI: Using ACPI for IRQ routing
[   42.194547] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   42.237296] NET: Registered protocol family 8
[   42.237299] NET: Registered protocol family 20
[   42.237365] AppArmor: AppArmor Filesystem Enabled
[   42.241265] Time: tsc clocksource has been installed.
[   42.249294] system 00:00: ioport range 0x1000-0x107f has been reserved
[   42.249297] system 00:00: ioport range 0x1080-0x10ff has been reserved
[   42.249300] system 00:00: ioport range 0x1400-0x147f has been reserved
[   42.249302] system 00:00: ioport range 0x1480-0x14ff has been reserved
[   42.249305] system 00:00: ioport range 0x1800-0x187f has been reserved
[   42.249307] system 00:00: ioport range 0x1880-0x18ff has been reserved
[   42.249312] system 00:01: ioport range 0x1c00-0x1c3f has been reserved
[   42.249314] system 00:01: ioport range 0x2000-0x203f has been reserved
[   42.249320] system 00:02: iomem range 0xcf800-0xcffff has been reserved
[   42.249322] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   42.249325] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   42.249327] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   42.249330] system 00:02: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   42.249333] system 00:02: iomem range 0xffff0000-0xffffffff could not be reserved
[   42.249335] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[   42.249338] system 00:02: iomem range 0x100000-0x3ffeffff could not be reserved
[   42.249341] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[   42.249343] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[   42.249348] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   42.249351] system 00:04: ioport range 0x800-0x805 has been reserved
[   42.249353] system 00:04: ioport range 0x290-0x29f has been reserved
[   42.279742] PCI: Bridge: 0000:00:08.0
[   42.279744]   IO window: a000-cfff
[   42.279749]   MEM window: e6000000-e7ffffff
[   42.279753]   PREFETCH window: 50000000-500fffff
[   42.279758] PCI: Bridge: 0000:00:1e.0
[   42.279760]   IO window: d000-dfff
[   42.279763]   MEM window: e4000000-e5ffffff
[   42.279766]   PREFETCH window: d0000000-dfffffff
[   42.279776] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   42.279789] NET: Registered protocol family 2
[   42.317294] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   42.317609] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   42.318755] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   42.319309] TCP: Hash tables configured (established 131072 bind 65536)
[   42.319311] TCP reno registered
[   42.329346] checking if image is initramfs... it is
[   42.780933] Switched to high resolution mode on CPU 0
[   42.910007] Freeing initrd memory: 7567k freed
[   42.910643] audit: initializing netlink socket (disabled)
[   42.910656] audit(1229456113.264:1): initialized
[   42.910793] highmem bounce pool size: 64 pages
[   42.912551] VFS: Disk quotas dquot_6.5.1
[   42.912618] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.912734] io scheduler noop registered
[   42.912736] io scheduler anticipatory registered
[   42.912738] io scheduler deadline registered
[   42.912748] io scheduler cfq registered (default)
[   42.912871] Boot video device is 0000:02:00.0
[   42.913140] isapnp: Scanning for PnP cards...
[   43.267380] isapnp: No Plug & Play device found
[   43.294157] Real Time Clock Driver v1.12ac
[   43.294264] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   43.294392] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.294529] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.295052] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.295266] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.296013] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   43.296076] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   43.296162] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   43.296165] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   43.296612] serio: i8042 KBD port at 0x60,0x64 irq 1
[   43.308527] mice: PS/2 mouse device common for all mice
[   43.308637] EISA: Probing bus 0 at eisa.0
[   43.308645] Cannot allocate resource for EISA slot 1
[   43.308647] Cannot allocate resource for EISA slot 2
[   43.308675] EISA: Detected 0 cards.
[   43.308677] cpuidle: using governor ladder
[   43.308679] cpuidle: using governor menu
[   43.308807] NET: Registered protocol family 1
[   43.308832] Using IPI No-Shortcut mode
[   43.308862] registered taskstats version 1
[   43.308957]   Magic number: 4:285:597
[   43.309022]   hash matches device ptyd1
[   43.309112] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   43.309114] EDD information not available.
[   43.309457] Freeing unused kernel memory: 368k freed
[   43.309480] Write protecting the kernel read-only data: 801k
[   43.336472] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   44.509432] fuse init (API version 7.9)
[   45.219143] usbcore: registered new interface driver usbfs
[   45.219165] usbcore: registered new interface driver hub
[   45.227497] usbcore: registered new device driver usb
[   45.233447] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   45.233798] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   45.233806] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 16
[   45.233819] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.233823] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   45.234073] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   45.234091] ohci_hcd 0000:00:02.0: irq 16, io mem 0xe8002000
[   45.271278] SCSI subsystem initialized
[   45.289139] usb usb1: configuration #1 chosen from 1 choice
[   45.289166] hub 1-0:1.0: USB hub found
[   45.289175] hub 1-0:1.0: 3 ports detected
[   45.317995] libata version 3.00 loaded.
[   45.391329] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   45.391339] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 17
[   45.391353] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   45.391357] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   45.391380] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   45.391397] ohci_hcd 0000:00:02.1: irq 17, io mem 0xe8003000
[   45.449020] usb usb2: configuration #1 chosen from 1 choice
[   45.449045] hub 2-0:1.0: USB hub found
[   45.449054] hub 2-0:1.0: 3 ports detected
[   45.449138] Floppy drive(s): fd0 is 1.44M
[   45.474522] FDC 0 is a post-1991 82077
[   45.551302] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   45.551312] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 18
[   45.551324] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   45.551328] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   45.551352] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   45.551384] ehci_hcd 0000:00:02.2: debug port 1
[   45.551388] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   45.551398] ehci_hcd 0000:00:02.2: irq 18, io mem 0xe8004000
[   45.694715] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   45.706699] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.706823] usb usb3: configuration #1 chosen from 1 choice
[   45.706851] hub 3-0:1.0: USB hub found
[   45.706861] hub 3-0:1.0: 6 ports detected
[   45.810796] r8169 Gigabit Ethernet driver 2.2LK loaded
[   45.811005] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   45.811012] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 19
[   45.811237] eth0: RTL8110s at 0xf881e000, 00:0d:61:49:24:d0, XID 04000000 IRQ 19
[   45.814475] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   45.817067] sata_sil 0000:01:0d.0: version 2.3
[   45.817277] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   45.817284] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 20
[   45.817299] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
[   45.818940] scsi0 : sata_sil
[   45.819575] scsi1 : sata_sil
[   45.819612] ata1: SATA max UDMA/100 mmio m512@0xe7004000 tf 0xe7004080 irq 20
[   45.819616] ata2: SATA max UDMA/100 mmio m512@0xe7004000 tf 0xe70040c0 irq 20
[   46.130383] ata1: SATA link down (SStatus 0 SControl 310)
[   46.386184] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   46.442148] ata2: SATA link down (SStatus 0 SControl 310)
[   46.442313] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 19
[   46.492086] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e7005000-e70057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   46.494224] pata_amd 0000:00:09.0: version 0.3.10
[   46.494285] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   46.494973] scsi2 : pata_amd
[   46.495467] scsi3 : pata_amd
[   46.496182] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   46.496185] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   46.674504] ata3.00: ATA-5: IC35L100AVVA07-0, VA5OA52A, max UDMA/100
[   46.674507] ata3.00: 201045600 sectors, multi 16: LBA 
[   46.676082] ata3.01: ATA-7: Maxtor 6L250R0, BAH41G10, max UDMA/133
[   46.676084] ata3.01: 490234752 sectors, multi 16: LBA48 
[   46.689223] usb 3-1: configuration #1 chosen from 1 choice
[   46.698443] ata3.00: configured for UDMA/100
[   46.715756] ata3.01: configured for UDMA/133
[   47.301980] ata4.00: ATAPI: _NEC DVD_RW ND-2500A, 1.06, max UDMA/33
[   47.301997] ata4.01: ATAPI: JLMS DVD-ROM LTD-166S, DS08, max UDMA/44
[   47.417417] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   47.473759] ata4.00: configured for UDMA/33
[   47.629607] ata4.01: configured for UDMA/44
[   47.629716] scsi 2:0:0:0: Direct-Access     ATA      IC35L100AVVA07-0 VA5O PQ: 0 ANSI: 5
[   47.630095] scsi 2:0:1:0: Direct-Access     ATA      Maxtor 6L250R0   BAH4 PQ: 0 ANSI: 5
[   47.630765] usb 1-2: configuration #1 chosen from 1 choice
[   47.632157] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.06 PQ: 0 ANSI: 5
[   47.632460] scsi 3:0:1:0: CD-ROM              JLMS   DVD-ROM LTD-166S DS08 PQ: 0 ANSI: 5
[   47.644219] Driver 'sd' needs updating - please use bus_type methods
[   47.644308] sd 2:0:0:0: [sda] 201045600 512-byte hardware sectors (102935 MB)
[   47.644321] sd 2:0:0:0: [sda] Write Protect is off
[   47.644323] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.644339] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.644385] sd 2:0:0:0: [sda] 201045600 512-byte hardware sectors (102935 MB)
[   47.644394] sd 2:0:0:0: [sda] Write Protect is off
[   47.644397] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.644410] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.644414]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   47.658738]  sda1 sda2 sda3
[   47.658830] sd 2:0:0:0: [sda] Attached SCSI disk
[   47.658901] sd 2:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   47.658914] sd 2:0:1:0: [sdb] Write Protect is off
[   47.658916] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   47.658932] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.658972] sd 2:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[   47.658981] sd 2:0:1:0: [sdb] Write Protect is off
[   47.658984] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   47.658998] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.659001]  sdb: sdb1
[   47.677598] sd 2:0:1:0: [sdb] Attached SCSI disk
[   47.684579] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   47.684585] Uniform CD-ROM driver Revision: 3.20
[   47.684636] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   47.685050] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   47.685068] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   47.685082] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   47.685097] sr 3:0:1:0: Attached scsi generic sg3 type 5
[   47.687152] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   47.687209] sr 3:0:1:0: Attached scsi CD-ROM sr1
[   47.765340] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000d61000041d127]
[   47.937034] usb 1-3: new full speed USB device using ohci_hcd and address 4
[   48.161473] usb 1-3: configuration #1 chosen from 1 choice
[   48.164516] usbcore: registered new interface driver hiddev
[   48.169615] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input2
[   48.176969] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[   48.176991] usbcore: registered new interface driver usbhid
[   48.176995] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.295219] loop: module loaded
[   48.345207] kjournald starting.  Commit interval 5 seconds
[   48.345218] EXT3-fs: mounted filesystem with ordered data mode.
[   54.485125] Linux agpgart interface v0.102
[   54.606376] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.652125] agpgart: Detected NVIDIA nForce2 chipset
[   54.655722] agpgart: AGP aperture is 64M @ 0xe0000000
[   54.700117] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   54.700133] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   54.740073] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.780101] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   54.838165] input: Power Button (FF) as /devices/virtual/input/input4
[   54.847917] ACPI: Power Button (FF) [PWRF]
[   54.848041] input: Power Button (CM) as /devices/virtual/input/input5
[   54.863908] ACPI: Power Button (CM) [PWRB]
[   57.071739] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 19
[   57.499621] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7904
[   57.499638] usbcore: registered new interface driver usblp
[   57.869346] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   57.869353] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   57.869387] usbcore: registered new interface driver rt2500usb
[   57.901284] parport_pc 00:0c: reported by Plug and Play ACPI
[   57.901369] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   58.155649] phy1: Selected rate control algorithm 'simple'
[   58.219873] usbcore: registered new interface driver rt73usb
[   59.584810] lp0: using parport0 (interrupt-driven).
[   60.208925] EXT3 FS on loop0, internal journal
[  105.078599] kjournald starting.  Commit interval 5 seconds
[  105.078623] EXT3 FS on loop1, internal journal
[  105.078627] EXT3-fs: mounted filesystem with ordered data mode.
[  105.078949] kjournald starting.  Commit interval 5 seconds
[  105.078967] EXT3 FS on loop2, internal journal
[  105.078970] EXT3-fs: mounted filesystem with ordered data mode.
[  105.695951] Adding 975924k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:159 across:6243932k
[  108.027280] ip_tables: (C) 2000-2006 Netfilter Core Team
[  108.281952] No dock devices found.
[  109.354114] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  109.354119] apm: overridden by ACPI.
[  109.491759] ppdev: user-space parallel port driver
[  109.586189] audit(1229456181.109:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5404 profile="/usr/sbin/cupsd" namespace="default"
[  113.494301] r8169: eth0: link down
[  113.597009] Bluetooth: Core ver 2.11
[  113.597655] NET: Registered protocol family 31
[  113.597659] Bluetooth: HCI device and connection manager initialized
[  113.597663] Bluetooth: HCI socket layer initialized
[  113.623418] Bluetooth: L2CAP ver 2.9
[  113.623423] Bluetooth: L2CAP socket layer initialized
[  113.679837] Bluetooth: RFCOMM socket layer initialized
[  113.680056] Bluetooth: RFCOMM TTY layer initialized
[  113.680059] Bluetooth: RFCOMM ver 1.8
[  114.578545] [drm] Initialized drm 1.1.0 20060810
[  179.305881] NET: Registered protocol family 10
[  179.306100] lo: Disabled Privacy Extensions
[  179.306466] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  179.306875] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  187.486163] NET: Registered protocol family 17
[  188.788707] wlan0: Initial auth_alg=1
[  188.788715] wlan0: authenticate with AP 00:18:f6:ad:77:a1
[  188.791606] wlan0: RX authentication from 00:18:f6:ad:77:a1 (alg=1 transaction=2 status=0)
[  188.791610] wlan0: replying to auth challenge
[  188.794615] wlan0: RX authentication from 00:18:f6:ad:77:a1 (alg=1 transaction=4 status=0)
[  188.794622] wlan0: authenticated
[  188.794624] wlan0: associate with AP 00:18:f6:ad:77:a1
[  188.797124] wlan0: RX AssocResp from 00:18:f6:ad:77:a1 (capab=0x411 status=0 aid=1)
[  188.797130] wlan0: associated
[  188.797174] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  188.797178] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  188.797181] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  188.797183] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  188.798119] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  189.080339] UDF-fs: No VRS found
[  189.104069] ISO 9660 Extensions: Microsoft Joliet Level 3
[  189.105674] ISOFS: changing to secondary root
[  211.403501] wlan0: no IPv6 routers present

```

hope some of it makes sence to you.

cheers.

---

### Post by jamesclayden on 2008-12-19
This was fixed with the vesa driver. It is the only driver i could get to work with my ati X1950.

thanks all

---


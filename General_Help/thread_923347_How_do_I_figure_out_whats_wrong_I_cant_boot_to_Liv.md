---
title: "How do I figure out whats wrong? I cant boot to Live CD"
date: 2008-09-18
forum: General Help
---

### Post by ju2wheels on 2008-09-18
I had originally posted this on the hardware side to see if any knew of hardware issues with my hardware but am getting nowhere.

I really want to know why I cant boot to the Live CD on my new computer, specs below, but I get no error outputs and just end up at a Busybox prompt.

How can I figure out whats going on, whether its something I can fix or whether its just that Ubuntu doesnt support my hardware? I can boot into a Knoppix 5.2 cd fine (of course everything isnt identified correctly) so I dont see why I shouldnt at least be able to get to a Gnome desktop on Ubuntu.

Hardware:

MSI P7N SLI-FI 750i SLI Chipset LGA775
NVIDIA GeForce 8500 GT 512MB 16X PCI Express
Core 2 Quad Q6600 @ 2.4GHz 1066FSB 8MB L2 Cache 64-bit
4gb PC6400 DDR2/800 Dual Channel Memory
Sata II HD on Sata2

---

### Post by drs305 on 2008-09-18
When you inserted the livecd, the third choice is to check the CD for defects. Have you run that to ensure the CD was burned without errors?

---

### Post by ju2wheels on 2008-09-18
Im using a bootable USB of ISO's I have used before. Ive tried multiple distros with essentially the same result across the board.

---

### Post by mempman on 2008-09-18
It may be because there are some core devices on your motherboard that don't have linux drivers for them.  For example, my lil bro's emachine PC cannot boot live cd.  Well it can, but the onboard video goes dead and unresponsive. I suppose he could make it work by buying a seperate gpu-card.

---

### Post by ju2wheels on 2008-09-18
Would it make a difference if I ignored the Live CD and tried the alternate? Meaning, if it doesnt work with the Live CD, what are the chances that doing an install with the alternate will result in a non functional install?

---

### Post by ModelM on 2008-09-18
Try adding
```

all_generic_ide
```

to the boot options.

---

### Post by jacobc2 on 2008-09-18
> **ju2wheels said:**
> Would it make a difference if I ignored the Live CD and tried the alternate? Meaning, if it doesnt work with the Live CD, what are the chances that doing an install with the alternate will result in a non functional install?
The alternate installer is made just for this reason.  It is 100% text based.  As long as you can see the kernel dumps on the screen you will be able to use the alternate installer.  It doesn't require a high level card to do what its doing.  I'm guessing that you can see the kernel dumps (boot screen) of the live CD and then it just goes blank or something.  If that is the case the alternate installer will work just fine.  But if the screen goes blank as soon as it startes booting your system has something that isn't supported, or your USB stick has an error on it somewhere.

---

### Post by ju2wheels on 2008-09-18
Ill have to try the alternate CD later, but in the mean time since I was using a bootable USB I was able to get Busybox to let me mount the USB stick so I could redirect the dmesg output to it.

This is what I got out of dmesg, but nothing looks out of line or odd to me except the fd0 errors, but that makes sense to me as theres no floppy in the drive...

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Aug 12 13:37:22 UTC 2008 (Ubuntu 2.6.24-21.40-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098000 (usable)
[    0.000000]  BIOS-e820: 0000000000098000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000bffee000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9E50 checksum 0
[    0.000000] ACPI: RSDP 000F9E50, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT BFF90000, 0034 (r1 071108 RSDT1534 20080711 MSFT       97)
[    0.000000] ACPI: FACP BFF90200, 0084 (r1 071108 FACP1534 20080711 MSFT       97)
[    0.000000] ACPI: DSDT BFF90450, 4E23 (r1  1AAAA 1AAAA000        0 INTL 20051117)
[    0.000000] ACPI: FACS BFF9E000, 0040
[    0.000000] ACPI: APIC BFF90390, 0080 (r1 071108 APIC1534 20080711 MSFT       97)
[    0.000000] ACPI: MCFG BFF90410, 003C (r1 071108 OEMMCFG  20080711 MSFT       97)
[    0.000000] ACPI: OEMB BFF9E040, 0072 (r1 071108 OEMB1534 20080711 MSFT       97)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
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
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
[    0.000000] swsusp: Registered nosave memory region: 0000000000098000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz all_generic_ide file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2399.967 MHz processor.
[   56.391445] spurious 8259A interrupt: IRQ7.
[   56.393529] Console: colour VGA+ 80x25
[   56.393531] console [tty0] enabled
[   56.393788] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   56.394025] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   56.526433] Memory: 3095240k/4194304k available (2177k kernel code, 48764k reserved, 1006k data, 368k init, 2227776k highmem)
[   56.526438] virtual kernel memory layout:
[   56.526438]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   56.526439]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   56.526440]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   56.526441]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   56.526441]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   56.526442]       .data : 0xc0320504 - 0xc041bdc4   (1006 kB)
[   56.526443]       .text : 0xc0100000 - 0xc0320504   (2177 kB)
[   56.526445] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   56.526479] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   56.606382] Calibrating delay using timer specific routine.. 4804.86 BogoMIPS (lpj=9609731)
[   56.606402] Security Framework initialized
[   56.606409] SELinux:  Disabled at boot.
[   56.606418] AppArmor: AppArmor initialized
[   56.606421] Failure registering capabilities with primary security module.
[   56.606427] Mount-cache hash table entries: 512
[   56.606525] Initializing cgroup subsys ns
[   56.606528] Initializing cgroup subsys cpuacct
[   56.606536] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   56.606542] monitor/mwait feature present.
[   56.606543] using mwait in idle threads.
[   56.606546] CPU: L1 I cache: 32K, L1 D cache: 32K
[   56.606547] CPU: L2 cache: 4096K
[   56.606549] CPU: Physical Processor ID: 0
[   56.606550] CPU: Processor Core ID: 0
[   56.606551] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043940 0000e3bd 00000000 00000001 00000000
[   56.606558] Compat vDSO mapped to ffffe000.
[   56.606568] Checking 'hlt' instruction... OK.
[   56.622639] SMP alternatives: switching to UP code
[   56.623810] Early unpacking initramfs... done
[   56.953390] ACPI: Core revision 20070126
[   56.953421] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   56.955697] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   56.955708] SMP alternatives: switching to SMP code
[   56.956198] Booting processor 1/1 eip 3000
[   56.966569] Initializing CPU#1
[   57.045713] Calibrating delay using timer specific routine.. 4800.28 BogoMIPS (lpj=9600579)
[   57.045718] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   57.045722] monitor/mwait feature present.
[   57.045724] CPU: L1 I cache: 32K, L1 D cache: 32K
[   57.045725] CPU: L2 cache: 4096K
[   57.045727] CPU: Physical Processor ID: 0
[   57.045727] CPU: Processor Core ID: 1
[   57.045728] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043940 0000e3bd 00000000 00000001 00000000
[   57.046286] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   57.046311] SMP alternatives: switching to SMP code
[   57.046818] Booting processor 2/2 eip 3000
[   57.057078] Initializing CPU#2
[   57.137574] Calibrating delay using timer specific routine.. 4800.32 BogoMIPS (lpj=9600647)
[   57.137579] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   57.137583] monitor/mwait feature present.
[   57.137585] CPU: L1 I cache: 32K, L1 D cache: 32K
[   57.137586] CPU: L2 cache: 4096K
[   57.137588] CPU: Physical Processor ID: 0
[   57.137588] CPU: Processor Core ID: 2
[   57.137589] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043940 0000e3bd 00000000 00000001 00000000
[   57.138095] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   57.138112] SMP alternatives: switching to SMP code
[   57.138468] Booting processor 3/3 eip 3000
[   57.148728] Initializing CPU#3
[   57.225441] Calibrating delay using timer specific routine.. 4800.35 BogoMIPS (lpj=9600703)
[   57.225446] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001 00000000
[   57.225449] monitor/mwait feature present.
[   57.225452] CPU: L1 I cache: 32K, L1 D cache: 32K
[   57.225453] CPU: L2 cache: 4096K
[   57.225454] CPU: Physical Processor ID: 0
[   57.225455] CPU: Processor Core ID: 3
[   57.225456] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043940 0000e3bd 00000000 00000001 00000000
[   57.225987] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   57.226004] Total of 4 processors activated (19205.83 BogoMIPS).
[   57.226264] ENABLING IO-APIC IRQs
[   57.226472] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   57.373299] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   57.393301] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   57.413313] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   57.433299] Brought up 4 CPUs
[   57.433322] CPU0 attaching sched-domain:
[   57.433324]  domain 0: span 03
[   57.433325]   groups: 01 02
[   57.433327]   domain 1: span 0f
[   57.433329]    groups: 03 0c
[   57.433330] CPU1 attaching sched-domain:
[   57.433331]  domain 0: span 03
[   57.433333]   groups: 02 01
[   57.433334]   domain 1: span 0f
[   57.433335]    groups: 03 0c
[   57.433337] CPU2 attaching sched-domain:
[   57.433338]  domain 0: span 0c
[   57.433339]   groups: 04 08
[   57.433341]   domain 1: span 0f
[   57.433342]    groups: 0c 03
[   57.433344] CPU3 attaching sched-domain:
[   57.433345]  domain 0: span 0c
[   57.433346]   groups: 08 04
[   57.433348]   domain 1: span 0f
[   57.433349]    groups: 0c 03
[   57.433557] net_namespace: 64 bytes
[   57.433566] Booting paravirtualized kernel on bare hardware
[   57.433904] Time: 10:45:09  Date: 09/18/08
[   57.433920] NET: Registered protocol family 16
[   57.434040] EISA bus registered
[   57.434044] ACPI: bus type pci registered
[   57.434286] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[   57.434288] PCI: Using configuration type 1
[   57.434308] Setting up standard PCI resources
[   57.441485] ACPI: EC: Look up EC in DSDT
[   57.444914] ACPI: Interpreter enabled
[   57.444916] ACPI: (supports S0 S1 S3 S4 S5)
[   57.444927] ACPI: Using IOAPIC for interrupt routing
[   57.445058] Error attaching device data
[   57.445085] Error attaching device data
[   57.445111] Error attaching device data
[   57.445140] Error attaching device data
[   57.451100] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   57.453185] PCI: Transparent bridge - 0000:00:10.0
[   57.453206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   57.453378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   57.453468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   57.453536] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[   57.453603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   57.462730] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   57.462882] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   57.463030] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   57.463179] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   57.463326] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[   57.463473] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   57.463621] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   57.463768] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   57.463916] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[   57.464063] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
[   57.464210] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[   57.464357] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[   57.464504] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   57.464654] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   57.464801] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[   57.464949] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[   57.465096] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[   57.465246] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[   57.465422] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   57.465507] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  60, should be 57 [20070126]
[   57.465511] Linux Plug and Play Support v0.97 (c) Adam Belay
[   57.465531] pnp: PnP ACPI init
[   57.465536] ACPI: bus type pnp registered
[   57.468835] pnp: PnP ACPI: found 14 devices
[   57.468837] ACPI: ACPI bus type pnp unregistered
[   57.468839] PnPBIOS: Disabled by ACPI PNP
[   57.468981] PCI: Using ACPI for IRQ routing
[   57.468983] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   57.532997] NET: Registered protocol family 8
[   57.532999] NET: Registered protocol family 20
[   57.533038] AppArmor: AppArmor Filesystem Enabled
[   57.536987] Time: tsc clocksource has been installed.
[   57.552986] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   57.552988] system 00:06: ioport range 0x800-0x80f has been reserved
[   57.552990] system 00:06: ioport range 0x4000-0x407f has been reserved
[   57.552991] system 00:06: ioport range 0x4080-0x40ff has been reserved
[   57.552993] system 00:06: ioport range 0x4400-0x447f has been reserved
[   57.552995] system 00:06: ioport range 0x4480-0x44ff has been reserved
[   57.552997] system 00:06: ioport range 0x4800-0x487f has been reserved
[   57.552998] system 00:06: ioport range 0x4880-0x48ff has been reserved
[   57.553000] system 00:06: ioport range 0x2000-0x207f has been reserved
[   57.553002] system 00:06: ioport range 0x2080-0x20ff has been reserved
[   57.553004] system 00:06: iomem range 0x0-0x0 could not be reserved
[   57.553006] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[   57.553010] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[   57.553012] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   57.553018] system 00:0b: ioport range 0xa00-0xadf has been reserved
[   57.553020] system 00:0b: ioport range 0xae0-0xaef has been reserved
[   57.553024] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   57.553029] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   57.553031] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   57.553033] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   57.553034] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[   57.553036] system 00:0d: iomem range 0xfed45000-0xffffffff could not be reserved
[   57.583272] PCI: Bridge: 0000:02:00.0
[   57.583274]   IO window: e000-efff
[   57.583278]   MEM window: fa000000-febfffff
[   57.583281]   PREFETCH window: d0000000-dfffffff
[   57.583284] PCI: Bridge: 0000:02:02.0
[   57.583285]   IO window: disabled.
[   57.583288]   MEM window: disabled.
[   57.583291]   PREFETCH window: disabled.
[   57.583294] PCI: Bridge: 0000:02:03.0
[   57.583295]   IO window: disabled.
[   57.583299]   MEM window: disabled.
[   57.583301]   PREFETCH window: disabled.
[   57.583304] PCI: Bridge: 0000:01:00.0
[   57.583306]   IO window: e000-efff
[   57.583310]   MEM window: fa000000-febfffff
[   57.583312]   PREFETCH window: d0000000-dfffffff
[   57.583316] PCI: Bridge: 0000:00:03.0
[   57.583317]   IO window: e000-efff
[   57.583320]   MEM window: fa000000-febfffff
[   57.583322]   PREFETCH window: d0000000-dfffffff
[   57.583324] PCI: Bridge: 0000:00:06.0
[   57.583325]   IO window: disabled.
[   57.583327]   MEM window: disabled.
[   57.583329]   PREFETCH window: disabled.
[   57.583331] PCI: Bridge: 0000:00:07.0
[   57.583332]   IO window: disabled.
[   57.583335]   MEM window: disabled.
[   57.583336]   PREFETCH window: disabled.
[   57.583339] PCI: Bridge: 0000:00:10.0
[   57.583340]   IO window: disabled.
[   57.583343]   MEM window: disabled.
[   57.583346]   PREFETCH window: disabled.
[   57.583358] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   57.583367] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   57.583377] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   57.583386] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   57.583396] PCI: Setting latency timer of device 0000:02:03.0 to 64
[   57.583404] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   57.583411] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   57.583421] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   57.583429] NET: Registered protocol family 2
[   57.624892] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   57.625046] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   57.625349] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   57.625492] TCP: Hash tables configured (established 131072 bind 65536)
[   57.625494] TCP reno registered
[   57.636925] checking if image is initramfs... it is
[   58.080241] Switched to high resolution mode on CPU 1
[   58.080274] Switched to high resolution mode on CPU 2
[   58.080312] Switched to high resolution mode on CPU 3
[   58.084160] Switched to high resolution mode on CPU 0
[   58.287560] Freeing initrd memory: 10901k freed
[   58.288467] audit: initializing netlink socket (disabled)
[   58.288477] audit(1221734709.612:1): initialized
[   58.288676] highmem bounce pool size: 64 pages
[   58.290244] VFS: Disk quotas dquot_6.5.1
[   58.290298] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   58.290392] io scheduler noop registered
[   58.290393] io scheduler anticipatory registered
[   58.290395] io scheduler deadline registered
[   58.290402] io scheduler cfq registered (default)
[   58.290529] pci 0000:00:03.0: Quirk disabling HT MSI mapping<6>pci 0000:00:06.0: Quirk disabling HT MSI mapping<6>pci 0000:00:07.0: Quirk disabling HT MSI mapping<6>pci 0000:00:09.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0f.0: Quirk disabling HT MSI mapping<6>pci 0000:00:10.0: Quirk disabling HT MSI mapping<6>pci 0000:00:10.1: Quirk disabling HT MSI mapping<7>Boot video device is 0000:03:00.0
[   58.313188] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   58.313222] assign_interrupt_mode Found MSI capability
[   58.313244] Allocate Port Service[0000:00:03.0:pcie00]
[   58.313311] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   58.313342] assign_interrupt_mode Found MSI capability
[   58.313363] Allocate Port Service[0000:00:06.0:pcie00]
[   58.313426] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   58.313457] assign_interrupt_mode Found MSI capability
[   58.313477] Allocate Port Service[0000:00:07.0:pcie00]
[   58.313545] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   58.313578] Allocate Port Service[0000:01:00.0:pcie10]
[   58.313647] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   58.313677] Allocate Port Service[0000:02:00.0:pcie20]
[   58.313744] PCI: Setting latency timer of device 0000:02:02.0 to 64
[   58.313774] Allocate Port Service[0000:02:02.0:pcie20]
[   58.313841] PCI: Setting latency timer of device 0000:02:03.0 to 64
[   58.313871] Allocate Port Service[0000:02:03.0:pcie20]
[   58.314077] isapnp: Scanning for PnP cards...
[   58.666978] isapnp: No Plug & Play device found
[   58.686996] Real Time Clock Driver v1.12ac
[   58.687073] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   58.687260] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   58.687690] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   58.688351] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   58.688401] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   58.688475] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   58.690616] serio: i8042 KBD port at 0x60,0x64 irq 1
[   58.690622] serio: i8042 AUX port at 0x60,0x64 irq 12
[   58.719098] mice: PS/2 mouse device common for all mice
[   58.719200] EISA: Probing bus 0 at eisa.0
[   58.719209] Cannot allocate resource for EISA slot 2
[   58.719214] Cannot allocate resource for EISA slot 4
[   58.719215] Cannot allocate resource for EISA slot 5
[   58.719217] Cannot allocate resource for EISA slot 6
[   58.719224] EISA: Detected 0 cards.
[   58.719226] cpuidle: using governor ladder
[   58.719227] cpuidle: using governor menu
[   58.719306] NET: Registered protocol family 1
[   58.719332] Using IPI No-Shortcut mode
[   58.719358] registered taskstats version 1
[   58.719476]   Magic number: 8:665:780
[   58.719558]   hash matches device ptyq2
[   58.719593] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   58.719594] EDD information not available.
[   58.719774] Freeing unused kernel memory: 368k freed
[   58.745076] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   58.792420] SCSI subsystem initialized
[   58.797476] libata version 3.00 loaded.
[   58.798544] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   58.798592] scsi0 : ata_generic
[   58.798645] scsi1 : ata_generic
[   58.799385] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   58.799387] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   59.282401] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB02, max UDMA/66
[   59.282414] ata2.00: configured for UDMA/66
[   59.283056] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB02 PQ: 0 ANSI: 5
[   60.373720] fuse init (API version 7.9)
[   60.641767] usbcore: registered new interface driver usbfs
[   60.641784] usbcore: registered new interface driver hub
[   60.641861] sata_nv 0000:00:0e.0: version 3.5
[   60.642109] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[   60.642117] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 16
[   60.642164] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   60.642214] usbcore: registered new device driver usb
[   60.642226] scsi2 : sata_nv
[   60.642260] scsi3 : sata_nv
[   60.642350] ata3: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 16
[   60.642352] ata4: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 16
[   60.650207] Floppy drive(s): fd0 is 1.44M
[   60.672246] FDC 0 is a post-1991 82077
[   60.673601] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   60.955382] ata3: SATA link down (SStatus 0 SControl 300)
[   61.430628] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   61.454940] ata4.00: ATA-7: Hitachi HDT725032VLA360, V54OA7EA, max UDMA/133
[   61.454943] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   61.470915] ata4.00: configured for UDMA/133
[   61.470994] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDT72503 V54O PQ: 0 ANSI: 5
[   61.471279] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[   61.471283] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 22 (level, low) -> IRQ 17
[   61.471310] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   61.471341] scsi4 : sata_nv
[   61.471372] scsi5 : sata_nv
[   61.471463] ata5: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 17
[   61.471465] ata6: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 17
[   61.714153] end_request: I/O error, dev fd0, sector 0
[   61.786022] ata5: SATA link down (SStatus 0 SControl 300)
[   62.105498] ata6: SATA link down (SStatus 0 SControl 300)
[   62.116420] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[   62.116424] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 21 (level, low) -> IRQ 18
[   62.116433] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   62.116435] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   62.116630] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   62.116644] ohci_hcd 0000:00:0b.0: irq 18, io mem 0xf9ffb000
[   62.121070] Driver 'sd' needs updating - please use bus_type methods
[   62.121132] sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   62.121141] sd 3:0:0:0: [sda] Write Protect is off
[   62.121142] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.121154] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   62.121185] sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   62.121192] sd 3:0:0:0: [sda] Write Protect is off
[   62.121194] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   62.121204] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   62.121207]  sda:
[   62.137713] sd 3:0:0:0: [sda] Attached SCSI disk
[   62.140719] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[   62.140733] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   62.175471] usb usb1: configuration #1 chosen from 1 choice
[   62.175488] hub 1-0:1.0: USB hub found
[   62.175494] hub 1-0:1.0: 8 ports detected
[   62.277553] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   62.277557] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 20 (level, low) -> IRQ 19
[   62.277564] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   62.277567] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   62.277584] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   62.277609] ehci_hcd 0000:00:0b.1: debug port 1
[   62.277614] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   62.277621] ehci_hcd 0000:00:0b.1: irq 19, io mem 0xf9ffac00
[   62.289694] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   62.289759] usb usb2: configuration #1 chosen from 1 choice
[   62.289774] hub 2-0:1.0: USB hub found
[   62.289778] hub 2-0:1.0: 8 ports detected
[   62.393116] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   62.393334] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   62.393336] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 16
[   62.393340] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   62.744467] end_request: I/O error, dev fd0, sector 0
[   62.804855] usb 2-5: new high speed USB device using ehci_hcd and address 2
[   62.912844] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:85:5a:5f:db
[   62.912847] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   62.919121] Driver 'sr' needs updating - please use bus_type methods
[   62.923706] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   62.923708] Uniform CD-ROM driver Revision: 3.20
[   62.923740] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   62.938907] usb 2-5: configuration #1 chosen from 1 choice
[   63.175748] usb 2-8: new high speed USB device using ehci_hcd and address 3
[   63.311570] usb 2-8: configuration #1 chosen from 1 choice
[   63.312119] usbcore: registered new interface driver libusual
[   63.315294] Initializing USB Mass Storage driver...
[   63.315344] scsi6 : SCSI emulation for USB Mass Storage devices
[   63.315376] usb-storage: device found at 2
[   63.315378] usb-storage: waiting for device to settle before scanning
[   63.315401] scsi7 : SCSI emulation for USB Mass Storage devices
[   63.315429] usb-storage: device found at 3
[   63.315430] usb-storage: waiting for device to settle before scanning
[   63.315434] usbcore: registered new interface driver usb-storage
[   63.315436] USB Mass Storage support registered.
[   63.794749] end_request: I/O error, dev fd0, sector 0
[   68.303543] usb-storage: device scan complete
[   68.304551] scsi 6:0:0:0: Direct-Access     TEAM     USB_DRIVE        1.00 PQ: 0 ANSI: 2
[   68.304569] usb-storage: device scan complete
[   68.306933] scsi 7:0:0:0: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[   68.307903] sd 6:0:0:0: [sdb] 15937536 512-byte hardware sectors (8160 MB)
[   68.308782] scsi 7:0:0:1: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[   68.309779] sd 6:0:0:0: [sdb] Write Protect is off
[   68.309781] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   68.309782] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   68.309786] scsi 7:0:0:2: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[   68.310910] scsi 7:0:0:3: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0 CCS
[   68.311783] scsi 7:0:0:4: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[   68.317387] sd 6:0:0:0: [sdb] 15937536 512-byte hardware sectors (8160 MB)
[   68.320256] sd 6:0:0:0: [sdb] Write Protect is off
[   68.320258] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   68.320259] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   68.320261]  sdb: sdb1
[   68.322419] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   68.322444] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   68.325405] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   68.325428] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   68.329524] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[   68.329548] sd 7:0:0:1: Attached scsi generic sg4 type 0
[   68.333398] sd 7:0:0:2: [sde] Attached SCSI removable disk
[   68.333426] sd 7:0:0:2: Attached scsi generic sg5 type 0
[   68.336400] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[   68.336432] sd 7:0:0:3: Attached scsi generic sg6 type 0
[   68.340379] sd 7:0:0:4: [sdg] Attached SCSI removable disk
[   68.340403] sd 7:0:0:4: Attached scsi generic sg7 type 0
[   72.951768] end_request: I/O error, dev fd0, sector 0
[   82.580017] end_request: I/O error, dev fd0, sector 0
[   92.228233] end_request: I/O error, dev fd0, sector 0
[  101.856482] end_request: I/O error, dev fd0, sector 0
[  111.504698] end_request: I/O error, dev fd0, sector 0
[  121.152912] end_request: I/O error, dev fd0, sector 0
[  130.801129] end_request: I/O error, dev fd0, sector 0
[  140.429378] end_request: I/O error, dev fd0, sector 0
[  150.077593] end_request: I/O error, dev fd0, sector 0
[  159.705842] end_request: I/O error, dev fd0, sector 0
[  169.334090] end_request: I/O error, dev fd0, sector 0
[  178.958345] end_request: I/O error, dev fd0, sector 0
[  188.586594] end_request: I/O error, dev fd0, sector 0
[  198.214842] end_request: I/O error, dev fd0, sector 0
[  207.843091] end_request: I/O error, dev fd0, sector 0
[  217.467346] end_request: I/O error, dev fd0, sector 0

```

---

### Post by ju2wheels on 2008-09-18
WOOOOOOOOOOOOOOOT!!!! Im doing hand stands right now. I finally got around to testing 64bit 8.0.4.1 just for the hell of it and its able to boot to the live CD. Sound works out of the box, which surprised me, and the ethernet appears to be too but I havent had a chance to test it.

Does any know what I would have to do to take advantage of my Nvidia card's advanced graphics. Ive never had a machine with a top noche graphics card that I really had to modify drivers for?

---


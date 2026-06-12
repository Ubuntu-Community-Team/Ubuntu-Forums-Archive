---
title: "Upgrade Dilemma"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by =Fus3= on 2009-09-28
Hewlo~

Okay, I had just upgraded from Ubuntu 8.10 to 9.04, right? Well, after restarting, on the login screen, the little box does not recognize any keystrokes or mouse movement! So now I'm stuck there and cannot enter my username so as to jack into my account. Any way to remedy this? I would prefer being able to get back on without reformatting or anything. :/ Oh yeah, and I'm positive it doesn't freeze either, since a line blinks on and off, taunting me as I punch in various key combinations and hope for the best! Well... thanks in advance.

---

### Post by tommcd on 2009-09-29
See if you can boot into recovery mode and run:
```
sudo dpkg-reconfigure console-setup
```
Then reboot.

---

### Post by =Fus3= on 2009-09-29
Yeah, I was able to boot into command line via recovery mode. Through some more handy, reliable Googling, however, I found that, upon reading the Xserver's list of things that were booting up at the login prompt, one of them failed: the hardware abstraction layer daemon. Anyways, I searched around for that little phrase and came across this string, which actually enabled my keyboard and mouse:

```
sudo /etc/init.d/dbus restart
```

...that seemed to do the trick, thankfully.

Regardless, thanks for trying to help out!

---

### Post by =Fus3= on 2009-09-29
Okay, two new errors to report:

*No sound in Jaunty
*Dbus still broken - gotta enter recovery mode and manually restart it to use my keyboard & mouse every time

Attempted to reinstall HAL and Dbus; didn't help. Solutions?

---

### Post by tommcd on 2009-09-30
Good job on figuring out that it was dbus not starting.
When you run "sudo /etc/init.d/dbus restart" does it give any messages about what is going on? I tried googling for this but the possible solutions seem to be all over the place. Also, when you boot Ubuntu edit the grub entry for Ubuntu and remove quiet and splash (hit "e" to edit your Ubuntu entry when you see grub come up, then hit "e" again over the kernel line and remove the words quiet and splash from the end). Then press "b" to boot. This will enable you to see each process that is starting or failing and may give a clue what needs to be fixed. Also check dmesg by running:
```
dmesg | less
```
so you can scroll through dmesg to hopefully find out what is going on.
As a quick and dirty work around, you could try adding "/etc/init.d/dbus restart" (without the quotes) to the /etc/rc.local file. Put it just above where it says "exit 0". This will force dbus to be restarted every time you boot. I just tried doing that on my laptop and everything seems to work, so it is safe enough.
EDIT: Before doing that, go to: system > administration > services. Hit the "unlock" button and enter your password. Then scroll down to the end where it has "System communication bus (dbus)". Make sure there is a check in the box. Then reboot and see if everything starts normally.

For the sound, try working your way through the troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by =Fus3= on 2009-09-30
I looked at Services and noticed that Dbus was already selected. I'll try editing the kernel now, though, and see if anything wrong shows up.
EDIT:
Tried editing the boot-up kernel in GRUB, eliminated splash and quiet, and I still got the error of "Cannot start hardware abstraction layer - make sure dbus is running." Also, it said that PulseAudio was disabled.

About dmesg | less - where do I enter that? Terminal?

Another question, is it normal that a glitchy picture of the wallpaper I'm using shows up before the GNOME login window appears? There are several black and red squares and it looks a bit malformed, I guess..

Did the guide to fix sound- to no avail. Hrm..

---

### Post by =Fus3= on 2009-09-30
More problems!..

*Hardware abstraction layer/HALD still fails, despite adding that new line to the /etc/rc.local via terminal
*Is it normal for the system to hang on a black screen for 25 seconds before the login window loads?
*STILL no sound. But, I'm *pretty* sure the ALSA AC97 driver is installed.
*For some odd reason, my eth0 was disabled after making the changes.

This is what I got when I entered dmesg | less in terminal:

```
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP W
ed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff60000 (usable)
[    0.000000]  BIOS-e820: 000000003ff60000 - 000000003ff77000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3ff60 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ff60000 (usable)
[    0.000000]  modified: 000000003ff60000 - 000000003ff77000 (ACPI data)
[    0.000000]  modified: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3ff60 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ff60000 (usable)
[    0.000000]  modified: 000000003ff60000 - 000000003ff77000 (ACPI data)
[    0.000000]  modified: 000000003ff77000 - 000000003ff79000 (ACPI NVS)
[    0.000000]  modified: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c8000 - 37fef61d
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fa461d
[    0.000000] Move RAMDISK from 00000000378c8000 - 0000000037fef61c to 0087d000 - 00fa461c
[    0.000000] ACPI: RSDP 000F6D70, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 3FF6A6CD, 004C (r1 IBM    TP-1R        3200  LTP        0)
[    0.000000] ACPI: FACP 3FF6A800, 00F4 (r3 IBM    TP-1R        3200 IBM         1)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080926]
[    0.000000] ACPI: DSDT 3FF6A9E7, C4D5 (r1 IBM    TP-1R        3200 MSFT  100000E)
[    0.000000] ACPI: FACS 3FF78000, 0040
[    0.000000] ACPI: SSDT 3FF6A9B4, 0033 (r1 IBM    TP-1R        3200 MSFT  100000E)
[    0.000000] ACPI: ECDT 3FF76EBC, 0052 (r1 IBM    TP-1R        3200 IBM         1)
[    0.000000] ACPI: TCPA 3FF76F0E, 0032 (r1 IBM    TP-1R        3200 PTL         1)
[    0.000000] ACPI: BOOT 3FF76FD8, 0028 (r1 IBM    TP-1R        3200  LTP        1)
[    0.000000] 139MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fa461d]      NEW RAMDISK ==> [000087d000 - 0000fa461d]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003ff60
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0003ff60
[    0.000000] On node 0 totalpages: 261861
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 279 pages used for memmap
[    0.000000]   HighMem zone: 35403 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf800000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259814
[    0.000000] Kernel command line: root=UUID=40f141fa-1ee3-40da-8453-5a6b1f487a46 ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1798.457 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5239680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1017928k/1047936k available (4116k kernel code, 29204k reserved, 2199k data, 532k init, 142728k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3596.91 BogoMIPS (lpj=7193828)
[    0.004098] Security Framework initialized
[    0.004138] SELinux:  Disabled at boot.
[    0.004190] AppArmor: AppArmor initialized
[    0.004230] Mount-cache hash table entries: 512
[    0.004397] Initializing cgroup subsys ns
[    0.004434] Initializing cgroup subsys cpuacct
[    0.004469] Initializing cgroup subsys memory
[    0.004505] Initializing cgroup subsys freezer
[    0.004553] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004608] CPU: L2 cache: 2048K
[    0.004651] Checking 'hlt' instruction... OK.
[    0.020743] SMP alternatives: switching to UP code
[    0.131054] Freeing SMP alternatives: 18k freed
[    0.131093] ACPI: Core revision 20080926
[    0.136713] ACPI: Checking initramfs for custom DSDT
[    0.471161] ACPI: setting ELCR to 0200 (from 0800)
[    0.472061] weird, boot CPU (#0) not listedby the BIOS.
[    0.472097] SMP motherboard not detected.
[    0.472132] Local APIC not detected. Using dummy APIC emulation.
[    0.472167] SMP disabled
[    0.472447] Brought up 1 CPUs
[    0.472481] Total of 1 processors activated (3596.91 BogoMIPS).
[    0.472527] CPU0 attaching NULL sched-domain.
[    0.472809] net_namespace: 776 bytes
[    0.472849] Booting paravirtualized kernel on bare hardware
[    0.473091] Time: 19:56:23  Date: 09/30/09
[    0.473129] regulator: core version 0.5
[    0.473194] NET: Registered protocol family 16
[    0.473352] EISA bus registered
[    0.473398] ACPI: bus type pci registered
[    0.473619] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    0.473656] PCI: Using configuration type 1 for base access
[    0.476676] ACPI: EC: EC description table is found, configuring boot EC
[    0.485176] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.492696] ACPI: Interpreter enabled
[    0.492732] ACPI: (supports S0 S3 S4 S5)
[    0.492863] ACPI: Using PIC for interrupt routing
[    0.504497] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.504535] ACPI: EC: driver started in interrupt mode
[    0.508502] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.508548] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.508624] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.508722] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.508770] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.508819] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.508874] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc0000000-0xc00003ff]
[    0.508916] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.508955] pci 0000:00:1d.7: PME# disabled
[    0.509063] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.509104] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.509151] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.509206] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.509213] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.509219] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.509226] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.509233] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.509240] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.509286] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.509325] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.509332] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.509338] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
[    0.509345] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
[    0.509366] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.509403] pci 0000:00:1f.5: PME# disabled
[    0.509463] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.509469] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.509497] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.509535] pci 0000:00:1f.6: PME# disabled
[    0.509601] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.509606] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.509612] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.509627] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.509636] pci 0000:01:00.0: supports D1 D2
[    0.509669] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.509673] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.509677] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.509710] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.509719] pci 0000:02:00.0: supports D1 D2
[    0.509722] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.509760] pci 0000:02:00.0: PME# disabled
[    0.509824] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.509834] pci 0000:02:00.1: supports D1 D2
[    0.509836] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.509874] pci 0000:02:00.1: PME# disabled
[    0.509943] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0240000-0xc025ffff]
[    0.509950] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.509957] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.509976] pci 0000:02:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.509985] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.510023] pci 0000:02:01.0: PME# disabled
[    0.510808] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc021ffff]
[    0.510877] pci 0000:00:1e.0: transparent bridge
[    0.510914] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.510919] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.510924] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.510961] bus 00 -> node 0
[    0.510969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.511029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.511057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.514657] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.515119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.515572] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.516036] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.516472] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.516957] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.517441] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.517943] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.518287] ACPI: Power Resource [PUBS] (on)
[    0.518287] ACPI: WMI: Mapper loaded
[    0.518287] SCSI subsystem initialized
[    0.518287] libata version 3.00 loaded.
[    0.518287] usbcore: registered new interface driver usbfs
[    0.518287] usbcore: registered new interface driver hub
[    0.518287] usbcore: registered new device driver usb
[    0.518287] PCI: Using ACPI for IRQ routing
[    0.518287] Bluetooth: Core ver 2.13
[    0.518287] NET: Registered protocol family 31
[    0.518287] Bluetooth: HCI device and connection manager initialized
[    0.518287] Bluetooth: HCI socket layer initialized
[    0.518287] NET: Registered protocol family 8
[    0.518287] NET: Registered protocol family 20
[    0.518287] NetLabel: Initializing
[    0.518287] NetLabel:  domain hash size = 128
[    0.518287] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.518287] NetLabel:  unlabeled traffic allowed by default
[    0.518287] AppArmor: AppArmor Filesystem Enabled
[    0.518287] pnp: PnP ACPI init
[    0.518287] ACPI: bus type pnp registered
[    0.524107] pnp: PnP ACPI: found 14 devices
[    0.524142] ACPI: ACPI bus type pnp unregistered
[    0.524177] PnPBIOS: Disabled by ACPI PNP
[    0.524218] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.524256] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.524293] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.524331] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.524368] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.524406] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.524443] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.524481] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.524518] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.524556] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.524593] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.524631] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.524668] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[    0.524714] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.524765] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.524802] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.524839] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.524876] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.524913] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.559632] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.559669] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.559706] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.559744] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
[    0.559795] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.559832] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.559869] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.559907] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.559945] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.559983] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.560028] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.560066] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.560103] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.560142] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.560180] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.560216] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.560255] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.560293] pci 0000:00:1e.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.560351] pci 0000:00:1e.0: setting latency timer to 64
[    0.560729] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.560766] PCI: setting IRQ 11 as level-triggered
[    0.560771] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.561184] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.561221] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.561270] bus: 00 index 0 io port: [0x00-0xffff]
[    0.561304] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.561340] bus: 01 index 0 io port: [0x3000-0x3fff]
[    0.561375] bus: 01 index 1 mmio: [0xc0100000-0xc01fffff]
[    0.561410] bus: 01 index 2 mmio: [0xe0000000-0xe7ffffff]
[    0.561445] bus: 01 index 3 mmio: [0x0-0x0]
[    0.561479] bus: 02 index 0 io port: [0x4000-0x8fff]
[    0.561514] bus: 02 index 1 mmio: [0xc0200000-0xcfffffff]
[    0.561549] bus: 02 index 2 mmio: [0xe8000000-0xefffffff]
[    0.561584] bus: 02 index 3 io port: [0x00-0xffff]
[    0.561619] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.561654] bus: 03 index 0 io port: [0x4000-0x40ff]
[    0.561688] bus: 03 index 1 io port: [0x4400-0x44ff]
[    0.561723] bus: 03 index 2 mmio: [0xe8000000-0xebffffff]
[    0.561759] bus: 03 index 3 mmio: [0xc4000000-0xc7ffffff]
[    0.561794] bus: 07 index 0 io port: [0x4800-0x48ff]
[    0.561828] bus: 07 index 1 io port: [0x4c00-0x4cff]
[    0.561863] bus: 07 index 2 mmio: [0xec000000-0xefffffff]
[    0.561898] bus: 07 index 3 mmio: [0xc8000000-0xcbffffff]
[    0.561940] NET: Registered protocol family 2
[    0.562077] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.562380] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.563312] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.563943] TCP: Hash tables configured (established 131072 bind 65536)
[    0.563982] TCP reno registered
[    0.564191] NET: Registered protocol family 1
[    0.564369] checking if image is initramfs... it is
[    1.060059] Switched to high resolution mode on CPU 0
[    1.238617] Freeing initrd memory: 7325k freed
[    1.238737] Simple Boot Flag at 0x35 set to 0x1
[    1.238805] cpufreq: No nForce2 chipset.
[    1.239009] audit: initializing netlink socket (disabled)
[    1.239076] type=2000 audit(1254340584.236:1): initialized
[    1.247238] highmem bounce pool size: 64 pages
[    1.247278] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.248701] VFS: Disk quotas dquot_6.5.1
[    1.248790] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.249455] fuse init (API version 7.10)
[    1.249572] msgmni has been set to 1724
[    1.249803] alg: No test for stdrng (krng)
[    1.249848] io scheduler noop registered
[    1.249881] io scheduler anticipatory registered
[    1.249915] io scheduler deadline registered
[    1.249962] io scheduler cfq registered (default)
[    1.250084] pci 0000:01:00.0: Boot video device
[    1.255943] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.255988] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.256469] ACPI: AC Adapter [AC] (on-line)
[    1.284128] ACPI: Battery Slot [BAT0] (battery present)
[    1.284232] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.284279] ACPI: Power Button (FF) [PWRF]
[    1.284361] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.284772] ACPI: Lid Switch [LID]
[    1.284849] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.284897] ACPI: Sleep Button (CM) [SLPB]
[    1.287330] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.287468] processor ACPI_CPU:00: registered as cooling_device0
[    1.287506] ACPI: Processor [CPU] (supports 8 throttling states)
[    1.292682] thermal LNXTHERM:01: registered as thermal_zone0
[    1.294209] ACPI: Thermal Zone [THM0] (55 C)
[    1.294283] isapnp: Scanning for PnP cards...
[    1.647104] isapnp: No Plug & Play device found
[    1.648255] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.649106] serial 00:0a: activated
[    1.649223] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    1.649372] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.649440] serial 0000:00:1f.6: PCI INT B disabled
[    1.650141] brd: module loaded
[    1.650485] loop: module loaded
[    1.650588] Fixed MDIO Bus: probed
[    1.650626] PPP generic driver version 2.4.2
[    1.650713] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.650785] Driver 'sd' needs updating - please use bus_type methods
[    1.650829] Driver 'sr' needs updating - please use bus_type methods
[    1.650941] ata_piix 0000:00:1f.1: version 2.12
[    1.650948] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.651367] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    1.651404] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.651493] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.651584] scsi0 : ata_piix
[    1.651803] scsi1 : ata_piix
[    1.652893] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    1.652931] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    1.816532] ata1.00: ATA-7: Hitachi HTS541612J9AT00, SBDOA70H, max UDMA/100
[    1.816570] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.832464] ata1.00: configured for UDMA/100
[    1.996437] ata2.00: ATAPI: UJDA765 DVD/CDRW, 1.02, max UDMA/33
[    2.012415] ata2.00: configured for UDMA/33
[    2.012810] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    2.012956] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    2.013017] sd 0:0:0:0: [sda] Write Protect is off
[    2.013053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.013078] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.013905] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    2.013963] sd 0:0:0:0: [sda] Write Protect is off
[    2.013998] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.014022] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.014070]  sda: sda1 sda2 < sda5 >
[    2.054897] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.054970] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.056465] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA765 DVD/CDRW 1.02 PQ: 0 ANSI: 5
[    2.059467] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.059506] Uniform CD-ROM driver Revision: 3.20
[    2.059617] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.059651] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.060304] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.060985] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    2.061398] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.061435] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.061505] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.061508] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.061608] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.065554] ehci_hcd 0000:00:1d.7: debug port 1
[    2.065592] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.065601] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    2.080022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.080143] usb usb1: configuration #1 chosen from 1 choice
[    2.080205] hub 1-0:1.0: USB hub found
[    2.080246] hub 1-0:1.0: 6 ports detected
[    2.080394] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.080445] uhci_hcd: USB Universal Host Controller Interface driver
[    2.080871] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.080912] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.080962] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.080965] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.081044] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.081107] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    2.081217] usb usb2: configuration #1 chosen from 1 choice
[    2.081275] hub 2-0:1.0: USB hub found
[    2.081314] hub 2-0:1.0: 2 ports detected
[    2.081799] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    2.082212] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    2.082249] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.082299] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.082302] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.082376] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.082438] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    2.082544] usb usb3: configuration #1 chosen from 1 choice
[    2.082602] hub 3-0:1.0: USB hub found
[    2.082602] hub 3-0:1.0: USB hub found
[    2.082641] hub 3-0:1.0: 2 ports detected
[    2.082750] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.082800] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.082804] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.082876] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.082938] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    2.083040] usb usb4: configuration #1 chosen from 1 choice
[    2.083102] hub 4-0:1.0: USB hub found
[    2.083140] hub 4-0:1.0: 2 ports detected
[    2.083304] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.088927] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.088966] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.089103] mice: PS/2 mouse device common for all mice
[    2.089284] rtc_cmos 00:06: RTC can wake from S4
[    2.089353] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.089403] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    2.089498] device-mapper: uevent: version 1.0.3
[    2.089645] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.089737] device-mapper: multipath: version 1.0.5 loaded
[    2.089773] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.089882] EISA: Probing bus 0 at eisa.0
[    2.089920] Cannot allocate resource for EISA slot 1
[    2.089964] Cannot allocate resource for EISA slot 2
[    2.089999] Cannot allocate resource for EISA slot 3
[    2.090034] Cannot allocate resource for EISA slot 4
[    2.090068] Cannot allocate resource for EISA slot 5
[    2.090103] Cannot allocate resource for EISA slot 6
[    2.090138] Cannot allocate resource for EISA slot 7
[    2.090173] Cannot allocate resource for EISA slot 8
[    2.090214] EISA: Detected 0 cards.
[    2.090309] cpuidle: using governor ladder
[    2.090410] cpuidle: using governor menu
[    2.090937] TCP cubic registered
[    2.091071] NET: Registered protocol family 10
[    2.091501] lo: Disabled Privacy Extensions
[    2.091839] NET: Registered protocol family 17
[    2.091890] Bluetooth: L2CAP ver 2.11
[    2.091923] Bluetooth: L2CAP socket layer initialized
[    2.091958] Bluetooth: SCO (Voice Link) ver 0.6
[    2.091992] Bluetooth: SCO socket layer initialized
[    2.092067] Bluetooth: RFCOMM socket layer initialized
[    2.092107] Bluetooth: RFCOMM TTY layer initialized
[    2.092141] Bluetooth: RFCOMM ver 1.10
[    2.092607] IO APIC resources could be not be allocated.
[    2.092644] Using IPI No-Shortcut mode
[    2.092754] registered taskstats version 1
[    2.092892]   Magic number: 9:181:952
[    2.092945] tty tty9: hash matches
[    2.093030] rtc_cmos 00:06: setting system clock to 2009-09-30 19:56:25 UTC (1254340585)
[    2.093077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.093112] EDD information not available.
[    2.093505] Freeing unused kernel memory: 532k freed
[    2.093653] Write protecting the kernel text: 4120k
[    2.093725] Write protecting the kernel read-only data: 1524k
[    2.096457] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.283881] Floppy drive(s): fd0 is 1.44M
[    2.303174] FDC 0 is a National Semiconductor PC87306
[    2.332908] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    2.332952] Copyright (c) 1999-2006 Intel Corporation.
[    2.333046] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.586682] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:10:c6:df:87:7a
[    2.587137] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    2.621477] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.717931] usb 1-3: configuration #1 chosen from 1 choice
[    2.796522] Initializing USB Mass Storage driver...
[    2.797732] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.797979] usbcore: registered new interface driver usb-storage
[    2.798017] USB Mass Storage support registered.
[    2.798200] usb-storage: device found at 2
[    2.798202] usb-storage: waiting for device to settle before scanning
[    2.831673] Marking TSC unstable due to TSC halts in idle
[    2.859527] PM: Starting manual resume from disk
[    2.859564] PM: Resume from partition 8:5
[    2.859566] PM: Checking hibernation image.
[    2.859728] PM: Resume from disk failed.
[    2.863289] EXT3-fs: INFO: recovery required on readonly filesystem.
[    2.863327] EXT3-fs: write access will be enabled during recovery.
[    3.120051] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    3.297530] usb 3-2: configuration #1 chosen from 1 choice
[    3.306936] usbcore: registered new interface driver hiddev
[    3.321026] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    3.321312] generic-usb 0003:046D:C044.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2/input0
[    3.321377] usbcore: registered new interface driver usbhid
[    3.321413] usbhid: v2.6:USB HID core driver
[    4.094466] kjournald starting.  Commit interval 5 seconds
[    4.094519] EXT3-fs: recovery complete.
[    4.095110] EXT3-fs: mounted filesystem with ordered data mode.
[    7.796180] usb-storage: device scan complete
[    7.796666] scsi 2:0:0:0: Direct-Access     WD       2500BEV External 1.05 PQ: 0 ANSI: 4
[    7.797642] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    7.798514] sd 2:0:0:0: [sdb] Write Protect is off
[    7.798552] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    7.798554] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.799264] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    7.800139] sd 2:0:0:0: [sdb] Write Protect is off
[    7.800176] sd 2:0:0:0: [sdb] Mode Sense: 21 00 00 00
[    7.800178] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.800216]  sdb: sdb1
[    8.215690] sd 2:0:0:0: [sdb] Attached SCSI disk
[    8.215798] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   12.930918] udev: starting version 141
[   14.034153] parport_pc 00:0b: reported by Plug and Play ACPI
[   14.034242] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   14.111323] Non-volatile memory driver v1.2
[   14.136286] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.234205] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.297490] ppdev: user-space parallel port driver
[   14.353234] intel_rng: FWH not detected
[   14.371996] Linux agpgart interface v0.103
[   14.388972] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input7
[   14.391933] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   14.507798] cfg80211: Calling CRDA to update world regulatory domain
[   14.538548] irda_init()
[   14.538559] NET: Registered protocol family 23
[   14.583692] cfg80211: World regulatory domain updated:
[   14.583730]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.583776]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.583814]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.583851]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.583888]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.583925]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.585655] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.617045] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[   14.617099] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   14.617145] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   14.617184] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[   14.659514] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   14.673590] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.691683] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.691723] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.691758] thinkpad_acpi: ThinkPad BIOS 1RETDOWW (3.20 ), EC 1RHT71WW-3.04
[   14.691795] thinkpad_acpi: IBM ThinkPad T42, model 2379RFU
[   14.696372] Registered led device: tpacpi::thinklight
[   14.696645] Registered led device: tpacpi::power
[   14.696717] Registered led device: tpacpi:orange:batt
[   14.696787] Registered led device: tpacpi:green:batt
[   14.696861] Registered led device: tpacpi::dock_active
[   14.696931] Registered led device: tpacpi::bay_active
[   14.697002] Registered led device: tpacpi::dock_batt
[   14.697074] Registered led device: tpacpi::unknown_led
[   14.697158] Registered led device: tpacpi::standby
[   14.704067] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   14.788451] iTCO_vendor_support: vendor-support=0
[   14.790629] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.790790] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.790906] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.848893] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
[   14.848939] yenta_cardbus 0000:02:00.0: Socket status: 30000086
[   14.848979] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   14.849027] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   14.850326] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   14.850375] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   14.850765] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[   14.850816] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   14.850862] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   14.850901] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[   14.872976] nsc-ircc 00:0c: activated
[   14.873013] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   14.873179] nsc-ircc, chip->init
[   14.873218] nsc-ircc, Found chip at base=0x02e
[   14.873273] nsc-ircc, driver loaded (Dag Brattli)
[   14.874028] IrDA: Registered device irda0
[   14.874063] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   15.083554] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   15.083711] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.084622] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[   15.084661] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[   15.084701] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   15.084749] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   15.085947] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   15.085995] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   15.087406] ath5k_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   15.087501] ath5k_pci 0000:02:02.0: registered as 'phy0'
[   15.125565] phy0: Selected rate control algorithm 'pid'
[   15.227824] Registered led device: ath5k-phy0::rx
[   15.227906] Registered led device: ath5k-phy0::tx
[   15.227942] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
[   15.227980] ath5k phy0: RF5112B multiband radio found (0x36)
[   15.232460] udev: renamed network interface wlan0 to ath0
[   15.253674] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   15.254725] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.255252] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   15.255674] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   15.256252] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   15.487872] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   15.487921] serio: Synaptics pass-through port at isa0060/serio1/input0
[   15.530795] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   15.652879] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.653946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.654473] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.654896] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.655454] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.008028] intel8x0_measure_ac97_clock: measured 55424 usecs
[   16.008074] intel8x0: clocking to 48000
[   16.099481] lp0: using parport0 (interrupt-driven).
[   16.216090] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   16.602235] EXT3 FS on sda1, internal journal
[   16.710450] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   17.020177] type=1505 audit(1254340600.426:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2099
[   17.075940] type=1505 audit(1254340600.478:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2103
[   17.076107] type=1505 audit(1254340600.482:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2103
[   17.076160] type=1505 audit(1254340600.482:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2103
[   17.076207] type=1505 audit(1254340600.482:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2103
[   17.243115] type=1505 audit(1254340600.646:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2108
[   17.243439] type=1505 audit(1254340600.646:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2108
[   17.275442] type=1505 audit(1254340600.678:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2112
[   18.204355] psmouse serio2: ID: 10 00 64<6>IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.813515] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input10
[   65.941642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.941645] Bluetooth: BNEP filters: protocol multicast
[   66.073482] Bridge firewalling registered
[   67.056437] pci 0000:01:00.0: power state changed by ACPI to D0
[   67.056449] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   67.609266] [drm] Initialized drm 1.1.0 20060810
[   67.803156] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   68.072412] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   68.072431] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   68.072466] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   68.491487] [drm] Setting GART location based on new memory map
[   68.491495] [drm] Loading R200 Microcode
[   68.491551] [drm] writeback test succeeded in 2 usecs
[   72.595809] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   72.596389] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   72.626505] ADDRCONF(NETDEV_UP): ath0: link is not ready
[   72.626722] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   82.287030] ath0: authenticate with AP 00:13:10:f3:c8:b7
[   82.288471] ath0: authenticated
[   82.288474] ath0: associate with AP 00:13:10:f3:c8:b7
[   82.294375] ath0: RX AssocResp from 00:13:10:f3:c8:b7 (capab=0x401 status=0 aid=1)
[   82.294379] ath0: associated
[   82.294849] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   82.636022] eth0: no IPv6 routers present
[   92.740024] ath0: no IPv6 routers present
[  131.556041] Clocksource tsc unstable (delta = -141320963 ns)
[  282.240148] e1000: eth0: e1000_watchdog: NIC Link is Down
[  284.388411] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
(END)
```

---

### Post by tommcd on 2009-10-01
> **=Fus3= said:**
> 
*Is it normal for the system to hang on a black screen for 25 seconds before the login window loads?
No it is not.
> **=Fus3= said:**
> 
*For some odd reason, my eth0 was disabled after making the changes.
If your eth0 was disabled after adding /etc/init.d/dbus restart to /etc/rc.local then remove that line from rc.local. 
> **=Fus3= said:**
> 
This is what I got when I entered dmesg | less in terminal...

I didn't see anything failing in dmesg. In case you are wondering, dmesg is a record of the boot messages as the kernel loads everything. I'm not sure what else you could try short of a clean install of 9.04.

---

### Post by =Fus3= on 2009-10-01
Looks as if I'm going to have to take your advice and reinstall Jaunty. It's a shame we couldn't get to the *root* of the problem, though.

Dohohohoho!

---


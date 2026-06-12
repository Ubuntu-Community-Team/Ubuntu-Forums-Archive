---
title: "Jan 28th, 2009 Updates Caused a Kernel Panic"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by em4r1z on 2009-01-28
A couple of hours ago I updated my system, it was up to date thus the updates available were a new kernel (linux-generic, linux-headers, etc.) and gnome-power-manager. After the update, I rebooted the system and lost access to the X server. I tried the former kernel (I only kept one) in both normal and recovery modes with no luck. As the system was mounted as read-only no matter what kernel or mode I tried, I couldn't run apt-get/aptitude to reinstall the NVIDIA drivers (where I think the problem lies.)

I used a live CD to visit this forum and check for possible workarounds and after a couple of restarts the system freezes during the booting stating there's a kernel panic due to 'not syncing - attempted to kill init!'.

Mine is an AMD64 Sempron Mobile 3500+ system with an NVIDIA GeForce Go 6100 video card using Ubuntu 8.10 64bit with the latest NVIDIA drivers provided by Ubuntu.

I already backed up the folders I needed. Any ideas on how to recover my system?

---

### Post by Pumalite on 2009-01-28
What about Recovery Mode of the latest kernel? Use 'xfix', then 'resume booting'

---

### Post by em4r1z on 2009-01-28
No matter what kernel or mode I try, there's a kernel panic. If I load any kernel in normal mode, the system freezes a few seconds after the booting process and the laptop leds light up. If I load any kernel in recovery mode, the 'kernel panic - not syncing - attempted to kill init' notification appears and the system freezes.

I searched the kernel panic message and it seems to be RAM-related, however I can run live CD's with no problem and the system sees the 2 Gb of RAM (running Conky and using the 'free' command.)

I tried the 'xfix' option before (when the problem was limited to not loading the X server) with both kernels with no luck.

---

### Post by drlmg on 2009-01-29
Same thing here...'kernel panic - not syncing - attempted to kill init' after an update. I too have NVIDEA chipset.

I had just taken 8.10 off my laptop and re-installed 8.042 due to issues I was unable to correct. I had done a lot of work (about 1 1/2 hrs.) on it tweaking and customizing...however I had not done a backup yet because I had not finished tweaking / customizing. Could someone tell me what folders/files I need to copy (ones I can simply take and overwrite the fresh install with) so as to preserve as much of the work as possible?

The only way I can boot is to run a live version.

Thank You.

---

### Post by dpolishannu on 2009-01-29
Does kernel panic mean, that I et only white screen when I should et login screen...

I have 8.10 64bit ubuntu installed.

Amd Athlon 64 X2 dual core 4800+

motherboard is asus m2a-vm, this have that annoying aperture size error on bootup, can not handle but 3.3Gb of memory.

Just updated upgrades (very latest, cause i update every/every other day) and booted the computer, and when should get login screen, I get white screen. I have ATI/AMD proprietary FGLRX graphics driver installed.

I can start my ubuntu with previous kernel. The list when I start my ubuntu... just select kernel 2.6.27-9-generic, the newest is 2.6.27-11-generic.

I am more than happy to post any logs, if I only know what and where and how.

Integrated graphics is ati radeon x1250, I use dvi output.

---

### Post by dambrow on 2009-01-29
i have had the same problem but i am using pentium 3 prosessor (1 ghz) with 280mbs of ram and a 40gb hard drive. i had to reinstall linux on my system but took 10 attempts after i dissconected one of my internal hard drives and setting the one inside to master from slave before i got a message saying that DISK BOOT ERROR INSERT SYSTEM DISK AND PRESS ENTER TO CONTINUE. i have also got a copy of windows but the disk will not boot i had to go though a perious installation of windows to do but i have accidently wiped windows i cant do it now help on why this happen i had only just installed linux at the time turned the pc off and back on got the message that it was killing help

---

### Post by em4r1z on 2009-01-29
Since I'd never experienced a kernel panic, I don't know how difficult it is to recover from one. Is a reinstall the only solution to my problem? I hate reinstalling but this is my main system and I cannot do without it any longer.

---

### Post by Tux Aubrey on 2009-01-29
Just confirming a fatal kernel panic after the latest kernel upgrade on an Acer One netbook running Xubuntu.  Safe mode also fails with the same error.  Reverting to the previous kernel worked OK for me.

---

### Post by Number13 on 2009-01-29
> **Tux Aubrey said:**
> Just confirming a fatal kernel panic after the latest kernel upgrade on an Acer One netbook running Xubuntu.  Safe mode also fails with the same error.  Reverting to the previous kernel worked OK for me.

I have the same PC and OS, and the same solution worked for me too.

---

### Post by em4r1z on 2009-01-29
I had to reinstall to get a working system. I'm currently using the 2.26.27-11 kernel on an AMD64 system with an NVIDIA chipset, and I've found these problems:

- While I can access the Internet, the Network Manager cannot administer the ethernet adapter.
- I cannot start the X server if I use the NVIDIA drivers (180.)

Since the ethernet adapter is controlled by the NVIDIA chipset, I guess both problems are related. Any leads on how to solve them?
Can I install an older kernel (27-9) and remove the latest one?

---

### Post by Pumalite on 2009-01-30
Post:
```
dmesg
```

---

### Post by sledhead45 on 2009-01-31
same exact problem for me on a dell m1330. I've since tried mounting the drive in the livecd and chmodding to it (per [these]("http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html") directions), but i always get the error:

```
chroot: cannot run command '/bin/bash': No such file or directory
```

Trying to load an older kernel from grub didn't work for me.Is this really going to require a reformat to fix? not cool.

---

### Post by em4r1z on 2009-01-31
**Pumalite**, I attached the output of 'dmesg'. There are plenty of *errors* I didn't know my system had.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] Command line: root=UUID=2ea0756f-8a46-4b20-8a3d-de4594addea4 ro quiet splash elevator=deadline
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000006ffd0000 - 000000006ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ffde000 - 0000000070000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x6ffd0 max_arch_pfn = 0x3ffffffff
[    0.000000] mtrr: your BIOS has set up an incorrect mask, fixing it up.
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 006fe00000 page 2M
[    0.000000]  006fe00000 - 006ffd0000 page 4k
[    0.000000] kernel direct mapping tables up to 6ffd0000 @ 10000-14000
[    0.000000] last_map_addr: 6ffd0000 end: 6ffd0000
[    0.000000] RAMDISK: 377e7000 - 37fef5e7
[    0.000000] ACPI: RSDP 000F8C00, 0014 (r0 M S I )
[    0.000000] ACPI: RSDT 6FFD0000, 0044 (r1 MSI_NB MEGABOOK 10312007 MSFT       97)
[    0.000000] ACPI: FACP 6FFD0200, 0084 (r2 M S I  1632     10312007 MSFT       97)
[    0.000000] ACPI: DSDT 6FFD05C0, 4A4D (r1 M S I  1632            7 INTL 20051117)
[    0.000000] ACPI: FACS 6FFDE000, 0040
[    0.000000] ACPI: APIC 6FFD0390, 0070 (r1 M S I  OEMAPIC  10312007 MSFT       97)
[    0.000000] ACPI: MCFG 6FFD0400, 003C (r1 M S I  OEMMCFG  10312007 MSFT       97)
[    0.000000] ACPI: SLIC 6FFD0440, 0176 (r1 MSI_NB MEGABOOK 10312007 MSFT       97)
[    0.000000] ACPI: SLIC 6FFD0440, 0176 (r1 MSI_NB MEGABOOK 10312007 MSFT       97)
[    0.000000] ACPI: OEMB 6FFDE040, 0071 (r1 M S I  AMI_OEM  10312007 MSFT       97)
[    0.000000] ACPI: HPET 6FFD5010, 0038 (r1 M S I  OEMHPET0 10312007 MSFT       97)
[    0.000000] ACPI: SSDT 6FFD5050, 0129 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000006ffd0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000006ffd0000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  0000000000024fff] pages e
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 006ffd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b9f5c]    TEXT DATA BSS ==> [0000200000 - 00008b9f5c]
[    0.000000]   #3 [00377e7000 - 0037fef5e7]          RAMDISK ==> [00377e7000 - 0037fef5e7]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006ffd0
[    0.000000] On node 0 totalpages: 458591
[    0.000000]   DMA zone: 2095 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 447504 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 70000000:8ec00000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 449599
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=2ea0756f-8a46-4b20-8a3d-de4594addea4 ro quiet splash elevator=deadline
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1808.186 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 1480000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1790284k/1834816k available (3116k kernel code, 44080k reserved, 1575k data, 540k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.37 BogoMIPS (lpj=7232744)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] tseg: 0000000000
[    0.004000] using C1E aware idle routine
[    0.004000] SMP alternatives: switching to UP code
[    0.008011] ACPI: Core revision 20080609
[    0.009587] ACPI: Checking initramfs for custom DSDT
[    0.372179] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.411878] CPU0: Mobile AMD Sempron(tm) Processor 3500+ stepping 02
[    0.411883] Using local APIC timer interrupts.
[    0.412027] APIC timer calibration result 12556877
[    0.412029] Detected 12.556 MHz APIC timer.
[    0.412106] Brought up 1 CPUs
[    0.412108] Total of 1 processors activated (3616.37 BogoMIPS).
[    0.412198] CPU0 attaching NULL sched-domain.
[    0.412493] net_namespace: 1552 bytes
[    0.412498] Booting paravirtualized kernel on bare hardware
[    0.412679] Time: 21:22:23  Date: 01/31/09
[    0.412715] NET: Registered protocol family 16
[    0.413037] node 0 link 0: io port [1000, ffffff]
[    0.413041] TOM: 0000000080000000 aka 2048M
[    0.413044] node 0 link 0: mmio [e0000000, efffffff]
[    0.413047] node 0 link 0: mmio [a0000, bffff]
[    0.413050] node 0 link 0: mmio [80000000, fe0bffff]
[    0.413053] bus: [00,ff] on node 0 link 0
[    0.413056] bus: 00 index 0 io port: [0, ffff]
[    0.413058] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.413060] bus: 00 index 2 mmio: [a0000, bffff]
[    0.413070] ACPI: bus type pci registered
[    0.413180] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.413183] PCI: Not using MMCONFIG.
[    0.413185] PCI: Using configuration type 1 for base access
[    0.414932] ACPI: EC: Look up EC in DSDT
[    0.423295] ACPI: Interpreter enabled
[    0.423299] ACPI: (supports S0 S1 S3 S4 S5)
[    0.423318] ACPI: Using IOAPIC for interrupt routing
[    0.423393] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.427914] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.442719] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.453638] ACPI: EC: GPE = 0x5c, I/O: command/status = 0x66, data = 0x62
[    0.453641] ACPI: EC: driver started in poll mode
[    0.453794] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.454060] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454063] pci 0000:00:03.0: PME# disabled
[    0.454077] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.454083] PCI: 0000:00:05.0 reg 14 64bit mmio: [d0000000, dfffffff]
[    0.454088] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fa000000, faffffff]
[    0.454093] PCI: 0000:00:05.0 reg 30 32bit mmio: [f9fe0000, f9ffffff]
[    0.454299] PCI: 0000:00:0a.1 reg 20 io port: [5000, 503f]
[    0.454304] PCI: 0000:00:0a.1 reg 24 io port: [6000, 603f]
[    0.454323] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.454328] pci 0000:00:0a.1: PME# disabled
[    0.454356] PCI: 0000:00:0a.3 reg 10 32bit mmio: [f9f80000, f9fbffff]
[    0.454440] PCI: 0000:00:0b.0 reg 10 32bit mmio: [f9fde000, f9fdefff]
[    0.454465] pci 0000:00:0b.0: supports D1
[    0.454467] pci 0000:00:0b.0: supports D2
[    0.454469] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454472] pci 0000:00:0b.0: PME# disabled
[    0.454494] PCI: 0000:00:0b.1 reg 10 32bit mmio: [f9fdfc00, f9fdfcff]
[    0.454520] pci 0000:00:0b.1: supports D1
[    0.454522] pci 0000:00:0b.1: supports D2
[    0.454524] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454527] pci 0000:00:0b.1: PME# disabled
[    0.454559] PCI: 0000:00:0d.0 reg 20 io port: [ffa0, ffaf]
[    0.454595] PCI: 0000:00:0e.0 reg 10 io port: [e800, e807]
[    0.454600] PCI: 0000:00:0e.0 reg 14 io port: [e480, e483]
[    0.454604] PCI: 0000:00:0e.0 reg 18 io port: [e400, e407]
[    0.454609] PCI: 0000:00:0e.0 reg 1c io port: [e080, e083]
[    0.454613] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.454618] PCI: 0000:00:0e.0 reg 24 32bit mmio: [f9fdd000, f9fddfff]
[    0.454654] PCI: 0000:00:0f.0 reg 10 io port: [dc00, dc07]
[    0.454659] PCI: 0000:00:0f.0 reg 14 io port: [d880, d883]
[    0.454663] PCI: 0000:00:0f.0 reg 18 io port: [d800, d807]
[    0.454668] PCI: 0000:00:0f.0 reg 1c io port: [d480, d483]
[    0.454672] PCI: 0000:00:0f.0 reg 20 io port: [d400, d40f]
[    0.454677] PCI: 0000:00:0f.0 reg 24 32bit mmio: [f9fdc000, f9fdcfff]
[    0.454743] PCI: 0000:00:10.1 reg 10 32bit mmio: [f9fd8000, f9fdbfff]
[    0.454771] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.454775] pci 0000:00:10.1: PME# disabled
[    0.454800] PCI: 0000:00:14.0 reg 10 32bit mmio: [f9fd7000, f9fd7fff]
[    0.454805] PCI: 0000:00:14.0 reg 14 io port: [d080, d087]
[    0.454826] pci 0000:00:14.0: supports D1
[    0.454827] pci 0000:00:14.0: supports D2
[    0.454829] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454833] pci 0000:00:14.0: PME# disabled
[    0.454931] PCI: bridge 0000:00:03.0 io port: [b000, bfff]
[    0.454934] PCI: bridge 0000:00:03.0 32bit mmio: [fc000000, feafffff]
[    0.454965] PCI: 0000:04:04.0 reg 10 32bit mmio: [febfd000, febfdfff]
[    0.454971] PCI: 0000:04:04.0 reg 14 32bit mmio: [febfe000, febfe7ff]
[    0.454999] pci 0000:04:04.0: supports D1
[    0.455000] pci 0000:04:04.0: supports D2
[    0.455002] pci 0000:04:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.455006] pci 0000:04:04.0: PME# disabled
[    0.455031] PCI: 0000:04:04.2 reg 10 32bit mmio: [febfec00, febfecff]
[    0.455066] pci 0000:04:04.2: supports D1
[    0.455067] pci 0000:04:04.2: supports D2
[    0.455069] pci 0000:04:04.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.455073] pci 0000:04:04.2: PME# disabled
[    0.455097] PCI: 0000:04:04.3 reg 10 32bit mmio: [febff000, febfffff]
[    0.455132] pci 0000:04:04.3: supports D1
[    0.455134] pci 0000:04:04.3: supports D2
[    0.455136] pci 0000:04:04.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.455140] pci 0000:04:04.3: PME# disabled
[    0.455170] PCI: 0000:04:09.0 reg 10 32bit mmio: [febf0000, febf7fff]
[    0.455224] pci 0000:00:10.0: transparent bridge
[    0.455229] PCI: bridge 0000:00:10.0 32bit mmio: [feb00000, febfffff]
[    0.455243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.455690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.455934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.471416] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.471725] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.472039] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *10
[    0.472344] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.472649] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.472954] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.473260] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *10
[    0.473565] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.473871] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *7
[    0.474176] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *14
[    0.474482] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.474786] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.475090] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.475396] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.475705] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[    0.476019] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *11
[    0.476357] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.476667] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[    0.477034] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.477307] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.477344] pnp: PnP ACPI init
[    0.477353] ACPI: bus type pnp registered
[    0.482133] pnp: PnP ACPI: found 13 devices
[    0.482136] ACPI: ACPI bus type pnp unregistered
[    0.482517] PCI: Using ACPI for IRQ routing
[    0.492086] NET: Registered protocol family 8
[    0.492088] NET: Registered protocol family 20
[    0.492125] NetLabel: Initializing
[    0.492127] NetLabel:  domain hash size = 128
[    0.492129] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492144] NetLabel:  unlabeled traffic allowed by default
[    0.492336] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.492341] hpet0: 3 32-bit timers, 25000000 Hz
[    0.494710] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.494712]    actual entries 65586
[    0.494854] AppArmor: AppArmor Filesystem Enabled
[    0.494883] ACPI: RTC can wake from S4
[    0.496048] Switched to high resolution mode on CPU 0
[    0.504041] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.504050] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.504053] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.504056] system 00:08: ioport range 0x4000-0x407f has been reserved
[    0.504063] system 00:08: ioport range 0x4080-0x40ff has been reserved
[    0.504066] system 00:08: ioport range 0x4400-0x447f has been reserved
[    0.504069] system 00:08: ioport range 0x4480-0x44ff has been reserved
[    0.504072] system 00:08: ioport range 0x4800-0x487f has been reserved
[    0.504075] system 00:08: ioport range 0x4880-0x48ff has been reserved
[    0.504077] system 00:08: ioport range 0x2000-0x207f has been reserved
[    0.504080] system 00:08: ioport range 0x2080-0x20ff has been reserved
[    0.504084] system 00:08: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.504092] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.504095] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.504104] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.504111] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.504114] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.504117] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.504120] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.504123] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.509233] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.509236] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.509240] pci 0000:00:03.0:   MEM window: 0xfc000000-0xfeafffff
[    0.509243] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.509247] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.509249] pci 0000:00:10.0:   IO window: disabled
[    0.509252] pci 0000:00:10.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.509255] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.509265] pci 0000:00:03.0: enabling device (0000 -> 0003)
[    0.509270] pci 0000:00:03.0: setting latency timer to 64
[    0.509275] pci 0000:00:10.0: setting latency timer to 64
[    0.509278] bus: 00 index 0 io port: [0, ffff]
[    0.509280] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.509283] bus: 01 index 0 io port: [b000, bfff]
[    0.509285] bus: 01 index 1 mmio: [fc000000, feafffff]
[    0.509287] bus: 01 index 2 mmio: [0, 0]
[    0.509289] bus: 01 index 3 mmio: [0, 0]
[    0.509291] bus: 04 index 0 mmio: [0, 0]
[    0.509292] bus: 04 index 1 mmio: [feb00000, febfffff]
[    0.509294] bus: 04 index 2 mmio: [0, 0]
[    0.509296] bus: 04 index 3 io port: [0, ffff]
[    0.509298] bus: 04 index 4 mmio: [0, ffffffffffffffff]
[    0.509313] NET: Registered protocol family 2
[    0.548124] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.549006] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.551024] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.551544] TCP: Hash tables configured (established 262144 bind 65536)
[    0.551547] TCP reno registered
[    0.560106] NET: Registered protocol family 1
[    0.560240] checking if image is initramfs... it is
[    1.418051] Freeing initrd memory: 8225k freed
[    1.423465] audit: initializing netlink socket (disabled)
[    1.423481] type=2000 audit(1233436943.420:1): initialized
[    1.429940] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.432540] VFS: Disk quotas dquot_6.5.1
[    1.432639] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.432754] msgmni has been set to 3512
[    1.432899] io scheduler noop registered
[    1.432901] io scheduler anticipatory registered
[    1.432904] io scheduler deadline registered (default)
[    1.433031] io scheduler cfq registered
[    1.433047] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.433085] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.433094] pci 0000:00:05.0: Boot video device
[    1.433115] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.433184] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.433196] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.433206] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.433218] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.433349] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.433372] pcieport-driver 0000:00:03.0: found MSI capability
[    1.433395] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.433442] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.472340] hpet_resources: 0xfed00000 is busy
[    1.472419] Linux agpgart interface v0.103
[    1.472424] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.474740] brd: module loaded
[    1.474821] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.474952] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.475307] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.475393] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.475398] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.475401] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.475403] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.475406] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.484293] mice: PS/2 mouse device common for all mice
[    1.484432] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.484469] rtc0: alarms up to one year, y3k, hpet irqs
[    1.484511] cpuidle: using governor ladder
[    1.484513] cpuidle: using governor menu
[    1.484972] TCP cubic registered
[    1.485211] registered taskstats version 1
[    1.485383]   Magic number: 9:350:400
[    1.485538] rtc_cmos 00:02: setting system clock to 2009-01-31 21:22:24 UTC (1233436944)
[    1.485541] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.485543] EDD information not available.
[    1.485589] Freeing unused kernel memory: 540k freed
[    1.485871] Write protecting the kernel read-only data: 4352k
[    1.490202] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.600823] fuse init (API version 7.9)
[    1.621371] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.621436] processor ACPI0007:00: registered as cooling_device0
[    1.623877] thermal LNXTHERM:01: registered as thermal_zone0
[    1.624132] ACPI: Thermal Zone [THRM] (75 C)
[    2.276893] usbcore: registered new interface driver usbfs
[    2.276920] usbcore: registered new interface driver hub
[    2.284076] usbcore: registered new device driver usb
[    2.286110] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.286633] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    2.286645] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    2.286658] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.286662] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.286713] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.286748] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf9fde000
[    2.296179] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.306974] No dock devices found.
[    2.342180] usb usb1: configuration #1 chosen from 1 choice
[    2.342210] hub 1-0:1.0: USB hub found
[    2.342221] hub 1-0:1.0: 8 ports detected
[    2.352488] SCSI subsystem initialized
[    2.420062] libata version 3.00 loaded.
[    2.444955] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    2.444968] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    2.444982] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.444986] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.445014] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.445048] ehci_hcd 0000:00:0b.1: debug port 1
[    2.445052] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.445079] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xf9fdfc00
[    2.456101] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.456261] usb usb2: configuration #1 chosen from 1 choice
[    2.456291] hub 2-0:1.0: USB hub found
[    2.456300] hub 2-0:1.0: 8 ports detected
[    2.560369] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.560876] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    2.560889] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    2.560895] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.560928] nv_probe: set workaround bit for reversed mac addr
[    3.080781] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:db:3e:26:97
[    3.080786] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    3.081770] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[    3.081783] ohci1394 0000:04:04.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[    3.131560] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febfd000-febfd7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    3.137410] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.137929] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 20
[    3.137941] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.137959] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.137968] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.138407] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 23
[    3.138411] pata_acpi 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 23 (level, low) -> IRQ 23
[    3.138428] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    3.138437] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    3.143224] sata_nv 0000:00:0e.0: version 3.5
[    3.143239] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 20 (level, low) -> IRQ 20
[    3.143242] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.143291] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.146202] scsi0 : sata_nv
[    3.149925] scsi1 : sata_nv
[    3.150180] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe000 irq 20
[    3.150184] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[    3.616086] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.671162] ata1.00: ATA-7: WDC WD800BEVS-22RST0, 04.01G04, max UDMA/133
[    3.671165] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.684442] ata1.00: configured for UDMA/133
[    3.996089] isa bounce pool size: 16 pages
[    3.996158] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-22 04.0 PQ: 0 ANSI: 5
[    3.997784] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 23 (level, low) -> IRQ 23
[    3.997788] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    3.997834] sata_nv 0000:00:0f.0: setting latency timer to 64
[    3.997959] scsi2 : sata_nv
[    3.999037] scsi3 : sata_nv
[    3.999258] ata3: SATA max UDMA/133 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 23
[    3.999262] ata4: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 23
[    4.405329] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc1000a3c41d01]
[    4.620663] pata_amd 0000:00:0d.0: version 0.3.10
[    4.620715] pata_amd 0000:00:0d.0: setting latency timer to 64
[    4.627489] scsi4 : pata_amd
[    4.630883] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.635298] scsi5 : pata_amd
[    4.637866] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.637869] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.637902] ata5: port disabled. ignoring.
[    4.658982] Driver 'sd' needs updating - please use bus_type methods
[    4.659090] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.659107] sd 0:0:0:0: [sda] Write Protect is off
[    4.659110] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.659136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.659208] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.659223] sd 0:0:0:0: [sda] Write Protect is off
[    4.659225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.659251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.659256]  sda: sda1 sda2 sda3
[    4.710450] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.800351] ata6.00: ATAPI: Optiarc DVD RW AD-7530B, NX02, max UDMA/33
[    4.800368] ata6: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc000) ACPI=0x701f (60:900:0x11)
[    4.816317] ata6.00: configured for UDMA/33
[    4.817593] scsi 5:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[    4.817771] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[    4.862627] Driver 'sr' needs updating - please use bus_type methods
[    4.873471] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.873477] Uniform CD-ROM driver Revision: 3.20
[    4.873582] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.366523] PM: Starting manual resume from disk
[    5.366527] PM: Resume from partition 8:1
[    5.366529] PM: Checking hibernation image.
[    5.366799] PM: Resume from disk failed.
[    5.373933] JFS: nTxBlock = 8192, nTxLock = 65536
[    8.505289] udevd version 124 started
[    9.532037] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.645372] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.734722] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    9.740222] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    9.740256] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[    9.768024] ACPI: Power Button (FF) [PWRF]
[    9.768161] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/PNP0C09:00/PNP0C0D:00/input/input3
[    9.768720] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.772864] ACPI: Lid Switch [LID0]
[    9.772977] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/PNP0C09:00/PNP0C0E:00/input/input4
[    9.784042] ACPI: Sleep Button (CM) [SLPB]
[    9.784201] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[    9.800026] ACPI: Power Button (CM) [PWRB]
[   10.908620] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/input/input6
[   10.920025] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.969184] ACPI: AC Adapter [ADP1] (on-line)
[   11.152247] ACPI: Battery Slot [BAT1] (battery present)
[   11.864137] sdhci: Secure Digital Host Controller Interface driver
[   11.864141] sdhci: Copyright(c) Pierre Ossman
[   11.901156] sdhci-pci 0000:04:04.2: SDHCI controller found [1217:7120] (rev 1)
[   11.901175] sdhci-pci 0000:04:04.2: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[   11.901195] mmc0: Unknown controller version (16). You may experience problems.
[   11.901323] mmc0: SDHCI controller on PCI [0000:04:04.2] using PIO
[   12.820916] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   12.820924] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   12.820946] HDA Intel 0000:00:10.1: setting latency timer to 64
[   12.916780] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.004173] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   13.004187] rt61pci 0000:04:09.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[   13.021247] phy0: Selected rate control algorithm 'pid'
[   13.120626] Registered led device: rt61pci-phy0:radio
[   13.120648] Registered led device: rt61pci-phy0:assoc
[   13.589646] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio2/input/input8
[   15.062268] loop: module loaded
[   15.148356] lp: driver loaded but no devices found
[   15.562128] Adding 2650684k swap on /dev/sda1.  Priority:-1 extents:1 across:2650684k
[   17.650052] type=1505 audit(1233436960.736:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3853
[   17.650277] type=1505 audit(1233436960.736:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3853
[   18.004719] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.540429] NET: Registered protocol family 17
[   23.866763] NET: Registered protocol family 10
[   23.867326] lo: Disabled Privacy Extensions
[   24.814416] ACPI: WMI: Mapper loaded
[   26.228675] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.592242] ppdev: user-space parallel port driver
[   29.278900] Bluetooth: Core ver 2.13
[   29.281091] NET: Registered protocol family 31
[   29.281096] Bluetooth: HCI device and connection manager initialized
[   29.281100] Bluetooth: HCI socket layer initialized
[   29.309132] Bluetooth: L2CAP ver 2.11
[   29.309137] Bluetooth: L2CAP socket layer initialized
[   29.355469] Bluetooth: SCO (Voice Link) ver 0.6
[   29.355474] Bluetooth: SCO socket layer initialized
[   29.399799] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.399804] Bluetooth: BNEP filters: protocol multicast
[   29.458275] Bridge firewalling registered
[   29.466540] Bluetooth: RFCOMM socket layer initialized
[   29.466882] Bluetooth: RFCOMM TTY layer initialized
[   29.466886] Bluetooth: RFCOMM ver 1.10
[   33.680408] firmware: requesting rt2561.bin
[   33.816566] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by paulderol on 2009-02-02
+1 for me. going to have to go in and re-install the whole bag. any news as to what caused this wonderous event, and whether or not it will be fixed? 

AMD 4200 
Nvidia 7300 GT
Nforce 4 chipset controlling onboard lan and audio--both in use.

---

### Post by sledhead45 on 2009-02-02
No idea what caused it. I decided it would be quicker/easier to reformat/reinstall then wait for a fix. 
I will add after the reinstall all the updates applied fine and my system is up to date and running good.

---

### Post by paulderol on 2009-02-02
currently wishing i hadn't trashed all my live-usbs for transferring files,,,,and using a kubuntu 8.10 lying around to pull my saved files out of the scrapper. i wonder why the update kills but install-update doesn't.

---


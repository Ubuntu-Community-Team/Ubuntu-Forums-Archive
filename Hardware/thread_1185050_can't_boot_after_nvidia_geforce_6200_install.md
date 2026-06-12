---
title: "can't boot after nvidia geforce 6200 install"
date: 2009-06-11
forum: Hardware
---

### Post by tars_ac on 2009-06-11
Hi all,

I've been using my old computer (Dell Dimension 2350 P4 with upgraded RAM [a desktop]) to run Ubuntu (currently 9.04) for years, and recently decided that I was fed up with it being so slow.  I got a PCI graphics card (a GeForce 6200) after reading elsewhere on these forums that it worked.  I tried Windows (XP) first to make sure the card was working, and it works fine there, although because it's Windows it's not something I want to have to use often :).  However, it just won't boot under Linux.  I was able to re-enable the integrated graphics to get in to try to install nvidia drivers, but it rarely gets past loading the driver before it just stops.  I've tried selecting various kernels from my GRUB menu - I got one to get to the login screen but it told me it couldn't find my home directory when I tried to log in.

I've tried the latest nvidia driver in the repositories (sorry, don't remember what that version was) and also 185.18.14 direct from nvidia's website, with the same result.  I'm using kernel 2.6.28-6.20-386 and compiled the driver using those headers.

I'm sure there's something I'm missing, but I don't know enough about graphics cards or drivers to figure it out.  I would really appreciate any advice.  Please let me know if you need any more info.  I've attached some logs that might help...

/var/log/messages:
```
Jun 11 14:58:52 BrianL syslogd 1.5.0#5ubuntu3: restart.
Jun 11 14:58:52 BrianL kernel: Inspecting /boot/System.map-2.6.28-6-386
Jun 11 14:58:52 BrianL kernel: Cannot find map file.
Jun 11 14:58:52 BrianL kernel: Loaded 51964 symbols from 102 modules.
Jun 11 14:58:52 BrianL kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Jun 11 14:58:52 BrianL kernel: [    0.000000] Linux version 2.6.28-6-386 (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 (Ubuntu 2.6.28-6.20-386)
Jun 11 14:58:52 BrianL kernel: [    0.000000] KERNEL supported cpus:
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Intel GenuineIntel
Jun 11 14:58:52 BrianL kernel: [    0.000000]   AMD AuthenticAMD
Jun 11 14:58:52 BrianL kernel: [    0.000000]   NSC Geode by NSC
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Cyrix CyrixInstead
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Centaur CentaurHauls
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 11 14:58:52 BrianL kernel: [    0.000000]   UMC UMC UMC UMC
Jun 11 14:58:52 BrianL kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000] DMI 2.3 present.
Jun 11 14:58:52 BrianL kernel: [    0.000000] last_pfn = 0x3fef0 max_arch_pfn = 0x100000
Jun 11 14:58:52 BrianL kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jun 11 14:58:52 BrianL kernel: [    0.000000] modified physical RAM map:
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 0000000000001000 - 0000000000010000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 0000000000100000 - 000000003fef0000 (usable)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 000000003fef3000 - 000000003ff00000 (ACPI data)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
Jun 11 14:58:52 BrianL kernel: [    0.000000] RAMDISK: 3f655000 - 3fedf7f2
Jun 11 14:58:52 BrianL kernel: [    0.000000] Allocated new RAMDISK: 005da000 - 00e647f2
Jun 11 14:58:52 BrianL kernel: [    0.000000] Move RAMDISK from 000000003f655000 - 000000003fedf7f1 to 005da000 - 00e647f1
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: RSDT 3FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: FACP 3FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: DSDT 3FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: FACS 3FEF0000, 0040
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: BOOT 3FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: APIC 3FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
Jun 11 14:58:52 BrianL kernel: [    0.000000] 134MB HIGHMEM available.
Jun 11 14:58:52 BrianL kernel: [    0.000000] 887MB LOWMEM available.
Jun 11 14:58:52 BrianL kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun 11 14:58:52 BrianL kernel: [    0.000000]   low ram: 00000000 - 377fe000
Jun 11 14:58:52 BrianL kernel: [    0.000000]   bootmap 00012000 - 00018f00
Jun 11 14:58:52 BrianL kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #1 [0000100000 - 00005d6d7c]    TEXT DATA BSS ==> [0000100000 - 00005d6d7c]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #2 [00005d7000 - 00005da000]    INIT_PG_TABLE ==> [00005d7000 - 00005da000]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #3 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #4 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #5 [00005da000 - 0000e647f2]      NEW RAMDISK ==> [00005da000 - 0000e647f2]
Jun 11 14:58:52 BrianL kernel: [    0.000000]   #6 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Jun 11 14:58:52 BrianL kernel: [    0.000000] found SMP MP-table at [c00f4ba0] 000f4ba0
Jun 11 14:58:52 BrianL kernel: [    0.000000] Zone PFN ranges:
Jun 11 14:58:52 BrianL kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun 11 14:58:52 BrianL kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun 11 14:58:52 BrianL kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003fef0
Jun 11 14:58:52 BrianL kernel: [    0.000000] Movable zone start PFN for each node
Jun 11 14:58:52 BrianL kernel: [    0.000000] early_node_map[3] active PFN ranges
Jun 11 14:58:52 BrianL kernel: [    0.000000]     0: 0x00000000 -> 0x00000001
Jun 11 14:58:52 BrianL kernel: [    0.000000]     0: 0x00000010 -> 0x00000090
Jun 11 14:58:52 BrianL kernel: [    0.000000]     0: 0x00000100 -> 0x0003fef0
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 11 14:58:52 BrianL kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 11 14:58:52 BrianL kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 11 14:58:52 BrianL kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 11 14:58:52 BrianL kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 11 14:58:52 BrianL kernel: [    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000010000
Jun 11 14:58:52 BrianL kernel: [    0.000000] PM: Registered nosave memory: 0000000000090000 - 00000000000a0000
Jun 11 14:58:52 BrianL kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jun 11 14:58:52 BrianL kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jun 11 14:58:52 BrianL kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
Jun 11 14:58:52 BrianL kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259699
Jun 11 14:58:52 BrianL kernel: [    0.000000] Kernel command line: root=UUID=a798423e-8893-41ee-851e-0f1bd0da6d35 ro splash 
Jun 11 14:58:52 BrianL kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 11 14:58:52 BrianL kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 11 14:58:52 BrianL kernel: [    0.000000] Initializing CPU#0
Jun 11 14:58:52 BrianL kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.000000] Fast TSC calibration using PIT
Jun 11 14:58:52 BrianL kernel: [    0.000000] Detected 1794.271 MHz processor.
Jun 11 14:58:52 BrianL kernel: [    0.004000] Console: colour VGA+ 80x25
Jun 11 14:58:52 BrianL kernel: [    0.004000] console [tty0] enabled
Jun 11 14:58:52 BrianL kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Jun 11 14:58:52 BrianL kernel: [    0.004000] Memory: 1023880k/1047488k available (2641k kernel code, 22740k reserved, 1282k data, 440k init, 138184k highmem)
Jun 11 14:58:52 BrianL kernel: [    0.004000] virtual kernel memory layout:
Jun 11 14:58:52 BrianL kernel: [    0.004000]     fixmap  : 0xfffaa000 - 0xfffff000   ( 340 kB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]       .init : 0xc04d8000 - 0xc0546000   ( 440 kB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]       .data : 0xc0394633 - 0xc04d509c   (1282 kB)
Jun 11 14:58:52 BrianL kernel: [    0.004000]       .text : 0xc0100000 - 0xc0394633   (2641 kB)
Jun 11 14:58:52 BrianL kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 11 14:58:52 BrianL kernel: [    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jun 11 14:58:52 BrianL kernel: [    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3588.54 BogoMIPS (lpj=7177084)
Jun 11 14:58:52 BrianL kernel: [    0.004151] Security Framework initialized
Jun 11 14:58:52 BrianL kernel: [    0.004218] SELinux:  Disabled at boot.
Jun 11 14:58:52 BrianL kernel: [    0.004299] AppArmor: AppArmor initialized
Jun 11 14:58:52 BrianL kernel: [    0.004361] Mount-cache hash table entries: 512
Jun 11 14:58:52 BrianL kernel: [    0.004622] Initializing cgroup subsys ns
Jun 11 14:58:52 BrianL kernel: [    0.004680] Initializing cgroup subsys cpuacct
Jun 11 14:58:52 BrianL kernel: [    0.004736] Initializing cgroup subsys freezer
Jun 11 14:58:52 BrianL kernel: [    0.004813] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 11 14:58:52 BrianL kernel: [    0.004906] CPU: L2 cache: 512K
Jun 11 14:58:52 BrianL kernel: [    0.004975] CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 07
Jun 11 14:58:52 BrianL kernel: [    0.005112] Checking 'hlt' instruction... OK.
Jun 11 14:58:52 BrianL kernel: [    0.023101] Freeing SMP alternatives: 0k freed
Jun 11 14:58:52 BrianL kernel: [    0.023162] ACPI: Core revision 20080926
Jun 11 14:58:52 BrianL kernel: [    0.026126] ACPI: Checking initramfs for custom DSDT
Jun 11 14:58:52 BrianL kernel: [    0.556797] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 11 14:58:52 BrianL kernel: [    0.600000] net_namespace: 752 bytes
Jun 11 14:58:52 BrianL kernel: [    0.600000] Booting paravirtualized kernel on bare hardware
Jun 11 14:58:52 BrianL kernel: [    0.600000] regulator: core version 0.5
Jun 11 14:58:52 BrianL kernel: [    0.600000] NET: Registered protocol family 16
Jun 11 14:58:52 BrianL kernel: [    0.600000] EISA bus registered
Jun 11 14:58:52 BrianL kernel: [    0.600000] ACPI: bus type pci registered
Jun 11 14:58:52 BrianL kernel: [    0.626523] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
Jun 11 14:58:52 BrianL kernel: [    0.626581] PCI: Using configuration type 1 for base access
Jun 11 14:58:52 BrianL kernel: [    0.635259] ACPI: Interpreter enabled
Jun 11 14:58:52 BrianL kernel: [    0.635325] ACPI: (supports S0 S1 S3 S4 S5)
Jun 11 14:58:52 BrianL kernel: [    0.635587] ACPI: Using IOAPIC for interrupt routing
Jun 11 14:58:52 BrianL kernel: [    0.641355] ACPI: No dock devices found.
Jun 11 14:58:52 BrianL kernel: [    0.641425] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 11 14:58:52 BrianL kernel: [    0.642001] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jun 11 14:58:52 BrianL kernel: [    0.642062] pci 0000:00:1d.7: PME# disabled
Jun 11 14:58:52 BrianL kernel: [    0.642166] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Jun 11 14:58:52 BrianL kernel: [    0.642168] * this clock source is slow. If you are sure your timer does not have
Jun 11 14:58:52 BrianL kernel: [    0.642170] * this bug, please use "acpi_pm_good" to disable the workaround
Jun 11 14:58:52 BrianL kernel: [    0.642400] HPET not enabled in BIOS. You might try hpet=force boot option
Jun 11 14:58:52 BrianL kernel: [    0.642464] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
Jun 11 14:58:52 BrianL kernel: [    0.642535] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
Jun 11 14:58:52 BrianL kernel: [    0.642823] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
Jun 11 14:58:52 BrianL kernel: [    0.642881] pci 0000:00:1f.5: PME# disabled
Jun 11 14:58:52 BrianL kernel: [    0.643031] pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
Jun 11 14:58:52 BrianL kernel: [    0.643089] pci 0000:01:04.0: PME# disabled
Jun 11 14:58:52 BrianL kernel: [    0.643318] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 11 14:58:52 BrianL kernel: [    0.643378] pci 0000:01:09.0: PME# disabled
Jun 11 14:58:52 BrianL kernel: [    0.643466] pci 0000:00:1e.0: transparent bridge
Jun 11 14:58:52 BrianL kernel: [    0.668435] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
Jun 11 14:58:52 BrianL kernel: [    0.669110] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jun 11 14:58:52 BrianL kernel: [    0.669780] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
Jun 11 14:58:52 BrianL kernel: [    0.670449] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Jun 11 14:58:52 BrianL kernel: [    0.671121] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 11 14:58:52 BrianL kernel: [    0.671873] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 11 14:58:52 BrianL kernel: [    0.672605] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Jun 11 14:58:52 BrianL kernel: [    0.673356] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Jun 11 14:58:52 BrianL kernel: [    0.674179] usbcore: registered new interface driver usbfs
Jun 11 14:58:52 BrianL kernel: [    0.674261] usbcore: registered new interface driver hub
Jun 11 14:58:52 BrianL kernel: [    0.674353] usbcore: registered new device driver usb
Jun 11 14:58:52 BrianL kernel: [    0.674514] PCI: Using ACPI for IRQ routing
Jun 11 14:58:52 BrianL kernel: [    0.674723] NET: Registered protocol family 8
Jun 11 14:58:52 BrianL kernel: [    0.674778] NET: Registered protocol family 20
Jun 11 14:58:52 BrianL kernel: [    0.674946] AppArmor: AppArmor Filesystem Enabled
Jun 11 14:58:52 BrianL kernel: [    0.675023] pnp: PnP ACPI init
Jun 11 14:58:52 BrianL kernel: [    0.676021] ACPI: bus type pnp registered
Jun 11 14:58:52 BrianL kernel: [    0.680142] pnp: PnP ACPI: found 12 devices
Jun 11 14:58:52 BrianL kernel: [    0.680200] ACPI: ACPI bus type pnp unregistered
Jun 11 14:58:52 BrianL kernel: [    0.680257] PnPBIOS: Disabled by ACPI PNP
Jun 11 14:58:52 BrianL kernel: [    0.680324] system 00:00: iomem range 0xcc000-0xcffff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680382] system 00:00: iomem range 0xd5800-0xd7fff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680440] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.680499] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.680557] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.680627] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.680685] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.680755] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680814] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680873] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680933] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.680992] system 00:00: iomem range 0xe0000-0xeffff has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.681056] system 00:02: ioport range 0x400-0x4bf could not be reserved
Jun 11 14:58:52 BrianL kernel: [    0.681119] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.681177] system 00:03: ioport range 0x800-0x87f has been reserved
Jun 11 14:58:52 BrianL kernel: [    0.716064] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
Jun 11 14:58:52 BrianL kernel: [    0.716124] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
Jun 11 14:58:52 BrianL kernel: [    0.716183] pci 0000:00:1e.0:   MEM window: 0xdc000000-0xdfffffff
Jun 11 14:58:52 BrianL kernel: [    0.716243] pci 0000:00:1e.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Jun 11 14:58:52 BrianL kernel: [    0.716334] bus: 00 index 0 io port: [0x00-0xffff]
Jun 11 14:58:52 BrianL kernel: [    0.716390] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Jun 11 14:58:52 BrianL kernel: [    0.716445] bus: 01 index 0 io port: [0xc000-0xcfff]
Jun 11 14:58:52 BrianL kernel: [    0.716499] bus: 01 index 1 mmio: [0xdc000000-0xdfffffff]
Jun 11 14:58:52 BrianL kernel: [    0.716555] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
Jun 11 14:58:52 BrianL kernel: [    0.716611] bus: 01 index 3 io port: [0x00-0xffff]
Jun 11 14:58:52 BrianL kernel: [    0.716665] bus: 01 index 4 mmio: [0x000000-0xffffffff]
Jun 11 14:58:52 BrianL kernel: [    0.716732] NET: Registered protocol family 2
Jun 11 14:58:52 BrianL kernel: [    0.716943] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.717489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.718876] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Jun 11 14:58:52 BrianL kernel: [    0.719361] TCP: Hash tables configured (established 131072 bind 65536)
Jun 11 14:58:52 BrianL kernel: [    0.719419] TCP reno registered
Jun 11 14:58:52 BrianL kernel: [    0.719651] NET: Registered protocol family 1
Jun 11 14:58:52 BrianL kernel: [    0.719955] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Jun 11 14:58:52 BrianL kernel: [    1.239910]  it is
Jun 11 14:58:52 BrianL kernel: [    1.813280] Freeing initrd memory: 8745k freed
Jun 11 14:58:52 BrianL kernel: [    1.813415] Simple Boot Flag at 0x59 set to 0x1
Jun 11 14:58:52 BrianL kernel: [    1.813729] audit: initializing netlink socket (disabled)
Jun 11 14:58:52 BrianL kernel: [    1.813812] type=2000 audit(1244746705.812:1): initialized
Jun 11 14:58:52 BrianL kernel: [    1.821759] highmem bounce pool size: 64 pages
Jun 11 14:58:52 BrianL kernel: [    1.823498] VFS: Disk quotas dquot_6.5.1
Jun 11 14:58:52 BrianL kernel: [    1.823590] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 11 14:58:52 BrianL kernel: [    1.823717] fuse init (API version 7.10)
Jun 11 14:58:52 BrianL kernel: [    1.823898] msgmni has been set to 1747
Jun 11 14:58:52 BrianL kernel: [    1.824204] alg: No test for stdrng (krng)
Jun 11 14:58:52 BrianL kernel: [    1.824274] io scheduler noop registered
Jun 11 14:58:52 BrianL kernel: [    1.824328] io scheduler anticipatory registered
Jun 11 14:58:52 BrianL kernel: [    1.824382] io scheduler deadline registered
Jun 11 14:58:52 BrianL kernel: [    1.824457] io scheduler cfq registered (default)
Jun 11 14:58:52 BrianL kernel: [    1.828532] isapnp: Scanning for PnP cards...
Jun 11 14:58:52 BrianL kernel: [    2.182634] isapnp: No Plug & Play device found
Jun 11 14:58:52 BrianL kernel: [    2.184300] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jun 11 14:58:52 BrianL kernel: [    2.184463] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 11 14:58:52 BrianL kernel: [    2.185030] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 11 14:58:52 BrianL kernel: [    2.186127] brd: module loaded
Jun 11 14:58:52 BrianL kernel: [    2.186223] Fixed MDIO Bus: probed
Jun 11 14:58:52 BrianL kernel: [    2.186341] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 11 14:58:52 BrianL kernel: [    2.186434] Uniform Multi-Platform E-IDE driver
Jun 11 14:58:52 BrianL kernel: [    2.186582] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 11 14:58:52 BrianL kernel: [    2.186685] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Jun 11 14:58:52 BrianL kernel: [    2.186781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 11 14:58:52 BrianL kernel: [    2.186923] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jun 11 14:58:52 BrianL kernel: [    2.190925] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe0080000
Jun 11 14:58:52 BrianL kernel: [    2.204009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jun 11 14:58:52 BrianL kernel: [    2.204190] usb usb1: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    2.204288] hub 1-0:1.0: USB hub found
Jun 11 14:58:52 BrianL kernel: [    2.204351] hub 1-0:1.0: 6 ports detected
Jun 11 14:58:52 BrianL kernel: [    2.204571] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 11 14:58:52 BrianL kernel: [    2.204646] uhci_hcd: USB Universal Host Controller Interface driver
Jun 11 14:58:52 BrianL kernel: [    2.204753] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 14:58:52 BrianL kernel: [    2.204825] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 11 14:58:52 BrianL kernel: [    2.204947] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 11 14:58:52 BrianL kernel: [    2.205045] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
Jun 11 14:58:52 BrianL kernel: [    2.205207] usb usb2: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    2.205301] hub 2-0:1.0: USB hub found
Jun 11 14:58:52 BrianL kernel: [    2.205361] hub 2-0:1.0: 2 ports detected
Jun 11 14:58:52 BrianL kernel: [    2.205542] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 11 14:58:52 BrianL kernel: [    2.205611] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 11 14:58:52 BrianL kernel: [    2.205726] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jun 11 14:58:52 BrianL kernel: [    2.205821] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
Jun 11 14:58:52 BrianL kernel: [    2.205979] usb usb3: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    2.206070] hub 3-0:1.0: USB hub found
Jun 11 14:58:52 BrianL kernel: [    2.206133] hub 3-0:1.0: 2 ports detected
Jun 11 14:58:52 BrianL kernel: [    2.206303] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jun 11 14:58:52 BrianL kernel: [    2.206372] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 11 14:58:52 BrianL kernel: [    2.206486] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jun 11 14:58:52 BrianL kernel: [    2.206581] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
Jun 11 14:58:52 BrianL kernel: [    2.206752] usb usb4: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    2.206843] hub 4-0:1.0: USB hub found
Jun 11 14:58:52 BrianL kernel: [    2.206904] hub 4-0:1.0: 2 ports detected
Jun 11 14:58:52 BrianL kernel: [    2.207130] usbcore: registered new interface driver libusual
Jun 11 14:58:52 BrianL kernel: [    2.207251] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun 11 14:58:52 BrianL kernel: [    2.207309] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun 11 14:58:52 BrianL kernel: [    2.207910] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 11 14:58:52 BrianL kernel: [    2.208123] mice: PS/2 mouse device common for all mice
Jun 11 14:58:52 BrianL kernel: [    2.208243] EISA: Probing bus 0 at eisa.0
Jun 11 14:58:52 BrianL kernel: [    2.208335] EISA: Detected 0 cards.
Jun 11 14:58:52 BrianL kernel: [    2.208390] cpuidle: using governor ladder
Jun 11 14:58:52 BrianL kernel: [    2.209122] TCP cubic registered
Jun 11 14:58:52 BrianL kernel: [    2.209225] Using IPI Shortcut mode
Jun 11 14:58:52 BrianL kernel: [    2.209394] registered taskstats version 1
Jun 11 14:58:52 BrianL kernel: [    2.209618] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 11 14:58:52 BrianL kernel: [    2.209676] EDD information not available.
Jun 11 14:58:52 BrianL kernel: [    2.210425] Freeing unused kernel memory: 440k freed
Jun 11 14:58:52 BrianL kernel: [    2.252519] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 11 14:58:52 BrianL kernel: [    2.648388] processor ACPI_CPU:00: registered as cooling_device0
Jun 11 14:58:52 BrianL kernel: [    2.648397] ACPI: Processor [CPU0] (supports 2 throttling states)
Jun 11 14:58:52 BrianL kernel: [    2.684032] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jun 11 14:58:52 BrianL kernel: [    2.702769] device-mapper: uevent: version 1.0.3
Jun 11 14:58:52 BrianL kernel: [    2.702927] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jun 11 14:58:52 BrianL kernel: [    2.781146] md: linear personality registered for level -1
Jun 11 14:58:52 BrianL kernel: [    2.785945] md: multipath personality registered for level -4
Jun 11 14:58:52 BrianL kernel: [    2.815193] md: raid0 personality registered for level 0
Jun 11 14:58:52 BrianL kernel: [    2.838847] md: raid1 personality registered for level 1
Jun 11 14:58:52 BrianL kernel: [    2.870471] xor: automatically using best checksumming function: pIII_sse
Jun 11 14:58:52 BrianL kernel: [    2.888009]    pIII_sse  :  2260.000 MB/sec
Jun 11 14:58:52 BrianL kernel: [    2.888013] xor: using function: pIII_sse (2260.000 MB/sec)
Jun 11 14:58:52 BrianL kernel: [    2.901790] async_tx: api initialized (async)
Jun 11 14:58:52 BrianL kernel: [    2.976066] raid6: int32x1    499 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.044030] raid6: int32x2    571 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.112044] raid6: int32x4    577 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.180016] raid6: int32x8    406 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.248047] raid6: mmxx1     1489 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.316029] raid6: mmxx2     1874 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.384021] raid6: sse1x1     878 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.452043] raid6: sse1x2    1606 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.520028] raid6: sse2x1    1808 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.588006] raid6: sse2x2    1943 MB/s
Jun 11 14:58:52 BrianL kernel: [    3.588011] raid6: using algorithm sse2x2 (1943 MB/s)
Jun 11 14:58:52 BrianL kernel: [    3.588018] md: raid6 personality registered for level 6
Jun 11 14:58:52 BrianL kernel: [    3.588022] md: raid5 personality registered for level 5
Jun 11 14:58:52 BrianL kernel: [    3.588025] md: raid4 personality registered for level 4
Jun 11 14:58:52 BrianL kernel: [    3.674074] usb 1-4: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    3.912015] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun 11 14:58:52 BrianL kernel: [    4.095811] usb 2-1: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    4.337637] usb 3-1: new low speed USB device using uhci_hcd and address 2
Jun 11 14:58:52 BrianL kernel: [    4.337745] md: raid10 personality registered for level 10
Jun 11 14:58:52 BrianL kernel: [    4.507540] usb 3-1: configuration #1 chosen from 1 choice
Jun 11 14:58:52 BrianL kernel: [    4.705830] Floppy drive(s): fd0 is 1.44M
Jun 11 14:58:52 BrianL kernel: [    4.723820] FDC 0 is a post-1991 82077
Jun 11 14:58:52 BrianL kernel: [    4.973792] usbcore: registered new interface driver hiddev
Jun 11 14:58:52 BrianL kernel: [    4.989812] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
Jun 11 14:58:52 BrianL kernel: [    5.004183] generic-usb 0003:1267:0212.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1/input0
Jun 11 14:58:52 BrianL kernel: [    5.004216] usbcore: registered new interface driver usbhid
Jun 11 14:58:52 BrianL kernel: [    5.004222] usbhid: v2.6:USB HID core driver
Jun 11 14:58:52 BrianL kernel: [    5.192266] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 11 14:58:52 BrianL kernel: [    5.212138] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
Jun 11 14:58:52 BrianL kernel: [    5.212150] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
Jun 11 14:58:52 BrianL kernel: [    5.212158] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
Jun 11 14:58:52 BrianL kernel: [    5.268139] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
Jun 11 14:58:52 BrianL kernel: [    5.268174] b44.c:v2.0
Jun 11 14:58:52 BrianL kernel: [    5.276598] SCSI subsystem initialized
Jun 11 14:58:52 BrianL kernel: [    5.306602] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:08:74:bc:c7:f1
Jun 11 14:58:52 BrianL kernel: [    5.341807] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 11 14:58:52 BrianL kernel: [    5.352040] scsi0 : ata_piix
Jun 11 14:58:52 BrianL kernel: [    5.353800] scsi1 : ata_piix
Jun 11 14:58:52 BrianL kernel: [    5.355302] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jun 11 14:58:52 BrianL kernel: [    5.355307] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jun 11 14:58:52 BrianL kernel: [    5.524505] ata1.00: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
Jun 11 14:58:52 BrianL kernel: [    5.524513] ata1.00: 80293248 sectors, multi 16: LBA 
Jun 11 14:58:52 BrianL kernel: [    5.525668] ata1.01: ATA-6: WDC WD2000JB-00EVA0, 15.05R15, max UDMA/100
Jun 11 14:58:52 BrianL kernel: [    5.525676] ata1.01: 390721968 sectors, multi 16: LBA48 
Jun 11 14:58:52 BrianL kernel: [    5.540464] ata1.00: configured for UDMA/100
Jun 11 14:58:52 BrianL kernel: [    5.557450] ata1.01: configured for UDMA/100
Jun 11 14:58:52 BrianL kernel: [    5.728406] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, B105, max UDMA/33
Jun 11 14:58:52 BrianL kernel: [    5.728474] ata2.01: ATAPI: HL-DT-ST GCE-8400B, B104, max UDMA/33
Jun 11 14:58:52 BrianL kernel: [    5.736462] ata2.00: configured for UDMA/33
Jun 11 14:58:52 BrianL kernel: [    5.752342] ata2.01: configured for UDMA/33
Jun 11 14:58:52 BrianL kernel: [    5.752941] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
Jun 11 14:58:52 BrianL kernel: [    5.753156] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2000JB-00E 15.0 PQ: 0 ANSI: 5
Jun 11 14:58:52 BrianL kernel: [    5.753464] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B105 PQ: 0 ANSI: 5
Jun 11 14:58:52 BrianL kernel: [    5.753832] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  B104 PQ: 0 ANSI: 5
Jun 11 14:58:52 BrianL kernel: [    6.736128] Driver 'sd' needs updating - please use bus_type methods
Jun 11 14:58:52 BrianL kernel: [    6.736280] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
Jun 11 14:58:52 BrianL kernel: [    6.736306] sd 0:0:0:0: [sda] Write Protect is off
Jun 11 14:58:52 BrianL kernel: [    6.736349] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 14:58:52 BrianL kernel: [    6.736443] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
Jun 11 14:58:52 BrianL kernel: [    6.736465] sd 0:0:0:0: [sda] Write Protect is off
Jun 11 14:58:52 BrianL kernel: [    6.736506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 14:58:52 BrianL kernel: [    6.736512]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 11 14:58:52 BrianL kernel: [    7.448093]  sda1 sda2
Jun 11 14:58:52 BrianL kernel: [    7.448310] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 11 14:58:52 BrianL kernel: [    7.448445] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
Jun 11 14:58:52 BrianL kernel: [    7.448472] sd 0:0:1:0: [sdb] Write Protect is off
Jun 11 14:58:52 BrianL kernel: [    7.448515] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 14:58:52 BrianL kernel: [    7.449712] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
Jun 11 14:58:52 BrianL kernel: [    7.449763] sd 0:0:1:0: [sdb] Write Protect is off
Jun 11 14:58:52 BrianL kernel: [    7.449806] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 11 14:58:52 BrianL kernel: [    7.449814]  sdb: sdb1 sdb2 sdb3
Jun 11 14:58:52 BrianL kernel: [    7.468061] sd 0:0:1:0: [sdb] Attached SCSI disk
Jun 11 14:58:52 BrianL kernel: [    7.475851] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 11 14:58:52 BrianL kernel: [    7.475895] sd 0:0:1:0: Attached scsi generic sg1 type 0
Jun 11 14:58:52 BrianL kernel: [    7.475933] sr 1:0:0:0: Attached scsi generic sg2 type 5
Jun 11 14:58:52 BrianL kernel: [    7.475971] scsi 1:0:1:0: Attached scsi generic sg3 type 5
Jun 11 14:58:52 BrianL kernel: [    7.477447] sr0: scsi3-mmc drive: 40x/48x cd/rw xa/form2 cdda tray
Jun 11 14:58:52 BrianL kernel: [    7.477457] Uniform CD-ROM driver Revision: 3.20
Jun 11 14:58:52 BrianL kernel: [    7.479592] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jun 11 14:58:52 BrianL kernel: [    8.312029] kjournald starting.  Commit interval 5 seconds
Jun 11 14:58:52 BrianL kernel: [    8.312055] EXT3-fs: mounted filesystem with ordered data mode.
Jun 11 14:58:52 BrianL kernel: [   17.649642] udev: starting version 141
Jun 11 14:58:52 BrianL kernel: [   17.949578] Linux agpgart interface v0.103
Jun 11 14:58:52 BrianL kernel: [   17.961318] agpgart-intel 0000:00:00.0: Intel 830M Chipset
Jun 11 14:58:52 BrianL kernel: [   17.961616] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Jun 11 14:58:52 BrianL kernel: [   17.964324] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
Jun 11 14:58:52 BrianL kernel: [   17.972807] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jun 11 14:58:52 BrianL kernel: [   17.992055] ACPI: Power Button (FF) [PWRF]
Jun 11 14:58:52 BrianL kernel: [   17.992297] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Jun 11 14:58:52 BrianL kernel: [   18.012040] ACPI: Power Button (CM) [PWRB]
Jun 11 14:58:52 BrianL kernel: [   18.069186] parport_pc 00:0a: reported by Plug and Play ACPI
Jun 11 14:58:52 BrianL kernel: [   18.069217] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Jun 11 14:58:52 BrianL kernel: [   18.222882] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7404
Jun 11 14:58:52 BrianL kernel: [   18.222922] usbcore: registered new interface driver usblp
Jun 11 14:58:52 BrianL kernel: [   18.512111] cfg80211: Calling CRDA to update world regulatory domain
Jun 11 14:58:52 BrianL kernel: [   18.567735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 11 14:58:52 BrianL kernel: [   18.572443] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 11 14:58:52 BrianL kernel: [   18.585431] intel_rng: FWH not detected
Jun 11 14:58:52 BrianL kernel: [   18.650452] iTCO_vendor_support: vendor-support=0
Jun 11 14:58:52 BrianL kernel: [   18.653026] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Jun 11 14:58:52 BrianL kernel: [   18.653203] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
Jun 11 14:58:52 BrianL kernel: [   18.653328] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 11 14:58:52 BrianL kernel: [   18.768992] usbcore: registered new interface driver rt2500usb
Jun 11 14:58:52 BrianL kernel: [   19.319062] Registered led device: rt73usb-phy1:radio
Jun 11 14:58:52 BrianL kernel: [   19.319129] Registered led device: rt73usb-phy1:assoc
Jun 11 14:58:52 BrianL kernel: [   19.319194] Registered led device: rt73usb-phy1:quality
Jun 11 14:58:52 BrianL kernel: [   19.321030] usbcore: registered new interface driver rt73usb
Jun 11 14:58:52 BrianL kernel: [   19.469804] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 11 14:58:52 BrianL kernel: [   19.754459] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Jun 11 14:58:52 BrianL kernel: [   19.892034] intel8x0_measure_ac97_clock: measured 54867 usecs
Jun 11 14:58:52 BrianL kernel: [   19.892041] intel8x0: clocking to 48000
Jun 11 14:58:52 BrianL kernel: [   20.642762] ppdev: user-space parallel port driver
Jun 11 14:58:52 BrianL kernel: [   20.866177] cfg80211: World regulatory domain updated:
Jun 11 14:58:52 BrianL kernel: [   20.866187] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 11 14:58:52 BrianL kernel: [   20.866193] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 11 14:58:52 BrianL kernel: [   20.866197] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 11 14:58:52 BrianL kernel: [   20.866202] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 11 14:58:52 BrianL kernel: [   20.866206] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 11 14:58:52 BrianL kernel: [   20.866210] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 11 14:58:52 BrianL kernel: [   21.898872] Intel ISA PCIC probe: not found.
Jun 11 14:58:52 BrianL kernel: [   22.020390] lp0: using parport0 (interrupt-driven).
Jun 11 14:58:52 BrianL kernel: [   23.293569] Adding 979924k swap on /dev/sdb1.  Priority:-1 extents:1 across:979924k
Jun 11 14:58:52 BrianL kernel: [   24.043425] EXT3 FS on sdb2, internal journal
Jun 11 14:58:52 BrianL kernel: [   26.044024] kjournald starting.  Commit interval 5 seconds
Jun 11 14:58:52 BrianL kernel: [   26.044426] EXT3 FS on sdb3, internal journal
Jun 11 14:58:52 BrianL kernel: [   26.044434] EXT3-fs: mounted filesystem with ordered data mode.
Jun 11 14:58:52 BrianL kernel: [   26.791263] type=1505 audit(1244746730.788:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2048
Jun 11 14:58:52 BrianL kernel: [   26.874149] type=1505 audit(1244746730.872:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2052
Jun 11 14:58:52 BrianL kernel: [   26.874461] type=1505 audit(1244746730.872:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2052
Jun 11 14:58:52 BrianL kernel: [   26.874552] type=1505 audit(1244746730.872:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2052
Jun 11 14:58:52 BrianL kernel: [   26.874634] type=1505 audit(1244746730.872:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2052
Jun 11 14:58:52 BrianL kernel: [   27.105769] type=1505 audit(1244746731.104:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2057
Jun 11 14:58:52 BrianL kernel: [   27.106170] type=1505 audit(1244746731.104:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2057
Jun 11 14:58:52 BrianL kernel: [   27.156761] type=1505 audit(1244746731.156:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2061
Jun 11 14:58:56 BrianL kernel: [   32.712583] Bluetooth: Core ver 2.13
Jun 11 14:58:56 BrianL kernel: [   32.738241] NET: Registered protocol family 31
Jun 11 14:58:56 BrianL kernel: [   32.738247] Bluetooth: HCI device and connection manager initialized
Jun 11 14:58:56 BrianL kernel: [   32.738253] Bluetooth: HCI socket layer initialized
Jun 11 14:58:56 BrianL kernel: [   32.835043] Bluetooth: L2CAP ver 2.11
Jun 11 14:58:56 BrianL kernel: [   32.835048] Bluetooth: L2CAP socket layer initialized
Jun 11 14:58:56 BrianL kernel: [   32.969963] Bluetooth: RFCOMM socket layer initialized
Jun 11 14:58:56 BrianL kernel: [   32.969986] Bluetooth: RFCOMM TTY layer initialized
Jun 11 14:58:56 BrianL kernel: [   32.969989] Bluetooth: RFCOMM ver 1.10
Jun 11 14:58:56 BrianL kernel: [   32.979627] Bluetooth: SCO (Voice Link) ver 0.6
Jun 11 14:58:56 BrianL kernel: [   32.979632] Bluetooth: SCO socket layer initialized
Jun 11 14:58:56 BrianL kernel: [   32.994960] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 11 14:58:56 BrianL kernel: [   32.994966] Bluetooth: BNEP filters: protocol multicast
Jun 11 14:58:57 BrianL kernel: [   33.082633] Bridge firewalling registered
Jun 11 14:59:03 BrianL kernel: [   39.011437] rt73usb 1-4:1.0: firmware: requesting rt73.bin
Jun 11 14:59:03 BrianL kernel: [   39.322472] NET: Registered protocol family 17
Jun 11 14:59:05 BrianL kernel: [   41.816173] b44: eth0: Link is up at 100 Mbps, full duplex.
Jun 11 14:59:05 BrianL kernel: [   41.816179] b44: eth0: Flow control is off for TX and off for RX.
Jun 11 14:59:09 BrianL kernel: [   45.450456] NET: Registered protocol family 10
Jun 11 14:59:09 BrianL kernel: [   45.451326] lo: Disabled Privacy Extensions
Jun 11 14:59:09 BrianL kernel: [   45.456675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 11 18:59:33 BrianL kernel: [   68.926645] UDF-fs: No VRS found
Jun 11 19:13:52 BrianL kernel: [  927.465034] [drm] Initialized drm 1.1.0 20060810
Jun 11 19:13:52 BrianL kernel: [  927.475529] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 11 19:13:52 BrianL kernel: [  927.475794] [drm] Initialized i915 1.6.0 20080730 on minor 0
Jun 11 19:16:36 BrianL kernel: [ 1091.522681] nvidia: module license 'NVIDIA' taints kernel.
Jun 11 19:16:36 BrianL kernel: [ 1091.787978] nvidia 0000:01:06.0: enabling device (0000 -> 0002)
Jun 11 19:16:36 BrianL kernel: [ 1091.787993] nvidia 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 11 19:16:36 BrianL kernel: [ 1091.792196] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
Jun 11 19:25:37 BrianL exiting on signal 15

```


/var/log/Xorg.0.log:
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux BrianL 2.6.28-6-386 #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 11 19:13:51 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xd0000000/134217728, 0xe0000000/524288
(--) PCI: (0@1:6:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile IntelÂ® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xE0000000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 1 display pipe available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SAM", prod id 799
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): EDID vendor "SAM", prod id 799
(II) intel(0): Output VGA connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA using initial mode 1680x1050
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (470, 300) mm
(**) intel(0): DPI set to (90, 142)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 240640 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 962556 kB available
(WW) intel(0): DRI2 requires UXA
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xe0000000
(II) intel(0): [dri] visual configs initialized
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 41287680 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0589f000 (pgoffset 22687)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x058a0000 (pgoffset 22688)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x0589efff: DRI memory manager (89856 kB)
(II) intel(0): 0x0589f000-0x0589ffff: overlay registers (4 kB, 0x000000002f0fc000 physical
)
(II) intel(0): 0x058a0000-0x07ffffff: exa offscreen (40320 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x000df000:            start of memory manager
(II) intel(0): 0x01000000-0x01ffffff: depth buffer (16384 kB) X tiled
(II) intel(0): 0x02000000-0x02ffffff: back buffer (16384 kB) X tiled
(II) intel(0): 0x03000000-0x03ffffff: front buffer (16384 kB) X tiled
(II) intel(0): 0x00100000-0x00104fff: HW cursors (20 kB)
(II) intel(0): 0x0589f000:            end of memory manager
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] mapped front buffer at 0xd3000000, handle = 0xd3000000
(II) intel(0): [drm] mapped back buffer at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] mapped depth buffer at 0xd1000000, handle = 0xd1000000
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: XF86DRI Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 474 x 296
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc104"
(**) AT Translated Set 2 keyboard: xkb_model: "pc104"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2+USB Mouse
(**) PS/2+USB Mouse: always reports core events
(**) PS/2+USB Mouse: Device: "/dev/input/event2"
(II) PS/2+USB Mouse: Found 5 mouse buttons
(II) PS/2+USB Mouse: Found x and y relative axes
(II) PS/2+USB Mouse: Configuring as mouse
(**) PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE)
(**) PS/2+USB Mouse: (accel) keeping acceleration scheme 1
(**) PS/2+USB Mouse: (accel) filter chain progression: 2.00
(**) PS/2+USB Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2+USB Mouse: (accel) set acceleration profile 0
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "SAM", prod id 799
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): EDID vendor "SAM", prod id 799
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) PS/2+USB Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8066000 at 0xb7907000
(II) intel(0): [drm] Closed DRM master.
 ddxSigGiveUp: Closing log

```

/var/log/dmesg:
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Linux version 2.6.28-6-386 (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 (Ubuntu 2.6.28-6.20-386)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3fef0 max_arch_pfn = 0x100000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  modified: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  modified: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-16000
[    0.000000] RAMDISK: 3f655000 - 3fedf7f2
[    0.000000] Allocated new RAMDISK: 005da000 - 00e647f2
[    0.000000] Move RAMDISK from 000000003f655000 - 000000003fedf7f1 to 005da000 - 00e647f1
[    0.000000] ACPI: RSDP 000F6D40, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 3FEF3000, 0030 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEF30C0, 3543 (r1 INTELR AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FEF0000, 0040
[    0.000000] ACPI: BOOT 3FEF6640, 0028 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEF6680, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 134MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 00000000 - 377fe000
[    0.000000]   bootmap 00012000 - 00018f00
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000100000 - 00005d6d7c]    TEXT DATA BSS ==> [0000100000 - 00005d6d7c]
[    0.000000]   #2 [00005d7000 - 00005da000]    INIT_PG_TABLE ==> [00005d7000 - 00005da000]
[    0.000000]   #3 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #4 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #5 [00005da000 - 0000e647f2]      NEW RAMDISK ==> [00005da000 - 0000e647f2]
[    0.000000]   #6 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f4ba0] 000f4ba0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000010 -> 0x00000090
[    0.000000]     0: 0x00000100 -> 0x0003fef0
[    0.000000] On node 0 totalpages: 261745
[    0.000000] free_area_init_node: node 0, pgdat c04c9e00, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3937 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 270 pages used for memmap
[    0.000000]   HighMem zone: 34276 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259699
[    0.000000] Kernel command line: root=UUID=a798423e-8893-41ee-851e-0f1bd0da6d35 ro splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1794.271 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1023880k/1047488k available (2641k kernel code, 22740k reserved, 1282k data, 440k init, 138184k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfffaa000 - 0xfffff000   ( 340 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.004000]       .init : 0xc04d8000 - 0xc0546000   ( 440 kB)
[    0.004000]       .data : 0xc0394633 - 0xc04d509c   (1282 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0394633   (2641 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3588.54 BogoMIPS (lpj=7177084)
[    0.004151] Security Framework initialized
[    0.004218] SELinux:  Disabled at boot.
[    0.004299] AppArmor: AppArmor initialized
[    0.004361] Mount-cache hash table entries: 512
[    0.004622] Initializing cgroup subsys ns
[    0.004680] Initializing cgroup subsys cpuacct
[    0.004736] Initializing cgroup subsys freezer
[    0.004813] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004906] CPU: L2 cache: 512K
[    0.004975] CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 07
[    0.005112] Checking 'hlt' instruction... OK.
[    0.023101] Freeing SMP alternatives: 0k freed
[    0.023162] ACPI: Core revision 20080926
[    0.026126] ACPI: Checking initramfs for custom DSDT
[    0.556797] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.600000] net_namespace: 752 bytes
[    0.600000] Booting paravirtualized kernel on bare hardware
[    0.600000] regulator: core version 0.5
[    0.600000] NET: Registered protocol family 16
[    0.600000] EISA bus registered
[    0.600000] ACPI: bus type pci registered
[    0.626523] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
[    0.626581] PCI: Using configuration type 1 for base access
[    0.628051] ACPI: EC: Look up EC in DSDT
[    0.635259] ACPI: Interpreter enabled
[    0.635325] ACPI: (supports S0 S1 S3 S4 S5)
[    0.635587] ACPI: Using IOAPIC for interrupt routing
[    0.641355] ACPI: No dock devices found.
[    0.641425] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.641547] pci 0000:00:00.0: reg 10 32bit mmio: [0xd8000000-0xdbffffff]
[    0.641632] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.641642] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.641766] pci 0000:00:1d.0: reg 20 io port: [0xd800-0xd81f]
[    0.641828] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
[    0.641889] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
[    0.641950] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0080000-0xe00803ff]
[    0.642001] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.642062] pci 0000:00:1d.7: PME# disabled
[    0.642166] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.642168] * this clock source is slow. If you are sure your timer does not have
[    0.642170] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.642400] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.642464] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.642535] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.642615] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.642623] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.642632] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.642641] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.642649] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.642658] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.642717] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.642770] pci 0000:00:1f.5: reg 10 io port: [0xe000-0xe0ff]
[    0.642778] pci 0000:00:1f.5: reg 14 io port: [0xe400-0xe43f]
[    0.642787] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0081000-0xe00811ff]
[    0.642796] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0082000-0xe00820ff]
[    0.642823] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.642881] pci 0000:00:1f.5: PME# disabled
[    0.642985] pci 0000:01:04.0: reg 10 32bit mmio: [0xdf000000-0xdf00ffff]
[    0.642994] pci 0000:01:04.0: reg 14 io port: [0xc000-0xc007]
[    0.643031] pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
[    0.643089] pci 0000:01:04.0: PME# disabled
[    0.643178] pci 0000:01:06.0: reg 10 32bit mmio: [0xdc000000-0xdcffffff]
[    0.643187] pci 0000:01:06.0: reg 14 32bit mmio: [0xc0000000-0xcfffffff]
[    0.643196] pci 0000:01:06.0: reg 18 32bit mmio: [0xdd000000-0xddffffff]
[    0.643220] pci 0000:01:06.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.643268] pci 0000:01:09.0: reg 10 32bit mmio: [0xdf010000-0xdf011fff]
[    0.643303] pci 0000:01:09.0: reg 30 32bit mmio: [0x000000-0x003fff]
[    0.643315] pci 0000:01:09.0: supports D1 D2
[    0.643318] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.643378] pci 0000:01:09.0: PME# disabled
[    0.643466] pci 0000:00:1e.0: transparent bridge
[    0.643524] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.643530] pci 0000:00:1e.0: bridge 32bit mmio: [0xdc000000-0xdfffffff]
[    0.643537] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.643549] bus 00 -> node 0
[    0.643560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.643983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.668435] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.669110] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.669780] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.670449] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.671121] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.671873] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.672605] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.673356] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.674179] usbcore: registered new interface driver usbfs
[    0.674261] usbcore: registered new interface driver hub
[    0.674353] usbcore: registered new device driver usb
[    0.674514] PCI: Using ACPI for IRQ routing
[    0.674723] NET: Registered protocol family 8
[    0.674778] NET: Registered protocol family 20
[    0.674946] AppArmor: AppArmor Filesystem Enabled
[    0.675023] pnp: PnP ACPI init
[    0.676021] ACPI: bus type pnp registered
[    0.680142] pnp: PnP ACPI: found 12 devices
[    0.680200] ACPI: ACPI bus type pnp unregistered
[    0.680257] PnPBIOS: Disabled by ACPI PNP
[    0.680324] system 00:00: iomem range 0xcc000-0xcffff has been reserved
[    0.680382] system 00:00: iomem range 0xd5800-0xd7fff has been reserved
[    0.680440] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[    0.680499] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.680557] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved
[    0.680627] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.680685] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved
[    0.680755] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.680814] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.680873] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.680933] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.680992] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.681056] system 00:02: ioport range 0x400-0x4bf could not be reserved
[    0.681119] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.681177] system 00:03: ioport range 0x800-0x87f has been reserved
[    0.716064] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.716124] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.716183] pci 0000:00:1e.0:   MEM window: 0xdc000000-0xdfffffff
[    0.716243] pci 0000:00:1e.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.716327] pci 0000:00:1e.0: setting latency timer to 64
[    0.716334] bus: 00 index 0 io port: [0x00-0xffff]
[    0.716390] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.716445] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.716499] bus: 01 index 1 mmio: [0xdc000000-0xdfffffff]
[    0.716555] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.716611] bus: 01 index 3 io port: [0x00-0xffff]
[    0.716665] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.716732] NET: Registered protocol family 2
[    0.716943] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.717489] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.718876] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.719361] TCP: Hash tables configured (established 131072 bind 65536)
[    0.719419] TCP reno registered
[    0.719651] NET: Registered protocol family 1
[    0.719955] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.239910]  it is
[    1.813280] Freeing initrd memory: 8745k freed
[    1.813415] Simple Boot Flag at 0x59 set to 0x1
[    1.813729] audit: initializing netlink socket (disabled)
[    1.813812] type=2000 audit(1244746705.812:1): initialized
[    1.821759] highmem bounce pool size: 64 pages
[    1.823498] VFS: Disk quotas dquot_6.5.1
[    1.823590] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.823717] fuse init (API version 7.10)
[    1.823898] msgmni has been set to 1747
[    1.824204] alg: No test for stdrng (krng)
[    1.824274] io scheduler noop registered
[    1.824328] io scheduler anticipatory registered
[    1.824382] io scheduler deadline registered
[    1.824457] io scheduler cfq registered (default)
[    1.824530] pci 0000:00:02.0: Boot video device
[    1.828532] isapnp: Scanning for PnP cards...
[    2.182634] isapnp: No Plug & Play device found
[    2.184300] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.184463] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.185030] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.186127] brd: module loaded
[    2.186223] Fixed MDIO Bus: probed
[    2.186341] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.186434] Uniform Multi-Platform E-IDE driver
[    2.186582] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.186685] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.186775] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.186781] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.186923] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.190907] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.190925] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe0080000
[    2.204009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.204190] usb usb1: configuration #1 chosen from 1 choice
[    2.204288] hub 1-0:1.0: USB hub found
[    2.204351] hub 1-0:1.0: 6 ports detected
[    2.204571] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.204646] uhci_hcd: USB Universal Host Controller Interface driver
[    2.204753] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.204820] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.204825] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.204947] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.205045] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[    2.205207] usb usb2: configuration #1 chosen from 1 choice
[    2.205301] hub 2-0:1.0: USB hub found
[    2.205361] hub 2-0:1.0: 2 ports detected
[    2.205542] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.205606] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.205611] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.205726] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.205821] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
[    2.205979] usb usb3: configuration #1 chosen from 1 choice
[    2.206070] hub 3-0:1.0: USB hub found
[    2.206133] hub 3-0:1.0: 2 ports detected
[    2.206303] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.206367] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.206372] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.206486] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.206581] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[    2.206752] usb usb4: configuration #1 chosen from 1 choice
[    2.206843] hub 4-0:1.0: USB hub found
[    2.206904] hub 4-0:1.0: 2 ports detected
[    2.207130] usbcore: registered new interface driver libusual
[    2.207251] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.207309] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.207910] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.208123] mice: PS/2 mouse device common for all mice
[    2.208243] EISA: Probing bus 0 at eisa.0
[    2.208335] EISA: Detected 0 cards.
[    2.208390] cpuidle: using governor ladder
[    2.209122] TCP cubic registered
[    2.209225] Using IPI Shortcut mode
[    2.209394] registered taskstats version 1
[    2.209618] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.209676] EDD information not available.
[    2.210425] Freeing unused kernel memory: 440k freed
[    2.252519] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.648388] processor ACPI_CPU:00: registered as cooling_device0
[    2.648397] ACPI: Processor [CPU0] (supports 2 throttling states)
[    2.684032] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    2.702769] device-mapper: uevent: version 1.0.3
[    2.702927] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.781146] md: linear personality registered for level -1
[    2.785945] md: multipath personality registered for level -4
[    2.815193] md: raid0 personality registered for level 0
[    2.838847] md: raid1 personality registered for level 1
[    2.870471] xor: automatically using best checksumming function: pIII_sse
[    2.888009]    pIII_sse  :  2260.000 MB/sec
[    2.888013] xor: using function: pIII_sse (2260.000 MB/sec)
[    2.901790] async_tx: api initialized (async)
[    2.976066] raid6: int32x1    499 MB/s
[    3.044030] raid6: int32x2    571 MB/s
[    3.112044] raid6: int32x4    577 MB/s
[    3.180016] raid6: int32x8    406 MB/s
[    3.248047] raid6: mmxx1     1489 MB/s
[    3.316029] raid6: mmxx2     1874 MB/s
[    3.384021] raid6: sse1x1     878 MB/s
[    3.452043] raid6: sse1x2    1606 MB/s
[    3.520028] raid6: sse2x1    1808 MB/s
[    3.588006] raid6: sse2x2    1943 MB/s
[    3.588011] raid6: using algorithm sse2x2 (1943 MB/s)
[    3.588018] md: raid6 personality registered for level 6
[    3.588022] md: raid5 personality registered for level 5
[    3.588025] md: raid4 personality registered for level 4
[    3.674074] usb 1-4: configuration #1 chosen from 1 choice
[    3.912015] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.095811] usb 2-1: configuration #1 chosen from 1 choice
[    4.337637] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.337745] md: raid10 personality registered for level 10
[    4.507540] usb 3-1: configuration #1 chosen from 1 choice
[    4.705830] Floppy drive(s): fd0 is 1.44M
[    4.723820] FDC 0 is a post-1991 82077
[    4.973792] usbcore: registered new interface driver hiddev
[    4.989812] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    5.004183] generic-usb 0003:1267:0212.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1/input0
[    5.004216] usbcore: registered new interface driver usbhid
[    5.004222] usbhid: v2.6:USB HID core driver
[    5.192266] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.212138] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    5.212150] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    5.212158] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[    5.251300] ssb: SPROM revision 1 detected.
[    5.268139] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    5.268174] b44.c:v2.0
[    5.276598] SCSI subsystem initialized
[    5.306602] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:08:74:bc:c7:f1
[    5.337278] libata version 3.00 loaded.
[    5.341783] ata_piix 0000:00:1f.1: version 2.12
[    5.341807] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.341883] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.352040] scsi0 : ata_piix
[    5.353800] scsi1 : ata_piix
[    5.355302] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    5.355307] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    5.524505] ata1.00: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[    5.524513] ata1.00: 80293248 sectors, multi 16: LBA 
[    5.525668] ata1.01: ATA-6: WDC WD2000JB-00EVA0, 15.05R15, max UDMA/100
[    5.525676] ata1.01: 390721968 sectors, multi 16: LBA48 
[    5.540464] ata1.00: configured for UDMA/100
[    5.557450] ata1.01: configured for UDMA/100
[    5.728406] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, B105, max UDMA/33
[    5.728474] ata2.01: ATAPI: HL-DT-ST GCE-8400B, B104, max UDMA/33
[    5.736462] ata2.00: configured for UDMA/33
[    5.752342] ata2.01: configured for UDMA/33
[    5.752941] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    5.753156] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2000JB-00E 15.0 PQ: 0 ANSI: 5
[    5.753464] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B105 PQ: 0 ANSI: 5
[    5.753832] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  B104 PQ: 0 ANSI: 5
[    6.736128] Driver 'sd' needs updating - please use bus_type methods
[    6.736280] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    6.736306] sd 0:0:0:0: [sda] Write Protect is off
[    6.736311] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.736349] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.736443] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    6.736465] sd 0:0:0:0: [sda] Write Protect is off
[    6.736469] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.736506] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.736512]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.448093]  sda1 sda2
[    7.448310] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.448445] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    7.448472] sd 0:0:1:0: [sdb] Write Protect is off
[    7.448476] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    7.448515] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.449712] sd 0:0:1:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    7.449763] sd 0:0:1:0: [sdb] Write Protect is off
[    7.449768] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    7.449806] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.449814]  sdb: sdb1 sdb2 sdb3
[    7.468061] sd 0:0:1:0: [sdb] Attached SCSI disk
[    7.475851] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.475895] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    7.475933] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    7.475971] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    7.477447] sr0: scsi3-mmc drive: 40x/48x cd/rw xa/form2 cdda tray
[    7.477457] Uniform CD-ROM driver Revision: 3.20
[    7.477615] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.479592] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    7.479696] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    8.312029] kjournald starting.  Commit interval 5 seconds
[    8.312055] EXT3-fs: mounted filesystem with ordered data mode.
[   17.649642] udev: starting version 141
[   17.949578] Linux agpgart interface v0.103
[   17.961318] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   17.961616] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   17.964324] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd0000000
[   17.972807] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   17.992055] ACPI: Power Button (FF) [PWRF]
[   17.992297] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   18.012040] ACPI: Power Button (CM) [PWRB]
[   18.069186] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.069217] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   18.222882] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7404
[   18.222922] usbcore: registered new interface driver usblp
[   18.512111] cfg80211: Calling CRDA to update world regulatory domain
[   18.567735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.572443] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.585431] intel_rng: FWH not detected
[   18.650452] iTCO_vendor_support: vendor-support=0
[   18.653026] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   18.653203] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   18.653328] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.768908] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   18.768919] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   18.768992] usbcore: registered new interface driver rt2500usb
[   19.060272] phy1: Selected rate control algorithm 'pid'
[   19.319062] Registered led device: rt73usb-phy1:radio
[   19.319129] Registered led device: rt73usb-phy1:assoc
[   19.319194] Registered led device: rt73usb-phy1:quality
[   19.321030] usbcore: registered new interface driver rt73usb
[   19.469804] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.469922] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.754459] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.892034] intel8x0_measure_ac97_clock: measured 54867 usecs
[   19.892041] intel8x0: clocking to 48000
[   20.642762] ppdev: user-space parallel port driver
[   20.866177] cfg80211: World regulatory domain updated:
[   20.866187] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.866193] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.866197] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.866202] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.866206] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.866210] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.898872] Intel ISA PCIC probe: not found.
[   22.020390] lp0: using parport0 (interrupt-driven).
[   23.293569] Adding 979924k swap on /dev/sdb1.  Priority:-1 extents:1 across:979924k
[   24.043425] EXT3 FS on sdb2, internal journal
[   26.044024] kjournald starting.  Commit interval 5 seconds
[   26.044426] EXT3 FS on sdb3, internal journal
[   26.044434] EXT3-fs: mounted filesystem with ordered data mode.
[   26.791263] type=1505 audit(1244746730.788:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2048
[   26.874149] type=1505 audit(1244746730.872:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2052
[   26.874461] type=1505 audit(1244746730.872:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2052
[   26.874552] type=1505 audit(1244746730.872:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2052
[   26.874634] type=1505 audit(1244746730.872:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2052
[   27.105769] type=1505 audit(1244746731.104:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2057
[   27.106170] type=1505 audit(1244746731.104:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2057
[   27.156761] type=1505 audit(1244746731.156:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2061
[   32.712583] Bluetooth: Core ver 2.13
[   32.738241] NET: Registered protocol family 31
[   32.738247] Bluetooth: HCI device and connection manager initialized
[   32.738253] Bluetooth: HCI socket layer initialized
[   32.835043] Bluetooth: L2CAP ver 2.11
[   32.835048] Bluetooth: L2CAP socket layer initialized
[   32.969963] Bluetooth: RFCOMM socket layer initialized
[   32.969986] Bluetooth: RFCOMM TTY layer initialized
[   32.969989] Bluetooth: RFCOMM ver 1.10
[   32.979627] Bluetooth: SCO (Voice Link) ver 0.6
[   32.979632] Bluetooth: SCO socket layer initialized
[   32.994960] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.994966] Bluetooth: BNEP filters: protocol multicast
[   33.082633] Bridge firewalling registered
[   37.015925] ppdev0: registered pardevice
[   37.064825] ppdev0: unregistered pardevice

```

Thanks,
Tars

---

### Post by tars_ac on 2009-06-13
Anyone have any ideas?

Thanks.

---

### Post by tars_ac on 2009-06-13
Aha!

The problem was that my computer was still loading the integrated graphics driver, which apparently conflicts with the nvidia driver.  Adding "blacklist intel_agp" to /etc/modprobe.d/blacklist.conf file made it boot with no issues at all.  Haven't tried using the actual 3d effects or anything, but at this point just booting makes me happy.

Also, it turns out that there's a better way to install nvidia graphics drivers, unless you really need the bleeding edge from nvidia.  Just go to System->Administration->Hardware Drivers and it will do it for you (although you will still need to potentially blacklist your integrated graphics).  To find out what to blacklist, you can do "lsmod" on a terminal and look for something that seems like it might be your integrated graphics.

I know it seems silly that I didn't know about "Hardware Drivers", but it didn't exactly jump out at me that I would have to do that.  I hope this helps someone else with the same problem.

---

### Post by scgauvin on 2009-11-16
Thanks for posting your experience.  I had the same problem and this solved it for me. Thanks for sharing; saved me a lot of time and frustration!  :D

---


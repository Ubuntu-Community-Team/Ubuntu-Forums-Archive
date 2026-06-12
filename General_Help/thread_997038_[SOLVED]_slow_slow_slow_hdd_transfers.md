---
title: "[SOLVED] slow slow slow hdd transfers"
date: 2008-11-29
forum: General Help
---

### Post by moosefist on 2008-11-29
I am posting this from a SAW linux boot cd because my Ubuntu Intrepid install was completely incapable of transfering the files.

In my PC i have a 750 GB, and 250 GB IDE harddrives, and i have a 1tb, 2 x 500gb SATA harddrives.  I am trying to eliminate the 750gb HD so i can use it in another project, but when transfering the files to the 1tb drive in ubuntu the speeds start out at about 40MB/s and steadily drop to about 100kb/s and my whole comp becomes unrecoverably slow.

In the SAW linux boot cd the transfer stays at a constant 25MB/s and i can do other things (like write this post)  all of which seemed impossible in ubuntu.

A matter of fact in order not to get kicked out to Busybox during the boot process in ubuntu when i have my SATA controller active I have to add "all_generic_ide floppy=off irqpoll" to my boot arguments in GRUB.

Could that be my problem, because thats the only way i can get into ubuntu, other than waiting 5 minutes and typing exit into busybox.

Any suggestions for fixes, even if that means another distro i am open to.  I just cant deal with a 100Kb file transfer that locks up my comp to an unusable state.

---

### Post by moosefist on 2008-12-01
any ideas?

---

### Post by lavinog on 2008-12-01
I don't have a solution, but I would think that posting output of dmesg might help

---

### Post by moosefist on 2008-12-01
Here my dmesg comes,  its very long and if there is anything i need to remove for security reasons  someone please let me know.  Also if there is anything that just needs to be removed for size let me know.  I havent every read through one of these and i am not exactly sure what it contains.

Thanks for the suggestion.

---

### Post by moosefist on 2008-12-01
Dec  1 21:16:06 raul-desktop syslogd 1.5.0#2ubuntu6: restart.
Dec  1 21:16:06 raul-desktop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec  1 21:16:06 raul-desktop kernel: Cannot find map file.
Dec  1 21:16:06 raul-desktop kernel: Loaded 65311 symbols from 81 modules.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0001000 (reserved)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] last_pfn = 0x3fee0 max_arch_pfn = 0x100000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] RAMDISK: 37831000 - 37fef704
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] DMI 2.3 present.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: RSDP 000F7790, 0024 (r2 K8T890)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: XSDT 3FEE30C0, 003C (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: FACP 3FEEA100, 00F4 (r3 K8T890 AWRDACPI 42302E31 AWRD        0)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: DSDT 3FEE3240, 6E57 (r1 K8T890 AWRDACPI     1000 MSFT  100000E)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: FACS 3FEE0000, 0040
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: MCFG 3FEEA300, 003C (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: APIC 3FEEA240, 0074 (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] 126MB HIGHMEM available.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] 896MB LOWMEM available.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   low ram: 00000000 - 38000000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #4 [0037831000 - 0037fef704]          RAMDISK ==> [0037831000 - 0037fef704]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] found SMP MP-table at [c00f5850] 000f5850
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Zone PFN ranges:
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0003fee0
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Movable zone start PFN for each node
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Dec  1 21:16:06 raul-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x0003fee0
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259457
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Kernel command line: root=UUID=f0a73b2a-3122-4b05-84b3-a2f2a1dd4931 ro quiet splash all_generic_ide floppy=off irqpoll 
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Misrouted IRQ fixup and polling support enabled
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] This may significantly impact system performance
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Initializing CPU#0
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Extended CMOS year: 2000
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] TSC: using PIT calibration value
Dec  1 21:16:06 raul-desktop kernel: [    0.000000] Detected 2000.009 MHz processor.
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Console: colour VGA+ 80x25
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] console [tty0] enabled
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Memory: 1023804k/1047424k available (2572k kernel code, 22952k reserved, 1160k data, 424k init, 129920k highmem)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] virtual kernel memory layout:
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec  1 21:16:06 raul-desktop kernel: [    0.004044] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.01 BogoMIPS (lpj=8000036)
Dec  1 21:16:06 raul-desktop kernel: [    0.004064] Security Framework initialized
Dec  1 21:16:06 raul-desktop kernel: [    0.004071] SELinux:  Disabled at boot.
Dec  1 21:16:06 raul-desktop kernel: [    0.004095] AppArmor: AppArmor initialized
Dec  1 21:16:06 raul-desktop kernel: [    0.004103] Mount-cache hash table entries: 512
Dec  1 21:16:06 raul-desktop kernel: [    0.004262] Initializing cgroup subsys ns
Dec  1 21:16:06 raul-desktop kernel: [    0.004266] Initializing cgroup subsys cpuacct
Dec  1 21:16:06 raul-desktop kernel: [    0.004269] Initializing cgroup subsys memory
Dec  1 21:16:06 raul-desktop kernel: [    0.004283] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  1 21:16:06 raul-desktop kernel: [    0.004285] CPU: L2 Cache: 256K (64 bytes/line)
Dec  1 21:16:06 raul-desktop kernel: [    0.004288] CPU 0(2) -> Core 0
Dec  1 21:16:06 raul-desktop kernel: [    0.004299] Checking 'hlt' instruction... OK.
Dec  1 21:16:06 raul-desktop kernel: [    0.021593] ACPI: Core revision 20080609
Dec  1 21:16:06 raul-desktop kernel: [    0.023912] ACPI: Checking initramfs for custom DSDT
Dec  1 21:16:06 raul-desktop kernel: [    0.364711] ENABLING IO-APIC IRQs
Dec  1 21:16:06 raul-desktop kernel: [    0.365031] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
Dec  1 21:16:06 raul-desktop kernel: [    0.405003] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 01
Dec  1 21:16:06 raul-desktop kernel: [    0.408025] Booting processor 1/1 ip 6000
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Initializing CPU#1
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 4000.38 BogoMIPS (lpj=8000777)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
Dec  1 21:16:06 raul-desktop kernel: [    0.004000] CPU 1(2) -> Core 1
Dec  1 21:16:06 raul-desktop kernel: [    0.492171] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 01
Dec  1 21:16:06 raul-desktop kernel: [    0.492200] Brought up 2 CPUs
Dec  1 21:16:06 raul-desktop kernel: [    0.492203] Total of 2 processors activated (8000.40 BogoMIPS).
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] net_namespace: 840 bytes
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] Booting paravirtualized kernel on bare hardware
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] Time:  3:15:43  Date: 12/02/08
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] NET: Registered protocol family 16
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] EISA bus registered
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] ACPI: bus type pci registered
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] PCI: MCFG area at e0000000 reserved in E820
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] PCI: Using MMCONFIG for extended config space
Dec  1 21:16:06 raul-desktop kernel: [    0.492354] PCI: Using configuration type 1 for base access
Dec  1 21:16:06 raul-desktop kernel: [    0.508694] ACPI: Interpreter enabled
Dec  1 21:16:06 raul-desktop kernel: [    0.508700] ACPI: (supports S0 S1 S3 S4 S5)
Dec  1 21:16:06 raul-desktop kernel: [    0.508720] ACPI: Using IOAPIC for interrupt routing
Dec  1 21:16:06 raul-desktop kernel: [    0.520576] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec  1 21:16:06 raul-desktop kernel: [    0.520576] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520576] pci 0000:00:02.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520576] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520576] pci 0000:00:03.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520602] pci 0000:00:03.1: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520606] pci 0000:00:03.1: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520654] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520659] pci 0000:00:03.2: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520707] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520711] pci 0000:00:03.3: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520820] pci 0000:00:0f.0: PME# supported from D3hot
Dec  1 21:16:06 raul-desktop kernel: [    0.520825] pci 0000:00:0f.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.520966] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.520971] pci 0000:00:10.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.521041] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.521045] pci 0000:00:10.1: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.521114] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.521118] pci 0000:00:10.2: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.521186] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.521191] pci 0000:00:10.3: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.521268] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.521273] pci 0000:00:10.4: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.521470] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.521474] pci 0000:00:12.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.522030] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.522034] pci 0000:07:00.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524043] pci 0000:07:00.1: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.524047] pci 0000:07:00.1: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524121] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
Dec  1 21:16:06 raul-desktop kernel: [    0.524125] pci 0000:07:01.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524362] pci 0000:0a:0d.0: PME# supported from D0 D1 D2 D3hot
Dec  1 21:16:06 raul-desktop kernel: [    0.524367] pci 0000:0a:0d.0: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524435] pci 0000:0a:0d.1: PME# supported from D0 D1 D2 D3hot
Dec  1 21:16:06 raul-desktop kernel: [    0.524439] pci 0000:0a:0d.1: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524507] pci 0000:0a:0d.2: PME# supported from D0 D1 D2 D3hot
Dec  1 21:16:06 raul-desktop kernel: [    0.524511] pci 0000:0a:0d.2: PME# disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.524541] pci 0000:00:13.1: transparent bridge
Dec  1 21:16:06 raul-desktop kernel: [    0.652367] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
Dec  1 21:16:06 raul-desktop kernel: [    0.652524] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 6 7 10 11 12)
Dec  1 21:16:06 raul-desktop kernel: [    0.652775] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Dec  1 21:16:06 raul-desktop kernel: [    0.653026] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)
Dec  1 21:16:06 raul-desktop kernel: [    0.653245] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  1 21:16:06 raul-desktop kernel: [    0.653458] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  1 21:16:06 raul-desktop kernel: [    0.653670] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Dec  1 21:16:06 raul-desktop kernel: [    0.653904] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 *11 12)
Dec  1 21:16:06 raul-desktop kernel: [    0.656083] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec  1 21:16:06 raul-desktop kernel: [    0.656096] pnp: PnP ACPI init
Dec  1 21:16:06 raul-desktop kernel: [    0.656096] ACPI: bus type pnp registered
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xccc00-0xcffff) overlaps 0000:00:03.0 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf0000-0xf7fff) overlaps 0000:00:03.0 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf8000-0xfbfff) overlaps 0000:00:03.0 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xfc000-0xfffff) overlaps 0000:00:03.0 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0x0-0x9ffff) overlaps 0000:00:03.0 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xccc00-0xcffff) overlaps 0000:00:03.1 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf0000-0xf7fff) overlaps 0000:00:03.1 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf8000-0xfbfff) overlaps 0000:00:03.1 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xfc000-0xfffff) overlaps 0000:00:03.1 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0x0-0x9ffff) overlaps 0000:00:03.1 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xccc00-0xcffff) overlaps 0000:00:03.2 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf0000-0xf7fff) overlaps 0000:00:03.2 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf8000-0xfbfff) overlaps 0000:00:03.2 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xfc000-0xfffff) overlaps 0000:00:03.2 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0x0-0x9ffff) overlaps 0000:00:03.2 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xccc00-0xcffff) overlaps 0000:00:03.3 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf0000-0xf7fff) overlaps 0000:00:03.3 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xf8000-0xfbfff) overlaps 0000:00:03.3 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0xfc000-0xfffff) overlaps 0000:00:03.3 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp 00:0e: mem resource (0x0-0x9ffff) overlaps 0000:00:03.3 BAR 8 (0x0-0xfffff), disabling
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] pnp: PnP ACPI: found 15 devices
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] ACPI: ACPI bus type pnp unregistered
Dec  1 21:16:06 raul-desktop kernel: [    0.661271] PnPBIOS: Disabled by ACPI PNP
Dec  1 21:16:06 raul-desktop kernel: [    0.664052] PCI: Using ACPI for IRQ routing
Dec  1 21:16:06 raul-desktop kernel: [    0.664052] pci 0000:00:03.0: BAR 8: can't allocate resource
Dec  1 21:16:06 raul-desktop kernel: [    0.664052] pci 0000:00:03.1: BAR 8: can't allocate resource
Dec  1 21:16:06 raul-desktop kernel: [    0.664052] pci 0000:00:03.2: BAR 8: can't allocate resource
Dec  1 21:16:06 raul-desktop kernel: [    0.664052] pci 0000:00:03.3: BAR 8: can't allocate resource
Dec  1 21:16:06 raul-desktop kernel: [    0.672041] NET: Registered protocol family 8
Dec  1 21:16:06 raul-desktop kernel: [    0.672044] NET: Registered protocol family 20
Dec  1 21:16:06 raul-desktop kernel: [    0.672074] NetLabel: Initializing
Dec  1 21:16:06 raul-desktop kernel: [    0.672076] NetLabel:  domain hash size = 128
Dec  1 21:16:06 raul-desktop kernel: [    0.672078] NetLabel:  protocols = UNLABELED CIPSOv4
Dec  1 21:16:06 raul-desktop kernel: [    0.672093] NetLabel:  unlabeled traffic allowed by default
Dec  1 21:16:06 raul-desktop kernel: [    0.672674] tracer: 772 pages allocated for 65536 entries of 48 bytes
Dec  1 21:16:06 raul-desktop kernel: [    0.672677]    actual entries 65620
Dec  1 21:16:06 raul-desktop kernel: [    0.672810] AppArmor: AppArmor Filesystem Enabled
Dec  1 21:16:06 raul-desktop kernel: [    0.672830] ACPI: RTC can wake from S4
Dec  1 21:16:06 raul-desktop kernel: [    0.680064] system 00:01: ioport range 0x400-0x47f has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680067] system 00:01: ioport range 0x500-0x50f has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680075] system 00:02: iomem range 0x10000000-0x10000fff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680083] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680086] system 00:03: ioport range 0x290-0x29f has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680089] system 00:03: ioport range 0x800-0x805 has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680092] system 00:03: ioport range 0x290-0x297 has been reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680105] system 00:0d: iomem range 0xe0000000-0xf0000fff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680113] system 00:0e: iomem range 0x3fef0000-0x3ffeffff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680117] system 00:0e: iomem range 0x3fee0000-0x3fefffff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680121] system 00:0e: iomem range 0xffff0000-0xffffffff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680125] system 00:0e: iomem range 0x100000-0x3fedffff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680128] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680131] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.680135] system 00:0e: iomem range 0xfff80000-0xfffeffff could not be reserved
Dec  1 21:16:06 raul-desktop kernel: [    0.715334] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec  1 21:16:06 raul-desktop kernel: [    0.715337] pci 0000:00:01.0:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715342] pci 0000:00:01.0:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715346] pci 0000:00:01.0:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715353] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
Dec  1 21:16:06 raul-desktop kernel: [    0.715356] pci 0000:00:02.0:   IO window: 0xe000-0xefff
Dec  1 21:16:06 raul-desktop kernel: [    0.715362] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
Dec  1 21:16:06 raul-desktop kernel: [    0.715367] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
Dec  1 21:16:06 raul-desktop kernel: [    0.715374] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
Dec  1 21:16:06 raul-desktop kernel: [    0.715376] pci 0000:00:03.0:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715381] pci 0000:00:03.0:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715385] pci 0000:00:03.0:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715392] pci 0000:00:03.1: PCI bridge, secondary bus 0000:04
Dec  1 21:16:06 raul-desktop kernel: [    0.715394] pci 0000:00:03.1:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715399] pci 0000:00:03.1:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715403] pci 0000:00:03.1:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715410] pci 0000:00:03.2: PCI bridge, secondary bus 0000:05
Dec  1 21:16:06 raul-desktop kernel: [    0.715412] pci 0000:00:03.2:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715418] pci 0000:00:03.2:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715422] pci 0000:00:03.2:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715428] pci 0000:00:03.3: PCI bridge, secondary bus 0000:06
Dec  1 21:16:06 raul-desktop kernel: [    0.715430] pci 0000:00:03.3:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715436] pci 0000:00:03.3:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715440] pci 0000:00:03.3:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715447] pci 0000:07:00.0: PCI bridge, secondary bus 0000:08
Dec  1 21:16:06 raul-desktop kernel: [    0.715449] pci 0000:07:00.0:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715454] pci 0000:07:00.0:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715457] pci 0000:07:00.0:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715463] pci 0000:07:00.1: PCI bridge, secondary bus 0000:09
Dec  1 21:16:06 raul-desktop kernel: [    0.715465] pci 0000:07:00.1:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715470] pci 0000:07:00.1:   MEM window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715473] pci 0000:07:00.1:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715479] pci 0000:00:13.0: PCI bridge, secondary bus 0000:07
Dec  1 21:16:06 raul-desktop kernel: [    0.715481] pci 0000:00:13.0:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715486] pci 0000:00:13.0:   MEM window: 0xfde00000-0xfdefffff
Dec  1 21:16:06 raul-desktop kernel: [    0.715490] pci 0000:00:13.0:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715496] pci 0000:00:13.1: PCI bridge, secondary bus 0000:0a
Dec  1 21:16:06 raul-desktop kernel: [    0.715498] pci 0000:00:13.1:   IO window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715503] pci 0000:00:13.1:   MEM window: 0xfdd00000-0xfddfffff
Dec  1 21:16:06 raul-desktop kernel: [    0.715507] pci 0000:00:13.1:   PREFETCH window: disabled
Dec  1 21:16:06 raul-desktop kernel: [    0.715537] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
Dec  1 21:16:06 raul-desktop kernel: [    0.715552] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31
Dec  1 21:16:06 raul-desktop kernel: [    0.715567] pci 0000:00:03.1: PCI INT B -> GSI 35 (level, low) -> IRQ 35
Dec  1 21:16:06 raul-desktop kernel: [    0.715583] pci 0000:00:03.2: PCI INT C -> GSI 39 (level, low) -> IRQ 39
Dec  1 21:16:06 raul-desktop kernel: [    0.715598] pci 0000:00:03.3: PCI INT D -> GSI 43 (level, low) -> IRQ 43
Dec  1 21:16:06 raul-desktop kernel: [    0.715621] pci 0000:07:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec  1 21:16:06 raul-desktop kernel: [    0.715638] pci 0000:07:00.1: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec  1 21:16:06 raul-desktop kernel: [    0.715658] bus: 00 index 0 io port: [0, ffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715661] bus: 00 index 1 mmio: [0, ffffffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715663] bus: 01 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715665] bus: 01 index 1 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715667] bus: 01 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715670] bus: 01 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715672] bus: 02 index 0 io port: [e000, efff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715674] bus: 02 index 1 mmio: [f8000000, fbffffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715676] bus: 02 index 2 mmio: [c0000000, cfffffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715679] bus: 02 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715681] bus: 03 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715683] bus: 03 index 1 mmio: [0, fffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715685] bus: 03 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715687] bus: 03 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715689] bus: 04 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715692] bus: 04 index 1 mmio: [0, fffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715694] bus: 04 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715696] bus: 04 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715698] bus: 05 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715700] bus: 05 index 1 mmio: [0, fffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715702] bus: 05 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715704] bus: 05 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715706] bus: 06 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715708] bus: 06 index 1 mmio: [0, fffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715710] bus: 06 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715712] bus: 06 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715715] bus: 07 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715717] bus: 07 index 1 mmio: [fde00000, fdefffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715719] bus: 07 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715721] bus: 07 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715723] bus: 08 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715725] bus: 08 index 1 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715727] bus: 08 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715729] bus: 08 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715731] bus: 09 index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715734] bus: 09 index 1 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715736] bus: 09 index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715738] bus: 09 index 3 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715740] bus: 0a index 0 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715742] bus: 0a index 1 mmio: [fdd00000, fddfffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715744] bus: 0a index 2 mmio: [0, 0]
Dec  1 21:16:06 raul-desktop kernel: [    0.715747] bus: 0a index 3 io port: [0, ffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715749] bus: 0a index 4 mmio: [0, ffffffff]
Dec  1 21:16:06 raul-desktop kernel: [    0.715763] NET: Registered protocol family 2
Dec  1 21:16:06 raul-desktop kernel: [    0.728067] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.728359] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.729038] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    0.729376] TCP: Hash tables configured (established 131072 bind 65536)
Dec  1 21:16:06 raul-desktop kernel: [    0.729381] TCP reno registered
Dec  1 21:16:06 raul-desktop kernel: [    0.736091] NET: Registered protocol family 1
Dec  1 21:16:06 raul-desktop kernel: [    0.736218] checking if image is initramfs... it is
Dec  1 21:16:06 raul-desktop kernel: [    1.428382] Freeing initrd memory: 7929k freed
Dec  1 21:16:06 raul-desktop kernel: [    1.429600] audit: initializing netlink socket (disabled)
Dec  1 21:16:06 raul-desktop kernel: [    1.429622] type=2000 audit(1228187743.428:1): initialized
Dec  1 21:16:06 raul-desktop kernel: [    1.435702] highmem bounce pool size: 64 pages
Dec  1 21:16:06 raul-desktop kernel: [    1.435708] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec  1 21:16:06 raul-desktop kernel: [    1.438299] VFS: Disk quotas dquot_6.5.1
Dec  1 21:16:06 raul-desktop kernel: [    1.438413] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec  1 21:16:06 raul-desktop kernel: [    1.438538] msgmni has been set to 1761
Dec  1 21:16:06 raul-desktop kernel: [    1.438674] io scheduler noop registered
Dec  1 21:16:06 raul-desktop kernel: [    1.438677] io scheduler anticipatory registered
Dec  1 21:16:06 raul-desktop kernel: [    1.438679] io scheduler deadline registered
Dec  1 21:16:06 raul-desktop kernel: [    1.438692] io scheduler cfq registered (default)
Dec  1 21:16:06 raul-desktop kernel: [    1.438711] PCI: VIA PCI bridge detected.Disabling DAC.
Dec  1 21:16:06 raul-desktop kernel: [    1.439051] pcieport-driver 0000:00:02.0: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.439383] pcieport-driver 0000:00:03.0: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.439695] pcieport-driver 0000:00:03.1: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.440012] pcieport-driver 0000:00:03.2: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.440471] pcieport-driver 0000:00:03.3: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.440833] pcieport-driver 0000:07:00.0: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.441125] pcieport-driver 0000:07:00.1: found MSI capability
Dec  1 21:16:06 raul-desktop kernel: [    1.442457] isapnp: Scanning for PnP cards...
Dec  1 21:16:06 raul-desktop kernel: [    1.796410] isapnp: No Plug & Play device found
Dec  1 21:16:06 raul-desktop kernel: [    1.838691] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Dec  1 21:16:06 raul-desktop kernel: [    1.838838] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  1 21:16:06 raul-desktop kernel: [    1.839688] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec  1 21:16:06 raul-desktop kernel: [    1.841910] brd: module loaded
Dec  1 21:16:06 raul-desktop kernel: [    1.841994] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec  1 21:16:06 raul-desktop kernel: [    1.842133] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec  1 21:16:06 raul-desktop kernel: [    1.842136] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Dec  1 21:16:06 raul-desktop kernel: [    1.842307] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec  1 21:16:06 raul-desktop kernel: [    1.845149] mice: PS/2 mouse device common for all mice
Dec  1 21:16:06 raul-desktop kernel: [    1.845303] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Dec  1 21:16:06 raul-desktop kernel: [    1.845343] rtc0: alarms up to one year, y3k
Dec  1 21:16:06 raul-desktop kernel: [    1.845524] EISA: Probing bus 0 at eisa.0
Dec  1 21:16:06 raul-desktop kernel: [    1.845564] EISA: Detected 0 cards.
Dec  1 21:16:06 raul-desktop kernel: [    1.845568] cpuidle: using governor ladder
Dec  1 21:16:06 raul-desktop kernel: [    1.845571] cpuidle: using governor menu
Dec  1 21:16:06 raul-desktop kernel: [    1.846080] TCP cubic registered
Dec  1 21:16:06 raul-desktop kernel: [    1.846111] Using IPI No-Shortcut mode
Dec  1 21:16:06 raul-desktop kernel: [    1.846381] registered taskstats version 1
Dec  1 21:16:06 raul-desktop kernel: [    1.846556]   Magic number: 4:221:259
Dec  1 21:16:06 raul-desktop kernel: [    1.846588] tty ttyx1: hash matches
Dec  1 21:16:06 raul-desktop kernel: [    1.846755] rtc_cmos 00:05: setting system clock to 2008-12-02 03:15:44 UTC (1228187744)
Dec  1 21:16:06 raul-desktop kernel: [    1.846759] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec  1 21:16:06 raul-desktop kernel: [    1.846761] EDD information not available.
Dec  1 21:16:06 raul-desktop kernel: [    1.847039] Freeing unused kernel memory: 424k freed
Dec  1 21:16:06 raul-desktop kernel: [    1.847106] Write protecting the kernel text: 2576k
Dec  1 21:16:06 raul-desktop kernel: [    1.847147] Write protecting the kernel read-only data: 936k
Dec  1 21:16:06 raul-desktop kernel: [    1.870614] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec  1 21:16:06 raul-desktop kernel: [    1.911450] No dock devices found.
Dec  1 21:16:06 raul-desktop kernel: [    1.925199] SCSI subsystem initialized
Dec  1 21:16:06 raul-desktop kernel: [    1.942720] ata_generic 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec  1 21:16:06 raul-desktop kernel: [    1.942839] scsi0 : ata_generic
Dec  1 21:16:06 raul-desktop kernel: [    1.943005] scsi1 : ata_generic
Dec  1 21:16:06 raul-desktop kernel: [    1.945275] ata1: PATA max UDMA/100 cmd 0xff00 ctl 0xfe00 bmdma 0xfb00 irq 21
Dec  1 21:16:06 raul-desktop kernel: [    1.945278] ata2: PATA max UDMA/100 cmd 0xfd00 ctl 0xfc00 bmdma 0xfb08 irq 21
Dec  1 21:16:06 raul-desktop kernel: [    2.132336] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01109, max UDMA7
Dec  1 21:16:06 raul-desktop kernel: [    2.132341] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  1 21:16:06 raul-desktop kernel: [    2.132352] ata1.00: configured for UDMA7
Dec  1 21:16:06 raul-desktop kernel: [    2.336787] ata2.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max UDMA/133
Dec  1 21:16:06 raul-desktop kernel: [    2.336790] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  1 21:16:06 raul-desktop kernel: [    2.336921] ata2.01: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
Dec  1 21:16:06 raul-desktop kernel: [    2.336925] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  1 21:16:06 raul-desktop kernel: [    2.336935] ata2.00: configured for UDMA/133
Dec  1 21:16:06 raul-desktop kernel: [    2.336937] ata2.01: configured for UDMA7
Dec  1 21:16:06 raul-desktop kernel: [    2.337055] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.337335] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.337553] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.337872] scsi2 : ata_generic
Dec  1 21:16:06 raul-desktop kernel: [    2.338018] scsi3 : ata_generic
Dec  1 21:16:06 raul-desktop kernel: [    2.340874] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Dec  1 21:16:06 raul-desktop kernel: [    2.340877] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Dec  1 21:16:06 raul-desktop kernel: [    2.555980] ata3.00: ATA-7: ST3750640A, 3.AAE, max UDMA/100
Dec  1 21:16:06 raul-desktop kernel: [    2.555983] ata3.00: 1465149168 sectors, multi 16: LBA48 
Dec  1 21:16:06 raul-desktop kernel: [    2.581150] ata3.01: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
Dec  1 21:16:06 raul-desktop kernel: [    2.581153] ata3.01: 488397168 sectors, multi 16: LBA48 
Dec  1 21:16:06 raul-desktop kernel: [    2.581163] ata3.00: configured for UDMA/100
Dec  1 21:16:06 raul-desktop kernel: [    2.581165] ata3.01: configured for UDMA/100
Dec  1 21:16:06 raul-desktop kernel: [    2.752272] ata4.00: ATAPI: SONY    DVD RW AW-Q170A, 1.70, max UDMA/66
Dec  1 21:16:06 raul-desktop kernel: [    2.752289] ata4.01: ATAPI: PLEXTOR CD-R   PX-W4012A, 1.05, max UDMA/33
Dec  1 21:16:06 raul-desktop kernel: [    2.752299] ata4.00: configured for UDMA/66
Dec  1 21:16:06 raul-desktop kernel: [    2.752301] ata4.01: configured for UDMA/33
Dec  1 21:16:06 raul-desktop kernel: [    2.752400] scsi 2:0:0:0: Direct-Access     ATA      ST3750640A       3.AA PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.752627] scsi 2:0:1:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.754074] scsi 3:0:0:0: CD-ROM            SONY     DVD RW AW-Q170A  1.70 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.754964] scsi 3:0:1:0: CD-ROM            PLEXTOR  CD-R   PX-W4012A 1.05 PQ: 0 ANSI: 5
Dec  1 21:16:06 raul-desktop kernel: [    2.829225] fuse init (API version 7.9)
Dec  1 21:16:06 raul-desktop kernel: [    2.865244] fan PNP0C0B:00: registered as cooling_device0
Dec  1 21:16:06 raul-desktop kernel: [    2.865252] ACPI: Fan [FAN] (on)
Dec  1 21:16:06 raul-desktop kernel: [    2.877313] processor ACPI0007:00: registered as cooling_device1
Dec  1 21:16:06 raul-desktop kernel: [    2.877387] processor ACPI0007:01: registered as cooling_device2
Dec  1 21:16:06 raul-desktop kernel: [    2.880468] thermal LNXTHERM:01: registered as thermal_zone0
Dec  1 21:16:06 raul-desktop kernel: [    2.880907] ACPI: Thermal Zone [THRM] (40 C)
Dec  1 21:16:06 raul-desktop kernel: [    3.502936] usbcore: registered new interface driver usbfs
Dec  1 21:16:06 raul-desktop kernel: [    3.502962] usbcore: registered new interface driver hub
Dec  1 21:16:06 raul-desktop kernel: [    3.503070] usbcore: registered new device driver usb
Dec  1 21:16:06 raul-desktop kernel: [    3.507456] USB Universal Host Controller Interface driver v3.0
Dec  1 21:16:06 raul-desktop kernel: [    3.507520] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec  1 21:16:06 raul-desktop kernel: [    3.507531] uhci_hcd 0000:00:10.0: UHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    3.507585] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Dec  1 21:16:06 raul-desktop kernel: [    3.507626] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000f900
Dec  1 21:16:06 raul-desktop kernel: [    3.507794] usb usb1: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    3.507822] hub 1-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    3.507830] hub 1-0:1.0: 2 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    3.523242] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Dec  1 21:16:06 raul-desktop kernel: [    3.523280] scsi 1:0:0:0: Attached scsi generic sg1 type 0
Dec  1 21:16:06 raul-desktop kernel: [    3.523323] scsi 1:0:1:0: Attached scsi generic sg2 type 0
Dec  1 21:16:06 raul-desktop kernel: [    3.523359] scsi 2:0:0:0: Attached scsi generic sg3 type 0
Dec  1 21:16:06 raul-desktop kernel: [    3.523393] scsi 2:0:1:0: Attached scsi generic sg4 type 0
Dec  1 21:16:06 raul-desktop kernel: [    3.523429] scsi 3:0:0:0: Attached scsi generic sg5 type 5
Dec  1 21:16:06 raul-desktop kernel: [    3.523463] scsi 3:0:1:0: Attached scsi generic sg6 type 5
Dec  1 21:16:06 raul-desktop kernel: [    3.622550] Driver 'sd' needs updating - please use bus_type methods
Dec  1 21:16:06 raul-desktop kernel: [    3.622674] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.622695] sd 0:0:0:0: [sda] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.622729] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.622801] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.622818] sd 0:0:0:0: [sda] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.622851] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.622855]  sda: sda1
Dec  1 21:16:06 raul-desktop kernel: [    3.632352] sd 0:0:0:0: [sda] Attached SCSI disk
Dec  1 21:16:06 raul-desktop kernel: [    3.632478] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.632502] sd 1:0:0:0: [sdb] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.632543] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.632614] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.632634] sd 1:0:0:0: [sdb] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.632673] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.632678]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
Dec  1 21:16:06 raul-desktop kernel: [    3.642144]  sdb1
Dec  1 21:16:06 raul-desktop kernel: [    3.642279] sd 1:0:0:0: [sdb] Attached SCSI disk
Dec  1 21:16:06 raul-desktop kernel: [    3.642405] sd 1:0:1:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.642428] sd 1:0:1:0: [sdc] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.642468] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.642535] sd 1:0:1:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.642556] sd 1:0:1:0: [sdc] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.642595] sd 1:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.642599]  sdc:<6>via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Dec  1 21:16:06 raul-desktop kernel: [    3.683182]  sdc1
Dec  1 21:16:06 raul-desktop kernel: [    3.683326] sd 1:0:1:0: [sdc] Attached SCSI disk
Dec  1 21:16:06 raul-desktop kernel: [    3.683469] sd 2:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.683491] sd 2:0:0:0: [sdd] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.683527] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.683594] sd 2:0:0:0: [sdd] 1465149168 512-byte hardware sectors (750156 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.683612] sd 2:0:0:0: [sdd] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.683646] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.683650]  sdd:<7>ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Dec  1 21:16:06 raul-desktop kernel: [    3.704980]  sdd1 sdd2 <<6>uhci_hcd 0000:00:10.1: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec  1 21:16:06 raul-desktop kernel: [    3.713361] uhci_hcd 0000:00:10.1: UHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    3.713388] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Dec  1 21:16:06 raul-desktop kernel: [    3.713427] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000f800
Dec  1 21:16:06 raul-desktop kernel: [    3.713842] usb usb2: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    3.713876] hub 2-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    3.713885] hub 2-0:1.0: 2 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    3.725618]  sdd5 >
Dec  1 21:16:06 raul-desktop kernel: [    3.725815] sd 2:0:0:0: [sdd] Attached SCSI disk
Dec  1 21:16:06 raul-desktop kernel: [    3.725943] sd 2:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.725962] sd 2:0:1:0: [sde] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.725995] sd 2:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.726057] sd 2:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
Dec  1 21:16:06 raul-desktop kernel: [    3.726074] sd 2:0:1:0: [sde] Write Protect is off
Dec  1 21:16:06 raul-desktop kernel: [    3.726106] sd 2:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  1 21:16:06 raul-desktop kernel: [    3.726111]  sde: sde1
Dec  1 21:16:06 raul-desktop kernel: [    3.731480] sd 2:0:1:0: [sde] Attached SCSI disk
Dec  1 21:16:06 raul-desktop kernel: [    3.757328] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Dec  1 21:16:06 raul-desktop kernel: [    3.757333] Uniform CD-ROM driver Revision: 3.20
Dec  1 21:16:06 raul-desktop kernel: [    3.764341] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Dec  1 21:16:06 raul-desktop kernel: [    3.921432] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec  1 21:16:06 raul-desktop kernel: [    3.921445] uhci_hcd 0000:00:10.2: UHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    3.921493] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Dec  1 21:16:06 raul-desktop kernel: [    3.921521] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000f700
Dec  1 21:16:06 raul-desktop kernel: [    3.921723] usb usb3: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    3.921752] hub 3-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    3.921761] hub 3-0:1.0: 2 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    4.128364] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec  1 21:16:06 raul-desktop kernel: [    4.128376] uhci_hcd 0000:00:10.3: UHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    4.128404] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Dec  1 21:16:06 raul-desktop kernel: [    4.128451] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000f600
Dec  1 21:16:06 raul-desktop kernel: [    4.128574] usb usb4: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    4.128605] hub 4-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    4.128612] hub 4-0:1.0: 2 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    4.240034] usb 3-2: new low speed USB device using uhci_hcd and address 2
Dec  1 21:16:06 raul-desktop kernel: [    4.336719] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec  1 21:16:06 raul-desktop kernel: [    4.336740] ehci_hcd 0000:00:10.4: EHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    4.336798] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Dec  1 21:16:06 raul-desktop kernel: [    4.336833] ehci_hcd 0000:00:10.4: debug port 1
Dec  1 21:16:06 raul-desktop kernel: [    4.336848] ehci_hcd 0000:00:10.4: irq 22, io mem 0xfdffe000
Dec  1 21:16:06 raul-desktop kernel: [    4.369040] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec  1 21:16:06 raul-desktop kernel: [    4.369215] usb usb5: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    4.369244] hub 5-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    4.369254] hub 5-0:1.0: 8 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    4.576341] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec  1 21:16:06 raul-desktop kernel: [    4.576673] eth0: VIA Rhine II at 0xfdffd000, 00:1a:92:6f:58:55, IRQ 23.
Dec  1 21:16:06 raul-desktop kernel: [    4.577383] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
Dec  1 21:16:06 raul-desktop kernel: [    4.577538] ehci_hcd 0000:0a:0d.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
Dec  1 21:16:06 raul-desktop kernel: [    4.577554] ehci_hcd 0000:0a:0d.2: EHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    4.577597] ehci_hcd 0000:0a:0d.2: new USB bus registered, assigned bus number 6
Dec  1 21:16:06 raul-desktop kernel: [    4.600045] ehci_hcd 0000:0a:0d.2: irq 16, io mem 0xfddfd000
Dec  1 21:16:06 raul-desktop kernel: [    4.613013] ehci_hcd 0000:0a:0d.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec  1 21:16:06 raul-desktop kernel: [    4.613168] usb usb6: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    4.613197] hub 6-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    4.613207] hub 6-0:1.0: 5 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    4.820305] ohci_hcd 0000:0a:0d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec  1 21:16:06 raul-desktop kernel: [    4.820316] ohci_hcd 0000:0a:0d.0: OHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    4.820360] ohci_hcd 0000:0a:0d.0: new USB bus registered, assigned bus number 7
Dec  1 21:16:06 raul-desktop kernel: [    4.820396] ohci_hcd 0000:0a:0d.0: irq 18, io mem 0xfddff000
Dec  1 21:16:06 raul-desktop kernel: [    4.905968] usb usb7: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    4.905999] hub 7-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    4.906010] hub 7-0:1.0: 3 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    5.112261] ohci_hcd 0000:0a:0d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec  1 21:16:06 raul-desktop kernel: [    5.112278] ohci_hcd 0000:0a:0d.1: OHCI Host Controller
Dec  1 21:16:06 raul-desktop kernel: [    5.112306] ohci_hcd 0000:0a:0d.1: new USB bus registered, assigned bus number 8
Dec  1 21:16:06 raul-desktop kernel: [    5.112333] ohci_hcd 0000:0a:0d.1: irq 19, io mem 0xfddfe000
Dec  1 21:16:06 raul-desktop kernel: [    5.197932] usb usb8: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    5.197962] hub 8-0:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    5.197975] hub 8-0:1.0: 2 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    5.229016] usb 3-2: new low speed USB device using uhci_hcd and address 4
Dec  1 21:16:06 raul-desktop kernel: [    5.401628] usb 3-2: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    5.407510] PM: Starting manual resume from disk
Dec  1 21:16:06 raul-desktop kernel: [    5.464746] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec  1 21:16:06 raul-desktop kernel: [    5.464752] EXT3-fs: write access will be enabled during recovery.
Dec  1 21:16:06 raul-desktop kernel: [    5.581024] usb 7-3: new full speed USB device using ohci_hcd and address 2
Dec  1 21:16:06 raul-desktop kernel: [    5.803181] usb 7-3: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    5.806194] hub 7-3:1.0: USB hub found
Dec  1 21:16:06 raul-desktop kernel: [    5.808996] hub 7-3:1.0: 3 ports detected
Dec  1 21:16:06 raul-desktop kernel: [    6.118981] usb 7-3.2: new full speed USB device using ohci_hcd and address 3
Dec  1 21:16:06 raul-desktop kernel: [    6.247135] usb 7-3.2: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    6.330968] usb 7-3.3: new full speed USB device using ohci_hcd and address 4
Dec  1 21:16:06 raul-desktop kernel: [    6.455145] usb 7-3.3: configuration #1 chosen from 1 choice
Dec  1 21:16:06 raul-desktop kernel: [    6.462075] usbcore: registered new interface driver hiddev
Dec  1 21:16:06 raul-desktop kernel: [    6.474878] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-2/3-2:1.0/input/input2
Dec  1 21:16:06 raul-desktop kernel: [    6.476174] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-2
Dec  1 21:16:06 raul-desktop kernel: [    6.485065] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:13.1/0000:0a:0d.0/usb7/7-3/7-3.2/7-3.2:1.0/input/input3
Dec  1 21:16:06 raul-desktop kernel: [    6.485491] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:0a:0d.0-3.2
Dec  1 21:16:06 raul-desktop kernel: [    6.496127] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:13.1/0000:0a:0d.0/usb7/7-3/7-3.3/7-3.3:1.0/input/input4
Dec  1 21:16:06 raul-desktop kernel: [    6.504206] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:0a:0d.0-3.3
Dec  1 21:16:06 raul-desktop kernel: [    6.504230] usbcore: registered new interface driver usbhid
Dec  1 21:16:06 raul-desktop kernel: [    6.504234] usbhid: v2.6:USB HID core driver
Dec  1 21:16:06 raul-desktop kernel: [    7.423488] kjournald starting.  Commit interval 5 seconds
Dec  1 21:16:06 raul-desktop kernel: [    7.423507] EXT3-fs: sdd1: orphan cleanup on readonly fs
Dec  1 21:16:06 raul-desktop kernel: [    7.464738] EXT3-fs: sdd1: 1 orphan inode deleted
Dec  1 21:16:06 raul-desktop kernel: [    7.464741] EXT3-fs: recovery complete.
Dec  1 21:16:06 raul-desktop kernel: [    7.478374] EXT3-fs: mounted filesystem with ordered data mode.
Dec  1 21:16:06 raul-desktop kernel: [   13.189598] udevd version 124 started
Dec  1 21:16:06 raul-desktop kernel: [   13.645168] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec  1 21:16:06 raul-desktop kernel: [   13.678766] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec  1 21:16:06 raul-desktop kernel: [   13.748124] Linux agpgart interface v0.103
Dec  1 21:16:06 raul-desktop kernel: [   13.773205] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0238]
Dec  1 21:16:06 raul-desktop kernel: [   13.779795] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xb6000000
Dec  1 21:16:06 raul-desktop kernel: [   13.915163] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
Dec  1 21:16:06 raul-desktop kernel: [   13.933049] ACPI: Power Button (FF) [PWRF]
Dec  1 21:16:06 raul-desktop kernel: [   13.933145] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
Dec  1 21:16:06 raul-desktop kernel: [   13.965034] ACPI: Power Button (CM) [PWRB]
Dec  1 21:16:06 raul-desktop kernel: [   14.043713] nvidia: module license 'NVIDIA' taints kernel.
Dec  1 21:16:06 raul-desktop kernel: [   14.417505] parport_pc 00:09: reported by Plug and Play ACPI
Dec  1 21:16:06 raul-desktop kernel: [   14.417559] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Dec  1 21:16:06 raul-desktop kernel: [   14.443159] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
Dec  1 21:16:06 raul-desktop kernel: [   14.443464] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
Dec  1 21:16:06 raul-desktop kernel: [   15.525574] input: PC Speaker as /devices/platform/pcspkr/input/input7
Dec  1 21:16:06 raul-desktop kernel: [   15.907625] HDA Intel 0000:07:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  1 21:16:06 raul-desktop kernel: [   20.123604] lp0: using parport0 (interrupt-driven).
Dec  1 21:16:06 raul-desktop kernel: [   20.264501] Adding 3020180k swap on /dev/sdd5.  Priority:-1 extents:1 across:3020180k
Dec  1 21:16:06 raul-desktop kernel: [   20.835359] EXT3 FS on sdd1, internal journal
Dec  1 21:16:06 raul-desktop kernel: [   21.909968] type=1505 audit(1228187764.904:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4627
Dec  1 21:16:06 raul-desktop kernel: [   22.125652] type=1505 audit(1228187765.120:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4632
Dec  1 21:16:06 raul-desktop kernel: [   22.125898] type=1505 audit(1228187765.120:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4632
Dec  1 21:16:06 raul-desktop kernel: [   22.277254] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec  1 21:16:06 raul-desktop kernel: [   22.798462] ACPI: WMI: Mapper loaded
Dec  1 21:16:06 raul-desktop kernel: [   23.192095] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
Dec  1 21:16:07 raul-desktop kernel: [   23.992688] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Dec  1 21:16:07 raul-desktop kernel: [   24.084989] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec  1 21:16:07 raul-desktop kernel: [   24.085023] apm: disabled - APM is not SMP safe.
Dec  1 21:16:07 raul-desktop kernel: [   24.213284] ppdev: user-space parallel port driver
Dec  1 21:16:12 raul-desktop kernel: [   29.071501] Bluetooth: Core ver 2.13
Dec  1 21:16:12 raul-desktop kernel: [   29.072166] NET: Registered protocol family 31
Dec  1 21:16:12 raul-desktop kernel: [   29.072171] Bluetooth: HCI device and connection manager initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.072176] Bluetooth: HCI socket layer initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.085027] Bluetooth: L2CAP ver 2.11
Dec  1 21:16:12 raul-desktop kernel: [   29.085034] Bluetooth: L2CAP socket layer initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.093602] Bluetooth: SCO (Voice Link) ver 0.6
Dec  1 21:16:12 raul-desktop kernel: [   29.093608] Bluetooth: SCO socket layer initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.102187] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec  1 21:16:12 raul-desktop kernel: [   29.102195] Bluetooth: BNEP filters: protocol multicast
Dec  1 21:16:12 raul-desktop kernel: [   29.153319] Bridge firewalling registered
Dec  1 21:16:12 raul-desktop kernel: [   29.398126] Bluetooth: RFCOMM socket layer initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.398146] Bluetooth: RFCOMM TTY layer initialized
Dec  1 21:16:12 raul-desktop kernel: [   29.398149] Bluetooth: RFCOMM ver 1.10
Dec  1 21:16:12 raul-desktop kernel: [   29.643620] usb 7-3.1: new full speed USB device using ohci_hcd and address 5
Dec  1 21:16:12 raul-desktop kernel: [   29.765767] usb 7-3.1: configuration #1 chosen from 1 choice
Dec  1 21:16:12 raul-desktop kernel: [   29.865860] Bluetooth: Generic Bluetooth USB driver ver 0.3
Dec  1 21:16:12 raul-desktop kernel: [   29.866852] usbcore: registered new interface driver btusb
Dec  1 21:16:16 raul-desktop kernel: [   33.501025] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Dec  1 21:16:17 raul-desktop kernel: [   34.221596] NET: Registered protocol family 17
Dec  1 21:16:16 raul-desktop pulseaudio[6122]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  1 21:16:16 raul-desktop pulseaudio[6124]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  1 21:16:16 raul-desktop pulseaudio[6124]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  1 21:16:16 raul-desktop kernel: [   39.234516] hda-intel: Invalid position buffer, using LPIB read method instead.
Dec  1 21:16:16 raul-desktop kernel: [   39.234537] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec  1 21:16:39 raul-desktop kernel: [   61.964066] UDF-fs: No VRS found
Dec  1 21:28:08 raul-desktop kernel: [  750.787522] NET: Registered protocol family 10
Dec  1 21:28:08 raul-desktop kernel: [  750.788738] lo: Disabled Privacy Extensions

---

### Post by lavinog on 2008-12-01
I am thinking that all_generic_ide is causing your sata drives to be reduced in performance.

If you just remove that from the kernel options do you still get bumped to busybox?
if so does it say why?

Try to boot with all ide devices that are not essential to boot ubuntu disconnected (including cdrom) and see if it still kicks you out to busy box..

also what is your mobo model

---

### Post by moosefist on 2008-12-02
the all_generic_ide is required for it to not drop me to busybox.  I should have a chance to try booting with my cd drives not connected tomm.

my mobo is a ASUS a8v-xe

I attached a screen of what it says in my

---

### Post by lavinog on 2008-12-02
> **moosefist said:**
> the all_generic_ide is required for it to not drop me to busybox.  I should have a chance to try booting with my cd drives not connected tomm.

my mobo is a ASUS a8v-xe

I attached a screen of what it says in my

I almost want to say the problem is in your /etc/fstab file its hard to tell since the screenshot cuts off the wording

reboot as normal and post your /etc/fstab

---

### Post by lavinog on 2008-12-02
Actually I could be wrong...but what type of drive is your root drive (the one with ubuntu...sata or ide)

---

### Post by lavinog on 2008-12-02
found a thread for you to read:
[http://ubuntuforums.org/showthread.php?t=956183](http://ubuntuforums.org/showthread.php?t=956183)

[quote=post 19]add the option pci=nomsi to the kernel to boot,[/quote]

bugreport:
[https://bugs.launchpad.net/ubuntu/+bug/190492](https://bugs.launchpad.net/ubuntu/+bug/190492)

---

### Post by moosefist on 2008-12-02
here is another screen that isn't cropped as much, but its a little blurry.

The OS is on the 750gb ide drive, but soon it will be on the 250gb ide.  i gotta put the 750 in another comp.  in a month or 2 i plan the eliminate the ide HD's entirely.

---

### Post by moosefist on 2008-12-02
> **lavinog said:**
> found a thread for you to read:
[http://ubuntuforums.org/showthread.php?t=956183](http://ubuntuforums.org/showthread.php?t=956183)



bugreport:
[https://bugs.launchpad.net/ubuntu/+bug/190492](https://bugs.launchpad.net/ubuntu/+bug/190492)

AMAZING!!!!

This fixed it exactly my file transfers are a consistantly 30-55Mb/s with that option, boot seemed quicker also.

You sir have helped a bunch.  Thanks.

---

### Post by lavinog on 2008-12-02
Glad to help.
Make sure you mark this thread as solved using the thread tools link.

---


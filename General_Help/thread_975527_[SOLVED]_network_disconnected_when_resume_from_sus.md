---
title: "[SOLVED] network disconnected when resume from suspend"
date: 2008-11-08
forum: General Help
---

### Post by karlmp on 2008-11-08
whenever I resume from suspend there's no network connection, so I have to restart

I'm running intrepid

thanks in advance

---

### Post by cmnorton on 2008-11-08
You might get more help by providing more information.

What kind of network connection is this, wired, wireless?

What kind of hardware is this, laptop or not?

What is the Ubuntu version, 8.10, 8.04, or something earlier?

Is there anything tell-tail in the logs (/var/log/messages, output of dmesg, or /var/log/syslog)?

---

### Post by karlmp on 2008-11-08
is wired, a laptop, 8.10

/var/log/messages:

```
Nov  8 10:45:06 karl-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov  8 11:02:55 karl-laptop -- MARK --
Nov  8 11:22:55 karl-laptop -- MARK --
Nov  8 11:25:02 karl-laptop kernel: [ 3751.722631] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
Nov  8 11:25:02 karl-laptop kernel: [ 3751.722640] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Nov  8 11:25:02 karl-laptop kernel: [ 3751.722643] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
Nov  8 11:42:55 karl-laptop -- MARK --
Nov  8 11:49:46 karl-laptop kernel: [ 4992.409984] PM: Syncing filesystems ... done.
Nov  8 11:49:48 karl-laptop kernel: [ 4992.410637] Freezing user space processes ... (elapsed 0.33 seconds) done.
Nov  8 11:49:48 karl-laptop kernel: [ 4992.745146] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Nov  8 11:49:48 karl-laptop kernel: [ 4992.836020] Suspending console(s) (use no_console_suspend to debug)
Nov  8 11:49:48 karl-laptop kernel: [ 4992.836503] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  8 11:49:48 karl-laptop kernel: [ 4992.868136] sd 0:0:0:0: [sda] Stopping disk
Nov  8 11:49:48 karl-laptop kernel: [ 4993.932861] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4993.948069] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D3
Nov  8 11:49:48 karl-laptop kernel: [ 4993.948650] VIA 82xx Audio 0000:00:11.5: PCI INT C disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4993.964053] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D3
Nov  8 11:49:48 karl-laptop kernel: [ 4993.964148] pata_via 0000:00:11.1: PCI INT A disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4993.980063] pata_via 0000:00:11.1: power state changed by ACPI to D3
Nov  8 11:49:48 karl-laptop kernel: [ 4993.980126] ehci_hcd 0000:00:10.3: PCI INT D disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4993.996048] uhci_hcd 0000:00:10.2: PCI INT C disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.012045] uhci_hcd 0000:00:10.1: PCI INT B disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.028045] uhci_hcd 0000:00:10.0: PCI INT A disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.044067] rt61pci 0000:00:0d.0: PCI INT A disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.060059] sdhci-pci 0000:00:0c.4: PCI INT B disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.076056] sdhci-pci 0000:00:0c.2: PCI INT B disabled
Nov  8 11:49:48 karl-laptop kernel: [ 4994.108041] PM: suspend devices took 1.272 seconds
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188036] ACPI: Preparing to enter system sleep state S3
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] Disabling non-boot CPUs ...
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 3, using IRQ 23
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
Nov  8 11:49:48 karl-laptop kernel: [ 4994.188776] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 9, using IRQ 21
Nov  8 11:49:48 karl-laptop kernel: [ 4994.189605] ACPI: Waking up from system sleep state S3
Nov  8 11:49:48 karl-laptop kernel: [ 4994.508188] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  8 11:49:48 karl-laptop kernel: [ 4995.024013] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  8 11:49:48 karl-laptop kernel: [ 4996.508059] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 11:49:48 karl-laptop kernel: [ 4996.524054] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 11:49:48 karl-laptop kernel: [ 4996.540016] rt61pci 0000:00:0d.0: enabling device (0000 -> 0002)
Nov  8 11:49:48 karl-laptop kernel: [ 4996.540021] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 11:49:48 karl-laptop kernel: [ 4996.556017] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:49:48 karl-laptop kernel: [ 4996.556061] usb usb2: root hub lost power or was reset
Nov  8 11:49:48 karl-laptop kernel: [ 4996.572017] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:49:48 karl-laptop kernel: [ 4996.572059] usb usb3: root hub lost power or was reset
Nov  8 11:49:48 karl-laptop kernel: [ 4996.588017] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:49:48 karl-laptop kernel: [ 4996.588059] usb usb4: root hub lost power or was reset
Nov  8 11:49:48 karl-laptop kernel: [ 4996.604017] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:49:48 karl-laptop kernel: [ 4996.604047] usb usb1: root hub lost power or was reset
Nov  8 11:49:48 karl-laptop kernel: [ 4996.604126] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.604188] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.604193] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
Nov  8 11:49:48 karl-laptop kernel: [ 4996.606131] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.606218] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.606224] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 11:49:48 karl-laptop kernel: [ 4996.609510] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.609595] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.609601] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 11:49:48 karl-laptop kernel: [ 4996.612646] pci 0000:01:00.0: power state changed by ACPI to D0
Nov  8 11:49:48 karl-laptop kernel: [ 4996.612654] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 11:49:48 karl-laptop kernel: [ 4996.760353] sd 0:0:0:0: [sda] Starting disk
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768678] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768680] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768682] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768846] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768848] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.768850] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  8 11:49:48 karl-laptop kernel: [ 4996.784422] ata2.00: configured for UDMA/33
Nov  8 11:49:48 karl-laptop kernel: [ 4996.784542] ata1.00: configured for UDMA/100
Nov  8 11:49:48 karl-laptop kernel: [ 4996.886388] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 11:49:48 karl-laptop kernel: [ 4996.886409] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 11:49:48 karl-laptop kernel: [ 4996.886442] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 11:49:48 karl-laptop kernel: [ 4996.886627] PM: resume devices took 2.496 seconds
Nov  8 11:49:48 karl-laptop kernel: [ 4996.886758] Restarting tasks ... done.
Nov  8 11:53:50 karl-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov  8 11:53:50 karl-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov  8 11:53:50 karl-laptop kernel: Cannot find map file.
Nov  8 11:53:50 karl-laptop kernel: Loaded 52295 symbols from 106 modules.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bef0000 - 000000000befa000 (ACPI data)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000befa000 - 000000000bf00000 (ACPI NVS)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] RAMDISK: 0b712000 - 0bedfaa7
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] DMI present.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: RSDP 000F7C80, 0014 (r0 PTLTD )
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: RSDT 0BEF6B92, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: FACP 0BEF9E0D, 0074 (r1 PN800  PTLTW     6040000 PTL_    F4240)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: DSDT 0BEF6BC2, 324B (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: FACS 0BEFAFC0, 0040
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: APIC 0BEF9E81, 0046 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: SSDT 0BEF9EC7, 0139 (r1 PTLTD    CpuGv3  6040000  LTP        1)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] 190MB LOWMEM available.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   mapped low ram: 0 - 0bef0000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   low ram: 00000000 - 0bef0000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   bootmap 00002000 - 000037e0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #4 [000b712000 - 000bedfaa7]          RAMDISK ==> [000b712000 - 000bedfaa7]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] found SMP MP-table at [c00f7cb0] 000f7cb0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Zone PFN ranges:
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0000bef0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Nov  8 11:53:50 karl-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0000bef0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3f80000)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48353
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Kernel command line: root=UUID=56b35b8f-d3f2-47ea-8972-3dad5a106954 ro quiet splash 
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Initializing CPU#0
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] TSC: using PIT calibration value
Nov  8 11:53:50 karl-laptop kernel: [    0.000000] Detected 2138.122 MHz processor.
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] console [tty0] enabled
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] Memory: 180092k/195520k available (2572k kernel code, 14888k reserved, 1160k data, 424k init, 0k highmem)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] virtual kernel memory layout:
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov  8 11:53:50 karl-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Nov  8 11:53:50 karl-laptop kernel: [    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 4276.24 BogoMIPS (lpj=8552488)
Nov  8 11:53:50 karl-laptop kernel: [    0.004044] Security Framework initialized
Nov  8 11:53:50 karl-laptop kernel: [    0.004060] SELinux:  Disabled at boot.
Nov  8 11:53:50 karl-laptop kernel: [    0.004092] AppArmor: AppArmor initialized
Nov  8 11:53:50 karl-laptop kernel: [    0.004105] Mount-cache hash table entries: 512
Nov  8 11:53:50 karl-laptop kernel: [    0.004334] Initializing cgroup subsys ns
Nov  8 11:53:50 karl-laptop kernel: [    0.004344] Initializing cgroup subsys cpuacct
Nov  8 11:53:50 karl-laptop kernel: [    0.004346] Initializing cgroup subsys memory
Nov  8 11:53:50 karl-laptop kernel: [    0.004367] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  8 11:53:50 karl-laptop kernel: [    0.004369] CPU: L2 cache: 2048K
Nov  8 11:53:50 karl-laptop kernel: [    0.004391] Checking 'hlt' instruction... OK.
Nov  8 11:53:50 karl-laptop kernel: [    0.020587] SMP alternatives: switching to UP code
Nov  8 11:53:50 karl-laptop kernel: [    0.024014] Freeing SMP alternatives: 11k freed
Nov  8 11:53:50 karl-laptop kernel: [    0.024018] ACPI: Core revision 20080609
Nov  8 11:53:50 karl-laptop kernel: [    0.026118] ACPI: Checking initramfs for custom DSDT
Nov  8 11:53:50 karl-laptop kernel: [    0.343708] ENABLING IO-APIC IRQs
Nov  8 11:53:50 karl-laptop kernel: [    0.344021] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov  8 11:53:50 karl-laptop kernel: [    0.348021] ...trying to set up timer (IRQ0) through the 8259A ...
Nov  8 11:53:50 karl-laptop kernel: [    0.348021] ..... (found apic 0 pin 0) ...
Nov  8 11:53:50 karl-laptop kernel: [    0.391524] ....... works.
Nov  8 11:53:50 karl-laptop kernel: [    0.391525] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] Brought up 1 CPUs
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] Total of 1 processors activated (4276.24 BogoMIPS).
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] net_namespace: 840 bytes
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] Booting paravirtualized kernel on bare hardware
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] Time: 11:53:24  Date: 11/08/08
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] NET: Registered protocol family 16
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] EISA bus registered
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] ACPI: bus type pci registered
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] PCI: PCI BIOS revision 2.10 entry at 0xfd8fc, last bus=1
Nov  8 11:53:50 karl-laptop kernel: [    0.392024] PCI: Using configuration type 1 for base access
Nov  8 11:53:50 karl-laptop kernel: [    0.393762] ACPI: Interpreter enabled
Nov  8 11:53:50 karl-laptop kernel: [    0.393765] ACPI: (supports S0 S3 S4 S5)
Nov  8 11:53:50 karl-laptop kernel: [    0.393777] ACPI: Using IOAPIC for interrupt routing
Nov  8 11:53:50 karl-laptop kernel: [    0.394345] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  8 11:53:50 karl-laptop kernel: [    0.908034] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  8 11:53:50 karl-laptop kernel: [    1.020212] ACPI: EC: GPE = 0xb, I/O: command/status = 0x66, data = 0x62
Nov  8 11:53:50 karl-laptop kernel: [    1.020215] ACPI: EC: driver started in poll mode
Nov  8 11:53:50 karl-laptop kernel: [    1.020261] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 11:53:50 karl-laptop kernel: [    1.020630] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.020635] pci 0000:00:0c.0: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.020701] pci 0000:00:0c.1: PME# supported from D0 D1 D2 D3hot
Nov  8 11:53:50 karl-laptop kernel: [    1.020705] pci 0000:00:0c.1: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.020771] pci 0000:00:0c.2: PME# supported from D0 D1 D2 D3hot
Nov  8 11:53:50 karl-laptop kernel: [    1.020775] pci 0000:00:0c.2: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.020842] pci 0000:00:0c.4: PME# supported from D0 D1 D2 D3hot
Nov  8 11:53:50 karl-laptop kernel: [    1.020846] pci 0000:00:0c.4: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.020974] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.020978] pci 0000:00:10.0: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.021041] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.021045] pci 0000:00:10.1: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.021108] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.021112] pci 0000:00:10.2: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.021175] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.021179] pci 0000:00:10.3: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.021238] HPET not enabled in BIOS. You might try hpet=force boot option
Nov  8 11:53:50 karl-laptop kernel: [    1.021245] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
Nov  8 11:53:50 karl-laptop kernel: [    1.021249] pci 0000:00:11.0: quirk: region 8100-810f claimed by vt8235 SMB
Nov  8 11:53:50 karl-laptop kernel: [    1.021513] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 11:53:50 karl-laptop kernel: [    1.021517] pci 0000:00:12.0: PME# disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.029584] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *3, disabled.
Nov  8 11:53:50 karl-laptop kernel: [    1.029685] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *4, disabled.
Nov  8 11:53:50 karl-laptop kernel: [    1.029784] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
Nov  8 11:53:50 karl-laptop kernel: [    1.029880] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *9, disabled.
Nov  8 11:53:50 karl-laptop kernel: [    1.030010] ACPI: PCI Interrupt Link [LNKA] (IRQs *3)
Nov  8 11:53:50 karl-laptop kernel: [    1.030138] ACPI: PCI Interrupt Link [LNKB] (IRQs *4)
Nov  8 11:53:50 karl-laptop kernel: [    1.030265] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
Nov  8 11:53:50 karl-laptop kernel: [    1.030401] ACPI: PCI Interrupt Link [LNKD] (IRQs 6) *9
Nov  8 11:53:50 karl-laptop kernel: [    1.030567] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 11:53:50 karl-laptop kernel: [    1.030600] pnp: PnP ACPI init
Nov  8 11:53:50 karl-laptop kernel: [    1.030607] ACPI: bus type pnp registered
Nov  8 11:53:50 karl-laptop kernel: [    1.064060] pnp: PnP ACPI: found 9 devices
Nov  8 11:53:50 karl-laptop kernel: [    1.064063] ACPI: ACPI bus type pnp unregistered
Nov  8 11:53:50 karl-laptop kernel: [    1.064066] PnPBIOS: Disabled by ACPI PNP
Nov  8 11:53:50 karl-laptop kernel: [    1.064371] PCI: Using ACPI for IRQ routing
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NET: Registered protocol family 8
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NET: Registered protocol family 20
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NetLabel: Initializing
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NetLabel:  domain hash size = 128
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] NetLabel:  unlabeled traffic allowed by default
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] tracer: 772 pages allocated for 65536 entries of 48 bytes
Nov  8 11:53:50 karl-laptop kernel: [    1.064487]    actual entries 65620
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] AppArmor: AppArmor Filesystem Enabled
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0x0-0x9ffff could not be reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xffb80000-0xffbfffff has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xff380000-0xff3fffff has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xff780000-0xff7fffff has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:06: ioport range 0xfe10-0xfe11 has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:06: ioport range 0x4000-0x407f has been reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.064487] system 00:06: ioport range 0x8100-0x811f could not be reserved
Nov  8 11:53:50 karl-laptop kernel: [    1.099975] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf4000000-0xf3ffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.099979] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov  8 11:53:50 karl-laptop kernel: [    1.099981] pci 0000:00:01.0:   IO window: disabled
Nov  8 11:53:50 karl-laptop kernel: [    1.099986] pci 0000:00:01.0:   MEM window: 0xd1000000-0xd1ffffff
Nov  8 11:53:50 karl-laptop kernel: [    1.099990] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
Nov  8 11:53:50 karl-laptop kernel: [    1.099996] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
Nov  8 11:53:50 karl-laptop kernel: [    1.099998] pci 0000:00:0c.0:   IO window: 0x002000-0x0020ff
Nov  8 11:53:50 karl-laptop kernel: [    1.100003] pci 0000:00:0c.0:   IO window: 0x002400-0x0024ff
Nov  8 11:53:50 karl-laptop kernel: [    1.100007] pci 0000:00:0c.0:   PREFETCH window: 0x10000000-0x13ffffff
Nov  8 11:53:50 karl-laptop kernel: [    1.100012] pci 0000:00:0c.0:   MEM window: 0x14000000-0x17ffffff
Nov  8 11:53:50 karl-laptop kernel: [    1.100042] pci 0000:00:0c.0: enabling device (0000 -> 0003)
Nov  8 11:53:50 karl-laptop kernel: [    1.100049] pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 11:53:50 karl-laptop kernel: [    1.100063] bus: 00 index 0 io port: [0, ffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100065] bus: 00 index 1 mmio: [0, ffffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100067] bus: 01 index 0 mmio: [0, 0]
Nov  8 11:53:50 karl-laptop kernel: [    1.100069] bus: 01 index 1 mmio: [d1000000, d1ffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100071] bus: 01 index 2 mmio: [f0000000, f3ffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100073] bus: 01 index 3 mmio: [0, 0]
Nov  8 11:53:50 karl-laptop kernel: [    1.100075] bus: 02 index 0 io port: [2000, 20ff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100077] bus: 02 index 1 io port: [2400, 24ff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100079] bus: 02 index 2 mmio: [10000000, 13ffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100081] bus: 02 index 3 mmio: [14000000, 17ffffff]
Nov  8 11:53:50 karl-laptop kernel: [    1.100091] NET: Registered protocol family 2
Nov  8 11:53:50 karl-laptop kernel: [    1.100207] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    1.100394] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    1.100460] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    1.100519] TCP: Hash tables configured (established 8192 bind 8192)
Nov  8 11:53:50 karl-laptop kernel: [    1.100523] TCP reno registered
Nov  8 11:53:50 karl-laptop kernel: [    1.100582] NET: Registered protocol family 1
Nov  8 11:53:50 karl-laptop kernel: [    1.100697] checking if image is initramfs... it is
Nov  8 11:53:50 karl-laptop kernel: [    1.749076] Freeing initrd memory: 7990k freed
Nov  8 11:53:50 karl-laptop kernel: [    1.749988] audit: initializing netlink socket (disabled)
Nov  8 11:53:50 karl-laptop kernel: [    1.750016] type=2000 audit(1226145204.748:1): initialized
Nov  8 11:53:50 karl-laptop kernel: [    1.755852] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov  8 11:53:50 karl-laptop kernel: [    1.758103] VFS: Disk quotas dquot_6.5.1
Nov  8 11:53:50 karl-laptop kernel: [    1.758194] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 11:53:50 karl-laptop kernel: [    1.758310] msgmni has been set to 367
Nov  8 11:53:50 karl-laptop kernel: [    1.758453] io scheduler noop registered
Nov  8 11:53:50 karl-laptop kernel: [    1.758456] io scheduler anticipatory registered
Nov  8 11:53:50 karl-laptop kernel: [    1.758458] io scheduler deadline registered
Nov  8 11:53:50 karl-laptop kernel: [    1.758469] io scheduler cfq registered (default)
Nov  8 11:53:50 karl-laptop kernel: [    1.758491] PCI: VIA PCI bridge detected.Disabling DAC.
Nov  8 11:53:50 karl-laptop kernel: [    1.758929] isapnp: Scanning for PnP cards...
Nov  8 11:53:50 karl-laptop kernel: [    2.112666] isapnp: No Plug & Play device found
Nov  8 11:53:50 karl-laptop kernel: [    2.145588] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov  8 11:53:50 karl-laptop kernel: [    2.147779] brd: module loaded
Nov  8 11:53:50 karl-laptop kernel: [    2.147856] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov  8 11:53:50 karl-laptop kernel: [    2.147983] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  8 11:53:50 karl-laptop kernel: [    2.150547] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov  8 11:53:50 karl-laptop kernel: [    2.151844] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 11:53:50 karl-laptop kernel: [    2.151852] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov  8 11:53:50 karl-laptop kernel: [    2.151854] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov  8 11:53:50 karl-laptop kernel: [    2.151857] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov  8 11:53:50 karl-laptop kernel: [    2.151859] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov  8 11:53:50 karl-laptop kernel: [    2.152404] mice: PS/2 mouse device common for all mice
Nov  8 11:53:50 karl-laptop kernel: [    2.152543] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov  8 11:53:50 karl-laptop kernel: [    2.152586] rtc0: alarms up to one year, y3k
Nov  8 11:53:50 karl-laptop kernel: [    2.152697] EISA: Probing bus 0 at eisa.0
Nov  8 11:53:50 karl-laptop kernel: [    2.152705] Cannot allocate resource for EISA slot 1
Nov  8 11:53:50 karl-laptop kernel: [    2.152708] Cannot allocate resource for EISA slot 2
Nov  8 11:53:50 karl-laptop kernel: [    2.152714] Cannot allocate resource for EISA slot 4
Nov  8 11:53:50 karl-laptop kernel: [    2.152730] EISA: Detected 0 cards.
Nov  8 11:53:50 karl-laptop kernel: [    2.152736] cpuidle: using governor ladder
Nov  8 11:53:50 karl-laptop kernel: [    2.152738] cpuidle: using governor menu
Nov  8 11:53:50 karl-laptop kernel: [    2.153233] TCP cubic registered
Nov  8 11:53:50 karl-laptop kernel: [    2.153273] Using IPI No-Shortcut mode
Nov  8 11:53:50 karl-laptop kernel: [    2.153455] registered taskstats version 1
Nov  8 11:53:50 karl-laptop kernel: [    2.153576]   Magic number: 0:137:883
Nov  8 11:53:50 karl-laptop kernel: [    2.153673] tty ptyx7: hash matches
Nov  8 11:53:50 karl-laptop kernel: [    2.153689] tty ptyua: hash matches
Nov  8 11:53:50 karl-laptop kernel: [    2.153808] rtc_cmos 00:02: setting system clock to 2008-11-08 11:53:26 UTC (1226145206)
Nov  8 11:53:50 karl-laptop kernel: [    2.153812] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  8 11:53:50 karl-laptop kernel: [    2.153814] EDD information not available.
Nov  8 11:53:50 karl-laptop kernel: [    2.154108] Freeing unused kernel memory: 424k freed
Nov  8 11:53:50 karl-laptop kernel: [    2.154153] Write protecting the kernel text: 2576k
Nov  8 11:53:50 karl-laptop kernel: [    2.154180] Write protecting the kernel read-only data: 936k
Nov  8 11:53:50 karl-laptop kernel: [    2.175928] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov  8 11:53:50 karl-laptop kernel: [    2.334020] fuse init (API version 7.9)
Nov  8 11:53:50 karl-laptop kernel: [    2.509760] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov  8 11:53:50 karl-laptop kernel: [    2.509819] processor ACPI0007:00: registered as cooling_device0
Nov  8 11:53:50 karl-laptop kernel: [    2.509823] ACPI: Processor [CPU0] (supports 16 throttling states)
Nov  8 11:53:50 karl-laptop kernel: [    2.516025] Marking TSC unstable due to TSC halts in idle
Nov  8 11:53:50 karl-laptop kernel: [    2.769493] thermal LNXTHERM:01: registered as thermal_zone0
Nov  8 11:53:50 karl-laptop kernel: [    3.024038] ACPI: Thermal Zone [THRM] (25 C)
Nov  8 11:53:50 karl-laptop kernel: [    3.540091] usbcore: registered new interface driver usbfs
Nov  8 11:53:50 karl-laptop kernel: [    3.540121] usbcore: registered new interface driver hub
Nov  8 11:53:50 karl-laptop kernel: [    3.540444] usbcore: registered new device driver usb
Nov  8 11:53:50 karl-laptop kernel: [    3.546955] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
Nov  8 11:53:50 karl-laptop kernel: [    3.547030] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    3.547033] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    3.547043] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    3.547061] ehci_hcd 0000:00:10.3: EHCI Host Controller
Nov  8 11:53:50 karl-laptop kernel: [    3.547127] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
Nov  8 11:53:50 karl-laptop kernel: [    3.547172] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0000c00
Nov  8 11:53:50 karl-laptop kernel: [    3.556037] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 11:53:50 karl-laptop kernel: [    3.556282] usb usb1: configuration #1 chosen from 1 choice
Nov  8 11:53:50 karl-laptop kernel: [    3.556313] hub 1-0:1.0: USB hub found
Nov  8 11:53:50 karl-laptop kernel: [    3.556328] hub 1-0:1.0: 6 ports detected
Nov  8 11:53:50 karl-laptop kernel: [    3.556435] USB Universal Host Controller Interface driver v3.0
Nov  8 11:53:50 karl-laptop kernel: [    3.569933] No dock devices found.
Nov  8 11:53:50 karl-laptop kernel: [    3.600476] SCSI subsystem initialized
Nov  8 11:53:50 karl-laptop kernel: [    3.660487] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    3.660500] uhci_hcd 0000:00:10.0: UHCI Host Controller
Nov  8 11:53:50 karl-laptop kernel: [    3.660526] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Nov  8 11:53:50 karl-laptop kernel: [    3.660551] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001020
Nov  8 11:53:50 karl-laptop kernel: [    3.660646] usb usb2: configuration #1 chosen from 1 choice
Nov  8 11:53:50 karl-laptop kernel: [    3.660673] hub 2-0:1.0: USB hub found
Nov  8 11:53:50 karl-laptop kernel: [    3.660682] hub 2-0:1.0: 2 ports detected
Nov  8 11:53:50 karl-laptop kernel: [    3.694574] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Nov  8 11:53:50 karl-laptop kernel: [    3.868469] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    3.868484] uhci_hcd 0000:00:10.1: UHCI Host Controller
Nov  8 11:53:50 karl-laptop kernel: [    3.868516] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Nov  8 11:53:50 karl-laptop kernel: [    3.868543] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001040
Nov  8 11:53:50 karl-laptop kernel: [    3.868643] usb usb3: configuration #1 chosen from 1 choice
Nov  8 11:53:50 karl-laptop kernel: [    3.868672] hub 3-0:1.0: USB hub found
Nov  8 11:53:50 karl-laptop kernel: [    3.868680] hub 3-0:1.0: 2 ports detected
Nov  8 11:53:50 karl-laptop kernel: [    4.076369] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 11:53:50 karl-laptop kernel: [    4.076384] uhci_hcd 0000:00:10.2: UHCI Host Controller
Nov  8 11:53:50 karl-laptop kernel: [    4.076411] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Nov  8 11:53:50 karl-laptop kernel: [    4.076438] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001060
Nov  8 11:53:50 karl-laptop kernel: [    4.076537] usb usb4: configuration #1 chosen from 1 choice
Nov  8 11:53:50 karl-laptop kernel: [    4.076566] hub 4-0:1.0: USB hub found
Nov  8 11:53:50 karl-laptop kernel: [    4.076573] hub 4-0:1.0: 2 ports detected
Nov  8 11:53:50 karl-laptop kernel: [    4.284522] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  8 11:53:50 karl-laptop kernel: [    4.288817] eth0: VIA Rhine II at 0xd0001000, 00:90:f5:37:fa:d5, IRQ 23.
Nov  8 11:53:50 karl-laptop kernel: [    4.289524] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
Nov  8 11:53:50 karl-laptop kernel: [    4.294028] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 11:53:50 karl-laptop kernel: [    4.294112] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
Nov  8 11:53:50 karl-laptop kernel: [    4.294187] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
Nov  8 11:53:50 karl-laptop kernel: [    4.294189] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
Nov  8 11:53:50 karl-laptop kernel: [    4.294193] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
Nov  8 11:53:50 karl-laptop kernel: [    4.295142] scsi0 : pata_via
Nov  8 11:53:50 karl-laptop kernel: [    4.295260] scsi1 : pata_via
Nov  8 11:53:50 karl-laptop kernel: [    4.296104] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
Nov  8 11:53:50 karl-laptop kernel: [    4.296108] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
Nov  8 11:53:50 karl-laptop kernel: [    4.572518] ata1.00: ATA-7: SAMSUNG MP0402H, YQ200-06, max UDMA/100
Nov  8 11:53:50 karl-laptop kernel: [    4.572523] ata1.00: 78242976 sectors, multi 16: LBA48 
Nov  8 11:53:50 karl-laptop kernel: [    4.588357] ata1.00: configured for UDMA/100
Nov  8 11:53:50 karl-laptop kernel: [    4.752357] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TX11, max UDMA/33
Nov  8 11:53:50 karl-laptop kernel: [    4.768224] ata2.00: configured for UDMA/33
Nov  8 11:53:50 karl-laptop kernel: [    4.768372] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0402H  YQ20 PQ: 0 ANSI: 5
Nov  8 11:53:50 karl-laptop kernel: [    4.769118] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TX11 PQ: 0 ANSI: 5
Nov  8 11:53:50 karl-laptop kernel: [    4.780905] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 11:53:50 karl-laptop kernel: [    4.780944] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Nov  8 11:53:50 karl-laptop kernel: [    4.795498] Driver 'sd' needs updating - please use bus_type methods
Nov  8 11:53:50 karl-laptop kernel: [    4.795636] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 11:53:50 karl-laptop kernel: [    4.795656] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 11:53:50 karl-laptop kernel: [    4.795689] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 11:53:50 karl-laptop kernel: [    4.795768] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 11:53:50 karl-laptop kernel: [    4.795784] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 11:53:50 karl-laptop kernel: [    4.795817] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 11:53:50 karl-laptop kernel: [    4.795822]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov  8 11:53:50 karl-laptop kernel: [    5.258617]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Nov  8 11:53:50 karl-laptop kernel: [    5.309784] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 11:53:50 karl-laptop kernel: [    5.319953] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
Nov  8 11:53:50 karl-laptop kernel: [    5.319957] Uniform CD-ROM driver Revision: 3.20
Nov  8 11:53:50 karl-laptop kernel: [    5.771531] PM: Starting manual resume from disk
Nov  8 11:53:50 karl-laptop kernel: [    5.789129] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov  8 11:53:50 karl-laptop kernel: [    5.789134] EXT3-fs: write access will be enabled during recovery.
Nov  8 11:53:50 karl-laptop kernel: [    7.849453] kjournald starting.  Commit interval 5 seconds
Nov  8 11:53:50 karl-laptop kernel: [    7.849477] EXT3-fs: sda2: orphan cleanup on readonly fs
Nov  8 11:53:50 karl-laptop kernel: [    7.849526] EXT3-fs: sda2: 1 orphan inode deleted
Nov  8 11:53:50 karl-laptop kernel: [    7.849528] EXT3-fs: recovery complete.
Nov  8 11:53:50 karl-laptop kernel: [    7.866012] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 11:53:50 karl-laptop kernel: [   15.971888] udevd version 124 started
Nov  8 11:53:50 karl-laptop kernel: [   16.438866] Linux agpgart interface v0.103
Nov  8 11:53:50 karl-laptop kernel: [   16.507615] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
Nov  8 11:53:50 karl-laptop kernel: [   16.515492] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Nov  8 11:53:50 karl-laptop kernel: [   16.689463] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov  8 11:53:50 karl-laptop kernel: [   16.704045] ACPI: Power Button (FF) [PWRF]
Nov  8 11:53:50 karl-laptop kernel: [   16.704169] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov  8 11:53:50 karl-laptop kernel: [   16.720019] ACPI: Power Button (CM) [PWRB]
Nov  8 11:53:50 karl-laptop kernel: [   16.720117] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Nov  8 11:53:50 karl-laptop kernel: [   16.736021] ACPI: Sleep Button (CM) [SLPB]
Nov  8 11:53:50 karl-laptop kernel: [   16.736103] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
Nov  8 11:53:50 karl-laptop kernel: [   16.768073] ACPI: Lid Switch [LID]
Nov  8 11:53:50 karl-laptop kernel: [   16.805204] ACPI: AC Adapter [AC] (on-line)
Nov  8 11:53:50 karl-laptop kernel: [   17.099820] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 11:53:50 karl-laptop kernel: [   17.153129] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 11:53:50 karl-laptop kernel: [   17.300271] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:5402]
Nov  8 11:53:50 karl-laptop kernel: [   17.300291] Yenta: Enabling burst memory read transactions
Nov  8 11:53:50 karl-laptop kernel: [   17.300295] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov  8 11:53:50 karl-laptop kernel: [   17.300297] Yenta: Routing CardBus interrupts to PCI
Nov  8 11:53:50 karl-laptop kernel: [   17.300302] Yenta TI: socket 0000:00:0c.0, mfunc 0x00001202, devctl 0x44
Nov  8 11:53:50 karl-laptop kernel: [   17.424193] sdhci: Secure Digital Host Controller Interface driver
Nov  8 11:53:50 karl-laptop kernel: [   17.424198] sdhci: Copyright(c) Pierre Ossman
Nov  8 11:53:50 karl-laptop kernel: [   17.532853] Yenta: ISA IRQ mask 0x0a80, PCI irq 16
Nov  8 11:53:50 karl-laptop kernel: [   17.532858] Socket status: 30000006
Nov  8 11:53:50 karl-laptop kernel: [   17.568419] sdhci-pci 0000:00:0c.2: SDHCI controller found [1524:0550] (rev 1)
Nov  8 11:53:50 karl-laptop kernel: [   17.568432] sdhci-pci 0000:00:0c.2: enabling device (0000 -> 0002)
Nov  8 11:53:50 karl-laptop kernel: [   17.568450] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 11:53:50 karl-laptop kernel: [   17.568540] mmc0: SDHCI controller on PCI [0000:00:0c.2] using PIO
Nov  8 11:53:50 karl-laptop kernel: [   17.568561] sdhci-pci 0000:00:0c.4: SDHCI controller found [1524:0551] (rev 1)
Nov  8 11:53:50 karl-laptop kernel: [   17.568570] sdhci-pci 0000:00:0c.4: enabling device (0000 -> 0002)
Nov  8 11:53:50 karl-laptop kernel: [   17.568579] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 11:53:50 karl-laptop kernel: [   17.568609] mmc1: SDHCI controller on PCI [0000:00:0c.4] using PIO
Nov  8 11:53:50 karl-laptop kernel: [   18.032134] ACPI: Battery Slot [BAT0] (battery present)
Nov  8 11:53:50 karl-laptop kernel: [   18.032932] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/input/input6
Nov  8 11:53:50 karl-laptop kernel: [   18.048034] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov  8 11:53:50 karl-laptop kernel: [   18.402466] NET: Registered protocol family 23
Nov  8 11:53:50 karl-laptop kernel: [   18.598293] input: PC Speaker as /devices/platform/pcspkr/input/input7
Nov  8 11:53:50 karl-laptop kernel: [   18.855207] rt61pci 0000:00:0d.0: enabling device (0010 -> 0012)
Nov  8 11:53:50 karl-laptop kernel: [   18.855221] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 11:53:50 karl-laptop kernel: [   19.484929] Registered led device: rt61pci-phy0:radio
Nov  8 11:53:50 karl-laptop kernel: [   19.484945] Registered led device: rt61pci-phy0:assoc
Nov  8 11:53:50 karl-laptop kernel: [   19.589820] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 11:53:50 karl-laptop kernel: [   19.589830] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Nov  8 11:53:50 karl-laptop kernel: [   19.589902] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
Nov  8 11:53:50 karl-laptop kernel: [   19.589972] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Nov  8 11:53:50 karl-laptop kernel: [   19.589975] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Nov  8 11:53:50 karl-laptop kernel: [   19.589984] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 11:53:50 karl-laptop kernel: [   19.930664] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
Nov  8 11:53:50 karl-laptop kernel: [   20.200097] MC'97 1 converters and GPIO not ready (0xff00)
Nov  8 11:53:50 karl-laptop kernel: [   20.239560] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 11:53:50 karl-laptop kernel: [   20.239576] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 11:53:50 karl-laptop kernel: [   20.885953] cs: IO port probe 0x100-0x3af: clean.
Nov  8 11:53:50 karl-laptop kernel: [   20.887962] cs: IO port probe 0x3e0-0x4ff: clean.
Nov  8 11:53:50 karl-laptop kernel: [   20.888791] cs: IO port probe 0x820-0x8ff: clean.
Nov  8 11:53:50 karl-laptop kernel: [   20.889462] cs: IO port probe 0xc00-0xcf7: clean.
Nov  8 11:53:50 karl-laptop kernel: [   20.890285] cs: IO port probe 0xa00-0xaff: clean.
Nov  8 11:53:50 karl-laptop kernel: [   22.151843] lp: driver loaded but no devices found
Nov  8 11:53:50 karl-laptop kernel: [   22.211503] [drm] Initialized drm 1.1.0 20060810
Nov  8 11:53:50 karl-laptop kernel: [   22.243624] pci 0000:01:00.0: power state changed by ACPI to D0
Nov  8 11:53:50 karl-laptop kernel: [   22.243642] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 11:53:50 karl-laptop kernel: [   22.244543] [drm] Initialized via 2.11.1 20070202 on minor 0
Nov  8 11:53:50 karl-laptop kernel: [   22.369695] Adding 554200k swap on /dev/sda5.  Priority:-1 extents:1 across:554200k
Nov  8 11:53:50 karl-laptop kernel: [   22.451874] Adding 554168k swap on /dev/sda6.  Priority:-2 extents:1 across:554168k
Nov  8 11:53:50 karl-laptop kernel: [   22.509115] Adding 425648k swap on /dev/sda7.  Priority:-3 extents:1 across:425648k
Nov  8 11:53:50 karl-laptop kernel: [   23.070653] EXT3 FS on sda2, internal journal
Nov  8 11:53:50 karl-laptop kernel: [   24.019731] type=1505 audit(1226161428.131:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4207
Nov  8 11:53:50 karl-laptop kernel: [   24.198515] type=1505 audit(1226161428.311:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4212
Nov  8 11:53:50 karl-laptop kernel: [   24.198892] type=1505 audit(1226161428.311:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4212
Nov  8 11:53:50 karl-laptop kernel: [   24.319457] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  8 11:53:50 karl-laptop kernel: [   25.096014] Clocksource tsc unstable (delta = 4687126080 ns)
Nov  8 11:53:50 karl-laptop kernel: [   25.575009] ACPI: WMI: Mapper loaded
Nov  8 11:53:50 karl-laptop kernel: [   26.362122] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Nov  8 11:53:50 karl-laptop kernel: [   26.409203] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 11:53:50 karl-laptop kernel: [   26.409210] apm: overridden by ACPI.
Nov  8 11:53:50 karl-laptop kernel: [   26.571852] ppdev: user-space parallel port driver
Nov  8 11:53:52 karl-laptop kernel: [   28.280005] Bluetooth: Core ver 2.13
Nov  8 11:53:52 karl-laptop kernel: [   28.283173] NET: Registered protocol family 31
Nov  8 11:53:52 karl-laptop kernel: [   28.283188] Bluetooth: HCI device and connection manager initialized
Nov  8 11:53:52 karl-laptop kernel: [   28.283198] Bluetooth: HCI socket layer initialized
Nov  8 11:53:52 karl-laptop kernel: [   28.343886] Bluetooth: L2CAP ver 2.11
Nov  8 11:53:52 karl-laptop kernel: [   28.343904] Bluetooth: L2CAP socket layer initialized
Nov  8 11:53:52 karl-laptop kernel: [   28.392474] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  8 11:53:52 karl-laptop kernel: [   28.392495] Bluetooth: BNEP filters: protocol multicast
Nov  8 11:53:52 karl-laptop kernel: [   28.448005] Bridge firewalling registered
Nov  8 11:53:52 karl-laptop kernel: [   28.472009] Bluetooth: RFCOMM socket layer initialized
Nov  8 11:53:52 karl-laptop kernel: [   28.472364] Bluetooth: RFCOMM TTY layer initialized
Nov  8 11:53:52 karl-laptop kernel: [   28.472384] Bluetooth: RFCOMM ver 1.10
Nov  8 11:53:52 karl-laptop kernel: [   28.492006] Bluetooth: SCO (Voice Link) ver 0.6
Nov  8 11:53:52 karl-laptop kernel: [   28.492006] Bluetooth: SCO socket layer initialized
Nov  8 11:53:55 karl-laptop kernel: [   30.969120] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Nov  8 11:53:55 karl-laptop kernel: [   30.969151] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Nov  8 11:53:55 karl-laptop kernel: [   30.969158] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
Nov  8 11:53:55 karl-laptop kernel: [   30.969238] pci 0000:01:00.0: putting AGP V2 device into 0x mode
Nov  8 11:53:56 karl-laptop kernel: [   32.626098] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  8 11:53:56 karl-laptop kernel: [   32.629011] firmware: requesting rt2561.bin
Nov  8 11:53:56 karl-laptop kernel: [   32.883245] NET: Registered protocol family 17
Nov  8 11:54:24 karl-laptop pulseaudio[5549]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 11:54:24 karl-laptop pulseaudio[5551]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 11:54:24 karl-laptop pulseaudio[5551]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 11:54:25 karl-laptop pulseaudio[5551]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  8 11:56:25 karl-laptop kernel: [  175.857481] type=1503 audit(1226161585.238:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5774/net/" pid=5774 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.075340] type=1503 audit(1226161586.453:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5778/net/" pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.379211] NET: Registered protocol family 10
Nov  8 11:56:26 karl-laptop kernel: [  177.380723] lo: Disabled Privacy Extensions
Nov  8 11:56:26 karl-laptop kernel: [  177.382313] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  8 11:56:26 karl-laptop kernel: [  177.383507] type=1503 audit(1226161586.761:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383517] type=1503 audit(1226161586.761:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383524] type=1503 audit(1226161586.761:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383530] type=1503 audit(1226161586.761:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383536] type=1503 audit(1226161586.761:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383542] type=1503 audit(1226161586.761:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383548] type=1503 audit(1226161586.761:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 11:56:26 karl-laptop kernel: [  177.383555] type=1503 audit(1226161586.761:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5778 profile="/usr/sbin/cupsd"
Nov  8 12:13:55 karl-laptop -- MARK --
Nov  8 12:33:56 karl-laptop -- MARK --
Nov  8 12:53:56 karl-laptop -- MARK --
Nov  8 12:58:22 karl-laptop kernel: [ 3892.622711] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 12:58:22 karl-laptop kernel: [ 3892.622732] apm: disabled on user request.
Nov  8 12:58:23 karl-laptop bonobo-activation-server (karl-6361): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ytlTcHXjdd: Connection refused
Nov  8 12:58:24 karl-laptop kernel: [ 3895.380761] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov  8 12:58:44 karl-laptop exiting on signal 15
Nov  8 12:59:26 karl-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov  8 12:59:26 karl-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov  8 12:59:26 karl-laptop kernel: Cannot find map file.
Nov  8 12:59:26 karl-laptop kernel: Loaded 52295 symbols from 106 modules.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bef0000 - 000000000befa000 (ACPI data)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000befa000 - 000000000bf00000 (ACPI NVS)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] RAMDISK: 0b712000 - 0bedfaa7
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] DMI present.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: RSDP 000F7C80, 0014 (r0 PTLTD )
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: RSDT 0BEF6B92, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: FACP 0BEF9E0D, 0074 (r1 PN800  PTLTW     6040000 PTL_    F4240)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: DSDT 0BEF6BC2, 324B (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: FACS 0BEFAFC0, 0040
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: APIC 0BEF9E81, 0046 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: SSDT 0BEF9EC7, 0139 (r1 PTLTD    CpuGv3  6040000  LTP        1)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] 190MB LOWMEM available.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   mapped low ram: 0 - 0bef0000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   low ram: 00000000 - 0bef0000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   bootmap 00002000 - 000037e0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #4 [000b712000 - 000bedfaa7]          RAMDISK ==> [000b712000 - 000bedfaa7]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] found SMP MP-table at [c00f7cb0] 000f7cb0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Zone PFN ranges:
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0000bef0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Nov  8 12:59:26 karl-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0000bef0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3f80000)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48353
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Kernel command line: root=UUID=56b35b8f-d3f2-47ea-8972-3dad5a106954 ro quiet splash 
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Initializing CPU#0
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] TSC: using PIT calibration value
Nov  8 12:59:26 karl-laptop kernel: [    0.000000] Detected 2138.122 MHz processor.
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] console [tty0] enabled
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] Memory: 180092k/195520k available (2572k kernel code, 14888k reserved, 1160k data, 424k init, 0k highmem)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] virtual kernel memory layout:
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov  8 12:59:26 karl-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Nov  8 12:59:26 karl-laptop kernel: [    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 4276.24 BogoMIPS (lpj=8552488)
Nov  8 12:59:26 karl-laptop kernel: [    0.004045] Security Framework initialized
Nov  8 12:59:26 karl-laptop kernel: [    0.004061] SELinux:  Disabled at boot.
Nov  8 12:59:26 karl-laptop kernel: [    0.004094] AppArmor: AppArmor initialized
Nov  8 12:59:26 karl-laptop kernel: [    0.004105] Mount-cache hash table entries: 512
Nov  8 12:59:26 karl-laptop kernel: [    0.004338] Initializing cgroup subsys ns
Nov  8 12:59:26 karl-laptop kernel: [    0.004348] Initializing cgroup subsys cpuacct
Nov  8 12:59:26 karl-laptop kernel: [    0.004351] Initializing cgroup subsys memory
Nov  8 12:59:26 karl-laptop kernel: [    0.004373] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  8 12:59:26 karl-laptop kernel: [    0.004376] CPU: L2 cache: 2048K
Nov  8 12:59:26 karl-laptop kernel: [    0.004398] Checking 'hlt' instruction... OK.
Nov  8 12:59:26 karl-laptop kernel: [    0.020590] SMP alternatives: switching to UP code
Nov  8 12:59:26 karl-laptop kernel: [    0.024015] Freeing SMP alternatives: 11k freed
Nov  8 12:59:26 karl-laptop kernel: [    0.024019] ACPI: Core revision 20080609
Nov  8 12:59:26 karl-laptop kernel: [    0.026121] ACPI: Checking initramfs for custom DSDT
Nov  8 12:59:26 karl-laptop kernel: [    0.344090] ENABLING IO-APIC IRQs
Nov  8 12:59:26 karl-laptop kernel: [    0.344414] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov  8 12:59:26 karl-laptop kernel: [    0.348021] ...trying to set up timer (IRQ0) through the 8259A ...
Nov  8 12:59:26 karl-laptop kernel: [    0.348021] ..... (found apic 0 pin 0) ...
Nov  8 12:59:26 karl-laptop kernel: [    0.387902] ....... works.
Nov  8 12:59:26 karl-laptop kernel: [    0.387904] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] Brought up 1 CPUs
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] Total of 1 processors activated (4276.24 BogoMIPS).
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] net_namespace: 840 bytes
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] Booting paravirtualized kernel on bare hardware
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] Time: 12:59:02  Date: 11/08/08
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] NET: Registered protocol family 16
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] EISA bus registered
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] ACPI: bus type pci registered
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] PCI: PCI BIOS revision 2.10 entry at 0xfd8fc, last bus=1
Nov  8 12:59:26 karl-laptop kernel: [    0.388024] PCI: Using configuration type 1 for base access
Nov  8 12:59:26 karl-laptop kernel: [    0.389777] ACPI: Interpreter enabled
Nov  8 12:59:26 karl-laptop kernel: [    0.389780] ACPI: (supports S0 S3 S4 S5)
Nov  8 12:59:26 karl-laptop kernel: [    0.389792] ACPI: Using IOAPIC for interrupt routing
Nov  8 12:59:26 karl-laptop kernel: [    0.390357] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  8 12:59:26 karl-laptop kernel: [    0.904034] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  8 12:59:26 karl-laptop kernel: [    1.016212] ACPI: EC: GPE = 0xb, I/O: command/status = 0x66, data = 0x62
Nov  8 12:59:26 karl-laptop kernel: [    1.016215] ACPI: EC: driver started in poll mode
Nov  8 12:59:26 karl-laptop kernel: [    1.016261] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 12:59:26 karl-laptop kernel: [    1.016630] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.016635] pci 0000:00:0c.0: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.016701] pci 0000:00:0c.1: PME# supported from D0 D1 D2 D3hot
Nov  8 12:59:26 karl-laptop kernel: [    1.016705] pci 0000:00:0c.1: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.016771] pci 0000:00:0c.2: PME# supported from D0 D1 D2 D3hot
Nov  8 12:59:26 karl-laptop kernel: [    1.016775] pci 0000:00:0c.2: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.016843] pci 0000:00:0c.4: PME# supported from D0 D1 D2 D3hot
Nov  8 12:59:26 karl-laptop kernel: [    1.016847] pci 0000:00:0c.4: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.016975] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.016979] pci 0000:00:10.0: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.017041] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.017045] pci 0000:00:10.1: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.017108] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.017112] pci 0000:00:10.2: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.017175] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.017179] pci 0000:00:10.3: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.017239] HPET not enabled in BIOS. You might try hpet=force boot option
Nov  8 12:59:26 karl-laptop kernel: [    1.017246] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
Nov  8 12:59:26 karl-laptop kernel: [    1.017249] pci 0000:00:11.0: quirk: region 8100-810f claimed by vt8235 SMB
Nov  8 12:59:26 karl-laptop kernel: [    1.017513] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 12:59:26 karl-laptop kernel: [    1.017517] pci 0000:00:12.0: PME# disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.025586] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *3, disabled.
Nov  8 12:59:26 karl-laptop kernel: [    1.025687] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *4, disabled.
Nov  8 12:59:26 karl-laptop kernel: [    1.025786] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
Nov  8 12:59:26 karl-laptop kernel: [    1.025883] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *9, disabled.
Nov  8 12:59:26 karl-laptop kernel: [    1.026013] ACPI: PCI Interrupt Link [LNKA] (IRQs *3)
Nov  8 12:59:26 karl-laptop kernel: [    1.026142] ACPI: PCI Interrupt Link [LNKB] (IRQs *4)
Nov  8 12:59:26 karl-laptop kernel: [    1.026269] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
Nov  8 12:59:26 karl-laptop kernel: [    1.026404] ACPI: PCI Interrupt Link [LNKD] (IRQs 6) *9
Nov  8 12:59:26 karl-laptop kernel: [    1.026570] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 12:59:26 karl-laptop kernel: [    1.026604] pnp: PnP ACPI init
Nov  8 12:59:26 karl-laptop kernel: [    1.026610] ACPI: bus type pnp registered
Nov  8 12:59:26 karl-laptop kernel: [    1.060060] pnp: PnP ACPI: found 9 devices
Nov  8 12:59:26 karl-laptop kernel: [    1.060063] ACPI: ACPI bus type pnp unregistered
Nov  8 12:59:26 karl-laptop kernel: [    1.060066] PnPBIOS: Disabled by ACPI PNP
Nov  8 12:59:26 karl-laptop kernel: [    1.060372] PCI: Using ACPI for IRQ routing
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NET: Registered protocol family 8
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NET: Registered protocol family 20
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NetLabel: Initializing
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NetLabel:  domain hash size = 128
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] NetLabel:  unlabeled traffic allowed by default
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] tracer: 772 pages allocated for 65536 entries of 48 bytes
Nov  8 12:59:26 karl-laptop kernel: [    1.060489]    actual entries 65620
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] AppArmor: AppArmor Filesystem Enabled
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0x0-0x9ffff could not be reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xffb80000-0xffbfffff has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xff380000-0xff3fffff has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xff780000-0xff7fffff has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:06: ioport range 0xfe10-0xfe11 has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:06: ioport range 0x4000-0x407f has been reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.060489] system 00:06: ioport range 0x8100-0x811f could not be reserved
Nov  8 12:59:26 karl-laptop kernel: [    1.095975] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf4000000-0xf3ffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.095979] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov  8 12:59:26 karl-laptop kernel: [    1.095981] pci 0000:00:01.0:   IO window: disabled
Nov  8 12:59:26 karl-laptop kernel: [    1.095986] pci 0000:00:01.0:   MEM window: 0xd1000000-0xd1ffffff
Nov  8 12:59:26 karl-laptop kernel: [    1.095990] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
Nov  8 12:59:26 karl-laptop kernel: [    1.095996] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
Nov  8 12:59:26 karl-laptop kernel: [    1.095998] pci 0000:00:0c.0:   IO window: 0x002000-0x0020ff
Nov  8 12:59:26 karl-laptop kernel: [    1.096003] pci 0000:00:0c.0:   IO window: 0x002400-0x0024ff
Nov  8 12:59:26 karl-laptop kernel: [    1.096007] pci 0000:00:0c.0:   PREFETCH window: 0x10000000-0x13ffffff
Nov  8 12:59:26 karl-laptop kernel: [    1.096011] pci 0000:00:0c.0:   MEM window: 0x14000000-0x17ffffff
Nov  8 12:59:26 karl-laptop kernel: [    1.096042] pci 0000:00:0c.0: enabling device (0000 -> 0003)
Nov  8 12:59:26 karl-laptop kernel: [    1.096048] pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 12:59:26 karl-laptop kernel: [    1.096062] bus: 00 index 0 io port: [0, ffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096064] bus: 00 index 1 mmio: [0, ffffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096066] bus: 01 index 0 mmio: [0, 0]
Nov  8 12:59:26 karl-laptop kernel: [    1.096068] bus: 01 index 1 mmio: [d1000000, d1ffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096070] bus: 01 index 2 mmio: [f0000000, f3ffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096072] bus: 01 index 3 mmio: [0, 0]
Nov  8 12:59:26 karl-laptop kernel: [    1.096074] bus: 02 index 0 io port: [2000, 20ff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096076] bus: 02 index 1 io port: [2400, 24ff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096078] bus: 02 index 2 mmio: [10000000, 13ffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096080] bus: 02 index 3 mmio: [14000000, 17ffffff]
Nov  8 12:59:26 karl-laptop kernel: [    1.096089] NET: Registered protocol family 2
Nov  8 12:59:26 karl-laptop kernel: [    1.096205] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    1.096393] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    1.096459] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    1.096519] TCP: Hash tables configured (established 8192 bind 8192)
Nov  8 12:59:26 karl-laptop kernel: [    1.096523] TCP reno registered
Nov  8 12:59:26 karl-laptop kernel: [    1.096583] NET: Registered protocol family 1
Nov  8 12:59:26 karl-laptop kernel: [    1.096699] checking if image is initramfs... it is
Nov  8 12:59:26 karl-laptop kernel: [    1.745050] Freeing initrd memory: 7990k freed
Nov  8 12:59:26 karl-laptop kernel: [    1.745959] audit: initializing netlink socket (disabled)
Nov  8 12:59:26 karl-laptop kernel: [    1.745986] type=2000 audit(1226149143.744:1): initialized
Nov  8 12:59:26 karl-laptop kernel: [    1.751822] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov  8 12:59:26 karl-laptop kernel: [    1.754076] VFS: Disk quotas dquot_6.5.1
Nov  8 12:59:26 karl-laptop kernel: [    1.754166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 12:59:26 karl-laptop kernel: [    1.754279] msgmni has been set to 367
Nov  8 12:59:26 karl-laptop kernel: [    1.754421] io scheduler noop registered
Nov  8 12:59:26 karl-laptop kernel: [    1.754425] io scheduler anticipatory registered
Nov  8 12:59:26 karl-laptop kernel: [    1.754427] io scheduler deadline registered
Nov  8 12:59:26 karl-laptop kernel: [    1.754438] io scheduler cfq registered (default)
Nov  8 12:59:26 karl-laptop kernel: [    1.754460] PCI: VIA PCI bridge detected.Disabling DAC.
Nov  8 12:59:26 karl-laptop kernel: [    1.754895] isapnp: Scanning for PnP cards...
Nov  8 12:59:26 karl-laptop kernel: [    2.108669] isapnp: No Plug & Play device found
Nov  8 12:59:26 karl-laptop kernel: [    2.141682] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov  8 12:59:26 karl-laptop kernel: [    2.143848] brd: module loaded
Nov  8 12:59:26 karl-laptop kernel: [    2.143922] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov  8 12:59:26 karl-laptop kernel: [    2.144328] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  8 12:59:26 karl-laptop kernel: [    2.146766] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov  8 12:59:26 karl-laptop kernel: [    2.147911] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 12:59:26 karl-laptop kernel: [    2.147918] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov  8 12:59:26 karl-laptop kernel: [    2.147921] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov  8 12:59:26 karl-laptop kernel: [    2.147923] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov  8 12:59:26 karl-laptop kernel: [    2.147925] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov  8 12:59:26 karl-laptop kernel: [    2.148362] mice: PS/2 mouse device common for all mice
Nov  8 12:59:26 karl-laptop kernel: [    2.148500] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov  8 12:59:26 karl-laptop kernel: [    2.148542] rtc0: alarms up to one year, y3k
Nov  8 12:59:26 karl-laptop kernel: [    2.148660] EISA: Probing bus 0 at eisa.0
Nov  8 12:59:26 karl-laptop kernel: [    2.148669] Cannot allocate resource for EISA slot 1
Nov  8 12:59:26 karl-laptop kernel: [    2.148671] Cannot allocate resource for EISA slot 2
Nov  8 12:59:26 karl-laptop kernel: [    2.148677] Cannot allocate resource for EISA slot 4
Nov  8 12:59:26 karl-laptop kernel: [    2.148694] EISA: Detected 0 cards.
Nov  8 12:59:26 karl-laptop kernel: [    2.148699] cpuidle: using governor ladder
Nov  8 12:59:26 karl-laptop kernel: [    2.148701] cpuidle: using governor menu
Nov  8 12:59:26 karl-laptop kernel: [    2.149199] TCP cubic registered
Nov  8 12:59:26 karl-laptop kernel: [    2.149241] Using IPI No-Shortcut mode
Nov  8 12:59:26 karl-laptop kernel: [    2.149427] registered taskstats version 1
Nov  8 12:59:26 karl-laptop kernel: [    2.149547]   Magic number: 0:346:986
Nov  8 12:59:26 karl-laptop kernel: [    2.149775] rtc_cmos 00:02: setting system clock to 2008-11-08 12:59:04 UTC (1226149144)
Nov  8 12:59:26 karl-laptop kernel: [    2.149779] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  8 12:59:26 karl-laptop kernel: [    2.149781] EDD information not available.
Nov  8 12:59:26 karl-laptop kernel: [    2.150074] Freeing unused kernel memory: 424k freed
Nov  8 12:59:26 karl-laptop kernel: [    2.150120] Write protecting the kernel text: 2576k
Nov  8 12:59:26 karl-laptop kernel: [    2.150147] Write protecting the kernel read-only data: 936k
Nov  8 12:59:26 karl-laptop kernel: [    2.172087] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov  8 12:59:26 karl-laptop kernel: [    2.319904] fuse init (API version 7.9)
Nov  8 12:59:26 karl-laptop kernel: [    2.504578] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov  8 12:59:26 karl-laptop kernel: [    2.504634] processor ACPI0007:00: registered as cooling_device0
Nov  8 12:59:26 karl-laptop kernel: [    2.504638] ACPI: Processor [CPU0] (supports 16 throttling states)
Nov  8 12:59:26 karl-laptop kernel: [    2.506870] Marking TSC unstable due to TSC halts in idle
Nov  8 12:59:26 karl-laptop kernel: [    2.764359] thermal LNXTHERM:01: registered as thermal_zone0
Nov  8 12:59:26 karl-laptop kernel: [    3.020036] ACPI: Thermal Zone [THRM] (52 C)
Nov  8 12:59:26 karl-laptop kernel: [    3.534155] usbcore: registered new interface driver usbfs
Nov  8 12:59:26 karl-laptop kernel: [    3.534186] usbcore: registered new interface driver hub
Nov  8 12:59:26 karl-laptop kernel: [    3.534234] usbcore: registered new device driver usb
Nov  8 12:59:26 karl-laptop kernel: [    3.536392] USB Universal Host Controller Interface driver v3.0
Nov  8 12:59:26 karl-laptop kernel: [    3.539019] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
Nov  8 12:59:26 karl-laptop kernel: [    3.539093] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    3.539096] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    3.539107] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    3.539118] uhci_hcd 0000:00:10.0: UHCI Host Controller
Nov  8 12:59:26 karl-laptop kernel: [    3.539181] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Nov  8 12:59:26 karl-laptop kernel: [    3.539218] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001020
Nov  8 12:59:26 karl-laptop kernel: [    3.539447] usb usb1: configuration #1 chosen from 1 choice
Nov  8 12:59:26 karl-laptop kernel: [    3.539479] hub 1-0:1.0: USB hub found
Nov  8 12:59:26 karl-laptop kernel: [    3.539494] hub 1-0:1.0: 2 ports detected
Nov  8 12:59:26 karl-laptop kernel: [    3.568537] No dock devices found.
Nov  8 12:59:26 karl-laptop kernel: [    3.595849] SCSI subsystem initialized
Nov  8 12:59:26 karl-laptop kernel: [    3.666010] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Nov  8 12:59:26 karl-laptop kernel: [    3.744397] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    3.744411] uhci_hcd 0000:00:10.1: UHCI Host Controller
Nov  8 12:59:26 karl-laptop kernel: [    3.744436] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Nov  8 12:59:26 karl-laptop kernel: [    3.744462] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001040
Nov  8 12:59:26 karl-laptop kernel: [    3.744565] usb usb2: configuration #1 chosen from 1 choice
Nov  8 12:59:26 karl-laptop kernel: [    3.744592] hub 2-0:1.0: USB hub found
Nov  8 12:59:26 karl-laptop kernel: [    3.744602] hub 2-0:1.0: 2 ports detected
Nov  8 12:59:26 karl-laptop kernel: [    3.952393] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    3.952408] uhci_hcd 0000:00:10.2: UHCI Host Controller
Nov  8 12:59:26 karl-laptop kernel: [    3.952437] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Nov  8 12:59:26 karl-laptop kernel: [    3.952463] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001060
Nov  8 12:59:26 karl-laptop kernel: [    3.952568] usb usb3: configuration #1 chosen from 1 choice
Nov  8 12:59:26 karl-laptop kernel: [    3.952595] hub 3-0:1.0: USB hub found
Nov  8 12:59:26 karl-laptop kernel: [    3.952602] hub 3-0:1.0: 2 ports detected
Nov  8 12:59:26 karl-laptop kernel: [    4.160437] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 12:59:26 karl-laptop kernel: [    4.160460] ehci_hcd 0000:00:10.3: EHCI Host Controller
Nov  8 12:59:26 karl-laptop kernel: [    4.160484] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Nov  8 12:59:26 karl-laptop kernel: [    4.160517] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0000c00
Nov  8 12:59:26 karl-laptop kernel: [    4.172046] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 12:59:26 karl-laptop kernel: [    4.172275] usb usb4: configuration #1 chosen from 1 choice
Nov  8 12:59:26 karl-laptop kernel: [    4.172305] hub 4-0:1.0: USB hub found
Nov  8 12:59:26 karl-laptop kernel: [    4.172314] hub 4-0:1.0: 6 ports detected
Nov  8 12:59:26 karl-laptop kernel: [    4.276402] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  8 12:59:26 karl-laptop kernel: [    4.280592] eth0: VIA Rhine II at 0xd0001000, 00:90:f5:37:fa:d5, IRQ 23.
Nov  8 12:59:26 karl-laptop kernel: [    4.281299] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Nov  8 12:59:26 karl-laptop kernel: [    4.284782] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 12:59:26 karl-laptop kernel: [    4.284866] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
Nov  8 12:59:26 karl-laptop kernel: [    4.284939] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
Nov  8 12:59:26 karl-laptop kernel: [    4.284941] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
Nov  8 12:59:26 karl-laptop kernel: [    4.284944] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
Nov  8 12:59:26 karl-laptop kernel: [    4.285986] scsi0 : pata_via
Nov  8 12:59:26 karl-laptop kernel: [    4.286097] scsi1 : pata_via
Nov  8 12:59:26 karl-laptop kernel: [    4.286902] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
Nov  8 12:59:26 karl-laptop kernel: [    4.286905] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
Nov  8 12:59:26 karl-laptop kernel: [    4.784516] ata1.00: ATA-7: SAMSUNG MP0402H, YQ200-06, max UDMA/100
Nov  8 12:59:26 karl-laptop kernel: [    4.784521] ata1.00: 78242976 sectors, multi 16: LBA48 
Nov  8 12:59:26 karl-laptop kernel: [    4.800356] ata1.00: configured for UDMA/100
Nov  8 12:59:26 karl-laptop kernel: [    4.964348] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TX11, max UDMA/33
Nov  8 12:59:26 karl-laptop kernel: [    4.980226] ata2.00: configured for UDMA/33
Nov  8 12:59:26 karl-laptop kernel: [    4.980373] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0402H  YQ20 PQ: 0 ANSI: 5
Nov  8 12:59:26 karl-laptop kernel: [    4.981105] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TX11 PQ: 0 ANSI: 5
Nov  8 12:59:26 karl-laptop kernel: [    4.992889] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 12:59:26 karl-laptop kernel: [    4.992929] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Nov  8 12:59:26 karl-laptop kernel: [    5.008816] Driver 'sd' needs updating - please use bus_type methods
Nov  8 12:59:26 karl-laptop kernel: [    5.008950] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 12:59:26 karl-laptop kernel: [    5.008970] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 12:59:26 karl-laptop kernel: [    5.009003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 12:59:26 karl-laptop kernel: [    5.009081] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 12:59:26 karl-laptop kernel: [    5.009098] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 12:59:26 karl-laptop kernel: [    5.009131] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 12:59:26 karl-laptop kernel: [    5.009135]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov  8 12:59:26 karl-laptop kernel: [    5.488437]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Nov  8 12:59:26 karl-laptop kernel: [    5.530499] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 12:59:26 karl-laptop kernel: [    5.540126] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
Nov  8 12:59:26 karl-laptop kernel: [    5.540132] Uniform CD-ROM driver Revision: 3.20
Nov  8 12:59:26 karl-laptop kernel: [    5.987865] PM: Starting manual resume from disk
Nov  8 12:59:26 karl-laptop kernel: [    6.024598] kjournald starting.  Commit interval 5 seconds
Nov  8 12:59:26 karl-laptop kernel: [    6.024611] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 12:59:26 karl-laptop kernel: [   13.617842] udevd version 124 started
Nov  8 12:59:26 karl-laptop kernel: [   14.188138] Linux agpgart interface v0.103
Nov  8 12:59:26 karl-laptop kernel: [   14.272860] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
Nov  8 12:59:26 karl-laptop kernel: [   14.280635] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Nov  8 12:59:26 karl-laptop kernel: [   14.402295] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 12:59:26 karl-laptop kernel: [   14.455412] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 12:59:26 karl-laptop kernel: [   14.693130] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov  8 12:59:26 karl-laptop kernel: [   14.708037] ACPI: Power Button (FF) [PWRF]
Nov  8 12:59:26 karl-laptop kernel: [   14.708196] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov  8 12:59:26 karl-laptop kernel: [   14.724022] ACPI: Power Button (CM) [PWRB]
Nov  8 12:59:26 karl-laptop kernel: [   14.724118] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Nov  8 12:59:26 karl-laptop kernel: [   14.737041] ACPI: Sleep Button (CM) [SLPB]
Nov  8 12:59:26 karl-laptop kernel: [   14.737133] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
Nov  8 12:59:26 karl-laptop kernel: [   14.737331] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:5402]
Nov  8 12:59:26 karl-laptop kernel: [   14.737348] Yenta: Enabling burst memory read transactions
Nov  8 12:59:26 karl-laptop kernel: [   14.737352] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov  8 12:59:26 karl-laptop kernel: [   14.737354] Yenta: Routing CardBus interrupts to PCI
Nov  8 12:59:26 karl-laptop kernel: [   14.737358] Yenta TI: socket 0000:00:0c.0, mfunc 0x00001202, devctl 0x44
Nov  8 12:59:26 karl-laptop kernel: [   14.768075] ACPI: Lid Switch [LID]
Nov  8 12:59:26 karl-laptop kernel: [   14.782631] sdhci: Secure Digital Host Controller Interface driver
Nov  8 12:59:26 karl-laptop kernel: [   14.782634] sdhci: Copyright(c) Pierre Ossman
Nov  8 12:59:26 karl-laptop kernel: [   14.968900] Yenta: ISA IRQ mask 0x0af8, PCI irq 16
Nov  8 12:59:26 karl-laptop kernel: [   14.968981] Socket status: 30000006
Nov  8 12:59:26 karl-laptop kernel: [   14.969342] sdhci-pci 0000:00:0c.2: SDHCI controller found [1524:0550] (rev 1)
Nov  8 12:59:26 karl-laptop kernel: [   14.969354] sdhci-pci 0000:00:0c.2: enabling device (0000 -> 0002)
Nov  8 12:59:26 karl-laptop kernel: [   14.969371] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 12:59:26 karl-laptop kernel: [   14.969456] mmc0: SDHCI controller on PCI [0000:00:0c.2] using PIO
Nov  8 12:59:26 karl-laptop kernel: [   14.969474] sdhci-pci 0000:00:0c.4: SDHCI controller found [1524:0551] (rev 1)
Nov  8 12:59:26 karl-laptop kernel: [   14.969483] sdhci-pci 0000:00:0c.4: enabling device (0000 -> 0002)
Nov  8 12:59:26 karl-laptop kernel: [   14.969492] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 12:59:26 karl-laptop kernel: [   14.969523] mmc1: SDHCI controller on PCI [0000:00:0c.4] using PIO
Nov  8 12:59:26 karl-laptop kernel: [   15.460228] rt61pci 0000:00:0d.0: enabling device (0010 -> 0012)
Nov  8 12:59:26 karl-laptop kernel: [   15.460242] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 12:59:26 karl-laptop kernel: [   15.836667] Registered led device: rt61pci-phy0:radio
Nov  8 12:59:26 karl-laptop kernel: [   15.836684] Registered led device: rt61pci-phy0:assoc
Nov  8 12:59:26 karl-laptop kernel: [   16.164230] NET: Registered protocol family 23
Nov  8 12:59:26 karl-laptop kernel: [   16.316131] ACPI: Battery Slot [BAT0] (battery present)
Nov  8 12:59:26 karl-laptop kernel: [   16.348158] ACPI: AC Adapter [AC] (on-line)
Nov  8 12:59:26 karl-laptop kernel: [   16.348505] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/input/input6
Nov  8 12:59:26 karl-laptop kernel: [   16.364043] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov  8 12:59:26 karl-laptop kernel: [   16.565731] input: PC Speaker as /devices/platform/pcspkr/input/input7
Nov  8 12:59:26 karl-laptop kernel: [   16.980230] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 12:59:26 karl-laptop kernel: [   16.980240] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Nov  8 12:59:26 karl-laptop kernel: [   16.980312] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
Nov  8 12:59:26 karl-laptop kernel: [   16.980382] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Nov  8 12:59:26 karl-laptop kernel: [   16.980385] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Nov  8 12:59:26 karl-laptop kernel: [   16.980395] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 12:59:26 karl-laptop kernel: [   17.592156] MC'97 1 converters and GPIO not ready (0xff00)
Nov  8 12:59:26 karl-laptop kernel: [   17.593172] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 12:59:26 karl-laptop kernel: [   17.593188] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 12:59:26 karl-laptop kernel: [   17.690752] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
Nov  8 12:59:26 karl-laptop kernel: [   18.531838] cs: IO port probe 0x100-0x3af: clean.
Nov  8 12:59:26 karl-laptop kernel: [   18.533802] cs: IO port probe 0x3e0-0x4ff: clean.
Nov  8 12:59:26 karl-laptop kernel: [   18.534612] cs: IO port probe 0x820-0x8ff: clean.
Nov  8 12:59:26 karl-laptop kernel: [   18.535283] cs: IO port probe 0xc00-0xcf7: clean.
Nov  8 12:59:26 karl-laptop kernel: [   18.536170] cs: IO port probe 0xa00-0xaff: clean.
Nov  8 12:59:26 karl-laptop kernel: [   19.797730] lp: driver loaded but no devices found
Nov  8 12:59:26 karl-laptop kernel: [   19.854277] [drm] Initialized drm 1.1.0 20060810
Nov  8 12:59:26 karl-laptop kernel: [   19.900628] pci 0000:01:00.0: power state changed by ACPI to D0
Nov  8 12:59:26 karl-laptop kernel: [   19.900646] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 12:59:26 karl-laptop kernel: [   19.901486] [drm] Initialized via 2.11.1 20070202 on minor 0
Nov  8 12:59:26 karl-laptop kernel: [   20.015491] Adding 554200k swap on /dev/sda5.  Priority:-1 extents:1 across:554200k
Nov  8 12:59:26 karl-laptop kernel: [   20.053933] Adding 554168k swap on /dev/sda6.  Priority:-2 extents:1 across:554168k
Nov  8 12:59:26 karl-laptop kernel: [   20.110617] Adding 425648k swap on /dev/sda7.  Priority:-3 extents:1 across:425648k
Nov  8 12:59:26 karl-laptop kernel: [   20.670604] EXT3 FS on sda2, internal journal
Nov  8 12:59:26 karl-laptop kernel: [   21.698852] type=1505 audit(1226165364.163:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4220
Nov  8 12:59:26 karl-laptop kernel: [   21.877718] type=1505 audit(1226165364.343:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4225
Nov  8 12:59:26 karl-laptop kernel: [   21.878080] type=1505 audit(1226165364.343:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4225
Nov  8 12:59:26 karl-laptop kernel: [   22.020758] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  8 12:59:26 karl-laptop kernel: [   22.682640] Clocksource tsc unstable (delta = 4687130677 ns)
Nov  8 12:59:26 karl-laptop kernel: [   23.764189] ACPI: WMI: Mapper loaded
Nov  8 12:59:27 karl-laptop kernel: [   24.606786] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Nov  8 12:59:27 karl-laptop kernel: [   24.690613] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 12:59:27 karl-laptop kernel: [   24.690621] apm: overridden by ACPI.
Nov  8 12:59:27 karl-laptop kernel: [   24.883564] ppdev: user-space parallel port driver
Nov  8 12:59:29 karl-laptop kernel: [   26.712005] Bluetooth: Core ver 2.13
Nov  8 12:59:29 karl-laptop kernel: [   26.715936] NET: Registered protocol family 31
Nov  8 12:59:29 karl-laptop kernel: [   26.715951] Bluetooth: HCI device and connection manager initialized
Nov  8 12:59:29 karl-laptop kernel: [   26.715961] Bluetooth: HCI socket layer initialized
Nov  8 12:59:29 karl-laptop kernel: [   26.754230] Bluetooth: L2CAP ver 2.11
Nov  8 12:59:29 karl-laptop kernel: [   26.754249] Bluetooth: L2CAP socket layer initialized
Nov  8 12:59:29 karl-laptop kernel: [   26.792064] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  8 12:59:29 karl-laptop kernel: [   26.792084] Bluetooth: BNEP filters: protocol multicast
Nov  8 12:59:29 karl-laptop kernel: [   26.846482] Bridge firewalling registered
Nov  8 12:59:29 karl-laptop kernel: [   26.880006] Bluetooth: RFCOMM socket layer initialized
Nov  8 12:59:29 karl-laptop kernel: [   26.880006] Bluetooth: RFCOMM TTY layer initialized
Nov  8 12:59:29 karl-laptop kernel: [   26.880006] Bluetooth: RFCOMM ver 1.10
Nov  8 12:59:29 karl-laptop kernel: [   26.883210] Bluetooth: SCO (Voice Link) ver 0.6
Nov  8 12:59:29 karl-laptop kernel: [   26.883225] Bluetooth: SCO socket layer initialized
Nov  8 12:59:31 karl-laptop kernel: [   29.402079] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Nov  8 12:59:31 karl-laptop kernel: [   29.402109] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Nov  8 12:59:31 karl-laptop kernel: [   29.402116] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
Nov  8 12:59:31 karl-laptop kernel: [   29.402195] pci 0000:01:00.0: putting AGP V2 device into 0x mode
Nov  8 12:59:33 karl-laptop kernel: [   30.972991] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  8 12:59:33 karl-laptop kernel: [   30.974353] firmware: requesting rt2561.bin
Nov  8 12:59:33 karl-laptop kernel: [   31.412006] NET: Registered protocol family 17
Nov  8 12:59:52 karl-laptop pulseaudio[5562]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 12:59:52 karl-laptop pulseaudio[5564]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 12:59:52 karl-laptop pulseaudio[5564]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 12:59:52 karl-laptop pulseaudio[5564]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  8 13:02:05 karl-laptop kernel: [  178.101146] type=1503 audit(1226165525.815:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5832/net/" pid=5832 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.371203] type=1503 audit(1226165527.083:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5836/net/" pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.631775] NET: Registered protocol family 10
Nov  8 13:02:07 karl-laptop kernel: [  179.632845] lo: Disabled Privacy Extensions
Nov  8 13:02:07 karl-laptop kernel: [  179.634421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  8 13:02:07 karl-laptop kernel: [  179.635639] type=1503 audit(1226165527.347:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635649] type=1503 audit(1226165527.347:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635656] type=1503 audit(1226165527.347:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635662] type=1503 audit(1226165527.347:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635669] type=1503 audit(1226165527.347:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635675] type=1503 audit(1226165527.347:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635681] type=1503 audit(1226165527.347:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:02:07 karl-laptop kernel: [  179.635687] type=1503 audit(1226165527.347:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5836 profile="/usr/sbin/cupsd"
Nov  8 13:19:32 karl-laptop -- MARK --
Nov  8 13:39:33 karl-laptop -- MARK --
Nov  8 14:33:03 karl-laptop kernel: [ 2674.642504] PM: Syncing filesystems ... done.
Nov  8 14:33:04 karl-laptop kernel: [ 2674.642623] Freezing user space processes ... (elapsed 0.28 seconds) done.
Nov  8 14:33:04 karl-laptop kernel: [ 2674.931126] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov  8 14:33:04 karl-laptop kernel: [ 2674.931197] Suspending console(s) (use no_console_suspend to debug)
Nov  8 14:33:04 karl-laptop kernel: [ 2674.931675] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov  8 14:33:04 karl-laptop kernel: [ 2675.187388] sd 0:0:0:0: [sda] Stopping disk
Nov  8 14:33:04 karl-laptop kernel: [ 2676.252848] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.268055] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D3
Nov  8 14:33:04 karl-laptop kernel: [ 2676.268639] VIA 82xx Audio 0000:00:11.5: PCI INT C disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.284052] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D3
Nov  8 14:33:04 karl-laptop kernel: [ 2676.284144] pata_via 0000:00:11.1: PCI INT A disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.300063] pata_via 0000:00:11.1: power state changed by ACPI to D3
Nov  8 14:33:04 karl-laptop kernel: [ 2676.300126] ehci_hcd 0000:00:10.3: PCI INT D disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.316048] uhci_hcd 0000:00:10.2: PCI INT C disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.332046] uhci_hcd 0000:00:10.1: PCI INT B disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.348045] uhci_hcd 0000:00:10.0: PCI INT A disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.364065] rt61pci 0000:00:0d.0: PCI INT A disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.380058] sdhci-pci 0000:00:0c.4: PCI INT B disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.396057] sdhci-pci 0000:00:0c.2: PCI INT B disabled
Nov  8 14:33:04 karl-laptop kernel: [ 2676.428040] PM: suspend devices took 1.500 seconds
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508037] ACPI: Preparing to enter system sleep state S3
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] Disabling non-boot CPUs ...
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 3, using IRQ 23
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
Nov  8 14:33:04 karl-laptop kernel: [ 2676.508776] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 9, using IRQ 21
Nov  8 14:33:04 karl-laptop kernel: [ 2676.509618] ACPI: Waking up from system sleep state S3
Nov  8 14:33:04 karl-laptop kernel: [ 2676.828190] __ratelimit: 3 callbacks suppressed
Nov  8 14:33:04 karl-laptop kernel: [ 2676.828192] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  8 14:33:04 karl-laptop kernel: [ 2677.344014] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  8 14:33:04 karl-laptop kernel: [ 2678.828059] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 14:33:04 karl-laptop kernel: [ 2678.844054] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 14:33:04 karl-laptop kernel: [ 2678.860016] rt61pci 0000:00:0d.0: enabling device (0000 -> 0002)
Nov  8 14:33:04 karl-laptop kernel: [ 2678.860022] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 14:33:04 karl-laptop kernel: [ 2678.876017] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:33:04 karl-laptop kernel: [ 2678.876062] usb usb1: root hub lost power or was reset
Nov  8 14:33:04 karl-laptop kernel: [ 2678.892017] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:33:04 karl-laptop kernel: [ 2678.892059] usb usb2: root hub lost power or was reset
Nov  8 14:33:04 karl-laptop kernel: [ 2678.908017] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:33:04 karl-laptop kernel: [ 2678.908059] usb usb3: root hub lost power or was reset
Nov  8 14:33:04 karl-laptop kernel: [ 2678.924016] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:33:04 karl-laptop kernel: [ 2678.924047] usb usb4: root hub lost power or was reset
Nov  8 14:33:04 karl-laptop kernel: [ 2678.924125] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.924187] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.924193] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
Nov  8 14:33:04 karl-laptop kernel: [ 2678.926125] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.926211] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.926218] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 14:33:04 karl-laptop kernel: [ 2678.929504] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.929589] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.929595] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 14:33:04 karl-laptop kernel: [ 2678.932639] pci 0000:01:00.0: power state changed by ACPI to D0
Nov  8 14:33:04 karl-laptop kernel: [ 2678.932648] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 14:33:04 karl-laptop kernel: [ 2679.080346] sd 0:0:0:0: [sda] Starting disk
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088678] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088680] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088682] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088847] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088849] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.088851] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  8 14:33:04 karl-laptop kernel: [ 2679.104422] ata2.00: configured for UDMA/33
Nov  8 14:33:04 karl-laptop kernel: [ 2679.104541] ata1.00: configured for UDMA/100
Nov  8 14:33:04 karl-laptop kernel: [ 2679.205738] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 14:33:04 karl-laptop kernel: [ 2679.205759] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 14:33:04 karl-laptop kernel: [ 2679.205793] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 14:33:04 karl-laptop kernel: [ 2679.205979] PM: resume devices took 2.496 seconds
Nov  8 14:33:04 karl-laptop kernel: [ 2679.206110] Restarting tasks ... done.
Nov  8 14:33:36 karl-laptop kernel: [ 2711.320014] via-rhine: Reset not complete yet. Trying harder.
Nov  8 14:33:36 karl-laptop kernel: [ 2711.328007] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000046] ------------[ cut here ]------------
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000065] WARNING: at /build/buildd/linux-2.6.27/net/sched/sch_generic.c:219 dev_watchdog+0x21a/0x230()
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000075] NETDEV WATCHDOG: eth0 (via-rhine): transmit timed out
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000082] Modules linked in: ipv6 af_packet binfmt_misc sco rfcomm bridge stp bnep l2cap bluetooth ppdev acpi_cpufreq cpufreq_userspace cpufreq_conservative cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table wmi sbs container pci_slot sbshc iptable_filter ip_tables x_tables via drm parport_pc lp parport pcmcia snd_via82xx gameport snd_mpu401_uart snd_seq_dummy evdev snd_via82xx_modem serio_raw snd_seq_oss psmouse snd_ac97_codec snd_seq_midi snd_rawmidi ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_midi_event snd_pcm pcspkr snd_seq snd_timer snd_seq_device snd i2c_viapro snd_page_alloc i2c_core soundcore via_ircc irda crc_ccitt arc4 ecb crypto_blkcipher video output rt61pci crc_itu_t rt2x00pci rt2x00lib rfkill led_class mac80211 cfg80211 eeprom_93cx6 ac battery sdhci_pci sdhci yenta_socket rsrc_nonstatic button mmc_core pcmcia_core shpchp pci_hotplug via_agp agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi pata_via ata_generic via_rhine mii libata scs
Nov  8 14:34:20 karl-laptop kernel: _mod dock ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000356] Pid: 0, comm: swapper Not tainted 2.6.27-7-generic #1
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000366]  [<c0131d65>] warn_slowpath+0x65/0x90
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000384]  [<c0153200>] ? tick_program_event+0x30/0x40
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000399]  [<c014a675>] ? hrtimer_reprogram+0x85/0xc0
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000413]  [<c02dfe98>] ? acpi_pm_read+0x8/0x20
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000427]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000440]  [<c01136c0>] ? lapic_next_event+0x20/0x30
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000456]  [<c02dfe98>] ? acpi_pm_read+0x8/0x20
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000467]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000480]  [<c0136976>] ? set_normalized_timespec+0x16/0x90
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000493]  [<c014b76d>] ? ktime_get_ts+0x5d/0x70
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000505]  [<c0154387>] ? timer_stats_update_stats+0x17/0x250
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000517]  [<c0254299>] ? strlen+0x9/0x20
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000531]  [<c025231d>] ? strlcpy+0x1d/0x60
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000543]  [<c02f0967>] ? netdev_drivername+0x37/0x40
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000555]  [<c0305b6a>] dev_watchdog+0x21a/0x230
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000568]  [<c02fb0c0>] ? neigh_table_init_no_netlink+0x150/0x1e0
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000584]  [<c02fa870>] ? neigh_periodic_timer+0x0/0x190
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000596]  [<c013ca1f>] ? mod_timer+0x3f/0x80
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000610]  [<c02fa996>] ? neigh_periodic_timer+0x126/0x190
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000657]  [<c013bf88>] run_timer_softirq+0x138/0x210
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000669]  [<c0305950>] ? dev_watchdog+0x0/0x230
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000681]  [<c0305950>] ? dev_watchdog+0x0/0x230
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000694]  [<c0137682>] __do_softirq+0x92/0x120
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000704]  [<c013776d>] do_softirq+0x5d/0x60
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000714]  [<c01378e5>] irq_exit+0x55/0x90
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000724]  [<c0113f8d>] smp_apic_timer_interrupt+0x5d/0x90
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000736]  [<c01050f8>] apic_timer_interrupt+0x28/0x30
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000749]  [<c015007b>] ? sysfs_show_available_clocksources+0x1b/0xe0
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000764]  [<c011aba5>] ? native_safe_halt+0x5/0x10
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000802]  [<cc84fab4>] acpi_safe_halt+0x2f/0x47 [processor]
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000840]  [<cc850501>] acpi_idle_do_entry+0x21/0x30 [processor]
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000872]  [<cc850577>] acpi_idle_enter_c1+0x67/0x88 [processor]
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000897]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000907]  [<c010288d>] cpu_idle+0x7d/0x140
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000917]  [<c036edd3>] rest_init+0x53/0x60
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000932]  =======================
Nov  8 14:34:20 karl-laptop kernel: [ 2756.000939] ---[ end trace 9f2ea66ed32a5b0c ]---
Nov  8 14:34:20 karl-laptop kernel: [ 2756.002882] eth0: Transmit timed out, status ffff, PHY status ffff, resetting...
Nov  8 14:34:20 karl-laptop kernel: [ 2756.003102] via-rhine: Reset not complete yet. Trying harder.
Nov  8 14:34:20 karl-laptop kernel: [ 2756.004009] eth0: link up, 100Mbps, full-duplex, lpa 0xFFFF
Nov  8 14:40:21 karl-laptop kernel: [ 3116.610236] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 14:40:21 karl-laptop kernel: [ 3116.610257] apm: disabled on user request.
Nov  8 14:40:22 karl-laptop bonobo-activation-server (karl-8980): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LugE7jLYkz: Connection refused
Nov  8 14:40:22 karl-laptop kernel: [ 3118.094087] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov  8 14:40:26 karl-laptop exiting on signal 15
Nov  8 14:41:08 karl-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov  8 14:41:08 karl-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Nov  8 14:41:08 karl-laptop kernel: Cannot find map file.
Nov  8 14:41:08 karl-laptop kernel: Loaded 52295 symbols from 106 modules.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bef0000 - 000000000befa000 (ACPI data)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000befa000 - 000000000bf00000 (ACPI NVS)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] RAMDISK: 0b712000 - 0bedfaa7
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] DMI present.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: RSDP 000F7C80, 0014 (r0 PTLTD )
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: RSDT 0BEF6B92, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: FACP 0BEF9E0D, 0074 (r1 PN800  PTLTW     6040000 PTL_    F4240)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: DSDT 0BEF6BC2, 324B (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: FACS 0BEFAFC0, 0040
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: APIC 0BEF9E81, 0046 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: SSDT 0BEF9EC7, 0139 (r1 PTLTD    CpuGv3  6040000  LTP        1)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] 190MB LOWMEM available.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   mapped low ram: 0 - 0bef0000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   low ram: 00000000 - 0bef0000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   bootmap 00002000 - 000037e0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #4 [000b712000 - 000bedfaa7]          RAMDISK ==> [000b712000 - 000bedfaa7]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] found SMP MP-table at [c00f7cb0] 000f7cb0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Zone PFN ranges:
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0000bef0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Movable zone start PFN for each node
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Nov  8 14:41:08 karl-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0000bef0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3f80000)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48353
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Kernel command line: root=UUID=56b35b8f-d3f2-47ea-8972-3dad5a106954 ro quiet splash 
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Initializing CPU#0
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] TSC: using PIT calibration value
Nov  8 14:41:08 karl-laptop kernel: [    0.000000] Detected 2138.121 MHz processor.
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] console [tty0] enabled
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] Memory: 180092k/195520k available (2572k kernel code, 14888k reserved, 1160k data, 424k init, 0k highmem)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] virtual kernel memory layout:
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov  8 14:41:08 karl-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Nov  8 14:41:08 karl-laptop kernel: [    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 4276.24 BogoMIPS (lpj=8552484)
Nov  8 14:41:08 karl-laptop kernel: [    0.004045] Security Framework initialized
Nov  8 14:41:08 karl-laptop kernel: [    0.004061] SELinux:  Disabled at boot.
Nov  8 14:41:08 karl-laptop kernel: [    0.004093] AppArmor: AppArmor initialized
Nov  8 14:41:08 karl-laptop kernel: [    0.004104] Mount-cache hash table entries: 512
Nov  8 14:41:08 karl-laptop kernel: [    0.004334] Initializing cgroup subsys ns
Nov  8 14:41:08 karl-laptop kernel: [    0.004343] Initializing cgroup subsys cpuacct
Nov  8 14:41:08 karl-laptop kernel: [    0.004346] Initializing cgroup subsys memory
Nov  8 14:41:08 karl-laptop kernel: [    0.004368] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov  8 14:41:08 karl-laptop kernel: [    0.004370] CPU: L2 cache: 2048K
Nov  8 14:41:08 karl-laptop kernel: [    0.004391] Checking 'hlt' instruction... OK.
Nov  8 14:41:08 karl-laptop kernel: [    0.020590] SMP alternatives: switching to UP code
Nov  8 14:41:08 karl-laptop kernel: [    0.024014] Freeing SMP alternatives: 11k freed
Nov  8 14:41:08 karl-laptop kernel: [    0.024017] ACPI: Core revision 20080609
Nov  8 14:41:08 karl-laptop kernel: [    0.026131] ACPI: Checking initramfs for custom DSDT
Nov  8 14:41:08 karl-laptop kernel: [    0.343640] ENABLING IO-APIC IRQs
Nov  8 14:41:08 karl-laptop kernel: [    0.343966] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Nov  8 14:41:08 karl-laptop kernel: [    0.344021] ...trying to set up timer (IRQ0) through the 8259A ...
Nov  8 14:41:08 karl-laptop kernel: [    0.344021] ..... (found apic 0 pin 0) ...
Nov  8 14:41:08 karl-laptop kernel: [    0.387451] ....... works.
Nov  8 14:41:08 karl-laptop kernel: [    0.387452] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] Brought up 1 CPUs
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] Total of 1 processors activated (4276.24 BogoMIPS).
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] net_namespace: 840 bytes
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] Booting paravirtualized kernel on bare hardware
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] Time: 14:40:44  Date: 11/08/08
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] NET: Registered protocol family 16
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] EISA bus registered
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] ACPI: bus type pci registered
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] PCI: PCI BIOS revision 2.10 entry at 0xfd8fc, last bus=1
Nov  8 14:41:08 karl-laptop kernel: [    0.388024] PCI: Using configuration type 1 for base access
Nov  8 14:41:08 karl-laptop kernel: [    0.389773] ACPI: Interpreter enabled
Nov  8 14:41:08 karl-laptop kernel: [    0.389776] ACPI: (supports S0 S3 S4 S5)
Nov  8 14:41:08 karl-laptop kernel: [    0.389788] ACPI: Using IOAPIC for interrupt routing
Nov  8 14:41:08 karl-laptop kernel: [    0.390358] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov  8 14:41:08 karl-laptop kernel: [    0.960034] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  8 14:41:08 karl-laptop kernel: [    1.016212] ACPI: EC: GPE = 0xb, I/O: command/status = 0x66, data = 0x62
Nov  8 14:41:08 karl-laptop kernel: [    1.016215] ACPI: EC: driver started in poll mode
Nov  8 14:41:08 karl-laptop kernel: [    1.016260] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov  8 14:41:08 karl-laptop kernel: [    1.016630] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.016634] pci 0000:00:0c.0: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.016701] pci 0000:00:0c.1: PME# supported from D0 D1 D2 D3hot
Nov  8 14:41:08 karl-laptop kernel: [    1.016705] pci 0000:00:0c.1: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.016771] pci 0000:00:0c.2: PME# supported from D0 D1 D2 D3hot
Nov  8 14:41:08 karl-laptop kernel: [    1.016775] pci 0000:00:0c.2: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.016842] pci 0000:00:0c.4: PME# supported from D0 D1 D2 D3hot
Nov  8 14:41:08 karl-laptop kernel: [    1.016846] pci 0000:00:0c.4: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.016974] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.016978] pci 0000:00:10.0: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.017041] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.017045] pci 0000:00:10.1: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.017107] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.017111] pci 0000:00:10.2: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.017174] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.017178] pci 0000:00:10.3: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.017238] HPET not enabled in BIOS. You might try hpet=force boot option
Nov  8 14:41:08 karl-laptop kernel: [    1.017245] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
Nov  8 14:41:08 karl-laptop kernel: [    1.017248] pci 0000:00:11.0: quirk: region 8100-810f claimed by vt8235 SMB
Nov  8 14:41:08 karl-laptop kernel: [    1.017513] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov  8 14:41:08 karl-laptop kernel: [    1.017517] pci 0000:00:12.0: PME# disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.025593] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *3, disabled.
Nov  8 14:41:08 karl-laptop kernel: [    1.025695] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *4, disabled.
Nov  8 14:41:08 karl-laptop kernel: [    1.025793] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
Nov  8 14:41:08 karl-laptop kernel: [    1.025890] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *9, disabled.
Nov  8 14:41:08 karl-laptop kernel: [    1.026019] ACPI: PCI Interrupt Link [LNKA] (IRQs *3)
Nov  8 14:41:08 karl-laptop kernel: [    1.026145] ACPI: PCI Interrupt Link [LNKB] (IRQs *4)
Nov  8 14:41:08 karl-laptop kernel: [    1.026272] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
Nov  8 14:41:08 karl-laptop kernel: [    1.026406] ACPI: PCI Interrupt Link [LNKD] (IRQs 6) *9
Nov  8 14:41:08 karl-laptop kernel: [    1.026571] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov  8 14:41:08 karl-laptop kernel: [    1.026604] pnp: PnP ACPI init
Nov  8 14:41:08 karl-laptop kernel: [    1.026611] ACPI: bus type pnp registered
Nov  8 14:41:08 karl-laptop kernel: [    1.060060] pnp: PnP ACPI: found 9 devices
Nov  8 14:41:08 karl-laptop kernel: [    1.060063] ACPI: ACPI bus type pnp unregistered
Nov  8 14:41:08 karl-laptop kernel: [    1.060066] PnPBIOS: Disabled by ACPI PNP
Nov  8 14:41:08 karl-laptop kernel: [    1.060373] PCI: Using ACPI for IRQ routing
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NET: Registered protocol family 8
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NET: Registered protocol family 20
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NetLabel: Initializing
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NetLabel:  domain hash size = 128
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NetLabel:  protocols = UNLABELED CIPSOv4
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] NetLabel:  unlabeled traffic allowed by default
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] tracer: 772 pages allocated for 65536 entries of 48 bytes
Nov  8 14:41:08 karl-laptop kernel: [    1.060490]    actual entries 65620
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] AppArmor: AppArmor Filesystem Enabled
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0x0-0x9ffff could not be reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xffb80000-0xffbfffff has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xff380000-0xff3fffff has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xff780000-0xff7fffff has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:06: ioport range 0xfe10-0xfe11 has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:06: ioport range 0x4000-0x407f has been reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.060490] system 00:06: ioport range 0x8100-0x811f could not be reserved
Nov  8 14:41:08 karl-laptop kernel: [    1.095975] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf4000000-0xf3ffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.095979] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Nov  8 14:41:08 karl-laptop kernel: [    1.095981] pci 0000:00:01.0:   IO window: disabled
Nov  8 14:41:08 karl-laptop kernel: [    1.095985] pci 0000:00:01.0:   MEM window: 0xd1000000-0xd1ffffff
Nov  8 14:41:08 karl-laptop kernel: [    1.095989] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
Nov  8 14:41:08 karl-laptop kernel: [    1.095996] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
Nov  8 14:41:08 karl-laptop kernel: [    1.095998] pci 0000:00:0c.0:   IO window: 0x002000-0x0020ff
Nov  8 14:41:08 karl-laptop kernel: [    1.096002] pci 0000:00:0c.0:   IO window: 0x002400-0x0024ff
Nov  8 14:41:08 karl-laptop kernel: [    1.096007] pci 0000:00:0c.0:   PREFETCH window: 0x10000000-0x13ffffff
Nov  8 14:41:08 karl-laptop kernel: [    1.096011] pci 0000:00:0c.0:   MEM window: 0x14000000-0x17ffffff
Nov  8 14:41:08 karl-laptop kernel: [    1.096041] pci 0000:00:0c.0: enabling device (0000 -> 0003)
Nov  8 14:41:08 karl-laptop kernel: [    1.096047] pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 14:41:08 karl-laptop kernel: [    1.096061] bus: 00 index 0 io port: [0, ffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096063] bus: 00 index 1 mmio: [0, ffffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096065] bus: 01 index 0 mmio: [0, 0]
Nov  8 14:41:08 karl-laptop kernel: [    1.096067] bus: 01 index 1 mmio: [d1000000, d1ffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096069] bus: 01 index 2 mmio: [f0000000, f3ffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096071] bus: 01 index 3 mmio: [0, 0]
Nov  8 14:41:08 karl-laptop kernel: [    1.096073] bus: 02 index 0 io port: [2000, 20ff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096074] bus: 02 index 1 io port: [2400, 24ff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096077] bus: 02 index 2 mmio: [10000000, 13ffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096079] bus: 02 index 3 mmio: [14000000, 17ffffff]
Nov  8 14:41:08 karl-laptop kernel: [    1.096087] NET: Registered protocol family 2
Nov  8 14:41:08 karl-laptop kernel: [    1.096202] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    1.096387] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    1.096453] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    1.096513] TCP: Hash tables configured (established 8192 bind 8192)
Nov  8 14:41:08 karl-laptop kernel: [    1.096516] TCP reno registered
Nov  8 14:41:08 karl-laptop kernel: [    1.096575] NET: Registered protocol family 1
Nov  8 14:41:08 karl-laptop kernel: [    1.096690] checking if image is initramfs... it is
Nov  8 14:41:08 karl-laptop kernel: [    1.745106] Freeing initrd memory: 7990k freed
Nov  8 14:41:08 karl-laptop kernel: [    1.746020] audit: initializing netlink socket (disabled)
Nov  8 14:41:08 karl-laptop kernel: [    1.746047] type=2000 audit(1226155244.744:1): initialized
Nov  8 14:41:08 karl-laptop kernel: [    1.751878] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov  8 14:41:08 karl-laptop kernel: [    1.754133] VFS: Disk quotas dquot_6.5.1
Nov  8 14:41:08 karl-laptop kernel: [    1.754226] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov  8 14:41:08 karl-laptop kernel: [    1.754343] msgmni has been set to 367
Nov  8 14:41:08 karl-laptop kernel: [    1.754485] io scheduler noop registered
Nov  8 14:41:08 karl-laptop kernel: [    1.754488] io scheduler anticipatory registered
Nov  8 14:41:08 karl-laptop kernel: [    1.754490] io scheduler deadline registered
Nov  8 14:41:08 karl-laptop kernel: [    1.754502] io scheduler cfq registered (default)
Nov  8 14:41:08 karl-laptop kernel: [    1.754523] PCI: VIA PCI bridge detected.Disabling DAC.
Nov  8 14:41:08 karl-laptop kernel: [    1.754959] isapnp: Scanning for PnP cards...
Nov  8 14:41:08 karl-laptop kernel: [    2.108690] isapnp: No Plug & Play device found
Nov  8 14:41:08 karl-laptop kernel: [    2.141568] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Nov  8 14:41:08 karl-laptop kernel: [    2.143755] brd: module loaded
Nov  8 14:41:08 karl-laptop kernel: [    2.143831] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov  8 14:41:08 karl-laptop kernel: [    2.143956] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov  8 14:41:08 karl-laptop kernel: [    2.146417] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov  8 14:41:08 karl-laptop kernel: [    2.147764] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov  8 14:41:08 karl-laptop kernel: [    2.147772] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov  8 14:41:08 karl-laptop kernel: [    2.147774] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov  8 14:41:08 karl-laptop kernel: [    2.147777] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov  8 14:41:08 karl-laptop kernel: [    2.147779] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov  8 14:41:08 karl-laptop kernel: [    2.148320] mice: PS/2 mouse device common for all mice
Nov  8 14:41:08 karl-laptop kernel: [    2.148458] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Nov  8 14:41:08 karl-laptop kernel: [    2.148500] rtc0: alarms up to one year, y3k
Nov  8 14:41:08 karl-laptop kernel: [    2.148614] EISA: Probing bus 0 at eisa.0
Nov  8 14:41:08 karl-laptop kernel: [    2.148622] Cannot allocate resource for EISA slot 1
Nov  8 14:41:08 karl-laptop kernel: [    2.148624] Cannot allocate resource for EISA slot 2
Nov  8 14:41:08 karl-laptop kernel: [    2.148631] Cannot allocate resource for EISA slot 4
Nov  8 14:41:08 karl-laptop kernel: [    2.148648] EISA: Detected 0 cards.
Nov  8 14:41:08 karl-laptop kernel: [    2.148653] cpuidle: using governor ladder
Nov  8 14:41:08 karl-laptop kernel: [    2.148655] cpuidle: using governor menu
Nov  8 14:41:08 karl-laptop kernel: [    2.149146] TCP cubic registered
Nov  8 14:41:08 karl-laptop kernel: [    2.149186] Using IPI No-Shortcut mode
Nov  8 14:41:08 karl-laptop kernel: [    2.149369] registered taskstats version 1
Nov  8 14:41:08 karl-laptop kernel: [    2.149488]   Magic number: 0:249:687
Nov  8 14:41:08 karl-laptop kernel: [    2.149716] rtc_cmos 00:02: setting system clock to 2008-11-08 14:40:45 UTC (1226155245)
Nov  8 14:41:08 karl-laptop kernel: [    2.149720] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov  8 14:41:08 karl-laptop kernel: [    2.149722] EDD information not available.
Nov  8 14:41:08 karl-laptop kernel: [    2.150012] Freeing unused kernel memory: 424k freed
Nov  8 14:41:08 karl-laptop kernel: [    2.150060] Write protecting the kernel text: 2576k
Nov  8 14:41:08 karl-laptop kernel: [    2.150086] Write protecting the kernel read-only data: 936k
Nov  8 14:41:08 karl-laptop kernel: [    2.171804] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov  8 14:41:08 karl-laptop kernel: [    2.330959] fuse init (API version 7.9)
Nov  8 14:41:08 karl-laptop kernel: [    2.504312] ACPI: CPU0 (power states: C1[C1] C2[C2])
Nov  8 14:41:08 karl-laptop kernel: [    2.504369] processor ACPI0007:00: registered as cooling_device0
Nov  8 14:41:08 karl-laptop kernel: [    2.504373] ACPI: Processor [CPU0] (supports 16 throttling states)
Nov  8 14:41:08 karl-laptop kernel: [    2.506621] Marking TSC unstable due to TSC halts in idle
Nov  8 14:41:08 karl-laptop kernel: [    2.763325] thermal LNXTHERM:01: registered as thermal_zone0
Nov  8 14:41:08 karl-laptop kernel: [    3.016037] ACPI: Thermal Zone [THRM] (48 C)
Nov  8 14:41:08 karl-laptop kernel: [    3.512131] usbcore: registered new interface driver usbfs
Nov  8 14:41:08 karl-laptop kernel: [    3.512162] usbcore: registered new interface driver hub
Nov  8 14:41:08 karl-laptop kernel: [    3.512218] usbcore: registered new device driver usb
Nov  8 14:41:08 karl-laptop kernel: [    3.514326] USB Universal Host Controller Interface driver v3.0
Nov  8 14:41:08 karl-laptop kernel: [    3.514523] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
Nov  8 14:41:08 karl-laptop kernel: [    3.514598] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    3.514600] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    3.514612] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    3.514623] uhci_hcd 0000:00:10.0: UHCI Host Controller
Nov  8 14:41:08 karl-laptop kernel: [    3.514685] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Nov  8 14:41:08 karl-laptop kernel: [    3.514720] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001020
Nov  8 14:41:08 karl-laptop kernel: [    3.514948] usb usb1: configuration #1 chosen from 1 choice
Nov  8 14:41:08 karl-laptop kernel: [    3.514977] hub 1-0:1.0: USB hub found
Nov  8 14:41:08 karl-laptop kernel: [    3.514983] hub 1-0:1.0: 2 ports detected
Nov  8 14:41:08 karl-laptop kernel: [    3.557800] No dock devices found.
Nov  8 14:41:08 karl-laptop kernel: [    3.603017] SCSI subsystem initialized
Nov  8 14:41:08 karl-laptop kernel: [    3.687155] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Nov  8 14:41:08 karl-laptop kernel: [    3.720368] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    3.720381] uhci_hcd 0000:00:10.1: UHCI Host Controller
Nov  8 14:41:08 karl-laptop kernel: [    3.720407] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Nov  8 14:41:08 karl-laptop kernel: [    3.720433] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001040
Nov  8 14:41:08 karl-laptop kernel: [    3.720534] usb usb2: configuration #1 chosen from 1 choice
Nov  8 14:41:08 karl-laptop kernel: [    3.720561] hub 2-0:1.0: USB hub found
Nov  8 14:41:08 karl-laptop kernel: [    3.720570] hub 2-0:1.0: 2 ports detected
Nov  8 14:41:08 karl-laptop kernel: [    3.928392] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    3.928407] uhci_hcd 0000:00:10.2: UHCI Host Controller
Nov  8 14:41:08 karl-laptop kernel: [    3.928436] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Nov  8 14:41:08 karl-laptop kernel: [    3.928462] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001060
Nov  8 14:41:08 karl-laptop kernel: [    3.928573] usb usb3: configuration #1 chosen from 1 choice
Nov  8 14:41:08 karl-laptop kernel: [    3.928600] hub 3-0:1.0: USB hub found
Nov  8 14:41:08 karl-laptop kernel: [    3.928609] hub 3-0:1.0: 2 ports detected
Nov  8 14:41:08 karl-laptop kernel: [    4.136542] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
Nov  8 14:41:08 karl-laptop kernel: [    4.136565] ehci_hcd 0000:00:10.3: EHCI Host Controller
Nov  8 14:41:08 karl-laptop kernel: [    4.136590] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Nov  8 14:41:08 karl-laptop kernel: [    4.136622] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0000c00
Nov  8 14:41:08 karl-laptop kernel: [    4.148075] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov  8 14:41:08 karl-laptop kernel: [    4.148305] usb usb4: configuration #1 chosen from 1 choice
Nov  8 14:41:08 karl-laptop kernel: [    4.148335] hub 4-0:1.0: USB hub found
Nov  8 14:41:08 karl-laptop kernel: [    4.148345] hub 4-0:1.0: 6 ports detected
Nov  8 14:41:08 karl-laptop kernel: [    4.252404] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov  8 14:41:08 karl-laptop kernel: [    4.256594] eth0: VIA Rhine II at 0xd0001000, 00:90:f5:37:fa:d5, IRQ 23.
Nov  8 14:41:08 karl-laptop kernel: [    4.257302] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Nov  8 14:41:08 karl-laptop kernel: [    4.260808] pata_via 0000:00:11.1: power state changed by ACPI to D0
Nov  8 14:41:08 karl-laptop kernel: [    4.260892] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
Nov  8 14:41:08 karl-laptop kernel: [    4.260966] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
Nov  8 14:41:08 karl-laptop kernel: [    4.260969] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
Nov  8 14:41:08 karl-laptop kernel: [    4.260972] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
Nov  8 14:41:08 karl-laptop kernel: [    4.261964] scsi0 : pata_via
Nov  8 14:41:08 karl-laptop kernel: [    4.262080] scsi1 : pata_via
Nov  8 14:41:08 karl-laptop kernel: [    4.262895] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
Nov  8 14:41:08 karl-laptop kernel: [    4.262899] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
Nov  8 14:41:08 karl-laptop kernel: [    4.816516] ata1.00: ATA-7: SAMSUNG MP0402H, YQ200-06, max UDMA/100
Nov  8 14:41:08 karl-laptop kernel: [    4.816521] ata1.00: 78242976 sectors, multi 16: LBA48 
Nov  8 14:41:08 karl-laptop kernel: [    4.832356] ata1.00: configured for UDMA/100
Nov  8 14:41:08 karl-laptop kernel: [    4.996351] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TX11, max UDMA/33
Nov  8 14:41:08 karl-laptop kernel: [    5.012228] ata2.00: configured for UDMA/33
Nov  8 14:41:08 karl-laptop kernel: [    5.012375] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0402H  YQ20 PQ: 0 ANSI: 5
Nov  8 14:41:08 karl-laptop kernel: [    5.013126] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TX11 PQ: 0 ANSI: 5
Nov  8 14:41:08 karl-laptop kernel: [    5.024935] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Nov  8 14:41:08 karl-laptop kernel: [    5.024974] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Nov  8 14:41:08 karl-laptop kernel: [    5.039663] Driver 'sd' needs updating - please use bus_type methods
Nov  8 14:41:08 karl-laptop kernel: [    5.039796] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 14:41:08 karl-laptop kernel: [    5.039816] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 14:41:08 karl-laptop kernel: [    5.039848] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 14:41:08 karl-laptop kernel: [    5.039928] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
Nov  8 14:41:08 karl-laptop kernel: [    5.039944] sd 0:0:0:0: [sda] Write Protect is off
Nov  8 14:41:08 karl-laptop kernel: [    5.039977] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  8 14:41:08 karl-laptop kernel: [    5.039981]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov  8 14:41:08 karl-laptop kernel: [    5.521138]  sda1 sda2 sda3 < sda5 sda6 sda7 >
Nov  8 14:41:08 karl-laptop kernel: [    5.572907] sd 0:0:0:0: [sda] Attached SCSI disk
Nov  8 14:41:08 karl-laptop kernel: [    5.582477] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
Nov  8 14:41:08 karl-laptop kernel: [    5.582483] Uniform CD-ROM driver Revision: 3.20
Nov  8 14:41:08 karl-laptop kernel: [    6.126145] PM: Starting manual resume from disk
Nov  8 14:41:08 karl-laptop kernel: [    6.168210] kjournald starting.  Commit interval 5 seconds
Nov  8 14:41:08 karl-laptop kernel: [    6.168224] EXT3-fs: mounted filesystem with ordered data mode.
Nov  8 14:41:08 karl-laptop kernel: [   14.371660] udevd version 124 started
Nov  8 14:41:08 karl-laptop kernel: [   14.839241] Linux agpgart interface v0.103
Nov  8 14:41:08 karl-laptop kernel: [   14.889760] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
Nov  8 14:41:08 karl-laptop kernel: [   14.901496] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Nov  8 14:41:08 karl-laptop kernel: [   15.140407] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Nov  8 14:41:08 karl-laptop kernel: [   15.156031] ACPI: Power Button (FF) [PWRF]
Nov  8 14:41:08 karl-laptop kernel: [   15.156161] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Nov  8 14:41:08 karl-laptop kernel: [   15.172017] ACPI: Power Button (CM) [PWRB]
Nov  8 14:41:08 karl-laptop kernel: [   15.172110] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Nov  8 14:41:08 karl-laptop kernel: [   15.184019] ACPI: Sleep Button (CM) [SLPB]
Nov  8 14:41:08 karl-laptop kernel: [   15.184095] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
Nov  8 14:41:08 karl-laptop kernel: [   15.184320] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov  8 14:41:08 karl-laptop kernel: [   15.216073] ACPI: Lid Switch [LID]
Nov  8 14:41:08 karl-laptop kernel: [   15.237892] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov  8 14:41:08 karl-laptop kernel: [   15.320161] ACPI: AC Adapter [AC] (on-line)
Nov  8 14:41:08 karl-laptop kernel: [   15.701632] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:5402]
Nov  8 14:41:08 karl-laptop kernel: [   15.701650] Yenta: Enabling burst memory read transactions
Nov  8 14:41:08 karl-laptop kernel: [   15.701654] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov  8 14:41:08 karl-laptop kernel: [   15.701656] Yenta: Routing CardBus interrupts to PCI
Nov  8 14:41:08 karl-laptop kernel: [   15.701661] Yenta TI: socket 0000:00:0c.0, mfunc 0x00001202, devctl 0x44
Nov  8 14:41:08 karl-laptop kernel: [   15.755852] sdhci: Secure Digital Host Controller Interface driver
Nov  8 14:41:08 karl-laptop kernel: [   15.755856] sdhci: Copyright(c) Pierre Ossman
Nov  8 14:41:08 karl-laptop kernel: [   15.932878] Yenta: ISA IRQ mask 0x0800, PCI irq 16
Nov  8 14:41:08 karl-laptop kernel: [   15.932882] Socket status: 30000006
Nov  8 14:41:08 karl-laptop kernel: [   15.975887] sdhci-pci 0000:00:0c.2: SDHCI controller found [1524:0550] (rev 1)
Nov  8 14:41:08 karl-laptop kernel: [   15.975900] sdhci-pci 0000:00:0c.2: enabling device (0000 -> 0002)
Nov  8 14:41:08 karl-laptop kernel: [   15.975917] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 14:41:08 karl-laptop kernel: [   15.976022] mmc0: SDHCI controller on PCI [0000:00:0c.2] using PIO
Nov  8 14:41:08 karl-laptop kernel: [   15.976049] sdhci-pci 0000:00:0c.4: SDHCI controller found [1524:0551] (rev 1)
Nov  8 14:41:08 karl-laptop kernel: [   15.976058] sdhci-pci 0000:00:0c.4: enabling device (0000 -> 0002)
Nov  8 14:41:08 karl-laptop kernel: [   15.976066] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov  8 14:41:08 karl-laptop kernel: [   15.976096] mmc1: SDHCI controller on PCI [0000:00:0c.4] using PIO
Nov  8 14:41:08 karl-laptop kernel: [   16.516128] ACPI: Battery Slot [BAT0] (battery present)
Nov  8 14:41:08 karl-laptop kernel: [   16.516525] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/input/input6
Nov  8 14:41:08 karl-laptop kernel: [   16.528020] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov  8 14:41:08 karl-laptop kernel: [   16.919536] NET: Registered protocol family 23
Nov  8 14:41:08 karl-laptop kernel: [   17.005493] input: PC Speaker as /devices/platform/pcspkr/input/input7
Nov  8 14:41:08 karl-laptop kernel: [   17.224028] rt61pci 0000:00:0d.0: enabling device (0010 -> 0012)
Nov  8 14:41:08 karl-laptop kernel: [   17.224042] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 14:41:08 karl-laptop kernel: [   17.684232] Registered led device: rt61pci-phy0:radio
Nov  8 14:41:08 karl-laptop kernel: [   17.684250] Registered led device: rt61pci-phy0:assoc
Nov  8 14:41:08 karl-laptop kernel: [   18.209735] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
Nov  8 14:41:08 karl-laptop kernel: [   18.701243] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
Nov  8 14:41:08 karl-laptop kernel: [   18.701253] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
Nov  8 14:41:08 karl-laptop kernel: [   18.701325] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
Nov  8 14:41:08 karl-laptop kernel: [   18.701395] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Nov  8 14:41:08 karl-laptop kernel: [   18.701398] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Nov  8 14:41:08 karl-laptop kernel: [   18.701408] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 14:41:08 karl-laptop kernel: [   19.312078] MC'97 1 converters and GPIO not ready (0xff00)
Nov  8 14:41:08 karl-laptop kernel: [   19.313884] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
Nov  8 14:41:08 karl-laptop kernel: [   19.313899] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
Nov  8 14:41:08 karl-laptop kernel: [   19.396672] cs: IO port probe 0x100-0x3af: clean.
Nov  8 14:41:08 karl-laptop kernel: [   19.398610] cs: IO port probe 0x3e0-0x4ff: clean.
Nov  8 14:41:08 karl-laptop kernel: [   19.399420] cs: IO port probe 0x820-0x8ff: clean.
Nov  8 14:41:08 karl-laptop kernel: [   19.400122] cs: IO port probe 0xc00-0xcf7: clean.
Nov  8 14:41:08 karl-laptop kernel: [   19.400951] cs: IO port probe 0xa00-0xaff: clean.
Nov  8 14:41:08 karl-laptop kernel: [   20.357595] lp: driver loaded but no devices found
Nov  8 14:41:08 karl-laptop kernel: [   20.419855] [drm] Initialized drm 1.1.0 20060810
Nov  8 14:41:08 karl-laptop kernel: [   20.454961] pci 0000:01:00.0: power state changed by ACPI to D0
Nov  8 14:41:08 karl-laptop kernel: [   20.454979] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  8 14:41:08 karl-laptop kernel: [   20.455850] [drm] Initialized via 2.11.1 20070202 on minor 0
Nov  8 14:41:08 karl-laptop kernel: [   20.580881] Adding 554200k swap on /dev/sda5.  Priority:-1 extents:1 across:554200k
Nov  8 14:41:08 karl-laptop kernel: [   20.663213] Adding 554168k swap on /dev/sda6.  Priority:-2 extents:1 across:554168k
Nov  8 14:41:08 karl-laptop kernel: [   20.720434] Adding 425648k swap on /dev/sda7.  Priority:-3 extents:1 across:425648k
Nov  8 14:41:08 karl-laptop kernel: [   21.278544] EXT3 FS on sda2, internal journal
Nov  8 14:41:08 karl-laptop kernel: [   22.297593] type=1505 audit(1226171466.096:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4227
Nov  8 14:41:08 karl-laptop kernel: [   22.476257] type=1505 audit(1226171466.276:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4232
Nov  8 14:41:08 karl-laptop kernel: [   22.476626] type=1505 audit(1226171466.276:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4232
Nov  8 14:41:08 karl-laptop kernel: [   22.597331] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov  8 14:41:08 karl-laptop kernel: [   23.248349] Clocksource tsc unstable (delta = 4687137221 ns)
Nov  8 14:41:08 karl-laptop kernel: [   23.897914] ACPI: WMI: Mapper loaded
Nov  8 14:41:08 karl-laptop kernel: [   24.762124] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Nov  8 14:41:08 karl-laptop kernel: [   24.834947] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov  8 14:41:08 karl-laptop kernel: [   24.834955] apm: overridden by ACPI.
Nov  8 14:41:08 karl-laptop kernel: [   25.027249] ppdev: user-space parallel port driver
Nov  8 14:41:10 karl-laptop kernel: [   26.790564] Bluetooth: Core ver 2.13
Nov  8 14:41:10 karl-laptop kernel: [   26.793478] NET: Registered protocol family 31
Nov  8 14:41:10 karl-laptop kernel: [   26.793494] Bluetooth: HCI device and connection manager initialized
Nov  8 14:41:10 karl-laptop kernel: [   26.793504] Bluetooth: HCI socket layer initialized
Nov  8 14:41:10 karl-laptop kernel: [   26.865032] Bluetooth: L2CAP ver 2.11
Nov  8 14:41:10 karl-laptop kernel: [   26.865051] Bluetooth: L2CAP socket layer initialized
Nov  8 14:41:10 karl-laptop kernel: [   26.931431] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov  8 14:41:10 karl-laptop kernel: [   26.931449] Bluetooth: BNEP filters: protocol multicast
Nov  8 14:41:10 karl-laptop kernel: [   26.956009] Bluetooth: RFCOMM socket layer initialized
Nov  8 14:41:10 karl-laptop kernel: [   26.956295] Bluetooth: RFCOMM TTY layer initialized
Nov  8 14:41:10 karl-laptop kernel: [   26.956312] Bluetooth: RFCOMM ver 1.10
Nov  8 14:41:10 karl-laptop kernel: [   27.056442] Bridge firewalling registered
Nov  8 14:41:10 karl-laptop kernel: [   27.067981] Bluetooth: SCO (Voice Link) ver 0.6
Nov  8 14:41:10 karl-laptop kernel: [   27.067988] Bluetooth: SCO socket layer initialized
Nov  8 14:41:13 karl-laptop kernel: [   29.724024] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Nov  8 14:41:13 karl-laptop kernel: [   29.724054] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Nov  8 14:41:13 karl-laptop kernel: [   29.724061] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
Nov  8 14:41:13 karl-laptop kernel: [   29.724140] pci 0000:01:00.0: putting AGP V2 device into 0x mode
Nov  8 14:41:15 karl-laptop kernel: [   31.228991] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  8 14:41:15 karl-laptop kernel: [   31.236202] firmware: requesting rt2561.bin
Nov  8 14:41:15 karl-laptop kernel: [   31.682451] NET: Registered protocol family 17
Nov  8 14:41:34 karl-laptop pulseaudio[5569]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  8 14:41:34 karl-laptop pulseaudio[5571]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  8 14:41:34 karl-laptop pulseaudio[5571]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  8 14:41:34 karl-laptop pulseaudio[5571]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  8 14:44:02 karl-laptop kernel: [  192.589733] NET: Registered protocol family 10
Nov  8 14:44:02 karl-laptop kernel: [  192.591451] lo: Disabled Privacy Extensions
Nov  8 14:44:02 karl-laptop kernel: [  192.593745] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  8 14:44:08 karl-laptop kernel: [  199.859405] type=1503 audit(1226171648.735:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5818/net/" pid=5818 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.254600] type=1503 audit(1226171650.131:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5822/net/" pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.259117] type=1503 audit(1226171650.135:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.262121] type=1503 audit(1226171650.139:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265249] type=1503 audit(1226171650.143:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265280] type=1503 audit(1226171650.143:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265302] type=1503 audit(1226171650.143:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265324] type=1503 audit(1226171650.143:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265345] type=1503 audit(1226171650.143:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 14:44:10 karl-laptop kernel: [  201.265366] type=1503 audit(1226171650.143:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5822 profile="/usr/sbin/cupsd"
Nov  8 15:01:13 karl-laptop -- MARK --
Nov  8 15:18:04 karl-laptop kernel: [ 2235.497658] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by cmnorton on 2008-11-08
I would attach yourself (comment) to an existing bug that sounds like your problem, or issue a new bug at Ubuntu launchpad. I have mostly used laptops with Ubuntu. I have never gotten suspend to work well. Interestingly, it worked fine on an old Acer desktop of mine.

---

### Post by Monohielo on 2008-11-17
I have the same problem with an Nvidia CK804 Network card on my desktop.  This is a wired connection with DHCP enabled.  When I resume from Sleep, the network manager tries to pull an address, but fails.  Manually shutting down the connection with ifconfig eth0 down/up doesn't help.  

If there are some logs that I can post that may help, let me know and I will paste them when I get home.

---

### Post by karlmp on 2008-11-27
dmesg:

```
karl@karlzt:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
[    0.000000]  BIOS-e820: 000000000bef0000 - 000000000befa000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000befa000 - 000000000bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to bef0000 @ 7000-d000
[    0.000000] RAMDISK: 0b712000 - 0bedf89e
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7C80, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0BEF6B92, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0BEF9E0D, 0074 (r1 PN800  PTLTW     6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 0BEF6BC2, 324B (r1  VIA   PTL_ACPI  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 0BEFAFC0, 0040
[    0.000000] ACPI: APIC 0BEF9E81, 0046 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 0BEF9EC7, 0139 (r1 PTLTD    CpuGv3  6040000  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 190MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bef0000
[    0.000000]   low ram: 00000000 - 0bef0000
[    0.000000]   bootmap 00002000 - 000037e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [000b712000 - 000bedf89e]          RAMDISK ==> [000b712000 - 000bedf89e]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000004000]          BOOTMAP ==> [0000002000 - 0000004000]
[    0.000000] found SMP MP-table at [c00f7cb0] 000f7cb0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bef0
[    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000bef0
[    0.000000] On node 0 totalpages: 48783
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 44390 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3f80000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48353
[    0.000000] Kernel command line: root=UUID=db1f2eaa-85bc-4f21-9116-8e523b73d0d1 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2138.100 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] Memory: 180092k/195520k available (2572k kernel code, 14888k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xcc800000 - 0xff3fe000   ( 811 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 4276.20 BogoMIPS (lpj=8552400)
[    0.004043] Security Framework initialized
[    0.004059] SELinux:  Disabled at boot.
[    0.004091] AppArmor: AppArmor initialized
[    0.004103] Mount-cache hash table entries: 512
[    0.004334] Initializing cgroup subsys ns
[    0.004343] Initializing cgroup subsys cpuacct
[    0.004345] Initializing cgroup subsys memory
[    0.004368] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004370] CPU: L2 cache: 2048K
[    0.004392] Checking 'hlt' instruction... OK.
[    0.020592] SMP alternatives: switching to UP code
[    0.024015] Freeing SMP alternatives: 11k freed
[    0.024018] ACPI: Core revision 20080609
[    0.026153] ACPI: Checking initramfs for custom DSDT
[    0.344172] ENABLING IO-APIC IRQs
[    0.344497] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.348021] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.348021] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.348021] ..... (found apic 0 pin 0) ...
[    0.387983] ....... works.
[    0.387984] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[    0.388024] Brought up 1 CPUs
[    0.388024] Total of 1 processors activated (4276.20 BogoMIPS).
[    0.388024] CPU0 attaching sched-domain:
[    0.388024]  domain 0: span 0 level CPU
[    0.388024]   groups: 0
[    0.388024] net_namespace: 840 bytes
[    0.388024] Booting paravirtualized kernel on bare hardware
[    0.388024] Time: 10:00:13  Date: 11/27/08
[    0.388024] NET: Registered protocol family 16
[    0.388024] EISA bus registered
[    0.388024] ACPI: bus type pci registered
[    0.388024] PCI: PCI BIOS revision 2.10 entry at 0xfd8fc, last bus=1
[    0.388024] PCI: Using configuration type 1 for base access
[    0.388024] ACPI: EC: Look up EC in DSDT
[    0.389769] ACPI: Interpreter enabled
[    0.389772] ACPI: (supports S0 S3 S4 S5)
[    0.389784] ACPI: Using IOAPIC for interrupt routing
[    0.390355] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.904034] ACPI: EC: missing confirmations, switch off interrupt mode.
[    1.016212] ACPI: EC: GPE = 0xb, I/O: command/status = 0x66, data = 0x62
[    1.016215] ACPI: EC: driver started in poll mode
[    1.016260] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.016333] PCI: 0000:00:00.0 reg 10 32bit mmio: [d8000000, dfffffff]
[    1.016577] pci 0000:00:01.0: supports D1
[    1.016613] PCI: 0000:00:0c.0 reg 10 32bit mmio: [0, fff]
[    1.016626] pci 0000:00:0c.0: supports D1
[    1.016627] pci 0000:00:0c.0: supports D2
[    1.016629] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.016634] pci 0000:00:0c.0: PME# disabled
[    1.016659] PCI: 0000:00:0c.1 reg 10 32bit mmio: [d0000000, d000007f]
[    1.016697] pci 0000:00:0c.1: supports D1
[    1.016698] pci 0000:00:0c.1: supports D2
[    1.016701] pci 0000:00:0c.1: PME# supported from D0 D1 D2 D3hot
[    1.016705] pci 0000:00:0c.1: PME# disabled
[    1.016729] PCI: 0000:00:0c.2 reg 10 32bit mmio: [d0000400, d00004ff]
[    1.016767] pci 0000:00:0c.2: supports D1
[    1.016768] pci 0000:00:0c.2: supports D2
[    1.016770] pci 0000:00:0c.2: PME# supported from D0 D1 D2 D3hot
[    1.016774] pci 0000:00:0c.2: PME# disabled
[    1.016801] PCI: 0000:00:0c.4 reg 10 32bit mmio: [0, ff]
[    1.016839] pci 0000:00:0c.4: supports D1
[    1.016840] pci 0000:00:0c.4: supports D2
[    1.016842] pci 0000:00:0c.4: PME# supported from D0 D1 D2 D3hot
[    1.016846] pci 0000:00:0c.4: PME# disabled
[    1.016873] PCI: 0000:00:0d.0 reg 10 32bit mmio: [d0008000, d000ffff]
[    1.016950] PCI: 0000:00:10.0 reg 20 io port: [1020, 103f]
[    1.016970] pci 0000:00:10.0: supports D1
[    1.016972] pci 0000:00:10.0: supports D2
[    1.016974] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.016978] pci 0000:00:10.0: PME# disabled
[    1.017017] PCI: 0000:00:10.1 reg 20 io port: [1040, 105f]
[    1.017037] pci 0000:00:10.1: supports D1
[    1.017039] pci 0000:00:10.1: supports D2
[    1.017040] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.017044] pci 0000:00:10.1: PME# disabled
[    1.017084] PCI: 0000:00:10.2 reg 20 io port: [1060, 107f]
[    1.017104] pci 0000:00:10.2: supports D1
[    1.017105] pci 0000:00:10.2: supports D2
[    1.017107] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.017111] pci 0000:00:10.2: PME# disabled
[    1.017135] PCI: 0000:00:10.3 reg 10 32bit mmio: [d0000c00, d0000cff]
[    1.017171] pci 0000:00:10.3: supports D1
[    1.017172] pci 0000:00:10.3: supports D2
[    1.017174] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    1.017178] pci 0000:00:10.3: PME# disabled
[    1.017238] HPET not enabled in BIOS. You might try hpet=force boot option
[    1.017245] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    1.017249] pci 0000:00:11.0: quirk: region 8100-810f claimed by vt8235 SMB
[    1.017295] PCI: 0000:00:11.1 reg 20 io port: [1000, 100f]
[    1.017344] PCI: 0000:00:11.5 reg 10 io port: [1400, 14ff]
[    1.017382] pci 0000:00:11.5: supports D1
[    1.017384] pci 0000:00:11.5: supports D2
[    1.017408] PCI: 0000:00:11.6 reg 10 io port: [1800, 18ff]
[    1.017470] PCI: 0000:00:12.0 reg 10 io port: [1c00, 1cff]
[    1.017476] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0001000, d00010ff]
[    1.017509] pci 0000:00:12.0: supports D1
[    1.017511] pci 0000:00:12.0: supports D2
[    1.017513] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.017517] pci 0000:00:12.0: PME# disabled
[    1.017559] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f3ffffff]
[    1.017565] PCI: 0000:01:00.0 reg 14 32bit mmio: [d1000000, d1ffffff]
[    1.017583] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    1.017595] pci 0000:01:00.0: supports D1
[    1.017596] pci 0000:01:00.0: supports D2
[    1.017628] PCI: bridge 0000:00:01.0 32bit mmio: [d1000000, d1ffffff]
[    1.017632] PCI: bridge 0000:00:01.0 32bit mmio pref: [f0000000, f3ffffff]
[    1.017653] bus 00 -> node 0
[    1.017659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.025595] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *3, disabled.
[    1.025695] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *4, disabled.
[    1.025795] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[    1.025891] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *9, disabled.
[    1.026021] ACPI: PCI Interrupt Link [LNKA] (IRQs *3)
[    1.026149] ACPI: PCI Interrupt Link [LNKB] (IRQs *4)
[    1.026276] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    1.026411] ACPI: PCI Interrupt Link [LNKD] (IRQs 6) *9
[    1.026576] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.026609] pnp: PnP ACPI init
[    1.026616] ACPI: bus type pnp registered
[    1.060060] pnp: PnP ACPI: found 9 devices
[    1.060063] ACPI: ACPI bus type pnp unregistered
[    1.060066] PnPBIOS: Disabled by ACPI PNP
[    1.060373] PCI: Using ACPI for IRQ routing
[    1.060489] NET: Registered protocol family 8
[    1.060489] NET: Registered protocol family 20
[    1.060489] NetLabel: Initializing
[    1.060489] NetLabel:  domain hash size = 128
[    1.060489] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.060489] NetLabel:  unlabeled traffic allowed by default
[    1.060489] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.060489]    actual entries 65620
[    1.060489] AppArmor: AppArmor Filesystem Enabled
[    1.060489] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    1.060489] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    1.060489] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.060489] system 00:05: iomem range 0xffb80000-0xffbfffff has been reserved
[    1.060489] system 00:05: iomem range 0xff380000-0xff3fffff has been reserved
[    1.060489] system 00:05: iomem range 0xff780000-0xff7fffff has been reserved
[    1.060489] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved
[    1.060489] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved
[    1.060489] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    1.060489] system 00:06: ioport range 0xfe10-0xfe11 has been reserved
[    1.060489] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    1.060489] system 00:06: ioport range 0x4000-0x407f has been reserved
[    1.060489] system 00:06: ioport range 0x8100-0x811f could not be reserved
[    1.095975] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf4000000-0xf3ffffff]
[    1.095978] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.095980] pci 0000:00:01.0:   IO window: disabled
[    1.095985] pci 0000:00:01.0:   MEM window: 0xd1000000-0xd1ffffff
[    1.095989] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    1.095995] pci 0000:00:0c.0: CardBus bridge, secondary bus 0000:02
[    1.095998] pci 0000:00:0c.0:   IO window: 0x002000-0x0020ff
[    1.096002] pci 0000:00:0c.0:   IO window: 0x002400-0x0024ff
[    1.096006] pci 0000:00:0c.0:   PREFETCH window: 0x10000000-0x13ffffff
[    1.096010] pci 0000:00:0c.0:   MEM window: 0x14000000-0x17ffffff
[    1.096025] pci 0000:00:01.0: setting latency timer to 64
[    1.096041] pci 0000:00:0c.0: enabling device (0000 -> 0003)
[    1.096047] pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.096057] pci 0000:00:0c.0: setting latency timer to 64
[    1.096061] bus: 00 index 0 io port: [0, ffff]
[    1.096063] bus: 00 index 1 mmio: [0, ffffffff]
[    1.096065] bus: 01 index 0 mmio: [0, 0]
[    1.096067] bus: 01 index 1 mmio: [d1000000, d1ffffff]
[    1.096069] bus: 01 index 2 mmio: [f0000000, f3ffffff]
[    1.096071] bus: 01 index 3 mmio: [0, 0]
[    1.096073] bus: 02 index 0 io port: [2000, 20ff]
[    1.096075] bus: 02 index 1 io port: [2400, 24ff]
[    1.096077] bus: 02 index 2 mmio: [10000000, 13ffffff]
[    1.096079] bus: 02 index 3 mmio: [14000000, 17ffffff]
[    1.096089] NET: Registered protocol family 2
[    1.096205] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    1.096393] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    1.096458] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    1.096517] TCP: Hash tables configured (established 8192 bind 8192)
[    1.096521] TCP reno registered
[    1.096580] NET: Registered protocol family 1
[    1.096693] checking if image is initramfs... it is
[    1.596088] Switched to high resolution mode on CPU 0
[    1.746455] Freeing initrd memory: 7990k freed
[    1.747357] audit: initializing netlink socket (disabled)
[    1.747384] type=2000 audit(1227780014.744:1): initialized
[    1.753235] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.755481] VFS: Disk quotas dquot_6.5.1
[    1.755569] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.755681] msgmni has been set to 367
[    1.755823] io scheduler noop registered
[    1.755827] io scheduler anticipatory registered
[    1.755829] io scheduler deadline registered
[    1.755840] io scheduler cfq registered (default)
[    1.755861] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.755941] pci 0000:01:00.0: Boot video device
[    1.756327] isapnp: Scanning for PnP cards...
[    2.110050] isapnp: No Plug & Play device found
[    2.142922] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.145129] brd: module loaded
[    2.145207] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.145341] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.147797] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.148900] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.148908] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.148910] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.148913] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.148915] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.149501] mice: PS/2 mouse device common for all mice
[    2.149640] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.149682] rtc0: alarms up to one year, y3k
[    2.149795] EISA: Probing bus 0 at eisa.0
[    2.149804] Cannot allocate resource for EISA slot 1
[    2.149806] Cannot allocate resource for EISA slot 2
[    2.149812] Cannot allocate resource for EISA slot 4
[    2.149829] EISA: Detected 0 cards.
[    2.149834] cpuidle: using governor ladder
[    2.149836] cpuidle: using governor menu
[    2.150330] TCP cubic registered
[    2.150372] Using IPI No-Shortcut mode
[    2.150566] registered taskstats version 1
[    2.150686]   Magic number: 0:82:23
[    2.150914] rtc_cmos 00:02: setting system clock to 2008-11-27 10:00:15 UTC (1227780015)
[    2.150918] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.150920] EDD information not available.
[    2.151211] Freeing unused kernel memory: 424k freed
[    2.151257] Write protecting the kernel text: 2576k
[    2.151284] Write protecting the kernel read-only data: 936k
[    2.173109] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.325464] fuse init (API version 7.9)
[    2.510750] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.510806] processor ACPI0007:00: registered as cooling_device0
[    2.510810] ACPI: Processor [CPU0] (supports 16 throttling states)
[    2.513078] Marking TSC unstable due to TSC halts in idle
[    2.770203] thermal LNXTHERM:01: registered as thermal_zone0
[    3.024038] ACPI: Thermal Zone [THRM] (25 C)
[    3.554982] usbcore: registered new interface driver usbfs
[    3.555012] usbcore: registered new interface driver hub
[    3.555067] usbcore: registered new device driver usb
[    3.567828] No dock devices found.
[    3.570792] USB Universal Host Controller Interface driver v3.0
[    3.570973] ACPI: PCI Interrupt Link [ALKD] disabled and referenced, BIOS bug
[    3.571047] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 21
[    3.571050] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 21
[    3.571061] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.571072] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.571128] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.571166] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001020
[    3.571406] usb usb1: configuration #1 chosen from 1 choice
[    3.571435] hub 1-0:1.0: USB hub found
[    3.571441] hub 1-0:1.0: 2 ports detected
[    3.604467] SCSI subsystem initialized
[    3.682620] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.692057] libata version 3.00 loaded.
[    3.776380] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.776393] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.776418] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.776444] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001040
[    3.776540] usb usb2: configuration #1 chosen from 1 choice
[    3.776568] hub 2-0:1.0: USB hub found
[    3.776575] hub 2-0:1.0: 2 ports detected
[    3.984387] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    3.984401] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.984427] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.984454] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001060
[    3.984558] usb usb3: configuration #1 chosen from 1 choice
[    3.984586] hub 3-0:1.0: USB hub found
[    3.984593] hub 3-0:1.0: 2 ports detected
[    4.192473] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    4.192494] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    4.192517] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    4.192546] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0000c00
[    4.204068] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.204294] usb usb4: configuration #1 chosen from 1 choice
[    4.204322] hub 4-0:1.0: USB hub found
[    4.204332] hub 4-0:1.0: 6 ports detected
[    4.308389] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.312576] eth0: VIA Rhine II at 0xd0001000, 00:90:f5:37:fa:d5, IRQ 23.
[    4.313283] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[    4.316298] pata_acpi 0000:00:11.1: power state changed by ACPI to D0
[    4.316382] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    4.316455] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 23
[    4.316458] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 23
[    4.316461] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
[    4.316507] pata_acpi 0000:00:11.1: PCI INT A disabled
[    4.319583] pata_via 0000:00:11.1: version 0.3.3
[    4.319623] pata_via 0000:00:11.1: power state changed by ACPI to D0
[    4.319630] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
[    4.320639] scsi0 : pata_via
[    4.320762] scsi1 : pata_via
[    4.321578] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1000 irq 14
[    4.321581] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1008 irq 15
[    4.764516] ata1.00: ATA-7: SAMSUNG MP0402H, YQ200-06, max UDMA/100
[    4.764520] ata1.00: 78242976 sectors, multi 16: LBA48 
[    4.780356] ata1.00: configured for UDMA/100
[    4.944351] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TX11, max UDMA/33
[    4.960226] ata2.00: configured for UDMA/33
[    4.960370] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MP0402H  YQ20 PQ: 0 ANSI: 5
[    4.961118] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TX11 PQ: 0 ANSI: 5
[    4.966808] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.966844] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.980730] Driver 'sd' needs updating - please use bus_type methods
[    4.980862] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[    4.980885] sd 0:0:0:0: [sda] Write Protect is off
[    4.980887] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.980923] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.981006] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[    4.981026] sd 0:0:0:0: [sda] Write Protect is off
[    4.981028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.981064] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.981068]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.452262]  sda1 sda3 < sda5 sda6 sda7 >
[    5.494060] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.503591] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.503596] Uniform CD-ROM driver Revision: 3.20
[    5.503691] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.020061] PM: Starting manual resume from disk
[    6.020065] PM: Resume from partition 8:5
[    6.020067] PM: Checking hibernation image.
[    6.020262] PM: Resume from disk failed.
[    6.062130] kjournald starting.  Commit interval 5 seconds
[    6.062145] EXT3-fs: mounted filesystem with ordered data mode.
[   13.579948] udevd version 124 started
[   14.055188] Linux agpgart interface v0.103
[   14.115010] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[   14.122856] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   14.248124] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.321950] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.433658] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   14.444032] ACPI: Power Button (FF) [PWRF]
[   14.444137] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   14.460024] ACPI: Power Button (CM) [PWRB]
[   14.460141] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   14.476023] ACPI: Sleep Button (CM) [SLPB]
[   14.476179] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   14.508071] ACPI: Lid Switch [LID]
[   14.540183] ACPI: AC Adapter [AC] (on-line)
[   14.547509] Yenta: CardBus bridge found at 0000:00:0c.0 [1558:5402]
[   14.547527] Yenta: Enabling burst memory read transactions
[   14.547532] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.547533] Yenta: Routing CardBus interrupts to PCI
[   14.547538] Yenta TI: socket 0000:00:0c.0, mfunc 0x00001202, devctl 0x44
[   14.776885] Yenta: ISA IRQ mask 0x0800, PCI irq 16
[   14.776889] Socket status: 30000006
[   14.809301] sdhci: Secure Digital Host Controller Interface driver
[   14.809305] sdhci: Copyright(c) Pierre Ossman
[   14.887320] sdhci-pci 0000:00:0c.2: SDHCI controller found [1524:0550] (rev 1)
[   14.887335] sdhci-pci 0000:00:0c.2: enabling device (0000 -> 0002)
[   14.887353] sdhci-pci 0000:00:0c.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.887454] mmc0: SDHCI controller on PCI [0000:00:0c.2] using PIO
[   14.887463] sdhci-pci 0000:00:0c.4: SDHCI controller found [1524:0551] (rev 1)
[   14.887472] sdhci-pci 0000:00:0c.4: enabling device (0000 -> 0002)
[   14.887481] sdhci-pci 0000:00:0c.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.890546] mmc1: SDHCI controller on PCI [0000:00:0c.4] using PIO
[   15.418641] rt61pci 0000:00:0d.0: enabling device (0010 -> 0012)
[   15.418655] rt61pci 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.459215] phy0: Selected rate control algorithm 'pid'
[   15.776138] ACPI: Battery Slot [BAT0] (battery present)
[   15.776840] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/device:12/input/input6
[   15.792404] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.924076] Registered led device: rt61pci-phy0:radio
[   15.924098] Registered led device: rt61pci-phy0:assoc
[   16.145121] irda_init()
[   16.145138] NET: Registered protocol family 23
[   16.906045] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.919249] VIA 82xx Modem 0000:00:11.6: power state changed by ACPI to D0
[   16.919258] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   16.919329] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   16.919400] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   16.919402] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   16.919413] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   16.920022] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   17.528125] MC'97 1 converters and GPIO not ready (0xff00)
[   17.529151] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   17.529166] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   17.529304] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   17.532663] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
[   18.272352] cs: IO port probe 0x100-0x3af: clean.
[   18.274291] cs: IO port probe 0x3e0-0x4ff: clean.
[   18.275101] cs: IO port probe 0x820-0x8ff: clean.
[   18.275772] cs: IO port probe 0xc00-0xcf7: clean.
[   18.276628] cs: IO port probe 0xa00-0xaff: clean.
[   18.848092] lp: driver loaded but no devices found
[   19.023265] Adding 554200k swap on /dev/sda5.  Priority:-1 extents:1 across:554200k
[   19.027088] Adding 554168k swap on /dev/sda6.  Priority:-2 extents:1 across:554168k
[   19.685630] EXT3 FS on sda7, internal journal
[   20.748399] type=1505 audit(1227796234.262:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4206
[   20.930984] type=1505 audit(1227796234.442:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4211
[   20.931344] type=1505 audit(1227796234.442:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4211
[   21.068893] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.772153] Clocksource tsc unstable (delta = 4687187920 ns)
[   22.765045] ACPI: WMI: Mapper loaded
[   23.577378] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.659198] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   23.659205] apm: overridden by ACPI.
[   23.826027] ppdev: user-space parallel port driver
[   25.839462] Bluetooth: Core ver 2.13
[   25.842122] NET: Registered protocol family 31
[   25.842137] Bluetooth: HCI device and connection manager initialized
[   25.842146] Bluetooth: HCI socket layer initialized
[   25.913916] Bluetooth: L2CAP ver 2.11
[   25.913935] Bluetooth: L2CAP socket layer initialized
[   25.966897] Bluetooth: SCO (Voice Link) ver 0.6
[   25.966904] Bluetooth: SCO socket layer initialized
[   25.994466] Bluetooth: RFCOMM socket layer initialized
[   25.994767] Bluetooth: RFCOMM TTY layer initialized
[   25.994772] Bluetooth: RFCOMM ver 1.10
[   25.995523] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.995528] Bluetooth: BNEP filters: protocol multicast
[   26.033433] Bridge firewalling registered
[   26.034174] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.859522] [drm] Initialized drm 1.1.0 20060810
[   28.900871] pci 0000:01:00.0: power state changed by ACPI to D0
[   28.900913] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.906960] [drm] Initialized via 2.11.1 20070202 on minor 0
[   28.960009] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   28.960009] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   28.960009] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   28.960009] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   30.109911] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   30.112696] firmware: requesting rt2561.bin
[   30.339232] NET: Registered protocol family 17
[   42.644005] NET: Registered protocol family 10
[   42.647750] lo: Disabled Privacy Extensions
[   42.651683] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.044026] eth0: no IPv6 routers present
[ 3465.049239] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[ 3465.049281] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[ 3465.049287] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[ 3465.049367] pci 0000:01:00.0: putting AGP V2 device into 0x mode
karl@karlzt:~$ 


```

---

### Post by nukeqler on 2008-11-27
Same problem here, IBM T41 laptop with atheros wifi card.  The interfaces all show up with ifconfig, but the Wired and Wireless options on the Network Manager are greyed out.

This always worked correctly for me in Hardy, only changed when I upgraded to Intrepid.

Thanks in advance to whoever comes up with the solution.  Aside from this and the DRI problem with X, Intrepid seems pretty great.

---

### Post by linux4me on 2008-11-27
I was having the same problem on a new Intrepid upgrade using a wired connection with an nVidia MCP61 onboard ethernet chip.

I can't claim credit for the solution, as I found it in [this post]("http://ubuntuforums.org/showpost.php?p=6129947&postcount=5"), but here's the process that worked for me.

First, get a list of your hardware:
```
lshw
```

Look through the list for the ethernet device you're using, whether wired or wireless. In the section containing the ethernet device info, there will be a "configuration" line that lists the driver. In my case, it was "driver=forcedeth."

Next, run this command to edit the 00sleep_module file:

```
sudo gedit /etc/pm/config.d/00sleep_module
```

At the end of the file, add a line that looks like the following, substituting the name of your driver for "forcedeth."

```
SUSPEND_MODULES="forcedeth"
```

That worked for me.

---

### Post by Eric Qel-Droma on 2008-11-30
I'm going to have to try this, too, as I'm having the same problem.  

Side question:  Does this officially count as a bug?  Is there an easy way to submit a bug?  I've never done it before.

---

### Post by karlmp on 2008-12-02
thank you linux4me:)

**thank you all__**

---

### Post by Thomaseov on 2008-12-03
worked for me with an atheros card, intrepid on a laptop.  Networking was all screwed up after suspend and refusing to connect, linux4me's suggestion did the trick.

---

### Post by gib2800 on 2008-12-04
Thanks. This fixed the same problem I was having in Kubuntu 8.10 Intrepid.

---

### Post by Nisuspi on 2008-12-11
@linux4me

You are a beautiful, beautiful person. I can't tell you how frustrated I've been by this issue since 8.10 came out.

---

### Post by threezee on 2008-12-19
Thanks. Worked like a charm.

---

### Post by chiron80 on 2008-12-29
I used the fix suggested here by linux4me (and in the Release Notes [1]), and now I am experiencing another problem.

Upon resuming my networking is disabled. In this case, fixing it is simple... I just right-click on the network manager icon and check the box labeled "Enable Networking" and everything works smoothly. However, this is definitely a regression from previous behavior, and is kind of annoying. Anybody know how to fix this issue?

[1] [https://wiki.ubuntu.com/IntrepidReleaseNotes#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver](https://wiki.ubuntu.com/IntrepidReleaseNotes#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver)

---

### Post by dcstar on 2008-12-30
> **chiron80 said:**
> I used the fix suggested here by linux4me (and in the Release Notes [1]), and now I am experiencing another problem.
.........

Please don't hijack threads the OP has marked as Solved, if you have a different problem start a new thread that you control.

---

### Post by chiron80 on 2008-12-30
> **dcstar said:**
> Please don't hijack threads the OP has marked as Solved, if you have a different problem start a new thread that you control.

Sorry for the misguided thread "hijack".

I posted here because this thread repeatedly came up when I was searching for a solution, which made me think that others with a similar problem would end up here as well.

As you suggested, I've started a new thread with the new issue:
[http://ubuntuforums.org/showthread.php?t=1025617](http://ubuntuforums.org/showthread.php?t=1025617)

- Ben

---

### Post by biehlbuddy on 2009-01-15
Worked on my IBM ThinkPad X31 with AR5212 802.11abg NIC.  Thanks for saving my suspend.

---

### Post by the_maplebar on 2009-02-12
Thanks worked for me.


Note for other people looking, it did not work at first.  I had a 7.10 upgraded to 8.04 upgraded to 8.10 and I had played with networking setup trying to get WOL.  On a fresh install of 8.10 adding SUSPEND_MODULES="forcedeth" worked perfectly.

---

### Post by king.knut on 2009-12-07
Tried what you proposed but it didn't work for me. In the end simply disabling rt2500pci and installing a Windows driver using ndiswrapper according to this post

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

did the job.

Thanks anyway. Reading this and some other threads eventually helped me to make the right conclusions.

I'm running Kubuntu Karmic using KDE 3.5.10 and nm-applet on an Averatec 3280. Wireless card is a RaLink RT2500 802.11g Cardbus/mini-PCI.

---


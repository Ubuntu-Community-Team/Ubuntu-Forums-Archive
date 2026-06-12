---
title: "Hardy Hangs on Boot"
date: 2008-08-28
forum: General Help
---

### Post by merlin051 on 2008-08-28
Upon booting up my laptop hangs on:

Aug 28 20:17:14 BA57ARD kernel: [    8.916204] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Aug 28 20:17:14 BA57ARD kernel: [    8.916279] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Aug 28 20:17:14 BA57ARD kernel: [    9.242842] ata1.00: ATA-7: SAMSUNG HM160JC, AP100-16, max UDMA/100

As you can see by the timestamp its about 15-20 seconds of doing nothing.

Also another thing thats concerning me is the addition of the bluetooth modules loading on startup, this laptop has no bluetooth device how do i disable them? 

I've removed the bluez tools and that didnt seem to do anything.

```
Aug 28 20:17:14 BA57ARD syslogd 1.5.0#1ubuntu1: restart.
Aug 28 20:17:14 BA57ARD kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 28 20:17:14 BA57ARD kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 28 20:17:14 BA57ARD kernel: Symbols match kernel version 2.6.24.
Aug 28 20:17:14 BA57ARD kernel: Loaded 18290 symbols from 83 modules.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7d3800 (usable)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 000000002f7d3800 - 0000000030000000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] 0MB HIGHMEM available.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] 759MB LOWMEM available.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Zone PFN ranges:
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]   DMA             0 ->     4096
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]   Normal       4096 ->   194515
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]   HighMem    194515 ->   194515
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Movable zone start PFN for each node
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 28 20:17:14 BA57ARD kernel: [    0.000000]     0:        0 ->   194515
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] DMI 2.3 present.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC970 checksum 0
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: RSDP 000FC970, 0014 (r0 DELL  )
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: RSDT 2F7D3FD3, 003C (r1 DELL    D05     27D60118 ASL        61)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: FACP 2F7D4C00, 0074 (r1 DELL    D05     27D60118 ASL        61)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: DSDT 2F7D5800, 324F (r1 INT430 SYSFexxx     1001 MSFT  100000E)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: FACS 2F7E4000, 0040
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: APIC 2F7D5400, 0068 (r1 DELL    D05     27D60118 ASL        47)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: MCFG 2F7D53C0, 003E (r16 DELL    D05     27D60118 ASL        61)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: SSDT 2F7D43E2, 02C2 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: SSDT 2F7D420A, 01D8 (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: SSDT 2F7D400F, 01FB (r1  PmRef    CpuPm     3000 INTL 20030522)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Processor #0 6:13 APIC version 20
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:b0000000)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192996
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Kernel command line: root=UUID=64fa49db-eafc-45ef-9b5d-c6adf7e5142f ro pci=routeirq 
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Initializing CPU#0
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    0.000000] Detected 1695.839 MHz processor.
Aug 28 20:17:14 BA57ARD kernel: [    5.530899] Console: colour VGA+ 80x25
Aug 28 20:17:14 BA57ARD kernel: [    5.530903] console [tty0] enabled
Aug 28 20:17:14 BA57ARD kernel: [    5.535112] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    5.535676] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    5.554318] Memory: 759044k/778060k available (2177k kernel code, 18340k reserved, 1006k data, 368k init, 0k highmem)
Aug 28 20:17:14 BA57ARD kernel: [    5.554430] virtual kernel memory layout:
Aug 28 20:17:14 BA57ARD kernel: [    5.554431]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554432]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554434]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554435]     lowmem  : 0xc0000000 - 0xef7d3000   ( 759 MB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554436]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554437]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554439]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Aug 28 20:17:14 BA57ARD kernel: [    5.554977] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 28 20:17:14 BA57ARD kernel: [    5.555143] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug 28 20:17:14 BA57ARD kernel: [    5.635154] Calibrating delay using timer specific routine.. 3395.48 BogoMIPS (lpj=6790961)
Aug 28 20:17:14 BA57ARD kernel: [    5.635309] Security Framework initialized
Aug 28 20:17:14 BA57ARD kernel: [    5.635380] SELinux:  Disabled at boot.
Aug 28 20:17:14 BA57ARD kernel: [    5.635456] AppArmor: AppArmor initialized
Aug 28 20:17:14 BA57ARD kernel: [    5.635523] Failure registering capabilities with primary security module.
Aug 28 20:17:14 BA57ARD kernel: [    5.635604] Mount-cache hash table entries: 512
Aug 28 20:17:14 BA57ARD kernel: [    5.635795] Initializing cgroup subsys ns
Aug 28 20:17:14 BA57ARD kernel: [    5.635864] Initializing cgroup subsys cpuacct
Aug 28 20:17:14 BA57ARD kernel: [    5.635950] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 28 20:17:14 BA57ARD kernel: [    5.636050] CPU: L2 cache: 2048K
Aug 28 20:17:14 BA57ARD kernel: [    5.636123] Compat vDSO mapped to ffffe000.
Aug 28 20:17:14 BA57ARD kernel: [    5.636198] Checking 'hlt' instruction... OK.
Aug 28 20:17:14 BA57ARD kernel: [    5.651600] SMP alternatives: switching to UP code
Aug 28 20:17:14 BA57ARD kernel: [    5.653619] Freeing SMP alternatives: 11k freed
Aug 28 20:17:14 BA57ARD kernel: [    5.653795] Early unpacking initramfs... done
Aug 28 20:17:14 BA57ARD kernel: [    6.012274] ACPI: Core revision 20070126
Aug 28 20:17:14 BA57ARD kernel: [    6.012396] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 28 20:17:14 BA57ARD kernel: [    6.014899] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
Aug 28 20:17:14 BA57ARD kernel: [    6.015060] Total of 1 processors activated (3395.48 BogoMIPS).
Aug 28 20:17:14 BA57ARD kernel: [    6.015318] ENABLING IO-APIC IRQs
Aug 28 20:17:14 BA57ARD kernel: [    6.015573] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 28 20:17:14 BA57ARD kernel: [    6.162500] Brought up 1 CPUs
Aug 28 20:17:14 BA57ARD kernel: [    6.162763] net_namespace: 64 bytes
Aug 28 20:17:14 BA57ARD kernel: [    6.162835] Booting paravirtualized kernel on bare hardware
Aug 28 20:17:14 BA57ARD kernel: [    6.163363] Time: 20:16:27  Date: 08/28/08
Aug 28 20:17:14 BA57ARD kernel: [    6.163451] NET: Registered protocol family 16
Aug 28 20:17:14 BA57ARD kernel: [    6.163708] EISA bus registered
Aug 28 20:17:14 BA57ARD kernel: [    6.163794] ACPI: bus type pci registered
Aug 28 20:17:14 BA57ARD kernel: [    6.194732] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13
Aug 28 20:17:14 BA57ARD kernel: [    6.194804] PCI: Using configuration type 1
Aug 28 20:17:14 BA57ARD kernel: [    6.194881] Setting up standard PCI resources
Aug 28 20:17:14 BA57ARD kernel: [    6.203163] ACPI: Interpreter enabled
Aug 28 20:17:14 BA57ARD kernel: [    6.203229] ACPI: (supports S0 S3 S4 S5)
Aug 28 20:17:14 BA57ARD kernel: [    6.203433] ACPI: Using IOAPIC for interrupt routing
Aug 28 20:17:14 BA57ARD kernel: [    6.215548] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 28 20:17:14 BA57ARD kernel: [    6.216363] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Aug 28 20:17:14 BA57ARD kernel: [    6.216437] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Aug 28 20:17:14 BA57ARD kernel: [    6.216988] PCI: Transparent bridge - 0000:00:1e.0
Aug 28 20:17:14 BA57ARD kernel: [    6.224322] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Aug 28 20:17:14 BA57ARD kernel: [    6.224656] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Aug 28 20:17:14 BA57ARD kernel: [    6.224988] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Aug 28 20:17:14 BA57ARD kernel: [    6.225319] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
Aug 28 20:17:14 BA57ARD kernel: [    6.225703] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.226383] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.227059] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.227766] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 28 20:17:14 BA57ARD kernel: [    6.227866] pnp: PnP ACPI init
Aug 28 20:17:14 BA57ARD kernel: [    6.227933] ACPI: bus type pnp registered
Aug 28 20:17:14 BA57ARD kernel: [    6.241414] pnpacpi: exceeded the max number of mem resources: 12
Aug 28 20:17:14 BA57ARD kernel: [    6.253485] pnp: PnP ACPI: found 11 devices
Aug 28 20:17:14 BA57ARD kernel: [    6.253552] ACPI: ACPI bus type pnp unregistered
Aug 28 20:17:14 BA57ARD kernel: [    6.253620] PnPBIOS: Disabled by ACPI PNP
Aug 28 20:17:14 BA57ARD kernel: [    6.253889] PCI: Using ACPI for IRQ routing
Aug 28 20:17:14 BA57ARD kernel: [    6.253956] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
Aug 28 20:17:14 BA57ARD kernel: [    6.254055] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.254184] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.254311] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.254442] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Aug 28 20:17:14 BA57ARD kernel: [    6.254570] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.254699] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Aug 28 20:17:14 BA57ARD kernel: [    6.254827] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Aug 28 20:17:14 BA57ARD kernel: [    6.254955] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Aug 28 20:17:14 BA57ARD kernel: [    6.255083] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.255211] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.255339] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Aug 28 20:17:14 BA57ARD kernel: [    6.255466] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Aug 28 20:17:14 BA57ARD kernel: [    6.298280] NET: Registered protocol family 8
Aug 28 20:17:14 BA57ARD kernel: [    6.298346] NET: Registered protocol family 20
Aug 28 20:17:14 BA57ARD kernel: [    6.298578] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 28 20:17:14 BA57ARD kernel: [    6.298777] hpet0: 3 64-bit timers, 14318180 Hz
Aug 28 20:17:14 BA57ARD kernel: [    6.299878] AppArmor: AppArmor Filesystem Enabled
Aug 28 20:17:14 BA57ARD kernel: [    6.302265] Time: tsc clocksource has been installed.
Aug 28 20:17:14 BA57ARD kernel: [    6.310291] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310365] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310439] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310513] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310587] system 00:00: iomem range 0x100000-0x2f7d37ff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310683] system 00:00: iomem range 0x2f7d3800-0x2f7fffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310778] system 00:00: iomem range 0x2f800000-0x2fffffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310874] system 00:00: iomem range 0xfeda0000-0xfedfffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.310969] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311065] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311162] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311258] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311357] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311429] system 00:02: ioport range 0x1000-0x1005 has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311502] system 00:02: ioport range 0x1008-0x100f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.311577] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.312859] system 00:03: ioport range 0x1006-0x1007 has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.312932] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313006] system 00:03: ioport range 0x1060-0x107f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313079] system 00:03: ioport range 0x1080-0x10bf has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313152] system 00:03: ioport range 0x10c0-0x10df has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313224] system 00:03: ioport range 0x10e0-0x10ff has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313301] system 00:08: ioport range 0x900-0x90f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313373] system 00:08: ioport range 0x910-0x91f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313445] system 00:08: ioport range 0x920-0x92f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313517] system 00:08: ioport range 0x930-0x93f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.313589] system 00:08: ioport range 0x940-0x97f has been reserved
Aug 28 20:17:14 BA57ARD kernel: [    6.344015] PCI: Bridge: 0000:00:1c.0
Aug 28 20:17:14 BA57ARD kernel: [    6.344079]   IO window: disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.344148]   MEM window: disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.344213]   PREFETCH window: disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.344281] PCI: Bridge: 0000:00:1c.3
Aug 28 20:17:14 BA57ARD kernel: [    6.344347]   IO window: d000-dfff
Aug 28 20:17:14 BA57ARD kernel: [    6.344413]   MEM window: dfc00000-dfdfffff
Aug 28 20:17:14 BA57ARD kernel: [    6.344481]   PREFETCH window: d0000000-d01fffff
Aug 28 20:17:14 BA57ARD kernel: [    6.344552] PCI: Bridge: 0000:00:1e.0
Aug 28 20:17:14 BA57ARD kernel: [    6.344616]   IO window: disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.344683]   MEM window: dfb00000-dfbfffff
Aug 28 20:17:14 BA57ARD kernel: [    6.344750]   PREFETCH window: disabled.
Aug 28 20:17:14 BA57ARD kernel: [    6.344844] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    6.344998] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Aug 28 20:17:14 BA57ARD kernel: [    6.345152] NET: Registered protocol family 2
Aug 28 20:17:14 BA57ARD kernel: [    6.382216] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    6.382525] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    6.383496] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    6.384107] TCP: Hash tables configured (established 131072 bind 65536)
Aug 28 20:17:14 BA57ARD kernel: [    6.384182] TCP reno registered
Aug 28 20:17:14 BA57ARD kernel: [    6.394307] checking if image is initramfs... it is
Aug 28 20:17:14 BA57ARD kernel: [    7.098451] Freeing initrd memory: 7321k freed
Aug 28 20:17:14 BA57ARD kernel: [    7.099182] audit: initializing netlink socket (disabled)
Aug 28 20:17:14 BA57ARD kernel: [    7.099271] audit(1219954587.440:1): initialized
Aug 28 20:17:14 BA57ARD kernel: [    7.101451] VFS: Disk quotas dquot_6.5.1
Aug 28 20:17:14 BA57ARD kernel: [    7.101596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 28 20:17:14 BA57ARD kernel: [    7.101831] io scheduler noop registered
Aug 28 20:17:14 BA57ARD kernel: [    7.101897] io scheduler anticipatory registered
Aug 28 20:17:14 BA57ARD kernel: [    7.101963] io scheduler deadline registered
Aug 28 20:17:14 BA57ARD kernel: [    7.102040] io scheduler cfq registered (default)
Aug 28 20:17:14 BA57ARD kernel: [    7.102378] assign_interrupt_mode Found MSI capability
Aug 28 20:17:14 BA57ARD kernel: [    7.102688] assign_interrupt_mode Found MSI capability
Aug 28 20:17:14 BA57ARD kernel: [    7.103087] isapnp: Scanning for PnP cards...
Aug 28 20:17:14 BA57ARD kernel: [    7.456938] isapnp: No Plug & Play device found
Aug 28 20:17:14 BA57ARD kernel: [    7.484203] Real Time Clock Driver v1.12ac
Aug 28 20:17:14 BA57ARD kernel: [    7.484398] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 28 20:17:14 BA57ARD kernel: [    7.485667] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 28 20:17:14 BA57ARD kernel: [    7.485841] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 28 20:17:14 BA57ARD kernel: [    7.486029] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 28 20:17:14 BA57ARD kernel: [    7.486266] i8042.c: Warning: Keylock active.
Aug 28 20:17:14 BA57ARD kernel: [    7.487769] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 28 20:17:14 BA57ARD kernel: [    7.487839] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 28 20:17:14 BA57ARD kernel: [    7.488783] mice: PS/2 mouse device common for all mice
Aug 28 20:17:14 BA57ARD kernel: [    7.488957] EISA: Probing bus 0 at eisa.0
Aug 28 20:17:14 BA57ARD kernel: [    7.489035] Cannot allocate resource for EISA slot 1
Aug 28 20:17:14 BA57ARD kernel: [    7.489133] EISA: Detected 0 cards.
Aug 28 20:17:14 BA57ARD kernel: [    7.489198] cpuidle: using governor ladder
Aug 28 20:17:14 BA57ARD kernel: [    7.489264] cpuidle: using governor menu
Aug 28 20:17:14 BA57ARD kernel: [    7.489422] NET: Registered protocol family 1
Aug 28 20:17:14 BA57ARD kernel: [    7.489516] Using IPI No-Shortcut mode
Aug 28 20:17:14 BA57ARD kernel: [    7.489615] registered taskstats version 1
Aug 28 20:17:14 BA57ARD kernel: [    7.489783]   Magic number: 4:957:296
Aug 28 20:17:14 BA57ARD kernel: [    7.489863]   hash matches device ttywd
Aug 28 20:17:14 BA57ARD kernel: [    7.489988]   hash matches device tty29
Aug 28 20:17:14 BA57ARD kernel: [    7.490076] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 28 20:17:14 BA57ARD kernel: [    7.490146] EDD information not available.
Aug 28 20:17:14 BA57ARD kernel: [    7.490442] Freeing unused kernel memory: 368k freed
Aug 28 20:17:14 BA57ARD kernel: [    7.491903] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 28 20:17:14 BA57ARD kernel: [    7.693352] fuse init (API version 7.9)
Aug 28 20:17:14 BA57ARD kernel: [    7.712359] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Aug 28 20:17:14 BA57ARD kernel: [    7.712600] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 28 20:17:14 BA57ARD kernel: [    7.712748] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 28 20:17:14 BA57ARD kernel: [    7.717334] ACPI: Thermal Zone [THM] (55 C)
Aug 28 20:17:14 BA57ARD kernel: [    8.335421] usbcore: registered new interface driver usbfs
Aug 28 20:17:14 BA57ARD kernel: [    8.335520] usbcore: registered new interface driver hub
Aug 28 20:17:14 BA57ARD kernel: [    8.347159] usbcore: registered new device driver usb
Aug 28 20:17:14 BA57ARD kernel: [    8.359355] USB Universal Host Controller Interface driver v3.0
Aug 28 20:17:14 BA57ARD kernel: [    8.359490] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    8.359633] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 28 20:17:14 BA57ARD kernel: [    8.360114] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug 28 20:17:14 BA57ARD kernel: [    8.360240] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
Aug 28 20:17:14 BA57ARD kernel: [    8.360454] usb usb1: configuration #1 chosen from 1 choice
Aug 28 20:17:14 BA57ARD kernel: [    8.360549] hub 1-0:1.0: USB hub found
Aug 28 20:17:14 BA57ARD kernel: [    8.360618] hub 1-0:1.0: 2 ports detected
Aug 28 20:17:14 BA57ARD kernel: [    8.430807] SCSI subsystem initialized
Aug 28 20:17:14 BA57ARD kernel: [    8.463269] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 18
Aug 28 20:17:14 BA57ARD kernel: [    8.463420] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 28 20:17:14 BA57ARD kernel: [    8.463511] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug 28 20:17:14 BA57ARD kernel: [    8.463637] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000bf60
Aug 28 20:17:14 BA57ARD kernel: [    8.463817] usb usb2: configuration #1 chosen from 1 choice
Aug 28 20:17:14 BA57ARD kernel: [    8.463912] hub 2-0:1.0: USB hub found
Aug 28 20:17:14 BA57ARD kernel: [    8.463980] hub 2-0:1.0: 2 ports detected
Aug 28 20:17:14 BA57ARD kernel: [    8.567126] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Aug 28 20:17:14 BA57ARD kernel: [    8.567274] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 28 20:17:14 BA57ARD kernel: [    8.567366] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug 28 20:17:14 BA57ARD kernel: [    8.567493] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
Aug 28 20:17:14 BA57ARD kernel: [    8.567674] usb usb3: configuration #1 chosen from 1 choice
Aug 28 20:17:14 BA57ARD kernel: [    8.567766] hub 3-0:1.0: USB hub found
Aug 28 20:17:14 BA57ARD kernel: [    8.567835] hub 3-0:1.0: 2 ports detected
Aug 28 20:17:14 BA57ARD kernel: [    8.670970] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
Aug 28 20:17:14 BA57ARD kernel: [    8.671119] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 28 20:17:14 BA57ARD kernel: [    8.671210] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Aug 28 20:17:14 BA57ARD kernel: [    8.671337] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000bf20
Aug 28 20:17:14 BA57ARD kernel: [    8.671519] usb usb4: configuration #1 chosen from 1 choice
Aug 28 20:17:14 BA57ARD kernel: [    8.671610] hub 4-0:1.0: USB hub found
Aug 28 20:17:14 BA57ARD kernel: [    8.671678] hub 4-0:1.0: 2 ports detected
Aug 28 20:17:14 BA57ARD kernel: [    8.774959] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    8.775111] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 28 20:17:14 BA57ARD kernel: [    8.775202] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Aug 28 20:17:14 BA57ARD kernel: [    8.779206] ehci_hcd 0000:00:1d.7: debug port 1
Aug 28 20:17:14 BA57ARD kernel: [    8.779284] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
Aug 28 20:17:14 BA57ARD kernel: [    8.794693] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 28 20:17:14 BA57ARD kernel: [    8.794899] usb usb5: configuration #1 chosen from 1 choice
Aug 28 20:17:14 BA57ARD kernel: [    8.794994] hub 5-0:1.0: USB hub found
Aug 28 20:17:14 BA57ARD kernel: [    8.795063] hub 5-0:1.0: 8 ports detected
Aug 28 20:17:14 BA57ARD kernel: [    8.900205] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [    8.914913] scsi0 : ata_piix
Aug 28 20:17:14 BA57ARD kernel: [    8.915543] scsi1 : ata_piix
Aug 28 20:17:14 BA57ARD kernel: [    8.916204] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Aug 28 20:17:14 BA57ARD kernel: [    8.916279] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Aug 28 20:17:14 BA57ARD kernel: [    9.242842] ata1.00: ATA-7: SAMSUNG HM160JC, AP100-16, max UDMA/100
Aug 28 20:17:14 BA57ARD kernel: [    9.242922] ata1.00: 312581808 sectors, multi 8: LBA48 
Aug 28 20:17:14 BA57ARD kernel: [    9.243015] ata1.01: ATAPI: TSSTcorp DVD+/-RW TS-L532B, DE03, max UDMA/33
Aug 28 20:17:14 BA57ARD kernel: [    9.258748] ata1.00: configured for UDMA/100
Aug 28 20:17:14 BA57ARD kernel: [    9.293972] Clocksource tsc unstable (delta = -26784026280 ns)
Aug 28 20:17:14 BA57ARD kernel: [    9.297980] Time: hpet clocksource has been installed.
Aug 28 20:17:14 BA57ARD kernel: [    9.305369] ata1.01: configured for UDMA/33
Aug 28 20:17:14 BA57ARD kernel: [    9.305631] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160JC  AP10 PQ: 0 ANSI: 5
Aug 28 20:17:14 BA57ARD kernel: [    9.306491] scsi 0:0:1:0: CD-ROM            TSSTcorp DVD+-RW TS-L532B DE03 PQ: 0 ANSI: 5
Aug 28 20:17:14 BA57ARD kernel: [    9.309986] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
Aug 28 20:17:14 BA57ARD kernel: [    9.314975] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Aug 28 20:17:14 BA57ARD kernel: [    9.315076] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Aug 28 20:17:14 BA57ARD kernel: [    9.315152] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Aug 28 20:17:14 BA57ARD kernel: [    9.319095] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
Aug 28 20:17:14 BA57ARD kernel: [    9.319188] b44.c:v2.0
Aug 28 20:17:14 BA57ARD kernel: [    9.320435] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:9c:f4:ed
Aug 28 20:17:14 BA57ARD kernel: [    9.352515] Driver 'sd' needs updating - please use bus_type methods
Aug 28 20:17:14 BA57ARD kernel: [    9.352673] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 28 20:17:14 BA57ARD kernel: [    9.352758] sd 0:0:0:0: [sda] Write Protect is off
Aug 28 20:17:14 BA57ARD kernel: [    9.352841] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 28 20:17:14 BA57ARD kernel: [    9.352986] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 28 20:17:14 BA57ARD kernel: [    9.353067] sd 0:0:0:0: [sda] Write Protect is off
Aug 28 20:17:14 BA57ARD kernel: [    9.353149] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 28 20:17:14 BA57ARD kernel: [    9.354458]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 28 20:17:14 BA57ARD kernel: [    9.378075]  sda1 sda2 < sda5 sda6 sda7 >
Aug 28 20:17:14 BA57ARD kernel: [    9.379621] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 28 20:17:14 BA57ARD kernel: [    9.384895] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 28 20:17:14 BA57ARD kernel: [    9.384982] sr 0:0:1:0: Attached scsi generic sg1 type 5
Aug 28 20:17:14 BA57ARD kernel: [    9.407821] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Aug 28 20:17:14 BA57ARD kernel: [    9.407899] Uniform CD-ROM driver Revision: 3.20
Aug 28 20:17:14 BA57ARD kernel: [    9.493191] Attempting manual resume
Aug 28 20:17:14 BA57ARD kernel: [    9.508647] kjournald starting.  Commit interval 5 seconds
Aug 28 20:17:14 BA57ARD kernel: [    9.508729] EXT3-fs: mounted filesystem with ordered data mode.
Aug 28 20:17:14 BA57ARD kernel: [   11.785976] Linux agpgart interface v0.102
Aug 28 20:17:14 BA57ARD kernel: [   11.913866] agpgart: Detected an Intel 915GM Chipset.
Aug 28 20:17:14 BA57ARD kernel: [   11.914479] agpgart: Detected 7932K stolen memory.
Aug 28 20:17:14 BA57ARD kernel: [   12.033634] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 28 20:17:14 BA57ARD kernel: [   12.089575] agpgart: AGP aperture is 256M @ 0xc0000000
Aug 28 20:17:14 BA57ARD kernel: [   12.090525] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 28 20:17:14 BA57ARD kernel: [   12.437418] ACPI: AC Adapter [AC] (on-line)
Aug 28 20:17:14 BA57ARD kernel: [   12.816468] ACPI: Battery Slot [BAT0] (battery present)
Aug 28 20:17:14 BA57ARD kernel: [   12.816604] input: Lid Switch as /devices/virtual/input/input2
Aug 28 20:17:14 BA57ARD kernel: [   12.817225] ACPI: Lid Switch [LID]
Aug 28 20:17:14 BA57ARD kernel: [   12.817331] input: Power Button (CM) as /devices/virtual/input/input3
Aug 28 20:17:14 BA57ARD kernel: [   12.832426] ACPI: Power Button (CM) [PBTN]
Aug 28 20:17:14 BA57ARD kernel: [   12.832560] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 28 20:17:14 BA57ARD kernel: [   12.848402] ACPI: Sleep Button (CM) [SBTN]
Aug 28 20:17:14 BA57ARD kernel: [   13.080736] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
Aug 28 20:17:14 BA57ARD kernel: [   13.092053] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Aug 28 20:17:14 BA57ARD kernel: [   13.092290] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
Aug 28 20:17:14 BA57ARD kernel: [   13.108025] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Aug 28 20:17:14 BA57ARD kernel: [   14.739055] iTCO_vendor_support: vendor-support=0
Aug 28 20:17:14 BA57ARD kernel: [   14.801564] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Aug 28 20:17:14 BA57ARD kernel: [   14.801742] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
Aug 28 20:17:14 BA57ARD kernel: [   14.801849] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug 28 20:17:14 BA57ARD kernel: [   14.806962] ath_hal: module license 'Proprietary' taints kernel.
Aug 28 20:17:14 BA57ARD kernel: [   14.841512] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Aug 28 20:17:14 BA57ARD kernel: [   15.009606] wlan: 0.9.4
Aug 28 20:17:14 BA57ARD kernel: [   15.056408] ath_pci: 0.9.4
Aug 28 20:17:14 BA57ARD kernel: [   15.056552] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 18
Aug 28 20:17:14 BA57ARD kernel: [   15.749935] input: PC Speaker as /devices/platform/pcspkr/input/input7
Aug 28 20:17:14 BA57ARD kernel: [   15.955965] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:14 BA57ARD kernel: [   16.314598] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000
Aug 28 20:17:14 BA57ARD kernel: [   16.350855] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Aug 28 20:17:14 BA57ARD kernel: [   16.395639] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug 28 20:17:14 BA57ARD kernel: [   16.505853] NET: Registered protocol family 10
Aug 28 20:17:14 BA57ARD kernel: [   16.506125] lo: Disabled Privacy Extensions
Aug 28 20:17:14 BA57ARD kernel: [   16.507459] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 28 20:17:14 BA57ARD kernel: [   16.538282] ath_rate_sample: 1.2 (0.9.4)
Aug 28 20:17:14 BA57ARD kernel: [   16.539074] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Aug 28 20:17:14 BA57ARD kernel: [   16.539309] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Aug 28 20:17:14 BA57ARD kernel: [   16.539838] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Aug 28 20:17:14 BA57ARD kernel: [   16.540197] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Aug 28 20:17:14 BA57ARD kernel: [   16.540430] wifi0: mac 7.9 phy 4.5 radio 5.6
Aug 28 20:17:14 BA57ARD kernel: [   16.540565] wifi0: Use hw queue 1 for WME_AC_BE traffic
Aug 28 20:17:14 BA57ARD kernel: [   16.540633] wifi0: Use hw queue 0 for WME_AC_BK traffic
Aug 28 20:17:14 BA57ARD kernel: [   16.540703] wifi0: Use hw queue 2 for WME_AC_VI traffic
Aug 28 20:17:14 BA57ARD kernel: [   16.540771] wifi0: Use hw queue 3 for WME_AC_VO traffic
Aug 28 20:17:14 BA57ARD kernel: [   16.540840] wifi0: Use hw queue 8 for CAB traffic
Aug 28 20:17:14 BA57ARD kernel: [   16.540907] wifi0: Use hw queue 9 for beacons
Aug 28 20:17:14 BA57ARD kernel: [   16.568868] wifi0: Atheros 5212: mem=0xdfbf0000, irq=18
Aug 28 20:17:14 BA57ARD kernel: [   17.694079] lp: driver loaded but no devices found
Aug 28 20:17:14 BA57ARD kernel: [   17.873726] Adding 2249060k swap on /dev/sda6.  Priority:-1 extents:1 across:2249060k
Aug 28 20:17:14 BA57ARD kernel: [   17.944428] EXT3 FS on sda5, internal journal
Aug 28 20:17:14 BA57ARD kernel: [   18.314177] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 28 20:17:14 BA57ARD kernel: [   18.684697] No dock devices found.
Aug 28 20:17:14 BA57ARD kernel: [   18.838564] b44: eth0: Link is up at 100 Mbps, full duplex.
Aug 28 20:17:14 BA57ARD kernel: [   18.838568] b44: eth0: Flow control is off for TX and off for RX.
Aug 28 20:17:14 BA57ARD kernel: [   18.839983] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 28 20:17:14 BA57ARD kernel: [   19.245056] apm: BIOS not found.
Aug 28 20:17:14 BA57ARD kernel: [   19.278610] ppdev: user-space parallel port driver
Aug 28 20:17:15 BA57ARD kernel: [   19.297802] audit(1219951035.001:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6102 profile="/usr/sbin/cupsd" namespace="default"
Aug 28 20:17:15 BA57ARD kernel: [   23.523056] Marking TSC unstable due to: cpufreq changes.
Aug 28 20:17:15 BA57ARD dhcdbd: Started up.
Aug 28 20:17:17 BA57ARD kernel: [   57.045121] Bluetooth: Core ver 2.11
Aug 28 20:17:17 BA57ARD kernel: [   57.045955] NET: Registered protocol family 31
Aug 28 20:17:17 BA57ARD kernel: [   57.045964] Bluetooth: HCI device and connection manager initialized
Aug 28 20:17:17 BA57ARD kernel: [   57.045974] Bluetooth: HCI socket layer initialized
Aug 28 20:17:17 BA57ARD kernel: [   20.247999] Bluetooth: L2CAP ver 2.9
Aug 28 20:17:17 BA57ARD kernel: [   20.248003] Bluetooth: L2CAP socket layer initialized
Aug 28 20:17:17 BA57ARD kernel: [   20.338484] Bluetooth: RFCOMM socket layer initialized
Aug 28 20:17:17 BA57ARD kernel: [   20.338500] Bluetooth: RFCOMM TTY layer initialized
Aug 28 20:17:17 BA57ARD kernel: [   20.338502] Bluetooth: RFCOMM ver 1.8
Aug 28 20:17:20 BA57ARD kernel: [   63.040352] [drm] Initialized drm 1.1.0 20060810
Aug 28 20:17:20 BA57ARD kernel: [   63.047028] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 28 20:17:20 BA57ARD kernel: [   63.047183] [drm] Initialized i915 1.6.0 20060119 on minor 0
```

[IMG]http://www.freeimagehosting.net/uploads/faf202dbb6.png[/IMG]

---

### Post by MyR on 2008-08-29
I had a similar problem. Upon changing it to display text during boot I could see it was hanging on "waiting for root file system...".
I had to edit /boot/grub/menu.lst and added all_generic_ide to the end of the kernel line I was using to boot. (I'll assume you know how to do this)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=609e0be5-312f-4218-8a17-10abaacfe591 ro splash quiet all_generic_ide

I haven't noticed any negative side effects and it has resolved the issue.

Also, have you disabled the bluetooth service? in system > administration > services

peace

---

### Post by merlin051 on 2008-08-29
I've removed the bluetooth from 'system > administration > services' and removed it from 'system > preferenced > sessions'

Its still running, so I've either missed something or there is something else that still calls it on boot.

I'll try adding 'all_generic_ide' to the kernal line and see if it has any effect.

Another thing that I noticed I'm getting this message on boot:
```
Aug 28 20:17:14 BA57ARD kernel: [    7.712359] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Aug 28 20:17:14 BA57ARD kernel: [    7.712600] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 28 20:17:14 BA57ARD kernel: [    7.712748] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 28 20:17:14 BA57ARD kernel: [    7.717334] ACPI: Thermal Zone [THM] (55 C)

```

[COLOR="Red"]**AE_NOT_FOUND, Processor Device is not present [20070126]**[/COLOR]

Anything i can do to stop this happening? does it mean anything?

Cheers

---

### Post by jcfuller on 2008-08-30
> **MyR said:**
> I had a similar problem. Upon changing it to display text during boot I could see it was hanging on "waiting for root file system...".
I had to edit /boot/grub/menu.lst and added all_generic_ide to the end of the kernel line I was using to boot. (I'll assume you know how to do this)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=609e0be5-312f-4218-8a17-10abaacfe591 ro splash quiet all_generic_ide

I haven't noticed any negative side effects and it has resolved the issue.

Also, have you disabled the bluetooth service? in system > administration > services

peace

Thank you sir. Worked like a champ so far.

James

---

### Post by merlin051 on 2008-09-01
Wow, my startup speed up by about 20 seconds now, thanks alot!!

Its giving me some other erros i didnt see before which if i can find a solution for those might make a further improovement to my bootup.

Thanks!!

---


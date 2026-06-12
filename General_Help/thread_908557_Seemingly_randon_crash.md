---
title: "Seemingly randon crash?"
date: 2008-09-02
forum: General Help
---

### Post by parabolee on 2008-09-02
Sometimes my Ubuntu laptop seems to just randomly crash.

Today it seemed to happen when I clicked on the desktop of my external/extended screen. But it sometimes happens when I'm not using an external/extended screen and am just using my laptop screen.

It just crashed twice in a row within minutes, seemingly after I click on the seconds screen.

Can anyone help?

Here are my Messages and syslog readout after the crashes -

MESSAGES ---------------------------------------------------------------------------

Sep  2 15:38:17 lee-laptop-ub-linux -- MARK --
Sep  2 15:46:21 lee-laptop-ub-linux gnome-power-manager: (lee) GNOME interactive logout. Reason: The power button has been pressed.
Sep  2 15:47:10 lee-laptop-ub-linux syslogd 1.5.0#1ubuntu1: restart.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Symbols match kernel version 2.6.24.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Loaded 24943 symbols from 100 modules.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfed3400 (usable)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000cfed3400 - 00000000d0000000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] 2430MB HIGHMEM available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Zone PFN ranges:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   HighMem    229376 ->   851667
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Movable zone start PFN for each node
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]     0:        0 ->   851667
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] DMI 2.4 present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDT CFED39CD, 0040 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: FACP CFED4800, 0074 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: DSDT CFED5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: FACS CFEE3C00, 0040
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: HPET CFED4F00, 0038 (r1 DELL    M07            1 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: APIC CFED5000, 0068 (r1 DELL    M07     27D70205 ASL        47)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: MCFG CFED4FC0, 003E (r16 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: SLIC CFED509C, 0176 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: BOOT CFED4BC0, 0028 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: SSDT CFED3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Processor #0 6:14 APIC version 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Processor #1 6:14 APIC version 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Allocating PCI resources starting at d2000000 (gap: d0000000:20000000)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845014
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Kernel command line: root=UUID=2ddf34a7-c94d-48bf-b1cd-15c9ecd19f55 ro quiet splash
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing CPU#0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Detected 1729.063 MHz processor.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706529] Console: colour VGA+ 80x25
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706533] console [tty0] enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706842] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.707228] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947556] Memory: 3366388k/3406668k available (2177k kernel code, 38972k reserved, 1006k data, 368k init, 2489164k highmem)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947565] virtual kernel memory layout:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947566]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947567]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947568]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947570]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947571]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947572]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947573]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947577] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947618] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027739] Calibrating delay using timer specific routine.. 3462.05 BogoMIPS (lpj=6924106)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027762] Security Framework initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027770] SELinux:  Disabled at boot.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027785] AppArmor: AppArmor initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027789] Failure registering capabilities with primary security module.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027798] Mount-cache hash table entries: 512
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027928] Initializing cgroup subsys ns
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027933] Initializing cgroup subsys cpuacct
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027951] monitor/mwait feature present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027953] using mwait in idle threads.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027957] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027960] CPU: L2 cache: 2048K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027963] CPU: Physical Processor ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027964] CPU: Processor Core ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027977] Compat vDSO mapped to ffffe000.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027989] Checking 'hlt' instruction... OK.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.044126] SMP alternatives: switching to UP code
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.045908] Early unpacking initramfs... done
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.396930] ACPI: Core revision 20070126
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.396986] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.399715] CPU0: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.399732] SMP alternatives: switching to SMP code
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.400403] Booting processor 1/1 eip 3000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.435279] Initializing CPU#1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514458] Calibrating delay using timer specific routine.. 3458.08 BogoMIPS (lpj=6916166)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514471] monitor/mwait feature present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514474] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514476] CPU: L2 cache: 2048K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514478] CPU: Physical Processor ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514480] CPU: Processor Core ID: 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492091] CPU1: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492114] Total of 2 processors activated (6920.13 BogoMIPS).
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492314] ENABLING IO-APIC IRQs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492509] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.639588] checking TSC synchronization [CPU#0 -> CPU#1]:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659587] Measured 3499110940 cycles TSC warp between CPUs, turning off TSC clock.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659590] Marking TSC unstable due to: check_tsc_sync_source failed.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659603] Brought up 2 CPUs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.682816] net_namespace: 64 bytes
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.682826] Booting paravirtualized kernel on bare hardware
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683295] Time: 15:46:47  Date: 09/02/08
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683324] NET: Registered protocol family 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683546] EISA bus registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683551] ACPI: bus type pci registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712285] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712287] PCI: Using configuration type 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712302] Setting up standard PCI resources
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699905] ACPI: Interpreter enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699909] ACPI: (supports S0 S3 S4 S5)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699922] ACPI: Using IOAPIC for interrupt routing
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.713685] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.714433] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.714438] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716115] PCI: Transparent bridge - 0000:00:1e.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.724832] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.724942] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725049] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725156] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725264] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725374] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725485] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725594] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725746] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725780] pnp: PnP ACPI init
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725788] ACPI: bus type pnp registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.742058] pnpacpi: exceeded the max number of mem resources: 12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754700] pnp: PnP ACPI: found 12 devices
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754703] ACPI: ACPI bus type pnp unregistered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754706] PnPBIOS: Disabled by ACPI PNP
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.777879] PCI: Using ACPI for IRQ routing
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.777882] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854449] NET: Registered protocol family 8
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854451] NET: Registered protocol family 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854493] hpet0: 3 64-bit timers, 14318180 Hz
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.855527] AppArmor: AppArmor Filesystem Enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.835392] Time: hpet clocksource has been installed.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848389] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848393] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848396] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848399] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848402] system 00:00: iomem range 0x100000-0xcfed33ff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848406] system 00:00: iomem range 0xcfed3400-0xcfefffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848409] system 00:00: iomem range 0xcff00000-0xcfffffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848412] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848415] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848419] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848422] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848425] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848432] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848435] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848438] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848444] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848447] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848450] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848453] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848456] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848459] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848462] system 00:03: ioport range 0x1010-0x102f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848465] system 00:03: ioport range 0x809-0x809 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848473] system 00:08: ioport range 0xc80-0xcff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848476] system 00:08: ioport range 0x910-0x91f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848479] system 00:08: ioport range 0x920-0x92f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848482] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848484] system 00:08: ioport range 0x930-0x97f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848495] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878955] PCI: Bridge: 0000:00:01.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878958]   IO window: e000-efff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878962]   MEM window: efd00000-efefffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878965]   PREFETCH window: d0000000-dfffffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878969] PCI: Bridge: 0000:00:1c.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878971]   IO window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878976]   MEM window: efc00000-efcfffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878981]   PREFETCH window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878987] PCI: Bridge: 0000:00:1c.3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878990]   IO window: d000-dfff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878996]   MEM window: efa00000-efbfffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879001]   PREFETCH window: e0000000-e01fffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879007] PCI: Bridge: 0000:00:1e.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879009]   IO window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879014]   MEM window: ef900000-ef9fffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879019]   PREFETCH window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879037] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879066] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879097] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879128] NET: Registered protocol family 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.923371] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.923601] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924305] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924656] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924658] TCP reno registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.935458] checking if image is initramfs... it is
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.630969] Freeing initrd memory: 7324k freed
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.631143] Simple Boot Flag at 0x79 set to 0x1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.654788] audit: initializing netlink socket (disabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.654801] audit(1220370407.560:1): initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.632168] highmem bounce pool size: 64 pages
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634297] VFS: Disk quotas dquot_6.5.1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634375] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634510] io scheduler noop registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634512] io scheduler anticipatory registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634515] io scheduler deadline registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634526] io scheduler cfq registered (default)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634794] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634969] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635231] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635601] isapnp: Scanning for PnP cards...
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.990460] isapnp: No Plug & Play device found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.019931] Real Time Clock Driver v1.12ac
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.020143] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021399] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021473] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021575] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.024509] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.024514] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.042890] mice: PS/2 mouse device common for all mice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043016] EISA: Probing bus 0 at eisa.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043025] Cannot allocate resource for EISA slot 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043055] EISA: Detected 0 cards.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043058] cpuidle: using governor ladder
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043060] cpuidle: using governor menu
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043148] NET: Registered protocol family 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043175] Using IPI No-Shortcut mode
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043212] registered taskstats version 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043324]   Magic number: 8:992:789
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043411] EDD information not available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043617] Freeing unused kernel memory: 368k freed
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.068908] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.283229] fuse init (API version 7.9)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.301282] ACPI: SSDT CFED4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.301476] ACPI: SSDT CFED3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279150] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279156] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279388] ACPI: SSDT CFED4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279570] ACPI: SSDT CFED40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.303143] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.303148] ACPI: Processor [CPU1] (supports 8 throttling states)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.308284] ACPI: Thermal Zone [THM] (51 C)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.648337] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670104] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670128] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670147] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670166] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.692224] usbcore: registered new interface driver usbfs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.692248] usbcore: registered new interface driver hub
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.696756] usbcore: registered new device driver usb
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.698558] USB Universal Host Controller Interface driver v3.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714156] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714211] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714227] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714493] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714528] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714663] usb usb1: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714689] hub 1-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714695] hub 1-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.764802] SCSI subsystem initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818059] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818078] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818101] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818135] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818253] usb usb2: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818276] hub 2-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818282] hub 2-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944955] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944974] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944999] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945033] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945152] usb usb3: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945176] hub 3-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945181] hub 3-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045897] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045914] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045938] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045971] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046089] usb usb4: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046115] hub 4-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046120] hub 4-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.126986] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.127006] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.127033] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.130961] ehci_hcd 0000:00:1d.7: debug port 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.130976] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149815] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149945] usb usb5: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149970] hub 5-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149976] hub 5-0:1.0: 8 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.253983] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.306771] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.310887] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333763] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333771] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333779] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393701] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393726] b44.c:v2.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393761] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393791] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393902] scsi0 : ata_piix
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393950] scsi1 : ata_piix
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.394730] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.394733] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.412995] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:68:2e:68
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.564574] usb 5-7: new high speed USB device using ehci_hcd and address 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.573547] ata1.00: ATA-8: WDC WD3200BEVT-00ZCT0, 11.01A11, max UDMA/133
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.573551] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.591131] ata1.00: configured for UDMA/133
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674034] usb 5-7: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674200] hub 5-7:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674300] hub 5-7:1.0: 4 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.956916] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.993560] usb 5-7.1: new high speed USB device using ehci_hcd and address 3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.086360] usb 5-7.1: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.148731] ata2.00: configured for UDMA/33
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.125983] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 11.0 PQ: 0 ANSI: 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.134547] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167683] Driver 'sd' needs updating - please use bus_type methods
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167762] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167775] sd 0:0:0:0: [sda] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167849] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167860] sd 0:0:0:0: [sda] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167883] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167887]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.196241]  sda1 sda2 < sda5 sda6 >
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.225454] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.231036] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.231057] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.290356] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.290361] Uniform CD-ROM driver Revision: 3.20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.302419] usb 5-7.4: new low speed USB device using ehci_hcd and address 4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.418721] usb 5-7.4: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.442614] usbcore: registered new interface driver libusual
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.448622] Initializing USB Mass Storage driver...
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.449847] scsi2 : SCSI emulation for USB Mass Storage devices
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450329] usbcore: registered new interface driver usb-storage
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450333] USB Mass Storage support registered.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.466039] usbcore: registered new interface driver hiddev
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.451188] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7.4/5-7.4:1.0/input/input2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477229] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.7-7.4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477243] usbcore: registered new interface driver usbhid
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477246] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.651438] Attempting manual resume
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.665923] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.665926] EXT3-fs: write access will be enabled during recovery.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   28.842955] kjournald starting.  Commit interval 5 seconds
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820060] EXT3-fs: sda5: orphan cleanup on readonly fs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820139] EXT3-fs: sda5: 4 orphan inodes deleted
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820141] EXT3-fs: recovery complete.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.842508] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.447479] scsi 2:0:0:0: Direct-Access     HP       Officejet Pro L7 1.00 PQ: 0 ANSI: 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449086] sd 2:0:0:0: [sdb] 4030462 512-byte hardware sectors (2064 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449576] sd 2:0:0:0: [sdb] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452333] sd 2:0:0:0: [sdb] 4030462 512-byte hardware sectors (2064 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452832] sd 2:0:0:0: [sdb] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452840]  sdb: unknown partition table
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.480630] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.480665] sd 2:0:0:0: Attached scsi generic sg2 type 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.268648] input: PC Speaker as /devices/platform/pcspkr/input/input3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.582685] Linux agpgart interface v0.102
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.679519] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.720680] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.714994] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.749925] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.805533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.084818] ACPI: Battery Slot [BAT0] (battery present)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.137609] input: Lid Switch as /devices/virtual/input/input5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.151570] ACPI: Lid Switch [LID]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.151634] input: Power Button (CM) as /devices/virtual/input/input6
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.215113] ACPI: Power Button (CM) [PBTN]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.215182] input: Sleep Button (CM) as /devices/virtual/input/input7
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.279068] ACPI: Sleep Button (CM) [SBTN]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.279189] ACPI: WMI-Acer: Mapper loaded
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480287] ricoh-mmc: Ricoh MMC Controller disabling driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480291] ricoh-mmc: Copyright(c) Philip Langdale
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480327] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480340] ricoh-mmc: Controller is now disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.492423] ACPI: AC Adapter [AC] (on-line)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.586339] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input8
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.646896] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.654652] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.678894] iTCO_vendor_support: vendor-support=0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699041] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699141] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699178] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.710873] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.711027] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input10
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.758842] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871682] sdhci: Secure Digital Host Controller Interface driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871687] sdhci: Copyright(c) Pierre Ossman
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871727] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871754] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871822] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.911649] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.937460] [fglrx] Maximum main memory to use for locked dma buffers: 3145 MBytes.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.937500] [fglrx] ASYNCIO init succeed!
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.938574] [fglrx] PAT is enabled successfully!
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.938598] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.421135] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2212
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.421155] usbcore: registered new interface driver usblp
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.463686] usbcore: registered new interface driver lmpcm_usb
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.463691] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.805519] b43-phy0: Broadcom 4311 WLAN found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   40.931234] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.521143] lp: driver loaded but no devices found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.679456] Adding 8434084k swap on /dev/sda6.  Priority:-1 extents:1 across:8434084k
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   40.205067] EXT3 FS on sda5, internal journal
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.467740] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.881194] No dock devices found.
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.286650] apm: BIOS not found.
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.554075] ppdev: user-space parallel port driver
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.772064] audit(1220384831.500:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5273 profile="/usr/sbin/cupsd" namespace="default"
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829954] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   47.155794] tun: Universal TUN/TAP device driver, 1.6
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   47.155803] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  2 15:47:15 lee-laptop-ub-linux dhcdbd: Started up.
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.733497] Bluetooth: Core ver 2.11
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.756789] input: b43-phy0 as /devices/virtual/input/input11
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757090] NET: Registered protocol family 31
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757096] Bluetooth: HCI device and connection manager initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757103] Bluetooth: HCI socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.786223] Bluetooth: L2CAP ver 2.9
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.786233] Bluetooth: L2CAP socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863140] Bluetooth: RFCOMM socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863154] Bluetooth: RFCOMM TTY layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863156] Bluetooth: RFCOMM ver 1.8
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348801] Registered led device: b43-phy0:tx
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348829] Registered led device: b43-phy0:rx
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348855] Registered led device: b43-phy0:radio
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   52.574360] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   54.883693] b44: eth0: Link is up at 100 Mbps, full duplex.
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   54.883698] b44: eth0: Flow control is off for TX and off for RX.
Sep  2 15:47:21 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934401] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934411] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934416] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
Sep  2 15:47:23 lee-laptop-ub-linux kernel: [   55.738931] NET: Registered protocol family 17
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.064125] NET: Registered protocol family 10
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.064655] lo: Disabled Privacy Extensions
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.068392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  2 15:58:17 lee-laptop-ub-linux syslogd 1.5.0#1ubuntu1: restart.
Sep  2 15:58:18 lee-laptop-ub-linux kernel: Inspecting /boot/System.map-2.6.24-19-generic

SYSSLOG-----------------------------------------

Sep  2 15:38:17 lee-laptop-ub-linux -- MARK --
Sep  2 15:46:21 lee-laptop-ub-linux gnome-power-manager: (lee) GNOME interactive logout. Reason: The power button has been pressed.
Sep  2 15:47:10 lee-laptop-ub-linux syslogd 1.5.0#1ubuntu1: restart.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Symbols match kernel version 2.6.24.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: Loaded 24943 symbols from 100 modules.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfed3400 (usable)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000cfed3400 - 00000000d0000000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] 2430MB HIGHMEM available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] 896MB LOWMEM available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Entering add_active_range(0, 0, 851667) 0 entries of 256 used
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Zone PFN ranges:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   DMA             0 ->     4096
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   Normal       4096 ->   229376
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   HighMem    229376 ->   851667
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Movable zone start PFN for each node
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]     0:        0 ->   851667
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] On node 0 totalpages: 851667
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   HighMem zone: 4861 pages used for memmap
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   HighMem zone: 617430 pages, LIFO batch:31
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] DMI 2.4 present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: RSDT CFED39CD, 0040 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: FACP CFED4800, 0074 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: DSDT CFED5400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: FACS CFEE3C00, 0040
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: HPET CFED4F00, 0038 (r1 DELL    M07            1 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: APIC CFED5000, 0068 (r1 DELL    M07     27D70205 ASL        47)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: MCFG CFED4FC0, 003E (r16 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: SLIC CFED509C, 0176 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: BOOT CFED4BC0, 0028 (r1 DELL    M07     27D70205 ASL        61)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: SSDT CFED3A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Processor #0 6:14 APIC version 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Processor #1 6:14 APIC version 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Allocating PCI resources starting at d2000000 (gap: d0000000:20000000)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845014
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Kernel command line: root=UUID=2ddf34a7-c94d-48bf-b1cd-15c9ecd19f55 ro quiet splash
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Initializing CPU#0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [    0.000000] Detected 1729.063 MHz processor.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706529] Console: colour VGA+ 80x25
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706533] console [tty0] enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.706842] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.707228] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947556] Memory: 3366388k/3406668k available (2177k kernel code, 38972k reserved, 1006k data, 368k init, 2489164k highmem)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947565] virtual kernel memory layout:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947566]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947567]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947568]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947570]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947571]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947572]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947573]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947577] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947618] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   18.947765] hpet clockevent registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027739] Calibrating delay using timer specific routine.. 3462.05 BogoMIPS (lpj=6924106)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027762] Security Framework initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027770] SELinux:  Disabled at boot.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027785] AppArmor: AppArmor initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027789] Failure registering capabilities with primary security module.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027798] Mount-cache hash table entries: 512
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027928] Initializing cgroup subsys ns
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027933] Initializing cgroup subsys cpuacct
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027943] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027951] monitor/mwait feature present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027953] using mwait in idle threads.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027957] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027960] CPU: L2 cache: 2048K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027963] CPU: Physical Processor ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027964] CPU: Processor Core ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027966] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027977] Compat vDSO mapped to ffffe000.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.027989] Checking 'hlt' instruction... OK.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.044126] SMP alternatives: switching to UP code
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.045908] Early unpacking initramfs... done
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.396930] ACPI: Core revision 20070126
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.396986] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.399715] CPU0: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.399732] SMP alternatives: switching to SMP code
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.400403] Booting processor 1/1 eip 3000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.435279] Initializing CPU#1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514458] Calibrating delay using timer specific routine.. 3458.08 BogoMIPS (lpj=6916166)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514465] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000 00000000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514471] monitor/mwait feature present.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514474] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514476] CPU: L2 cache: 2048K
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514478] CPU: Physical Processor ID: 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514480] CPU: Processor Core ID: 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.514481] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000 00000000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492091] CPU1: Intel(R) Core(TM) Duo CPU      T2250  @ 1.73GHz stepping 0c
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492114] Total of 2 processors activated (6920.13 BogoMIPS).
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492314] ENABLING IO-APIC IRQs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.492509] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.639588] checking TSC synchronization [CPU#0 -> CPU#1]:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659587] Measured 3499110940 cycles TSC warp between CPUs, turning off TSC clock.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659590] Marking TSC unstable due to: check_tsc_sync_source failed.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659603] Brought up 2 CPUs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659629] CPU0 attaching sched-domain:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659632]  domain 0: span 03
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659634]   groups: 01 02
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659637] CPU1 attaching sched-domain:
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659639]  domain 0: span 03
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.659641]   groups: 02 01
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.682816] net_namespace: 64 bytes
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.682826] Booting paravirtualized kernel on bare hardware
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683295] Time: 15:46:47  Date: 09/02/08
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683324] NET: Registered protocol family 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683546] EISA bus registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.683551] ACPI: bus type pci registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712285] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712287] PCI: Using configuration type 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.712302] Setting up standard PCI resources
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.694986] ACPI: EC: Look up EC in DSDT
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699905] ACPI: Interpreter enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699909] ACPI: (supports S0 S3 S4 S5)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.699922] ACPI: Using IOAPIC for interrupt routing
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.713685] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.714433] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.714438] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716115] PCI: Transparent bridge - 0000:00:1e.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.716948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.724832] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.724942] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725049] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725156] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725264] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725374] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725485] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725594] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725746] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725780] pnp: PnP ACPI init
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.725788] ACPI: bus type pnp registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.742058] pnpacpi: exceeded the max number of mem resources: 12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754700] pnp: PnP ACPI: found 12 devices
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754703] ACPI: ACPI bus type pnp unregistered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.754706] PnPBIOS: Disabled by ACPI PNP
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.777879] PCI: Using ACPI for IRQ routing
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.777882] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854449] NET: Registered protocol family 8
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854451] NET: Registered protocol family 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.854493] hpet0: 3 64-bit timers, 14318180 Hz
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.855527] AppArmor: AppArmor Filesystem Enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.835392] Time: hpet clocksource has been installed.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.835410] Switched to high resolution mode on CPU 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.858447] Switched to high resolution mode on CPU 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848389] system 00:00: iomem range 0x0-0x9fbff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848393] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848396] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848399] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848402] system 00:00: iomem range 0x100000-0xcfed33ff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848406] system 00:00: iomem range 0xcfed3400-0xcfefffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848409] system 00:00: iomem range 0xcff00000-0xcfffffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848412] system 00:00: iomem range 0xffb00000-0xffffffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848415] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848419] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848422] system 00:00: iomem range 0xfed20000-0xfed9ffff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848425] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848432] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848435] system 00:02: ioport range 0x1000-0x1005 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848438] system 00:02: ioport range 0x1008-0x100f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848444] system 00:03: ioport range 0xf400-0xf4fe has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848447] system 00:03: ioport range 0x1006-0x1007 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848450] system 00:03: ioport range 0x100a-0x1059 could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848453] system 00:03: ioport range 0x1060-0x107f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848456] system 00:03: ioport range 0x1080-0x10bf has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848459] system 00:03: ioport range 0x10c0-0x10df has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848462] system 00:03: ioport range 0x1010-0x102f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848465] system 00:03: ioport range 0x809-0x809 has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848473] system 00:08: ioport range 0xc80-0xcff could not be reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848476] system 00:08: ioport range 0x910-0x91f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848479] system 00:08: ioport range 0x920-0x92f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848482] system 00:08: ioport range 0xcb0-0xcbf has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848484] system 00:08: ioport range 0x930-0x97f has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.848495] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878955] PCI: Bridge: 0000:00:01.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878958]   IO window: e000-efff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878962]   MEM window: efd00000-efefffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878965]   PREFETCH window: d0000000-dfffffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878969] PCI: Bridge: 0000:00:1c.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878971]   IO window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878976]   MEM window: efc00000-efcfffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878981]   PREFETCH window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878987] PCI: Bridge: 0000:00:1c.3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878990]   IO window: d000-dfff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.878996]   MEM window: efa00000-efbfffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879001]   PREFETCH window: e0000000-e01fffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879007] PCI: Bridge: 0000:00:1e.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879009]   IO window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879014]   MEM window: ef900000-ef9fffff
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879019]   PREFETCH window: disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879037] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879043] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879066] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879072] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879097] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879103] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879117] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.879128] NET: Registered protocol family 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.923371] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.923601] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924305] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924656] TCP: Hash tables configured (established 131072 bind 65536)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.924658] TCP reno registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   19.935458] checking if image is initramfs... it is
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.630969] Freeing initrd memory: 7324k freed
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.631143] Simple Boot Flag at 0x79 set to 0x1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.654788] audit: initializing netlink socket (disabled)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.654801] audit(1220370407.560:1): initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.632168] highmem bounce pool size: 64 pages
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634297] VFS: Disk quotas dquot_6.5.1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634375] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634510] io scheduler noop registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634512] io scheduler anticipatory registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634515] io scheduler deadline registered
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634526] io scheduler cfq registered (default)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634635] Boot video device is 0000:01:00.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634756] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634794] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634826] Allocate Port Service[0000:00:01.0:pcie00]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634911] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.634969] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635027] Allocate Port Service[0000:00:1c.0:pcie00]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635066] Allocate Port Service[0000:00:1c.0:pcie02]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635172] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635231] assign_interrupt_mode Found MSI capability
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635277] Allocate Port Service[0000:00:1c.3:pcie00]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635313] Allocate Port Service[0000:00:1c.3:pcie02]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.635601] isapnp: Scanning for PnP cards...
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   20.990460] isapnp: No Plug & Play device found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.019931] Real Time Clock Driver v1.12ac
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.020089] hpet_resources: 0xfed00000 is busy
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.020143] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021399] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021473] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.021575] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.024509] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.024514] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.042890] mice: PS/2 mouse device common for all mice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043016] EISA: Probing bus 0 at eisa.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043025] Cannot allocate resource for EISA slot 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043055] EISA: Detected 0 cards.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043058] cpuidle: using governor ladder
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043060] cpuidle: using governor menu
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043148] NET: Registered protocol family 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043175] Using IPI No-Shortcut mode
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043212] registered taskstats version 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043324]   Magic number: 8:992:789
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043409] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043411] EDD information not available.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   21.043617] Freeing unused kernel memory: 368k freed
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.068908] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.283229] fuse init (API version 7.9)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.301282] ACPI: SSDT CFED4134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.301476] ACPI: SSDT CFED3EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279150] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279156] ACPI: Processor [CPU0] (supports 8 throttling states)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279388] ACPI: SSDT CFED4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.279570] ACPI: SSDT CFED40AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.303143] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.303148] ACPI: Processor [CPU1] (supports 8 throttling states)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.308284] ACPI: Thermal Zone [THM] (51 C)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.648337] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.648360] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670104] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670128] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670147] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.670166] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.692224] usbcore: registered new interface driver usbfs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.692248] usbcore: registered new interface driver hub
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.696756] usbcore: registered new device driver usb
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.698558] USB Universal Host Controller Interface driver v3.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714156] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714211] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714223] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714227] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714493] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714528] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714663] usb usb1: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714689] hub 1-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.714695] hub 1-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.764802] SCSI subsystem initialized
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818059] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818073] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818078] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818101] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818135] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818253] usb usb2: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818276] hub 2-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.818282] hub 2-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   22.852461] libata version 3.00 loaded.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944955] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944969] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944974] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.944999] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945033] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945152] usb usb3: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945176] hub 3-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.945181] hub 3-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045897] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045910] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045914] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045938] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.045971] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046089] usb usb4: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046115] hub 4-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.046120] hub 4-0:1.0: 2 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.126986] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.127001] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.127006] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.127033] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.130961] ehci_hcd 0000:00:1d.7: debug port 1
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.130968] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.130976] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149815] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149945] usb usb5: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149970] hub 5-0:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.149976] hub 5-0:1.0: 8 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.253983] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.306771] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.310887] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333763] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333771] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.333779] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393701] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393726] b44.c:v2.0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393755] ata_piix 0000:00:1f.2: version 2.12
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393761] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393791] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393827] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393902] scsi0 : ata_piix
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.393950] scsi1 : ata_piix
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.394730] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.394733] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.412995] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:68:2e:68
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.564574] usb 5-7: new high speed USB device using ehci_hcd and address 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.573547] ata1.00: ATA-8: WDC WD3200BEVT-00ZCT0, 11.01A11, max UDMA/133
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.573551] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.591131] ata1.00: configured for UDMA/133
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674034] usb 5-7: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674200] hub 5-7:1.0: USB hub found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.674300] hub 5-7:1.0: 4 ports detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   25.956916] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   23.993560] usb 5-7.1: new high speed USB device using ehci_hcd and address 3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.086360] usb 5-7.1: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.148731] ata2.00: configured for UDMA/33
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.125983] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 11.0 PQ: 0 ANSI: 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.134547] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167683] Driver 'sd' needs updating - please use bus_type methods
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167762] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167775] sd 0:0:0:0: [sda] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167778] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167849] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167860] sd 0:0:0:0: [sda] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167883] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.167887]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.196241]  sda1 sda2 < sda5 sda6 >
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.225454] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.231036] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.231057] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.290356] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.290361] Uniform CD-ROM driver Revision: 3.20
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.290415] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.302419] usb 5-7.4: new low speed USB device using ehci_hcd and address 4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.418721] usb 5-7.4: configuration #1 chosen from 1 choice
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.442614] usbcore: registered new interface driver libusual
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.448622] Initializing USB Mass Storage driver...
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.449847] scsi2 : SCSI emulation for USB Mass Storage devices
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450329] usbcore: registered new interface driver usb-storage
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450333] USB Mass Storage support registered.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450418] usb-storage: device found at 3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.450420] usb-storage: waiting for device to settle before scanning
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.466039] usbcore: registered new interface driver hiddev
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.451188] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7.4/5-7.4:1.0/input/input2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477229] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.7-7.4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477243] usbcore: registered new interface driver usbhid
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.477246] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.605411] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[324fc00024336161]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.651438] Attempting manual resume
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.651442] swsusp: Resume From Partition 8:6
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.651444] PM: Checking swsusp image.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.651660] PM: Resume from disk failed.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.665923] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   24.665926] EXT3-fs: write access will be enabled during recovery.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   28.842955] kjournald starting.  Commit interval 5 seconds
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820060] EXT3-fs: sda5: orphan cleanup on readonly fs
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820067] ext3_orphan_cleanup: deleting unreferenced inode 12402784
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820099] ext3_orphan_cleanup: deleting unreferenced inode 12402783
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820111] ext3_orphan_cleanup: deleting unreferenced inode 7062262
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820132] ext3_orphan_cleanup: deleting unreferenced inode 12402704
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820139] EXT3-fs: sda5: 4 orphan inodes deleted
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.820141] EXT3-fs: recovery complete.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   26.842508] EXT3-fs: mounted filesystem with ordered data mode.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   29.424078] usb-storage: device scan complete
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.447479] scsi 2:0:0:0: Direct-Access     HP       Officejet Pro L7 1.00 PQ: 0 ANSI: 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449086] sd 2:0:0:0: [sdb] 4030462 512-byte hardware sectors (2064 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449576] sd 2:0:0:0: [sdb] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449582] sd 2:0:0:0: [sdb] Mode Sense: 17 00 00 08
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.449588] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452333] sd 2:0:0:0: [sdb] 4030462 512-byte hardware sectors (2064 MB)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452832] sd 2:0:0:0: [sdb] Write Protect is off
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452835] sd 2:0:0:0: [sdb] Mode Sense: 17 00 00 08
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452837] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.452840]  sdb: unknown partition table
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.480630] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   31.480665] sd 2:0:0:0: Attached scsi generic sg2 type 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.268648] input: PC Speaker as /devices/platform/pcspkr/input/input3
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.582685] Linux agpgart interface v0.102
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.679519] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.720680] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.714994] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.749925] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.805533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   36.884302] intel_rng: FWH not detected
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.084818] ACPI: Battery Slot [BAT0] (battery present)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.137609] input: Lid Switch as /devices/virtual/input/input5
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.151570] ACPI: Lid Switch [LID]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.151634] input: Power Button (CM) as /devices/virtual/input/input6
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.215113] ACPI: Power Button (CM) [PBTN]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.215182] input: Sleep Button (CM) as /devices/virtual/input/input7
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.279068] ACPI: Sleep Button (CM) [SBTN]
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.279189] ACPI: WMI-Acer: Mapper loaded
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480287] ricoh-mmc: Ricoh MMC Controller disabling driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480291] ricoh-mmc: Copyright(c) Philip Langdale
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480327] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 1)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.480340] ricoh-mmc: Controller is now disabled.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.492423] ACPI: AC Adapter [AC] (on-line)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.586339] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input8
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.646896] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.654652] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.678894] iTCO_vendor_support: vendor-support=0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699041] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699141] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.699178] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.710873] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.711027] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input10
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.758842] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871682] sdhci: Secure Digital Host Controller Interface driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871687] sdhci: Copyright(c) Pierre Ossman
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871727] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871754] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   37.871822] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.911649] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.937460] [fglrx] Maximum main memory to use for locked dma buffers: 3145 MBytes.
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.937500] [fglrx] ASYNCIO init succeed!
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.938574] [fglrx] PAT is enabled successfully!
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.938598] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.421135] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2212
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.421155] usbcore: registered new interface driver usblp
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.463686] usbcore: registered new interface driver lmpcm_usb
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.463691] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.805519] b43-phy0: Broadcom 4311 WLAN found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.846335] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.846364] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   38.878862] phy0: Selected rate control algorithm 'simple'
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   40.931234] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   40.931260] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   39.521143] lp: driver loaded but no devices found
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.679456] Adding 8434084k swap on /dev/sda6.  Priority:-1 extents:1 across:8434084k
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   40.205067] EXT3 FS on sda5, internal journal
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.467740] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep  2 15:47:10 lee-laptop-ub-linux kernel: [   41.881194] No dock devices found.
Sep  2 15:47:10 lee-laptop-ub-linux NetworkManager: <info>  starting... 
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Successfully dropped root privileges.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: avahi-daemon 0.6.22 starting up.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Successfully called chroot().
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Successfully dropped remaining capabilities.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: No service file found in /etc/avahi/services.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Network interface enumeration completed.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Registering HINFO record with values 'I686'/'LINUX'.
Sep  2 15:47:10 lee-laptop-ub-linux avahi-daemon[5216]: Server startup complete. Host name is lee-laptop-ub-linux.local. Local service cookie is 2595704930.
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.286650] apm: BIOS not found.
Sep  2 15:47:11 lee-laptop-ub-linux atieventsd[5246]: ATI External Events Daemon started... 
Sep  2 15:47:11 lee-laptop-ub-linux atieventsd[5246]: Event daemon control socket created 
Sep  2 15:47:11 lee-laptop-ub-linux atieventsd[5246]: acpid connection established 
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.554075] ppdev: user-space parallel port driver
Sep  2 15:47:11 lee-laptop-ub-linux kernel: [   43.772064] audit(1220384831.500:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5273 profile="/usr/sbin/cupsd" namespace="default"
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829835] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829846] vboxdrv: Successfully done.
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829850] vboxdrv: Found 2 processor cores.
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829882] vboxdrv: fAsync=1 u64DiffCores=3499114918.
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829954] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   46.829959] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   47.155794] tun: Universal TUN/TAP device driver, 1.6
Sep  2 15:47:14 lee-laptop-ub-linux kernel: [   47.155803] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  2 15:47:15 lee-laptop-ub-linux dhcdbd: Started up.
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  eth0: Device is fully-supported using driver '(null)'. 
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Sep  2 15:47:17 lee-laptop-ub-linux NetworkManager: <info>  Deactivating device eth0. 
Sep  2 15:47:17 lee-laptop-ub-linux hcid[5649]: Bluetooth HCI daemon
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.733497] Bluetooth: Core ver 2.11
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.756789] input: b43-phy0 as /devices/virtual/input/input11
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757090] NET: Registered protocol family 31
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757096] Bluetooth: HCI device and connection manager initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   51.757103] Bluetooth: HCI socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux hcid[5649]: Starting SDP server
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.786223] Bluetooth: L2CAP ver 2.9
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.786233] Bluetooth: L2CAP socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux hcid[5649]: Created local server at unix:abstract=/var/run/dbus-403RkTGs81,guid=14f3b39cfae40f68e2970fd748bd9845
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: Bluetooth Audio daemon
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: Unix socket created: 5
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: audio.conf: Key file does not have key 'Enable'
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: audio.conf: Key file does not have key 'Disable'
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863140] Bluetooth: RFCOMM socket layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863154] Bluetooth: RFCOMM TTY layer initialized
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   49.863156] Bluetooth: RFCOMM ver 1.8
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: add_service_record: got record id 0x10000
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: audio.conf: Key file does not have key 'Disable'
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: audio.conf: Key file does not have group 'A2DP'
Sep  2 15:47:17 lee-laptop-ub-linux last message repeated 3 times
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: SEP 0x806d748 registered: type:0 codec:0 seid:1
Sep  2 15:47:17 lee-laptop-ub-linux input[5677]: Bluetooth Input daemon
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: add_service_record: got record id 0x10001
Sep  2 15:47:17 lee-laptop-ub-linux input[5677]: Registered input manager path:/org/bluez/input
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: add_service_record: got record id 0x10002
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: add_service_record: got record id 0x10003
Sep  2 15:47:17 lee-laptop-ub-linux audio[5676]: Registered manager path:/org/bluez/audio
Sep  2 15:47:17 lee-laptop-ub-linux kernel: [   50.028404] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
Sep  2 15:47:18 lee-laptop-ub-linux hal_lpadmin: add
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.328979] b43-phy0 debug: Chip initialized
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.329239] b43-phy0 debug: 32-bit DMA initialized
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348801] Registered led device: b43-phy0:tx
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348829] Registered led device: b43-phy0:rx
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348855] Registered led device: b43-phy0:radio
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.348940] b43-phy0 debug: Wireless interface started
Sep  2 15:47:19 lee-laptop-ub-linux kernel: [   51.388826] b43-phy0 debug: Adding Interface type 2
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  wlan0: Device is fully-supported using driver '(null)'. 
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Sep  2 15:47:19 lee-laptop-ub-linux NetworkManager: <info>  Deactivating device wlan0. 
Sep  2 15:47:19 lee-laptop-ub-linux hal_lpadmin: URIs: ['hp:/usb/Officejet_Pro_L7600?serial=MY726250P9', 'usb://HP/Officejet%20Pro%20L7600?serial=MY726250P9', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_2212_MY726250P9_if1_printer_MY726250P9']
Sep  2 15:47:19 lee-laptop-ub-linux hal_lpadmin: HPLIP Fax URIs: ['hpfax:/usb/Officejet_Pro_L7600?serial=MY726250P9']
Sep  2 15:47:19 lee-laptop-ub-linux hal_lpadmin: Not adding printer: Officejet_Pro_L7600 already exists
Sep  2 15:47:19 lee-laptop-ub-linux hal_lpadmin: Not adding fax printer: Officejet_Pro_L7600_fax already exists
Sep  2 15:47:20 lee-laptop-ub-linux anacron[5786]: Anacron 2.3 started on 2008-09-02
Sep  2 15:47:20 lee-laptop-ub-linux anacron[5786]: Normal exit (0 jobs run)
Sep  2 15:47:20 lee-laptop-ub-linux /usr/sbin/cron[5813]: (CRON) INFO (pidfile fd = 3)
Sep  2 15:47:20 lee-laptop-ub-linux /usr/sbin/cron[5814]: (CRON) STARTUP (fork ok)
Sep  2 15:47:20 lee-laptop-ub-linux /usr/sbin/cron[5814]: (CRON) INFO (Running @reboot jobs)
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   52.574360] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   54.883693] b44: eth0: Link is up at 100 Mbps, full duplex.
Sep  2 15:47:20 lee-laptop-ub-linux kernel: [   54.883698] b44: eth0: Flow control is off for TX and off for RX.
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <debug> [1220384841.150551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <debug> [1220384841.151441] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_6'). 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <debug> [1220384841.151845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_2212_MY726250P9_if1_printer_MY726250P9'). 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep  2 15:47:21 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Will activate connection 'eth0'. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Device eth0 activation scheduled... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) started... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Sep  2 15:47:21 lee-laptop-ub-linux NetworkManager: <info>  Wireless now enabled by radio killswitch 
Sep  2 15:47:22 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep  2 15:47:22 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep  2 15:47:22 lee-laptop-ub-linux NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep  2 15:47:22 lee-laptop-ub-linux dhclient: wmaster0: unknown hardware address type 801
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934401] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934411] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Sep  2 15:47:22 lee-laptop-ub-linux kernel: [   54.934416] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
Sep  2 15:47:23 lee-laptop-ub-linux dhclient: wmaster0: unknown hardware address type 801
Sep  2 15:47:23 lee-laptop-ub-linux NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep  2 15:47:23 lee-laptop-ub-linux kernel: [   55.738931] NET: Registered protocol family 17
Sep  2 15:47:26 lee-laptop-ub-linux dhclient: DHCPREQUEST of 10.1.10.158 on eth0 to 255.255.255.255 port 67
Sep  2 15:47:27 lee-laptop-ub-linux dhclient: DHCPACK of 10.1.10.158 from 10.1.10.1
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.10.158.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: New relevant interface eth0.IPv4 for mDNS.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Registering new address record for 10.1.10.158 on eth0.IPv4.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Withdrawing address record for 10.1.10.158 on eth0.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.10.158.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.10.158.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: New relevant interface eth0.IPv4 for mDNS.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Registering new address record for 10.1.10.158 on eth0.IPv4.
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Sep  2 15:47:27 lee-laptop-ub-linux dhclient: bound to 10.1.10.158 -- renewal in 231288 seconds.
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    address 10.1.10.158 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    netmask 255.255.255.0 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    broadcast 10.1.10.255 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    gateway 10.1.10.1 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    nameserver 68.87.64.146 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    nameserver 68.87.75.194 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>    domain name 'wp.comcast.net' 
Sep  2 15:47:27 lee-laptop-ub-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Sep  2 15:47:27 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Withdrawing address record for 10.1.10.158 on eth0.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.1.10.158.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.1.10.158.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: New relevant interface eth0.IPv4 for mDNS.
Sep  2 15:47:27 lee-laptop-ub-linux avahi-daemon[5216]: Registering new address record for 10.1.10.158 on eth0.IPv4.
Sep  2 15:47:28 lee-laptop-ub-linux NetworkManager: <info>  Clearing nscd hosts cache. 
Sep  2 15:47:28 lee-laptop-ub-linux NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Sep  2 15:47:28 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) successful, device activated. 
Sep  2 15:47:28 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Sep  2 15:47:28 lee-laptop-ub-linux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.064125] NET: Registered protocol family 10
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.064655] lo: Disabled Privacy Extensions
Sep  2 15:47:28 lee-laptop-ub-linux kernel: [   63.068392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  2 15:47:29 lee-laptop-ub-linux ntpdate[6062]: step time server 91.189.94.4 offset 1.091156 sec
Sep  2 15:47:31 lee-laptop-ub-linux avahi-daemon[5216]: Registering new address record for fe80::219:b9ff:fe68:2e68 on eth0.*.
Sep  2 15:47:40 lee-laptop-ub-linux kernel: [   73.370620] eth0: no IPv6 routers present
Sep  2 15:47:43 lee-laptop-ub-linux hcid[5649]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Sep  2 15:47:43 lee-laptop-ub-linux hcid[5649]: Default authorization agent (:1.22, /org/bluez/auth) registered
Sep  2 15:47:47 lee-laptop-ub-linux NetworkManager: <info>  Updating allowed wireless network lists. 
Sep  2 15:47:53 lee-laptop-ub-linux anacron[6368]: Anacron 2.3 started on 2008-09-02
Sep  2 15:47:53 lee-laptop-ub-linux anacron[6368]: Normal exit (0 jobs run)
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.960561] CPU0 attaching NULL sched-domain.
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.960569] CPU1 attaching NULL sched-domain.
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976231] CPU0 attaching sched-domain:
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976237]  domain 0: span 03
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976240]   groups: 01 02
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976248] CPU1 attaching sched-domain:
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976253]  domain 0: span 03
Sep  2 15:47:53 lee-laptop-ub-linux kernel: [   84.976256]   groups: 02 01
Sep  2 15:48:00 lee-laptop-ub-linux hald: mounted /dev/sdb on behalf of uid 1000
Sep  2 15:58:17 lee-laptop-ub-linux syslogd 1.5.0#1ubuntu1: restart.

---


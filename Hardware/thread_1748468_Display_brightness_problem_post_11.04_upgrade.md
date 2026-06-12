---
title: "Display brightness: problem post 11.04 upgrade"
date: 2011-05-03
forum: Hardware
---

### Post by tornadof3 on 2011-05-03
So I upgraded to 11.04 using the synaptic package manager upgrade feature...

I have googled this problem and there is a lot of help available but none of a recent date and I never had this problem with Ubuntu 10.10 etc...

I have a HP 6735s laptop with the ATI 3200 graphics card. I have (re)installed the ATI flgrx additional graphics drivers etc. No fix:

The gnome display applet reads "Cannot get laptop panel brightness" and the Fn + F7/F8 buttons no longer work (they did on 10.10). My screen is very dim - almost unreadable.

I know variations on this question have been asked by many users, but all posts seem quite old and not related to my problem. Any ideas? Thanks for any help.

---

### Post by frozenfiree on 2011-05-04
Hello,
i had the same problem and it seems to be a problem of the new kernel and ati driver. To solve it you just have to add ```
nomodeset acpi_backlight=vendor
``` to the GRUB_CMDLINE_LINUX_DEFAULT  string in /etc/default/grub.

Looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```

After that you need to update the grub -> ```
sudo update-grub
```

After reboot it should be normal.

worked in my case

Greets,
ff

---

### Post by tornadof3 on 2011-05-05
Thank you for replying. I did this unfortunately it hasn't solved the problem... do you also have the HP 6735s laptop or is yours a bit different? I have included the contents of /etc/default/grub below to ensure I have ammended as per your suggestion and I have run sudo update-grub and rebooted

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by tornadof3 on 2011-05-07
Whilst not a solution to the problem, I have found a work around to the dim screen - the Fn + brightness keys DO work at the BIOS screen and grub OS selection screen, so I set the screen to bright and then continue the boot process and the screen remains bright (although the panel applet still cannot detect/adjust brightness)

---

### Post by frozenfiree on 2011-05-08
yes same hardware.

can you look in your /boot/grub/grub.cfg.

The part beneath ```
menuentry 'Ubuntu, with Linux 2.6.38-8-generic'
```. Is there ```
quiet splash nomodeset acpi_backlight=vendor
```?

greets,
ff

---

### Post by tornadof3 on 2011-05-08
Yes that entry is there

---

### Post by frozenfiree on 2011-05-08
did you install the ati driver?

K-Menu->Application->System->Additional Drivers

---

### Post by tornadof3 on 2011-05-08
Yep; ati driver installed and working

---

### Post by frozenfiree on 2011-05-08
what says dmesg?

---

### Post by tornadof3 on 2011-05-08
dmesg says quite a lot. How much should it say?

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=/dev/mapper/hp--laptop-root ro nomodeset acpi_backlight=vendor
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000acb70000 (usable)
[    0.000000]  BIOS-e820: 00000000acb70000 - 00000000acb80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000acb80000 - 00000000afd4f000 (usable)
[    0.000000]  BIOS-e820: 00000000afd4f000 - 00000000afdcf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdcf000 - 00000000afecf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afecf000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq 6735s/30E4, BIOS 68GPP Ver. F.06 10/02/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 0100000000 mask FFC0000000 write-back
[    0.000000]   4 base 00FFE00000 mask FFFFE00000 write-protect
[    0.000000]   5 base 00FFF40000 mask FFFFFF0000 write-protect
[    0.000000]   6 base 00ACB70000 mask FFFFFF0000 uncachable
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000140000000 aka 5120M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000aff00000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00aff00000 page 4k
[    0.000000] kernel direct mapping tables up to aff00000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ afd49000-afd4f000
[    0.000000] RAMDISK: 359b2000 - 36cd1000
[    0.000000] ACPI: RSDP 00000000000f68b0 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 00000000afefe038 0003C (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP 00000000afefd000 00074 (v01 HP     0944     00000003 HP   00000001)
[    0.000000] ACPI: DSDT 00000000afee5000 1475B (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: FACS 00000000afea1000 00040
[    0.000000] ACPI: APIC 00000000afefc000 00084 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 00000000afefb000 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SLIC 00000000afefa000 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: HPET 00000000afee3000 00038 (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 00000000afee2000 002B4 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000013fffb000 - 000000013fffffff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff88013c200000-ffff88013f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000acb70
[    0.000000]     0: 0x000acb80 -> 0x000afd4f
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 982223
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 701816 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000acb70000 - 00000000acb80000
[    0.000000] PM: Registered nosave memory: 00000000afd4f000 - 00000000afdcf000
[    0.000000] PM: Registered nosave memory: 00000000afdcf000 - 00000000afecf000
[    0.000000] PM: Registered nosave memory: 00000000afecf000 - 00000000afeff000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb01000
[    0.000000] PM: Registered nosave memory: 00000000feb01000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800ac800000 s84416 r8192 d22080 u524288
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 964297
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=/dev/mapper/hp--laptop-root ro nomodeset acpi_backlight=vendor
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3774060k/5242880k available (5940k kernel code, 1313988k absent, 154832k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1900.146 MHz processor.
[    0.020006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3800.29 BogoMIPS (lpj=19001460)
[    0.020102] pid_max: default: 32768 minimum: 301
[    0.020187] Security Framework initialized
[    0.020297] AppArmor: AppArmor initialized
[    0.020344] Yama: becoming mindful.
[    0.020997] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.024492] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.025843] Mount-cache hash table entries: 256
[    0.026107] Initializing cgroup subsys ns
[    0.026185] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.026237] Initializing cgroup subsys cpuacct
[    0.026283] Initializing cgroup subsys memory
[    0.026335] Initializing cgroup subsys devices
[    0.026378] Initializing cgroup subsys freezer
[    0.026420] Initializing cgroup subsys net_cls
[    0.026463] Initializing cgroup subsys blkio
[    0.026546] tseg: 00aff00000
[    0.026549] CPU: Physical Processor ID: 0
[    0.026625] CPU: Processor Core ID: 0
[    0.026667] mce: CPU supports 5 MCE banks
[    0.031595] ACPI: Core revision 20110112
[    0.040018] ftrace: allocating 24314 entries in 96 pages
[    0.050124] Setting APIC routing to flat
[    0.050565] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.153164] CPU0: AMD Athlon(tm)X2 DualCore QL-60 stepping 01
[    0.160000] Performance Events: AMD PMU driver.
[    0.160000] ... version:                0
[    0.160000] ... bit width:              48
[    0.160000] ... generic registers:      4
[    0.160000] ... value mask:             0000ffffffffffff
[    0.160000] ... max period:             00007fffffffffff
[    0.160000] ... fixed-purpose events:   0
[    0.160000] ... event mask:             000000000000000f
[    0.160000] Booting Node   0, Processors  #1
[    0.320000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.320000] Measured 15226347 cycles TSC warp between CPUs, turning off TSC clock.
[    0.320000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.320015] Brought up 2 CPUs
[    0.320056] Total of 2 processors activated (7590.87 BogoMIPS).
[    0.320363] devtmpfs: initialized
[    0.321276] print_constraints: dummy: 
[    0.321381] Time: 18:36:19  Date: 05/08/11
[    0.321477] NET: Registered protocol family 16
[    0.321606] Trying to unpack rootfs image as initramfs...
[    0.321744] TOM: 00000000c0000000 aka 3072M
[    0.321747] Fam 10h mmconf [e0000000, efffffff]
[    0.321756] TOM2: 0000000140000000 aka 5120M
[    0.321882] Extended Config Space enabled on 0 nodes
[    0.321901] ACPI: bus type pci registered
[    0.321999] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.322003] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.360622] PCI: Using configuration type 1 for base access
[    0.361816] bio: create slab <bio-0> at 0
[    0.363568] ACPI: EC: Look up EC in DSDT
[    0.821892] Freeing initrd memory: 19580k freed
[    1.030096] ACPI: Interpreter enabled
[    1.030178] ACPI: (supports S0 S3 S4 S5)
[    1.030376] ACPI: Using IOAPIC for interrupt routing
[    1.033236] ACPI: Power Resource [APPR] (off)
[    1.212085] ACPI: Power Resource [PFN0] (off)
[    1.212226] ACPI: Power Resource [PFN1] (off)
[    1.212367] ACPI: Power Resource [PFN2] (off)
[    1.212504] ACPI: Power Resource [PFN3] (off)
[    1.213243] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    1.213631] ACPI: No dock devices found.
[    1.213707] HEST: Table not found.
[    1.213750] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.213927] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.214258] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    1.214337] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    1.214382] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.215035] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    1.215085] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    1.215134] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    1.215183] pci_root PNP0A03:00: host bridge window [mem 0x000cc000-0x000cffff]
[    1.215233] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.215286] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.215342] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.215396] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.215449] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.215502] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.215557] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    1.215613] pci_root PNP0A03:00: host bridge window [mem 0x000ec000-0x000effff]
[    1.215665] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    1.215720] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfffdffff]
[    1.215775] pci_root PNP0A03:00: host bridge window [mem 0xffe00000-0xffffffff]
[    1.215832] pci_root PNP0A03:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xffe00000-0xffffffff] ignored
[    1.215896] pci_root PNP0A03:00: address space collision: host bridge window [mem 0x000ec000-0x000effff] conflicts with reserved [mem 0x000ef000-0x000fffff]
[    1.215979] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    1.216070] pci 0000:00:01.0: [1022:9602] type 1 class 0x000604
[    1.216176] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    1.216226] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.216231] pci 0000:00:04.0: PME# disabled
[    1.216294] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
[    1.216343] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.216348] pci 0000:00:07.0: PME# disabled
[    1.216409] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
[    1.216463] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.216467] pci 0000:00:09.0: PME# disabled
[    1.216548] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    1.216577] pci 0000:00:11.0: reg 10: [io  0x6018-0x601f]
[    1.216591] pci 0000:00:11.0: reg 14: [io  0x6024-0x6027]
[    1.216604] pci 0000:00:11.0: reg 18: [io  0x6010-0x6017]
[    1.216618] pci 0000:00:11.0: reg 1c: [io  0x6020-0x6023]
[    1.216631] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
[    1.216645] pci 0000:00:11.0: reg 24: [mem 0xd4409000-0xd44093ff]
[    1.216709] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    1.216729] pci 0000:00:12.0: reg 10: [mem 0xd4408000-0xd4408fff]
[    1.216817] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    1.216835] pci 0000:00:12.1: reg 10: [mem 0xd4407000-0xd4407fff]
[    1.216934] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    1.216961] pci 0000:00:12.2: reg 10: [mem 0xd4409500-0xd44095ff]
[    1.217055] pci 0000:00:12.2: supports D1 D2
[    1.217058] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.217063] pci 0000:00:12.2: PME# disabled
[    1.217095] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    1.217112] pci 0000:00:13.0: reg 10: [mem 0xd4406000-0xd4406fff]
[    1.217198] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    1.217218] pci 0000:00:13.1: reg 10: [mem 0xd4405000-0xd4405fff]
[    1.217315] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    1.217341] pci 0000:00:13.2: reg 10: [mem 0xd4409400-0xd44094ff]
[    1.217435] pci 0000:00:13.2: supports D1 D2
[    1.217438] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.217443] pci 0000:00:13.2: PME# disabled
[    1.217481] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    1.217611] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    1.217641] pci 0000:00:14.2: reg 10: [mem 0xd4400000-0xd4403fff 64bit]
[    1.217722] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.217728] pci 0000:00:14.2: PME# disabled
[    1.217747] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    1.217852] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    1.217913] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    1.217932] pci 0000:00:14.5: reg 10: [mem 0xd4404000-0xd4404fff]
[    1.218024] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
[    1.218061] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
[    1.218091] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
[    1.218122] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    1.218158] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
[    1.218277] pci 0000:01:05.0: [1002:9612] type 0 class 0x000300
[    1.218292] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    1.218301] pci 0000:01:05.0: reg 14: [io  0x5000-0x50ff]
[    1.218309] pci 0000:01:05.0: reg 18: [mem 0xd4300000-0xd430ffff]
[    1.218327] pci 0000:01:05.0: reg 24: [mem 0xd4200000-0xd42fffff]
[    1.218350] pci 0000:01:05.0: supports D1 D2
[    1.218443] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.218495] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    1.218500] pci 0000:00:01.0:   bridge window [mem 0xd4200000-0xd43fffff]
[    1.218506] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.218593] pci 0000:02:00.0: [11ab:4357] type 0 class 0x000200
[    1.218638] pci 0000:02:00.0: reg 10: [mem 0xd3100000-0xd3103fff 64bit]
[    1.218653] pci 0000:02:00.0: reg 18: [io  0x3000-0x30ff]
[    1.218765] pci 0000:02:00.0: supports D1 D2
[    1.218768] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.218796] pci 0000:02:00.0: PME# disabled
[    2.230004] pci 0000:00:04.0: ASPM: Could not configure common clock
[    2.230108] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.230154] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    2.230158] pci 0000:00:04.0:   bridge window [mem 0xd3100000-0xd41fffff]
[    2.230164] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.230203] pci 0000:00:07.0: PCI bridge to [bus 03-05]
[    2.230283] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    2.230287] pci 0000:00:07.0:   bridge window [mem 0xd2100000-0xd30fffff]
[    2.230293] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.230431] pci 0000:06:00.0: [14e4:4315] type 0 class 0x000280
[    2.230454] pci 0000:06:00.0: reg 10: [mem 0xd2000000-0xd2003fff 64bit]
[    2.230541] pci 0000:06:00.0: supports D1 D2
[    2.250082] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    2.250163] pci 0000:00:09.0:   bridge window [io  0xfffffffffffff000-0x0000] (disabled)
[    2.250168] pci 0000:00:09.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    2.250174] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.250249] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    2.250297] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.250303] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.250309] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.250313] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.250316] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.250320] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.250323] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    2.250327] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    2.250330] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    2.250334] pci 0000:00:14.4:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
[    2.250337] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    2.250341] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    2.250344] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    2.250348] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    2.250351] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    2.250354] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    2.250358] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    2.250362] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    2.250365] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    2.250424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.250515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    2.250569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    2.250635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB9_._PRT]
[    2.250695] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    2.250833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    2.250873]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.258136] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.258661] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.259181] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.259701] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.260261] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.260780] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.261299] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.261819] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    2.262438] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    2.262523] vgaarb: loaded
[    2.262825] SCSI subsystem initialized
[    2.262925] libata version 3.00 loaded.
[    2.262925] usbcore: registered new interface driver usbfs
[    2.262925] usbcore: registered new interface driver hub
[    2.262925] usbcore: registered new device driver usb
[    2.262925] wmi: Mapper loaded
[    2.262925] PCI: Using ACPI for IRQ routing
[    2.262925] PCI: pci_cache_line_size set to 64 bytes
[    2.262925] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    2.262925] reserve RAM buffer: 00000000acb70000 - 00000000afffffff 
[    2.262925] reserve RAM buffer: 00000000afd4f000 - 00000000afffffff 
[    2.262925] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    2.262925] NetLabel: Initializing
[    2.262925] NetLabel:  domain hash size = 128
[    2.262925] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.262925] NetLabel:  unlabeled traffic allowed by default
[    2.262925] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    2.262925] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    2.263709] Switching to clocksource hpet
[    2.263762] Switched to NOHz mode on CPU #0
[    2.263754] Switched to NOHz mode on CPU #1
[    2.270184] AppArmor: AppArmor Filesystem Enabled
[    2.270306] pnp: PnP ACPI init
[    2.270409] ACPI: bus type pnp registered
[    2.270648] pnp 00:00: [bus 00-ff]
[    2.270652] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.270655] pnp 00:00: [io  0x0d00-0xffff window]
[    2.270658] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.270661] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    2.270664] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    2.270667] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    2.270670] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    2.270673] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    2.270677] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    2.270680] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    2.270683] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    2.270686] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    2.270689] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    2.270692] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    2.270695] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    2.270698] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    2.270701] pnp 00:00: [mem 0xf0000000-0xfffdffff window]
[    2.270704] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.270707] pnp 00:00: [mem 0xffe00000-0xffffffff]
[    2.270817] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    2.270975] pnp 00:01: [io  0x0000-0x000f]
[    2.270979] pnp 00:01: [io  0x0081-0x008f]
[    2.270981] pnp 00:01: [io  0x00c0-0x00df]
[    2.270985] pnp 00:01: [dma 4]
[    2.271028] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.271040] pnp 00:02: [io  0x00f0-0x00fe]
[    2.271089] pnp 00:02: [irq 13]
[    2.271135] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.271146] pnp 00:03: [io  0x0061]
[    2.271191] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.271252] pnp 00:04: [io  0x0010-0x001f]
[    2.271255] pnp 00:04: [io  0x002e-0x002f]
[    2.271258] pnp 00:04: [io  0x004e-0x004f]
[    2.271264] pnp 00:04: [io  0x0072-0x0073]
[    2.271267] pnp 00:04: [io  0x0080]
[    2.271269] pnp 00:04: [io  0x00b0-0x00b1]
[    2.271271] pnp 00:04: [io  0x0092]
[    2.271274] pnp 00:04: [io  0x0400-0x04cf]
[    2.271277] pnp 00:04: [io  0x04d0-0x04d1]
[    2.271279] pnp 00:04: [io  0x04d6]
[    2.271282] pnp 00:04: [io  0x0680-0x06ff]
[    2.271284] pnp 00:04: [io  0x077a]
[    2.271286] pnp 00:04: [io  0x0c00-0x0c01]
[    2.271289] pnp 00:04: [io  0x0c14]
[    2.271291] pnp 00:04: [io  0x0c50-0x0c52]
[    2.271294] pnp 00:04: [io  0x0c6c]
[    2.271296] pnp 00:04: [io  0x0c6f]
[    2.271299] pnp 00:04: [io  0x0cd0-0x0cdb]
[    2.271301] pnp 00:04: [io  0x0220-0x0227]
[    2.271304] pnp 00:04: [io  0x0260-0x0273]
[    2.271306] pnp 00:04: [io  0x0800]
[    2.271309] pnp 00:04: [io  0x0804]
[    2.271311] pnp 00:04: [io  0x087f]
[    2.271313] pnp 00:04: [io  0x0cdc-0x0cdf]
[    2.271316] pnp 00:04: [io  0x00b8]
[    2.271318] pnp 00:04: [io  0x0022-0x0023]
[    2.271321] pnp 00:04: [io  0x0b00-0x0b0f]
[    2.271323] pnp 00:04: [io  0x0b20-0x0b3f]
[    2.271326] pnp 00:04: [io  0x0200-0x027f]
[    2.271451] system 00:04: [io  0x0400-0x04cf] has been reserved
[    2.271530] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    2.271574] system 00:04: [io  0x04d6] has been reserved
[    2.271617] system 00:04: [io  0x0680-0x06ff] has been reserved
[    2.271661] system 00:04: [io  0x077a] has been reserved
[    2.271705] system 00:04: [io  0x0c00-0x0c01] has been reserved
[    2.271749] system 00:04: [io  0x0c14] has been reserved
[    2.271792] system 00:04: [io  0x0c50-0x0c52] has been reserved
[    2.271836] system 00:04: [io  0x0c6c] has been reserved
[    2.271880] system 00:04: [io  0x0c6f] has been reserved
[    2.271923] system 00:04: [io  0x0cd0-0x0cdb] has been reserved
[    2.271967] system 00:04: [io  0x0220-0x0227] has been reserved
[    2.272011] system 00:04: [io  0x0260-0x0273] has been reserved
[    2.272055] system 00:04: [io  0x0800] has been reserved
[    2.272098] system 00:04: [io  0x0804] has been reserved
[    2.272141] system 00:04: [io  0x087f] has been reserved
[    2.272185] system 00:04: [io  0x0cdc-0x0cdf] has been reserved
[    2.272229] system 00:04: [io  0x0b00-0x0b0f] has been reserved
[    2.272277] system 00:04: [io  0x0b20-0x0b3f] has been reserved
[    2.272322] system 00:04: [io  0x0200-0x027f] could not be reserved
[    2.272367] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.272424] pnp 00:05: [mem 0x00000000-0x0009ffff]
[    2.272427] pnp 00:05: [mem 0x000ec000-0x000fffff]
[    2.272430] pnp 00:05: [mem 0x00100000-0xbfffffff]
[    2.272433] pnp 00:05: [mem 0xe0000000-0xefffffff]
[    2.272435] pnp 00:05: [mem 0xfeb00000-0xfeb00fff]
[    2.272438] pnp 00:05: [mem 0xfec00000-0xfec00fff]
[    2.272441] pnp 00:05: [mem 0xfee00000-0xfee00fff]
[    2.272516] system 00:05: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.272596] system 00:05: [mem 0x000ec000-0x000fffff] could not be reserved
[    2.272642] system 00:05: [mem 0x00100000-0xbfffffff] could not be reserved
[    2.272688] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    2.272733] system 00:05: [mem 0xfeb00000-0xfeb00fff] has been reserved
[    2.272779] system 00:05: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.272824] system 00:05: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.272870] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.272905] pnp 00:06: [io  0x0070-0x0071]
[    2.272912] pnp 00:06: [irq 8]
[    2.272956] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.273085] pnp 00:07: [mem 0xfed00000-0xfed003ff]
[    2.273133] pnp 00:07: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.273171] pnp 00:08: [io  0x0060]
[    2.273174] pnp 00:08: [io  0x0064]
[    2.273214] pnp 00:08: [irq 1]
[    2.273260] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    2.273308] pnp 00:09: [irq 12]
[    2.273359] pnp 00:09: Plug and Play ACPI device, IDs SYN0141 SYN0100 SYN0002 PNP0f13 (active)
[    2.273989] pnp 00:0a: [irq 23]
[    2.274051] pnp 00:0a: Plug and Play ACPI device, IDs HPQ0004 (active)
[    2.274340] pnp: PnP ACPI: found 11 devices
[    2.274383] ACPI: ACPI bus type pnp unregistered
[    2.281700] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.281754] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    2.281805] pci 0000:00:01.0:   bridge window [mem 0xd4200000-0xd43fffff]
[    2.281852] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    2.281905] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    2.281949] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    2.281995] pci 0000:00:04.0:   bridge window [mem 0xd3100000-0xd41fffff]
[    2.282041] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.282093] pci 0000:00:07.0: PCI bridge to [bus 03-05]
[    2.282136] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    2.282182] pci 0000:00:07.0:   bridge window [mem 0xd2100000-0xd30fffff]
[    2.282228] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.282281] pci 0000:00:09.0: PCI bridge to [bus 06-06]
[    2.282323] pci 0000:00:09.0:   bridge window [io  disabled]
[    2.282369] pci 0000:00:09.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    2.282414] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    2.282460] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    2.282504] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    2.282552] pci 0000:00:14.4:   bridge window [mem disabled]
[    2.282598] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    2.282656] pci 0000:00:01.0: setting latency timer to 64
[    2.282664] pci 0000:00:04.0: setting latency timer to 64
[    2.282672] pci 0000:00:07.0: setting latency timer to 64
[    2.282679] pci 0000:00:09.0: setting latency timer to 64
[    2.282690] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.282693] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.282696] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.282699] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.282702] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.282705] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.282708] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    2.282711] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    2.282714] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    2.282717] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    2.282720] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    2.282723] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    2.282726] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    2.282729] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    2.282732] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    2.282735] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xffffffff]
[    2.282738] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    2.282741] pci_bus 0000:01: resource 1 [mem 0xd4200000-0xd43fffff]
[    2.282744] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    2.282748] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    2.282751] pci_bus 0000:02: resource 1 [mem 0xd3100000-0xd41fffff]
[    2.282754] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    2.282757] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    2.282760] pci_bus 0000:03: resource 1 [mem 0xd2100000-0xd30fffff]
[    2.282763] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
[    2.282766] pci_bus 0000:06: resource 1 [mem 0xd2000000-0xd20fffff]
[    2.282770] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    2.282772] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    2.282775] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    2.282778] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    2.282781] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    2.282784] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    2.282787] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    2.282790] pci_bus 0000:80: resource 10 [mem 0x000cc000-0x000cffff]
[    2.282793] pci_bus 0000:80: resource 11 [mem 0x000d0000-0x000d3fff]
[    2.282796] pci_bus 0000:80: resource 12 [mem 0x000d4000-0x000d7fff]
[    2.282799] pci_bus 0000:80: resource 13 [mem 0x000d8000-0x000dbfff]
[    2.282802] pci_bus 0000:80: resource 14 [mem 0x000dc000-0x000dffff]
[    2.282805] pci_bus 0000:80: resource 15 [mem 0x000e0000-0x000e3fff]
[    2.282808] pci_bus 0000:80: resource 16 [mem 0x000e4000-0x000e7fff]
[    2.282811] pci_bus 0000:80: resource 17 [mem 0x000e8000-0x000ebfff]
[    2.282814] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    2.282817] pci_bus 0000:80: resource 19 [mem 0xf0000000-0xffffffff]
[    2.282867] NET: Registered protocol family 2
[    2.283145] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.285310] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.290812] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.291514] TCP: Hash tables configured (established 524288 bind 65536)
[    2.291594] TCP reno registered
[    2.291659] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    2.291756] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    2.292006] NET: Registered protocol family 1
[    2.292097] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    2.292339] PCI: CLS mismatch (64 != 32), using 64 bytes
[    2.292373] pci 0000:01:05.0: Boot video device
[    2.292381] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.292426] Placing 64MB software IO TLB between ffff8800a876e000 - ffff8800ac76e000
[    2.292476] software IO TLB at phys 0xa876e000 - 0xac76e000
[    2.293032] audit: initializing netlink socket (disabled)
[    2.293119] type=2000 audit(1304879781.290:1): initialized
[    2.310977] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.313608] VFS: Disk quotas dquot_6.5.2
[    2.313745] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.314779] fuse init (API version 7.16)
[    2.315002] msgmni has been set to 7409
[    2.315688] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.315799] io scheduler noop registered
[    2.315844] io scheduler deadline registered
[    2.315945] io scheduler cfq registered (default)
[    2.316195] pcieport 0000:00:04.0: setting latency timer to 64
[    2.316246] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    2.316315] pcieport 0000:00:07.0: setting latency timer to 64
[    2.316351] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    2.316417] pcieport 0000:00:09.0: setting latency timer to 64
[    2.316456] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
[    2.316546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.316650] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.320817] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.321062] ACPI: AC Adapter [AC] (on-line)
[    2.321484] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    2.321573] ACPI: Sleep Button [SLPB]
[    2.321665] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.321788] ACPI: Lid Switch [LID]
[    2.321885] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.321970] ACPI: Power Button [PWRF]
[    2.322114] ACPI: Fan [FAN0] (off)
[    2.322243] ACPI: Fan [FAN1] (off)
[    2.322377] ACPI: Fan [FAN2] (off)
[    2.322505] ACPI: Fan [FAN3] (off)
[    2.322773] ACPI: acpi_idle registered with cpuidle
[    2.335015] thermal LNXTHERM:00: registered as thermal_zone0
[    2.335094] ACPI: Thermal Zone [CPUZ] (67 C)
[    2.335182] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    2.335933] ERST: Table is not found!
[    2.335976] ACPI: Battery Slot [BAT0] (battery absent)
[    2.336168] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.660636] Linux agpgart interface v0.103
[    2.662267] brd: module loaded
[    2.663084] loop: module loaded
[    2.663322] i2c-core: driver [adp5520] using legacy suspend method
[    2.663404] i2c-core: driver [adp5520] using legacy resume method
[    2.664057] Fixed MDIO Bus: probed
[    2.664175] PPP generic driver version 2.4.2
[    2.664313] tun: Universal TUN/TAP device driver, 1.6
[    2.664394] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.664544] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.664678] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.664774] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    2.664780] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    2.664875] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.665070] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.665159] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    2.665228] ehci_hcd 0000:00:12.2: debug port 1
[    2.665313] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd4409500
[    2.680058] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.680326] hub 1-0:1.0: USB hub found
[    2.680411] hub 1-0:1.0: 6 ports detected
[    2.680636] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.680717] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    2.680721] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.680824] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.680971] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.681053] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    2.681123] ehci_hcd 0000:00:13.2: debug port 1
[    2.681204] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd4409400
[    2.700060] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.700286] hub 2-0:1.0: USB hub found
[    2.700366] hub 2-0:1.0: 6 ports detected
[    2.700523] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.700623] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.700684] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    2.700688] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.700793] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    2.700946] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd4408000
[    2.764206] hub 3-0:1.0: USB hub found
[    2.764287] hub 3-0:1.0: 3 ports detected
[    2.764464] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.764527] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    2.764532] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    2.764622] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    2.764772] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd4407000
[    2.824217] hub 4-0:1.0: USB hub found
[    2.824298] hub 4-0:1.0: 3 ports detected
[    2.824480] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.824546] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    2.824550] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.824642] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    2.824793] ohci_hcd 0000:00:13.0: irq 17, io mem 0xd4406000
[    2.884206] hub 5-0:1.0: USB hub found
[    2.884287] hub 5-0:1.0: 3 ports detected
[    2.884472] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.884533] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    2.884538] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.884626] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    2.884774] ohci_hcd 0000:00:13.1: irq 17, io mem 0xd4405000
[    2.944242] hub 6-0:1.0: USB hub found
[    2.944322] hub 6-0:1.0: 3 ports detected
[    2.944513] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.944574] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    2.944578] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    2.944668] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    2.950098] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd4404000
[    3.014202] hub 7-0:1.0: USB hub found
[    3.014283] hub 7-0:1.0: 2 ports detected
[    3.014465] uhci_hcd: USB Universal Host Controller Interface driver
[    3.014705] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.016693] i8042: Detected active multiplexing controller, rev 1.1
[    3.017805] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.017853] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.017935] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.018047] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.018123] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.018326] mousedev: PS/2 mouse device common for all mice
[    3.018682] rtc_cmos 00:06: RTC can wake from S4
[    3.018873] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.018982] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    3.019193] device-mapper: uevent: version 1.0.3
[    3.019383] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    3.019691] device-mapper: multipath: version 1.2.0 loaded
[    3.019737] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.020056] cpuidle: using governor ladder
[    3.020100] cpuidle: using governor menu
[    3.020556] TCP cubic registered
[    3.020788] NET: Registered protocol family 10
[    3.021783] NET: Registered protocol family 17
[    3.021883] Registering the dns_resolver key type
[    3.021962] powernow-k8: Found 1 AMD Athlon(tm)X2 DualCore QL-60 (2 cpu cores) (version 2.20.00)
[    3.022058] powernow-k8:    0 : pstate 0 (1900 MHz)
[    3.022100] powernow-k8:    1 : pstate 1 (950 MHz)
[    3.022735] PM: Hibernation image not present or could not be loaded.
[    3.022753] registered taskstats version 1
[    3.023287]   Magic number: 11:85:645
[    3.023534] rtc_cmos 00:06: setting system clock to 2011-05-08 18:36:22 UTC (1304879782)
[    3.023585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.023628] EDD information not available.
[    3.025986] Freeing unused kernel memory: 956k freed
[    3.026606] Write protecting the kernel read-only data: 10240k
[    3.027729] Freeing unused kernel memory: 184k freed
[    3.034220] Freeing unused kernel memory: 1444k freed
[    3.040118] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.074075] <30>udev[65]: starting version 167
[    3.210882] ahci 0000:00:11.0: version 3.0
[    3.210953] ahci 0000:00:11.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.211226] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    3.211280] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio ccc 
[    3.219053] sky2: driver version 1.28
[    3.219221] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.219313] sky2 0000:02:00.0: setting latency timer to 64
[    3.219394] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    3.219682] sky2 0000:02:00.0: irq 43 for MSI/MSI-X
[    3.223991] scsi0 : ahci
[    3.227802] scsi1 : ahci
[    3.228057] sky2 0000:02:00.0: eth0: addr 00:22:64:5f:11:aa
[    3.230550] scsi2 : ahci
[    3.234740] scsi3 : ahci
[    3.237416] scsi4 : ahci
[    3.239821] scsi5 : ahci
[    3.240763] ata1: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409100 irq 20
[    3.240818] ata2: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409180 irq 20
[    3.240869] ata3: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409200 irq 20
[    3.240922] ata4: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409280 irq 20
[    3.240973] ata5: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409300 irq 20
[    3.241026] ata6: SATA max UDMA/133 abar m1024@0xd4409000 port 0xd4409380 irq 20
[    3.253584] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input4
[    3.253753] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[    3.270092] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    3.580066] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    3.590078] ata6: SATA link down (SStatus 0 SControl 300)
[    3.590162] ata4: SATA link down (SStatus 0 SControl 300)
[    3.590244] ata5: SATA link down (SStatus 0 SControl 300)
[    3.590321] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.590400] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.590474] ata3: SATA link down (SStatus 0 SControl 300)
[    3.591421] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC44C, max UDMA/100
[    3.591467] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.592672] ata1.00: configured for UDMA/100
[    3.592994] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[    3.593294] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.593494] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.593720] sd 0:0:0:0: [sda] Write Protect is off
[    3.593764] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.593818] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.609136] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[    3.613944] ata2.00: configured for UDMA/100
[    3.625556]  sda: sda1 sda2 < sda5 >
[    3.626091] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.725818] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[    3.835783] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.835841] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.836098] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.836213] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.854601] input: USB Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input5
[    3.854946] generic-usb 0003:15D9:0A33.0001: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:12.0-1/input0
[    3.855778] usbcore: registered new interface driver usbhid
[    3.855858] usbhid: USB HID core driver
[   21.574068] Intel AES-NI instructions are not detected.
[   22.718394] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[   22.718416] EXT4-fs (dm-1): write access will be enabled during recovery
[   26.561319] EXT4-fs (dm-1): orphan cleanup on readonly fs
[   26.561349] EXT4-fs (dm-1): ext4_orphan_cleanup: deleting unreferenced inode 3932647
[   26.561516] EXT4-fs (dm-1): ext4_orphan_cleanup: deleting unreferenced inode 3932364
[   26.561534] EXT4-fs (dm-1): 2 orphan inodes deleted
[   26.561547] EXT4-fs (dm-1): recovery complete
[   26.834160] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   45.469357] <30>udev[455]: starting version 167
[   45.490830] Adding 9924604k swap on /dev/mapper/hp--laptop-swap_1.  Priority:-1 extents:1 across:9924604k 
[   45.523678] lp: driver loaded but no devices found
[   45.642719] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   45.687483] hp_accel: laptop model unknown, using default axes configuration
[   45.688311] lis3lv02d: 8 bits sensor found
[   45.768086] lib80211: common routines for IEEE802.11 drivers
[   45.768091] lib80211_crypt: registered algorithm 'NULL'
[   45.787422] wl: module license 'MIXED/Proprietary' taints kernel.
[   45.787429] Disabling lock debugging due to kernel taint
[   45.797333] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.797940] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   45.797946] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   45.798033] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.813612] type=1400 audit(1304879825.282:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=595 comm="apparmor_parser"
[   45.814068] type=1400 audit(1304879825.282:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=595 comm="apparmor_parser"
[   45.814353] type=1400 audit(1304879825.282:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=595 comm="apparmor_parser"
[   45.830348] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   45.845131] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   45.845567] Registered led device: hp::hddprotect
[   45.845655] hp_accel: driver loaded
[   45.889843] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   45.958729] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   45.975789] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   45.975903] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   45.988044] wl 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   45.988057] wl 0000:06:00.0: setting latency timer to 64
[   46.214680] lib80211_crypt: registered algorithm 'TKIP'
[   46.474325] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[   46.765567] [fglrx] Maximum main memory to use for locked dma buffers: 3549 MBytes.
[   46.765645] [fglrx]   vendor: 1002 device: 9612 count: 1
[   46.766167] [fglrx] ioport: bar 1, base 0x5000, size: 0x100
[   46.766188] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   46.766195] pci 0000:01:05.0: setting latency timer to 64
[   46.766673] [fglrx] Kernel PAT support is enabled
[   46.766709] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   46.790148] Linux video capture interface: v2.00
[   46.796198] uvcvideo: Found UVC 1.00 device CKF7063 (04f2:b083)
[   46.812718] input: CKF7063 as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input7
[   46.813031] usbcore: registered new interface driver uvcvideo
[   46.813034] USB Video Class driver (v1.0.0)
[   46.970900] input: HP WMI hotkeys as /devices/virtual/input/input8
[   47.089963] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000/0x0
[   47.093611] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   47.093625] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   47.093640] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   47.130147] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   50.325785] type=1400 audit(1304879829.792:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1132 comm="apparmor_parser"
[   50.329504] ppdev: user-space parallel port driver
[   50.352258] type=1400 audit(1304879829.822:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1133 comm="apparmor_parser"
[   50.363768] type=1400 audit(1304879829.832:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1133 comm="apparmor_parser"
[   50.364064] type=1400 audit(1304879829.832:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1133 comm="apparmor_parser"
[   50.398794] type=1400 audit(1304879829.862:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1143 comm="apparmor_parser"
[   50.404322] type=1400 audit(1304879829.872:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1150 comm="apparmor_parser"
[   50.408813] type=1400 audit(1304879829.872:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1150 comm="apparmor_parser"
[   50.604011] sky2 0000:02:00.0: eth0: enabling interface
[   50.610940] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.987945] audit_printk_skb: 24 callbacks suppressed
[   50.987950] type=1400 audit(1304879830.452:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1353 comm="apparmor_parser"
[   51.291757] vboxdrv: Found 2 processor cores.
[   51.293460] vboxdrv: fAsync=1 offMin=0xe83f54 offMax=0xe83f54
[   51.295407] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   51.295413] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   51.439878] [fglrx] GART Table is not in FRAME_BUFFER range 
[   51.440414] [fglrx] Could not enable MSI; System prevented initialization
[   51.441166] [fglrx] Firegl kernel thread PID: 1462
[   51.441378] [fglrx] Firegl kernel thread PID: 1463
[   51.442707] [fglrx] Firegl kernel thread PID: 1464
[   51.443035] [fglrx] IRQ 18 Enabled
[   51.920163] [fglrx] Gart USWC size:1160 M.
[   51.920168] [fglrx] Gart cacheable size:459 M.
[   51.920175] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   51.920178] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   57.790511] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   60.770034] eth1: no IPv6 routers present
[   71.503648] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   90.640017] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x003f0600
[   91.650019] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x003f0600
```

---

### Post by JoWi on 2011-05-23
Had the same problem, could solve it with the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor" line. Thanks! :)

Edit: Sorry, too fast reply, see next post.

---

### Post by JoWi on 2011-06-02
> **JoWi said:**
> Had the same problem, could solve it with the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor" line. Thanks! :)

Sorry, worked only for the first time, now, the display is dark again and I cannot change the brightness. 

Any suggestions to track down and solve this problem?

---

### Post by RikRas on 2011-06-02
Also have an HP 6735s, like TornadoF3, also have the ATI drivers installed... also cannot get the screen brightness buttons to work. 
Edited the grub file, and brightness adjustments works in the grub loader, but not after boot.

---

### Post by JoWi on 2011-06-12
Similar situation here: 

[LIST]
[*] HP 6735s and Ubuntu 11.04 with ATI Cathalyst video drivers installed. Never had a problem with video stuff before upgrading to 11.04. Since 11.04, I generally cannot change the backlight brightness.
[*] I tried the "echo 6 > /sys/class/backlight/acpi_video0/brightness" trick, but this doesn't work, neither, because the target file does not exist - actually, the directory /sys/class/backlight is empty
[*] The funny thing is: When I unplug the power supply, then the backlight becomes brighter, and turns back darker, when I plug the power supply again. (I.e. just vice versa to the normal behaviour). Manual brightness controll does not work at all. 
[*] It's a matter of luck, how bright the screen is after a reboot. Sometimes, a simple reboot makes the screen brighter, sometimes I boot windows and then linux again, then it's bright enough to work. (Btw in windows, brightness control works, but has no reproducible effect on the brightness in Ubuntu after rebooting.) 
[*] Actually, sometimes brightness control via Fn+F7/F8 does work, but that's probably one out of ten times rebooting. Even then, the brightness control works only delayed, i.e. the brightness always adjusts one key-press later than it should.
[/LIST]

If I can contribute any more information that might help solving this problem, please tell me. I would be so happy to have this solved, sometimes, when I'm really desperate, I even start using Windows :-$ - i.e. this has really brought me far! Thanks for any hints!

---

### Post by tamalatamala on 2011-06-13
Good description! I am having same problems on HP 6735b laptop. Most of the time adjusting the screen brightness works, but occasionally it doesn't. Today I can't make it work, tried rebooting many many times. :(

Adjusting screen brightness in BIOS doesn't always work either and doesn't seem to help. If it works and I set the screen to brightest possible, it still mostly readjusts. Really annoying!

PS: JoWi, thank you for the tips above. I finally made my screen brightness work for today. Had to reboot into Windows and than back into Linux. I didn't notice this connection before. Thanks.

PPS: What would people that don't have windows installed do? Does screen brightness work for them or not?

---

### Post by JamesSmith on 2011-06-13
Having exactly the same problem with an HP6735s in Ubuntu 11.04.

Display fn controls do not work and I have the ATI driver installed and GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor line in grub.conf.  No joy.

I could try booting Vista, but a week would go by and I'd forget what I was doing...

---

### Post by JamesSmith on 2011-06-13
Slightly off topic, I know, but has anyone else with the HP 6735s had problems with getting the wireless working (Broadcom - working now, but a PIA to set up), the boot splash screen breaking, and the machine not powering off on shutdown or reboot?  Just curious.

---

### Post by tornadof3 on 2011-06-14
Splash screen, not powering off, display brightness, all same symptoms. HP 6735s Ubuntu 11.04

---

### Post by tamalatamala on 2011-06-23
I also initially had some problems with the computer not wanting to turn off, but that stopped happening. Occasionally it happens that the screen goes black and I can not bring the laptop back to life - but I believe that is due to old age and overheating (I've had problems with the fan before). The screen brightness problem is still annoying me, unfortunately.

---

### Post by JoWi on 2011-06-25
Same here: Power-off problem well-known, but not happening any more. However: Screen brightness problem persists. I added the screen brightness tool to my gnome bar, but this icon displays a red error symbol indicating that it is not able to determine the current brightness of the screen.

---

### Post by inkarkat on 2011-07-30
Same problem here with an HP 6735s laptop; tried the "acpi_backlight=vendor" to no avail. I'm currently working around this by sticking to the 10.10 kernel (2.6.35-28-generic); I changed the default boot entry in /boot/grub/menu.lst. 

There recently was a kernel update from 2.6.38-8 to 2.6.38-10, but it didn't help. Has anyone already submitted a defect, so that the Ubuntu / kernel developers are aware of this? I didn't find any such defect (and am not sure what kind of information would be helpful to troubleshoot this issue)?!

---

### Post by JoWi on 2011-07-30
Thanks for the advice to use the old kernel. I'd like to try and install it right now. Can you tell me, how to do that? This kernel version is not available in synaptic.

I have not reported the defect, since I have no experience how to do that. If it has not been reported yet, it would be great if someone finally does this. ;)

---

### Post by Otto-C on 2011-07-30
Lucid 10.04.

My solution was:

System > Preferences > Power Management
At Power Management Preferences click On Battery Power and
untick Reduce backlight brightness.
Authenticate w/password and your good to go.
otto-c

---

### Post by JoWi on 2011-07-30
Up to 10.10 I had not experienced any problems with the backlight brightness.

---

### Post by elviscankovic on 2011-08-01
Hello!
I have same problem with my hp 6735b but problem starts after I install additional driver (ATI).Before additional driver installation at the photo I attach bellow there was a slider I can move and adjust brightness.Now there is no that slider and that is the problem.I tried everything suggested here on forum but have no luck till now. Looking forward for solution.[IMG]http://i49.servimg.com/u/f49/16/69/29/78/screen10.png[/IMG]

---

### Post by JoWi on 2011-08-01
Hi all. Since the kernel update to 2.6.38-10, things got a LITTLE bit better. Now, I can at least reproducibly enable brightness control, as long as I have some power supply available: If I find out, after booting my system, that the brightness control fails, I reboot without AC connected (with battery power) and then connect the AC. This usually works. Not nice, but at least a workaround for when I'm at home. :-/

---

### Post by elviscankovic on 2011-08-01
> **elviscankovic said:**
> Hello!
I have same problem with my hp 6735b but problem starts after I install additional driver (ATI).Before additional driver installation at the photo I attach bellow there was a slider I can move and adjust brightness.Now there is no that slider and that is the problem.I tried everything suggested here on forum but have no luck till now. Looking forward for solution.[IMG]http://i49.servimg.com/u/f49/16/69/29/78/screen10.png[/IMG]

I forget to say that I tried to deactivate additional driver but nothing happens.No slider for brightness control.

---

### Post by elviscankovic on 2011-08-12
> **frozenfiree said:**
> Hello,
i had the same problem and it seems to be a problem of the new kernel and ati driver. To solve it you just have to add ```
nomodeset acpi_backlight=vendor
``` to the GRUB_CMDLINE_LINUX_DEFAULT  string in /etc/default/grub.

Looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```After that you need to update the grub -> ```
sudo update-grub
```After reboot it should be normal.

worked in my case

Greets,
ff

I own HP 6735b laptop and Ubuntu 11.04 with all of updates and this solution works for me to but...
After I changed grub, I restart the computer and during bios loading I keep pressing Fn+Brightness UP key until I set brightness to 100%.
After this my computer brightness is always at 100 % with battery an on the power source.

---

### Post by gregor171 on 2011-08-24
This was also mine problem. I have HP EliteBook 8560p with graphics AMD Radeon... **Update of graphics drivers (manualy) worked for me.** 
However there is 
*Kmenu>Applications>System>AdditionalDrivers *
but would not update xorg.conf perhaps because of VirtualBox Guest Adidtions.  

Grub change did not help!

Update drivers if you can't, then do it manualy!
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by andrei90 on 2011-08-24
Hello.

Please try this:

 1.   sudo gedit /etc/default/grub
  2.  Change the line GRUB_CMDLINE_LINUX="" into
  3.  GRUB_CMDLINE_LINUX="acpi_osi=Linux"
  4.  sudo update-grub
  5.  Restart your linux

Credits to this [**man**]("http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html")

---

### Post by tamalatamala on 2011-09-20
Andrei, it did not work for me.

---

### Post by GnuSense on 2011-12-07
My friend has an HP 6735s which I upgraded from 11.04 to 11.10.  The screen was too dull, I guess the backlighting was off, oddly, it would brighten up when the power plug was disconnected, but was still to dark. We were able to fix the issue in 11.04 with changes to /etc/default/grub, but I played with all kinds of versions of those modifications in 11.10 to no effect. 

I fixed it by upgrading the BIOS to the most current version.  That is, I believe that is what fixed it. It is possible that upgrading to libcolord1 0.1.12-1ubuntu2.1 may have fixed the issue (I did a dist-upgrade that upgraded libcolord1 just before I flashed the new BIOS).  I downloaded and extracted this file, then burnt the rom.iso file in the ISO subdirectory to a CD-R and booted from the optical drive.

[ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45715.exe](ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45715.exe)

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687621&prodNameId=3687622&swEnvOID=2094&swLang=13&mode=2&taskId=135&swItem=ob-77904-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687621&prodNameId=3687622&swEnvOID=2094&swLang=13&mode=2&taskId=135&swItem=ob-77904-1)

What a pain.

---

### Post by JoWi on 2011-12-28
I just installed a BIOS update, and it worked for me (HP Compaq 6735s), thanks for the advice! :)

Now, I can adjust the monitor brightness with the Fn+F7 Fn+F8 keys and the automatic dimming when (dis)connecting AC works as it should.

I received the BIOS update from [HP Support Center]("http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=3687622&taskId=135&prodTypeId=321957&prodSeriesId=3687621&lang=en&cc=us") and installed it using the HPQFlash tool (booting my laptop with windows).

---

### Post by arthurc on 2012-01-27
I have the same laptop with the intel video card. I tried every solution posted but nothing worked. My power cable came unplugged and the backlight came back on! I had to plug the laptop back up right away since my battery refuses to charge and the light went did again. After some playing around I cold booted without the power cord and used the fn key in grub to brighten the screen and as soon as it booted the same problem! So I plugged the cord back in and now the backlight is on. I tried switching the aclpi settings but that didnt help....weird problem! So now I start without the power cord then plug it back in once im logged in. Hope this is helpful to someone...and maybe someone can tell me why this battery wont charge!

arthurc

---


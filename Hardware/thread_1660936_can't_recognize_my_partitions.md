---
title: "can't recognize my partitions"
date: 2011-01-06
forum: Hardware
---

### Post by sinoohe on 2011-01-06
hi
i have asus T91MT
some days before I was working with my netbook and in one second the display stop and I couldn't move mouse or type and also my hdd lamp was working!!
I reset it and linux not start up
I boot it with live cd and i can't partition my ssd hard drive!
```

ubuntu@ubuntu:~$ find /dev/disk/
/dev/disk/
/dev/disk/by-uuid
/dev/disk/by-uuid/BD48-A7FF
/dev/disk/by-path
/dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0-part1
/dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0-part5
/dev/disk/by-path/pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0-part1
/dev/disk/by-path/pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0
/dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0-part2
/dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0
/dev/disk/by-id
/dev/disk/by-id/usb-_Patriot_Memory_07960C08FFC70035-0:0-part1
/dev/disk/by-id/usb-_Patriot_Memory_07960C08FFC70035-0:0

```
```

root@ubuntu:~# fdisk /dev/sda

Unable to read /dev/sda

```
```

root@ubuntu:~# parted /dev/sda
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: /dev/sda: unrecognised disk label

```
```

ubuntu@ubuntu:~$ ls /dev/ | grep sd
sda
sda1
sda2
sda5
sdb
sdb1

```
note that sda is my ssd hard and sdb is my flash that i boot ubuntu from it
what can I do to solve this problem?
plz help

---

### Post by Fafler on 2011-01-06
Try reading the raw device with dd
```
dd if=/dev/sda of=/dev/null
```

And look for any errors:
```
dmesg | grep sda
```

---

### Post by sinoohe on 2011-01-06
```

root@ubuntu:~# dd if=/dev/sda of=/dev/null
dd: reading `/dev/sda': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00242657 s, 0.0 kB/s

```
```

root@ubuntu:~# dmesg | grep sda
.....
ER_OK
[  184.906666] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 1e 90 80 00 00 08 00
[  184.906696] end_request: I/O error, dev sda, sector 2003072
[  184.906769] sd 1:0:0:0: [sda] Unhandled error code
[  184.906777] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  184.906788] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 1e 90 00 00 00 08 00
[  184.906818] end_request: I/O error, dev sda, sector 2002944
[  184.906890] sd 1:0:0:0: [sda] Unhandled error code
[  184.906898] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  184.906909] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 1e 90 00 00 00 08 00
[  184.906939] end_request: I/O error, dev sda, sector 2002944
[  184.907023] sd 1:0:0:0: [sda] Unhandled error code
[  184.907031] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  184.907042] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 1e a0 00 00 00 08 00
[  184.907072] end_request: I/O error, dev sda, sector 2007040
[  184.907281] sd 1:0:0:0: [sda] Unhandled error code
[  184.907292] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  184.907305] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  184.907337] end_request: I/O error, dev sda, sector 0
[  184.907489] sd 1:0:0:0: [sda] Unhandled error code
[  184.907499] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  184.907511] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  184.907544] end_request: I/O error, dev sda, sector 0
[  290.918800] sd 1:0:0:0: [sda] Unhandled error code
[  290.918813] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  290.918827] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[  290.918861] end_request: I/O error, dev sda, sector 0
[  290.918884] Buffer I/O error on device sda, logical block 0
[  290.918922] Buffer I/O error on device sda, logical block 1
[  290.918933] Buffer I/O error on device sda, logical block 2
[  290.918944] Buffer I/O error on device sda, logical block 3
[  290.919082] sd 1:0:0:0: [sda] Unhandled error code
[  290.919092] sd 1:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  290.919104] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  290.919135] end_request: I/O error, dev sda, sector 0
[  290.919147] Buffer I/O error on device sda, logical block 0


```

---

### Post by Fafler on 2011-01-06
Seems like a defective drive. Should still be under warranty.

---

### Post by sinoohe on 2011-01-06
I carry this to warranty but the man out there inserted a bootable partition editor (that base of it was windows) and removed the partitions!! and he said that the problem fixed!
after that i wanted to change partitions with gparted. gparted failed!

---

### Post by Fafler on 2011-01-06
Install smartmontools, run smartctl -all /dev/sda and report back.

---

### Post by sinoohe on 2011-01-06
```

ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

```
```

ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda -T permissive
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
SMART Health Status: OK
Read defect list: asked for grown list but didn't get it

Error Counter logging not supported
Device does not support Self Test logging

```

---

### Post by Fafler on 2011-01-06
Which probably moves the problem from the hardware layer to the software layer. Still, the way the problem occurred speaks against it.

```
dmesg | grep SATA
```

The drive stayed in your laptop while the tech guy did that thing?

---

### Post by sinoohe on 2011-01-09
i found the problem that ubuntu couldn't detect my ssd hard drive:
i boot it with 'partition wizard' (a live cd partition editor) and change the partition table
again i boot it with ubuntu, i can write every thing i want to my hard disc
now the actual problem is that i can't install ubuntu on it: at the start of installing it says IO error!

now i tried the commands above:
```

root@ubuntu:~# smartctl --all /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SanDisk pSSD-P2 32GB
Serial Number:    APZ012710080724
Firmware Version: SSD 5.20
User Capacity:    32,017,047,552 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Not recognized. Minor revision code: 0x28
Local Time is:    Sun Jan  9 08:33:53 2011 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 120) seconds.
Offline data collection
capabilities:                    (0x11) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0000) Automatic saving of SMART data         is not implemented.
Error logging capability:        (0x00) Error logging NOT supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   0) minutes.
Extended self-test routine
recommended polling time:        (   0) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
232 Unknown_Attribute       0x0000   100   100   005    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
 12 Power_Cycle_Count       0x0000   004   004   000    Old_age   Offline      -       0
171 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
172 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
174 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
187 Reported_Uncorrect      0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
241 Unknown_Attribute       0x0000   024   024   000    Old_age   Offline      -       0
242 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 5304

Warning: device does not support Error Logging
Error SMART Error Log Read failed
Smartctl: SMART Error Log Read Failed
Error SMART Error Self-Test Log Read failed
Smartctl: SMART Self Test Log Read Failed
Device does not support Selective Self Tests/Logging

```
```

root@ubuntu:~# dd if=/dev/sda of=/dev/null
dd: reading `/dev/sda': Input/output error
262368+0 records in
262368+0 records out
134332416 bytes (134 MB) copied, 221.175 s, 607 kB/s


```
```

root@ubuntu:~# dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f650000 (usable)
[    0.000000]  BIOS-e820: 000000003f650000 - 000000003f660000 (reserved)
[    0.000000]  BIOS-e820: 000000003f660000 - 000000003f66e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f66e000 - 000000003f6b0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6b0000 - 000000003f6c0000 (reserved)
[    0.000000]  BIOS-e820: 000000003f6c8000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f650 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f650000 (usable)
[    0.000000]  modified: 000000003f650000 - 000000003f660000 (reserved)
[    0.000000]  modified: 000000003f660000 - 000000003f66e000 (ACPI data)
[    0.000000]  modified: 000000003f66e000 - 000000003f6b0000 (ACPI NVS)
[    0.000000]  modified: 000000003f6b0000 - 000000003f6c0000 (reserved)
[    0.000000]  modified: 000000003f6c8000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 3ed5f000 - 3f64e2d6
[    0.000000] Allocated new RAMDISK: 008de000 - 011cd2d6
[    0.000000] Move RAMDISK from 000000003ed5f000 - 000000003f64e2d5 to 008de000 - 011cd2d5
[    0.000000] ACPI: RSDP 000fc280 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 3f660100 00064 (v01 _ASUS_ Notebook 20091126 MSFT 00000097)
[    0.000000] ACPI: FACP 3f660290 000F4 (v04 112609 FACP2205 20091126 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f660430 09573 (v02  A1410 A1410000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 3f66e000 00040
[    0.000000] ACPI: APIC 3f660390 0005C (v02 112609 APIC2205 20091126 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f6603f0 0003C (v01 112609 OEMMCFG  20091126 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f66e040 0012C (v01 112609 OEMB2205 20091126 MSFT 00000097)
[    0.000000] ACPI: HPET 3f6699b0 00038 (v01 112609 OEMHPET  20091126 MSFT 00000097)
[    0.000000] ACPI: GSCI 3f66e170 02024 (v01 112609 GMCHSCI  20091126 MSFT 00000097)
[    0.000000] ACPI: SSDT 3f670b60 004F0 (v01  PmRef    CpuPm 00003000 INTL 20060113)
[    0.000000] ACPI: SLIC 3f6699f0 00176 (v01 _ASUS_ Notebook 20091126 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd1b0]              BRK ==> [00008da000 - 00008dd1b0]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008de000 - 00011cd2d6]      NEW RAMDISK ==> [00008de000 - 00011cd2d6]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f650
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f650
[    0.000000] On node 0 totalpages: 259551
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c11cf200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32085 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1c00000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257522
[    0.000000] Kernel command line: initrd=/ubninit file=/cdrom/preseed/kubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5192960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f650)
[    0.000000] Memory: 1006288k/1038656k available (4673k kernel code, 31356k reserved, 2122k data, 656k init, 129352k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1332.526 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 2665.05 BogoMIPS (lpj=5330104)
[    0.004057] Security Framework initialized
[    0.004110] AppArmor: AppArmor initialized
[    0.004130] Mount-cache hash table entries: 512
[    0.004417] Initializing cgroup subsys ns
[    0.004430] Initializing cgroup subsys cpuacct
[    0.004441] Initializing cgroup subsys memory
[    0.004458] Initializing cgroup subsys devices
[    0.004466] Initializing cgroup subsys freezer
[    0.004473] Initializing cgroup subsys net_cls
[    0.004519] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004527] CPU: L2 cache: 512K
[    0.004534] CPU: Physical Processor ID: 0
[    0.004539] CPU: Processor Core ID: 0
[    0.004548] mce: CPU supports 5 MCE banks
[    0.004569] CPU0: Thermal monitoring enabled (TM2)
[    0.004579] using mwait in idle threads.
[    0.004593] Performance Events: Atom events, Intel PMU driver.
[    0.004613] ... version:                3
[    0.004619] ... bit width:              40
[    0.004624] ... generic registers:      2
[    0.004630] ... value mask:             000000ffffffffff
[    0.004637] ... max period:             000000007fffffff
[    0.004642] ... fixed-purpose events:   3
[    0.004648] ... event mask:             0000000700000003
[    0.004659] Checking 'hlt' instruction... OK.
[    0.020010] Disabling 4MB page tables to avoid TLB bug
[    0.025198] ACPI: Core revision 20090903
[    0.052046] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.052064] ftrace: allocating 21771 entries in 43 pages
[    0.056123] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.060207] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.099899] CPU0: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.100001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.184126] CPU1: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.184157] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.188041] Brought up 2 CPUs
[    0.188050] Total of 2 processors activated (5330.44 BogoMIPS).
[    0.188313] CPU0 attaching sched-domain:
[    0.188324]  domain 0: span 0-1 level SIBLING
[    0.188331]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.188346]   domain 1: span 0-1 level MC
[    0.188353]    groups: 0-1 (cpu_power = 1178)
[    0.188368] CPU1 attaching sched-domain:
[    0.188374]  domain 0: span 0-1 level SIBLING
[    0.188380]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.188394]   domain 1: span 0-1 level MC
[    0.188400]    groups: 0-1 (cpu_power = 1178)
[    0.188673] devtmpfs: initialized
[    0.188673] regulator: core version 0.5
[    0.188673] Time:  7:52:27  Date: 01/09/11
[    0.188673] NET: Registered protocol family 16
[    0.188673] Trying to unpack rootfs image as initramfs...
[    0.188674] EISA bus registered
[    0.188707] ACPI: bus type pci registered
[    0.188917] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.188929] PCI: Not using MMCONFIG.
[    0.189242] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.189250] PCI: Using configuration type 1 for base access
[    0.195146] bio: create slab <bio-0> at 0
[    0.199097] ACPI: EC: Look up EC in DSDT
[    0.203389] ACPI: Executed 1 blocks of module-level executable AML code
[    0.219474] ACPI: Interpreter enabled
[    0.219503] ACPI: (supports S0 S3 S4 S5)
[    0.219603] ACPI: Using IOAPIC for interrupt routing
[    0.219794] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.224566] ACPI: BIOS _OSI(Linux) query ignored
[    0.232279] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.232291] PCI: Using MMCONFIG for extended config space
[    0.253819] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[    0.254084] ACPI Warning: Incorrect checksum in table [OEMB] - 01, should be 51 (20090903/tbutils-314)
[    0.255567] ACPI: No dock devices found.
[    0.256170] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.256423] pci 0000:00:02.0: reg 10 32bit mmio: [0xf3f80000-0xf3ffffff]
[    0.256441] pci 0000:00:02.0: reg 14 io port: [0xc880-0xc887]
[    0.256458] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.256476] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf3f40000-0xf3f7ffff]
[    0.256635] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3f38000-0xf3f3bfff]
[    0.256703] pci 0000:00:1b.0: PME# supported from D0 D3hot
[    0.256716] pci 0000:00:1b.0: PME# disabled
[    0.256817] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.256829] pci 0000:00:1c.0: PME# disabled
[    0.256931] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.256943] pci 0000:00:1c.1: PME# disabled
[    0.257023] pci 0000:00:1d.0: reg 20 io port: [0xb880-0xb89f]
[    0.257104] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.257185] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.257290] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3f37c00-0xf3f37fff]
[    0.257388] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.257402] pci 0000:00:1d.7: PME# disabled
[    0.257545] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.257673] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff]
[    0.257694] pci 0000:03:00.0: reg 18 io port: [0xe880-0xe8ff]
[    0.257786] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.257800] pci 0000:03:00.0: PME# disabled
[    0.257891] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.257904] pci 0000:00:1c.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.257999] pci 0000:01:00.0: reg 10 64bit mmio: [0xfbef0000-0xfbefffff]
[    0.258094] pci 0000:01:00.0: supports D1
[    0.258103] pci 0000:01:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.258116] pci 0000:01:00.0: PME# disabled
[    0.258210] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.258223] pci 0000:00:1c.1: bridge 32bit mmio: [0xf4000000-0xfbefffff]
[    0.258238] pci 0000:00:1c.1: bridge 32bit mmio pref: [0xcc000000-0xcfffffff]
[    0.258262] pci_bus 0000:00: on NUMA node 0
[    0.258283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.258732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP4._PRT]
[    0.258926] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP5._PRT]
[    0.284941] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.285419] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.285891] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.286363] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.286832] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.287299] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.287767] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.288258] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.288684] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.288714] vgaarb: loaded
[    0.289139] SCSI subsystem initialized
[    0.289432] libata version 3.00 loaded.
[    0.289710] usbcore: registered new interface driver usbfs
[    0.289764] usbcore: registered new interface driver hub
[    0.289866] usbcore: registered new device driver usb
[    0.290391] ACPI: WMI: Mapper loaded
[    0.290399] PCI: Using ACPI for IRQ routing
[    0.290866] NetLabel: Initializing
[    0.290874] NetLabel:  domain hash size = 128
[    0.290881] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.290923] NetLabel:  unlabeled traffic allowed by default
[    0.291050] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.291070] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    5.712130] Switching to clocksource tsc
[    5.718724] AppArmor: AppArmor Filesystem Enabled
[    5.718811] pnp: PnP ACPI init
[    5.718886] ACPI: bus type pnp registered
[    5.730346] pnp: PnP ACPI: found 14 devices
[    5.730358] ACPI: ACPI bus type pnp unregistered
[    5.730372] PnPBIOS: Disabled by ACPI PNP
[    5.730433] system 00:01: iomem range 0x40000000-0x7fffffff has been reserved
[    5.730449] system 00:01: iomem range 0x3f800000-0x3fffffff could not be reserved
[    5.730490] system 00:06: ioport range 0x374-0x375 has been reserved
[    5.730507] system 00:06: ioport range 0x3f4-0x3f5 has been reserved
[    5.730523] system 00:06: ioport range 0x380-0x383 has been reserved
[    5.730535] system 00:06: ioport range 0x9f4-0x9ff has been reserved
[    5.730548] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    5.730561] system 00:06: ioport range 0x900-0x9f3 has been reserved
[    5.730574] system 00:06: ioport range 0x400-0x43f has been reserved
[    5.730587] system 00:06: ioport range 0x480-0x4bf has been reserved
[    5.730605] system 00:06: iomem range 0xf0000000-0xf0003fff has been reserved
[    5.730654] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    5.730668] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    5.730697] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    5.730724] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    5.730737] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    5.730750] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    5.730763] system 00:0d: iomem range 0x100000-0x3f7fffff could not be reserved
[    5.766177] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    5.766196] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    5.766214] pci 0000:00:1c.0:   MEM window: 0xfbf00000-0xfbffffff
[    5.766230] pci 0000:00:1c.0:   PREFETCH window: 0x80000000-0x801fffff
[    5.766249] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
[    5.766262] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    5.766276] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xfbefffff
[    5.766289] pci 0000:00:1c.1:   PREFETCH window: 0xcc000000-0xcfffffff
[    5.766332]   alloc irq_desc for 16 on node -1
[    5.766341]   alloc kstat_irqs on node -1
[    5.766365] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.766381] pci 0000:00:1c.0: setting latency timer to 64
[    5.766406]   alloc irq_desc for 17 on node -1
[    5.766414]   alloc kstat_irqs on node -1
[    5.766429] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.766442] pci 0000:00:1c.1: setting latency timer to 64
[    5.766457] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    5.766469] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    5.766480] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    5.766492] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    5.766503] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x801fffff]
[    5.766515] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    5.766526] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xfbefffff]
[    5.766537] pci_bus 0000:01: resource 2 pref mem [0xcc000000-0xcfffffff]
[    5.766674] NET: Registered protocol family 2
[    5.767029] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    5.768340] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    5.769926] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    5.770913] TCP: Hash tables configured (established 131072 bind 65536)
[    5.770926] TCP reno registered
[    5.771361] NET: Registered protocol family 1
[    5.771440] pci 0000:00:02.0: Boot video device
[    5.772404] cpufreq-nforce2: No nForce2 chipset.
[    5.772524] Scanning for low memory corruption every 60 seconds
[    5.773133] audit: initializing netlink socket (disabled)
[    5.773201] type=2000 audit(1294559552.772:1): initialized
[    5.799594] highmem bounce pool size: 64 pages
[    5.799618] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    5.806651] VFS: Disk quotas dquot_6.5.2
[    5.806921] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.809891] fuse init (API version 7.13)
[    5.810410] msgmni has been set to 1713
[    5.811639] alg: No test for stdrng (krng)
[    5.811984] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    5.812001] io scheduler noop registered
[    5.812008] io scheduler anticipatory registered
[    5.812015] io scheduler deadline registered
[    5.812223] io scheduler cfq registered (default)
[    5.812623] pcieport 0000:00:1c.0: setting latency timer to 64
[    5.812892] pcieport 0000:00:1c.1: setting latency timer to 64
[    5.813246] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.813672] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.814146] ACPI: AC Adapter [AC0] (off-line)
[    5.814549] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    5.819927] ACPI: Lid Switch [LID]
[    5.820156] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    5.820172] ACPI: Sleep Button [SLPB]
[    5.820358] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    5.820371] ACPI: Power Button [PWRB]
[    5.822974] ACPI: SSDT 3f670270 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20060113)
[    5.825216] ACPI: SSDT 3f670500 0065D (v01  PmRef  Cpu0Cst 00003001 INTL 20060113)
[    5.827669] Monitor-Mwait will be used to enter C-1 state
[    5.832161] Monitor-Mwait will be used to enter C-2 state
[    5.832339] Monitor-Mwait will be used to enter C-3 state
[    5.832443] Monitor-Mwait will be used to enter C-3 state
[    5.832473] Marking TSC unstable due to TSC halts in idle
[    5.832630] processor LNXCPU:00: registered as cooling_device0
[    5.833660] ACPI: SSDT 3f6701a0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20060113)
[    5.834589] ACPI: SSDT 3f670470 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060113)
[    5.836289] Switching to clocksource hpet
[    5.837193] processor LNXCPU:01: registered as cooling_device1
[    5.845583] Freeing initrd memory: 9148k freed
[    5.858978] thermal LNXTHERM:01: registered as thermal_zone0
[    5.859009] ACPI: Thermal Zone [TZ00] (45 C)
[    5.860117] isapnp: Scanning for PnP cards...
[    5.865951] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    5.870517] brd: module loaded
[    5.872285] loop: module loaded
[    5.872593] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    5.873109] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    5.874257] Fixed MDIO Bus: probed
[    5.874387] PPP generic driver version 2.4.2
[    5.874517] tun: Universal TUN/TAP device driver, 1.6
[    5.874525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.874803] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.874858]   alloc irq_desc for 19 on node -1
[    5.874866]   alloc kstat_irqs on node -1
[    5.874886] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.874923] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.874934] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.875055] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    5.875123] ehci_hcd 0000:00:1d.7: debug port 1
[    5.879021] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.879061] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf3f37c00
[    5.893045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.893336] usb usb1: configuration #1 chosen from 1 choice
[    5.893439] hub 1-0:1.0: USB hub found
[    5.893475] hub 1-0:1.0: 8 ports detected
[    5.893678] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.893731] uhci_hcd: USB Universal Host Controller Interface driver
[    5.893822]   alloc irq_desc for 20 on node -1
[    5.893830]   alloc kstat_irqs on node -1
[    5.893848] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.893867] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.893877] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.893998] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    5.894060] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000b880
[    5.894368] usb usb2: configuration #1 chosen from 1 choice
[    5.894466] hub 2-0:1.0: USB hub found
[    5.894489] hub 2-0:1.0: 2 ports detected
[    5.894626]   alloc irq_desc for 21 on node -1
[    5.894634]   alloc kstat_irqs on node -1
[    5.894649] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.894670] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.894679] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.894803] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    5.894859] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c080
[    5.895158] usb usb3: configuration #1 chosen from 1 choice
[    5.895253] hub 3-0:1.0: USB hub found
[    5.895276] hub 3-0:1.0: 2 ports detected
[    5.895403]   alloc irq_desc for 18 on node -1
[    5.895411]   alloc kstat_irqs on node -1
[    5.895425] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.895440] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.895449] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.895558] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    5.895613] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    5.895916] usb usb4: configuration #1 chosen from 1 choice
[    5.896013] hub 4-0:1.0: USB hub found
[    5.896038] hub 4-0:1.0: 2 ports detected
[    5.896336] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.919252] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.919275] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.919748] mice: PS/2 mouse device common for all mice
[    5.920761] rtc_cmos 00:02: RTC can wake from S4
[    5.920883] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    5.920926] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    5.921349] device-mapper: uevent: version 1.0.3
[    5.921692] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    5.921920] device-mapper: multipath: version 1.1.0 loaded
[    5.921930] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.922331] EISA: Probing bus 0 at eisa.0
[    5.922395] EISA: Detected 0 cards.
[    5.922943] cpuidle: using governor ladder
[    5.923434] cpuidle: using governor menu
[    5.924935] TCP cubic registered
[    5.925536] NET: Registered protocol family 10
[    5.927040] lo: Disabled Privacy Extensions
[    5.928145] NET: Registered protocol family 17
[    5.929980] Using IPI No-Shortcut mode
[    5.930279] PM: Resume from disk failed.
[    5.930313] registered taskstats version 1
[    5.930812]   Magic number: 11:722:874
[    5.930950] rtc_cmos 00:02: setting system clock to 2011-01-09 07:52:33 UTC (1294559553)
[    5.930961] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.930967] EDD information not available.
[    5.949444] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    6.085197] ACPI: Battery Slot [BAT0] (battery present)
[    6.215426] isapnp: No Plug & Play device found
[    6.215479] Freeing unused kernel memory: 656k freed
[    6.216257] Write protecting the kernel text: 4676k
[    6.216346] Write protecting the kernel read-only data: 1840k
[    6.237145] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    6.272640] udev: starting version 151
[    6.383198] usb 1-2: configuration #1 chosen from 1 choice
[    6.445243] pata_sch 0000:00:1f.1: version 0.2
[    6.445352] pata_sch 0000:00:1f.1: setting latency timer to 64
[    6.460201] scsi0 : pata_sch
[    6.489357] scsi1 : pata_sch
[    6.490937] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.490951] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.524998] vga16fb: initializing
[    6.525098] vga16fb: mapped to 0xc00a0000
[    6.525291] fb0: VGA16 VGA frame buffer device
[    6.612178] Initializing USB Mass Storage driver...
[    6.612636] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.612914] usbcore: registered new interface driver usb-storage
[    6.612928] USB Mass Storage support registered.
[    6.612950] usb-storage: device found at 2
[    6.612956] usb-storage: waiting for device to settle before scanning
[    6.655517] ata1.00: ATA-8: SanDisk pSSD-P2 32GB, SSD 5.20, max UDMA/133
[    6.655534] ata1.00: 62533296 sectors, multi 0: LBA48 
[    6.663200] ata1.00: configured for UDMA/100
[    6.663605] scsi 0:0:0:0: Direct-Access     ATA      SanDisk pSSD-P2  SSD  PQ: 0 ANSI: 5
[    6.664201] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    6.664211] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.664472] sd 0:0:0:0: [sda] Write Protect is off
[    6.664483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.664584] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.665325]  sda: sda1
[    6.667292] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.720291] usb 1-7: new high speed USB device using ehci_hcd and address 5
[    6.929496] usb 1-7: configuration #1 chosen from 1 choice
[    7.029917] Console: switching to colour frame buffer device 80x30
[    7.176053] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    7.346378] usb 4-1: configuration #1 chosen from 1 choice
[    7.396813] usbcore: registered new interface driver hiddev
[    7.396943] usbcore: registered new interface driver usbhid
[    7.396956] usbhid: v2.6:USB HID core driver
[    7.575853] xor: automatically using best checksumming function: pIII_sse
[    7.593039]    pIII_sse  :  2995.000 MB/sec
[    7.593048] xor: using function: pIII_sse (2995.000 MB/sec)
[    7.604171] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    7.604221] device-mapper: dm-raid45: initialized v0.2594b
[    7.788560] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.788571] EXT3-fs: write access will be enabled during recovery.
[    7.792399] usb 4-2: configuration #1 chosen from 1 choice
[    7.806912] kjournald starting.  Commit interval 5 seconds
[    7.806958] EXT3-fs: recovery complete.
[    7.809700] EXT3-fs: mounted filesystem with ordered data mode.
[   11.608966] usb-storage: device scan complete
[   11.610531] scsi 2:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[   11.612301] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   11.613519] sd 2:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[   11.614110] sd 2:0:0:0: [sdb] Write Protect is off
[   11.614124] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   11.614134] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.616750] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.616767]  sdb: sdb1
[   11.620810] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.620827] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   13.082583] aufs 2-standalone.tree-20091207
[   13.118317] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   40.081581] udev: starting version 151
[   41.011802] Bluetooth: Core ver 2.15
[   41.016498] ACPI: resource isch_smbus [0x400-0x43f] conflicts with ACPI region SMRG [0x400-0x43f]
[   41.016511] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   41.019299] atl1c 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.019329] atl1c 0000:03:00.0: setting latency timer to 64
[   41.101442] NET: Registered protocol family 31
[   41.101452] Bluetooth: HCI device and connection manager initialized
[   41.101463] Bluetooth: HCI socket layer initialized
[   41.127486] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   41.130823] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   41.132553] usbcore: registered new interface driver btusb
[   41.270124] Linux video capture interface: v2.00
[   41.439928] cfg80211: Calling CRDA to update world regulatory domain
[   41.562728] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:509b)
[   41.583775] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/input/input5
[   41.583978] usbcore: registered new interface driver uvcvideo
[   41.583990] USB Video Class driver (v0.1.0)
[   42.012894] ath9k 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   42.012921] ath9k 0000:01:00.0: setting latency timer to 64
[   42.031541]   alloc irq_desc for 24 on node -1
[   42.031553]   alloc kstat_irqs on node -1
[   42.031584] atl1c 0000:03:00.0: irq 24 for MSI/MSI-X
[   42.032552] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.062533] ath: EEPROM regdomain: 0x60
[   42.062543] ath: EEPROM indicates we should expect a direct regpair map
[   42.062555] ath: Country alpha2 being used: 00
[   42.062561] ath: Regpair used: 0x60
[   42.098498] Bluetooth: L2CAP ver 2.14
[   42.098508] Bluetooth: L2CAP socket layer initialized
[   42.174697] cfg80211: World regulatory domain updated:
[   42.174708]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.174722]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.174734]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.174745]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   42.174757]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.174768]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   42.395590] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   42.398541] Registered led device: ath9k-phy0::radio
[   42.398620] Registered led device: ath9k-phy0::assoc
[   42.398696] Registered led device: ath9k-phy0::tx
[   42.398772] Registered led device: ath9k-phy0::rx
[   42.402524] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf82a0000, irq=17
[   42.417250] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000
[   42.493224] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.493236] Bluetooth: BNEP filters: protocol multicast
[   42.509371] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   42.759675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.807882] Bridge firewalling registered
[   42.927400] Bluetooth: SCO (Voice Link) ver 0.6
[   42.927410] Bluetooth: SCO socket layer initialized
[   43.127971] Bluetooth: RFCOMM TTY layer initialized
[   43.127990] Bluetooth: RFCOMM socket layer initialized
[   43.127999] Bluetooth: RFCOMM ver 1.11
[   43.318910]   alloc irq_desc for 23 on node -1
[   43.318922]   alloc kstat_irqs on node -1
[   43.318946] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   43.319051] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   43.490277] hda_codec: ALC269: BIOS auto-probing.
[   43.490963] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   44.924715] lp: driver loaded but no devices found
[   45.058278] ppdev: user-space parallel port driver
[   89.714344] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[  121.065465] hda-intel: Invalid position buffer, using LPIB read method instead.
[  155.595791] wlan0: deauthenticating from 00:21:29:7e:3f:3e by local choice (reason=3)
[  155.607159] wlan0: direct probe to AP 00:21:29:7e:3f:3e (try 1)
[  155.611781] wlan0: direct probe responded
[  155.611796] wlan0: authenticate with AP 00:21:29:7e:3f:3e (try 1)
[  155.615239] wlan0: authenticated
[  155.615314] wlan0: associate with AP 00:21:29:7e:3f:3e (try 1)
[  155.619777] wlan0: RX AssocResp from 00:21:29:7e:3f:3e (capab=0x431 status=0 aid=2)
[  155.619790] wlan0: associated
[  155.620707] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  166.473224] wlan0: no IPv6 routers present
[  211.916117] uvcvideo: Failed to query (135) UVC control 4 (unit 3) : -32 (exp. 2).
[  212.427114] uvcvideo: Failed to query (135) UVC control 4 (unit 3) : -32 (exp. 2).
[ 2343.855847] kjournald starting.  Commit interval 5 seconds
[ 2343.857814] EXT3 FS on sda1, internal journal
[ 2343.857832] EXT3-fs: mounted filesystem with ordered data mode.
[ 2475.989268] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2475.989288] ata1.00: failed command: READ DMA
[ 2475.989310] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2475.989314]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2475.989323] ata1.00: status: { DRDY }
[ 2475.989351] ata1: soft resetting link
[ 2476.175339] ata1.00: configured for UDMA/100
[ 2476.175435] ata1.00: device reported invalid CHS sector 0
[ 2476.175622] ata1: EH complete
[ 2507.000352] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2507.000376] ata1.00: failed command: READ DMA
[ 2507.000405] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2507.000411]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2507.000425] ata1.00: status: { DRDY }
[ 2507.000465] ata1: soft resetting link
[ 2507.175192] ata1.00: configured for UDMA/100
[ 2507.175213] ata1.00: device reported invalid CHS sector 0
[ 2507.175252] ata1: EH complete
[ 2538.000132] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2538.000147] ata1.00: failed command: READ DMA
[ 2538.000165] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2538.000169]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2538.000177] ata1.00: status: { DRDY }
[ 2538.000206] ata1: soft resetting link
[ 2538.175224] ata1.00: configured for UDMA/100
[ 2538.175246] ata1.00: device reported invalid CHS sector 0
[ 2538.175285] ata1: EH complete
[ 2569.000138] ata1.00: limiting speed to UDMA/66:PIO4
[ 2569.000151] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2569.000164] ata1.00: failed command: READ DMA
[ 2569.000181] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2569.000185]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2569.000194] ata1.00: status: { DRDY }
[ 2569.000223] ata1: soft resetting link
[ 2569.178876] ata1.00: configured for UDMA/66
[ 2569.178896] ata1.00: device reported invalid CHS sector 0
[ 2569.178930] ata1: EH complete
[ 2600.000146] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2600.000164] ata1.00: failed command: READ DMA
[ 2600.000187] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2600.000192]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2600.000203] ata1.00: status: { DRDY }
[ 2600.000235] ata1: soft resetting link
[ 2600.180648] ata1.00: configured for UDMA/66
[ 2600.180738] ata1.00: device reported invalid CHS sector 0
[ 2600.180922] ata1: EH complete
[ 2631.000205] ata1.00: limiting speed to UDMA/33:PIO4
[ 2631.000226] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2631.000245] ata1.00: failed command: READ DMA
[ 2631.000274] ata1.00: cmd c8/00:00:e0:00:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2631.000280]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2631.000294] ata1.00: status: { DRDY }
[ 2631.000332] ata1: soft resetting link
[ 2631.174840] ata1.00: configured for UDMA/33
[ 2631.174868] ata1.00: device reported invalid CHS sector 0
[ 2631.174920] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2631.174942] sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[ 2631.174970] Descriptor sense data with sense descriptors (in hex):
[ 2631.174984]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2631.175043]         00 00 00 00 
[ 2631.175068] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[ 2631.175092] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 04 00 e0 00 01 00 00
[ 2631.175145] end_request: I/O error, dev sda, sector 262368
[ 2631.175168] Buffer I/O error on device sda, logical block 32796
[ 2631.175203] Buffer I/O error on device sda, logical block 32797
[ 2631.175223] Buffer I/O error on device sda, logical block 32798
[ 2631.175241] Buffer I/O error on device sda, logical block 32799
[ 2631.175259] Buffer I/O error on device sda, logical block 32800
[ 2631.175278] Buffer I/O error on device sda, logical block 32801
[ 2631.175296] Buffer I/O error on device sda, logical block 32802
[ 2631.175314] Buffer I/O error on device sda, logical block 32803
[ 2631.175333] Buffer I/O error on device sda, logical block 32804
[ 2631.175351] Buffer I/O error on device sda, logical block 32805
[ 2631.175448] ata1: EH complete
[ 2662.001326] ata1.00: limiting speed to PIO4
[ 2662.001343] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2662.001360] ata1.00: failed command: READ DMA
[ 2662.001383] ata1.00: cmd c8/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 dma 131072 in
[ 2662.001389]          res 40/00:01:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 2662.001400] ata1.00: status: { DRDY }
[ 2662.001432] ata1: soft resetting link
[ 2662.175205] ata1.00: configured for PIO4
[ 2662.175227] ata1.00: device reported invalid CHS sector 0
[ 2662.175265] ata1: EH complete
[ 2662.217186] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2662.217209] ata1.00: failed command: READ SECTOR(S)
[ 2662.217239] ata1.00: cmd 20/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 pio 131072 in
[ 2662.217245]          res 51/40:21:bf:02:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2662.217260] ata1.00: status: { DRDY ERR }
[ 2662.217270] ata1.00: error: { UNC }
[ 2662.239073] ata1.00: configured for PIO4
[ 2662.239134] ata1: EH complete
[ 2662.282070] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2662.282101] ata1.00: failed command: READ SECTOR(S)
[ 2662.282138] ata1.00: cmd 20/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 pio 131072 in
[ 2662.282143]          res 51/40:21:bf:02:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2662.282156] ata1.00: status: { DRDY ERR }
[ 2662.282165] ata1.00: error: { UNC }
[ 2662.303197] ata1.00: configured for PIO4
[ 2662.303244] ata1: EH complete
[ 2662.346704] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2662.346727] ata1.00: failed command: READ SECTOR(S)
[ 2662.346756] ata1.00: cmd 20/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 pio 131072 in
[ 2662.346763]          res 51/40:21:bf:02:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2662.346777] ata1.00: status: { DRDY ERR }
[ 2662.346788] ata1.00: error: { UNC }
[ 2662.362968] ata1.00: configured for PIO4
[ 2662.363015] ata1: EH complete
[ 2662.405174] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2662.405205] ata1.00: failed command: READ SECTOR(S)
[ 2662.405244] ata1.00: cmd 20/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 pio 131072 in
[ 2662.405252]          res 51/40:21:bf:02:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2662.405271] ata1.00: status: { DRDY ERR }
[ 2662.405284] ata1.00: error: { UNC }
[ 2662.427189] ata1.00: configured for PIO4
[ 2662.427236] ata1: EH complete
[ 2662.470585] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2662.470608] ata1.00: failed command: READ SECTOR(S)
[ 2662.470637] ata1.00: cmd 20/00:00:e0:01:04/00:00:00:00:00/e0 tag 0 pio 131072 in
[ 2662.470644]          res 51/40:21:bf:02:04/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 2662.470658] ata1.00: status: { DRDY ERR }
[ 2662.470669] ata1.00: error: { UNC }
[ 2662.492308] ata1.00: configured for PIO4
[ 2662.492412] sd 0:0:0:0: [sda] Unhandled sense code
[ 2662.492424] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2662.492440] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2662.492459] Descriptor sense data with sense descriptors (in hex):
[ 2662.492470]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2662.492512]         00 04 02 bf 
[ 2662.492530] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2662.492550] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 04 01 e0 00 01 00 00
[ 2662.492588] end_request: I/O error, dev sda, sector 262847
[ 2662.492602] __ratelimit: 22 callbacks suppressed
[ 2662.492614] Buffer I/O error on device sda, logical block 32855
[ 2662.492629] Buffer I/O error on device sda, logical block 32856
[ 2662.492641] Buffer I/O error on device sda, logical block 32857
[ 2662.492654] Buffer I/O error on device sda, logical block 32858
[ 2662.492666] Buffer I/O error on device sda, logical block 32859
[ 2662.492717] ata1: EH complete


```

---


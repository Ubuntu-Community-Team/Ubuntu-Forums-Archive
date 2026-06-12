---
title: "Computer suddenly shutting down with no warning"
date: 2009-05-02
forum: Hardware
---

### Post by Sarai the Geek on 2009-05-02
I upgraded to Jaunty a few days ago. Since then, my computer has twice shut off with no warning. One second it will be fine, the next it's dead. Both times it was running on battery power.
The first time (yesterday) I tried to turn it back on and nothing happened, so I assumed the battery had died, plugged it in, and it was fine. However, this time (about ten minutes ago) it had been completely charged when it died. I didn't try to restart it until it was plugged in.

Here's the system log from around the time it happened. I don't know a whole lot about reading logs so I can't find the relevant parts, sorry.

```
May  2 12:23:54 Sarai-Laptop kernel: [  842.769011] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:54 Sarai-Laptop kernel: [  842.770307] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:54 Sarai-Laptop kernel: [  842.771881] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:54 Sarai-Laptop kernel: [  842.773210] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:54 Sarai-Laptop kernel: [  842.775294] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:54 Sarai-Laptop kernel: [  842.775300] psmouse.c: issuing reconnect request
May  2 12:23:54 Sarai-Laptop kernel: [  842.775334] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  2 12:23:58 Sarai-Laptop kernel: [  846.802533] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:58 Sarai-Laptop kernel: [  846.804165] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:58 Sarai-Laptop kernel: [  846.805658] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:58 Sarai-Laptop kernel: [  846.807122] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:58 Sarai-Laptop kernel: [  846.808714] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 12:23:58 Sarai-Laptop kernel: [  846.808720] psmouse.c: issuing reconnect request
May  2 12:23:58 Sarai-Laptop kernel: [  846.808890] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  2 12:25:26 Sarai-Laptop python: hp-systray[5621]: warning: Qt/PyQt 4 initialization failed.
May  2 12:28:38 Sarai-Laptop kernel: [ 1127.524031] CE: hpet increasing min_delta_ns to 15000 nsec
May  2 12:38:49 Sarai-Laptop kernel: [ 1738.068405] python[5899]: segfault at 3c0c ip b6d0671b sp bfa990c0 error 4 in libgail.so[b6ce5000+40000]
May  2 12:42:48 Sarai-Laptop kernel: [ 1976.688582] python[6427]: segfault at 3c0c ip b6dbf71b sp bfc52270 error 4 in libgail.so[b6d9e000+40000]
May  2 12:44:48 Sarai-Laptop kernel: [ 2096.795680] python[6628]: segfault at 300c ip b6cff71b sp bff925b0 error 4 in libgail.so[b6cde000+40000]
May  2 12:47:31 Sarai-Laptop kernel: [ 2260.131671] python[6645]: segfault at 3c0c ip b6d8f71b sp bf823e40 error 4 in libgail.so[b6d6e000+40000]
May  2 12:48:35 Sarai-Laptop kernel: [ 2324.144394] python[6668]: segfault at 3c0c ip b6d1b71b sp bfdb0bd0 error 4 in libgail.so[b6cfa000+40000]
May  2 12:48:55 Sarai-Laptop kernel: [ 2343.710255] python[6682]: segfault at 2c0c ip b6cef71b sp bfe844a0 error 4 in libgail.so[b6cce000+40000]
May  2 12:49:53 Sarai-Laptop kernel: [ 2401.845318] python[6691]: segfault at 3c0c ip b6c8a71b sp bf81d640 error 4 in libgail.so[b6c69000+40000]
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.145083] usb 1-1: new high speed USB device using ehci_hcd and address 7
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.295212] usb 1-1: configuration #1 chosen from 1 choice
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.300971] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.1/input/input13
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.322841] Initializing USB Mass Storage driver...
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.325573] generic-usb 0003:1058:0705.0001: input,hidraw0: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:0b.1-1/input1
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.380069] scsi4 : SCSI emulation for USB Mass Storage devices
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.383232] usbcore: registered new interface driver usb-storage
May  2 12:53:22 Sarai-Laptop kernel: [ 2611.383244] USB Mass Storage support registered.
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.383946] scsi 4:0:0:0: Direct-Access     WD       3200BMV External 1.75 PQ: 0 ANSI: 4
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.385807] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.386819] sd 4:0:0:0: [sdb] Write Protect is off
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.387551] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.390755] sd 4:0:0:0: [sdb] Write Protect is off
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.390768]  sdb: sdb1
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.434340] sd 4:0:0:0: [sdb] Attached SCSI disk
May  2 12:53:27 Sarai-Laptop kernel: [ 2616.434409] sd 4:0:0:0: Attached scsi generic sg2 type 0
May  2 12:59:19 Sarai-Laptop syslogd 1.5.0#5ubuntu3: restart.
May  2 12:59:19 Sarai-Laptop kernel: Inspecting /boot/System.map-2.6.28-11-generic
May  2 12:59:19 Sarai-Laptop kernel: Cannot find map file.
May  2 12:59:19 Sarai-Laptop kernel: Loaded 74111 symbols from 40 modules.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009dc00/0009dc00
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Initializing cgroup subsys cpu
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] KERNEL supported cpus:
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Intel GenuineIntel
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   AMD AuthenticAMD
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   NSC Geode by NSC
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Cyrix CyrixInstead
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Centaur CentaurHauls
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Transmeta GenuineTMx86
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Transmeta TransmetaCPU
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   UMC UMC UMC UMC
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] BIOS-provided physical RAM map:
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 000000007bf00000 - 000000007bf0a000 (ACPI data)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 000000007bf0a000 - 000000007bf80000 (ACPI NVS)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] DMI present.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] last_pfn = 0x7bf00 max_arch_pfn = 0x100000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Scanning 2 areas for low memory corruption
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] modified physical RAM map:
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000090c00 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000007bf00000 (usable)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 000000007bf00000 - 000000007bf0a000 (ACPI data)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 000000007bf0a000 - 000000007bf80000 (ACPI NVS)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 000000007bf80000 - 0000000080000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] RAMDISK: 378c1000 - 37fefa4d
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fafa4d
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Move RAMDISK from 00000000378c1000 - 0000000037fefa4c to 00881000 - 00fafa4c
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: RSDP 000F8920, 0014 (r0 HP    )
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: RSDT 7BF00968, 0040 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: FACP 7BF09B16, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: DSDT 7BF009A8, 916E (r1 HP       MCP51M  6040000 MSFT  3000000)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: FACS 7BF0AFC0, 0040
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: SSDT 7BF09B8A, 0206 (r1 HP     POWERNOW  6040000  LTP        1)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: MCFG 7BF09D90, 003C (r1 HP       MCFG    6040000  LTP        0)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: HPET 7BF09DCC, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: APIC 7BF09E04, 005E (r1 HP     ^I APIC    6040000  LTP        0)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: BOOT 7BF09E62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: SLIC 7BF09E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] 1099MB HIGHMEM available.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] 883MB LOWMEM available.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   mapped low ram: 0 - 373fe000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   low ram: 00000000 - 373fe000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   bootmap 00012000 - 00018e80
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #5 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #7 [0000881000 - 0000fafa4d]      NEW RAMDISK ==> [0000881000 - 0000fafa4d]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] found SMP MP-table at [c00f89e0] 000f89e0
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Zone PFN ranges:
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]   HighMem  0x000373fe -> 0x0007bf00
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Movable zone start PFN for each node
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] early_node_map[4] active PFN ranges
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]     0: 0x00000010 -> 0x00000090
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0007bf00
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000090000 - 000000000009e000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503556
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Kernel command line: root=UUID=b93303ba-72c2-4efd-b5f0-481cd5c92dd1 ro quiet splash vga=791
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Initializing CPU#0
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Fast TSC calibration using PIT
May  2 12:59:19 Sarai-Laptop kernel: [    0.000000] Detected 1994.528 MHz processor.
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Console: colour dummy device 80x25
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] console [tty0] enabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] allocated 10152960 bytes of page_cgroup
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Memory: 1987436k/2030592k available (4126k kernel code, 41784k reserved, 2208k data, 532k init, 1125384k highmem)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] virtual kernel memory layout:
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.05 BogoMIPS (lpj=7978112)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Security Framework initialized
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] SELinux:  Disabled at boot.
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] AppArmor: AppArmor initialized
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Mount-cache hash table entries: 512
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Initializing cgroup subsys ns
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Initializing cgroup subsys memory
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Initializing cgroup subsys freezer
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: Processor Core ID: 0
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] using C1E aware idle routine
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
May  2 12:59:19 Sarai-Laptop kernel: [    0.017984] ACPI: Core revision 20080926
May  2 12:59:19 Sarai-Laptop kernel: [    0.020834] ACPI: Checking initramfs for custom DSDT
May  2 12:59:19 Sarai-Laptop kernel: [    0.308635] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May  2 12:59:19 Sarai-Laptop kernel: [    0.349662] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
May  2 12:59:19 Sarai-Laptop kernel: [    0.352001] Booting processor 1 APIC 0x1 ip 0x6000
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Initializing CPU#1
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3989.29 BogoMIPS (lpj=7978599)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
May  2 12:59:19 Sarai-Laptop kernel: [    0.004000] CPU: Processor Core ID: 1
May  2 12:59:19 Sarai-Laptop kernel: [    0.436176] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
May  2 12:59:19 Sarai-Laptop kernel: [    0.436230] Brought up 2 CPUs
May  2 12:59:19 Sarai-Laptop kernel: [    0.436232] Total of 2 processors activated (7978.35 BogoMIPS).
May  2 12:59:19 Sarai-Laptop kernel: [    0.436229] System has AMD C1E enabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.436229] Switch to broadcast mode on CPU1
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] Switch to broadcast mode on CPU0
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] net_namespace: 776 bytes
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] Booting paravirtualized kernel on bare hardware
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] Time: 20:58:57  Date: 05/02/09
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] regulator: core version 0.5
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] NET: Registered protocol family 16
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] EISA bus registered
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] ACPI: bus type pci registered
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] PCI: MCFG area at e0000000 reserved in E820
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] PCI: Using MMCONFIG for extended config space
May  2 12:59:19 Sarai-Laptop kernel: [    0.436423] PCI: Using configuration type 1 for base access
May  2 12:59:19 Sarai-Laptop kernel: [    0.466648] ACPI: BIOS _OSI(Linux) query ignored
May  2 12:59:19 Sarai-Laptop kernel: [    0.472024] ACPI: EC: non-query interrupt received, switching to interrupt mode
May  2 12:59:19 Sarai-Laptop kernel: [    0.472114] ACPI: Interpreter enabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.472118] ACPI: (supports S0 S3 S4 S5)
May  2 12:59:19 Sarai-Laptop kernel: [    0.472146] ACPI: Using IOAPIC for interrupt routing
May  2 12:59:19 Sarai-Laptop kernel: [    0.539194] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
May  2 12:59:19 Sarai-Laptop kernel: [    0.539194] ACPI: EC: driver started in interrupt mode
May  2 12:59:19 Sarai-Laptop kernel: [    0.539556] ACPI: ACPI Dock Station Driver: 1 docks/bays found
May  2 12:59:19 Sarai-Laptop kernel: [    0.539567] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  2 12:59:19 Sarai-Laptop kernel: [    0.539788] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.539791] pci 0000:00:02.0: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.539815] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.539817] pci 0000:00:03.0: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540086] pci 0000:00:0a.1: PME# supported from D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.540092] pci 0000:00:0a.1: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540240] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.540244] pci 0000:00:0b.0: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540299] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.540302] pci 0000:00:0b.1: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540494] pci 0000:00:10.1: PME# supported from D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.540498] pci 0000:00:10.1: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540554] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
May  2 12:59:19 Sarai-Laptop kernel: [    0.540557] pci 0000:00:14.0: PME# disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.540822] pci 0000:00:10.0: transparent bridge
May  2 12:59:19 Sarai-Laptop kernel: [    0.578695] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.578921] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *10 11 14 15)
May  2 12:59:19 Sarai-Laptop kernel: [    0.579142] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.579364] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.579586] ACPI: PCI Interrupt Link [LK1E] (IRQs 19) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.579805] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.580033] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *10
May  2 12:59:19 Sarai-Laptop kernel: [    0.580254] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.580475] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 20 22 23) *10
May  2 12:59:19 Sarai-Laptop kernel: [    0.580706] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 20 22 23) *11
May  2 12:59:19 Sarai-Laptop kernel: [    0.580926] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 20 22 23) *11
May  2 12:59:19 Sarai-Laptop kernel: [    0.581148] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 20 22 23) *7
May  2 12:59:19 Sarai-Laptop kernel: [    0.581370] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 20 22 23) *11
May  2 12:59:19 Sarai-Laptop kernel: [    0.581597] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.581818] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.582040] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.582262] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 20 22 23) *0, disabled.
May  2 12:59:19 Sarai-Laptop kernel: [    0.582491] ACPI: PCI Interrupt Link [LTID] (IRQs 21) *5
May  2 12:59:19 Sarai-Laptop kernel: [    0.582717] ACPI: PCI Interrupt Link [LSI1] (IRQs 21) *0
May  2 12:59:19 Sarai-Laptop kernel: [    0.582922] ACPI: WMI: Mapper loaded
May  2 12:59:19 Sarai-Laptop kernel: [    0.584113] SCSI subsystem initialized
May  2 12:59:19 Sarai-Laptop kernel: [    0.584120] usbcore: registered new interface driver usbfs
May  2 12:59:19 Sarai-Laptop kernel: [    0.584120] usbcore: registered new interface driver hub
May  2 12:59:19 Sarai-Laptop kernel: [    0.584120] usbcore: registered new device driver usb
May  2 12:59:19 Sarai-Laptop kernel: [    0.584120] PCI: Using ACPI for IRQ routing
May  2 12:59:19 Sarai-Laptop kernel: [    0.588013] Bluetooth: Core ver 2.13
May  2 12:59:19 Sarai-Laptop kernel: [    0.592013] NET: Registered protocol family 31
May  2 12:59:19 Sarai-Laptop kernel: [    0.592013] Bluetooth: HCI device and connection manager initialized
May  2 12:59:19 Sarai-Laptop kernel: [    0.592015] Bluetooth: HCI socket layer initialized
May  2 12:59:19 Sarai-Laptop kernel: [    0.592018] NET: Registered protocol family 8
May  2 12:59:19 Sarai-Laptop kernel: [    0.592019] NET: Registered protocol family 20
May  2 12:59:19 Sarai-Laptop kernel: [    0.592029] NetLabel: Initializing
May  2 12:59:19 Sarai-Laptop kernel: [    0.592031] NetLabel:  domain hash size = 128
May  2 12:59:19 Sarai-Laptop kernel: [    0.592032] NetLabel:  protocols = UNLABELED CIPSOv4
May  2 12:59:19 Sarai-Laptop kernel: [    0.592048] NetLabel:  unlabeled traffic allowed by default
May  2 12:59:19 Sarai-Laptop kernel: [    0.592063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
May  2 12:59:19 Sarai-Laptop kernel: [    0.592068] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
May  2 12:59:19 Sarai-Laptop kernel: [    0.596080] AppArmor: AppArmor Filesystem Enabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.604056] pnp: PnP ACPI init
May  2 12:59:19 Sarai-Laptop kernel: [    0.604064] ACPI: bus type pnp registered
May  2 12:59:19 Sarai-Laptop kernel: [    0.635824] pnp: PnP ACPI: found 13 devices
May  2 12:59:19 Sarai-Laptop kernel: [    0.635827] ACPI: ACPI bus type pnp unregistered
May  2 12:59:19 Sarai-Laptop kernel: [    0.635829] PnPBIOS: Disabled by ACPI PNP
May  2 12:59:19 Sarai-Laptop kernel: [    0.635838] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635845] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635848] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635851] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635853] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635859] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635865] system 00:04: ioport range 0x1000-0x107f has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635868] system 00:04: ioport range 0x1080-0x10ff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635871] system 00:04: ioport range 0x1400-0x147f has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635873] system 00:04: ioport range 0x1480-0x14ff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635876] system 00:04: ioport range 0x1800-0x187f has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635879] system 00:04: ioport range 0x1880-0x18ff has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635882] system 00:04: ioport range 0x2000-0x203f has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635887] system 00:05: ioport range 0x360-0x361 has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635890] system 00:05: ioport range 0x380-0x383 has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.635893] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
May  2 12:59:19 Sarai-Laptop kernel: [    0.670607] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
May  2 12:59:19 Sarai-Laptop kernel: [    0.670610] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
May  2 12:59:19 Sarai-Laptop kernel: [    0.670613] pci 0000:00:02.0:   MEM window: 0xc4000000-0xc7ffffff
May  2 12:59:19 Sarai-Laptop kernel: [    0.670616] pci 0000:00:02.0:   PREFETCH window: 0x000000c9000000-0x000000c91fffff
May  2 12:59:19 Sarai-Laptop kernel: [    0.670620] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
May  2 12:59:19 Sarai-Laptop kernel: [    0.670622] pci 0000:00:03.0:   IO window: disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.670625] pci 0000:00:03.0:   MEM window: 0xc8000000-0xc8ffffff
May  2 12:59:19 Sarai-Laptop kernel: [    0.670628] pci 0000:00:03.0:   PREFETCH window: 0x000000c9200000-0x000000c93fffff
May  2 12:59:19 Sarai-Laptop kernel: [    0.670632] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
May  2 12:59:19 Sarai-Laptop kernel: [    0.670633] pci 0000:00:10.0:   IO window: disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.670637] pci 0000:00:10.0:   MEM window: disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.670640] pci 0000:00:10.0:   PREFETCH window: disabled
May  2 12:59:19 Sarai-Laptop kernel: [    0.670661] bus: 00 index 0 io port: [0x00-0xffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670663] bus: 00 index 1 mmio: [0x000000-0xffffffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670665] bus: 01 index 0 io port: [0x4000-0x4fff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670668] bus: 01 index 1 mmio: [0xc4000000-0xc7ffffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670670] bus: 01 index 2 mmio: [0xc9000000-0xc91fffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670672] bus: 01 index 3 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670674] bus: 03 index 0 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670676] bus: 03 index 1 mmio: [0xc8000000-0xc8ffffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670678] bus: 03 index 2 mmio: [0xc9200000-0xc93fffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670680] bus: 03 index 3 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670682] bus: 07 index 0 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670684] bus: 07 index 1 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670685] bus: 07 index 2 mmio: [0x0-0x0]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670687] bus: 07 index 3 io port: [0x00-0xffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670689] bus: 07 index 4 mmio: [0x000000-0xffffffff]
May  2 12:59:19 Sarai-Laptop kernel: [    0.670700] NET: Registered protocol family 2
May  2 12:59:19 Sarai-Laptop kernel: [    0.681084] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.681372] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.682028] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    0.682375] TCP: Hash tables configured (established 131072 bind 65536)
May  2 12:59:19 Sarai-Laptop kernel: [    0.682377] TCP reno registered
May  2 12:59:19 Sarai-Laptop kernel: [    0.685114] NET: Registered protocol family 1
May  2 12:59:19 Sarai-Laptop kernel: [    0.685239] checking if image is initramfs... it is
May  2 12:59:19 Sarai-Laptop kernel: [    1.268014] Freeing initrd memory: 7354k freed
May  2 12:59:19 Sarai-Laptop kernel: [    1.268047] Simple Boot Flag at 0x36 set to 0x1
May  2 12:59:19 Sarai-Laptop kernel: [    1.268215] cpufreq: No nForce2 chipset.
May  2 12:59:19 Sarai-Laptop kernel: [    1.268338] audit: initializing netlink socket (disabled)
May  2 12:59:19 Sarai-Laptop kernel: [    1.268352] type=2000 audit(1241297937.265:1): initialized
May  2 12:59:19 Sarai-Laptop kernel: [    1.276335] highmem bounce pool size: 64 pages
May  2 12:59:19 Sarai-Laptop kernel: [    1.276341] HugeTLB registered 4 MB page size, pre-allocated 0 pages
May  2 12:59:19 Sarai-Laptop kernel: [    1.277609] VFS: Disk quotas dquot_6.5.1
May  2 12:59:19 Sarai-Laptop kernel: [    1.277666] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  2 12:59:19 Sarai-Laptop kernel: [    1.278264] fuse init (API version 7.10)
May  2 12:59:19 Sarai-Laptop kernel: [    1.278340] msgmni has been set to 1699
May  2 12:59:19 Sarai-Laptop kernel: [    1.278547] alg: No test for stdrng (krng)
May  2 12:59:19 Sarai-Laptop kernel: [    1.278559] io scheduler noop registered
May  2 12:59:19 Sarai-Laptop kernel: [    1.278561] io scheduler anticipatory registered
May  2 12:59:19 Sarai-Laptop kernel: [    1.278563] io scheduler deadline registered
May  2 12:59:19 Sarai-Laptop kernel: [    1.278578] io scheduler cfq registered (default)
May  2 12:59:19 Sarai-Laptop kernel: [    1.278592] pci 0000:00:00.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278630] pci 0000:00:02.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278640] pci 0000:00:03.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278671] pci 0000:00:09.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278757] pci 0000:00:0e.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278768] pci 0000:00:10.0: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.278780] pci 0000:00:10.1: Enabling HT MSI Mapping
May  2 12:59:19 Sarai-Laptop kernel: [    1.334612] pcieport-driver 0000:00:02.0: found MSI capability
May  2 12:59:19 Sarai-Laptop kernel: [    1.334705] pcieport-driver 0000:00:03.0: found MSI capability
May  2 12:59:19 Sarai-Laptop kernel: [    1.334784] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  2 12:59:19 Sarai-Laptop kernel: [    1.334795] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May  2 12:59:19 Sarai-Laptop kernel: [    1.335566] ACPI: AC Adapter [ACAD] (on-line)
May  2 12:59:19 Sarai-Laptop kernel: [    1.944804] ACPI: Battery Slot [BAT0] (battery present)
May  2 12:59:19 Sarai-Laptop kernel: [    1.944888] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
May  2 12:59:19 Sarai-Laptop kernel: [    1.944892] ACPI: Power Button (FF) [PWRF]
May  2 12:59:19 Sarai-Laptop kernel: [    1.944933] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
May  2 12:59:19 Sarai-Laptop kernel: [    1.944935] ACPI: Power Button (CM) [PWRB]
May  2 12:59:19 Sarai-Laptop kernel: [    1.944980] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
May  2 12:59:19 Sarai-Laptop kernel: [    1.944982] ACPI: Sleep Button (CM) [SLPB]
May  2 12:59:19 Sarai-Laptop kernel: [    1.945037] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
May  2 12:59:19 Sarai-Laptop kernel: [    1.945099] ACPI: Lid Switch [LID]
May  2 12:59:19 Sarai-Laptop kernel: [    1.945366] ACPI: processor limited to max C-state 1
May  2 12:59:19 Sarai-Laptop kernel: [    1.945393] processor ACPI_CPU:00: registered as cooling_device0
May  2 12:59:19 Sarai-Laptop kernel: [    1.945429] processor ACPI_CPU:01: registered as cooling_device1
May  2 12:59:19 Sarai-Laptop kernel: [    2.230821] thermal LNXTHERM:01: registered as thermal_zone0
May  2 12:59:19 Sarai-Laptop kernel: [    2.232561] ACPI: Thermal Zone [THRM] (62 C)
May  2 12:59:19 Sarai-Laptop kernel: [    2.232615] isapnp: Scanning for PnP cards...
May  2 12:59:19 Sarai-Laptop kernel: [    2.585363] isapnp: No Plug & Play device found
May  2 12:59:19 Sarai-Laptop kernel: [    2.597261] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
May  2 12:59:19 Sarai-Laptop kernel: [    2.598179] brd: module loaded
May  2 12:59:19 Sarai-Laptop kernel: [    2.598485] loop: module loaded
May  2 12:59:19 Sarai-Laptop kernel: [    2.598551] Fixed MDIO Bus: probed
May  2 12:59:19 Sarai-Laptop kernel: [    2.598557] PPP generic driver version 2.4.2
May  2 12:59:19 Sarai-Laptop kernel: [    2.598618] input: Macintosh mouse button emulation as /devices/virtual/input/input4
May  2 12:59:19 Sarai-Laptop kernel: [    2.598645] Driver 'sd' needs updating - please use bus_type methods
May  2 12:59:19 Sarai-Laptop kernel: [    2.598653] Driver 'sr' needs updating - please use bus_type methods
May  2 12:59:19 Sarai-Laptop kernel: [    2.599202] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
May  2 12:59:19 Sarai-Laptop kernel: [    2.599214] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 21 (level, high) -> IRQ 21
May  2 12:59:19 Sarai-Laptop kernel: [    2.599217] sata_nv 0000:00:0e.0: Using SWNCQ mode
May  2 12:59:19 Sarai-Laptop kernel: [    2.599446] scsi0 : sata_nv
May  2 12:59:19 Sarai-Laptop kernel: [    2.599564] scsi1 : sata_nv
May  2 12:59:19 Sarai-Laptop kernel: [    2.599718] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 21
May  2 12:59:19 Sarai-Laptop kernel: [    2.599721] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 21
May  2 12:59:19 Sarai-Laptop kernel: [    3.476065] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May  2 12:59:19 Sarai-Laptop kernel: [    3.484231] ata1.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
May  2 12:59:19 Sarai-Laptop kernel: [    3.484234] ata1.00: 312581808 sectors, multi 16: LBA48 
May  2 12:59:19 Sarai-Laptop kernel: [    3.500244] ata1.00: configured for UDMA/100
May  2 12:59:19 Sarai-Laptop kernel: [    4.234579] ata2: SATA link down (SStatus 0 SControl 300)
May  2 12:59:19 Sarai-Laptop kernel: [    4.234687] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
May  2 12:59:19 Sarai-Laptop kernel: [    4.234780] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
May  2 12:59:19 Sarai-Laptop kernel: [    4.234796] sd 0:0:0:0: [sda] Write Protect is off
May  2 12:59:19 Sarai-Laptop kernel: [    4.234823] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  2 12:59:19 Sarai-Laptop kernel: [    4.234893] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
May  2 12:59:19 Sarai-Laptop kernel: [    4.234907] sd 0:0:0:0: [sda] Write Protect is off
May  2 12:59:19 Sarai-Laptop kernel: [    4.234931] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  2 12:59:19 Sarai-Laptop kernel: [    4.234935]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
May  2 12:59:19 Sarai-Laptop kernel: [    4.320824] sd 0:0:0:0: [sda] Attached SCSI disk
May  2 12:59:19 Sarai-Laptop kernel: [    4.320874] sd 0:0:0:0: Attached scsi generic sg0 type 0
May  2 12:59:19 Sarai-Laptop kernel: [    4.321113] scsi2 : pata_amd
May  2 12:59:19 Sarai-Laptop kernel: [    4.321188] scsi3 : pata_amd
May  2 12:59:19 Sarai-Laptop kernel: [    4.321943] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
May  2 12:59:19 Sarai-Laptop kernel: [    4.321946] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
May  2 12:59:19 Sarai-Laptop kernel: [    4.508327] ata3.00: ATAPI: Slimtype DVD A  DS8A1H, WH66, max MWDMA2
May  2 12:59:19 Sarai-Laptop kernel: [    4.548278] ata3.00: configured for MWDMA2
May  2 12:59:19 Sarai-Laptop kernel: [    4.552393] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A1H    WH66 PQ: 0 ANSI: 5
May  2 12:59:19 Sarai-Laptop kernel: [    4.562890] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
May  2 12:59:19 Sarai-Laptop kernel: [    4.562893] Uniform CD-ROM driver Revision: 3.20
May  2 12:59:19 Sarai-Laptop kernel: [    4.563026] sr 2:0:0:0: Attached scsi generic sg1 type 5
May  2 12:59:19 Sarai-Laptop kernel: [    4.563519] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May  2 12:59:19 Sarai-Laptop kernel: [    4.563878] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
May  2 12:59:19 Sarai-Laptop kernel: [    4.563890] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 23 (level, high) -> IRQ 23
May  2 12:59:19 Sarai-Laptop kernel: [    4.563912] ehci_hcd 0000:00:0b.1: EHCI Host Controller
May  2 12:59:19 Sarai-Laptop kernel: [    4.563973] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
May  2 12:59:19 Sarai-Laptop kernel: [    4.564002] ehci_hcd 0000:00:0b.1: debug port 1
May  2 12:59:19 Sarai-Laptop kernel: [    4.564027] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xc0005000
May  2 12:59:19 Sarai-Laptop kernel: [    4.572035] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
May  2 12:59:19 Sarai-Laptop kernel: [    4.572108] usb usb1: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    4.572135] hub 1-0:1.0: USB hub found
May  2 12:59:19 Sarai-Laptop kernel: [    4.572143] hub 1-0:1.0: 8 ports detected
May  2 12:59:19 Sarai-Laptop kernel: [    4.572245] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May  2 12:59:19 Sarai-Laptop kernel: [    4.572593] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
May  2 12:59:19 Sarai-Laptop kernel: [    4.572602] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
May  2 12:59:19 Sarai-Laptop kernel: [    4.572616] ohci_hcd 0000:00:0b.0: OHCI Host Controller
May  2 12:59:19 Sarai-Laptop kernel: [    4.572656] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
May  2 12:59:19 Sarai-Laptop kernel: [    4.572683] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
May  2 12:59:19 Sarai-Laptop kernel: [    4.630076] usb usb2: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    4.630099] hub 2-0:1.0: USB hub found
May  2 12:59:19 Sarai-Laptop kernel: [    4.630109] hub 2-0:1.0: 8 ports detected
May  2 12:59:19 Sarai-Laptop kernel: [    4.630207] uhci_hcd: USB Universal Host Controller Interface driver
May  2 12:59:19 Sarai-Laptop kernel: [    4.630265] usbcore: registered new interface driver libusual
May  2 12:59:19 Sarai-Laptop kernel: [    4.630297] usbcore: registered new interface driver usbserial
May  2 12:59:19 Sarai-Laptop kernel: [    4.630308] USB Serial support registered for generic
May  2 12:59:19 Sarai-Laptop kernel: [    4.630320] usbcore: registered new interface driver usbserial_generic
May  2 12:59:19 Sarai-Laptop kernel: [    4.630322] usbserial: USB Serial Driver core
May  2 12:59:19 Sarai-Laptop kernel: [    4.630365] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
May  2 12:59:19 Sarai-Laptop kernel: [    4.645061] serio: i8042 KBD port at 0x60,0x64 irq 1
May  2 12:59:19 Sarai-Laptop kernel: [    4.645068] serio: i8042 AUX port at 0x60,0x64 irq 12
May  2 12:59:19 Sarai-Laptop kernel: [    4.648058] mice: PS/2 mouse device common for all mice
May  2 12:59:19 Sarai-Laptop kernel: [    4.669099] rtc_cmos 00:09: RTC can wake from S4
May  2 12:59:19 Sarai-Laptop kernel: [    4.669129] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
May  2 12:59:19 Sarai-Laptop kernel: [    4.669168] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
May  2 12:59:19 Sarai-Laptop kernel: [    4.669226] device-mapper: uevent: version 1.0.3
May  2 12:59:19 Sarai-Laptop kernel: [    4.669329] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
May  2 12:59:19 Sarai-Laptop kernel: [    4.669481] device-mapper: multipath: version 1.0.5 loaded
May  2 12:59:19 Sarai-Laptop kernel: [    4.669484] device-mapper: multipath round-robin: version 1.0.0 loaded
May  2 12:59:19 Sarai-Laptop kernel: [    4.669589] EISA: Probing bus 0 at eisa.0
May  2 12:59:19 Sarai-Laptop kernel: [    4.669595] Cannot allocate resource for EISA slot 1
May  2 12:59:19 Sarai-Laptop kernel: [    4.669597] Cannot allocate resource for EISA slot 2
May  2 12:59:19 Sarai-Laptop kernel: [    4.669599] Cannot allocate resource for EISA slot 3
May  2 12:59:19 Sarai-Laptop kernel: [    4.669601] Cannot allocate resource for EISA slot 4
May  2 12:59:19 Sarai-Laptop kernel: [    4.669614] EISA: Detected 0 cards.
May  2 12:59:19 Sarai-Laptop kernel: [    4.669713] cpuidle: using governor ladder
May  2 12:59:19 Sarai-Laptop kernel: [    4.669715] cpuidle: using governor menu
May  2 12:59:19 Sarai-Laptop kernel: [    4.670193] TCP cubic registered
May  2 12:59:19 Sarai-Laptop kernel: [    4.670288] NET: Registered protocol family 10
May  2 12:59:19 Sarai-Laptop kernel: [    4.670680] lo: Disabled Privacy Extensions
May  2 12:59:19 Sarai-Laptop kernel: [    4.670977] NET: Registered protocol family 17
May  2 12:59:19 Sarai-Laptop kernel: [    4.670993] Bluetooth: L2CAP ver 2.11
May  2 12:59:19 Sarai-Laptop kernel: [    4.670995] Bluetooth: L2CAP socket layer initialized
May  2 12:59:19 Sarai-Laptop kernel: [    4.670997] Bluetooth: SCO (Voice Link) ver 0.6
May  2 12:59:19 Sarai-Laptop kernel: [    4.670999] Bluetooth: SCO socket layer initialized
May  2 12:59:19 Sarai-Laptop kernel: [    4.671050] Bluetooth: RFCOMM socket layer initialized
May  2 12:59:19 Sarai-Laptop kernel: [    4.671056] Bluetooth: RFCOMM TTY layer initialized
May  2 12:59:19 Sarai-Laptop kernel: [    4.671058] Bluetooth: RFCOMM ver 1.10
May  2 12:59:19 Sarai-Laptop kernel: [    4.671111] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
May  2 12:59:19 Sarai-Laptop kernel: [    4.671155] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
May  2 12:59:19 Sarai-Laptop kernel: [    4.671158] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
May  2 12:59:19 Sarai-Laptop kernel: [    4.671160] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
May  2 12:59:19 Sarai-Laptop kernel: [    4.671162] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
May  2 12:59:19 Sarai-Laptop kernel: [    4.671214] Using IPI No-Shortcut mode
May  2 12:59:19 Sarai-Laptop kernel: [    4.671298] registered taskstats version 1
May  2 12:59:19 Sarai-Laptop kernel: [    4.671433]   Magic number: 9:706:1002
May  2 12:59:19 Sarai-Laptop kernel: [    4.671477] system 00:04: hash matches
May  2 12:59:19 Sarai-Laptop kernel: [    4.671543] rtc_cmos 00:09: setting system clock to 2009-05-02 20:59:01 UTC (1241297941)
May  2 12:59:19 Sarai-Laptop kernel: [    4.671546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May  2 12:59:19 Sarai-Laptop kernel: [    4.671548] EDD information not available.
May  2 12:59:19 Sarai-Laptop kernel: [    4.671903] Freeing unused kernel memory: 532k freed
May  2 12:59:19 Sarai-Laptop kernel: [    4.672072] Write protecting the kernel text: 4128k
May  2 12:59:19 Sarai-Laptop kernel: [    4.672125] Write protecting the kernel read-only data: 1532k
May  2 12:59:19 Sarai-Laptop kernel: [    4.679681] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
May  2 12:59:19 Sarai-Laptop kernel: [    4.745473] vesafb: framebuffer at 0xd0000000, mapped to 0xf7d00000, using 3072k, total 65536k
May  2 12:59:19 Sarai-Laptop kernel: [    4.745477] vesafb: mode is 1024x768x16, linelength=2048, pages=1
May  2 12:59:19 Sarai-Laptop kernel: [    4.745480] vesafb: protected mode interface info at c000:d750
May  2 12:59:19 Sarai-Laptop kernel: [    4.745483] vesafb: pmi: set display start = c00cd786, set palette = c00cd7f0
May  2 12:59:19 Sarai-Laptop kernel: [    4.745485] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
May  2 12:59:19 Sarai-Laptop kernel: [    4.745496] vesafb: scrolling: redraw
May  2 12:59:19 Sarai-Laptop kernel: [    4.745499] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
May  2 12:59:19 Sarai-Laptop kernel: [    4.745583] Console: switching to colour frame buffer device 128x48
May  2 12:59:19 Sarai-Laptop kernel: [    4.772557] fb0: VESA VGA frame buffer device
May  2 12:59:19 Sarai-Laptop kernel: [    4.888041] usb 1-1: new high speed USB device using ehci_hcd and address 2
May  2 12:59:19 Sarai-Laptop kernel: [    5.021254] usb 1-1: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    5.025275] Initializing USB Mass Storage driver...
May  2 12:59:19 Sarai-Laptop kernel: [    5.025380] scsi4 : SCSI emulation for USB Mass Storage devices
May  2 12:59:19 Sarai-Laptop kernel: [    5.025466] usbcore: registered new interface driver usb-storage
May  2 12:59:19 Sarai-Laptop kernel: [    5.025469] USB Mass Storage support registered.
May  2 12:59:19 Sarai-Laptop kernel: [    5.029197] usbcore: registered new interface driver hiddev
May  2 12:59:19 Sarai-Laptop kernel: [    5.029992] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.1/input/input6
May  2 12:59:19 Sarai-Laptop kernel: [    5.036110] generic-usb 0003:1058:0705.0001: input,hidraw0: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:0b.1-1/input1
May  2 12:59:19 Sarai-Laptop kernel: [    5.036123] usbcore: registered new interface driver usbhid
May  2 12:59:19 Sarai-Laptop kernel: [    5.036126] usbhid: v2.6:USB HID core driver
May  2 12:59:19 Sarai-Laptop kernel: [    5.132032] usb 1-2: new high speed USB device using ehci_hcd and address 3
May  2 12:59:19 Sarai-Laptop kernel: [    5.256533] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
May  2 12:59:19 Sarai-Laptop kernel: [    5.256913] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
May  2 12:59:19 Sarai-Laptop kernel: [    5.256925] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
May  2 12:59:19 Sarai-Laptop kernel: [    5.266502] usb 1-2: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    5.266583] hub 1-2:1.0: USB hub found
May  2 12:59:19 Sarai-Laptop kernel: [    5.266678] hub 1-2:1.0: 4 ports detected
May  2 12:59:19 Sarai-Laptop kernel: [    5.680036] usb 2-7: new full speed USB device using ohci_hcd and address 2
May  2 12:59:19 Sarai-Laptop kernel: [    5.777193] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:1b:26:af
May  2 12:59:19 Sarai-Laptop kernel: [    5.777197] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
May  2 12:59:19 Sarai-Laptop kernel: [    5.912486] usb 2-7: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    5.990199] usb 1-2.1: new high speed USB device using ehci_hcd and address 5
May  2 12:59:19 Sarai-Laptop kernel: [    6.000740] PM: Starting manual resume from disk
May  2 12:59:19 Sarai-Laptop kernel: [    6.004359] EXT3-fs: INFO: recovery required on readonly filesystem.
May  2 12:59:19 Sarai-Laptop kernel: [    6.004362] EXT3-fs: write access will be enabled during recovery.
May  2 12:59:19 Sarai-Laptop kernel: [    6.090384] usb 1-2.1: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    6.165290] usb 1-2.2: new full speed USB device using ehci_hcd and address 6
May  2 12:59:19 Sarai-Laptop kernel: [    6.258132] usb 1-2.2: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [    6.333194] usb 1-2.3: new full speed USB device using ehci_hcd and address 7
May  2 12:59:19 Sarai-Laptop kernel: [    6.427388] usb 1-2.3: configuration #1 chosen from 1 choice
May  2 12:59:19 Sarai-Laptop kernel: [   10.026334] scsi 4:0:0:0: Direct-Access     WD       3200BMV External 1.75 PQ: 0 ANSI: 4
May  2 12:59:19 Sarai-Laptop kernel: [   10.027565] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  2 12:59:19 Sarai-Laptop kernel: [   10.028209] sd 4:0:0:0: [sdb] Write Protect is off
May  2 12:59:19 Sarai-Laptop kernel: [   10.029189] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
May  2 12:59:19 Sarai-Laptop kernel: [   10.030185] sd 4:0:0:0: [sdb] Write Protect is off
May  2 12:59:19 Sarai-Laptop kernel: [   10.030501]  sdb: sdb1
May  2 12:59:19 Sarai-Laptop kernel: [   10.033229] sd 4:0:0:0: [sdb] Attached SCSI disk
May  2 12:59:19 Sarai-Laptop kernel: [   10.033292] sd 4:0:0:0: Attached scsi generic sg2 type 0
May  2 12:59:19 Sarai-Laptop kernel: [   11.281259] kjournald starting.  Commit interval 5 seconds
May  2 12:59:19 Sarai-Laptop kernel: [   11.281281] EXT3-fs: sda1: orphan cleanup on readonly fs
May  2 12:59:19 Sarai-Laptop kernel: [   11.281346] EXT3-fs: sda1: 3 orphan inodes deleted
May  2 12:59:19 Sarai-Laptop kernel: [   11.281348] EXT3-fs: recovery complete.
May  2 12:59:19 Sarai-Laptop kernel: [   11.292402] EXT3-fs: mounted filesystem with ordered data mode.
May  2 12:59:19 Sarai-Laptop kernel: [   17.810799] udev: starting version 141
May  2 12:59:19 Sarai-Laptop kernel: [   18.143101] acpi device:2d: registered as cooling_device2
May  2 12:59:19 Sarai-Laptop kernel: [   18.143351] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/input/input7
May  2 12:59:19 Sarai-Laptop kernel: [   18.165176] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
May  2 12:59:19 Sarai-Laptop kernel: [   18.236697] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
May  2 12:59:19 Sarai-Laptop kernel: [   18.236740] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
May  2 12:59:19 Sarai-Laptop kernel: [   19.011685] wl: module license '' taints kernel.
May  2 12:59:19 Sarai-Laptop kernel: [   19.014173] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 19
May  2 12:59:19 Sarai-Laptop kernel: [   19.014186] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
May  2 12:59:19 Sarai-Laptop kernel: [   19.258611] Linux agpgart interface v0.103
May  2 12:59:19 Sarai-Laptop kernel: [   19.441611] Bluetooth: Generic Bluetooth USB driver ver 0.3
May  2 12:59:19 Sarai-Laptop kernel: [   19.441730] usbcore: registered new interface driver btusb
May  2 12:59:19 Sarai-Laptop kernel: [   19.499362] input: PC Speaker as /devices/platform/pcspkr/input/input8
May  2 12:59:19 Sarai-Laptop kernel: [   19.513517] Linux video capture interface: v2.00
May  2 12:59:19 Sarai-Laptop kernel: [   19.541742] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.79.10
May  2 12:59:19 Sarai-Laptop kernel: [   19.548944] wacom: probe of 1-2.3:1.0 failed with error -113
May  2 12:59:19 Sarai-Laptop kernel: [   19.549786] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.1/input/input9
May  2 12:59:19 Sarai-Laptop kernel: [   19.553095] usbcore: registered new interface driver wacom
May  2 12:59:19 Sarai-Laptop kernel: [   19.553117] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
May  2 12:59:19 Sarai-Laptop kernel: [   19.933809] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
May  2 12:59:19 Sarai-Laptop kernel: [   19.933824] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
May  2 12:59:19 Sarai-Laptop kernel: [   19.954226] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
May  2 12:59:19 Sarai-Laptop kernel: [   19.955235] input: HP Webcam as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.1/1-2.1:1.0/input/input10
May  2 12:59:19 Sarai-Laptop kernel: [   20.078990] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  2 12:59:19 Sarai-Laptop kernel: [   20.116256] usbcore: registered new interface driver uvcvideo
May  2 12:59:19 Sarai-Laptop kernel: [   20.116281] USB Video Class driver (v0.1.0)
May  2 12:59:19 Sarai-Laptop kernel: [   20.912398] nvidia 0000:00:05.0: power state changed by ACPI to D0
May  2 12:59:19 Sarai-Laptop kernel: [   20.912802] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
May  2 12:59:19 Sarai-Laptop kernel: [   20.912815] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
May  2 12:59:19 Sarai-Laptop kernel: [   20.913143] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
May  2 12:59:19 Sarai-Laptop kernel: [   21.059863] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
May  2 12:59:19 Sarai-Laptop kernel: [   21.101876] lp: driver loaded but no devices found
May  2 12:59:19 Sarai-Laptop kernel: [   21.121173] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
May  2 12:59:19 Sarai-Laptop kernel: [   21.217815] Adding 5871716k swap on /dev/sda5.  Priority:-1 extents:1 across:5871716k
May  2 12:59:19 Sarai-Laptop kernel: [   21.436998] EXT3 FS on sda1, internal journal
May  2 12:59:19 Sarai-Laptop kernel: [   21.820506] type=1505 audit(1241297958.648:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2273
May  2 12:59:19 Sarai-Laptop kernel: [   21.873082] type=1505 audit(1241297958.700:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2277
May  2 12:59:19 Sarai-Laptop kernel: [   21.873217] type=1505 audit(1241297958.700:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2277
May  2 12:59:19 Sarai-Laptop kernel: [   21.873268] type=1505 audit(1241297958.700:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2277
May  2 12:59:19 Sarai-Laptop kernel: [   21.873316] type=1505 audit(1241297958.700:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2277
May  2 12:59:19 Sarai-Laptop kernel: [   22.025065] type=1505 audit(1241297958.853:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2282
May  2 12:59:19 Sarai-Laptop kernel: [   22.025260] type=1505 audit(1241297958.853:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2282
May  2 12:59:19 Sarai-Laptop kernel: [   22.055811] type=1505 audit(1241297958.881:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2286
May  2 12:59:25 Sarai-Laptop kernel: [   28.463637] vboxdrv: fAsync=1 offMin=0x2a0a offMax=0x2a0a
May  2 12:59:25 Sarai-Laptop kernel: [   28.463685] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
May  2 12:59:27 Sarai-Laptop kernel: [   30.450254] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  2 12:59:27 Sarai-Laptop kernel: [   30.450258] Bluetooth: BNEP filters: protocol multicast
May  2 12:59:27 Sarai-Laptop kernel: [   30.533112] Bridge firewalling registered
May  2 12:59:28 Sarai-Laptop kernel: [   32.091837] ppdev: user-space parallel port driver
May  2 12:59:32 Sarai-Laptop kernel: [   35.172975] eth0: no link during initialization.
May  2 12:59:32 Sarai-Laptop kernel: [   35.173428] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  2 13:00:06 Sarai-Laptop python: hp-systray[3861]: warning: Qt/PyQt 4 initialization failed.
May  2 13:00:27 Sarai-Laptop pulseaudio[4456]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
May  2 13:00:27 Sarai-Laptop pulseaudio[4456]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
May  2 13:00:27 Sarai-Laptop pulseaudio[4456]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
May  2 13:00:32 Sarai-Laptop kernel: [   95.501450] Clocksource tsc unstable (delta = -100476118 ns)
May  2 13:02:48 Sarai-Laptop kernel: [  231.468640] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.470218] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.471537] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.472853] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.484423] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
May  2 13:02:48 Sarai-Laptop kernel: [  231.639041] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.640635] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.642079] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.643478] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.644768] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
May  2 13:02:48 Sarai-Laptop kernel: [  231.644774] psmouse.c: issuing reconnect request
May  2 13:02:48 Sarai-Laptop kernel: [  231.644895] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
May  2 13:04:20 Sarai-Laptop bonobo-activation-server (sarai-5201): could not associate with desktop session: Failed to connect to socket /tmp/dbus-CHtqXqiGWf: Connection refused
```

My computer info is in my signature, and it is fully up to date according to the update manager.

---

### Post by Sarai the Geek on 2009-05-02
*bump* :)

---

### Post by mdurham on 2009-05-02
Simple suggestion, as a first step, try running the live CD for a while and see if that shuts down too.

---

### Post by pastalavista on 2009-05-02
Laptops will do that if they overheat. Mine has done it recently while watching Flash vids in Firefox. I have taken to running the acpi temp meter in screenlets to monitor how hot it gets.. pause the vid when the temp reaches 100C. It has only happened since I upgraded to 9.04 because (I think) the ATI graphic driver isn't up to the job. The old flgrx drivers worked better but they won't work in Jaunty so the processor is now handling a lot more graphics that it did before.

---

### Post by Sarai the Geek on 2009-05-02
> **mdurham said:**
> Simple suggestion, as a first step, try running the live CD for a while and see if that shuts down too.

Well, for reasons too weird to get into I've spent most of my day on live CDs, mostly Linux Mint and Xubuntu. I don't at the current time posses an Ubuntu live cd (gave my only one to a friend) but I can burn another.

> **pastalavista said:**
> Laptops will do that if they overheat. Mine has done it recently while watching Flash vids in Firefox. I have taken to running the acpi temp meter in screenlets to monitor how hot it gets.. pause the vid when the temp reaches 100C. It has only happened since I upgraded to 9.04 because (I think) the ATI graphic driver isn't up to the job. The old flgrx drivers worked better but they won't work in Jaunty so the processor is now handling a lot more graphics that it did before.

That was my first thought, but because I've been burned in the past (literally) by hot laptops I'm very careful about temperature- I've got panel applets that monitor HD, CPU, and GPU temperatures along with an acpi temperature guage in Conky. Under a heavy load (boxee, virtualbox, handbrake etc) it's never gone above 90 degrees and I usually use my chillmat when doing these things. As far as these crashes, it wasn't under anything I'd consider a heavy load compared to the paces I sometimes put it through- nothing more than my usual rhythymbox, firefox, thunderbird, and pidgin.

---

### Post by Fir3chi3f on 2009-05-03
It maybe unrelated but, I had a desktop that had the same problem of sudden reboots.

I did what mdurham was saying

Running off of a liveCD worked for hours but running window$ or ubuntu off the hard drive would make it reboot. -dying harddrive

I was doing the same thing your doing too, keeping temp monitors on everything.

Good luck

---

### Post by Sarai the Geek on 2009-05-03
> **Fir3chi3f said:**
> It maybe unrelated but, I had a desktop that had the same problem of sudden reboots.

I did what mdurham was saying

Running off of a liveCD worked for hours but running window$ or ubuntu off the hard drive would make it reboot. -dying harddrive

I was doing the same thing your doing too keeping temp monitors on everything.

Good luck

Well that's just my frigging luck. This is laptop number 2 that hasn't even lasted a year. It's so annoying how it's almost always cheaper to replace it than to get it fixed, especially with this computer since it's got massive cracks in the screen, a dead usb port, and a cd-rom drive that randomly decides to shut off. Oi.

Good thing I will be getting a new Ubuntastic sys76 pangolin for mah b-day in July!

---

### Post by blackened on 2009-05-03
> **Sarai the Geek said:**
> ...Good thing I will be getting a new Ubuntastic sys76 pangolin for mah b-day in July!

I'm green with envy. We should all be so lucky. :P

I use my eee (average temps of 55+ C = warm) more than all my other machines combined. It's only 5 months old, but I need something with a little more battery life, so I will likely sell it in lieu of buying a 901.

---

### Post by Sarai the Geek on 2009-05-03
> **blackened said:**
> I'm green with envy. We should all be so lucky. :P

I know! I'm so excited...

---


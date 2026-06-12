---
title: "partition problems"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by natman on 2009-05-28
Hi,
When i go to boot up my ubuntu just hangs for like 1osec then boots as normal, im pretty sure i know what the problem is but i cant fix it. This is what i think the problem is
> natman@natman-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bcb0fb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       19628   156122112    7  HPFS/NTFS
/dev/sda3           19629       20920    10377990   83  Linux
/dev/sda4           20921       38913   144528772+   5  Extended
/dev/sda5           20921       21163     1951866   82  Linux swap / Solaris
/dev/sda6           21164       38913   142576843+  83  Linux
natman@natman-laptop:~$

Im guessing that partition does not end on cylinder boundary thing is bad? How do i fix it, i tried a tool called testdisk but have no idea how to use it. Please help!

---

### Post by Mark Phelps on 2009-05-28
Before you mess with sda1, would be best to find out what's in it.

Your partition list shows NTFS -- so are you running Vista or XP?

I'm guessing that you bought this machine with the OS preinstalled.  If that's correct, then sda1 is likely to be a "recovery partition" supplied by the vendor.  In which case, you should most definitely NOT mess with it.

---

### Post by rehilliard on 2009-05-28
Once the ubuntu logo shows up, press alt-f1 and watch the console or look at the logs after you login.

---

### Post by natman on 2009-05-28
Ya i bought my laptop with vista pre installed onto it, there was one vista recovery partiton, a C drive partition, then a data partition. I wiped the data one and that where i put ubuntu. I have made all my recovery disks for vista also.
But this problem at boot up is weird, after grub i get the message, booting from hda0,ext3 "big list of numbers" this stays for about 10sec then boots into kubuntu as normal. Whats that 10sec delay for?

---

### Post by natman on 2009-05-28
I tried pressing alt+F1 at the logo i couldn't see any failures or weird things, but then again it was very fast.
Is my problem a normal problem?

---

### Post by hal8000 on 2009-05-28
I'm not convinced that the cylinder boundary is the problem. I got jaunty installed and mine wizzes through and boots in 20 secs as measured with bootchart. To top it all I have Solaris and FreeBSD primary partitions and the FreeBSD entry does not end on cylinder boundary.

anc@orac:~$ sudo fdisk -l
[sudo] password for anc: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8001b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650        8669     8193150   bf  Solaris
/dev/sda3            8670       10194    12249121+  a5  FreeBSD
Partition 3 does not end on cylinder boundary.
/dev/sda4           10194       19929    78196797+   5  Extended
/dev/sda5           10194       10255      490392   82  Linux swap / Solaris
/dev/sda6           10256       11147     7164958+  83  Linux
/dev/sda7           11148       11876     5855661   83  Linux
/dev/sda8           11877       12849     7815591   83  Linux
/dev/sda9           12850       13822     7815591   83  Linux
--snip--


Check the system clock, reboot and then check the output of /var/log/messages
This is much easier done from Gnome by going to System, Admin, Log file viewer. Perhaps there is something in the message log that can help track down the problem

---

### Post by natman on 2009-05-28
Ok i just did a restart and timed it with my watch, the time from after grub selects ubuntu to the start of the graphical loader ( ie the bar is just about to start moving to the right ) is 23 sec! To me that seems like 23 sec of wasted time. The only message it displays is
"boot from (hd0,2) ext3 long number sequence
Starting up....."

Also here is the start of the content of /var/log/message
> May 28 02:03:23 natman-laptop syslogd 1.5.0#5ubuntu3: restart.
May 28 02:32:40 natman-laptop -- MARK --
May 28 02:52:40 natman-laptop -- MARK --
May 28 02:56:57 natman-laptop exiting on signal 15
May 28 13:37:57 natman-laptop syslogd 1.5.0#5ubuntu3: restart.
May 28 13:37:57 natman-laptop kernel: Inspecting /boot/System.map-2.6.28-11-generic
May 28 13:37:57 natman-laptop kernel: Cannot find map file.
May 28 13:37:57 natman-laptop kernel: Loaded 56625 symbols from 53 modules.
May 28 13:37:57 natman-laptop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
May 28 13:37:57 natman-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
May 28 13:37:57 natman-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
May 28 13:37:57 natman-laptop kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
May 28 13:37:57 natman-laptop kernel: [    0.000000] KERNEL supported cpus:
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Intel GenuineIntel
May 28 13:37:57 natman-laptop kernel: [    0.000000]   AMD AuthenticAMD
May 28 13:37:57 natman-laptop kernel: [    0.000000]   NSC Geode by NSC
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Cyrix CyrixInstead
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Centaur CentaurHauls
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
May 28 13:37:57 natman-laptop kernel: [    0.000000]   UMC UMC UMC UMC
May 28 13:37:57 natman-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7b6c000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7b6c000 - 00000000b7bbf000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7bbf000 - 00000000b7c86000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7c86000 - 00000000b7cbf000 (ACPI NVS)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7cbf000 - 00000000b7cec000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7cec000 - 00000000b7cff000 (ACPI data)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7cff000 - 00000000b7d00000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000b7d00000 - 00000000c0000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000] DMI 2.4 present.
May 28 13:37:57 natman-laptop kernel: [    0.000000] last_pfn = 0xb7d00 max_arch_pfn = 0x100000
May 28 13:37:57 natman-laptop kernel: [    0.000000] Scanning 2 areas for low memory corruption
May 28 13:37:57 natman-laptop kernel: [    0.000000] modified physical RAM map:
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000091000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000b7b6c000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7b6c000 - 00000000b7bbf000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7bbf000 - 00000000b7c86000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7c86000 - 00000000b7cbf000 (ACPI NVS)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7cbf000 - 00000000b7cec000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7cec000 - 00000000b7cff000 (ACPI data)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7cff000 - 00000000b7d00000 (usable)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000b7d00000 - 00000000c0000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
May 28 13:37:57 natman-laptop kernel: [    0.000000] RAMDISK: 378c1000 - 37fef9a4
May 28 13:37:57 natman-laptop kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00faf9a4
May 28 13:37:57 natman-laptop kernel: [    0.000000] Move RAMDISK from 00000000378c1000 - 0000000037fef9a3 to 00881000 - 00faf9a3
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: RSDP 000FE020, 0024 (r2 TOSINV)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: XSDT B7CFE120, 0064 (r1 TOSINV TOSINV00        1       1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: FACP B7CFD000, 00F4 (r4 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: DSDT B7CEF000, 90BA (r1 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: FACS B7C93000, 0040
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: HPET B7CFC000, 0038 (r1 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: APIC B7CFB000, 006C (r2 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: MCFG B7CFA000, 003C (r1 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: ASF! B7CF9000, 00A5 (r32 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: SLIC B7CEE000, 0176 (r1 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: BOOT B7CED000, 0028 (r1 TOSINV TOSINV00        1 MSFT  1000013)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: SSDT B7CEC000, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117)
May 28 13:37:57 natman-laptop kernel: [    0.000000] 2057MB HIGHMEM available.
May 28 13:37:57 natman-laptop kernel: [    0.000000] 883MB LOWMEM available.
May 28 13:37:57 natman-laptop kernel: [    0.000000]   mapped low ram: 0 - 373fe000
May 28 13:37:57 natman-laptop kernel: [    0.000000]   low ram: 00000000 - 373fe000
May 28 13:37:57 natman-laptop kernel: [    0.000000]   bootmap 00012000 - 00018e80
May 28 13:37:57 natman-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #5 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #7 [0000881000 - 0000faf9a4]      NEW RAMDISK ==> [0000881000 - 0000faf9a4]
May 28 13:37:57 natman-laptop kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
May 28 13:37:57 natman-laptop kernel: [    0.000000] Zone PFN ranges:
May 28 13:37:57 natman-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
May 28 13:37:57 natman-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
May 28 13:37:57 natman-laptop kernel: [    0.000000]   HighMem  0x000373fe -> 0x000b7d00
May 28 13:37:57 natman-laptop kernel: [    0.000000] Movable zone start PFN for each node
May 28 13:37:57 natman-laptop kernel: [    0.000000] early_node_map[7] active PFN ranges
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x00000007
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000b7b6c
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x000b7bbf -> 0x000b7c86
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x000b7cbf -> 0x000b7cec
May 28 13:37:57 natman-laptop kernel: [    0.000000]     0: 0x000b7cff -> 0x000b7d00
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
May 28 13:37:57 natman-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 28 13:37:57 natman-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May 28 13:37:57 natman-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
May 28 13:37:57 natman-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 28 13:37:57 natman-laptop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009e000
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May 28 13:37:57 natman-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May 28 13:37:57 natman-laptop kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000)
May 28 13:37:57 natman-laptop kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
May 28 13:37:57 natman-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746730
May 28 13:37:57 natman-laptop kernel: [    0.000000] Kernel command line: root=UUID=9234a81f-e276-4b5a-ad15-6561959eac4c ro quiet splash 
May 28 13:37:57 natman-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 28 13:37:57 natman-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 28 13:37:57 natman-laptop kernel: [    0.000000] Initializing CPU#0
May 28 13:37:57 natman-laptop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
May 28 13:37:57 natman-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May 28 13:37:57 natman-laptop kernel: [    0.000000] Fast TSC calibration using PIT
May 28 13:37:57 natman-laptop kernel: [    0.000000] Detected 1995.056 MHz processor.
May 28 13:37:57 natman-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
May 28 13:37:57 natman-laptop kernel: [    0.004000] console [tty0] enabled
May 28 13:37:57 natman-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May 28 13:37:57 natman-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May 28 13:37:57 natman-laptop kernel: [    0.004000] allocated 15057920 bytes of page_cgroup
May 28 13:37:57 natman-laptop kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
May 28 13:37:57 natman-laptop kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
May 28 13:37:57 natman-laptop kernel: [    0.004000] Memory: 2955240k/3011584k available (4126k kernel code, 54372k reserved, 2208k data, 532k init, 2105740k highmem)
May 28 13:37:57 natman-laptop kernel: [    0.004000] virtual kernel memory layout:
May 28 13:37:57 natman-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
May 28 13:37:57 natman-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
May 28 13:37:57 natman-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
May 28 13:37:57 natman-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May 28 13:37:57 natman-laptop kernel: [    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
May 28 13:37:57 natman-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.11 BogoMIPS (lpj=7980224)
May 28 13:37:57 natman-laptop kernel: [    0.004000] Security Framework initialized
May 28 13:37:57 natman-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
May 28 13:37:57 natman-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
May 28 13:37:57 natman-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
May 28 13:37:57 natman-laptop kernel: [    0.004000] Initializing cgroup subsys ns
May 28 13:37:57 natman-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
May 28 13:37:57 natman-laptop kernel: [    0.004000] Initializing cgroup subsys memory
May 28 13:37:57 natman-laptop kernel: [    0.004000] Initializing cgroup subsys freezer
May 28 13:37:57 natman-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
May 28 13:37:57 natman-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
May 28 13:37:57 natman-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
May 28 13:37:57 natman-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
May 28 13:37:57 natman-laptop kernel: [    0.004000] using mwait in idle threads.
May 28 13:37:57 natman-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
May 28 13:37:57 natman-laptop kernel: [    0.018495] ACPI: Core revision 20080926
May 28 13:37:57 natman-laptop kernel: [    0.021692] ACPI: Checking initramfs for custom DSDT
May 28 13:37:57 natman-laptop kernel: [    0.324438] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 28 13:37:57 natman-laptop kernel: [    0.367452] CPU0: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz stepping 0a
May 28 13:37:57 natman-laptop kernel: [    0.368001] Booting processor 1 APIC 0x1 ip 0x6000
The file was too large to attach or paste in:

---

### Post by presence1960 on 2009-05-28
> **natman said:**
> Ok i just did a restart and timed it with my watch, the time from after grub selects ubuntu to the start of the graphical loader ( ie the bar is just about to start moving to the right ) is 23 sec! To me that seems like 23 sec of wasted time. The only message it displays is
"boot from (hd0,2) ext3 long number sequence
Starting up....."

Also here is the start of the content of /var/log/message

The file was too large to attach or paste in:

That long number and letter sequence is the UUID of your partition. That is normal for something like this to display after selecting an option to boot :```
 boot from (hd0,2) ext3 8319981e-03bb-4bd9-9d2e-276da66b4f1c
```

I use Jaunty now, with Hardy installed as a backup. Using ext 4 on Jaunty my bootchart reading is 13 seconds. I never noticed how slowly the other versions boot because I had nothing fast to compare them to. After using Jaunty if I boot into Hardy I am keenly aware of the difference. Pre-Jaunty I thought nothing of it-that was just how life was.

---

### Post by natman on 2009-05-29
Thats my whole point i am using jaunty now ( fresh install ext3 ) and i still get this hang of about 20sec before the actual booting starts ( the blue bar moving to the right part ). Does anyone know why this is?

---

### Post by binary10 on 2009-05-29
> **natman said:**
> Thats my whole point i am using jaunty now ( fresh install ext3 ) and i still get this hang of about 20sec before the actual booting starts ( the blue bar moving to the right part ). Does anyone know why this is?

Sounds like the unpacking and setting up of initrd,

you could always duplicate/create a dummy boot grub entry and modify your root line to point to something bad.. and check to see if you get the busybox commandline up.

---

### Post by natman on 2009-05-29
Thanks but i have no idea how do such a thing? Still seems weird i cant actually find what the problem is.

---


---
title: "Only 4 GB RAM detected from 8 GB"
date: 2010-07-20
forum: Hardware
---

### Post by andrei2 on 2010-07-20
Hi,
  
  I have Intel Core i5 750 PC with MSI P55-CD53 mainboard.
  Installed Mint 9 (based on Ubuntu 10.04) with 4GB RAM - all hardware was smoothly recognized.
  Then I've upgraded my RAM from 4 to 8 GB (4x2GB DDR3).
  
  Bios detects/reports all 8192MB (ok).
  Windows CPUZ app reports 8192MB  (ok).
  
  BUT! 
  Ubuntu (Mint) 10.04 64 bit detects 4GB only. :cry:
  
  I've tried to add mem=8192M option to /etc/default/grub, but it didn't helped.
  
  Any idea how to convince Ubuntu to use all of the available RAM?
  
  uname -a:
  ```

 *Linux pinguin 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
 *
```free -m:
  ```

 *andrei@pinguin ~ $ free -m
 *** * * * * * total * * * used * * * free * * shared * *buffers * * cached
 *Mem: * * * * *3954 * * * 1129 * * * 2824 * * * * *0 * * * * 70 * * * *317
 *-/+ buffers/cache: * * * *741 * * * 3212
 *Swap: * * * * 9571 * * * * *0 * * * 9571
 *
 *
```dmesg:
  ```

 *[ * *0.000000] Initializing cgroup subsys cpuset
 *[ * *0.000000] Initializing cgroup subsys cpu
 *[ * *0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
 *[ * *0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=c5385312-1295-410a-b839-d50c7eae3e04 ro vga=792 mem=8192M
 *[ * *0.000000] KERNEL supported cpus:
 *[ * *0.000000] * Intel GenuineIntel
 *[ * *0.000000] * AMD AuthenticAMD
 *[ * *0.000000] * Centaur CentaurHauls
 *[ * *0.000000] BIOS-provided physical RAM map:
 *[ * *0.000000] *BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
 *[ * *0.000000] *BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
 *[ * *0.000000] *BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 *[ * *0.000000] *BIOS-e820: 0000000000100000 - 00000000cf780000 (usable)
 *[ * *0.000000] *BIOS-e820: 00000000cf780000 - 00000000cf78e000 (ACPI data)
 *[ * *0.000000] *BIOS-e820: 00000000cf78e000 - 00000000cf7d0000 (ACPI NVS)
 *[ * *0.000000] *BIOS-e820: 00000000cf7d0000 - 00000000cf7e0000 (reserved)
 *[ * *0.000000] *BIOS-e820: 00000000cf7ed000 - 00000000d0000000 (reserved)
 *[ * *0.000000] *BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 *[ * *0.000000] *BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
 *[ * *0.000000] *BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
 *[ * *0.000000] user-defined physical RAM map:
 *[ * *0.000000] *user: 0000000000000000 - 000000000009e800 (usable)
 *[ * *0.000000] *user: 000000000009e800 - 00000000000a0000 (reserved)
 *[ * *0.000000] *user: 00000000000e0000 - 0000000000100000 (reserved)
 *[ * *0.000000] *user: 0000000000100000 - 00000000cf780000 (usable)
 *[ * *0.000000] *user: 00000000cf780000 - 00000000cf78e000 (ACPI data)
 *[ * *0.000000] *user: 00000000cf78e000 - 00000000cf7d0000 (ACPI NVS)
 *[ * *0.000000] *user: 00000000cf7d0000 - 00000000cf7e0000 (reserved)
 *[ * *0.000000] *user: 00000000cf7ed000 - 00000000d0000000 (reserved)
 *[ * *0.000000] *user: 00000000fee00000 - 00000000fee01000 (reserved)
 *[ * *0.000000] *user: 00000000ffe00000 - 0000000100000000 (reserved)
 *[ * *0.000000] *user: 0000000100000000 - 0000000130000000 (usable)
 *[ * *0.000000] DMI present.
 *[ * *0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
 *[ * *0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
 *[ * *0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
 *[ * *0.000000] MTRR default type: uncachable
 *[ * *0.000000] MTRR fixed ranges enabled:
 *[ * *0.000000] * 00000-9FFFF write-back
 *[ * *0.000000] * A0000-BFFFF uncachable
 *[ * *0.000000] * C0000-CFFFF write-protect
 *[ * *0.000000] * D0000-DFFFF uncachable
 *[ * *0.000000] * E0000-E7FFF write-protect
 *[ * *0.000000] * E8000-EFFFF write-through
 *[ * *0.000000] * F0000-FFFFF write-protect
 *[ * *0.000000] MTRR variable ranges enabled:
 *[ * *0.000000] * 0 base 000000000 mask F00000000 write-back
 *[ * *0.000000] * 1 base 100000000 mask FE0000000 write-back
 *[ * *0.000000] * 2 base 120000000 mask FF0000000 write-back
 *[ * *0.000000] * 3 base 0D0000000 mask FF0000000 uncachable
 *[ * *0.000000] * 4 base 0E0000000 mask FE0000000 uncachable
 *[ * *0.000000] * 5 disabled
 *[ * *0.000000] * 6 disabled
 *[ * *0.000000] * 7 disabled
 *[ * *0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
 *[ * *0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
 *[ * *0.000000] last_pfn = 0xcf780 max_arch_pfn = 0x400000000
 *[ * *0.000000] Scanning 0 areas for low memory corruption
 *[ * *0.000000] modified physical RAM map:
 *[ * *0.000000] *modified: 0000000000000000 - 0000000000010000 (reserved)
 *[ * *0.000000] *modified: 0000000000010000 - 000000000009e800 (usable)
 *[ * *0.000000] *modified: 000000000009e800 - 00000000000a0000 (reserved)
 *[ * *0.000000] *modified: 00000000000e0000 - 0000000000100000 (reserved)
 *[ * *0.000000] *modified: 0000000000100000 - 00000000cf780000 (usable)
 *[ * *0.000000] *modified: 00000000cf780000 - 00000000cf78e000 (ACPI data)
 *[ * *0.000000] *modified: 00000000cf78e000 - 00000000cf7d0000 (ACPI NVS)
 *[ * *0.000000] *modified: 00000000cf7d0000 - 00000000cf7e0000 (reserved)
 *[ * *0.000000] *modified: 00000000cf7ed000 - 00000000d0000000 (reserved)
 *[ * *0.000000] *modified: 00000000fee00000 - 00000000fee01000 (reserved)
 *[ * *0.000000] *modified: 00000000ffe00000 - 0000000100000000 (reserved)
 *[ * *0.000000] *modified: 0000000100000000 - 0000000130000000 (usable)
 *[ * *0.000000] initial memory mapped : 0 - 20000000
 *[ * *0.000000] init_memory_mapping: 0000000000000000-00000000cf780000
 *[ * *0.000000] NX (Execute Disable) protection: active
 *[ * *0.000000] *0000000000 - 00cf600000 page 2M
 *[ * *0.000000] *00cf600000 - 00cf780000 page 4k
 *[ * *0.000000] kernel direct mapping tables up to cf780000 @ 10000-16000
 *[ * *0.000000] init_memory_mapping: 0000000100000000-0000000130000000
 *[ * *0.000000] NX (Execute Disable) protection: active
 *[ * *0.000000] *0100000000 - 0130000000 page 2M
 *[ * *0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
 *[ * *0.000000] RAMDISK: 371fb000 - 37feff46
 *[ * *0.000000] ACPI: RSDP 00000000000fa560 00014 (v00 ACPIAM)
 *[ * *0.000000] ACPI: RSDT 00000000cf780000 00040 (v01 7586MS A7586100 20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: FACP 00000000cf780200 00084 (v01 7586MS A7586100 20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: DSDT 00000000cf7805e0 07419 (v01 *A7586 A7586100 00000100 INTL 20051117)
 *[ * *0.000000] ACPI: FACS 00000000cf78e000 00040
 *[ * *0.000000] ACPI: APIC 00000000cf780390 0008C (v01 7586MS A7586100 20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: MCFG 00000000cf780420 0003C (v01 7586MS OEMMCFG *20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: OEMB 00000000cf78e040 00072 (v01 7586MS A7586100 20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: HPET 00000000cf78a5e0 00038 (v01 7586MS OEMHPET *20100624 MSFT 00000097)
 *[ * *0.000000] ACPI: DMAR 00000000cf78e0c0 00100 (v01 * *AMI *OEMDMAR 00000001 MSFT 00000097)
 *[ * *0.000000] ACPI: SSDT 00000000cf78f7f0 00363 (v01 DpgPmm * *CpuPm 00000012 INTL 20051117)
 *[ * *0.000000] ACPI: Local APIC address 0xfee00000
 *[ * *0.000000] No NUMA configuration found
 *[ * *0.000000] Faking a node at 0000000000000000-0000000130000000
 *[ * *0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
 *[ * *0.000000] * NODE_DATA [0000000000015000 - 0000000000019fff]
 *[ * *0.000000] * bootmap [000000000001a000 - *000000000003ffff] pages 26
 *[ * *0.000000] (8 early reservations) ==> bootmem [0000000000 - 0130000000]
 *[ * *0.000000] * #0 [0000000000 - 0000001000] * BIOS data page ==> [0000000000 - 0000001000]
 *[ * *0.000000] * #1 [0000006000 - 0000008000] * * * TRAMPOLINE ==> [0000006000 - 0000008000]
 *[ * *0.000000] * #2 [0001000000 - 0001a29e64] * *TEXT DATA BSS ==> [0001000000 - 0001a29e64]
 *[ * *0.000000] * #3 [00371fb000 - 0037feff46] * * * * *RAMDISK ==> [00371fb000 - 0037feff46]
 *[ * *0.000000] * #4 [000009e800 - 0000100000] * *BIOS reserved ==> [000009e800 - 0000100000]
 *[ * *0.000000] * #5 [0001a2a000 - 0001a2a10b] * * * * * * *BRK ==> [0001a2a000 - 0001a2a10b]
 *[ * *0.000000] * #6 [0000010000 - 0000014000] * * * * *PGTABLE ==> [0000010000 - 0000014000]
 *[ * *0.000000] * #7 [0000014000 - 0000015000] * * * * *PGTABLE ==> [0000014000 - 0000015000]
 *[ * *0.000000] found SMP MP-table at [ffff8800000ff780] ff780
 *[ * *0.000000] *[ffffea0000000000-ffffea00043fffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
 *[ * *0.000000] Zone PFN ranges:
 *[ * *0.000000] * DMA * * *0x00000010 -> 0x00001000
 *[ * *0.000000] * DMA32 * *0x00001000 -> 0x00100000
 *[ * *0.000000] * Normal * 0x00100000 -> 0x00130000
 *[ * *0.000000] Movable zone start PFN for each node
 *[ * *0.000000] early_node_map[3] active PFN ranges
 *[ * *0.000000] * * 0: 0x00000010 -> 0x0000009e
 *[ * *0.000000] * * 0: 0x00000100 -> 0x000cf780
 *[ * *0.000000] * * 0: 0x00100000 -> 0x00130000
 *[ * *0.000000] On node 0 totalpages: 1046286
 *[ * *0.000000] * DMA zone: 56 pages used for memmap
 *[ * *0.000000] * DMA zone: 105 pages reserved
 *[ * *0.000000] * DMA zone: 3821 pages, LIFO batch:0
 *[ * *0.000000] * DMA32 zone: 14280 pages used for memmap
 *[ * *0.000000] * DMA32 zone: 831416 pages, LIFO batch:31
 *[ * *0.000000] * Normal zone: 2688 pages used for memmap
 *[ * *0.000000][ * *0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
 *[ * *0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
 *[ * *0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
 *[ * *0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
 *[ * *0.000000] PM: Registered nosave memory: 00000000cf780000 - 00000000cf78e000
 *[ * *0.000000] PM: Registered nosave memory: 00000000cf78e000 - 00000000cf7d0000
 *[ * *0.000000] PM: Registered nosave memory: 00000000cf7d0000 - 00000000cf7e0000
 *[ * *0.000000] PM: Registered nosave memory: 00000000cf7e0000 - 00000000cf7ed000
 *[ * *0.000000] PM: Registered nosave memory: 00000000cf7ed000 - 00000000d0000000
 *[ * *0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fee00000
 *[ * *0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
 *[ * *0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
 *[ * *0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
 *[ * *0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ee00000)
 *[ * *0.000000] Booting paravirtualized kernel on bare hardware
 *[ * *0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
 *[ * *0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u262144
 *[ * *0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
 *[ * *0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
 *[ * *0.000000] Built 1 zonelists in Node order, mobility grouping on. *Total pages: 1029157
 *[ * *0.000000] Policy zone: Normal
 *[ * *0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=c5385312-1295-410a-b839-d50c7eae3e04 ro vga=792 mem=8192M
 *[ * *0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
 *[ * *0.000000] Initializing CPU#0
 *[ * *0.000000] Checking aperture...
 *[ * *0.000000] No AGP bridge found
 *[ * *0.000000] Calgary: detecting Calgary via BIOS EBDA area
 *[ * *0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
 *[ * *0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
 *[ * *0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
 *[ * *0.000000] software IO TLB at phys 0x20000000 - 0x24000000
 *[ * *0.000000] Memory: 4033888k/4980736k available (5409k kernel code, 795592k absent, 151256k reserved, 2976k data, 876k init)
 *** Normal zone: 193920 pages, LIFO batch:31
 *
 *
```


<update>
This was a hardware issue: the CPU was not properly installed in the mainboard - it seems that some pins (from the memory controller?) was not connected. So at the end, mainboard has shown all 8 GB but CPU was not able to connect to the second RAM pair.
After moving CPU on the sockel a little bit I saw all the 8 GB.
Thanks all for the help, and sorry for the trouble.
Regards,
Andrei*
</update>

---

### Post by cascade9 on 2010-07-21
Looks like you are using the 'generic' kernel. You want the PAE kernel. 

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by andrei2 on 2010-07-21
> **cascade9 said:**
> Looks like you are using the 'generic' kernel. You want the PAE kernel. 

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Yes, because I'm using 64 bit kernel, which does not need PAE tricks.

Any other suggestions?

---

### Post by cascade9 on 2010-07-21
Thats what I get for not readign the whole output fo "uname -a". (in fairness, I get  'amd64' where you got 'generic')

---

### Post by PresenceofMind on 2010-07-21
> **andrei2 said:**
> Hi,

I have Intel Core i5 750 PC with MSI P55-CD53 mainboard.
Installed Mint 9 (based on Ubuntu 10.04) with 4GB RAM - all hardware was  smoothly recognized.
Then I've upgraded my RAM from 4 to 8 GB (4x2GB DDR3).

Bios detects/reports all 8192MB (ok).
Windows CPUZ app reports 8192MB  (ok).

BUT! 
Ubuntu (Mint) 10.04 64 bit detects 4GB only. :cry:

I've tried to add mem=8192M option to /etc/default/grub, but it didn't  helped.

Any idea how to convince Ubuntu to use all of the available RAM?

uname -a:
```

Linux pinguin 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC  2010 x86_64 GNU/Linux

```free -m:
```

andrei@pinguin ~ $ free -m
             total       used       free     shared    buffers      cached
Mem:          3954       1129       2824          0         70         317
-/+ buffers/cache:        741       3212
Swap:         9571          0       9571


```dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc  version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16  08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic  root=UUID=c5385312-1295-410a-b839-d50c7eae3e04 ro vga=792 mem=8192M
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000  (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000  (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf780000 (usable)
[    0.000000]  BIOS-e820: 00000000cf780000 - 00000000cf78e000 (ACPI  data)
[    0.000000]  BIOS-e820: 00000000cf78e000 - 00000000cf7d0000 (ACPI  NVS)
[    0.000000]  BIOS-e820: 00000000cf7d0000 - 00000000cf7e0000  (reserved)
[    0.000000]  BIOS-e820: 00000000cf7ed000 - 00000000d0000000  (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000  (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000  (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] user-defined physical RAM map:
[    0.000000]  user: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  user: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  user: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  user: 0000000000100000 - 00000000cf780000 (usable)
[    0.000000]  user: 00000000cf780000 - 00000000cf78e000 (ACPI data)
[    0.000000]  user: 00000000cf78e000 - 00000000cf7d0000 (ACPI NVS)
[    0.000000]  user: 00000000cf7d0000 - 00000000cf7e0000 (reserved)
[    0.000000]  user: 00000000cf7ed000 - 00000000d0000000 (reserved)
[    0.000000]  user: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  user: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  user: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working  around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000  (usable) ==> (reserved)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new  0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000  (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcf780 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cf780000 (usable)
[    0.000000]  modified: 00000000cf780000 - 00000000cf78e000 (ACPI  data)
[    0.000000]  modified: 00000000cf78e000 - 00000000cf7d0000 (ACPI NVS)
[    0.000000]  modified: 00000000cf7d0000 - 00000000cf7e0000 (reserved)
[    0.000000]  modified: 00000000cf7ed000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cf780000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00cf600000 page 2M
[    0.000000]  00cf600000 - 00cf780000 page 4k
[    0.000000] kernel direct mapping tables up to cf780000 @ 10000-16000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @  14000-1a000
[    0.000000] RAMDISK: 371fb000 - 37feff46
[    0.000000] ACPI: RSDP 00000000000fa560 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cf780000 00040 (v01 7586MS A7586100  20100624 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cf780200 00084 (v01 7586MS A7586100  20100624 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cf7805e0 07419 (v01  A7586 A7586100  00000100 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cf78e000 00040
[    0.000000] ACPI: APIC 00000000cf780390 0008C (v01 7586MS A7586100  20100624 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cf780420 0003C (v01 7586MS OEMMCFG   20100624 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cf78e040 00072 (v01 7586MS A7586100  20100624 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cf78a5e0 00038 (v01 7586MS OEMHPET   20100624 MSFT 00000097)
[    0.000000] ACPI: DMAR 00000000cf78e0c0 00100 (v01    AMI  OEMDMAR  00000001 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cf78f7f0 00363 (v01 DpgPmm    CpuPm  00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000015000 - 0000000000019fff]
[    0.000000]   bootmap [000000000001a000 -  000000000003ffff] pages 26
[    0.000000] (8 early reservations) ==> bootmem [0000000000 -  0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==>  [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==>  [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==>  [0001000000 - 0001a29e64]
[    0.000000]   #3 [00371fb000 - 0037feff46]          RAMDISK ==>  [00371fb000 - 0037feff46]
[    0.000000]   #4 [000009e800 - 0000100000]    BIOS reserved ==>  [000009e800 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a10b]              BRK ==>  [0001a2a000 - 0001a2a10b]
[    0.000000]   #6 [0000010000 - 0000014000]          PGTABLE ==>  [0000010000 - 0000014000]
[    0.000000]   #7 [0000014000 - 0000015000]          PGTABLE ==>  [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD ->  [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cf780
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1046286
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3821 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 831416 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000][    0.000000] PM: Registered nosave memory:  000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 -  00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 -  00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 -  0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cf780000 -  00000000cf78e000
[    0.000000] PM: Registered nosave memory: 00000000cf78e000 -  00000000cf7d0000
[    0.000000] PM: Registered nosave memory: 00000000cf7d0000 -  00000000cf7e0000
[    0.000000] PM: Registered nosave memory: 00000000cf7e0000 -  00000000cf7ed000
[    0.000000] PM: Registered nosave memory: 00000000cf7ed000 -  00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 -  00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 -  00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 -  00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 -  0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap:  d0000000:2ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544  r8192 d23144 u262144
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.   Total pages: 1029157
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic  root=UUID=c5385312-1295-410a-b839-d50c7eae3e04 ro vga=792 mem=8192M
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA -  bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 -  ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4033888k/4980736k available (5409k kernel code,  795592k absent, 151256k reserved, 2976k data, 876k init)
   Normal zone: 193920 pages, LIFO batch:31


```

Hmmmm....

According to the MTRR output on your report, Sections 5, 6 & 7 are disabled. Since it's the variable range, I think the CPU might extend it when the need arises. Until the need comes, the range is set to use 4GB at the moment. So the system software must have access to 4GB (which is cached) right now and, hence, the reason for your system only seeing 4GB. Things like BIOS and software used to probe (like CPU-Z) are exempt from this.

Someone correct me if i'm wrong.....

If it doesn't cause you any inconvenience, can you post the results after typing this into your terminal?

```
top
```

---

### Post by andrei2 on 2010-07-21
> **PresenceofMind said:**
> Probably, until the need comes, the range is set to use 4GB at the moment.

But what I supposed to do to allow system to see/access the disabled 4gb?

Is this link somehow related: [http://www.phoronix.com/forums/showthread.php?t=21871]("http://www.phoronix.com/forums/showthread.php?t=21871")?

---

### Post by PresenceofMind on 2010-07-21
> **andrei2 said:**
> But what I supposed to do to allow system to see/access the disabled 4gb?

Is this link somehow related: [http://www.phoronix.com/forums/showthread.php?t=21871](http://www.phoronix.com/forums/showthread.php?t=21871)?

Physically change the MTRR values....they are the ones that set the range of "visible" memory available for use.....

Type this your Terminal and see what you get:

```
cat /proc/mtrr
```

According to your link, it may have other complications...

---

### Post by andrei2 on 2010-07-21
> **PresenceofMind said:**
> Physically change the MTRR values....


How?

Here is the output:
```

cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back
reg02: base=0x120000000 ( 4608MB), size=  256MB, count=1: write-back
reg04: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable

```

---

### Post by PresenceofMind on 2010-07-21
Hello again,

Exactly how you change an MTRR value is beyond my reach =(.....
I need someone else's help here, as it involves adding lines to your Grub file. 

Are you sure you are using the 64-bit Kernel?.... it should be normally read as 'AMD-64' (As pointed out by Cascade9) Have you checked your system monitor?

---

### Post by andrei2 on 2010-07-22
> **PresenceofMind said:**
> 
Are you sure you are using the 64-bit Kernel?.... it should be normally read as 'AMD-64' (As pointed out by Cascade9) Have you checked your system monitor?

Yes, I'm sure. Initially I've installed 32 bit Mint distro and saw only 3.5 GB RAM (from 4), then I've installed 64 bit and got 3.9 (from 4). 

After that, for some reason I've simply assumed that with today's Linuxes there should be no issue to run even more RAM (8 GB) - and now I see that this is not (always) true. Sadly, I hoped to leave Windows forever, but it seems that without guru's help the only solution is back to Windows 7 64 bit.

I've even tried to install 2.6.35 64 bit kernel, but the result was same (or worse) - the memory reported on the prompt is still 4 GB, but additionally I can not get Gnome to start.

I guess that there should be some clever kernel parameter/switches to allow me to use all 8 Gig? Has anybody any idea?

---


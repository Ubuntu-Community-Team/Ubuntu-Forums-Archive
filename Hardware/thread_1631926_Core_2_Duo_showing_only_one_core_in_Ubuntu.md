---
title: "Core 2 Duo showing only one core in Ubuntu"
date: 2010-11-27
forum: Hardware
---

### Post by wiznillyp on 2010-11-27
I have a MacBook PRO 7.1 and just re-installed Ubuntu on it this week-end.  The first install showed two CPUs in **System Monitor**, but this one does not. Looks like only one CPU is available.

Here is my output to **uname -a**
```
Linux WillBookPro 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux
```Output to **cat /proc/cpuinfo**
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping    : 10
cpu MHz        : 798.000
cache size    : 3072 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dts tpr_shadow vnmi flexpriority
bogomips    : 4778.30
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```lshw does show 2 CPUs.  Any ideas on what to check?

---

### Post by Fafler on 2010-11-27
Output uname -a instead of uname -r
Also, 
```
cat /var/log/messages | grep "log source" -m 1 -A 300 | tee bootlog.txt

```
And post the file here.

---

### Post by wiznillyp on 2010-11-27
I changed the uname -r to uname -a info  just before you posted, see edit in original post.  Thanks.

Here is the log information (I will just post here, since the file exceeds the forum limits...):```
Nov 26 08:20:49 WillBookPro kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 26 08:20:49 WillBookPro rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="748" x-info="http://www.rsyslog.com"] (re)start
Nov 26 08:20:49 WillBookPro rsyslogd: rsyslogd's groupid changed to 103
Nov 26 08:20:49 WillBookPro rsyslogd: rsyslogd's userid changed to 101
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a7cc948c-326a-4cf5-aaba-6122d66b7498 ro quiet splash
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000af000000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000af000000 - 00000000bf000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bf000000 - 00000000bf70f000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bf70f000 - 00000000bf930000 (ACPI NVS)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bf930000 - 00000000bf931000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bf931000 - 00000000bf939000 (ACPI NVS)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bf939000 - 00000000bfef9000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000d3400000 - 00000000d3401000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] DMI 2.4 present.
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] No AGP bridge found
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] last_pfn = 0xbf70f max_arch_pfn = 0x400000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] modified physical RAM map:
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 0000000000100000 - 00000000af000000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000af000000 - 00000000bf000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bf000000 - 00000000bf70f000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bf70f000 - 00000000bf930000 (ACPI NVS)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bf930000 - 00000000bf931000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bf931000 - 00000000bf939000 (ACPI NVS)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bf939000 - 00000000bfef9000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bfef9000 - 00000000bfeff000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000bfeff000 - 00000000bff00000 (ACPI data)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000d3400000 - 00000000d3401000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bf70f000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] RAMDISK: 37571000 - 37ff0000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 APPLE )
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: XSDT 00000000bf96a1c0 00084 (v01 APPLE   Apple00 00000039      01000013)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: FACP 00000000bf968000 000F4 (v04 APPLE   Apple00 00000039 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: DSDT 00000000bf95a000 06101 (v01 APPLE  MacBookP 00070001 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: FACS 00000000bf71e000 00040
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: HPET 00000000bf967000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: APIC 00000000bf966000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: APIC 00000000bf965000 00068 (v02 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: ASF! 00000000bf963000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: SBST 00000000bf962000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: ECDT 00000000bf961000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: SSDT 00000000bf956000 00024 (v01 APPLE     Apple 00001000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: SSDT 00000000bf955000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: MCFG 00000000bf964000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: SSDT 00000000bf959000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: SSDT 00000000bf958000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
[B]Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org[/B]
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] No NUMA configuration found
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Initmem setup node 0 0000000000000000-0000000140000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Zone PFN ranges:
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Movable zone start PFN for each node
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] early_node_map[4] active PFN ranges
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     0: 0x00000100 -> 0x000af000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     0: 0x000bf000 -> 0x000bf70f
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
**Nov 26 08:20:49 WillBookPro kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs**
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000af000000 - 00000000bf000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bf70f000 - 00000000bf930000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bf930000 - 00000000bf931000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bf931000 - 00000000bf939000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bf939000 - 00000000bfef9000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bfef9000 - 00000000bfeff000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bfeff000 - 00000000bff00000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000d3400000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000d3400000 - 00000000d3401000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000d3401000 - 00000000f0000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f4000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000fec00000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Allocating PCI resources starting at d3401000 (gap: d3401000:1cbff000)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u1048576
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u1048576 alloc=1*2097152
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 962718
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Policy zone: Normal
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=a7cc948c-326a-4cf5-aaba-6122d66b7498 ro quiet splash
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Checking aperture...
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] No AGP bridge found
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Subtract (60 early reservations)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #4 [0001d18000 - 0001d181e9]             BRK
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #7 [0000016000 - 0000019000]         PGTABLE
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #8 [0000019000 - 000001a000]         PGTABLE
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #9 [0100000000 - 0100005000]       NODE_DATA
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #10 [0001d18200 - 0001d19200]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #11 [0001d17140 - 0001d17428]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #12 [0100005000 - 0100006000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #13 [0100006000 - 0100007000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #14 [0100200000 - 0103a00000]        MEMMAP 0
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #15 [0001d17440 - 0001d175c0]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #16 [0001d19200 - 0001d31200]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #17 [0001d31200 - 0001d37200]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #18 [0001d38000 - 0001d39000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #19 [0001d175c0 - 0001d17601]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #20 [0001d17640 - 0001d17683]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #21 [0001d176c0 - 0001d17ae8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #22 [0001d17b00 - 0001d17b68]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #23 [0001d17b80 - 0001d17be8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #24 [0001d17c00 - 0001d17c68]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #25 [0001d17c80 - 0001d17ce8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #26 [0001d17d00 - 0001d17d68]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #27 [0001d17d80 - 0001d17de8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #28 [0001d17e00 - 0001d17e68]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #29 [0001d17e80 - 0001d17ee8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #30 [0001d17f00 - 0001d17f68]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #31 [0001d17f80 - 0001d17fe8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #32 [0001d37200 - 0001d37268]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #33 [0001d37280 - 0001d372e8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #34 [0001d37300 - 0001d37368]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #35 [0001d37380 - 0001d373e8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #36 [0001d37400 - 0001d37468]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #37 [0001d37480 - 0001d374e8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #38 [0001d37500 - 0001d37568]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #39 [0001d37580 - 0001d375e8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #40 [0001d37600 - 0001d37620]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #41 [0001d37640 - 0001d37660]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #42 [0001d37680 - 0001d376a0]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #43 [0001d376c0 - 0001d3772a]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #44 [0001d37740 - 0001d377aa]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #45 [0001e00000 - 0001e1e000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #46 [0001f00000 - 0001f1e000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #47 [0001d377c0 - 0001d377c8]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #48 [0001d37800 - 0001d37808]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #49 [0001d37840 - 0001d37848]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #50 [0001d37880 - 0001d37890]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #51 [0001d378c0 - 0001d37a00]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #52 [0001d37a00 - 0001d37a60]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #53 [0001d37a80 - 0001d37ae0]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #54 [0001d39000 - 0001d41000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #55 [0001d37b00 - 0001d37d40]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #56 [0001f1e000 - 0005f1e000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #57 [0001d41000 - 0001d61000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #58 [0001d61000 - 0001da1000]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]   #59 [000001b800 - 0000023800]         BOOTMEM
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Memory: 3774624k/5242880k available (5708k kernel code, 1320328k absent, 147928k reserved, 5382k data, 908k init)
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Hierarchical RCU implementation.
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] NR_IRQS:4352 nr_irqs:512
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Extended CMOS year: 2000
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Console: colour VGA+ 80x25
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] console [tty0] enabled
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] allocated 40632320 bytes of page_cgroup
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Fast TSC calibration using PIT
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] Detected 2388.958 MHz processor.
Nov 26 08:20:49 WillBookPro kernel: [    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4777.91 BogoMIPS (lpj=23889580)
Nov 26 08:20:49 WillBookPro kernel: [    0.010013] pid_max: default: 32768 minimum: 301
Nov 26 08:20:49 WillBookPro kernel: [    0.010035] Security Framework initialized
Nov 26 08:20:49 WillBookPro kernel: [    0.010054] AppArmor: AppArmor initialized
Nov 26 08:20:49 WillBookPro kernel: [    0.010055] Yama: becoming mindful.
Nov 26 08:20:49 WillBookPro kernel: [    0.010452] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 26 08:20:49 WillBookPro kernel: [    0.012464] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 26 08:20:49 WillBookPro kernel: [    0.013346] Mount-cache hash table entries: 256
Nov 26 08:20:49 WillBookPro kernel: [    0.013481] Initializing cgroup subsys ns
Nov 26 08:20:49 WillBookPro kernel: [    0.013486] Initializing cgroup subsys cpuacct
Nov 26 08:20:49 WillBookPro kernel: [    0.013490] Initializing cgroup subsys memory
Nov 26 08:20:49 WillBookPro kernel: [    0.013498] Initializing cgroup subsys devices
Nov 26 08:20:49 WillBookPro kernel: [    0.013500] Initializing cgroup subsys freezer
Nov 26 08:20:49 WillBookPro kernel: [    0.013503] Initializing cgroup subsys net_cls
Nov 26 08:20:49 WillBookPro kernel: [    0.013531] CPU: Physical Processor ID: 0
Nov 26 08:20:49 WillBookPro kernel: [    0.013532] CPU: Processor Core ID: 0
Nov 26 08:20:49 WillBookPro kernel: [    0.013534] mce: CPU supports 6 MCE banks
Nov 26 08:20:49 WillBookPro kernel: [    0.013542] CPU0: Thermal monitoring enabled (TM2)
Nov 26 08:20:49 WillBookPro kernel: [    0.013547] using mwait in idle threads.
Nov 26 08:20:49 WillBookPro kernel: [    0.013549] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Nov 26 08:20:49 WillBookPro kernel: [    0.013556] ... version:                2
Nov 26 08:20:49 WillBookPro kernel: [    0.013558] ... bit width:              40
Nov 26 08:20:49 WillBookPro kernel: [    0.013559] ... generic registers:      2
Nov 26 08:20:49 WillBookPro kernel: [    0.013560] ... value mask:             000000ffffffffff
Nov 26 08:20:49 WillBookPro kernel: [    0.013562] ... max period:             000000007fffffff
Nov 26 08:20:49 WillBookPro kernel: [    0.013563] ... fixed-purpose events:   3
Nov 26 08:20:49 WillBookPro kernel: [    0.013565] ... event mask:             0000000700000003
Nov 26 08:20:49 WillBookPro kernel: [    0.016068] ACPI: Core revision 20100428
Nov 26 08:20:49 WillBookPro kernel: [    0.029205] ftrace: converting mcount calls to 0f 1f 44 00 00
Nov 26 08:20:49 WillBookPro kernel: [    0.029210] ftrace: allocating 22680 entries in 89 pages
Nov 26 08:20:49 WillBookPro kernel: [    0.030051] Setting APIC routing to flat
Nov 26 08:20:49 WillBookPro kernel: [    0.030445] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[B]Nov 26 08:20:49 WillBookPro kernel: [    0.139844] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
Nov 26 08:20:49 WillBookPro kernel: [    0.140000] Booting Node   0, Processors  #1 Ok.
Nov 26 08:20:49 WillBookPro kernel: [    0.300015] Brought up 2 CPUs
Nov 26 08:20:49 WillBookPro kernel: [    0.300019] Total of 2 processors activated (9556.42 BogoMIPS).[/B]
Nov 26 08:20:49 WillBookPro kernel: [    0.300655] devtmpfs: initialized
Nov 26 08:20:49 WillBookPro kernel: [    0.300655] regulator: core version 0.5
Nov 26 08:20:49 WillBookPro kernel: [    0.300705] Time: 13:20:42  Date: 11/26/10
Nov 26 08:20:49 WillBookPro kernel: [    0.300738] NET: Registered protocol family 16
Nov 26 08:20:49 WillBookPro kernel: [    0.300757] Trying to unpack rootfs image as initramfs...
Nov 26 08:20:49 WillBookPro kernel: [    0.300853] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Nov 26 08:20:49 WillBookPro kernel: [    0.300856] ACPI: bus type pci registered
Nov 26 08:20:49 WillBookPro kernel: [    0.301119] PCI: MMCONFIG for domain 0000 [bus 00-04] at [mem 0xf0000000-0xf04fffff] (base 0xf0000000)
Nov 26 08:20:49 WillBookPro kernel: [    0.301122] PCI: MMCONFIG at [mem 0xf0000000-0xf04fffff] reserved in E820
Nov 26 08:20:49 WillBookPro kernel: [    0.302116] PCI: Using configuration type 1 for base access
Nov 26 08:20:49 WillBookPro kernel: [    0.310168] bio: create slab <bio-0> at 0
Nov 26 08:20:49 WillBookPro kernel: [    0.311727] ACPI: EC: EC description table is found, configuring boot EC
Nov 26 08:20:49 WillBookPro kernel: [    0.313293] ACPI: BIOS _OSI(Linux) query ignored
Nov 26 08:20:49 WillBookPro kernel: [    0.314270] ACPI: SSDT 00000000bf71dc18 0027A (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.314681] ACPI: Dynamic OEM Table Load:
Nov 26 08:20:49 WillBookPro kernel: [    0.314684] ACPI: SSDT (null) 0027A (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.314942] ACPI: SSDT 00000000bf71c618 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.315337] ACPI: Dynamic OEM Table Load:
Nov 26 08:20:49 WillBookPro kernel: [    0.315339] ACPI: SSDT (null) 005A6 (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.315725] ACPI: SSDT 00000000bf71df18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.316125] ACPI: Dynamic OEM Table Load:
Nov 26 08:20:49 WillBookPro kernel: [    0.316128] ACPI: SSDT (null) 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.316257] ACPI: SSDT 00000000bf71bf18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.316650] ACPI: Dynamic OEM Table Load:
Nov 26 08:20:49 WillBookPro kernel: [    0.316653] ACPI: SSDT (null) 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Nov 26 08:20:49 WillBookPro kernel: [    0.316753] ACPI: Interpreter enabled
Nov 26 08:20:49 WillBookPro kernel: [    0.316756] ACPI: (supports S0 S3 S4 S5)
Nov 26 08:20:49 WillBookPro kernel: [    0.316775] ACPI: Using IOAPIC for interrupt routing
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] ACPI: EC: GPE = 0x57, I/O: command/status = 0x66, data = 0x62
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] ACPI: No dock devices found.
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci 0000:00:0e.0: PCI bridge to [bus 01-01]
Nov 26 08:20:49 WillBookPro kernel: [    0.335044] pci 0000:00:15.0: PCI bridge to [bus 02-02]
Nov 26 08:20:49 WillBookPro kernel: [    0.340333] pci 0000:00:16.0: PCI bridge to [bus 03-03]
Nov 26 08:20:49 WillBookPro kernel: [    0.340476] pci 0000:00:17.0: PCI bridge to [bus 04-04]
Nov 26 08:20:49 WillBookPro kernel: [    0.393833] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.394065] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.394289] ACPI: PCI Interrupt Link [LNK3] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 26 08:20:49 WillBookPro kernel: [    0.394515] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.

```

---

### Post by Fafler on 2010-11-27
So you did :-) A non SMP kernel would have been easy to change, but i don't even think single processor installations use that anymore.

The acpi_apic_instance=2 thing might be worth trying. Press shift to enter the grub menu when booting, e to edit and put acpi_apic_instance=2 after "quiet splash" in the fourth or fifth line. Press ctrl + x to boot. Or maybe you should ask the question in the Mac subforum.

---

### Post by wiznillyp on 2010-11-27
Well this is nice... 

As stated in the logs, I added "acpi_apic_instance=2" to **/etc/default/grub**... and now it works!```
Nov 26 08:20:49 WillBookPro kernel: [    0.030051] Setting APIC routing to flat
Nov 26 08:20:49 WillBookPro kernel: [    0.030445] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 26 08:20:49 WillBookPro kernel: [    0.139844] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
Nov 26 08:20:49 WillBookPro kernel: [    0.140000] Booting Node   0, Processors  #1 Ok.
Nov 26 08:20:49 WillBookPro kernel: [    0.300015] Brought up 2 CPUs
Nov 26 08:20:49 WillBookPro kernel: [    0.300019] Total of 2 processors activated (9556.42 BogoMIPS).
```Thanks for your guidance.

---

### Post by wiznillyp on 2010-11-27
> **Fafler said:**
> So you did :-) A non SMP kernel would have been easy to change, but i don't even think single processor installations use that anymore.

The acpi_apic_instance=2 thing might be worth trying. Press shift to enter the grub menu when booting, e to edit and put acpi_apic_instance=2 after "quiet splash" in the fourth or fifth line. Press ctrl + x to boot. Or maybe you should ask the question in the Mac subforum.Ha!!!  One step ahead of you again!!!

:p

Looks like that was the culprit!  Excellent.  Should I actually send an email to the person, as stated here?:

[I]Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Nov 26 08:20:49 WillBookPro kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL][/I]

---

### Post by Fafler on 2010-11-27
That's a really good idea. It's probably Mac related, and it's always good to get rid of compatibility problems like that.

---

### Post by wiznillyp on 2010-11-27
Done, email sent and updated the wiki found here, [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

:p

My next challenge is to grow my beard longer.

---


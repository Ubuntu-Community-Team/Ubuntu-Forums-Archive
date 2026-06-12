---
title: "Dual channel memory support"
date: 2011-01-10
forum: Hardware
---

### Post by [Snc] on 2011-01-10
Greetings, i have problems with my ram, i can only see/use half of it and even that is in single channel mode.

I'm using 4 * OCZ3G1333LV2G (4*2Gib) of ram on a HD55HC motherboard

My OS is 64bit and lshw sees my full amount of ram, the OS doesn't, I have already been "sent away" by the Intel support, since i use Linux :(, they say: "If you would have used windows, everything would work normally".

---

### Post by Grenage on 2011-01-10
First things first, where are you getting your information from?  Where does it say that only 4GB is available?

---

### Post by [Snc] on 2011-01-10
From *System Monitor* also if i open up a terminal and type "free -mo" i get
```
Mem:          3894       2978        915          0         33       1881
Swap:         2537          0       2537
```with 3894 - being the 3.8Gib i was talking about.

---

### Post by ellgor on 2011-01-10
Hi,

I have dual channel and on mine it has to be activated through the bios, F2 gets my bios at bootup and in the options there is the dual channel function.

Regards, Ellgor.

---

### Post by [Snc] on 2011-01-10
> **ellgor said:**
> Hi,

I have dual channel and on mine it has to be activated through the bios, F2 gets my bios at bootup and in the options there is the dual channel function.

Regards, Ellgor.

Thank you for your response, Ellgor!

I have swept through all of the bios settings and found nothing, as i have also said, i also contacted Intel and told them about the problem i have and they said it was a "Linux thing"

again, "sudo lshw -c memory" prints out this:
```
 *-memory
       description: System Memory
       physical id: 28
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: OCZ3G1333LV2G
          vendor: Undefined
          physical id: 0
          serial: 00000000
          slot: CHANNEL A
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:1
          description: DIMM Synchronous 1333 MHz (0.8 ns)
          product: OCZ3G1333LV2G
          vendor: Undefined
          physical id: 1
          serial: 00000000
          slot: CHANNEL A
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:2
          description: DIMM Synchronous 1066 MHz (0.9 ns)
          product: OCZ3G1333LV2G
          vendor: Undefined
          physical id: 2
          serial: 00000000
          slot: CHANNEL B
          size: 2GiB
          width: 64 bits
          clock: 1066MHz (0.9ns)
     *-bank:3
          description: DIMM Synchronous 1333 MHz (0.8 ns)
          product: OCZ3G1333LV2G
          vendor: Undefined
          physical id: 3
          serial: 00000000
          slot: CHANNEL B
          size: 2GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
```so both my channels should working normaly :(
(i wouldnt mind if only single-channel would be activated and i would have 8Gb of ram available)

---

### Post by Yellow Pasque on 2011-01-10
> **'[Snc] said:**
> i also contacted Intel and told them about the problem i have and they said it was a "Linux thing"

From your lshw output, it looks like dual-channel is activated, but if the mobo displays a message indicating otherwise (at boot), then you should definitely try to get dual-channel working. The OS has nothing to do with single-channel/dual-channel setting. If the RAM sticks are paired in the correct slots (as shown in the mobo manual), then the dual-channel feature should automatically activate. I've never seen a setting for it in any BIOS, and I'm not sure why there would be (except maybe in the unlikely event that only part of the memory controller malfunctions).

Look at:
```
dmesg
```
and you should see something like this:
```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: TA890FXE/TA890FXE, BIOS 080015  06/29/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
```
^Post that

---

### Post by Grenage on 2011-01-10
> **Temüjin said:**
> I've never seen a setting for it in any BIOS, and I'm not sure why there would be (except maybe in the unlikely event that only part of the memory controller malfunctions).

It's not so common now, but a lot of older boards (like mine) have the option.  Most of our HP work machines seem to have it, too.

---

### Post by [Snc] on 2011-01-10
my motherboard is not even a year old and has the newest bios update (2 months old or something like that)

>*Temüjin*
thank you for showing me something new :) i did not know **dmesg** yet, and currently don't se anything that could help me :} i hope your (or somebody elses) skilled eye can track something helpful bellow

i have copied the whole output of dmesg in the code field here
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c000 (usable)
[    0.000000]  BIOS-e820: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cbc52000 (usable)
[    0.000000]  BIOS-e820: 00000000cbc52000 - 00000000cbc97000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbc97000 - 00000000cbd0b000 (reserved)
[    0.000000]  BIOS-e820: 00000000cbd0b000 - 00000000cbd0d000 (usable)
[    0.000000]  BIOS-e820: 00000000cbd0d000 - 00000000cbe13000 (reserved)
[    0.000000]  BIOS-e820: 00000000cbe13000 - 00000000cbe14000 (usable)
[    0.000000]  BIOS-e820: 00000000cbe14000 - 00000000cbe15000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbe15000 - 00000000cbe1d000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cbe1d000 - 00000000cbe1e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbe1e000 - 00000000cbe20000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cbe20000 - 00000000cbe28000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbe28000 - 00000000cbe49000 (reserved)
[    0.000000]  BIOS-e820: 00000000cbe49000 - 00000000cbe8c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cbe8c000 - 00000000cc000000 (usable)
[    0.000000]  BIOS-e820: 00000000cc000000 - 00000000cf800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcc000 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009c000 (usable)
[    0.000000]  modified: 000000000009c000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cbc52000 (usable)
[    0.000000]  modified: 00000000cbc52000 - 00000000cbc97000 (ACPI NVS)
[    0.000000]  modified: 00000000cbc97000 - 00000000cbd0b000 (reserved)
[    0.000000]  modified: 00000000cbd0b000 - 00000000cbd0d000 (usable)
[    0.000000]  modified: 00000000cbd0d000 - 00000000cbe13000 (reserved)
[    0.000000]  modified: 00000000cbe13000 - 00000000cbe14000 (usable)
[    0.000000]  modified: 00000000cbe14000 - 00000000cbe15000 (ACPI NVS)
[    0.000000]  modified: 00000000cbe15000 - 00000000cbe1d000 (ACPI data)
[    0.000000]  modified: 00000000cbe1d000 - 00000000cbe1e000 (ACPI NVS)
[    0.000000]  modified: 00000000cbe1e000 - 00000000cbe20000 (ACPI data)
[    0.000000]  modified: 00000000cbe20000 - 00000000cbe28000 (ACPI NVS)
[    0.000000]  modified: 00000000cbe28000 - 00000000cbe49000 (reserved)
[    0.000000]  modified: 00000000cbe49000 - 00000000cbe8c000 (ACPI NVS)
[    0.000000]  modified: 00000000cbe8c000 - 00000000cc000000 (usable)
[    0.000000]  modified: 00000000cc000000 - 00000000cf800000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000fcd60] fcd60
[    0.000000] init_memory_mapping: 0000000000000000-00000000cc000000
[    0.000000]  0000000000 - 00cc000000 page 2M
[    0.000000] kernel direct mapping tables up to cc000000 @ 16000-1b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 19000-1f000
[    0.000000] RAMDISK: 37049000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 00000000cbe1ee18 0005C (v01 INTEL  DH55HC   01072009 MSFT 00010013)
[    0.000000] ACPI: FACP 00000000cbe1cd98 000F4 (v04 INTEL  DH55HC   01072009 MSFT 00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20100428/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCBE1DF40/0x00000000CBE1DE40, using 32 (20100428/tbfadt-486)
[    0.000000] ACPI: DSDT 00000000cbe15018 06B88 (v01 INTEL  DH55HC   00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cbe1df40 00040
[    0.000000] ACPI: APIC 00000000cbe1cf18 000CC (v02 INTEL  DH55HC   01072009 MSFT 00010013)
[    0.000000] ACPI: SSDT 00000000cbe1cc18 00102 (v01 INTEL  DH55HC   00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000cbe1ff18 0003C (v01 INTEL  DH55HC   01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cbe1fe98 00038 (v01 INTEL  DH55HC   01072009 AMI. 00000003)
[    0.000000] ACPI: ASF! 00000000cbe1ec18 000A0 (v32 INTEL  DH55HC   00000001 TFSM 000F4240)
[    0.000000] ACPI: DMAR 00000000cbe1eb18 00068 (v01 INTEL  DH55HC   00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000cbc52
[    0.000000]     0: 0x000cbd0b -> 0x000cbd0d
[    0.000000]     0: 0x000cbe13 -> 0x000cbe14
[    0.000000]     0: 0x000cbe8c -> 0x000cc000
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1031509
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3924 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 816641 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cbc52000 - 00000000cbc97000
[    0.000000] PM: Registered nosave memory: 00000000cbc97000 - 00000000cbd0b000
[    0.000000] PM: Registered nosave memory: 00000000cbd0d000 - 00000000cbe13000
[    0.000000] PM: Registered nosave memory: 00000000cbe14000 - 00000000cbe15000
[    0.000000] PM: Registered nosave memory: 00000000cbe15000 - 00000000cbe1d000
[    0.000000] PM: Registered nosave memory: 00000000cbe1d000 - 00000000cbe1e000
[    0.000000] PM: Registered nosave memory: 00000000cbe1e000 - 00000000cbe20000
[    0.000000] PM: Registered nosave memory: 00000000cbe20000 - 00000000cbe28000
[    0.000000] PM: Registered nosave memory: 00000000cbe28000 - 00000000cbe49000
[    0.000000] PM: Registered nosave memory: 00000000cbe49000 - 00000000cbe8c000
[    0.000000] PM: Registered nosave memory: 00000000cc000000 - 00000000cf800000
[    0.000000] PM: Registered nosave memory: 00000000cf800000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e4000000 (gap: e4000000:1ad1c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u131072
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1014485
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=b7740ce2-5580-4416-a5d3-fadf8786194a ro quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-2.6.35/drivers/pci/dmar.c:633 warn_invalid_dmar+0x8f/0xa0()
[    0.000000] Hardware name:         
[    0.000000] Your BIOS is broken; DMAR reported at address fed90000 returns all ones!
[    0.000000] BIOS vendor: Intel Corp.; Ver: TCIBX10H.86A.0040.2010.1018.1100; Product Version:         
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 2.6.35-24-generic #42-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff8106089f>] warn_slowpath_common+0x7f/0xc0
[    0.000000]  [<ffffffff8106093f>] warn_slowpath_fmt_taint+0x3f/0x50
[    0.000000]  [<ffffffff810366e9>] ? native_flush_tlb_single+0x9/0x10
[    0.000000]  [<ffffffff810366e9>] ? native_flush_tlb_single+0x9/0x10
[    0.000000]  [<ffffffff812eeb0f>] warn_invalid_dmar+0x8f/0xa0
[    0.000000]  [<ffffffff81b1a167>] check_zero_address+0xf2/0x11e
[    0.000000]  [<ffffffff8132cbab>] ? acpi_get_table_with_size+0x5a/0xb4
[    0.000000]  [<ffffffff81593e03>] ? _etext+0x0/0x1
[    0.000000]  [<ffffffff81b1a1a5>] detect_intel_iommu+0x12/0x69
[    0.000000]  [<ffffffff81af488c>] pci_iommu_alloc+0x1c/0x28
[    0.000000]  [<ffffffff81b03f8f>] mem_init+0x19/0xec
[    0.000000]  [<ffffffff81af2064>] ? trap_init+0x1e2/0x1e9
[    0.000000]  [<ffffffff81aedab4>] start_kernel+0x19e/0x390
[    0.000000]  [<ffffffff81aed341>] x86_64_start_reservations+0x12c/0x130
[    0.000000]  [<ffffffff81aed43f>] x86_64_start_kernel+0xfa/0x109
[    0.000000] ---[ end trace a7919e7f17c0a725 ]---
[    0.000000] Disabling lock debugging due to kernel taint
[    0.000000] Subtract (83 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037049000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d180f9]             BRK
[    0.000000]   #4 [00000fcd70 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000fcd60 - 00000fcd70]    MP-table mpf
[    0.000000]   #6 [000009c000 - 00000fc9f0]   BIOS reserved
[    0.000000]   #7 [00000fccdc - 00000fcd60]   BIOS reserved
[    0.000000]   #8 [00000fc9f0 - 00000fccdc]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000019000]         PGTABLE
[    0.000000]   #12 [0000019000 - 000001a000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18100 - 0001d19100]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19100 - 0001d31100]         BOOTMEM
[    0.000000]   #21 [0001d31100 - 0001d37100]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #25 [0001d176c0 - 0001d17bc8]         BOOTMEM
[    0.000000]   #26 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #27 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #28 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #29 [0001d17d80 - 0001d17de8]         BOOTMEM
[    0.000000]   #30 [0001d17e00 - 0001d17e68]         BOOTMEM
[    0.000000]   #31 [0001d17e80 - 0001d17ee8]         BOOTMEM
[    0.000000]   #32 [0001d17f00 - 0001d17f68]         BOOTMEM
[    0.000000]   #33 [0001d17f80 - 0001d17fe8]         BOOTMEM
[    0.000000]   #34 [0001d37100 - 0001d37168]         BOOTMEM
[    0.000000]   #35 [0001d37180 - 0001d371e8]         BOOTMEM
[    0.000000]   #36 [0001d37200 - 0001d37268]         BOOTMEM
[    0.000000]   #37 [0001d37280 - 0001d372e8]         BOOTMEM
[    0.000000]   #38 [0001d37300 - 0001d37368]         BOOTMEM
[    0.000000]   #39 [0001d37380 - 0001d373e8]         BOOTMEM
[    0.000000]   #40 [0001d37400 - 0001d37468]         BOOTMEM
[    0.000000]   #41 [0001d37480 - 0001d374e8]         BOOTMEM
[    0.000000]   #42 [0001d37500 - 0001d37568]         BOOTMEM
[    0.000000]   #43 [0001d37580 - 0001d375e8]         BOOTMEM
[    0.000000]   #44 [0001d37600 - 0001d37668]         BOOTMEM
[    0.000000]   #45 [0001d37680 - 0001d376e8]         BOOTMEM
[    0.000000]   #46 [0001d37700 - 0001d37768]         BOOTMEM
[    0.000000]   #47 [0001d37780 - 0001d377e8]         BOOTMEM
[    0.000000]   #48 [0001d37800 - 0001d37820]         BOOTMEM
[    0.000000]   #49 [0001d37840 - 0001d37860]         BOOTMEM
[    0.000000]   #50 [0001d37880 - 0001d378a0]         BOOTMEM
[    0.000000]   #51 [0001d378c0 - 0001d378e0]         BOOTMEM
[    0.000000]   #52 [0001d37900 - 0001d37920]         BOOTMEM
[    0.000000]   #53 [0001d37940 - 0001d379ef]         BOOTMEM
[    0.000000]   #54 [0001d37a00 - 0001d37aaf]         BOOTMEM
[    0.000000]   #55 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #56 [0001e20000 - 0001e3e000]         BOOTMEM
[    0.000000]   #57 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #58 [0001e60000 - 0001e7e000]         BOOTMEM
[    0.000000]   #59 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #60 [0001ea0000 - 0001ebe000]         BOOTMEM
[    0.000000]   #61 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #62 [0001ee0000 - 0001efe000]         BOOTMEM
[    0.000000]   #63 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #64 [0001f20000 - 0001f3e000]         BOOTMEM
[    0.000000]   #65 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #66 [0001f60000 - 0001f7e000]         BOOTMEM
[    0.000000]   #67 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #68 [0001fa0000 - 0001fbe000]         BOOTMEM
[    0.000000]   #69 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #70 [0001fe0000 - 0001ffe000]         BOOTMEM
[    0.000000]   #71 [0001d37ac0 - 0001d37ac8]         BOOTMEM
[    0.000000]   #72 [0001d37b00 - 0001d37b08]         BOOTMEM
[    0.000000]   #73 [0001d37b40 - 0001d37b80]         BOOTMEM
[    0.000000]   #74 [0001d37b80 - 0001d37c00]         BOOTMEM
[    0.000000]   #75 [0001d37c00 - 0001d37d10]         BOOTMEM
[    0.000000]   #76 [0001d37d40 - 0001d37d88]         BOOTMEM
[    0.000000]   #77 [0001d37dc0 - 0001d37e08]         BOOTMEM
[    0.000000]   #78 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #79 [0001ffe000 - 0005ffe000]         BOOTMEM
[    0.000000]   #80 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #81 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #82 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 3969100k/4980736k available (5711k kernel code, 854700k absent, 156936k reserved, 5379k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:808
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2660.342 MHz processor.
[    0.000008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5320.68 BogoMIPS (lpj=26603420)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000031] Security Framework initialized
[    0.000042] AppArmor: AppArmor initialized
[    0.000044] Yama: becoming mindful.
[    0.000397] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001724] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002316] Mount-cache hash table entries: 256
[    0.002414] Initializing cgroup subsys ns
[    0.002417] Initializing cgroup subsys cpuacct
[    0.002421] Initializing cgroup subsys memory
[    0.002427] Initializing cgroup subsys devices
[    0.002429] Initializing cgroup subsys freezer
[    0.002430] Initializing cgroup subsys net_cls
[    0.002449] CPU: Physical Processor ID: 0
[    0.002450] CPU: Processor Core ID: 0
[    0.002455] mce: CPU supports 9 MCE banks
[    0.002464] CPU0: Thermal monitoring enabled (TM1)
[    0.002471] using mwait in idle threads.
[    0.002472] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.002478] ... version:                3
[    0.002479] ... bit width:              48
[    0.002480] ... generic registers:      4
[    0.002481] ... value mask:             0000ffffffffffff
[    0.002483] ... max period:             000000007fffffff
[    0.002484] ... fixed-purpose events:   3
[    0.002485] ... event mask:             000000070000000f
[    0.004248] ACPI: Core revision 20100428
[    0.010825] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.010828] ftrace: allocating 22678 entries in 89 pages
[    0.017148] DMAR: Host address width 36
[    0.017150] DMAR: DRHD base: 0x000000fed90000 flags: 0x1
[    0.017164] DMAR: parse DMAR table failure.
[    0.017165] Setting APIC routing to physical flat
[    0.017536] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.117307] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05
[    0.228121] Booting Node   0, Processors  #1 #2 #3
[    0.766728] Brought up 4 CPUs
[    0.766731] Total of 4 processors activated (21280.41 BogoMIPS).
[    0.768221] devtmpfs: initialized
[    0.769033] regulator: core version 0.5
[    0.769060] Time: 17:34:40  Date: 01/10/11
[    0.769087] NET: Registered protocol family 16
[    0.769154] Trying to unpack rootfs image as initramfs...
[    0.769167] ACPI: bus type pci registered
[    0.769235] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.769238] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.781693] PCI: Using configuration type 1 for base access
[    0.782251] bio: create slab <bio-0> at 0
[    0.783408] ACPI: EC: Look up EC in DSDT
[    0.784847] ACPI: Executed 1 blocks of module-level executable AML code
[    0.791037] ACPI: SSDT 00000000cbe14c18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.791389] ACPI: Dynamic OEM Table Load:
[    0.791391] ACPI: SSDT (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.791431] ACPI Warning: Incorrect checksum in table [SSDT] - 0x3F, should be 0x1F (20100428/tbutils-314)
[    0.791435] ACPI: SSDT 00000000cbe1dd18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.791736] ACPI: Dynamic OEM Table Load:
[    0.791738] ACPI: SSDT (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.792746] ACPI: Interpreter enabled
[    0.792748] ACPI: (supports S0 S1 S3 S4 S5)
[    0.792764] ACPI: Using IOAPIC for interrupt routing
[    0.792977] ACPI: BIOS _OSI(Linux) query ignored
[    0.799415] ACPI: No dock devices found.
[    0.799418] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.799610] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.799757] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.799759] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.799761] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.799763] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xffffffff]
[    0.799847] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.799849] pci 0000:00:03.0: PME# disabled
[    0.800111] pci 0000:00:16.0: reg 10: [mem 0xfe708000-0xfe70800f 64bit]
[    0.800167] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.800175] pci 0000:00:16.0: PME# disabled
[    0.800219] pci 0000:00:16.2: reg 10: [io  0xf130-0xf137]
[    0.800228] pci 0000:00:16.2: reg 14: [io  0xf120-0xf123]
[    0.800238] pci 0000:00:16.2: reg 18: [io  0xf110-0xf117]
[    0.800248] pci 0000:00:16.2: reg 1c: [io  0xf100-0xf103]
[    0.800258] pci 0000:00:16.2: reg 20: [io  0xf0f0-0xf0ff]
[    0.800331] pci 0000:00:16.3: reg 10: [io  0xf0e0-0xf0e7]
[    0.800341] pci 0000:00:16.3: reg 14: [mem 0xfe707000-0xfe707fff]
[    0.800439] pci 0000:00:1a.0: reg 10: [mem 0xfe706000-0xfe7063ff]
[    0.800492] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.800501] pci 0000:00:1a.0: PME# disabled
[    0.800540] pci 0000:00:1b.0: reg 10: [mem 0xfe700000-0xfe703fff 64bit]
[    0.800582] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.800590] pci 0000:00:1b.0: PME# disabled
[    0.800662] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.800669] pci 0000:00:1c.0: PME# disabled
[    0.800741] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.800748] pci 0000:00:1c.5: PME# disabled
[    0.800787] pci 0000:00:1d.0: reg 10: [mem 0xfe705000-0xfe7053ff]
[    0.800846] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.800853] pci 0000:00:1d.0: PME# disabled
[    0.801031] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    0.801041] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    0.801049] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    0.801058] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    0.801067] pci 0000:00:1f.2: reg 20: [io  0xf090-0xf09f]
[    0.801077] pci 0000:00:1f.2: reg 24: [io  0xf080-0xf08f]
[    0.801130] pci 0000:00:1f.3: reg 10: [mem 0xfe704000-0xfe7040ff 64bit]
[    0.801146] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
[    0.801193] pci 0000:00:1f.5: reg 10: [io  0xf070-0xf077]
[    0.801202] pci 0000:00:1f.5: reg 14: [io  0xf060-0xf063]
[    0.801210] pci 0000:00:1f.5: reg 18: [io  0xf050-0xf057]
[    0.801219] pci 0000:00:1f.5: reg 1c: [io  0xf040-0xf043]
[    0.801228] pci 0000:00:1f.5: reg 20: [io  0xf030-0xf03f]
[    0.801237] pci 0000:00:1f.5: reg 24: [io  0xf020-0xf02f]
[    0.801316] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.801325] pci 0000:01:00.0: reg 18: [mem 0xfe620000-0xfe62ffff 64bit]
[    0.801330] pci 0000:01:00.0: reg 20: [io  0xe000-0xe0ff]
[    0.801337] pci 0000:01:00.0: reg 30: [mem 0xfe600000-0xfe61ffff pref]
[    0.801354] pci 0000:01:00.0: supports D1 D2
[    0.801379] pci 0000:01:00.1: reg 10: [mem 0xfe630000-0xfe633fff 64bit]
[    0.801411] pci 0000:01:00.1: supports D1 D2
[    0.816630] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    0.816633] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    0.816636] pci 0000:00:03.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.816640] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.816681] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.816689] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.816696] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.816706] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.816746] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    0.816753] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.816760] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.816770] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.816820] pci 0000:04:00.0: reg 10: [mem 0xfe502000-0xfe502fff]
[    0.816870] pci 0000:04:00.0: supports D1 D2
[    0.816871] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot
[    0.816878] pci 0000:04:00.0: PME# disabled
[    0.816911] pci 0000:04:00.1: reg 10: [mem 0xfe501000-0xfe501fff]
[    0.816960] pci 0000:04:00.1: supports D1 D2
[    0.816962] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot
[    0.816969] pci 0000:04:00.1: PME# disabled
[    0.817002] pci 0000:04:00.2: reg 10: [mem 0xfe500000-0xfe5000ff]
[    0.817051] pci 0000:04:00.2: supports D1 D2
[    0.817052] pci 0000:04:00.2: PME# supported from D0 D1 D2 D3hot
[    0.817060] pci 0000:04:00.2: PME# disabled
[    0.817104] pci 0000:04:02.0: reg 10: [io  0xd000-0xd0ff]
[    0.817156] pci 0000:04:02.0: supports D1 D2
[    0.817199] pci 0000:00:1e.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.817206] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.817210] pci 0000:00:1e.0:   bridge window [mem 0xfe500000-0xfe5fffff]
[    0.817219] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.817221] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.817222] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.817224] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.817226] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xffffffff] (subtractive decode)
[    0.817252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.817420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.817467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.817515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    1.043786] Freeing initrd memory: 16028k freed
[    1.817046] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.817154] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.817259] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.817364] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.817469] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    1.817574] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    1.817679] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.817782] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    1.817830] HEST: Table is not found!
[    1.817905] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.817908] vgaarb: loaded
[    1.818013] SCSI subsystem initialized
[    1.818090] libata version 3.00 loaded.
[    1.818122] usbcore: registered new interface driver usbfs
[    1.818130] usbcore: registered new interface driver hub
[    1.818145] usbcore: registered new device driver usb
[    1.818223] ACPI: WMI: Mapper loaded
[    1.818224] PCI: Using ACPI for IRQ routing
[    1.818226] PCI: pci_cache_line_size set to 64 bytes
[    1.818389] reserve RAM buffer: 000000000009c000 - 000000000009ffff 
[    1.818391] reserve RAM buffer: 00000000cbc52000 - 00000000cbffffff 
[    1.818394] reserve RAM buffer: 00000000cbd0d000 - 00000000cbffffff 
[    1.818396] reserve RAM buffer: 00000000cbe14000 - 00000000cbffffff 
[    1.818465] NetLabel: Initializing
[    1.818467] NetLabel:  domain hash size = 128
[    1.818468] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.818477] NetLabel:  unlabeled traffic allowed by default
[    1.818504]   alloc irq_desc for 40 on node -1
[    1.818505]   alloc kstat_irqs on node -1
[    1.818515]   alloc irq_desc for 41 on node -1
[    1.818516]   alloc kstat_irqs on node -1
[    1.818523]   alloc irq_desc for 42 on node -1
[    1.818524]   alloc kstat_irqs on node -1
[    1.818531]   alloc irq_desc for 43 on node -1
[    1.818532]   alloc kstat_irqs on node -1
[    1.818538]   alloc irq_desc for 44 on node -1
[    1.818540]   alloc kstat_irqs on node -1
[    1.818542] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    1.818550] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    1.818555] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.824206] hpet: hpet2 irq 40 for MSI
[    1.824288] hpet: hpet3 irq 41 for MSI
[    1.824331] hpet: hpet4 irq 42 for MSI
[    1.834259] hpet: hpet5 irq 43 for MSI
[    1.834298] Switching to clocksource tsc
[    1.840743] AppArmor: AppArmor Filesystem Enabled
[    1.840751] pnp: PnP ACPI init
[    1.840761] ACPI: bus type pnp registered
[    1.842813] pnp: PnP ACPI: found 11 devices
[    1.842814] ACPI: ACPI bus type pnp unregistered
[    1.842822] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    1.842824] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    1.842826] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.842828] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.842830] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
[    1.842837] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    1.842840] system 00:09: [io  0x0400-0x047f] has been reserved
[    1.842842] system 00:09: [io  0x1180-0x119f] has been reserved
[    1.842844] system 00:09: [io  0x0500-0x057f] has been reserved
[    1.842846] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.842851] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
[    1.842853] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
[    1.842855] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
[    1.848340] pci 0000:00:03.0: PCI bridge to [bus 01-01]
[    1.848343] pci 0000:00:03.0:   bridge window [io  0xe000-0xefff]
[    1.848346] pci 0000:00:03.0:   bridge window [mem 0xfe600000-0xfe6fffff]
[    1.848349] pci 0000:00:03.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.848353] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.848354] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.848362] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.848369] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.848374] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
[    1.848375] pci 0000:00:1c.5:   bridge window [io  disabled]
[    1.848383] pci 0000:00:1c.5:   bridge window [mem disabled]
[    1.848390] pci 0000:00:1c.5:   bridge window [mem pref disabled]
[    1.848399] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    1.848406] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    1.848414] pci 0000:00:1e.0:   bridge window [mem 0xfe500000-0xfe5fffff]
[    1.848421] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    1.848437] pci 0000:00:03.0: setting latency timer to 64
[    1.848448]   alloc irq_desc for 17 on node -1
[    1.848450]   alloc kstat_irqs on node -1
[    1.848454] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.848458] pci 0000:00:1c.0: setting latency timer to 64
[    1.848468]   alloc irq_desc for 16 on node -1
[    1.848470]   alloc kstat_irqs on node -1
[    1.848472] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.848477] pci 0000:00:1c.5: setting latency timer to 64
[    1.848491] pci 0000:00:1e.0: setting latency timer to 64
[    1.848498] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.848500] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.848501] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.848503] pci_bus 0000:00: resource 7 [mem 0xd0000000-0xffffffff]
[    1.848505] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    1.848506] pci_bus 0000:01: resource 1 [mem 0xfe600000-0xfe6fffff]
[    1.848508] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.848510] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    1.848511] pci_bus 0000:04: resource 1 [mem 0xfe500000-0xfe5fffff]
[    1.848513] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    1.848515] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    1.848516] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    1.848518] pci_bus 0000:04: resource 7 [mem 0xd0000000-0xffffffff]
[    1.848540] NET: Registered protocol family 2
[    1.848664] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.849505] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.851944] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.852228] TCP: Hash tables configured (established 524288 bind 65536)
[    1.852230] TCP reno registered
[    1.852239] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.852271] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.852398] NET: Registered protocol family 1
[    1.894246] pci 0000:01:00.0: Boot video device
[    1.894330] PCI: CLS 64 bytes, default 64
[    1.894332] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.894334] Placing 64MB software IO TLB between ffff880001ffe000 - ffff880005ffe000
[    1.894336] software IO TLB at phys 0x1ffe000 - 0x5ffe000
[    1.894562] Scanning for low memory corruption every 60 seconds
[    1.894668] audit: initializing netlink socket (disabled)
[    1.894675] type=2000 audit(1294680880.760:1): initialized
[    1.906787] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.907923] VFS: Disk quotas dquot_6.5.2
[    1.907970] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.908415] fuse init (API version 7.14)
[    1.908476] msgmni has been set to 7783
[    1.910159] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.910162] io scheduler noop registered
[    1.910163] io scheduler deadline registered
[    1.910193] io scheduler cfq registered (default)
[    1.910267] pcieport 0000:00:03.0: setting latency timer to 64
[    1.910290]   alloc irq_desc for 45 on node -1
[    1.910291]   alloc kstat_irqs on node -1
[    1.910299] pcieport 0000:00:03.0: irq 45 for MSI/MSI-X
[    1.910353] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.910384]   alloc irq_desc for 46 on node -1
[    1.910385]   alloc kstat_irqs on node -1
[    1.910395] pcieport 0000:00:1c.0: irq 46 for MSI/MSI-X
[    1.910456] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.910487]   alloc irq_desc for 47 on node -1
[    1.910488]   alloc kstat_irqs on node -1
[    1.910497] pcieport 0000:00:1c.5: irq 47 for MSI/MSI-X
[    1.910721] aer 0000:00:03.0:pcie02: service driver aer loaded
[    1.910735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.910748] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.910799] intel_idle: MWAIT substates: 0x1120
[    1.910800] intel_idle: v0.4 model 0x1E
[    1.910801] intel_idle: lapic_timer_reliable_states 0x2
[    1.910887] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.910891] ACPI: Power Button [PWRB]
[    1.910921] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.910923] ACPI: Power Button [PWRF]
[    1.911150] ACPI: acpi_idle yielding to intel_idle
[    1.914069] ERST: Table is not found!
[    1.914217] Linux agpgart interface v0.103
[    1.914230] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.914503] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.914579] 0000:00:16.3: ttyS0 at I/O 0xf0e0 (irq = 17) is a 16550A
[    1.915328] brd: module loaded
[    1.915678] loop: module loaded
[    1.915786] ata_piix 0000:00:1f.2: version 2.13
[    1.915799]   alloc irq_desc for 19 on node -1
[    1.915801]   alloc kstat_irqs on node -1
[    1.915805] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.915809] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.074725] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.074805] scsi0 : ata_piix
[    2.074860] scsi1 : ata_piix
[    2.076152] ata1: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 19
[    2.076161] ata2: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 19
[    2.076177] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.076185] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.233410] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    2.233436] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.233488] scsi2 : ata_piix
[    2.233527] scsi3 : ata_piix
[    2.234553] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 19
[    2.234555] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 19
[    2.234593]   alloc irq_desc for 18 on node -1
[    2.234595]   alloc kstat_irqs on node -1
[    2.234599] pata_acpi 0000:00:16.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.234616] pata_acpi 0000:00:16.2: setting latency timer to 64
[    2.234625] pata_acpi 0000:00:16.2: PCI INT C disabled
[    2.234807] Fixed MDIO Bus: probed
[    2.234826] PPP generic driver version 2.4.2
[    2.234851] tun: Universal TUN/TAP device driver, 1.6
[    2.234852] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.234902] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.234920] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.234938] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.234945] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.234966] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.234998] ehci_hcd 0000:00:1a.0: debug port 2
[    2.238928] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.238945] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe706000
[    2.253648] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.253762] hub 1-0:1.0: USB hub found
[    2.253766] hub 1-0:1.0: 2 ports detected
[    2.253817]   alloc irq_desc for 23 on node -1
[    2.253818]   alloc kstat_irqs on node -1
[    2.253822] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.253836] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.253842] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.253867] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.253895] ehci_hcd 0000:00:1d.0: debug port 2
[    2.257833] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.257847] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe705000
[    2.273600] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.273708] hub 2-0:1.0: USB hub found
[    2.273711] hub 2-0:1.0: 2 ports detected
[    2.273751] ehci_hcd 0000:04:00.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    2.273765] ehci_hcd 0000:04:00.2: EHCI Host Controller
[    2.273789] ehci_hcd 0000:04:00.2: new USB bus registered, assigned bus number 3
[    2.303550] ehci_hcd 0000:04:00.2: irq 23, io mem 0xfe500000
[    2.323490] ehci_hcd 0000:04:00.2: USB 2.0 started, EHCI 1.00
[    2.323589] hub 3-0:1.0: USB hub found
[    2.323592] hub 3-0:1.0: 5 ports detected
[    2.323642] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.323660]   alloc irq_desc for 21 on node -1
[    2.323661]   alloc kstat_irqs on node -1
[    2.323665] ohci_hcd 0000:04:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.323679] ohci_hcd 0000:04:00.0: OHCI Host Controller
[    2.323702] ohci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    2.323726] ohci_hcd 0000:04:00.0: irq 21, io mem 0xfe502000
[    2.413339] hub 4-0:1.0: USB hub found
[    2.413345] hub 4-0:1.0: 3 ports detected
[    2.413400]   alloc irq_desc for 22 on node -1
[    2.413401]   alloc kstat_irqs on node -1
[    2.413405] ohci_hcd 0000:04:00.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.413419] ohci_hcd 0000:04:00.1: OHCI Host Controller
[    2.413448] ohci_hcd 0000:04:00.1: new USB bus registered, assigned bus number 5
[    2.413472] ohci_hcd 0000:04:00.1: irq 22, io mem 0xfe501000
[    2.503121] hub 5-0:1.0: USB hub found
[    2.503126] hub 5-0:1.0: 2 ports detected
[    2.503172] uhci_hcd: USB Universal Host Controller Interface driver
[    2.503237] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.503239] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.503907] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.503947] mice: PS/2 mouse device common for all mice
[    2.504014] rtc_cmos 00:04: RTC can wake from S4
[    2.504038] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.504071] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.504139] device-mapper: uevent: version 1.0.3
[    2.504202] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    2.504287] device-mapper: multipath: version 1.1.1 loaded
[    2.504288] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.504533] cpuidle: using governor ladder
[    2.504640] cpuidle: using governor menu
[    2.504843] TCP cubic registered
[    2.504930] NET: Registered protocol family 10
[    2.505232] lo: Disabled Privacy Extensions
[    2.505375] NET: Registered protocol family 17
[    2.506219] PM: Resume from disk failed.
[    2.506225] registered taskstats version 1
[    2.506534]   Magic number: 11:551:592
[    2.506740] rtc_cmos 00:04: setting system clock to 2011-01-10 17:34:42 UTC (1294680882)
[    2.506742] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.506743] EDD information not available.
[    2.522800] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.573587] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.723073] hub 1-1:1.0: USB hub found
[    2.723283] hub 1-1:1.0: 6 ports detected
[    2.842025] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.931863] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.931893] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.971902] ata1.00: ATA-8: TS64GSSD25S-M, V0826, max UDMA/100
[    2.971908] ata1.00: 125206528 sectors, multi 0: LBA 
[    2.971921] ata1.00: applying bridge limits
[    2.971965] ata1.01: ATAPI: Optiarc DVD RW AD-7243S, 1.03, max UDMA/100
[    2.991873] ata1.00: configured for UDMA/100
[    2.992534] hub 2-1:1.0: USB hub found
[    2.992730] hub 2-1:1.0: 8 ports detected
[    3.031797] ata1.01: configured for UDMA/100
[    3.032728] scsi 0:0:0:0: Direct-Access     ATA      TS64GSSD25S-M    V082 PQ: 0 ANSI: 5
[    3.032901] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.034543] scsi 0:0:1:0: CD-ROM            Optiarc  DVD RW AD-7243S  1.03 PQ: 0 ANSI: 5
[    3.034571] sd 0:0:0:0: [sda] 125206528 512-byte logical blocks: (64.1 GB/59.7 GiB)
[    3.039215] sd 0:0:0:0: [sda] Write Protect is off
[    3.039221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040249] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.040254] Uniform CD-ROM driver Revision: 3.20
[    3.040314] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.040382] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.040416] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    3.040454]  sda: sda1 sda2 < sda5 >
[    3.041490] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.111378] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    3.263310] hub 3-1:1.0: USB hub found
[    3.263633] hub 3-1:1.0: 4 ports detected
[    3.340991] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    3.490455] ata2.01: failed to resume link (SControl 0)
[    3.540685] usb 3-1.1: new low speed USB device using ehci_hcd and address 3
[    3.650152] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.650171] ata2.01: SATA link down (SStatus 0 SControl 0)
[    3.670535] ata2.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    3.670541] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.690503] ata2.00: configured for UDMA/133
[    3.690790] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    3.690959] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    3.691135] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.691568] sd 1:0:0:0: [sdb] Write Protect is off
[    3.691574] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.691745] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.692448]  sdb:
[    3.730185] usb 3-1.4: new high speed USB device using ehci_hcd and address 4
[    4.236523]  sdb1
[    4.236846] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.236957] Freeing unused kernel memory: 908k freed
[    4.237121] Write protecting the kernel read-only data: 10240k
[    4.237644] Freeing unused kernel memory: 412k freed
[    4.237938] Freeing unused kernel memory: 1644k freed
[    4.255077] udev[109]: starting version 163
[    4.295181] Initializing USB Mass Storage driver...
[    4.302618] scsi4 : usb-storage 3-1.4:1.0
[    4.302690] usbcore: registered new interface driver hiddev
[    4.302884] usbcore: registered new interface driver usb-storage
[    4.302886] USB Mass Storage support registered.
[    4.307573] input: 2.4GHz 2way RF Mouse Receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/usb3/3-1/3-1.1/3-1.1:1.0/input/input3
[    4.307674] generic-usb 0003:1BCF:0535.0001: input,hiddev96,hidraw0: USB HID v1.11 Mouse [2.4GHz 2way RF Mouse Receiver] on usb-0000:04:00.2-1.1/input0
[    4.307686] usbcore: registered new interface driver usbhid
[    4.307687] usbhid: USB HID core driver
[    4.412287] uvesafb: (C) 1988-2005, ATI Technologies Inc. , RV710, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
[    4.438425] uvesafb: VBIOS/hardware supports DDC2 transfers
[    4.490011] uvesafb: monitor limits: vf = 75 Hz, hf = 81 kHz, clk = 150 MHz
[    4.490137] uvesafb: scrolling: redraw
[    4.492038] mtrr: type mismatch for d0000000,800000 old: write-back new: write-combining
[    4.492040] mtrr: type mismatch for d0000000,400000 old: write-back new: write-combining
[    4.492042] mtrr: type mismatch for d0000000,200000 old: write-back new: write-combining
[    4.492044] mtrr: type mismatch for d0000000,100000 old: write-back new: write-combining
[    4.492046] mtrr: type mismatch for d0000000,80000 old: write-back new: write-combining
[    4.492047] mtrr: type mismatch for d0000000,40000 old: write-back new: write-combining
[    4.492049] mtrr: type mismatch for d0000000,20000 old: write-back new: write-combining
[    4.492051] mtrr: type mismatch for d0000000,10000 old: write-back new: write-combining
[    4.492053] mtrr: type mismatch for d0000000,8000 old: write-back new: write-combining
[    4.492054] mtrr: type mismatch for d0000000,4000 old: write-back new: write-combining
[    4.492056] mtrr: type mismatch for d0000000,2000 old: write-back new: write-combining
[    4.492058] mtrr: type mismatch for d0000000,1000 old: write-back new: write-combining
[    4.493587] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    4.643734] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    4.963856] Console: switching to colour frame buffer device 175x65
[    4.964112] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    5.280552] uvesafb: framebuffer at 0xd0000000, mapped to 0xffffc90005100000, using 11550k, total 16384k
[    5.280554] fb0: VESA VGA frame buffer device
[    5.285603] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    5.298625] scsi 4:0:0:0: Direct-Access     Generic  Compact Flash    0.00 PQ: 0 ANSI: 2
[    5.299246] scsi 4:0:0:1: Direct-Access     Generic  SD/MMC           0.00 PQ: 0 ANSI: 2
[    5.299845] scsi 4:0:0:2: Direct-Access     Generic  microSD          0.00 PQ: 0 ANSI: 2
[    5.300466] scsi 4:0:0:3: Direct-Access     Generic  MS/MS-PRO        0.00 PQ: 0 ANSI: 2
[    5.300967] scsi 4:0:0:4: Direct-Access     Generic  SM/xD-Picture    0.00 PQ: 0 ANSI: 2
[    5.301707] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    5.301795] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    5.301902] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    5.302019] sd 4:0:0:3: Attached scsi generic sg6 type 0
[    5.303137] sd 4:0:0:4: Attached scsi generic sg7 type 0
[    5.304199] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[    5.307785] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[    5.308507] sd 4:0:0:2: [sde] Attached SCSI removable disk
[    5.309161] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[    5.309788] sd 4:0:0:4: [sdg] Attached SCSI removable disk
[    5.970717] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.036108] Adding 2598908k swap on /dev/sda5.  Priority:-1 extents:1 across:2598908k 
[   10.047981] udev[467]: starting version 163
[   10.072047] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.155420] lp: driver loaded but no devices found
[   10.162300] [fglrx] Maximum main memory to use for locked dma buffers: 3733 MBytes.
[   10.162429] [fglrx]   vendor: 1002 device: 954f count: 1
[   10.162736] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   10.162749] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.162753] pci 0000:01:00.0: setting latency timer to 64
[   10.162954] [fglrx] Kernel PAT support is enabled
[   10.162968] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   10.186506] cfg80211: Calling CRDA to update world regulatory domain
[   10.205638] cfg80211: World regulatory domain updated:
[   10.205640]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.205642]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.205644]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.205646]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.205648]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.205649]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.225487] C-Media PCI 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.261605] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.261698]   alloc irq_desc for 48 on node -1
[   10.261700]   alloc kstat_irqs on node -1
[   10.261709] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   10.261741] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.295203] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.296785] type=1400 audit(1294680890.297:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=807 comm="apparmor_parser"
[   10.297180] type=1400 audit(1294680890.297:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
[   10.297395] type=1400 audit(1294680890.297:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
[   10.335090] hda-intel: no codecs found!
[   10.335146] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   10.335182] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.335293] HDA Intel 0000:01:00.1: irq 48 for MSI/MSI-X
[   10.335307] HDA Intel 0000:01:00.1: setting latency timer to 64
[   10.404132] EXT4-fs (sdb1): warning: maximal mount count reached, running e2fsck is recommended
[   10.415627] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   10.421971] phy0: Selected rate control algorithm 'minstrel'
[   10.422317] phy0: hwaddr 00:11:6b:18:1c:fb, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   10.439396] rtl8187: Customer ID is 0xFF
[   10.439440] Registered led device: rtl8187-phy0::radio
[   10.439450] Registered led device: rtl8187-phy0::tx
[   10.439459] Registered led device: rtl8187-phy0::rx
[   10.440051] rtl8187: wireless switch is on
[   10.440079] usbcore: registered new interface driver rtl8187
[   10.472607] type=1400 audit(1294680890.467:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1122 comm="apparmor_parser"
[   10.473088] type=1400 audit(1294680890.467:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1122 comm="apparmor_parser"
[   10.485108] type=1400 audit(1294680890.487:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1148 comm="apparmor_parser"
[   10.485496] type=1400 audit(1294680890.487:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1148 comm="apparmor_parser"
[   10.485708] type=1400 audit(1294680890.487:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1148 comm="apparmor_parser"
[   10.486571] type=1400 audit(1294680890.487:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1147 comm="apparmor_parser"
[   10.488642] type=1400 audit(1294680890.487:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1217 comm="apparmor_parser"
[   10.494396] ppdev: user-space parallel port driver
[   10.608332] vboxdrv: Found 4 processor cores.
[   10.608402] VBoxDrv: dbg - g_abExecMemory=ffffffffa04b6e00
[   10.608539] vboxdrv: fAsync=0 offMin=0x1d2 offMax=0x266a8
[   10.608578] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   10.608580] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
[   10.713242]   alloc irq_desc for 49 on node -1
[   10.713244]   alloc kstat_irqs on node -1
[   10.713253] fglrx_pci 0000:01:00.0: irq 49 for MSI/MSI-X
[   10.713706] [fglrx] Firegl kernel thread PID: 1359
[   10.713903] [fglrx] IRQ 49 Enabled
[   11.100063] [fglrx] Gart USWC size:1216 M.
[   11.100065] [fglrx] Gart cacheable size:482 M.
[   11.100069] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   11.100071] [fglrx] Reserved FB block: Unshared offset:fc31000, size:3cf000 
[   11.100072] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   11.606910] [fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
[   12.806103] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   12.810376] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   12.960104] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.086964] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   18.017136] wlan0: authenticate with 00:1f:c6:62:2a:7c (try 1)
[   18.019039] wlan0: authenticated
[   18.096998] wlan0: associate with 00:1f:c6:62:2a:7c (try 1)
[   18.295269] wlan0: associate with 00:1f:c6:62:2a:7c (try 2)
[   18.297389] wlan0: RX AssocResp from 00:1f:c6:62:2a:7c (capab=0x411 status=0 aid=2)
[   18.297394] wlan0: associated
[   18.379371] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.064152] wlan0: no IPv6 routers present
[  306.394307] usb 3-1.2: new high speed USB device using ehci_hcd and address 5
[  306.541034] scsi5 : usb-storage 3-1.2:1.1
[  306.541741] scsi6 : usb-storage 3-1.2:1.2
[  306.836826] usb 3-1.2: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[  306.837369] usb 3-1.2: usbfs: interface 2 claimed by usb-storage while 'bcharge' sets config #1
[  307.534785] scsi 6:0:0:0: Direct-Access     RIM      BlackBerry SD    0002 PQ: 0 ANSI: 0 CCS
[  307.536557] sd 6:0:0:0: Attached scsi generic sg8 type 0
[  307.538972] sd 6:0:0:0: [sdh] Attached SCSI removable disk
[  307.911373] usb 3-1.2: reset high speed USB device using ehci_hcd and address 5
[  350.592578] usb 3-1.2: reset high speed USB device using ehci_hcd and address 5
[  376.654026] usb 3-1.2: usbfs: process 2960 (barrybackup) did not claim interface 0 before use
[  414.673274] usb 3-1.2: USB disconnect, address 5
[  414.960539] usb 3-1.2: new high speed USB device using ehci_hcd and address 6
[  415.110238] scsi7 : usb-storage 3-1.2:1.1
[  415.140181] scsi8 : usb-storage 3-1.2:1.2
[  415.434585] usb 3-1.2: usbfs: interface 1 claimed by usb-storage while 'bcharge' sets config #1
[  415.434926] usb 3-1.2: usbfs: interface 2 claimed by usb-storage while 'bcharge' sets config #1
[  416.160889] scsi 8:0:0:0: Direct-Access     RIM      BlackBerry SD    0002 PQ: 0 ANSI: 0 CCS
[  416.161747] sd 8:0:0:0: Attached scsi generic sg8 type 0
[  416.163671] sd 8:0:0:0: [sdh] Attached SCSI removable disk
[  416.509008] usb 3-1.2: reset high speed USB device using ehci_hcd and address 6
[  612.814241] usb 3-1.2: USB disconnect, address 6
[  647.534294] usb 3-1.2: new high speed USB device using ehci_hcd and address 7
[  647.646433] usb-storage 3-1.2:1.0: Quirks match for vid 071b pid 3203: 400
[  647.646644] scsi9 : usb-storage 3-1.2:1.0
[  648.676004] scsi 9:0:0:0: Direct-Access     MP-233   MP4 Player       1.00 PQ: 0 ANSI: 0
[  648.677663] sd 9:0:0:0: Attached scsi generic sg8 type 0
[  648.680454] sd 9:0:0:0: [sdh] 3903488 512-byte logical blocks: (1.99 GB/1.86 GiB)
[  648.681068] sd 9:0:0:0: [sdh] Write Protect is off
[  648.681073] sd 9:0:0:0: [sdh] Mode Sense: 03 00 00 00
[  648.681077] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[  648.684046] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[  648.684054]  sdh: sdh1
[  648.687428] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[  648.687434] sd 9:0:0:0: [sdh] Attached SCSI removable disk

```

---

### Post by psusi on 2011-01-10
Intel is usually more supportive of Linux than that.  It sounds like you just got a low level slacker and need to ask to be escalated.  What makes you think it is not running in dual channel mode?  That is a function of the hardware and bios, not the OS.  It is a bit odd though, that lshw reports your dimms are being run at two different speeds.

As for why you don't see the full amount of ram, it appears that your bios is broken and is only reporting that you have about 5gb of ram, then the kernel throws out 768mb of it for some reason, here:

x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)

---

### Post by [Snc] on 2011-01-10
> **psusi said:**
> Intel is usually more supportive of Linux than that.  It sounds like you just got a low level slacker and need to ask to be escalated.  What makes you think it is not running in dual channel mode?  That is a function of the hardware and bios, not the OS.  It is a bit odd though, that lshw reports your dimms are being run at two different speeds.

As for why you don't see the full amount of ram, it appears that your bios is broken and is only reporting that you have about 5gb of ram, then the kernel throws out 768mb of it for some reason, here:

x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)

hm :( thats bad, and yes, the rams are of different speed (same model/make number, different speed)

well ... besides buying a new motherboard, what can i do about it :}

---

### Post by psusi on 2011-01-10
> **'[Snc] said:**
> hm :( thats bad, and yes, the rams are of different speed (same model/make number, different speed)

well ... besides buying a new motherboard, what can i do about it :}

That is odd.. if it is a different speed it should have a different model number.  You can complain to Intel ;)

---

### Post by [Snc] on 2011-01-10
> **psusi said:**
> T... You can complain to Intel ;)

not Intel, the ram is from OCZ Technology, first i ordered a 2*2Gib set and after a few months ordered another one with the same same part number (and same specs) and got something else.

even so, the odd thing is, that someone said the machine reports about 5Gb of ram, well even with just 2*2Gib, i couldn't make it run in dual channel mode, so i guess the problem is with the motherboard :confused:

---

### Post by Yellow Pasque on 2011-01-10
Yeah, Intel mobos are just rebrands from a mass manufacturer (Foxconn or ECS IIRC). Either way, they're probably not the best boards and won't have good enough tech support to fix these issues (which are hard enough to get addressed by big-name mobo makers like Asus). Good luck with that, though...

---

### Post by psusi on 2011-01-10
Again, how do you know it isn't running in dual channel mode?  It could be because they are not the same speed, so pull the two slower ones out and see if the faster pair will run dual channel.

---

### Post by [Snc] on 2011-01-11
> **psusi said:**
> Again, how do you know it isn't running in dual channel mode?  It could be because they are not the same speed, so pull the two slower ones out and see if the faster pair will run dual channel.

i already did that, before when i had only one pair of modules (the slow ones) and in dual channel mode, the OS just showed me half the ram (2Gb), so i flipped it back into single channel mode and did not bother, since 4Gb was good enough and the speed was satisfying :). 

but since then, i bought another pair and all 4 slots where filled now, with - what should have given me 8Gb of ram, but it does not :(, even after i tried every possible available combination (also including using only 3 sticks).

well, i'm slightly lost now :) and also slightly disappointed over Intel (as a mobo producer and non Linux supporter...), so i guess ill just stick to buying a gigabyte mobo, or something like that ... 

any suggestions on a good mobo? price/performance counts :)

**Intel, i am disappoint!!!**

---

### Post by psusi on 2011-01-11
Wait, so when you only had two sticks, if you enabled dual channel in the bios, only 2gb showed up, but you got all 4gb when you disabled dual channel?

Yea, that is a b0rked motherboard alright.

---

### Post by psusi on 2011-01-11
Forums have been messed up lately.  Kept getting a proxy error and retrying.

---

### Post by psusi on 2011-01-11
Grrr, busticated forums.

---

### Post by [Snc] on 2011-01-11
> **psusi said:**
> Grrr, busticated forums.
yes, 

2*2Gb sticks (any pair or combination)
dual channel -> half ram
single channel -> full ram ("free -mo" says 3894M total <- I guess that's not OK either???)

4*2Gb
:confused: i am not even sure if anything goes dual there, "free -mo" gives me the same result as above...

Anyhow ... i guess i will/should end this thread, since it obviously is a "bad mobo" problem and no one can help me there :(

PS. I just wanted to say kudos & tnx to you all, that tried!

---


---
title: "Core 2 Duo Frequency Scaling"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2008-02-12
Hi Ubuntuers!

I've come across a so far utterly confounding problem with my new 64-bit Gutsy install.   The machine's CPU is an Intel Core 2 Duo E8500, which supposedly runs at 3.16Ghz, 1333Mhz bus.  

Cpufreq has incorrectly identified -- or is incorrectly reporting -- the CPU's maximum frequency as 3 Ghz.  The reported available speeds are 2 and 3 GHz, and nothing in between.  I can't find it anywhere online, but I expect that the CPU supports more than just two speeds.  

Since the speed is correctly reported in /proc/cpuinfo I suspect this might be just a reporting problem.  But the issue with the number of steps (if indeed there are more than two) has got to be something deeper. 

Any help will be appreciated muchly!

Here's dmsg and other possibly helpful things.


Cheers,

Simon




```

simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 2.00 GHz - 3.00 GHz
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 2.00 GHz and 3.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 2.00 GHz - 3.00 GHz
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 2.00 GHz and 3.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.00 GHz.
simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$


simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ more *gov*
::::::::::::::
scaling_available_governors
::::::::::::::
conservative powersave ondemand userspace performance
::::::::::::::
scaling_governor
::::::::::::::
performance




simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ more *freq*
::::::::::::::
cpuinfo_max_freq
::::::::::::::
3000000
::::::::::::::
cpuinfo_min_freq
::::::::::::::
2000000
::::::::::::::
scaling_available_frequencies
::::::::::::::
3000000 2000000
::::::::::::::
scaling_cur_freq
::::::::::::::
2000000
::::::::::::::
scaling_max_freq
::::::::::::::
3000000
::::::::::::::
scaling_min_freq
::::::::::::::
2000000


simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq/ondemand$ cat /proc/cpuinfo | grep '^cpu MHz'
cpu MHz         : 2000.000
cpu MHz         : 2000.000



simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq/ondemand$ lsmod | grep freq
acpi_cpufreq           10632  0
cpufreq_conservative     9608  0
cpufreq_powersave       3072  0
cpufreq_stats           8160  0
cpufreq_ondemand       10896  2
cpufreq_userspace       6048  0
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              36232  2 acpi_cpufreq,thermal


simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq/ondemand$ cpufreq-info | grep available
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  available frequency steps: 3.00 GHz, 2.00 GHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance


simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq/ondemand$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3000000 2000000

simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ cat cpuinfo_max_freq
3000000
simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ cat scaling_driver
acpi-cpufreq
simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ cat scaling_governor
ondemand


simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping        : 6
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6337.34
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping        : 6
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6333.31
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Jan 31 23:33:13 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] Command line: root=UUID=83ac3697-62d6-49e7-ae0d-62aa3e498077 ro vga=4
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6B60 checksum 0
[    0.000000] ACPI: RSDP 000F6B60, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT DFEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP DFEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT DFEE3180, 4B25 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS DFEE0000, 0040
[    0.000000] ACPI: HPET DFEE7E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG DFEE7E80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC DFEE7D00, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT DFEE7F00, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT DFEE8390, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1179648
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   917216
[    0.000000]     0:  1048576 ->  1179648
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1127 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898840 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000dfee0000 - 00000000dfee3000
[    0.000000] swsusp: Registered nosave memory region: 00000000dfee3000 - 00000000dfef0000
[    0.000000] swsusp: Registered nosave memory region: 00000000dfef0000 - 00000000dff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000dff00000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000f4000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f4000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1030936
[    0.000000] Kernel command line: root=UUID=83ac3697-62d6-49e7-ae0d-62aa3e498077 ro vga=4
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   34.130741] time.c: Detected 3166.664 MHz processor.
[   34.132107] Console: colour VGA+ 80x30
[   34.134913] Checking aperture...
[   34.134955] Calgary: detecting Calgary via BIOS EBDA area
[   34.134956] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   34.134957] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   34.161420] Placing software IO TLB between 0x104c000 - 0x504c000
[   34.187896] Memory: 4049948k/4718592k available (2274k kernel code, 142816k reserved, 1181k data, 296k init)
[   34.187974] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   34.267007] Calibrating delay using timer specific routine.. 6337.34 BogoMIPS (lpj=12674693)
[   34.267100] Security Framework v1.0.0 initialized
[   34.267142] SELinux:  Disabled at boot.
[   34.267385] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   34.269151] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   34.270012] Mount-cache hash table entries: 256
[   34.270135] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.270201] CPU: L2 cache: 6144K
[   34.270238] CPU 0/0 -> Node 0
[   34.270275] using mwait in idle threads.
[   34.270312] CPU: Physical Processor ID: 0
[   34.270349] CPU: Processor Core ID: 0
[   34.270390] CPU0: Thermal monitoring enabled (TM2)
[   34.270434] SMP alternatives: switching to UP code
[   34.270635] Early unpacking initramfs... done
[   34.486176] ACPI: Core revision 20070126
[   34.486239] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   34.528683] Using local APIC timer interrupts.
[   34.560268] result 20833321
[   34.560304] Detected 20.833 MHz APIC timer.
[   34.562702] SMP alternatives: switching to SMP code
[   34.562792] Booting processor 1/2 APIC 0x1
[   34.573342] Initializing CPU#1
[   34.650568] Calibrating delay using timer specific routine.. 6333.31 BogoMIPS (lpj=12666632)
[   34.650572] CPU: L1 I cache: 32K, L1 D cache: 32K
[   34.650573] CPU: L2 cache: 6144K
[   34.650575] CPU 1/1 -> Node 0
[   34.650576] CPU: Physical Processor ID: 0
[   34.650576] CPU: Processor Core ID: 1
[   34.650580] CPU1: Thermal monitoring enabled (TM2)
[   34.651161] Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz stepping 06
[   34.651214] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   34.674551] Brought up 2 CPUs
[   34.742800] migration_cost=9
[   34.743001] NET: Registered protocol family 16
[   34.743090] ACPI: bus type pci registered
[   34.743131] PCI: Using configuration type 1
[   34.743829] ACPI: EC: Look up EC in DSDT
[   34.746676] ACPI: Interpreter enabled
[   34.746717] ACPI: (supports S0 S3 S4 S5)
[   34.746895] ACPI: Using IOAPIC for interrupt routing
[   34.750319] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.750367] PCI: Probing PCI hardware (bus 00)
[   34.751317] PCI: Transparent bridge - 0000:00:1e.0
[   34.751396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.751478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   34.751521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   34.751566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   34.751607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   34.760398] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   34.760833] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   34.761319] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   34.761755] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   34.762189] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   34.762678] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[   34.763111] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   34.763544] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   34.763973] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.764017] pnp: PnP ACPI init
[   34.764058] ACPI: bus type pnp registered
[   34.765492] pnp: PnP ACPI: found 13 devices
[   34.765530] ACPI: ACPI bus type pnp unregistered
[   34.765598] PCI: Using ACPI for IRQ routing
[   34.765636] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.765742] NET: Registered protocol family 8
[   34.765780] NET: Registered protocol family 20
[   34.765825] PCI-GART: No AMD northbridge found.
[   34.765866] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   34.766033] hpet0: 4 64-bit timers, 14318180 Hz
[   34.767114] pnp: 00:09: ioport range 0x400-0x4bf has been reserved
[   34.767155] pnp: 00:0a: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   34.767205] pnp: 00:0b: iomem range 0xcca00-0xcffff has been reserved
[   34.767245] pnp: 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   34.767285] pnp: 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   34.767326] pnp: 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   34.767525] PCI: Bridge: 0000:00:01.0
[   34.767563]   IO window: b000-bfff
[   34.767601]   MEM window: f4000000-f7ffffff
[   34.767639]   PREFETCH window: e0000000-efffffff
[   34.767678] PCI: Bridge: 0000:00:1c.0
[   34.767716]   IO window: 9000-9fff
[   34.767754]   MEM window: disabled.
[   34.767792]   PREFETCH window: disabled.
[   34.767832] PCI: Bridge: 0000:00:1c.3
[   34.767869]   IO window: c000-cfff
[   34.767908]   MEM window: f8000000-f8ffffff
[   34.767947]   PREFETCH window: disabled.
[   34.767986] PCI: Bridge: 0000:00:1c.4
[   34.768024]   IO window: d000-dfff
[   34.768062]   MEM window: f9000000-faffffff
[   34.768101]   PREFETCH window: fb100000-fb1fffff
[   34.768141] PCI: Bridge: 0000:00:1e.0
[   34.769049]   IO window: a000-afff
[   34.769088]   MEM window: disabled.
[   34.769125]   PREFETCH window: disabled.
[   34.769170] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.769245] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   34.769255] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.769330] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   34.769341] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   34.769417] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   34.769427] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   34.769502] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   34.769509] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   34.769514] NET: Registered protocol family 2
[   34.770432] Time: tsc clocksource has been installed.
[   34.810476] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   34.811232] TCP established hash table entries: 524288 (order: 11, 12582912 bytes)
[   34.815316] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   34.815771] TCP: Hash tables configured (established 524288 bind 65536)
[   34.815812] TCP reno registered
[   34.830492] checking if image is initramfs... it is
[   35.256962] Freeing initrd memory: 7519k freed
[   35.258927] audit: initializing netlink socket (disabled)
[   35.258980] audit(1202864867.092:1): initialized
[   35.260163] VFS: Disk quotas dquot_6.5.1
[   35.260227] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   35.260316] io scheduler noop registered
[   35.260354] io scheduler anticipatory registered
[   35.260392] io scheduler deadline registered
[   35.260480] io scheduler cfq registered (default)
[   35.265004] Boot video device is 0000:01:00.0
[   35.265086] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.265104] assign_interrupt_mode Found MSI capability
[   35.265145] Allocate Port Service[0000:00:01.0:pcie00]
[   35.265189] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   35.265215] assign_interrupt_mode Found MSI capability
[   35.265253] Allocate Port Service[0000:00:1c.0:pcie00]
[   35.265272] Allocate Port Service[0000:00:1c.0:pcie02]
[   35.265318] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   35.265344] assign_interrupt_mode Found MSI capability
[   35.265383] Allocate Port Service[0000:00:1c.3:pcie00]
[   35.265398] Allocate Port Service[0000:00:1c.3:pcie02]
[   35.265446] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   35.265472] assign_interrupt_mode Found MSI capability
[   35.265510] Allocate Port Service[0000:00:1c.4:pcie00]
[   35.265528] Allocate Port Service[0000:00:1c.4:pcie02]
[   35.276233] Real Time Clock Driver v1.12ac
[   35.276367] hpet_resources: 0xfed00000 is busy
[   35.276388] Linux agpgart interface v0.102 (c) Dave Jones
[   35.276427] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.276550] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.276877] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.277256] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.277370] input: Macintosh mouse button emulation as /class/input/input0
[   35.277468] PNP: No PS/2 controller found. Probing ports directly.
[   35.277760] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.277803] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.277968] mice: PS/2 mouse device common for all mice
[   35.278125] TCP cubic registered
[   35.278197] NET: Registered protocol family 1
[   35.278339] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   35.278393] Freeing unused kernel memory: 296k freed
[   35.365801] AppArmor: AppArmor initialized<5>audit(1202864867.200:2):  type=1505 info="AppArmor initialized" pid=1233
[   35.369070] fuse init (API version 7.8)
[   35.371374] Failure registering capabilities with primary security module.
[   35.393642] ACPI: Processor [CPU0] (supports 8 throttling states)
[   35.393798] ACPI: SSDT DFEE8300, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   35.393958] ACPI: Processor [CPU1] (supports 8 throttling states)
[   35.394054] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.394159] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   35.599552] usbcore: registered new interface driver usbfs
[   35.599607] usbcore: registered new interface driver hub
[   35.602678] usbcore: registered new device driver usb
[   35.603180] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   35.604429] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   35.604434] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   35.604570] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   35.604644] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   35.604651] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb004000
[   35.608563] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.608670] usb usb1: configuration #1 chosen from 1 choice
[   35.608723] hub 1-0:1.0: USB hub found
[   35.608763] hub 1-0:1.0: 6 ports detected
[   35.609208] USB Universal Host Controller Interface driver v3.0
[   35.612360] SCSI subsystem initialized
[   35.614668] libata version 2.21 loaded.
[   35.713620] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   35.714837] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   35.714841] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   35.715049] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   35.715119] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   35.715126] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb005000
[   35.719035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.719278] usb usb2: configuration #1 chosen from 1 choice
[   35.719408] hub 2-0:1.0: USB hub found
[   35.719448] hub 2-0:1.0: 6 ports detected
[   35.821484] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.821564] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   35.821566] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   35.821615] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   35.821683] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[   35.821771] usb usb3: configuration #1 chosen from 1 choice
[   35.821821] hub 3-0:1.0: USB hub found
[   35.821862] hub 3-0:1.0: 2 ports detected
[   35.925188] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   35.925273] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   35.925275] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   35.925322] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   35.925387] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[   35.925472] usb usb4: configuration #1 chosen from 1 choice
[   35.925522] hub 4-0:1.0: USB hub found
[   35.925561] hub 4-0:1.0: 2 ports detected
[   35.965086] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   36.029070] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   36.029155] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   36.029157] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   36.029203] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[   36.029267] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[   36.029355] usb usb5: configuration #1 chosen from 1 choice
[   36.029404] hub 5-0:1.0: USB hub found
[   36.029444] hub 5-0:1.0: 2 ports detected
[   36.097315] usb 1-2: configuration #1 chosen from 1 choice
[   36.097429] hub 1-2:1.0: USB hub found
[   36.097568] hub 1-2:1.0: 4 ports detected
[   36.132958] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   36.133043] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   36.133045] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   36.133091] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[   36.133155] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[   36.133238] usb usb6: configuration #1 chosen from 1 choice
[   36.133288] hub 6-0:1.0: USB hub found
[   36.133327] hub 6-0:1.0: 2 ports detected
[   36.236841] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   36.236926] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   36.236927] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   36.236975] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[   36.237040] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[   36.237127] usb usb7: configuration #1 chosen from 1 choice
[   36.237176] hub 7-0:1.0: USB hub found
[   36.237215] hub 7-0:1.0: 2 ports detected
[   36.340729] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   36.340813] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   36.340815] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   36.340863] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[   36.340927] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[   36.341012] usb usb8: configuration #1 chosen from 1 choice
[   36.341062] hub 8-0:1.0: USB hub found
[   36.341101] hub 8-0:1.0: 2 ports detected
[   36.444691] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.444743] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.444826] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   36.444987] eth0: RTL8168b/8111b at 0xffffc2000143a000, 00:1d:7d:a5:de:dc, XID 38000000 IRQ 16
[   36.447701] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   36.447795] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   36.447933] scsi0 : pata_jmicron
[   36.448528] scsi1 : pata_jmicron
[   36.448625] ata1: PATA max UDMA/100 cmd 0x000000000001c000 ctl 0x000000000001c102 bmdma 0x000000000001c400 irq 19
[   36.448676] ata2: PATA max UDMA/100 cmd 0x000000000001c200 ctl 0x000000000001c302 bmdma 0x000000000001c408 irq 19
[   36.760286] ata_piix 0000:00:1f.2: version 2.11
[   36.760292] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   36.760483] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   36.760580] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   36.760610] scsi2 : ata_piix
[   36.761544] scsi3 : ata_piix
[   36.761634] ata3: SATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001f000 irq 14
[   36.761686] ata4: SATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001f008 irq 15
[   37.175758] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   37.235862] ata3.00: ATAPI: ASUS    DRW-2014L1T, 1.00, max UDMA/66
[   37.355871] usb 4-1: configuration #1 chosen from 1 choice
[   37.407674] ata3.00: configured for UDMA/66
[   37.574419] scsi 2:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.00 PQ: 0 ANSI: 5
[   37.574519] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   37.574695] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   37.574781] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   37.574797] scsi4 : ata_piix
[   37.574851] scsi5 : ata_piix
[   37.574934] ata5: SATA max UDMA/133 cmd 0x000000000001e700 ctl 0x000000000001e802 bmdma 0x000000000001eb00 irq 19
[   37.574986] ata6: SATA max UDMA/133 cmd 0x000000000001e900 ctl 0x000000000001ea02 bmdma 0x000000000001eb08 irq 19
[   37.607291] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   37.735417] ata5.00: Host Protected Area detected:
[   37.735418]  current size: 976771055 sectors
[   37.735419]  native size: 976773168 sectors
[   37.735656] ata5.00: native size increased to 976773168 sectors
[   37.735700] ata5.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   37.735742] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.743412] ata5.00: configured for UDMA/133
[   37.794363] usb 4-2: configuration #1 chosen from 1 choice
[   37.923216] ata6.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   37.923258] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.931205] ata6.00: configured for UDMA/133
[   37.931295] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   37.931548] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   37.934371] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   37.934416] sd 4:0:0:0: [sda] Write Protect is off
[   37.934455] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.934462] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.934536] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   37.934583] sd 4:0:0:0: [sda] Write Protect is off
[   37.934621] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.934630] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.934681]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   37.941133] Uniform CD-ROM driver Revision: 3.20
[   37.941199] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   38.003150]  sda1 sda2 sda3
[   38.022593] sd 4:0:0:0: [sda] Attached SCSI disk
[   38.022724] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   38.022768] sd 5:0:0:0: [sdb] Write Protect is off
[   38.022807] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.022814] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.022881] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   38.022925] sd 5:0:0:0: [sdb] Write Protect is off
[   38.022964] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.022971] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.023021]  sdb: sdb1
[   38.031704] sd 5:0:0:0: [sdb] Attached SCSI disk
[   38.033453] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   38.033501] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   38.033549] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   38.034829] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   38.177779] Attempting manual resume
[   38.177817] swsusp: Resume From Partition 8:3
[   38.177818] PM: Checking swsusp image.
[   38.177961] PM: Resume from disk failed.
[   38.210906] usb 5-1: configuration #1 chosen from 1 choice
[   38.216230] kjournald starting.  Commit interval 5 seconds
[   38.216235] EXT3-fs: mounted filesystem with ordered data mode.
[   38.430503] usb 1-2.4: new high speed USB device using ehci_hcd and address 6
[   38.523332] usb 1-2.4: configuration #1 chosen from 1 choice
[   38.523788] usbcore: registered new interface driver hiddev
[   38.537627] input: Kingsis Peripherals  Evoluent VerticalMouse 3  as /class/input/input1
[   38.537684] input: USB HID v1.10 Mouse [Kingsis Peripherals  Evoluent VerticalMouse 3 ] on usb-0000:00:1a.1-1
[   38.551611] input: SEJIN SEJIN USB joint Keyboard as /class/input/input2
[   38.551654] input: USB HID v1.10 Keyboard [SEJIN SEJIN USB joint Keyboard] on usb-0000:00:1a.2-1
[   38.551758] usbcore: registered new interface driver usbhid
[   38.551797] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.236266] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.238961] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.257049] usbcore: registered new interface driver libusual
[   44.286273] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   44.286316] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   44.296336] parport_pc 00:08: reported by Plug and Play ACPI
[   44.296416] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   44.373464] Initializing USB Mass Storage driver...
[   44.373548] scsi6 : SCSI emulation for USB Mass Storage devices
[   44.373612] usb-storage: device found at 6
[   44.373614] usb-storage: waiting for device to settle before scanning
[   44.373617] usbcore: registered new interface driver usb-storage
[   44.373657] USB Mass Storage support registered.
[   44.396076] input: PC Speaker as /class/input/input3
[   44.449784] nvidia: module license 'NVIDIA' taints kernel.
[   44.701809] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.701891] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   44.701937] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   44.822643] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   44.823806] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.859455] usbcore: registered new interface driver snd-usb-audio
[   45.718606] lp0: using parport0 (interrupt-driven).
[   45.765194] it87: Found IT8718F chip at 0x290, revision 4
[   45.765240] it87: in3 is VCC (+5V)
[   45.813562] Adding 9767512k swap on /dev/sda3.  Priority:-1 extents:1 across:9767512k
[   46.154469] EXT3 FS on sda1, internal journal
[   46.262257] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   46.813846] kjournald starting.  Commit interval 5 seconds
[   46.814237] EXT3 FS on sda2, internal journal
[   46.814240] EXT3-fs: mounted filesystem with ordered data mode.
[   49.196497] input: Power Button (FF) as /class/input/input4
[   49.196588] ACPI: Power Button (FF) [PWRF]
[   49.209994] input: Power Button (CM) as /class/input/input5
[   49.211265] ACPI: Power Button (CM) [PWRB]
[   49.222559] No dock devices found.
[   49.366917] usb-storage: device scan complete
[   49.367544] scsi 6:0:0:0: Direct-Access     Initio   HD501LJ          4.36 PQ: 0 ANSI: 0
[   49.368655] sd 6:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   49.369281] sd 6:0:0:0: [sdc] Write Protect is off
[   49.369283] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   49.369285] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   49.370153] sd 6:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   49.370778] sd 6:0:0:0: [sdc] Write Protect is off
[   49.370780] sd 6:0:0:0: [sdc] Mode Sense: 00 00 00 00
[   49.370781] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   49.370830]  sdc: sdc1 sdc2 sdc3 sdc4
[   49.371842] sd 6:0:0:0: [sdc] Attached SCSI disk
[   49.371871] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   49.857064] ppdev: user-space parallel port driver
[   50.012379] r8169: eth0: link up
[   50.012385] r8169: eth0: link up
[   50.055350] audit(1202864882.408:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5654 profile="/usr/sbin/cupsd"
[   50.263263] Netfilter messages via NETLINK v0.30.
[   50.271974] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   50.314626] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.509697] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   50.564172] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   50.568770] NFSD: starting 90-second grace period
[   51.530494] Failure registering capabilities with primary security module.
[   51.653724] Bluetooth: Core ver 2.11
[   51.653834] NET: Registered protocol family 31
[   51.653835] Bluetooth: HCI device and connection manager initialized
[   51.653837] Bluetooth: HCI socket layer initialized
[   51.658000] Bluetooth: L2CAP ver 2.8
[   51.658002] Bluetooth: L2CAP socket layer initialized
[   51.749379] Bluetooth: RFCOMM socket layer initialized
[   51.749464] Bluetooth: RFCOMM TTY layer initialized
[   51.749466] Bluetooth: RFCOMM ver 1.8
[   52.383970] NET: Registered protocol family 10
[   52.384021] lo: Disabled Privacy Extensions
[   54.175384] /dev/vmmon[6362]: VMCI: Driver initialized.
[   54.175546] /dev/vmmon[6362]: Module vmmon: registered with major=10 minor=165
[   54.175631] /dev/vmmon[6362]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   54.175633] /dev/vmmon[6362]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   54.175635] /dev/vmmon[6362]: Module vmmon: initialized
[   54.476670] /dev/vmnet: open called by PID 6409 (vmnet-bridge)
[   54.476675] /dev/vmnet: hub 0 does not exist, allocating memory.
[   54.476681] /dev/vmnet: port on hub 0 successfully opened
[   54.476685] bridge-eth0: enabling the bridge
[   54.476687] bridge-eth0: up
[   54.476688] bridge-eth0: already up
[   54.476689] bridge-eth0: attached
[   54.614517] /dev/vmnet: open called by PID 6426 (vmnet-netifup)
[   54.614609] /dev/vmnet: hub 1 does not exist, allocating memory.
[   54.614682] /dev/vmnet: port on hub 1 successfully opened
[   54.689370] /dev/vmnet: open called by PID 6425 (vmnet-dhcpd)
[   54.689467] /dev/vmnet: port on hub 1 successfully opened
[   54.691431] /dev/vmnet: open called by PID 6446 (vmnet-netifup)
[   54.691509] /dev/vmnet: hub 8 does not exist, allocating memory.
[   54.691582] /dev/vmnet: port on hub 8 successfully opened
[   54.723723] /dev/vmnet: open called by PID 6459 (vmnet-dhcpd)
[   54.723732] /dev/vmnet: port on hub 8 successfully opened
[   54.744861] /dev/vmnet: open called by PID 6469 (vmnet-natd)
[   54.744865] /dev/vmnet: port on hub 8 successfully opened
[   55.988503] NET: Registered protocol family 17
[   64.706765] vmnet1: no IPv6 routers present
[   65.426021] vmnet8: no IPv6 routers present
[   68.502840] eth0: no IPv6 routers present
[   80.407262] kjournald starting.  Commit interval 5 seconds
[   80.407627] EXT3 FS on sdc4, internal journal
[   80.407683] EXT3-fs: mounted filesystem with ordered data mode.
[   80.447343] kjournald starting.  Commit interval 5 seconds
[   80.458820] EXT3 FS on sdc1, internal journal
[   80.458824] EXT3-fs: mounted filesystem with ordered data mode.
[   80.490792] kjournald starting.  Commit interval 5 seconds
[   80.490800] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   80.491283] EXT3 FS on sdc2, internal journal
[   80.491286] EXT3-fs: mounted filesystem with ordered data mode.


```

---

### Post by Existentialist on 2008-02-13
The default settings in BIOS for intel motherboards allows the OS to send a signal to BIOS which drops the cpu multiplier by 3.  For the e800 series with a 333fsb this drops the cpu frequency (3x333=~1Ghz).  It only allows for these two settings (9.5x and 6.5x on the e8500) unless you manually drop the multiplier.

Since these e8000 cpus are new I would check your BIOS to ensure the multiplier was set correctly by BIOS to 9.5x, I know when I first booted with my e8400 BIOS had it set at a 7x multiplier (should be 9x).  The speedstep frequency scaling features are usually called C1E & EIST on the motherboard if you want to check out what settings your BIOS offers for that also.

---

### Post by simoncullen on 2008-02-13
Hi! 

Thanks for your reply.  

I have checked the BIOS and the multiplier is set correctly to 9.5.  I'm pretty sure that's not the problem since (1) the processor is actually reported correctly and (2) even when using the "performance" cpufreq governor it maxes out at 3Ghz.

Interestingly, my vmware VM reports the correct frequency too.  The CPU frequency monitor reports the correct frequency (3.16Ghz) when I disable ACPI (by booting with the "noacpi" flag).  Unfortunately, this also disables scaling and all the other nice power saving features.

Any more ideas?

Simon

---

### Post by Existentialist on 2008-02-13
I was noticing in your original post you said the /proc/cpuinfo was reporting correctly.  I assume you were looking at this line:

model name      : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz

This is actually the name as reported by the cpu rather than the actual speed it is running at.  For example, mine says:

model name      : Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz

even though it is overclocked to 3.6.  It is actually reading the frequency as:

cpu MHz         : 2000.000

So it is scaling down to the 6x multiplier fine.  As for to see if it runs at the stated 3.16 you would have to put a load on the cpu and then run /proc/cpuinfo and that should cause the cpu to scale back to its 9.5x multiplier and run at 3160MHz.

---

### Post by simoncullen on 2008-02-13
> **Existentialist said:**
> I was noticing in your original post you said the /proc/cpuinfo was reporting correctly.  I assume you were looking at this line:

model name      : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz.


And this one from dmesg:

```
[ 34.130741] time.c: Detected 3166.664 MHz processor.
```

I think cpufreq is incorrectly identifying the mix/max frequencies.  Under full load it still reports 3Ghz.

How many speed steps does your CPU have?


Simon

---

### Post by Existentialist on 2008-02-13
I know from being in windows that when the cpu is scaled down it drops from my 9x multiplier to 6x (so from 3.6GHz to 2.4GHz).  Unfortunately I read somewhere about a config file you have to change in Ubuntu 8.04 to get frequency scaling to work after you have overclocked the cpu, and I can't find that post again to try it.  Until I figure it out I don't even have /proc/cpuinfo, but if I figure it out I'll tell you my results.

---

### Post by Existentialist on 2008-02-13
Thought I would post an interesting article about speedstep on Linux I found from Intel while searching for better answers to both of our questions.

[http://softwarecommunity.intel.com/articles/eng/1611.htm](http://softwarecommunity.intel.com/articles/eng/1611.htm)

---

### Post by simoncullen on 2008-02-15
That is an interesting article.  I've been Googling and searching various forums and so far nothing has turned up!  This is a most vexatious problem!

---

### Post by simoncullen on 2008-02-16
This bug report seems relevant: [http://bugzilla.kernel.org/show_bug.cgi?id=9636](http://bugzilla.kernel.org/show_bug.cgi?id=9636)

Interestingly, I've found that dmesg reports "ACPI: Processor [CPU1] (supports 8 throttling states)" -- but only two are ever available -- 2Ghz and 3Ghz.  There is also this exception directly below:

> [   25.670140] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.670245] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]



Here's the full output:

```
simon@aristurtle:/sys/devices/system/cpu/cpu1/cpufreq$ dmesg |grep -i acpi[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6B60 checksum 0
[    0.000000] ACPI: RSDP 000F6B60, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT DFEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP DFEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT DFEE3180, 4B25 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS DFEE0000, 0040
[    0.000000] ACPI: HPET DFEE7E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG DFEE7E80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC DFEE7D00, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT DFEE7F00, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT DFEE8390, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   22.646220] ACPI: Core revision 20070126
[   22.646282] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.025681] ACPI: bus type pci registered
[   25.026418] ACPI: EC: Look up EC in DSDT
[   25.029263] ACPI: Interpreter enabled
[   25.029304] ACPI: (supports S0 S3 S4 S5)
[   25.029482] ACPI: Using IOAPIC for interrupt routing
[   25.032883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.033955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.034037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   25.034080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   25.034122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   25.034166] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.042992] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.043426] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.043911] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   25.044343] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[   25.044776] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.045261] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   25.045693] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.046126] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[   25.046611] pnp: PnP ACPI init
[   25.046651] ACPI: bus type pnp registered
[   25.048038] pnp: PnP ACPI: found 12 devices
[   25.048075] ACPI: ACPI bus type pnp unregistered
[   25.048141] PCI: Using ACPI for IRQ routing
[   25.050924] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.051009] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.051095] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   25.051181] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI[B] 16 (level, low) -> IRQ 16
[   25.669723] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.669885] ACPI: SSDT DFEE8300, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   25.670045] ACPI: Processor [CPU1] (supports 8 throttling states)
[   25.670140] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.670245] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.934031] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16[/B]
[   25.937656] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.045502] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   26.153382] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.261263] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   26.369146] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   26.477029] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.585737] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   26.953350] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   27.786819] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   27.786883] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   28.099358] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   35.342053] parport_pc 00:07: reported by Plug and Play ACPI
[   35.720283] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.809882] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   94.318355] ACPI: Power Button (FF) [PWRF]
[   94.318381] ACPI: Power Button (CM) [PWR
```

---

### Post by Yellow Pasque on 2008-02-16
It almost seems as if the acpi driver can't cope with half-multipliers. (6*333=2 GHz, 9*333=3GHz).

---

### Post by simoncullen on 2008-02-16
That's an interesting suggestion.  I wonder if other people are having the same difficulty?

I'm using a Gigabyt GA-P35-DS3L mobo -- is it possible that it's taking care of the CPU scaling?  There is no appreciable difference in temperature or voltage when I run it at 3Ghz or 2Ghz.  

I thought I'd play around with the BIOS settings and for fun I tired to  overclock the CPU.  I turned up the core voltage to 1.2v (from 1.15) and got it to run (seemingly) stable at 3.6Ghz.  This totally disables cpufreq's ability to modulate the clock speed (cpufreq-info reports:"no or unknown cpufreq driver is active on this CPU").  Which you might expect would increase the CPU temperature significantly.  But, lo, it seems almost entirely uneffected -- idling now at 35 degrees.  Does this suggest that the BIOS is taking care of scaling back the voltage/clock?

The BIOS has options to enable/disable CPU Enhanced Halt (C1E) / CPU EIST Function.  I wonder if it also manages these functions.


Edit: after searching around, all I've been able to find on this topic is one paragraph from a "e-pinion" review: 
> 
The Gigabyte P35-DS3L has a feature called M.I.T. (Motherboard Intelligent Tweaker) which allows for automatic dynamic overclocking. It works with SpeedStep as well, so you can still save power when idling without sacraficing speed. When the CPU is fully loaded (100% utilization), SpeedStep will bring the CPU to the max multiplier (for my E2180, its 10x). Then M.I.T. will start turning up the FSB. So with just SpeedStep, I get a stock 10x200 MHz FSB = 2.0GHz. M.I.T. will start turning up the FSB as high as it can go without sacraficing stability. It may go as high as 250 MHz for a result of 10x250 MHz FSB = 2.5GHz at stock voltage! Talk about a lazy man's way to overclock!



Edit 2: I thought of a way of testing that hypothesis, and it seems to be false.    I completely disabled EIST (Speedstep) in the BIOS and the temps are still very good (30 degrees at the moment).

Does this have much of an impact on power usage?

---

### Post by Existentialist on 2008-02-16
On the temp issue, these e8400 & e8500 are clocked much lower than they were capable of from Intel (possibly due to no real competition from AMD?).  I have read many other accounts of people pushing the fsb to 400 with no increase in voltage or temperature on these new Wolfdale processors.  I have mine at 3.6GHz with stock voltage and temps idle at 33-35C, same as it did at 3.0GHz.  Since the voltage isn't being increased you wouldn't expect much more in heat output.

As for the EIST, the function you see in BIOS just enables the processor to be scaled.  The chipset, drivers, and OS take care of actually sending the commands to scale the CPU.  Since I also run Windows XP, I have used some of the many monitoring and system information tools to find out what I could about this for you.  Using Everest Ultimate edition I found that the processor has 2 states 6x and 9x multipliers.  With EIST, these are the only 2 settings the cpu should run at (9.5x and 6x in your case).  I have never seen the voltage change while the cpu was running at the lower multiplier though.  Maybe it would if the vcore voltage is left to auto in BIOS rather than having it manually set?

I did find another article from Intel about speedstep and its required hardware/software.

[http://www.intel.com/cd/channel/reseller/emea/eng/203838.htm](http://www.intel.com/cd/channel/reseller/emea/eng/203838.htm)

---

### Post by simoncullen on 2008-02-17
Thanks, Existentialist!  

I clocked my CPU up to 3.6Ghz with only minor tweaking.  This disables scaling altogether (it boots with the message "CPU frequency scaling not supported. You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling").   Ideally, I'd like to leave the machine OC'ed (who can resist!?) and get Speedstep working.    I've found a few other people whose speedstep appears to be disabled by overclocking.

Do you notice any change in temps when you switch between the "powersave" and "performance" governors?  Also, do you think it makes a considerable difference to the power consumption of the computer?  Since the temps all seem to be largely unaffected, I imagine it's not that significant?

Thanks, again.

Simon 



> **Existentialist said:**
> On the temp issue, these e8400 & e8500 are clocked much lower than they were capable of from Intel (possibly due to no real competition from AMD?).  I have read many other accounts of people pushing the fsb to 400 with no increase in voltage or temperature on these new Wolfdale processors.  I have mine at 3.6GHz with stock voltage and temps idle at 33-35C, same as it did at 3.0GHz.  Since the voltage isn't being increased you wouldn't expect much more in heat output.

As for the EIST, the function you see in BIOS just enables the processor to be scaled.  The chipset, drivers, and OS take care of actually sending the commands to scale the CPU.  Since I also run Windows XP, I have used some of the many monitoring and system information tools to find out what I could about this for you.  Using Everest Ultimate edition I found that the processor has 2 states 6x and 9x multipliers.  With EIST, these are the only 2 settings the cpu should run at (9.5x and 6x in your case).  I have never seen the voltage change while the cpu was running at the lower multiplier though.  Maybe it would if the vcore voltage is left to auto in BIOS rather than having it manually set?

I did find another article from Intel about speedstep and its required hardware/software.

[http://www.intel.com/cd/channel/reseller/emea/eng/203838.htm](http://www.intel.com/cd/channel/reseller/emea/eng/203838.htm)

---

### Post by Existentialist on 2008-02-17
The temperature sensors are another thing people have been having issues with with these cpus.  I noticed that no matter what ambient temperature my room is at, I got idle temps of 35 on core 1 and 33 on core 2.  Everest reads the cpu temp (the temp of the heatspreader I believe) as around 27.  When I start stress tests the core temps often take a while to rise until they eventually start changing to about 45-50, which leads me to believe that for some reason the temp sensors are not correctly reporting the temps below 35 and 33.  But I do notice that load temps are the same at 3.6GHz as they were at 3.0 (at least within 1-2 degrees).

As for power savings, I imagine that when the cores are idle you probably only use around 5-10 watts with these 45nm cpus.  So in that sense they probably are saving power, but I don't empirically know how much.  The site tomshardware.com, has an article coming out this week about the new Wolfdale processors overclocking abilities.  They usually do a pretty good job, and I imagine they will include actual temperature and power consumption readings from tools designed to measure each, rather than relying on software.

If I can recommend, your overclock is good, but these chips will hit a 400fsb on stock voltage or a very slight boost.  If you are going to overclock it you mine as well get 3.8GHz out of running 9.5x400.  This should be able to be done on stock voltage.  It is the advantage you get from buying the e8500 rather then the e8400.  Either way if you are running basic ddr2 make sure you keep the memory fsb ratio 1:1 (ie fsb 400 ram 800MHz) for best performance.

---

### Post by Existentialist on 2008-02-17
One more thing.  I finally found the thread I was looking for about somebody loosing speedstep capabilities after overclocking there core 2 quad.

[http://ubuntuforums.org/showthread.php?t=585946](http://ubuntuforums.org/showthread.php?t=585946)

There is at least one solution in there you could try which may also fix your original issue of getting 3.16GHz before overclocking.

Edit: Just noticed you already posted there, sorry.

---

### Post by simoncullen on 2008-02-18
I got to 3.8Ghz by setting the vcore to 1.275 -- which I wouldn't worry about if I wasn't trying to build a "silent" PC.  The sink/fan I'm using at the moment aren't top of the line either, and I'm forcing the cpu and case fan to run at very low speeds.  Still, the temps were pretty good - as reported in Ubuntu and BIOS.

I have to use vmware a lot to do dictation in to Dragon NaturallySpeaking as I have RSI from typing, and it was incredibly responsive at 3.8Ghz.  Still, I ran mprime and got a stability error after a few minutes -- so I'd need to up the voltage beyond 1.275 to get it to be truly stable, which I'd rather not do given the circumstances.

So I'm back at 3Ghz, stock settings, trying to get Speedstep to work correctly!

I'd already tried setting the MAX_SPEED and MIN_SPEED in  /etc/init.d/cpufrequtils to no avail.  I didn't expect it to work since it says in that file:
> 
Both MIN_SPEED and MAX_SPEED must be values listed in:  cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 

I've just tried booting from an OpenSuSE Live CD and I found the same problem.  So the bug is not limited to Ubuntu.


I'll keep searching.  I'm thinking I might install Windows to see if the bug is reproduced there too.

Simon

---

### Post by Existentialist on 2008-02-18
> **simoncullen said:**
> 
I'll keep searching.  I'm thinking I might install Windows to see if the bug is reproduced there too.


I can save you the time and hassle of that.  It does work in windows, even overclocked.  Unless you somehow have a bad motherboard you will not have problems in windows.

---

### Post by Existentialist on 2008-02-19
Thought I would post a link to the article tomshardware did about overclocking the Wolfdales.  Page 4 talks a little about the speedstep.

[http://www.tomshardware.com/2008/02/19/wolfdale_on_steroids/](http://www.tomshardware.com/2008/02/19/wolfdale_on_steroids/)

---

### Post by simoncullen on 2008-02-20
> **Existentialist said:**
> 
If I can recommend, your overclock is good, but these chips will hit a 400fsb on stock voltage or a very slight boost.  If you are going to overclock it you mine as well get 3.8GHz out of running 9.5x400.  This should be able to be done on stock voltage.  It is the advantage you get from buying the e8500 rather then the e8400.  Either way if you are running basic ddr2 make sure you keep the memory fsb ratio 1:1 (ie fsb 400 ram 800MHz) for best performance.

Hi! I tried your recommendation.  It runs happily at 3.8Ghz with the fsb at 400 Mhz.  

In the interest of my silent computing aspirations,I got a new (and very substantial) heatsink today -- the ThermalTake Extreme 120.  It's running with a super-quiet (8dB) low-speed (800RPM) Scythe fan.  

At 3.8Ghz the machine was idling at 27 degrees with 1.3 volts (ambient was around 24 degrees).  So I decided to play around and I discovered that I can easily get it to 4Ghz if I give it 1.35 volts and set the fsb to 421 (421 x 9.15 = 4000).    

This gives an fsb-to-memory ratio of 1:1, viz., 421:842.*  

I've left the multiplier which generates the memory frequency from the fsb frequency at X2.   So it will always be in a 1:1 ratio no matter what I set the fsb.  Is this right?  I suspect I might be misunderstanding something ...  Or is this optimum?



*That's 1:2 -- but because the ram is DDR2 the real frequency is 421, right?

Thanks! 


Is this acceptable for the fsb to clock ratio -- which I understand should optimally be 1:1? If not, what would be the next overclock you would recommend?   

At the moment it's running two instances of mprime which generates a 100% load, and it's sitting on 50 degrees (ambient is 24).

---

### Post by Existentialist on 2008-02-20
Since the RAM is dual channel, running it at 842 will result in being 1:1 with the fsb at 421.

On to overclocking.  With these first gen. 45nm chips as long as you run a sufficient cooler (like the extreme 120 or zalman 9700) you shouldn't be limited by heat output, but rather by voltage limitations.  For everyday use I wouldn't recommend exceeding the Intel specified 1.365 volts by very much.  Due to vdrop, this may result in a BIOS setting of around 1.4 volts at most.  You never said what kind of RAM you are running, but as you increase beyond 850MHz speeds, you may need to relax the timings, or increase the voltage of your RAM.  Additionally, the voltage to the FSB may need to be bumped up once you start getting near the 450MHz fsb.  Here are my more exact specs:

CPU [Zalman 9700 cooler]
FSB - 420MHz
Multi - 9x
Vcore - 1.3V (about 1.275 with vdrop under load)

RAM [4x1gb]
840MHz
Timings:
tCL (CAS Latency): 4
tRCD: 4
tRP: 3
tRAS: 10
Command Per Clock (CMD): 2T
** Advanced Memory Settings **
tRRD: 3
tRC: auto (23)
tWR: auto
tWTR: auto
tREF: Auto (7.8us) 

RAM Voltage - 2.1V
FSB Voltage - 1.3-1.4V (still on auto)

This is 100% stable, and with these voltages I'm comfortable running the comp 24/7 which is important to me.  I definitely could push it further, but you do start to get diminishing returns once you get beyond 450MHz fsb for normal use.  If you want to post your specific components, like kind and speed of RAM, I'd be happy to recommend settings.  Also, what do you intend on doing with the comp?  Gaming, or just everyday use?

---

### Post by simoncullen on 2008-02-20
Hiya.  Thanks for that.  

The board is a GA-P35-DS3L; memory is 2 x 2Gb "Silicon Power".  

I've applied an extra .2 volts to my ram to get an operating voltage of  1.95.  I'm not sure about the timings ... I'll need to get back to you once I've rebooted to check out the BIOS. 

I'm at 1.3v core voltage in BIOS which lm-sensors is measuring as 1.26v at present.  The current temp (light use) is 32 degrees, the system temp is 36 degrees (there is no system fan on this board), ambient is about 22 degrees.

The cooler is powered by a slow Scythe fan, there are Ante 3-speed fans running very slowly for intake and exhaust. 

I don't play any games, but I do compile a lot of code and use vmware so as I can run Dragon NaturallySpeaking for dictation.  That's something which really benefits from the added speed.  I found it almost painful on a 1.6Ghz C2D laptop (which is well above the specs Nuance provide!).

Unfortunately, by raising the heatsink above the board and by having a sideways shooting fan the motherboard's heatsink gets almost no breeze.  Hence the system temps of 40c.

Cheers!

---

### Post by Existentialist on 2008-02-20
I think the primary bottleneck of your system is going to be, or already is your RAM.  Silicon Power's web site seems to be broken at the DRAM section, so I couldn't find any specific information about your RAM as for timings.  Let me know what kind of settings you got when you check BIOS some time.  The real issue is going to be pushing it much further then you already have.  I have to assume it is DDR2-800 or you wouldn't have gotten it where you have it now (842MHz), and I'm not sure how much farther it will go.  I without knowing the specific limitations of that RAM, I wouldn't push it over 2.0V if it doesn't have any sort of heatspreader.  I would also make sure and run something like memtest86+ to check for the RAM stability.  I'm sure mprime will pass, as the CPU is not being pushed to hard yet, but I don't know how large of FFT mprime uses.  If it is less than 6MB it is all being cached in the L2 cache of the CPU, and hence not testing the RAM's stability very well.  Since this is most likely your bottleneck, make sure the RAM is also stable.  Whenever you get a chance post anymore you find about your RAM like timings and model number or something and I'll help you further.

---

### Post by ori_ab on 2008-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i'm having the same issue with frequency scaling.
cpu is e2200 and mobo is gigabyte ga-p35-ds3l.
iv'e noticed many of these "unable to get frequency scaling" threads mention gigabyte mobo's, maybe its a BIOS thingy?

anyways, I opened a bug - [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119)

---

### Post by 23meg on 2008-04-25
I have a similar issue with an E8500: frequency scaling is unsupported, but the maximum clock speed of 3.16GHz is detected correctly. I have a Gigabyte X38T-DQ6 motherboard.

```
$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 3166.305
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6336.58
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping	: 6
cpu MHz		: 3166.305
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6332.59
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

I also have no temperature readings available under /proc/acpi/thermal_zone (it's empty). This is with 64 bit Hardy.

---

### Post by mrfuzzemz on 2008-04-27
Intel Core 2 Duo E8400 3.0Ghz using Hardy 64-bit.  Also tried 32-bit. Would really like to be able to dynamically clock down to save power.

> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 3002.955
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6009.71
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
stepping	: 6
cpu MHz		: 3002.955
cache size	: 6144 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm
bogomips	: 6005.79
clflush size	: 64


---


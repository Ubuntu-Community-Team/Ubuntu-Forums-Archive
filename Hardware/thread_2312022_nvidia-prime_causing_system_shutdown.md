---
title: "nvidia-prime causing system shutdown"
date: 2016-02-01
forum: Hardware
---

### Post by Abdulhadi_81 on 2016-02-01
I have recently installed Ubuntu Mate 15.10 on a laptop. The laptop contains both an Intel integrated graphics card and an nVidia graphics card. Below are the details of both cards from running the lspci command

```
~$ lspci | grep -iE 'nvidia | vga'
00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 950M] (rev a2)
```

To enable me to use both cards, I successfully installed the nvidia-prime package by following the steps on this page: [http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

Although in my case, I installed the nvidia-352 package instead of the nvidia-319 package.

After rebooting, the nVidia X Server settings application was up and running and I was able to switch between the two graphics cards using the PRIME Profiles section of that application. There is, however, one annoying problem left. When I am currently using the nVidia card and decide to switch to the Intel card, I select "Intel (Power Saving Mode)" in the settings application and then reboot. Once I have logged back into my desktop, the settings application icon in the panel clearly shows the Intel logo so I know the switch was successful. However, if I wait for a couple of minutes after logging back in (and not doing anything in the meantime) then my laptop fan will start running violently and the system will then shut down on its own !! I guess something is overheating inside the laptop that is causing this behaviour.

I don't have any issues working on the laptop when the nVidia card is selected but selecting the Intel card will cause system shut-down after just a couple of minutes of being idle. If I can only use my system in nVidia mode then that defeats the purpose of nvidia-prime ! What do I need to do to enable me to use the system in Intel mode ?

---

### Post by Vladlenin5000 on 2016-02-01
Hi and welcome.

Please also post the exact make/model of your laptop.

---

### Post by Abdulhadi_81 on 2016-02-02
Thank you for taking the time to help me :). The laptop is a customised Cosmos IV 15.6" laptop that I bought from the British retailer "PC Specialist". The official page for that laptop is here:

[https://www.pcspecialist.co.uk/notebooks/cosmosIV-15/](https://www.pcspecialist.co.uk/notebooks/cosmosIV-15/)

The specifications I selected when I ordered the laptop are listed below:

**Chassis & Display**
Cosmos Series: 15.6" Matte Full HD IPS LED Widescreen (1920x1080)
**Processor (CPU)**
Intel® Core™ i7 Quad Core Processor 6700HQ (2.6GHz, 3.5GHz Turbo)
**Memory (RAM)**
8GB Kingston SODIMM DDR3 1600MHz (1 x 8GB)
**Graphics Card**
NVIDIA® GeForce® GTX 950M - 2.0GB DDR3 Video RAM - DirectX® 12
**1st Hard Disk**
500GB Samsung 850 EVO SSD, SATA 6Gb/s (upto 540MB/sR | 520MB/sW)
**1st DVD/BLU-RAY Drive**
8x SATA DVD±R/RW/Dual Layer (+ 24x CD-RW)
**Memory Card Reader**
Internal 9 in 1 Card Reader (MMC/RSMMC/SD: Mini, XC & HC/MS: Pro & Duo)
**Thermal Paste**
ARCTIC MX-4 EXTREME THERMAL CONDUCTIVITY COMPOUND
**Sound Card**
Intel 2 Channel High Definition Audio + MIC/Headphone Jack
**Wireless/Wired Networking**
GIGABIT LAN & WIRELESS INTEL® AC-8260 M.2 (867Mbps, 802.11BGN) + BLUETOOTH
**USB Options**
3 x USB 3.0 PORTS + 1 x USB 2.0 PORT AS STANDARD
**Battery**
Cosmos Series 6 Cell Lithium Ion Battery (48.84WH)
**Power Cable**
1 x UK Power Lead & 120W AC Adaptor
**Keyboard Language**
COSMOS SERIES UK KEYBOARD WITH NUMBER PAD
**Operating System**
NO OPERATING SYSTEM REQUIRED
**DVD Recovery Media**
NO DVD RECOVERY MEDIA REQUIRED
** Office Software**
NO OFFICE SOFTWARE
**Anti-Virus**
NO ANTI-VIRUS SOFTWARE
**Mouse**
INTEGRATED 2 BUTTON TOUCHPAD MOUSE
**Webcam**
INTEGRATED 2.0 MEGAPIXEL WEBCAM

---

### Post by KenSharp on 2016-02-02
Fans going insane and computer shutting down is a driver issue. But you might glean a clue from checking dmesg or the syslog.

---

### Post by Vladlenin5000 on 2016-02-02
> **KenSharp said:**
> Fans going insane and computer shutting down is a driver issue. But you might glean a clue from checking dmesg or the syslog.

+1

I see nothing unusual or outstanding in the hardware, except the Skylake CPU which we already now has some issues with the current Ubuntu releases. As such, for the moment, it requires additional boot arguments in GRUB:
```
i915.preliminary_hw_support=1
nouveau.modeset=0
```

And this is all I know... Search for "skylake" in this forum so you can get a better view of similar machines and how users are dealing with this issues.

---

### Post by Abdulhadi_81 on 2016-02-03
I was already adding "**nouveau.modeset=0**" to the kernel boot parameters and then I tried adding "**i915.preliminary_hw_support=1**" to the list of parameters and rebooted but the laptop still forced a shutdown in Intel mode. Here is the output from the dmesg command:

```
~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-16-generic (buildd@lcy01-07) (gcc version 5.2.1 20151003 (Ubuntu 5.2.1-21ubuntu2) ) #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 (Ubuntu 4.2.0-16.19-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=6dc83146-91ce-490a-913c-7c2cfe7a1c80 ro nouveau.modeset=0 i915.preliminary_hw_support=1
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
[    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009b7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007377efff] usable
[    0.000000] BIOS-e820: [mem 0x000000007377f000-0x0000000073a88fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000073a89000-0x00000000747cffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000747d0000-0x00000000747d0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000747d1000-0x000000007481afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007481b000-0x0000000076db8fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000076db9000-0x0000000077733fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000077734000-0x0000000077818fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077819000-0x0000000077ba2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000077ba3000-0x0000000077ffefff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000077fff000-0x0000000077ffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000078000000-0x00000000780fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000281ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 3.0 present.
[    0.000000] DMI: PC Specialist Limited W65_W67RC/W65_W67RC, BIOS 5.11 10/07/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x282000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   1 base 007C000000 mask 7FFC000000 uncachable
[    0.000000]   2 base 007A000000 mask 7FFE000000 uncachable
[    0.000000]   3 base 0079000000 mask 7FFF000000 uncachable
[    0.000000]   4 base 0078800000 mask 7FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x78000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcce0-0x000fccef] mapped at [ffff8800000fcce0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x281e00000-0x281ffffff]
[    0.000000]  [mem 0x281e00000-0x281ffffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x280000000-0x281dfffff]
[    0.000000]  [mem 0x280000000-0x281dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x260000000-0x27fffffff]
[    0.000000]  [mem 0x260000000-0x27fffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x7377efff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x735fffff] page 2M
[    0.000000]  [mem 0x73600000-0x7377efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x73a89000-0x747cffff]
[    0.000000]  [mem 0x73a89000-0x73bfffff] page 4k
[    0.000000]  [mem 0x73c00000-0x745fffff] page 2M
[    0.000000]  [mem 0x74600000-0x747cffff] page 4k
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x7481b000-0x76db8fff]
[    0.000000]  [mem 0x7481b000-0x749fffff] page 4k
[    0.000000]  [mem 0x74a00000-0x76bfffff] page 2M
[    0.000000]  [mem 0x76c00000-0x76db8fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x77734000-0x77818fff]
[    0.000000]  [mem 0x77734000-0x77818fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x77fff000-0x77ffffff]
[    0.000000]  [mem 0x77fff000-0x77ffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x25fffffff]
[    0.000000]  [mem 0x100000000-0x25fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x340bc000-0x36055fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F05B0 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x0000000077819090 0000A4 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000778334C0 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000778191D0 01A2F0 (v02 ALASKA A M I    01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000077BA2F80 000040
[    0.000000] ACPI: APIC 0x00000000778335D0 0000BC (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x0000000077833690 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000778336D8 00009C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x0000000077833778 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000778337B8 000038 (v01 ALASKA A M I    01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x00000000778337F0 000315 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000077833B08 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000077833B40 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000077833B98 005806 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000778393A0 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: SSDT 0x00000000778393E8 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x000000007783A240 00009F (v02 SgRef  SgPeg    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x000000007783A2E0 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x000000007783A388 001970 (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x000000007783BCF8 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000281ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x281ff4000-0x281ff8fff]
[    0.000000]  [ffffea0000000000-ffffea000a1fffff] PMD -> [ffff880279600000-ffff8802815fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x0000000281ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009afff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000007377efff]
[    0.000000]   node   0: [mem 0x0000000073a89000-0x00000000747cffff]
[    0.000000]   node   0: [mem 0x000000007481b000-0x0000000076db8fff]
[    0.000000]   node   0: [mem 0x0000000077734000-0x0000000077818fff]
[    0.000000]   node   0: [mem 0x0000000077fff000-0x0000000077ffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000281ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000281ffffff]
[    0.000000] On node 0 totalpages: 2067172
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7534 pages used for memmap
[    0.000000]   DMA32 zone: 482122 pages, LIFO batch:31
[    0.000000]   Normal zone: 24704 pages used for memmap
[    0.000000]   Normal zone: 1581056 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x79000000-0x7cffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7377f000-0x73a88fff]
[    0.000000] PM: Registered nosave memory: [mem 0x747d0000-0x747d0fff]
[    0.000000] PM: Registered nosave memory: [mem 0x747d1000-0x7481afff]
[    0.000000] PM: Registered nosave memory: [mem 0x76db9000-0x77733fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77819000-0x77ba2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x77ba3000-0x77ffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x78000000-0x780fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x78100000-0x78ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x79000000-0x7cffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7d000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x7d000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff880281c00000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2034849
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic root=UUID=6dc83146-91ce-490a-913c-7c2cfe7a1c80 ro nouveau.modeset=0 i915.preliminary_hw_support=1
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8021420K/8268688K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 247268K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:2048 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Unable to calibrate against PIT
[    0.000000] tsc: using HPET reference calibration
[    0.000000] tsc: Detected 2592.022 MHz processor
[    0.000024] Calibrating delay loop (skipped), value calculated using timer frequency.. 5184.04 BogoMIPS (lpj=10368088)
[    0.000192] pid_max: default: 32768 minimum: 301
[    0.000278] ACPI: Core revision 20150619
[    0.023648] ACPI: All ACPI Tables successfully acquired
[    0.023856] Security Framework initialized
[    0.023946] AppArmor: AppArmor initialized
[    0.024027] Yama: becoming mindful.
[    0.024479] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.027417] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.028187] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.028281] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.028555] Initializing cgroup subsys blkio
[    0.028638] Initializing cgroup subsys memory
[    0.028723] Initializing cgroup subsys devices
[    0.028806] Initializing cgroup subsys freezer
[    0.028888] Initializing cgroup subsys net_cls
[    0.028971] Initializing cgroup subsys perf_event
[    0.029054] Initializing cgroup subsys net_prio
[    0.029137] Initializing cgroup subsys hugetlb
[    0.029237] CPU: Physical Processor ID: 0
[    0.029318] CPU: Processor Core ID: 0
[    0.029400] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.029485] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.030470] mce: CPU supports 10 MCE banks
[    0.030564] CPU0: Thermal monitoring enabled (TM1)
[    0.030653] process: using mwait in idle threads
[    0.030737] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.030821] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.031175] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.033737] ftrace: allocating 30905 entries in 121 pages
[    0.043691] DMAR: Host address width 39
[    0.043773] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.043861] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.043968] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.044055] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.044161] DMAR: RMRR base: 0x000000774ae000 end: 0x000000774cdfff
[    0.044247] DMAR: RMRR base: 0x00000078800000 end: 0x0000007cffffff
[    0.044334] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.044420] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.044504] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.044576] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.046161] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.046243] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.050387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.090156] TSC deadline timer enabled
[    0.090161] smpboot: CPU0: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (fam: 06, model: 5e, stepping: 03)
[    0.090452] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.090858] ... version:                4
[    0.090938] ... bit width:              48
[    0.091019] ... generic registers:      4
[    0.091100] ... value mask:             0000ffffffffffff
[    0.091184] ... max period:             0000ffffffffffff
[    0.091267] ... fixed-purpose events:   3
[    0.091348] ... event mask:             000000070000000f
[    0.092025] x86: Booting SMP configuration:
[    0.092107] .... node  #0, CPUs:      #1
[    0.096506] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.096744]  #2 #3 #4 #5 #6 #7
[    0.122598] x86: Booted up 1 node, 8 CPUs
[    0.122765] smpboot: Total of 8 processors activated (41472.35 BogoMIPS)
[    0.129314] devtmpfs: initialized
[    0.131007] evm: security.selinux
[    0.131086] evm: security.SMACK64
[    0.131166] evm: security.SMACK64EXEC
[    0.131245] evm: security.SMACK64TRANSMUTE
[    0.131326] evm: security.SMACK64MMAP
[    0.131406] evm: security.ima
[    0.131484] evm: security.capability
[    0.131599] PM: Registering ACPI NVS region [mem 0x7377f000-0x73a88fff] (3186688 bytes)
[    0.131731] PM: Registering ACPI NVS region [mem 0x747d0000-0x747d0fff] (4096 bytes)
[    0.131837] PM: Registering ACPI NVS region [mem 0x77819000-0x77ba2fff] (3710976 bytes)
[    0.132028] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.132202] pinctrl core: initialized pinctrl subsystem
[    0.132423] RTC time: 20:58:59, date: 02/03/16
[    0.133275] NET: Registered protocol family 16
[    0.145146] cpuidle: using governor ladder
[    0.149147] cpuidle: using governor menu
[    0.149281] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.149388] ACPI: bus type PCI registered
[    0.149470] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.149609] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149721] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149817] PCI: Using configuration type 1 for base access
[    0.153409] ACPI: Added _OSI(Module Device)
[    0.153493] ACPI: Added _OSI(Processor Device)
[    0.153577] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.153662] ACPI: Added _OSI(Processor Aggregator Device)
[    0.159329] ACPI: Executed 23 blocks of module-level executable AML code
[    0.163445] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.166267] ACPI: Dynamic OEM Table Load:
[    0.166475] ACPI: SSDT 0xFFFF880277A94400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.167304] ACPI: Dynamic OEM Table Load:
[    0.167497] ACPI: SSDT 0xFFFF880277A9A800 0005DC (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.169144] ACPI: Dynamic OEM Table Load:
[    0.169338] ACPI: SSDT 0xFFFF880277A9B000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.170319] ACPI: Dynamic OEM Table Load:
[    0.170512] ACPI: SSDT 0xFFFF880277A8F600 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.174506] ACPI : EC: EC started
[    0.175350] ACPI: Interpreter enabled
[    0.175449] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.175673] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.175907] ACPI: (supports S0 S3 S4 S5)
[    0.175987] ACPI: Using IOAPIC for interrupt routing
[    0.176096] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.177712] ACPI: Power Resource [PG00] (on)
[    0.177810] ACPI: Power Resource [PG02] (on)
[    0.178199] ACPI: Power Resource [PG01] (on)
[    0.178527] ACPI: Power Resource [PG02] (on)
[    0.188125] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.188215] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.188343] \_SB_.PCI0:_OSC invalid UUID
[    0.188344] _OSC request data:1 1f 0 
[    0.188346] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.188846] PCI host bridge to bus 0000:00
[    0.188928] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.189014] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.189101] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.189191] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.189296] pci_bus 0000:00: root bus resource [mem 0x7d000000-0xdfffffff window]
[    0.189402] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.189512] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.189586] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.189612] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.189687] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.189818] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.189828] pci 0000:00:02.0: reg 0x10: [mem 0xdd000000-0xddffffff 64bit]
[    0.189832] pci 0000:00:02.0: reg 0x18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.189836] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.189964] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.189987] pci 0000:00:14.0: reg 0x10: [mem 0xdf310000-0xdf31ffff 64bit]
[    0.190030] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.190090] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.190202] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.190223] pci 0000:00:14.2: reg 0x10: [mem 0xdf32e000-0xdf32efff 64bit]
[    0.190329] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.190349] pci 0000:00:16.0: reg 0x10: [mem 0xdf32d000-0xdf32dfff 64bit]
[    0.190383] pci 0000:00:16.0: PME# supported from D3hot
[    0.190480] pci 0000:00:17.0: [8086:a103] type 00 class 0x010601
[    0.190498] pci 0000:00:17.0: reg 0x10: [mem 0xdf328000-0xdf329fff]
[    0.190504] pci 0000:00:17.0: reg 0x14: [mem 0xdf32c000-0xdf32c0ff]
[    0.190510] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.190516] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.190522] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.190528] pci 0000:00:17.0: reg 0x24: [mem 0xdf32b000-0xdf32b7ff]
[    0.190549] pci 0000:00:17.0: PME# supported from D3hot
[    0.190636] pci 0000:00:1c.0: [8086:a114] type 01 class 0x060400
[    0.190679] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.190747] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.190872] pci 0000:00:1c.6: [8086:a116] type 01 class 0x060400
[    0.190917] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.190984] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.191100] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.191263] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.191275] pci 0000:00:1f.2: reg 0x10: [mem 0xdf324000-0xdf327fff]
[    0.191391] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.191422] pci 0000:00:1f.3: reg 0x10: [mem 0xdf320000-0xdf323fff 64bit]
[    0.191450] pci 0000:00:1f.3: reg 0x20: [mem 0xdf300000-0xdf30ffff 64bit]
[    0.191477] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.191574] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.191690] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.191744] pci 0000:00:1f.4: reg 0x10: [mem 0xdf32a000-0xdf32a0ff 64bit]
[    0.191813] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.191976] pci 0000:01:00.0: [10de:139a] type 00 class 0x030200
[    0.191989] pci 0000:01:00.0: reg 0x10: [mem 0xde000000-0xdeffffff]
[    0.191995] pci 0000:01:00.0: reg 0x14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.192002] pci 0000:01:00.0: reg 0x1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.192006] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.192011] pci 0000:01:00.0: reg 0x30: [mem 0xdf000000-0xdf07ffff pref]
[    0.192062] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.197200] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.197287] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.197289] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.197292] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.197363] pci 0000:02:00.0: [10ec:5287] type 00 class 0xff0000
[    0.197397] pci 0000:02:00.0: reg 0x10: [mem 0xdf215000-0xdf215fff]
[    0.197452] pci 0000:02:00.0: reg 0x30: [mem 0xdf200000-0xdf20ffff pref]
[    0.197499] pci 0000:02:00.0: supports D1 D2
[    0.197500] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.197532] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.197655] pci 0000:02:00.1: [10ec:8168] type 00 class 0x020000
[    0.197689] pci 0000:02:00.1: reg 0x10: [io  0xd000-0xd0ff]
[    0.197713] pci 0000:02:00.1: reg 0x18: [mem 0xdf214000-0xdf214fff 64bit]
[    0.197729] pci 0000:02:00.1: reg 0x20: [mem 0xdf210000-0xdf213fff 64bit]
[    0.197779] pci 0000:02:00.1: supports D1 D2
[    0.197780] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205207] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.205292] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.205295] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf2fffff]
[    0.205377] pci 0000:03:00.0: [8086:24f3] type 00 class 0x028000
[    0.205433] pci 0000:03:00.0: reg 0x10: [mem 0xdf100000-0xdf101fff 64bit]
[    0.205574] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.205611] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.213220] pci 0000:00:1c.6: PCI bridge to [bus 03]
[    0.213308] pci 0000:00:1c.6:   bridge window [mem 0xdf100000-0xdf1fffff]
[    0.214192] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.214931] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.215667] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.216402] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.217137] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.217876] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.218610] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.219346] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.220282] ACPI: Enabled 5 GPEs in block 00 to 7F
[    0.220546] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.220715] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.220803] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.220915] vgaarb: loaded
[    0.220995] vgaarb: bridge control possible 0000:00:02.0
[    0.221281] SCSI subsystem initialized
[    0.221391] libata version 3.00 loaded.
[    0.221406] ACPI: bus type USB registered
[    0.221510] usbcore: registered new interface driver usbfs
[    0.221600] usbcore: registered new interface driver hub
[    0.221698] usbcore: registered new device driver usb
[    0.221877] PCI: Using ACPI for IRQ routing
[    0.249868] PCI: pci_cache_line_size set to 64 bytes
[    0.249934] e820: reserve RAM buffer [mem 0x0009b800-0x0009ffff]
[    0.249935] e820: reserve RAM buffer [mem 0x7377f000-0x73ffffff]
[    0.249936] e820: reserve RAM buffer [mem 0x747d0000-0x77ffffff]
[    0.249937] e820: reserve RAM buffer [mem 0x76db9000-0x77ffffff]
[    0.249938] e820: reserve RAM buffer [mem 0x77819000-0x77ffffff]
[    0.249939] e820: reserve RAM buffer [mem 0x282000000-0x283ffffff]
[    0.250010] NetLabel: Initializing
[    0.250089] NetLabel:  domain hash size = 128
[    0.250171] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.250260] NetLabel:  unlabeled traffic allowed by default
[    0.250424] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.251008] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.253137] clocksource: Switched to clocksource hpet
[    0.257474] AppArmor: AppArmor Filesystem Enabled
[    0.257589] pnp: PnP ACPI init
[    0.257802] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.257888] system 00:00: [io  0xffff] has been reserved
[    0.257973] system 00:00: [io  0xffff] has been reserved
[    0.258057] system 00:00: [io  0xffff] has been reserved
[    0.259393] system 00:00: [io  0x1800-0x18fe] could not be reserved
[    0.259479] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.259565] system 00:00: [io  0x3322-0x3323] has been reserved
[    0.259652] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.259710] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.259796] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.259810] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.259834] system 00:03: [io  0x1854-0x1857] has been reserved
[    0.259920] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.259936] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.260010] pnp 00:05: Plug and Play ACPI device, IDs SYN1218 PNP0f13 (active)
[    0.260142] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.260230] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.260316] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.260404] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.260491] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.260578] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.260666] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.260753] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.260840] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.260928] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.261016] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.261043] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.261130] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.261236] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.261323] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.261411] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.261498] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.261585] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.261673] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.261858] system 00:08: [io  0xff00-0xfffe] has been reserved
[    0.261944] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.262621] system 00:09: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.262709] system 00:09: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.262796] system 00:09: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.262883] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.263256] pnp: PnP ACPI: found 10 devices
[    0.272027] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.272153] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.272237] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.272324] pci 0000:00:01.0:   bridge window [mem 0xde000000-0xdf0fffff]
[    0.272412] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.272520] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.272604] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.272691] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdf2fffff]
[    0.272782] pci 0000:00:1c.6: PCI bridge to [bus 03]
[    0.272867] pci 0000:00:1c.6:   bridge window [mem 0xdf100000-0xdf1fffff]
[    0.272959] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.272960] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.272961] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.272962] pci_bus 0000:00: resource 7 [mem 0x7d000000-0xdfffffff window]
[    0.272963] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff window]
[    0.272964] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.272965] pci_bus 0000:01: resource 1 [mem 0xde000000-0xdf0fffff]
[    0.272966] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.272967] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.272968] pci_bus 0000:02: resource 1 [mem 0xdf200000-0xdf2fffff]
[    0.272969] pci_bus 0000:03: resource 1 [mem 0xdf100000-0xdf1fffff]
[    0.272991] NET: Registered protocol family 2
[    0.273226] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.273538] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.273793] TCP: Hash tables configured (established 65536 bind 65536)
[    0.273901] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.274015] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.274152] NET: Registered protocol family 1
[    0.274243] pci 0000:00:02.0: Video device with shadowed ROM
[    0.274671] PCI: CLS 0 bytes, default 64
[    0.274702] Trying to unpack rootfs image as initramfs...
[    0.650818] Freeing initrd memory: 32360K (ffff8800340bc000 - ffff880036056000)
[    0.650951] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.651039] software IO TLB [mem 0x6f77f000-0x7377f000] (64MB) mapped at [ffff88006f77f000-ffff88007377efff]
[    0.651332] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x49
[    0.651436] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x49
[    0.651545] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x49
[    0.651642] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x49
[    0.651739] microcode: CPU4 sig=0x506e3, pf=0x20, revision=0x49
[    0.651848] microcode: CPU5 sig=0x506e3, pf=0x20, revision=0x49
[    0.651955] microcode: CPU6 sig=0x506e3, pf=0x20, revision=0x49
[    0.652051] microcode: CPU7 sig=0x506e3, pf=0x20, revision=0x49
[    0.652195] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.652411] Scanning for low memory corruption every 60 seconds
[    0.652940] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.653053] Initialise system trusted keyring
[    0.653215] audit: initializing netlink subsys (disabled)
[    0.653314] audit: type=2000 audit(1454533139.656:1): initialized
[    0.653689] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.653791] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.654819] zpool: loaded
[    0.654898] zbud: loaded
[    0.655193] VFS: Disk quotas dquot_6.6.0
[    0.655294] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.655856] fuse init (API version 7.23)
[    0.656075] Key type big_key registered
[    0.657837] Key type asymmetric registered
[    0.657934] Asymmetric key parser 'x509' registered
[    0.658029] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.658346] io scheduler noop registered
[    0.658445] io scheduler deadline registered (default)
[    0.658552] io scheduler cfq registered
[    0.658978] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.659067] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.659179] intel_idle: MWAIT substates: 0x11142120
[    0.659180] intel_idle: v0.4 model 0x5E
[    0.659180] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.660512] ACPI: AC Adapter [AC] (on-line)
[    0.660641] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.660751] ACPI: Power Button [PWRB]
[    0.660853] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.660962] ACPI: Sleep Button [SLPB]
[    0.661064] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.661243] ACPI: Lid Switch [LID0]
[    0.661345] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.661452] ACPI: Power Button [PWRF]
[    0.661986] thermal LNXTHERM:00: registered as thermal_zone0
[    0.662071] ACPI: Thermal Zone [TZ0] (44 C)
[    0.662181] GHES: HEST is not enabled!
[    0.662427] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.662629] ACPI: Battery Slot [BAT0] (battery present)
[    0.665933] Linux agpgart interface v0.103
[    0.668564] brd: module loaded
[    0.670186] loop: module loaded
[    0.670547] libphy: Fixed MDIO Bus: probed
[    0.670641] tun: Universal TUN/TAP device driver, 1.6
[    0.670724] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.670945] PPP generic driver version 2.4.2
[    0.671280] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.671366] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.671553] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.671665] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.671720] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.671808] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.671912] usb usb1: Product: xHCI Host Controller
[    0.671995] usb usb1: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.672081] usb usb1: SerialNumber: 0000:00:14.0
[    0.672300] hub 1-0:1.0: USB hub found
[    0.672393] hub 1-0:1.0: 16 ports detected
[    0.679850] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.679936] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.680060] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.680147] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680252] usb usb2: Product: xHCI Host Controller
[    0.680336] usb usb2: Manufacturer: Linux 4.2.0-16-generic xhci-hcd
[    0.680422] usb usb2: SerialNumber: 0000:00:14.0
[    0.680652] hub 2-0:1.0: USB hub found
[    0.680741] hub 2-0:1.0: 8 ports detected
[    0.683130] usb: failed to peer usb2-port5 and usb1-port7 by location (usb2-port5:none) (usb1-port7:usb2-port4)
[    0.683242] usb usb2-port5: failed to peer to usb1-port7 (-16)
[    0.683326] usb: port power management may be unreliable
[    0.683827] usb: failed to peer usb2-port6 and usb1-port1 by location (usb2-port6:none) (usb1-port1:usb2-port1)
[    0.683938] usb usb2-port6: failed to peer to usb1-port1 (-16)
[    0.684440] usb: failed to peer usb2-port7 and usb1-port7 by location (usb2-port7:none) (usb1-port7:usb2-port4)
[    0.684551] usb usb2-port7: failed to peer to usb1-port7 (-16)
[    0.685052] usb: failed to peer usb2-port8 and usb1-port1 by location (usb2-port8:none) (usb1-port1:usb2-port1)
[    0.685251] usb usb2-port8: failed to peer to usb1-port1 (-16)
[    0.685412] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.685501] ehci-pci: EHCI PCI platform driver
[    0.685587] ehci-platform: EHCI generic platform driver
[    0.685675] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.685762] ohci-pci: OHCI PCI platform driver
[    0.685847] ohci-platform: OHCI generic platform driver
[    0.685934] uhci_hcd: USB Universal Host Controller Interface driver
[    0.686048] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:SYNM] at 0x60,0x64 irq 1,12
[    1.233084] i8042: Detected active multiplexing controller, rev 1.1
[    1.234825] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.234909] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.235009] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.235105] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.235201] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.235518] mousedev: PS/2 mouse device common for all mice
[    1.236146] rtc_cmos 00:02: RTC can wake from S4
[    1.236666] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.236830] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.236964] i2c /dev entries driver
[    1.237380] device-mapper: uevent: version 1.0.3
[    1.237649] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    1.237780] Intel P-state driver initializing.
[    1.238440] ledtrig-cpu: registered to indicate activity on CPUs
[    1.239437] PCCT header not found.
[    1.239779] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.239951] NET: Registered protocol family 10
[    1.240386] NET: Registered protocol family 17
[    1.240531] Key type dns_resolver registered
[    1.241781] Loading compiled-in X.509 certificates
[    1.244921] Loaded X.509 cert 'Build time autogenerated kernel key: 6a1c9c21f04ab86fd1d7ced6ca113540fc8e35b6'
[    1.245180] registered taskstats version 1
[    1.245284] zswap: loading zswap
[    1.245363] zswap: using zbud pool
[    1.245445] zswap: using lzo compressor
[    1.247761] Key type trusted registered
[    1.252568] Key type encrypted registered
[    1.252653] AppArmor: AppArmor sha1 policy hashing enabled
[    1.252740] ima: No TPM chip found, activating TPM-bypass!
[    1.252837] evm: HMAC attrs: 0x1
[    1.253968]   Magic number: 4:763:1002
[    1.254076] i8042 kbd 00:04: hash matches
[    1.254185] memory memory41: hash matches
[    1.254579] rtc_cmos 00:02: setting system clock to 2016-02-03 20:59:00 UTC (1454533140)
[    1.254977] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.255187] EDD information not available.
[    1.255315] PM: Hibernation image not present or could not be loaded.
[    1.255947] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    1.256055] Write protecting the kernel read-only data: 12288k
[    1.256701] Freeing unused kernel memory: 36K (ffff8800017f7000 - ffff880001800000)
[    1.257277] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    1.266826] random: systemd-udevd urandom read with 11 bits of entropy available
[    1.289261] hidraw: raw HID events driver (C) Jiri Kosina
[    1.314828] rtsx_pci 0000:02:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 124
[    1.315702] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.316070] r8169 0000:02:00.1: can't disable ASPM; OS doesn't have ASPM control
[    1.316741] ahci 0000:00:17.0: version 3.0
[    1.317165] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0xc impl SATA mode
[    1.317411] ahci 0000:00:17.0: flags: 64bit ncq sntf pm led clo only pio slum part ems deso sadm sds apst 
[    1.318306] [drm] Initialized drm 1.1.0 20060810
[    1.322487] r8169 0000:02:00.1 eth0: RTL8411 at 0xffffc90000c8e000, 80:fa:5b:22:7b:06, XID 1c800800 IRQ 126
[    1.322808] r8169 0000:02:00.1 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.326108] scsi host0: ahci
[    1.326824] scsi host1: ahci
[    1.327581] scsi host2: ahci
[    1.328298] scsi host3: ahci
[    1.328644] ata1: DUMMY
[    1.328936] ata2: DUMMY
[    1.329551] ata3: SATA max UDMA/133 abar m2048@0xdf32b000 port 0xdf32b200 irq 125
[    1.329993] ata4: SATA max UDMA/133 abar m2048@0xdf32b000 port 0xdf32b280 irq 125
[    1.340108] [drm] Memory usable by graphics device = 4096M
[    1.341106] [drm] Replacing VGA console driver
[    1.344126] Console: switching to colour dummy device 80x25
[    1.351791] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.351795] [drm] Driver supports precise vblank timestamp query.
[    1.357834] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.363514] r8169 0000:02:00.1 enp2s0f1: renamed from eth0
[    1.372455] fbcon: inteldrmfb (fb0) is primary device
[    1.372592] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.373286] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
[    1.373568] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150619/video-1157)
[    1.373569] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    1.373595] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input11
[    1.373808] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.441085] usb 1-2: new high-speed USB device number 2 using xhci_hcd
[    1.606987] usb 1-2: New USB device found, idVendor=04f2, idProduct=b550
[    1.606988] usb 1-2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.606988] usb 1-2: Product: Chicony USB 2.0 Camera
[    1.606989] usb 1-2: Manufacturer: Generic
[    1.606989] usb 1-2: SerialNumber: 200901010001
[    1.649149] tsc: Refined TSC clocksource calibration: 2591.999 MHz
[    1.649151] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x255cb5c6a11, max_idle_ns: 440795249002 ns
[    1.649153] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.649193] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.650813] ata3.00: supports DRM functions and may not be fully accessible
[    1.650964] ata3.00: READ LOG DMA EXT failed, trying unqueued
[    1.651018] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.651019] ata3.00: ATA-9: Samsung SSD 850 EVO 500GB, EMT01B6Q, max UDMA/133
[    1.651019] ata3.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.651426] ata3.00: supports DRM functions and may not be fully accessible
[    1.651527] ata3.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.651632] ata3.00: configured for UDMA/133
[    1.651887] ata4.00: ATAPI: HL-DT-ST DVDRAM GTB0N, 1.00, max UDMA/133
[    1.654011] ata4.00: configured for UDMA/133
[    1.661318] scsi 2:0:0:0: Direct-Access     ATA      Samsung SSD 850  1B6Q PQ: 0 ANSI: 5
[    1.661816] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.661954] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.662619] sd 2:0:0:0: [sda] Write Protect is off
[    1.662620] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.662768] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.664220]  sda: sda1 sda2 < sda5 >
[    1.665094] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GTB0N     1.00 PQ: 0 ANSI: 5
[    1.665669] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.720687] sr 3:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.720688] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.720887] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.721170] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.781070] usb 1-3: new full-speed USB device number 3 using xhci_hcd
[    1.939664] usb 1-3: New USB device found, idVendor=8087, idProduct=0a2b
[    1.939665] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.561332] psmouse serio2: synaptics: queried max coordinates: x [..5674], y [..4758]
[    2.649476] clocksource: Switched to clocksource tsc
[    2.680018] psmouse serio2: synaptics: queried min coordinates: x [1268..], y [1096..]
[    2.813158] [drm] RC6 on
[    2.828044] psmouse serio2: synaptics: Touchpad model: 1, fw: 8.2, id: 0x1e2b1, caps: 0xf00123/0x840300/0x26800/0x0, board id: 3189, fw id: 1944273
[    2.870992] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input12
[    3.435800] Console: switching to colour frame buffer device 240x67
[    3.443358] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.444104] i915 0000:00:02.0: registered panic notifier
[    3.565182] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.620402] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    3.626699] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    3.627954] systemd[1]: Detected architecture x86-64.
[    3.632628] systemd[1]: Set hostname to <fresh-mate>.
[    3.679024] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    3.680760] systemd[1]: Created slice Root Slice.
[    3.682414] systemd[1]: Listening on Journal Socket (/dev/log).
[    3.684013] systemd[1]: Reached target Remote File Systems (Pre).
[    3.685807] systemd[1]: Listening on udev Kernel Socket.
[    3.687416] systemd[1]: Reached target Encrypted Volumes.
[    3.689067] systemd[1]: Reached target User and Group Name Lookups.
[    3.690740] systemd[1]: Listening on Journal Audit Socket.
[    3.692344] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.694170] systemd[1]: Created slice System Slice.
[    3.695846] systemd[1]: Created slice system-getty.slice.
[    3.697845] systemd[1]: Starting Increase datagram queue length...
[    3.699743] systemd[1]: Listening on fsck to fsckd communication Socket.
[    3.701587] systemd[1]: Created slice User and Session Slice.
[    3.703444] systemd[1]: Reached target Slices.
[    3.705449] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    3.707135] systemd[1]: Listening on Journal Socket.
[    3.709816] systemd[1]: Starting Load Kernel Modules...
[    3.712029] systemd[1]: Mounting Huge Pages File System...
[    3.715188] systemd[1]: Mounting POSIX Message Queue File System...
[    3.718202] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    3.721071] systemd[1]: Started Braille Device Support.
[    3.722279] lp: driver loaded but no devices found
[    3.724907] systemd[1]: Mounting Debug File System...
[    3.725174] ppdev: user-space parallel port driver
[    3.728873] systemd[1]: Starting Uncomplicated firewall...
[    3.731451] systemd[1]: Starting Setup Virtual Console...
[    3.733890] systemd[1]: Started Read required files in advance.
[    3.735823] systemd[1]: Listening on udev Control Socket.
[    3.738048] systemd[1]: Starting udev Coldplug all Devices...
[    3.740582] systemd[1]: Mounted POSIX Message Queue File System.
[    3.742782] systemd[1]: Mounted Huge Pages File System.
[    3.745872] systemd[1]: Mounted Debug File System.
[    3.749083] systemd[1]: Started Increase datagram queue length.
[    3.751143] systemd[1]: Started Load Kernel Modules.
[    3.753059] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    3.755411] systemd[1]: Started Uncomplicated firewall.
[    3.757267] systemd[1]: Started Setup Virtual Console.
[    3.768132] systemd[1]: Starting Create Static Device Nodes in /dev...
[    3.770518] systemd[1]: Starting Apply Kernel Variables...
[    3.772900] systemd[1]: Mounting FUSE Control File System...
[    3.774950] systemd[1]: Listening on Syslog Socket.
[    3.776182] systemd[1]: Starting Journal Service...
[    3.777611] systemd[1]: Mounted FUSE Control File System.
[    3.778671] systemd[1]: Started Create Static Device Nodes in /dev.
[    3.779687] systemd[1]: Started Apply Kernel Variables.
[    3.783613] systemd[1]: Starting udev Kernel Device Manager...
[    3.785067] systemd[1]: Started udev Coldplug all Devices.
[    3.798443] systemd[1]: Started Journal Service.
[    3.806363] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.837672] systemd-journald[290]: Received request to flush runtime journal from PID 1
[    3.841172] wmi: Mapper loaded
[    3.867262] audit: type=1400 audit(1454533143.107:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=433 comm="apparmor_parser"
[    3.867269] audit: type=1400 audit(1454533143.107:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=433 comm="apparmor_parser"
[    3.870537] audit: type=1400 audit(1454533143.111:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=433 comm="apparmor_parser"
[    3.870544] audit: type=1400 audit(1454533143.111:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=433 comm="apparmor_parser"
[    3.870549] audit: type=1400 audit(1454533143.111:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=433 comm="apparmor_parser"
[    3.870554] audit: type=1400 audit(1454533143.111:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=433 comm="apparmor_parser"
[    3.872073] audit: type=1400 audit(1454533143.111:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=433 comm="apparmor_parser"
[    3.875523] audit: type=1400 audit(1454533143.115:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=433 comm="apparmor_parser"
[    3.875529] audit: type=1400 audit(1454533143.115:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=433 comm="apparmor_parser"
[    3.880289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.886281] random: nonblocking pool is initialized
[    3.892537] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[    3.915599] Intel(R) Wireless WiFi driver for Linux
[    3.915601] Copyright(c) 2003- 2015 Intel Corporation
[    3.918830] AVX2 version of gcm_enc/dec engaged.
[    3.918832] AES CTR mode by8 optimization enabled
[    3.931040] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-15.ucode failed with error -2
[    3.932232] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-8000C-14.ucode failed with error -2
[    3.942450] intel_rapl: Found RAPL domain package
[    3.942453] intel_rapl: Found RAPL domain core
[    3.942454] intel_rapl: Found RAPL domain uncore
[    3.942455] intel_rapl: Found RAPL domain dram
[    3.946561] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.948640] iwlwifi 0000:03:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    3.956005] nvidia: module license 'NVIDIA' taints kernel.
[    3.956008] Disabling lock debugging due to kernel taint
[    3.961378] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    3.963922] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    3.963990] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    3.964254] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    3.964808] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
[    3.966859] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[    3.966863] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
[    3.971487] Adding 8267772k swap on /dev/sda5.  Priority:-1 extents:1 across:8267772k SSFS
[    3.974425] cfg80211: World regulatory domain updated:
[    3.974427] cfg80211:  DFS Master region: unset
[    3.974429] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    3.974431] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    3.974433] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    3.974434] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    3.974436] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    3.974438] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    3.974440] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    3.974441] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    3.974443] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    3.978752] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC269VC: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.978754] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.978755] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    3.978756] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.978757] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.978758] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[    3.978759] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    3.993328] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[    3.993378] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[    3.993421] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[    3.993463] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[    3.993503] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19
[    4.098693] snd_hda_intel 0000:00:1f.3: control 2:0:0:PCM Playback Volume:0 is already present
[    4.109100] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.109770] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.222495] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
[    4.226515] Non-volatile memory driver v1.3
[    4.246635] r8169 0000:02:00.1 enp2s0f1: link down
[    4.246700] IPv6: ADDRCONF(NETDEV_UP): enp2s0f1: link is not ready
[    4.249475] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.249588] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.249842] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.250490] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
[    4.380561] ahci 0000:00:17.0: port does not support device sleep
[    4.391529] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.391789] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.392228] iwlwifi 0000:03:00.0: can't access the RSA semaphore it is write protected
[    4.466446] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.509131] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    4.568764] bbswitch: version 0.7
[    4.568770] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    4.568773] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    4.568780] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    4.568840] bbswitch: detected an Optimus _DSM function
[    4.568846] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    4.571230] [drm] Module unloaded
[    4.585407] bbswitch: disabling discrete graphics
[    4.585416] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    4.951300] [drm:intel_pipe_update_end [i915]] *ERROR* Atomic update failure on pipe A (start=1049 end=1055)
[    5.834731] media: Linux media interface: v0.10
[    5.837924] Linux video capture interface: v2.00
[    5.854449] Bluetooth: Core ver 2.20
[    5.854459] NET: Registered protocol family 31
[    5.854460] Bluetooth: HCI device and connection manager initialized
[    5.854462] Bluetooth: HCI socket layer initialized
[    5.854464] Bluetooth: L2CAP socket layer initialized
[    5.854467] Bluetooth: SCO socket layer initialized
[    5.925293] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b550)
[    5.927977] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/input/input20
[    5.928070] usbcore: registered new interface driver uvcvideo
[    5.928072] USB Video Class driver (1.1.1)
[    5.940914] usbcore: registered new interface driver btusb
[    5.942210] Bluetooth: hci0: Firmware revision 0.0 build 90 week 25 2015
[    6.003865] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.003869] Bluetooth: BNEP filters: protocol multicast
[    6.003873] Bluetooth: BNEP socket layer initialized
[    7.589135] wlp3s0: authenticate with 50:6a:03:31:aa:b8
[    7.598241] wlp3s0: send auth to 50:6a:03:31:aa:b8 (try 1/3)
[    7.607355] wlp3s0: authenticated
[    7.608019] wlp3s0: associate with 50:6a:03:31:aa:b8 (try 1/3)
[    7.611931] wlp3s0: RX AssocResp from 50:6a:03:31:aa:b8 (capab=0x411 status=0 aid=1)
[    7.613690] wlp3s0: associated
[    7.613721] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[    7.703576] wlp3s0: Limiting TX power to 19 (22 - 3) dBm as advertised by 50:6a:03:31:aa:b8
[   16.543358] Bluetooth: RFCOMM TTY layer initialized
[   16.543370] Bluetooth: RFCOMM socket layer initialized
[   16.543377] Bluetooth: RFCOMM ver 1.11
[   44.686670] psmouse serio2: TouchPad at isa0060/serio2/input0 lost synchronization, throwing 5 bytes away.
```

I'm really surprised that Intel drivers (of all drivers) is causing me trouble !! Any more ideas about how to resolve this ?

---

### Post by Abdulhadi_81 on 2016-02-04
I managed to find a solution to my problem. I basically upgraded my nVidia drivers to the latest ones using a Personal Package Archive (PPA). Here are the commands that I executed to enable me to achieve this:

```
sudo apt-get purge nvida-*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361 nvidia-prime nvidia-settings
```

I then rebooted the system. Since then, I managed to log into the desktop and change the PRIME Profile from nVidia to Intel and vice versa many times without experiencing any forced shut downs in Intel mode.

I would like to take this opportunity to wholeheartedly thank myself for finding the answer =d>:grin::cool:

I would also like to thank jchedstrom, Kensharp and Vladlenin5000 for providing hints to the answer.

---


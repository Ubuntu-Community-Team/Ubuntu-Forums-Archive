---
title: "Frequency scaling doesn't work on Intel T2300 in Gutsy"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by cadnr on 2007-11-12
I have an acer Aspire 5562 Core Duo laptop.  Frequency scaling worked perfectly under Hoary Hedgehog but since upgrading to Gutsy Gibbon I can't get the frequency scaling module to load at all. Speed stepping works fine in windows and there is no bios setting to turn speedstepping on or off. Please help because this cripples my battery life in linux :(

Can anybody explain why this happens, if I can fix it manually or whether it will be fixed by any future ubuntu upgrades?  I was under the impression that both speedstep-centrino and acpi-cpufreq should work with my hardware, but neither seem to.

>cat /proc/cpuinfo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1662.785
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3329.64
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1662.785
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3325.44
clflush size    : 64

```

>uname -r
```
2.6.22-14-generic

```

>cpufreq-info
```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```


>sudo modprobe acpi-cpufreq
```
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```


>sudo modprobe speedstep-centrino
```
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
```

---

### Post by cadnr on 2007-11-13
Bump

---

### Post by Daelyn on 2007-11-13
I just checked my system and mine uses "powernowd" package to control the cpu scaling and not the acpi-cpufreq speedstep-centrino.

THe powernow daemon is less complex than those two and should work with less effort.

Check if you have that package installed, I suspect everyone has. Also, it does not depend on any module if I unserstand it correctly.

Run ```
 sudo powernowd 
``` and see if you get any output.

My outputs
```
 matt@admin-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4339.77
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4333.96
clflush size    : 64
```

 and for POWERNOW Daemon

```
matt@admin-laptop:~$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1000Mhz - 2167Mhz (4 steps)
powernowd:   cpu1: 1000Mhz - 2167Mhz (4 steps)
```

---

### Post by cadnr on 2007-11-13
Hi, thanks for the reply.  Unfortunately powernowd gives the following error:

```
PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.

```

My dmesg contains the following errors

```
 ACPI Error (psargs-0355): [\_PR_.CPU0.CSTX] Namespace lookup failure, AE_NOT_FOUND
[   80.953499] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q44] (Node dd208360), AE_NOT_FOUND
[  108.910707] ACPI Error (psargs-0355): [\_PR_.CPU0.CSTX] Namespace lookup failure, AE_NOT_FOUND
[  108.910723] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q45] (Node dd20834c), AE_NOT_FOUND
```

which may or may not be related to the problem. I still think the issue lies with the fact that the acpi-cpufreq module is failing to load.

---

### Post by chourave on 2007-11-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/gnome-power-manager/+bug/149665](https://bugs.launchpad.net/ubuntu/gutsy/+source/gnome-power-manager/+bug/149665) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a similar problem with my laptop  : 
cpufreq seem not to work,

```
 powernowd -v
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
Go away, you are not root. Only root can run me.
concombre@NEANT:~$ man powernowd
concombre@NEANT:~$ sudo powernowd -v
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Settings:
powernowd:   verbosity:        1
powernowd:   mode:             1     (AGGRESSIVE)
powernowd:   step:           100 MHz (100000 kHz)
powernowd:   lowwater:        20 %
powernowd:   highwater:       80 %
powernowd:   poll interval: 1000 ms
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
```

and simaler lines in my dmesg : 

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f67a0
[    0.000000] Entering add_active_range(0, 0, 259808) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259808
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259808
[    0.000000] On node 0 totalpages: 259808
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30195 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6720 checksum 0
[    0.000000] ACPI: RSDP 000F6720, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 3F6E7BFF, 0094 (r1 LENOVO TP-63          62  LTP        0)
[    0.000000] ACPI: FACP 3F6EDBD2, 00F4 (r3 INTEL  TP-63          62 ALAN        1)
[    0.000000] ACPI: DSDT 3F6E95C3, 459B (r1 LENOVO TP-63          62 INTL 20060608)
[    0.000000] ACPI: FACS 3F6EEFC0, 0040
[    0.000000] ACPI: APIC 3F6EDCC6, 0068 (r1 INTEL  TP-63          62 LOHR       5A)
[    0.000000] ACPI: HPET 3F6EDD2E, 0038 (r1 INTEL  TP-63          62 LOHR       5A)
[    0.000000] ACPI: MCFG 3F6EDD66, 003C (r1 INTEL  TP-63          62 LOHR       5A)
[    0.000000] ACPI: TCPA 3F6EDDA2, 0032 (r1 Phoeni TP-63          62  TL         0)
[    0.000000] ACPI: SLIC 3F6EDDD4, 0176 (r1 LENOVO TP-63          62 TBD         1)
[    0.000000] ACPI: DBGP 3F6EDF4A, 0034 (r1 LENOVO TP-63          62 LOHR        0)
[    0.000000] ACPI: APIC 3F6EDF7E, 005A (r1 PTLTD  TP-63          62  LTP        0)
[    0.000000] ACPI: BOOT 3F6EDFD8, 0028 (r1 PTLTD  TP-63          62  LTP        1)
[    0.000000] ACPI: SSDT 3F6E8F74, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E88E2, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E83FA, 04E8 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E819B, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6E7C93, 0508 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257779
[    0.000000] Kernel command line: root=UUID=b1e84baf-89a2-456a-967e-37f85882a1f5 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.123 MHz processor.
[   22.648555] Console: colour VGA+ 80x25
[   22.648838] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.649222] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.680710] Memory: 1018612k/1039232k available (2015k kernel code, 19860k reserved, 916k data, 364k init, 121728k highmem)
[   22.680720] virtual kernel memory layout:
[   22.680721]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.680722]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.680724]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   22.680725]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   22.680726]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.680728]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   22.680729]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   22.680732] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.680769] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.680911] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.680916] hpet0: 3 64-bit timers, 14318180 Hz
[   22.761903] Calibrating delay using timer specific routine.. 3461.91 BogoMIPS (lpj=6923832)
[   22.761926] Security Framework v1.0.0 initialized
[   22.761933] SELinux:  Disabled at boot.
[   22.761948] Mount-cache hash table entries: 512
[   22.762075] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   22.762084] monitor/mwait feature present.
[   22.762086] using mwait in idle threads.
[   22.762090] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.762093] CPU: L2 cache: 1024K
[   22.762096] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   22.762106] Compat vDSO mapped to ffffe000.
[   22.762118] Checking 'hlt' instruction... OK.
[   22.778016] SMP alternatives: switching to UP code
[   22.778228] Freeing SMP alternatives: 11k freed
[   22.778506] Early unpacking initramfs... done
[   23.114063] ACPI: Core revision 20070126
[   23.114124] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.145798] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 0c
[   23.145824] Total of 1 processors activated (3461.91 BogoMIPS).
[   23.146020] ENABLING IO-APIC IRQs
[   23.146225] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.293711] Brought up 1 CPUs
[   23.293814] Booting paravirtualized kernel on bare hardware
[   23.293899] Time: 11:22:17  Date: 10/14/107
[   23.293919] NET: Registered protocol family 16
[   23.293994] EISA bus registered
[   23.293999] ACPI: bus type pci registered
[   23.315639] PCI: PCI BIOS revision 2.10 entry at 0xfd883, last bus=5
[   23.315641] PCI: Using configuration type 1
[   23.315643] Setting up standard PCI resources
[   23.319854] ACPI: EC: Look up EC in DSDT
[   23.320454] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   23.354814] ACPI: System BIOS is requesting _OSI(Linux)
[   23.354816] ACPI: Please test with "acpi_osi=!Linux"
[   23.354818] Please send dmidecode to linux-acpi@vger.kernel.org
[   23.355342] ACPI: Interpreter enabled
[   23.355344] ACPI: (supports S0 S3 S4 S5)
[   23.355360] ACPI: Using IOAPIC for interrupt routing
[   23.398416] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   23.398462] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.398470] PCI: Probing PCI hardware (bus 00)
[   23.399178] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   23.399183] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   23.400314] PCI: Transparent bridge - 0000:00:1e.0
[   23.400434] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.400742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   23.400866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   23.401001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   23.406442] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   23.406537] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.406628] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   23.406721] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.406817] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   23.406909] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.407001] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.407092] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   23.407185] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.407195] pnp: PnP ACPI init
[   23.407202] ACPI: bus type pnp registered
[   23.425778] pnp: PnP ACPI: found 11 devices
[   23.425781] ACPI: ACPI bus type pnp unregistered
[   23.425784] PnPBIOS: Disabled by ACPI PNP
[   23.425827] PCI: Using ACPI for IRQ routing
[   23.425830] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.446438] NET: Registered protocol family 8
[   23.446441] NET: Registered protocol family 20
[   23.446490] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.446494] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   23.446497] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   23.446501] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   23.446509] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   23.446511] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   23.449608] Time: tsc clocksource has been installed.
[   23.449624] Switched to high resolution mode on CPU 0
[   23.476780] PCI: Bridge: 0000:00:1c.0
[   23.476781]   IO window: disabled.
[   23.476787]   MEM window: disabled.
[   23.476792]   PREFETCH window: disabled.
[   23.476798] PCI: Bridge: 0000:00:1c.1
[   23.476799]   IO window: disabled.
[   23.476805]   MEM window: d0000000-d00fffff
[   23.476810]   PREFETCH window: disabled.
[   23.476823] PCI: Bus 6, cardbus bridge: 0000:05:04.0
[   23.476825]   IO window: 00002400-000024ff
[   23.476831]   IO window: 00002800-000028ff
[   23.476836]   PREFETCH window: 50000000-53ffffff
[   23.476842]   MEM window: 54000000-57ffffff
[   23.476847] PCI: Bridge: 0000:00:1e.0
[   23.476850]   IO window: 2000-2fff
[   23.476856]   MEM window: d0100000-d01fffff
[   23.476861]   PREFETCH window: 50000000-53ffffff
[   23.476894] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   23.476901] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.476925] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   23.476931] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   23.476942] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   23.476948] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.476966] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   23.476980] NET: Registered protocol family 2
[   23.513579] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.513652] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   23.514745] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   23.515130] TCP: Hash tables configured (established 131072 bind 65536)
[   23.515133] TCP reno registered
[   23.525693] checking if image is initramfs... it is
[   24.192106] Freeing initrd memory: 7059k freed
[   24.192373] Simple Boot Flag at 0x36 set to 0x1
[   24.192708] audit: initializing netlink socket (disabled)
[   24.192722] audit(1195039337.132:1): initialized
[   24.192787] highmem bounce pool size: 64 pages
[   24.194874] VFS: Disk quotas dquot_6.5.1
[   24.194920] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.195005] io scheduler noop registered
[   24.195007] io scheduler anticipatory registered
[   24.195009] io scheduler deadline registered
[   24.195024] io scheduler cfq registered (default)
[   24.195037] Boot video device is 0000:00:02.0
[   24.195202] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.195260] assign_interrupt_mode Found MSI capability
[   24.195263] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.195295] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.195390] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   24.195447] assign_interrupt_mode Found MSI capability
[   24.195450] Allocate Port Service[0000:00:1c.1:pcie00]
[   24.195483] Allocate Port Service[0000:00:1c.1:pcie02]
[   24.195627] isapnp: Scanning for PnP cards...
[   24.549729] isapnp: No Plug & Play device found
[   24.575160] Real Time Clock Driver v1.12ac
[   24.575367] hpet_resources: 0xfed00000 is busy
[   24.575390] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.576566] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.576744] input: Macintosh mouse button emulation as /class/input/input0
[   24.576817] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.600438] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.621982] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.621988] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.621991] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.621999] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.622002] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.622194] mice: PS/2 mouse device common for all mice
[   24.624617] EISA: Probing bus 0 at eisa.0
[   24.624624] Cannot allocate resource for EISA slot 1
[   24.624627] Cannot allocate resource for EISA slot 2
[   24.624652] EISA: Detected 0 cards.
[   24.624744] TCP cubic registered
[   24.624759] NET: Registered protocol family 1
[   24.624785] Using IPI No-Shortcut mode
[   24.624937]   Magic number: 15:71:378
[   24.625273] Freeing unused kernel memory: 364k freed
[   24.671695] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.841076] AppArmor: AppArmor initialized<5>audit(1195039338.632:2):  type=1505 info="AppArmor initialized" pid=1215
[   25.846828] fuse init (API version 7.8)
[   25.852252] Failure registering capabilities with primary security module.
[   25.872985] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   25.872992] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.873004] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.880240] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   25.882259] ACPI: Thermal Zone [TZ00] (31 C)
[   26.348177] usbcore: registered new interface driver usbfs
[   26.348201] usbcore: registered new interface driver hub
[   26.348220] usbcore: registered new device driver usb
[   26.349012] USB Universal Host Controller Interface driver v3.0
[   26.349073] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   26.349084] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.349089] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.349255] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.349288] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   26.349396] usb usb1: configuration #1 chosen from 1 choice
[   26.349419] hub 1-0:1.0: USB hub found
[   26.349426] hub 1-0:1.0: 2 ports detected
[   26.447349] SCSI subsystem initialized
[   26.452608] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   26.452620] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.452624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.452646] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.452680] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   26.452771] usb usb2: configuration #1 chosen from 1 choice
[   26.452796] hub 2-0:1.0: USB hub found
[   26.452802] hub 2-0:1.0: 2 ports detected
[   26.466457] libata version 2.21 loaded.
[   26.482191] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.556465] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   26.556478] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.556482] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.556504] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.556538] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[   26.556635] usb usb3: configuration #1 chosen from 1 choice
[   26.556659] hub 3-0:1.0: USB hub found
[   26.556665] hub 3-0:1.0: 2 ports detected
[   26.660426] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   26.660439] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.660444] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.660466] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   26.660501] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   26.660596] usb usb4: configuration #1 chosen from 1 choice
[   26.660621] hub 4-0:1.0: USB hub found
[   26.660627] hub 4-0:1.0: 2 ports detected
[    3.868000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.872000] Time: hpet clocksource has been installed.
[    3.876000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.948000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[    3.948000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.948000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.948000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.948000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.948000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.948000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd0544000
[    3.996000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.996000] usb usb5: configuration #1 chosen from 1 choice
[    3.996000] hub 5-0:1.0: USB hub found
[    3.996000] hub 5-0:1.0: 8 ports detected
[    4.100000] ata_piix 0000:00:1f.2: version 2.11
[    4.100000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.256000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    4.256000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.256000] scsi0 : ata_piix
[    4.256000] scsi1 : ata_piix
[    4.256000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.256000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.404000] usb 1-1: device not accepting address 2, error -71
[    4.420000] ata1.00: ATA-7: HITACHI HTS541680J9SA00, SB2IC7JP, max UDMA/100
[    4.420000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.436000] ata1.00: configured for UDMA/100
[    4.756000] ata2.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HA01, max UDMA/33
[    4.884000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    4.928000] ata2.00: configured for UDMA/33
[    4.928000] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
[    4.932000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HA01 PQ: 0 ANSI: 5
[    4.932000] 8139cp 0000:05:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.932000] 8139cp 0000:05:01.0: Try the "8139too" driver instead.
[    4.932000] 8139too Fast Ethernet driver 0.9.28
[    4.932000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[    4.932000] PCI: Setting latency timer of device 0000:05:01.0 to 64
[    4.932000] eth0: RealTek RTL8139 at 0xf884e000, 00:0f:b0:d6:1d:27, IRQ 21
[    4.932000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.932000] PCI: Enabling device 0000:05:06.0 (0000 -> 0002)
[    4.932000] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[    4.932000] PCI: Setting latency timer of device 0000:05:06.0 to 64
[    4.988000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.008000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.008000] sd 0:0:0:0: [sda] Write Protect is off
[    5.008000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.008000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.008000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.008000] sd 0:0:0:0: [sda] Write Protect is off
[    5.008000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.008000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.008000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6<6>usb 1-1: configuration #1 chosen from 1 choice
[    5.084000]  sda7 >
[    5.084000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.092000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.092000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.112000] usbcore: registered new interface driver hiddev
[    5.116000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.116000] Uniform CD-ROM driver Revision: 3.20
[    5.116000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.132000] input: HID 1241:1122 as /class/input/input2
[    5.132000] input: USB HID v1.00 Mouse [HID 1241:1122] on usb-0000:00:1d.0-1
[    5.132000] usbcore: registered new interface driver usbhid
[    5.132000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.552000] Attempting manual resume
[    5.552000] swsusp: Resume From Partition 8:6
[    5.552000] PM: Checking swsusp image.
[    5.552000] PM: Resume from disk failed.
[    5.588000] kjournald starting.  Commit interval 5 seconds
[    5.588000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.264000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f76a04000d5]
[   12.976000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.984000] agpgart: Detected an Intel 945GM Chipset.
[   12.984000] agpgart: Detected 7932K stolen memory.
[   13.000000] agpgart: AGP aperture is 256M @ 0xc0000000
[   13.132000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.372000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.532000] Yenta: CardBus bridge found at 0000:05:04.0 [17aa:3828]
[   13.532000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   13.532000] Yenta: Routing CardBus interrupts to PCI
[   13.532000] Yenta TI: socket 0000:05:04.0, mfunc 0x01111c12, devctl 0x44
[   13.764000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   13.764000] Socket status: 30000006
[   13.764000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   13.764000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   13.764000] cs: IO port probe 0x2000-0x2fff: clean.
[   13.764000] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   13.764000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   13.904000] sdhci: Secure Digital Host Controller Interface driver
[   13.904000] sdhci: Copyright(c) Pierre Ossman
[   13.904000] sdhci: SDHCI controller found at 0000:05:06.1 [1180:0822] (rev 19)
[   13.904000] PCI: Enabling device 0000:05:06.1 (0000 -> 0002)
[   13.904000] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
[   13.904000] PCI: Setting latency timer of device 0000:05:06.1 to 64
[   13.904000] mmc0: SDHCI at 0xd0100400 irq 18 DMA
[   14.072000] intel_rng: FWH not detected
[   14.116000] iTCO_vendor_support: vendor-support=0
[   14.144000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.440000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   14.440000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.740000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.812000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   14.816000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.816000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.844000] ieee80211_crypt: registered algorithm 'NULL'
[   14.852000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.852000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.012000] bcm43xx driver
[   15.168000] cs: IO port probe 0x100-0x3af: clean.
[   15.168000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.168000] cs: IO port probe 0x820-0x8ff: clean.
[   15.168000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.172000] cs: IO port probe 0xa00-0xaff: clean.
[   15.388000] si3054: cannot initialize. EXT MID = 0000
[   15.408000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.408000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   15.632000] lp: driver loaded but no devices found
[   15.732000] Adding 1518100k swap on /dev/sda6.  Priority:-1 extents:1 across:1518100k
[   16.384000] EXT3 FS on sda5, internal journal
[   17.296000] kjournald starting.  Commit interval 5 seconds
[   17.300000] EXT3 FS on sda7, internal journal
[   17.300000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.688000] ACPI: AC Adapter [ACAD] (on-line)
[   18.740000] No dock devices found.
[   18.792000] input: Power Button (FF) as /class/input/input4
[   18.796000] ACPI: Power Button (FF) [PWRF]
[   18.836000] input: Lid Switch as /class/input/input5
[   18.840000] ACPI: Lid Switch [LID0]
[   18.876000] input: Power Button (CM) as /class/input/input6
[   18.880000] ACPI: Power Button (CM) [PWRB]
[   18.948000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.960000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.068000] ACPI: Battery Slot [BAT1] (battery present)
[   20.396000] ppdev: user-space parallel port driver
[   20.500000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   20.692000] audit(1195035756.898:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4821 profile="/usr/sbin/cupsd"
[   21.284000] apm: BIOS not found.
[   21.760000] Failure registering capabilities with primary security module.
[   21.952000] Bluetooth: Core ver 2.11
[   21.952000] NET: Registered protocol family 31
[   21.952000] Bluetooth: HCI device and connection manager initialized
[   21.952000] Bluetooth: HCI socket layer initialized
[   21.972000] Bluetooth: L2CAP ver 2.8
[   21.972000] Bluetooth: L2CAP socket layer initialized
[   22.060000] Bluetooth: RFCOMM socket layer initialized
[   22.060000] Bluetooth: RFCOMM TTY layer initialized
[   22.060000] Bluetooth: RFCOMM ver 1.8
[   23.252000] [drm] Initialized drm 1.1.0 20060810
[   23.256000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   23.260000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.024000] ata1.00: configured for UDMA/100
[   26.024000] ata1: EH complete
[   26.024000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   26.024000] sd 0:0:0:0: [sda] Write Protect is off
[   26.024000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.044000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.168000] NET: Registered protocol family 17
[   27.928000] NET: Registered protocol family 10
[   27.928000] lo: Disabled Privacy Extensions
[   27.928000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   38.092000] eth0: no IPv6 routers present
[  675.976000] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  675.976000] usb 1-1: USB disconnect, address 4
[  676.088000] usb 1-1: new low speed USB device using uhci_hcd and address 5
[  676.252000] usb 1-1: configuration #1 chosen from 1 choice
[  676.272000] input: HID 1241:1122 as /class/input/input7
[  676.272000] input: USB HID v1.00 Mouse [HID 1241:1122] on usb-0000:00:1d.0-1
```


what can i do to diagnose / debug this ?

thanks,

---

### Post by Daelyn on 2007-11-14
try using "modconf", It loads drivers you select..

```
sudo apt-get install modconf
```
```
sudo modconf
```

Scroll around, look in menus and activate the CPU freq drivers found.. One of them might just work.. I cant really say, but feels like some trial and error has to be done to succeed with your issues.

Some of the more linux experienced forum members might have some more input. Lets cross our fingers.

---

### Post by cadnr on 2007-11-14
chourave:  I believe your problem may be that you are unlucky enough to have a pentium-M whose frequency scaling is not supported in the Kernel, and needs to be patched in using the PHC patch: [https://www.dedigentoo.org/trac/linux-phc/](https://www.dedigentoo.org/trac/linux-phc/)

I'm not certain of this though, but I came across this as a fix to your pentium-M problem when searching for a solution to my own problem.

---

### Post by cadnr on 2007-11-14
Daelyn:  The p4-clockmod driver does install without errors (although the dmesg complains that it might not be the optimal driver for my CPU).  However, the ondemnd power profile is then hopeless because it only controls one of my CPU's  (and with a very slow response time when I put computational load on), making my computer so sluggish.  Meanwhile the other CPU is set at only 300 MHz.  This is not a satisfactory solution. The correct driver should be acpi-cpufreq which is supposed to work with my hardware....

---

### Post by Daelyn on 2007-11-15
> **cadnr said:**
> Daelyn:  The p4-clockmod driver does install without errors (although the dmesg complains that it might not be the optimal driver for my CPU).  However, the ondemnd power profile is then hopeless because it only controls one of my CPU's  (and with a very slow response time when I put computational load on), making my computer so sluggish.  Meanwhile the other CPU is set at only 300 MHz.  This is not a satisfactory solution. The correct driver should be acpi-cpufreq which is supposed to work with my hardware....

I wish I knew more mate, but I don't have a clue of what could be wrong.
If you search the forum for freq scaling issues etc you might be lucky finding something. I'll keep this thread in my "interesting issues" bookmark folder. If I come across anything that sounds remotely applicable, I'll get in touch.

---


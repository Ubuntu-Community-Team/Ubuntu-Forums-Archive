---
title: "Ubuntu 12.10 (32-bit) only detects 3.2GB RAM"
date: 2013-05-19
forum: Hardware
---

### Post by jabrilm on 2013-05-19
I recently added some RAM to my older machine to try to extend its life, increasing it from 2GB to 4GB. However, Ubuntu only detects 3.2 GB (according to System Monitor and the 'free' command).

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3265       2172       1093          0        405       1161
-/+ buffers/cache:        605       2660
Swap:         3812          0       3812

```

When I first added the new RAM, I was using Ubuntu 12.04 and followed the instructions for enabling PAE support, though I wasn't sure it worked. The output of 'uname -r' didn't change after enabling PAE, PAE did not appear in the GRUB loader, and the amount of detected RAM did not change. So I upgraded to Ubuntu 12.10, since I knew PAE was enabled by default in 12.10. However, the full 4GB is still not detected.

Some details:
[LIST]
[*]Motherboard: Intel DG33TL 
[*]Processor: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz 
[*]RAM: 4 x 1GB 667MHz 
[/LIST]

BIOS detects all 4 GB, so I don't think it is a BIOS upgrade issue. At this point I think either PAE is somehow not enabled (it should be in 12.10, though, right?) or the "missing" RAM is simply allocated for onboard video or something else.

My processor seems to support PAE:


```
$ grep --color=always -i PAE /proc/cpuinfo
flags        : fpu vme de pse tsc msr **pae** mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
flags        : fpu vme de pse tsc msr **pae** mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority
```

Kernel info:

```
$ uname -r
3.2.0-29-generic
```

According to my mobo documentation, it should support up to 8 GB RAM.

Any ideas? At this point I am thinking my only option is to install the 64-bit OS.

Some partial output of 'lshw':

```
$ sudo lshw
                 
    description: Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=DF0F5F60-8B0B-11DC-9634-00E018889BFA
  *-core
       description: Motherboard
       product: DG33TL
       vendor: Intel Corporation
       physical id: 0
       version: AAD89517-803
       serial: BQTL744006XY
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: J1PR
          size: 1998MHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: DPP3510J.86A.0293.2007.1002.1519
          date: 10/02/2007
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x7F7F7F7F7F9B0000
             physical id: 0
             serial: 0xFFFFFFFF
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M3 78T2953EZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: 0x49624C0B
             slot: J6H2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x000000000000000000000000000000000000
             vendor: 0x7F7F7F7F7F9B0000
             physical id: 2
             serial: 0xFFFFFFFF
             slot: J6J1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M3 78T2953EZ3-CE6
             vendor: Samsung
             physical id: 3
             serial: 0x49624BBE
             slot: J6J2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

```

---

### Post by mörgæs on 2013-05-20
Yes, you should go for the 64 bit version. 

There are many threads about only 3,2 or 3,3 GB memory being shown out of 4 GB available. It's likely to be used by other hardware.

---

### Post by jabrilm on 2013-05-21
Yes, I've seen many other threads describing similar issues, but in those cases the solution is usually either 1) enable PAE, or 2) upgrade BIOS. Neither of those seem to be the case here -- unless there is some way that PAE is not enabled in my installation of 12.10. Is there a way to check that? 

Before upgrading to 64-bit, I'm curious if there is a way to 1) confirm that PAE really is enabled, and 2) confirm if that missing 0.8 GB RAM is being allocated for onboard video.

---

### Post by mörgæs on 2013-05-21
In 12.10 PAE is always enabled. The non-PAE 32 bit version has been abandoned. 

You don't have to upgrade to 64 bit in order to find out how it behaves. A live boot will do.

---


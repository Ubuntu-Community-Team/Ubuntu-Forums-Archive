---
title: "Mac Pro Ram upgrade in 10.10 64 not showing total correctly"
date: 2011-02-09
forum: Hardware
---

### Post by UziCorp on 2011-02-09
Hey guys,

I'm relatively new to Ubuntu and am loving it very much. 

At work I use a MacPro which had 8GB of RAM in it. It's a powerful machine with dual xeons and great for software development and running virtual machines. I put in another 6GB totalling the RAM to 16GB. However this does not show up in Ubuntu, it says I have 11.7GB. 

I am using 10.10 64.

When booting into OSX it shows the full 16GB  but that OS is pap and I'd rather use Ubuntu any day!

I'm not sure how to debug this or diagnose what is going on under the covers. Any tips would be much appreciated.

Please find below my output of sudo lshw and below that the output from top:

```

usman@usman-MacPro:~$ sudo lshw
usman-macpro              
    description: Tower Computer
    product: MacPro4,1
    vendor: Apple Inc.
    version: 0.0
    serial: CK01606H20H
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=tower uuid=9A5D59EB-433B-7946-8A78-CF4C41DE04D0
  *-core
       description: Motherboard
       product: Mac-F221BEC8
       vendor: Apple Inc.
       physical id: 0
       serial: C07012303R9DCVHA5
       slot: Part Component
     *-memory
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x484D54313235553742465238432D47372020
             vendor: 0x80AD
             physical id: 0
             serial: 0x0D144707
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x484D54313235553742465238432D47372020
             vendor: 0x80AD
             physical id: 1
             serial: 0x0D34470A
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x393930353437322D3030322E4130314C4620
             vendor: 0x0198
             physical id: 2
             serial: 0x35028640
             slot: DIMM 3
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x393930353437322D3030322E4130314C4620
             vendor: 0x0198
             physical id: 3
             serial: 0x35028540
             slot: DIMM 4
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:4
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x484D54313235553742465238432D47372020
             vendor: 0x80AD
             physical id: 4
             serial: 0x0D944715
             slot: DIMM 5
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:5
             description: DIMM 1066 MHz (0.9 ns)
             product: 0x484D54313235553742465238432D47372020
             vendor: 0x80AD
             physical id: 5
             serial: 0x0D94470F
             slot: DIMM 6
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:6
             description: [empty]
             physical id: 6
             slot: DIMM 7
        *-bank:7
             description: [empty]
             physical id: 7
             slot: DIMM 8
     *-cpu:0
          description: CPU
          product: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (00)
          size: 1596MHz
          capacity: 1596MHz
          width: 64 bits
          clock: 132MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 1c
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 1e
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 1f
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:0
          description: L1 cache
          physical id: 1d
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:1
          description: CPU
          product: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 20
          bus info: cpu@1
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (01)
          size: 2394MHz
          capacity: 2394MHz
          width: 64 bits
          clock: 132MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 21
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 23
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 24
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:1
          description: L1 cache
          physical id: 22
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:2
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 25
          bus info: cpu@2
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (02)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 26
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 28
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 29
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:2
          description: L1 cache
          physical id: 27
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:3
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 2a
          bus info: cpu@3
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (03)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 2b
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 2d
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 2e
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:3
          description: L1 cache
          physical id: 2c
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:4
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 2f
          bus info: cpu@4
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (04)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 30
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 32
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 33
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:4
          description: L1 cache
          physical id: 31
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:5
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 34
          bus info: cpu@5
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (05)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 35
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 37
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 38
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:5
          description: L1 cache
          physical id: 36
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:6
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 39
          bus info: cpu@6
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (06)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 3a
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 3c
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 3d
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:6
          description: L1 cache
          physical id: 3b
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:7
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 3e
          bus info: cpu@7
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-A (07)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 3f
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 41
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 42
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:7
          description: L1 cache
          physical id: 40
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:8
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 43
          bus info: cpu@8
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (00)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 44
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 46
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 47
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:8
          description: L1 cache
          physical id: 45
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:9
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 48
          bus info: cpu@9
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (01)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 49
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 4b
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 4c
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:9
          description: L1 cache
          physical id: 4a
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:10
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 4d
          bus info: cpu@10
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (02)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 4e
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 50
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 51
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:10
          description: L1 cache
          physical id: 4f
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:11
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 52
          bus info: cpu@11
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (03)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 53
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 55
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 56
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:11
          description: L1 cache
          physical id: 54
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:12
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 57
          bus info: cpu@12
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (04)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 58
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 5a
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 5b
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:12
          description: L1 cache
          physical id: 59
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:13
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 5c
          bus info: cpu@13
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (05)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 5d
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 5f
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 60
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:13
          description: L1 cache
          physical id: 5e
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:14
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 61
          bus info: cpu@14
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (06)
          size: 1596MHz
          capacity: 1596MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 62
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 64
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 65
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:14
          description: L1 cache
          physical id: 63
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-cpu:15
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 66
          bus info: cpu@15
          version: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
          slot: CPU-B (07)
          size: 2394MHz
          capacity: 2394MHz
          clock: 132MHz
          capabilities: cpufreq
        *-cache:0
             description: L3 cache
             physical id: 67
             slot: Unknown
             size: 8MiB
             capacity: 8MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 69
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
        *-cache:2
             description: L1 cache
             physical id: 6a
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
     *-cache:15
          description: L1 cache
          physical id: 68
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
     *-firmware
          description: BIOS
          vendor: Apple Inc.
          physical id: 6b
          version: MP41.88Z.0081.B08.1001221313 (01/22/10)
          size: 1MiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect acpi ieee1394boot smartbattery netboot
     *-pci:0
          description: Host bridge
          product: 5520 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 22
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
           *-pci
                description: PCI bridge
                product: PES12T3G2 PCI Express Gen2 Switch
                vendor: Integrated Device Technology, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:0
              *-pci:0
                   description: PCI bridge
                   product: PES12T3G2 PCI Express Gen2 Switch
                   vendor: Integrated Device Technology, Inc.
                   physical id: 2
                   bus info: pci@0000:02:02.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:50
              *-pci:1
                   description: PCI bridge
                   product: PES12T3G2 PCI Express Gen2 Switch
                   vendor: Integrated Device Technology, Inc.
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:51
        *-pci:1
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:90300000-903fffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4870]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:67 memory:80000000-8fffffff memory:90320000-9032ffff ioport:3000(size=256) memory:90300000-9031ffff
        *-pci:2
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43
        *-generic:0 UNCLAIMED
             description: Performance counters
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Physical and Link Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Routing and Protocol Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: 5520/5500 Physical and Link Layer Registers Port 1
             vendor: Intel Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: 8259 cap_list
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: PIC
             product: 5520/5500 Routing & Protocol Layer Register Port 1
             vendor: Intel Corporation
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm io_x_-apic cap_list
             configuration: latency=0
             resources: memory:90427000-90427fff
        *-generic:6
             description: PIC
             product: 5520/5500/X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: driver=i7core_edac latency=0
             resources: irq:0
        *-generic:7 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: latency=0
        *-generic:8 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: latency=0
        *-generic:9 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Throttle Registers
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-generic:10 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Trusted Execution Technology Registers
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic
             configuration: latency=0
        *-generic:11
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:11 memory:90400000-90403fff
        *-generic:12
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.1
             bus info: pci@0000:00:16.1
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:10 memory:90404000-90407fff
        *-generic:13
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:5 memory:90408000-9040bfff
        *-generic:14
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:11 memory:9040c000-9040ffff
        *-generic:15
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.4
             bus info: pci@0000:00:16.4
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:11 memory:90410000-90413fff
        *-generic:16
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.5
             bus info: pci@0000:00:16.5
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:10 memory:90414000-90417fff
        *-generic:17
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.6
             bus info: pci@0000:00:16.6
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:5 memory:90418000-9041bfff
        *-generic:18
             description: System peripheral
             product: 5520/5500/X58 Chipset QuickData Technology Device
             vendor: Intel Corporation
             physical id: 16.7
             bus info: pci@0000:00:16.7
             version: 22
             width: 64 bits
             clock: 33MHz
             capabilities: msix pciexpress pm bus_master cap_list
             configuration: driver=ioatdma latency=0
             resources: irq:11 memory:9041c000-9041ffff
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:40e0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:40c0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:40a0(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:90426000-904263ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:66 memory:90420000-90423fff
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:2000(size=4096) memory:90200000-902fffff ioport:90500000(size=1048576)
           *-network
                description: Ethernet interface
                product: 82574L Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 00
                serial: 00:25:00:f4:41:5f
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.9-0 ip=10.92.16.82 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
                resources: irq:18 memory:90200000-9021ffff memory:90220000-9022ffff ioport:2000(size=32) memory:90230000-90233fff memory:90500000-9053ffff
        *-pci:6
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:1000(size=4096) memory:90100000-901fffff ioport:90600000(size=1048576)
           *-network
                description: Ethernet interface
                product: 82574L Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0a:00.0
                logical name: eth1
                version: 00
                serial: 00:25:00:f4:a5:54
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.9-0 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:19 memory:90100000-9011ffff memory:90120000-9012ffff ioport:1000(size=32) memory:90130000-90133fff memory:90600000-9063ffff
        *-pci:7
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:48 memory:90000000-900fffff
           *-pci
                description: PCI bridge
                product: XIO2213A/B/XIO2221 PCI Express to PCI Bridge
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                resources: memory:90000000-900fffff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller
                   vendor: Texas Instruments
                   physical id: 0
                   bus info: pci@0000:0c:00.0
                   version: 01
                   width: 32 bits
                   clock: 66MHz
                   capabilities: pm ohci bus_master cap_list
                   configuration: driver=firewire_ohci latency=248 maxlatency=4 mingnt=2
                   resources: irq:16 memory:90004000-900047ff memory:90000000-90003fff
        *-pci:8
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:49
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:4080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:4060(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4040(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:90425000-904253ff
        *-pci:9
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:4138(size=8) ioport:414c(size=4) ioport:4130(size=8) ioport:4148(size=4) ioport:4020(size=16) ioport:8000(size=16)
           *-cdrom
                description: DVD writer
                product: DVD-RW GH41N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PQ06
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: Hitachi HDE72106
                vendor: Hitachi
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: ST0B
                serial: STND08MG22193F
                size: 596GiB (640GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00006eee
              *-volume:0 UNCLAIMED
                   description: EFI GPT partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   capacity: 2047KiB
                   capabilities: primary nofs
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: 719a7ca4-abb9-4e5c-8fdc-630e4a17c2c6
                   size: 573GiB
                   capacity: 573GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-11-23 13:44:46 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;J&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-11-23 13:55:06 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-07 19:01:26 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 3fa44cef-77af-44ad-90f5-68d2f7f5a8ec
                   size: 22GiB
                   capacity: 22GiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:90424000-904240ff ioport:4000(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:4128(size=8) ioport:4144(size=4) ioport:4120(size=8) ioport:4140(size=4) ioport:4110(size=16) ioport:4100(size=16)
     *-pci:1
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:00:0d.0
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:00:0d.1
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:00:0d.2
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:00:0d.3
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 5520/5500/X58 Physical Layer Port 0
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:00:0d.4
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 5520/5500 Physical Layer Port 1
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:00:0d.5
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:00:0d.6
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:00:0d.7
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:00:0e.0
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:00:0e.1
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:00:0e.2
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:00:0e.3
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:00:0e.4
          version: 22
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:fe:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:fe:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:16
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 0
          vendor: Intel Corporation
          physical id: 110
          bus info: pci@0000:fe:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:17
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 0
          vendor: Intel Corporation
          physical id: 111
          bus info: pci@0000:fe:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:18
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 1
          vendor: Intel Corporation
          physical id: 112
          bus info: pci@0000:fe:02.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:19
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 1
          vendor: Intel Corporation
          physical id: 113
          bus info: pci@0000:fe:02.5
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:20
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 114
          bus info: pci@0000:fe:03.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:21
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 115
          bus info: pci@0000:fe:03.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:22
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller RAS Registers
          vendor: Intel Corporation
          physical id: 116
          bus info: pci@0000:fe:03.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:23
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 117
          bus info: pci@0000:fe:03.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:24
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 118
          bus info: pci@0000:fe:04.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:25
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 119
          bus info: pci@0000:fe:04.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:26
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 11a
          bus info: pci@0000:fe:04.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:27
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 11b
          bus info: pci@0000:fe:04.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:28
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 11c
          bus info: pci@0000:fe:05.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:29
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 11d
          bus info: pci@0000:fe:05.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:30
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 11e
          bus info: pci@0000:fe:05.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:31
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 11f
          bus info: pci@0000:fe:05.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:32
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers
          vendor: Intel Corporation
          physical id: 120
          bus info: pci@0000:fe:06.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:33
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers
          vendor: Intel Corporation
          physical id: 121
          bus info: pci@0000:fe:06.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:34
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers
          vendor: Intel Corporation
          physical id: 122
          bus info: pci@0000:fe:06.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:35
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 123
          bus info: pci@0000:fe:06.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:36
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 124
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:37
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 125
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:38
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 0
          vendor: Intel Corporation
          physical id: 126
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:39
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 0
          vendor: Intel Corporation
          physical id: 127
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:40
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 1
          vendor: Intel Corporation
          physical id: 128
          bus info: pci@0000:ff:02.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:41
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 1
          vendor: Intel Corporation
          physical id: 129
          bus info: pci@0000:ff:02.5
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:42
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 12a
          bus info: pci@0000:ff:03.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:43
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 12b
          bus info: pci@0000:ff:03.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:44
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller RAS Registers
          vendor: Intel Corporation
          physical id: 12c
          bus info: pci@0000:ff:03.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:45
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 12d
          bus info: pci@0000:ff:03.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:46
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 12e
          bus info: pci@0000:ff:04.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:47
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 12f
          bus info: pci@0000:ff:04.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:48
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 130
          bus info: pci@0000:ff:04.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:49
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 131
          bus info: pci@0000:ff:04.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:50
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 132
          bus info: pci@0000:ff:05.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:51
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 133
          bus info: pci@0000:ff:05.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:52
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 134
          bus info: pci@0000:ff:05.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:53
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 135
          bus info: pci@0000:ff:05.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:54
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers
          vendor: Intel Corporation
          physical id: 136
          bus info: pci@0000:ff:06.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:55
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers
          vendor: Intel Corporation
          physical id: 137
          bus info: pci@0000:ff:06.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:56
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers
          vendor: Intel Corporation
          physical id: 138
          bus info: pci@0000:ff:06.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:57
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 139
          bus info: pci@0000:ff:06.3
          version: 05
          width: 32 bits
          clock: 33MHz
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth0.118
       serial: 00:25:00:f4:41:5f
       size: 1GB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=802.1Q VLAN Support driverversion=1.8 duplex=full firmware=N/A link=yes multicast=yes port=twisted pair speed=1GB/s


```Top:
```

top - 15:37:35 up 1 day, 20:36,  7 users,  load average: 1.47, 1.36, 1.27
Tasks: 377 total,   1 running, 376 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  5.4%sy,  1.2%ni, 90.7%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:  12319716k total, 11822284k used,   497432k free,   209184k buffers
Swap: 23969788k total,       56k used, 23969732k free,  4270920k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                        
 4171 usman     20   0 1494m 885m 869m S   21  7.4 364:01.68 VirtualBox                                                                     
 2968 usman     20   0 1679m 346m 328m S   20  2.9 464:41.24 VirtualBox                                                                     
17065 usman     20   0 1219m 588m 570m S   20  4.9  60:52.25 VirtualBox                                                                     
 2919 usman     20   0 1368m 142m 120m S   20  1.2 464:40.17 VirtualBox                                                                     
 4120 usman     20   0 1458m 588m 571m S   20  4.9 349:27.91 VirtualBox                                                                     
 2891 usman     20   0 1340m 248m 232m S   20  2.1 463:38.03 VirtualBox                                                                     
 2944 usman     20   0 1408m 334m 316m S   19  2.8 450:33.83 VirtualBox                                                                     
 1850 root      20   0  638m 213m 176m S   15  1.8   1299:30 Xorg                                                                           
22454 usman     20   0  885m 262m  35m S   11  2.2   5:10.31 firefox-bin                                                                    
 2701 usman     20   0  364m  42m  14m S    5  0.4   1774:42 gnome-system-mo                                                                
12929 usman     20   0  411m 100m  19m S    3  0.8  42:54.38 npviewer.bin                                                                   
22500 usman     20   0  383m  83m  17m S    2  0.7   4:02.93 npviewer.bin                                                                   
 3042 usman     20   0 1840m 1.1g 129m S    2  9.5  72:02.49 java                                                                           
 6193 usman     20   0  476m  26m  12m S    2  0.2   4:49.64 gnome-terminal                                                                 
  197 root      20   0     0    0    0 S    1  0.0  27:26.21 kondemand/1                                                                    
 2210 usman     20   0  308m  36m 8704 S    1  0.3  22:06.37 compiz                                                                         
 2252 usman      9 -11  846m  13m  11m S    1  0.1  22:24.49 pulseaudio                                                                     
 2266 usman     20   0  852m  78m  24m S    1  0.6   8:38.95 nautilus                                                                       
 2853 usman     20   0  276m 9532 6352 S    1  0.1  18:50.63 VBoxSVC                                                                        
   37 root      20   0     0    0    0 S    1  0.0   5:38.42 ksoftirqd/11                                                                   
  196 root      20   0     0    0    0 S    1  0.0  20:09.27 kondemand/0                                                                    
 2454 usman     20   0  304m  15m  10m S    1  0.1   0:38.65 gtk-window-deco                                                                
 2543 usman     20   0  278m  10m 8324 S    1  0.1  16:01.95 multiload-apple                                                                
24157 usman     20   0 19536 1648 1060 R    1  0.0   0:00.28 top                                                                            
    3 root      20   0     0    0    0 S    0  0.0   0:43.45 ksoftirqd/0                                                                    
   54 root      20   0     0    0    0 S    0  0.0   0:03.11 events/3                                                                       
 1711 root      20   0 78324 3420 2752 S    0  0.0   2:44.83 gdm-binary                                                                     
 2177 usman     20   0  464m  43m  10m S    0  0.4   4:19.35 gnome-settings-                                                                
 2258 usman     20   0  346m  19m  12m S    0  0.2   5:00.88 gnome-panel                                                                    
 2535 usman     20   0  338m  16m  11m S    0  0.1   0:49.18 wnck-applet                                                                    
 2555 usman     20   0  326m  14m  10m S    0  0.1   3:36.98 netspeed_applet                                                                
 2844 usman     20   0 86052 4320 3272 S    0  0.0   7:56.42 VBoxXPCOMIPCD                                                                  
16785 usman     20   0  554m  42m  28m S    0  0.4   0:04.39 VirtualBox                                                                     
23401 usman     20   0  479m  75m  14m S    0  0.6   0:11.88 evince                                                                         
    1 root      20   0 23880 2016 1280 S    0  0.0   0:03.26 init                                                                           
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                       
    4 root      RT   0     0    0    0 S    0  0.0   0:02.28 migration/0                                                                    
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                     
    6 root      RT   0     0    0    0 S    0  0.0   0:01.47 migration/1                                                                    
    7 root      20   0     0    0    0 S    0  0.0   0:02.18 ksoftirqd/1                                                                    
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1  

```

Thanks in advance.

---

### Post by UziCorp on 2011-02-14
bump - anyone had anything similar on mac hardware?

---


---
title: "CPU Frequency slow down"
date: 2010-07-19
forum: Hardware
---

### Post by Moonlext on 2010-07-19
Hi all, I compiled a kernel, eliminating a large number of modules and otherwise in order to optimize the boot time, but I feel slower.

I have checked with the command "lshw" and compared it with the previous result, I found that there are the following changes:

```
*-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          **size: 2GHz**
          capacity: 2GHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq

           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:03:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                **resources: irq:18 memory:f1bff400-f1bff4ff**
           ***-generic:1**
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:03:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                **configuration: driver=ricoh-mmc latency=64**
                **resources: irq:5 memory:f1bff500-f1bff5ff**
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:03:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                **resources: memory:f1bff600-f1bff6ff**
           [B]*-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 9.4
                bus info: pci@0000:03:09.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatenc[/B]

  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       **logical name: vboxnet0**
       **serial: 0a:00:27:00:00:00**
       capabilities: ethernet physical
       **configuration: broadcast=yes multicast=yes**
```

```
*-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          **size: 1GHz**
          capacity: 2GHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq

           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:03:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                **resources: irq:18 memory:f1bff500-f1bff5ff**
           ***-generic:1 UNCLAIMED**
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:03:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                **configuration: latency=64**
                **resources: memory:f1bff600-f1bff6ff**
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:03:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                **resources: memory:f1bff700-f1bff7ff**

  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       **logical name: ifb0**
       **serial: be:3e:88:7a:8d:f6**
       capabilities: ethernet physical
       **configuration: broadcast=yes**
  [B]*-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: ifb1
       serial: 6e:41:c2:ea:e2:a6
       capabilities: ethernet physical
       configuration: broadcast=yes[/B]
```

Sorry for my english and thank for help.

---

### Post by Moonlext on 2010-07-19
Ok, I fixed that disabling "CPU Frequency Scaling" option in menuconfig.

Thanks. :)

---


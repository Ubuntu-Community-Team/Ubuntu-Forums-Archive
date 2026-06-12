---
title: "Problemas con placa de video Intel HD - UBUNTU 11.04"
date: 2011-06-10
forum: Hardware
---

### Post by TitanARG on 2011-06-10
Hola, el problema que tengo es que la única forma de poder iniciar ubuntu 11.04, es editando en grub al inicio y colocar i915.modeset=0. La verdad ya no se que hacer.
De todas formas no es detectada la placa de video.
Este es un detalle casi al final está la parte de video.

   *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 2GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.5.5
          serial: 0002-0655-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 1.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 1.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 1.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 1.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 1.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 1.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 1.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 1.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 1.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 1.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 1.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 1.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 1.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 1.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 18
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:fb800000-fbbfffff memory:d0000000-dfffffff ioport:dc00(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:fbcfa000-fbcfa00f

---


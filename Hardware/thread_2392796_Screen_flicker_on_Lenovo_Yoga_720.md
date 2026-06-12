---
title: "Screen flicker on Lenovo Yoga 720"
date: 2018-05-25
forum: Hardware
---

### Post by helotbc-0 on 2018-05-25
Good morning, I am running Ubuntu 18.4 on a Yoga 720. No matter what the brightness setting, my screen momentarily dims and then un-dims in about 5sec intervals. Any help would be appreciated. My system is:
b-tron
    description: Convertible
    product: 81C3 (LENOVO_MT_81C3_BU_idea_FM_YOGA 720-13IKB)
    vendor: LENOVO
    version: Lenovo YOGA 720-13IKB
    serial: MP1CHKDC
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=convertible family=YOGA 720-13IKB frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_81C3_BU_idea_FM_YOGA 720-13IKB uuid=D501F8CA-87C3-E711-BBB6-9829A61F3AF2
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: SDK0J40709 WIN
       serial: MP1CHKDC
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 1YCN36WW(V2.03)
          date: 09/11/2017
          size: 128KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3399MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves ibpb ibrs stibp dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: M471A5244CB0-CRC
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: M471A5244CB0-CRC
             vendor: Samsung
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:128 memory:2ff0000000-2ff0ffffff memory:2fe0000000-2fefffffff ioport:4000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Skylake Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: iomemory:2f0-2ef irq:16 memory:2ff1010000-2ff1017fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:7a300000-7a30ffff
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: iomemory:2f0-2ef irq:18 memory:2ff1022000-2ff1022fff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: iomemory:2f0-2ef irq:16 memory:2ff1021000-2ff1021fff
        *-generic:3
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: iomemory:2f0-2ef irq:17 memory:2ff1020000-2ff1020fff
        *-generic:4
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #2
             vendor: Intel Corporation
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: iomemory:2f0-2ef irq:18 memory:2ff101f000-2ff101ffff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: iomemory:2f0-2ef irq:127 memory:2ff101e000-2ff101efff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:3000(size=4096) memory:63000000-63ffffff ioport:62000000(size=16777216)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:5000(size=4096) memory:64000000-7a0fffff ioport:40000000(size=570425344)
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:7a200000-7a2fffff
           *-network
                description: Wireless interface
                product: Wireless 8265 / 8275
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:3f:00.0
                logical name: wlp63s0
                version: 78
                serial: 00:e1:8c:77:b7:62
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-20-generic firmware=34.0.1 ip=192.168.1.174 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:136 memory:7a200000-7a201fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 memory:7a100000-7a1fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM961/PM961
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:40:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:7a100000-7a103fff
        *-generic:5
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO UART Controller #0
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: iomemory:2f0-2ef irq:20 memory:2ff101d000-2ff101dfff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:7a310000-7a313fff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:130 memory:2ff1018000-2ff101bfff memory:2ff1000000-2ff100ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:2f0-2ef memory:2ff101c000-2ff101c0ff ioport:4040(size=32)
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh

---

### Post by gerbalblaste on 2018-06-15
Is the setting "Automatic brightness" under Settings -> Power enabled?

---

### Post by OiPenguin on 2018-07-18
Have you managed to resolve the issue with the screen flicker? How is your overall experience with Ubuntu on Yoga? Are you able to use it as a tablet as well as a laptop? I've just ordered one, although reluctantly. I was initially planning to install 16.04 LTS (to keep using Unity), but wonder if I'm better of choosing a more recent Version of Ubuntu.

---


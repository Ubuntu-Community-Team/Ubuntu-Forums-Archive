---
title: "Toshiba Thunderbolt 3 Dock - Ubuntu 16.04 - Configuration Help Please"
date: 2017-12-08
forum: Hardware
---

### Post by Rocko262c on 2017-12-08
Dear Everyone,

I have a Toshiba Portege X30-D-143 with a Toshiba Thunderbolt 3 Dock. My computer is dual boot with Windows 10 and Ubuntu 16.04. 

Unfortunately the Toshiba Thunderbolt 3 Dock only provides power to the computer. The network and USB ports don't work and I haven't even attempted to try a monitor yet. Can someone help getting this device to run?

I have performed a lshw
```
sudo lshw
```

Here is the output:
[HTML]    description: Notebook
    product: PORTEGE X30-D (PT272E)
    vendor: TOSHIBA
    version: PT272E-03X00SGR
    serial: 9H060071H
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=PORTEGE frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=PT272E uuid=C60B7F80-9564-11E7-8145-C83948060071
  *-core
       description: Motherboard
       product: 10 PCBA 3
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: C0440506B0H91010
       slot: Center
     *-memory
          description: System Memory
          physical id: 2
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: ChannelA-DIMM0
        *-bank:1
             description: SODIMM Synchronous 2133 MHz (0,5 ns)
             product: M471A2K43CB1-CRC
             vendor: Samsung
             physical id: 1
             serial: 9891DC4A
             slot: ChannelB-DIMM0
             size: 16GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-cache:0
          description: L1 cache
          physical id: 7
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 8
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 9
          slot: L3 Cache
          size: 4MiB
          capacity: 4MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz
          vendor: Intel Corp.
          physical id: a
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-7500U CPU @ 2.70GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3499MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 11
          version: Version 2.50
          date: 06/28/2017
          size: 1MiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:281 memory:cf000000-cfffffff memory:90000000-9fffffff ioport:3000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:d0300000-d030ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-42-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Primax Electronics, Ltd
                   physical id: 1
                   bus info: usb@1:1
                   version: 2.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1Mbit/s
              *-usb:1
                   description: Human interface device
                   product: SiS HID Touch Controller
                   physical id: 5
                   bus info: usb@1:5
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Video
                   product: TOSHIBA Web Camera - HD
                   vendor: Chicony Electronics Co.,Ltd.
                   physical id: 6
                   bus info: usb@1:6
                   version: 26.15
                   serial: 0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:3 UNCLAIMED
                   description: Generic USB device
                   vendor: Synaptics, Inc.
                   physical id: 7
                   bus info: usb@1:7
                   version: 1.54
                   serial: d76e9800960c
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:4
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.10
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-42-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb
                   description: Communication device
                   product: EM7455
                   vendor: Sierra Wireless, Incorporated
                   physical id: 2
                   bus info: usb@2:2
                   version: 0.06
                   serial: LF73063180031020
                   capabilities: usb-3.00
                   configuration: driver=cdc_mbim maxpower=504mA speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:d0328000-d0328fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:285 memory:d0329000-d0329fff
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
             resources: irq:122 memory:d0200000-d02fffff
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:279 memory:d0200000-d0200fff
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
             resources: irq:123 memory:d0100000-d01fffff
           *-network
                description: Wireless interface
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 78
                serial: cc:2f:71:f7:49:c8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-42-generic firmware=22.391740.0 ip=192.168.0.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:286 memory:d0100000-d0101fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:d0000000-d00fffff
           *-storage
                description: Non-Volatile memory controller
                product: Samsung Electronics Co Ltd
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:d0000000-d0003fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:4000(size=4096) memory:a0000000-ce0fffff ioport:40000000(size=1241513984)
           *-pci
                description: PCI bridge
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: iomemory:1f10-1f0f irq:287 memory:a0000000-ce0fffff ioport:40000000(size=1241513984)
              *-pci:0
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:05:00.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:288 memory:ce000000-ce0fffff
                 *-generic UNCLAIMED
                      description: System peripheral
                      product: Intel Corporation
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:06:00.0
                      version: 02
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list
                      configuration: latency=0
                      resources: memory:ce000000-ce03ffff memory:ce040000-ce040fff
              *-pci:1
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:05:01.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:289 memory:a0000000-b7efffff ioport:40000000(size=536870912)
              *-pci:2
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:05:02.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:290 memory:b7f00000-b7ffffff
              *-pci:3
                   description: PCI bridge
                   product: Intel Corporation
                   vendor: Intel Corporation
                   physical id: 4
                   bus info: pci@0000:05:04.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:291 memory:b8000000-cdffffff ioport:60000000(size=704643072)
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
        *-memory
             description: Memory controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:d0324000-d0327fff
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
             configuration: driver=snd_hda_intel latency=64
             resources: irq:292 memory:d0320000-d0323fff memory:d0310000-d031ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d032a000-d032a0ff ioport:efa0(size=32)
  *-battery
       vendor: TOSHIBA
       physical id: 1
       version: **/**/****
       serial: 0000000000
       slot: 1st Battery
  *-power UNCLAIMED
       physical id: 2
       capacity: 32768mWh
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: wwp0s20f0u2i12
       serial: 0e:32:92:6b:88:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes
[/HTML]

Thanks in advance.

Cheers,
Rocko262c

---


---
title: "Custom laptop issues"
date: 2020-03-06
forum: Hardware
---

### Post by a3lm on 2020-03-06
Hi,
I bought a laptop from a custom assembler, and I am having some issues like gui freezings, crashes, no external monitor detection or other gui freezes after using vmware, random no usb detection, and other strange minor behaviours that I cannot say if are caused by some kind of hardware incompatibility.
The laptop is a XMG 507 value edition (tell me if I can link the manufacturer site, otherwise is accessibile by googling it) and this is the output from lshw:
```
     
    description: Notebook
    product: XMG Mobile A507 VE (XA507VEL18)
    vendor: SchenkerTechnologiesGmbH
    version: Not Applicable
    serial: 1901N857EJ1M1KAPA000079
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=notebook family=XMG A507 VE sku=XA507VEL18 uuid=80FA5B65-9BF7-0000-0000-000000000000
  *-core
       description: Motherboard
       product: N857EX1M
       vendor: SchenkerTechnologiesGmbH
       physical id: 0
       version: Not Applicable
       serial: NKN857EJ1M19A00079
       slot: Not Applicable
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1.07.06RGME3_10004
          date: 11/21/2019
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CTD
             vendor: Samsung
             physical id: 0
             serial: 41724E34
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2667 MHz (0,4 ns)
             product: M471A1K43CB1-CTD
             vendor: Samsung
             physical id: 1
             serial: 3223779A
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: 1d
          slot: L1 Cache
          size: 384KiB
          capacity: 384KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 1e
          slot: L2 Cache
          size: 1536KiB
          capacity: 1536KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 1f
          slot: L3 Cache
          size: 9MiB
          capacity: 9MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 20
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2210MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=6 enabledcores=6 threads=12
     *-pci
          description: Host bridge
          product: 8th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:4000(size=4096) memory:a3000000-a40fffff ioport:90000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GP107M [GeForce GTX 1050 Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:159 memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128) memory:a4000000-a407ffff
           *-multimedia
                description: Audio device
                product: GP107GL High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:a4080000-a4083fff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:157 memory:a2000000-a2ffffff memory:80000000-8fffffff ioport:5000(size=64) memory:c0000-dffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
             resources: memory:a4422000-a4422fff
        *-generic:1
             description: Signal processing controller
             product: Cannon Lake PCH Thermal Controller
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a4421000-a4421fff
        *-usb
             description: USB controller
             product: Cannon Lake PCH USB 3.1 xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:a4400000-a440ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.3.0-40-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: 2.4G Wireless Mouse
                   vendor: MOSART Semi.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.08
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Wireless Mouse & KeyBoard V1.01
                   vendor: G-Tech CHINA
                   physical id: 6
                   bus info: usb@1:6
                   version: 0.20
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:2
                   description: Video
                   product: Chicony USB 2.0 Camera
                   vendor: SunplusIT Inc
                   physical id: 8
                   bus info: usb@1:8
                   version: 36.04
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: e
                   bus info: usb@1:e
                   version: 0.02
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.3.0-40-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-3.10
                configuration: driver=hub slots=8 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Cannon Lake PCH Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:a441a000-a441bfff memory:a4420000-a4420fff
        *-network
             description: Wireless interface
             product: Wireless-AC 9560 [Jefferson Peak]
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             logical name: wlo1
             version: 10
             serial: 50:76:af:da:8b:2b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-40-generic firmware=46.6bf1df06.0 ip=192.168.1.79 latency=0 link=yes multicast=yes wireless=IEEE 802.11
             resources: irq:16 memory:a4414000-a4417fff
        *-communication
             description: Communication controller
             product: Cannon Lake PCH HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:142 memory:a441f000-a441ffff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:127 memory:a4418000-a4419fff memory:a441e000-a441e0ff ioport:5090(size=8) ioport:5080(size=4) ioport:5060(size=32) memory:a441d000-a441d7ff
        *-pci:1
             description: PCI bridge
             product: Cannon Lake PCH PCI Express Root Port 9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:a4300000-a43fffff
           *-storage
                description: Non-Volatile memory controller
                product: Kingston Technology Company, Inc.
                vendor: Kingston Technology Company, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:a4300000-a4303fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.6
             bus info: pci@0000:00:1d.6
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 ioport:3000(size=4096) memory:a4200000-a42fffff
           *-generic
                description: Unassigned class
                product: RTL8411B PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:126 memory:a4215000-a4215fff memory:a4200000-a420ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: enp3s0f1
                version: 12
                serial: 80:fa:5b:65:9b:f7
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII
                resources: irq:18 ioport:3000(size=256) memory:a4214000-a4214fff memory:a4210000-a4213fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Cannon Lake PCH cAVS
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:158 memory:a4410000-a4413fff memory:a4100000-a41fffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Cannon Lake PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a441c000-a441c0ff ioport:efa0(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Cannon Lake PCH SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff



```

Can You tell what may I do to check me if there is any particular hardware issue, or drivers i should rely on?
Or what steps should I  do to configure it right after a clean install? 
I just installed proprietary nvidia drivers at first due to the fact at first clean ubuntu's installation it showed no gui.

---

### Post by QIII on 2020-03-06
Hello!

Did this machine come with Windows pre-installed, or without any OS?

Which release of Ubuntu did you install?  Was it the server image?  Where did you get the image?

The more you can tell us, the better the chances we can help.

Cheers!

---

### Post by a3lm on 2020-03-06
Hi, thanks for the interest.
The machine was with no os installed, and I installed Ubuntu 18.04.4 LTS, desktop version

---

### Post by ajgreeny on 2020-03-06
What driver have you installed, if any, from the additional drivers utility?

That Nvidia 1050 card will probably need a driver selected from those listed there.

---

### Post by sterfan-54563424 on 2020-03-18
Hi,
I have the same Notebook and running it with Linux Mint Cinnamon 19...3 I guess.
and with the Nvidia Driver supplied by Mint (ubuntu)
I think I had trouble with wifi but after installing the intel driver (iwlwifi) they are working now and I have to run the VGA in performance mode or I only connect 1 external monitor.
USB mouse , keyboard and headset are working fine.

R u sure you do not have a broken machine? have you tried installing windows 10 and see it if has trouble too?

bye

---


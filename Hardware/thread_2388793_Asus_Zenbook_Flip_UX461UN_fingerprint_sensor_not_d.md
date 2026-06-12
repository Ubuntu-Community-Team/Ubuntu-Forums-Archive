---
title: "Asus Zenbook Flip UX461UN fingerprint sensor not detected"
date: 2018-04-07
forum: Hardware
---

### Post by lifeboy on 2018-04-07
Ubuntu 17.10 (Kernel 4.14.29-041429-generic #201803211330 SMP Wed Mar 21 13:32:35 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux) does not detect any hardware of this type at all.

```
sudo lshw -businfo
Bus info          Device  Class          Description
====================================================
                          system         UX461UN
                          bus            UX461UN
                          memory         64KiB BIOS
                          memory         16GiB System Memory
                          memory         8GiB Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
                          memory         8GiB Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
                          memory         256KiB L1 cache
                          memory         1MiB L2 cache
                          memory         8MiB L3 cache
cpu@0                     processor      Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
pci@0000:00:00.0          bridge         Intel Corporation
pci@0000:00:02.0          display        Intel Corporation
pci@0000:00:04.0          generic        Skylake Processor Thermal Subsystem
pci@0000:00:13.0          generic        Intel Corporation
pci@0000:00:14.0          bus            Sunrise Point-LP USB 3.0 xHCI Controller
usb@1             usb1    bus            xHCI Host Controller
usb@1:1                   input          Dell USB Keyboard
usb@1:5                   multimedia     USB2.0 HD UVC WebCam
usb@1:8                   communication  Bluetooth wireless interface
usb@2             usb2    bus            xHCI Host Controller
pci@0000:00:14.2          generic        Sunrise Point-LP Thermal subsystem
pci@0000:00:15.0          generic        Sunrise Point-LP Serial IO I2C Controller #0
pci@0000:00:15.1          generic        Sunrise Point-LP Serial IO I2C Controller #1
pci@0000:00:16.0          communication  Sunrise Point-LP CSME HECI #1
pci@0000:00:1c.0          bridge         Intel Corporation
pci@0000:01:00.0          display        NVIDIA Corporation
pci@0000:00:1c.6          bridge         Sunrise Point-LP PCI Express Root Port #7
pci@0000:02:00.0  wlp2s0  network        Wireless 8265 / 8275
pci@0000:00:1d.0          bridge         Sunrise Point-LP PCI Express Root Port #9
pci@0000:03:00.0          storage        Intel Corporation
pci@0000:00:1e.0          generic        Sunrise Point-LP Serial IO UART Controller #0
pci@0000:00:1e.2          generic        Sunrise Point-LP Serial IO SPI Controller #0
pci@0000:00:1f.0          bridge         Intel Corporation
pci@0000:00:1f.2          memory         Memory controller
pci@0000:00:1f.3          multimedia     Intel Corporation
pci@0000:00:1f.4          bus            Sunrise Point-LP SMBus

```

Even the full lshw finds nothing:

```

roland-zenbook              
    description: Convertible
    product: UX461UN
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: J1N0CX17A84604B
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=convertible family=UX uuid=4A314E30-4358-3137-4138-343630344241
  *-core
       description: Motherboard
       product: UX461UN
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: QCCBKQ0JE80300258
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: UX461UN.305
          date: 12/04/2017
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: K4EBE304EB-EGCG
             vendor: Samsung
             physical id: 0
             serial: 55000000
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: K4EBE304EB-EGCG
             vendor: Samsung
             physical id: 1
             serial: 55000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-cache:0
          description: L1 cache
          physical id: d
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: e
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: f
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 10
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3155MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
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
             resources: irq:135 memory:ed000000-edffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
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
             resources: irq:16 memory:ef320000-ef327fff
        *-generic:1
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: irq:20 memory:ef337000-ef337fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:ef310000-ef31ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.14.29-041429-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.14
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: Dell USB Keyboard
                   vendor: Dell
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: USB2.0 HD UVC WebCam
                   vendor: Azurewave
                   physical id: 5
                   bus info: usb@1:5
                   version: 17.04
                   serial: 0x0001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.10
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.14.29-041429-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.14
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:ef336000-ef336fff
        *-generic:3
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
             resources: irq:16 memory:ef335000-ef335fff
        *-generic:4
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
             resources: irq:17 memory:ef334000-ef334fff
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
             resources: irq:138 memory:ef333000-ef333fff
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
             resources: irq:122 ioport:e000(size=4096) memory:ee000000-ef0fffff ioport:d0000000(size=301989888)
           *-display
                description: 3D controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:127 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:ef000000-ef07ffff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:ef200000-ef2fffff
           *-network
                description: Wireless interface
                product: Wireless 8265 / 8275
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 78
                serial: e0:9d:31:f2:c0:f6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.14.29-041429-generic firmware=31.560484.0 ip=192.168.1.109 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:139 memory:ef200000-ef201fff
        *-pci:2
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
             resources: irq:124 memory:ef100000-ef1fffff
           *-storage
                description: Non-Volatile memory controller
                product: Intel Corporation
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:ef100000-ef103fff
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
             resources: irq:20 memory:ef332000-ef332fff
        *-generic:6
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO SPI Controller #0
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:22 memory:ef331000-ef331fff
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
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:ef32c000-ef32ffff
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
             resources: irq:140 memory:ef328000-ef32bfff memory:ef300000-ef30ffff
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
             resources: memory:ef330000-ef3300ff ioport:f040(size=32)

```

lsusb only finds the keyboard, not even the touchpad into which the fingerprint sensor is embedded.

```

sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 13d3:56a2 IMC Networks
Bus 001 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

However, Ubuntu does see the touchpad and it works properly:

[ATTACH=CONFIG]279194[/ATTACH]

---

### Post by Ducktor on 2018-04-21
I have the same issue. I searched for drivers for my fingerprint sensor, but I realized, that even lsusb doesn't see it, so I don't know how to continue. By the way, I'm using Antergos (almost identical to Arch Linux) at the moment.
I can confirm that it works in Windows, and says its driver is ELAN, so it should be found under Linux, even if it wouldn't work out of the box.

---


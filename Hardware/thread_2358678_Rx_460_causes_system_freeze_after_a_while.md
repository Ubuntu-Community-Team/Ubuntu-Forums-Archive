---
title: "Rx 460 causes system freeze after a while"
date: 2017-04-16
forum: Hardware
---

### Post by cgameing on 2017-04-16
This issue has been a problem for some time, and even happens on the proprietary drivers. However it should be noted that this only happens on linux and not on windows, so its definitely a software issue.

It  should be noted that this issue still happens with no applications open  and just leaving the system alone, however the time it takes for the  system to hang is greatly accelerated by having applications open that  use a ton of gpu resources, (ie steam games, mostly 3D ones with  shaders).

The  gpu is not overheating as the thermals don't get very high and as  mentioned before it can happen with idle temperatures (37.0 degrees  Celsius), also it time it takes can also be decreased by using a second  gpu, in this case a r7-240.


I have tried the following drivers to no avail.
padoka ppa
mesa 17 (Installed by default in 17.04 where it was tested)
default mesa drivers for ubuntu 16.04 and 16.10
Properietary drivers (16.50, 16.60, 17.10)

Also these posts do not provide a working solution
[https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly](https://askubuntu.com/questions/761706/ubuntu-15-10-and-16-04-keep-freezing-randomly)
[https://ubuntuforums.org/showthread.php?t=2343073](https://ubuntuforums.org/showthread.php?t=2343073)




Any assistance to prevent my gpu from freezing is greatly appreciated.

---

### Post by mörgæs on 2017-04-17
Please begin with a complete hardware description, for example by copying ```
sudo lshw -sanitize > lshw.txt
``` into the terminal and execute it. After that post lshw.txt in CODE tags.

---

### Post by cgameing on 2017-05-25
```
computer
    description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PRIME B350-PLUS
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0609
          date: 04/19/2017
          size: 64KiB
          capacity: 15MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335) [empty]
             product: Unknown
             vendor: Unknown
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A1
        *-bank:1
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335) [empty]
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_A2
        *-bank:2
             description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: CMV8GX4M1A2133C15
             vendor: Unknown
             physical id: 2
             serial: [REMOVED]
             slot: DIMM_B1
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335)Project-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-02 13:04+0000Last-Translator: Joel Addison <jaddi27@gmail.com>Language-Team: English (Australia) <en_AU@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2017-04-04 11:54+0000X-Generator: Launchpad (build 18335) [empty]
             product: Unknown
             vendor: Unknown
             physical id: 3
             serial: [REMOVED]
             slot: DIMM_B2
     *-cache:0
          description: L1 cache
          physical id: 2e
          slot: L1 - Cache
          size: 768KiB
          capacity: 768KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 2f
          slot: L2 - Cache
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 30
          slot: L3 - Cache
          size: 16MiB
          capacity: 16MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 7 1700 Eight-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 31
          bus info: cpu@0
          version: AMD Ryzen 7 1700 Eight-Core Processor
          serial: [REMOVED]
          slot: AM4
          size: 1550MHz
          capacity: 3750MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_l2 mwaitx hw_pstate vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic overflow_recov succor smca cpufreq
          configuration: cores=8 enabledcores=8 threads=8
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:f000(size=4096) memory:fe600000-fe7fffff
           *-usb
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: msi pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:225 memory:fe7a0000-fe7a7fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.10.0-21-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 4.10
                   capabilities: usb-2.00
                   configuration: driver=hub slots=10 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 1
                      bus info: usb@1:1
                      version: 12.03
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                 *-usb:1
                      description: Keyboard
                      product: COUGAR600K Gaming Keyboard
                      vendor: COUGAR600K
                      physical id: 2
                      bus info: usb@1:2
                      version: 0.33
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:2
                      description: Wireless interface
                      product: MotoG3
                      vendor: motorola
                      physical id: 3
                      bus info: usb@1:3
                      version: ff.ff
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=rndis_host maxpower=500mA speed=480Mbit/s
                 *-usb:3
                      description: Generic USB device
                      product: Gamepad F310
                      vendor: Logitech
                      physical id: 4
                      bus info: usb@1:4
                      version: 40.14
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=xpad maxpower=500mA speed=12Mbit/s
                 *-usb:4
                      description: Bluetooth wireless interface
                      vendor: Intel Corp.
                      physical id: 9
                      bus info: usb@1:9
                      version: 0.01
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.10.0-21-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 4.10
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
           *-storage
                description: SATA controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:228 memory:fe780000-fe79ffff memory:fe700000-fe77ffff
           *-pci
                description: PCI bridge
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:219 ioport:f000(size=4096) memory:fe600000-fe6fffff
              *-pci:0
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 0
                   bus info: pci@0000:1d:00.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:221 ioport:f000(size=4096) memory:fe600000-fe6fffff
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:1e:00.0
                      logical name: enp30s0
                      version: 15
                      serial: [REMOVED]
                      size: 10Mbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                      resources: irq:229 ioport:f000(size=256) memory:fe604000-fe604fff memory:fe600000-fe603fff
              *-pci:1
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 1
                   bus info: pci@0000:1d:01.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:223
                 *-pci
                      description: PCI bridge
                      product: ASM1083/1085 PCIe to PCI Bridge
                      vendor: ASMedia Technology Inc.
                      physical id: 0
                      bus info: pci@0000:1f:00.0
                      version: 04
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
              *-pci:2
                   description: PCI bridge
                   product: Advanced Micro Devices, Inc. [AMD]
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 4
                   bus info: pci@0000:1d:04.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci msi pm pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:224
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:e000(size=4096) memory:fe900000-fe9fffff ioport:e0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Baffin [Radeon RX 460]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:22:00.0
                version: cf
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=amdgpu latency=0
                resources: irq:233 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:fe900000-fe93ffff memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD/ATI]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:22:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:238 memory:fe960000-fe963fff
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:fe300000-fe5fffff
           *-generic:0 UNCLAIMED
                description: Non-Essential Instrumentation
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:23:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
           *-generic:1
                description: Encryption controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:23:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: driver=ccp latency=0
                resources: irq:234 memory:fe400000-fe4fffff memory:fe500000-fe501fff
           *-usb
                description: USB controller
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:23:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:227 memory:fe300000-fe3fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.10.0-21-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.10
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb
                      description: Audio device
                      product: Turtle Beach PLa Headset
                      vendor: Turtle Beach
                      physical id: 3
                      bus info: usb@3:3
                      version: 1.00
                      serial: [REMOVED]
                      capabilities: usb-2.00 audio-control
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.10.0-21-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.10
                   capabilities: usb-3.00
                   configuration: driver=hub slots=4 speed=5000Mbit/s
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:217 memory:fe800000-fe8fffff
           *-generic UNCLAIMED
                description: Non-Essential Instrumentation
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:24:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
           *-storage
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:24:00.2
                version: 51
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msi ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:231 memory:fe808000-fe808fff
           *-multimedia
                description: Audio device
                product: Advanced Micro Devices, Inc. [AMD]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:24:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:240 memory:fe800000-fe807fff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 59
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:04.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:07.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10b
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10c
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10d
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10e
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK5076GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1C
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=8a36d69f
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-05-23 19:01:50 filesystem=ext4 lastmountpoint=/ modified=2017-05-25 19:34:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-05-25 18:44:38 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000AAKX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 1H19
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=ec5831d6-7d3c-bd43-b652-bba74eb1c07e logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                serial: [REMOVED]
                capacity: 465GiB
                configuration: name=zfs-8ee7bc95a154a56b
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@1:0.0.0,9
                logical name: /dev/sdb9
                serial: [REMOVED]
                capacity: 8191KiB
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10JPVX-75J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: 1A01
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=ba918e00-84a9-434a-a767-899ab2337d19 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                serial: [REMOVED]
                capacity: 931GiB
                configuration: name=zfs-915a08a33700acf4
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@4:0.0.0,9
                logical name: /dev/sdc9
                serial: [REMOVED]
                capacity: 8191KiB
     *-scsi:3
          physical id: 4
          logical name: scsi5
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000BPKT-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdd
             version: 1A01
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=e40a8839-7cc2-c047-bb37-b266964a6773 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdd1
                serial: [REMOVED]
                capacity: 465GiB
                configuration: name=zfs-6dc4e0ade2e0258d
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@5:0.0.0,9
                logical name: /dev/sdd9
                serial: [REMOVED]
                capacity: 8191KiB
     *-scsi:4
          physical id: 5
          logical name: scsi10
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS545050A7
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sde
             version: AH10
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7e2f6f4b-51c3-db4e-a1ac-e967506a84f4 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: OS X ZFS partition or Solaris /usr partition
                vendor: Solaris
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sde1
                serial: [REMOVED]
                capacity: 465GiB
                configuration: name=zfs-3e189e4c1e66d515
           *-volume:1
                description: reserved partition
                vendor: Solaris
                physical id: 9
                bus info: scsi@10:0.0.0,9
                logical name: /dev/sde9
                serial: [REMOVED]
                capacity: 8191KiB
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp3s0f0u3
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=[REMOVED] link=yes multicast=yes
```

---

### Post by mörgæs on 2017-05-26
The hardware is about as new as it gets and I can't help you much here, sorry. My experience is mostly within old gear.

Maybe some others can get an idea from reading your lshw. 

It would be interesting to try how 17.10 behaves in a live boot. It's probably too young to install but just to see if there is any improvement coming up. If this one also freezes the developers would appreciate a bug report.

---


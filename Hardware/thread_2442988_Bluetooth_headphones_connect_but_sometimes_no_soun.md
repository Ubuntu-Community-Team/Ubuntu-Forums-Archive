---
title: "Bluetooth headphones connect but sometimes no sound"
date: 2020-05-10
forum: Hardware
---

### Post by folivorax on 2020-05-10
I am trying to use sony WH-1000xm3 headphones with kubuntu laptop (previously 19.04, now 20.04).

The laptop will see the headphones, in fact there are two entries showing: WH-1000XM3 and LE_WH-1000XM3, with different addresses. Connecting threw (say) blueman to the latter works, but not to the former.

However, when connecting it is not recognized as an audio output (e.g. pavucontrol dos not show an output stream for that).  It does show the device as paired.
I tried various options in blueman, and upgraded to 20.04 since there was a claim that newer version of bluez have some bug fixes (20.04 includes bluez 5.53). Nothing seemed to help, though just now, after at least 5 attempts as  before, it connected and is playing audio (albeit at a very low volume,  that I cannot seem to amplify).

Headphones are working with no issue with other devices, including linux computers, and the laptop is connecting with no issue to a different bluetooth speaker I have, so just this pair is giving me trouble. It is possible that the problem is broader, and this laptop-headphones pair is the one I tried the most, so mayby I only noticed that.

This is being used for work, so connecting 10 times until it eventually works is not practical, in addition to being silly.  Only other suggestions I found from searching was newer bluez versions. Perhaps I missed something? 

Any help would be much appreciated.

---

### Post by mIk3_08 on 2020-05-10
Please run this command:
```
sudo lshw
```
and 
```
lsusb
```
Paste the result here.

Please use Code tags for the terminal output.

---

### Post by folivorax on 2020-05-11
Here are lsusb and lshw outputs. 

```

 % lsusb 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0bda:0328 Realtek Semiconductor Corp. USB3.0-CRW
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 06cb:009a Synaptics, Inc. 
Bus 001 Device 006: ID 13d3:56b2 IMC Networks Integrated Camera
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 045e:07b2 Microsoft Corp. 2.4GHz Transceiver v8.0 used by mouse Wireless Desktop 900
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshw output (long):

```

    description: Notebook
    product: 20KHCTO1WW (LENOVO_MT_20KH_BU_Think_FM_ThinkPad X1 Carbon 6th)
    vendor: LENOVO
    version: ThinkPad X1 Carbon 6th
    serial: PF1PAA91
    width: 64 bits
    capabilities: smbios-3.0.0 dmi-3.0.0 smp vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad X1 Carbon 6th power-on_password=disabled sku=LENOVO_MT_20KH_BU_Think_FM_ThinkPad X1 Carbon 6th uuid=CC5FC76E-1D22-B211-A85C-9263688AE66F
  *-core
       description: Motherboard
       product: 20KHCTO1WW
       vendor: LENOVO
       physical id: 0
       version: SDK0J40709 WIN
       serial: L1HF94P031E
       slot: Not Available
     *-memory
          description: System Memory
          physical id: 3
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: H9CCNNNCLGALAR-NVD
             vendor: SK Hynix
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: Row of chips LPDDR3 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
             product: H9CCNNNCLGALAR-NVD
             vendor: SK Hynix
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
     *-cache:0
          description: L1 cache
          physical id: 7
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 8
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 9
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: a
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
          serial: None
          slot: U3E1
          size: 2013MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: b
          version: N23ET62W (1.37 )
          date: 02/19/2019
          size: 128KiB
          capacity: 16MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification uefi
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: UHD Graphics 620
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             logical name: /dev/fb0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
             configuration: depth=32 driver=i915 latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
             resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:149 memory:2ffa000000-2ffaffffff memory:2fa0000000-2fafffffff ioport:e000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 08
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: iomemory:2f0-2ef irq:16 memory:2ffb020000-2ffb027fff
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: latency=0
             resources: iomemory:2f0-2ef memory:2ffb02f000-2ffb02ffff
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
             resources: iomemory:2f0-2ef irq:129 memory:2ffb010000-2ffb01ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-29-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: Microsoft
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 7.04
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.10
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Video
                   product: Integrated Camera
                   vendor: SunplusIT Inc
                   physical id: 8
                   bus info: usb@1:8
                   version: 17.11
                   capabilities: usb-2.01
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:3 UNCLAIMED
                   description: Generic USB device
                   vendor: Synaptics, Inc.
                   physical id: 9
                   bus info: usb@1:9
                   version: 1.64
                   serial: d7afa40744df
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-29-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
              *-usb
                   description: Mass storage device
                   product: USB3.0-CRW
                   vendor: Generic
                   physical id: 3
                   bus info: usb@2:3
                   logical name: scsi0
                   version: 29.08
                   serial: 28203008282014000
                   capabilities: usb-3.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=800mA speed=5000Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: SD/MMC CRW
                      vendor: Generic-
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 1.00
                      serial: 2012062914345300
                      capabilities: removable
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sda
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
             resources: iomemory:2f0-2ef irq:18 memory:2ffb02e000-2ffb02efff
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
             resources: iomemory:2f0-2ef irq:147 memory:2ffb02d000-2ffb02dfff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 memory:ee200000-ee2fffff
           *-network
                description: Wireless interface
                product: Wireless 8265 / 8275
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 78
                serial: 48:89:e7:30:56:ce
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-29-generic firmware=36.77d01142.0 ip=10.0.0.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:159 memory:ee200000-ee201fff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:ee100000-ee1fffff
           *-storage
                description: Non-Volatile memory controller
                product: Lenovo
                vendor: Lenovo
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:ee100000-ee103fff
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
             resources: irq:124 ioport:2000(size=12288) memory:c0000000-ee0fffff ioport:2fb0000000(size=1241513984)
           *-pci
                description: PCI bridge
                product: JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:16 ioport:2000(size=8192) memory:c0000000-ee0fffff ioport:2fb0000000(size=1241513984)
              *-pci:0
                   description: PCI bridge
                   product: JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:06:00.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:125 memory:ee000000-ee0fffff
                 *-generic
                      description: System peripheral
                      product: JHL6540 Thunderbolt 3 NHI (C step) [Alpine Ridge 4C 2016]
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:07:00.0
                      version: 02
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress msix bus_master cap_list
                      configuration: driver=thunderbolt latency=0
                      resources: irq:16 memory:ee000000-ee03ffff memory:ee040000-ee040fff
              *-pci:1
                   description: PCI bridge
                   product: JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:06:01.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:126 ioport:2000(size=4096) memory:c0000000-d7efffff ioport:2fb0000000(size=536870912)
              *-pci:2
                   description: PCI bridge
                   product: JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
                   vendor: Intel Corporation
                   physical id: 2
                   bus info: pci@0000:06:02.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:127 memory:d7f00000-d7ffffff
                 *-usb
                      description: USB controller
                      product: JHL6540 Thunderbolt 3 USB Controller (C step) [Alpine Ridge 4C 2016]
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:3b:00.0
                      version: 02
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pm msi pciexpress xhci cap_list
                      configuration: driver=xhci_hcd latency=0
                      resources: irq:130 memory:d7f00000-d7f0ffff
                    *-usbhost:0
                         product: xHCI Host Controller
                         vendor: Linux 5.4.0-29-generic xhci-hcd
                         physical id: 0
                         bus info: usb@3
                         logical name: usb3
                         version: 5.04
                         capabilities: usb-2.00
                         configuration: driver=hub slots=2 speed=480Mbit/s
                    *-usbhost:1
                         product: xHCI Host Controller
                         vendor: Linux 5.4.0-29-generic xhci-hcd
                         physical id: 1
                         bus info: usb@4
                         logical name: usb4
                         version: 5.04
                         capabilities: usb-3.10
                         configuration: driver=hub slots=2 speed=10000Mbit/s
              *-pci:3
                   description: PCI bridge
                   product: JHL6540 Thunderbolt 3 Bridge (C step) [Alpine Ridge 4C 2016]
                   vendor: Intel Corporation
                   physical id: 4
                   bus info: pci@0000:06:04.0
                   version: 02
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:128 ioport:3000(size=4096) memory:d8000000-edffffff ioport:2fd0000000(size=704643072)
        *-isa
             description: ISA bridge
             product: Sunrise Point LPC Controller/eSPI Controller
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
             configuration: latency=0
             resources: memory:ee320000-ee323fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:158 memory:2ffb028000-2ffb02bfff memory:2ffb000000-2ffb00ffff
        *-serial
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: iomemory:2f0-2ef irq:16 memory:2ffb02c000-2ffb02c0ff ioport:efa0(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (4) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 21
             serial: e8:6a:64:fb:56:76
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:160 memory:ee300000-ee31ffff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 0
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0b00
          physical id: 5
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:05
          product: PnP device INT3f0d
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device LEN0071
          physical id: c
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:07
          product: PnP device LEN0091
          physical id: d
          capabilities: pnp
          configuration: driver=i8042 aux
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: e
          capabilities: pnp
          configuration: driver=system
     *-pnp00:09
          product: PnP device PNP0c02
          physical id: f
          capabilities: pnp
          configuration: driver=system
     *-pnp00:0a
          product: PnP device PNP0c02
          physical id: 10
          capabilities: pnp
          configuration: driver=system
     *-pnp00:0b
          product: PnP device PNP0c01
          physical id: 11
          capabilities: pnp
          configuration: driver=system
  *-battery
       product: 01AV494
       vendor: LGC
       physical id: 1
       slot: Front
       capacity: 57000mWh
       configuration: voltage=11.6V

```

---

### Post by mIk3_08 on 2020-05-12
Try to connect via command "bluetoothctl"


```

bluetoothctl 
power on 
scan on
discoverable on 
pair 
trust

```


pair using the device mac address: 
ex. 
```

pair aa:bb:cc:....

```

when successfully connected be sure to "disable/turn-off" the visibility of your systems Bluetooth and have a lock on Bluetooth icon; 
See image below:
     [ATTACH=CONFIG]285836[/ATTACH]

         [ATTACH=CONFIG]285837[/ATTACH]

---

### Post by folivorax on 2020-05-13
Thanks. I've been using bluetoothctl in the past as well. When the issue persisted, it would not connect either. It is working at the moment, and of course eliminating non-consistent bugs is harder.  I will post back here if/when the problem returns.

I use blueman applet on kde, and do not have the lock option (what does that do?) nor is there a discoverable switch. What applet is in your images?

---

### Post by mIk3_08 on 2020-05-13
Its a secure Bluetooth device connection I think, on Ubuntu 18.04 lts unity desktop. It only appears when you have successfully connected to the device. I also have blueman applet installed.

---

### Post by chrisgibbons on 2020-05-15
i have same problem. takes a while to connect, then it will disconect. when connected there is no sound and youtube video stalls. this is the same for my laptop and desktop computer. all worked ok with 18.04

---

### Post by mIk3_08 on 2020-05-16
> **chrisgibbons said:**
> i have same problem. takes a while to connect, then it will disconect. when connected there is no sound and youtube video stalls. this is the same for my laptop and desktop computer. all worked ok with 18.04

Hi [COLOR=#000000]chrisgibbons
[/COLOR]Please run the following command on terminal and paste the result here and wrap it;
```
sudo lshw
```
```
lsusb
```

---

### Post by folivorax on 2020-05-26
Since the above discussions, the headphones have been connecting to my laptop, but the laptop does not seem to recognize the headphones microphone.
It had worked at some time in the past, but not recently.

Any idea how to get a laptop to recognize the mic in the headphones?

---


---
title: "Backlight control not working in kubuntu 12.04"
date: 2013-03-19
forum: Hardware
---

### Post by tomane on 2013-03-19
Hi all.

I have a Toshiba A300-202 laptop. With older installations of kubuntu I hadd full control over the backlight. After a clean instalation of kubuntu 12.04.1 the backlight control stopped working.
The desktop responds to the brightness Fn-keys but there's no response from the display.

Here's the output of lshw
```

WARNING: you should run this program as super-user.
tinta-roriz               
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3953MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 1                                                                                                                                                                                       
          bus info: cpu@0                                                                                                                                                                                      
          size: 2667MHz
          capacity: 2667MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:d6300000-d63fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV635 [Mobility Radeon HD 3650]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:46 memory:c0000000-cfffffff ioport:5000(size=256) memory:d6300000-d630ffff memory:d6320000-d633ffff
           *-multimedia
                description: Audio device
                product: RV635 HDMI Audio [Radeon HD 3600 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:49 memory:d6310000-d6313fff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60e0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:60c0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:d6405c00-d6405fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:d6400000-d6403fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=8192) memory:d5300000-d62fffff ioport:d0000000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:90:eb:df
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=10.112.40.121 latency=0 multicast=yes port=MII speed=100Mbit/s
                resources: irq:45 ioport:3000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:d4200000-d52fffff ioport:d1100000(size=16777216)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:fa:18:fb:24
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-38-generic firmware=8.83.5.1 build 33692 ip=172.22.1.154 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:d4200000-d4201fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:1000(size=4096) memory:d3200000-d41fffff ioport:d2100000(size=16777216)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:60a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6080(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:6060(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6040(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d6405800-d6405bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d3100000-d31fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:17 memory:d3100000-d31007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:04:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:17 memory:d3100b00-d3100bff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:04:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:17 memory:d3100900-d31009ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:04:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:17 memory:d3100800-d31008ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:6108(size=8) ioport:6114(size=4) ioport:6100(size=8) ioport:6110(size=4) ioport:6020(size=32) memory:d6405000-d64057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6406000-d64060ff ioport:6000(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

Unfortunately, display brightness is permanently set to the maximum, which is extremelly uncomfortable.
Does anyone has a hint on how to fix this up?
Thanks!

---

### Post by Bashing-om on 2013-03-19
tomane; Hi !

This solution is directed to the Acer products, but may prove of value in your situation. Worth a try.
The boot parameters :"acpi_osi=Linux acpi_backlight=vendor".
Try these in grub's booting. If it works in that instance then commit the changes in /etc/default/grub config file.[INDENT=2]
hope this helps

[/INDENT]

---

### Post by tomane on 2013-03-19
( weird-o, some post just got removed, but its contents weren't all that useful either... 0.o)

Bashing-om, thanks for your hint. I think I already tried some boot param trick before but I'm pretty sure that is was different from your suggestion. I'll give it a try and see how it goes.

Cheers,

---

### Post by tomane on 2013-03-19
I just checked and actually I already had tried the **acpi_backlight=vendor** portion. 

Adding the **acpi_osi=Linux** caused the Fn-keys not to be recognized anymore. However, trying to change backlight intensity using the GUI (using the mouse and system settings) still yelded no effect.

Then, just for kicks, I decided to try **acpi_osi=Windows***. *Fn-keys are recognized (including BL control), but there's no change in actual display brightness.

Either the backlight is not controlled by ACPI (maybe the GFX card is in charge of this??) or somehow the desktop reacts to keys but doesn't notify the bios/acpi/whatever about the command.

Does anyone know some trick for laptops using Radeon cards or Toshiba laptops?

Thanks...

---


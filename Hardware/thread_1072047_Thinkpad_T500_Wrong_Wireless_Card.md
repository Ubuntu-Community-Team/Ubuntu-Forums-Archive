---
title: "Thinkpad T500 Wrong Wireless Card"
date: 2009-02-17
forum: Hardware
---

### Post by Squid Spectre on 2009-02-17
I just got my new T500 from Lenovo and was browsing through some system information when I found something unsettling. It would seem Ubuntu sees an Intel 5100 AGN wireless card rather than the 5300 AGN I paid for. Check out the terminal output below.

```
sudo lshw                  
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3017MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 2534MHz
          capacity: 2534MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
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
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3650
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: Mobile 4 Series Chipset MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-ide UNCLAIMED
             description: IDE interface
             product: Mobile 4 Series Chipset PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: ide cap_list
             configuration: latency=0
        *-communication:1
             description: Serial controller
             product: Mobile 4 Series Chipset AMT SOL Redirection
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 07
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=serial latency=0
        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:21:86:a2:02:2e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 module=e1000e multicast=yes
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
              [B]  description: Wireless interface
                product: Wireless WiFi Link 5100[/B]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:6a:12:a5:a0
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.126 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b01716150-b0171614f
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=32 module=sdhci_pci
           *-generic
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0.3
                bus info: pci@0000:15:00.3
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255 module=ricoh_mmc
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:15:00.4
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.5
                bus info: pci@0000:15:00.5
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
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
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
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

```

The way I see its one of two very likely things. The first is that Lenovo sent me the wrong card and charged me for the right one, I've heard of this happening a lot. The other is that the two wireless cards are so much a like Ubuntu simply can't distinguish between the two. It is my understanding the two cards are nearly identical with the exception of the antenna array, where the 5100 only has a 1x2 input/output array ad the 5300 has a 3x3 respectively.

 Any input from other Intel 5300 AGN owners?

EDIT:
Forgot to mention, (but I suspect some people will be able to see in the code above) I'm running 32-bit 8.10 with the 2.6.27-11-generic kernel.

---

### Post by Squid Spectre on 2009-02-17
Bump. Any other thinkpad owner's have anything similar?

---

### Post by Squid Spectre on 2009-02-18
Last bump before I give up. Upon further, and much more troubling, investigation is looks like they put DDR2 memory in place of the DDR3 I payed for, or at the very least its being bottlenecked and throttled down by a system that should be DDR3 optimized. I even get the clocked down speed in memtest. I tried to lookup the what the motherboard bus speed should be but Lenovo hasn't made it easy to find.

Why on earth would they force you to put DDR3 memory on a DDR2 board?

I'm beginning to suspect its not the hardware, Lenovo may not be the most *accurate* vendor when it comes to putting computers together but this just seems like too much. Rather I think the software here simply isn't seeing something correctly. Can someone else wit ha T500/400 or recent thinkpad post their output for lshw?

EDIT:
Did some digging, it is a hardware issue according to this article/posts
      [http://www.thinkpadtoday.com/lenovo-thinkpad-t400-%E2%80%93-t500-a-quick-review.htm](http://www.thinkpadtoday.com/lenovo-thinkpad-t400-%E2%80%93-t500-a-quick-review.htm)
      [http://forums.lenovo.com/lnv/board/message?board.id=T400_series_ThinkPads&message.id=7911](http://forums.lenovo.com/lnv/board/message?board.id=T400_series_ThinkPads&message.id=7911)
It the motherboard on this machine uses a 201 pin socket, making it impossible to use anything but DDR3 RAM. That said I have solved nothing, from what I gather the motherbaord itself reports the speed of the memory wrong but (maybe?) runs at DDR3 speeds. 

Still doesn't address the wireless card though, I still believe it could be that since the 5300 has issues in the current linux kernel it could be subject to a generalization of the driver. Or they just sent me the wrong card :(

---


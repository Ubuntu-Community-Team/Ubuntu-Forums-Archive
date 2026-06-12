---
title: "Acer Aspire 5601AWLMi Hardware Problems"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by quail-linux on 2006-10-29
Hi all,

As i am an owner of an Acer Aspire 5601AWLMi, and had to work my way through some of the hardware problems with it.

Here is a wiki page i have put together to help others with the same laptop to fix some of the problems.
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo)

Enjoy
Dale

---

### Post by quail-linux on 2006-11-07
> **quail-linux said:**
> Hi all,

As i am an owner of an Acer Aspire 5601AWLMi, and had to work my way through some of the hardware problems with it.

Here is a wiki page i have put together to help others with the same laptop to fix some of the problems.
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo)

Enjoy
Dale

Added to the howto page, how to get the 5 in 1 card reader working under Edgy to read SD media cards.

---

### Post by Carlos Santiago on 2007-07-01
Hi.

I own a Acer Travelmate 4150 and I still cannot work with 2 devices, namely Infrared and MMC/SD memory card reader.

I would love to know if you could help me on those. For hardware details plz see below the lshw and lspci.

For the infrared I have installed irda-utils but I still cannot connect to the device. And now I don't have the minimum idea of what to do next. If you could help me on that I would be very appreciated because is the only way I have to connect to my mobile phone.

For the card reader, I followed your instructions in [http://ubuntuforums.org/showthread.php?t=200360&page=3](http://ubuntuforums.org/showthread.php?t=200360&page=3) and after the command:
```
sudo update-pciids
```
my card reader shows on lspci. It wasn't there before that command.
```

01:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

But I still cannot mount it. However I only test it with a 1GB SD card.
In the /dev/sd* only the partitions of my hard drive (dev/sda) are shown

Following the 'ls -1 /dev/sd*'
```
$ ls -1 /dev/sd*
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5
/dev/sda6

```

and 'lspci'
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
01:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

and 'lshw'
```
qu
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1003MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 798MHz
          capacity: 798MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0000000-d007ffff ioport:e000-e007 iomemory:a0000000-afffffff iomemory:d0080000-d00bffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:d0100000-d017ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1200-121f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1220-123f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1240-125f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1260-127f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-lowlatency uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:40000000-400003ff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=2
                resources: iomemory:c0004000-c00047ff iomemory:c0008000-c000bfff irq:17
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@01:01.0
                logical name: eth1
                version: 02
                serial: 00:0f:b0:7e:93:72
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=1.01 latency=128 multicast=yes
                resources: iomemory:c0002000-c0003fff irq:21
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@01:02.0
                logical name: eth0
                version: 05
                serial: 00:12:f0:6e:58:19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
                resources: iomemory:c0001000-c0001fff irq:23
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@01:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:c0005000-c0005fff irq:16
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@01:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=128 maxlatency=4 mingnt=1
                resources: iomemory:c0000000-c000007f irq:5
           *-system
                description: Generic system peripheral
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@01:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=128 maxlatency=72 mingnt=32
                resources: iomemory:c0000100-c00001ff irq:22
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@01:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=128 maxlatency=4 mingnt=1
                resources: iomemory:c0000200-c000027f irq:5
           *-memory:2 UNCLAIMED
                description: FLASH memory
                product: ENE Technology Inc
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@01:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=72 mingnt=32
                resources: iomemory:c0000300-c00003ff irq:255
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:e100-e1ff ioport:e200-e23f iomemory:d00c0000-d00c01ff iomemory:d00c0200-d00c02ff irq:22
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:e300-e3ff ioport:e400-e47f irq:17
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1100-110f irq:19
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1400-141f irq:11

```


Thank you very much for any help

---


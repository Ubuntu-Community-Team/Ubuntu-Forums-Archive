---
title: "internal SD card not configured.."
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by eitan_a on 2006-12-27
Hey guys, I installed Ubuntu 6.10 today on a new Sony Vaio and everything is working okay except the internal SD card reader.  In winxp, the internal reader works fine but in linux I need to use my USB SD reader since the internal one does nothing.  With some help, I found where the reader was in ubuntu's device manager but I don't know where to go from there.  It says it's accessing it through a PCI interface and I read somewhere that to make these work you need to change it to a USB interface.  I'm new at this, but learning.  Any help will be mucho appreciated.  Thanks!

---

### Post by eitan_a on 2006-12-29
Bump..still not resolved and I'm not good enough at linux to figure it out myself, so help would be much appreciated.

---

### Post by rdxdude on 2006-12-29
yeah any help would be awesome i have the same problem

---

### Post by bascuppen on 2006-12-29
So, I plugged in my SD card in my (internal) card reader on my Acer Aspire 5024 wmli and *'it dit not work'* Hate it when that happens.

I opened up a console (aka terminal) and a quick ```
bascuppen@Hex:~$ dmesg | less
``` learned me that:
```
[17234955.300000] tifm_7xx1: sd card detected in socket 3
```.
After that I just 'knew' I had to:
(ok, ok I admit, I had help)
```

bascuppen@Hex:~$ sudo modprobe tifm_core
bascuppen@Hex:~$ sudo modprobe tifm_sd

```
And [COLOR="Red"]*pling*[/COLOR] ubuntu comes with the message: A new photo card has been found! Life is sweet. I figure if I want to make this permanent, I'll have to add those modules to /etc/modules. Might be I have to read a man page even, to be able to do that. And google might come in handy too.

Thanks to js, for helping me with the knowing. ([http://kanotix.com/PNphpBB2-viewtopic-t-22959.html]("http://kanotix.com/PNphpBB2-viewtopic-t-22959.html"))

Of course, if your 'dmesg | less'  doesn't come up with a line containing 'sd card' (while viewing something with less you can search with the '/'-key) or if there's no mention of 'tifm_7xx1', this solution might not be the right one for you. In that case, repost your question, with a detailed account of the things you have tried to find out more about your device. (dmesg and lspci are good tools to start with. They both have man-pages which both can be read by typing 'man dmesg' or 'man lspci' in a terminal.

If this post seams a bit frivolous to you, my apologies. Don't take it personal :p

---

### Post by eitan_a on 2006-12-29
I've done a dmesg (it doesn't show anything about sd cards), i've done those modprobes...and it still doesn't read my sd card.

---

### Post by njee on 2006-12-30
not very helpful but I think a lot of people have problems with the internal SD cards, to my knowledge I dont think anyone has been able to get internal ones to work, especially on my laptop.

---

### Post by eitan_a on 2006-12-30
Thanks for your help guys.  Here is more information!  First, the laptop is a Sony Vaio VGN-N130G, ubuntu edgy 6.10 installed.

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 13)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:03.0 CardBus bridge: Texas Instruments Unknown device 8039
08:03.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:03.2 Mass storage controller: Texas Instruments Unknown device 803b

lshw

    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1002MB
     *-cpu:0
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-cpu:1
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:dc100000-dc17ffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:dc200000-dc23ffff irq:177
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dc180000-dc1fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dc240000-dc243fff irq:58
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8036 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 13
                serial: 00:13:a9:7f:98:b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 multicast=yes
                resources: iomemory:d6000000-d6003fff ioport:2000-20ff irq:50
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                logical name: eth1
                version: 02
                serial: 00:18:de:8e:9d:fa
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 ip=192.168.0.3 multicast=yes wireless=IEEE 802.11b
                resources: iomemory:da000000-da000fff irq:185
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:dc444000-dc4443ff irq:233
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@08:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:dc006000-dc006fff irq:177
           *-firewire
                description: FireWire (IEEE 1394)
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3.1
                bus info: pci@08:03.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:dc005000-dc0057ff iomemory:dc000000-dc003fff irq:177
           *-storage
                description: Mass storage controller
                product: Texas Instruments
                vendor: Texas Instruments
                physical id: 3.2
                bus info: pci@08:03.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1
                resources: iomemory:dc004000-dc004fff irq:185
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f irq:185
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   product: PIONEER DVD-RW DVR-K16D
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capabilities: packet
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix
             resources: ioport:18b0-18b7 ioport:18a4-18a7 ioport:18a8-18af ioport:18a0-18a3 ioport:1890-189f iomemory:dc444400-dc4447ff irq:225
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:18c0-18df irq:10

Finally, dmesg.. (last few lines)

[17182446.556000] end_request: I/O error, dev mmcblk0, sector 4019192
[17182446.556000] Buffer I/O error on device mmcblk0, logical block 502399
[17182446.556000] mmcblk0: error 4 sending stop command
[17182446.556000] end_request: I/O error, dev mmcblk0, sector 4019192
[17182446.556000] Buffer I/O error on device mmcblk0, logical block 502399
[17182446.564000] mmcblk0: error 4 sending stop command
[17182446.564000] end_request: I/O error, dev mmcblk0, sector 4019192
[17182446.568000] mmcblk0: error 4 sending stop command
[17182446.568000] end_request: I/O error, dev mmcblk0, sector 4019192

NEWS!  It works!  I put my card in just now and it read it!  I don't know why it wasn't working yesterday...perhaps I needed a long reboot?  Well it's reading the card, the 1 gb is super fast but the 2 gb is a bit slow.  Maybe you can help with those errors?  Thanks much again!

---

### Post by golem3 on 2007-01-25
Thanks, people. Once again, you have saved the day.

---


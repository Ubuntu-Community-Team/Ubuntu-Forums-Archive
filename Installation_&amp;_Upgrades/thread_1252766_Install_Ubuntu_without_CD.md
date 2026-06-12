---
title: "Install Ubuntu without CD?"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Jordii on 2009-08-29
I just installed Ubuntu with wubi just from my destkop, so without any cd. It seems to work, no internet connection (but I never had with ubuntu:confused: can't get it to work)
Will this give me problems?

---

### Post by konqueror7 on 2009-08-29
no problems will occur because of your installation via wubi, so nothing to worry. and welcome to the forums!:P

---

### Post by Jordii on 2009-08-29
Thanks :p hopefully I will find out soon how to make Ubuntu automatically search for my wireless network, because it doesn't.

---

### Post by Bölvaður on 2009-08-29
well having no internet on a desktop linux distro is unbarable in my opinion, but I guess you are talking about wireless internet so you can always just plug your lan cable in.

the only restrictions of using wubi is that it is in a file on your windows partition. which means that you cannot format it or anything, and if it is very fragmented you'll experience sluggishness in ubuntu, as well as you are not reaping the benefits of having a proper filesystem like EXT4 on the partition you are running ubuntu off.

other than that there shouldnt be any problems.
there is even a way to copy the wubi virtual partition from your windows partition and make a copy of it on the hard disk drive, so it will become like a normal install.
I think that is only possible with the latest version of wubi or something, will be on the ubuntu koala 9.10 disk

---

### Post by Bölvaður on 2009-08-29
> **Jordii said:**
> Thanks :p hopefully I will find out soon how to make Ubuntu automatically search for my wireless network, because it doesn't.

search for your wireless with this command

(applications &#8594; accessories &#8594; terminal)
```
lshw
```

google the name of the card and include either linux or ubuntu in the search. It should give you a how-to to get it to work

---

### Post by Jordii on 2009-08-29
Thank you! I'm not sure where I can find the card in the code..:
ubuntu 
description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 502MiB
*-cpu
product: Intel(R) Celeron(R) M CPU 410 @ 1.46GHz
vendor: Intel Corp.
physical id: 1
bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
version: 6.14.8
serial: 0000-06E8-0000-0000-0000-0000
size: 150MHz
width: 32 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts pni monitor tm2 xtpr pdcm
*-pci
description: Host bridge
product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 03
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-intel module=intel_agp
*-display:0 UNCLAIMED
description: VGA compatible controller
product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
*-multimedia
description: Audio device
product: 82801G (ICH7 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
*-pci:0
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:16:36:8c:35:34
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
*-pci:1
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-pci:2
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 3
vendor: Intel Corporation
physical id: 1c.2
bus info: pci@0000:00:1c.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-pci:3
description: PCI bridge
product: 82801G (ICH7 Family) PCI Express Port 4
vendor: Intel Corporation
physical id: 1c.3
bus info: pci@0000:00:1c.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
configuration: driver=pcieport-driver
*-usb:0
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:1
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #2
vendor: Intel Corporation
physical id: 1d.1
bus info: pci@0000:00:1d.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:2
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:3
description: USB Controller
product: 82801G (ICH7 Family) USB UHCI Controller #4
vendor: Intel Corporation
physical id: 1d.3
bus info: pci@0000:00:1d.3
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:4
description: USB Controller
product: 82801G (ICH7 Family) USB2 EHCI Controller
vendor: Intel Corporation
physical id: 1d.7
bus info: pci@0000:00:1d.7
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ehci_hcd latency=0 module=ehci_hcd
*-pci:4
description: PCI bridge
product: 82801 Mobile PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: e2
width: 32 bits
clock: 33MHz
capabilities: pci bus_master cap_list
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:0a:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=96 module=ssb
*-pcmcia
description: CardBus bridge
product: PCIxx12 Cardbus Controller
vendor: Texas Instruments
physical id: 9
bus info: pci@0000:0a:09.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
*-storage
description: Mass storage controller
product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
vendor: Texas Instruments
physical id: 9.2
bus info: pci@0000:0a:09.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: storage bus_master cap_list
configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1
*-isa
description: ISA bridge
product: 82801GBM (ICH7-M) LPC Interface Bridge
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: latency=0
*-ide
description: IDE interface
product: 82801G (ICH7 Family) IDE Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=ata_piix latency=0
*-serial UNCLAIMED
description: SMBus
product: 82801G (ICH7 Family) SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:16:cf:7a:3a:b9
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: e6:78:2f:1b:20:bd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Bölvaður on 2009-08-29
I think I found it -.- pretty obvious
> **Jordii said:**
> 
*-network:0 DISABLED
description: **Wireless interface**
physical id: 1
logical name: wlan0
serial: 00:16:cf:7a:3a:b9
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: e6:78:2f:1b:20:bd
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I'd guess you have a switch to power on and off the wifi card. At the moment I would guess it is off, so finding the switch or button is vital in your quest for internet access.

when it is on try connect again, if it doesnt work then try see if **-network:1 DISABLED* will change into *ENABLED* and what vendor it is from and chip this is.

---


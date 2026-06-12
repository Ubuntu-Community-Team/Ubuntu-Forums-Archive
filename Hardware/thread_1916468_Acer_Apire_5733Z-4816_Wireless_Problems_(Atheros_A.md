---
title: "Acer Apire 5733Z-4816 Wireless Problems (Atheros AR5B125)"
date: 2012-01-28
forum: Hardware
---

### Post by fgbfx on 2012-01-28
Hello! I received a new laptop ~2 days ago and, as always, decided to get 10.04 LTS installed. Everything went find, except screen brightness adjustments and the wireless access. Some simple googling got me a solution to adjusting screen brightness, but having followed almost every guide to getting Atheros cards to work has gotten me nowhere.

The thing I find most interesting is most people are having stability or detection of network issues (something I thought I'd had), however I can't get the card to work at all. It's like we're not even aware it exists. It's not listed in my connections (both in terminal and obviously in the system control panels). My wired connection functions perfectly, and my wireless works fine in Win 7 (which came on the laptop), I've tried using the keyboard switches (Fn+F3) to see if they'll turn the wireless on/off, but it seems to have 0 effect.

I'll be happy to provide any info, or screen shots requested.

---

### Post by fgbfx on 2012-01-29
ran lshw -C network, just because, and found my devices listed but 'unclaimed'

```

  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: dc:0e:a1:1d:3a:a3
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 memory:d3400000-d340ffff
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2400000-d247ffff memory:d1400000-d140ffff(prefetchable)

```

some googling leads to the answer "reinstall ubuntu and try this random driver". I'd like another opinion before going through with that, obviously.

---

### Post by fgbfx on 2012-01-29
I've also gone ahead and run lspci

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. Device 0032 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

I'm also doing a full kernal update to 11.10 just to see if the new kernals detect the hardware or have drivers for it.

---

### Post by fgbfx on 2012-01-29
Tore ubuntu out entirely, after nsdwrapper and a complete kernal update is nothing to help. Reinstalled using 11.10 disc, and suddenly, FM, it works. Leaving this thread as unsolved for the moment, because I have no idea what the problem was in the first place.

---


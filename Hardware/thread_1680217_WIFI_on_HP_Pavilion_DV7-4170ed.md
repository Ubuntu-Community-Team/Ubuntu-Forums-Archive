---
title: "WIFI on HP Pavilion DV7-4170ed"
date: 2011-02-02
forum: Hardware
---

### Post by mhogendoorn on 2011-02-02
Who can pls help me getting the WIFI working on a HP Pavilion DV7-4170ed ?
-------
* Clicking on the network manager applet give "device not ready"
-------
* System -> Admin -> Hardware drivers gives nothing related
-------
* lshw -C network  returns:
description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
*-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:3000(size=4096) memory:c3400000-c43fffff ioport:c0400000(size=16777216)
           *-network DISABLED
                description: Wireless interface
                product: RT3090 Wireless 802.11n 1T/1R PCIe
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
                resources: irq:16 memory:c3400000-c340ffff

-------
* iwconfig returns:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

usb0      no wireless extensions.

pan0      no wireless extensions.

-------
* rfkill list gives:
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
-------

what to do ?  How can i get this WIFI working ? 
It runs on Ubuntu 10.04 64bits... (is that a wise choice?)
THANKS !
Maarten

---


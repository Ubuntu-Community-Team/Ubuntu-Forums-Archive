---
title: "ipw2100 is off for an unknown reason"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by seaking69 on 2007-01-06
hey,
working on edgy... toshiba T, m2

i have a ipw2100 wifi but suddenly its not working (it worked a few days ago)

when "network-admin"
its not mentioning the card (eth1)

when iwconfig its not mentioned as well

dmesg output is:

> [17179593.472000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17179593.936000] ipw2100: eth1: ipw2100_verify failed: -5
[17179593.936000] ipw2100: eth1: Failed to power on the adapter.
[17179593.936000] ipw2100: eth1: Failed to start the firmware.
[17179593.936000] ipw2100Error calling register_netdev.
[17179593.936000] ACPI: PCI interrupt for device 0000:02:05.0 disabled


lshw -C network:

> 
 *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@02:05.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:fcefd000-fcefdfff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:2c:60:06
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.2.50 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:fcefc000-fcefcfff ioport:cf40-cf7f irq:11



yet the eth0 is the wierd one?! (i dono if this is the problem)

lspci -v:
> 
02:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Unknown device 2581
        Flags: medium devsel, IRQ 11
        Memory at fcefd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at fcefc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at cf40 [size=64]
        Capabilities: [dc] Power Management version 2


> 
00:00.0 0600: 8086:3340 (rev 21)
00:01.0 0604: 8086:3341 (rev 21)
00:1d.0 0c03: 8086:24c2 (rev 03)
00:1d.1 0c03: 8086:24c4 (rev 03)
00:1d.2 0c03: 8086:24c7 (rev 03)
00:1d.7 0c03: 8086:24cd (rev 03)
00:1e.0 0604: 8086:2448 (rev 83)
00:1f.0 0601: 8086:24cc (rev 03)
00:1f.1 0101: 8086:24ca (rev 03)
00:1f.5 0401: 8086:24c5 (rev 03)
00:1f.6 0703: 8086:24c6 (rev 03)
01:00.0 0300: 10de:0328 (rev a1)
02:05.0 0280: 8086:1043 (rev 04)
02:08.0 0200: 8086:103d (rev 83)
02:0b.0 0607: 1179:0617 (rev 32)
02:0b.1 0607: 1179:0617 (rev 32)
02:0d.0 0880: 1179:0805 (rev 03)




and i really need the wifi so if anyone can help me i'll be gratefully :)

---


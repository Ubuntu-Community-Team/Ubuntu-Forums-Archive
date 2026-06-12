---
title: "Lubuntu Wireless Card problems HP Pavilion dv6t Quad edition"
date: 2012-06-23
forum: Hardware
---

### Post by ConfusedHP on 2012-06-23
Hey guys, I am relatively new to lubuntu but I have done my homework. I have searched the forums for the solution to this problem, but to no avail. Maybe one of you can help?

[LEFT][COLOR=#333333][FONT=Ubuntu]sudo lshw -C network > ~/Desktop/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]output.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]txt:

*-network DISABLED
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan0
       version: 00
       serial: 08:ed:b9:1b:0c:b2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.2.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:d3500000-d350ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: 08:2e:5f:72:cf:1d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d3404000-d3404fff memory:d3400000-d3403fff

---------------------------------------------------------------------
[/FONT][/COLOR][/LEFT][COLOR=#505050][FONT=sans-serif]Ralink corp. Device 539a is my wireless device

[/FONT][/COLOR][COLOR=#505050][FONT=sans-serif][/FONT][/COLOR][LEFT][COLOR=#333333][FONT=Ubuntu]HP Pavilion dv6t Quad Edition PC

I have both windows and lubuntu installed on separate partitions

Any help would be greatly appreciated... I really cannot figure this thing out.




[/FONT][/COLOR][/LEFT]

---

### Post by ConfusedHP on 2012-06-23
Is there any information that I did not include that would be a hindrance to this query?

---

### Post by ConfusedHP on 2012-06-26
Sigh.

I think I may have found a hackneyed solution to my own problem. 

I typed:

sudo rmmod hp_wmi

and it worked. then I did:

sudo leafpad /etc/modprobe.d/blacklist.conf

and put in 'blacklist hp_wmi'

everything seems to be working fine so far, but after a few reboots something else might happen. Stay tuned.

---


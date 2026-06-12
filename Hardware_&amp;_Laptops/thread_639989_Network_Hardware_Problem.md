---
title: "Network Hardware Problem"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by Pulser on 2007-12-13
[FONT="Georgia"]Hello, I'm not sure if this should be on the Ubuntu forum because of the OS but I'll post it anyway.

I've got a Windows XP cd that I want to install on a computer, I've installed it but once it is installed I cannot connect to the internet, someone has told me it's probaly a hardware problem and I need to download a driver, so I look at my hardware by using the "*lspci*" command in Terminal, I then find my hardware which is* 00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2).*

I google bits of this and all I get is Linux forums and websites, why don't I get anything which is related to the driver I need to download?

Overall I need a driver for my network hardware, the details are:

[I]00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@00:07.0
          logical name: eth0
          version: a2
          serial: 00:17:31:74:3e:a3
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full ip=192.168.2.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02d000-fe02dfff ioport:ec00-ec07 irq:19
[/I]

Thanks if you can find me the driver or tell me why I only see linux related things when I googled it.

Thank you.[/FONT]

---

### Post by Pulser on 2007-12-18
No one?

---


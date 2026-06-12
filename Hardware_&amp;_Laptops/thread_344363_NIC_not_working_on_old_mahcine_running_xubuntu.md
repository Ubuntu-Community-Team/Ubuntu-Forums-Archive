---
title: "NIC not working on old mahcine running xubuntu"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by Tiny Grasshopper on 2007-01-22
I'm having trouble connecting my computer to my router. I think it could be hardware problems with the NIC since it is a fairly old computer, but I don't know what commands can be used to diagnose it more completely.
lshw tells me this for the Network card

           *-network DISABLED
                description: Ethernet interface
                product: SMC2-1211TX
                vendor: Accton Technology Corporation
                physical id: 9
                bus info: pci@01:09.0
                logical name: eth0
                version: 10
                serial: 00:10:b5:8a:99:c7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full link=yes multicast=yes port=MII speed=100MB/s
                resources: ioport:2800-28ff iomemory:f4100400-f41004ff irq:9

I assume it was disabled because it's not working properly but I don't know whether it could be that or misconfiguration somewhere. It's just two machines connected to a router, this one and a laptop. This machine is running xubuntu and the laptop is running ubuntu and the laptop connected just fine. The laptop is also using NetworkManager.

What can I do to further diagnose whether it be hardware or misconfiguration?

---


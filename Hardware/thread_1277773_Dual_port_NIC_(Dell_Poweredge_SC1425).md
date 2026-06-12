---
title: "Dual port NIC (Dell Poweredge SC1425)"
date: 2009-09-28
forum: Hardware
---

### Post by StrangeWill on 2009-09-28
My dual NIC shows up as one card:
```

              *-network
                   description: Ethernet interface
                   product: 82541GI Gigabit Ethernet Controller
                   vendor: Intel Corporation
                   physical id: 4
                   bus info: pci@0000:02:04.0
                   logical name: eth0
                   version: 05
                   serial: 00:14:22:b0:5f:c1
                   size: 1GB/s
                   capacity: 1GB/s
                   width: 32 bits
                   clock: 66MHz
                   capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                   configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=172.16.100.178 latency=32 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s


```

How can I have this set up so one port is eth0 and the other is eth1? I only have eth0 and makes it impossible to do anything I need to.

---

### Post by StrangeWill on 2009-09-29
Err never mind.

NIC works much better if you enable it in BIOS.

---


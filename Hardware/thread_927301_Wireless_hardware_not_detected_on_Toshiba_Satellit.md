---
title: "Wireless hardware not detected on Toshiba Satellite A205-S582"
date: 2008-09-22
forum: Hardware
---

### Post by jmorgan24 on 2008-09-22
I've installed Hardy on this laptop and everything worked beautifully except the wireless is nowhere to be found. Nothing on lscpi or lshw, wired only. I believe the chipset on this model is Realtek RTL8187b.

Thanks

---

### Post by Crafty Kisses on 2008-09-22
Post the results of this command:
```
lshw -C network
```

---

### Post by jmorgan24 on 2008-09-22
```
 *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:95:77:8b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

```

---

### Post by jmorgan24 on 2008-09-22
Oh and the light does work, if that matters.

---


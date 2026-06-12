---
title: "ar242x Wireless on Compaq Presario CQ60"
date: 2009-02-20
forum: Hardware
---

### Post by jenkinbr on 2009-02-20
I'm trying to get Ubuntu to run on a friend's laptop, but am having problems with, as is typical of laptops, the wireless.

I looked in the help files in Ubuntu, and it said to turn the wireless on, so I did this, both from the nm-applet Icon and by pressing the orange wireless button.  The problem is that in Windows, the button turns blue when this is done, but in Ubuntu, it does nothing, and has no effect.

Any ideas?

Output of lshw -C network:
```

  *-network
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:62:74:29
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:ac:b4:08:8d:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by binbash on 2009-02-20
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by benhur99ph on 2009-02-23
I have a CQ20 and my wireless works right out of the box. What I did is to enable the restricted drivers for my Broadcom STA Wireless card. Since your's is a different model, I don't know if this will work, try it nonetheless.

---


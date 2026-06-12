---
title: "My wireless card isn't working"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by Xamindar on 2008-01-25
I have the following wireless card in this laptop:

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Ubuntu tells me it is using the madwifi driver for it but I don't see any wireless networks listed in networkmanager.  Is there something else I need to do to get it working?  Load frmware or something?

```
 *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0

```

---


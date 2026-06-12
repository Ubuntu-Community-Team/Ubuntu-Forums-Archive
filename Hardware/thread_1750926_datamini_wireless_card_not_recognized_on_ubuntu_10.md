---
title: "datamini wireless card not recognized on ubuntu 10.04"
date: 2011-05-06
forum: Hardware
---

### Post by tomaldguz on 2011-05-06
Hi, I am new to this forum, I hope I am posting in the right place.  I installed ubuntu 10.04 in my netbook datamini. I would tell you the model of the datamini netbook but I don't know how to find out.  My problem is that ubuntu doesn't recognize the wireless card in my netbook.  I think it is because I need to turn it on first, in windows I do this by tiping (fn F3) wich turns on wireless. 

I ran "lshw -C network" as I saw in other thread and I get:

```

*-network
        description: Ethernet interface
        product: RTL8101E/TRL8102E PCI Express Fast Ehternet controller
        vendor: Realtek Semiconducto Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eht0
        version: 02
        serial: 00:e0:5c:86:9a:23
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list rom ehternet physical
        configuration: boradcast=yes driver=r8101 driverversion=1.020.00-NAPI latency=0 multicast=yes
        resources: irq:16 ioport:2000(size=256) memory:d0100000-d0100fff memory:d0000000-d000ffff(prefetchable) memory:d0020000-d003ffff(prefetchable)

```

and iwconfig returns:
```

lo         no wireless extensions.

eth0    no wireless extensions.

```

So I think i need to turn on the wireless card for the SO to recognice it, but pressing the key combination doesnt do it.  Any suggestions?

---


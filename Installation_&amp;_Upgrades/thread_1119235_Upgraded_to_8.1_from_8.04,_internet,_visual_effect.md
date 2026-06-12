---
title: "Upgraded to 8.1 from 8.04, internet, visual effects non-working"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by schimm1 on 2009-04-07
everything worked before i updated. i tried removing the gnome network manager and manually editing files and putting in my network data, static ip, gateway etc. also, the visual effects used to be at normal, now they won't go past none.

any help?

---

### Post by cariboo on 2009-04-07
Could you explain what your problems are? I can infer that you are having network problems and video problems, is that right?

Could you open an Applications-->Accessories-->Terminal and paste the output of the following commands in your next post:

```
sudo lshw -C network
```

and

```
sudo lshw -C video
```

Jim

---

### Post by schimm1 on 2009-04-07
network:
```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:e0:7d:df:54:b7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.20 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth1
       version: 01
       serial: 00:0d:56:67:45:4c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.19 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:d1:90:a3:92:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

and video:
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by 123456789123456789123456 on 2009-04-07
Was the effects of video automatically allowed by 8.04, or did you have to do something in order to get the visual effects to work?  If the latter is true, have you attempted the same thing with 8.10?

---

### Post by schimm1 on 2009-04-07
> **123456789123456789123456 said:**
> Was the effects of video automatically allowed by 8.04, or did you have to do something in order to get the visual effects to work?  If the latter is true, have you attempted the same thing with 8.10?

it was automatically allowed.

---

### Post by schimm1 on 2009-04-07
i can connect to my router and put files on another computer, but it doesn't want to connect to websites.

---

### Post by schimm1 on 2009-04-13
got networking working, dawg, downgrading to 804, want lts anyway

---


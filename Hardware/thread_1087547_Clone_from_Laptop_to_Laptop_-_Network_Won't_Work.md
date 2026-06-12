---
title: "Clone from Laptop to Laptop - Network Won't Work"
date: 2009-03-05
forum: Hardware
---

### Post by sickanimations on 2009-03-05
Unfortunately the laptop acting as my server was to be repossessed... So I cloned the hard drive of my server (Toshiba Satellite P100) and dumped it on a more modest system (Compaq nx6120). I'm running Ubuntu 8.10.

I copied /etc/X11 from a Live CD session to get the graphics going. Now everything works except the network and sound. I don't care about the sound but the network REALLY matters.

Network (and sound) works perfectly in Live CD 8.10. Is there some way to scrape the config from a session and drop it into my install?

Here are some relevant looking things:
DMESG
```

[    4.327860] eth0: Tigon3 [partno(BCM95705A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:14:38:1d:ad:45
[    4.327867] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    4.327871] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
...
[   28.967713] udev: renamed network interface eth0 to eth2
[   56.824698] ADDRCONF(NETDEV_UP): eth2: link is not ready

```

lspci.txt
```

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

```

I've tried solving by editing /etc/network/interfaces to default, tried copying the live session's version. No luck - same errors.

I really, really, really don't want to do a clean install. If I wanted to do things that way I'd install Windows on my server (which would be so much easier but I wouldn't learn ANYTHING)...

If you got to this paragraph - thank you for reading :) If you have any suggestion at all - I encourage you to contribute it :)

---


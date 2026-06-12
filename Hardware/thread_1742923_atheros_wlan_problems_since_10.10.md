---
title: "atheros wlan problems since 10.10"
date: 2011-04-29
forum: Hardware
---

### Post by samjam on 2011-04-29
I have an Acer Aspire 9300 with an Atheros network card described like this:

```

        *-network
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: 5
             bus info: pci@0000:04:05.0
             logical name: wlan0
             version: 01
             serial: 00:19:7d:6a:76:57
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:c3000000-c300ffff

```

It *works* but is pretty rubbish, takes ages to associate and keeps losing packets. Ubuntu 10.04 was fine, 10.10 and 11.04 atheros drivers are dreadful.

Right now I'm using a USB dongle.

Any tips?

---


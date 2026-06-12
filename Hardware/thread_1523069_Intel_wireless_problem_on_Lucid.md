---
title: "Intel wireless problem on Lucid"
date: 2010-07-03
forum: Hardware
---

### Post by sambarluc on 2010-07-03
I have a problem with the wireless connection of my laptop, using Lucid 10.04. The card is correctly detected by the system, but it doesn't work (it doesn't detect any wireless, even if there are). On 9.10 I used it with linux-backports-module, but what should I do on Lucid? I'm using linux-image-2.6.31-22-generic kernel because the newer kernel has some problems with my video card. Thanks for any suggestion!
Here is the output of lshw:

                description: Wireless interface
                product: WiFi Link 6000 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:43:00.0
                logical name: wmaster0
                version: 35
                serial: 00:23:14:0a:6e:64
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:35 memory:90500000-90501fff

---


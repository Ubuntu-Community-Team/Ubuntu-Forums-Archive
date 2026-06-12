---
title: "mic stops working when using camera"
date: 2010-03-01
forum: Hardware
---

### Post by la_monda on 2010-03-01
Hi I m facing the following weird problem.
While using skype if i have my camera closed the mic works well. If i open my camera the mic works for a while but all of a sudden stops. Any clue?
My laptop is a HP probook 4515s M100

pelagia@hp-laptop ~ $ sudo lshw -class sound
[sudo] password for pelagia:
*-multimedia
description: Audio device
product: ATI Technologies Inc
vendor: ATI Technologies Inc
physical id: 5.1
bus info: pci@0000:01:05.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: driver=HDA Intel latency=0
resources: irq:19 memory:54310000-54313fff
*-multimedia
description: Audio device
product: SBx00 Azalia (Intel HDA)
vendor: ATI Technologies Inc
physical id: 14.2
bus info: pci@0000:00:14.2
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=HDA Intel latency=64
resources: irq:16 memory:54400000-54403fff

Thnx in advance for the support!!

---


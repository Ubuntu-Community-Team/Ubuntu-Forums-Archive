---
title: "What is best wireless internet card for Ubuntu 14?"
date: 2015-04-29
forum: Hardware
---

### Post by rtroxel2 on 2015-04-29
For the past 5 years, I've been using the MSI PC60G wireless card on my PC, which now has Ubuntu 14 installed. Although it has worked well in the past, that hasn't been the case since I installed 14. Internet connectivity drops out unexpectedly, and video streaming is almost impossible.  I checked the MSI web site and it doesn't look as though they supply Linux drivers for their cards.

Any suggestions would be welcome.

Thanks, in advance,

Roy

---

### Post by ajgreeny on 2015-04-29
Let's see the output of ```
lspci -nnk | grep -iA2 net
``` which will tell us a lot more about the wireless card.

---

### Post by rtroxel2 on 2015-04-30
> **ajgreeny said:**
> Let's see the output of ```
lspci -nnk | grep -iA2 net
``` which will tell us a lot more about the wireless card.

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
05:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:b834]
    Kernel driver in use: rt61pci

---


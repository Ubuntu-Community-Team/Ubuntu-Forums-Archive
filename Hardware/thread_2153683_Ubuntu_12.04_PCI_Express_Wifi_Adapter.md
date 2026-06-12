---
title: "Ubuntu 12.04 PCI Express Wifi Adapter"
date: 2013-06-11
forum: Hardware
---

### Post by jgoett154 on 2013-06-11
I have recently purchased a TP-Link TL-WDN4800 from newegg, but sadly I am having some issues with it. I am getting poor performance and sometimes even dropped connection.

lspci -nnk | grep -iA2 net
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless LAN adaptor [168c:0030] (rev 01)    Subsystem: Atheros Communications Inc. Device [168c:3112]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
```

I have tried adding options ath9k nohwcrypt=1 to /etc/modprobe.d/ath9k.conf but it has not helped any either. I have searched around a while and haven't found a solution that has worked for me yet. I will provide whatever information needed to help figure out the issue.

Thanks,
Joe Goett

---


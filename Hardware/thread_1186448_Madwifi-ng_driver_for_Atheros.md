---
title: "Madwifi-ng driver for Atheros"
date: 2009-06-13
forum: Hardware
---

### Post by Neckbeard Stallman on 2009-06-13
I have a Toshiba Satellite a135 s4656 and with and Atheros card
```
$ lspci | grep Ethernet
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```pretty sure madwifi-ng is will work with this. But I don't know where to start. Can someone help me please?
Also when I go to the madwifi website to download the driver I always get a 404 error?

---

### Post by synapsys on 2009-06-13
You can use the latest subversion of madwifi-ng or you can use ath5k which works 'out of the box' with version 9.04 jaunty. What version of ubuntu are you running?

---

### Post by Neckbeard Stallman on 2009-06-13
I got the newest version 9.10

 But I don't think ath5k supports Network monitoring or packet injection hence the madwifi-ng. Basically I'm just trying to fix this driver so that I can audit my wireless network's security.

---

### Post by Amilo1718 on 2009-06-13
> **Neckbeard Stallman said:**
> Network monitoring or packet injection 
is that hardware?
i thought network monitoring was a software tool & udp a protocol...
but i could be wrong :p

---

### Post by Neckbeard Stallman on 2009-06-13
your point is moot.

---


---
title: "Wifi"
date: 2009-07-29
forum: Hardware
---

### Post by Happy_Killmore on 2009-07-29
I am new to linux and need wifi help. My bars only show one bar even if I am in the same room as my router. If you need info on my network card, tell me how to get it please.

---

### Post by IQRules on 2009-07-29
$ lspci -v | grep -i net
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by Happy_Killmore on 2009-07-29
I am not sure what any of that is.:confused:

---


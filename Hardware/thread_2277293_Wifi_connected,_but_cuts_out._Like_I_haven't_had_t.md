---
title: "Wifi connected, but cuts out. Like I haven't had this happen before..."
date: 2015-05-07
forum: Hardware
---

### Post by Teethdude on 2015-05-07
As the title says. I'm near the point where I find WIFI unusable in Ubuntu. It's connected to the router, works for anywhere from several hours to 3 seconds, and then doens't work. It claims to still be connected to Wifi, but there's no ping to anything in or outside the network.

Results of "lspci -nnk | grep -iA2 net"
```
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091] (rev 13)	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:10ec]
	Kernel driver in use: alx
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi

```
This connection issue has come to the point where I can't stand it anymore and am ready to toss out Ubuntu because the Wireless works fine on Windows, and this isn't the first time I've had the issue. I've had it on a veriety of wifi chips (Broadcom, RealTek, and now Intel).
Thanks for any help.

---


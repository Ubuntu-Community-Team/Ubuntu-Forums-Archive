---
title: "ipw2200 no longer works with no obvious error after upgrade to Intrepid"
date: 2008-12-29
forum: Hardware
---

### Post by mathfeel on 2008-12-29
I have a Dell 700m with the following wireless hardware:
```
~$ lspci | grep 2200
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

It was working just fine with Hardy. I did a dist-upgrade over christmas and afterword, NetworkManger does not list any of the nearby network.

The ipw2200 modules seems to have loaded just fine:
```
$ dmesg | grep ipw
[   47.702669] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   47.702674] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   47.703018] ipw2200 0000:02:01.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   47.708722] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   47.708776] firmware: requesting ipw2200-bss.fw
[   51.086783] ipw2200: Radio Frequency Kill Switch is On:
[   51.088907] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```

but there is no scanned result:
```
$ sudo iwlist eth1 scan
eth1      No scan results
```

My other laptop can see the network just fine (different hardware). I also tested with the live desktop off the 8.10 liveCD and get the exact same result.

EDIT: pressd Fn-F2 to enable wireless actually made it works.

---


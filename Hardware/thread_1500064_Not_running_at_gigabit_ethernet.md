---
title: "Not running at gigabit ethernet?"
date: 2010-06-02
forum: Hardware
---

### Post by Eddles on 2010-06-02
Hello all,

I need to transfer files from my desktop PC to my laptop.  Both computers has a gigabit ethernet card, and I have an gigabit ethernet switch.  The laptop output shows:

```
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

and the card is running at gigabit ethernet speeds:

```
eth0: negotiated 1000baseT-FD flow-control, link ok
  product info: Yukon-EC 88E1111 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```

From my desktop computer:

```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

but the driver says the card's running at Fast Ethernet speeds and isn't able to run at gigabit ethernet speeds:

```
eth0: negotiated 100baseTx-FD, link ok
  product info: vendor 00:07:32, model 17 rev 2
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
```

How do I make my desktop's ethernet card run at gigabit ethernet speeds?  The desktop is using Ubuntu 10.04 and running kernel 2.6.32.  The laptop's about 4 years old, and the desktop is only a month old.

Thanks very much for your help in advance!

Regards - Piers

---


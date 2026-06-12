---
title: "Broadcom 4401 problems"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by zkyez on 2006-02-09
hello.
I have a laptop (fujitsu siemens amilo 1310G) with a broadcom 4401 lan card (onboard). here is the problem:

at random times, the nic hangs up. it doesn`t do any traffic at all. i still have a link in my switch, i can see incoming traffic via tcpdump but no outgoing traffic. i tried with 2.6.12 and 2.6.15 kernels (from breezy and dapper), with the driver from the manufacturer, but it`s the same: it locks up. i edited the source of the driver like this:


After unpacking, and before compiling, change the following line (line 51) in b44um.c:

replace the line
#define TX_TIMEOUT (2*HZ)

with
#define TX_TIMEOUT (5*HZ)


but no luck.

Any hints here?
Thanks

---

### Post by Rogers on 2006-02-09
Is this stable working hardware?  NIC cards fail.  You may be beating a dead horse.  I've seen NICs act like that before and the only solution was to replace them (no the best solution for you).

---

### Post by zkyez on 2006-02-09
it works just fine in windows, so i think it`s a driver problem not a hardware one

---


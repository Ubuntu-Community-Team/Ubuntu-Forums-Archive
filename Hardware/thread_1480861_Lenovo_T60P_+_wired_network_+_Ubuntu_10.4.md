---
title: "Lenovo T60P + wired network + Ubuntu 10.4"
date: 2010-05-12
forum: Hardware
---

### Post by ablatzhe on 2010-05-12
Hi, 
curios that I got problems with my wired network adapter. So I use a Lenovo T60p and all works fine except the wired network adapter. 

lsmod shows the following driver entry: 
...
e1000e                136205  0 
...

lspci shows the following device:
...
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
...

However, it seems that there is no mapping between the driver and the hardware. So there should be a way to do that manually. 

THX
Andreas

---


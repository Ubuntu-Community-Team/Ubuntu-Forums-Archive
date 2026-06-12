---
title: "HP Presario V2000 (Internet Problem)"
date: 2008-12-28
forum: Hardware
---

### Post by zirun292 on 2008-12-28
HP Compaq Presario V2000
Ubuntu 8.04

(Network Problem)
I don't know whether the Ethernet Card or the Network Cable is not functioning.
But when I put the Network Cable to the Ethernet Card. It seems to be working. But when I try to connect to [WWW.google.com](WWW.google.com), it failed. It doesn't connect.

---

### Post by teaker1s on 2008-12-30
you want to try to ping with network tools or numeric ip of your router. could just be a dns issue
failing that 
```
lspci -v
``` will help locate your network adapter make.

---


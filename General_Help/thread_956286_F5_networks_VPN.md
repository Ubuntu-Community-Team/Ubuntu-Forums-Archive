---
title: "F5 networks VPN"
date: 2008-10-23
forum: General Help
---

### Post by tacutu on 2008-10-23
Hi all
I'm trying to connect to a F5 Networks VPN.

I installed firefox 2, since it seems that firefox3 is not supported. I managed to install the plugin. Firefox reports that it is connected to the VPN, but in the terminal I launch firefox from, I get 
```
SIOCADDRT no such process
SIOCDELRT no such process
```
and nothing works (no ping, no browsing, nothing)

```
route gives me:

133.30.46.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

172.16.192.254    0.0.0.0         255.255.255.0   U     0      0        0 eth0

0.0.0.0         172.16.192.254  0.0.0.0         UG    100    0        0 eth0
```

My intuition tells me the problem is with a badly configured route / gateway.
Any suggestions would be appreciated.

---

### Post by tacutu on 2008-10-24
bump

---


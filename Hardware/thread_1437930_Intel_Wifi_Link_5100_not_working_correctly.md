---
title: "Intel Wifi Link 5100 not working correctly"
date: 2010-03-24
forum: Hardware
---

### Post by Hawk__0 on 2010-03-24
I recently purchased an asus ux50v and the wireless is acting very odd.

Firstly, I can pick up wireless network with it if I install WICD, because knetworkmanager picks up no networks.  Secondly, if I type wlist scan a bunch of networks do show up.

I tried connecting to my wireless network with authentication being required and it kept saying "bad password", I tried after configuring my wireless router with open access and it still couldn't connect.

Are there any ways I can fix this?  Why doesn't knetworkmanager not show my networks?

EDIT:

Perhaps the problem is here?
wlan0     Link encap:Ethernet  HWaddr 00:22:fb:7c:3c:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

is it supposed to say encap:Ethernet?

---

### Post by Hawk__0 on 2010-03-25
bump

---

### Post by Hawk__0 on 2010-03-26
bump

---

### Post by Hawk__0 on 2010-03-29
switched from kubuntu 10.04 alpha to ubuntu 10.04 beta and it works.

---


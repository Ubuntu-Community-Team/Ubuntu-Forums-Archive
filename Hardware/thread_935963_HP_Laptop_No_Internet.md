---
title: "HP Laptop No Internet"
date: 2008-10-02
forum: Hardware
---

### Post by boosted on 2008-10-02
HP pavilion ze5600 Laptop

Fresh install of Ubuntu Desktop

I can't post any terminal output because I am on my other computer right now in order to post this.
But when when LSPCI is entered I get for ethernet:
00:09.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
and
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

When I type:
sudo lshw -C network
I get that :
Network 1
Autonegotiation=on  broadcast=yes  driver=natsemi  driverversion=2.1  duplex=full  ip=192.168.0.116  latency=90  link=yes  maxlatency=52  

When sudo ifconfig is used:
eth1: 
inet addr: 192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
RX packets:720  errors:0  dropped:0  overruns:0  frame:0
TX packets:42  errors:0  dropped:0  overruns:0 carrier:0
Collision:0  txqueuelen:1000
RX bytes:44040 TX bytes:5587





I can't connect to the internet or get any updates.  Please help me out here.
Thanks

---

### Post by Sef on 2008-10-02
>  Fresh install of Ubuntu Desktop

Which version?

---

### Post by boosted on 2008-10-02
v.8.04.1

---

### Post by boosted on 2008-10-02
anyone? Please....

edit:

I can log into my router and see that the laptop is connected.
I can also open up Network on the laptop and view my *cough* windows shares.  But, no internet access...  some one please help me out here.

---

### Post by boosted on 2008-10-02
any ideas?  This crap is really getting aggravating!

---

### Post by boosted on 2008-10-02
ok I fixed it.  Weird.. but it fixed it.  The network icon in the upper right hand corner... I just clicked it then re-clicked the wired ethernet and it reconnected again.  Now it works?

---


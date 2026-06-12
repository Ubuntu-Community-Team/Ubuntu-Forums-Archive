---
title: "Hamachi can't ping/vnc machines:"
date: 2008-10-25
forum: General Help
---

### Post by klepto on 2008-10-25
For the record I already have port forwarding setup and I use uTorrent in wine
all the time and it works just fine. 

I joined my local network and another network in hamachi and it shows them as green but I am not receiving any packets. Here is my problem: 

ham0      Link encap:Ethernet  HWaddr 92:ed:7a:20:3e:47
          inet addr:5.60.105.62  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 B)  TX bytes:7848 (7.8 KB)

I am using Ubuntu Intrepid Ibex

---

### Post by klepto on 2008-10-28
Ok Fixed!!

Here's the [solution]("https://forums.hamachi.cc/viewtopic.php?t=18424&highlight=ping")

"you have to right click on the "group" or "network" in the linux client and select "change status" so that you are online for that "network""

---


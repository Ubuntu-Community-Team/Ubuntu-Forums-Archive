---
title: "LAN not working ASUS EEE 1201T - 10.04"
date: 2010-05-20
forum: Hardware
---

### Post by AsusEEE on 2010-05-20
Hi All -

Just installed 10.04 on my ASUS 1201T netbook.  Install went fine (from USB).

Can't get ethernet working.  Have tried fiddling with it and also reinstalling 

Keeps trying to connect, then saying it cannot (i've verified the connection is hot by plugging into another pc).   Should be 100MB / Auto according to the router.

**Here is what the ifconfig output is:**
eth0      Link encap:Ethernet  HWaddr 48:5b:39:10:d4:3d  
          inet6 addr: fe80::4a5b:39ff:fe10:d43d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:92 dropped:0 overruns:0 frame:14
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:195
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:41208 (41.2 KB)
          Interrupt:27 

**Here's what I see when i   dmesg|grep eth0**

1773.159572] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Full Duplex>
[ 1774.005145] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down
[ 1790.166710] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Full Duplex>
[ 1793.006585] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down
[ 1806.770250] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Full Duplex>
[ 1808.005552] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Down


Any ideas?

Thanks,

Chad

---


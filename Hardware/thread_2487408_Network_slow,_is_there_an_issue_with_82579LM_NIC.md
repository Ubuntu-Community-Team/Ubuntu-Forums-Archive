---
title: "Network slow, is there an issue with 82579LM NIC?"
date: 2023-06-03
forum: Hardware
---

### Post by funkytwig4 on 2023-06-03
I was on reddit HomeNetowrok forum as I was having a problem with network speed.  I only get 30 MS/s between 2 servers which are next to each other conected to a TP Link Gigabit switch conected with 2M internet cables.  I have ordered a few replacement cables (from 3 diferent semingly reputable makes) but someone said there may be issues with the 82579LM NIC in Linux, so here I am asking.

Is this an issue,was this an issues that is not fixed.  I am on 18.04.6 LTS at one end and 22.04.2 LTS on the other.  Would rather not upgrade the first one as it is being decomisioned (and replaced with other one) but can if people know it resolves isses wit the NIC/networking.

regards,
Ben

---

### Post by TheFu on 2023-06-03
I'm unfamiliar with "MS/s" and "2M" units?  Could you please be technically accurate?

Typically, network speeds are in Mbps (megabits per second).  Some end-user applications will use MBps (megabytes per second).  But "GigE" NICs are 1000 Mbps ... in the real world, that translates to between 920-940 Mbps.

I don't have that, 82579LM, NIC, but I do have other Intel NICs.  Using iperf3, pure network performance can be measured.
So, on a 20.04 "server" with an Intel I211 using the igb driver, I'm seeing 
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.4 port 52230 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   958 Mbits/sec    0    380 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   941 Mbits/sec    0    380 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   941 Mbits/sec    0    380 KBytes       
[  4]   3.00-4.00   sec   112 MBytes   941 Mbits/sec    0    380 KBytes       
[  4]   4.00-5.00   sec   112 MBytes   941 Mbits/sec    0    380 KBytes       
[  4]   5.00-6.00   sec   112 MBytes   942 Mbits/sec    0    400 KBytes       
[  4]   6.00-7.00   sec   112 MBytes   941 Mbits/sec    0    400 KBytes       
[  4]   7.00-8.00   sec   112 MBytes   941 Mbits/sec    0    400 KBytes       
[  4]   8.00-9.00   sec   112 MBytes   941 Mbits/sec    0    400 KBytes       
[  4]   9.00-10.00  sec   112 MBytes   941 Mbits/sec    0    400 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  1.10 GBytes   941 Mbits/sec                  receiver

iperf Done.
```
from an 18.04 client with an Intel 82574L using the e1000e driver.

Between two 20.04 systems, but with Intel I211 NICs, I see:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  5] local 172.22.22.20 port 48034 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   956 Mbits/sec    0    361 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   938 Mbits/sec    0    361 KBytes       
[  5]   2.00-3.00   sec   113 MBytes   945 Mbits/sec    0    361 KBytes       
[  5]   3.00-4.00   sec   112 MBytes   938 Mbits/sec    0    361 KBytes       
[  5]   4.00-5.00   sec   112 MBytes   942 Mbits/sec    0    382 KBytes       
[  5]   5.00-6.00   sec   112 MBytes   941 Mbits/sec    0    382 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   941 Mbits/sec    0    382 KBytes       
[  5]   7.00-8.00   sec   113 MBytes   947 Mbits/sec    0    382 KBytes       
[  5]   8.00-9.00   sec   112 MBytes   941 Mbits/sec    0    382 KBytes       
[  5]   9.00-10.00  sec   112 MBytes   941 Mbits/sec    0    382 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.10 GBytes   937 Mbits/sec                  receiver

iperf Done.

```

I have some Intel 82575GB NICs, but they are on a private network that connects to storage or directly used by VMs on the internet.  My internet connection isn't very fast.

Anyway, if you'll use iperf3 to gather some facts, maybe someone can help?

BTW, I'm in a similar situation regarding system OS upgrades.  The 18.04 system is planned to be retired, but needs some storage hardware removed and connected to another system first.  One of the 20.04 systems was just upgraded from 18.04 in the last 2-3 weeks (I don't remember exactly when). Life and other priorities get in the way.

---

### Post by funkytwig4 on 2023-06-03
Thanks for pointing me at iperf3. 

Ive got 85 MB/s and 115 MS/s depending whitch direction I do the test so its not that (Megabytes a second).  Sorry about the MS/s typo.  So its not the network :(.

---

### Post by TheFu on 2023-06-03
If this is solved, please use the thread tools button to mark it that way.

Otherwise, you'll need to be specific about what you mean by >  I only get 30 MS/s between 2 servers 
since the units don't matter and you aren't saying anything about what "between 2 servers" means.  Please be technically accurate with your words and fix any typos, like MS/s, which means nothing.

---

### Post by funkytwig4 on 2023-06-03
Werry odd, I thought I had repled to this.  Sorry about the typo.  I meant MB/s (megabytes).  Thanks for pointing me at iperf3.  I got 85 MB/s in one direction and 110 MB/s in the other so its not the network.  Will mark as solved, kind of ;).

---


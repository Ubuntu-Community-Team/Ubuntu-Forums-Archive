---
title: "[SOLVED] newbie having trouble w/ traceroute"
date: 2008-09-30
forum: General Help
---

### Post by d3nali on 2008-09-30
yep another linux newbie.

i can't seem to run traceroutes either from terminal or from the network tools utility.  ping works fine, just can't trace. i'm not running any firewall right now, but i'm also not sure if ubuntu has a built in firewall like windows (if it does i can't find it).  i'm running hardy heron 8.04 on a acer apireone.

anyone else running into problems like this?

d3nali@d3nali-laptop:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (72.14.205.99), 30 hops max, 40 byte packets
 1  192.168.9.254 (192.168.9.254)  2.856 ms  6.882 ms  10.338 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *

thanks in advance :D

---

### Post by dcstar on 2008-09-30
> **d3nali said:**
> yep another linux newbie.

i can't seem to run traceroutes either from terminal or from the network tools utility.  ping works fine, just can't trace. i'm not running any firewall right now, but i'm also not sure if ubuntu has a built in firewall like windows (if it does i can't find it).  i'm running hardy heron 8.04 on a acer apireone.

anyone else running into problems like this?

d3nali@d3nali-laptop:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (72.14.205.99), 30 hops max, 40 byte packets
 1  192.168.9.254 (192.168.9.254)  2.856 ms  6.882 ms  10.338 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *

thanks in advance :D

You have already left "Ubuntu", the issue is in the network setup with whatever connects to your 192.168.9.254 device (or that device itself).

---

### Post by ilrudie on 2008-10-01
Perhaps your router or ISP blocks standard traceroute UDP packets.  Try using traceroute with the -I (capital i) flag to send ICMP probe packets instead.  Ping is working so they shouldn't be blocked by anything.

---

### Post by d3nali on 2008-10-01
Thanks for the response guys,

i initially thought it was a router issue (192.168.9.254 is my wireless router) but i have a windows box that can trace out to the web no problems.

i dug a little deeper and bypassed my router, plugged directly into my broadband modem and sure enough traceroutes work.

thinking it might be a wireless issue, i moved a device back and plugged directly into my router and i'm back to the same problem (trace dies at the router). so while behind the router, using either the local card or the wifi card the trace dies at the router.

it sure seems like it would be a router issue, but i'm a little confused why the windows box isn't having the same problem. 

i will say this....i installed this distro myself and i did have some problems initially setting up the wifi, but i eventually got it work.  is it possible the network manager is having problems?  if so, can i reinstall it?

anywho, i'm going to try it out on another network and see if the problem follows.

any and all help is always appreciated.  thanks again. :D

---

### Post by d3nali on 2008-10-01
UPDATE

i was able to use this laptop on a different network and the traceroute worked.

so it IS an issue w/ my router, specifically processing UDP vs ICMP pkts.  i will play around w/ it and see if i can get it to allow UDP.

thanks again

---


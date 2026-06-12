---
title: "Core i7 system load"
date: 2009-09-05
forum: Hardware
---

### Post by omax on 2009-09-05
Hi!

I'm running 9.04 2.6.28-15-generic and it's working allright.
However, anytime I get some load on my CPU (such as hashing in rtorrent or unraring archives) it puts all the load on one of the 8 virtual cores. Thus, I have 7 virtual cores that are practically unused. But the computer becomes unresponsive. Not lethal, but compiz lags and it's quite annoying for being a i7 920 with 6GB RAM and other really good hardware.

Is anyone else having these problems? Is it ubuntu/linux-specific? Should I compile my own kernel to solve this?

---

### Post by Arup on 2009-09-05
Actually hyper threading is program specific, so far with my dual quad core and other i7 I have used, the load balancing in Linux is far superior but sometimes it depends on the particular program as well and in your case, it could be an issue with rtorrent, when I unrar, usually at least four of my cores are in action.

---

### Post by omax on 2009-09-05
That sounds about right. unrar uses 2-3 cores simultaneously.
So perhaps there is a patch for rtorrent that makes use of hyperthreading?

---


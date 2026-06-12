---
title: "&quot;no route to host&quot; after Karmic Upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Angstroem on 2009-11-02
Hi there,

on Sunday I upgraded from Hardy to Karmic. While the upgrade went smooth, I'm fighting one weirdness since then:

In my network, I have 3 machines, let's call them A, B, and C. Networking works fine for all of them besides the following: the two 9.10 machines, A and B, cannot see each other. C is still running 8.04 and shows no problem, just as A and B did while still running 8.04.

Whether I use traceroute or try ssh, I get "no route to host" when trying to access A from B or vice versa. Both machines are of course registered with the router and do get network connection (in fact, I'm writing this from one of these).

I can traceroute anything but traceroute from A to B or B to A -- both throw a "no route to host". Traceroute to C works.

I can ssh anything but A from B or B from A. Both are able to ssh into C, likewise C can ssh into A or B.

"iptables --flush" and "ufw disable", as suggested in another "ssh shows no route tohost" thread didn't do anything to resolve this problem.

Any idea what's going on here and how to fix it?

---

### Post by Angstroem on 2009-11-03
Solved. Looks like it's an issue with the current wicd version.

---


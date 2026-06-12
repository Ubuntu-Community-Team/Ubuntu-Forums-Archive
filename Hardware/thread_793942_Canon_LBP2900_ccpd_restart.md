---
title: "Canon LBP2900 ccpd restart"
date: 2008-05-14
forum: Hardware
---

### Post by killerclick on 2008-05-14
Hi,

I've set up a Canon LBP2900 and sometimes it stops working. When I try 
$ captstatusui -P LBP2900

it says Socket Error. I fix that easily by typing 

sudo/etc/init.d/ccpd restart

Now is there a way to fix this permanently? The printer has a problem when I restart the machine. This computer also has HP 2600c and a HP Scanner attached.

---


---
title: "Ubuntu 12.04 Wireless Dropping Connection Dell E6420"
date: 2012-05-03
forum: Hardware
---

### Post by zcline on 2012-05-03
Hi all,

I have a Dell E6420 that i'm having wireless issues with. I generate a key, and it will connect, but it drops connection minutes later, and won't accept the unique key I generated previously as being valid. 

It seems in general to have issues connecting to any of the networks we have, sometimes I have to enable and disable networking all together to get it to simply connect to our  network.

I have made sure the card itself is working correctly, as the machine is partitioned with Windows and has no issues connecting in that environment.

I have attempted to disable the power managment on the wlan0 interface thinking it may be dropping the connection to save power, but have had no luck in getting it to stay connected.

Any suggestions from here?

---

### Post by zcline on 2012-05-03
[SOLVED]

I edited /etc/nsswitch.conf 

from:

hosts: files mdns4_minimal [NOTFOUND=return] dns MDNS4

to:

hosts: files mdns4_minimal [NOTFOUND=continue] dns MDNS4

---


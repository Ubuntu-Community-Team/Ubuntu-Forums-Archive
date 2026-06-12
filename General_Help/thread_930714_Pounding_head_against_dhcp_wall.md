---
title: "Pounding head against dhcp wall"
date: 2008-09-26
forum: General Help
---

### Post by jbmckim on 2008-09-26
I'm running debian 8.04.1.

I'm trying to set up a firewall and am stuck hard on the dhcp server.  I've tried a number of the examples both on these boards and from other sources and I always wind up with:
* Starting DHCP server dhcpd3    [fail]

I'm running 2 nics.  One to the WAN and one to the LAN.  Is there a dead bang sure example somewhere I'm missing?  One problem I've had is that many such scripts include varibles that either don't apply to my situation or are a complete mystery as to how to complete.  Also, I'm wondering if I might have some artifact from the system install that might need to be deleted or modified?  In any case, it seems to be a high, wide wall.

Help and patience is appreciated.

Thanks.

---

### Post by nsche on 2008-09-27
I assume (don't have the server on my machine) there is a config file for the dhcp server and that is most likely what is giving you the problem.  About the only other probable problem is if you are running it as the wrong user (cannot write/read files or open ports).  Could you post your config file?

---


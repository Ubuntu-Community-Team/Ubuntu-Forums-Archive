---
title: "How to setup networking on 8.04 w/o GUI?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by nubie777 on 2009-08-12
I've installed Ubuntu 9.04 (GUI) and Ubuntu 8.04.2 Server (no GUI) on ESXi 3.5 U4.  This is connected to a P2P network (10.10.0.xxx)

How do I setup networking on 8.04.2 so I have Internet access and P2P access from the command line?
 
On 9.04 and 8.04 the /etc/network/interfaces file contains:
auto lo
iface lo inet loopback

Screen shot is ifconfig of 9.04.  ifconfig of 8.04 lists loopback only.

Thanks much.

---

### Post by slakkie on 2009-08-12
See my sig, the part about no network managers.

---


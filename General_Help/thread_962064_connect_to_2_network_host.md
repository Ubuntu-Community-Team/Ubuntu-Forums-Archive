---
title: "connect to 2 network host"
date: 2008-10-28
forum: General Help
---

### Post by harsonohaqy on 2008-10-28
I had just install Ubuntu and I have a problem with my network connection. because I have two ethernet card that related to two workgroup. One's network have internet use ADSL router using IP Gateway (Workgroup name:con1, left one just need to LAN connection for 6 workstation (WorkGroup Name:con2).

When I browsed to the network, It just appeared Con1 network. I could not see Con2 network. I had unplug RJ45 Connector related to con1 but I still get a problem to open con2 network.

Please...anybody can help?
I newbie in linux..I'll be appriciated any of advice

Best regard's
Rudi H

---

### Post by alienprdkt on 2008-10-28
I had to go through this when I build a router, for me to have it see the pcs on one nic and a pppoe connection on the other, i had to setup a dhcp server, then configure NAT within iptables.

then again this maybe just the Gentoo way of doing things, but atleast you now have some things to google.

---

### Post by DGortze380 on 2008-10-28
> **harsonohaqy said:**
> I had just install Ubuntu and I have a problem with my network connection. because I have two ethernet card that related to two workgroup. One's network have internet use ADSL router using IP Gateway (Workgroup name:con1, left one just need to LAN connection for 6 workstation (WorkGroup Name:con2).

When I browsed to the network, It just appeared Con1 network. I could not see Con2 network. I had unplug RJ45 Connector related to con1 but I still get a problem to open con2 network.

Please...anybody can help?
I newbie in linux..I'll be appriciated any of advice

Best regard's
Rudi H

Unless you have samba set up, 'workgroups' don't apply like they do in Windows.

to start, please post the output of ifconfig.

---


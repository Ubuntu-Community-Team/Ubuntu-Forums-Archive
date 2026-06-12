---
title: "Toshiba A100-216 unable to reliably obtain/refresh DHCP lease. (Intel 3945ABG)"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by jarthurs on 2007-12-31
I had this problem with Feisty and now again with Gutsy. Sometimes my laptop fails to obtain a DHCP lease at boot, it also fails to renew a lease. 

With Feisty the machine **never** obtained a DHCP lease on boot, this resulted in a very long delay during boot and then I manually restarted networking *sudo etc/init.d/networking restart* to obtain a lease. In Gutsy things are more successful in that it mostly manages to obtain a lease on boot, but when the lease expires it is unable to renew it without human intervention.

I have been manually using *sudo ifdown eth1* and *sudo ifup eth1* to coax it into obtaining/renewing a lease, but even this occasionally results in "No DHCPOFFER received". This is the only machine on the network that has problems, and it worked flawlessly under Windows XP so I've no doubt the hardware is fine.

DHCP runs on my IPCop firewall box, and the three laptops (Dell Inspiron 7000 + Atheros card with Xubuntu, Toshiba Equium L10 + Intel MiniPCI with XP Home) in the house connect to that via a Netgear WPN824 802.11g AP.

Not quite sure where to go from here?

Regards,
Jason.

---


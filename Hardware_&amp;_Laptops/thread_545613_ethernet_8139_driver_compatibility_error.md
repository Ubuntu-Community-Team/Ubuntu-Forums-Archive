---
title: "ethernet 8139 driver compatibility error"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by 4KvRMU7Nnv on 2007-09-07
When I updated to the 2.6.22-10-generic kernel, when I boot up it now tells me this:

[    2.780000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.588000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.588000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.
[    5.592000] 8139too Fast Ethernet driver 0.9.28

"lsmod | grep 8139" shows that 8139cp and 8139too are both running and the ethernet cable internet is working fine.  I don't want to see this message, however, and would like to know how to get it to go away/ fix whatever it wants me to fix.  any ideas?

---


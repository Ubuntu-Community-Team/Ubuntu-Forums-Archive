---
title: "LiveCD Persistence with a network share?"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by jonmccune on 2008-12-22
Hello,

LiveCD persistence with a USB drive is awesome.  Is there an easy way (i.e., existing HowTo) to use a network share to store the persistence data instead?  This is compelling on a system without USB 2.0 and where it is not practical to setup a server with TFTP, DHCP, etc for a full DiskLess configuration.

Thanks,
-Jon

---

### Post by namdung on 2008-12-22
> **jonmccune said:**
> Hello,

LiveCD persistence with a USB drive is awesome.  Is there an easy way (i.e., existing HowTo) to use a network share to store the persistence data instead?  This is compelling on a system without USB 2.0 and where it is not practical to setup a server with TFTP, DHCP, etc for a full DiskLess configuration.

Thanks,
-Jon

The PC needs one of the following mediums (primarily) to boot
[LIST]
[*]HDD
[*]FDD
[*]CDD
[*]USB
[*]Network PXE Boot
[/LIST]

So if you don't have a HDD and USB, then consider Thin Clients with PXE boot.

---

### Post by jonmccune on 2008-12-22
Thanks for your reply.  I suppose a more precise way of asking my question is: I'd like to avoid PXE boot by using a bootable CD-ROM.  It's fine if everything else loads via the network.

Thanks,
-Jon

---


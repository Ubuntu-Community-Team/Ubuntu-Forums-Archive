---
title: "Router, multiple IP addresses to each PC?"
date: 2014-05-29
forum: Hardware
---

### Post by satimis on 2014-05-29
Hi all,

I have 2 PCs, each running Oracle VirtualBox with about 30VMs installed and standing on the same table.

On shopping router I found TP-Link

TL-WR741ND
150Mbps Wireless N Router
[http://www.tp-link.com/en/products/details/?model=TL-WR741ND#spec](http://www.tp-link.com/en/products/details/?model=TL-WR741ND#spec)

Please advise can it assign 30 IP addresses to each PC?  Thanks

Rgds
satimis

---

### Post by dannyboy79 on 2014-05-29
the router should theoretically be able to assign 253 IP addresses

---

### Post by satimis on 2014-05-29
> **dannyboy79 said:**
> the router should theoretically be able to assign 253 IP addresses
Hi,

Thanks for your advice.

Sorry for not explaining in more detail on my original posting.  What I'm prepared to achieve is as follow;

1)
I have no problem making VMs accessing Internet even without a router, using NAT.

2)
I need to assign each VM a static internal(network) IP so that Internet can access all VMs on each box (ONLY one PC will run) browsing the websites running on them via static IP (I'm subscribing static IP).  

I did it several several years before making use of Perdition and MySQL for routing.  They ran on VMs specifically for this operation something similar to the design of WordPress.  It worked.

I'll start another thread later for advice to see whether there are different/better solutions.

Rgds
satimis

---


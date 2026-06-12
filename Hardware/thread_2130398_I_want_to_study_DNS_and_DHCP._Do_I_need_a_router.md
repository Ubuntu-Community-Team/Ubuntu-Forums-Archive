---
title: "I want to study DNS and DHCP. Do I need a router?"
date: 2013-03-29
forum: Hardware
---

### Post by asker2013 on 2013-03-29
Hi everyone. I am new to this forum and this is my first post.

I have three laptops, three 2-meter straight-through cables, and a D-Link 8-port 10/100 Desktop switch (DES-1008A).
I want to study DNS and DHCP in Ubuntu by creating a small INTERNAL network (1 server and 2 clients).
I have installed Ubuntu 12.04 desktop i386 32bit in all three laptops and have downloaded and updated all necessary files for my study.

My questions are:

1. Do I need to buy a router? If so, what is the exact model of the cheapest router that will suffice for my needs?

2. If I don't need a physical router, how will I configure my default gateway? 

Thanks in advance!

---

### Post by SeijiSensei on 2013-03-29
If the server allows you to install a second network card, you can configure it to be a [NAT router]("https://help.ubuntu.com/community/Internet/ConnectionSharing").  

Alternatively you can just buy a basic router for $25-30 from some place like [NewEgg]("http://www.newegg.com/Wired-Routers/SubCategory/ID-28?Order=PRICE").  Read the reviews.

---

### Post by Iowan on 2013-03-30
I have a separate Ubuntu box set up as DHCP/DNS server. I disabled the DNS/DHCP server in my router.
( I also bought a used DLink WRT-54GL with Tomato ... although I haven't put it online, yet.)

My first router was a floppy-based Freesco dial-up machine.

---


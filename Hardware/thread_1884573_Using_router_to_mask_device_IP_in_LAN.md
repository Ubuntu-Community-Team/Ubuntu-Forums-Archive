---
title: "Using router to mask device IP in LAN?"
date: 2011-11-21
forum: Hardware
---

### Post by xianbei on 2011-11-21
Hi! Thanks for reading my post.

I'm looking to connect to TWO devices that have the same hard-coded IP address: 192.168.0.1

I am thinking that this may be possible with two routers, each with an independent IP address;

PC --> Router1 --> Device1(192.168.0.1)
........................|
.........................--> Router2(192.168.0.2) --> Device2(192.168.0.1)
........................|
.........................--> PC(192.168.0.3)

Does this approach make sense? If so, any tips on router setup would be most appreciated.

Thanks!

---

### Post by An Sanct on 2011-11-21
Hello! :)

What kind of a device uses a hardcoded IP (IPv4 even!) address???????

Well, it should be possible, with the following configuration:

a: router1, IP 192.168.1.3
b: router2, IP 192.168.1.4
c: computer, IP 192.168.1.4
d1: strange device 1, IP 192.168.0.1
 d2: strange device 2, IP 192.168.0.1

all have Netmask 255.255.0.0 (two 0s, to extend the network!)
if possible, set the gateway of one of the routers to the other routers IP, set c, d1 and d2's gatewat to this same IP too.

It was a long time ago, when I last ASCII doodled, so I will just kind of comment on what has to be connected to what...

d1->a
d2->b
a->b
c->b
b->internetZ

Now :) theoretically, this should work :)

---

### Post by xianbei on 2011-11-28
Thanks An Sanct!

The device is for wind resource measurement. I don't technically have root access to change the IP address for configuration access.

For internet access, the device allows Dynamic IP.

I'll give this a try and report back!

---


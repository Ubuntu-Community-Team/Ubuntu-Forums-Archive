---
title: "Remastered alternate CD install - alternate lan driver?"
date: 2009-01-15
forum: Hardware
---

### Post by bazzer on 2009-01-15
OK, so the new motherboard I have doesn't have a lan driver that works on the Alternate Install CD. How do I get the initrd.img from [this thread]("http://ubuntuforums.org/showthread.php?t=843398") 'into' my remastered CD?

Please help!

---

### Post by bazzer on 2009-01-15
Just a thought, I'm trying to remaster 8.04, I think 8.10 will work, can I copy the lan driver from the 8.10 CD to the 8.04 CD or is that way to simple?

---

### Post by bazzer on 2009-02-03
Bump. Oh the shame.

---

### Post by bazzer on 2009-02-04
maybe some more information?:

It would appear it's a realtek r8169 or similar, on the motherboard, Intel G31 based.

The install stops at the dhcp stage, no dhcp leases are found, presumably because the driver has already loaded as part of the vmlinuz on the disc itself.

So, is there an 'append' I can apply to tell the kernel to load a different LAN driver?

---

### Post by fruit003 on 2009-12-23
I don't understand why your or Google would want to release a Google product to the public that would be mostly useless to the public. I understand that a lot of people like using Google's services, but Google is not a lifestyle brand beyond search. Their services are all built on data organization and search, not operating systems. I don't want crappy Google boxer shorts: I want better Google search, and that's what we're all getting, and I'm glad that Google isn't doing otherwise except as as jokery.
==========
[gmc envoy wheel bearing](http://www.carpartswarehouse.com/gmc-envoy-wheel-bearing.html)
[importing car to canada](http://www.vehicleexporting.com/)

---


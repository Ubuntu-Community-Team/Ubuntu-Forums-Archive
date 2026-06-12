---
title: "Ubuntu with UnionFS"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by SnappyU on 2009-05-01
Hi all,

Having used the eeepc 701/4g with default Xandros OS, I wonder if we can use Ubuntu with UnionFS.

I would like to set it up as follow:

/dev/sda1 - root (system, readonly)
/dev/sda2 - root (user, readwrite)
/dev/sda3 - home (system, ro)
/dev/sda4 - home (user, rw)

Can I "glue" sda1+sda2 and sda3+sda4 so that I can quickly do a system restore to whatever sda1/3 is?  This is what Xandros is doing, without the separate home partition.

Further, when I upgrade or install a new version of Ubuntu, I will first test it by installing it over sda2 and if it works and I like it, I will install to sda1 and it becomes the permanent base system that I restore to.

So, how would I do this?  
Or is it not possible?  If it is not possible, why?
Do I need sda1 & sda2 to be identical in size?  How about sda3 & sda4?

Many thanks!

---


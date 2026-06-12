---
title: "USB Hard drive how to?"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by pinkpanther_bc on 2007-02-01
Just got a 250 gig external HD, and need a little guidance.

I am going to use the HD for back up from my linux and a Mac.
What file system should i use?
Should i install a Ubuntu os on the HD etc.
What is the best way to do this?

Thanx:)

---

### Post by dan_kent on 2007-02-01
One option would be to format the drive as ext3 of fat32, nount it and create a samba share on it so that the mac and linux box would be able to access it via a network if you have one.
Failing that i'd just format it as Fat32 and you should be alright, Linux will read HTFS but it can take a bit of fiddling.

---


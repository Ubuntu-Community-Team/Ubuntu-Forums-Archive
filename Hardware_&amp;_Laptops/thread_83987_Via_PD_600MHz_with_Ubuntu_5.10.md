---
title: "Via PD 600MHz with Ubuntu 5.10"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by James Mansion on 2005-10-30
Weird - but I've had this system run Fedora 3, Fedora 4, and slackware.  And FreeBSD and PCBSD.

But Ubuntu locks - not immediately but after a short-ish while.

Seems to happen most reproducably when I select a new package to add in Synaptic.

Happens with the default kernel, also with a local kernel with lots of devices removed and compiled for Via C3.  (Kernel for C3-2 bombs immediately).

Have you heard of anything?

First hang I had was during second stage of installation before X was started, so I don't think its X server related.

I'm rebuilding with 'generic pentium' now, and will try to find time to get a raw kernel.org kernel 2.6.14 kernel.

I really hope this is going to work, because on my Portable under VMWare I'm really enjoying it.

James

---

### Post by ssam on 2005-11-12
i think i am getting this too. on a via epia MII

i think it is slightly x related, because it will run for days if x is not started. (i mostly log into my epia from another machine so it does not have x running)

---


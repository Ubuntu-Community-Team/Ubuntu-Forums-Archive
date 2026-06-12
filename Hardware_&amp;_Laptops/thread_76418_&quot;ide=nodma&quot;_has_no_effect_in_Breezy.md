---
title: "&quot;ide=nodma&quot; has no effect in Breezy"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by blujay on 2005-10-15
My old, quirky laptop's DMA support doesn't get along with Linux.  There are minutes-long timeouts in the boot sequence, complaining about DMA timeouts, etc.  With Hoary, "ide=nodma" added to the kernel params fixed it completely.  With Breezy--which nicely copied over the kernel params from the old kernels--"ide=nodma" in 2.6.12 does nothing.  Also plain "nodma" does nothing.  As a result, every bootup takes a REALLY LONG TIME.

I've Googled and searched here, but I can't find anything about those kernel params in Breezy or 2.6.12.  Can't find anything in the Wiki, or release notes.

Any help?  :(

---

### Post by blujay on 2005-10-15
Filed a bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17871](http://bugzilla.ubuntu.com/show_bug.cgi?id=17871)

---


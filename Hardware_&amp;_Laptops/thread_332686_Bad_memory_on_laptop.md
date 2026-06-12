---
title: "Bad memory on laptop"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by broy55 on 2007-01-06
I was given a Gateway laptop with bad on-board memory. There is no way to fix it other than replacing the mother board which is too expensive. I found that the bad region is just above the 380mb mark. I was hoping I could install Linux on this laptop but somehow bypass the bad memory region. I found some info on using the 'mem=' function and was wondering if anyone had any experience with it? Is there anyway to simply isolate the bad region of memory in Linux?

---

### Post by RandomJoe on 2007-01-06
I've never done it (don't have any machines with bad RAM anymore, but was considering it at one time) but there is the BadRam kernel patch.  [http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/)

Not sure how you would get the system installed in the first place to then get a patched kernel running.

---

### Post by broy55 on 2007-01-06
I was able to install Fedora using the 'linux mem=380M' switch. I couldn't figure out a way to do the same in Ubuntu though. The 'badram' patch looks promising but I would need to install Debian. Maybe I'll give that a try. I has hoping to use Ubuntu since I'm still a rookie with Linux.

---


---
title: "SSD w/ TRIM but. . . &quot;Limit 8 blocks&quot;?"
date: 2011-06-20
forum: Hardware
---

### Post by wwitzke on 2011-06-20
Hello everyone,

I just upgraded my laptop with an Intel 320 series SSD. Intel claims that it supports TRIM, and indeed when I check hdparm -I, I do see that Data Set Management TRIM supported has a star by it. However, I also see that there is an additional note - "limit 8 blocks".

I have enabled TRIM by mounting my drive with the "discard" option, and everything appears to be working fine. In fact, it's quite a lot faster than my older SSD that did *not* support TRIM. However, the "limit 8 blocks" note has been bothering me, and I have been having trouble finding any information about what this means, or whether this could cause problems.

Does anybody know if "limit 8 blocks" will cause any problems with the 11.04 Linux kernel (2.6.38-8) implementation of TRIM support? Does anybody even know what "limit 8 blocks" really means?

Thanks!

Wayne

---

### Post by psusi on 2011-06-20
It sounds like it means you can only trim 8 blocks at a time.  It shouldn't be a problem.

---


---
title: "mount after kernel upgrade"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by bastupungen on 2006-09-26
Hello!
I was just going to write an long post about mounting my sata drives since upgrading the kernel to 2.6.17**. Through the 2.6.15 way of mounting, using the sata device /dev/sdb1, i could not mount anything, except the system drive, automaticly at boot. But through sheer luck i found an small post that said my drives may be called /dev/evms/sdb1. This was true and now everything is fine.

But, WHY? was this information not easily availible through some kind of readme or local information. It can't really be that hard to check what, commands, paths, etc etc, have been changed with this new STABLE!! kernel, perhaps right after the kernel compilation.

Anyways, I got really frustrated by this after futile searching the internet for hours for an solution. And then finding it in a LITTLE post in this forum made me, well.. disappointed.

Anyhow, the main "question" of this post is WHY was this changed, and if the change was neccessary then why not make this public information?

Sorry for ranting, but these kind of things are frustrating and one of the reasons why linux should NOT go mainstream.

---


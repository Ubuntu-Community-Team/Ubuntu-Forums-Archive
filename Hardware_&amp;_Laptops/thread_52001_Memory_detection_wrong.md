---
title: "Memory detection wrong?"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Grischgl on 2005-07-26
Hi guys,

I just installed Ubuntu 5.04 on my system and noticed that it didn't detect all my RAM.
I have 1.5GB (which is used without any problem by my WindowsXP installation), but /proc/meminfo and free tell me that I only have 906660 kB of memory?!

What should I do? Is there some way to tell Ubuntu the real value?
 :?

---

### Post by heimo on 2005-07-26
I remember others having the same problem and solution was to install processor specific kernel (easy to do) and possibly using kernel parameter (editing one text file). For more details on this, search the forum using keyword 906660 and you'll find couple threads discussing the problem and solutions.

---

### Post by TSJason on 2005-07-26
Hi,

 Affirmative on heimo's thoughts. You need a kernel running with support for the 4Gb range of ram. Without that anything bigger than 1Gb won't be recognized.

---

### Post by Grischgl on 2005-07-27
Thanks!
It works now!

Didn't think that installing another kernel would be this easy.
:)

---


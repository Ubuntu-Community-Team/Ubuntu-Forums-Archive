---
title: "wireless card disappeared"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by banditti on 2005-06-09
ath0 is gone.  If I do ifup ath0, it says it isn't valid.  How do I get it back?

---

### Post by banditti on 2005-06-10
I fixed it.  Maybe this will help someone else.

I upgraded my kernel to 586 to take advantage of my processor and my memory and doing so, I forgot to do the following:

apt-get install linux-restricted-modules-$(uname -r)


Worked like a champ.

---

### Post by Vorian on 2005-06-27
[QUOTE=banditti]I fixed it.  Maybe this will help someone else.

I upgraded my kernel to 586 to take advantage of my processor and my memory and doing so, I forgot to do the following:

apt-get install linux-restricted-modules-$(uname -r)


Worked like a champ.[/QUOTE]


apt-get install linux-restricted-modules-$(uname -r) did not work for me
anyone else have an idea?

---


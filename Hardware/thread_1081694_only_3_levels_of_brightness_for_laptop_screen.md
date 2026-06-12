---
title: "only 3 levels of brightness for laptop screen"
date: 2009-02-26
forum: Hardware
---

### Post by TimDaniels on 2009-02-26
With Ubuntu (8.04) there are only 3 levels of screen brightness for my Dell XPS M1330 laptop:  0%, 50%, and 100%.  Under Vista, there are more levels.  Is there a parameter to set for Ubuntu that allows more levels of screen brightness?

*TimDaniels*

---

### Post by TimDaniels on 2009-02-27
"biocorp" in the Dell Support group had the answer:

put "blacklist video" in /etc/modprobe.d/blacklist

That gives 7 levels of brightness instead of just 3.

*TimDaniels*

---


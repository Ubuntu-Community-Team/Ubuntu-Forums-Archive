---
title: "Advice needed on mounting /tmp to tmpfs"
date: 2008-08-28
forum: General Help
---

### Post by treehouse on 2008-08-28
I read some advice saying to mount /tmp as tmpfs to increase performance while manipulating audio. I am worried, however, that I'll either run out of memory or /tmp space since I'm only running 256mb RAM with a 750mb swap. I would re-partition my swap, but it's on my OS drive and I'm not sure how to do it non-destructively, plus I'd still only have the 256mb of real RAM and I don't know if that'll cut it.

Advice?

---

### Post by waster on 2009-03-27
if you really can't get more RAM in the box, then I still wouldn't mess with tmpfs - it'll just make everything else swap more.

try changing swappinness instead, by moderate amounts. benchmark it, or don't bother, as the defaults are usually very good in the first place.

---


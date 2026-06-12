---
title: "Memtest fails, what does it mean?"
date: 2008-12-31
forum: Hardware
---

### Post by Mozork on 2008-12-31
Hi,

I tried to set up Intrepid Ibex on my Dell Inspiron 6400 Laptop, so I burned a Live CD, checked whether the CD was valid with the checker on the Live CD, which it was, but halfway through the installation process (at about 25%) the application told me that the process could not be continued and that either my CD or HD was faulty.
The problem is now, that I tried it with two different CD's (the other being a Hardy Heron Live CD) of which both passed the CD check and I also tried to install ubuntu on my (very recently bought) external HD which failed also.
I started searcing on the internet for similar phenomenons and found someone having had the same problem and having it solved by unplugging some of his RAM.
So I ran the Memtest on the Live CD and it got me a lot of errors.
Now this is what confuses me: How can the Live CD work (it operates solely on memory from what I know) ans still my memory be faulty, and why does the Live CD work but I cannot install ubuntu?
An how can I possibly fix this?

---

### Post by jrusso2 on 2008-12-31
Its possible your not using that memory.  Take out the strips that have the most errors and try it.

---

### Post by brandon88tube on 2008-12-31
Its possible you have some hardware that is conflicting with the system and is giving you those errors.

---

### Post by Mozork on 2008-12-31
Thanks a lot.

I switched both 1GB RAMs and the error still occured in the first part, so the problem must lie with the motherboard. When I' remove the RAM from the first slot everything is fine and I succeeded installing Interpid, so thanks a lot.

---


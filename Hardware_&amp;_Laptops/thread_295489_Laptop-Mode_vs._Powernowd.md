---
title: "Laptop-Mode vs. Powernowd"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by davebed on 2006-11-08
I have noticed now, after enabling Laptop-mode-tools, that once it engages (after AC has been removed) and it lowers the CPU freq., the CPU freq soon jumps back up to full. I susspect this could be due to Powernowd taking controll of the CPU freqency.
Could this be so?  How could I trace this?

In general, there seems to be some overlap in the funcionality of Powernowd and Laptop-mode-tools. I'm quite new to Ubuntu/linux and would appreciate someone laying out the differences between the two for me.

Many thanks.

Dell Inspiron e1505
T2300e 1.66GHz dual core CPU
2 GB RAM
7200 rpm HD
7200

---

### Post by suoko on 2007-10-28
I noticed the opposite on my asus A6:
even if I disable powernowd service, the cpu continues to behave as it was enabled since freq scales anyway (even with AC). 
I guess laptop-mode enables freq scaling by default. Is this true?
Moreover I noticed that it continuosly scales up and down even if I run heavy tasks causing a slow "behaviour".

---


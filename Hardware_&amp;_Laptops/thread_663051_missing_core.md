---
title: "missing core?"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by buddah1620 on 2008-01-09
When I was running XP pro and brought up the task manager, you could see the read out of both of my AMD X2 cores.  When I'm in Gutsy and look at system monitor, it only has 1 read out for the cpu.  So, is Gutsy only seeing one of my 2 cores?  How could I know for certain that it is utilizing both cores?

Thanks

---

### Post by buddah1620 on 2008-02-12
Guys?  Anyone?

---

### Post by noremac on 2008-02-13
Run something that uses 100% CPU. Such as Folding@Home for example. 
F@H will only utilize one core at the 100%, so the stats will measure that at 50% if everything is working properly. 

-C

[edit] Mine shows only one as well, yet I know there are two working due to the F@H idea) [/edit]

---

### Post by buddah1620 on 2008-03-31
what is that program?

---

### Post by mcduck on 2008-03-31
Just open a terminal and run "cat /proc/cpuinfo". If the output shows 2 cores (numbers 0 and 1) everything is working properly.

---


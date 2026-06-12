---
title: "Constant &gt; 40% memory load (hp nx9010)"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by Reggie on 2005-12-24
I have a constant memory load of 40% or more .. now it's 100% and I'm not running anything else then firefox. When I close it it's still 90% or so ... is there any way to free some memory ?

---

### Post by localzuk on 2005-12-24
Hi,

Linux uses a different method of memory management than windows. It is not uncommon to see 100% usage of physical memory at all times. Do not worry about this as applications will be able to operate as normal, without slowdown. The way it works, if I recall correctly, is that applications are assigned memory which they keep hold of even after having finished using it. This is to speed up the process of getting more memory should they need it again (which is based on the idea that if you have used the app once, you may use it again). If another app wants memory and there is none marked as free, some of the unused memory from the other apps is assigned to it.

(I am trying to remember a comp-sci lecture :) )

Hope this helps

---

### Post by Reggie on 2005-12-27
Yes, I've noticed that indeed my programs run smoothly, even when CPU is 90%. I'll read some more about it. Thnx !

---


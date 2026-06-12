---
title: "swapping"
date: 2020-05-27
forum: Hardware
---

### Post by bardiamgtgc on 2020-05-27
im running a ubuntu 18.04 on my server and im running out of memory 
i was thinking to specify swap to only certain pkgs not all of them or just go and upgrade my plan for 8gb 
is there anyway to do that? like make apache and java use swap

---

### Post by TheFu on 2020-05-28
No. Swap (virtual memory) is an OS resource.  Java can be tuned to control memory use. About 15 yrs ago when we used Java, I would usually need to increase the heap amount available.
To reduce apache RAM use, limit the modules, limit the workers, and scale sideways as needed. Often, apache becomes network-bound before it is CPU or RAM bound, but that assumes a reasonable server size.

---


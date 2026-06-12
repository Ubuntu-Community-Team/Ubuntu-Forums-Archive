---
title: "How big is my swap space?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by jhhoward on 2007-03-26
I've been using Edgy for quite a while now, but I've never managed to get suspend or hibernate to work reliably on my laptop. I was just wondering if the reason that hibernate won't work is something to do with how big my swap partition is. If it isn't big enough to fit my RAM image in then it won't work right? How do I check how big my swap partition is?

Thanks,
James

---

### Post by taurus on 2007-03-26
Applications -> Accessories -> Terminal
```
free
```

---

### Post by jhhoward on 2007-03-26
Such an obvious answer I just couldn't think of the program name!
So this is what I got:
             total       used       free     shared    buffers     cached
Mem:       1034152     444888     589264          0      14780     215604
-/+ buffers/cache:     214504     819648
Swap:      1020088          0    1020088

meaning that my swap space is slightly smaller than my RAM. Could this be the reason that hibernate doesn't work? I'm not sure if I can rely on this theory, as where would the swapped memory go to?

---


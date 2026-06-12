---
title: "PAE kernel not seeming to access more than 3gb RAM"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by practic on 2009-11-11
I have a fairly modern computer (Intel Core2Duo E7200) and recently did a fresh install of Ubuntu 9.10. A few weeks later I decided to up the RAM from 2gb to 4gb. Naturally, the 32-bit Ubuntu only saw about 3gb of the RAM.

I read that installing the PAE server kernel would allow me to access all the RAM. I did that (from synaptic), and it seems like I am now using that kernel (all other kernels were uninstalled, so I only have PAE in the grub list).

However, every utility I've tried, still tells me that I've only got about 3gb of RAM. Running "dmidecode" and looking under the ""Memory Array Mapped Address" section in value "Range Size" shows 4gb. "top", "free" and the System Monitor on the panel all show 3gb.

What gives?

---

### Post by mathieu1911 on 2009-11-28
Same problem for me, instead that I have originally 4gb of RAM (laptop LG r405). Installed PAE on ubuntu 9.10 and unistalled old generic. Still see 3gb...

---

### Post by NoaHall on 2009-11-28
Can you post the output of ```
free -m
```  for me?

---

### Post by mathieu1911 on 2009-11-28
```
root@mathieu-laptop:~# free -m
                   total       used       free     shared    buffers     cached
Mem:          3212        527       2684          0         35        228
-/+ buffers/cache:        264       2948
Swap:         1999          0       1999

```

---


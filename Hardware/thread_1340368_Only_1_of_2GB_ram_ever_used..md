---
title: "Only 1 of 2GB ram ever used."
date: 2009-11-28
forum: Hardware
---

### Post by QwUo173Hy on 2009-11-28
The computer got very slow earlier when I switched user.

I ran System Monitor, and it detects my 2GB (2 X 1GB) of ram. 1GB of ram was entirely used, and the 700MB swap was completely full.

Normally, I'd assume the second 1GB stick of ram wasn't working. But since System Monitor actually detects that I do have 2GB, I'm confused!?

Anyone know what might be going on?

---

### Post by NoaHall on 2009-11-28
Open a terminal, and type ```
 free -m
```
That's a better idea of what's being used.

---

### Post by QwUo173Hy on 2009-11-28
Thanks NoaHall. That gives me:
```
             total       used       free     shared    buffers     cached
Mem:          2007       1935         71          0          4       1148
-/+ buffers/cache:        782       1224
Swap:           78         78          0

```

Which implies that most of my memory has been used at some stage by the system. Would that be correct?

---

### Post by NoaHall on 2009-11-29
Yes, it shows that all the RAM is being used(which is good) but it also shows your swap partition is under 100MB big. No wonder it's all being used, if it's that small. Any reason for it being that size? You may/may not get better performance if you increase it a little.

---

### Post by QwUo173Hy on 2009-11-29
Ah okay - I thought that with 2 gigs of ram, I wouldn't even need a swap partition, so I kept it small. I can increase it and I bet I'll see an improvement.

Thanks so much NoaHall

---

### Post by iponeverything on 2009-11-29
> **jarlath said:**
> Ah okay - I thought that with 2 gigs of ram, I wouldn't even need a swap partition, so I kept it small. I can increase it and I bet I'll see an improvement.

Thanks so much NoaHall

That would have been my assumption as well. ie. with 2 gigs of ram why have swap at all..

---


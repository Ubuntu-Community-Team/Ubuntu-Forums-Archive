---
title: "too much ram usage"
date: 2008-08-20
forum: General Help
---

### Post by ..p4.. on 2008-08-20
hi..i hav just changed from windows xp to ubuntu 7.10..but it is showing 65 % ram usage on my 512 mb dual core lenevo laptop.how can i reuce ram usage without compromisisng on effects??

---

### Post by Elfy on 2008-08-20
RAM is used differently here - that's perfectly normal, your ram will be freed for current apps as it is required. Open aterminal and run

```
free -m
```

>              total       used       free     shared    buffers     cached
Mem:          1265        942        323          0         80        547
-/+ buffers/cache:        314        950
Swap:          956          0        956

As I understand it the buffers/cache line shows it best - I have 314Mb in use and 950MB as cached - it could be progrmas I've used recently or things linux expects me to use. IF I was using a lot of memory then swap would be being used.

But the thing is not to worry to much.

Welcome to the forum as well :)

---


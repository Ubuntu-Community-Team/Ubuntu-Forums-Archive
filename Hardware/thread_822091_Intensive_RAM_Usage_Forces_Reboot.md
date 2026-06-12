---
title: "Intensive RAM Usage Forces Reboot"
date: 2008-06-07
forum: Hardware
---

### Post by TroyDowling on 2008-06-07
I haven't noticed this before until I installed the newest release of Hardy onto my HP Pavilion dv9013ca laptop. When I first boot the computer, my memory use is nominal and everything works perfectly. However, over the span of hours, it seems as if Ubuntu caches things and never un-caches them! Eventually, my RAM usage reaches into the 90%'s or more and I am forced to reboot as everything is too sluggish to use. I've included dumps of the RAM usuages:

At Boot:
```
             total       used       free     shared    buffers     cached
Mem:       1001844     597488     404356          0      16160     284216
-/+ buffers/cache:     297112     704732
Swap:      2096472          0    2096472
```

Before reboot:
```
             total       used       free     shared    buffers     cached
Mem:       1001844     991376      10468          0        468      42068
-/+ buffers/cache:     948840      53004
Swap:      2096472     378060    1718412
```

Thanks for any help and suggestions,
Troy.

---

### Post by woodcarver on 2008-06-08
The OS obviously has a bug, try a total reload.

---

### Post by sdennie on 2008-06-08
Both of your "free" outputs look normal to me.  It looks like you are simply using too much memory and so it's causing swap to be used.  When the system begins to slow down, go to System->Administration->System Monitor and see if you notice any applications using a lot of memory.

---

### Post by TroyDowling on 2008-06-08
> **vor said:**
> Both of your "free" outputs look normal to me.  It looks like you are simply using too much memory and so it's causing swap to be used.  When the system begins to slow down, go to System->Administration->System Monitor and see if you notice any applications using a lot of memory.

Yeah, I've done that. Nothing looks out of the ordinary there either. "gnome-panel" is usually the highest with around 10MB being used. I'm not loving the idea of a total reload, but I guess I may have no other choice. Ubuntu Hardy has been the worst release ever in my opinion, I jus keep having issues with it. Not like beautiful Gutsy... Unfortunately, Gutsy won't run on my Pavilion. Does anyone think it would be worth waiting for 8.04.1?

---


---
title: "Memory Support"
date: 2008-10-25
forum: Hardware
---

### Post by Mjsch on 2008-10-25
I have just installed Hardy 8.04 LTS, on a lower-grade computer of mine. I have 512mb RAM installed and a 1.4Ghz processor (AMD). Ubuntu is not recognizing all of my RAM, it tells me I only have 218MB installed... I use on-board graphics also. 


Here is the output of my memory: (sudo free)

             total       used       free     shared    buffers     cached
Mem:        223172     207324      15848          0       4304      55952
-/+ buffers/cache:     147068      76104
Swap:       578300     198812     379488

Any thoughts. I am kind of new to Linux, would prefer not to re-compile my kernel if at all possible.

---

### Post by cariboo on 2008-10-25
It looks like you have a bad ram module, or your video card is sharing a lot of the ram, my vote would be the graphics adapter. Go into the BIOS and you should be able to change how much ram your on board video adapter uses.

Compiling the kerenl won't help with this problem :) I've been using linux for about ten years and I haven't had to complie a kernel since my dual cpu server died about 4 yearts ago.

Jim

---

### Post by Mjsch on 2008-10-25
It is definitely not a bad ram module. I ran memtest, and memtest recognizes all of it. I will try the BIOS now, but I don't know exactly what's going to happen.

Thanks

---

### Post by ardvark71 on 2008-10-25
> **Mjsch said:**
> It is definitely not a bad ram module. I ran memtest, and memtest recognizes all of it. I will try the BIOS now, but I don't know exactly what's going to happen.

Thanks

How much memory is your graphics chip set to use? If your copy of Ubuntu is sharing it, it would amount to 294 MB's of video memory. :confused:

Best Regards...

---

### Post by Mjsch on 2008-10-26
I do not know what I did, but I reset my computer this morning and now it recognizes everything...

Thanks anyway

---


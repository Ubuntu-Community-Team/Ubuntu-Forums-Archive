---
title: "Thinkpad T60 suddenly won't wake up"
date: 2008-07-04
forum: Hardware
---

### Post by diverse_izzue on 2008-07-04
I have a Thinkpad T60 that used to suspend to RAM just fine. Recently, it doesn't work anymore, I just get a black screen after wakeup. I'm not sure what change I did to my system to break it. I recently installed the NetworkManager 0.7 packages from the PPA, maybe that caused the problem. On the other hand, after downgrading to the 0.6.6 package from Hardy, it still won't work.

I followed the debugging guide in the wiki ([https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)) and found out the following:

[   18.230778]   Magic number: 0:731:232
[   18.230780]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:76
[   18.230796]   hash matches device ttyv2

Now, that doesn't help me, because ttyv2 is not a module. Any ideas?

---


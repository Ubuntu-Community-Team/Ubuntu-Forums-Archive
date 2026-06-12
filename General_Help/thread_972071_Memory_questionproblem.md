---
title: "Memory question/problem"
date: 2008-11-05
forum: General Help
---

### Post by james.king@4act.com on 2008-11-05
I have 3.8GB of ram. Twice today I have chosen to reboot because my memory in use by programs, as reported by system monitor, (not swap) has almost reach its limit. I closed all of my open windows and it only freed up a small percentage of that memory.When I look in the processes tab of System Monitor (set to list all processes) the amount of memory in use could not add up to over 1.5GB of memory. 

Yesterday I installed monodevelop and a few of the most recent updates.

Is it possible that some process managed to request a chunk of memory that was not reported by system monitor and that was not freed after killing it?

Thanks

---

### Post by CatKiller on 2008-11-05
Linux uses memory in a different way than you are probably used to. It uses the principle that empty memory is wasted memory. Whenever you load a file, it remains in RAM until that RAM is actually needed for something else. If you need that file in the future, it can be quickly retrieved from the RAM without the incredibly long wait for a read from the disk. If that file isn't needed in the future, it hasn't cost you anything, since the memory has to be powered even if there's nothing useful in it.

---

### Post by james.king@4act.com on 2008-11-05
My apologies. 

In my post I said "not swap". However, I meant "not cache." I use the system monitor plugin for gnome panel and it tells me which memory is in use by programs and which is in use as cache. It said that over 90% was in use by programs and that the leftover 10% was in use as cache.

---


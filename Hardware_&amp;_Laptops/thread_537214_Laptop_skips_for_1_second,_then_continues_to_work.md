---
title: "Laptop skips for 1 second, then continues to work"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by leonidas666 on 2007-08-28
Hi, 
I have a hp nx 5000 laptop (kubuntu, pentium m 1,5GHz, video: i810, i'm using the built-in wlan). Eveything is running well, the only thing is that seemingly randomly the laptop will freeze (even the mouse does not move anymore)  for around 1 seond, and then it continues to work normally. Most of the time this happens twice in short succession, e.g.:
freeze (1sec), work (2 sec), freeze (1sec) and then it works again for some time (maybe 30 minutes or one hour).  
i checkd dmesg right after one freeze, but there was no extra output. Somehow i have the hunch that this problem is related to the requency scaling of the cpu because the freezes seem to correlate with heavy cpu activity, although i could be completely wrong also (the freeze is random, i did not find a way to trigger it directly).  I already tried setting the cpu frequency scaling policy in the kde power manager dialog to different setting but it did make any change.

Any ideas how i could find out the reason for the freeze?

---

### Post by jnorthr on 2007-08-28
System>Administration>System Monitor gives some nice graphical panels showing whats up doc. Could this be swap file activity ? How big is ur swap file 2 or 3 x ram is better. My swap file usage goes up to 95% under heavy load.

---

### Post by leonidas666 on 2007-08-29
Extra Info: I have 512 MB Ram, 1 GB Swap-Partition.
I used the Kde System Guard (did you mean that, jnorthr?) to check the CPU usage after one freeze. I did not see anything special in the memory and swap usage. The cpu usage had a big spike for "system load".  

By the way, when the freeze occurs, the laptop does not do anything. No HDD activity, nothing changes on the display. That's why i don't think it has anything to do with swap.

---


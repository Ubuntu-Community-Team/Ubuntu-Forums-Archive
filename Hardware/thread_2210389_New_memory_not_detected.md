---
title: "New memory not detected?"
date: 2014-03-10
forum: Hardware
---

### Post by PDA1 on 2014-03-10
I'm running Ubuntu 12.04 on an Acer Aspireone ZG5 and just plugged in 1g of ram on the motherboard.

I appears to be that the new memory isn't detected. Here's the free -m report;

```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:           483        414         69          0         14        188
-/+ buffers/cache:        212        271
Swap:         2444         47       2397


```

The system is up to date.

Can you tell me why free -m doesn't show 1g of ram? 

How can I fix it so that it recognizes it?

---

### Post by varunendra on 2014-03-11
Is the memory detected by BIOS? Please check there first. If BIOS reports the added size, try -
```
sudo lshw -C memory
```
Or
```
sudo dmidecode -t memory
```

Although I can't think why 'free' command won't recognize if it is detected by the OS, so it seems to me that it wasn't detected by the BIOS at all.

---

### Post by PDA1 on 2014-03-11
The Bios doesn't detect the new ram. It still just says there's 500 meg.

My guess is the memory's incompatible with the machine.  What'd I expect for$12 including shipping?!

But, the machine truly is much faster....just don't understand why.

---

### Post by varunendra on 2014-03-11
> **PDA1 said:**
> But, the machine truly is much faster....just don't understand why.

Illusion? Power of suggestion? :D

Although this sure is weird, because as per my knowledge and experience so far, a motherboard shouldn't even boot with an incompatible memory module. Maybe yours has some mechanism to simply disable a memory bank in that case? (never heard of such a 'feature', and it sounds silly to myself)

---


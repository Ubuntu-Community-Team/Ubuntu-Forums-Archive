---
title: "16 Gb RAM, Only 4 Gb Detected"
date: 2011-11-11
forum: Hardware
---

### Post by robson9776 on 2011-11-11
Hi guys...

I have 16 Gb memory module installed on my PC (Ubuntu 11.10). actually 4 Gb x 4 pcs. and when I checked using :

$ sudo dmidecode --type 17

I found there are 4 memory installed with different serial number, etc. but when I try to see how many free memory do I have using this command :

$ free -m

the output is like this :

             total       used       free     shared    buffers     cached
Mem:          3015        312       2703          0         17        140
-/+ buffers/cache:        154       2861
Swap:        16363          0      16363

it means, my Ubuntu only detect 4 of 16 Gb memory I have, right? if so, how to enable all my memory module?

thanks!

---

### Post by dashnak on 2011-11-11
Yo should probably check if your processor is 32 or 64 bits. If it's 64 bits and you installed a 32 bit version of ubuntu, you'll only see those 4 GB

---

### Post by robson9776 on 2011-11-11
> **dashnak said:**
> Yo should probably check if your processor is 32 or 64 bits. If it's 64 bits and you installed a 32 bit version of ubuntu, you'll only see those 4 GB

Geezz you're the man, bro!!! I just realize that I installed 32 bit Ubuntu on my 64 bit Intel processor. Thanks bro!!!

---

### Post by djsephiroth on 2011-11-11
Instead of redoing everything, you can always switch to a PAE kernel. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by dashnak on 2011-11-11
You're welcome! :) Glad I could help.

---

### Post by MoreOrLess on 2011-11-11
> **djsephiroth said:**
> Instead of redoing everything, you can always switch to a PAE kernel. [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

No reason for that on a relatively fresh install. It may allow the kernel to see more RAM, but it won't let processes use more than 2GB of RAM (and it won't take advantage of other 64-bit optimizations).

---


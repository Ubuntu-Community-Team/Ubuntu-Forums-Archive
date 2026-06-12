---
title: "Memory usage?"
date: 2010-10-04
forum: Hardware
---

### Post by isecore on 2010-10-04
I'm wondering about this with memory usage.

I have 4 gigabytes of RAM and I run Ubuntu 64-bit. Yet seemingly, Ubuntu refuses to take advantage of the memory. It recognizes it, but likes to leave about a gigabyte free. Only when I really load up on applications can I push it up to about 3.5 gigs of usage - and then we're talking really loaded. Two virtual machines, Google Earth running, etc.

Currently memory usage according to htop is a smidgen over 3 gigabytes. This is annoying since right now my computer is spending a lot of time moving stuff into and out of swap, which means that the performance is less than stellar. Why is this? Why not use the gigabyte of memory that actually is available instead? To me this makes very little sense.

I know quite a lot about computers, but this has got me stumped is this due to reserved memory and all that hoopla that affects 32-bit systems trying to access four gigs of RAM? I'm planning on adding another four gigs to my system, which of course should alleviate this a bit, but will that then mean that my computer will ignore two gigabytes of memory rather than one?

I'm running Lucid x64 on an AMD Phenom II 955 @ 3.2 Ghz with 4 gigs of ram. It's all patched up with the latest updates. If you need any more information, I will be happy to give it to you. I'm just wondering why my computer ignores a quarter of my memory most of the time, and only uses parts of that ignored quarter when really pushed.

Any help in gaining insight into this is greatly appreciated!

Oh, and I've set swappiness to 0, if that makes any difference.

---

### Post by mikewhatever on 2010-10-04
The tendency to use swap in Linux is governed by the value of swappiness. The higher the value, the higher the tendency to swap; it's set to 60 by default.  
cat /proc/sys/vm/swappiness

In your case, lowering the value of swappiness to, say, 10 would make sure more RAM and less swap is used.
Here is a 'howto change it' guide -> [http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

---

### Post by isecore on 2010-10-04
Yes, thank you, I know about swappiness. 

Do note though that I've set it to 0. As far as I know that means that it should not try to swap out at all. Or am I gravely mistaken and is 10 actually a better value?

> **mikewhatever said:**
> The tendency to use swap in Linux is governed by the value of swappiness. The higher the value, the higher the tendency to swap; it's set to 60 by default.  
cat /proc/sys/vm/swappiness

In your case, lowering the value of swappiness to, say, 10 would make sure more RAM and less swap is used.
Here is a 'howto change it' guide -> [http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_](http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_)

---

### Post by mikewhatever on 2010-10-04
Interesting, can you post the outputs of 

cat /proc/sys/vm/swappiness

free -m

swappiness=0 is more agressive then swappiness=10, yet it's neither better or worth.

---

### Post by isecore on 2010-10-04
I'll set it back to 10 then and see what happens. That's what I usually keep it at, but I thought 0 would be somewhat more aggressive. But perhaps it's counter-productive to be too aggressive.

EDIT: This is confusing.

free -m reports

```
             total       used       free     shared    buffers     cached
Mem:          3961       3671        290          0          2        665
-/+ buffers/cache:       3003        958
Swap:        11603         19      11584
```

but htop reports that 3024 of 3961 is in use. Thus a discrepancy of something like 900 megabytes.


> **mikewhatever said:**
> Interesting, can you post the outputs of 

cat /proc/sys/vm/swappiness

free -m

swappiness=0 is more agressive then swappiness=10, yet it's neither better or worth.

---

### Post by mikewhatever on 2010-10-04
According to 'free -m', most of the RAM is used, with only 290MB left free. Note that 665MB is used to cache stuff and 3003MB to run programs.

---

### Post by isecore on 2010-10-04
Yes, that much is obvious. But why is htop (a nicer version of top) insisting that only about 3025 megabytes is in use? Which of them is right?

I always trusted htop for brief system monitoring but it seems more like it's a lie. Or possibly not optimized for 64-bit systems or whatever.

> **mikewhatever said:**
> According to 'free -m', most of the RAM is used, with only 290MB left free. Note that 665MB is used to cache stuff and 3003MB to run programs.

---

### Post by cascade9 on 2010-10-05
[LEFT]They are both right. 

htop is showing all the 'free' memory, and free /m is showing how much of the 'free' memory is being used for cache/buffers (which can be swapped out or removed totally if the RAM is needed for something else)
[/LEFT]

---

### Post by isecore on 2010-10-05
That does make quite good sense. The memory cache is of course not of much importance, and unused memory is wasted memory. But I still wondery why it does't use that memory (the gigabyte that exists according to htop) for applications rather than cache instead?

Which is faster? Allowing applications the memory they need, or use it to cache stuff instead?

> **cascade9 said:**
> [LEFT]They are both right. 

htop is showing all the 'free' memory, and free /m is showing how much of the 'free' memory is being used for cache/buffers (which can be swapped out or removed totally if the RAM is needed for something else)
[/LEFT]

---


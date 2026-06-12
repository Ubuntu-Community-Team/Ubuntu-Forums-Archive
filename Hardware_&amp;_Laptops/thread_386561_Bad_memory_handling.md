---
title: "Bad memory handling"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by greew on 2007-03-17
Hi all,

My laptop has started to have extremely bad memory handling. I'm using Kubuntu Edgy Eft. It seems like the memory is never flushed or something (I'm not very much into this hardware/software stuff).

I've experienced it several times now, but I'll just describe the situation today:

My computer has been turned on for 3 hours now and 960 MB of RAM is used (75MB free). I've used Eclipse and several Firefox instances, plus a few other standard low-memory-usage programs and I can really feel how the computer is getting slower and slower.

Can anybody help me by eg. telling which log files or configuration files to put up, so you can look at them or - well - just anything. I'm kind of desperate.

Best regards - and have a nice weekend all!
- Jesper

---

### Post by mcduck on 2007-03-17
No, it's most likely handled just as it should. Linux doesn't leave your free memory sitting there wasted, it uses it as disk cache instead. The memory used for cache is still available for programs to use, as cached data is dropped instantly if some program needs more memory.

To get the real memory usage, run 'free -m' in a terminal, and then look at the '-/+ buffers/cache'-line to check the real memory usage.

---

### Post by greew on 2007-03-17
Ok.. this is this output from "free -m":
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        995         15          0          3        623
-/+ buffers/cache:        369        642
Swap:         1223        147       1076

```

So.. it doesn't seems like I really need memory.. then I don't know what's wrong... my computer gets really slow when Mem: gets bigger than 850MB..

---

### Post by greew on 2007-03-18
And as it seems it has nothing to do with buffers/cache. No matter how high or low they are, the computer is still running slow.

---


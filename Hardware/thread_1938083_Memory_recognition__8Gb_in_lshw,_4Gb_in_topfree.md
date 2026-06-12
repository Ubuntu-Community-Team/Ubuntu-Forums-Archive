---
title: "Memory recognition : 8Gb in lshw, 4Gb in top/free"
date: 2012-03-09
forum: Hardware
---

### Post by hoseung on 2012-03-09
Hello,
I'm using Ubuntu 11.10 64bit. 
recently I found that top shows the memory on my box is 4Gb whereas I have 4*2Gb module on my box. I check BIOS and found BIOS itself was nor fully recognizing the memory. 
So I updated BIOS (using HDD from another box with win7) and now BIOS says 8Gb. 
And in linux, **lshw show all 4 banks are full and physical memory is 8Gb**. But still I see **4Gb in top or free**. (And also in system info)

What's going on? 

I'm not thinking of re-installing Ubuntu because too many things need to be backed-up.

---

### Post by SlugSlug on 2012-03-09
could you post output of 
```
uname -a
```

---

### Post by hoseung on 2012-03-09
> **SlugSlug said:**
> could you post output of 
```
uname -a
```


uname -a gives

3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---


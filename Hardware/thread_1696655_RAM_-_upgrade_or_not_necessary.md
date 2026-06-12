---
title: "RAM - upgrade or not necessary?"
date: 2011-02-27
forum: Hardware
---

### Post by jlparsons on 2011-02-27
I have 2gb 1333mhz ram installed on a encrypted-disk maverick installation on my laptop and an empty slot in which I could put another 2gb for not much outlay.  Question is would it make any difference?  I notice even when running all the programs I ever run simultaneously that the system monitor never shows all the memory being used, however it looks like the system uses all of it for caching so possibly there may be benefit from adding more.  The following is my "free" output:

```
             total       used       free     shared    buffers     cached
Mem:          1868       1834         34          0         24       1140
-/+ buffers/cache:        669       1199
Swap:         5475         18       5457

```

Any opinions?  Go for 4gb?

---

### Post by doas777 on 2011-02-27
I'd say you are fine as is, but I also would not restrain you from upgrading if you have the means to do so. you won;t notice any differance other than that you will have more capacity for multitasking. also having more mem for cache means that more data will be available quicker, so the speed and strenght of your HDDs comes into the equation as well. if your disks are slow, then investing in cache capacity is a good bet.

---

### Post by cchhrriiss121212 on 2011-02-27
>  Go for 4gb?
Seems pointless unless you are planning to actually use the extra RAM. I doubt you will see any performance increase.

---

### Post by jlparsons on 2011-02-28
> I'd say you are fine as is, but I also would not restrain you from  upgrading if you have the means to do so. you won;t notice any  differance other than that you will have more capacity for multitasking.  also having more mem for cache means that more data will be available  quicker, so the speed and strenght of your HDDs comes into the equation  as well. if your disks are slow, then investing in cache capacity is a  good bet.     so given that I use a 5400rpm encrypted hard disk (slow) the extra caching may be beneficial?

---

### Post by Hedgehog1 on 2011-02-28
I love more RAM; **_HOWEVER on a laptop_** - if you run on batteries - those two extra memory stick will draw some power, shortening the battery run time.

If you never really run from the battery, upgrade (which is what I think your really are hoping to hear).  If battery life is more important, stay at your current 2gig level.

:KS

---

### Post by doas777 on 2011-02-28
> **jlparsons said:**
> so given that I use a 5400rpm encrypted hard disk (slow) the extra caching may be beneficial?
yes, though since you mention encryption, it does mean that some of your data will be stored in the clear in ram. of course this is the case no matter how much ram you have unless you disable io caching. this is probably not a huge concern, but it is somthing to consider. yes in your case I would definitely consider an upgrade.

---

### Post by jlparsons on 2011-02-28
> **Hedgehog1 said:**
> (which is what I think your really are hoping to hear)


Hehehe... yup.  As long as there's good reason to think it's the case, which it seems there is.  Sold!

Thanks all!

---

### Post by KegHead on 2011-02-28
Hi!

Maximize your RAM.

I fill all of my slots to the max..my machines are crazy fast.

KegHead

---

### Post by Yellow Pasque on 2011-02-28
The RAM is usually used for caching. You still have 1.2 GB free in your example, so if that's the most you use, extra RAM will be a waste. If you have more intensive RAM usage scenarios, check the RAM while you're doing them.

---

### Post by jlparsons on 2011-03-10
Well, i upgraded and things do appear to be slightly faster.  I reset preload's cache engine, decreased (slightly) its minimum file size and increased its memory usage.  I now have the following:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3760       3696         64          0         14       2997
-/+ buffers/cache:        684       3075
Swap:         5475          0       5475

```So, caching is up hence speed is a bit better.  Not a massive difference but worth the small outlay.  Boot takes significantly longer as you would expect - the system has to load lots of cache from the encrypted drive so that takes time, but once loaded it works fine and my laptop suspends/resumes like a champ so I rarely have to reboot anyway.  I haven't noticed any difference in battery life - there will doubtless be a difference but I don't use it away from my desk enough to notice.

---


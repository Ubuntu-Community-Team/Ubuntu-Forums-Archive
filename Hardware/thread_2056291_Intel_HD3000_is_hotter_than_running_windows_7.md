---
title: "Intel HD3000 is hotter than running windows 7"
date: 2012-09-11
forum: Hardware
---

### Post by Tobo27 on 2012-09-11
Hi all!

I bought a new laptop: HP pavilion g6 1364sl 

Intel i5 2450M
ATI radeon 6400(6450 maybe)M
Intel HD 3000
Ram 4GB

Running ubuntu 12.04 up to date.

Well, I followed the instruction in [this thread]("http://ubuntuforums.org/showthread.php?t=1930450") and both video cards work well in 3D mode.
But checking cards temperatures I noticed that running windows 7 intel HD 3000 has a temperature of 40°C, under ubuntu the temperature gets to 50°C (both OS in idle)

I never had heat problems running ubuntu, actually it used to be cooler than windows, so I'm a bit worried about this thing.

What am I supposed to do? I googled around but I found nothing.

Thanks in advance
Tobo.

---

### Post by Mark Phelps on 2012-09-12
The overheating problem is due to a bug in recent Linux kernels.  So, if you ran an older version, you wouldn't have encountered the overheating problem.

You can try using Jupiter -- link below:

[http://ubuntuforums.org/showthread.php?t=1854019]("http://ubuntuforums.org/showthread.php?t=1854019")

---

### Post by Tobo27 on 2012-09-13
Thank you very much!
What version should I install? 3.0 or I have to get back to 2.9 kernels?

---

### Post by Ubunterrific on 2012-09-13
> **Tobo27 said:**
> Thank you very much!
What version should I install? 3.0 or I have to get back to 2.9 kernels?

I'd recommend 2.6.32 personally. The power analysis results posted on phoronix a while back show that it's a bit of a gem.

(Before kernel 3.0 they used to number it differently, before 3.0 was 2.6.39 etc)

---

### Post by Tobo27 on 2012-09-13
oh, sorry, I didn't know it :lolflag:

Thank you very much, I'm gonna try that kernel version, i'll let you know ;)

---

### Post by Tobo27 on 2012-09-26
Ok, still hot under "new" old kernel 2.6.32 (.39 too)

Any other suggest? I like ubuntu, and I'd rather not to use windows 7 anymore :)

---


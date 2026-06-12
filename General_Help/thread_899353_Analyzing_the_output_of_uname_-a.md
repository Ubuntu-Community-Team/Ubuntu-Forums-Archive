---
title: "Analyzing the output of uname -a"
date: 2008-08-24
forum: General Help
---

### Post by adcwoef on 2008-08-24
Hello.

When I type* uname -a* ina shell it looks like this

```

adcwoef@adcwoef:~$ uname -a
Linux adcwoef 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686 GNU/Linux

```

But what does this really mean?

Linux = OS
adcwoef = system name
2.6.24-19-server = kernel version I guess?
#1 SMP = ?
Sat Jul 12 00:40:01 UTC 2008 = ? What date is that?
i686 = processor type?
GNU/Linux = OS + programs

---

### Post by bthoward on 2008-08-24
SMP = Symmetric Multiprocessing
Just means the kernel can support multi core processors

UTC = Universal Cordinated Time (don't ask me why the characters are swapped)
UTC = GMT (grennwich mean time)  (pretty much the time in London)

---

### Post by coffeecat on 2008-08-24
> **bthoward said:**
> grennwich mean time

[Greenwich]("http://en.wikipedia.org/wiki/Greenwich"), actually, but pronounced somewhat like grennidge, which is certainly nearer your spelling. :wink: See also the Old Saxon spelling in that article.

And [Greenwich Mean Time]("http://en.wikipedia.org/wiki/Greenwich_Mean_Time").

> **bthoward said:**
> pretty much the time in London

Except during the summer ([British Summer Time]("http://en.wikipedia.org/wiki/British_summer_time")), or what's passing for summer this year. :(

---

### Post by Nepherte on 2008-08-24
i686 is the cpu architecture (you either have a 32 bit computer or you installed a 32 bit ubuntu on a 64 bit machine).

---


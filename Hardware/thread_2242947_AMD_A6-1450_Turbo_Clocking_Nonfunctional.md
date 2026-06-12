---
title: "AMD A6-1450 Turbo Clocking Nonfunctional"
date: 2014-09-05
forum: Hardware
---

### Post by Demosofpyr on 2014-09-05
The AMD A6-1450 proc operates normally at 1.0Ghz while on battery, but when plugged into AC power is capable of overclocking to 1.4.

This is roughly a 40% performance increase, accompanied by a similar 25% clock speed boost for the GPU, provided AMD's "Turbo Dock" functionality worked under ubuntu.

I've tried every power state setting I can think of while plugged into AC and running a heavy (single threaded) application like dwarf fortress, but I never see any clock speeds fluctuate above 1Ghz while using tools like cpu-g.

Searching google for this issue has turned up an archlinux bug post located here: [http://lists.freedesktop.org/archives/dri-devel/2014-June/061795.html](http://lists.freedesktop.org/archives/dri-devel/2014-June/061795.html)
but I have not been able to find any detailed fixes for ubuntu, and don't understand quite enough yet to be able to see if the archlinux post might be useful for solving this problem on my platform.

System Specs:
Dell Inspiron 3135 ([http://www.dell.com/us/p/inspiron-3135/pd](http://www.dell.com/us/p/inspiron-3135/pd))
AMD A6-1450 APU ([http://www.notebookcheck.net/AMD-A-Series-A6-1450-Notebook-Processor.92120.0.html](http://www.notebookcheck.net/AMD-A-Series-A6-1450-Notebook-Processor.92120.0.html))
4GB RAM

Ubuntu 14.04 LTS (latest patch ver, non Pre-Release)

I'd appreciate any assistance y'all could provide this perplexed learner!

---

### Post by Vladlenin5000 on 2014-09-05
Hi, welcome.

I suppose you're running standard Ubuntu with the default open source drivers - Radeon -. Have you tried the proprietary drivers already?
System settings > Software & Updates > Additional drivers tab...

---

### Post by Yellow Pasque on 2014-09-06
[http://ubuntuforums.org/showthread.php?t=2235903](http://ubuntuforums.org/showthread.php?t=2235903)

---

### Post by Demosofpyr on 2014-09-07
Thank you, my perceived problem was just an illusion!  The steps in post [http://ubuntuforums.org/showthread.php?t=2235903](http://ubuntuforums.org/showthread.php?t=2235903) revealed that the turbo is working properly.

---

### Post by jmvelasquezestrada on 2015-04-21
Hello!

I have the same laptop, and I would like to turbo clock it, but I don't find a good source of information on how to do it, can you give me some links to read? 

Thanks!

---

### Post by Vladlenin5000 on 2015-04-21
> **jmvelasquezestrada said:**
> I have the same laptop, and I would like to turbo clock it, but I don't find a good source of information on how to do it, can you give me some links to read?

Sure. Start by reading the one in the post before yours. And next time try to at least read the posts already in the thread where you decided to post.

---


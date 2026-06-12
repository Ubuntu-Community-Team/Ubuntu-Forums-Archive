---
title: "How about Ubuntu intrepid performance?"
date: 2008-10-31
forum: General Help
---

### Post by syms on 2008-10-31
Hello,
ive read article in phoronix.com that ubuntu 8.10 is slower than previous ubuntu releases, and ive seen benchmarks that gtk in 8.10 is 30% slower than in 8.04. So how do you feel about intrepid performance? i havent tried it yet but i want to hear - is it slower? is it faster? does boot is faster than 8.04?
Thank you for your answers

---

### Post by the8thstar on 2008-10-31
Performance overall is equivalent. I didn't  notice any difference. Boot time though is considerably longer though. It went from 45s to 1m20s on my machine. I tried the usual tricks to "trim the fat" to no avail.

Is anyone knows how to make it boot faster, let me know!

---

### Post by alienprdkt on 2008-10-31
Seems bout the same so far, even though even though all I am using it for is a LAMP, it just pretty much sits there holding my website data. Boot up time bout the same (bout 25secs from grub to login, and then another 20sec., yeah bout the same as Hardy)

---

### Post by saberz on 2008-10-31
I followed these steps and noticed a bit of a boost.


[http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/](http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/)


Good stuff :)

---

### Post by WiFi Ed on 2008-10-31
What I've noticed, aside from slightly improved boot up and shutdown times, is significantly improved file copy performance. Under Hardy I got about 70MB/s transfer speeds copying a 5 Gig music folder, now under Intrepid I see about 120MB/s speeds. That's with Intrepid installed on a 7200 rpm SATA HD, not my VelociRaptor (that's where Vista is installed)!

I addition, certain websites with streaming audio/video feeds that only worked for me under IE/Windows now work in Firefox/Intrepid (CNN, Foxnews, etc.).

Kudos to the developers!
:guitar:

---

### Post by the8thstar on 2008-10-31
> **saberz said:**
> I followed these steps and noticed a bit of a boost.


[http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/](http://www.sysadminsjourney.com/2008/08/31/quick-painless-ubuntu-speed-tweaks/)

Good stuff :)


Unfortunately, this didn't work. I'm downloading the 8.10 and I'll do a clean install from there.

---

### Post by bibleman on 2008-10-31
I haven't noticed any difference in performance or boot up time. I have 8.10 installed on my HP zt3000 laptop.

---

### Post by sdennie on 2008-10-31
> **syms said:**
> Hello,
ive read article in phoronix.com that ubuntu 8.10 is slower than previous ubuntu releases, and ive seen benchmarks that gtk in 8.10 is 30% slower than in 8.04. So how do you feel about intrepid performance? i havent tried it yet but i want to hear - is it slower? is it faster? does boot is faster than 8.04?
Thank you for your answers

gtkperf numbers can vary based on theme, compiz. kernel or even the placement of the gtkperf window.  Regardless, if you are running with nvidia graphics, you could try to use these instructions and you will likely see something close to a 2x speedup in gtkperf numbers: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088).  

Based on the fact that I get a 30% decrease in performance in gtkperf in Hardy when switching from a 2.6.24 kernel to a 2.6.27 kernel and that I'm on nvidia but the phronoix tests were on ATI, it's fairly safe to assume that the kernel is causing the performance decrease.

---

### Post by the8thstar on 2008-11-01
A fresh install saved me 10s. I still have to reinstall AWN though so I might end up with another +10s... back to square 1.

Anyway, **[COLOR="Red"]1m20s is the new standard for bootup time for a single core Intel. That's way too slow in my opinion.[/COLOR]**

---

### Post by Vadi on 2008-11-01
It boots faster for me than 8.04, and seems to work faster. So, on my hardware, I didn't experience slowdowns or fps drops in games.

---

### Post by syms on 2008-11-04
> **the8thstar said:**
> A fresh install saved me 10s. I still have to reinstall AWN though so I might end up with another +10s... back to square 1.

Anyway, **[COLOR="Red"]1m20s is the new standard for bootup time for a single core Intel. That's way too slow in my opinion.[/COLOR]**

well my computer is single 3000+ amd athlon 64 512 mb ram and ubuntu boots fully in about 50 seconds. actually single core can be faster in many things than dual core

---

### Post by Vadi on 2008-11-04
Under 2s for me, with a fully encrypted hd and a 2.2ghz dualcore

---

### Post by d_skillz on 2008-11-04
> **the8thstar said:**
> Performance overall is equivalent. I didn't  notice any difference. Boot time though is considerably longer though. It went from 45s to 1m20s on my machine. I tried the usual tricks to "trim the fat" to no avail.

Is anyone knows how to make it boot faster, let me know!

same here exact same boot time, I hope they can significantly improve this for the next release.

---

### Post by imbjr on 2008-11-04
I've noticed certain occasions where the cursors lags, but that's possibly because the system was under heavy load from either:

a) Virtual Box running XP with 2G RAM given to it. However, I had pretty much that set up under Hardy and did not notice cursor lag.

b) Disk transfers to an external HD. I was sorting out my master backups and so was doing a lot of external disk access. However, the CPU graph never indicated a load problem.

One website with a number of animated GIF thumbnails on it was showing the lag quite frequently, but since the external disk access has stopped I've not noticed any lag. About 1/2 hour ago I was in Photoshop in my Virtual Box XP session and noticed a brief spell of lag, but that was it and I half expect that under such conditions - tho as mentioned above I don't think Hardy ever did it.

It's amazing how sensitive one becomes to one's cursor movement after seeing it lag! Sometimes I question myself - did I see that just lag? I seem to go through this phase whenever I re-install an OS anyways.

---

### Post by hufferd on 2008-11-04
> **syms said:**
> Hello,
ive read article in phoronix.com that ubuntu 8.10 is slower than previous ubuntu releases, and ive seen benchmarks that gtk in 8.10 is 30% slower than in 8.04. So how do you feel about intrepid performance? i havent tried it yet but i want to hear - is it slower? is it faster? does boot is faster than 8.04?
Thank you for your answers

The only thing I have noticed is what many are saying here BOOT TIME is much longer then it was..... But once I am up and running I have NOT noticed any issues at all Performance seems about that same as 8.04 if not a little better. As with anything else I think allot depends on system hardware more then anything. :)

---

### Post by xjgnsdof on 2009-01-04
I use significantly overclocked hardware, so I rarely notice speed *improvements*. Nevertheless, I noticed that Intrepid booted faster than Hardy and generally loads apps faster.

---


---
title: "Dell shutdowns on high CPU load, temperature"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by ldrn on 2007-08-16
Hello.  I am having a problem with a Dell XPS Gen 2 laptop.

Basically, it's shutting itself down whenever I am watching certain videos or while encoding audio. Using i8kmone), I can tell that even with both fans running full speed and an external cooling device under the laptop, the temperature climbs and hits 100 before it happens. 

I'm aware this is a safety feature, but it happens often enough that I can't deal with it anymore, even though I really do like Linux. I tried reinstalling Ubuntu once, then took the added step of reinstalling Windows; the issue appears to be confined to Linux, although I am not sure if it is Linux in general or just Ubuntu/Debian -- I had tried Suse on the same machine in the past and do not remember this being a problem.

I'm hoping there is a way I can tell the power management to scale back the CPU use instead of shutting down at high temperatures, or failing that, setting the temperature limit higher.  I worry that the second option is not safe, but at the same time, I know I've pushed this machine much harder -- and hotter --in Windows running certain games than this without it protesting.  Does anyone know how to do that, or have any other advice?

---

### Post by tgalati4 on 2007-08-17
Could be several things:

Poor contact between the CPU die and the heat sink.

Too much or too little heat sink paste.

Poor heat sink design, since it can't take 100% CPU load.

Poor cooling design--either fans or vents or pathways.

Software optimization would help, but it seems that frequent shutting down due to thermal halt is a design/manufacturing issue.

How long does it take before it shuts down under load?

Have your tried installing lm-sensors to see what your fan speeds and other temperatures are at?  There could be a thermal problem somewhere else on the board--like a southbridge handling audio and network and harddisk management all at the same time.

---

### Post by ldrn on 2007-08-17
Thanks for the help;

I am not certain it is not a hardware problem, but also don't want to check -- it is still under warranty, provided I don't crack it open or anything. I am not sure how to use lm-sensors, but since it is a Dell, I use i8kmon to get the same information; both fans spin up to 2 (the highest speed it allows) fairly early on.  

It only does this when the CPU is running at 100% for more than around 2 minutes. It can handle prolonged high CPU use at lower levels just fine.

It doesn't actually feel that hot, either, compared to how hot it gets when I'm using the GPU heavily.

---

### Post by bimmerd00d on 2007-08-17
My Latitude D820 does this from time to time too.  T7400 in it.  It does it in Windows too, so i chalked it up to a mobo/cpu issue.

---

### Post by ldrn on 2007-08-20
*edit*
For a while, I moved the shutdown command... not a good solution. Anyway, I found out that, for whatever reason, my laptop wasn't throttling the CPU down when the temperature got too high, which is what I assume Windows was doing to avoid the same problems I was having. I tried a few solutions online, and the best one for my laptop was cpufreqd; I installed it by apt and was ready to go!

It works great; the default configuration wasn't aggressive enough for me, but it was really easy to understand and add more rules for slowing down the CPU as the temperature rose. I'm very happy; even though my laptop might not run as fast all the time, it doesn't overheat and die -- it's a huge improvement. :) Anyway, I hope adding this will help anyone else who runs into a similar problem.

---


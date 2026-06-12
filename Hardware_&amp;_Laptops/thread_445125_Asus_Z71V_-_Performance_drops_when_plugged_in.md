---
title: "Asus Z71V - Performance drops when plugged in"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by arrow15 on 2007-05-15
I have a Asus Z71V based laptop. I've used both Ubuntu and Kubuntu on it (currently Kubuntu), and in both cases, the performance of the machine in running videos, displaying graphic intensive screensavers, etc has dropped quite significantly whenever the machine is plugged into the wall.

I have my power manager set to dynamic for both wall and battery, but I've tried every setting and the result is the same. If i'm in the middle of a video w/ AC in, it'll have choppy playback, but if i take the plug out of the back, it immediately becomes quite smooth in playback.

I use the nvidia drivers (proprietary in Ubuntu, glx-new install by automatix in Kubuntu). The machine has a NVidia 6600 Go, Pentium M 2.13, 2GB RAM, and a 7200 RPM drive. In windows and I believe in (K)Ubuntu on battery power, the system is quite capable of flawless HD playback.

Anyone have an idea of what might be causing these problems?

---

### Post by arrow15 on 2007-05-16
bump.

I'm still having the issue. Battery - fine. Plugged in - terrible. I've tried the power manager, taking the battery out and plugging directly into the wall, letting the battery charge all the way, etc., and still no progress.

---

### Post by mikuton on 2007-05-16
Hi arrow15. Are you running the 2.6.20-15-generic kernel (with Feisty)? You could try installing the 2.6.20-15-386 kernel from the repositories and check whether running you laptop with that one fixes your problem. I was having the same issue with my laptop (ASUS A6VM), but migrating to the 386 kernel "fixed" it.

---

### Post by arrow15 on 2007-05-16
Thank you very much for the reply, your suggestion solved the problem. The 386 kernel works perfectly with my machine, I get no more video lag at all.

:D :D :D

---


---
title: "System Profiler: CPU rating changes"
date: 2010-05-20
forum: Hardware
---

### Post by geovino on 2010-05-20
I have an Acer Extensa 4420 laptop w/ AMD X2 TK-57 CPU which is dual core 1900mhz. 

I've installed virtualbox w/winXP and it seems to make it run slower. I checked the System Profiler and now it says that the CPU is dual core 800mhz! How does this happen? Is there a way to change it? Is this because of virtualbox?

I'm running Ubuntu 10.04 32bit (because I needed to install winXP 32bit)

---

### Post by cascade9 on 2010-05-20
I'm pretty sure thats because of being in virtualbox, and its reported the CPUs downclocked speed (by cpufreq)

BTW, you can use a 64bit OS and then run a 32bit OS in virtualbox, and if your dual-booting, the OSes have nothing to do with each other, so it doesnt matter if one is 32bit, the other 64bit.

---

### Post by geovino on 2010-05-20
> **cascade9 said:**
> I'm pretty sure thats because of being in virtualbox, and its reported the CPUs downclocked speed (by cpufreq)

BTW, you can use a 64bit OS and then run a 32bit OS in virtualbox, and if your dual-booting, the OSes have nothing to do with each other, so it doesnt matter if one is 32bit, the other 64bit.

Thanks. When I was running in 64bit and trying to install winxp 32bit in vbox it wouldn't read the disk. So I thought I had to be in 32bit Ubuntu. How would you get it to except it?

---

### Post by cascade9 on 2010-05-21
No idea. The one time I ran a 32bit OS with virtual box on a 64bit OS everything worked fine.

---


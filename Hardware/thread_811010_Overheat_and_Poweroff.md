---
title: "Overheat and Poweroff"
date: 2008-05-28
forum: Hardware
---

### Post by jdpellegrino on 2008-05-28
Ok folks, I've been having a bit of a problem lately. It seems that while performing certain intensive tasks, my laptop will overheat and eventually automatically shut itself off. I am running the new 8.04 version on a Dell Inspiron 1501 with a AMD Turion(tm) 64 X2 Mobile Technology TL-50 1600Mhz.

I have found that setting the scaling_max_freq of CPU0 and CPU1 to 800000 prevents the problem but I am hoping for a more permanent solution. I've read here and there of others having similar problems but I don't think I've seen a firm solution. I was hoping that going to 8.04 with the 2.6.24 kernel would square it away since it seems to have been lingering around for a while. But it seems I was wrong. So is there any incite on this problem?

---

### Post by jdpellegrino on 2008-05-29
:bump anyone?

---

### Post by jocko on 2008-05-30
I found [this thread]("http://ubuntuforums.org/showthread.php?t=786402") which explains how to undervolt the cpu.
The script in that thread did not work that well for me (something seems to override the cpu speed settings the script tries to use and it also only tests one core), but I managed to find some good settings myself by trial and error.
Running the cpu at lower voltage reduces heat production and extends the battery life of laptops with no loss of performance.
But if it's set too low your system will become unstable.
I managed to get my cpu core temps from 55-60 C to 40-45 C (idle) and the temp on full load from >90 C (sometimes hot enough to trigger a shutdown) to below 80 C.

---


---
title: "Latop in Battery mode runs on lowest frequency only"
date: 2010-02-17
forum: Hardware
---

### Post by osfight.de on 2010-02-17
Dear community, 

I have an annoying problem. I cannot make my Ubuntu to change the cpu frequency while being in battery mode with my laptop, it will always run in lowest mode (800Mhz), making it impossible to watch flash movies or doing other demanding tasks.

Trying to change the cpu frequency via cpufreq-selector does not work, not as root or user.

```
root@user-laptop:~# cpufreq-selector -f 2200 &
[1] 4251
root@user-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 
800000
root@user-laptop:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
userspace
root@user-laptop:~# 

```Hope anybody can help and has a hint. 

Best regards,

osfight.de

---

### Post by chewearn on 2010-02-17
I change the frequency by using the CPU Frequency Scaling Monitor applet.

Add the applet to the gnome-panel, and you should be able to change the frequency by clicking on the applet.

---

### Post by osfight.de on 2010-03-02
Thanks for your input, but I have tried this already. The scaling monitor is in my panel but does not have any effect in battery mode, so does not the command in the terminal. 

Any other idea?

---

### Post by marius311 on 2010-03-02
I had a similar problem. For me, it was a BIOS setting for power saving which was the culprit.

---

### Post by osfight.de on 2010-03-07
> **marius311 said:**
> I had a similar problem. For me, it was a BIOS setting for power saving which was the culprit.

That is awesome, I changed the BIOS setting from *Battery Life* to *Performance*  and now I am able set the frequency even in battery mode, partially. 

Unfortunately the maxium frequency settable in battery mode is now 1600MHz out of 2200MHz. Obviously there is an additional setting blocking the full frequency range. 

Thanks for help solving the problem partially, we are getting there.

---


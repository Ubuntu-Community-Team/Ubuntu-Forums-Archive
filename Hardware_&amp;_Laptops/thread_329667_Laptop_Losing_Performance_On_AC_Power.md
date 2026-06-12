---
title: "Laptop Losing Performance On AC Power"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by gwayland on 2007-01-02
I tried to search the forums and didn't find anything to help. My laptop runs great and will handle anything on battery. As soon as I plug it in, it slows way down. Even scrolling a large menu is jumpy. KBounce is a good example: on battery, it is very smooth. When I plug it in, it becomes unplayable. This affects all my apps. I installed emifreq and set it to max performance, have played with power management setting, and have done everything else I could think of. I have no idea what is going on. I am running:
ASUS M5A Laptop
1.6 GHz Pentium M
1 G.B. RAM
Running Edgy with all updates.

If anyone could help I would appreciate it. Thanks.

---

### Post by MrHorus on 2007-01-02
[QUOTE=gwayland;1956897]I tried to search the forums and didn't find anything to help. My laptop runs great and will handle anything on battery. As soon as I plug it in, it slows way down. [\QUOTE]

I suspect it might be a problem with CPU throttling.

Please paste the output of ```
cat /proc/cpuinfo 
``` with the AC plugged in and without.

---

### Post by gwayland on 2007-01-02
Plugged in:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 1596.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 3196.00

On battery:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 1596.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 3196.00

---

### Post by gwayland on 2007-01-03
*bump*

---

### Post by gwayland on 2007-01-15
Well, I figured it out on my own. All I had to do was install the i386 kernel instead of the generic version.  That also cut my boot time in half.

---

### Post by noxxle on 2007-03-07
Im having the exact same problem with my Z33ae. I cannot use ANY distro unless there is a 386 kernel available for that distro. Any idea why? Just curious, what hard drive are you using?

---

### Post by BungaMan on 2007-04-13
hmm, I'm also having this problem.  Strange however is that I've been running without the battery plugged in and did not experience this until a couple of days ago.  Plugging in the battery gives much better performance.  I'm always booting up with the same generic kernel (2.6.17).  Since I started to have this problem my battery seems to have gone flat (0% charged) and doesn't want to recharge anymore.  On top of that my computer can sometimes simply switch off power by itself and the screen can turn very dark.  Then I have to press ctrl-alt-f1 to go to a terminal (I can barely see any of this on the screen), close the lid (this turns off the monitor) and open it to give me a normal brightness again.

---

### Post by gwayland on 2007-04-16
I am using a WD400VE. It was a decent model that had a good price. I think that it is odd that you had the exact same problem with this model of laptop. I checked out a couple of other computers and laptops and mine is the only one that it made such a huge difference on. I also find it interesting that other distros give you problems. I still don't know why the kernel made such a difference, though.

^ Sound like you may need a new battery. I would imagine that a completely broken battery might cause all kinds of power management problems. I don't know for sure, but that would seem likely to me.

---


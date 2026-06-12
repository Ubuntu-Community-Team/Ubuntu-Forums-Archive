---
title: "Single core 1.7Ghz Centrino stuck at 600MHz?"
date: 2009-05-12
forum: Hardware
---

### Post by Cenoforums on 2009-05-12
Hi,

I'm been experiencing quite a slow performance on Ubuntu, specially on flash videos, and finally I discovered the it was not xorg or firefox or the ati driver but rather the cpu is stuck at 600MHz according to /proc/cpuinfo.

[I]model name	: Intel(R) Pentium(R) M processor 1.70GHz
stepping	: 6
cpu MHz		: 600.012[/I]


I had been experiencing sudden burst in performance for a while, and now I'm guessing that all of a sudden the cpu just "breaks free" and goes to full power for absolutely no reason, without my intervention. I'm waiting for this to happen again, but I'm pretty sure this is the problem.

I've been trying to fix it for a while but it's been quite difficult. I installed powernowd (success was reported here [http://ubuntuforums.org/showthread.php?t=1134657]("http://ubuntuforums.org/showthread.php?t=1134657")), and running it says

[I]Please make sure that:
 - ....
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel[/I]

Which I don't by checking lsmod | grep cpu, and no wonder, because according to something I read the new ubuntu kernel has the cpufreq modules built-in. But something is indeed failing because running ls /sys/devices/system/cpu/cpu0 reveals

cpuidle  crash_notes  topology

The frequency part is missing.

Any input? Can I refer to any log for further info?

Thx in advance, I would really like to fix this thing... O_o

---

### Post by rpineger on 2009-10-03
Hi, mine appears stuck on 798MHz although previously it was working. Because there was no response here, I've raised a bug in Launchpad. Please vote for it by clicking **"This bug affects me too"**. This is most frustrating, my Dell Inspiron 9300 already has no 3D graphics due to lack of OpenGL drivers for my _premium_ graphics card - yes I paid for the better card and screen - now I'm also running at 1/2 speed! Hey, I guess that even with half power Ubuntu still runs smoothly so it isn't all bad - I'm sure it would cripple XP.

Bug #441169 URL:
[https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/441169](https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/441169)

If you can offer any solutions or workarounds then let me know!

Thanks, Richard

---

### Post by wilee-nilee on 2009-10-03
edit

---

### Post by wilee-nilee on 2009-10-03
If you right click on a panel then add to panel there is a cpu controller add on. I think though not knowing the memory amount that it is more then just the low cpu that is making stuff slow. You might post what flash your using.

---

### Post by Cenoforums on 2009-11-13
I kinda forgot about this thread.

For future reference, my problem was in the BIOS. Apparently, there are some frequency tables that are set by the BIOS for the kernel to read. Apparently, my BIOS wasn't doing that and the cpu was stuck at the lost frequency. A stupid workaround solved the issue.
I have a old fujitsu siemens, so our problems are of a different kind :-\

---


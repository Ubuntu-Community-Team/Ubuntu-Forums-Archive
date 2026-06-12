---
title: "Thinkpad t400 - Ububtu 11.04 - Slows down / Freezes"
date: 2011-05-26
forum: Hardware
---

### Post by Red62 on 2011-05-26
Hi,

I have a Lenovo T400 Thinkpad and have installed a fresh 11.04.  The thinkpad performs great but randomly slows right down and almost freezes making it unusable.

I believe the issue is power related - if I plug in the power supply it clears the situation.  Also seem to happen more when the machine is left idle.

Any ideas?  I have installed the latest BIOS.

thanks

---

### Post by Red62 on 2011-05-27
this definitely seems to be a power related issue... I have read some info on ACPI and connecting and disconncting the power does free up the system again...

Does anybody have any ideas of suggestions?

Is anybody running 11.04 on a Thinkpad t400?  I recall a similar problem existed in 10.10 when it was briefly installed

thanks

---

### Post by kleskjr on 2011-05-27
Check the frequency of your CPU during freeze. I have a T410 for almost an year now, and I noticed that after a kernel update the CPU was stuck at the lowest frequency, reflecting in a very poor performance. After downgrading to kernel 2.6.32-24 I have no longer that issue (almost :D ). I read about other people having similar problems but didn't have time to get into the issue.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706089](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706089)

cheers

---

### Post by Red62 on 2011-05-27
thanks for the reply.. how do I find out what speed my cpu is running at?

cheers

---

### Post by Red62 on 2011-05-27
used 

cat /proc/cpuinfo

shows CPU at 2.4ghz... which is the max for my t400... I will see if I can run next time the machine slows down

Cheers

---

### Post by Red62 on 2011-05-29
Well I seem to have found a fix that involves using noapic and nolapic in my grub config... this seems to make the thinkpad run with only 1 cpu.... performance seems good so I am not sure if really is running with 1 cpu or that is just how the system monitor is seeing it.

---


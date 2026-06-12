---
title: "Super LFM (Intel Santa Rosa and Above)"
date: 2010-09-01
forum: Hardware
---

### Post by Local.tosh on 2010-09-01
Hi,

Just bought a new laptop (Toshiba R700) which has a Intel Core i5 processor. Battery life compared to Win7 in Ubuntu isn't very good. One of the (perhaps many) reasons for this is that Intel super low frequency mode doesn't seem to work.

Can i somehow implement this or is this a kernel issue? If so is anyone working on this?

---

### Post by ilovelinux33467 on 2010-09-01
I don't know if this will work but may be upgrading to a later kernel version like 2.6.35?

---

### Post by Local.tosh on 2010-09-01
Hmm not sure how to do that. Any tutorials for that?

---

### Post by ilovelinux33467 on 2010-09-01
Hi,

Have a look at:
[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/")

---

### Post by Local.tosh on 2010-09-01
> **ilovelinux33467 said:**
> Hi,

Have a look at:
[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/")

Thanks that was easy went for 2.6.35 seems work fine, however 

cat /proc/cpuinfo

Still reports ~1200mhz at idle (should be ~600 mhz)

---

### Post by connect404 on 2010-09-02
So any battery life gains to report?

---

### Post by Local.tosh on 2010-09-02
> **connect404 said:**
> So any battery life gains to report?

No it seems superLFM is still broken in 2.6.35. Headphones now work, haven't had time to check if anything else is broken or fixed on the R700 yet.

---

### Post by connect404 on 2010-09-03
> **Local.tosh said:**
> No it seems superLFM is still broken in 2.6.35. Headphones now work, haven't had time to check if anything else is broken or fixed on the R700 yet.

So the kernel update fixed the headphone issue?

---

### Post by omerp on 2010-09-03
You can get this fix, at least for the R705, without going to upstream kernels, by using the official alsa backports package. See this post in the "official R700/R705" thread for details:

[http://ubuntuforums.org/showthread.php?p=9802968#post9802968](http://ubuntuforums.org/showthread.php?p=9802968#post9802968)

---

### Post by Local.tosh on 2010-09-07
> **omerp said:**
> You can get this fix, at least for the R705, without going to upstream kernels, by using the official alsa backports package. See this post in the "official R700/R705" thread for details:

[http://ubuntuforums.org/showthread.php?p=9802968#post9802968](http://ubuntuforums.org/showthread.php?p=9802968#post9802968)

This thread is not about the sound issue!

Someone must know how to fix this or be working on a solution. I assume all Intel laptops of the santa rosa generation and above have the problem

---

### Post by ArcherTC on 2010-09-13
I have the R705-P25 model with the i3 processor.  Using Fewt's Jupiter utility the cpu frequency drops from 2266 in maximum performance to 933 in power saver mode.  I haven't had a chance to do any battery life studies but maybe this helps?  I'm a newbie -- what frequency would I expect from the i3 in Super LFM?

---

### Post by Local.tosh on 2010-09-15
~466 mhz (993 / 2) is what i expect from a core i3 in super LFM! My i5 520m should be ~665mhz this is is what i get in win7. In Ubuntu 1200 mhz is my minimum.

---

### Post by Local.tosh on 2010-09-23
Update: completely upgraded to Ubuntu 10.10 Beta, does not remedy the problem still the min clocks are 1200 mhz.

Did not expect this to work as the kernel only upgrade also yielded nothing.

on the plus side 10.10 seems to work just fine.

---

### Post by solnyshok on 2011-10-08
one year later, ubuntu 11/10. same problem.

---


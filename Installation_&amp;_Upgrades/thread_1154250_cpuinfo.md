---
title: "cpuinfo"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by fred0843 on 2009-05-09
I have Ubuntu 9.04 installed on a AMD64 FX55.When I do a cat /proc/cpuinfo I get 1200 Mhz not 2600Mhz.U think this is normal ? What can I turn off or uninstall get get it to show 2600 Mhz.

---

### Post by stefangr1 on 2009-05-09
> **fred0843 said:**
> I have Ubuntu 9.04 installed on a AMD64 FX55.When I do a cat /proc/cpuinfo I get 1200 Mhz not 2600Mhz.U think this is normal ? What can I turn off or uninstall get get it to show 2600 Mhz.

If your CPU is idle the kernel will scale the frequency down. You can whether this works well on your system by doing cat /proc/cpuinfo when your system is on full load. 

If it still shows 1200Mhz, there's a chance the value reported isn't correct, or worse... that the scaling feature isn't working correct. In that case you have to turn that off.

---

### Post by cariboo on 2009-05-09
Do you have cool and quiet enable in the BIOS, this will cut the frequency by 50% at idle.

---

### Post by fred0843 on 2009-05-09
Cool N Quiet is off

In Ubuntu 8.10 when I was get 1200 and not 2600 computer would lockup.I had to turn off cpu freq Manager when I got 2600Mhz and no lockups.I can not find any thing to turn off in 9.04.

---

### Post by stefangr1 on 2009-05-09
O.K., than it seems you really have a problem with CPU scaling. The way you can turn this off has changed in Jaunty. It can now be done with the rcconf utility. You can read about that in the following theat:

[http://ubuntuforums.org/showthread.php?t=1111609&page=2](http://ubuntuforums.org/showthread.php?t=1111609&page=2)

---

### Post by fred0843 on 2009-05-09
stefangr1 That did it.

Thanks Guys

---


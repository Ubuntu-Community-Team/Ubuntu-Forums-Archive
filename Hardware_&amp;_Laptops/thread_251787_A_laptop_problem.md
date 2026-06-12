---
title: "A laptop problem"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by Cyraxzz on 2006-09-05
I installed Ubuntu on a Amilo M 1420

Pentium M 1.6 GHz and 1 GB of ram. the Problem is that it's somewhat slow to launch apps and opening folders with nautilus is slow as well, however the apps run properly. Is this CPU type not supported by Ubuntu or something?

---

### Post by kidders on 2006-09-06
I'm not 100% positive about specific support for the Pentium M, but there are a couple of things you can do to speed up application loading times all the same:

**CPU POWER GOVERNOR**

Check to make sure the "ondemand" scaling governor isn't active. It prolongs battery life by dialling down your CPU when it's not being pushed very hard. There's usually a few seconds of a lag between *needing* a CPU at full power and *getting* it, which adversely affects performance. The CPU governor /sys entries generally hang out someplace like **/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor**.


**PRELINKING**

If you're still not happy, you can prelink your executable binaries. Apple calls this "Optimising application performance" or some such euphamism, in case you're a Mac head (like me :-P )

The idea is that you can pre-bind your apps to the libraries they require at runtime, saving a few milliseconds for each one. Big, clunky apps like KDE get a suprising performance boost out of being prelinked.

Incidentally, how much virtual memory have you allocated?

Post back if either of these take your fancy!

---


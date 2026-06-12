---
title: "speed step - cpufreq messy configuration"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by vagrant on 2007-05-17
Hi all, im currently using a core 2 duo cpu for my system and that is fine and i like how it works under ubuntu and everything. But when installing my system using any distro basically my cpu speed step is set to an interval of 600-700mhz/core when it could be up tp 1860mhz. Well fine i get the whole speed step thing and the cool features it brings...like saving energy and reducing heat and making the computer more quiet.

But why is the interval per default set to 600-700mhz by cpufreq, sure i can manually go to \sys\devices\system\cpu\cpu0 or cpu1\cpufreq and set the value to a higher one but somehow when doing this its either going at the max mhz or 600-700mhz.

I have recompiled my kernel to better support core 2 and also checked so that there is speed step support for intel compiled in the kernel.

The way this is set up by default is very ugly in my opinion, i mean since most people buying a new computer go for intel core 2 duo or maybe AMD X2 (not sure if there is the same problem) is this a bug ? do you have a good solution for this?

---

### Post by vagrant on 2007-06-22
anyone, this is a huge issue for most core2duo users

---


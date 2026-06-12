---
title: "Can't get undervolting to work on my Thinkpad X60"
date: 2010-11-16
forum: Hardware
---

### Post by lemino on 2010-11-16
Hi, a late night and still i stumble at the last steps in order to get my Thinkpad X60 undervolted, darn it. Anyway, I followed this guide:

[http://openmindedbrain.info/26/10/2010/undervolting-in-ubuntu-10-10-maverick/](http://openmindedbrain.info/26/10/2010/undervolting-in-ubuntu-10-10-maverick/)

which is really good, only it doesn't completely work for me. What I get stuck at is the installation of the module. When I type "make prepare" I get:

Makefile detected your kernel version as 2.6.35
***FOUND AVAILABLE PATCHSET. PREPARING.***
./prepare.sh: rad 12: patch: kommandot finns inte

The last part there is swedish, meaning 'line 12', 'the commando can't be found'.

After this, if I try 'make', everything looks ok. I then launch 'sudo make install' which finishes quite nicely. But, when i get to the step where I type 

cat /sys/devices/system/cpu/cpu0/cpufreq/phc

I don't have a 'cpufeq'-library in my cpu0. Why is this? I have restarted and mande sure to use the right kernel, so that shouldn't be it. I'd be really greatful for any help!

/Erik

---

### Post by Decatf on 2010-11-16
apt-get install patch

Then run go back to the make prepare step.

---

### Post by lemino on 2010-11-17
Thanks, the patching now works, but I still don't get that /cpufreq/-directory that the guide is talking about. What's wrong? Is the module not loaded correctly?

---


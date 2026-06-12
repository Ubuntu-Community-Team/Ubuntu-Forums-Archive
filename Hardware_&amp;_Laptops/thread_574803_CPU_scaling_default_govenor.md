---
title: "CPU scaling default govenor"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by thebert on 2007-10-13
I am currently running and I am using the CPU Frequency Scaling Monitor applet. I ran the sudo dpkg-reconfigure to allow me to use this applet to change the way scaling works. By default Ubuntu uses the ondemand setting, but I would prefer to use the conservative setting, as ondemand causes my laptop to get hot quickly. I have been trying to figure out how to change the default setting to conservative, as every time i switch to the battery or back to the ac adapter, the scaling governor changes back to the default ondemand setting.

I am using an HP nw8240 with a 2.13GHz Pentium M. Even though I am running gutsy, it works the same way in feisty.

Any idea how to change the default setting? Just keeping it on conservative would be nice, but even better would be to specify different governors for battery and ac power.

---

### Post by thebert on 2007-10-18
I found the answer on my own so I figured I'd post it just in case anyone else is searching for the same thing.

The option is in gconf-editor under apps->gnome-power-manager->cpufreq

Hopefully this will help someone.

---

### Post by brujoand on 2007-10-21
Thanks for posting the answer, I've bin strugglin with that for a while :)

---

### Post by xzero1 on 2007-10-27
Thanks, you may want to make a "How to" for this.

---

### Post by njparton on 2007-10-30
Yeah, a how to would be great, thanks :)

---

### Post by MorphiusFaydal on 2008-02-09
Thanks man, I've been looking for this solution!

---

### Post by thebert on 2008-02-09
btw, I did write up a howto:

[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

Check it out.

---


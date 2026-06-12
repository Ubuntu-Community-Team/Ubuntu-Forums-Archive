---
title: "Need Battery Guide"
date: 2009-10-02
forum: Hardware
---

### Post by LinScape on 2009-10-02
Hi,

I was searching for guides on how to save battery power on ubuntu Jaunty but the ones i found only applied to older versions of ubuntu. Can some one help me find or write a small guide on how to save battery energy on ubuntu?

---

### Post by nixscripter on 2009-10-03
One simple suggestion: install the **cpufrequtils** package. It will allow you to select an algorithm (called a governor) to choose how CPUs adjust frequency (CPU frequency scaling). Lower frequency means lower power.

Just edit **/etc/init.d/cpufrequtils** to set the governor to use. Here are the options which ship with the kernel:

Performance - max frequency all the time
Powersave - min frequency all the time
On demand - min frequency, raises based on usage
Conservative - like on demand, but will "lag" usage, meaning it will delay scaling up to see if you "mean it"

It's not a guide, but I would consider it a key suggestion to any one would write.

I would also suggest looking at the Gentoo Power Management Guide for suggestions. However, it's for people who build systems from scratch, so goes into a lot of (un-necessary) depth.

[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)

Hope this helps, and good luck if you write one.

---

### Post by LinScape on 2009-10-03
ok,thanks.

---

### Post by LinScape on 2009-10-04
is cpufrequtils a command line program or one that has a gui?

---

### Post by nixscripter on 2009-10-06
cpufrequtils is a package. The commands it provides are **cpufreq-set** to change the governor, and **cpufreq-info** to list information about current settings.

There is also a GNOME applet for monitoring it, called the CPU Freq Scaling Monitor. I don't know about KDE.

---


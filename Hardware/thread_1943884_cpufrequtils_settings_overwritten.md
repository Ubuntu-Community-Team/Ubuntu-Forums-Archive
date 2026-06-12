---
title: "cpufrequtils settings overwritten"
date: 2012-03-20
forum: Hardware
---

### Post by tririver on 2012-03-20
Hi, all,

My laptop has an over-heating problem thus I want to downscale it's cpu frequency (to powersave). After put GOVERNOR="powersave" in /etc/detault/cpufrequtils, when I do "service cpufrequtils start", I can keep my laptop in powersave state. However, after reboot the governor becomes "ondemond" again. 

Thus my question is: how to let my laptop run in powersave mode from startup?

====== here are some of my unsuccessful attempts ======

I don't know how to use upstart, thus I put a line into /etc/rc.local:
service cpufrequtils start

Then funny things happens: when the computer just enters unity shell, command cpufreq-info shows 

> The governor "powersave" may decide which speed to use within this range.which is fine. However, after a minute when I run cpufreq-info again, I found something else has set cpu to ondemond.

Thus there is an additional question: how to find out which process modified the status of cpufreq?

I also tried cpufreqd, but it doesn't work for me.

BTW: after a few of years using archlinux, I found myself a newbie when switched back to Ubuntu :)

---

### Post by mc4man on 2012-03-20
The script 'ondemand' in /etc/init.d is set to sleep 60 then run. It's   running after your /etc/rc.local:

You probably could edit that script to use powersave instead of ondemand (line 27 here

You also could lower the sleep a bit to save on running longer than needed at high performance for boot, I use 30 here

---

### Post by tririver on 2012-03-20
Thanks a lot! This is exactly the solution. Now I removed cpufrequtils, simply changed the settings in /etc/init.d/ondemond and everything works fine.

> **mc4man said:**
> The script 'ondemand' in /etc/init.d is set to sleep 60 then run. It's   running after your /etc/rc.local:

You probably could edit that script to use powersave instead of ondemand (line 27 here

You also could lower the sleep a bit to save on running longer than needed at high performance for boot, I use 30 here

---


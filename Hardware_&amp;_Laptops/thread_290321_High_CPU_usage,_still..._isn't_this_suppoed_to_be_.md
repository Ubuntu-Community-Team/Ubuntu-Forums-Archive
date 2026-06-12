---
title: "High CPU usage, still... isn't this suppoed to be fixed?"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-11-01
I have done a fair bit of reading about this excessive CPU usage.  and it appears as if has been fixed (launchpad) but i still have to use the maxcstate switch to get my machine to idle properly.

why is this still broken for me?  

edgy 6.10
asus z70va 1024mb x700 w/ radeon drivers
pentium m CPU

---

### Post by amo-ej1 on 2006-11-01
maxcstate ?do you have a link on that ?

---

### Post by hardyn on 2006-11-01
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570)

<quote> My inspiron 6000 (Pentium M) exhibits this problem on at least 2.6.15-23-686 and 2.6.15-25-686, and the max_cstate fix:

echo 1 > /sys/module/processor/parameters/max_cstate
</quote>

there you go, its pretty well documented, and seems to apply to ubuntu only

Arlen.

---


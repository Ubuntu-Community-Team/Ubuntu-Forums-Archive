---
title: "Packard Bell EasyNote R1100"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by 1smg on 2006-09-11
How to get a Packard Hell R1100 working...

xorg.conf: 
```
Driver via
```
and
```
ModeLine "1280x800" 87.09 1280 1336 1616 1728 800 802 814 840 #60Hz
```

ath0:
download [http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/), install kernel-headers, make install rfswitch

/etc/network/interfaces:
```
post-up modprobe pbe5
post-up echo 1 > /proc/pbe5/radio
post-down echo 0 > /proc/pbe5/radio
```

works like a charm!

---

### Post by daller on 2006-09-12
Your notes should be added here:

[https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100](https://wiki.ubuntu.com/LaptopTestingTeam/PackardBellR1100)

And please check if the other information is correct!

If you don't have an account - Please make one!

It's of great importance to make the developers aware of any problems whatsoever...

---

### Post by 1smg on 2006-09-13
been there, done that.

the only "real" problems where "Fn+F1 Antenna Switch" and fiddeling with cpufreq.

Ubuntu is working really nice on this laptop - i came over from *BSD (for this machine ;-) where i had various problems with getting hibernate and antenna working.

regards,
sven

---

### Post by daller on 2006-09-14
> **1smg said:**
> been there, done that.

the only "real" problems where "Fn+F1 Antenna Switch" and fiddeling with cpufreq.

Ubuntu is working really nice on this laptop - i came over from *BSD (for this machine ;-) where i had various problems with getting hibernate and antenna working.

regards,
sven

Thank you!

---


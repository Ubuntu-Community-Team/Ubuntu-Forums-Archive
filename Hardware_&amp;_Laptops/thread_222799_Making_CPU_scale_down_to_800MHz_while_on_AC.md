---
title: "Making CPU scale down to 800MHz while on AC"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by tibbe on 2006-07-25
I would like to have my CPU (an 1.6GHz Pentium-M on a IBM T41) scale down to 800MHz even when I'm on AC as long as the computer doesn't need to use more. What would be the easiest way to set this up? I remember messing with cpufreqd on Gentoo but I don't know what Ubuntu uses.

---

### Post by gborzi on 2006-07-25
Ubuntu has cpufreqd, but by default it installs powernowd. You can set it through /etc/default/powernowd (/etc/default is like the /etc/conf.d). I have noticed one strange thing in dapper on my Compaq evo n610c, that has a 2.0 GHz Pentium-M. The /proc/cpuinfo files always reports the maximum frequency, but the correct frequency is reported in /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq

---


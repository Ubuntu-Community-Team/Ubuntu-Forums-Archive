---
title: "clock change from dual boot"
date: 2005-11-04
forum: General Help
---

### Post by ahh_dee on 2005-11-04
Hey guys I am dual booting xp and ubuntu on my 700m but when I run windows and later on boot to linux, the time on the computer reads 4 hours ahead of the actual time. does anyone know how to change this? I tried using "date" to fix it but it didnt do it thanks.

---

### Post by raaguileraa on 2005-11-04
i think your problem is UTC(Universal Time Coordinated) vs. Local Time.

One of yours OS is on UTC and the other in "Local Time" ([http://www.linuxsa.org.au/tips/time.html)](http://www.linuxsa.org.au/tips/time.html)), so they read in a different way your hardware clock.

try with this on Linux:
/sbin/hwclock --systohc 
or
/sbin/hwclock --systohc --utc

---


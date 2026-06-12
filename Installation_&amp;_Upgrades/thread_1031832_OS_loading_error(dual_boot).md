---
title: "OS loading error(dual boot)"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by abhimanyu1234 on 2009-01-05
:confused:i am new linux user so pls help 
my system configuration is amd 64 bit with ubuntu and windows dual boot

Everything was going fine. then one day i installed all the upgrades and upgraded my system to 8.10 from that day onwards my system shows 3 os at the time of starting one being ubuntu 2.7 something and the other being 2.9 something along with windows of-course. How do i correct this error pls help also pls tell me the steps in detail as i am new to ubuntu/linux.

---

### Post by Pumalite on 2009-01-05
Post menu.lst:
cat /boot/grub/menu.lst

---

### Post by Pumalite on 2009-01-05
This is amd64:
Linux pumalite-desktop 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686 GNU/Linux

---

### Post by tuxxy on 2009-01-05
The different numbers 2.7 and 2.9 represent the different kernels you have on the machine, they are still Ubuntu so don't worry just select the most recent eg the 2.9 one.

---


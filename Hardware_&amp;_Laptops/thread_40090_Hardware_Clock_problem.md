---
title: "Hardware Clock problem"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by BIGGER on 2005-06-07
I have a Dell Inspiron that I dual-boot between Ubuntu 5.04 and Windows XP Pro SP2.  I set the clock in the BIOS, boot into Windows and the clock is correct.  I can logout of Windows boot into Ubuntu and the clock is correct.  If I reboot out of Ubuntu and go into the BIOS the clock is off by 6 hrs.  When I log into Windows XP it is also off by 6 hrs.  Both Operating Systems are set to be in CST (GMT -6).

This is more of an annoyance than anything, but I was wondering if there is some way to stop Ubuntu from messing with the system clock?

Thanks in advance,
Brent

P.S. Ubuntu is now my favorite Linux flavor.

---

### Post by Seti on 2005-06-07
Sounds like you had your hardware clock set to local time (which is what you want since you're dual-booting) but during setup you may have told Ubuntu that your hardware clock was set to GMT (Greenwich Mean Time, aka Coordinated Universal time). Hence the 6 hour difference.

---


---
title: "Xorg + 915GM chipset: screen doesn't power off (dpms)"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by quini on 2006-08-13
Hallo!

A friend's Benq S52 laptop (915GM chipset with integrated Intel video card) has a problem with Xorg: despite the screen is set to power off in 1 minute, it does not.

That behaviour is a problem on a laptop, as it wastes battery power.

Xorg logs show the following:
-----
antonio@benq:~$ cat /var/log/Xorg.0.log | grep DPMS
(II) Loading extension DPMS
(II) I810(0): No DPMS capabilities specified; RGB/Color Display
(**) I810(0): DPMS enabled
-----

It says DPMS has been enabled, but... ](*,) 

Any idea?  TIA  ;)

---


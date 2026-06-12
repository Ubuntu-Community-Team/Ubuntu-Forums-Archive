---
title: "Radeon R9 390X fans not spinning"
date: 2016-03-11
forum: Hardware
---

### Post by dugite-code on 2016-03-11
OS: xubuntu 15.10
Motherboard: Asrock Fatal1ty H170
Graphics card: Gigabyte Radeon R9 390X
RAM: 32 Gig Kingston
PSU: Corsair HX850

Upgraded my motherboard so I performed a fresh install of xubuntu 15.10. However my graphics card fans were not spinning AFTER I passed the hard drive encryption entry screen at boot, at bios fans run as expected.

As the card was starting to get quite hot to the touch I installed the proprietary fglrx drivers from the additional drivers dialogue, this hasn't helped.

I am currently using the command ```
aticonfig --pplib-cmd "set fanspeed 0 100"
``` in order to keep the card cool whilst searching of solutions

*Edit: I should note with my previous install of xubuntu and Asus motherboard I did not have this issue

---


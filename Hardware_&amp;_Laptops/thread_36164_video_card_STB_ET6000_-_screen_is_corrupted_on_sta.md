---
title: "video card STB ET6000 - screen is corrupted on startup"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by matej on 2005-05-22
I have whole screen corrupted on startup.

When I switch to text mode and back to graphic mode, then screen is ok. But after that, text mode is corrupted instead. It behave like that with vesa and tseng xorg drivers.

Bugzilla: [https://bugs.freedesktop.org/show_bug.cgi?id=3363]("https://bugs.freedesktop.org/show_bug.cgi?id=3363")

Any workaround?

---

### Post by matej on 2005-06-09
Solved, it was caused by some other program than X.org. 

bug in Ubuntu, that caused that: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8801]("https://bugzilla.ubuntu.com/show_bug.cgi?id=8801")
(fixing this bug solves problem)

more info in my X.org bug comments: [https://bugs.freedesktop.org/show_bug.cgi?id=3363]("https://bugs.freedesktop.org/show_bug.cgi?id=3363")

---


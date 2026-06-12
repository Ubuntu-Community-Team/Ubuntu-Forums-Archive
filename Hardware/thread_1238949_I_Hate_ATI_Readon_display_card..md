---
title: "I Hate ATI Readon display card."
date: 2009-08-13
forum: Hardware
---

### Post by Nathan.zhu on 2009-08-13
I have a thinkpad r400 series laptop.  install ubuntu 9.0.4 64bit, I try to find way to install display card driver in it. find some archives and try many many ways to do it, alway failed. 
So, Suck. let me reinstall system more times.
xorg open soureces driver and ATI Catalyst™ 9.7 Proprietary Linux x86 Display Driver
both not successed.
But hope somebody have a efficient way to resolve it or somebody install success driver, maybe can sharing for me.

---

### Post by Tigersmind on 2009-08-13
I keep finding that your laptop has a Intel GMA 4500MHD Dynamic Video Memory Technology 5.0  Thats it, no mention of ATI. Was yours a special order and if so whats the model?

ATI did just legacy a bunch of cards. No drivers past 9.3 will work and those drivers do not work with Jaunty (I have to use the default driver).

---

### Post by Nathan.zhu on 2009-08-13
There have two diaplay card in my laptop.
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

---

### Post by markbuntu on 2009-08-13
To use the ati driver you need to disable the intel in the bios.

---


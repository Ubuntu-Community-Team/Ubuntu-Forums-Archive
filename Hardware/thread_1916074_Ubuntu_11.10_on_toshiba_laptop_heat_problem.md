---
title: "Ubuntu 11.10 on toshiba laptop heat problem"
date: 2012-01-27
forum: Hardware
---

### Post by ivh90 on 2012-01-27
I have installed ubuntu 11.10 64 bit on a toshiba a500 laptop and everything is working well except for the heat problem, when i check for cpu temp it is usually between 65 - 75 C when Idle and i dont think this is ok, I have tried several possible fixes but nothing seems to be working.
note: my laptop has an nvidia card and i installed the recommended driver so i dont think it is a GPU problem.

any help?

---

### Post by SpkrBox850 on 2012-05-02
What I would do is partition the drive and install XP on the other half then run speedfan to compare your temperatures.

That way you can tell if the systems always that hot or if Ubuntu is making it hotter than it should be.

---

### Post by 1grouchy on 2012-05-03
I have a dual boot Ubuntu 11.10 64bit / Win 7.
Toshiba L500, Intel i3, Radeon HD 5145.

Until a few days ago my CPU temperature was from 45c to 55c on Ubuntu. These days 75c - 88c!!!
Windows 7 keeps temperature on 45 - 55 on fresh install (without Gadgets etc.).
I try:
- Reinstall Ubuntu 11.10 64bit
- Install Ubuntu 12.04 64bit
- Install Ubuntu 11.10 32bit (In this moment I'm downloading Updates and cpu temp is 82c- 86c)

The main problem is that Fan works all the time at the same speed (Low), and when the CPU is intensive temperature is growing to to 88c and in that point Fan begins to work properly and reduce the temperature but just to 80c.

I use Ubuntu for years and I like it, but after this problem, Win 7 rules.

---

### Post by 1grouchy on 2012-05-03
I solve my problem with installing FGLRX driver from Aditional Drivers instead of official Amd Ati Catalyst.

---


---
title: "Laptop Fixes-Contrast 11.04"
date: 2011-06-14
forum: Hardware
---

### Post by Montalo on 2011-06-14
hello all

my screen on my laptop is unusable, and i am forced to use an external monitor in order to use my laptop. that said, a suggestion said to me was to check the contrast, and that may be the problem. the brightness is at 100%, so that couldnt(i think) be it

my question to you guys. How would i go about changing the contrast on ubuntu 11.04?

many thanks in advance

(also, if you have any other ideas on why my screen isnt working, those are appreciates as well)

---

### Post by Toz on 2011-06-14
It would be helpful if we knew something about your computer. For starters, what is the make/model? And, open a terminal window, type in the following, and post back the results:```
lspci | grep VGA
```

---

### Post by Montalo on 2011-06-14
sorry about that

pavillion dv5
dv5z-1000


jon@jon-HP-Pavilion-dv5-Notebook-PC-KS878:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

---

### Post by Toz on 2011-06-14
Did you enable the restricted drivers? (System->Admin->Additional Drivers)

Does your laptop have brightness keys? Do they work?

---

### Post by Montalo on 2011-06-21
well, it ends up that all it was was a hardware problem

i replaced the power inverter, and my screen is perfectjust

---


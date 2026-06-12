---
title: "Amd cpu @ 60 °c"
date: 2011-05-03
forum: Hardware
---

### Post by rebel.yell on 2011-05-03
hi!
I have an AMD Laptop w/ AMD P540 and Radeon HD5470.
Problem: 
Win 7 - CPU @ 43 °C - measured w/ CoreTemp
Ubuntu 11.04 - CPU @ 60 °C - measured w/ XSensors

why?

---

### Post by ivanovnegro on 2011-05-03
It could be due to the newest power regression in the Kernel 2.6.38 used in Natty but dont have to.
But it could be also something else, maybe you are watching Youtube videos, Flash content in general what increases the CPU usage and also the temperature of it.
I would look at your processes that are running, System Monitor or type in a terminal:

```
top
```,

to see what is running and what is consuming CPU. Could be whatever.

---

### Post by rebel.yell on 2011-05-03
I forgot to mention that the laptop is in idle state and ubuntu is a natty fresh install.
CPU @ 5% load.

---


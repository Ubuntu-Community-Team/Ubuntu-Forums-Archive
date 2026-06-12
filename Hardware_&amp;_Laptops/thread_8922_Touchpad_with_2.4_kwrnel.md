---
title: "Touchpad with 2.4 kwrnel"
date: 2004-12-22
forum: Hardware &amp; Laptops
---

### Post by metf on 2004-12-22
For  to working D211 Nokia card i had to downgrade to kernel 2.4 series (no driver for 2.6).  But in 2.4 enviroment dont work touchpad (synaptics driver) . Everything is the same but in 2.4 there is no psmouse kernel module.  There is loaded only mousedev driver in 2.4.  I dont know which driver had to load or what another do to work touchpad.  cat /dev/psaux is working (type a lot of mishmash if I use touchpad) so there is no problem with special file. And XFree86-4.config is ok because in 2.6 is everything ok. Please help, thanks

---


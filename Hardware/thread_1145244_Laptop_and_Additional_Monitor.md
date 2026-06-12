---
title: "Laptop and Additional Monitor"
date: 2009-05-01
forum: Hardware
---

### Post by dmweyer on 2009-05-01
Hi All,

I am new to ubuntu and have recently moved over to ubuntu at home on my desktop which smooth with little problem. I decided to setup my lapyop (HP Compaq 6735s), which I use for work, with dual boot. 

The first problem that I have come across is that I cant get compiz to run when I use my laptop with an additional monitor. The message, if I remember correctly, was something along the lines of cant exceed 2048?? resolution. 

I am assuming that this is just due to me not setting something up correctly. Has anyone else come across this problem and if so could you resolve it?

Please let me know if there is any other info I should submit that may help diagnose.

Thanks in advance
Dill

---

### Post by BugFixBug on 2009-05-01
Do you have the restricted nvidia drivers installed? and used "NVIDIA X server settings" to enable dual monitors?

---

### Post by dmweyer on 2009-05-01
Its an intel graphics card (Mobile Intel GM45 Express chipset ) not nvidia. Just notice I put the incorrect laptop model, is a 6730s.

---

### Post by dmweyer on 2009-05-05
bump

---

### Post by Mez on 2009-05-07
I've briefly worked with dmweyer on this, and we've come to a resolution.

It seems that this was because of the limitation of the Intel driver, upgrading to experimental packages for X seems to fix this

You can find the experimental packages @

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

---


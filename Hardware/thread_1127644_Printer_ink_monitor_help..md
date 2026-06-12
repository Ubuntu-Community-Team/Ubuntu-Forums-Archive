---
title: "Printer ink monitor help."
date: 2009-04-16
forum: Hardware
---

### Post by GARoss on 2009-04-16
I have successfully downloaded & installed drivers & software from Canon Japan printer support, [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/), but having trouble getting monitor software to work. There are numerous png files that can be found of ink monitor levels & windows (all in Janpanese of course; but, that can be fixed!) 
Has anyone figured this out? 
Is there cups software that supports ink monitoring?
George

---

### Post by GARoss on 2009-04-17
Bump

---

### Post by patond on 2009-04-26
Hi - I had this problem with Intrepid with a Epson SX200.  In a terminal type:
pipslitestm

This provides a graphical output of the ink levels.

If it works you can put it in a menu.

In jaunty I got an error message and had to start piplited as root as follows:
/etc/init.d/pipslited start

Then pipslitestm worked OK.

---


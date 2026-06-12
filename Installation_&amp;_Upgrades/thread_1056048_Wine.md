---
title: "Wine??"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by Me_the_man on 2009-01-31
Ok i want to install wine but everytime i want to install it a message pops up saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

help pls

---

### Post by taurus on 2009-01-31
Make sure you have closed add/remove or synaptic first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install wine
```

---

### Post by fenario on 2009-01-31
I had wine problems too. The old wine files I installed did not work on intrepid.
The budgetdedicated site did not work either with synaptic. So I searched and downloaded the file manually from:
[http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/](http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/)
It is the latest version 1.1.14 and now netmeter (NetMeter_v113.exe) works well.

good luck

rolf

---

### Post by Me_the_man on 2009-02-01
Yea thanks a lot :)

but now i have a new problem... 
when i start an application, it just clses as soon as i want to put summin in

---


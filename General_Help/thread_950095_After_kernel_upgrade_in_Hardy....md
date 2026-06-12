---
title: "After kernel upgrade in Hardy..."
date: 2008-10-16
forum: General Help
---

### Post by repsol on 2008-10-16
My wireless broke.

It took away wlan0 and created wlan1. I can't connect to anything. If I roll back everything works. I am fine with rolling back, but I was wondering if anybody else is having the same problems.

Gateway laptop M1625
USB internal wireless card

repsol@pedrosa:~$ lsusb
Bus 006 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 006 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 006 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.

Another weird thing is the WICD doesn't work anymore either. Actually if I manually type sudo /etc/init.d/networking restarts WICD. If I type dmesg

I find wlan1 tx is disabled. 

Again this is weird because I use wlan0 not 1 and all of a sudden it is re-written and TX is disabled. 

Thanks for any advice or if there is anybody having the same problem that wants to work on it together

:popcorn:

---


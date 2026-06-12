---
title: "Wi-fi sometimes works sometimes doesn't"
date: 2009-07-05
forum: Hardware
---

### Post by MysteriousHoatzin on 2009-07-05
I have a Thinkpad T30 and I've had Ubuntu on it since I accidentally pwned the XP recovery partition some six months ago. The wifi under Intrepid worked better than it did when this was a Windows machine. But since I upgraded to Jaunty on certain boots it connects instantaneously and if I disconect and connect again, it connects fine, but on other boots it spins for a minute and declares it cannot connect. It can see the signal just fine, and I can sit there forever clicking on the network I want and it will spin for a minute and not connect.

The weirdest thing about it is that **if I reboot, chances are it will work fine**. This doesn't happen just with my home router, but pretty much any and all friendly wifi spots I connect to.

I have no idea where to start troubleshooting this one.I tried poking around with **nm-tool** and **NetworkManager**, but I don't see anything conspicuous and it doesn't seem others have the same flavor of wifi woes I do.

---

### Post by MysteriousHoatzin on 2009-07-06
just fwy, restarting NetworkManager itself rather than whole machine fixes the problem more reliably—or at least, less laboriously than restarting the whole machine.

---


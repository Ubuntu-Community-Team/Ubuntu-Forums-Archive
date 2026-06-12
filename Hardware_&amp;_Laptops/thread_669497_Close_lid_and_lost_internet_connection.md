---
title: "Close lid and lost internet connection"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by jeepintx on 2008-01-16
Hello, I have a compaq v6000 and im running kubuntu 7.10. Ive been having hell with my internet connection and just now noticed my wireless card loses connection when i close the lid. I don thave it on suspend or hibernate. It just turns off the monitor and loses connection. Ive heard of irq conflicts with broadcom 4311 wireless cards and nvidia cards does anyone know if this could be the problem? If so i there a fix or workaround for it. Thanks it advance

---

### Post by jeepintx on 2008-01-17
bump!

---

### Post by freddyp on 2008-01-17
Have you checked System>Preferences>Power Management to make sure the "When laptop lid is closed" actions are set to "Do nothing" for the AC and Battery tabs?  Don't mean to insult, but thought we'd start with the simple things first.  Or is that what you meant when you said "I don't have it on suspend or hibernate"?

---

### Post by jeepintx on 2008-01-18
no my computer is set to do nothing when i close the lid. it seems like when the monitor turns off my wireless card just stops working

---

### Post by jeepintx on 2008-01-18
bump!

---

### Post by Qdlaty on 2008-07-19
It's strange but after one year from the last post I'm also having this problem with 8.04 i386.

But the solution was quite simple - just removing the linux-backport-modules fixed the problem.

---


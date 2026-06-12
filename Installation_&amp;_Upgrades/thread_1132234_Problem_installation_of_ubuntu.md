---
title: "Problem installation of ubuntu"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by nounouING on 2009-04-21
hi ;
i install ubuntu 8.10 in my PC. The installation is completed successfully. 
When i restart my PC and i write the password and the username, i listen a sound indicate that the authentification is correctly done but a black screen appears and nothing appears. I try the Live ubunt and it run corrcetly
My PC is Fujistu SIEMENS Amlio Pro v 2060.
Can you help me to solve this problem.
Thank you.

---

### Post by reis.tiago on 2009-04-21
Not sure if it will solve the problem, but still try to reconfigure Xorg

# sudo dpkg-reconfigure -phigh xserver-xorg

To access a terminal, press "Ctrl + Alt + F1" in the login screen, then insert your user and password.

---


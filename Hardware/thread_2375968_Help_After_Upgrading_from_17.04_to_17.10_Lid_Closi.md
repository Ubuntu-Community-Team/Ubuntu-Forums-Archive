---
title: "Help: After Upgrading from 17.04 to 17.10 Lid Closing action no more configurable?"
date: 2017-10-29
forum: Hardware
---

### Post by saladriel on 2017-10-29
Hello, I've recently updated my laptop (An Acer Aspire 5738G) from 17.04 to 17.10 and my "Do Nothing" configuration on lid closing has gone lost: now the OS suspends everytime I close my laptop. 
On top of that I can't seem to find lid closing action configuration anywhere (This can be my bad, but I spent a couple of hours searching).

Could please somebody help me?

Thanx in advance

---

### Post by saladriel on 2017-10-30
Bump

---

### Post by saladriel on 2017-10-30
Done some research: 
Lid closing action is no more configurable via graphical interface with the new version of Ubuntu.
I found it is still configurable modifiying logind.conf, but:
If I try to run Gedit with Sudo, I get an error telling "Cannot open display :0" 
If I try to run gksudo or gksu the passowrd request window opens, but you can't actually type in it and the password is typed into the shell, making it unusable.

---

### Post by saladriel on 2017-10-30
Solved: 
- sudo nano /etc/systemd/logind.conf  
- inserted a line stating: HandleLidSwitch=ignore

[FONT=arial]After a reboot, the system does nothing when lid is closed[/FONT]

---


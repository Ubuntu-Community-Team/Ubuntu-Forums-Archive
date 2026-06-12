---
title: "change terminal login message"
date: 2008-10-09
forum: General Help
---

### Post by ThaddeusW on 2008-10-09
Ok I would like to change the terminal log in behavior. I have a bare Ubuntu install with fluxbox thrown in and no graphical log in manager, I just type startx. I want to change the login message when I first log in and get the command line. 

I also want to add a welcome message and maybe a fortune to my Xterms when opened.

---

### Post by Dr Small on 2008-10-09
When you say welcome message, I am assuming you mean MOtD. That can be changed in /etc/motd.

If you want to have fortune spill out some fortune telling at the open of xterm or any bash prompt for that matter, append the "fortune" command at the end of your ~/.bashrc

Dr Small

---

### Post by SuperSonic4 on 2008-10-09
> **Dr Small said:**
> When you say welcome message, I am assuming you mean MOtD. That can be changed in /etc/motd.

If you want to have fortune spill out some fortune telling at the open of xterm or any bash prompt for that matter, append the "fortune" command at the end of your ~/.bashrc

Dr Small

Or you can have any special fortune you have installed too

mine has "fortune futurama" and it gives me futurama quotes xD

---

### Post by KeyserSoze93 on 2008-10-10
For the pre-login message, edit /etc/issue (by default, it just says Ubuntu version whatever)

For the post-login message, use motd as Dr Small said.

---


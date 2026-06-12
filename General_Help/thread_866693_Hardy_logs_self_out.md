---
title: "Hardy logs self out?"
date: 2008-07-22
forum: General Help
---

### Post by TrikeKid on 2008-07-22
Twice now I've had my computer log me out without my doing anything. I'll be surfing the web and the screen will go black save for a bunch of dash like lines then it brings me to the login page. I'm not doing anything extreme here, I simply had pidgin open and 2 or 3 tabs in FF running, all of which were already loaded. It's only happened so far while running FF (I have a few add ons, nothing too intense, just download statusbar, and download helper currently. Had Cooliris and Forecast Fox running the first time it did it, but I've decided to go back to not running a status bar so forecast fox went away, and I just don't use cooliris anymore. Everything is up to date system wise and I have more than enough power to run everything.

---

### Post by Gunman1982 on 2008-07-22
Sounds like your X server crashes from time to time. You can check the logs by opening a console and executing 'less /var/log/Xorg.0.log'. Or you log out, switch to a terminal 'ctrl+alt+F1', log in with username/password, execute: 'sudo killall gdm' and then execute startx. If it crashes then you can see what happened on the terminal. At least you should.

---


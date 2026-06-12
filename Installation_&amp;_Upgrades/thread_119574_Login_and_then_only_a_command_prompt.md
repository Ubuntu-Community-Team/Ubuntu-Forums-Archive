---
title: "Login and then only a command prompt"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by corytoneill on 2006-01-19
I installed ubuntu from the iso burnt to a disk that I downloaded from the website... Everything seemed to go fine.. then It has me login.. I do and all it it shows is a command prompt type thing... I need help I am new to linux

---

### Post by aysiu on 2006-01-19
Does it say *Login:* or does it say *blahblahblabh@ubuntu~$*?

If it says *login*, log in.

Then, try this: ```
startx
```

If that doesn't work, try this: ```
sudo dpkg-reconfigure xserver-xorg
```

If that doesn't work, try this: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by corytoneill on 2006-01-19
Thank you... the third thing seems to be working it is at 5% so far

---

### Post by aysiu on 2006-01-19
[QUOTE=corytoneill]Thank you... the third thing seems to be working it is at 5% so far[/QUOTE] My guess is that you accidentally did a server install, which doesn't install a graphical user interface.

---


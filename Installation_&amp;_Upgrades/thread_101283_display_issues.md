---
title: "display issues"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by reddog on 2005-12-09
im having trouble with my display on ubuntu......it says it will shut down the x server but i don't know how to fix this issue could someone please help??when it says shutting down the x server it says something about xfree86 but i don't know what to do with this again any input would certainly help

---

### Post by blueplazma on 2005-12-09
Can you post your X server log files (/var/log/Xorg.0.log) as well as the output of running ```
sudo /etc/init.d/gdm restart
```

---

### Post by rlange on 2005-12-09
[QUOTE=blueplazma]Can you post your X server log files (/var/log/Xorg.0.log) as well as the output of running ```
sudo /etc/init.d/gdm restart
```[/QUOTE]

To do the above,go to Applications then Terminal then enter:
```
gedit /var/log/Xorg.0.log
```

then under edit select **select all** then **copy**

and paste in next message

---


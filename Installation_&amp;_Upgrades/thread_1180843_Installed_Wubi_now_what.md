---
title: "Installed Wubi now what?"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by Leventcos21 on 2009-06-07
I downloaed WUBI and it seemed to install. I comes up with a command prompt asking for username & password. I enter but all I get is ```
levent@ubuntu: ~$
```
 
When I tpe in sudo apt-get install ubuntu-desktop. it says that the desktop version is already installed. What happens next?
 
Laptop spec:
AMD Athlon XP-M
512 RAM
80GB HD
 
 
Thanks

---

### Post by oldos2er on 2009-06-07
Try **startx**

---

### Post by Leventcos21 on 2009-06-07
Thanks, but that leads to a 
EE Chrome(0): NO valid modes found
EE Screens found, but not ahve a usable configuration.
 
 
FATAL Server Error: no screens found
 
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3) : server error
 
When I try /etc/X11/xorg.conf
I get a Permission denied.
 
I went to this thread and was able to resolve my video card conflict for my averatec laptop.
[http://ubuntuforums.org/showthread.php?t=930121&page=8](http://ubuntuforums.org/showthread.php?t=930121&page=8)
 
Thanks in advance.

---


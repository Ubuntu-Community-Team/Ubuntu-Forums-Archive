---
title: "changing the monitor"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by legit on 2005-09-19
hey all,
so i have two inter-related problems.  First off i finally finished installing the nvidia drivers for my card, this is all well and good but i am still having problems with my monitor.  the computer stills thinks its using a crt monitor and i switched over to an lcd monitor. problem 1: how do i switch it to recognize the lcd monitor?  secondly i should be able to get 1280x1024 screen resolution but its not allowing me to go this high, so how can i make it go this large?
thanks
- legit

---

### Post by heimo on 2005-09-20
Close all programs, type in terminal (this closes your graphical user interface):
 ```
sudo /etc/init.d/gdm stop
``` 

Log in, run:
 ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg

``` 
This will ask you bunch of questions about graphics card, monitor, keyboard, mouse... And it can do some probing / autoconfiguring too. After you've your new configuration file ready, start X using:
 ```
sudo /etc/init.d/gdm start
``` 

Some related information:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by legit on 2005-09-20
awesome that works, thanks

---


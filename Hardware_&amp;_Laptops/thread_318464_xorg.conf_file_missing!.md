---
title: "xorg.conf file missing!"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by ashi on 2006-12-14
Hi

A friend of mine played around with his Ubuntu (6.10) computer, while trying to change the screen resolution. He opened a window with the command ctrl+alt+back space, and then he pressed the shutdown button. When he then restarted, the file corg.conf was missing from the /etc/X11/ dir, and he can't load ubuntu in graphical interface anymore. How do I / he recreate the xorg.conf file?

---

### Post by kimusabi on 2006-12-14
Yea, The amount of times I've done that.
When you reboot, press CTRL+ALT+1 and login, afterwards type in 

```
 sudo dpkg-reconfigure xserver-xorg 
```

That'll guide you through making a new xorg. 

-Kimmeh

---

### Post by pay on 2006-12-14
I think the command is ```
Xorg -conf
```
EDIT: or as kimusabi said " sudo dpkg-reconfigure xserver-xorg" which I think is more Ubuntu specific.

---

### Post by Ethos on 2006-12-14
Is he still stuck in in non gui mode? If so tell him to issue the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
sudo /etc/init.d/gdm restart
``` and he should be brought back to the graphical logon-- I had to do this a couple times when I was installing my nvidia drivers...

---


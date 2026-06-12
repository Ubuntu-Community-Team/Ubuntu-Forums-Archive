---
title: "remotely reboot with putty"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by roody on 2007-12-14
Hi
Whenever I try to reboot remotely with putty, my laptop shuts down.

the command I am using:

sudo reboot

---

### Post by purdticker on 2007-12-14
I always do a:

> sudo shutdown -r now [optional description]

-r requests a reboot

---

### Post by roody on 2007-12-17
I am gonna try today when i m not home, thx for ur help



> **purdticker said:**
> I always do a:



-r requests a reboot

---

### Post by roody on 2007-12-17
I tried it and it didn't restart. Now i can't start it remotely hehe

> **roody said:**
> I am gonna try today when i m not home, thx for ur help

---

### Post by njparton on 2007-12-17
```
sudo reboot
```
that works for me via putty.

What do you have set in gnome power management?

Also search these forums for suspend or reboot hooks. There are a set of scripts that are run when you press the power button etc. you may need to remap these so that your computer knows what to do when you press a given button or issue the equivalent command.

---

### Post by kesman on 2007-12-17
can you reboot your computer even locally with sudo reboot or sudo shutdown -r now ?

---

### Post by roody on 2007-12-18
yes it works locally, i dnt know how to check the power management, any hint? I m using ubuntu with KDE...

thx

> **kesman said:**
> can you reboot your computer even locally with sudo reboot or sudo shutdown -r now ?

---

### Post by njparton on 2007-12-18
In that case install Kpowersave (it adds an icon to the system tray when run).

---


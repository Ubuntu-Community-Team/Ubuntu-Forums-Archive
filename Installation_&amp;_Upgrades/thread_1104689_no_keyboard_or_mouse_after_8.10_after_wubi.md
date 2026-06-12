---
title: "no keyboard or mouse after 8.10 after wubi"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by deanf on 2009-03-23
I've installed 8.10 on my laptop via wubi.  When I get to the GUI login screen, the keyboard doesn't work and I have a mouse cursor that won't respond to my touchpad.  I can turn caps-lock on/off and do Ctrl-Alt command, so I know they keyboard is responding.  Appears to be a ubuntu problem . . .

Anyone . . . ?

---

### Post by deanf on 2009-03-24
bump

---

### Post by deanf on 2009-03-24
Also during boot I get the following messages:

* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon          [[COLOR="Red"]fail[/COLOR]]

[COLOR="Red"]*[/COLOR] Can't start Hardware abstraction layer - Please ensure dbus is running

---

### Post by deanf on 2009-03-25
I've installed 8.10 on my laptop (Gateway model W340UI or MT3705, depending on which sticker you look at) via wubi. When I get to the GUI login screen, the keyboard doesn't work and I have a mouse cursor that won't respond to my touchpad or USB mouse. I can turn caps-lock on/off and do Ctrl-Alt commands, so I know they keyboard is responding. Appears to be a ubuntu problem . . . I was able to login during the installation process.

Also during boot I get the following messages:

* Starting Avahi mDNS/DNS-SD Daemon avahi-daemon [[COLOR="Red"]fail[/COLOR]]

[COLOR="Red"]*[/COLOR] Can't start Hardware abstraction layer - Please ensure dbus is running



Anyone . . . ?

---

### Post by overdrank on 2009-03-25
Please do not create multiple threads on the same issue. Threads merged.
Are you able to reach a virtual terminal with the ctrl, alt, F1 keys.

---

### Post by deanf on 2009-03-25
Yes.

---

### Post by overdrank on 2009-03-25
> **deanf said:**
> Yes.

Ok then if you can login there, use the command ```
sudo /etc/init.d/gdm stop 
```
Then```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then use the command ```
sudo /etc/init.d/gdm start 
```

---

### Post by deanf on 2009-03-25
All commands successfully executed.  Same result after computer restart.

---

### Post by deanf on 2009-03-26
Just followed steps in [this post](http://ubuntuforums.org/showthread.php?t=964847&highlight=Can%27t+login).  Still doesn't work.

---


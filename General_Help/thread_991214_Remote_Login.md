---
title: "Remote Login"
date: 2008-11-23
forum: General Help
---

### Post by PcFrk256 on 2008-11-23
The few times a month that I have to reboot my server, I have to physically go to it and login before I can VNC to it later. How can I access the main login screen using VNC? I'm sure it's possible...just...how?

---

### Post by ITAndrew on 2008-11-23
You might want to install the tight vnc server. I know for the embedded VNC server Ubuntu uses you need to either log in first, or have the system automaticly log in.

In other words use:

> sudo apt-get update && sudo apt-get install tightvncserver

then you can start a VNC server by ssh into the system as local user then typing:

> tightvncserver :1

You will no longer need to physicly log in to open a VNC server.

---

### Post by PcFrk256 on 2008-11-23
...I need the desktop view....this is just giving me a console...

---

### Post by ITAndrew on 2008-11-23
PuTTY my good sir..

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---


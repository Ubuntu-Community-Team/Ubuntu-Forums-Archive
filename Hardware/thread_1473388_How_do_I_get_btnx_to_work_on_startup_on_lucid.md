---
title: "How do I get btnx to work on startup on lucid ?"
date: 2010-05-05
forum: Hardware
---

### Post by kubunut on 2010-05-05
Hey everyone,


Been trying to setup btnx to automatically start on boot. Having no luck using Autostart add script option in System Settings.

How do I get this command to fire up during startup ?

sudo /etc/init.d/btnx restart


Thanks,

Really impressed with Lucid so far. It seems better at multitasking than Karmic.

---

### Post by dino99 on 2010-05-05
have you tried : sudo btnx, or system Tools -> btnx, or system prefs starting apps ?

old howto:

[http://cad.cx/blog/2008/04/25/howto-install-btnx-for-better-mouse-control-in-ubuntu-hardy/](http://cad.cx/blog/2008/04/25/howto-install-btnx-for-better-mouse-control-in-ubuntu-hardy/)

---

### Post by kubunut on 2010-05-05
> **dino99 said:**
> have you tried : sudo btnx, or system Tools -> btnx, or system prefs starting apps ?

old howto:

[http://cad.cx/blog/2008/04/25/howto-install-btnx-for-better-mouse-control-in-ubuntu-hardy/](http://cad.cx/blog/2008/04/25/howto-install-btnx-for-better-mouse-control-in-ubuntu-hardy/)

Yeh saw that one. Didn´t help me add btnx to work on boot up.

If I run it normally it´&#347; fine System-->btnx-->restart btnx, but I want it to automatically start up.  ;)

I think the only thing KDE provides is Autostart a program or a script. None of these seem to work with a sudo command....


I am totally over my head :-s

Thanks anyway,

Kubunut

---

### Post by kubunut on 2010-05-05
OK I tried setting btnx as a program in Autostart, I edited the startup thing as root. Setting User and Group as root for it.

First time it asked for a root password, second time I tried sudo btnx and it asked for no root password. But still didn´t work.

Any other idea´s ?

---


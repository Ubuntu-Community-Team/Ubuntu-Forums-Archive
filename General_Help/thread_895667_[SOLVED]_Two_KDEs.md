---
title: "[SOLVED] Two KDEs??"
date: 2008-08-20
forum: General Help
---

### Post by armageddon08 on 2008-08-20
Hi everybody.....

I've installed KDE4 in my Ubuntu install. But....I don't think I'm quite happy with it. I would like to install KDE3 and also like to keep KDE4 as well.

Anybody could tell me how to do it?

---

### Post by piousp on 2008-08-20
Sure, just type (in a terminal):

```
sudo aptitude install kubuntu-desktop
```

and you will get your KDE3.5 along with KDE4 and gnome

I will recommend 'Aptitude' instead of 'Apt-get' since it will handle all the dependencies if you want to un-install it later.

Also, try to [check out this]("http://www.psychocats.net/ubuntu/kde") site

---

### Post by armageddon08 on 2008-08-20
Will this give me option to select between KDE3 and KDE4 at login-time?

---

### Post by piousp on 2008-08-20
It will be something like:


Session type:

 - Gnome
 - KDE
 - KDE 4


Just to let you know, i have kubuntu with KDE3 and KDE4 and there is no problem at all between the 2 of em.
They will create different config files and directories, dont worry about it.

---

### Post by armageddon08 on 2008-08-20
Thanks.........I'll do it now. Thank you.

---

### Post by piousp on 2008-08-20
You are welcome. If you run into any trouble, dont hesitate to ask :KS

---

### Post by a1437053 on 2008-08-20
> **piousp said:**
> Sure, just type (in a terminal):

```
sudo aptitude install kubuntu-desktop
```

and you will get your KDE3.5 along with KDE4 and gnome

I will recommend 'Aptitude' instead of 'Apt-get' since it will handle all the dependencies if you want to un-install it later.

Also, try to [check out this]("http://www.psychocats.net/ubuntu/kde") site


This worked great for me! I installed Kubuntu w/ KDE4.1 but wanted to downgrade/install KDE3.59

Thank you! (I couldn't handle the oversize PANEL, for now.)

Jose

---

### Post by piousp on 2008-08-21
Glad to hear that.
By the way, you CAN resize your panel on KDE4.

---


---
title: "compiz fusion icon in 8.10"
date: 2008-11-08
forum: General Help
---

### Post by acegik on 2008-11-08
hi does anyone knows how to install compz icon? when i install it and i put it in my tray, i click on it and it restarts my compiz when i right click in it it doesnt give mme the options like restart compiz or switch to emerald. plz im lost ive been trying to find the aswer or a week

thanx

---

### Post by masterpop on 2008-11-10
Hi, i have the same issue. I found that installing the emerald package using

sudo apt-get install emerald

and then restarting the fusion icon, brought that up.

However I still don't see the "Settings Manager"-- i'm guessing under 8.04 I had something already installed... so need to find what's missing.

---

### Post by fooman on 2008-11-10
masterpop,  for the "settings manager"...you will need to install "compizconfig-settings-manager" from synaptic,  or from a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

after it installs, you will find it in system > preferences....or in the fusion icon of course.

---

### Post by fooman on 2008-11-10
> **acegik said:**
> hi does anyone knows how to install compz icon? when i install it and i put it in my tray, i click on it and it restarts my compiz when i right click in it it doesnt give mme the options like restart compiz or switch to emerald. plz im lost ive been trying to find the aswer or a week

thanx

to use fusion icon,  all you have to do is go to applications > system tools and click on compiz fusion icon.  or in a terminal type:

```
fusion-icon
```

that will add it to your panel.

if you want it to autostart,  just add fusion-icon to the startup programs in system > preferences > sessions

hope that helps

---


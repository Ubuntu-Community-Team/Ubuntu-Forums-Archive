---
title: "Screen Resolution Help"
date: 2008-07-31
forum: General Help
---

### Post by xVehemencityx on 2008-07-31
Hi, I just got a new monitor today (finally!) (well, it's actually really old, but better than mine) and it only supports up to 800x600 resolution, and that's just not big enough for me.  Is there anyway to increase my resolution, even though I can't change it under Screen Resolution?

---

### Post by tuxxy on 2008-07-31
If your monitor only supprts that res its gonna be difficult to get it any higher I would of thought.

---

### Post by xVehemencityx on 2008-07-31
Well, I don't really know that's all it supports.  That's just all it shows.

---

### Post by Sef on 2008-08-01
> Well, I don't really know that's all it supports. That's just all it shows.

Google the model of the monitor that you have.  You should be able to find out what other resolutions you can get.

---

### Post by overdrank on 2008-08-01
> **xVehemencityx said:**
> Hi, I just got a new monitor today (finally!) (well, it's actually really old, but better than mine) and it only supports up to 800x600 resolution, and that's just not big enough for me.  Is there anyway to increase my resolution, even though I can't change it under Screen Resolution?

You may try the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by pietjanjaap on 2008-08-01
You cab try this if you think ubuntu did not identify your monitor coorectly:

With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.

---


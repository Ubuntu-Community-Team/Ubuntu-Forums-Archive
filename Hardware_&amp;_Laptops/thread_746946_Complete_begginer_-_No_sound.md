---
title: "Complete begginer - No sound"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by therev on 2008-04-06
Hi,

I've just installed Ubuntu 8.04 on an Advent Laptop and am so far very impressed, the only problem I've come across is that it seems not to play any sound. The laptop's sound card is a Realtek alc861-vd and after doing a bit of googling and searching through this forum I've seen it's a known problem - unfortunatly I'm still at a bit of a loss about how to fix it. Anyone got any suggestions?

Cheers in advance.

---

### Post by sdennie on 2008-04-06
I've had problems with 8.04 and sound as well (with a Dell laptop).  I would first make sure that you don't simply have sound muted (double click on the little speaker icon and see if you can fix it from there).  I'm not sure what the Ubuntu team has done to the 8.04 kernel because my sound works fine with a vanilla 2.6.24.4 kernel but, you could try to install the latest alsa drivers ([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)) and see if that helps.

(If you need help with installing the drivers, send me a private message and I can walk you through it.)

---

### Post by smartbei on 2008-04-06
Random sound thing (not sure if it applies here) - every time I reinstall I need to run
```

alsamixer

```
and make sure that everything is at 100. Use the arrow keys tomove around, ESC to exit.

---


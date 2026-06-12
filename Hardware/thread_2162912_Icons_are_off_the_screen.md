---
title: "Icons are off the screen"
date: 2013-07-16
forum: Hardware
---

### Post by anafshalom on 2013-07-16
I have a Toshiba Satelite Laptop using  Ubuntu 13.04.  I have an acer 24" monitor attached in extended desktop mode.  I have only a few icons on my desktop--laptop is primary--but they go off the top of the screen, so I can't see them.  I have not been anle to figure out how to fix this.

Any idead?

Reuven

---

### Post by dino99 on 2013-07-16
into a terminal:

dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

---

### Post by anafshalom on 2013-07-16
> **dino99 said:**
> into a terminal:

dconf reset -f /org/compiz/
unity --reset-icons
setsid unity

OK, so I think there is a misunderstanding here.  I am not having a problem with the launcher icons.  My problem is with the file and folder icons I have placed on my desktop.  When I choose "Organize Desktop by Name" from the deskltop contextual menu, the icons arrange themselves in a column at the right of my laptop monitor (that part is fine) but the top icons in the column are off the screen.

Can you (or somebody) help me with this?

Reuven

---

### Post by jp734 on 2013-07-16
When you move your mouse to the top of the screen or towards the direction where all you icons are, does the screen move until the icons show up?

---

### Post by anafshalom on 2013-07-16
> **jp734 said:**
> When you move your mouse to the top of the screen or towards the direction where all you icons are, does the screen move until the icons show up?

no

---


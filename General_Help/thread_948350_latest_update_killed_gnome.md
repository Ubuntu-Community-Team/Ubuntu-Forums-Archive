---
title: "latest update killed gnome"
date: 2008-10-15
forum: General Help
---

### Post by mo.reina on 2008-10-15
today's update totally screwed up my gnome.  now all i get is a white screen with the mouse pointer.

is there any way to rollback to what it was before the update? i'm using another computer right now to write this, i really need my lappy to get back online cuz i use it at work.

---

### Post by geirha on 2008-10-15
Sounds like a problem with compiz and the graphics card driver. What graphics card driver do you have, and how did you install it?

Also, It's probably the kernel update that triggered this, so try the previous kernel from the grub menu next time you boot.

---

### Post by mo.reina on 2008-10-15
graphics card is ATI Radeon 2400, installed throught catalyst driver.

i've tried using the previous kernel, still a no go.  even recovery mode brings up the white screen.

---

### Post by mo.reina on 2008-10-16
seems like the issue is between the ati driver and the latest xorg.  at least that's what i gathered from several sources.  i've just done a fresh install from a newly downloaded version of hardy, and as soon as i install the ati driver it gives me the white screen right away, compiz hasn't even been enabled yet.

is there any way to use an older version of xorg?  anyone else have this problem?

---

### Post by pabloscotty on 2008-10-16
I have the same issue. you can run your system in "safe mode". To me it works for while.

---

### Post by pabloscotty on 2008-10-16
solved!!! reistaled ATI Drives to new ones, and works pefectly !!!

---

### Post by mo.reina on 2008-10-16
which new ones?  i downloaded the driver from the ATI website yesterday and still have that issue.

---

### Post by pabloscotty on 2008-10-17
The problem is - compiz!!!. When I log in safe mode everything works pretty well but I tryed to turn compiz on the same thing happened. So I removed previous driver with Envy, dowloaded latest from ATI and problem is gone. My card is FireGL 3100.

good luck.

look here: [http://brainstorm.ubuntu.com/idea/7426/](http://brainstorm.ubuntu.com/idea/7426/)

---


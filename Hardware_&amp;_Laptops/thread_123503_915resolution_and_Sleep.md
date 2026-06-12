---
title: "915resolution and Sleep"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by macbuff on 2006-01-30
On my DELL Latitude D610, I managed to get the beast to work in 1400x1050 by running the 915resolution program just before X is started.  If the laptop is put to sleep, it reverts to 1280x1024 on wakeup.  Any ideas on how to get the beast to maintain 1400x1050 ?

John

---

### Post by zachstruck on 2006-02-02
I have a similar problem.  I'm running Dapper with 915resolution to fix my resolution.  Hibernate works except that it doesn't reload the script to fix the resolution.  I would guess that the problem has something to do with the resume script, or something.  But I really don't know...

---

### Post by Rollmops on 2006-02-03
[QUOTE=macbuff]On my DELL Latitude D610, I managed to get the beast to work in 1400x1050 by running the 915resolution program just before X is started.  If the laptop is put to sleep, it reverts to 1280x1024 on wakeup.  Any ideas on how to get the beast to maintain 1400x1050 ?

John[/QUOTE]
Try to use the 855resolution package wich comes with Ubuntu. This has all the scripts needed to get the correct resolution after suspend. Don't forget to fill in the correct settings in yout /etc/default/855resolution file.
I'm using this with no problems on my Samsung X20 notebook.

---

### Post by macbuff on 2006-02-03
855resolution is for the 855G chipset.

915resolution is for the 915G chipset (which is in the DELL Latitude D610) and is just a recompiled copy of 855resolution with extra functionality...

John

---

### Post by Rollmops on 2006-02-03
[QUOTE=macbuff]855resolution is for the 855G chipset.

915resolution is for the 915G chipset (which is in the DELL Latitude D610) and is just a recompiled copy of 855resolution with extra functionality...

John[/QUOTE]
That's right... but 855resolution does it also without much configuration. Just put your desired resolution in /etc/default/855resolution. I've got a 915GM chipset and it runs well this way.. ;-)

---


---
title: "No Audio Ubuntu 8.04 Acer Laptop"
date: 2008-09-27
forum: Hardware
---

### Post by jptelthorst on 2008-09-27
I just installed Ubuntu 8.04, I have an Acer Travelmate 2440.  A Volume control icon is displayed next to the clock, but I don't actually have audio.  I've tried youtube videos as well as the system sounds and nothing.  Any help would be appreciated.

---

### Post by TriggerIsHappy on 2008-09-27
I have an Acer Aspire 5920 and had the same problem with the sound. One of the main threads I found that helped me out was the following. Give it a try.


[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Trigger

---

### Post by NoWayBill on 2008-09-27
I've an Acer Extensa 5620Z.
Although my sound worked initially, it didn't work right.
My sound chip is Intel.
Had to add...

options snd-hda-intel model=acer

...to /etc/modprobe.d/alsa-base

---

### Post by jptelthorst on 2008-09-28
> **NoWayBill said:**
> I've an Acer Extensa 5620Z.
Although my sound worked initially, it didn't work right.
My sound chip is Intel.
Had to add...

options snd-hda-intel model=acer

...to /etc/modprobe.d/alsa-base

That worked, thanks!

---


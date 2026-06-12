---
title: "Constant &quot;beep&quot; noise on Dell Laptop: HDD's permanent activity???"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by Burnout on 2006-06-18
Hello, I want to catch up an old thread [http://www.ubuntuforums.org/showthread.php?t=86025&highlight=dell+beep](http://www.ubuntuforums.org/showthread.php?t=86025&highlight=dell+beep) 

I'm running Ubuntu 6.06 on a Dell Inspiron 6400 laptop. It works very nice with laptop-mode enabled using battery power BUT... there's one little problem. The harddisk spindown timer is set to 5 seconds. So the HD spins down very often. When it spins up, it makes a little beep (not the system beep, but the little beep I can here when I boot up the laptop). I tested this on windows and there it didn't seem to happen when I use a tool called SpinDown which sets the spindown timer to 3 secs (winxp spins up the hd nearly immediately).

So what to do about it? I raised the spindown timer, but that isn't solving the problem.

---

### Post by Burnout on 2006-06-18
I just tested this on windows XP too. I setted the harddrive spindown timer on 3 minutes. After a total spin down, the HD makes the same "beeping" noise.

Is this normal? And what to do about it?

The laptop-mode settings of 5 seconds hd idle time seems a bit to low for me.

---

### Post by evil_elman on 2006-06-18
My brother has a DELL laptop (can't remember model) in which the HDD is also making beeping noises. However, my brother's laptop HDD is beeping in a more constant way. It didn't matter if it spun down or if you're watching a movie (when the HDD is constantly reading)...

---

### Post by Burnout on 2006-06-18
It's not the typicial "vvvrrrrRRRkrrrrrvvvvvvvvvvvvvvvvvvvvv" sound. :p Really a little "beep" when it spinz up.

---

### Post by AeroHunter on 2006-08-07
I am having the similiar problem.  I have a XPS M140 same as 630M.  I only have it for about 4 months.  It starts beeping after 1.5 hour of continuous use.  The beeping noise occurs more freguently after awhile, then the systme will lock up.  I tried to monitor temperature of the system, it seems all temperature are normal.  so, it is not overheating,  What could it be?

---

### Post by dev.andrej on 2006-08-07
I have experienced this kind of random beeping on Latitude D600 and D610. (That is if you're talking about a high-pitch kind of beeping that you can only hear in a semi-quiet room)
What has worked for me is when I added an extra parameter sending to my kernel in grub.conf

I went to /boot/grub/grub.conf (or menu.lst) and added this: **idle=halt**
so my kernel line looked something like this:
```
kernel /boot/kernel-2.6.13-15 root=/dev/sda3 idle=halt
```

I hope this helps.

---


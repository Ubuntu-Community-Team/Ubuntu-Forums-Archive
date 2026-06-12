---
title: "Feisty Fawn hangs when idle on a Toshiba"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by fher98 on 2007-05-28
hi all!!!

See im takin a look at the new ubuntu, i intalled it on my toshiba Satellite A75-S125 and well really its quite impressive, the drivers for wifi, the power managment and cpu time... wow quite an amazing job (and Im dreaming with beryl finally on my desktop). 

But i have one problem, if I leave the laptop alone for a while, when i get back its like froze, the mouse responds but the windos or keyboard dont. 

I really dont know what happens when it goes idle, I tough it was gnome, so I installed kde, left it last night downloading other stuff and today in the morning it was showing the desktop no screen saver (cuz i was trying to see if the saver was hanging the computer), 

can any one help me out, thanks

---

### Post by xpd777 on 2007-05-29
I also have the same problem. I had my feisty installed on my A75-S1253. I have everything running, even have virtual box with xp and it's guest additions.

i also tried turning on my screen saver. still freezes.

then after tried turning off my screen saver. sill freezes.



is there a log file where in we could check on the errors? like a black box on an airplane.

---

### Post by xzero1 on 2007-05-29
There have been many reports of problems with suspend. Try turning that off. There are logs under System|Administration|System Log.

---

### Post by fher98 on 2007-05-30
Its not only suspend, something not right with acpi, of course the cpu frequency works nicely, but on the long run it just hangs more and more often, and I cant put my finger on the problem. A couple of times it froze just after i logged in...  


Anyways im back to Debian!

---

### Post by se2131 on 2007-06-04
I also have a Toshiba A75.  Follow these instructions to get it working perfectly fine again: [http://ubuntuforums.org/showpost.php?p=2528532&postcount=10](http://ubuntuforums.org/showpost.php?p=2528532&postcount=10)

---

### Post by noctrex on 2007-06-08
I have a Toshiba Tecra A8, and have the same problem (Feisty x86-64):
When i leave the system idle, after about 10-15 minutes the screen gets black, but the monitor is on, and the whole laptop is unresponsive, no keyboard no mouse no nothing. it doesn't wake up. the only thing i can do is forcefully powering off.
I've tried the suggestion from the above post with the noapic kernel option, but then the dual-core is shown as single-core and also the problem isn't solved.
Is there any other apic/acpi related option for this kind of problem?

---


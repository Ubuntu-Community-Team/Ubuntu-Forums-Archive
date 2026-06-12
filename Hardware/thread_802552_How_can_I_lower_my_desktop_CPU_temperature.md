---
title: "How can I lower my desktop CPU temperature?"
date: 2008-05-21
forum: Hardware
---

### Post by Kalinda on 2008-05-21
Hallo,

My Pentium 4 desktop CPU runs at 43-45C when idle and when I run my Windows XP VM through Virtual Box it goes up to 55C or, depending on what I'm doing with the VM, 60C (which is apparently near the max. temp for this CPU).

I've been told that my CPU should be running at 38C, but it never is. I've got plenty of fans and my heatsink is clean. I also wonder why the CPU fan doesn't adjust itself to compensate for the CPU's rising temperature... right now it's running at 2710 RPM and the CPU temp is 55C.

So why isn't my computer cooler? Could lm_sensors be malfunctioning? Should I open up my box and reapply the thermal paste to my CPU?

I'm really worried my computer is gonna overheat; yesturday it froze and I think that's why. How can I make my CPU as cool as it's supposed to be?

---

### Post by TheLions on 2008-05-21
most probably is the paste...

reapply it thinner as possible to get lower temp...

also before reapplying the paste try open your casing for a day to see if temp will fall.

---

### Post by nicedude on 2008-05-21
You should probably buy a better cpu cooler as well if you are using the one that came with your CPU and make sure you use good thermal paste, or better yet Artic Silver since its only $6 online. A upgraded CPU cooler is inexpensive as well ( Good one for home PC $15-$25 ) and can usually make a big improvement over the stock intel ones.

If you dont get a new cooler I would definitely get Artic Silver if your using  the paste that came with the CPU.

Hope that helps,

nicedude

---

### Post by solitaire on 2008-05-21
One word:

"Lapping"

Take 4 grades of Wet/Dry Sandpaper
1 very flat surface (mirror)
some water
Some Brasso soaked wire pads 
add a dollop of elbow grease

Few hours lapping to smooth the bottom of the heatsink to a mirror finish. using progresevly finer sand paper.

That should take 5c -10c off your temps with good thermal paste :D

---

### Post by Kalinda on 2008-05-27
Thanks guys! Re-applying the paste worked :) Also, my CPU heatsink was loose, which I'm sure didn't help much...

My temp is now 38 to 43C, though it still goes up a bunch when I run my VM, but hey... 48-49C isn't so bad.

I didn't use alcohol or anything proper to wipe off the thermal paste before I re-applied it, though, so I assume this is only a temporary solution till I can do it properly... like I might try that lapping thing.

---

### Post by krlhc8 on 2008-05-27
Feast your eyes on exhibit A: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)
It's a tutorial that worked for me and many others on how to undervolt your cpu.  It appears that the linux kernel makes general assumptions on what the switching voltages should be.  This tutorial details how to find the optimal voltage for your specific cpu using a handy bash script.  It's a long process (2hr) but worth it.  My laptop's Centrino Duo used to run at 40Watts at 70C; now it runs at 25Watts at 50C.

---

### Post by TheLions on 2008-05-27
> **Kalinda said:**
> Thanks guys! Re-applying the paste worked :) Also, my CPU heatsink was loose, which I'm sure didn't help much...

My temp is now 38 to 43C, though it still goes up a bunch when I run my VM, but hey... 48-49C isn't so bad.

I didn't use alcohol or anything proper to wipe off the thermal paste before I re-applied it, though, so I assume this is only a temporary solution till I can do it properly... like I might try that lapping thing.

if you re-applied the in the thin layer then it is permanent solution!!!

---


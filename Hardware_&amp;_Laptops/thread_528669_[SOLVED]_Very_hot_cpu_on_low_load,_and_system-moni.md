---
title: "[SOLVED] Very hot cpu on low load, and system-monitor question!"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by olavjunior on 2007-08-18
I have a laptopp, hp dv2130, and lately I think it's gotten real hot. I have started using the sensor-aplet to get to know what the prosessor temp is. And it can easily go up to 85 degrees celsius. Is this normal??

And another thing; I want to know what's causing the hard load on my machine, so I have the gnome-system-monitor always graphically monitoring the load, and the small window shows that some prosesses are going, but when I open the monitor, and choose to see all prosesses, there's none shoing cpu-usage! (maby just gnome-monitor with a few %) Altough the graph on my desktop shows that there is significant cpu-usage. 

So I feel that gnome-system-monitor is incomplete in some way. Is there any better alternative?

---

### Post by ajgreeny on 2007-08-18
Use the terminal and command top which shows all the processes in action and the total cpu load against all in the list.  Interestingly, when running gnome the system monitor shows much higher cpu load figures than running kde, and there is always a  peak in network activity every three seconds, and also peaks every few seconds in cpu load.  I normally use kde so it is not something I've looked into, but if I use top in terminal the peaks in the loadings don't occur, so I wonder if it is just system monitor that is causing them; if I have system monitor and top running together in gnome, it is system monitor that seems to be at the top of top, if you see what I mean.

---

### Post by olavjunior on 2007-08-18
Oh, thanx! The top command was quite something different then system-monitor! Great! But I'm still of the opinion that system-monitor ought to have shown the same as top does. I've also notised a continoius peak in the graph sometimes, but that can be so many things causing that.

I see now that sorg is using some prosess. What might that be? Because of Compiz? Maby I should look into the xorg.conf again?

---

### Post by olavjunior on 2007-08-18
Well, I tried different solutions for the xorg.conf. I removed the AIGLX and AddARGBVisuals. (Don't know why I had them. Maby Beryl needed them, compiz runs smooth without)
I still have AddARGBGLXVisuals option enabled. Does anyone think that those posts in my xorg made my comp sluggish? Sure hope so... :)

---

### Post by olavjunior on 2007-08-23
But hey, my cpu is still very hot on low load!! Inkl my harddrive. 

Can't seem to have noticed this under edgy

---

### Post by Austin_KW on 2007-08-23
Laptops accumulate dust, blocking the airflow and causing overheating, you need to clean it out regularly.

Blow air into the 'air outtakes', you should see a cloud of dust from the 'air intakes'. Do not blow into the air intakes or you will force the dust in deeper.

You might also try vacuuming the air intakes. Either way you should do this every few weeks

---

### Post by Dark Star on 2007-08-23
2nd that :D CLeaning the laptop is a good idea.. If you are afraid you can take the lappy to service center for cleaning :D

---

### Post by olavjunior on 2007-08-23
Thanx alot guys! Actually I just read this tip in another thread. Had never done that before :) And yes, it helped alot! :)

Now my temp is about 55-60 on normal /low use. That's not to bad, is it? I'm gonna try the vakuum-cleaner later on. But I porbably have to be a little bit careful with that one, it's very powerfull..

---

### Post by excogitation on 2008-03-18
I know this thread is "old", but still:

If you use compressed air or a vacuum trying to clean your laptop
without opening it up - make sure to block the fan while doing so
(use a toothpick, whatever) - if you ever want to kill a fan - just hold a vacuum to one side and let it spin.

The other thing - I don't know where you live - but cleaning the laptop once a year or every other year should really suffice.

---


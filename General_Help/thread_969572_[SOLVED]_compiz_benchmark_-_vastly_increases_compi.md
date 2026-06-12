---
title: "[SOLVED] compiz benchmark - vastly increases compiz performance when on"
date: 2008-11-03
forum: General Help
---

### Post by earthpigg on 2008-11-03
yeah. this one has me baffled. when i have the compiz benchmark plugin activated, enabled, and displaying my framerate... it goes up. drastically. very drastically. 

i noticed a drastic framerate drop when i went from 8.04 to 8.10, but now suddenly with this plugin active it goes back to 8.04 performance.... but its annoying having that thing on my screen all the time so i dont want to do that :)

this is a weird one.

i COULD just leave it on 24/7 and move it 4000 pixels over so i cant see it... but thats a half-arsed solution.

any ideas?

im using nvidia's 177 driver on a laptop 8800. 8.10 64 bit.

---

### Post by earthpigg on 2008-11-03
bump.

should i do a bug report for this?

---

### Post by mister_pink on 2008-11-03
What about if you untick disable limiter in the benchmark settings?

---

### Post by earthpigg on 2008-11-03
> **mister_pink said:**
> What about if you untick disable limiter in the benchmark settings?

it suddenly starts getting choppy again, and drops to ~20-40 fps. without doing that, it doesnt drop below 80 fps no matter how fast i rotate my desktop cube.

edit - it MAY be going the same speed as 8.04 was going, but im not sure

---

### Post by jbg7474 on 2008-11-03
Perhaps this is caused by "better" power management in Intrepid?  It may be that under normal conditions your GPU is underclocking to save power, and when it is used more heavily, it comes back up to speed.  I saw a post somewhere where a guy made a script that continuously polled the GPU for some piece of information that kept it at the higher clock rate.  Wish I could find it again for you, it might solve your problem.

---

### Post by earthpigg on 2008-11-04
ah, now it is starting to make a bit of sense. hardy is trying to be 'smart' and detected that i have a laptop, perhaps, and is thus trying to save me battery time?

when i get home, i will try disabling **all **power management stuff. if i want my computer off, i turn it off... i have no use for hibernate, etc.

---

### Post by earthpigg on 2008-11-05
turning all the power management stuff off did not work :\

---

### Post by MickJT on 2008-11-08
The solution for this is to open up ccsm, go into General Options, then click the Display tab. Untick Detect Refresh Rate, tick Sync to VBlank and set your refresh rate to 75.

---

### Post by riley99 on 2009-02-18
All of these solutions did not work for me...  I have the answer.. For the life of me I could not get my quad core beast with a good video card to get any compiz to look smooth.  

Enable the CCSM benchmark
Enable the 'Disable Limiter'
Disable the 'Screen Output'   (this stops the compiz benchmark results to show on the screen)

My framerate shot up to over 500 fps

---

### Post by mister_pink on 2009-02-18
The answer here seems obvious to me: when you uncheck disable limiter the framerate goes up. Therefore, the framerate is low because of this limiter.

Basically I think its just so it doesn't go mental rendering 500 fps when in all honesty thats pointless. Is it a problem having a low frame rate?

---

### Post by riley99 on 2009-02-18
> **mister_pink said:**
> The answer here seems obvious to me: when you uncheck disable limiter the framerate goes up. Therefore, the framerate is low because of this limiter.

Basically I think its just so it doesn't go mental rendering 500 fps when in all honesty thats pointless. Is it a problem having a low frame rate?

Hi there.. I would say it is a major problem.. The performance was jerky and unattractictive.  To the point that I thought linux was coded horibly wrong and could not make use of my hardware potential.   Now that I have discovered this feature, It looks as smooth as a brand new mac!  My opinion is totally flipped :p

---

### Post by Dieseler on 2009-02-18
Do any of you have window borders while using compiz?
I seem to lose them whenever I enable normal or extra visual effects in 8.04 Hardy. I know to do the metacity trick to get them back but then I lose the compiz.

---

### Post by Aklem on 2009-11-01
i have the same problem.. i need to know the changes!
i need to know how to fix it without that benchmark application running

---

### Post by Aklem on 2009-11-01
Bump

---

### Post by olifhar on 2009-12-08
The above didn't work for me, but what did was unticking Workarounds > "Fix screen updates in XGL with fglrx". In my case I think the problem was that although I have an ATI graphics card, I'm using the open source driver (xserver-xorg-ati) rather than the proprietary Catalyst driver, which no longer supports my card (Mobility Radeon X1600).

If this isn't exactly a fix for the rest of you, I hope it might at least be a hint. Best.

---

### Post by elicoten on 2011-01-16
Wow unticking that workaround worked a treat! Thanks so much for that :) 

I'm using ATI Radeon Express X1250

---


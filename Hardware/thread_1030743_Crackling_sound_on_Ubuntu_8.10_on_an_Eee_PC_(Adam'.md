---
title: "Crackling sound on Ubuntu 8.10 on an Eee PC (Adam's Kernel)"
date: 2009-01-04
forum: Hardware
---

### Post by henriquemaia on 2009-01-04
I have an Eee PC 1000H and it was running like (almost) a dream until today. What happened was that I was hearing some music and, all the sudden, I start hearing this loud crackling sound out of nowhere. I didn't pay much attention to it, I restarted the computer thinking that this would solve the problem. But no, now it's always like this. Whenever an app uses sound, I start hearing the crackling noise and it's only when sound is not in use that I have no crackling noise. Another thing that seems to be related is that now people hear me through the internal mic when using skype (it was not working before).

I've tried the lean kernel and the eee pc kernel and the result is always the same. Crackling noise all the time sound is in use.

Any ideas on how to solve this?
(I've been googling a lot about this)


note: the sound is continuous during any sound. It only ceases when alsa releases the sink (I guess). Also, the crackling sound also stops if I turn off alsa by hand ex: sudo /etc/init.d/alsa-utils stop.

---

### Post by deathsshadow77 on 2009-01-04
i have the same issue, but only when I turn my sound all the way down. I have a 900ha

---

### Post by henriquemaia on 2009-01-04
> **deathsshadow77 said:**
> i have the same issue, but only when I turn my sound all the way down. I have a 900ha

hm..... In the eee-pc kernel, if I put the microphone and mic boost all the way up, the crackling sound almost disappears.

My worry is if this is some hardware problem. The computer is new, I bought it on the 17th of December, but one never knows.

---

### Post by henriquemaia on 2009-01-05
Worst solution ever... (because of its randomness)

Shut down your Eee and disconnect it from the main plug. Leave it off for some time (I don't even know if you have to leave off more or less time, maybe just turning it off and disconnecting it from the plug will do the trick).

Turn it back on. Sound problem solved. 

The wonder of this solution is that I feel that this is as scientific as kicking an appliance to get it back to work. But if it works for you, at least you can get to business as usual. 

Good luck.

---

### Post by Neo4 on 2009-03-31
> **deathsshadow77 said:**
> i have the same issue, but only when I turn my sound all the way down. I have a 900ha

same here on a 1000h and ubuntu 8.10 after installing intel 2.5.1 drivers...

---

### Post by Fenris_rising on 2009-03-31
Check the easy peasy wiki. There was a fix for this. I have a 904HD which initially had the crackling issue until I did the fix.

regards

Fenris

---

### Post by henriquemaia on 2009-03-31
> **Fenris_rising said:**
> Check the easy peasy wiki. There was a fix for this. I have a 904HD which initially had the crackling issue until I did the fix.

regards

Fenris

Do you have the specific link to this wiki page? 

Thanks

---

### Post by Neo4 on 2009-04-04
> **henriquemaia said:**
> Do you have the specific link to this wiki page? 

Thanks

I ask the same I couldn't find it!

---

### Post by henriquemaia on 2009-04-04
> **Neo4 said:**
> I ask the same I couldn't find it!

I try googling around for it, but the said Wiki was not online at the time. Too bad.

---

### Post by Neo4 on 2009-04-04
easy peasy site is online again, so the wiki should be too

---

### Post by henriquemaia on 2009-04-04
I've searched again and only found this [page]("http://www.ubuntu-eee.com/wiki/index.php5?title=Known_bugs_and_fixes_for_Easy_Peasy_1.0#Audio_levels_too_low.2C_and.2For_muting_results_in_crackling_noises"). Not particularly helpful in my case (the configuration proposed doesn't apply to my settings).

---

### Post by Rob Loach on 2009-04-14
I've noticed that this only happens when the audio volume is set to mute. Running Ubuntu Faunty. EeePC 1000H.

---

### Post by Neo4 on 2009-04-14
> **Rob Loach said:**
> I've noticed that this only happens when the audio volume is set to mute. Running Ubuntu Faunty. EeePC 1000H.

yes only on mute

---

### Post by calebegg on 2009-08-11
I found [this page]("http://forums.geteasypeasy.com/viewtopic.php?f=12&t=543") that has a purported fix, but it didn't work for me.

:-(

---


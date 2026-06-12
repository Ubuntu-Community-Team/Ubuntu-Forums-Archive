---
title: "Laptop w/ built in subwoofer"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by mcwizard on 2007-03-25
Not sure if this post should go in multimedia instead but...

I'm running Edgy (Ubuntu Ultimate 1.2 w/ all recent updates) on a ECS G900 laptop, most everything works great, multimedia keys were a bit of a pain but they work most of the time now.  

My last remaining problem that bothers me is the sound.  The laptop has 4.1 built in sound (2 mid, 2 high, and a sub) but the sound level is not nearly what it is in windows. I tried changing the number of channels from 2-4-6 in alsamixer and I can hear the sub pop as it re inits the sound system (makes the same pop noise on boot also), but when playing music it has no effect.

The sound card reported through alsamixer is a SiS7012 and the chip is a C-Media Electronics CMI9761.  

Any ideas on what to try or where to search, my searches have turned up empty.

---

### Post by s0cket on 2007-03-26
It depends completely on the alsa driver your soundcard is using.  Sometimes the bass channel is call "LFE" or "Master Mono".  Check to see if you have an option to add that to your mixer.

---

### Post by mcwizard on 2007-03-27
I've adjusted everything I can in alsamixer, the LFE channel has no effect, sub is still doesn't make a sound.  Is there a special driver I could use for SiS7012 or C-Media, or am I SOL till this becomes a more common problem.

---


---
title: "Mute Koala"
date: 2010-04-04
forum: Hardware
---

### Post by Majik_420 on 2010-04-04
I just upgraded to Karmic and now my sound is gone. I have been doing a little reading so far, and The only thing I've tried is resetting alsa with 

sudo /etc/init.d/alsa-utils reset

and i get

* Resetting ALSA...
Amixer: Invalid Command!

I'm a little tired and I Haven't played with Kubuntu for a few months so sorry if I haven't searched enough, I'll continue searching, just figured I'd throw a line out and see what I catch. Thanks

*edit: Headphones do work.

* Reading Though Comprehensive Sound Problem Solutions Guide v0.5e at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

First two steps success, 3rd step I don't understand where I'm supposed to search for my chipset... and 4th step gets this

FATAL: Module snd- not found.

:KS Guess I'm gonna try :KS Getting the ALSA drivers from a *fresh* kernel:KS now...

* Ok, Criticize me all you want, but that solved my problem. Sorry for a useless post, unless this will help anyone else. Guess I just needed a place to keep track of my progress.

---


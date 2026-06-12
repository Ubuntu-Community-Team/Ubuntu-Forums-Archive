---
title: "Getting &quot;mildly&quot; annoyed! First gfx, now sound!"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by oled on 2006-11-26
I just need to get this out before I explode and thrash my computer.

It all started when I upgraded my Htpc to edgy. (I wanted all the new stuff especialy mythtv 0.20). First problem some applications failed with floating point overflow, nothing else. Found out that it was the onboard Ati gfx of my motherboard. So what do I do? I get buy a cheap nvidia geforce 6200tc with svhs out, and get a much better tvout than the onboard Ati had, I can now run those applications that faild(including mythtv) and everything is good until I sit down to watch a movie! 10-15 min and the pc freezes. After several reinstalls and many hours of forums searches and error searching. The conclusion is that ati chipset and nvidia gfx is a no go on linux. I even bought anohter nvidia gfx (6600gt) because somebody ment that is was the turbo cache part of the 6200 that was causing my problems. So the solution is a new motherboard without Ati chipset. So after install the new motherboard I can run mythtv and watch movies without the pc freezing, but theres no sound. I only want spdif, but analog dosn't work either. The new motherboard has a via vt82xx (intel-hda) sound chip. After compiling alsa and reinstalling a couple of times I give up. In another pc I have a Soundblaster Audigy 2, so why not give it a try. Out with it, into the htpc reinstall (alsa was totally messed up by the old soundcard). After having messed around with alsamixer and alot of .asoundrc files I'm about to give up. Once I had sound using aplay and a lot of parameters, but no sound in other apps. Now theres nothing, not even with the same config and same parameters. 

Why does it have to be so hard? 

So please can anybody tell me exactly how alsamixer has to be configured and what my .asoundrc file should look like? in order to get spdif sound on a Audigy 2 sound card? 

I would really really really hate to be forced to digging out the old windows cds. 

/Oled

---


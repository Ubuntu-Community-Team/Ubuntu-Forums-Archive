---
title: "wacom intuos art ... working but not configurable 16.04.2 LTS"
date: 2017-10-05
forum: Hardware
---

### Post by geoffrussell on 2017-10-05
System settings tells me "No tablet detected" ... but it works and xsetwacom --list devices gives:

Wacom Intuos PT S 2 Pen stylus  	id: 10	type: STYLUS    
Wacom Intuos PT S 2 Finger touch	id: 11	type: TOUCH     
Wacom Intuos PT S 2 Pad pad     	id: 12	type: PAD  

The device is recognised and works in Inkscape. 

But I don't know how to configure it without System Settings recognising it.

Any ideas?

Cheers,
Geoff Russell

---

### Post by mörgæs on 2017-10-06
The Wacom support is evolving fast, getting better and better for each Buntu release. 

Is there any difference if you try a live boot of 17.10 (beta)?

---

### Post by geoffrussell on 2017-10-07
Thanks ... I'll try a live boot of 17.10.

---

### Post by geoffrussell on 2017-10-07
> **mörgæs said:**
> The Wacom support is evolving fast, getting better and better for each Buntu release. 

Is there any difference if you try a live boot of 17.10 (beta)?

Just tried 17.10 beta and the configuration is working. The tablet is recognised and configuration appears ... with a few funny things ... like the buttons on the tablet not corresponding to those on the button config screen. 

So I guess I should hope that the code eventually shows up in 16 LTS.  I can wait ... I'm still learning about this device and not ready to explore all the details yet anyway.

Many thanks.

---

### Post by mörgæs on 2017-10-07
16.04 was finished 'as is' one and a half years ago. Though some hardware enablement packages are backported to 16.04 the general rule is that 16.04 is stable, that is unchanged. If everything from 17.10 were to be backported then 16.04 would essentially be 17.10, making the latter obsolete. 

I suggest one of two options: 
A) Try 17.04 in a live boot. If it works for your Wacon then do a fresh install of this one, keeping it until January. 
B) If 17.04 does not support the Wacom fully then keep 16.04 and install 17.10 in a dual boot. This way 16.04 can serve as a fallback. 

Under all circumstances you should get away from running the obsolete 16.04 as your primary system. It's only relevant for dated or semi-dated hardware.

---

### Post by geoffrussell on 2017-10-13
> **mörgæs said:**
> 16.04 was finished 'as is' one and a half years ago. Though some hardware enablement packages are backported to 16.04 the general rule is that 16.04 is stable, that is unchanged. If everything from 17.10 were to be backported then 16.04 would essentially be 17.10, making the latter obsolete. 

I suggest one of two options: 
A) Try 17.04 in a live boot. If it works for your Wacon then do a fresh install of this one, keeping it until January. 
B) If 17.04 does not support the Wacom fully then keep 16.04 and install 17.10 in a dual boot. This way 16.04 can serve as a fallback. 

Under all circumstances you should get away from running the obsolete 16.04 as your primary system. It's only relevant for dated or semi-dated hardware.

Thanks for your assistance but we come from different worlds. I hate being told that my 3 year old phone is obsolete and I'm not keen on being told that by 18 month old OS is obsolete. The IT industry has to 
rethink how it evolves software. Nuclear power reactors are being designed with 80 year lifespans ... that's what I call real engineering! We need to think of software the same way ... which isn't easy, but 
its time we stopped putting users though upgrade hell as though it were some kind of blessing we were bestowing on them.

LTS has meant "Long Term Support" for as long as I can remember, meaning important bug fixes are back ported. I can assure you that there is a constant string of changes to my 16.04.3 LTS.  It is stable, but
not at all unchanging.   But I can understand that not all things 
are considered important enough to backport and while I might regard not recognising this device as a bug, someone else may regard actually recognising the existence of the tablet as a new feature.  The fact that it works
fine under Gimp indicates that a bug is the most likely problem rather than some WACOM change which has busted compatibility.

LTS versions are an important reason I use Ubuntu. I need my machine stable 24x7 ... it's a work horse ... and have no plans to upgrade for at least 2 years ... and maybe much longer.

---

### Post by mörgæs on 2017-10-13
That's why I suggested a dual boot.

---


---
title: "Dell Mini 1012"
date: 2010-07-09
forum: Hardware
---

### Post by h1ll39 on 2010-07-09
I just got the Dell Mini 1012. Luckily WiFi works out of the box and everything with Ubuntu Netbook Remix 10.04.

Only complaint is I can't find a driver for my video card. Anyone know anything I'm missing?

---

### Post by kerry_s on 2010-07-09
it's already using it, intel is supported out of the box.

---

### Post by h1ll39 on 2010-07-09
It wont' let me enable compiz effects though?

---

### Post by AltomineUK on 2010-07-09
Do you have any idea what your Graphics card is? If it is Intel, then it is supported by Ubuntu as Intel uses open source drivers.
 Try enabling the Visual Effects, by right-clicking the desktop and using the "Change Background" option.

---

### Post by kerry_s on 2010-07-09
might be because compiz & netbook don't get along.

i know it can be enabled with a few work a rounds, but you'll get so many other problems, it's really not worth it.

---

### Post by AltomineUK on 2010-07-09
Um they do get along...... mine does :D

---

### Post by AltomineUK on 2010-07-09
However, my netbooks running Ubuntu 10.04 Desktop edition. Even then, I have seen people, on youtube, run compiz on the netbook edition quite well.

---

### Post by kerry_s on 2010-07-09
> **AltomineUK said:**
> However, my netbooks running Ubuntu 10.04 Desktop edition. Even then, I have seen people, on youtube, run compiz on the netbook edition quite well.

and what part of:
> i know it can be enabled with a few work a rounds, but you'll get so many other problems, it's really not worth it.

did you not understand?

a couple of minutes in a video don't tell you crap, it don't tell what they had to go through to make it work or about when the computer locks because of it.

> Um they do get along...... mine does


i know your running the desktop edition, thats why you don't have a clue. i been there, done that.

the pics to show i can turn it on, but i don't keep it on cause i already know it will lock up.

---

### Post by kerry_s on 2010-07-09
it may also be the type of intel vid.

i think mines a bit old, but common?

---

### Post by AltomineUK on 2010-07-09
Calm down.. I too have been through the netbook remix edition which is why I chose the desktop edition .If u want evidence, you can check my posts, where I once highlight one of many tiny niggles that I came across during my time with the Netbook remix. Perhaps it might work out for you, but that doesn't necessarily mean it has to work out for me.

As for the youtube, I was trying to show some possibities and you might find some useful help there as well. Because as you can see, we have been going nowhere here. Plus it's more interesting than some screenshots.....

Besides we should be helping the guy who has the problem instead of bickering about amongst ourselves. Forums nowadays have far too many comments aimed at insulting each other's intellect rather than stimulating a creative, positive "fun" environment.

And Finally @ h1II39: From my experience and as kerry_s so gracefully explained, the netbook remix edition is able to produce compiz effects while running the risk of locking-up. Dell Mini 1012 should have the hardware requirements covered for Compiz effects to take place, but the software side may need some pushing.  

BUT it would help us all if you can find out about your Graphics Accelerator. Simply type the following into a terminal:

```
lspci -v | less
```This will list your graphics card and the memory controller amongst many other things.

---

### Post by kerry_s on 2010-07-09
according to the dell specs it's:
> Integrated Intel®  Graphics Media Accelerator 3150

i'm pretty sure compiz & netbook can work, but intel & compiz have been iffy as long as i can remember.

to the op, if you want to try forcing it to see:
press-> **alt+f2**
type-> **compiz --replace**

that should skip the checks & activate immediately.

@ AltomineUK, peace brother. ;)

it's 3am here, time to hit the sack.

---

### Post by AltomineUK on 2010-07-09
@kerry_s: Cheers mate. Take care yourself. :D

 Hmmm.... I checked on the Dell website here and the graphics seemed to be powered by the NM10 Express chipset. So I'm not exactly sure which chipset is being used in the Dell that's having the problem.

---

### Post by h1ll39 on 2010-07-09
I just wont' mess with it. Maybe later. Thanks though

---


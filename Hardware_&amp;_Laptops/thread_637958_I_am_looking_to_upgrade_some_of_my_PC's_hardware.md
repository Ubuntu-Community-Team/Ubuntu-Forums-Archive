---
title: "I am looking to upgrade some of my PC's hardware"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by krelverehan on 2007-12-11
Hello everyone,

Right now I am currently running Ubuntu (Gutsy) fine on a 4 year old PC that was pretty spiffy at the time. Now, I am happy with my monitor (I bought a new one recently), my sound card and my hard-drives, but I am looking to upgrade my CPU and my Video card and to get some new RAM. 

I am curious on finding the right hardware that is going to give me the least amount of problems on Ubuntu. I mostly use my computer for watching movies, listening to music and surfing the web so I am also not looking to spend millions but at the same time I wouldn't mind having some fancy desktop effects up and running (beryl nor compiz won't run with the machine I am using) and maybe one day having two active monitors.
 
Here are some specs of my current PC:
Memory: 1011MB
CPU:  AMD Athlon(tm) XP 1800+ (1550MHz)
Video:  Radeon RV100 QY [Radeon 7000/VE]
Sound: SB Live! EMU10k1
Monitor: Dell SE198WFP 19 inch Silver Flat Panel Display
Hard-drives: Master 149gb, 37gb slave, 149gb external

Thanks!

---

### Post by jexxie on 2007-12-11
Hi there,

I'm not sure how much you're looking to spend, are you looking for a dual-core processor?  DDR2 ram?

An AMD64 4000 is about $75, Asus M2NPV-VM motherboard with onboard video is about $95, and DDR2 ram is dirt cheap, you can get about 2 x 1024MB sticks of ram for $30-40 after mailin rebate.

Probably about $240ish, after taxes and the like.

Cheers!

---

### Post by krelverehan on 2007-12-11
Will I need a new motherboard (is that a stupid question)?

And I think I will opt for a single core processor. And DDR2 sounds pretty standard for RAM.

And if I do get a new motherboard, are the onboard video cards good enough?

Thanks!

---

### Post by Yellow Pasque on 2007-12-11
I agree with the above, except I'd recommend a GeForce 7050PV-based board as opposed to the older 61x0 series.

I've read great reviews of the BIOSTAR TForce TF7050-M2 at silentpcreview.com

---

### Post by Yellow Pasque on 2007-12-11
> **krelverehan said:**
> Will I need a new motherboard (is that a stupid question)?
And I think I will opt for a single core processor. And DDR2 sounds pretty standard for RAM.
And if I do get a new motherboard, are the onboard video cards good enough?

Yes, you'll probably need another mobo. What do you have now? Your upgrade path sounds pretty limited, and with new components as cheap as they are, it doesn't make sense to spend money on an aging platform. For example, the DDR mem that your board probably uses is more expensive than DDR2.
It's pretty hard to pass up dual-core when an X2-4000 Brisbane runs ~$60
You didn't mention any demanding gaming in your usage, so yes, onboard video will work nicely.

---

### Post by krelverehan on 2007-12-11
I don't really know what kind of Motherboard I have, the computer was a hand-me-down from an old roommate of mine.

And the results of bashing in lshw shows this as my 'mobo'

  *-core
       description: Motherboard
       physical id: 0

So not too many ideas on what it is short of unscrewing the tower and looking.

---

### Post by Yellow Pasque on 2007-12-12
Try:
```
sudo dmidecode | more
```
to ID the mobo (thanks to Sef for that tip)

---

### Post by krelverehan on 2007-12-12
If that is the case, I have a GA-7VAX motherboard. I guess, regardless of what kind it is, the mobo is still over 4 years old and is in need of replacement.

So does all of this sound good?
CPU:X2-4000 Brisbane
Mobo:BIOSTAR TForce TF7050-M2 (using its build in video card)
and 2 sticks of 1024 DDR2 RAM.

---

### Post by CREEPING DEATH on 2007-12-12
Just build a new one.  It really isn't worth it to upgrade, you have an obsolete Socket A mobo and dated, slow components.  I recently rebuilt an old eMachines for about $165 including a new mobo, Celeron D, Antec PS.  Adding 512 MB RAM would still keep the total about $200, and you can add a large SATA HDD for less than another $100.

CD

---


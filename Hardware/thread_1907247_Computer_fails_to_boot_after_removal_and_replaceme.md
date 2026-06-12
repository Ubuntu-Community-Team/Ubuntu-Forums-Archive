---
title: "Computer fails to boot after removal and replacement of RAM"
date: 2012-01-11
forum: Hardware
---

### Post by geekman2 on 2012-01-11
I know this isn't technically an ubuntu question but I need some help.I got some new RAM and tried to install it in my custom PC, it didn't work and so I put the old RAM back in. It won't boot anymore

---

### Post by carl4926 on 2012-01-11
Check it's in correctly
Make sure it's fully slotted down and the clips are retaining it

Can we assume you did take anti-static precautions in the process ?

---

### Post by geekman2 on 2012-01-11
I already checked all of the above multiple times thanks for the quick reply

---

### Post by carl4926 on 2012-01-11
Can we assume the new RAM was the wrong type or something?

You are only putting back what was there originally? In the same slot/s
It's easy stuff to damage

---

### Post by jmate24 on 2012-01-11
or you may have accidentally fried everything or the motherboard.
also DDR, DDR2, & DDR3 are not interchangeable. There should be a sticker that has the letters DDR either just the letters DDR or followed by a number 2 or 3.

DDR has been around since the Pentium 3 and Pentium 4 chip era.
DDR2 showed up when Intel started to introduce HyperThreading and dual-core processors. AMD started their K7 and K8(64-bit) and added  more processor features.  and stuck around for dual-core and tri-core processors.
DDR3 is For the Newer generation Processors that have more than 3 cores. Currently AMD is either working on or has a 12-core processor named "Magny Cours". That may take the new DDR5 that is currently being used in their ATI video cards (p.s. I own one it is a Radeon Saphire 5670.
DDR5 is not in production for PCs yet. but i have some pages below that might help.

[http://en.wikipedia.org/wiki/DIMM]("http://en.wikipedia.org/wiki/DIMM")
[http://en.wikipedia.org/wiki/Advanced_Micro_Devices]("http://en.wikipedia.org/wiki/Advanced_Micro_Devices")
[http://en.wikipedia.org/wiki/Intel]("http://en.wikipedia.org/wiki/Intel")
[http://www.youtube.com/watch?v=wWqiv8ag0s4]("http://www.youtube.com/watch?v=wWqiv8ag0s4")

I'm Glad to be of help.

---

### Post by prshah on 2012-01-11
> **geekman2 said:**
> I know this isn't technically an ubuntu question but I need some help.I got some new RAM and tried to install it in my custom PC, it didn't work and so I put the old RAM back in. It won't boot anymore

Does your computer beep when you try to start it? That is a classic way to diagnose a "no display" situation.

If you get continuous beeps, the memory is either damaged (unlikely) or not seated properly (very likely).

If you get a pattern of beeps (usually short, short, long, then a pause, then repeated) then it is likely the problem is with the display subsystem - Eg, loose graphics card if you have one.

Failing all else, try clearing the CMOS memory and starting: You will need to study the manual for your motherboard for this procedure. Essentially, switch off your machine (unplug for safety), remove the CMOS battery (Usually a CR2032 "coin" battery), and look for CMOS reset jumper. After about 30 seconds, reverse everything and try to start the computer.

If you are not too keen to try the above, then I would advise applying to technical help or a knowledgeable geek.

---

### Post by geekman2 on 2012-01-12
I am replacing the exact same RAM that has been working for almost a year now and have reseated it multiple times in an attempt to get it to work, also for some reason I get no beeps only LED's on the motherboard

---

### Post by geekman2 on 2012-01-12
I also removed and replaced the CMOS battery

---

### Post by carl4926 on 2012-01-13
> **geekman2 said:**
> I am replacing the exact same RAM that has been working for almost a year now and have reseated it multiple times in an attempt to get it to work, also for some reason I get no beeps only LED's on the motherboard

It sounds terminal

---

### Post by mastablasta on 2012-01-13
yup. no beeps is bad. very very bad.

---


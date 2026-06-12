---
title: "Grr, computer turning itself off randomly"
date: 2009-10-10
forum: Hardware
---

### Post by Aped on 2009-10-10
This has been happening to me on and off for a while, and recently started happening to a friend of mine as well. I'll list my stats (don't know hers off the top of my head) and throw out what I believe to be the most likely culprits. I can't afford to spend on something that isn't a pretty sure-fire solution though, as I am dirt poor.

This is likely a hardware issue, it happens to me in all environments. It seems to be triggered by heavy load or by certain types of load on the computer; specifically video games and video. 

My spex: 
ASUS P5K-E w/Wifi mobo
2.66 Core 2 Duo
4 gigs of RAM
geForce 8800gts
120gig WD
360gig Seagate

The issue: 
It just shuts off sometimes. If it does, it won't turn back on unless I wait a few minutes. There doesn't seem to be a TON of rhyme or reason to this, except that it does seem more frequent when under heavier load, as mentioned. 

Most likely culprits imo:
Two things I've noticed similar between my setup and my friend's: the geForce 8800gts and the fact that at least one of the PSU's rails (5v for mine, +12 for hers) is more than 5% off consistently. For me, it's the 5v running at about 5.52, which is more than 10% off if you don't care to do any math. Her 12v is running at 11.3, which is JUST past the 5% threshold. 

Other than that, I can't think of anything really. My PCU was heating up so I threw an extra fan in there, and eventually started shutting off sensors in the BIOS in order to isolate the issue. The RAM is quite new, so it's probably not bad. 

Things I've tried or am about to try:
Turned off almost all sensors, disconnected nonessential drives. If push comes to shove I'll disconnect ram sticks 2 at a time, flash my BIOS on the very offhand chance that an old version might cause some problems with hardware, and then... I don't know, start borrowing parts till it works? 

Is there a way to check what happened to cause a bad shutdown, maybe give me an error code I could google? BIOS post message maybe? Is this a common issue? Anyone have experience with this sort of thing?

---

### Post by wilee-nilee on 2009-10-10
If it is a hardware issue then you may need to have it looked at by a professional, I doubt you will get any answers on the forums that is going to fix the problems. If you continue to have this shutdown problem every time it does this it is probably damaging whatever HD's that are running, so you might want to consider, the cost of frying a part that will cost more then having it looked at.

---

### Post by Aped on 2009-10-11
I was hoping that someone might have had a similar issue, or that someone could tell me if +/- >5% voltage could cause this sort of thing.

Yeah these HDDs are taking it pretty rough, I'll replace the one with the OS on it eventually though, it's a piece of crap. 

Anyway, I guess I'll hold out in hopes of some sort of response- the level of guru on these forums never ceases to impress me.

---

### Post by tqft on 2009-10-11
> **Aped said:**
> I was hoping that someone might have had a similar issue, or that someone could tell me if +/- >5% voltage could cause this sort of thing.

Yeah these HDDs are taking it pretty rough, I'll replace the one with the OS on it eventually though, it's a piece of crap. 

Anyway, I guess I'll hold out in hopes of some sort of response- the level of guru on these forums never ceases to impress me.

When you get it to boot, have a look at the system logs.

System Administration, Log File Viewer
If there no log files showing File Open from the Log File Viewer menu.

It sounds like your computer is over heating - something may show in the logs.

The following isn't meant to be insulting as it seems like you have a clue but others reading on similar problems might not have thought of these:

You put another fan in - but is the box in a tight corner without airflow?

Did you clear the air holes of dust so the air can flow?

---

### Post by IcarusR on 2009-10-12
Have you cleaned the cpu heat sink fins. Get hold of an air duster aerosol & blow it out. 
I have a server that runs 24/7 & every 6 months or so I clean the heat sink. Othwise it eventually becomes unstable.

---

### Post by pricetech on 2009-10-12
Sounds heat related to me also.  A "can of air" would be helpful to remove embedded dust and such.  A soft paint brush with china bristles can be used to knock loose anything the air doesn't remove on its own.

From your specs it looks like you're giving your power supply a lot of work to do.  Consider upgrading that as a possible solution.

I hope this isn't the case but;  Heat may have already damaged the processor, though I usually see that manifested with lockups, not shutdowns.

---

### Post by ulibumpa on 2009-10-12
I had similar issues with my old laptop but I just cleaned it out. The amount of dust would have been impossible to "blow out"! Five years of dust=thick rug and absolutely no air flow. It was easy to to open up and get it out though and now it works like a charm!

---

### Post by PrePenguin on 2009-10-12
This is a prime example of power supply overheating as one person said clean the cooling vent and the power supply or if that dont help this is a typical symptom of a bad power supply..

---

### Post by viper250 on 2009-10-12
I agree this is a heat issue of a power supply.
Its easier to replace the power supply than it is to try to fix it I would recommend no smaller than a 350 to 450 watt power supply.
if your ide cables are flat ribbon type harness together with a velcro strap do not use a zip tie as they can break the fine wires in the cable.
 try to place the cables so they wont block air flow around cpu or ram:P(30 years as computer tech)

---

### Post by cascade9 on 2009-10-13
That sure sounds like a heat and/or power supply issue. Like everyone else, try giving it a clean out. Cans of air work nicely, but don't forget the power of the cotton bud! (q-tip?) 

Also, once you have the case of to try to clean it out, you can try pointing a running desktop fan into the computer case. The extra airflow should help a lot if your having overheating issues. 

> **Aped said:**
> 
Two things I've noticed similar between my setup and my friend's: the geForce 8800gts and the fact that at least one of the PSU's rails (5v for mine, +12 for hers) is more than 5% off consistently. For me, it's the 5v running at about 5.52, which is more than 10% off if you don't care to do any math. Her 12v is running at 11.3, which is JUST past the 5% threshold. 

Other than that, I can't think of anything really. My PCU was heating up so I threw an extra fan in there, and eventually started shutting off sensors in the BIOS in order to isolate the issue. The RAM is quite new, so it's probably not bad. 

Things I've tried or am about to try:
Turned off almost all sensors, disconnected nonessential drives. If push comes to shove I'll disconnect ram sticks 2 at a time, flash my BIOS on the very offhand chance that an old version might cause some problems with hardware, and then... I don't know, start borrowing parts till it works? 

Is there a way to check what happened to cause a bad shutdown, maybe give me an error code I could google? BIOS post message maybe? Is this a common issue? Anyone have experience with this sort of thing?

I assume that your voltages are taken from BIOS? If so, I would be getting a new power supply. The voltage rails _should_ be within 10%. I perfer with 5%. Anything over 10%, and its junk. I have seen computers do exactly what your experiencing from bad power supplies. The only times I have seen serious 'out of voltage range' issues its been either a very old, very very cheap, or underpowered power supply. 

Depending on your motherboard, you may or may not get an 'overheating' BIOS alarm. I guess you are not, so maybe its just a power supply issue. If it was your RAM you should get a bad RAM BIOS beep, so I really doubt its that as well.

---

### Post by Aped on 2009-10-14
Hey thanks everyone for the input. I threw a big box fan next to the computer and it really seems to be doing the trick, which means I'll probably just have to clean out the heatsink fans, as people were mentioning. 

My current PSU is a corsair 450W, I could upgrade to a 500W (or higher) unit but this seems like it should have plenty of power. Also it's not a no-name brand from Quangdongxhing, China or something. 

I'll clean out the computer and let y'all know how it goes!

Thanks again for the great advice.

---

### Post by PayPaul on 2011-09-18
It definitely sounds like a Power Supply issue if it will just shuts off like that. I was looking in here for some new info on the System log viewer but this thread did give me some further indicators that my problem is a hard drive issue. Yes, and I need to open my machine to dust it off too. 

You seem to have also upgraded everything but the HD and the Power Supply. The size of the HD (120gb) seems to indicate it's an old one if I'm not mistaken. I would have actually thought with those upgrades to RAM and the addition of a fan a dusting would be in order as well. When I do open my machine to do an upgrade that's usually SOP for me to do an overall dusting out.

---

### Post by Rubi1200 on 2011-09-18
Thread closed.

Reason: Necromancy

---


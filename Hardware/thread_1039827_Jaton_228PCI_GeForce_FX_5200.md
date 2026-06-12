---
title: "Jaton 228PCI GeForce FX 5200"
date: 2009-01-14
forum: Hardware
---

### Post by High_Speed on 2009-01-14
Hi all, new Ubuntu addict, here, first time poster.

Over the course of the last week since I decided to try the Linux waters again (after about 8 years), I first installed Ubuntu on a P3 600mhz with 256mb of RAM only to find it too sluggish.  Then Xubuntu, only to return to Ubuntu on a P3 1ghz with 512mb of RAM.  Now it's running much smoother...except the old 32mb graphics card I have is sluggish.

SO...today I ordered one of these:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814139143](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139143)

Afterwards, I read further on these forums only to find some people having some serious problems with the GeForce FX 5200 chipsets.  So my question is...will I even be able to use this card, or should I return it upon arrival and look elsewhere.

Something else that's puzzling me is that the onboard vga in this old Dell I had laying around, I can't seem to turn off.  When I run, for example, compiz-check, it shows that I have TWO video adaptors running, even though I only want to use the PCI.

My hardware is as follows:
Dell Optiplex GX150 desktop
P3 1ghz
512mb of RAM

Thanks for any advice.

---

### Post by igknighted on 2009-01-15
That card got end-of-lifed by nvidia, and is no longer supported by current drivers.

If you are using older hardware, ATI is probably a safer bet, as there is a community-supported 3d driver that works well enough (and wont drop support for your card), whereas nvidia has no community driver and drops chipsets fairly frequently.  Intel's integrated graphics also are well supported by open source drivers.

If you really want to go nvidia, I'd go for something like this that is many years newer and will be supported much, much longer: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042)

---

### Post by High_Speed on 2009-01-15
I thought I had read that a lot of people had been having problems with ATI cards under Intrepid?  Maybe that's all fixed by now?

If you think ATI would be a better bet for me, could you suggest something in the $50 (or even less) range?  Won't be doing any gaming, just want a comfortable computing linux box that looks halfway decent (ie won't freak out on 3d screensavers or when watching a video in full screen).  I'm thinking down the road, might build a better, more modern, rig anyway.  This is just a little cheap project with stuff I had laying around.

---

### Post by igknighted on 2009-01-15
> **High_Speed said:**
> I thought I had read that a lot of people had been having problems with ATI cards under Intrepid?  Maybe that's all fixed by now?

If you think ATI would be a better bet for me, could you suggest something in the $50 (or even less) range?  Won't be doing any gaming, just want a comfortable computing linux box that looks halfway decent (ie won't freak out on 3d screensavers or when watching a video in full screen).  I'm thinking down the road, might build a better, more modern, rig anyway.  This is just a little cheap project with stuff I had laying around.

If you are running ati's current products they can be a PITA at times.  But for older products like the ones you would be looking at, ati is better supported.  That 8400 I linked you to might be your best bet though, that looks like a hell of a deal.

---

### Post by High_Speed on 2009-01-15
> **igknighted said:**
> If you are running ati's current products they can be a PITA at times.  But for older products like the ones you would be looking at, ati is better supported.  That 8400 I linked you to might be your best bet though, that looks like a hell of a deal.

Thanks for the info.  Would that 8400 install without issues and give me 3d funcionality with Compiz and the "desktop effects?"

---

### Post by nick09 on 2009-01-15
You can get this one, but its just a tad over your budget:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814131082](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131082)

It might have flickering in the videos with compiz but enter gstreamer-properties in a terminal to set the output video(or Applications--> Accessories and select it there, if its there). I'd also try using the ATI drivers from the Hardware Drivers menu. I have a HD 3450 installed in my system and it works great on my 5+ old Compaq Presario SR1226NX.

---

### Post by High_Speed on 2009-01-15
> **nick09 said:**
> You can get this one, but its just a tad over your budget:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814131082](http://www.newegg.com/Product/Product.aspx?Item=N82E16814131082)

It might have flickering in the videos with compiz but enter gstreamer-properties in a terminal to set the output video(or Applications--> Accessories and select it there, if its there). I'd also try using the ATI drivers from the Hardware Drivers menu. I have a HD 3450 installed in my system and it works great on my 5+ old Compaq Presario SR1226NX.



Well in a nutshell, what do I need in order to be able to run comfortably with compiz and effects?  No interest in gaming...

---

### Post by nick09 on 2009-01-15
If so, the graphics card should do what you want just fine then.

---

### Post by High_Speed on 2009-01-15
> **nick09 said:**
> If so, the graphics card should do what you want just fine then.

I'm sorry, which graphics card are you referring to?

---

### Post by nick09 on 2009-01-15
I was referring to the one I posted. I should of noted which graphics card anyways.

---


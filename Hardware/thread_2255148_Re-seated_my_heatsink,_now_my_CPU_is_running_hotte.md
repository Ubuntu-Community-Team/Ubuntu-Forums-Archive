---
title: "Re-seated my heatsink, now my CPU is running hotter."
date: 2014-12-02
forum: Hardware
---

### Post by SagaciousKJB on 2014-12-02
I've had this computer for about 5 years or so.  It's a AMD Phenom 9950BE and a CoolerMaster HyperCool212 heatsink--it's massive and has two 120 mm fans.  So I use to have no problem keeping it cool, and in the winter when my ambient temps are between 65-70 F I usually saw it idlin'g in the 22C range.  Last night I noticed it in the 32C range and realized I probably needed to maintenance it--it was caked with dust.

Problem is I didn't really have that much thermal paste left.  I actually had to use a needle to drip into the Artic Silver syringe thingy and get enough out to smear a smalllll little layer on the CPU and the heatsink base.  A lot less than I had used before, but considering that I used so much it practically welded the CPU to the heatsink, I figured a little less would be fine.

But now it's still idling at 29C for the same ambient temperatures.  The only difference I can tell is that one of my case fans on top for exhaust burn out, but I still have a 120mm intake fan blowing in and the dual 120mm fans on the CPU so I didn't really think that exhaust fan could account for a 7 degree difference.

Should I bother reseating my heatsink again or focus on replacing the exhaust fans?

Edit

I'm not really sure if this is the right forum for this since it's not really Ubuntu related.

---

### Post by QIII on 2014-12-02
Hello!

Smearing is not a good idea.  It introduces tiny air bubbles, which hinders the thermal transfer to the base of the HSF.  Thermal compound is not really very good at thermal transfer.  It's just better than the air it displaces from the tiny imperfections between the top of the CPU and the HSF base.  Too much and it's an insulator.  Too little and all those imperfections are full of air.  That is especially true if you have smeared it unevenly and there is not even contact across the entire plane.

If your top fan has gone out since you were getting the previous temperatures (those were actually lower than the die due to AMD's wacky temperature reporting -- which is not the actual temperature of the die), then case temperature may actually be the problem.  Even with those two fans on the heat sink, if the air in the case is not being moved it gets warm.  Your effective ambient temperature is the case temperature, not the room temperature.  The temperature in the case will rise if the air is not circulated.

The HSF can only cool relative to its ambient temperature.

So, to answer your question:  Use an appropriate amount of new compound *and *replace your fans.

---

### Post by QIII on 2014-12-02
By the way, this is a perfectly good question to ask on the Ubuntu Forums and this section is fine.

---

### Post by SagaciousKJB on 2014-12-02
So then I could probably assume that the amount/application that I put on is effectively like it's not even there?  Before I used WAY too much, I wasn't exaggerating when I said it basically welded the CPU to the heatsink.

Thanks!

---

### Post by QIII on 2014-12-02
Even when applied properly, older thermal compound, when overly dried out, can be like cement.

There is a bit of art to applying it.  A tiny dab is not enough to fill the voids.  Enough that it squeezes out the sides when you tighten the HSF down is a thermal blanket.  There is sort of a rule of thumb that says too much is worse than not enough, but that doesn't mean too little is OK..  Sometimes one has to monitor the performance for a while and re-do it.

---

### Post by SagaciousKJB on 2014-12-02
I blame the deceptive Artic Silver tube, thought there was some left :(  I wonder if Radioshack has some cheap stuff I can use...  They use to way back in the Athlon days.

---

### Post by QIII on 2014-12-02
Radio Shack has it.  But do you want to trust your CPU to the Lowest Bidder of the Week supplier to Radio Shack?  It's probably worth it to pay $10 more for Arctic Silver.  Cooler Master's product rates pretty well, as does Noctua's -- if you can find it without ordering it.

Two things never to be cheap on:  PSUs and thermal compound.   For a little extra you avoid expensive events.

---

### Post by SagaciousKJB on 2014-12-03
Well I ordered some Artic Cermaique off Newegg.  Hope that works well.  I'm just gonna wait on the fans because there's seriously not a lack of air flow in there.  I have a 120mm intake and the two 120mm CPU fans, and that's in a Antec P180 so it's all partitioned physically from the PSU and HDDs--which also have their own fan.

I'm hoping that the increase in temperatures from last year just has to do with the compound aging.  I hear you're supposed to replace it every 6 months, not ever 6 years :P

---

### Post by Yellow Pasque on 2014-12-03
> Last night I noticed it in the 32C range and realized I probably needed to maintenance it--it was caked with dust.
You should have just used compressed air to blow out the heatsink. I'm not sure why you chose to reapply the heatsink. I've got a Phenom II X3 730 (95W TDP) with a Thermalright Ultra 120 heatsink, using Arctic Silver 5 and one 120mm Yate Loon fan running off 5V (probably between 600-800 RPM) and blowing the dust out gets the temps back to about where they were when I first built the system 5 years ago.

> But now it's still idling at 29C for the same ambient temperatures.
That's nothing to worry about, especially if temps are less than 55-60C when running a heavy load for an extended period of time. A burnt out exhaust fan can certainly account for the difference since it might change the whole airflow scheme of the system even if the other fans are still working.

> I hear you're supposed to replace it every 6 months, not ever 6 years
Citation? Please don't tell me this comes from companies manufacturing/selling thermal compound.

---

### Post by WinEunuchs2Unix on 2014-12-03
When I replaced my dead laptop fan and researching the process most people recommended NOT removing the heat sink pipe and applying new thermal paste.  Something about factory seal being superior.  FWIW.

There are lots of tantalizing video's on youtube on how to apply thermal paste but I erred on the side of caution, laziness, frugality and  1 thousand times bitten 1 million times shy.

---

### Post by sammiev on 2014-12-03
> **WinEunuchs2Unix said:**
> When I replaced my dead laptop fan and researching the process most people recommended NOT removing the heat sink pipe and applying new thermal paste.  Something about factory seal being superior.  FWIW.

There are lots of tantalizing video's on youtube on how to apply thermal paste but I erred on the side of caution, laziness, frugality and  1 thousand times bitten 1 million times shy.

+1 well spoken. ;)

---

### Post by SagaciousKJB on 2014-12-04
> **Temüjin said:**
> You should have just used compressed air to blow out the heatsink. I'm not sure why you chose to reapply the heatsink. I've got a Phenom II X3 730 (95W TDP) with a Thermalright Ultra 120 heatsink, using Arctic Silver 5 and one 120mm Yate Loon fan running off 5V (probably between 600-800 RPM) and blowing the dust out gets the temps back to about where they were when I first built the system 5 years ago.


That's nothing to worry about, especially if temps are less than 55-60C when running a heavy load for an extended period of time. A burnt out exhaust fan can certainly account for the difference since it might change the whole airflow scheme of the system even if the other fans are still working.


Citation? Please don't tell me this comes from companies manufacturing/selling thermal compound.

No compressed air, I had to use the faucet.  So as you could tell I didn't want to leave it attached to the motherboard to do that :P

---

### Post by QIII on 2014-12-04
Factory "seal" better?  It's not a seal, it's a layer of thermal transfer compound between two reasonably (it is hoped) flat but imperfect surfaces.  You clean them up, butter one and clamp the other down on it.

A laptop is no different than a desktop with regard to the mechanical relationship of the CPU to HSF.  The difference is the ease with which the compents can be accessed and handled.  Most laptops are designed for manufacturability, not maintainability.

In any case, the OP was about a desktop.  :)

I would agree that it is best to leave things as they are from the factory because it is actually pretty rare that overheating is due to "old thermal paste". I've run computers for YEARS without changing HSFs unless permanently attached fans go out.  Newly noted overheating is more often dust or fans than anything else.

---

### Post by Mark Phelps on 2014-12-04
Last time I replaced an HSF, I read that applying the paste involved putting a dab on the center of the processor and then using a flat-edged scraper (like a credit card), to repeated spread the paste until only a very thin film was left.  I did that, and four years and more, the processor has been working fine without any overheating.

---

### Post by Yellow Pasque on 2014-12-04
> **QIII said:**
> I would agree that it is best to leave things as they are from the factory because it is actually pretty rare that overheating is due to "old thermal paste".

Agreed for the most part. I have read some complaints about cheap thermal pads in laptops that didn't perform well, especially when dust started to form.

---

### Post by QIII on 2014-12-04
I have often read the same.  And it appears to work for most people.

However, the manufacturers of Arctic Silver say it is optional to "tint" the base of the HSF and the CPU cap, and then use a card to spread a very thin layer and then wipe the base carefully with a lint free cloth so that only the very tiny valleys are filled with compound.  This should result in what appears to be no more than a slight discoloration of both surfaces.  They say NOT to spread the dab of compound that is applied to the CPU to avoid introducing air bubbles.  The top of the CPU is not machined to anything like a smooth surface (as the HSF base should be) and spreading the compound can "roll" it across the ridges, introducing air.

A slight twist of a few degrees left and right when the HSF is in place is acceptable to ensure good distribution.

No arguments.  Just going by manufacturer instructions.

And those thermal pads?  I agree.  Worthless.  They ease manufacture rather than ensuring good performance.

---

### Post by Yellow Pasque on 2014-12-04
Yeah, with AS5, you put a rice-sized bead at the center and install your heatsink (without lifting up). That way, you don't have air bubbles..

---

### Post by SagaciousKJB on 2014-12-04
*facepalm*

I was looking through the box for the CoolerMaster heatsink I have, looking for fan attachments, and guess what I found...  Thermal compound.  Sweet glad I ordered some already lol

Came with some kind of weird plastic washers though, I wonder what they are for...

---

### Post by Bashing-om on 2014-12-04
SagaciousKJB; Hello
> 
Came with some kind of weird plastic washers though, I wonder what they are for...

1st guess, the standoffs between the Motherboard and the case ?

[INDENT]amazing
[INDENT][INDENT][INDENT]what it takes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SagaciousKJB on 2014-12-04
Holy cow!  Apparently the bigger issue here is that my North Bridge has been dangerously overheating for the entire 5 years I've ran the desktop.  Before it was idling at 55C and would get up to 65C regularly O_O  I always thought that seemed really hot but saw other users of this DFI board report similar temps.  But now after applying better compound the NB idles at 39C and at max load I can't even get it beyond 45C.

I'm surprised this thing is still running

---

### Post by tgalati4 on 2014-12-04
North and Southbridge chips are common failure points and often ignored.  They don't have the same protections that the CPU has.  I've seen holes burned through them.

---

### Post by Yellow Pasque on 2014-12-05
> Before it was idling at 55C and would get up to 65C
Northbridge's usually have a fairly high max temp (much more than desktop CPU's). I wouldn't assume that 65C under load is "dangerous" or even overheating.

---

### Post by SagaciousKJB on 2014-12-05
> **Temüjin said:**
> Northbridge's usually have a fairly high max temp (much more than desktop CPU's). I wouldn't assume that 65C under load is "dangerous" or even overheating.

Yeah I haven't been able to find a verifiable source for what the max temperatures for them are.  I do know though that after applying the Cooler Master compound it dropped down to about 30-something C on idle.  I decided to use a small fan and point it at the heatsink on the NB and it's really got its temps down.  I sacrificed one of the CPU cooler fans to put it up on the top exhaust fan, but still need to replace the one on the side.

I love the Antec partitioned design.

[[IMG]http://i1266.photobucket.com/albums/jj528/sagaciouskjb/2014-12-05_15-18-50_150.jpg[/IMG]](http://s1266.photobucket.com/user/sagaciouskjb/media/2014-12-05_15-18-50_150.jpg.html)

---


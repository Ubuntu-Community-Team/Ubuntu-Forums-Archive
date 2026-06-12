---
title: "A Simple Recommendation"
date: 2008-11-12
forum: Hardware
---

### Post by oo-boon-too on 2008-11-12
I can buy an evga 9500GT for 76$
My current card's (Way better than that 9500gt, but is ATI) driver no matter what i do (OR it seems) will reuslt in slow, choppy windows.

So I guess the question is, will this nVidia card provide regular (As in, how it would preform under windows) window movements or would it not be worth the money?

I'm not worried about having to re-install ubuntu, hours of driver configuring, or anything of that sort, as long as the end result is a nice and clean windows dragging experience.

And as I said (Although not specifically) I have an ATI HD4850, which at the time of purchase was a little spendy (200$, spendy to me at least), so if this nVidia one will not be any different then I guess it would not be worth it.

And on a side note, what are stream processors? That nVidia one has 32, and the GTX's have like 130~, whereas my ati one has 800;\
Do they actually do anything special?

---

### Post by NewDisciple on 2008-11-12
**[SIZE="2"]What is your power supply?  That could have something to do with the actions you described.[/SIZE]**[SIZE="2"][/SIZE]

---

### Post by oo-boon-too on 2008-11-12
I sure hope not;\
I have an Antec TruePower Quattro 850W [http://www.antec.com/usa/productDetails.php?lan=us&id=27850](http://www.antec.com/usa/productDetails.php?lan=us&id=27850)

---

### Post by NewDisciple on 2008-11-12
[SIZE="2"]**I see that you have four rails.  I don't know what your settings are but I have read that with multiple rails you have to adjust the power settings in your bios to adjust for a more demanding video card. Find out how much power you need for your card & then check your bios to see if that's what it is actually getting.  On a power supply with multiple rails the stated wattage doesn't always mean much.  Check some hardware forums you can usually get good info on various systems.**[/SIZE]

---

### Post by oo-boon-too on 2008-11-13
Hmm, how exactly do i check the voltage of the card?
It works perfectly in Vista with the same setup that I have it in right now, unless Windows and Ubuntu can change the voltage it should all be the same...but I dont know much about that stuff.
EDIT: I know to look in bios but, where would it be? I see the 5V 1.30V and thr 12V displays, is that it? Or am i specifically looking for a "PCI-E Voltage"? <- Of which i cannot find;\

---

### Post by NewDisciple on 2008-11-13
[B]Need more info on your system.  Also include manufacturer name.  Mobo, ram, cpu.  Have you flashed your bios to latest & greatest?  Driver for your VGA card?
In the meantime heres a link about PSU's & balancing loads on multiple rails.  [www.playtool.com/pages/psumultirail/multirails.html]("www.playtool.com/pages/psumultirail/multirails.html")[/B]
Additionally, remember that heat issues can effect video card performance.
Temps?

---

### Post by oo-boon-too on 2008-11-13
Well really im just fed up with poor ati drivers and was wondering if that nvidia one i stated earlier (Now i might just think about a 8500gt) would work better, seeing as how everyone seems to have amazing results with nvidia.

My Computers manufacturer is, well, me i guess. Purchased in parts and pieced together by me.
Can't say anything about temps while in ubuntu, but under windows my temps for CPU, MOBO, and GPU were 30*, 34*, and 48 respectively.
(I don't use the bios for the temps, because im quite sure it isn't reading the correct temperature, even then, the temp would be 34*)
So specs:
Core 2 Duo E8400 3.0GHz 6M 1333M 775
4GB(2x2GB) DDR2 PC6400 800MHz Matched Pair Kingston
ASRock Wolfdale1333-D667 LGA 775 Intel 945GC Micro ATX Intel Motherboard
Antec TruePower Quattro 850W
Sapphire Radeon HD4850 512MB TV-Out/2DVI

In ubuntu I am using thr latest driver, and it doesn't perform as it should.
I know my card works, as i have been using it in Vista for things suck as Age of Conan, WoW, Crysis, Fallout 3, etc. and all works well.

I used my onboard graphics, which didn't come up with any drivers needed (in ubuntu), and it gives the same choppy effect.

My wiring is as follows:
The motherboard power, the 4-pin atx power, harddrive (IDE) and DVD drive all are using the base cables (Not sure what to call them, the ones that come out of the supply by default)
My GFX card has its 6-pin power supply being fed by a optional cable inserted into one of the two pci-e ports on the power supply.
[http://www.techreviewdb.com/images/stories/jreviews/383_TPQ850Q_1195568136.jpg](http://www.techreviewdb.com/images/stories/jreviews/383_TPQ850Q_1195568136.jpg)
Those extra slots on the bottom, if read, say "HDA;HDA;HDA;PCI-E;PCI-E". Nothing is plugged into the "HDA" ones, but one cable is plugged into the "PCI-E" one (Well, one of the two).
There is a 6(8 if desired) pin connector that is with the 'default' cables, which was what i had been using, until recently switching to just the 6-pin one. Both had the same effect on performance.
Also, this choppy-ness has happened on previous ATi cards:
my X1300PRO
and my HD3650

This is why I am left to believe that ATi is just not ready for the GNU/Linux era yet.

On the subject of bios updates, no i have not, as I have not realized there had been errors that required it to be (Nothing has ever gone wrong, other than windows has a giant target on its head for viruses).

---

### Post by NewDisciple on 2008-11-13
[B]Yeah, you're most likely right about the ATI driver as your hardware setup looks pretty good.  I had seen on one of the forums that the drivers may not be updated further, that they were skipping to the next generation.  I don't know, thats just what I read.  I'm going to have the same problem I think but I have to get past my DOA Asus P5Q issue first.  In any event Nvidia may not have a driver for a newly released kernel but it seems like they get it fairly quick.
Have you compared that Nvidia card you were looking at to the 9600GTX?  Just wondering.
My final thought is that maybe ATI just isn't ready for prime time on Linux yet.[/B]

---

### Post by oo-boon-too on 2008-11-13
I haven't Compared it, I'm looking for something fairly cheap, as all i really want are fluid windows and preferably some Compiz.
Maybe in the distant future ATi drivers will be good, then i can whip out my 4850...which is really quite a good card, eats everything i feed it in vista.

Well this helped, I now am confident that my system isn't just put together wrong (I've taken it apart and put it back many times).

Too bad nVidia doesnt have a "Trade your ATi card for one of equal performance" button on their site;)

---


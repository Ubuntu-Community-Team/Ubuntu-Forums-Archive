---
title: "what ram should i get?  its expensive and confusing &gt;.&lt;"
date: 2010-04-27
forum: Hardware
---

### Post by ChodeOfDoom on 2010-04-27
Hey guys,
Im working on designing my new gaming rig with an AMD Phenom II x6 Processor, MSI 790FX-GD70 AM3 ATX mobo, and dual GTX 480 GPUs.  My only issue is that i have absolutely no idea what ammount and type of RAM to get.  This rig will be used for hardcore gaming.  I did some looking around and decided that I would ask the experts before investing in $800 of 16 gb G Skill RAM.  I saw something about AMD needing special RAM or something, too.

I appreciate any help you guys can give me on this matter.

Thanks!
ChodeOfDoom

---

### Post by gordintoronto on 2010-04-28
You will get better answers to pure hardware questions at PCMech.com.

This memory looks fast:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231355](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231355) 
but it's sure expensive!

$1,000 worth of video cards?  Crazy!

---

### Post by porikonut on 2010-04-28
You can't do SLI on AMD chipsets so either get rid of one of the GTX480 or get a nice 5970 or make 5850/5870 crossfire.

---

### Post by cascade9 on 2010-04-28
> **ChodeOfDoom said:**
>  I did some looking around and decided that I would ask the experts before investing in $800 of 16 gb G Skill RAM. I saw something about AMD needing special RAM or something, too.

Just good, old fashioned, DDR3, 1333 or higher (anythign higher than 1333 is overclocking the RAM- it supports up to 2133 but you wont 'need' it). 

> **porikonut said:**
> You can't do SLI on AMD chipsets so either get rid of one of the GTX480 or get a nice 5970 or make 5850/5870 crossfire.

Just what I was thinking..... +1.

---

### Post by ChodeOfDoom on 2010-04-28
oh wow I didnt realize that I would have to do ati graphics... personally I prefer nVidia since they're just plain old better cards.  Also, how much RAM do you think i should go with?

---

### Post by Cato2 on 2010-04-28
A few comments, I'm assuming you want to do at least some gaming on Ubuntu since you are on this forum:

- look at Tom's Hardware and Anandtech for reviews of memory - mostly it doesn't make a lot of difference though unless you are doing serious overclocking

- avoid OCZ DDR3 RAM - I had major problems and the forums are full of similar stories where the RAM fails even at stock settings.  I had much better luck with Corsair DDR3.

- motherboard supported RAM lists are useful, but they didn't help with the OCZ RAM mentioned

- for gaming, I'd say 4GB is still plenty, but make sure you use only 2 slots so you have 2 spare slots for expansion.  Most games are still 32 bit so they won't begin to use the extra RAM.

- go for Ubuntu 64-bit (see my sig) as that will actually let you use your RAM

- look into Crossover Games - supports some Windows games very well (e.g. Half Life series, Team Fortress 2, Portal, WoW, etc), though most will require rebooting into Windows

- definitely go with NVidia for any gaming on WINE+Linux - drivers are much more mature

- do you really need 2 x GTX480 cards?  They will generate a huge amount of heat, requiring more fan noise to deal with, and much larger PSU, and most games don't give that much performance boost with SLI anyway.  Might be better to get one now, then upgrade to something faster in a year or two.  Tom's Hardware also does some good graphics card comparison reviews that show you performance on a choice of cards for various games.

- WINE doesn't support anti aliasing (AA) properly anyway (I tried a lot), so that reduces hardware requirements.  I have a GTX260 which is more than really needed for the games supported on WINE.

Hope that helps.

---

### Post by cascade9 on 2010-04-28
I dont know of any games that show any improvement over 8GB. Thats what I would get, maximum...but then again I would never even look at SLI/corssfire so maybe I'm just cheap. 

You should still be able to run nVidia fine, BTW, just not in SLI. If/when nVidia does a 4XX 'SLI on a card' (like the GTX295, 2x GTX chips on the one card) that would be fine as well.

---

### Post by ChodeOfDoom on 2010-04-28
Wow you guys are really helpful xD  Thanks for all your advice!  I am now planning to go with 1 ATI Radeon HD 5970 and 8 gigs of G Skill Ripjaw 1333mhz DDR3, saving me another boatload of money =)  Should I feel the need to get better video later on in life, I can throw in another 5970 on Crossfire!

oh yeah... one last question.  what PSU do I need for all this?  I was thinking maybe a 1000 watt just in case I upgrade video and need it, but I see a lot of SLI ready and no Crossfire ready.  Is this a problem?

++ I just remembered that I don't know 'poopie' about cooling systems, so any recommendation are appreciated.
P.S.
 I don't really see price as being an issue

---

### Post by cascade9 on 2010-04-28
Even if you went to crossfire, you still wouldnt need more than 700-750watts or so...a tiny bit more wouldnt hurt, but you wont need 1000watts. 

You say money is no issue? Then a seasonic M12D 850-

[http://www.silentpcreview.com/Seasonic_M12D_850W](http://www.silentpcreview.com/Seasonic_M12D_850W)

SLI ready should have no issues with crossfire (and really, provided your power supply has enough watts and the correct connections then even 'sli ready' means nothing). 

Cooling? Lots of aftermarket coolers out there if you dont want to use the standard cooler, I'd get a coolermaster V8. Not that its the only good choice....

BTW, if you really have no issues with money, slightly faster RAM than 1333 isnt going to hurt. Even if you dont run it at the rated speed, faster RAM normally has better timings- it might not matter much, but it helps.

---

### Post by Cato2 on 2010-04-30
ChodeOfDoom, I think you need to do quite a lot more research, particularly around the PSU and the 2 x GTX480 you are planning, but also generally to make sure everything is compatible.

For example - how many PEG connectors does the PSU provide, vs. the number required by the GTX480?  How much power does each card require, and how many amps?  Can the PSU provide enough amps?  Can your case airflow and fans handle the heat generated by two of these?

That's just one example - don't want to put you off, but the GTX480 is brand new and very power hungry so a build using this will be more of a challenge.  Even using an old NVidia 7900GS, I had to remove one hard drive just to reduce heat in a very well ventilated case (5 fans including CPU), otherwise I had artefacts in games due to the 7900GS overheating.

I would really recommend starting out with a single GTX480 not two - easier to get this working and it may well be enough - as one of the fastest available cards it should be fine (if very noisy) without SLI for almost any game and monitor resolution.  If you always play with headphones the noise may be a non-issue though.

One of the overclocker's forums, or Tom's Hardware or Anandtech, would be good to get comments on your build in more detail.  Also, eBuyer.com's Rate My Rig forum is good for this - people will go into detail on your proposed build, though it's mostly for UK users who shop at eBuyer.

---


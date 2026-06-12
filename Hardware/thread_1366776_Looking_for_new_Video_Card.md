---
title: "Looking for new Video Card"
date: 2009-12-28
forum: Hardware
---

### Post by IamJohnHayes on 2009-12-28
Basically looking for a new video card.  Card must be 8x AGP and i would prefer 1GB on board.  I thought I saw some w/ nVidia chipsets a few months ago but now i can't find any.  I have also heard ATI is getting better w/ Ubuntu.

Right now i'm looking at a Radeon HD 4650,  has anyone used one successfully?  Or could someone please recommend a card that is similar yet functional.

Thanks.

---

### Post by Ginsu543 on 2009-12-29
I believe the Radeon HD 4650 you're looking at is a PCI Express card, not an AGP card. Since AGP is an old defunct standard, I don't think there are any AGP cards with 1GB of onboard video ram.

---

### Post by 5nak3 on 2009-12-29
hi,

first up the 4650 still comes in AGP form, as i've also had my eye on that.

i'm currently running a Nvidia 6200 with 512 video ram, but I would also like a 1gb card if possible. Unfortunately i've been unable to find a Nvidia card with 1gb, only ATI seem to have released such a card. The problem is the ATI cards still seem to have quite a few problems, and personally i dont want that hassle.

if you could find a 7600 GS i think that came in 1gb form althogth my searches in UK stores have given no results.

OP, where are you from if you dont mind me asking, we are both in the same boat and it would be great if we could get an answer on this one!

One thing i would also point out that I'm not 100% sure on is the fact that my original card was DDR2, the Nvidia 6200 i have now is also DDR2 ram, i did notice a could of 512mb cards but with DDR3 ram and i was thinking these might be a better option as opposed to trying to find a 1gb card. But is it possible to tell if DDR3 will work with my motherboard?

---

### Post by IamJohnHayes on 2009-12-29
^^^ Snake is correct, it does come in AGP.  I know there were nVidia cards w/ 1GB onboard b/c i almost bought one a few months ago and put it off,  now I can't seem to find one.  I may end up going to a 128bit 512Mb Card if I can't find an ATI card that works.  but I really like the HDMI output on the 1GB cards.

---

### Post by HappyFeet on 2009-12-29
[Here]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639&name=AGP%204X%2f8X") are 40 AGP video cards to choose from. There are some 1GB models available. But my personal choice would be an Nvidia card.

---

### Post by IamJohnHayes on 2009-12-29
I have allready searched all the usual places. I'm more or less just trying to see if anyone here has a 1GB AGP ATI card that works with out too much hassel.  If not i'll end up w/ an OC'd 512.

---

### Post by 5nak3 on 2009-12-29
I noticed the link posted to the graphics cards are on Newegg, so am I safe in assuming that the OP and poster of the link are from the US? I do not think that Newegg ship to the UK and in any case the hassle of sending it overseas probably isn't worth it.

OP, you said you had seen a 1GB card do you by any chance remember the name of it?

I'll let you know where I stand at the moment:

My card is pretty much identical to this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814134076](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134076)

Although mine is made my PNY.

If I could boot Windows on this PC i'd probably go with the ATI card, fact of the matter is that the catalyst drivers are getting better. The newer cards are supported, but in my readings ATI cards have no end of problems. I found one thread similar to the problem you and I are having, albeit the user actually has the card.

[http://ubuntuforums.org/showthread.php?t=1346070&highlight=ATI+HD+4650](http://ubuntuforums.org/showthread.php?t=1346070&highlight=ATI+HD+4650)

As I am forced and stuck to using Linux on this box and I've already had bad experiences with ATI cards in Linux I think I'd be willing to overlook a 1gb card for a 512mb from Nvidia that would perform better than my current card. 

End of the day, unless you have a PCI-e slot, which I assume you don't, the AGP standard is pretty much finished. If anything happens to our cards in the near future, we are looking at pretty much a new system as getting our hands on AGP cards becomes more difficult.

Therefore, my aim is to buy a card which performs better than my current one, which is linux compatible with minimum fuss and use my current card as a backup in case things go wrong. 

In that respect, I think the best offering from Nvidia as far as AGP cards go is the 7600GS.

I'd be interested in hearing what you think!

---

### Post by 5nak3 on 2009-12-31
Well after much searching I found these two cards:

[http://www.amazon.co.uk/exec/obidos/ASIN/B00270O048/ref=pd_luc_mri?_encoding=UTF8&m=A11UYXL65U9RAB](http://www.amazon.co.uk/exec/obidos/ASIN/B00270O048/ref=pd_luc_mri?_encoding=UTF8&m=A11UYXL65U9RAB)

[http://www.amazon.co.uk/nVidia-GeForce-Graphics-Graphic-adapter/dp/B002I9FGTQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1262279502&sr=1-1](http://www.amazon.co.uk/nVidia-GeForce-Graphics-Graphic-adapter/dp/B002I9FGTQ/ref=sr_1_1?ie=UTF8&s=electronics&qid=1262279502&sr=1-1)

I'm not sure which one would be better though. It seems the 7950GT is slightly faster, but I've also heard there are some major build quality/problems with it that mean the fan runs at 100% all the time.

Any suggestions anyone?!

---

### Post by mickie.kext on 2009-12-31
> **IamJohnHayes said:**
> ^^^ Snake is correct, it does come in AGP.  I know there were nVidia cards w/ 1GB onboard b/c i almost bought one a few months ago and put it off,  now I can't seem to find one.  I may end up going to a 128bit 512Mb Card if I can't find an ATI card that works.  but I really like the HDMI output on the 1GB cards.

Why do you need 1GB card for? You know, 1GB models are generaly slower than 512MB ones, especially on AGP. It is because 512Mb models usualy use faster memory (DDR3 or fast DDR2) while 1GB models usually packs cheap and slow memory. And HD4650 can't really utilize even 512MB, with 1GB you have half of it wasted all the time. 

Another thing are broken ATI drivers and opensource ones are not yet very good.

Last thing... which procesor do you have? Since is AGP borad, it is probably single core CPU. Any new card is overkill for single core CPU so you will not see much improvement over you old GPU. 

I think there is no lot a sense in bying AGP card these days, PCI-E are cheaper and faster.

---

### Post by 5nak3 on 2009-12-31
> **mickie.kext said:**
> Why do you need 1GB card for? You know, 1GB models are generaly slower than 512MB ones, especially on AGP. It is because 512Mb models usualy use faster memory (DDR3 or fast DDR2) while 1GB models usually packs cheap and slow memory. And HD4650 can't really utilize even 512MB, with 1GB you have half of it wasted all the time. 


Last thing... which procesor do you have? Since is AGP borad, it is probably single core CPU. Any new card is overkill for single core CPU so you will not see much improvement over you old GPU. 

I think there is no lot a sense in bying AGP card these days, PCI-E are cheaper and faster.

Actually this is a good point Mickie, I've done some reading and it does seem that the bottleneck at least on my system is the CPU which is a single core 3ghz.

The reason I spent money on getting the 6200 a couple months ago was because the systems old GPU for some reason got fried, and I wasn't sure at the time if it was a GPU or something else. I bought the 6200 as a cheap testing unit.

Now that I have everything running again, added more ram and a new PSU, I thought I may as well get my hands on a spare AGP card because no matter which way I cut it, this is going to be my rig for the forseeable future. And given the difficulty in finding AGP cards at the moment, i thought it be best to try do something now as opposed to 5 or 6 months down the line. 

> **mickie.kext said:**
> Another thing are broken ATI drivers and opensource ones are not yet very good.

So you agree that considering an ATI card is, as I thought, a bad idea and it would be best to stick with Nvidia?

---

### Post by HappyFeet on 2009-12-31
> **5nak3 said:**
> 
So you agree that considering an ATI card is, as I thought, a bad idea and it would be best to stick with Nvidia?

Nvidia is the way to go.

---


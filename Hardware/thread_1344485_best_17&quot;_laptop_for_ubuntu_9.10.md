---
title: "best 17&quot; laptop for ubuntu 9.10"
date: 2009-12-03
forum: Hardware
---

### Post by jleaman on 2009-12-03
It may have been covered but could not find a answer, what would be the best supported, with all drivers, ie sound video lan burner video cam etc etc. I'm looking to buy a cheaper 17" laptop either a hp or a asus, or one that is recommended here.

What are your guy's suggestions I'm not looking for a 2000$ laptop something cheap, i see best buy sells a few for around 699$ ( canadian ) 

Thought's suggestions comments :)  I have fallen back in love with Ubuntu and would like to use it as main machine again.

Jase

---

### Post by u.b.u.n.t.u on 2009-12-03
Ubuntu would support common hardware first one would think. Therefore as long as your hardware meets this general principle you should be fine.

One thing I will add, ATI and Nvidia are two of the leading GPU manufacturers. You may wish to bare that in mind.

Make sure the specs meet or exceed the following:

[IMG]http://img145.imageshack.us/img145/2443/20091202211947.png[/IMG]
Source: [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)


UPDATE


This thread may be relevant:
[http://ubuntuforums.org/showthread.php?p=8431349#post8431349](http://ubuntuforums.org/showthread.php?p=8431349#post8431349)

---

### Post by jleaman on 2009-12-03
> **u.b.u.n.t.u said:**
> Ubuntu would support common hardware first one would think. Therefore as long as your hardware meets this general principle you should be fine.

One thing I will add, ATI and Nvidia are two of the leading GPU manufacturers. You may wish to bare that in mind.

Make sure the specs meet or exceed the following:

[IMG]http://img145.imageshack.us/img145/2443/20091202211947.png[/IMG]
Source: [http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)


UPDATE


This thread may be relevant:
[http://ubuntuforums.org/showthread.php?p=8431349#post8431349](http://ubuntuforums.org/showthread.php?p=8431349#post8431349)


Would taking the 9.10 disc with me to the store and booting of the disc and seeing if it works ? If all hardware works then it would work if i installed it ?  ( in therory )

---

### Post by coffeecat on 2009-12-03
> **jleaman said:**
> Would taking the 9.10 disc with me to the store and booting of the disc and seeing if it works ? If all hardware works then it would work if i installed it ?  ( in therory )

If they let you do that, that's the best thing you could do.

As far as the display card is concerned, go for nvidia or Intel (posting from a laptop with an ATI card. :rolleyes:) There were serious issues with **some but not all** Intel video chipsets with Jaunty, but the situation is better in Karmic. But if it works in the live session, it is likely to work in a hard disc installation.

One thing to watch out for is that some wireless chipsets seem to work OK in the live session, but turn out to have flaky connections long term. For example, in this Acer, I have a...

[quote="lspci from the terminal"]Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express)[/quote]

It worked fine for a few minutes with the live CD but wasn't reliable longer than that. Fortunately for me, installing a couple of backported kernel module packages solved this - but not something you can test with a live CD..

---

### Post by SeePU on 2009-12-03
I would try to get an Asus and try to get one with the best cpu that you can afford.  Also, if possible, one with Nvidia card.  An Intel card is okay but it's not much for gaming or intensive video work but it should be able to good enough for most video purposes.

Asus laptops get good reviews especially the newer ones and certainly better than comparable HP laptops.

As for hardware, try to Intel processors/chipsets and an Intel wireless card (many have Intel wifi so that shouldn't be too hard).

---

### Post by ubuntpetbe on 2009-12-03
look out for the graphic cards from ATI. 
Many very new models 5000 series are not well supported. 

There is currently a gap between the vendor support for newer models and FOSS-software drivers for older models. 

It's at the ATI radeon Xx00 up to the X2300 series. 
(The small x is a number, the big X stands for an X.) 
Beginning from X2600, you have support again. 


Also for any card, if they let you boot a LiveCD. 
open a terminal and type: glxinfo. 
Look at the OpenGL version string. 
(higher is better)

---

### Post by u.b.u.n.t.u on 2009-12-03
> **coffeecat said:**
> As far as the display card is concerned, go for nvidia or Intel (posting from a laptop with an ATI card. :rolleyes:)

Tomorrow ATI may work and Nvidia may not. I disagree with advising against ATI.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **jleaman said:**
> Would taking the 9.10 disc with me to the store and booting of the disc and seeing if it works ? If all hardware works then it would work if i installed it ?  ( in therory )

Sketch out on a piece of paper the minimum hardware specifications, a short list of alternative manufacturers, then see which laptop meets those criteria.

You don't want to go to a store and know less than the sales person. So best to do your homework on this, get up to speed on the topic, and then set out.

I build my own computers from scratch, desktops. Knowing what one is doing is essential and the same applies to purchasing a laptop.

No laptop is perfect. Ubuntu is in a constant state of development. So just do your best and good luck!

---

### Post by jleaman on 2009-12-03
thanks for all the heads up guys, much apreciated :)  I like the looks of the new Black asus laptops they look kinda sexy :) Nothing to fancy no huge bling bling lights and crap, just simple good and nice!

I'll try a live cd this weekend and see.!

Jase

---

### Post by u.b.u.n.t.u on 2009-12-03
Cheers.

---

### Post by SeePU on 2009-12-29
Right now, ATI is still crap.  If 3D doesn't work, then you probably don't have other features working as well!  Suspend/Hibernate and other features don't work properly with ATI cards.  ATI takes their time with support and are extremely slow at 'fixing issues.'  Also, they don't know if they want to improve open source support or proprietary support more.  They stick to haivng all their eggs in one basket when it comes to Windows as that is where the money is.  It isn't really their fault either as most companies would go with where the money is and their company is smaller than Nvidia although they now have AMD behind them.   But, I guess AMD is too worried about their struggle with Intel so they are not as concerned with whether ATI has good drivers in Linux.

When you buy a laptop, you're only buying for three or four years anyway.   You don't expect it to last 10 yrs (not nowadays).  So, yeah, one can recommend to buy one with a Nvidia card NOW.

---


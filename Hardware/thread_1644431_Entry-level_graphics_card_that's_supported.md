---
title: "Entry-level graphics card that's supported?"
date: 2010-12-13
forum: Hardware
---

### Post by bkapps on 2010-12-13
Hi all, I'm looking to upgrade my graphics from intel gma 950, are there any graphics cards that are innately supported and work well?
I've tried a geforce 8400gs and the damn thing wouldn't even let my computer boot.

---

### Post by pricetech on 2010-12-13
If I'm understanding you correctly, that's a BIOS problem first.  Try checking the BIOS without the card inserted first and make sure your video selection will accommodate the card, then insert it and see if it boots.

---

### Post by bkapps on 2010-12-13
No no no...I could get to GRUB, make a selection, and then after that I'd get nothing.  I tried LiveCD's, which booted to selection screens, like Maverick Meerkat where it lets you decide whether to install or to try and then it would just hang there.

I've been looking for something to give me more ummph when driving my 1920x1080 monitor for videos and video games.

---

### Post by noob_undo on 2011-01-08
I'd like to know what people recommend too. Preferably fanless.

---

### Post by Firezap on 2011-01-08
I am using a GT240. It works fine except the clock speeds are not correct. It's clock speed is correct when I boot up Windows though. Although I have yet run a program that lags behind in graphics. So as far as I am concerned, it is saving energy.:) I got a great deal on it, payed 60 dollars and it has 512 megabytes of DDR5 memory. So my graphics and little bit of gaming I do fly.:popcorn: All I had to do to get it to work was install the restricted driver and I had full 3d acceleration.:D

Sparkle seemed to have a nice fanless Geforce 9500 card for around 55 dollars. It seemed nice, never personally owned one. I use to use a low profile Geforce 6200 that worked flawless with Ubuntu a year or two ago on my old machine. It was fainless as well.

---

### Post by noob_undo on 2011-01-08
Sounds good. I'm looking for something fanless though, and preferably AMD. I'll post back with results when I've got something.

Is there a de-facto GPU forum around here somewhere?

---

### Post by cascade9 on 2011-01-08
For current nvidia, GT210, 220, 240 and GTS450 all have fanless versions. 

AMD, HD 5450, HD 5550, HD 5570, HD 5670, HD 5750 all have fnalless models. (its possible that there are other current ATI cards with linux support that have a fanless models) 

nVida has better closed drivers, and VDPAU (nvidia hardware video decoding). AMD has better open source drivers, but XvBA (ATI/AMD hardware video decoding) is buggy. 'Buggy' might actually be nice as far as XvBA goes, its a mess from what I've seen.

---

### Post by gradinaruvasile on 2011-01-08
If you want gaming, buy a nvidia. I recently tried an integrated ati 3000 and my (integrated) 8200 nvidia worked far better.

The 3000 had slightly more fps in games but had graphical glitches in wine games + had a very annoying bug that rendered all ioquake based games useless - the mouse input lagged 1-3 seconds. Maybe there is a fix for that somewhere but i did not found it in 1 hours of searching. Used the latest fglrx (10.12) driver.

My 8200 card in contrast had slightly lower fps but ran most games (including LotRO via wine) flawlessly + had vdpau hardware decoding that is better than the ati decoding (that uses libva).

---

### Post by efflandt on 2011-01-08
I have a GT 430 which seemed to be the best Nvidia I could get that did not require > 300 watt psu.  It is probably similar to GT 240, but is faster and cooler using less power than the GT 220 I had before, and can do directx 11 (200 series cannot).  It idles only 3C over room temperature with a quiet fan.  It is new enough that even Natty kernels do not know what model it is, but works fine with nvidia 260 drivers (although, default nouveau drivers before Natty default to low graphics).

---

### Post by Nutria on 2011-01-08
> **bkapps said:**
> No no no...I could get to GRUB, make a selection, and then after that I'd get nothing.  I tried LiveCD's, which booted to selection screens, like Maverick Meerkat where it lets you decide whether to install or to try and then it would just hang there.

I have seemingly the exact same problem w/ an on-board AMD HD4250 and a PCIe 8400GS.

My WAG is that the post-GRUB boot process is getting confused. :(

---

### Post by noob_undo on 2011-01-08
> **cascade9 said:**
> nVida has better closed drivers, and VDPAU (nvidia hardware video decoding). AMD has better open source drivers, but XvBA (ATI/AMD hardware video decoding) is buggy. 'Buggy' might actually be nice as far as XvBA goes, its a mess from what I've seen.

Thankyou, that was another thing I was wondering about - hardware video decoding.
What would be the practical advantage of using open-source drivers? I do plan to be doing some 3D animation as well as high-def playback / encoding, but again, none of it needs to be particularly sophisticated. 

Maybe I should just give up on the fanless part and find a way to have the guts of the computer in another room.

---

### Post by cascade9 on 2011-01-09
> **efflandt said:**
> I have a GT 430 which seemed to be the best Nvidia I could get that did not require > 300 watt psu. It is probably similar to GT 240, but is faster and cooler using less power than the GT 220 I had before, and can do directx 11 (200 series cannot). It idles only 3C over room temperature with a quiet fan. It is new enough that even Natty kernels do not know what model it is, but works fine with nvidia 260 drivers (although, default nouveau drivers before Natty default to low graphics).

GT240 is faster than GT430. Dont just look at the core MHz values- shaders, texture units and render output units have a big impact.....and the GT240 has twice as many shaders and render output units than the GT430. 

I have no idea why jockey isnt finding the it, the 260.19.29 drivers in natty are the 2nd set of drivers supporting the GT430. 

> **noob_undo said:**
> Thankyou, that was another thing I was wondering about - hardware video decoding.
What would be the practical advantage of using open-source drivers? I do plan to be doing some 3D animation as well as high-def playback / encoding, but again, none of it needs to be particularly sophisticated. 

Maybe I should just give up on the fanless part and find a way to have the guts of the computer in another room.

If you're doing HD playback, nvidia is a better choice. 

I'd have a good look at whatever 3D animation software you are planning on using, if it doesnt use the 3D card much (or at all) then adding a 'faster' card will just eat more power and create more heat.

---

### Post by noob_undo on 2011-01-09
> **cascade9 said:**
> 
I'd have a good look at whatever 3D animation software you are planning on using...

Max 5 with Jitter - definitely OpenGL.

Reading about the 220:

[http://www.tomshardware.com/reviews/geforce-gt-220,2445-4.html](http://www.tomshardware.com/reviews/geforce-gt-220,2445-4.html)

Led me to this: [http://preview.tinyurl.com/3y2nu22](http://preview.tinyurl.com/3y2nu22)

And the fps on COD4 isn't half bad at** full **quality, especially for the price:

[http://www.guru3d.com/article/geforce-9500-gt-review/8](http://www.guru3d.com/article/geforce-9500-gt-review/8)

So: Passive heat-sink, low price, pretty good spec, VGA, DVI, HDMI... Seems perfect.

But hasn't this card been around for a while? Could I get the same spec at a lower power consumption if I looked a bit further?

Hardware video encoding would be the dog's proverbials.

---

### Post by cascade9 on 2011-01-09
9500GTs are pretty old, and you can see on the tests you linked that  a GT220 can be faster. 

The GT220 would have a lower power consumption as well. GT240 might be similar to the 9500GT, I cant be sure as most of the 'power consumption' reviews are franky not worth the HTML they are viewed in.... 

I'd seriously go for a GT220 or GT240 over the 9500GT.  A passive GT240 is a fair bit more (70 quid or so), passive GT220 shouldnt be a much more thna 9500GT.

BTW, find good UK prices here- 

[http://www.staticice.co.uk/](http://www.staticice.co.uk/)

---

### Post by gradinaruvasile on 2011-01-15
> **Nutria said:**
> I have seemingly the exact same problem w/ an on-board AMD HD4250 and a PCIe 8400GS.

My WAG is that the post-GRUB boot process is getting confused. :(

Make absolutely sure that the on board card is disabled for good from BIOS.
I have in BIOS (Asus M3N78-VM mobo with integrated nvidia 8200) a setting that leaves both onboards and PCIE cards active and this is a problem when 2 different make cards are in it.
See what options are available to you, select something like init pcie card first if you have that option.

BTW i dont know what you will gain performance wise with the 8400 gs. The 4250 is supposed to have even hardware decoding that can be used from vlc via vaapi (libva).

---

### Post by Nutria on 2011-01-15
It turns out that G82 & G84 cards have some "flaws".

So, I replaced my old G84-based, sitting around for a couple of years 8400GS with a new G98-based 8400GS and all works swimmingly well.

---


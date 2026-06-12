---
title: "Please recommend me a motherboard..."
date: 2010-04-20
forum: Hardware
---

### Post by javyn999 on 2010-04-20
Hey all.  The time has come to build a new box, and am a bit confused these days (I haven't kept up with hardware in years!).

I have been shopping newegg looking for mATX form mobos that would be good to run Ubuntu on.

I've always been an Nvidia kinda guy, but much to my chagrin, every single mATX mobo for socket AM3 (I intend to get one of those Athlon II quad cores) comes with onboard ATI Radeon 4200 video!

What I have now is an Athlon XP2800+ (2.2 ghz)with an Nvidia AGP 4x video card (Geforce 6200 I believe).

Anyway, would the onboard ATI 4200 be comparable to the old AGP Nvidia card I had?

How do the drivers for ATI compare with Nvidia's?  A quick google search really concerned me, because it looks like getting drivers to work correctly for ATI under Ubuntu is a nightmare scenario.

Are there any good mobos that come with integrated Nvidia video, preferably Gigabyte, or even, no onboard video at all?

I'm imagining the integrated ATI isn't worth the hassle.  

If I do end up getting a mobo with integrated ATI, how hard is it to turn that off and use a PCIE video card instead?

Probably stupid questions, but I'm pretty confused here.

---

### Post by Penguin Guy on 2010-04-20
> **javyn999 said:**
> How do the drivers for ATI compare with Nvidia's?  A quick google search really concerned me, because it looks like getting drivers to work correctly for ATI under Ubuntu is a nightmare scenario.
I use an ATI Radeon 3850 and it worked out-of-the-box, although I can't say that it works perfectly. As for the mobo' I use a Gigabyte GA-MA790FXT-UD5P and everything seems to work great. I'm not very experienced at all of this though, so I'd wait for someone else's advice.

---

### Post by javyn999 on 2010-04-20
That Mobo looks great, and no onboard video, cool.  Newegg no longer stocks it though, strange.

Mind explaining what problems you are having with your ATI?

---

### Post by Sk41m4n on 2010-04-20
> **javyn999 said:**
>  
If I do end up getting a mobo with integrated ATI, how hard is it to turn that off and use a PCIE video card instead?


Not hard at all, many motherboards disables the integrated video card automagically when you install an external graphics card. And even if it wouldn't, you should be able to disable the onboard video manually in the BIOS and set it to use the PCI-E card as primary video device.

---

### Post by Objekt on 2010-04-20
I built a system a few months ago to run both Ubuntu 8.04.3 LTS and Windows XP.  All the hardware worked in both OS's.

The board was the ASUS M2N68-AM PLUS.  Link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613&cm_re=nvidia_geforce_7025-_-13-131-613-_-Product]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131613&cm_re=nvidia_geforce_7025-_-13-131-613-_-Product")

You can still buy it at Newegg, and it's cheap.

It has everything you want: 
-supports AM3 processors (I put an Athlon II X2 250 in mine),
 -micro ATX size, 
-built-in Nvidia 3D hardware. 

Also it will boot off USB media.  This is very nice for installing an operating system, as there is no need to burn an install disc.

I don't think there's a big reason to eschew ATI video in favor of Nvidia where Linux is concerned.  ATI's Linux drivers support all their recent cards, and are supposedly just as easy to install in Ubuntu (through the "Hardware Drivers" applet).  

As for using a video card: usually there is no problem disabling the onboard video device in BIOS.  Alternately, you could connect your monitor to the video card and ignore the connector for the onboard video.

You may find that a separate video card is unnecessary.  Recent built-in video devices, like the ATI HD 4200 and Nvidia GeForce 70250, are far more powerful than your old AGP card.  I encourage you to try the onboard video first.  You could save several bucks.

---

### Post by javyn999 on 2010-04-20
Thanks Objekt.  That mobo looks great!  I see that it uses DDR2 memory rather than DDR3, so I figured I'd save even more money taking the G.Skill DDR3 off my wishlist and adding DDR2, but it looks like the DDR3 is just as cheap as 2!

Edit...actually the DDR3 is a bit cheaper, what gives?  If I get the DDR3 it will still be compatible in this mobo, it just won't run at the full speed right?

Edit 2:  

Here is a link to my feeble attempt at a build.  Would you mind critiquing my wish list?

[http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408)

As far as video cards go, I'm not a gamer, but I love the Compiz flair.  Actually I do play a few old first person shooters every once in a while, but they are OLD and surely this onboard video would be able to handle it.  Like Halflife 1, Serious Sam, Morrowind (ok not an FPS but you get the idea).

If I want to play a game, 90% of the time I'm loading up Dosbox lol

---

### Post by Objekt on 2010-04-20
Glad I could help.  DDR2 should be fine.  I built a machine (parts listed in my signature) with DDR3 almost 2 years ago.  In retrospect, I'm not sure it was worth it.  I paid substantially more for both the RAM and the motherboard to use DDR3, but it is really disk access that is the slow part.

I'm not convinced DDR3 is of large benefit to anyone but cutting-edge Windows gamers, who want to build a Core i7-based system with a $500 video card.  DDR3 is required by the i7 architecture.

We have reached a point where you can build a faster PC than most people will ever need for well under $500.

---

### Post by javyn999 on 2010-04-20
Thanks.  I'm still going to go for the DDR3 I decided since it's a few bucks cheaper than the DDR2 of the same brand.

Also, I guess I should say, the point of building this is so my gf can use it as a workstation to edit audio and video.  Sony Vegas, Flash, Green Screen, etc.

I intend to use it to encode video using mencoder in Ubuntu, as well as Avidemux.

I'm assuming the quad core is the way to go for these tasks, although I'd love to save money by just getting a dual core.  Then again I don't want to be so cheap that I end up having to upgrade in 2 years anyway heh.  

So many tough decisions!

I mean, can mencoder, Avidemux, and those Windows editing programs even take advantage of dual/quad core cpus yet?

---

### Post by Yellow Pasque on 2010-04-20
Try again on the mobo. DDR3 and DDR2 are not interchangeable. Also, the Geforce 7025 is pretty antiquated. If it was me, I would get an AMD770 board with Socket AM3 (like [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179) ) and add an nvidia gt220 card.

---

### Post by v1ad on 2010-04-20
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131626)

asus is great for linux also. my current asus mobo even came with linux drivers.

---

### Post by javyn999 on 2010-04-20
Thanks, TEM, I didn't know they were not interchangeable.  Nice mobo, but a full ATX won't fit in my chassis.

v1ad...that one looks really good.  I may go with that.  My wish list has been updated.

Is opting for a quad core going to give me a big boost in tasks like video editing, encoding, and the like?  As opposed to dual core that is.  

I am not interested in gaming, but VERY interested in this doing the best possible job encoding video.  

And, no, I will never buy intel :)

---

### Post by Objekt on 2010-04-20
> **javyn999 said:**
> Edit...actually the DDR3 is a bit cheaper, what gives?  If I get the DDR3 it will still be compatible in this mobo, it just won't run at the full speed right?

No, it won't work at all.  DDR3 RAM has a different pin setup than DDR2.  DDR3 will not physically fit in a DDR2 slot.  That's why you have to buy a motherboard that uses either DDR2 or DDR3.

A little more info: [http://en.wikipedia.org/wiki/Ddr3]("http://en.wikipedia.org/wiki/Ddr3")

> **javyn999 said:**
> Here is a link to my feeble attempt at a build.  Would you mind critiquing my wish list?

[http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408)

Looks fine, but I'm not 100% sure about the Gskill RAM.  It is almost always the cheapest kind.  I've never used it, or known anyone who did, so I can't say it fails more often, but I'd be inclined to spend a few more bucks as "insurance."  Also it has to be DDR2, like I said above.

OCZ is the only brand I have used in my last 2 builds, just because I felt they were the right combination of speed & price.  The two OCZ DDR3 modules I bought two years ago have worked perfectly.  Not saying you have to buy OCZ, just it's the only brand I have actually used recently. 

It used to be that DDR3 always cost more than DDR2.  I guess things have changed, since a lot of people are building Core i7 machines, which require DDR3.  I see what you mean - the cheapest Gskill DDR3 now costs less than the cheapest Gskill DDR2.

The power supply size is a bit of guesswork.  Since you aren't using a separate video card, that drops your power requirement a lot.  630 W should be plenty, even if you decide later to add a video card.  Good on you for not skimping in this area.  The really cheap power supplies, and the ones that are included with cases, are mostly garbage.  The power supply will see constant use as long as you own the system, so there is no reason to go cheap.

Everything else looks fine.  There isn't much difference in price among various DVDRW drives any more.

500 GB should be a plenty big HDD for quite a while.  

Aren't you forgetting a new case?  I suppose you could re-use your existing one, but why not keep the old computer around for guests or as a file server?  You could keep it around as a "hot spare" just in case your new PC gets damaged, or you have to reinstall everything.

> **javyn999 said:**
> 
As far as video cards go, I'm not a gamer, but I love the Compiz flair.  Actually I do play a few old first person shooters every once in a while, but they are OLD and surely this onboard video would be able to handle it.  Like Halflife 1, Serious Sam, Morrowind (ok not an FPS but you get the idea).

If I want to play a game, 90% of the time I'm loading up Dosbox lol

I think you will be pleasantly surprised at the capabilities of the onboard video.  I doubt Compiz or any of those games will give the GeForce 7025 any trouble.  It doesn't sound like you have any need for a separate graphics card.

Glad I could help.

---

### Post by javyn999 on 2010-04-20
Thanks!  Actually, the case I'm going to use houses my gf's current pentium 4 something or other.  Her power supply went out and I was a moron and replaced it with one of those cheapo Rosewoods and it broke her USB controller.  

Well, it didn't 'break' it, I imagine this 250W or whatever power supply just isn't strong enough so her USB devices aren't powering up.  

Anyway, I intend to use her case for this new build, and transfer the p4 motherboard and processor to my Athlon XP2800+ system whose motherboard completely died on me last week.  

I'll salvage what I can from the Athlon XP system, and trash the rest.

I think the onboard video will be just fine honestly.  My coworker thinks I'm a moron for not getting one of those crazy expensive graphics cards, but really, I don't care about Crysis or whatever it is.

I downloaded a torrent with 2800 DOS games whose copyrights have gone abandoned, so I'm set as far as gaming goes hah.

---

### Post by Objekt on 2010-04-20
I have an old system that died, similar to yours.  Power comes on, and the fans run, but it does nothing else.  Not even a beep or an LED flicker.  Probably a dead motherboard.  

I've since repurposed most of the hardware.  There are a few parts I can't re-use, stuff like the CPU and AGP video card.  PM me if you think you can use anything.  I decided it wasn't worth the effort to rebuild the system with a new motherboard, since it was so old, but I haven't thrown away the rest yet.

I looked over the invoice from when I ordered parts for the cheap PC I mentioned.  I used Wintec DDR2 800 MHz RAM (2 x 1 GB sticks).  The pair was $39.99 last December, but Newegg doesn't carry the exact part number (3AXT6400C5-2048K) any longer.  I think it's worth a few extra bucks to get DDR2 1066 MHz RAM.  I mean, why not?  You don't have to overclock, so you might as well get all the performance you can.

I guess Wintec is fine as well as OCZ.  I've heard no complaints in the nearly 4 months the friend's dad has had the machine.  Windows XP and Ubuntu will run quite well with "only" 2 GB, and that amount was plenty for his needs.  However, if you're going to run a quad-core and do video editing, you probably do need 4 GB RAM.  No reason to skimp there.

I agree, you should be fine with the GeForce 7025.  Since it is an integrated video device, it does use system RAM as its video RAM.  This is a bit slower than a separate video card, which has its own, especially fast graphics RAM.  But, I don't think you'll notice the difference.  If you become dissatisfied, you can always get a PCI Express 2.0 16x card.  Perfectly good ones are available for well under $100.

Correction to my original response: I installed Ubuntu 8.04.3 LTS 32-bit on the gift PC, not Ubuntu 9.10.  I used 8.04.3 LTS both because I knew it would be supported for longer than 9.10, and because 9.10 has that annoying freezeup bug that has never been solved (and probably never will).  

I chose 32-bit because a few things are still easier to get working in the 32-bit version of Ubuntu, although support for a 64-bit environment has increased a lot in the last couple of years.

---

### Post by javyn999 on 2010-04-21
[http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=18447408)

I think I'm ready to order.....comments?  Suggestions?

Decided to get DDR3 with lower latency and heatsinks, and spend a little more.

---

### Post by Yellow Pasque on 2010-04-21
Your PSU is out of stock and there's no way you'll need over 500W unless you decide to slap 2 video cards in there. Alternatives ( [http://www.silentpcreview.com/article699-page1.html](http://www.silentpcreview.com/article699-page1.html) ):
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817151094](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151094)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371034](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371034)

---

### Post by Objekt on 2010-04-21
Hey, neat.  That motherboard is basically the one I built on a few months ago, except DDR3-compatible.  

Now that DDR3 is on par with or cheaper than DDR2, there's no reason not to use DDR3 really.

The above point about the power supply is a good one.

There is one more item you should consider: case fans.  

Since you are re-using a very old case, there is a good chance that some or all of the existing fans are nearly worn out.  You might as well replace all of them with new, ball- or fluid-bearing fans.  The additional cost is minimal, and it is less of a headache than having to order them later, as the old fans fail.  I always buy case fans from Newegg, as everyone local wants way too much ($20+ each).

---

### Post by javyn999 on 2010-04-22
Thanks.  Wish list updated, I decided to go for a full ATX Gigabyte mobo with a 700watt PSU (newegg combo deal with a Lite-On DVD writer made it just as cheap as a 500W).

Decided on this because my friend offered to give me his PCIE Geforce 7300 le.  256 meg, DDR2

---

### Post by Objekt on 2010-04-22
Stepping up to SATA 6.0 and USB 3.0 eh?  Not a bad idea, although a lot more money.  You'll be all set when SSD prices drop to a more reasonable level.

Let us know how Ubuntu goes on that rig.  I don't think you'll have any problems getting all your hardware to work.

---

### Post by javyn999 on 2010-04-22
Yeah, the idea is eventually down the line, years and years from now, when I want to upgrade, hopefully find the fastest best processor and hard drive for socket AM3 off craigslist for a few bucks lol.

I look forward to trying Ubuntu 64 bit, Windows 7....dreading that.  But Windows will be a necessary evil since really this is an Adobe CS4(5) box for the gf.

edit:  Also, the SATA 3.0, USB 2.0 Gigabye mobo will cost just as much as the one I have selected currently, after the 10 dollar mail in rebate. :)

---

### Post by cascade9 on 2010-04-22
> **Temüjin said:**
> Your PSU is out of stock and there's no way you'll need over 500W unless you decide to slap 2 video cards in there. Alternatives ( [http://www.silentpcreview.com/article699-page1.html](http://www.silentpcreview.com/article699-page1.html) ):
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16817151094](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151094)
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003](http://www.newegg.com/Product/Product.aspx?Item=N82E16817139003)
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16817371034](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371034)
  
  A large +1. Using megawatt power supplies for systems with 1 (or no) video card just costs you more, both to buy and to run. 
 
 > **Objekt said:**
> Hey, neat.  That motherboard is basically the one I built on a few months ago, except DDR3-compatible.  
 
 Now that DDR3 is on par with or cheaper than DDR2, there's no reason not to use DDR3 really.
 
 
 When it was new, DDr3 wasnt worth it- but even at a small premium (which it isnt anymore) its worth it IMO- just the extra bandwidth going from DDR2 800/1066 to DDR3 1333 is nice, even if its not a huge performance benefit.

> **Objekt said:**
> Stepping up to SATA 6.0 and USB 3.0 eh?  Not a bad idea, although a lot more money.  You'll be all set when SSD prices drop to a more reasonable level.

Let us know how Ubuntu goes on that rig.  I don't think you'll have any problems getting all your hardware to work.

IIRC, when gigabyte released the SATA3/USB3 770s, they were about $10 more than the 'normal' 770s. Not  alot more money. Well, more than if yuo bought a ECS 770 chipset motherboard, but I'd have the gigbyte any day.... 

BTW javyn999- I doubt you would want to do this, but that motherboard has 'ACC' (advanced clock calibration) that lets you unlock cores and cache. You could get a Phenom II X2 and unlock it to a X4. However, there is no way to know for sure if the CPU you get will work like this.

---

### Post by javyn999 on 2010-04-22
Thanks man!  I may keep that in mind for when the lottery core AMDs come out lol.

---

### Post by Objekt on 2010-04-22
> **javyn999 said:**
> I look forward to trying Ubuntu 64 bit, Windows 7....dreading that.  But Windows will be a necessary evil since really this is an Adobe CS4(5) box for the gf.

Adobe CS5 may be one of those Windows apps that doesn't virtualize well, since it's graphics-intensive.  Graphics-intensive software, read "games," is why I still dual-boot Ubuntu & Windows XP.

Windows 7 is nothing to dread, really.  Other than the price, although the student discount price is not bad ($64.95).  Windows 7 is vastly superior to XP in ease of installation & stability.  I think you'll be pleasantly surprised.

---

### Post by javyn999 on 2010-04-22
Ah, I don't plan on virtualizing it.  I'm a dual boot kinda guy.

---

### Post by Objekt on 2010-04-28
So, in the middle of building your box now?

---

### Post by cascade9 on 2010-04-28
> **Objekt said:**
> So, in the middle of building your box now?

If hes lucky, he waited, the release of the Phenom II X6s in the last day to 2 has meant all round price-drops on AMD CPUs.

---

### Post by Objekt on 2010-04-28
> **cascade9 said:**
> If hes lucky, he waited, the release of the Phenom II X6s in the last day to 2 has meant all round price-drops on AMD CPUs.

AMD actually drops their prices on old models when the new kit comes out?  Amazing!  

An Intel Core 2 Duo E8500 is still exactly the same price it was when I built my last machine, in 2008.  Ridiculous.  Intel is the Microsoft of CPUs.  It is one reason I will build with AMD next time around.

---

### Post by javyn999 on 2010-04-28
I have my components but have not started to build yet.  I did order the quad core, I don't care about a hundred, hundred fifty bucks extra for a 6 core lol.

Also the 630 Propus is still 99.00 I see so I have no regrets.

I have not started to build yet though because I googled around a bit on my Gigabyte mobo, and found that I need to purchase a "VRM area" heatsink for it since I'm going to be running a quad core.  

I am waiting on this item before I start to actually build, I'm very excited!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16835708016](http://www.newegg.com/Product/Product.aspx?Item=N82E16835708016)

This items comes VERY highly recommended for any Gigabyte 770x motherboard.

---

### Post by Objekt on 2010-04-28
I'm not sure why you think you need an aftermarket heatsink.  Planning to overclock?

---

### Post by cascade9 on 2010-04-28
> **Objekt said:**
> AMD actually drops their prices on old models when the new kit comes out?  Amazing!  

An Intel Core 2 Duo E8500 is still exactly the same price it was when I built my last machine, in 2008. Ridiculous. Intel is the Microsoft of CPUs. It is one reason I will build with AMD next time around.

Yes. The price on an AMD Phemon II X4 965 (previous dekstop flagship) dropped from about $200 to $180 in a couple of days (at newegg). 

The reason why your E8500 is still the same cost is in part that intel tries not to drop CPU prices (they prefer to bring out new models instead...they have the fabrication plants to do that) but also because that is pretty much the 'top of the line' Core2Duo. They do drop pirces at times (I saw some amazing deals on some of the Core2Quads mid to late last year) but it doesnt happen anywhere near as often as AMD does.


> **javyn999 said:**
> I have not started to build yet though because I googled around a bit on my Gigabyte mobo, and found that I need to purchase a "VRM area" heatsink for it since I'm going to be running a quad core.  

I doubt that. I'd really like to see a link.....I can imagine that you might, just might, need heatsinks for the mosfets for an older 140watt X4 965 (they are all 125watt parts now) or for _serious_ overclocking, but if you need heatsinks for the X4 630 (95watt), you would also need them for a lot of the dual/triple cores (lots of 95watt duals/triples)

Pity the 630 didnt drop in some ways, but I think it might soon. But at least it means you didnt buy at 'just the wrong time' ;)

---

### Post by javyn999 on 2010-05-26
Finally done piecemealing my box together now.  Idle core temp hovers around 31C, GPU temp around 34C.

Comments, criticism?

> Hardware:

CPU:  AMD Athlon II X4 630 Propus 2.8GHz Quad-Core
Mainboard:  GIGABYTE GA-770TA-UD3
Video:  ASUS EN9500GT GeForce 9500 GT 1GB 128-bit DDR2 PCI Express 2.0
Memory:  G.SKILL 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333
HDD:  Western Digital Caviar Blue 500GB 7200 RPM SATA 3.0Gb
DVD:  LITE-ON CD/DVD Burner - Bulk Black SATA Model
PSU:  OCZ ModXStream Pro OCZ700MXSP 700W ATX12V V2.
Chassis:  Antec 300 Black Steel ATX Mid Tower Computer Case
Cooling:  Enzotech MST-88 C1100 MOSFET copper heatsink
Input:  Microsoft Intellimouse, IBM Model M keyboard - DOM 1984, WACOM Graphire 3 tablet
Monitor:  17" LCD

Operating Systems:

Windows 7, 64 bit
Ubuntu 10.04 Lucid Lynx, 64 bit

---


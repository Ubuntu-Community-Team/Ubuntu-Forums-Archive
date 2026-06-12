---
title: "Core 2 Duo motherboard confusion"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by insane_alien on 2007-05-11
Hi, i'm planning a build to supercede my aging PIII machine i'm going to go the core2duo route but i've heard that some motherboards aren't compatible. so can someone suggest a good one to use. i'd also prefer it if it had the capability to handle 8GB of RAM as well as it will be processing extremely large data sets(20GB at the maximum but i don't plan on buying that much RAM :P) it probably won't get all the RAM in one go. it'll be chip by chip as i save up. i'm thinking of getting the E6700 as i heard that one gives the best performance for the price. if you have any suggestions for other things then fire away.

---

### Post by Tanker Bob on 2007-05-11
I just built the system in my tag line.  The MSI P6N SLI Platinum is a great mobo if you have legacy IDE hardware like I do.  The newest Intel mobos don't support IDE in the primary chipsets and can be a pain to set up if you don't have SATA drives.  Even then, getting your CD/DVD/etc. drives working can be a challenge with the companion PATA chip.  You can read about my decision process and the construction/installation effort on my blog.  The P6N proved a breeze to set up, and both Edgy and Feisty supported all its functions on their initial startup.

I bought the E6600 over the E6700 as more cost effective.  I'm overclocking my E6600 to 3.125 GHz, faster than the E6800 Extreme for a fraction of the price.  The E6600 will overclock to the E6700's 2.66 GHz on its head and save you about $700 in the process.  The E6600, E6700, and E6800 are identical chips except for their factory clock rating.  I have a basic blog post on overclocking as well, discussing it from a whole system perspective.  If you spend even a little bit of time on the host of hardware sites, you'll see that the E6600 is by far the most popular C2D CPU.

EDIT: For graphics cards, don't stray from NVIDIA.  They have the best Linux support by far, including a support forum that their support folks actively monitor.  If you intend to run Beryl or Compiz and can afford a GeForce 8800 GTS card, get one.  It flies!  From what I've read on the boards, nothing else comes close for the price.

Others have had successes with the new Intel, Asus, and Gigabyte mobos.  Every one has its quirks, including memory compatibility.  Search the forums and also the customer comments on newegg.com.  I spent hours and hours pouring over all the customer feedback on various boards before making my decision to go with the MSI P6N.  As a result, I encountered no surprises and have no hardware issues.

---

### Post by insane_alien on 2007-05-12
thanks dude it looks perfect. i was thinking of picking up a cheap 7 series GFX card simply because i don't need too much display power. thanks for the tip on the processor as well. i haven't built a machine in a while i thnk i've lost touch.

---

### Post by Tanker Bob on 2007-05-12
You're welcome.  I hadn't build a machine in a few years and had a lot of catching up to do.  If you don't use Beryl or Compiz, you probably don't need the 8800 GTS.  Beryl works smoothly and beautifully with it.

The thing with the E6600 is that you have to use a mobo that solidly supports overclocking.  A good number of other mobos do that, but few others have support for 4 IDE/ATA devices AND flexible overclocking.

---

### Post by z0phi3l on 2007-05-12
Beryl runs nicely on my 7800GS (AGP)

---

### Post by insane_alien on 2007-05-12
i do run beryl occasionally and it works fine on my laptops integrated graphics so my thinking is, i either have really low standards of quality or the beefy graphics cards aren't necessary. the 8800GTS isn't all that much more expensive than the one i was planning so i might just buy it anyway.

Heres what i've got so far, 

Processor: [http://www.ebuyer.com/UK/product/112706](http://www.ebuyer.com/UK/product/112706)
MB: [http://www.ebuyer.com/UK/product/125281](http://www.ebuyer.com/UK/product/125281)
RAM: [http://www.ebuyer.com/product/63623/product_info/rb/27735907967](http://www.ebuyer.com/product/63623/product_info/rb/27735907967)
GFX card: [http://www.ebuyer.com/UK/product/125325/rb/27734362592](http://www.ebuyer.com/UK/product/125325/rb/27734362592)
HDD: my old one, maybe i'll slot in another later but the 750GB i have now is quite happy by itself
DVD: DL-RW salvaged from my old computer.
Cooling: undecided. i want something better than stock but not as humungous as that zalman one bob here has.
PSU:[http://www.ebuyer.com/UK/product/115161/rb/27735583111](http://www.ebuyer.com/UK/product/115161/rb/27735583111) <that should cover it yeah?
Case:[http://www.ebuyer.com/UK/product/124931](http://www.ebuyer.com/UK/product/124931)

and a couple of other things. all in all it totals about £660 which is under my £700 budget :P

that is unless someone suggests a £40 heatsink and fan :P

---

### Post by Tanker Bob on 2007-05-12
I would recommend going with the faster 800 MHz (PC6400) DDR2 SDRAM.  I think that you'll see significant improvement in performance over the 533 MHz and I don't believe the price is all that different.  If you get a small tube of Active Silver 5 thermal compound, you may be able to live with the stock Intel cooler depending on how far you want to overclock.  With the Zalman, I'm getting aboug 31C on the CPU at 3.125 GHz (added .0125v to the core and 6% to the FSB) at idle--well within limits.  You might give it a try, anyway.  Power supply will cover you even with an 8800 GTS.

Note that the 8800 GTS has specific power requirements in amperage on its power cable.  I would guess that a Cool Master PSU would have the correct connector and power setup.

---

### Post by insane_alien on 2007-05-12
oh right, i read a bit on wikipedia about the memory being paired with the processor or something. thats why i went with the slower RAM. i'll go with some 6400 then. and there goes the drinking budget :(

i'm wanting a better cooler than the standard because the room where the computer is can get kinda warm and i am planning on OC'ing to at least e6700 speeds. probably nothing as much as 3.125GHz (unless you can pick up core 2 duos for £50 or something :P)

---

### Post by Tanker Bob on 2007-05-12
LOL...haven't seen 2 C2D's for 50 quid yet, but I'll be watching!

I believe that you'll be OK at 2.66 GHz on the E6600 with Intel's stock heatsink/fan, but I'd definitely go with a dab of Active Silver 5 to transfer the heat off of the CPU.  If your room is too hot, the CPU cooler won't matter because the best it can do is draw the ambient air across the heatsink.  Only a closed-cycle liquid cooling system will bring improvement under that condition.

---

### Post by insane_alien on 2007-05-13
i know how heat transfer works its a big part of my course at uni. i'll probably pick up a cheap(but still a good one) aftermarket cooler anyway. i've had some heat issues with the PIII i'm using now and if i'm overclocking a C2D i want to make sure its going to be cool.

---


---
title: "Building my Own PC (Tips?)"
date: 2008-05-22
forum: Hardware
---

### Post by chris062689 on 2008-05-22
I'm about ready to build my own PC from scratch, I've picked out the following parts:
```

SAMSUNG 20X DVD±R DVD Burner Black IDE Model SH-S202J - OEM
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827151161](http://www.newegg.com/Product/Product.aspx?Item=N82E16827151161)

ASUS TA-851 (generic) Black/ Silver Steel ATX Mid Tower Computer Case 350W Power Supply - Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811173032](http://www.newegg.com/Product/Product.aspx?Item=N82E16811173032)

ASUS M2A-VM AM2 AMD 690G Micro ATX AMD Motherboard - Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131172](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131172)

ECS N8600GT-512DZ GeForce 8600GT 512MB 128-bit GDDR2 PCI Express x16 SLI Supported Video Card - Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814134041](http://www.newegg.com/Product/Product.aspx?Item=N82E16814134041)

Logitech R-10 4 Watts 2.0 Speakers - Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16836121127](http://www.newegg.com/Product/Product.aspx?Item=N82E16836121127)

WINTEC AMPO 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Dual Channel Kit Desktop Memory
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820161677](http://www.newegg.com/Product/Product.aspx?Item=N82E16820161677)

AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Dual-Core Processor Model ADO5000DOBOX - Retail
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103211](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103211)

```
Will all of this hardware work with Ubuntu 8.04? OOTB?
Do you guys suggest any alterations?

---

### Post by nicedude on 2008-05-22
All that looks good and should work with Ubuntu as most desktops will and ASUS is both good and extra Linux friendly. That said please take one word of caution from me that although I am not 100% that AMD processors haven't changed this ( Since due to my experience I have sworn them off ) as I know it they have no thermal shutdown protection and as such if you install the heat sink improperly the CPU will fry in under a second and they wont warranty the CPU in question. I had that happen several years ago while building a box for myself via the heat sink was a large after market one and I didn't get it fully secured but thought I did and it fell off the first day of operation, POOF no more CPU in the blink of an eye and after some googling I found out about this problem ( Apparently no thermal shutdown protection is one of the ways AMD cuts corners compared to Intel ). It was enough to make me mad enough that while that was 4 years ago or so I have not bought another AMD since and wont. I find the socket 775 Intel chip to be mush easier to work with anyway and it has no pins on the CPU as well which means no chance of a bent pin ever.

If AMD has since changed their way of making chips as I said I am unaware but if you do go with this chip please just take care to be extra sure you secure the CPU cooler properly and I would further add a small tube of Artic Silver thermal compound to that newegg cart as it is superior to all the pastes that are included with CPU's and costs $5.99 at newegg.

So in my opinion I would google the problem I describe and see if AMD still builds processors in this way or not.

PS I am awaiting for a newegg order as we speak and you definitely made the right choice there in my opinion.

nicedude

---

### Post by stefangr1 on 2008-05-22
I would advise you to change the motherboard to one with an Intel chipset. I believe Intel chipsets are of slightly higher quality, and they have relatively good open source/linux support.

This system should run Linux just perfect. I would advise you to explain to the shop that you verified that all parts are linux compatible, and ask that you may - if you run in to trouble with certain parts nevertheless - you may return and change these parts.

---

### Post by starcannon on 2008-05-22
I like this board better:

Looked at your case, it can be any atx, so check out this Abit board (I've had great success with Abit myself) Do check to make sure your ram will work with this board, you may need different ram, not sure I didn't check that out.

[ ABIT AN52V AM2+/AM2 NVIDIA nForce 520 MCP ATX AMD Motherboard - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813127035")

I've used Nforce chipsets with linux for several years now, I have been very pleased. GL and most important, have fun building :)

---

### Post by chris062689 on 2008-05-22
I probably forgot to mention that I wanted it under $399.
I don't believe I will be able to build such a thing with the same amount of power with Intel.
Does anyone still know if AMD does not have heat protection (which is one think I think I will be needing if it's my first build.)
[EDIT: I found this fan, would this fit on my case?]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835101009](http://www.newegg.com/Product/Product.aspx?Item=N82E16835101009)
[EDIT2: I thought it showed CPU temperature, but I guess I was wrong, the LCD panel only shows RPMs which is kind of useless]
[EDIT3: I havn't seen anything about AMD not having heat protection.  Still I think I may want to invest in this fan, this is better than the AMD stock fan right?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835101010]](http://www.newegg.com/Product/Product.aspx?Item=N82E16835101010])

---

### Post by chris062689 on 2008-05-22
> **starcannon said:**
> I like this board better:

Looked at your case, it can be any atx, so check out this Abit board (I've had great success with Abit myself) Do check to make sure your ram will work with this board, you may need different ram, not sure I didn't check that out.

[ ABIT AN52V AM2+/AM2 NVIDIA nForce 520 MCP ATX AMD Motherboard - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813127035")

I've used Nforce chipsets with linux for several years now, I have been very pleased. GL and most important, have fun building :)
For the same price, I think I'm going to stay with Asus' brand.
Unless you can give me a better reason :)

---

### Post by chris062689 on 2008-05-22
> **nicedude said:**
> as I know it they have no thermal shutdown protection 

I talked to an AMD "nut" about this and they said they implimented thermal shutdown protection, so I'm safe there.

So all of this hardware works good with Ubuntu?
Can you guys think of anywhere I could bring the price down?
I found some great 2GB RAM for generally the same price, but it was a much higher speed, and it also was under my $399 budget so that's cool.

---

### Post by nicedude on 2008-05-26
I am glad the thermal protection issue has since been solved by AMD. But you should be able to build a Intel based system for no more than what you have selected. The Intel Mobo won't be any more for the same features and your CPU I see is $90 and you can get either a 3.0GHZ single core pentium or 2.4GHZ Pentium dual core for the same or less in the 3.0GHZ single cores case

2.4 GHZ dual core $90
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116070](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116070)

3.0 GHZ single core $80
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116004](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116004)

Both those have the same amount of good customer feedback as the AMD one you list.

I guess I just prefer Intel since AMD zapped me once with their corner  cutting :-(

---

### Post by starcannon on 2008-05-28
> **chris062689 said:**
> For the same price, I think I'm going to stay with Asus' brand.
Unless you can give me a better reason :)

I was reading through the reviews on the Asus board and googled the chipset, looked like some where having linux issues, the Abit board uses Nforce chipset, which I've used lots of over the years without any issues. Abit is a good brand name as well, I like it better than Asus myself, but now days I'm using FX, I don't really care about brand names, I go for quality construction (usually comes down to good capacitors) and linux friendly chipsets.

That said, if your ideal is an Asus based build then go for it, I was just throwing in my 2 cents, and at the end of the day advice is free, your the guy that has the fun (I love building new systems) 

So get what you enjoy, and have a blast :)

---

### Post by yogo on 2008-05-28
I guess since everyone else handles the mobo/chipset etc, I would just add, I would stay clear of a Samsung drive and go with Lite-on, they are cheap also but great quality and I have been using them for years and never, almost never make a coaster no matter what medium I use.

---


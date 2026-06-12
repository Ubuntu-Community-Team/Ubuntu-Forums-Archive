---
title: "Which computer parts are best?"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Sef on 2007-11-03
I'm looking to build my own computer and have a few quotes.   Is there one that is preferred?  I'm just basically using it with no gaming, internet, Word processing, probably gimp, and music mostly.  

_Parts_---------------_ 1_--------------------------------_2_-----------------_3_------------------------------_4_

Motherboard:-Asus (Intel 775)--------Intel 945----------Intel 945------------------ASUS P5VD2-X

CPU:-----------P4 Dual D2140---------Intel E 4500------P4 Dual 2140------------Intel E4500

Power---------350 Watts----------------400 Watts--------None quoted--------------SolarMax 425 Watts
Supply:

DVD-RW:-----None Quoted------------LG-----------------None quoted--------------LG

Questions:

1) Will these work with any DVD-RW and card reader?

2)  Will these work with Compiz Fusion with Compiz Fusion on on-board graphics or will a separate card be needed?

3) Can you use PATA harddrives with these motherboards?

4) Is there anything that I should look for in a case?

5) Is there anything that I missed?

---

### Post by mrvertigo on 2007-11-03
mmm interesting question, give us more info on the onboard graphics cards (I'm too lazy to google all 4 :P)

---

### Post by Sef on 2007-11-04
bump

---

### Post by Paulmd on 2007-11-05
> **Sef said:**
> I'm looking to build my own computer and have a few quotes.   Is there one that is preferred?  I'm just basically using it with no gaming, internet, Word processing, probably gimp, and music mostly.  

_Parts_---------------_ 1_--------------------------------_2_-----------------_3_------------------------------_4_

Motherboard:-Asus (Intel 775)--------Intel 945----------Intel 945------------------ASUS P5VD2-X

CPU:-----------P4 Dual D2140---------Intel E 4500------P4 Dual 2140------------Intel E4500

Power---------350 Watts----------------400 Watts--------None quoted--------------SolarMax 425 Watts
Supply:

DVD-RW:-----None Quoted------------LG-----------------None quoted--------------LG


Questions:

1) Will these work with any DVD-RW and card reader?

Yes.

2)  Will these work with Compiz Fusion with Compiz Fusion on on-board graphics or will a separate card be needed?

Not enough details, in most of these. Only 1 of the list is an actual mothgerboard name. 2 are chipsets, and one is just the socket style. 

The Intel 945 video is decent enough to run compiz. NOT EVERY BOARD WITH AN INTEL 945 CHIPSET HAS INTEGRATED VIDEO.


Intel 775 is just the socket style. This says nothing at all.

ASUS P5VD2-X has no integrated video. So yes, you will need a separate video card to run compiz! 



3) Can you use PATA harddrives with these motherboards?

ASUS P5VD2-X has both pata and sata sockets. The rest are not actually motherboard names, so I cannot tell you.

In any case, if they're sata only, you can get a pci ide controller. Not that you should buy a system without finding out first!

4) Is there anything that I should look for in a case?

Nothing special. Larger cases provide better cooling in general, but that's not a rule. Flashy cases invite thieves, if that's a problem in your area.

5) Is there anything that I missed?

Lots and lots.

Need motherboard names. Need to do more research in general.

---

### Post by Sef on 2007-11-07
I will probably go with number 4.  They did give me all the names of everything, so I googled them and found what I liked.

---

### Post by weblordpepe on 2007-11-07
Ok here is one solid bit of advice:
DO **NOT** BUY **ATi**.

Buy NVIDIA or INTEL.

The ATi drivers are an absolute mess. You will get nowhere with ATi graphics. Go with Intel or nVidia. They both have stable / good drivers that work with games, are fast as Windows, and work with compiz.

---

### Post by Paulmd on 2007-11-08
> **Sef said:**
> I will probably go with number 4.  They did give me all the names of everything, so I googled them and found what I liked.

Good choice. I don't trust a quote unless it has make and model. You know what you're getting, at least.

---

### Post by Ehtetur on 2007-11-08
> **weblordpepe said:**
> DO **NOT** BUY **ATi**.

Buy NVIDIA or INTEL.
I agree about ATI; it was a PITA for me to get it working right..
But when I was searching the forums for help with my ATI card, I noticed lots of posts bypeople having problems configuring their nVidia cards...

So... I'm wondering if the new nVidia cards aren't just as hard to set up as the new ATI/AMD cards.

---

### Post by Paulmd on 2007-11-08
> **Ehtetur said:**
> I agree about ATI; it was a PITA for me to get it working right..
But when I was searching the forums for help with my ATI card, I noticed lots of posts bypeople having problems configuring their nVidia cards...

So... I'm wondering if the new nVidia cards aren't just as hard to set up as the new ATI/AMD cards.


At least with NVidia, you can download the proper drivers from the manufacturer...

---

### Post by Mondoman on 2007-11-08
Definitely get an nVidia-based card.  nVidia 6xxx and 7xxx -based cards with 256MB of RAM onboard can be purchased very cheaply now, for example this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814125071](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125071)
That should let you run all the fancy Compiz visual effects, run Google Earth, and so forth. (I'm doing all that with a $30 6200LE card).

---

### Post by Sef on 2007-11-09
> DO NOT BUY ATi.

Actually, ATI has recently opensourced their drivers, so will wait a bit and then look at getting a better graphics card.  Now I have a NVidia MX4400.

---

### Post by jocko on 2007-11-09
> **Sef said:**
> Actually, ATI has recently opensourced their drivers, so will wait a bit and then look at getting a better graphics card.  Now I have a NVidia MX4400.

They did not open source their driver, they released specifications for one of their cards together with some very basic example code that the open source community can start working with (can't find the reference for this).
As far as I understand an open source driver with working 3d acceleration will take quite some time to develop, so if by "a bit" you mean months (or even years?), then wait.
Otherwise, my advice is to buy something that actually works now.

ATI's closed source driver was recently changed quite a lot, and they introduced some new features that have been missing, but there are still some problems that have been around for years.
If they manage to fix the things that are broken and get the new features (i.e aiglx) working better, maybe their driver will be as good as nvidia's, but that's still a "maybe".
So, if you want something that maybe will be as good as nvidia, then wait and see what ATI manage to come up with in the next few months.

---

### Post by weblordpepe on 2007-11-09
Yeah I have had a nVidia Geforce 7600GT runing perfectly in Ubuntu 6.10 with beryl/compiz.
It was running at 75hz, in perfect sync with my monitor. Nothing like playing Doom 3 on the side of a cube while a movie is on the other side of the cube. That's the kinda thing you can get away with if you use an nVidia card.

Ati is poop.

---

### Post by Sef on 2007-11-17
> Yeah I have had a nVidia Geforce 7600GT

I got an NVidia 8600 GT.  It works great.  

However, I have [NO Sound]("http://ubuntuforums.org/showthread.php?p=3787670").  If you can help me, please go to that thread.

---

### Post by Sef on 2007-11-17
> I have no sound. If you can help me, please to to my NO Sound thread.

Solved. :)  See NO Sound thread for answer. (Post #14 for link.)

---


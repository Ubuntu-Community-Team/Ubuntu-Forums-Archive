---
title: "SATA Drive On PATA Laptop 'Almost' Sucessful"
date: 2011-05-20
forum: Hardware
---

### Post by coljohnhannibalsmith on 2011-05-20
Hello,

I've been tinkering with the idea of trying to get a SATA HDD to work on a PATA Laptop, since about mid 2008; and I've gotten close a couple of times; but never quite hit the jackpot.  I just thought I'd post my experiences and see if any of you might have some comments about any possible work arounds. 

First of all SATA HDDS are cheaper, have higher capacity; and I'm eventually going to want to install the drive on a new system, since mine is due for replacement.  [COLOR=Blue]***The challenege is also kind of cool...***[/COLOR]

The first thing I did was buy a SATA to IDE adapter from **cooldrives.com** for about $20.00.

[http://www.cooldrives.com/index.php/2sahadrtoide.html](http://www.cooldrives.com/index.php/2sahadrtoide.html)

Then I tested it by attaching it to a 2.5" 500GB Western Digital Scorpio-Blue HDD; and attach it and the HDD to my **Apricorn Drivewire Universal Hard Drive Cloning Kit**.

[http://www.apricorn.com/product_detail.php?type=family&id=39](http://www.apricorn.com/product_detail.php?type=family&id=39)

I ***was*** able to clone my PATA HDD onto the SATA HDD using the cooldrive adapter on the Apricorn Adapter's 2.5" PATA interface, verifying that cooldrives' SATA to IDE adapter works.  I was originally warned by the liturature that the cooldrives adapter wouldn't fit in a Laptop, and was designed for POS systems.  I was undetered; but soon realized that they were right; and that the portion of my case that would have to be modified was right next to where the WiFi daughter-board was sitting.  At that point, case modification was out of the question.  So I thought about this for another couple of weeks.

Then I came up with the idea of using a PATA ribbon cable between the female PATA IDE interface on the mobo and the male PATA pins on the cooldrives adapter; with the intention of 'folding' the cable over the bottom of the HDD, once installed, so that ***I would only have to modify the compartment cover.*** [COLOR=Blue]*** This would have been possible.***[/COLOR] So, I started looking at ribbon cables and headers; and finally settled on a "6" 44-Pin Female to Male IDE True Extension" from **cablesonline.com**.

[http://www.cablesonline.com/644fetomaide.html](http://www.cablesonline.com/644fetomaide.html)

So, I added this between the female side of the Apricorn Adapter and the male pins on the cooldrive adapter; and again successfully cloned my PATA drive to the WD SATA drive.

The next thing I did was to attach the crossover-cable to the PATA IDE interface on my Laptop.  The drive didn't even power-up.  I'm guessing that this was because one of the pins that was supplying +5v to the SATA cooldrives adapter while attached to the Apricorn Adapter was 'not' suppling +5v from the PATA IDE interface of my Laptop.

Here I was thinking all the time that these interfaces were universal; when it in fact turns out that they're 'not,'  at least not entirely.  So, it appears that my next challenge is to try and determine which 'pin' was providing the extra voltage.

[COLOR=Blue][B][I]Can anyone hazard a guess as to which 'pin' this might be; and what other limitaions I might be facing???

[/I][/B][COLOR=Black]I'm hoping that ***one day*** I'll be able to say ***"It's Alive"...***[/COLOR]
[/COLOR]
[IMG]http://4.bp.blogspot.com/_An1Q1Ufxbx0/TNli7J0yL5I/AAAAAAAAABQ/wZTf73rGqXI/s1600/256px-Frankenstein%27s_monster_%28Boris_Karloff%29.jpg[/IMG]



**Thanks Hannibal**

---

### Post by kocoman on 2011-07-07
Hi did you make any progress?

---


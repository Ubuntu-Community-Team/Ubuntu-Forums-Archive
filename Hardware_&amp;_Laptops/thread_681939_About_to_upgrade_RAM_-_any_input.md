---
title: "About to upgrade RAM - any input?"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by intense.ego on 2008-01-29
I've created at least one other thread like this, but I am just about to buy some RAM and need make sure my choice is right and that I will have all that is needed.

I am about to buy the RAM from newegg.com and my dad will pick it up when he goes to the US in a week or so. The RAM is a 4gb kit (link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231135](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231135)) and although many people say it is unnecessary for ubuntu, i want to max out my RAM once and for all so that I never have to worry about it any more. Also, buying 4gb at a time will ensure they run dual channel (even though I have heard that it makes minimal difference).

 From a comparison I did with the compatible RAM from crucial (link: [http://www.crucial.com/store/listparts.aspx?model=ThinkPad%20T60%20Series%20%28Type%202008%29](http://www.crucial.com/store/listparts.aspx?model=ThinkPad%20T60%20Series%20%28Type%202008%29)), the RAM from newegg is compatible with my laptop.

I am aware that I will only be able to use 3gb of the 4gb RAM (at least that is what websites like crucial.com say) but like I said earlier, it will allow me to max out the RAM once and for all.

I also plan on buying an anti-static wrist strap (either [http://www.newegg.com/Product/Product.aspx?Item=N82E16899888207](http://www.newegg.com/Product/Product.aspx?Item=N82E16899888207) or [http://www.newegg.com/Product/Product.aspx?Item=N82E16899261005](http://www.newegg.com/Product/Product.aspx?Item=N82E16899261005) , I can't decide). 

What is your input on my choices? Is there anything else I need for installing the RAM?

EDIT: I just found out on the lenovo/ibm website that the model supports 4gb RAM. It seems that the page was created for several models, so it may not be the case. If it does support 4gb, will I have to install 64bit ubuntu? because it is only 32-bit.

---

### Post by oldsoundguy on 2008-01-29
first off .. install your ram at the kitchen table and take off your shoes and sox .. then a wrist strap is not needed as you will be grounded .. also just touching the power supply box while still plugged in and then UNPLUGGING will discharge any static electricity in your body.

BUT, did you read your MANUAL about just how much and what kind of ram you can put in there?

ALSO running sudo gtk-lshw will give you what you have IN the box right now.
If that fails you can do sudo lshw alone and get an on screen listing that will require some reading (and maybe printing)

---

### Post by jpittack on 2008-01-29
32 bit will only see 3 gb, 64 bit will see all 4.  I suggest moving to 64 bit, but research combatibility first.  Flash has no trouble once you use a script that is lingering in the forums somewhere.

When I installed my RAM, I didn't not use an anti-static wrist strap.  I don't suggest this.  Because you are on a laptop, here are some precautions.  Take out the battery.  Unplug the ac.  Press the power button to remove any residing charges. Ground yourself.  Take out old RAM, add new RAM.  Run memtest after putting the laptop back together.

I personally suggest Crucial's RAM.  I find it to be a better quality build, and at the same speeds, will give you better results.  Keep in mind, you will not notice the difference.

4GB is certaintly not too much for Ubuntu.  I have heard of a guy using 18 GB in Ubuntu server.  4GB would be too much for me, because of the applications I use.  I have 2 GB, and thats too much.

Extra RAM can be put to use.  Mount a ram disk and have files or downloads from firefox stored there, to increase privacy, and have the downloads deleted when you shutdown.  Or try booting to ram.  Thats what I am trying to do now.

---

### Post by intense.ego on 2008-01-29
I consulted my manual and I found this bit of text:
```
Note: Due to the limitation of the current 32-bit PC
architecture, actual usable memory size is limited to 3 GB
even though the physical installable memory size is 4 GB in
ThinkPad T60 and T60p computers.

```

---

### Post by oldsoundguy on 2008-01-29
don't blow your money on that unusable ram .. simple and plain.  Until they update the flash on the laptop to support 4 mb.  THEN add it, as most likely it will be cheaper next time around.  (I also like Crucial, but Kingston has a lifetime warranty and I use that a LOT .. 5 computers in this place)

---

### Post by jpittack on 2008-01-29
Good news.  You can enjoy all 4 GB.  If you plan on having your laptop for a long time, 4GB will serve you well.  It will draw more power and create more heat, as it is more dense.  From 1 GB to 2, I could feel the heat difference, but not the power difference.

---

### Post by intense.ego on 2008-01-29
> **oldsoundguy said:**
> 
ALSO running sudo gtk-lshw will give you what you have IN the box right now.
If that fails you can do sudo lshw alone and get an on screen listing that will require some reading (and maybe printing)

The command didn't work for me, but I can tell you that I have 512mb of RAM currently installed. 

@jpittack: My laptop doesn't normally run hot, but could adding some ram make that significant of a difference? Wouldn't it simply run at a slower, less hot speed until it needs to step up a level?

---

### Post by intense.ego on 2008-01-29
With regards to the chance of an overheating problem, what is your opinion of laptop coolers? Know of any good ones?

---

### Post by oldsoundguy on 2008-01-29
the lshw program may have to be installed.

I find it indispensable when making modifications to see IF they are seen!

But NOT a laptop user .. most of the stuff is just too proprietary for one thing, and for another, the majority of laptops are designed for women and kids with small hands.  As a touch typist with very large hands, I have to have a full sized keyboard AT LEAST and prefer an ergonomic.

---

### Post by jpittack on 2008-01-29
Overheating will not be an issue.  Its just something I noticed.  For 15.4 screens and less, targus.  Larger screens needs research.  Under 12", don't bother.

I did you use the targus cooler (don't buy for more then $20).  The wire next to the on/off switch is in half.  I need to soder it back together.  If you use that, there is no heat to the touch.  Great for home use.  Decreases battery life, but not noticable.

The density is what makes it hotter, not the speeds.  It should step down in speeds.

As for laptop designs.  Dell's 13.3 is a full size keyboard.

---

### Post by oldsoundguy on 2008-01-29
thanks for the tip on the Dell .. the HP media has a standard 103 keyboard also .. but I REALLY do NOT need a laptop what with 2 XP boxes and 3 Gutsy boxes and a Win2003 PDA with folding keyboard already here up and running! LOL

---

### Post by Yellow Pasque on 2008-01-29
Side note: To see memory usage:
```
free -m
```

---

### Post by intense.ego on 2008-01-30
anyone else have something to say?

---

### Post by jpittack on 2008-01-30
DDR2 ram will go up in price after it stops being produced, much like DDR is now.

---

### Post by intense.ego on 2008-01-30
That won't happen any time soon, I assume, but thanks for letting me know. Just to confirm, from the information I provided, would it be safe to assume that 4gb of ram would work (despite that the fact that my cpu is only 32bit)?

---

### Post by intense.ego on 2008-01-31
Bad news for me, newegg doesn't accept a shipping address different than the billing address of your credit card, so I can't get the ram there. There doesn't seem to be any deals here in the uk that can even compare. Should I just get a 2gb stick? Will it be a problem if one stick is so much larger than the other (in terms of capacity)?

---

### Post by intense.ego on 2008-01-31
I found these two deals and was wondering which one would be better value for money. First one is 2gb ([http://www.play.com/PC/PCs/4-/3497002/Kingston-KTA-MB667-2G-2GB-DDR2-SODIMM-Upgrade-For-Apple-iMac-MacBook/Product.html](http://www.play.com/PC/PCs/4-/3497002/Kingston-KTA-MB667-2G-2GB-DDR2-SODIMM-Upgrade-For-Apple-iMac-MacBook/Product.html)) and comes with free shipping. The second is 4gb ([http://www.dabs.com/ProductView.aspx?Quicklinx=4QB2&CategorySelectedId=11150&PageMode=1&NavigationKey=11150,48820000&InMerch=1](http://www.dabs.com/ProductView.aspx?Quicklinx=4QB2&CategorySelectedId=11150&PageMode=1&NavigationKey=11150,48820000&InMerch=1)). 

Also, just out of curiosity, why is is that most ram I look at for my laptop is 1.8V, but this ([http://www.novatech.co.uk/novatech/specpage.html?NBM-67%2F2GB](http://www.novatech.co.uk/novatech/specpage.html?NBM-67%2F2GB)) is 3.3V? Is it better or worse in any way?

---

### Post by Yellow Pasque on 2008-01-31
3.3V DDR2? Either it's a special kind of RAM that you won't be able to use or they listed the Voltage incorrectly (I suspect the latter). 3.3 Volts would fry normal DDR2 modules.

---

### Post by intense.ego on 2008-01-31
but what do you think of the deals i found?

To all the people in the UK: don't you just hate how the prices here are often more than double those from the US?

---

### Post by intense.ego on 2008-02-01
bump, anyone?

---

### Post by intense.ego on 2008-02-02
bump

---

### Post by intense.ego on 2008-02-02
bump. any advice would be appreciated.

---

### Post by SunnyRabbiera on 2008-02-02
well there is a brand I can suggest at least, if possible get a kingston as they are reliable and evenly priced.

---

### Post by intense.ego on 2008-02-02
I have heard good things about kingston and, because the price is the same as that on newegg, I won't feel too bad about missing out on a deal. Would the fact that one slot has 512mb and the other has 2gb make a difference? Also, in the future, if i was to buy another 2gb stick from a different manufacturer, would that be a problem?

---

### Post by Yellow Pasque on 2008-02-02
> Would the fact that one slot has 512mb and the other has 2gb make a difference?
Theoretically, no, but mobos have been known to be picky...

My recommendation would be to decide how much memory you want for the lilfe of the system now (i.e. just run two 1GB sticks, or if you plan on keeping this system a long time and/or running Vista, get a 4GB kit now). DDR2 isn't going to get any cheaper, so get it now. [http://www.techreport.com/discussions.x/13992](http://www.techreport.com/discussions.x/13992)

As for the 512MB stick, I would sell that to some poor soul trying to run Windows on a 512MB stick.

---

### Post by intense.ego on 2008-02-03
So, two of the kingston sticks or the crucial 4gb kit?

---

### Post by Yellow Pasque on 2008-02-03
> i.e. just run two 1GB sticks, or if you plan on keeping this system a long time and/or running Vista, get a 4GB kit now
I'll stand by this advice.

---

### Post by intense.ego on 2008-02-03
I'm not sure you understand my question. Would it be better to get two seperate 2gb sticks or buy a 4gb kit. I heard that often buying two seperate sticks does not allow for dual channel because they could be made by different manufacturers.

---

### Post by ljonesj on 2008-02-03
actually 32bit os can use 4gb of ram 64bit i think is 32gb of ram. its the bios that limits u or the os can limit u as the case of the eeepc its stock os only sees 1gb were bios sees 2gb if you put in that much

---

### Post by intense.ego on 2008-02-03
thanks for the info ljonesj. Do you think getting two seperate 2gb sticks would be better or a 4gb kit?

---

### Post by intense.ego on 2008-02-04
*bump* anyone?

---

### Post by ljonesj on 2008-02-04
i would get what u can afford and what is the best bang for the buck
actually i am wrong on the ram part 4 gb i think is winxp home limit and 32gb for pro and for 64 is between 32gb and 2tb not exact sure on that

---

### Post by intense.ego on 2008-02-13
*UPDATE* I'm now deciding between 27.75 quid for a 2gb stick or 53.50 for 2x2gb. Both are Corsair ValueRam and the prices I gave include delivery. What do you think?

---


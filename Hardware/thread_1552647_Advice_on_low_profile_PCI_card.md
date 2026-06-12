---
title: "Advice on low profile PCI card"
date: 2010-08-13
forum: Hardware
---

### Post by Viperman0986 on 2010-08-13
Hello All,

I am trying to improve flash performance on Ubuntu 10.04 that is currently using integrated graphics.  I need to be able to run pbskids.org smoothly so the kids dont get frustrated with the choppiness.  My cpu is a low end intel celeron D 325 processor @ 2.5ghz so I'm not sure if a low-profile gpu would even help?  I have maxed out @ 2gb of ram as well.  I was thinking about something like this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814139150](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139150)

Again, my worry is that the card will not help at all with such a low powered CPU.

Thanks for any advice!

---

### Post by earthpigg on 2010-08-13
i googled for "gpu flash linux"

there where lots of big stories in 2008 about how the then-new version of flash supported gpu acceleration in linux. the qualification seemed to be that this was only true if the user was *not using compiz*.

adding '2010' to the google search string returned [this]("http://www.anandtech.com/show/2876"):

> Adobe has just released a preview of Flash 10.1 (the final version is due out next year) for Windows, OS X and Linux. While all three platforms feature performance enhancements, the Windows version gets H.264 decode acceleration for flash video using DXVA (OS X and Linux are out of luck there for now).

im afriad that the best answer i can give you is "i doubt it".


i have a rather powerful video card, but when i watch flash.... it's still my CPU that is doing the work.

you have compiz off, right?

---

### Post by Viperman0986 on 2010-08-14
> **earthpigg said:**
> i googled for "gpu flash linux"

there where lots of big stories in 2008 about how the then-new version of flash supported gpu acceleration in linux. the qualification seemed to be that this was only true if the user was *not using compiz*.

adding '2010' to the google search string returned [this]("http://www.anandtech.com/show/2876"):



im afriad that the best answer i can give you is "i doubt it".


i have a rather powerful video card, but when i watch flash.... it's still my CPU that is doing the work.

you have compiz off, right?


Hello earthpigg,

Im pretty sure I have compiz off.  If by compiz, you mean did I disable all of the desktop visual effects (System>Preferences>Appearance>Visual Effects tab)?  Srry, I'm still figuring out the ubuntu lingo.

It's unfortunate that Adobe hasnt added gpu acceleration in linux yet.  I read that just last week they released a flash version that uses gpu acceleration for Mac's.  

Thanks for the info, I guess I'll just wait a bit and upgrade the desktop with something from [http://www.system76.com/](http://www.system76.com/) or wait for the second generation Dell Zino to be released.  [http://www.engadget.com/2010/07/31/dell-zino-hd-410-quietly-leaks-out-with-amd-quad-core-potential/](http://www.engadget.com/2010/07/31/dell-zino-hd-410-quietly-leaks-out-with-amd-quad-core-potential/)

Any thoughts on either brand/model?  I liked the nettop that system76 has but since ubuntu might not take advantage of the Ion chipset the atom processor worries me.  The dell zino has a much more robust cpu selection.

---

### Post by Viperman0986 on 2010-08-14
I forgot to mention that the my main reasoning behind these 2 computers is power efficiency...I believe both computers use less than 100W Power Supplies?

---

### Post by mastablasta on 2010-08-14
if you are lokoing for low power supply then a notebook might be for you.

BTW - i have a new Celeron 2.5Ghz, 256MB old radeon 9200 card and 1.3MB ram. flash runs normally now. i only got a Celeron, because they didn't have AMD card...

it also ran normally on 9.10 with very old 16MB card and underclocked processor AMD 833Mhz. After i put in a new card it became choppy. upgrade to 10.04 didn't help, so i decided to get a new processor (cheapest out there) and do some part salvaging. 

i think it works ok now. 

with a built in graphics card the main processor is doing the graphics as well as any other calculations etc. i am not sure but maybe it could help to get at least some load of the processor with a graphics card... well i am just following the logic here. main processor won't be taking care of picture anymore.

---

### Post by Viperman0986 on 2010-08-14
> **mastablasta said:**
> if you are lokoing for low power supply then a notebook might be for you.

BTW - i have a new Celeron 2.5Ghz, 256MB old radeon 9200 card and 1.3MB ram. flash runs normally now. i only got a Celeron, because they didn't have AMD card...

it also ran normally on 9.10 with very old 16MB card and underclocked processor AMD 833Mhz. After i put in a new card it became choppy. upgrade to 10.04 didn't help, so i decided to get a new processor (cheapest out there) and do some part salvaging. 

i think it works ok now. 

with a built in graphics card the main processor is doing the graphics as well as any other calculations etc. i am not sure but maybe it could help to get at least some load of the processor with a graphics card... well i am just following the logic here. main processor won't be taking care of picture anymore.


alright thanks for your input, ill consider it when purchasing a new gpu!

---


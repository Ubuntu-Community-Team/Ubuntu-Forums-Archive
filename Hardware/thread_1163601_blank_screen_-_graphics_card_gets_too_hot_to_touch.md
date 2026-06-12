---
title: "blank screen - graphics card gets too hot to touch"
date: 2009-05-18
forum: Hardware
---

### Post by angelsneverdie on 2009-05-18
Hello everyone.  My wife went to use the desktop today and couldn't get anything to appear on the screen, although she could hear that the computer was on.  So she called me up and I had the same issue, so I manually restarted the computer.  It booted normally except for what I saw on the screen was all jumbled - graphics were not right.  So i shut it down and took out the graphics card which was very hot.  the fan on the card had a lot of dust in it so i vacuumed it out.  I replaced the card and made sure all of the connections were secure and now when i turn on the computer the monitor wakes up and turns on but nothing appears on the screen.  the computer doesn't beep or anything.  

I've noticed that within seconds of turning on the computer the graphics card gets too hot to touch . . . 

anyone have any theories?  This is a machine I built myself several years ago, so i have no idea what the specs are - that will take some researching.

---

### Post by Dark_Stang on 2009-05-18
Well, it sounds like your video card was overheating and that's what caused the screen to go blank but the computer to keep running. Now it sounds like you're not getting any video at all. 
Maybe not enough power for the new card? 
Maybe a bad card?

---

### Post by JackH79 on 2009-05-18
I'd say you're probably having trouble with that fan. Check if its working properly. If it isn't, check if it uses a separate power lead from your psu and whether that's become lose.
Else I'd say your card's probably had it. Get a new one.

---

### Post by angelsneverdie on 2009-05-19
> **Dark_Stang said:**
> Well, it sounds like your video card was overheating and that's what caused the screen to go blank but the computer to keep running. Now it sounds like you're not getting any video at all. 
Maybe not enough power for the new card? 
Maybe a bad card?

It's not a new card - it is the same one that has been in there since the begining.  So I don't know why it would have started to act up now.

The only things i've replaced on the computer since i built it is the ram and the power supply (maybe two years ago - been working fine since then)

the fan on the card seems to draw it's power from the card itself . . . i'll check when i get home to see if I can hook it up to any other source.

---

### Post by angelsneverdie on 2009-05-19
also, here is the card that is currently in the computer:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814164017](http://www.newegg.com/Product/Product.aspx?Item=N82E16814164017)

would it be worth to try and replace it with something like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150345](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150345)

So many questions . . . as long as I have to get a new video card (if indeed that is what I need to do)  I need to make sure i get one that is compatible with ubuntu (since i'm not yet a technical wizard) and I need to get one that will be able to handle all of the compbiz stuff no problem, as my wife has very poor vision and uses the magnifier etc.  any suggestions?

---

### Post by Dark_Stang on 2009-05-19
> **angelsneverdie said:**
> I replaced the card and made sure all of the connections were secure and now when i turn on the computer the monitor wakes up and turns on but nothing appears on the screen.
I read that as, you replaced the card with a different one. If you have the same card in there it sounds like your card is simply overheating and not displaying video because of it. If you're under warranty I'd say swap it out. If not, I'd just get a new one.

---

### Post by angelsneverdie on 2009-05-19
> **Dark_Stang said:**
> I read that as, you replaced the card with a different one. If you have the same card in there it sounds like your card is simply overheating and not displaying video because of it. If you're under warranty I'd say swap it out. If not, I'd just get a new one.

I was afraid you would say that.  Are you sure there aren't any magical words i could say to make it just work again?

---

### Post by Dark_Stang on 2009-05-19
> **angelsneverdie said:**
> I was afraid you would say that.  Are you sure there aren't any magical words i could say to make it just work again?
Well without me playing with the computer I'm not 100% for sure that the video card is overheating. But it sounds like it is. You could try to remove the heatsink from the GPU, clean it off, and re-seat it with new thermal paste. 

Note: If your going to do this please remember to use as little thermal paste as possible. Just enough to cover the area where the heatsink comes into contact with the GPU.

---

### Post by angelsneverdie on 2009-05-19
Just from touching it, nothing seems to get very hot except the video card.  I'm going to try to replace it with the one i mentioned above (slightly better card for only $30).  I'll let you know if that works.  If it doesn't, I might just buy a barebones and start from scratch seeing as though i built this one in 2005 which now seems like forever ago.  

thanks for your help

---

### Post by coffeecat on 2009-05-19
> **angelsneverdie said:**
> also, here is the card that is currently in the computer:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814164017](http://www.newegg.com/Product/Product.aspx?Item=N82E16814164017)

would it be worth to try and replace it with something like this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150345](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150345)

So many questions . . . as long as I have to get a new video card (if indeed that is what I need to do)  I need to make sure i get one that is compatible with ubuntu (since i'm not yet a technical wizard) and I need to get one that will be able to handle all of the compbiz stuff no problem, as my wife has very poor vision and uses the magnifier etc.  any suggestions?

That replacement card will be fine with Ubuntu. It's got the nvidia GeForce 7200GS chipset which is more compiz capable than the old FX5500 one. Another advantage is that it's passively cooled (if NewEgg have posted an accurate picture - beware, some suppliers over here in the UK are careless with their pictures) which means quieter and no fan to get clogged up. Indeed I'm wondering if the dust stopped the fan from working properly which caused the GPU to overheat, which in turn has caused it to fail.

Since you're running compiz, you'll have the propretary Linux nvidia driver installed, but you may have an older version of this for what is now an old card. This may or may not be OK with the newer 7200GS card. If, after you've fitted the new card, the system boots up OK, simply go into System > Adminstration > Hardware Drivers and see if it wants to install a newer version of the driver. But if, when you boot up, the graphics server fails, reboot into recovery mode and run xfix. Now when you reboot again, you'll be using the open source nv driver and compiz will be disabled. So, now simply go to Hardware Drivers and install whichever verison of the proprietary driver it recommends and you will be able to re-enable compiz.

---

### Post by angelsneverdie on 2009-05-19
> **coffeecat said:**
> That replacement card will be fine with Ubuntu. It's got the nvidia GeForce 7200GS chipset which is more compiz capable than the old FX5500 one. Another advantage is that it's passively cooled (if NewEgg have posted an accurate picture - beware, some suppliers over here in the UK are careless with their pictures) which means quieter and no fan to get clogged up. Indeed I'm wondering if the dust stopped the fan from working properly which caused the GPU to overheat, which in turn has caused it to fail.

Since you're running compiz, you'll have the propretary Linux nvidia driver installed, but you may have an older version of this for what is now an old card. This may or may not be OK with the newer 7200GS card. If, after you've fitted the new card, the system boots up OK, simply go into System > Adminstration > Hardware Drivers and see if it wants to install a newer version of the driver. But if, when you boot up, the graphics server fails, reboot into recovery mode and run xfix. Now when you reboot again, you'll be using the open source nv driver and compiz will be disabled. So, now simply go to Hardware Drivers and install whichever verison of the proprietary driver it recommends and you will be able to re-enable compiz.

Wow, thanks for the info - I feel better about going into this now.  Hopefully everything will go smoothly, but I'll post back here.  I'm ordering the new card tonight.

---

### Post by angelsneverdie on 2009-05-19
> **coffeecat said:**
> That replacement card will be fine with Ubuntu. It's got the nvidia GeForce 7200GS chipset which is more compiz capable than the old FX5500 one. Another advantage is that it's passively cooled (if NewEgg have posted an accurate picture - beware, some suppliers over here in the UK are careless with their pictures) which means quieter and no fan to get clogged up. Indeed I'm wondering if the dust stopped the fan from working properly which caused the GPU to overheat, which in turn has caused it to fail.

Since you're running compiz, you'll have the propretary Linux nvidia driver installed, but you may have an older version of this for what is now an old card. This may or may not be OK with the newer 7200GS card. If, after you've fitted the new card, the system boots up OK, simply go into System > Adminstration > Hardware Drivers and see if it wants to install a newer version of the driver. But if, when you boot up, the graphics server fails, reboot into recovery mode and run xfix. Now when you reboot again, you'll be using the open source nv driver and compiz will be disabled. So, now simply go to Hardware Drivers and install whichever verison of the proprietary driver it recommends and you will be able to re-enable compiz.

One question before I order though is will I have any difficulties since i'm switching from agp to pci?

---

### Post by Dark_Stang on 2009-05-19
> **angelsneverdie said:**
> One question before I order though is will I have any difficulties since i'm switching from agp to pci?
Your computer won't care. But PCI is slower than AGP.

---

### Post by coffeecat on 2009-05-20
> **angelsneverdie said:**
> One question before I order though is will I have any difficulties since i'm switching from agp to pci?

Sorry - I missed that bit. You've chosen a PCIe card, not a PCI, and that won't do at all. Explanation - Older motherboards have AGP slots for graphics, newer ones PCIe. (And some even older ones, only PCI.) I very much doubt you'll have a PCIe slot - I've never heard of them co- existing.

I suggest you go back to that NewEgg site and see if you can get the same chipset card but with AGP. Go into their AGP section (if that's how they arrange things) and look for something in the GeForce 7*** range.

**Edit:** OK, I've had a quick look for you. [Here's their nVIDIA AGP page]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201069609639%201305520548&name=NVIDIA"). Inevitably, everything is more expensive. Older technology always is for some reason - probably volume of sales. There are no 7*** series cards, but there seem to be three possibilities. There's a Sparkle (never heard of them) card with the same 5500 chipset for $35, a PNY 6200 for $41 and a Gigabyte 6200 for $39. If I was buying, I'd go for the Gigabyte. The 6200 chipset isn't as fast as the 7200GS one, but I recently set up someone with Jaunty and a 6200 AGP card and compiz worked a treat.

By the way, be very cautious with the information on that site. It's as careless as some of the UK equivalents I mentioned. If you scroll down that page about halfway, you'll find a Gigabyte Radeon card for $95 with a chipset made by nvidia - apparently. I'm sure noth nvidia and ati would be startled by that assertion. I realise you probably won't want to spend $95, but don't get a radeon card. Even one made by nvidia! :roll: :wink:

**Final thought:** of course, make sure that the old card is an AGP one before buying. If you misidentified the old one and it is a PCIe then the replacement you chose will be fine. The motherboard manual should tell you what the slot is, and most cards have a little label saying whether they're AGP or PCIe.

---

### Post by angelsneverdie on 2009-05-20
ahhh i didn't even know PCIe existed.  I guess i'll be sending it back and getting the gigabyte one like you suggested.  thanks for catching that, you're a lifesaver.

---

### Post by coffeecat on 2009-05-21
Out of curiosity I went back to the NewEgg page to make sure I hadn't missed anything else, and I had, but this time I hope it's only a minor thing. The reason I mentioned the Gigabyte in particular is not because it was marginally cheaper, but because it's probably a better make. I've certainly had some problems with PNY products, but that may have been my bad luck.

Anyway, the thing I missed is that the Gigabyte seems only to have a DVI output - which is most unexpected. (The PNY has both DVI and VGA, which is more usual.) But if you click on the image it shows a picture of the pack contents which includes a DVI to VGA converter, so you should be OK. You're almost certain to be using VGA at the moment, but if the monitor has DVI input you'll get a better image with DVI.

Ho hum. I hope it all works out. All these details - bewildering. :confused:

---

### Post by angelsneverdie on 2009-06-01
I just put the gigabyte card in this evening and voila!  Video!  I find that having a working video card is integral to the whole desktop computing experience.  thanks to everyone who helped me!!!

---


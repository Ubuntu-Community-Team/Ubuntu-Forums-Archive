---
title: "New Computer - Are these parts good?"
date: 2008-11-26
forum: Hardware
---

### Post by Genius314 on 2008-11-26
[COLOR="Red"]UPDATE: See my latest post for the possibly final list of parts.[/COLOR]

I'm building a new PC (the first upgrade I've done in about 5 years...)
I'm keeping a few of the old parts, and will probably replace them later on.


Motherboard: GIGABYTE GA-EP45-UD3R

CPU: Intel Core 2 Duo E8500 Wolfdale 3.16GHz

Video Card: BFG Tech BFGE88512GTSE, GeForce 8800GTS 512 MB

RAM: Kingston HyperX 2GB (2 x 1GB), 240-pin DDR2 1066

DVD/CD Drive: LG GH20NS15 (I read in a review that someone couldn't boot from this on a Gigabyte board... This is my main concern, although I have a few ATA drives lying around, just in case)

Hard Drive 1: WD Caviar Black WD5001AALS 500GB SATA

Hard Drive 2: Maxtor 500GB ATA/100 (already own this... I'll probably use it as backup)

PSU: Antec 500W (no idea the model, I already own it. But if I should replace it, I will)

HSF: Dynatron P985 92mm (The best model that I could find that isn't held down with those tabs, which are supposedly annoying. I don't own this yet.)

Thermal Compound: Arctic Silver 5


I also have a Wacom Graphire 3 tablet, a Logitech Wave keyboard, and a Belkin wireless card. I'd assume these will work with any setup, since they're all USB.
My monitor is a MAG Innovision 17" CRT... I know it's obscure, and outdated, but I got it for $25, and it works fine. This should probably work with any card that has a DVI output, right?

I'm keeping the case. It's a mid-tower case (16" x 8" x 19"), so it should fit the motherboard.

So how good would this setup be? I don't play many games (other than emulators), but I do use 3D software like Blender and Compiz-Fusion, and might play around with programming OpenGL. I want to make sure that all of this hardware is going to work with Ubuntu, and that these programs will work well with the new hardware. (EDIT: I reworded the last sentence.)

Also, I'm buying all of this on NewEgg. They seem to have decent deals on everything, plus free shipping for a lot of them.

Any help or comments are appreciated. :)

---

### Post by ispyamoose on 2008-11-27
Everything looks good to me. I would suggest increasing the ram to 4 gb if possible, as it will increase the effectiveness of your upgrade. I would also suggest that you consider a Seagate hard drive or a WD Raptor (36 GB) drive instead of a standard 500 GB WD. You would be experiencing blazing speeds if you installed Ubuntu on the Raptor 10K, and used the other hard drive (500 GB, etc) for data.

I am a big fan of Blender myself, and it works perfectly with Ubuntu. Just check Add/Remove Programs and search for Blender. Just make sure "Show" is set to "All available applications."

As for Compiz Fusion, I use that as well. It works perfectly. Just open Synaptic Package Manager and search for Compiz. Make sure you have desktop effects enabled in Appearance settings, as well as the latest proprietary video driver.

As for your USB devices, they should work just fine I believe. The only trouble I've had with a USB device is with my Microsoft Lifechat headset (doesn't work, but will probably work eventually).

---

### Post by coastdweller on 2008-11-27
The drawback in ordering a board online is not being able to test the speed of the board before purchased.

We've built thousands of machines and an interesting pattern has cropped up.

Some boards are so wickedly fast it's very close to paying 2 to 300 more for a higher end cpu.

The ASUS p5q-e is one that's exhibiting this (We build many a week and have for over 16 years).

Oddly the lower-end p5kpl-cm showed this as well. A 90 dollar board running like a little quad core with a e2180 lol

---

### Post by tommcd on 2008-11-27
Install Intrepid instead of Hardy, since the newer kernel in Intrepid will have better support for the Intel P45 chipset with the ICH10 southbridge. Here is a review if the Gigabyte EP45-DS3L which is probably similar to your board. 
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_p45_mobos&num=1)
According to the article you need at least kernel 2.6.26+ for the sata controller to be detected. Intrepid has 2.6.27-7 so you should be good.
BTW, phoronix.com is a great site to check for linux hardware reviews.

---

### Post by Genius314 on 2008-11-27
> **ispyamoose said:**
> Everything looks good to me. I would suggest increasing the ram to 4 gb if possible, as it will increase the effectiveness of your upgrade. I would also suggest that you consider a Seagate hard drive or a WD Raptor (36 GB) drive instead of a standard 500 GB WD. You would be experiencing blazing speeds if you installed Ubuntu on the Raptor 10K, and used the other hard drive (500 GB, etc) for data.

I can always upgrade RAM in the future, which I probably will at some point. I probably could get 4 GB, but I don't think I would need it. Right now I only have 768 MB, and I hardly ever use more than 75% of that. So 2GB is plenty for now.

Are all the Seagate drives faster than the WD drive I picked, or is there a particular model that you're referring to? Newegg doesn't seem to sell any Seagate SATA drives with a faster RPM, but I can't imagine switching to a different 7200 would make much of a difference.
As for the WD Raptor, it's a little out of my price range. I'd also rather have a 500GB drive, to match the one I have.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148301](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148301)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148288](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148288)
Unless the similar Seagate models (like the two above) are actually better than the WD one that I've chosen, I probably won't switch.

EDIT: Also, I know those programs work in Ubuntu (I use them now in 8.10). I should have worded it better. I was actually wondering if those programs would work well with the *hardware* that I've chosen, and that the hardware will work in Ubuntu.

> Some boards are so wickedly fast it's very close to paying 2 to 300 more for a higher end cpu.

The ASUS p5q-e is one that's exhibiting this (We build many a week and have for over 16 years).

Oddly the lower-end p5kpl-cm showed this as well. A 90 dollar board running like a little quad core with a e2180 lol 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296)
This is the P5Q-E that you're talking about, right? (I know it's probably a stupid question, but I just want to be sure :)) It's about $40 more than what I was going to pay with the Gigabyte board, but if it's really as fast as you say, it might be worth it.
Plus, I've used Asus boards before, and they seem to work fine (I only chose GB because they had a lot of good reviews).

I don't want to get the P5KPL-CM, because it doesn't have the same features.

> Install Intrepid instead of Hardy, since the newer kernel in Intrepid will have better support for the Intel P45 chipset with the ICH10 southbridge. Here is a review if the Gigabyte EP45-DS3L which is probably similar to your board.
[http://www.phoronix.com/scan.php?pag...45_mobos&num=1](http://www.phoronix.com/scan.php?pag...45_mobos&num=1)
According to the article you need at least kernel 2.6.26+ for the sata controller to be detected. Intrepid has 2.6.27-7 so you should be good.
BTW, phoronix.com is a great site to check for linux hardware reviews.

I'm already using Intrepid, so that's not a problem.

Thanks for all the help so far. :)

---

### Post by coastdweller on 2008-11-27
Yep, that's the board. I went through the newegg reviews and pretty much know that any issues are already fixed (In fact yesterday I fixed the issue with the underperforming IDE, which is window's updates...

If you bring the OS up to date, remove the IDE devices and let them be found again its all good.

We've built quite a few mid level gaming system with this board and so far we're impressed with the speed.

Even the newegg reviewers actually mention it!

In the shop we say it's overclocking itself :lolflag:

---

### Post by Cracauer on 2008-11-27
Overall great. If you look for nitpicking:

> **Genius314 said:**
> I'm building a new PC (the first upgrade I've done in about 5 years...)
I'm keeping a few of the old parts, and will probably replace them later on.


Motherboard: GIGABYTE GA-EP45-UD3R



No ECC support but I guess that's OK with you.

The Gigabyte boards are the best 775 boards I've seen, except for the origina BadAxe.

> **Genius314 said:**
> 

RAM: Kingston HyperX 2GB (2 x 1GB), 240-pin DDR2 1066



Fast RAM is generally a waste of money for real-world applications.

You definitely want 4 GB, if not 8. In my general-purpose central nervous system station I was forced to abandon a whole platform (socket 939) becauuse the stupid NVidia drivers (probably) were taking up 2 of the 4 GB RAM max that I could have.

> **Genius314 said:**
> 

DVD/CD Drive: LG GH20NS15 (I read in a review that someone couldn't boot from this on a Gigabyte board... This is my main concern, although I have a few ATA drives lying around, just in case)



Hmmm, unlikely I'd say. In general I think DVD drives should stay on P-ATA.

> **Genius314 said:**
> 

Hard Drive 1: WD Caviar Black WD5001AALS 500GB SATA



I don't trust WD. They screw up firmware. But they are reliable. Depends on whaat you do with it.

> **Genius314 said:**
> 

Hard Drive 2: Maxtor 500GB ATA/100 (already own this... I'll probably use it as backup)



Maxtor might be unreliable but you are already running on it.

You might want to consider buying a 750 GB drive and then make a 400 GB raid-1 partition or so.

> **Genius314 said:**
> 

PSU: Antec 500W (no idea the model, I already own it. But if I should replace it, I will)



Antex markets PSUs that are, depending on specific model, made  both by junk manufacturers and others made by good  manufacturers. I don't think they have total lose PSUs, but without a model you can't pick the good stuff here.

> **Genius314 said:**
> 

I also have a Wacom Graphire 3 tablet, a Logitech Wave keyboard, and a Belkin wireless card. I'd assume these will work with any setup, since they're all USB.



Let me know how the Wacom works out. Last time I tried (years ago) I shelfed mine.

> **Genius314 said:**
> 
My monitor is a MAG Innovision 17" CRT... I know it's obscure, and outdated, but I got it for $25, and it works fine. This should probably work with any card that has a DVI output, right?



Sure.

> **Genius314 said:**
> 

I'm keeping the case. It's a mid-tower case (16" x 8" x 19"), so it should fit the motherboard.



A good case can have better ventilation and/or be quieter. Depends on what you want. If you don't overclock and don't mind noise it's probably fine as long as it has dual 80mm or one 120mm output fan.

> **Genius314 said:**
> 

So how good would this setup be? I don't play many games (other than emulators), but I do use 3D software like Blender and Compiz-Fusion, and might play around with programming OpenGL. I want to make sure that all of this hardware is going to work with Ubuntu, and that these programs will work well with the new hardware. (EDIT: I reworded the last sentence.)


The above nitpicking aside, in general it's a great machine.

My major concern is that the quality of the binary NVidia drivers is declining and the Xorg/DRI drivers for moderately new ATI cards are improving. You might not be able to outlive this NVidia card. However, I did not try the above programs with ATI/Xorg/DRI. I just got a recent ATI card for testing, but haven't gotten around to it.

---

### Post by damis648 on 2008-11-27
Hm... looks pretty nice. I would have a look at this video card though: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814143137](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143137) . It's a bit cheaper and an OC'd 9800GTX which looks quite nice. As far as the PSU goes, I recommend you check the model and look it up to make sure it has a combined 12V current rating of 28A or more, which is usually around the sum of the rails.

---

### Post by Genius314 on 2008-11-27
> **Cracauer said:**
> No ECC support but I guess that's OK with you.

The Gigabyte boards are the best 775 boards I've seen, except for the origina BadAxe.

I don't really know what ECC is... Googling tells me it has something to do with RAM. Is there a significant performance difference with ECC?

Of course, I'm now also considering the Asus board mentioned above:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131296)

> Fast RAM is generally a waste of money for real-world applications.

You definitely want 4 GB, if not 8. In my general-purpose central nervous system station I was forced to abandon a whole platform (socket 939) becauuse the stupid NVidia drivers (probably) were taking up 2 of the 4 GB RAM max that I could have.

So something like this, maybe:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134730](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134730)
(2 x 2GB DDR2 800)
The only thing is that it doesn't have a heat spreader, but I don't think I'll need it (correct me if I'm wrong).

EDIT: Or there's this, which has the best rating on Newegg for this type of RAM:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122)

> 
Hmmm, unlikely I'd say. In general I think DVD drives should stay on P-ATA.


Oh well. I already own a PATA DVD drive, which I'll probably use for booting Live CDs or whatever.
I might not get this drive, then, and save $25.
The only problem I see is that, while I'm moving and backing up data, I will have two ATA drives hooked up (I need to move a 40 and an 80 GB onto the Maxtor), and no CD drive (since the motherboard will only support two connections). I can boot without a CD drive hooked up, right? (I'd assume so, but I've never actually done that before)

> I don't trust WD. They screw up firmware. But they are reliable. Depends on whaat you do with it.

I plan on booting from a ~10GB partition, and using the rest for /home, and maybe another partition, if I need it. How exactly do they screw up firmware?

What do you think about Seagate? They seem to have a few similar drives for a little less.

> Maxtor might be unreliable but you are already running on it.

You might want to consider buying a 750 GB drive and then make a 400 GB raid-1 partition or so.

Well, the Maxtor works fine at the moment. But even if it fails, in my new system it will probably just be used for backup... So my data will be fine as long as the SATA drive works.

> Antex markets PSUs that are, depending on specific model, made  both by junk manufacturers and others made by good  manufacturers. I don't think they have total lose PSUs, but without a model you can't pick the good stuff here.

Well, it's working fine so far, and I've had it for at least a year (maybe even 2 years. I'm not sure exactly when I bought it)... I definitely need to open the case though, and find out which model it is.

> Let me know how the Wacom works out. Last time I tried (years ago) I shelfed mine.

It works great with my current system. Unfortunately, I still need to configure Xorg.conf to get it fully working on new installs... but that's pretty easy to do, of course.

> A good case can have better ventilation and/or be quieter. Depends on what you want. If you don't overclock and don't mind noise it's probably fine as long as it has dual 80mm or one 120mm output fan.

I think I have 4 80mm fans in this case. And I don't overclock (I'd love a little extra power, but its too much risk for too little benefit, IMO.)
Noise isn't a problem, either, since I usually have headphones on.
The only real reason I would replace this case is because it's an ugly beige case... but I don't look under my desk too often, so it's not a big deal. :p

> My major concern is that the quality of the binary NVidia drivers is declining and the Xorg/DRI drivers for moderately new ATI cards are improving. You might not be able to outlive this NVidia card. However, I did not try the above programs with ATI/Xorg/DRI. I just got a recent ATI card for testing, but haven't gotten around to it.

Really? I heard that ATI drivers are supposedly getting better, but I didn't think NVidia would be getting worse...
Right now I have an ATI All-in-Wonder 9800 Pro, but after upgrading to Intrepid, the proprietary driver doesn't work as well as it did in Hardy (for instance, the blur plugin in Compiz doesn't work correctly.) That was one of the main reasons why I chose nVidia.
If anyone has any problems in 8.10 with the 8800GTS (or the 9800GTX, see below), let me know.

[QUOTE=damis648]Hm... looks pretty nice. I would have a look at this video card though: [http://www.newegg.com/Product/Produc...82E16814143137](http://www.newegg.com/Product/Produc...82E16814143137) . It's a bit cheaper and an OC'd 9800GTX which looks quite nice. As far as the PSU goes, I recommend you check the model and look it up to make sure it has a combined 12V current rating of 28A or more, which is usually around the sum of the rails.[/QUOTE]

It seems like a slightly better card. But a quick Google search tells me that the card has identical performance compared to the 8800GTS.
If I understand correctly, this card is factory overclocked? I don't think I really like that idea... But I'm probably just worrying too much. :lolflag:
Actually, it's not cheaper. The 8800GTS has a $30 mail-in rebate, which means the final price will be $10 less than the 9800GTX.

I'll check the PSU model after I finish posting this...
EDIT: It's an Antec Basiq 500W.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371004](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371004)

[QUOTE=coastdweller]Yep, that's the board. I went through the newegg reviews and pretty much know that any issues are already fixed (In fact yesterday I fixed the issue with the underperforming IDE, which is window's updates...

If you bring the OS up to date, remove the IDE devices and let them be found again its all good.

We've built quite a few mid level gaming system with this board and so far we're impressed with the speed.

Even the newegg reviewers actually mention it!

In the shop we say it's overclocking itself :lolflag:[/QUOTE]

Well, then I'll probably get this board. It seems like a good enough investment.

Once again, thanks for all the helpful comments. :popcorn:


EDIT: So far I haven't heard any comments about the HSF. 
If I get one to replace the stock one, it will probably be either:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134](http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134)
or
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835114073](http://www.newegg.com/Product/Product.aspx?Item=N82E16835114073)
Freezer 7 Pro sounds like a really good heatsink, but the biggest complaints are the tabs that are used to hold it down, and it's size. Are the tabs really that bad? I've never used them before, but if they are, I'll get the Dynatron (which seems to be the highest rated HSF that uses a screw mount... although that rating might not be trustworthy, since there's less than 30 reviews for it)

---

### Post by Genius314 on 2008-11-28
(Bump)
Here is the updated list of what I plan on buying:

CPU: Intel Core 2 Duo E8500 Wolfdale 3.16GHz

Motherboard: ASUS P5Q-E (Thanks to coastdweller. You seem confident enough in this board, so I'm going with it.)

*Video Card: BFG Tech BFGE88512GTSE GeForce 8800GTS 512MB ($10 cheaper than the 9800GTX mentioned above, and reviews say they have pretty much the same performance.)

*Hard Drive: Either the WD Caviar Black WD5001AALS 500GB, or the Seagate Barracuda 7200.11 ST3500320AS 500GB. Both seem to have the same specs, but the Seagate is a little cheaper, and has a longer warranty (5 yrs vs 3 with WD). Right now I'm leaning towards the Seagate. Which one should I get?

RAM: G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 800

Heatsink: Probably the Arctic Cooling 7 Pro. Seems to be a good value, and a great HSF. And it comes with MX-1 compound, which is apparently better to leave on than to replace (which saves me about $28, since I don't need to buy any compound or cleaner).

(The ones with asterisks are the ones I'm still not really sure about.)

---

### Post by BFG on 2008-11-28
I have a GA-EP45-DS5 and 64bit ubuntu refuses to install.

Only help I've found so far is...
[http://georgia.ubuntuforums.com/showthread.php?p=6025913](http://georgia.ubuntuforums.com/showthread.php?p=6025913)

---

### Post by Genius314 on 2008-11-28
> **BFG said:**
> I have a GA-EP45-DS5 and 64bit ubuntu refuses to install.

Only help I've found so far is...
[http://georgia.ubuntuforums.com/showthread.php?p=6025913](http://georgia.ubuntuforums.com/showthread.php?p=6025913)

I've decided on the Asus P5Q-e, rather than the Gigabyte board.

...Well, almost.
There are some issues that still worry me.

Random lockups:
[http://www.tomshardware.com/forum/253406-30-build-issue-random-lockups](http://www.tomshardware.com/forum/253406-30-build-issue-random-lockups)

Ubuntu hangs on bootup: (A pretty simple fix is given, but I still don't want to have to do that :p)
[http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html](http://linuxrevolution.blogspot.com/2008/09/ubuntu-and-asus-p5q-e-motherboard.html)

USB Keyboard won't work in BIOS or GRUB (even with legacy enabled):
[http://ubuntuforums.org/showthread.php?t=953291](http://ubuntuforums.org/showthread.php?t=953291)

Coastdweller, you said that the problems stated in the Newegg reviews had all been fixed. Have these other problems been fixed as well?


Oh, and a few miscellaneous questions:
1. Is there a way to back up the SATA automatically on the ATA drive?

2. Will Ubuntu 8.10 32-bit be able to use both cores of the CPU, as well as all 4 GB of RAM, or will I have to upgrade to 64-bit?

---

### Post by Genius314 on 2008-11-28
Okay, well, I changed some parts around, to reduce the cost. I've read mixed reviews, and finally came up with the following setup:

-Gigabyte GA-EP45-UD3P (Pretty cheap, and reported to work in Ubuntu. It's also refundable, which the Asus board wasn't.)

-Intel Core 2 Duo 8E500 3.16GHz

-Arctic Cooling Freezer 7 Pro (Hoping it will fit)

-Corsair 4GB (2 x 2GB) DDR2 800 (Really cheap after rebate, and seems decent enough)

-BFG Tech BFGE88512GTSE GeForce 8800GTS 512MB

-Seagate Barracuda 7200.11 ST3500320AS 500GB

If anyone has anything to say about these, let me know NOW. I'm probably going to buy these tonight (within the next few hours)

---

### Post by Cracauer on 2008-11-30
Looks good.  Just for reference answers to the above questions:

> **Genius314 said:**
> I don't really know what ECC is... Googling tells me it has something to do with RAM. Is there a significant performance difference with ECC?



It's not about performance, it's about getting the same data out of your memory that you put in.




> **Genius314 said:**
> 


I plan on booting from a ~10GB partition, and using the rest for /home, and maybe another partition, if I need it. How exactly do they screw up firmware?



For example, you mix up sectors while you pretend to support command queuing.

> **Genius314 said:**
> 

What do you think about Seagate? They seem to have a few similar drives for a little less.




I only use Seagtes willingly. I have a couple other drives that I stuff into arrays that I don't care about.

> **Genius314 said:**
> 


Well, the Maxtor works fine at the moment. But even if it fails, in my new system it will probably just be used for backup... So my data will be fine as long as the SATA drive works.



Well, it's working fine so far, and I've had it for at least a year (maybe even 2 years. I'm not sure exactly when I bought it)... I definitely need to open the case though, and find out which model it is.




Some Maxtors had a very specific problem with dying after power fluctuations. That's bad for us RAID users since the same power fluctuation will affect multiple drives and hence you run a risk of losing the whole array.

> **Genius314 said:**
> 

Really? I heard that ATI drivers are supposedly getting better, but I didn't think NVidia would be getting worse...



No, head over to nvnews.com.  Horrible 2D performance, huge memory hogs, all kinds of regular bugs.

Definitely much worse than they used to be a couple years ago.

They run games fast, sure, but...

> **Genius314 said:**
> 
I'll check the PSU model after I finish posting this...
EDIT: It's an Antec Basiq 500W.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371004](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371004)




Never heard of it. Not a good sign. Most certainly junk.

> **Genius314 said:**
> 


EDIT: So far I haven't heard any comments about the HSF. 
If I get one to replace the stock one, it will probably be either:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134](http://www.newegg.com/Product/Product.aspx?Item=N82E16835186134)
or
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835114073](http://www.newegg.com/Product/Product.aspx?Item=N82E16835114073)
Freezer 7 Pro sounds like a really good heatsink, but the biggest complaints are the tabs that are used to hold it down, and it's size. Are the tabs really that bad? I've never used them before, but if they are, I'll get the Dynatron (which seems to be the highest rated HSF that uses a screw mount... although that rating might not be trustworthy, since there's less than 30 reviews for it)

Uh? I have a bazillion of Freezers, 7s and 64s, and I rate them as the best compromise of cooling, space and noise south of heavy overclocking. I am really, really tired of HSFs using non-standard mounting mechanisms. The Freezers use your standard mount. Huge advantage.

---

### Post by Genius314 on 2008-11-30
> **Cracauer said:**
> It's not about performance, it's about getting the same data out of your memory that you put in.

Yeah, I understand it a bit better now. I don't think I would need it (I've never had it before, so it shouldn't matter now)

> **Cracauer said:**
> For example, you mix up sectors while you pretend to support command queuing.

Okay. Luckily I went with the Seagate, so...

> **Cracauer said:**
> Some Maxtors had a very specific problem with dying after power fluctuations. That's bad for us RAID users since the same power fluctuation will affect multiple drives and hence you run a risk of losing the whole array.

Well, as long as I have *one* backup functioning...

> **Cracauer said:**
> No, head over to nvnews.com.  Horrible 2D performance, huge memory hogs, all kinds of regular bugs.

Definitely much worse than they used to be a couple years ago.

They run games fast, sure, but...

Not good. :( I already bought it, but if it gives me trouble, I'll send it back for an ATI.
Btw, that site points to non-existent domain. It should be nvnews.net. I'll check it out.
Are the Windows drivers similar, or just Linux?

> **Cracauer said:**
> Never heard of it. Not a good sign. Most certainly junk.

Probably. I've been using it at least 2 years, and it works well enough...
I'll probably replace it eventually, but I don't think I'll need to any time soon.

> **Cracauer said:**
> Uh? I have a bazillion of Freezers, 7s and 64s, and I rate them as the best compromise of cooling, space and noise south of heavy overclocking. I am really, really tired of HSFs using non-standard mounting mechanisms. The Freezers use your standard mount. Huge advantage.

Good to know. I don't overclock*, but the stock HSF seemed to be what people complained about the most. (And, knowing my luck, I would be the one who ends up with an overheated processor #-o)
*I might start overclocking one day... but for now, I really don't want to waste my money on that.


Well, this system should get here either tomorrow or Tuesday. Hopefully everything will work right (:lolflag:)

---

### Post by Cyhawk on 2008-11-30
I put my rant at the bottom... (about memory)

> Motherboard: GIGABYTE GA-EP45-UD3R
Not a super high-end board, but it will work. I personally have had mixed results with gigabyte (from boards that lasted in minutes, to my current NFS thats been running for nearly 6 years) From the reviews, its a mid level board. Though i dont think you'll need much higher. (most dont, even I dont)

> CPU: Intel Core 2 Duo E8500 Wolfdale 3.16GHz
At my current position, we just finished building 50 desktops with these in them. I assume we got a bad batch, I really do, nearly 20 of them failed within a week. Just to be on the safe side, make sure you can return them.

Other than my experience, its a solid chip, cant complain. (though im an AMD fanboy, Buy a quad-core Phenom, cheaper, more reliable, and not intel =)

> Video Card: BFG Tech BFGE88512GTSE, GeForce 8800GTS 512 MB
Decent chip (8800GTS), never used the manufacturer, and cant find any reviews I trust. 

> RAM: Kingston HyperX 2GB (2 x 1GB), 240-pin DDR2 1066

(See first statement)
Id also go with more ram, as others have said, max it out (4gb, or 8gb) as much as you can afford. ram is VERY VERY cheap right now, take advantage of it before the manufactures cut production and raise prices. (I predict this current state to last until about May next year, then prices will rise)

> DVD/CD Drive: LG GH20NS15 (I read in a review that someone couldn't boot from this on a Gigabyte board... This is my main concern, although I have a few ATA drives lying around, just in case)

Ive never had many bad LG drives. I cant complain. Its a good solid choice.

> Hard Drive 1: WD Caviar Black WD5001AALS 500GB SATA
Hard Drive 2: Maxtor 500GB ATA/100 (already own this... I'll probably use it as backup)PSU: Antec 500W (no idea the model, I already own it. But if I should replace it, I will)

Hard drives are hard drives =) Though I personally dislike WD. Theyve made enough bad drives in the past, I dont trust them anymore. If they last past 6 months, they last for good though. I beleive someone mentioned a Seagate or Raptor, Seagate is good and cheapish right now, Id go with them. (Raptors are just too bloody expensive)

Oh and side note: Who was the person that recommended a raid-1 with PARTITIONS!?? *smacks forhead* Alot of good that will do when the DRIVE fails :P

> HSF: Dynatron P985 92mm (The best model that I could find that isn't held down with those tabs, which are supposedly annoying. I don't own this yet.)

Its a fan... In a majority of cases, the basic fan that comes with the process works perfectly for years. Dont spend money where it isnt needed. (If you DO end up needing a fan, then buy it, dont waste now, do it when its needed =)

> Thermal Compound: Arctic Silver 5
Its Thermal compound... :P Who cares, heh. Seriously, its like Gas, its all pretty much the same.


--- Begin RAM rant --- 

Ok first off: I use to do Tech support for a memory company, I dont buy into BS =)

ECC, error correct code, its a type of ram that can detect ram errors and sometimes fix it. 99.99999% of the time, your average home user (you and me) dont need ECC. Its nice to have, but doesnt justify the cost. Also, it DOES slow down the memory by 1 clock cycle. This isnt needed outside of server environments where uptime and extreme reliability is needed. And, I can almost guarantee you will never encounter a situation where you'll need it. Sorry if this seems wordy and pushy but, see previous statement :P
Secondly, faster ram wont make a difference. Were talking 1-2% speed increases here, IF that. 5300(667) is more than enough. Heck, PC133 is good enough for what we all do. It "helps" but get the cheap stuff, its all the same, seriously it is. Just make sure where you buy it has a lifetime warranty so you can replace it when it goes bad. (which happens, ram is fragile)

---

### Post by binbash on 2008-11-30
WD has good hdds, i used both seagate and wd.I would go for seagate.
If you are going to use 4gb ram prepare to change your kernel cos you cant use more than 3.5(it was 3.5, it may be 3 if i am wrong :) )with default kernel.

---

### Post by Cracauer on 2008-12-01
> **Genius314 said:**
> Not good. :( I already bought it, but if it gives me trouble, I'll send it back for an ATI.
Btw, that site points to non-existent domain. It should be nvnews.net. I'll check it out.
Are the Windows drivers similar, or just Linux?




The binary NVidia Linux drivers used to be pretty much the same as Windoze, including same performance.

These days it seems that gaming and maybe other 3D performance is the only thing that works right anymore.

nvnews.net forum, yes.

> **Genius314 said:**
> 


Probably. I've been using it at least 2 years, and it works well enough...
I'll probably replace it eventually, but I don't think I'll need to any time soon.


Quite honestly I can't recommend to hang your new system to this PSU. You didn't post what you used before but you put a high-power video card and a 3.16 GHz dual-core in there. Just because it didn't blow up in the past doesn't mean it won't in the future.

A PSU blowing up can take all your components with it. At least you should do a google forum search looking for signs of trouble with that model PSU.

---

### Post by Genius314 on 2008-12-01
...

Okay, then... Any suggestion on a PSU that will work with my system? (Same parts as listed in post #13, plus an ATA drive, ATA optical drive, CRT monitor, and a few USB devices)

Here's the highest rated PSU's on Newegg:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010320058](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010320058)

I'm not looking to spend more than $100, and, if possible, I'd like one below $75.

Any help with this? The parts are probably going to come by tomorrow, and I want to get this built as quickly as possible (in case anything needs to be replaced or returned.)

EDIT: 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817703005](http://www.newegg.com/Product/Product.aspx?Item=N82E16817703005)
Here's one with a good price (and free shipping :D), a 12V rail at 49A, but only one rail. 610W, so that's probably plenty for my system (I've used a few PSU calculators, and despite them all giving different answers, none ever said I needed that much).
Is it a good buy?
EDIT2: It seems to have the right amount of connections... just need to make sure it has the right amperage and everything (really, I have no idea what a lot of this stuff actually means, but I'm learning...)

---

### Post by Cracauer on 2008-12-01
I haven't kept up-to-date with recent power supplies.

Seasonic and Fortron make good PSUs that are cheap and quiet and not hardcore but won't fall apart. The problem is figuring out which *brand* and *model* deliver which *manufacturer*'s prodcts. 

I have a couple of OCZs which are made by Fortron and the older 520W, forgot the manufacturer. But even the Fortron-made GameXtreme are good, I have two of the 700 watts. One holds a heavily overclocked gaming machine with 7800GTX and 7 CD drivers, the other my 4-CPU/8-core K8. No problems, although by real men's standards the Fortrons are considered meh-class. I use own-branded Seasonics in my regular worker machines. No problems either.

For hardcore overclocking I use a Zippy 700W but that's a server class part with appropriate noise level.

This used to be a high-class forum for PSU details, maybe it's still useful.
[http://www.jonnyguru.com/forums/forumdisplay.php?f=3](http://www.jonnyguru.com/forums/forumdisplay.php?f=3)

---

### Post by Genius314 on 2008-12-01
Well, the PC P&C seems to use the same parts that OCZ and Corsair use in similar models... but I can't find any information on it (not sure exactly what to search for).

Nevertheless, this seems like a pretty good PSU (except that they seem to have a high rate of DOA models). I might just go ahead and buy it, unless someone can offer a better choice. Anyone?

---

### Post by Cracauer on 2008-12-02
> **Genius314 said:**
> Well, the PC P&C seems to use the same parts that OCZ and Corsair use in similar models... but I can't find any information on it (not sure exactly what to search for).

Nevertheless, this seems like a pretty good PSU (except that they seem to have a high rate of DOA models). I might just go ahead and buy it, unless someone can offer a better choice. Anyone?

PCP&C is owned by OCZ now. Quality brand. Mostly Seasonic built IIRC.

---

### Post by Genius314 on 2008-12-02
> **Cracauer said:**
> PCP&C is owned by OCZ now. Quality brand. Mostly Seasonic built IIRC.

Cool. I'll probably get that one, then (assuming it will fit in my case... it's about an inch longer than standard PSU's, but I think I have room to spare)

Everything's arrived already, except the motherboard. I'll probably get next-day delivery on the power supply, so they come at about the same time.

Oh yeah, and now that I see the heatsink, it really seems overkill... Idk, I might send it back. But of course, it's never bad to have a little extra cooling (and it was pretty cheap).
I'm just afraid this thing's gonna snap my motherboard in half when I stand the tower up... :p

---

### Post by anttipupunen on 2009-02-27
Hey Dude, let me know if the combination P5q-e + E8500 + 8.10 worked Ok. Thanks!

---


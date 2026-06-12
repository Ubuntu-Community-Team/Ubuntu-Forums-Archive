---
title: "New System Config - Your opinion?"
date: 2009-10-19
forum: Hardware
---

### Post by MCSE_Crossover on 2009-10-19
Whats up guys and gals -

I'm building a new rig - wanted to get your opinions. Nothing special with it - light video editing, light gaming, web surfing, YouTube, moderate web design, kids online games, etc.

GIGABYTE GA-MA785GMT-UD2H
4 GB G.Skill DDR3 1600
400W Power Supply w/ CoolMaster Case
AMD Phenom II X2 545 Callisto 3.0GHz Dual Core
500GB 7200 RPM Hard Drive

Only problem i'm having is what to do about the video card. The MB comes with an integrated ATI HD 4200. I know i've had some issues in the past with Compiz and FGLRX compatibility. You think I should just stick with that card or go with a stand alone nVIDIA Card, like a GTS250 or something?

Thanks!

---

### Post by Dark_Stang on 2009-10-19
Unfortunately, ATI drivers tend to suck. ATI is makign better cards at this point (flat out amazing cards actually), but I'm still sticking with nVidia because of how well their driveres work. If you're using it for light gaming you don't need a GTS250. But hey, if you've got the money why not. I'd go with a higher wattage power supply though for that card. 550 or more just because I'm paranoid.

---

### Post by MCSE_Crossover on 2009-10-19
How about a 9600GT? I looked at the graphics hierarchy on [http://www.tomshardware.com/reviews/best-graphics-card,2404-7.html]("http://www.tomshardware.com/reviews/best-graphics-card,2404-7.html") and it seemed to be a great bargain! New egg has an "open box" for $63 - down from $95. 

Other then that, good ya think? I don't think that card requires seperate power...

---

### Post by MCSE_Crossover on 2009-10-19
Oh, yea, it does require power. But, according to [Power Calculator]("http://extreme.outervision.com/PSUEngine") i'll only be using about 275W. I think i'm straight with a 400, no?

---

### Post by madverb on 2009-10-19
Yeah, you should be fine with that. Just don't think about adding anything else.
If you want to have the option to add to your system you might want to consider a better PSU. Just to save having to buy a new on in the future anyway.

---

### Post by cascade9 on 2009-10-20
> **MCSE_Crossover said:**
> Whats up guys and gals -

I'm building a new rig - wanted to get your opinions. Nothing special with it - light video editing, light gaming, web surfing, YouTube, moderate web design, kids online games, etc.

GIGABYTE GA-MA785GMT-UD2H
4 GB G.Skill DDR3 1600
400W Power Supply w/ CoolMaster Case
AMD Phenom II X2 545 Callisto 3.0GHz Dual Core
500GB 7200 RPM Hard Drive

Only problem i'm having is what to do about the video card. The MB comes with an integrated ATI HD 4200. I know i've had some issues in the past with Compiz and FGLRX compatibility. You think I should just stick with that card or go with a stand alone nVIDIA Card, like a GTS250 or something?

Thanks!

Dont bother with a GTS250. Its just a revised version of the old G92 chip that appeared with the 8800GT! A better option would be a lower version of the G2XX series cards  like a GT210/GT220 or an older 9x series card- 9400GT/9600GT. You wont neeed a bigger card than a 9600GT, at most, for your stated uses. 

If you were going to get a higher end video card than a 9600GT I would get a bigger power supply as well, 400 watts might be a bit low (some of those higher end video cars EAT power). Also, I would consider getting a motherboard without intergrated graphics, if you are going to use a video card there is no point having on-board video. Maybe a Gigabyte GA-MA770-UD3P? 

BTW, I _think_ that you only get up to 1333 mhz without overclocking. If your paying much more for DDR3 1600 memory and your no going to overclock, maybe drop your memory speeds.

---

### Post by Dark_Stang on 2009-10-20
> **MCSE_Crossover said:**
> Oh, yea, it does require power. But, according to [Power Calculator]("http://extreme.outervision.com/PSUEngine") i'll only be using about 275W. I think i'm straight with a 400, no?

The problem isn't total power consumption, but the power consuption of the video cards. A 9600 on a 400w should be fine, but a GTS250 probably won't be. The problem is most of the lower wattage power supplies only put out so much power to the rails going to the video card. So yeah, you have 400w total power, but that individual rail going to your video card doesn't have enough to run it when you're gaming. That's why I was suggesting a higher end power supply.

Edit: Just to add to this. I have seen people with 800+w power supplies running SLi/Crossfire not have enough power going to those rails. When I replace this with a 750w Thermaltake power supply that works just fine they usually freak out at the logic and I have to explain this to them.

---

### Post by markbuntu on 2009-10-21
You should give the 4200 a whirl before spending more money.

Unless you install karmic do not use the driver offered by hardware manager/jockey. It does not support that card. Instead, install, update, get the latest driver from ati and install that by running the installer. There is a problem with some 3xxx igps that cause kernel panic if the igp memory is set below 500k. I do not know if it effects the 4200, probably not since I have seen no one complaining.

If you do decide to not use it it is very easy to remove fglrx if you installed it with the installer. There is a script usr/share/ati/fglrx-uninstall that will completely remove the driver, kernel modules and everything and give you a clean system back.

---


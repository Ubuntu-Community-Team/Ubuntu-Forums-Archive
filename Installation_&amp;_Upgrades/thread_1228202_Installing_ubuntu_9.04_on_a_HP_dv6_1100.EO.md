---
title: "Installing ubuntu 9.04 on a HP dv6 1100.EO"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by Turk4n on 2009-07-31
Hello !

I am quite new to ubuntu and the whole gnu/linux thing. I bought for myself a new laptop which is really cool and neat !

It works wonders with windows and I have no special problems or so. Now when I want to install ubuntu it seems like the ubuntu cd or dvd installs or even boot up(GUI mode). So I did a minimalistic installation and it went ok. Now comes the problem. I can't get my gfx to work, screen resolution is messed. ACPI bad and the laptop gets freaking hot !
I seem to not have any sound or so from any jacket !

So some specs...

AMD Turion X2 64 RM-74 2.2GHz 1MB L2 cache(512/core)
4GB DDR2 800MHz Samsung CXPC6400
ATi Mobility Radeon HD 4650 1GB GDDR3/DDR2
Sound Blaster 16Bit PRO...

Could anyone possibly help me as soon as possible?
I would really like to have fun working with gnu/linux before my summer vacation is over !
*Thanks in advance !*
P.S - Pardon for my bad English(not my mother tongue).

---

### Post by Topher88 on 2009-07-31
> **Turk4n said:**
> Hello !

I am quite new to ubuntu and the whole gnu/linux thing. I bought for myself a new laptop which is really cool and neat !

It works wonders with windows and I have no special problems or so. Now when I want to install ubuntu it seems like the ubuntu cd or dvd installs or even boot up(GUI mode). So I did a minimalistic installation and it went ok. Now comes the problem. I can't get my gfx to work, screen resolution is messed. ACPI bad and the laptop gets freaking hot !
I seem to not have any sound or so from any jacket !

So some specs...

AMD Turion X2 64 RM-74 2.2GHz 1MB L2 cache(512/core)
4GB DDR2 800MHz Samsung CXPC6400
ATi Mobility Radeon HD 4650 1GB GDDR3/DDR2
Sound Blaster 16Bit PRO...

Could anyone possibly help me as soon as possible?
I would really like to have fun working with gnu/linux before my summer vacation is over !
*Thanks in advance !*
P.S - Pardon for my bad English(not my mother tongue).

Ubuntu and ATI cards are notorious for not playing well together.  I am wanting to buy an HP with this exact same card as well, so if there are any workarounds, I'd like to know, too...

---

### Post by Turk4n on 2009-07-31
> **Topher88 said:**
> Ubuntu and ATI cards are notorious for not playing well together.  I am wanting to buy an HP with this exact same card as well, so if there are any workarounds, I'd like to know, too...

Thanks for replying, So GNU/Linux + ATI no good?
Then why, please tell me why does the laptop run so hot while running ubuntu with no proper driver !
I looked it up and wonder, doesn't gnu/linux support PowerNow! and why is the CPU always running at 100% ?

---

### Post by Topher88 on 2009-07-31
> **Turk4n said:**
> Thanks for replying, So GNU/Linux + ATI no good?
Then why, please tell me why does the laptop run so hot while running ubuntu with no proper driver !
I looked it up and wonder, doesn't gnu/linux support PowerNow! and why is the CPU always running at 100% ?

I THINK the computer will still work fine for very, very basic tasks, but the problem is that you can't use the card to it's fullest extent (utilizing desktop animation, using applications like compiz or other applications that use a lot of graphics, etc) without the proper drivers that, from what I've heard, are few and far between, depending on your setup.  Really, though, that'd be a question for someone a bit more advanced than me.  This is just what I've heard.  Sometimes you can work around with either propriety or open source drivers, and other times you'll be less fortunate; like I said, it depends on your setup.

---

### Post by Turk4n on 2009-07-31
> **Topher88 said:**
> I THINK the computer will still work fine for very, very basic tasks, but the problem is that you can't use the card to it's fullest extent (utilizing desktop animation, using applications like compiz or other applications that use a lot of graphics, etc) without the proper drivers that, from what I've heard, are few and far between, depending on your setup.  Really, though, that'd be a question for someone a bit more advanced than me.  This is just what I've heard.  Sometimes you can work around with either propriety or open source drivers, and other times you'll be less fortunate; like I said, it depends on your setup.

Okay, that's understandable,however why is it that my CPU runs at its fullest ?
I mean come on, while idling CPU runs max performance? Isn't PowerNow! On or something or is that, throttling doesn't work well in gnu/linux?

---

### Post by atomizer on 2009-07-31
have almost simular laptop (dv7-1110ed)

Did you install the drivers from ati? I have no problems with their drivers. CPU running at 4-5% idle with compiz on and no problems what so ever.

ati drivers can be found in system>administration>something with hardware (not on gnome atm)

type ```
top
``` in a terminal to see what is eating your cpu

---

### Post by Turk4n on 2009-08-01
> **atomizer said:**
> have almost simular laptop (dv7-1110ed)

Did you install the drivers from ati? I have no problems with their drivers. CPU running at 4-5% idle with compiz on and no problems what so ever.

ati drivers can be found in system>administration>something with hardware (not on gnome atm)

type ```
top
``` in a terminal to see what is eating your cpu

Nothing seems to be eating my CPU :(
I really want these problems to be solved :'(
CPU not throttling only staying on 100% and burning up, and video card needs proper drivers :(

---

### Post by atomizer on 2009-08-01
Am on gnome now.... the drivers are in system>administration>hardware drivers.

What is the max cpu your processes are running then? (top)

It is strange that the proces doesn't show in top. Maybe it is a rootkit?

---

### Post by Turk4n on 2009-08-01
> **atomizer said:**
> Am on gnome now.... the drivers are in system>administration>hardware drivers.

What is the max cpu your processes are running then? (top)

It is strange that the proces doesn't show in top. Maybe it is a rootkit?

How is that possible, when I downloaded the cd image and dvd image straight through ubuntus homepage?

---

### Post by atomizer on 2009-08-01
I don't know.

But when a process is eating your cpu, top should show it.


By the way, if you don't have system>administration>hardware drivers you can install them by doing ```
sudo apt-get install jockey-gtk fglrx-modaliases
```

this installs the standard gui for installing propetary ATI drivers

---

### Post by kg84 on 2009-08-01
> **atomizer said:**
> I don't know.

But when a process is eating your cpu, top should show it.

Exactly. I have a DV6 1130TX.

Today the fans turned on and stayed on - I wondered why as nothing was really running.

A look with Htop showed the alsa mixer chewing up 100% of the CPU. I quickly killed it and the fans went quiet.

---

### Post by W4l0ck on 2009-08-01
Well, probably a hardware error.

---

### Post by peoplenamed on 2009-08-11
i have a hp dv 6 dual booting with jaunty and vista both 64 bit.. both run awesome with minimal problems. HOWEVER.. im not 100% sure how i had it set up in the begining.. but when i had hardy i had compiz running 100% and no heat issues.. after the update i will be watching streaming video or listening to streaming music or watching a dvd my cpu goes upto 90something degrees celcius and the computer just shuts off. The first 20 times i couldnt figure what problem i was getting but that it might be associated with video.. now i know it is def a heat issue.. so i went through a bunch of steps in the forums and added a cpu heat check widget.. and noticed there was an option for something called cpu freq scaling monitor.. so i added it and now i have control of how much power im putting through to each cpu. it was auto set to on demand which would give me xtra cpu when i need it from 500mhz to 2ghz.. i set it to max at 500 and now my heat stays below 70 celcius for the most part even when playing a movie.. i still have all my compiz and hulu running at the same time with minimal interfearence.. but even 70 seems really hot.. its never below 50 celcius 5+ minutes after boot..i wish i knew more about this, but i do know that the computer works almost 100% with jaunty.. and very well with hardy.. too lazy to downgrade.. some1 find me a more permanent fix... please?

---

### Post by Turk4n on 2009-08-11
Seems, I can't use Linux at all, due to bad support from AMDs side. PowerNow works like crap and cpu always overheat. This isn't normal. Why should my idle temp be at 73 degree celsius and full load at 91?

---

### Post by peoplenamed on 2009-08-11
im idleing 58-64C running amd turion x2 64, ati radeon hd3200 when i play movies it sometimes goes to 100C and my laptop shuts off. if i lower my cpu to 500mhz vs 2.ghz it seems to correct this.. a little.. crappy.. but.. my top also says im not running anything but a fair amt of my cpu is being used. running ati proprietary drivers.. everything in jaunty works great! but this heat problem forces me to switch back and forth between vista.

---

### Post by peoplenamed on 2009-08-11
also, the box on my power cord gets flaming hot! is that because my cpu is so hot im just blowing through energy?

---

### Post by Turk4n on 2009-08-13
This is sucks, I really want to use and learn more about Linux. However I can't even run it properly what is this kind of bull?

---


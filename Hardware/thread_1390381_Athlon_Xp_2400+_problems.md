---
title: "Athlon Xp 2400+ problems"
date: 2010-01-25
forum: Hardware
---

### Post by Katman000 on 2010-01-25
Hey everyone, I really need a fast response, and I went here because this community is so great.

Long story short, I bought a new processor for my old computer and the Athlon Xp 2400+ came up as an 1800+

Googled the problem and found I needed to change my FSB in the Bios. Did that, and now my computer wont boot. 

Im using an MSI KTV4 mobo. The system boots up WinXp and gets the the boots screen with the scrolling blue bar. Then the system tanks and turns off.

Any ideas?

---

### Post by llawwehttam on 2010-01-25
I had an athlon 2200+ come up as a 1500+ but I just left it. Would like to know how to fix it tho.

EDIT: it was the FSB. What annoys me is that 2200+ is NOT 2.2 GHz. Its actually 1800MHz. 2200+ was meaning that it was equivalent to a pentium 4 2.2.

---

### Post by Katman000 on 2010-01-25
Well Ill be damned... 
I tried booting it up for the 10th time and it worked!
I tried loading up tf2 though and it shut down.
It was running a bit warm, 42 on idle... could that be the problem? 
I have an 80mm fan running plus the heatsink, my thermal compound was applied correctly; I have no idea why it is so hot.

---

### Post by llawwehttam on 2010-01-25
> **Katman000 said:**
> Well Ill be damned... 
I tried booting it up for the 10th time and it worked!
I tried loading up tf2 though and it shut down.
It was running a bit warm, 42 on idle... could that be the problem? 
I have an 80mm fan running plus the heatsink, my thermal compound was applied correctly; I have no idea why it is so hot.

I have a coolermaster cpu cooler I bought for $35 for my P4 and it runs at 36 on idle. 42 isn't too hot. You may have bad overclock values or your PSU may not be good enough.

---

### Post by Leshrac on 2010-01-25
You mean it shows up as 1800MHz?

If so, then it is most likely working as intended, the xxxx+ numbers on amd cpus are a marketing stunt, not actual ratings.

---

### Post by Katman000 on 2010-01-25
I got it to register as a 2400+, that's not the issue. The processor is running, but the computer shuts down during, or shortly after booting. 

Could it be the PSU? May I have to reinstall the OS?

---

### Post by Leshrac on 2010-01-25
> **Katman000 said:**
> I got it to register as a 2400+, that's not the issue. The processor is running, but the computer shuts down during, or shortly after booting. 

Could it be the PSU? May I have to reinstall the OS?

The way you describe it, it looks like a hardware problem.
Most likely overheating, but it could also be a defective cpu, or one that's received quite some abuse.

You could try underclocking it, or triple checking your heat sink setup.

Some people used to do really weird things with their athlon XPs back in the day: [http://www.phys.ncku.edu.tw/~htsu/humor/fry_egg.html]("http://www.phys.ncku.edu.tw/~htsu/humor/fry_egg.html")

---

### Post by Katman000 on 2010-01-25
Im not overclocking the machine, Im simply plugging in the correct settings.

I don't think its the PSU because and Athlon 64 would require 400 watts, and I have 350. I could be wrong though.

Restarting the cmos didn't work either.
Would I have the reinstall windows?

---

### Post by Katman000 on 2010-01-25
"underclocking" it to a 1800 would make the machine run, but that is only because the machine was used to an Athlon clocked at 1.2 Ghz with a FSB of 100. I think the OS is just doesn't like the new FSB, but I could be wrong....

---

### Post by underquark on 2010-01-25
Could be that the RAM doesn't cope with faster FSB.  Changing RAM latencies might help get it to run but maybe best just to ramp everything back down to slower FSB speed and live with it.

---

### Post by Katman000 on 2010-01-25
Checked the Ram Frequency in the bios and it was 133, allowing for a perfect 1:1 ratio. The Latency was set to Auto, any suggestions on what to set it to?

---

### Post by cascade9 on 2010-01-25
> **llawwehttam said:**
> I had an athlon 2200+ come up as a 1500+ but I just left it. Would like to know how to fix it tho.

You're running @ 100FSB, go into your BIOS and change it to 133 and you will get 2200+. (yeah, I've seen this happen, I was a long time 2200+ user)

> **Katman000 said:**
> "underclocking" it to a 1800 would make the machine run, but that is only because the machine was used to an Athlon clocked at 1.2 Ghz with a FSB of 100. I think the OS is just doesn't like the new FSB, but I could be wrong....

Thats never been an issue when I've done it. ;) 

> **Katman000 said:**
> Well Ill be damned... 
I tried booting it up for the 10th time and it worked!
I tried loading up tf2 though and it shut down.
It was running a bit warm, 42 on idle... could that be the problem? 
I have an 80mm fan running plus the heatsink, my thermal compound was applied correctly; I have no idea why it is so hot.

42C isnt that hot. Maybe if your were hitting the high 50s I would get worried.....

I'm just guessing, but I'd check to see if your RAM is rated high enough...you'llneed DDR266/PC2100, if there is DDR200/PC1600 you might get issues. 

Also, I'd check how hot your northbridge is. I've seen some cases where an overheating northbridge will make things go _very_ wonky.

---

### Post by Katman000 on 2010-01-27
Fixed main issue. I had to take out my smaller stick of ram as is was causing complications. Now my issue is crashes due to either heat or power. The AMD athlon xp 2400+ runs at 1.65V, but even at that setting, it can crap out. I'm lowering the volts to 1.625, as CPU-Z was saying that my voltage was 1.668. My idle is about 45 C, on a load it can crash. My guess is too much power is causing too much heat. Any other ideas?

I have a decent heatsink, running at 4500 RPM and a larger 80mm fan running at 2500 RPM.

---

### Post by llawwehttam on 2010-01-27
Try shoving it in a fish tank with baby oil.

On a more serious note make sure your machine's fans are all working well and if they have dust-filters give then a wash and dry. Make sure your heat-sinks are clean.

Apart from that you may want to get a new motherboard. The one must be ancient!

---

### Post by Katman000 on 2010-01-28
One fan is less than 2 weeks old, and the other is recently cleaned. My mobo doesn't seem to be the issue, it's also impossible to find a decent Socket A mobo anymore. I know it's time to upgrade, but I dont even have the cash for a $300 budget build at this point, I'm only in high school :P

Mobo is only 5 years old :D

My concern is that I either don't have enough RAM, or I need PC3200 instead of PC2700. I have 1GB of PC2700 RAM. 

Do I need more? Do I need PC3200? This is the last issue that I think I have with my machine, everything else checks out. I know it isn't a heat issue because the heat is max 45C on idle and I'm guessing in the high 50s 55-59C on a load. I have 2 fans on it and I'm not overclocking it.

I went to the Can You Run It? website and I meet all the requirements for Doom 3. I noticed my CPU was rated at 2.66GHZ. I'm still getting crashes on the game.

Any suggestion is appreciated :D

---

### Post by cascade9 on 2010-01-28
> **Katman000 said:**
> One fan is less than 2 weeks old, and the other is recently cleaned. My mobo doesn't seem to be the issue, it's also impossible to find a decent Socket A mobo anymore. I know it's time to upgrade, but I dont even have the cash for a $300 budget build at this point, I'm only in high school :P

Mobo is only 5 years old :D

I dont know...pulling a RAM stick fixed some problems makes me think that your motherboard has 'issues' at least. 

You wouldnt need $300 for a budget build. If yuo already have a decenish-power supply and case, you could probably get a motherboard/CPU/RAM for $150. 

> **Katman000 said:**
> 
My concern is that I either don't have enough RAM, or I need PC3200 instead of PC2700. I have 1GB of PC2700 RAM. 

Do I need more? Do I need PC3200? This is the last issue that I think I have with my machine, everything else checks out. I know it isn't a heat issue because the heat is max 45C on idle and I'm guessing in the high 50s 55-59C on a load. I have 2 fans on it and I'm not overclocking it.

No, you dont need PC3200. That is DDR400, you really only need DDR speeds to be the same or better than FSB speed (need is actually to strong a word, you can quite often get away with running slower RAM than your FSB, but it does give a performance hit). PC2700 is DDR333, thats more than your FSB, you should be OK. 

> **Katman000 said:**
> 
I went to the Can You Run It? website and I meet all the requirements for Doom 3. I noticed my CPU was rated at 2.66GHZ. I'm still getting crashes on the game.

Any suggestion is appreciated :D

Rated at 2.66Ghz? LOL. Its actually 2GHz. I was actually interested enough to go to the 'can you run it' website, but theres no way I'm going to d/l some poxy tool. (and it probably will end up being windows only). 

I'd seriously try the old trick- take the side off the case, get a desktop (house) fan and point it into the case. Turn on the fan, turn on the computer. I'd try this becasue while 45C isnt too hot...its still hotter than it should be IMO. 

I still think that you might very well have a northbridge issue. You might also have power supply issues. I've seen both cause nasty, intermittent problems.

---

### Post by Katman000 on 2010-01-29
Northbirdge problems, oh crap...

I tweaked my RAM settings and I hit a sweet spot, but I still get crashes, so based on what you are saying, it probably is a mobo issue.

****...

You're tight the Athlon XP 2400+ is a 2ghz CPU, but because of AMD's rating system the 2400+ stands for the performance level of an equivilent P4 CPU. I have all my BIOS setting set just right so I guess Can You Run It? is just getting weird. It's not malaware or anything, but because it is designed for gaming I do believe it is windows only, but it may have linux support, it's just a Java applet.

Because my machine is so old, (still using socket A :P) I would need a new CPU, RAM, Mobo, PSU, Vid Card, and Hard Drive. All amounting to about $300, for a decent build.

---

### Post by cascade9 on 2010-01-29
> **Katman000 said:**
> Northbirdge problems, oh crap...

I tweaked my RAM settings and I hit a sweet spot, but I still get crashes, so based on what you are saying, it probably is a mobo issue.

****...

It _probably_ is a mobo issue, but I've seen all sorts of things make things crash. Its possible its not...without actually have a nice bundle of parts its pretty hard to tell though. 

I'd seriously ty the case fan trick if you havent. Its also possible...I'd almost say probable from what I know of socket A, MSI and the age of the computer..that your heatsink paste on the northbridge has dried out, and instead of conductor heat, its being a blanket. 

> **Katman000 said:**
> 
You're tight the Athlon XP 2400+ is a 2ghz CPU, but because of AMD's rating system the 2400+ stands for the performance level of an equivilent P4 CPU. I have all my BIOS setting set just right so I guess Can You Run It? is just getting weird. It's not malaware or anything, but because it is designed for gaming I do believe it is windows only, but it may have linux support, it's just a Java applet.

Yeah, the 2400+ is meant to be measured against the P4, but who says that 'can you run it?' is doig that? It could be rating against celerons (so that people who know they have a x.xxGhz machine dont complain 'your software rated my 2.4Ghz celeron as 2.1Ghz! You sucketh!' etc). But its software, and software can be..funny...at times,l so who knows?  

> **Katman000 said:**
> 
Because my machine is so old, (still using socket A :P) I would need a new CPU, RAM, Mobo, PSU, Vid Card, and Hard Drive. All amounting to about $300, for a decent build.

Nah, you wont need all that. Just CPU/RAM/motherboard. Maybe the power supply (which, BTW, I have seen cause crashes like you are getting as well). 

Your current HDD will run in a modern motherboard (the majority of them have PATA ports). If you got a motherboard with onboard video then you wont need a card..you can always upgrade later if you want. 

An Athlon II 240 is about $50, you can get a nVidia 8100 chipset motherboard for about the same, 2x512MB DDR2 is about $25 (2x1GB for about $40). 

It would blow the socks of the old 2400+ as well. :) 

That isnt even cherry picking for the absolute cheapest stuff, you could drop that much further if you wanted....

---

### Post by Mze on 2010-01-30
Make sure you have thermal paste evenly applied on your processor before adding the heatsink.

---

### Post by cascade9 on 2010-01-30
> **Mze said:**
> Make sure you have thermal paste evenly applied on your processor before adding the heatsink.

Actually, you dont need to. The heat from the CPU and pressure of the heatsink weight and clamp will flatten out the heatsink paste. 

Its not a bad idea to spread the heatsink paste around, but its not 100% needed.

*edit- for a northbridge, southbridge or GPU it is though. ;)

---

### Post by Katman000 on 2010-02-02
From what I am seeing, I think we have cut the possible issues down to motherboard northbridge, or heat. Possibly RAM, but I highly doubt that.

I have an idea that I dont really like, but may be necessary: May I need to reformat my hard drive? I know that hardware switches are really important, it could be possible that its the OS that just isn't handling the switch, creating a hardware incompatibility, within Windows XP.

I think it isn't impossible, but what do you guys think?

---

### Post by Katman000 on 2010-02-03
I figured out what the issue was, im pretty sure this time.

My mobo supports my processor, but not with my old stock BIOS, I downloaded the new one, wrote it to a floppy disk, as well as created a MS-DOS floppy. I boot into the DOS floppy, put in my BIOS disk and run the bios program amifl827.exe. I dont really know what to do after that though.

I got a screen that needed me to input the current bios, and the new bios file. I'm a bit confused, can anyone help???

I have googled the issue but found my situation not really adressed. I noticed that a lot of updates had .bin files while mine comes with a .1C0 file, probably because the bios is v. 1.C. Any suggestions?

---

### Post by cascade9 on 2010-02-10
> **Katman000 said:**
> 
I have an idea that I dont really like, but may be necessary: May I need to reformat my hard drive? I know that hardware switches are really important, it could be possible that its the OS that just isn't handling the switch, creating a hardware incompatibility, within Windows XP.

I think it isn't impossible, but what do you guys think?

Not impossible, but its more likely that you've got a BIOS/CPU issue. *scratches head* you shouldnt have, the XP2400+ is the same as the 2200+, 2100+, etc., just a higher internal speed. 

Neat little guide o how to flash your BIOS here-

[http://freepctech.com/pc/001/006.shtml](http://freepctech.com/pc/001/006.shtml)

I'd try running a LiveCD and see if that crashes before trying the format/reinstall. ;)

---


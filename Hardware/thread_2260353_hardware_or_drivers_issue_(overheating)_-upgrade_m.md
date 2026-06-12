---
title: "hardware or drivers issue (overheating) -upgrade might be needed"
date: 2015-01-11
forum: Hardware
---

### Post by mastablasta on 2015-01-11
So i did plenty of reading and also some testing and it is still not really clear to me what is causing the issue. I was wondering if there is a way to solve this without extra investment.
So i have the E3300 dualcore 2,5 Ghz and an old AGP card ATI Radeon 9600 256MB. System is running Kubuntu.

now i can run games like Supertuxcart, Tux racer, Minecraft, UFO:Ai, Urban Terror (at leats this one used to run fine) and a few others an dolder ones just fine.

but i can not run jDoom or Enemy Territory. both crash after a short time. it seems that everytime the game demands a bit more it crashes after a while. 

Not so long ago i had an overheating issue. turns out the CPU & heatsink got loose. So i got a new paste, cleaned it replaced the past, reattached the heatsink firmly. i have psensors installed now and the CPU temp is moving between 40 and 50. quite high i guess. but not overheating according to CPU specs.
I turned the psensors loging on but it is so stupid that it doesn't keep the log from previous session. however i do have it setup to start on boot and after the ET crashed (works perfect for a few minutes and then it just freezes) i did a hard reset. by the time computer rebooted psensors showed the CPU temp 69C and rapidly droping being coooled by the fans. so it looks like overheating could have caused the freeze. 

question is why is it overheating? why the fans are not spinning to cool off the CPU strongly (i can't hear any spin increase)? additionally sometimes computer would just freeze when switching windows (like Alt+tab). the computer then boots into session at the resolution it crashed and this despite the fact that:
1. desktop effects are set to turn off when program is full screen (the alt tab switch on crash would suggest otherwise).
2. desktop session should load a clean session yet it somehow remembers the resolution upon crash.

i am not sure what si connected with what but it seems to me as if the opensource radeon drivers are poor poorly made and it all looks like they and kernel are actually causing the overheating of CPU and ultimate crash. or could it still be the harwdware failure? the reason i suspec the drivers is because onyl games that use certain openGl seems to cause the crash. but others work fine.

diablo 2 opnGl in wine seems to work ok. i plan to somehow move Morrowind from another PC to see if that one works good as well.

---

### Post by TheFu on 2015-01-11
Get the monitoring to save all the MB temps you can  - also add fan speed (for all the fans) to the monitors and save that too.  I'd connect CPU clock speed to the monitoring as well.  

Of course, removing any dust from inside the case and ensuring there is sufficient airflow **through** the case is important too. If there is excessive vibration, that could cause the CPU and CPU-fan to loosen. Is it ok?  I'd re-read the CPU coolant application instructions ... they say the most common error is applying too much. Is that possible in this situation?
Modern CPUs should slow down before thermal protection makes them stop.  I don't recall when that was added.  I recall burning up CPUs in the 1990s because there wasn't any protection at all.

Entire system cooling matters, not just the CPU.

Drivers could also be an issue - I dunno.  Just got X-wing running in DOSBOX here on a Celerion in a Chromebook, so high-end gaming really isn't my thing. The faster machines are too busy running 10 VMs each.

Sorry, no direct answer, just things you already know.

---

### Post by Mike_Walsh on 2015-01-11
I think you'll find thermal cut-out was probably added round the turn of the miliennium; I have a 2001 (approx) 'Tualatin'-core Intel Celeron, and that's got thermal protection. I'm guessing Intel, at least, were beginning to 'wise-up' to the burn-out problem.

What are you running there....laptop, or desktop? If it's a desktop, it should be a fairly simple matter to, if necessary, add some extra case fans; obviously, just make sure they're set to draw air out of the case, not blow air in... Should help.

If it's a lappie, not so simple...


Regards,

Mike.

---

### Post by mastablasta on 2015-01-12
well i've read that the intel stock coolers are not so good. still they should work in this case. it's not like I am running anything major on it. 

it's a desktop. yes I could just replace the cooler but that would cost me about 40, 50 EUR and it would be pointless to do it if it's not the heating issue. 

when I had the heating issue the cooler got detached on one side and it wasn't cooling it properly. I could then see the temp increasing up to the point when it just shut down (it didn't freeze). so after closer look I noticed the problem then followed 3 guides including the Intel guide on how to reapply the paste. seems to be reapplied ok. as I can see how the fan can cool off the CPU in psensor (it has a nice graph and you can see it cooling off while the fans spin down).

then again it could also be the GPU or just GPU driver. is there any way to know using software? I was thinking turning off all desktop effects then running the game in windowed mode and monitor the CPU graph.

---

### Post by mastablasta on 2015-01-28
OK so i've managed to get my hands on what seemed like a descent 80mm case fan. unfortunatelly the cable was not long enough to connect it to the motherboard. I am now "hunting" for an extension (haven't found a cheap one locally yet). 

anyway I decided to turn the fan around (the only way I could then connect it to the motherboard) so that the air is now blowing in. If I understand correctly the PSU is pulling the air out with it's huge fan. the fan is mounted in the back, the PSU is on top.a classic tower setup.

1. will this even have any effect or would it be better to get the extension and turn the fan around (to pull the heat out). there is no space for fan on the front side of the box (I mean there is space but it's blocked by some panel in the front)
2. the fan monitoring software (psensor and lm-sensors) show the 2000 rpm fan turning at speeds from -1 (?!) to almost 19000 RPM - what the hell is that supposed to mean?

The CPU does seem slightly cooler. though still running between 40C on idle and about 56C (sometimes 60C) working temp. I did another dust cleaning. this Intel Celeron supposedly does run a bit hotter. perhaps it needs a better cooler, but I am not sure how much I still want to invest into this old PC.

one thing I did try is to play supertuxkart on an unrelated notebook and it crashed there as well. proprietary drivers and all components different. so it seems it might be a game issue. I plan to do some testing in wine and perhaps some other FOSS game. the setup should at least handle some lighter & older games.  DOS games work fine :P

---

### Post by TheFu on 2015-01-28
You want airflow from the front-bottom of the case to the top back of the case.  Put the fan in the front sucking air in. What you've done now will probably cause overheating of other components, thus reducing their life span.

You can snip the fan power cable and extend it using any small wires you have laying around. Solder would be good, but those 20 cent twist connectors are fine too.  I've had to do this myself.

If you want to stress a CPU, have it calculate pi for a day.

---

### Post by mastablasta on 2015-02-02
i need to check the front of the case, but i think there is no intake place. there is a place to mount the fan but the front side is closed down. also i won't be able to access the screw holes... :confused:

so best i could do is get an extension and pull the hot air out the back as well. i Will have another look at this. maybe i need to throw the whole thing away....

now it pulls air in the back and then out the top (via PSU).

---

### Post by mastablasta on 2015-02-04
decided to test with Ultimateboot CD and for osme reason DVD/CD drives were not registering. I opened the box and checked the contacts. I tried to boot before I closed it and I noticed that the fan on GPU wasn't spinning. well no wonder it was crashing.

so I turned it off and checked the contacts there as well. on another reboot it started to spin. but kind of slow. I now plan to clean it over weekend, see if the whole thing improves if not I guess I need a new card. 

either AMD HD 5450 

or AMD R5 230

would that be good enough for some light and older games on descent frame rate - like left for dead and such? and you tube videos.
should I go with NVidia? and if s,o which one of those is descent in this price range?

if this will not work I guess i am also searching for a descent AGP card. they are quite hard to find these days understandably. I have a single core Athlon 64 with 1 GB ram and AGP plug. at the moment it has Radeon 9200. wehile this card works descent on windows XP the Linux performance is crappy. so I was thinking about upgrading that cheaply and getting an additional 1 GB ram to make it a descent PC for light gaming and internet browsing.

all this should cost me about 170 EUR. while any other solution like doing full upgrade (motherboard, RAM, an APU) is closer to 400 EUR at least for 2 PC. and I doubt they would be so much faster than these. besides If components work they are OK and there is no good reason for new PC then. right?

---

### Post by TheFu on 2015-02-04
I don't know about import taxes where you are, but for $120 here, you could get a dual core atom with built-in GPU that wuold almost certainly be faster than that Athlon 64. I saw a MB+APU deal for newer Pentium for $87 a few days ago at slickdeals. Don't remember the Pentium - Intel has been reusing those for systems that run like Core i3 boxes. Slickdeals is the website.  $20 will get you 4G of RAM.  While not perfect, you can compare CPU performance at a few different websites.  [http://www.cpubenchmark.net/cpu_list.php](http://www.cpubenchmark.net/cpu_list.php) - close enough for average users.

Any system using AGP needs to be replaced for a few reasons - heat, noise, power, performance, flexibility ...

---

### Post by Mike_Walsh on 2015-02-04
> **mastablasta said:**
> if this will not work I guess i am also searching for a descent AGP card. they are quite hard to find these days understandably. I have a single core Athlon 64 with 1 GB ram and AGP plug. at the moment it has Radeon 9200. wehile this card works descent on windows XP the Linux performance is crappy. so I was thinking about upgrading that cheaply and getting an additional 1 GB ram to make it a descent PC for light gaming and internet browsing.

My system is an old HP/Compaq desktop. I have the same CPU as you, an Athlon 64. I uprated the 1 GB RAM it came with, to 3 GB....which made a colossal difference. The motherboard only has a single PCIe x 16  slot, which is the very old 1.0a standard; can't find any current cards that are still compatible. So, it's being used by a USB 3.0 adapter card, since I don't have a PCIe x 1 slot for it. I'm using the onboard ATI Radeon Xpress200 graphics chip, which, miraculously, still works perfectly. The hardest use mine gets is watching videos, and using OpenShot to edit videos; gaming is NOT my scene!

Mind you, with a 1024 x 768 monitor, it's not being overworked...

Closest I ever got to gaming was about 15 years ago, when I had a go with Doom and Driver2 on a mate's original PS1; but the 'bug' never bit with me!

I'm no expert on these kinda things; I did attempt to install a GeForce GT 610
 
[http://www.asus.com/uk/Graphics_Cards/GT610SL2GD3L/](http://www.asus.com/uk/Graphics_Cards/GT610SL2GD3L/)

with passive cooling last year before I switched from Win XP to Ubuntu, but according to the onboard diagnostics HP had supplied with this thing, the PCIe slot was faulty....and all I kept getting was snail's pace response when I tried booting up with it, so there was some kind of issue there. I know most people think these passively-cooled cards are useless; but HP fitted massive fans and large air-intakes on this thing, and as I said to you a few months back when you had the overheating problem with the CPU, given the size of the stock cooler on my Athlon (it's a huge hunk of aluminium, with a hefty CoolerMaster fan), it's rare that my Athlon gets much over 40c.....even in mid-summer. And stripping things down, & re-seating the cooler with new paste dropped things by a further 5c; unless psensor is telling me porkies..!

If you've only got an AGP slot, you're going to be a bit limited as regards choice. Possibly the only thing you could do is to shop around on ebay, amazon, etc, and see what you can find. There ARE still new 'old stock' items out there that must have been sitting in the back of warehouses for years, but like The Fu says, they're very power-hungry compared to more modern PCIe cards, so.....can't really think what else TO suggest, apart from replacing the mobo, as and when funds permit. But I gather that's NOT really on the cards for you at the moment.

>  [COLOR=#000000]besides If components work they are OK and there is no good reason for new PC then. right? [/COLOR][COLOR=#000000]
[/COLOR]
Couldn't agree more. I can never see the point in throwing away stuff that still works perfectly okay. And while some of our worthy forum members are in the enviable position of being able to upgrade hardware as and when they want to (*sigh*), unfortunately others, like you & me, DO seem to be working at t'other end of the scale, I'm afraid..! :roll:

My 2005 Compaq was my sister's cast-off when she upgraded last year. And my even older 2002 Dell Inspiron lappie used to belong to my Mum; she replaced hers 4 years ago.....admittedly it's had LOTS of TLC. But they're both in perfect working order, and do everything I ask of them, so.....why chuck away and replace? Pointless.....


Regards,

Mike. :)

---

### Post by mastablasta on 2015-02-05
i don't know. hard to decide. at the moment I am just thinking. the old PC with 128MB AGP card and 1 GB ram server us well. but it used to have windows PX. something happened, possibly a combination of malware and the fact that the system disk was from 1998) so we restore it by installing Kubuntu low-fat on slightly newer disk partition that was sitting empty there. and the issue is that the card under Linux doesn't really perform well. 
 thanks you both for advice. it seems atoms are preety close but low power consumption.
 what I plan is to give my old PC and the one with AGP card to the kids for some light games. while I get a newish one. the PC I use is also this Athlon as at the time I bought it as place holder until I could gather somecash. by the time I had the money for replacement (e.g. phenom, Athlon dualcore etc), the socket didn't fit anymore to those that were on the market. I was thinking about getting new atoms, A4 or even A6, but no matter what I always get to around 200 EUR a piece. here I calculated I could upgrade 2 for that money. I need to do another check of the market.
 here is what I have:

**main PC **(here is where before I planned to change the CPU)
 Ahtlon 64 3200+ 
 4 GB DDR2 RAM
 Radeon HD 3650 512 MB ram, PCI-e
 is still running on windowsXP for now. the card, ram and CPU might not seem much by today's standards, but I can play various old games. League of Legends, Oblivion, Far cry, Left4 dead, Minecraft runs nicely, some strategy games... basically most stuff up to arorund 2010 will run nicely, 2012 stuff i play needs some tweaking but nothing new will porbably run. definitely nothing that need directX11. I think Skyrim should also run with some tweaking. since I don't have much time these days I mostly play maybe an hour or two a week some minecraft with my son or some Unreal Tournament 2004 or a quake3 engine based game (eg. padman or ET). the PC has 19" monitor usually running at 1280 x 1024.

---

**the other one **that is now having issue with crashing should actually be quite descent PC. it was assembled from very old parts and some new tech. the upgrade was very cheap.
 Celeron E3300 2.5 Ghz dual core
 1,25 GB DDR ram
 Radeon 9600 XT 256 MB ram, AGP
 here I could replace 1,2 GB DDR with max 2x1 GB DDR2. the motherboard has a PCI express where you can add a card. I think it can run either PCI or AGP but not both. not sure at the moment. would have to check the manual. PC has old, but good monitor running at 1680 x 1050 I believe. the current card (if it wasn't messing aruond with me) should run old games from 2005, 2006 relatively good. at least it did on windows. I ran Oblivion on med-high settings with it.

---

finally **the old PC**. only the chassis and the now nonworking disk (though smart tests seem to be indicating it is still good, so maybe it was just malware afterall). we got this one in 1998. it used to be a Pentium2 400 Mhz, the it got an upgrade to Celeron 1.6 Ghz using a socket upgrade. but after the motherboard gave in it received the current state:
 Athlon 64 3200+
 1 GB ddr2 ram (not sure how many Mhz it has...)
 ATI Radeon 9200 - 128 MB, AGP
 so this is all that needs upgrade (well apart from the first one which is actually running fast enough once it boots). 
 perhaps you are right. perhaps it is really time to donate these to someone that would need them. or just do some min upgrade. the monitor on this one is old 1024 x 786 LCD. I remember when I bought it it cost me 600 EUR. but I needed it so much because of my eyes and the old CRT made my eyes hurt.

---

[B]upgrade options
[/B]
 I was thinking maybe getting AMD R5 for the Celeron & some DDR2 ram - that would cost me about 70 EUR
 And then maybe I should dump the really old one. though the option I was thinking about before was a descent AGP card upgrade (maybe good used one) and 2 GB ram. which would cost me close to 60 EUR. I could get some newer SATA drive and all together would then be close to 200 EUR. the power consumption would be quite big so in the long run it might not be a cheap upgrade.
 if I exchange both it would cost me close to 400 EUR. and that's if I reuse the boxes and PSU (which are still relatively new)
 the import tax is not that much. especially with USA. the issue is VAT tax. the would just add 23% to stuff  during weekend I might have some time on my hands to go through this again and do some calculations. 

 the biggest problem I have is knowing how much I actually profit from getting newer PC and also how to know which CPU/APU is fater and how well it can perform. it takes time to go through reviews. various comparison sites don't say much. it seems many new APU still do not perform as my main computer. while I am searching something that would have at least that good GPU performance and possible a much better CPU performance.
AMD A4 is weaker (gpu), A6 is close I believe. AFAIK Atoms have weaker GPU. Celeron U = GPU is weaker. so I am more than happy to get any advice on combos like TheFu suggested. 

I was also exporing mini itx but they are quite expencive if you want a bit of performance. and the issue there is lack of upgrade options.

---

### Post by TheFu on 2015-02-05
> **mastablasta said:**
> VAT tax. the would just add 23% to stuff

That sounds like robbery to me!
Make friends with someone traveling to your part of the world and have them bring stuff that is below the VAT threshold, then leave it behind.  Entering the USA, there is an $800 exemption on goods brought in, for example.  That is a huge, extremely powerful, PC or 3 netbooks.

Have you considered having only 1 PC and using the others as remote display devices?  For non-video stuff, that works great.  You can probably get away with RaspberryPi type desktops that way.  Intel announced some PC-on-a-stick devices for $75 at CES this year. Should be available next month.

I held out for 5 yrs after AGP and DDR2 was dead and thought that was a long time. I think it was in 2008 when I finally bit the bullet and got a DDR3 system with PCIe/x (never remember which) which was a C2D.  I've retired that box and my recent purchases have been cheap items - $99 AMD E350 APU and a Chromebook for $200 with a Celeron mobile CPU that runs faster than the C2D retired above.  My most powerful systems are headless - no monitor, keyboard, mice.

OTOH, there are subtle issues that only you know with your setup.

---

### Post by Elfy on 2015-02-06
and I have jailed all the offtopic stuff

If there is anything of importance with regard to the thread - you'll have to repost it. I'm not wading through all of those to find on-topic information.

Thanks

---

### Post by mastablasta on 2015-02-06
right, we got carried away.

I am looking for Linux compatible CPU+GPU combo or APU that would have the similar or better GPU power to Radeon HD 3650 and a descent CPU for light gaming, watching you tube etc

Intel has more power in CPU but I am not convinced of their GPU part. besides they seem pricey. AMD GPU card I think maybe some R5 come close but are not that cheap. in AMD APU maybe A6 come close. Celeron U and Atoms seme to have stronger or comparable CPU, but their GPU is weak for any light gaming (e.g. old games) though they are natural candidates for media center. but Rpi already does that job just fine.

I am also checking Pentium G series, but the motherboards seem pricey (admittedly didn't look around that much yet). and the Pentiums are not that cheap either.


I was thinking upgrade might be cheapar in the short term, but having 3 or 4 PC pulling 300 or 400W each adds up. so energy efficient would be nice. no GPU's that need their own PSU please in the suggestions.

finally I am not at all familiar with NVidia as I never used one.

benchmark - let's say left for dead, stalker and such play nicely on the card. that gives me a bit of info to know where I am at with GPU power. numbers don't mean much to me at the moment.

---

### Post by Mike_Walsh on 2015-02-06
> **Elfy said:**
> and I have jailed all the offtopic stuff

If there is anything of importance with regard to the thread - you'll have to repost it. I'm not wading through all of those to find on-topic information.

Thanks

Point taken!

Apologies, Elfy; we DID get a wee bit carried away. Probably more suited to the Cafe, I feel, upon reflection...

Regards,

Mike. :oops:

---

### Post by Mike_Walsh on 2015-02-07
Right, then.....back 'on-topic'.

Having a think about this, you say you're OK with the idea of an APU, and you've got no problems with AMD (good man!)

How about this one, for consideration:-

[http://www.amazon.co.uk/AMD-A6-6400K-Richland-Processor-AD640KOKHLBOX/dp/B00CPLGFM4](http://www.amazon.co.uk/AMD-A6-6400K-Richland-Processor-AD640KOKHLBOX/dp/B00CPLGFM4)

It's an A6-series, the 6400K, with dual 'Richland' (Bulldozer architecture) cores (no hyperthreading, though), and the Radeon HD8470 GPU built-in. Even converting to Euros, I believe that should be well within your budget.

More detail here:-

[http://www.cpu-world.com/CPUs/Bulldozer/AMD-A6-Series%20A6-6400K.html](http://www.cpu-world.com/CPUs/Bulldozer/AMD-A6-Series%20A6-6400K.html)

There's some halfway decent mobos for the FM2 socket, down the bottom of the Amazon page. Both the MSI 'Micro' ATX and /or either of the two featured Gigabyte boards ought to work nicely for what you want, I feel. Yes, it'll mean buying new RAM, I'm afraid, but DDR3 is so ridiculously cheap nowadays, that it wouldn't add very much. You can get two sticks of DDR3 for what I pay for one of DDR1.

I'm recommending this for consideration because I'm seriously thinking about getting one myself; rebuilding my old Compaq with a new mobo, APU + RAM, and possibly a new PSU (though the one in here is a 400W one that replaced the original about 3 years ago, so it should be OK, really.....it doesn't get very heavy use with me). The 6400K uses slightly less power than the Athlon, anyhow, (for somewhat better performance) so I don't see a problem there.

It's not SO 'cutting-edge' that the Linux kernel won't recognise it, but it's got much better instruction sets than what either you or I have been used to, plus a fairly healthy speed increase.....all for a pretty reasonable outlay.

Food for thought perhaps? Of course, it goes without saying that it has to be YOUR decision at the end of the day; only you know what you actually want to do with it..... :-k


Regards,

Mike. ;)

---

### Post by mastablasta on 2015-02-09
that's the one i was looking for as well. i haven't managed to go webshopping yet. too many problems to be solved during weekend. besides kids wanted to play.

Anyway i was thinking A6 - 6400 K. even the weaker one 5000 that is more oriented toward mini-itx seems to give out a descent performance though boards are hard to find. as a matter of fact it seems like the only descent solution that is not too expencive. board probably needs at least 4GB ram if not more since the GPU shares the RAM or how does that work?

heh hyper-threading - wiki:
> In 2013 Intel dropped SMT in favor of out-of-order execution for its Silvermont processor cores, as they found this gave better performance

well i guess as long as the performance is descent hyperthreading is not that important.

i wonder what the drawback would be in using such an APU. it is certainly cheaper than CPU+GPU card. and you can always add a card later on if needed.

---

### Post by Mike_Walsh on 2015-02-09
Well, now...

Doing a bit of research on t'web just now seems to indicate that the A6-6400k APU dedicates between 768 MB - 1 GB RAM to the GPU side of the chip, so; I'd agree that you would want at least 4 GB to run most of what you want to use it for.

This old girl of mine has 3 GB, and performance is very good for what I do with it, especially with a single-core CPU (but then, I'm not in what you'd call a hurry these days! :lol: No, I'm quite happy with her, really); 256 MB of that goes to the ATI Xpress 200 chip for video, yet it runs Unity quite happily, with NO hiccups that I can remember. If I want to increase this by 1 more GB, I'm looking at about £45-50. I have 2 x 1 GB, and 2 x 512 MB. DDR1 max size is 1 GB, and the board's got 4 slots.....you do the maths. Basically, I've got to replace 50% of the RAM, to get a 33% increase; doesn't make a lot of sense, does it?

No doubt there ARE drawbacks with such a set-up (there's drawbacks to everything, one way or another), but to me, it looks a pretty good set of features. I don't want to go any higher than a dual-core; I simply cannot justify the extra cores with my 'workload' (which isn't THAT high). At most, I might be using the GIMP, with streaming audio going, and/or doing a bit of video-editing with Openshot, with the browser open (no more than 4-5 tabs). I'm NOT a 'gamer' (not even a LITTLE bit...)  What on earth do I want with an i7-4770k, or something similar? I'm never going to use even HALF of its capabilities...!

You can pick these Athlons up for a song nowadays; it's hard to believe they hit the market at somewhere around the $450-500 mark when they were released back in mid-2003..! And how Intel could EVER justify some of their chips exceeding $1000 over the years beats me...

Regards,

Mike.

---

### Post by mastablasta on 2015-02-11
I managed to check local stores and came to this configuration:

[TABLE="width: 300"]
[TR]
[TD]GA-F2A78M-DS2[/TD]
[TD]mobo[/TD]
[TD="align: right"]54,00 €[/TD]
[/TR]
[TR]
[TD]AMD 6420 K[/TD]
[TD]apu[/TD]
[TD="align: right"]58,00 €[/TD]
[/TR]
[TR]
[TD] [/TD]
[TD]frame[/TD]
[TD="align: right"]26,90 €[/TD]
[/TR]
[TR]
[TD]Kingston DDR3 1866 4GB[/TD]
[TD]ram[/TD]
[TD="align: right"]41,40 €[/TD]
[/TR]
[TR]
[TD]1tb[/TD]
[TD]disk[/TD]
[TD="align: right"]65,00 €[/TD]
[/TR]
[TR]
[TD]LC Super silent 600W[/TD]
[TD]psu[/TD]
[TD="align: right"]47,40 €[/TD]
[/TR]
[TR]
[TD] [/TD]
[TD]total[/TD]
[TD="align: right"]292,70 €[/TD]
[/TR]
[/TABLE]


maybe I would go with another frame and add a fan to it  which would cost me about 10 EUR more. so that's about 310 EUR for new PC. 

but the issue that makes me wonder if it's worth it is this: [http://www.cpu-world.com/benchmarks/AMD/A6-6420K.html](http://www.cpu-world.com/benchmarks/AMD/A6-6420K.html)

now if we can believe these sites, the CPU I am getting is only slightly faster than what is installed now. ok ram would be faster and I would get USB 3.0 (finally, as no PC I have, has it now :-) and probably the GPU is better. but on the other hand I do not get that much. I need to check if I can get this kind of configuration cheaper for 100 EUR in neighbouring countries.

because otherwise it would be a lot cheaper to get two sticks of DDR2 and add a newer card (should cost about 80 EUR altogether). I mean if performance would be only 30% or 40 % better then it is not worth buying a new PC. however for that old Athlon that currently has a single ram stick this would be a better solution. rather than trying to upgrade it. unless I can find a descent AGP card then even that one with a bit more ram would work descent.

---

### Post by TheFu on 2015-02-11
Why buy a new PSU at all - you certainly don't need 600W.
What's with the new HDD or "frame"?

Aren't you going to "swap" the MB?  That should mean all the old components like PSU, case and HDD get reused.

Plus my E350 APU was soldered onto the MB - did APUs stop coming with the MB? It has been a few years or is this a CPU?
I've been doing some research for a cheap replacement Plex/NAS server and came across some new dual core Celerons and Pentiums. They might hit 54W, but average is 6W. The Passmark numbers are 2x a 1st-gen Core2Duo. Of course, with Intel GPU the gaming performance would be weak.  AMD really has the best option for cheap gaming systems.

---

### Post by mastablasta on 2015-02-11
well I started thinking about full replacement and erasing & donating the old PC's.

> **TheFu said:**
> Why buy a new PSU at all - you certainly don't need 600W.

I could maybe leave that one out. I was thinking if I did some upgrades later on it could come in handy to have some extra power. besides thehsop I looked at didn't have much price difference (a few eur) between 400 W or 600 W.
> 
What's with the new HDD or "frame"?
Aren't you going to "swap" the MB?  That should mean all the old components like PSU, case and HDD get reused.


Current HDD is a 60 GB IDE HDD (the other one is green driver for data only). I would have to replace it with 1TB SATA disk. frame I meant case - the one I have is old and has no USB 3 ports  in the front. it also has no air intake on the front or the side. I could maybe get away with same case. the two front USB  plugs are not working now anyway. I am preety sure I attached them as per motherboard instructions yet they do not get recognised. maybe they are version 1 or something. originally this box had some AMD 1600mhz that was closed at 866 or something like that. I replaced the motherboard, CPU and re-used the rest of the parts and added a GPU I had lying around and a new PSU.


> 
Plus my E350 APU was soldered onto the MB - did APUs stop coming with the MB? It has been a few years or is this a CPU?


some still do (the smaller ones Atoms, E series replaced by some A series & Celeron U) others are sold separately. you have FM2 socket for AMD and I don't know which one for intels. you buy a motherboard and then pick A6, A8 or A10 various versions with various clock speeds and GPU chips, while I think A4 mostly comes soldered on board. I think the A8 have similar performance to i3, still weaker and use more power. but on the other hand they are not that much weaker than they are cheaper. and let's not forget that AMD boards are cheaper than intel's as well.


> 
I've been doing some research for a cheap replacement Plex/NAS server and came across some new dual core Celerons and Pentiums. They might hit 54W, but average is 6W. The Passmark numbers are 2x a 1st-gen Core2Duo. Of course, with Intel GPU the gaming performance would be weak.  AMD really has the best option for cheap gaming systems.

interesting but it seems (if we can believe these websites) that intel's GPU in Core i3 are not far off from these in cheaper AMD APU. Except that they have stronger CPU speed. of course one can always later ad a dedicated card.



additional question - if anyone knows - is PCIe 3.0 card backwards compatible? I mean with PCIe 2.0 socket?

---

### Post by Mike_Walsh on 2015-02-11
@TheFu:-

As far as I'm aware, the A6-6400k is just a regular, replaceable unit....just like any other CPU; just has the graphics built-in, is all. That's why you need a mobo with an FM3 (FM2?) socket:-


[ATTACH=CONFIG]259916[/ATTACH]


I do agree about the PSU, though; I honestly don't think mastablasta needs one, per se; but then of course, we don't know how old it is. IF & WHEN I get around to rebuilding my old girl, I shan't replace the one that's in here now; it's barely three years old, and at 400w, has ample juice for what I use her for. It just doesn't get very heavy use at all.

I may upgrade the monitor, though; the one I have now is 1024 x 768, and although it still gives a lovely, crisp, clear picture (despite being 10 yrs old), I think it's high time I treated myself to a new one.....my graphics projects deserve it!

-----------------------------------------------------------------------------------------------

@mastablasta;

Yes; without a doubt. I fitted a USB 3.0 card in my PCIe slot about a month ago. Gives me 4 ports@USB 3.0.....but I've tried 2.0 items in there, and it runs them with no problem at all. As I understand it, it's like memory; if you use slower RAM in a board that will handle faster stuff, it simply runs at the speed of what you have fitted. Backwards compatibility for USB is exactly the same. You could run USB 1.0 from them.....but it would take forever to do anything! :p

One thing I HAVE found is that you don't actually get the full 5 GBps they quote.....especially if you're running an assortment of differently-aged, different spec'd hardware. In my case, the biggest part of the reason is that my PCIe slot is the old 1.0a standard..!

I have a 10 GB file I regularly transfer. When the Seagate was in a USB 2.0 port, it would take 14-16 mins to transfer it. The same file, when plugged into a USB 3.0 port, now takes between 2-2.5  minutes. You can expect between 500-600% increase, which is well worth having for the cost of the card, and the 5 minutes or so it takes to fit it.

The card I've fitted also has headers for extra ports.....so if I can ever be bothered to (!), it's simply a case of fitting 3.0 ports on the front of the case, and hooking them up to the headers. No problem.


Regards,

Mike.

---

### Post by mastablasta on 2015-02-26
ok so I got another total crash, this time in minecraft. I hope I have time to investigate it better, but upon reboot psensor showed 51C. if it was over 90C it wouldn't cool down as fast. at least I think so.

so the issue can be anywhere else. either in the GPU, the GPU drivers or maybe even in sound drivers. it could also be the very old disk (though SMART shows no errors) or maybe the PSU has issues. the 256MB DDR ram stick is also ancient.  so many variables.

the system that is in place is actually good enough for what we do on it. it doesn't have to be better, stronger etc. ok the IDE disk (60GB) is a bit small (especially since I loaded some wine stuff). but still has about 13 GB free space left. and the ram is low. and though it is all strong enough if I had to choose these two would be the most needed upgrades.

with a new PC I would have a bit faster CPU, better GPU, less power consumption, more ram and all that. new upgrade options (PCIe slots) etc. however it would also cost me a lot more. so I think a better way would be to do the upgrade. save some money for other things or maybe for a better main PC. 

[SIZE=3]**my question: is there an error in my plan?**[/SIZE]

my upgrade plan would then be:
- get a new system SATA disk. - 1 TB (there is not much difference in price between 1TB and 500GB disk. if you ask me 500GB should be about 30-40 % cheaper but is not.
- upgrade RAM - mobo can handle max 2GB of DDR2 677Mhz ram. I plan to add two sticks of DDR2 800mhz 
- upgrade the GPU card to  something like R5 230 1GB. I am open to suggestion if there is any nVidia in similar price range that performs as good. in the hsop I am looking for they dont' have much choice of NVidia in this price segment. anyway I do not know which PCIe version is on the mobo but I am guessing this is backwards compatible?

so what i am looking for it a nice PC for web browsing, playing youtube videos in full screen (doesn't have to be HD) and some light gaming (minecraft, supertuxcart, enemy territory, jdoom, padman, ut2004, diablo2 and other old games).

if I decide or can afford new PC later on I can re-use many components. GPU can be reused in new PC, Hard disk can also be reused, ddr2 RAM can go in older box, the old GPU can go into older box if it will work ok.

---

### Post by TheFu on 2015-02-26
I would have cut bait long ago for something newer. That removes all sorts of issues, since computer components do have a lifespan. But that's me.  

I have 2 old C2D systems lying around here that haven't even been booted in 3+ yrs because they suck too much power and I've virtualized the tasks they did only another machine with a Core i5.  I've been removing systems here and virtualizing more, not trying to keep old systems running that use 50W more. Of course, if the machines need to be in different physical locations, virtualizing doesn't help.

30 sec ago, ordered a new MB and CPU for $126 total:
* Pentium G3258 - [https://www.amazon.com/gp/product/B00KPRWAZQ/](https://www.amazon.com/gp/product/B00KPRWAZQ/) - $63 - Passmark 4028
* Gigabyte GA-H81M-HD3 Micro ATX LGA1150 - [https://www.amazon.com/gp/product/B00F8AFMDC/](https://www.amazon.com/gp/product/B00F8AFMDC/) - $63
Reusing everything from an older C2D E6600 box - HDD, case, PSU, RAM.  Comes with a stock cooler, which will be fine.  This build will replace an AMD E350 (passmark 760) that has been my Plex Server/Kodi and NAS - That E350 will become a pfSense router.  I'm looking forward to plex transcoding any midia on-the-fly for cheap near-TV, silent devices.

Looked at an AMD build too:
* GIGABYTE GA-AM1M-S2H Micro ATX AMD Motherboard
* AMD 5350 2.05Ghz Quad-Core Processor (2602 passmark)
which was $91 - so an option with a stronger GPU if more gaming is planned. The MB wasn't as nice and the Passmark was about 50% less, which is very significant. NewEgg has combo deals on the AMD with RAM ($120) or with a 1TB HDD ($130). The AMD power use was a lower.
[http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-AMD-Athlon-5350](http://cpuboss.com/cpus/Intel-Pentium-G3258-vs-AMD-Athlon-5350) has a comparison.

---

### Post by mastablasta on 2015-03-02
decided to go with an upgrade: 
2 GB DDR2 ram
1 TB disk
AMD R7 240 2GB GPU

if it solves the issue, then it's a good enough machine .
if it doesn't solve the issue, i will replace the motherboard and CPU as well.

---


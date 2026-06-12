---
title: "Problem with AMD GPU driver for RX6600 XT on Ubuntu 20.04"
date: 2021-08-22
forum: Hardware
---

### Post by silentquote on 2021-08-22
I just bought an AMD RX6600 XT card and after plugging it in my PC, it seems no hardware acceleration is detected. I only notice that when I open 0ad, it says I am using llvmpipe graphics driver, and I am not able to find the root cause for this.

I tried without AMD GPU driver, with both AMD proprietary drivers pro/non-pro editions but with no success. Furthermore, I also tried to add amdgpu.dc=0 but that ended me with a black screen.

I also tried to install a fresh Ubuntu 20.04, but I ended up with the same situation.

Has anyone been able to successfully run an RX6600 XT card on Ubuntu 20.04?

---

The issue is now fixed. The problem is limited to 0ad installed from official Ubuntu repos and snap. I downloaded the game from PPA xtradeb/play, and I can get decent FPS with high graphics setting. I had to also play around with the game throttling to hit higher FPS. If I disable that, it goes really high, but I hear my PC Fans screaming.

I also tested some games from steam, and they were working flawlessly with 200-300 FPS.

---

### Post by mastablasta on 2021-08-24
what kernel are you using?

```
uname -a
```

just few days ago we got similar report over here. but HWE kernel and AMDGPU pro drivers should work. we don't know what the opensource AMDGPU are not working (yet) maybe kernel in 20-04 is too old.

btw what is the price on these nowadays? here they sell them for an arm and a leg if you can even find one. 850 EUR+ (approx 1000 USD+) are the prices for AMD cards.

---

### Post by silentquote on 2021-08-24
I found out that the problem was only limited to the version of 0ad I was using. Both the version from the Ubuntu repo and snap had this issue, they were just using the wrong driver.

I downloaded it from ppa:xtradeb/play, and I could hit 60 FPS and I learned that the game has an FPS throttling which limited the FPS. I pushed the limit a bit and I could get insane FPS, but I also hear my Fans run like crazy. I kept the throttling at around 70 FPS because my screen is 60 HZ anyway.

And regarding my card, I was lucky and got mine for €420 here in Germany. I think the cheapest I can see now is €480. At launch day there were plenty around €420 as well, but they were sold out almost in the same day.

And I have removed the AMD proprietary drivers, and I am running Kernel version 5.11.0-27-generic.

---

### Post by mastablasta on 2021-08-25
As soon as this covid craziness is over (current wave), it seems i need to do a road trip to Germany. I need to check the Preis Jäger, maybe Austria is cheaper as well. 480 still beats 850, even with fuel to get up there in person. Also actually i need a lower end card, but they have crazy prices here as well. and the AMD ones are all out anyway.  

yeah sometimes you need to add latest game version to work with new software. especially with these projects that are actively evolving. well happy conquering i guess. glad you sorted it out. don't forget to give steam games a try as well. i read yesterday that some of these new ray tracing and DLSS stuff is coming to proton. unfortunately my old GPU chip can't even handle Vulkan. so i am currently playing CS:GO at 30 FPS. :D

---

### Post by silentquote on 2021-08-30
Not sure where are you located. But if you can make the road trip, you can order one and make them ship it to a post office. It can stay there for up to two weeks and maybe if you call them they can keep it for longer.

The prices for RX 6600XT still reasonable. I still see some under €500. You can try to check in geizhals.de. They have good tracking for the whole category, so you do not have to track each model separately.

I have tried Steam already. That's where I knew the card was working. I started playing CS:GO.

Last time I played CS, it was around 15 years ago. So the world has changed. :D

I find myself now need to get a new screen and keyboard to have a proper gaming setup. My current screen is 34" 60HZ. I am looking to try one of the high refresh rates. I never used any gaming hardware, so I am just stepping in. I already got myself a new mouse which is, regardless of being a gaming mouse, is a breeze to use. It is Razr DeathAdder V2 Pro. I was really surprised about the ergonomics. I never thought about that before, and it really feels much better than the Dell mouse I have.

---

### Post by mastablasta on 2021-09-01
yeah gaming mice are more ergonomic. Lenovo Legion M500 mouse is also well made in that respect. i just got Razer Deathadder essential last week. material is not as good as on my previous no name // local brand, but sensor is good and shape is also well made so it fits into the arm well. i also suggest getting a good mouse pad, so the mouse glides nicely over it. Razer has OpenRazer drivers for linux ([https://openrazer.github.io/](https://openrazer.github.io/)) and some GUIs for additional mouse set up. i am using kernel driver for now as it is working fine for my needs.

i got a mechanical keyboard Logitech G413 (silver one) 4 months ago  as it was "on sale". it is not as comfortable for prolonged typing, but what a change in response time in games. they use their own switches (Romer-G red) and they take a bit more force to press, but are very responsive and you can register the key press well with fingers. i actually wanted to buy Cherry MX brown (which was about 40 EUR more), but they ran out of models that have our language letters on them. I think mechanical ones are worth the money. also both of these are well supported in linux and they don't have any blinking RGB stuff, just single colour backlight.

now i just need to upgrade the GPU card and monitor. maybe in January if there is any sale. i am after those that use less power, so GTX1650 or RX770 would be more than enough for me.

yes, CS:GO is completely different than the old CS. it fun to play - easy to learn, hard to master. major issue are cheaters in multiplayer. but since i bought prime and asked valve to review my trust factor (it was low before) it has been OK in match making. at least i can't see any cheating on match review. before we had to constantly kick people off the team for obvious cheating. i think that might have given me bad trust factor. 
we sometimes matched with higher ranks, so of course they were better. i mostly play it with my kids on private "listen" servers, but during weekend i would sometimes play match making (MM). the other annoying thing in MM is that most people if you queue random are silent so you don't know what they are trying to do and they mostly just die. they won't even ping, they would often type. Eastern Europeans like to do it like that for some reason. German, Austrian, Danish, Italian & Sweden players as well as those from Balkans are more chatty so it is easier to pull something off with them or have general fun in communication. 

as long as you don't take losses too serious and don't run into cheaters, you will still have fun. to me it is something to unwind after all the stress at work.

---

### Post by silentquote on 2021-09-02
I installed Openrazer and some of it's GUI tools. Unfortunately, I had to update its firmware because of a freeze issue I was having every 5 seconds or so. I could only do it in a Windows machine. The GUI tools are a good step, but they lack a bit. I wanted to set some profiles, which was not doable there. I ended up running a VM and pass-through the mouse there and use the Razer software in Windows. I set some profiles, and I am using them ever since. My only surprise after struggling so bad with the DPI is that I found high DPIs are kinda useless. I ended up with 800 DPI to make the mouse useful. I wonder why do they use those freaking high DPI sensors if we end up not using them.

I am currently in a hunt for a keyboard. I am looking for a 75% keyboard with low latency that have a German layout. I like Keychron, but it has a high latency and I cannot find an alternative so far. Logitech is a good brand, unfortunately there is no 75% keyboard yet. I would have bought it if they have one. I want to get the Cherry MX brown as well. TBH, after trying the new mouse I realized It's worth to upgrade those stuffs. I never used a gaming or ergonomic mouse before, and I felt like I missed a lot. This what made me want to get a new keyboard as well.

Speaking about GPUs. I am not sure if you would find any old GPUs ATM because they are kinda does not exist and when they do, they are with crazy prices. I think the RX6600 is the best option available ATM, at least here in Germany... Compare the prices with a 3060 for example, and you will see what I am talking about. I am happy to get that card after almost 6 months with 1030GT. I was not even able to run Wayland with that card. It sucks.

BTW, I am wondering where are you from?

In regard to CS:GO, I am playing the dead guy character so far. It is a bit better with the new mouse, though. I am currently looking to buy a new monitor as well. Mine is 60 Hz and I have a feeling I am seeing things too late. If I look at replays when I get killed, I see some shots which never appeared to me at all while playing. I already ordered a Dell S2721DGFA. I am expecting to get it on Saturday, so let us see how difference would it make.

I also do not know anything about the CS:GO environment. Sometimes I hear people speaking about cheaters, but I have no clue how do they cheat. Maybe when I spend more time with it, I will figure those things out. I never use my Mic at all, as I always play when my kids are asleep. Half an hour before bed.

Anyway, if you have any suggestions for a good 75% wireless gaming keyboard, let me know.

---

### Post by mastablasta on 2021-09-03
i believe it is a combination of High DPI and low sensitivity. so high DPI means you can move mouse pixel per pixel and low sensitivity is how fast it move i guess. i used mine on 2400DPI and on Razer it is probably default 5600 DPI or whatever it is. this is good for fast reaction (e.g. shotgun, SMG, but not so good for long range).

so you use short keyboard. i suggest checking youtube for reviews. there are a couple of good ones out there. if keys and switches on keyboard are standard you can exchange them with local langauge. say get a UK one and exchange with German. or sometimes they sell "engraved". i was worried about that but you can actually see letter quite clearly on some f it is necessary. 

i am from Slovenia, and we use "SLO keyboard variant", which means we create ö, ü, ë and such using the top left tilde key or Alt+Gr, but generally most latin letters are displayed in one way or another as we often need to write in foreign langauges. but the layout itself is actually called UK layout.

yes the lower end older model cards are hard to find or very expensive. but these high end models are a bit too much for me i think. but then again if there is nothing else around. i mean even GTX 1650 is a bit overkill for my needs, so if i got that or higher i am sure PC will get more occupied by the younger son who is using onboard AMD chip at the moment and can't play Doom 2016.

in CS:GO casual they are easy to spot. they will aim through wall. if you play match making you can see them flick toward you and hit (auto aim). some are trying to hide it by making every 3 shot hit. some are full rage hacking. looking at the floor, spinning (anti aitm so you cant' hit them), flicking and hitting head shots only. for example with rifle even pros have about 40-60% average HS. so if you see someone after plenty rounds having 90%, 100% HS rating and plenty kills, you they are very likely cheating. 

better monitor will show more. if you get hit but a guy looking the other way they likely have auto aim. in MM you can review and slow down the demo recording (demo review is really handled strange). anyway due to the way CS:Go and source engine works it is not uncommon to see someone shooting and hitting what should be a miss. i was once almost completely convinced they guy used wall hack when he hit me, but i reviewed the demo before reporting. and i am glad i did. he just made a lucky "flick shot". which even he admitted in text chat, but i didn't see it at the time.

mic is a must. kids won't wake up. even if you do something else. some more loud action in the room. :) you can die often, but if you can tell the others there are 4 enemies on your end, then the team knows there is only one at the other and they can push and take the site. or they will rotate fast if they are defending. i had games where i had only 2 kills and 8 assists, but i kept saying where enemy is and how many and where they are going and we won because of that. my team rotated fast enough, so they can stop them.

---


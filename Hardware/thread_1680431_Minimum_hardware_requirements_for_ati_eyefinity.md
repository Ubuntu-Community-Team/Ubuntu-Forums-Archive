---
title: "Minimum hardware requirements for ati eyefinity"
date: 2011-02-02
forum: Hardware
---

### Post by wwbdd on 2011-02-02
I have a triple monitor setup running under an nvidia 9800GT and a quadro NVS 295 (pcie x1). I have things setup with xinerama so that I can use all three of my monitors like it was one big huge thing.  So while this setup serves my purposes in many ways, there are also some annoyances:

1) xrandr doesn't work with xinerama
2) compositing doesn't work across two cards. So no compiz, and worse yet, no transparency.
3) fullscreen flash videos (youtube, hulu, etc.) don't work well at all.

I gather all of these issues stem from either xinerama or two video cards.  So I'm thinking it may be time to upgrade to an ati card that can run an eyefinity setup.

I don't really do that much that puts much strain on my graphics card(s).  I don't do a bunch of 3d stuff, in fact, most of what I do is in a terminal window or a web browser.  Occasionally I do some GPGPU stuff, but not all that much.

So basically what I am trying to ask here is what kind of hardware is recommended for someone needing to power 3x1920x1200. Can the cheap radeon 5450 do the trick? Or should I look more towards the mid range cards like the 5770?

I ask here on ubuntuforums because I am running this setup exclusively on linux.  I don't do any gaming, so I don't care how many FPS I get on CoD at 1920x1080 at max settings. Nor do I care what the windows experience rating is. I just want a graphics card that can power my 3 monitors without some of the aforementioned issues.

---

### Post by 0004tom on 2011-02-04
I can't comment on the 5450 with 3x1080p screens, but I don't see why it wouldn't, I can however say that the 5450 will happily power 3 1680 x 1050 with out problems. You will also need either a monitor with a Display Port input or a DVI/VGA to DP adaptor.

---

### Post by janthonywj on 2011-02-06
Bump. I have a similar concern. I'm trying desperately to find all the info I can but the web is FLOODED with outdated it information on this. I'm a pretty good searcher, but this one is getting to me. 

My specific situation: I'm going to be throwing a system together this next week or two. I am currently running on a laptop with a second monitor, but the laptop has become outdated. I have the budget to get 3 LED HD monitors to go with this system. Most of what I will be doing is serious multitasking from watching online video, movies, programming, web browsing, threads, blogs, etc. As most of you know it makes a world of difference to be able to have many windows in view when programming, and I like to have one monitor streaming a video or movie usually. 

I highly doubt I even load Windows on the system at all, and if I do it will most likely be in a VM. So Linux support for the video card is the biggest concern. I have very little experience with these high end video cards on Linux. (My laptop has an Intel card, and dual screens is a whole different story.) I've never had much of an issue with either brand on a laptop with Linux.

I prefer to only spend the money on ONE card rather than two. From what I take, nVidia has been better with Linux support than ATI/AMD in the past. I also have heard from friends that the recent Catalyst 11.1 release has caused serious problems with support. I've read that Catalyst 10.7 was to bring Eyefinity to Linux, and that would be great. I do occasionally play games like Starcraft 2 and CoD, and would LOVE if I could get the Eyefinity experience. HOWEVER, I have seen VERY few success stories of Eyefinity working on Linux. I would like a very simple answer of if it is actually supported or not. Should I refrain from getting the latest 6000 series cards? Is there even a way to get one nVidia card to run three monitors? I also understand that I will need a ACTIVE displayport to DVI adapter, which is not a problem. I also don't care much about sticking to open-source over proprietary, just whatever works best for me. 

If I can't get Eyefinity to work after I get an AMD card, what is the worst case situation, will I be stuck to two monitors? Should I make a safer bet with my money and get multiple cheaper nVidia cards and go that route?

I have a budget of $1500 so I should be able to build a pretty bad-A system here. I'm thinking the latest ASUS board with a AMD 3.5GHz Quad Core proc, 6GB/s Sata drive, and 8GB DDR3 1600 RAM.

---

### Post by 0004tom on 2011-02-07
> **janthonywj said:**
>  I've read that Catalyst 10.7 was to bring Eyefinity to Linux, and that would be great. 

Thats correct. And it has done.

> **janthonywj said:**
> I do occasionally play games like Starcraft 2 and CoD, and would LOVE if I could get the Eyefinity experience. HOWEVER, I have seen VERY few success stories of Eyefinity working on Linux.

This sadly is the case with most games and an ATI/AMD card, as the wine devs, build it with use with nVidia cards. And in my experience if you seek help trying to get a game running with FGLRX they just say get nVidia and stop responding.

> **janthonywj said:**
> I would like a very simple answer of if it is actually supported or not. Should I refrain from getting the latest 6000 series cards? Is there even a way to get one nVidia card to run three monitors? I also understand that I will need a ACTIVE displayport to DVI adapter, which is not a problem. I also don't care much about sticking to open-source over proprietary, just whatever works best for me.

Eyefinity does work, if you search though my post I've post several pictures on the forums here, and even some gameplay of A 0.D. nVidia do have 3 screen setups now, but they require 2 GTX 4xx IRC. The display port your also correct, however you can also use DP to VGA adaptors, that are a little more pricey but ever one of these adaptors on the market work with eyefinity.

With regards to the 6xxx series cards, there not yet fully supported in linux, I don't think, but will happily use the 5xxx series drivers. Which is also the case in windows. You just get a watermark on the screens saying unsupported hardware which can be removed with a simple script.

> **janthonywj said:**
> If I can't get Eyefinity to work after I get an AMD card, what is the worst case situation, will I be stuck to two monitors? Should I make a safer bet with my money and get multiple cheaper nVidia cards and go that route?

Correct, You will still beable to use 2 of the outputs if you can't get eyefinity working. The problem with 2 GFX cards in linux is that xorg can only use 2 or more if there pretty much the same card. I have a HD5450 and a HD6850 that happily power 6 screens in windows, however in linux one is not reconigsed as the cards are to different.

---

### Post by cascade9 on 2011-02-08
I know this is a silly answer, but its true. 

The minimum hardware requirements for eyefinity is a video card with eyefinity support. ;)  

> **0004tom said:**
> With regards to the 6xxx series cards, there not yet fully supported in linux, I don't think, but will happily use the 5xxx series drivers. Which is also the case in windows. You just get a watermark on the screens saying unsupported hardware which can be removed with a simple script.

New ATI/AMD drivers came out very recently (26/01/2011), and now the 6XXX card have support with linux.

---

### Post by 0004tom on 2011-02-08
> **cascade9 said:**
> New ATI/AMD drivers came out very recently (26/01/2011), and now the 6XXX card have support with linux.

Well there we go, the 6xxx series is supported on linux now. However alot of the FGLRX users are still getting the watermark, myself included.

---

### Post by janthonywj on 2011-02-10
> **0004tom said:**
> Well there we go, the 6xxx series is supported on linux now. However alot of the FGLRX users are still getting the watermark, myself included.

0004tom, I want to thank you for your reply. One of the many who make the Linux community so great. 

I couldn't resist. I've ordered a complete system and went with a steal of a buy on the whole thing I think. I got a Sappire ATI HD 5770 with support for Eyefinity for $119 w/ $20 rebate on top and an Active DP to VGA adapter (Also made by Sappire) for $26. Thank you NewEgg promotion codes. I ordered 3 LED monitors with tiny bezels as well. I'm giddy. 

I feel like if you say I can at least get Eyefinity running so I can use all three monitors during my daily multitasking life than it will be worth it, even if the games won't span the monitors. I'm confident I'll at least be able to PLAY the games, which is already an improvement. I might invest in Crossover games and see if that helps with support. If all else fails on the game front, I can bite the bullet and maybe boot Windoze, just maybe, I might just not play. ;)

(Triple monitor mounts are OUTRAGEOUS on price, I'll build my own thanks.) 

Soon to be running:

AMD Phenom II X6 1090T Black Edition Thuban 3.2GHz Socket AM3 125W Six-Core Desktop Processor 
CORSAIR Enthusiast Series CMPSU-650TX 650W ATX12V / EPS12V 
SAPPHIRE Active DisplayPort Adapter 100924 DisplayPort to DVI Interface
ASUS Crosshair IV Formula AM3 AMD 890FX SATA 6Gb/s USB 3.0 ATX AMD MB
Mushkin Enhanced Silverline 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1333 
SAPPHIRE 100283-3L Radeon HD 5770 1GB 128-bit GDDR5 PCI Express 2.0 x16 
3X Acer S211HLbd 21.5'' 5ms LED-Backlight LCD Monitor Slim Design (Eyefinity!)
Western Digital Caviar Black 1TB 7200 RPM SATA 6.0Gb/s 3.5" 
COOLER MASTER Storm Scout Case (Low red lighting)
Order Total	$1,301.90

I'll post back with a success story hopefully.

---

### Post by Fxkrait on 2011-02-10
looks like an awesome build, and i would love to have that tri monitor setup. Especially with some of those 30" monitors...would be amazing.

---

### Post by janthonywj on 2011-02-10
> **Fxkrait said:**
> looks like an awesome build, and i would love to have that tri monitor setup. Especially with some of those 30" monitors...would be amazing.

I wanted to get the same monitors in a 23 or 24 inch version, however the price was 120 more (40 a piece) for the extra inch or two of viewing space so I would have had to.change something to stay within $1400 budget. It wasn't worth it. I went to the local electronics store to check out the monitors and this one looks great. I plan to upgrade this setup in the future with another video card in CF with one 42 inch screen or so above these three, for video and news channels streamed online and gaming while working purposes. 

I agree though, with unlimited funds, I'd go with like 5 30 inch screens all on one row and in portrait. I think an odd number works better so you don't have a bezel in the center. One of those eyefinity 6 cards would work for that.

---

### Post by 0004tom on 2011-02-10
> **janthonywj said:**
> I can bite the bullet and maybe boot Windoze

Still alot of the game for windows don't fully support eyefinity, once in awhile we get a little gem, IE most recently Dead Space 2, with Eyefinity support out of the box. And this is on windows.

Most games, normally need some kind of hacking to config files, and in some case, need an app called widescreen fixer. Most notable game, can be any of the CoD series.

---

### Post by janthonywj on 2011-02-16
I came back to post a follow up. 

I have the build up and running. Went more smoothly than it ever has before. Everything as been so easy. I'm a little confused right now about eyefinity, but the new Catalyst 11.2 drivers are installed and running just fine. I don't see anything to complain about thus far, I should note though, all three monitors ran OOB. Ubuntu monitor manager configured them just fine. 

What I'm confused about is I don't have the option to "Create a group" as in the steps to configure Eyefinity. I can select the option to add them to a multi-display desktop, which I predicted to behave the same, although it still only maximizes windows to one display, leading me to think that the games running would do the same. 

I'm going to mess around with the options some more, but if anyone can lead me to the right direction, please do.

---

### Post by 0004tom on 2011-02-17
> **janthonywj said:**
> What I'm confused about is I don't have the option to "Create a group" as in the steps to configure Eyefinity. I can select the option to add them to a multi-display desktop, which I predicted to behave the same, although it still only maximizes windows to one display, leading me to think that the games running would do the same.

Yep thats all we get, the Create a Group option is windows only. Thanks to limitations in xorg. Most games will act the same some however will span all 3 screens, linux native ofc. Wine games no chance, I'm sure i've told you this already.

Ps thats me also answering your question in the other thread too.

---

### Post by janthonywj on 2011-02-17
> **0004tom said:**
> Yep thats all we get, the Create a Group option is windows only. Thanks to limitations in xorg. Most games will act the same some however will span all 3 screens, linux native ofc. Wine games no chance, I'm sure i've told you this already.

Ps thats me also answering your question in the other thread too.

I wonder if this will change with 11.04? I thought they were getting rid of Xorg and going with something else? Was it Wayland or something? Unity is just the layout of the desktop right? Eh, I could ask Questions forever. 

I'm going to see if it's possible to use Wine in windowed mode and see how big I can make the window with desktop effects off. That is, after I'm done making this sweet 5760x1080 wallpaper I'm working on. 

This setup is even better than I expected so far.

---

### Post by janthonywj on 2011-02-17
One thing I would like to note however, I don't see ANY difference between what I had with Ubuntu Display manager out-of-the-box and what I have with Catalyst.

---


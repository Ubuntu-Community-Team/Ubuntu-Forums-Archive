---
title: "Best notebook that will run Linux smoothly under $300?"
date: 2017-01-21
forum: Hardware
---

### Post by sebastiaan5 on 2017-01-21
Hello


Any advice on a new notebook 11.6 inch that will last 6h+ on battery?
What I need it for: programming (vim+plugins.tmux), watching a movie, searching on the net, ssh'ing, remote desktop (rdesktop/vnc)

What I think are good options: 

- Dell chromebook 11 (remove chromeOS)
- Pinebook


Any advice/tips would be greatly appreciated.

---

### Post by TheFu on 2017-01-21
I use my chromebook in that way today, but it was more than $400 (13in / 1080p / Core i3 / 4G RAM). Had an Acer C720 prior for about $250 (needed to swap out the SSD) to have a little more room.

For remote desktops, I have found x2go to be more convenient and feels 2-3x faster than any VNC version. Plus it uses ssh as part of the NX protocol, so security isn't an issue.  My same keys work.  People usually say it is like "night and day" in comparison. Plus, if you have a Linux remote client, it really is nice and almost like being there.  I like it enough that my primary desktop runs in a private cloud as a VM, accessible from anywhere in the world with ISDN or better connectivity.

Be certain you do the device specific research for the chromebook. Some run Linux/Ubuntu well, and others will never run it due to booting/BIOS issues.  Say with intel, not ARM for the best application support. In theory, it shouldn't matter, but ... 

The Acer C720 is very well supported and had a fairly fast processor (2955U w/ VT-x) for the time, but any CPU slower than that would feel sluggish, even with ChromeOS. My CB35-3350 is about 2x faster and gets better battery life.  I'm not on battery THAT much, but 6 hrs is routine - I don't think about it. If the screen is turned down, ACPI claims 10+ hrs, but I've never tried anything close to that.

Plus, be certain you can stand the keyboard.  It has been almost 4 yrs that I've been using chromebooks and I absolutely HATE the keyboard layout. Still miss the DELETE and F11/F12 keys. Sure, I've remapped them, but they put the F*&^ing power key where the DELETE key belongs!!!  If I came across that designer, I will not be responsible for the bodily harm that comes to him/her. Cannot say how many times I powered off the machine in the middle of editing stuff.  Took about 2 months before I got around to making suspend work (had higher priority chromebook issues), but that is just slightly less hassle than power-off.  The "search" becomes a "super" key for me. 

These days, I think I'd get a cheap Windows PC with similar features for about the same price - 2 yrs ago, that just wasn't possible.  2G of RAM isn't quite enough - 4G and I'm good.  Oddly, ran a Eee with 2G for many years with Ubuntu Server and fvwm - never had low RAM issues.

For me, chromeOS just doesn't provide quite enough control of the kernel for my needs. First issue was NFS, which mandated flushing ChromeOS - as you plan. ;)

---

### Post by sebastiaan5 on 2017-01-22
Thanks a lot for your response!

The Acer looks ver good but it's already 4 years old, I was also thinking of a cheap windows notebook/laptop but intel atom has mostly a fan and I actually want a fan less notebook so it would be very tin :p

---

### Post by mörgæs on 2017-01-22
4 years old is not necessarily a bad thing in the GNU/Linux world. It can take a little while for the developers to get complete hardware support because hardware manufacturers pay more attention to supporting Windows.

---

### Post by sebastiaan5 on 2017-01-22
Good point, but I think there are better options, I intend to use the netbook for quite a while so something newer would (I hope) be better. For example the 'Acer chromebook R11' looks very decent, although it doesn't have full Linux support yet.

---

### Post by TheFu on 2017-01-22
> **sebastiaan5 said:**
> Thanks a lot for your response!

The Acer looks ver good but it's already 4 years old, I was also thinking of a cheap windows notebook/laptop but intel atom has mostly a fan and I actually want a fan less notebook so it would be very tin :p

My current chromebook (CB35-3550) has a fan - barely hear it. It is only noticed when the system is doing work, not editing and not remote stuff on other systems. They use "heat pipes", so it is very thin - specs say 3/4inch, but it seems thinner. Weighs less than 3 lbs too.  Beautiful machine, actually.  The Celeron version for $100 less should be fast enough - the passmarks on that CPU, Celeron 3215U, are 1800-ish. Ah - they don't sell these anymore.  I would have easily been very happy with the 3215U rather than the 5015U for my remote access and video viewing needs.

Definitely watch out for Atoms.

Didn't really intend to suggest the C720 - just wanted to point out a known-to-be-linux-friendly machine. Mine is sitting bricked after I repaired the failed keyboard, broke the screen, repaired it and then couldn't get it booting (need about $50 in special hw to flash the bios).  Decided it was better to stop throwing money at a 768p system with a terrible keyboard. I really, really, really, missed the extra pixels. 1080p is my min these days and much prefer 1200+ for my personal sanity. In 2006, I owned a cheap Dell with a 1440p screen - before all the "hidef" marketing tricked people into thinking 720p was acceptable. 

If you decide to stay with a chromebook, a few suggestions before purchase:
* find the how-to for replacing the SSD on that exact model; many chromebooks have eMMC storage, not replaceable.
* find the replacement ROM for that exact model, review all the issues people have. [https://johnlewis.ie/custom-chromebook-firmware/rom-download/](https://johnlewis.ie/custom-chromebook-firmware/rom-download/) - I'd lean towards a full ROM replacement, if I couldn't find cheap Windows HW. 
* look for complaints about support - Toshiba is known to reject warranty issues with the screen and claim abuse. I'm extremely careful opening the screen only from the center and always carry it when opened from underneath, never by the screen.
* you might be able to run Ubuntu inside a chroot. Maintaining those is a slight hassle because it is different from normal maintenance. Forgetabout adding any kernel drivers if you do this. What the chromeOS kernel supports is all you have.

I'm not in the market for a new laptop, but if I were, cheap dell and asus would be at the top of my lists. I probably care more about pixels and the keyboard "feel" more than most people. As a tmux user, you know how important that is.

---

### Post by sebastiaan5 on 2017-01-22
As always very interesting answer.

The CB35-3350 looks very good tough, and has fine Linux support as I see on [https://wiki.galliumos.org/Hardware_Compatibility](https://wiki.galliumos.org/Hardware_Compatibility). It has a 1080p screen which is a great difference. It's a good option.

I would like to have a cheap dell, but dell and cheap aren't really good friends, the dell chromebook 11 looks quite well tough.


So what I have now is a choice between:

toshiba chromebook cb35 3550
dell chromebook 11
acer chromebook r11

---

### Post by TheFu on 2017-01-22
> **sebastiaan5 said:**
> 
So what I have now is a choice between:

toshiba chromebook cb35 3550
dell chromebook 11
acer chromebook r11

If you don't need the faster CPU, the cb35 C3300 is the same, just with a still good CPU for the Chromebook.  I made a mistake - it is a C3350, not C3550.  Also, watch out for most of the other models with similar numbers - the B3340 is a dog.   There appears to be A, B, C models ... but always, always, check the specific CPU and ensure that it provides the performance you desire.  I wouldn't buy these used. Laptops are one of those things where I want an honest, clear, history. A refurb would be interesting.

I have a few Acer devices. Something that wasn't my fault always failed or broke. For 1 device they had to send me 2 power adapters -  1st and 2nd were broke - made a hummmm, but wouldn't charge.  The 3rd has frayed and is held together by electrical tape since 3 months after getting it from Acer.  And the keyboard on the C720 started having dead keys after about 12 months. By 18 months there were so many dead keys that replacement was my only option. The "correct" method to replace it was $90 for a new keyboard/touchpad assembly ... for a $199 (new) device!!!  The keyboard uses plastic rivets, so removing it for replacement effectively means that superglue is needed to hold it in place.  Figured that you'd want to know with cheap machines, they use parts that are expected to break, quickly.  At least Acer does.  They are on my "never again" list (along with HP/Compaq).

Looked up the Dell's CPU - it is a dog. "Celeron N2840 passmark"  - you will feel it as "slow."  Watch out for Atoms like this. also, the Dell says it has eMMC storage - those are usually soldered on - NOT replaceable. I wouldn't touch it.  Tried to look for another option on the dell website, but they had like 10 "tracking" addons running, so I left.  I wasn't in a firejail browser in private mode at the time.

---

### Post by sebastiaan5 on 2017-01-22
I've did some further digging and found, what do you think of these?:

Dell i3147-3752SLV 11inch

[LIST]
[*][COLOR=#111111]Intel Pentium N3540 2.16 GHz Processor[/COLOR]
[*][COLOR=#111111]4 GB DDR3L SDRAM; Integrated Intel HD Graphics[/COLOR]
[*][COLOR=#111111]500 GB HDD Storage; No Optical Drive[/COLOR]
[*][COLOR=#111111]11.6 Inch WXGA (1366x768) LED-lit Screen[/COLOR]
[/LIST]
[COLOR=#111111][FONT=Arial]
Or 
[/FONT][/COLOR]
[COLOR=#111111]Asus vivobook E200HA[/COLOR]

[LIST]
[*][FONT=Arial][COLOR=#111111]Intel atom [/COLOR][/FONT]x5-Z8300
[*][COLOR=#111111]4 GB ram[/COLOR]
[*][COLOR=#111111]32gb emmc[/COLOR]
[*][COLOR=#111111]11.6 Inch (1366x768)[/COLOR]
[/LIST]

---

### Post by TheFu on 2017-01-22
For any x86 CPU, only you can determine if it meets your power, performance, and battery life. Search for the specific model of CPU and "passmark" to find that info.  I wouldn't touch any "atom" CPUs either. Could be handy to have VT-x support, right?

I wouldn't touch any machine with eMMC storage, but that is me.
I wouldn't touch any machine with less than 1080p screen resolution, but that is me.
I wouldn't touch any machine that weighs over 3.5 lbs, after having a sub-3lb machine.

And only you can decide about refurb vs used vs price.

As you can see, the choices really start to limit themselves.

---

### Post by sebastiaan5 on 2017-01-23
Good points, and I think the same, but I don't want to spend much money (I know right, I want the best but only cheap). I made up my mind and bought an asus vivobool E200HA for 150dollars I saw a lot of reviews and read about it, it has an intel atom which I need to be careful with but it's a quad-core which is quite decent. If I don't like I'll send it back and buy a Toshiba chromebook.

Thanks for all the good information!

---

### Post by deanium12 on 2017-04-17
Ignore the Asus Chromebook. Windows programs cannot be installed on it.

_[[COLOR=#333333]Yoga 11[/COLOR]]("http://pc4u.org/best-cheap-laptop-under-300-dollars-for-gaming-and-office/")_ may be a good choice. [https://www.amazon.com/gp/product/B01D11D8NA/](https://www.amazon.com/gp/product/B01D11D8NA/) 
The specs, 
1.83 GHz Intel Celeron N2940/ Intel HD Graphics (Bay Trail)
1366 x 768 Convertible Touchscreen
4GB RAM
128GB SSD

---

### Post by maddensteve19 on 2017-09-14
Found some useful suggestions on the internet, might be helpful for you: [laptops under 300]("https://www.techinpost.com/list-of-top-best-laptop-under-300-helpful-easy-guides/")

---

### Post by jasper31 on 2018-05-09
Dell XPS 13 9360
8th Generation Intel Quad-Core i5-8250U
8GB LPDDR3, 256GB SSD
13.3&#8243; Anti-Glare InfinityEdge Touchscreen FHD (1920×1080) Display
Intel HD Graphics 620
2.7 pounds
Read more: [http://www.bestlaptopninja.com/best-linux-laptops/]("http://www.bestlaptopninja.com/best-linux-laptops/")

---

### Post by jmlm-1970 on 2018-05-11
The minimum for today use:

Laptop, with detachable tactile screen and WiFi 802.11 AC (not b/g/n only) and USB 3 and SIM and keyboard with backlight for typing in the dark.

[SIM support is important because, who wants a PEN sticking out USB port, even if plugged with USB cord extension? Net PEN 4g USB spends lot of CPU percentage, precious to today internet]

Anyone know where to find it?

---


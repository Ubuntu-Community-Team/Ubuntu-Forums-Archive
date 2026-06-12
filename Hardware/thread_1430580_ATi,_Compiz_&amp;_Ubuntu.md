---
title: "ATi, Compiz &amp; Ubuntu"
date: 2010-03-15
forum: Hardware
---

### Post by Machwe on 2010-03-15
Hi everyone! 
This is the first of what will no doubt be many cries for help as I fully switch to Ubuntu.

I'm just about to buy a new laptop to run Ubuntu on. The laptop that I'm thinking of buying has a 512MB GDDR3 ATi Radeon HD 4650 graphics card.
Quite simply I want to know if an ATi card will really cause me lots of headaches, but more specifically - whether Compiz Fusion will run well (or at all) with it. 

I know that classically ATi support on Linux is much worse than Nvidia, I've been doing lots of researching and seeing lots of people saying don't bother with ATi because the proprietary driver is rubbish and the open diver can't do Compiz. But I'm thinking that these people are people who got burnt by ATi a long time ago and don't know the latest situation, since I have seen a few people recently saying that they've had no problems with their ATi card.

I'd really appreciate your opinion,
Cheers.

---

### Post by keep you kimi on 2010-03-15
i have 4670 with a proprietary driver and compiz runs fine
in fact everything works fine, but...


theres something i found called 'memory duplication and ATI R600/700 3D' by fedora

also called x.org memory leak... (i think it's the same issue...)

anyway, the problem means my system being idle still occupies 1.2-1.8 GB of memory. it just does not flush some x.org cache or sth...
nothing critical if you have 4Gb ram;)
but may be annoying if youre the type of person to take complete control over your system :D. 
I think it's already fixed in the kernel to come with next release of ubuntu, so not to worry too much...

just to let you know.

---

### Post by rastasean on 2010-03-15
There does seem to be ATI/ubuntu issues and maybe, just maybe, the next release will have a better version for these video drivers.

my 4350 did work but that was only until i re-imaged the computer. still don't know what broke the issue but clearly re-imaging does not resolve the issue since i have done that multiple times.

---

### Post by Machwe on 2010-03-16
Ok thanks.
Kimi: Unfortunately I am the OCD kind of person who has to have only the bare minimum of processes running at the same time but hopefully that issue will be fixed soon; and anyway I'm moving from Vista which idles at about 1.5G of RAM without any apparent memory leaks, so I should be able to cope ;) .

It would put my mind completely at rest if a few more people could say that their system is working fine with an ATi card.

Thanks everyone.

---

### Post by xhalarin on 2010-03-16
I'm running a Karmic 9.10 desktop with an ATI 4750 card and have had zero problems.  I haven't done a ton of gaming, but the games I have run haven't had issues. 

The biggest problem I've seen is some flickering when watching flash videos on Hulu.  I'm not sure if its a problem with the graphics driver or if the problem lies elsewhere.

---

### Post by Tikkyca on 2010-03-16
Everything works great on my ATI graphic card compiz runs awsome.

---

### Post by Machwe on 2010-03-17
Ok then thanks everyone I feel a lot better about this now. I've heard about the video flicker problem but there seems to be a few fixes floating around (like [this one]("http://ubuntuforums.org/showthread.php?t=754712"))

Thanks again; thread solved.

---

### Post by xhalarin on 2010-03-17
> **Machwe said:**
> Ok then thanks everyone I feel a lot better about this now. I've heard about the video flicker problem but there seems to be a few fixes floating around (like [this one]("http://ubuntuforums.org/showthread.php?t=754712"))

Thanks again; thread solved.

Thank you for the tip, I'll have to give that a try.

---

### Post by Failboat88 on 2010-03-17
I just installed Ubuntu and I'm not sure if my drivers are set up. I have a x300 ATI. What are steps I need to do to get the drivers and install them. My goal is to not use the ATI proprietary legacy driver.

---


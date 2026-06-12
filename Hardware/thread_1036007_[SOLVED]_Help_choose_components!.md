---
title: "[SOLVED] Help choose components!"
date: 2009-01-10
forum: Hardware
---

### Post by SS7 on 2009-01-10
I began fooling around with linux in '99.  I remember having lots of compatibility issues with various components before abandoning it to return to windows.

I have now setup ubuntu on my old tower, but would like to improve performance and would love input from you!  I want as seamless as possible hardware.  Current system is p4 2.4 (@2.8), 2x36g rapt raid, ati9800.  I have choppy video and compiz animation and program startup isn't as fast as I would like.

I will be upgrading mb, cpu, video, and a slave hd.  I don't want to run raid or overclock unless highly recommended.  Which mb, cpu, video would you buy if you were starting over?  I will need 2 epci, as I would like 4 displays in the future, if my budget allows.

This will be a desktop machine I will use for video playback, image manipulation, browsing, and compiling.

Thanks,
SS

---

### Post by markbuntu on 2009-01-10
I recently got a Biostar TA790GX A2+ mobo and a AMD Athlon X2 6000 cpu with 6GB 800mhz ram and it worked out of the box. All I did was plug the new mobo in and everything was recognized automagically when I booted it up.

HDA Intel ALC8800 7.1 audio ATI HD3300 gpu with vga, DVI-D and hdmi outs, Realtec RTL8111C ethernet, 6 USB, 6 SATA, 2IDE, 2 PCI2x16. 2 PCI2x1, 2PCI. It can do raid if you want and has overclocking bios and room for up to 16GB ram.

For the money (about $100) it was the best I could find. It is for ati gpu cards and my HD36501GB works great and I will be getting another one soon so I can play with crossfire and more monitors, and another 24 inch monitor. The ati drivers are improving with every release and as soon as xserver 1.0.16 is out with DRI2 which is any day now, the last of the flickering with compiz will be gone.

---

### Post by SS7 on 2009-01-10
Thanks for the reply.

I don't really have a budget set, but its critical that I achieve smooth video and fast program startup times.

I guess I need to know which cpu chipset I could most benefit from.  I've had intel for the last 3 PCs.  i7, dual, quad?  Any recommendations?

SS

---

### Post by crazyness003 on 2009-01-10
as of now, almost any setup is seamlessly itegrated. The one part you require, smooth compiz, will be achieved by the accelerated graphics. So right now January 10th, 2009, nvidia will give you the best compiz experience. esp if you use the beta drivers (so im told). But as markbuntu exclaimed, ATI is catching up at an incredible rate. So just about anything you throw at ubuntu wil stick.

I use AMD FX-55 with an EPoX mobo with nfoce4 chipset (i know, ancient) with a geforce6800 card, and I'm extremely happy with video display. with compiz and everything. (see sig for more details)

I think anything you pick will work RoXoR!

---

### Post by SS7 on 2009-01-10
Well I'm not well pleased with my current system performance.  I just wanted to make sure I got something quality for video..

The odd thing is, quality was much better with XP.  

Maybe display drivers?  How is the fglrx for my ati9800?  Should I have choppy animation and DVD playback?

SS

---

### Post by crazyness003 on 2009-01-10
The reason your current system lacks is the P4 chip :P also you have a nice card (no?) 
I havent read too many good things about ATI (drivers) and gnu/linux playing together. Its doable, but i never had the chance to mess with it (all my systems running *buntu have nvidia). 
It seems that nvidia is releasing more stable and more often than ATI. So if you're a die-hard ATI fan...look deep within the internets, post bugs, and maybe even write the ATI devs directly and demand better drivers!
If not, invest some time reseaching nvidia. Or look into using beta drivers or recompiling a kernel or module.
If you wanna keep your options open, i think there are mobos out there that support both X-fire and SLI. Look into those.
As for processors, Intel is the best for zOMG 1337 ROXOR! But it comes at a price. Whereas AMD's flagship is the Phenom II 940 is only $200-$300. It uses the AM2+ socket, so its compatible with any new AMD board out there. (ps. im an AMD fan. no offense).
I did read the new Intel i7 cores are VERY SWEET! but it boils down to $$$.
Hope this helps

---

### Post by SS7 on 2009-01-10
Yes, that was very helpful.  Thank you for your responce.

I'm no ATI fan, and would prefer to purchase a brand that supports the linux community.  Nvidia it is!

As far as the CPU, thanks for your recommendation.  I will be choosing the best option that makes economical sense.  I have no preference for Intel/AMD, either.  I will further research these and am stillopen to suggestions.  So much changes so fast, and I haven't kept up with the current technology.

Does the 64bit versions make a notible difference in performance?

SS

---

### Post by crazyness003 on 2009-01-10
to be honest: no. You are referring to the kernel right? 
If you're talking about processors, you can run a 32bit OS on a 64bit chip (been doing it for 5 years now). 
But if you're talking about installing Ubuntu 64 on your brand-spanking-new AMD64/EMT64 processor; Here is a list of notable differences:

[LIST]
[*] Number crunching (video encoding, compiling, any raw mathematical computations)
[*] Ram ceiling (32bit supports up to 4gb. 64bit supports up to 128 gb, i think)
[*] 64bit uses more Ram per process than 32bit. so that extra ram comes in handy.
[*] DO NOT RUN 64bit if you have little ram. it defeats the purpose
[*] 64bit kernel releases usually come in a little later, sometimes ranging from a minute to 3 days or longer.
[*] 99.9% of 32 bit apps have 64bit ports. So, if you find some obscure app, it may not run on 64bit.
[/LIST]
 
Other than that, i run 64bit just because i can. I like to use my machine's full throughput. Even If i just use it for web access and hacking.

---

### Post by SS7 on 2009-01-11
I think I'm going to rip some components out of my tablet and upgrade it instead of a fresh tower.

How well do you think the core2duo P8600 @2.4 w/4gb ddr3 1066 will do matched with a 1g nvidia chip?

I like this idea because both machines will be upgraded.

SS

---

### Post by SS7 on 2009-01-11
Nevermind, I see the socket is for notebooks..

i7 it is.

Thanks folks,
SS

---

### Post by DRF on 2010-02-02
I've not had many issues with the ati9800 graphics card so I'm a little surprised your finding performance quite so poor.

However since early 2009 ATI stopped releasing binary drivers (fglrx) for the ATI9800 (and older)cards and since then xorg has changed enough that I'm not sure if the last fglrx release would still work. Ubuntu should detect the ATI card and use the radeon open source driver to provide 3D acceleration but in 9.10 some people (myself included) have experienced some issues to do with the radeon module loading before the agp module, so you may want to read the bug report on the issue incase this is what your experiencing. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/468413)

Regarding what to get when you upgrade it depends on how you feel about open/closed drivers and how important performance is to you. Intel drivers are open source I've often found them to work well out the box but they are lacking in performance. Nvidia releases fairly good and regular binary drivers but the opensource support for nvidia used to be quite poor (but improving a lot recently with the nouveau project). ATI support the latest cards with binary drivers and release some specifications to aid the development of alternative opensource drivers.

Daniel

---


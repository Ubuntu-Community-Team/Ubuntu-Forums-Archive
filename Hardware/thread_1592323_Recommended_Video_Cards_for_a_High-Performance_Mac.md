---
title: "Recommended Video Cards for a High-Performance Machine"
date: 2010-10-10
forum: Hardware
---

### Post by rfkrocktk on 2010-10-10
I'm currently in the process of building a powerhouse machine, and the one thing I'm currently kind of stumped on is video cards. 

Here's basically what the machine is going to look like:
* Intel 980x i7 6-core processor
* 8GB Corsair XMS RAM
* ASUS Rampage III Extreme motherboard
* 2x Crucial RealSSD C300 128GB SSD (in RAID-0)
* 2x Western Digital Caviar Black 2TB HDD (in RAID-1)

The motherboard I'm getting supports both SLI and Crossfire (NVIDIA & ATI), and I want to be running two graphics cards if I can. Each graphics card should have at least one HDMI out, as that's how I'm driving my monitors. 

Should I go with NVIDIA or ATI? I currently have an NVIDIA card in my desktop machine and I'm pretty happy with the performance on it, even though it's an older card. If possible, I WOULD like to go with a free software solution, but performance is also very high on the priority list. Thoughts?

---

### Post by hawthornso23 on 2010-10-10
Lots of people here will tell you nvidia because in times gone by they offered better linux support. I don't think that is true anymore. I'd go with ATI if I were you.

---

### Post by Simian Man on 2010-10-10
If this is a Windows machine, I'd go with ATI.  If this is a Linux machine...why on earth would you want such a high spec Linux machine?

---

### Post by hawthornso23 on 2010-10-10
Ignore this.  How do you delete your own post? ... If you hover over the edit button it says edit/delete. But delete functionality seems to be lacking

---

### Post by PresenceofMind on 2010-10-10
lol nothing wrong with running an OS like linux on premium components. Afterall, linux will run super-quick......

As for GPU, ATi-based video cards are the fastest on the market at this time of the year. NVidia isn't bad either, but I think NVidia-based video cards do a damn slight better job of supporting linux.

Suggestions: ATi HD 5850, HD 5870, HD 5970
-------------: NVidia GTX 470 & GTX 480

---

### Post by rfkrocktk on 2010-10-10
> **Simian Man said:**
> If this is a Linux machine...why on earth would you want such a high spec Linux machine?

Correction:
> If this is a Linux machine... why on earth **WOULDN'T** you want such a high spec Linux machine?

:) 

Exactly. I basically want to be able to whatever I want to on my computer... you know, run 12 VirtualBox VMs at once, encode x264 at 1 billion frames per second... you know, stuff that everyone needs to do in the course of a day :)

---

### Post by Yellow Pasque on 2010-10-10
You should specify what you need from a video card so people can assist you better. Generally, if I was a gamer, I would get one GTX 460 1GB card and see if it handled my needs. If it didn't, I would get another one.

If I wasn't a gamer, I would just get a passively-cooled GT220 or lower-end GTX 400-series product to handle video playback.

> Lots of people here will tell you nvidia because in times gone by they offered better linux support. I don't think that is true anymore.
Have you ever tried to play HD content using ATI's xvba? It rarely works well with proprietary drivers and open-source drivers don't (yet) support video decode acceleration.

---

### Post by rfkrocktk on 2010-10-10
What I really need from a video card is the following:

1. Excellent driver support. If I'm going to be paying for a nice card, it had better play nice with Ubuntu and Linux in general. Also, I would greatly prefer a video card that has VERY good open source drivers, though if I have to go proprietary, I will.

2. Incredible rendering. I want to be running Compiz smooth as butter with an incredible framerate (>100fps at all times, if possible, even when playing videos and capturing the screen simultaneously). I also would like to be able to render 3D in software like Blender and have very good framerates for rendering. Also, I need to be able to cut, edit, and render 1080p video very well. HD playback is also very high on the priority list.

I might end up dual-booting to use SONAR Producer Edition for recording and mastering audio, as well as Premiere and After Effects. What do you think?

---

### Post by S.R on 2010-10-10
Dual ASUS EAH5830's..........

---

### Post by gordintoronto on 2010-10-11
> **rfkrocktk said:**
> 2. Incredible rendering. I want to be running Compiz smooth as butter with an incredible framerate (>100fps at all times, if possible, even when playing videos and capturing the screen simultaneously). I also would like to be able to render 3D in software like Blender and have very good framerates for rendering. Also, I need to be able to cut, edit, and render 1080p video very well. HD playback is also very high on the priority list.

I'm not certain of this, but I think all the things in Point 2 will depend on CPU and memory speed, and a cheap PCI-E 16x graphics card will be exactly as fast as an expensive one, for those tasks.

BTW, anything beyond 70 fps is completely wasted.

---

### Post by cascade9 on 2010-10-11
> **rfkrocktk said:**
> What I really need from a video card is the following:

1. Excellent driver support. If I'm going to be paying for a nice card, it had better play nice with Ubuntu and Linux in general. Also, I would greatly prefer a video card that has VERY good open source drivers, though if I have to go proprietary, I will.

2. Incredible rendering. I want to be running Compiz smooth as butter with an incredible framerate (>100fps at all times, if possible, even when playing videos and capturing the screen simultaneously). I also would like to be able to render 3D in software like Blender and have very good framerates for rendering. Also, I need to be able to cut, edit, and render 1080p video very well. HD playback is also very high on the priority list.

I might end up dual-booting to use SONAR Producer Edition for recording and mastering audio, as well as Premiere and After Effects. What do you think?

1- ATI probably has slightly better open source drivers from what I've seen, but I could well be wrong on that, I dont use nouveau very much. Your MUCH more likely to have issues with the open source drivers with SLI or crossifre than with a single card..... 

2- Compiz should be 'smooth as butter' with any modern video card/CPU/RAM setup. Rendering (with blender), editing video, etc, dont use SLI/crossfire (or even the GPU processing power of a single card) so multicard setups aret going to help there.  

HD playback? Go nvidia. Temüjins experiences are the same as might, XvBA doesnt work very well, VDPAU is mature and stable. Get a GT220, maybe a GT240 or a GTX460. Even the GTX460 is a waste for a non-gamer. 

It really doesnt soudn like you habve any reason to get dual (or more) video cards. If you really want to spend more money, get yourself a nice soundcard instead, at least that will be used.

---

### Post by PresenceofMind on 2010-10-11
> **rfkrocktk said:**
> What I really need from a video card is the following:

1. Excellent driver support. If I'm going to be paying for a nice card, it had better play nice with Ubuntu and Linux in general. Also, I would greatly prefer a video card that has VERY good open source drivers, though if I have to go proprietary, I will.

2. Incredible rendering. I want to be running Compiz smooth as butter with an incredible framerate (>100fps at all times, if possible, even when playing videos and capturing the screen simultaneously). I also would like to be able to render 3D in software like Blender and have very good framerates for rendering. Also, I need to be able to cut, edit, and render 1080p video very well. HD playback is also very high on the priority list.

I might end up dual-booting to use SONAR Producer Edition for recording and mastering audio, as well as Premiere and After Effects. What do you think?

I'd recommend using a GTX 470 or above(For ATi that would be a 5850 or above) for your high-end system....... That way you'd avoid any GPU bottlenecks and you'll be getting tons of performance from these cards both in Windows and Ubuntu..........and your PC can last longer without the need to change your video card.

Compatibility wise?....I'm confident in NVidia, but dunno about ATi (ATi does support linux but I don't know its effectiveness).

---


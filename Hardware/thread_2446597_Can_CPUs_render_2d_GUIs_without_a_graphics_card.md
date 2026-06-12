---
title: "Can CPUs render 2d GUIs without a graphics card?"
date: 2020-07-03
forum: Hardware
---

### Post by jcdenton1995 on 2020-07-03
Hello all,

So I can't find an answer to this question online, probably because its common knowledge.

Can a bog standard CPU render 2D GUIs such as a desktop envieroment without a dedicated graphics card, or alternatively an APU?

It seems crazy that someone who wanted to build a powerful machine but didn't plan to run any 3D graphical programs would need to buy a graphics card just to get a basic desktop graphical interface...

---

### Post by crip720 on 2020-07-03
Only my newest computer has  a GPU graphics card, the others don't.  Don't really find a difference in day to day stuff, maybe if bitcoin mining or working(not watching) on videos or heavy gaming .  Imagine there are a few CPUs without graphics capabilities, but they would be few and hard to find.

---

### Post by ajgreeny on 2020-07-03
I have been using an integrated graphics system for many years as as I am not a gamer needing high-end 3D graphics I have never noticed any problems at all.

Even the most resource hungry DE will generally run very happily on, for example, and intehrated graphics of an Intel i3 CPU as I have on a laptop I've been using since 2013.  No problems at all related to that, so don't worry.

And to answer crip720, there I think some CPUs that do not have integrated graphics, eg the AMD ryzen CPUs with a model number without a G at the end.  Of course, I may have misunderstood what I've read about them, so double check before making up your mind, if you're in the market for a new system or CPU.

---

### Post by oldfred on 2020-07-03
I do not game, so built this Haswell based system with intent not to use video card. I think all previous builds had CPU's without video.

But I made a mistake. Video in, on monitor was VGA or DMI-D and motherboard was displayport or HDMI out. So I used an old video card GT620 just for the ports.

But then found the Intel Haswell video performance specs were same or slightly better than the older  GT620, so found an adapter cable to connect motherboard & monitor directly.

But new video cards have much greater performance for those who want to game. 

Intel Icelake "Gen11" Graphics Are A Huge Upgrade Over Gen9 With Good Linux Support
[https://www.phoronix.com/scan.php?page=article&item=intel-gen9-gen11-clear&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-gen9-gen11-clear&num=1)

AMD vs Intel Integrated Graphics: Can't We Go Any Faster?
[https://www.tomshardware.com/features/amd-vs-intel-integrated-graphics](https://www.tomshardware.com/features/amd-vs-intel-integrated-graphics)

---

### Post by Yellow Pasque on 2020-07-03
Correct me if I'm wrong, but it seems like what you are asking is if you can use the motherboard's video output connection(s) with a normal Ryzen CPU without integrated graphics? The answer is no.
It would be nice if AMD made some higher end CPU's with integrated graphics for use cases like yours.
It would also be nice if AMD made inexpensive, passively-cooled, discrete GPU cards, but they've stopped doing that. (RadeonHD 6450 was probably the last good card they made like that.) I guess the profits aren't there and they don't want to cannibalize APU sales.

---

### Post by jcdenton1995 on 2020-07-04
> **Yellow Pasque said:**
> Correct me if I'm wrong, but it seems like what you are asking is if you can use the motherboard's video output connection(s) with a normal Ryzen CPU without integrated graphics? The answer is no.


Yes that's exactly what I was trying to say. It's odd because I'm sure there are some users who are into some more geeky stuff, and require a powerful CPU, but who aren't into the gaming side of things or 3D applications.

Surely the iGPU of a high powered APU (which I guess is what we are talking about) would only need to occupy a tiny proportion of the die, if it's only purpose was to render 2D desktop environments and such.

So it seems the only option for the aforementioned users is to buy a high end CPU and pair it with a low end GPU, which isn't such a problem cost-wise as I know there are some dirt cheap GPUs, but from a build perspective its less than Ideal to require a chunky graphics card sat there in your case, taking up much more room than would be needed for a barebones GPU that just served the users basic needs.

---

### Post by Yellow Pasque on 2020-07-04
Well, there are low-profile, fanless GPU's, New example: [https://www.newegg.com/asus-geforce-gt-1030-gt1030-2g-csm/p/N82E16814126203](https://www.newegg.com/asus-geforce-gt-1030-gt1030-2g-csm/p/N82E16814126203)
And if I wanted something really cheap/basic, I'd use something like: [https://www.amazon.com/Diamond-Multimedia-Radeon-GDDR3-6450PE31G/dp/B00519BEG4/](https://www.amazon.com/Diamond-Multimedia-Radeon-GDDR3-6450PE31G/dp/B00519BEG4/)

---

### Post by oldfred on 2020-07-04
Pays to compare low end cards with the internal video of a CPU chip.

[https://www.videocardbenchmark.net/compare/Radeon-HD-6450-vs-Intel-HD-Graphics-620/267vs3592](https://www.videocardbenchmark.net/compare/Radeon-HD-6450-vs-Intel-HD-Graphics-620/267vs3592)

[TABLE]
[TR="class: alt"]
[TD]G3D Mark    
HD6450     192
Intel 620    923    
[/TD]
[TD][/TD]
[TD="class: hiddentablecolumn"][/TD]
[/TR]
[/TABLE]

---


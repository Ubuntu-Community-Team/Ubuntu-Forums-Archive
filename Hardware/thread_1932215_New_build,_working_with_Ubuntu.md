---
title: "New build, working with Ubuntu?"
date: 2012-02-27
forum: Hardware
---

### Post by naxtek on 2012-02-27
Hello,

I'd really appreciate it if someone in the know could check my shopping list below.  I want to know if these parts are going to work with Ubuntu and if I'm likely to run into any issues.

Intel Core i5 2500K
[https://www.aria.co.uk/SuperSpecials/Intel+Core+i5-2500K+3.30GHz+%28Sandybridge%29+Socket+LGA1155+Unlocked+Processor+-+Retail+?productId=43216](https://www.aria.co.uk/SuperSpecials/Intel+Core+i5-2500K+3.30GHz+%28Sandybridge%29+Socket+LGA1155+Unlocked+Processor+-+Retail+?productId=43216)

GeForce GT 520
[https://www.aria.co.uk/Products/Components/Graphics+Cards/NVIDIA/NVIDIA+GT+520+Series/MSI+GeForce+GT+520+1024MB+GDDR3+PCI-Express+Graphics+Card+?productId=44473](https://www.aria.co.uk/Products/Components/Graphics+Cards/NVIDIA/NVIDIA+GT+520+Series/MSI+GeForce+GT+520+1024MB+GDDR3+PCI-Express+Graphics+Card+?productId=44473)

4GB DDR3 1600MHz RAM
[https://www.aria.co.uk/Products/Components/Memory/DDR3/Single+Modules/4GB+Mushkin+Blackline+%23991995+%281x4GB%29+DDR3+1600MHz+9-9-9-24+?productId=48151](https://www.aria.co.uk/Products/Components/Memory/DDR3/Single+Modules/4GB+Mushkin+Blackline+%23991995+%281x4GB%29+DDR3+1600MHz+9-9-9-24+?productId=48151)

Asus P8Z68-V Motherboard
[https://www.aria.co.uk/Products/Components/Motherboards/Intel+1155+Z68+%28B3%29/ASUS+P8Z68-V+LX+Intel+Z68+%28REV+B3%29+Socket+1155+DDR3+PCI-Express+Motherboard+?productId=48445](https://www.aria.co.uk/Products/Components/Motherboards/Intel+1155+Z68+%28B3%29/ASUS+P8Z68-V+LX+Intel+Z68+%28REV+B3%29+Socket+1155+DDR3+PCI-Express+Motherboard+?productId=48445)


It's also been a long time since I've built a machine so please tell me  if I've been stupid and listed parts which aren't compatible with each  other (I used to do it for a living, but that was over 5 years ago!).


Thanks,
Andrew

---

### Post by naxtek on 2012-02-27
Anyone?  Would really appreciate a little help :)

---

### Post by fjgaude on 2012-02-27
I'm using an ASRock Model 68M-ITX/HT Z68 with Intel i5-2405S CPU. The only issue I'm having is can't Resume after Suspend.

Works fine with 8GB of 1600MHz SDRAM.

It's fast and quick. No issue with booting from an SSD or the UEFI BIOS. Works with 10.10 through 12.04 Ubuntu.

Wish others would report their good fortune or issues.

---

### Post by naxtek on 2012-02-27
Thanks, not generally many problems with newer hardware then?

---

### Post by fjgaude on 2012-02-27
I believe this is true what you say if you use Ubuntu 11.10 or later. The kernels have most all hardware covered within themselves.

Good luck with you new build.

---

### Post by Jagoly on 2012-02-27
Thats a great list, you should get a tasty overclock from the i5 too (assuming you also get an aftermarket cooler).

The GT 520 works fine in ubuntu, just be warned that it is REALLY slow. That has nothing to do with ubuntu, it's just a slow graphics card. You should be able to get a last gen GT 430 or even GT 440 for about the same price, both of which are much faster.

Of course, if you don't play ANY GAMES AT all, the 520 is fine, it delivers a flawless desktop experience.

Good luck, compatibility seems to be alot less trouble with linux/ubuntu than it used to.

---

### Post by fjgaude on 2012-02-27
The integrated graphics of the i5-2500 will be all anyone needs except for the most demanding games. It's flawless on HD video.

---

### Post by Jagoly on 2012-02-27
I personally use minecraft maxed out as a baseline (at 1680x1050 in my case)
Intel's linux graphics drivers are still aweful compared to their windows counterparts (unlike nvidia or amd's). I've run tests with a 2600k, comparing results with a GT 520, Intel hd 3000 (on the cpu), and (my own) GTX 560ti. The 520 run minecraft at a smooth 60+ fps, the 560ti brings it over 300 minimum, but the HD 3000 struggles at around 40 - 50 fps (which is fine, but doesn't leave room for pretty mods).

Intel graphics also only support older versions of opengl (can't remember what though). A 520 on linux makes a lot bigger difference versus intergrated than it does in the windows results found around the net. Phoronix did some benchmarks as well under ubuntu (the reason I though I'd try it out myself) showing the performance lacking intel drivers as well.

Of course, intergrated graphics will manage a composited desktop. But a 520 or 430 gives you headroom for other things, as well as saves on system ram.

---

### Post by naxtek on 2012-02-28
Thanks for the help everyone, just what I wanted to hear.  I will look into slightly better GPUs.

It's not a gaming system - it's just for my parents, but I want something with decent enough headroom to last them a few years without any problems.  I tried to use the Intel integrated graphics on my Core i7 machine at work and ran into loads of problems (albeit on an older version of Ubuntu - I'm still 10.10 as I'm not keen on Unity).  I ended up getting a cheap Nvidia card for it and it works like a dream now - so for the sake of £30/£40 I thought it was worthwhile getting dedicated graphics for my parents.

---

### Post by Jagoly on 2012-02-28
> **naxtek said:**
> Thanks for the help everyone, just what I wanted to hear.  I will look into slightly better GPUs.

It's not a gaming system - it's just for my parents, but I want something with decent enough headroom to last them a few years without any problems.  I tried to use the Intel integrated graphics on my Core i7 machine at work and ran into loads of problems (albeit on an older version of Ubuntu - I'm still 10.10 as I'm not keen on Unity).  I ended up getting a cheap Nvidia card for it and it works like a dream now - so for the sake of £30/£40 I thought it was worthwhile getting dedicated graphics for my parents.

Oh, I see. In that case, a 520 would be adequate. If that is the case, would a 2500k be necessary over a standard 2500? If you want to get the k chip purely for the fun of overclocking (I would), than that's fine as well.

Your spot on with the low end discreet card in ubuntu over an IGP. That's exactly what I was saying, support is simply better.

---

### Post by whatthefunk on 2012-02-28
I have a similar build with the z68 chipset but on an Asrock motherboard.  Works brilliantly.

---

### Post by fjgaude on 2012-02-29
> **whatthefunk said:**
> I have a similar build with the z68 chipset but on an Asrock motherboard.  Works brilliantly.

I'm Z68 and ASRock but my box will not resume after suspend. Did you do anything special with yours?

---

### Post by whatthefunk on 2012-02-29
Mine doesnt resume either, but I dont normally use suspend so it doesnt bother me.

---

### Post by fjgaude on 2012-02-29
> **whatthefunk said:**
> Mine doesnt resume either, but I dont normally use suspend so it doesnt bother me.

Thanks, I'm off to figure out why it doesn't. It's th Z68, but how to fix it? Will issue a bug report and see what happens.

Thanks again!

---

### Post by gordintoronto on 2012-02-29
The wired Ethernet adapter is a Realtek 8111E, which might have issues -- but I think they are easy to fix.

[http://ubuntuforums.org/showthread.php?t=1860197](http://ubuntuforums.org/showthread.php?t=1860197)

Oddly, my computer has the same Ethernet adapter, but it has never caused a problem, because I've never plugged an Ethernet cable into it: wireless from day one.

Oh, it's also a UEFI BIOS, so you might want to research that a bit before you begin installing.

---

### Post by naxtek on 2012-03-01
Thanks for your help everyone - in case anyone finds this and is looking for help:

Everything went smoothly.  I had no problems with any of the hardware.  I just swapped over an old hard disk which already had Ubuntu installed and away it went.  No problems with the UEFI, or the network card, or anything else!  Just plug in and go!

---

### Post by fjgaude on 2012-03-01
> **naxtek said:**
> Thanks for your help everyone - in case anyone finds this and is looking for help:

Everything went smoothly.  I had no problems with any of the hardware.  I just swapped over an old hard disk which already had Ubuntu installed and away it went.  No problems with the UEFI, or the network card, or anything else!  Just plug in and go!

Glad to hear the good news! But, but does it suspend/resume?

---


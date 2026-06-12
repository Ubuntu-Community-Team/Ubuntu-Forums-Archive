---
title: "GeForce 8400GS in Ubuntu?"
date: 2009-12-19
forum: Hardware
---

### Post by spurs21 on 2009-12-19
Hi, I want to buy an LCD to run at 1920x1080, but since I'm not a gamer, I want to be cheap on the video card (plus my board only has a PCIEx16 1.0 slot anyways). I was looking at buying a 512MB GeForce 8400GS. I don't care anything about compiz effects, and don't mind turning all that stuff off if needed; all I want is a system capable of running at 1920x1080 so that I'll have enough room to for instance have my source code and created pdf open side by side when I'm writing something in LaTeX, have Eclipse and my documentation side by side when I'm writing something in Java, and so on. My current hardware is old (ASUS M2NPV-VM board with integerated GeForce6150, old Athlon64X2 CPU, 2GB DDR2 800 RAM), but it runs pretty well on Intrepid (32-bit) at 1280x1024, and I was hoping a cheap video card would be all I need to run 1920x1080. I'd really appreciate it if anyone knows whether its possible to do this resolution (without a really bad refresh rate) using a 512MB GeForce 8400GS.

Thanks!

---

### Post by laceration on 2009-12-19
I have a Nvidia Geforce 8500 GT, which I think is not quite as good as the 8400 GS, and have been watching 1920 x 1080 hidef TV on a 42 in. monitor for 2 years.  I also have had no problem using Compiz at full force.  The interesting thing is that the Nvidia drivers have just recently, with the 180+ series, starting offloading the video processing to the GPU(the GPU is the Graphical Processing Unit, the chip on video board).  I am still using the 173 drivers, which rely more on and can be limited by the CPU.  I am using Athlon 64 X2 4400 and performance is still more than satisfactory.  Especially with the newer drivers, you have nothing to worry about!

---

### Post by spurs21 on 2009-12-19
> **laceration said:**
> **  The interesting thing is that the Nvidia drivers have just recently, with the 180+ series, starting offloading the video processing to the GPU(the GPU is the Graphical Processing Unit, the chip on video board).**

Are you talking about VDPAU? (Video Decode and Presentation API for Unix). That's certainly a plus, especially if Ubuntu linked it into the stock MPlayer package, but that's a bit disheartening if the desktop is still done in software like the old days. My CPU has half the L2 cache of yours (2x512KB on the 4000x2 vs 2x1MB on the 4400x2).

---

### Post by laceration on 2009-12-20
```
Are you talking about VDPAU?
```
Yes.

An easy way to install a version of MPlayer that supports VDPAU and the latest Nvidia drivers is from the Nvidia PPA.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

I am running Hardy.  Jockey sucks in Hardy and won't install the newer drivers, that's why I am only using 173.  There is a probably a way to get them installed, but I am just going to wait until I do a fresh install of Karmic.  I don't know if Jockey works better in Intrepid.

---

### Post by spurs21 on 2009-12-20
> **laceration said:**
> ```
Are you talking about VDPAU?
```Yes.

An easy way to install a version of MPlayer that supports VDPAU and the latest Nvidia drivers is from the Nvidia PPA.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

I am running Hardy.  Jockey sucks in Hardy and won't install the newer drivers, that's why I am only using 173.  There is a probably a way to get them installed, but I am just going to wait until I do a fresh install of Karmic.  I don't know if Jockey works better in Intrepid.

I guess I'm still unsure of whether hardware acceleration is going to be used at all for rendering the desktop. Hardware acceleration to allow smooth viewing of HD movies is nice, but it's not all that important to me in comparison to running a large desktop that isn't going to strain my eyes.  My system absolutely cannot handle 1920x1080 as it stands right now (the flicker is pretty bad), so if the CPU is doing all the rendering, then it's still not going to acceptably render 1920x1080 with just an upgraded video card, correct? So I should upgrade the CPU instead in that case? Sorry if I'm coming off a bit clueless, as I do appreciate the help.

As an aside, that must be awesome being up in Bend. I have always wanted to see that area. Plus you guys in Oregon are neck-and-neck with Cali for the best beer in the nation! (world?)

---

### Post by laceration on 2009-12-20
I actually use the 42 in. monitor for my everyday normal computing too.  Rendering the desktop does not take close to the resources as video.  The 8400 GS will support 1920 x 1080.  Even though the older drivers do not utilize the GPU as effectively as they could, it doesn't mean that a 8400 GS will not out perform 6000 series onboard video.

You might be more sensitive to flickering than I am(was never an issue for me), so you will have to be the judge, but I think you will be ok.  42 in. is overkill for the desktop, but a good size for TV.  If were to buy a new one, I'd probably go 37 or 40.

Yeah, Deschutes Brewery from here is world class, its just too bad it's not free, as in software ;)

---

### Post by cascade9 on 2009-12-20
> **laceration said:**
> I have a Nvidia Geforce 8500 GT, which I think is not quite as good as the 8400 GS

*blinks* The 8500GT is a faster card than the 8400GS. There are 2 versions of the 8400GS (G86 and G98) but btoh of them are slower. *thinks* maybe you've just looked at the core speeds, the G98 8400 Gs has faster core speeds, but its still slower IIRC, thanks to the data bus (64 bit for 8400GS, 128bit for 8500GT) 

BTW, the 6150 should support up to 1920x1440 @ 75 Hz (VGA) or 1600x1200 @ 65Hz (DVI). It should run 1920x1080. Its possible that running your LCD in VGA not DVI would make it work without flickering, etc. But upgrading isnt a bad idea, any 8xxx 9xxx or 2xx series nVidia card should make 6150s seem pretty slow. The 8400 GS should do 1920x1200 @ 75Hz DVI so if your flickering is a refresh rate or widesceen problem, the 8400 should be better than the 6150.

---


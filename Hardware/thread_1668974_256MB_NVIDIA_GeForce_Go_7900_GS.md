---
title: "256MB NVIDIA GeForce Go 7900 GS"
date: 2011-01-17
forum: Hardware
---

### Post by caseman7 on 2011-01-17
Hi Y'all, 

I'm a new convert to Linux/Ubuntu - only 8 months in, but lovin it through the good times and the bad. Hoping one of you Jedi's can give me a hand solving a hardware issue: 

I've read that a recurring issue in Ubuntu tends to be graphics card compatibility. I run (Lucid/10.04 studio dual booted with windows vista) a Dell Inspiron 9400 Laptop, Core 2 Duo 2.2ghz, 4 gb ram, 500gb hdd and a 256MB NVIDIA GeForce Go 7900 GS. The last component is the source of my head scratching. Ubuntu has been a pretty sweet setup 'out of the box' with my laptop, but video (dvd's, streaming/downloaded video etc.) has been choopy, laggy and just downright ugly since the beginning, yet in windows it runs flawlessly. I have installed all of the 'extras' and proprietary driver/codec packs etc, but it still seems my video card is not working and my processor is having to shoulder all of the dirty work. Do any of you know a way I can run a diagnostic test or something to see if Ubuntu is even using my videocard? Does anyone have any info on the 256MB NVIDIA GeForce Go 7900 GS? I have searched the forum and found nothing so far. 

Cheers & thanks in advance for any contributions you can make. Any hints would be greatly appreciated. 

Casey

---

### Post by cascade9 on 2011-01-17
The 7XXX nVidia cards will use nVidia pure video with windows, which is designed to use the GPU for some video decoding and post-processing. The linux version, VDPAU, isnt supported by 7XXX cards, there is an 8XXX minimum for VDPAU. 

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

Also, flash is accelerated under windows, and not under linux. 

That is why your video is more choppy and laggy under linux. 

If you havent already, try installing the nVidia drivers (system-> administration-> hardware drivers). It might improve things.

---

### Post by caseman7 on 2011-01-18
Hi Cascade9 & thanks for the speedy reply and informative input. The flash & no pure pices expain a lot. 

I have tried installing the NVIDIA drivers in (system-> administration-> hardware drivers) as you suggest, but I go there and all I have is a blank screen saying " there are no proprietary drivers installed on your system". Do I need to do something there? 

Last night I downloaded a package off NVIDIA's website called: NVIDIA-Linux-x86-260.19.29.run Would installing that be a bad idea? It said it was Linux friendly, and it is supposed to be for my card? Even if that is Kosher, I have another problem with it... When I go into the right click contest menu of the file and into properties and enable the file to be run as an executable, it starts to install in Terminal just dandy, but then stops and it says the install must be done as root. Would that be a good or bad idea? If good - how would I do that?

So sorry to dump all these questions out there!

Cheers & talk to you soon, 

Casey

---

### Post by cascade9 on 2011-01-18
The newer drivers wont help at all, and manually installing the nvidia drivers like that means that if you get a kernel update, you'll have to stuff around to get your desktop back.

---


---
title: "Radeon 9550"
date: 2013-12-08
forum: Hardware
---

### Post by Will_McDade on 2013-12-08
Hi guys

So I recently got a new AGP 8X card for my pc. ATI/Connect3D Radeon 9550 256mb. Nice card. I can use it out of the box but when it came to drivers... I opened additional drivers, no proprietary driver there... I thought that is strange. I went on the AMD website, located the driver, would not install because of a kernel error. Then after a bit of googling i found [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/195535](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+question/195535) and apparently I need kernel 2.6.28 and xorg 1.5. I thought these are OLLLLLD. Should I stick with the opensource driver or downgrade xorg and the kernel? Will the open source driver be able to run steam games and stuff? I dual-boot with Windows 7 so I have a OS to fallback to. :)

Many thanks.

---

### Post by Mark Phelps on 2013-12-08
> Should I stick with the opensource driver or downgrade xorg and the kernel? 

You're not talking about going backward a few months, but instead, YEARS!  That's a really SERIOUS downgrade of both the kernel and the X-server, so much so, that I would be worried if your machine would even function when you're done!

It's very likely that such a regression will trash what you have.

Stick with the open-source drivers or get a newer video card.

---

### Post by Will_McDade on 2013-12-09
From what I have read I could install something like 7.04-9.04 and live with the driver, but thats a bit outdated. The newest of that lot is 8.04 which ended in may this year. Of course, I would still keep Windows 7 and Elementary OS Luna (12.04). I am suprised that Nvidia have better Ubuntu support than AMD because I always thought it was an opposite argument.

The alternative is to "somehow" get accelerated opengl support on the open source driver. I tried playing portal and the result was no opengl acceleration in your system (words to that effect).

---

### Post by Yellow Pasque on 2013-12-09
You do have OpenGL, but because your card is so old it only supports OpenGL 1.3, and a lot of apps will be looking for at least 2.1
To verify OpenGL is working, look at glxinfo:
```
sudo apt-get install mesa-utils
glxinfo
```

>  I am suprised that Nvidia have better Ubuntu support than AMD because I always thought it was an opposite argument.
Meh, even if AMD had maintained their binary driver for newer kernels and X, the card itself is just too old for what you want to use it for. You would still run into the same problem that you experience now because the hardware is only capable of OpenGL 1.x

If you want to game, the best thing you can do with an AGP slot nowadays is use it as an excuse to get yourself a better system ;)

---

### Post by Will_McDade on 2013-12-09
I mean, when I am in Windows, I can run portal at 1280x1024 (the native resolution) at about 50-70 FPS, so I don't see a problem. If my PC isnt dead by then, I will get an nvidia card, my problem with nvidia then is, steam will only run on linux for a certain nvidia driver or higher. Linux is cruel sometimes...

---

### Post by codenine75a on 2013-12-09
The kernel has ATI (AMD) Radeon support.  Try updating your kernel.

---

### Post by Yellow Pasque on 2013-12-10
> **Will_McDade said:**
> I mean, when I am in Windows, I can run portal at 1280x1024 (the native resolution) at about 50-70 FPS, so I don't see a problem.

The Windows version of Portal was originally done using DirectX 8 and 9, and the Radeon 9550 supports that, so it's no surprise. The OpenGL port may require OpenGL 2.1 while your card only supports 2.0 (I was wrong earlier and I had your card confused with a Radeon 9250 when I said it only did 1.3). Again, please show output of glxinfo

---

### Post by Bucky Ball on 2013-12-10
8.04 did not finish in May this year unless you are using the server version. The regular desktop version finished in April 2011. As advised, don't go this far back. You will be creating security vulnerabilities if you are online and there is very little support available to you here. 8.04 is long dead.

---


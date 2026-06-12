---
title: "Another Screen Resolution problem"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by m1scha_m on 2005-07-02
Over the last few years I have "tinkered" with Linux, and at some stages have even had it up and running for a day or two on a few computers. However I built a 64bit machine, and as I can't afford Microsoft's 64bit offering, decided to install the AMD64 Ubuntu version.

It installed like a dream, however the screen resolution was a bit low, but as I wanted to install Java, and FAH plus upgrade Firefox, I didn't immediately worry.

When I came to reset the screen resolution all I had was 1152x762 and lower. All my other computers are running 1152x864, and as all four use a 4 port KVM switch it wasn't merely a case of adjusting the monitor to fill up the waste space.

I rewrote the xorg.conf to include the higher resolution, and even increased the H and V sync KHz. My monitor will do H of 30 - 95, and V of 50 - 160, but as I only wanted a max of 1280 I used what I thought was a conservative H 95, V 90.

Now I could sign on, but that was it.

I reinstalled Ubuntu, with the same effect. All four computers use the same nVidia x 4 AGP card. Under WinXP, and 2K they can well and truly exceed 1152x762.

Is it a case of upgrading the nVidia drivers? Or is this inherent in the Kernel?

I must say I have never used Linux/Unix to the stage of installing anything like say Java, and to find references that say use java-package and fakeroot with out specifying that the Debian version isn't compatible, and to use the Ubuntu version is not making it easy. So if someone does respond to this, please advise if anything I need install is common to all flavours, or is Unbuntu specific.

---


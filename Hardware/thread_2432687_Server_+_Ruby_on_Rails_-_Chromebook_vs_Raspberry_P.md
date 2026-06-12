---
title: "Server + Ruby on Rails - Chromebook vs Raspberry Pi 4 ???"
date: 2019-12-06
forum: Hardware
---

### Post by rorserver on 2019-12-06
Thank you in advance for your help!


I want to install Ubuntu Server + Ruby on Rails.


Would a Chromebook or Raspberry Pi 4 be a better inexpensive platform for this?


Thank you!

---

### Post by TheFu on 2019-12-06
Rails, Ruby and gems are RAM hogs.  You'll need at least 2GB of RAM.  Sometimes, gem updates require lots of RAM.
I've never attempted ruby+rails on any ARM system.  My RoR webapp uses just under 1GB of RAM when running.  The more sessions there are, the more RAM will be needed.

Most of the work will be performed over ssh connections, so after networking is setup, there really isn't any need for a keyboard or monitor connected to the "server".  I've never installed ubuntu server on a raspberry pi. No clue if that works or how well it might work.

The main thing would be to get 4GB of RAM if this is a student environment.

Ruby performance is the next issue. I love ruby, but it is slow.  Getting the fastest CPU possible is only smart.  If you can get a fast chromebook with 4G of RAM cheaply, that could work.  Be certain to carefully check the CPU performance before buying any chromebook.  Newer isn't always faster.   

A few refurbished chromebooks at my local big-box, each $90:
Celeron N3050 = 850 passmark
Celeron N2840 = 1000 passmark

These are the chromebooks I have:
Celeron 29950U = 1500 passmarks - from 2013, new, $212
i3-5015U =  3000 passmarks -  from 2015, new, $430
Pentium G3258 = 3800 passmarks - from 2015, but a $50 desktop CPU

My current used, new-to-me, laptop was less than that new Core i3 chromebook. It has an i5-8250U;  7600 passmarks, double the RAM, 1TB disk, etc ... 

Look at the passmarks. Don't get screwed with a bad CPU.

---

### Post by katakaio on 2019-12-08
> **TheFu said:**
> I've never installed ubuntu server on a raspberry pi. No clue if that works or how well it might work.

I can say that this works quite well - for certain tasks. I'm currently running 18.04 on a RPi3, and you can too with [this handy guide]("https://ubuntu.com/download/raspberry-pi") from Ubuntu. I have to say that I'm impressed by how great the support is for arm64, as I haven't had to compile anything yet.

However, TheFu is right about RAM, which is something that the RPi3 doesn't have much of at all. If you go the RPi route, you should definitely consider the RPi4 for memory-intensive applications. At the end of the day, buying a RPi is a relatively inexpensive experiment!

---

### Post by TheFu on 2019-12-08
Doesn't the r-pi v4 come in 3 different RAM levels?  
[https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/) says there are 1G, 2G, and 4G versions.  Be certain to get the 4G version.

I've always used debian on my Pis.  Have a v2 and v3 - both with 1G of RAM.

Lots of choices.

---

### Post by rorserver on 2019-12-13
> **TheFu said:**
> Doesn't the r-pi v4 come in 3 different RAM levels?  
[https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/specifications/) says there are 1G, 2G, and 4G versions.  Be certain to get the 4G version.

I've always used debian on my Pis.  Have a v2 and v3 - both with 1G of RAM.

Lots of choices.

Thank you, all, for your responses.

I had actually already bought the Pi4 with 4G RAM before the initial reply, and based on the comment about RAM (latest Ubuntu Server can't access full 4 G yet), I went ahead and installed Raspbian and have my target Ruby on Rails application running.

Thanks for your help!

---

### Post by TheFu on 2019-12-13
Please use the "thread tools" button near the top to mark this thread as "SOLVED".
Doing that helps others both looking for answers and trying to help others find answers. Good for the community so these thread aren't just lost.

---

### Post by rorserver on 2019-12-13
> **TheFu said:**
> Please use the "thread tools" button near the top to mark this thread as "SOLVED".
Doing that helps others both looking for answers and trying to help others find answers. Good for the community so these thread aren't just lost.

Done. Thank you.

---


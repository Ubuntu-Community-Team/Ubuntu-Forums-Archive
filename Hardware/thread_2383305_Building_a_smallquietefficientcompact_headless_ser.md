---
title: "Building a small/quiet/efficient/compact headless server from scratch."
date: 2018-01-23
forum: Hardware
---

### Post by elsmandino2 on 2018-01-23
Hello,

I am thinking about putting together a new server from scratch and would be be really grateful for some suggestions as to what hardware to use - it has been many years since I have built anything, so I am a bit out-of-date when it comes to components.

My only real requirements at that it has room for four 3.5" hard drives plus an SSD.

It really doesn't have to be particularly powerful - it needs to be as power efficient as possible as I will need to leave it on 24/7.

My uses are going to be:

* Using it to record TV via TVHeadend.
* Stream music/video to a number of clients on my home network.
* Home automation/CCTV
* Downloading Podcasts

I won't need to do any transcoding.

Any advice would be much appreciated.

---

### Post by TheFu on 2018-01-23
If you don't need any transcoding then pretty much anything can be used.  For you, it is more about network performance, so stay with Intel NIC devices.  I have 7 systems running 24/7 here.  Power bill is usually just under $70/month.  To me, that is cheap, but I am slowly removing the 125W Core i7 systems for 65W ones.

I would look for a microATX with a 35W or less CPU.  Probably want to avoid DDR4 stuff, since DDR4 RAM is 5x the normal pricing thanks to bitcoin miners.  I have a G3258 which draws 53W peak, but usually much, much less.  It is overkill for your needs, but does handle transcoding 2 HD streams fine.  It is a storage server, plex server, and occasional TV recording machine (HDHR4 using wget).  I got it + a MB  + 8G of RAM for $126 about 5 yrs ago.  It is not silent and uses the stock (included) CPU fan.

With USB3, you can do all sorts of interesting storage connections these days.  A single USB3 port can support 100+ devices, in theory.  Spinning disks counts you or I will use aren't likely to come close to the USB3 bus limits.

You might look at a $150-ish APU2C4 device (has a 64-bit AMD CPU) and uses 10W of power, peak. That would be fanless, silent, about 1500 passmarks, no GPU.  Mine has 2 USB3 ports. A friend ran an x2go desktop on his. Said it performed well enough.  Mine is busy as a router, but you've got me thinking this might be a nice platform for a home server.  Because there's no way to add a GPU, it will always be console only.  Hummm.  I need to see if I have any SSDs that will fit it.  

A completely different ARM-based option is [https://category5.tv/shows/technology/episode/529/](https://category5.tv/shows/technology/episode/529/) . Don't know how well tvheadend is supported on ARM.  In theory, the SATA-to-USB converter and GigE NIC should make it a nice storage system.

Thanks for the question!

---

### Post by elsmandino2 on 2018-01-24
Thanks Fu - extremely helpful and informative reply.

That fact that you are using something not too dissimilar to my current server, makes me think that I should perhaps stick with it and spend money upgrading it instead.

Here is what I currenlty have:

G1840
MSI B85M-E45 m-ATX
12GB DDR3 (2x4GB and 2x2GB)
1x64GB Crucial M4 SSD
2 x 2TB Samsung F4 HDD
1 x 1TB Samsung F1 HDD
1 x 6TB WD Red HDD
Superflower Golden Green 350w PSU (Gold Rating)
Xigmatek Midgard Tower with 1 x 120mm exhaust fan and 1 x 140mm intake fan


Would you make any changes to it to make it quieter or more efficient?

I have considered removing the intake fan and swapping the PSU our for a Pico one.

---

### Post by TheFu on 2018-01-24
For what you've described, I wouldn't touch the system.

---

### Post by mastablasta on 2018-01-25
the only things that actually make a lot of noise are fans. so if you think it is loud (noticably not quiet), then perhaps only a fan replacement is needed. that should be cheap.

---

### Post by TheFu on 2018-01-25
> **mastablasta said:**
> the only things that actually make a lot of noise are fans. so if you think it is loud (noticably not quiet), then perhaps only a fan replacement is needed. that should be cheap.

PSUs can be noisy too.

---

### Post by elsmandino2 on 2018-01-25
Thanks very much for that - it is very reassuring that you don't think I need to go down the road of a brand new build.

I think I am going to have a mess around with the fans, though.

1. Do I really need an intake and exhaust fan?  I am using both, only because I can.  

2. Whilst I have been building PCs for years, the one thing that I have never done is messed with an aftermarket CPU cooler.  I can definitely hear a slight wine when CPU usage ramps up so that would also be a good candidate for an upgrade.  Do you think I could get away with something completely passive or should I stick with an active (but big and quiet) fan?

---

### Post by TheFu on 2018-01-25
It depends.  Get your temperature monitoring working for 3+ places on the system.  Watch those for a while.
Then try different solutions.  There's always liquid cooling.

I've never heard of a desktop CPU that didn't need cooling. That is for mobile and embedded systems. I have a few fanless computers. The entire case is the heatsink on 1 and the other has a huge heat-pipe. It is a chromebook.

---

### Post by hannabanana on 2018-01-27
Hi

regarding a quiet build, I can recommend picopsu and one or two Noctua fans
If you like compact builds, thermaltake core v21 is worth a look. I´m unsure if it´s possible to fit 4x3.5" + a 2.5"ssd in there though..

---


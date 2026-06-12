---
title: "DVD/CD combo, SATA or IDE? (and a quick eth0 question)"
date: 2006-03-06
forum: Hardware &amp; Laptops
---

### Post by mc__ on 2006-03-06
I currently have a BenQ cd burner and it works fairly nicely.

But i never really used it much. Yesterday i got neverwinter nights and i was installing it via the "ravage installer"... eventually I rebooted the computer because i couldn't kill the app, and nothing i done would end it (i only tried killall and right-click -> end then kill from gnome's system monitor).

I figured that it had hanged because it was taking half an hour to read off a 200kb wav file. You see, DMA is not enabled, and i cannot turn it on. I use the closed-source binary drivers from nvidia for my NFORCE-430 chipset. If i do not use it i cannot do a lot of things (such as have a working ethernet connection), so changing isn't really an option yet (the GFX is the 6150 onboard chipset also from nvidia, just FYI). I've tried searching google to see if this situation has changed, but it seems like it has not.

Anyway, i need a DVD burner, so i was wondering if i were to buy a SATA dvd burner would i have good performance, seeing as how an ide one will likely misbehave like my old ide cd burner? Or will it be much the same either way?


OT: My internet connection drops out when bit torrent is running in the bg even when i set it to 1kbps max up/down (latest stable azureus), and i get "network neighbour table overflows" and "no buffer space" error messages for ping and messages in the kernel log. I have azureus settings modified to hard limit maximum concurrent connections to be 25... surely this is not enough to overwhelm the system (seeing as how i'm not even actively sending data to more than like 1 or 2 of them at those low speeds)?

My loopback system is all perfect. Can this be caused by a speed limited DSL connection forced to run at 28.8k dialup equivelant, or is it solely a NIC issue (NIC = onboard nvidia 430 gigabit ethernet)?

---

### Post by bluevoodoo1 on 2006-03-06
Well, if I can say... do NOT buy an ASUS or a PIONEER DVD burner. I have an ASUS burner and from what I've read many of the ASUS burners are rebranded PIONEERS. In any case, like you, I can't turn on DMA. I've tried everything. All DMA guides, checking the cable, compiling the newest kernel with DMA support... nothing. I'm not going to try to upgrade the firmware because I'm not exactly certain it is a Pioneer. Right now, I have an LG DVD Burner on order. I'd read that some people had positive experiences with it with Linux. As for IDE or SATA, if the slowness is due to the drive's inability to use DMA, then an IDE drive that has DMA capabilities (and can be turned on...) should be fine, right? I'm not sure how the support for SATA DVD burners goes. SATA are supposed to be faster (I have an SATA hard disc and well, who nkows how much faster it is than an IDE drive). 
In any case, if you do buy another DVD burner, try to check out if it has problems with Linux and DMA (and/or any other problems).  I hope that was of some help for you.

---

### Post by mc__ on 2006-03-07
Hmm,

well my cd drive plus hdd both have dma support with this mobo under windoze, it is an issue with the linux support for the nforce 430 chipset from nvidia regardless of whether or not the drives themselves support it (because i know that they both do).

So no matter what dma will never work because nvidia won't let me... so i was wondering if a SATA optical drive will work good even without dma enabled. Still thanks for the ASSUS / PIONEER tip.

---

### Post by bluevoodoo1 on 2006-03-08
I'd like to retract my statement... there was a problem with my hardware setup. I tried my ASUS burner in another computer running Breezy and it worked flawlessly. I tinkered around with the faulty computer and I finally got it to work!!! I think now, I can approve of the drive!

---


---
title: "Building new 12.04 Desktop for use with VirtualBox"
date: 2012-05-08
forum: Hardware
---

### Post by T1Oracle on 2012-05-08
Currently I have a Core 2 Duo, 4GB of RAM, 1TB HD, and a GeForce 560. My computer runs Ubuntu very well, and I can boot my Windows 7 VM just fine in VirtualBox.  However, I want to run more virtual machines and doing so would require more RAM which would require a new motherboard.  I need a new motherboard because the one I have only has two working RAM slots :(

So, I figured I might as well bite the bullet and buy a new system.  I would like for it to be fast, quiet, and capable of running two small Linux server VM's at once and running the Win 7 VM whenever I need it for Photoshop or cross-platform software testing.  My machine will mostly be used to run servers as virtual machines, develop software, and compile source code.

Although I have built my systems in the past, I'd like to avoid the hassle this time around.  I am trying to figure out what hardware I need for this build.  Right now I've decided on the following specs:

1) Disaster recovery is critical to me, I have data that goes back for decades that I would like to keep and I would freak out if I ever lost it.  So I'm thinking of going with two 1 TB HD's in a RAID 1 mirror.  From there I could partition them so that 500 GB is for operations and 500GB is for continuous back ups and snap shots.  I really don't know what the best back up plan, I'm used to using Acronis True image to back up the entire primary HD to a secondary that I only use for that purpose.

2) VM's eat RAM, 16GB may be over kill but I figure I'll find some way to use it.  I could probably scrape by with 8.

3) 40GB SSD, this is really a like to have, but I figure it may help performance if I settle for a slower CPU.

4) Fractal Design R3 case.  This case reduces noise and I'm tired of loud computers. I figure this is the simple way to do that.

I have no clue which CPU I should use.  Should I get a Phenom II, a Core i5, or an i7?  I want this machine to be fast but I doubt I'll be able to play games.  I don't plan on running Windows natively, only in a VM.

I also don't know what GPU I should get.  I do want to get back into OpenGL development, but I don't expect to make the next Crysis for Linux anytime soon.  I figure it might be beneficial to go with a fanless GPU and save on the noise factor.

As for the CPU, all I have decided that I want at least 4 cores. However, I'd love to get this thing under $1100.  Right now I have a Core i7 build that is $2,017 without the SSD, and an Phenom II build for $1,300 with the SSD.  From what I've read the AMD CPU's are slow, but I don't know how that would affect my uses.  I mostly need multi-threading as I hope to develop distributed apps and multi-threaded apps.

Any advice is appreciated. Thanks :D

---

### Post by iMurshaq on 2012-05-08
From my experience, Intel CPU's are only slightly better than AMD's with Ubuntu but I doubt there will be much NOTICEABLE difference.

---

### Post by PhilGil on 2012-05-08
Why not one of the high end Bulldozer processors like the FX-8120 or 8150? The Bulldozers haven't received great reviews, except in use cases (such as yours) where the multiple cores can be put to good use.

If you want to go with Intel, you might see some good prices on Sandy Bridge processors now that the Ivy Bridges are reaching retailers. In my opinion, an i5 would be sufficient for your use case; the i7 is probably overkill.

---

### Post by T1Oracle on 2012-05-09
> **PhilGil said:**
> Why not one of the high end Bulldozer processors like the FX-8120 or 8150? The Bulldozers haven't received great reviews, except in use cases (such as yours) where the multiple cores can be put to good use.

If you want to go with Intel, you might see some good prices on Sandy Bridge processors now that the Ivy Bridges are reaching retailers. In my opinion, an i5 would be sufficient for your use case; the i7 is probably overkill.

Isn't the Phenom II better than the FX?

---

### Post by lukeiamyourfather on 2012-05-09
> **T1Oracle said:**
> 
1) Disaster recovery is critical to me, I have data that goes back for decades that I would like to keep and I would freak out if I ever lost it.  So I'm thinking of going with two 1 TB HD's in a RAID 1 mirror.  From there I could partition them so that 500 GB is for operations and 500GB is for continuous back ups and snap shots.  I really don't know what the best back up plan, I'm used to using Acronis True image to back up the entire primary HD to a secondary that I only use for that purpose.


RAID 1 is good for getting back online quickly from a disk failure but RAID doesn't protect against every other form of data loss (fire, power surge, accidental deletion, etc.). If the data is really important consider daily or hourly backups to a NAS or other network server and monthly or quarterly backups to an offsite location like a family member or commercial service. Check out rsync if you're not already familiar with it.

```
rsync -a --delete /source /destination
```

> **T1Oracle said:**
> 
2) VM's eat RAM, 16GB may be over kill but I figure I'll find some way to use it.  I could probably scrape by with 8.


Most modern motherboards with four or memory slots support at least 32 GB of memory. Given the relatively low price of memory right now I'd max out whatever you get if you plan to run a lot of virtual machines, especially with tasks like Photoshop.

> **T1Oracle said:**
> 
3) 40GB SSD, this is really a like to have, but I figure it may help performance if I settle for a slower CPU.


Waste of money for most users at this point in the game. For running lots of virtual machines the processor is far more important than the benefits a small SSD could offer.

> **T1Oracle said:**
> 
4) Fractal Design R3 case.  This case reduces noise and I'm tired of loud computers. I figure this is the simple way to do that.


Every component matters because if there's one loud fan that's all you'll pay attention to. 

> **T1Oracle said:**
> 
I have no clue which CPU I should use.  Should I get a Phenom II, a Core i5, or an i7?  I want this machine to be fast but I doubt I'll be able to play games.  I don't plan on running Windows natively, only in a VM.


For running lots of virtual machines the most important factor by far is the number of cores. For the money the best bang for the buck is the FX series from AMD, especially the 8 core offerings.

> **T1Oracle said:**
> Isn't the Phenom II better than the FX?

The Phenom II was replaced with the FX series processors. Depending on the task the Phenom II can be better (has floating point unit per core and the FX series shares a floating point unit for every two cores). Based on the tasks in the original post an FX series processor is the way to go. An 8 core system with 16 GB of memory is well within the budget of $1,100 for a complete system.

---

### Post by lukeiamyourfather on 2012-05-09
Here's a system for $1,100 that has 8 cores at 3.6 GHz and 32 GB of memory. Plus a passively cooled video card and the two hard disks for RAID 1. The power supply is 80Plus Gold certified. Swap out the factory fans in the case for some low noise ones. In other words a great computer to host a lot of virtual machines without spending thousands.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820226263](http://www.newegg.com/Product/Product.aspx?Item=N82E16820226263)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817151099](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151099)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102980](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102980)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131767](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131767)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148697](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148697)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811129180](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129180)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106289](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106289)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16835124023](http://www.newegg.com/Product/Product.aspx?Item=N82E16835124023)


Depending on what you want to do with the virtual machines you might want additional network cards like this.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833114037](http://www.newegg.com/Product/Product.aspx?Item=N82E16833114037)


Or these if you don't need as many which are a lot cheaper.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180026](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180026)

---

### Post by PhilGil on 2012-05-09
> **T1Oracle said:**
> Isn't the Phenom II better than the FX?
The Phenom II's benchmark better for single-threaded applications, but the Bulldozers do well with multi-threaded applications or use cases like yours where you'll be running multiple VM's simultaneously.

---

### Post by T1Oracle on 2012-05-09
Wow, Luke and Phil thanks a million guys! :D

I'll look at your suggestions and see what I can build.

Originally I was using [http://www.avadirect.com/]("http://www.avadirect.com/") to build my system, but I am going to price out my other options first and see what makes the most sense.

I should have come here sooner!

---

### Post by T1Oracle on 2012-05-16
Hey guys, I also need Wake On LAN. Does that motherboard (ASUS M5A97 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS) support it, or do I need a different one?  I don't see WOL advertised for the motherboards on NewEgg.

---

### Post by Yellow Pasque on 2012-05-16
Yes, WOL is supported:
[http://www.asus.com/Motherboards/AMD_AM3Plus/M5A97/#specifications](http://www.asus.com/Motherboards/AMD_AM3Plus/M5A97/#specifications)

---


---
title: "nvidia driver hell... can't find a solution"
date: 2009-04-04
forum: Hardware
---

### Post by scubabuddy on 2009-04-04
hi, so i'm running intrepid on my laptop with the nvidia GeForce Go 7400. I believe that the driver was working properly. Then i shut my computer down for a week while i was away for spring break. I came back and booted it up and now the driver won't work at all. I'm in low graphics mode right now typing this. 

I've tried both the NVIDIA driver straight from their website and installing the driver through synaptic, both of which fail. 

I've been reading everything i can find on the forums about this and will keep going. Any help would be absolutely great... as much as i love ubuntu i'm starting to get frustrated with the hardware compatibility problems i've had constantly. Actually, to the point of installing vista on another partition so i have a working OS :mad:

---

### Post by Ceyx on 2009-04-05
It seems to me that video drivers only get loaded when the computer boots. Is it possible that you installed new drivers just before spring break and never rebooted ( ie the day you went on break) ?

I have learned the hard way instead of fooling around with stuff I am just guessing at, plus the fact that I am very impatient - I just reinstall Ubuntu from scratch and never ever install the proprietary drivers, particularly if they do not come thru Synaptic.

There is a warning about proprietary drivers when you install them.  The source code is not available to the public (copyright BS) and thus make it almost impossible for any one to fix them or to know what they are doing.

Once you get Ubuntu stable it is worth it!

Install from scratch and forget about it....

---

### Post by norwoods on 2009-04-05
the nvidia 185.13 driver is now on the intrepid main repository.  you can install it with synaptic.

---

### Post by Vadi on 2009-04-05
I don't think his card is supported by the 185* series

---

### Post by starcannon on 2009-04-05
I had the same issue running intrepid on my twin 7950gt's in SLi mode, I finally had to get things done, and reverted back to 8.04 on the 177 drivers; the 180 drivers did the same thing even under 8.04, not sure what the deal is with the 7xxx cards and the latest drivers and new xserver, but its certainly a bit of an irratation(sic).

> **scubabuddy said:**
> hi, so i'm running intrepid on my laptop with the nvidia GeForce Go 7400. I believe that the driver was working properly. Then i shut my computer down for a week while i was away for spring break. I came back and booted it up and now the driver won't work at all. I'm in low graphics mode right now typing this. 

I've tried both the NVIDIA driver straight from their website and installing the driver through synaptic, both of which fail. 

I've been reading everything i can find on the forums about this and will keep going. Any help would be absolutely great... as much as i love ubuntu i'm starting to get frustrated with the hardware compatibility problems i've had constantly. Actually, to the point of installing vista on another partition so i have a working OS :mad:

---

### Post by scubabuddy on 2009-04-05
what's really got me pissed off is that it WAS working just fine. and then magically stopped.

i can't get the system->admin->hardware drivers to recognize any hardware drivers either. any ideas?

---

### Post by perpetuo on 2009-04-13
i'm experiencing the same problem.
i can't choose the 'normal' or 'extra' mode in the appearance preferences > visual effects.
did you get some solution mean while?

---

### Post by Vadi on 2009-04-13
go to system - administration - hardware drivers to install a driver first

---


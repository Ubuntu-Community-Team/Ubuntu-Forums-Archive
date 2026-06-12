---
title: "Buying new laptop.  How much RAM is recommended to emulate Ubuntu inside of Windows 7"
date: 2009-11-03
forum: Hardware
---

### Post by dpatel304 on 2009-11-03
Alright, so I'm going to be buying a new laptop in the next few weeks and have heard great things about Lenovo/Thinkpad laptops.  I really like the Lenovo T400, so I am most likely going to go with that model:
[http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400](http://shop.lenovo.com/us/notebooks/thinkpad/t-series/t400)

Ideally, I want to have Windows 7 as my default OS and be able to emulate Ubuntu.  I am hoping to eventually switch to only Ubuntu, but, while I learn the ins and outs of Ubuntu, I'd like to be able to quickly access both OSs, and this seems to be the best way.

My question is this, if anyone uses this laptop for Ubuntu, how does it run.  Also, how much RAM is recommended to run both Windows 7 and Ubuntu (emulated) well?  Is it recommended to do it that way, or to just have a dual boot set up (I'd really like to be able to access both OSs without having to restart, but if this would require too much RAM, I'd go with a dual boo).

---

### Post by dpatel304 on 2009-11-03
Anybody with any suggestions at all?  Thanks.

---

### Post by wilee-nilee on 2009-11-03
So what is your definition of emulate, is this a virtual which I think can be done or a wubi.

---

### Post by dpatel304 on 2009-11-03
I was thinking of using virtualbox or something similar.  Wasn't aware of Wubi.  Just looked it up.  Are there any disadvantages/advantages to using Wubi over virtualbox?

---

### Post by wilee-nilee on 2009-11-03
I'm not familiar with virtual in windows but a gig of ram should be all you need for Ubuntu it will run with 512/MiB but 1 gig is better. Wubi is a pseudo virtual but it will not run side by side with windows but give you a boot to windows or Ubuntu and it runs slower then a dual boot, and is inside windows. The dual boot having separate partitions will be the best install, your Ubuntu and Windows will be separate, but in this scenario you can access the windows partition if needed. The access can be done with Wubi as well but you just have to have the correct programs installed I don't know what they are but I saw a post on the forums yesterday. Wubi leaves the Windows OS open for viri to move from Ubuntu to windows. The Ubuntu OS can pick up viri and not be effected but can pass them on to a windows setup, in the Wubi set up theoretically, the same thing can happen with using wine a windows program reader in Ubuntu. You want to use a live CD to see if this model or any model you buy will run Ubuntu. Any new computer with W7 is going to have at least 2gigs of ram which would be okay in a dual boot but using a virtual I would get 4 gigs. A dual boot is really the best of all set ups unless you have a need to be running windows and Ubuntu at the same time. If I was buying a new laptop that is running Widows I would get 4 gigs of ram, and if your a gamer maybe even more, but there are limitations per computer to the max amount of ram.

---

### Post by snowpine on 2009-11-03
Ubuntu requires 256mb of ram bare minimum (more is better), Windows 7 apparently requires 1gb/2gb of ram (32 bit/64 bit). So you can do the math... 2gb should be plenty for 32 bit, or 3gb for 64 bit. 

I am a big fan of virtualization; I am running Windows XP in a virtual machine with Ubuntu as the host. This is on a desktop with 2gb of ram. I hardly ever go over 2gb (and into swap) even when using "heavy" applications like Adobe CS.

---

### Post by louieb on 2009-11-03
> I'd like to be able to quickly access both OSs,Have HP desktop 4GB memory, host OS is XP - I run Ubuntu inside  [VirtualBox]("http://www.virtualbox.org/") works well.

Memory - think you'll be lite  with the 2GB, but if it were me doing the buying I'd upgrade to 3GB or most likely 4GB memory. IMO - can't have too much.

---

### Post by Marlonsm on 2009-11-03
I run Windows XP inside Ubuntu with 2Gb just fine.
But as Windows 7 is heavier than XP, I think that you'd need at least 3Gb of RAM to run smoothly, leave around 2Gb for Windows and around 1Gb for Ubuntu.

If you use Wubi, it's almost like partitioning the HD and running Ubuntu nativelly, which is much faster and lighter on the hardware (although not as fast as partitioning), but with Wubi you can't run both OSs at the same time, you'll have to choose one during the boot.

---

### Post by dpatel304 on 2009-11-03
Thanks everyone for the responses.  I'm thinking I'll most likely go the dual boot route instead.  I could probably have enough ram to run ubuntu in virtual box on top of win7, but I don't see many reasons to do that over a dual boot.

---

### Post by wilee-nilee on 2009-11-04
> **dpatel304 said:**
> Thanks everyone for the responses.  I'm thinking I'll most likely go the dual boot route instead.  I could probably have enough ram to run ubuntu in virtual box on top of win7, but I don't see many reasons to do that over a dual boot.

Welcome to the world of Linux, a dual boot will be a good start, just make sure you know how to do the partitioning, it can all be done from the live cd install disc.

---


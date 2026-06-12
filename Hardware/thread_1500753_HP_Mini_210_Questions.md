---
title: "HP Mini 210 Questions"
date: 2010-06-03
forum: Hardware
---

### Post by zPenGuiNz on 2010-06-03
Dear Ubuntu Community:

I am very new to Linux as I don't know anything about it other than the helpful guides posted here. I have one quick question, my  netbook is a HP Mini 210 with an Intel Media Accelerator 3150 and runs the Ubuntu Netbook Remix latest version. Is the graphics accelerator natively supported or do I have to install a driver for it? If so, can anyone help me do it? It seems to lag when I play flash games, does that have to do with a driver for the video card missing, or the amount of RAM and my processor speed?

Thank you very much for your time!

---

### Post by dv3500ea on 2010-06-03
[this site]("http://www.intel.com/support/graphics/intelgma3150/sb/CS-031161.htm") says that linux doessn't use the intel driver. 
I'm not sure if it is natively supported or there are drivers available to download. 
To find out go to System -> Administration -> Hardware Drivers.
Note that you shouldn't expect amazing performance from this graphics card and that flash generally sucks anyway because Adobe can't be bothered to create a proper driver.

---

### Post by zPenGuiNz on 2010-06-03
When I went to Hardware Drivers, nothing showed up. Does this mean I have no drivers at all? :X

---

### Post by dv3500ea on 2010-06-04
> **zPenGuiNz said:**
> When I went to Hardware Drivers, nothing showed up. Does this mean I have no drivers at all? :X

It means that you have no drivers installed, and probably that there are no drivers available to install. This probably means that the GPU is supported directly by the kernel.

Regarding the flash games, I don't think the graphics processor has any effect as flash is not (at the moment) hardware accelerated. This means that the flash games don't even use the GPU. Apparently version 10.1 of adobe flash will support hardware acceleration, which should increase performance. [See this article.]("http://download.cnet.com/8301-2007_4-20001890-12.html")

---

### Post by Jonsan on 2010-06-04
YES, if you want to send your laptop and wait for a month to have that  "MINI" part upgraded OR, better talk to the shop you purchased and get  an opinion if they offer an upgrade for the laptop.

---

### Post by kameleontti on 2010-07-21
Here's solution to this problem with touchpad in HP mini 210-10xx -series:

[http://ubuntuforums.org/showthread.php?t=1388164&page=6](http://ubuntuforums.org/showthread.php?t=1388164&page=6)

And, Intel is one of linux-makers. They attend in development of linux drivers and hardware support of their hardware, their graphics cards... so that is included in linux-kernel. So that won't need extra driver installation, like ATI of Nvidia often does need. Moblin was Intel's linux-version and they are now doing MeeGo-linux together with Nokia, that brought their Maemo-linux-version to Moblin. So Intel, like IBM, RedHat, Novell/Suse is among those big linux-developers, has been for long time. Lots of money to linux-development comes there... of the incomes of sold Intel hardware worldwide.

Intel's Media Accelerator 3150 -graphics circuit in HP mini 210 -series doesn't include needed hardware ability to support that (graphics card) hardware acceleration of Flash 10.1 - so that won't work in HP mini 210. You can find Flash support specs in Adobe's web-site for that hardware acceleration. Only Intel media acceleration 4xxx HD -series and better and Ati's and Nvidia's better graphics cards/circuitry inclunde needed support for that - not basic and older models. So don't expect that. Most netbooks are lightweight laptops, not for heavier use. 

If you want netbook that can show smoothly HD-videos, HD-flashes and do easier games, buy HP mini 311 - it has Ati's better HD-graphics circuis and Nvidia's Ion mainboard circuitry in additon to Intel Atom -processor, that has enough ability to do those things. None of netbooks with just Atom-processor and Intel's basic 3xxx-series graphics circuitry with shared memory can play HD-videos smoothly nor handle heavy graphics games, not with any operating system. Hardware in them just doesn't have enough power.

Adding memory from that basic 1 gb to 2 gb eases these light netbooks to play more smoothly basic flash and to operate little better elseway too - but don't expect that to ease these netbooks to play HD(720 or better) flash/mp4 -videos nor heavy graphic games. Basic YouTube flash videos play smoothly and basic tv screening and dvd-quality videos are smoothly playable too but that's the high end of hardware ability with these netbooks - HD-videos are too needy for these. People often hope and it-sellers give imagination of better, but that's not true. Light and cheap is light. 

All we know how frustrating this is with linux-kernels and linux-distros, bcause hardware-architecture-support is changed all the time after kernel/distro version to version. Things work and gets working in time with one version... and then, again, all is messed up with next version and all just have to look after for solutions again. 

I must admit that they actually are way ahead with Windows 7 - everything worked in my HP mini 210-102x -series out of the box with Windows 7 plain installation... but with newest long time support Ubuntu 10.04 installation problems are with touch pad and wireless (can't find wireless like Win 7 does ootb). 

Seems that linux world is very open, indeed, and actually too open, so it openly messes thing up regularly. 
Too many variants maybe, too less organized and managed co-operation to keep all things in hand... especially for the regular user, that would feel pure joy with things just working out of the box - especially with pc-models sold so widely as HP mini 210 -series netbooks are. 

This list is quite bullshit

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

- misinformation and no relevancy with ubuntu versions. Moreover netbook models vary a little in different areas of the world, so information in this page is very often of no use

Thus, ubuntu is easiest distro to intall nowadays, but it's too far from good. Too many distros is the linux-problem nowadays - just one distro, done openly together, with options in it to select for everybody's needs, would be much much better for all.

---


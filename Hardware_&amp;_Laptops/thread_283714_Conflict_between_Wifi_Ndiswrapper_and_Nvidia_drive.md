---
title: "Conflict between Wifi Ndiswrapper and Nvidia driver"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by mlat on 2006-10-24
There is a problem which is currently not very noticed right now (I did some google searching, and I came to a few pages reporting the problem with no solutions).

I'd like to have a take at the folks here.

Basically I have a conflict between the Ndiswrapper program (I use it for BCM1390M (broadcom 4311)) and the Nvidia drivers. The problem is, whenever I have both installed, the wireless decides to crap out a few minutes (or instantly) when using it. So I'm either stuck without wireless or I use the generic nvidia drivers (which I'm doing).

However, the generic nvidia drivers are slower and have a few problems seeing how they're not designed for the video card in my laptop, so I want to try to get both working.

Essentially the problem as far as I know is that ndiswrapper has a IRQ conflict with the nvidia driver, which causes the wireless to cut out randomly. The first solution is for me to use a driver made for linux, however none exist for my wireless type yet. Some people were talking about messing around with the kernel on other sites but gave no specific detail, as I'm beginner-intermediate with linux (not even close to hacking at the kernel yet).

Right now, it's not a huge issue seeing how ubuntu works and I'm able to use it on a day to day basis. However, I'd rather bring it from "works" to "perfect" ;)

Any suggestions would be very helpful.

---

### Post by AlReece45 on 2006-10-28
Check to see if there's a BIOS Update for your computer. I had similar problems with a USB Mouse and Ethernet, of course my wireless wasn't working when there were conflicts.

---

### Post by cbruno on 2006-11-12
I have the same problem as you. When I use the generic smp enabled kernel on Ubuntu, I get an IRQ conflict with ndiswrapper and the nvidia drivers.

I found that the problem goes away if I use the 386 kernel. Of course, then you lose SMP functionality, which isnt really a big deal depending upon what you use your computer for.

Chris

---

### Post by LukeyMI on 2006-11-12
> **cbruno said:**
> I have the same problem as you. When I use the generic smp enabled kernel on Ubuntu, I get an IRQ conflict with ndiswrapper and the nvidia drivers.

I found that the problem goes away if I use the 386 kernel. Of course, then you lose SMP functionality, which isnt really a big deal depending upon what you use your computer for.

Chris

Check if you have the eeprom module loaded. I was tinkering around trying to get lm_sensors working on my new Compaq laptop (v6030 w/ 4311 broadcom wireless) and ended up having that module added to /etc/modules. That's when the trouble started, although it took finding a post somewhere on the forums here (sorry, don't remember what I searched for) to know that the eeprom module was my problem. I removed that from /etc/modules and have been trouble free ever since. I can't use lm_sensors (never got it working anyways), but to me having stable 3D video is more important.

I also have these in my xorg.conf just under the Driver "nvidia" line:

Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"

There was a nvidia driver wiki page and that was one of the suggested things to try on the wiki page. It seems like there were some other options to try but I don't have the addy for that either. :\ Maybe somebody can help with that?

---


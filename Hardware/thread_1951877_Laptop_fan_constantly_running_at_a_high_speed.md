---
title: "Laptop fan constantly running at a high speed"
date: 2012-04-03
forum: Hardware
---

### Post by regua on 2012-04-03
I've had my Lenovo Y530 for about two years now and had never had any problems with it. Recently, however, the fan started constantly running at a high speed, while previously it had been pretty much silent unless I was running a CPU-intensive program.

The first thing I did was open up the laptop and clean the fan - there was a lot of dust, and even though I didn't manage to take the fan out completely as some parts were blocking it, I think I removed almost all of the dust. The fan runs a little better now, but it still never goes silent - which is *really* annoying when I have to do work in a silent environment.

I checked if the problem lies on the side of the OS and haven't found anything. Obviously I checked [FONT="Courier New"]top[/FONT] for anything that could be straining the CPU. Unfortunately the fan in this Lenovo model cannot be controlled by Ubuntu as far as I'm aware ([FONT="Courier New"]fancontrol[/FONT] doesn't work, for instance), so my options were limited. I checked for overheating, but [FONT="Courier New"]sensors[/FONT] doesn't report anything unusual:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +35.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +36.0°C  (high = +90.0°C, crit = +90.0°C)

```There are also no BIOS updates for this model so that is out of the question.

Any suggestions? How can I locate the cause of the problem? I've read multiple threads on this topic and none of them solved the issue.

Thanks for any help!

---

### Post by Mark Phelps on 2012-04-04
Hate to say it, but if you use the laptop a lot (e.g., daily), it's possible the fan is simply wearing out.

I started encountering similar problems with my XP-era laptop a few months ago.  I opened it and cleaned it out, and had the same experience as you -- worked quietly for a while, but then over time, the fan started running more and more often.

The clue to me was when I started getting BIOS error messages about the fan being shut off!  It wasn't (because I could clearly hear it), but that bothered me a lot.

I replaced the fan with one I bought off the Internet.  It was a lot of work taking the laptop nearly completely apart and reassembling it -- but now, the new fan runs quietly and I no longer get those error messages.

My fan cost the great sum of $30 -- which I thought was well worth the cost when faced with spending $500 to get a new laptop with the same features.  But, if you're not up to the effort of tearing it apart, you should look into repair estimates.

---

### Post by regua on 2012-04-05
Hey Mark,

Thanks for the reply.

It's still under warranty so I might be able to get Lenovo to fix the fan, but I'm currently abroad so I thought that maybe a simpler solution exists and I wouldn't have to bother with their customer service.

---

### Post by Jose Catre-Vandis on 2012-04-05
What kernel are you running? I move up from 3.0 to 3.1 and that killed my fan controller.

---

### Post by regua on 2012-04-05
> **Jose Catre-Vandis said:**
> What kernel are you running? I move up from 3.0 to 3.1 and that killed my fan controller.

Hmm, I'm on 3.0. I might try 3.1 just to see if it has the opposite effect for me.

---

### Post by Mark Phelps on 2012-04-05
> **regua said:**
> Hey Mark,

Thanks for the reply.

It's still under warranty so I might be able to get Lenovo to fix the fan, but I'm currently abroad so I thought that maybe a simpler solution exists and I wouldn't have to bother with their customer service.

Unless the laptop came with Ubuntu preinstalled (and I'm guessing it did NOT), you're likely to get no help from their support folks -- and denial of support for a warranty claim.

If the fan misbehaves using the OS the laptop had originally, then you probably DO have a valid warranty claim.  In that case, I would backup your Ubuntu install, remove it from the laptop, and send the laptop back with ONLY the original OS on it.

---

